# Background
On March 22, an exploit in Resolv's USR stablecoin sent ripple effects throughout DeFi including a token Phoenix relies on, Dola by Inverse finance. The reasons and nature of the exploit are not the purpose of this article. More info can be ([found here](https://x.com/omeragoldberg/status/2035772805812453759)).

The effect on Dola was for it to briefly lose its $1 peg and drop as low as 1c. This lasted for a very short time but in DeFi, all it takes is one block for havoc to spread.

## Recap: Phoenix High Level view
If you know how phUSD works, you can skip this section. But having a basic understanding here will help understand both the attack and the solution.

### Mechanics
PhUSD is minted by supplying 1 of 2 tokens, USDC or Dola. The minting if fixed at 1:1. As time passes, the list of available tokens to mint will grow.
Each input token maps to a destination vault. When you mint with USDC, the USDC is deposited into AutoFinance (formerly Tokemak)'s USD vault. Dola is deposited into the AutoDola vault. 

The yield from both is collected and sent to a staking module. Holders of phUSD can stake to earn this yield.

Finally there's an AMM, Balancer, supplied with a pool of sUSDS and phUSD. Users who wish to sell their phUSD or buy on the open market can make use of this pool.

The yield funnel and NFT mechanics, while important, are not necessary to be understood for this article.

### Market dynamics
PhUSD's price is market determined and most of the liquidity is currently on Balancer. The circulating supply of phUSD is split between staked phUSD, earning yield and Balancer liquidity.

At the time of writing, this is the distribution of phUSD:

Source | Value
--- | ---
Total Supply | 26954
Staked | 11112
Balancer | 14230
Uniswap | 659
Remainder | 953

Remainder is all wallet balances but may include AMM liquidity not accounted for. It represents 3.5% of total supply. If it were all sold at once, it would result in 0.5% slippage.

### Backing of PhUSD

Unlike other stablecoins, phUSD isn't backed by one type of TVL source such as liquidity or a redeemable vault. Instead the backing of phUSD is split between the vault TVL and the AMM liquidity. The vault does not provide a redeemable backing but instead provides an ongoing staking APY to keep phUSD locked out of circulation. As long as phUSD is in either the staking module or the AMM, it backs the remainder. 

The technical reasons for the [backing of PhUSD is explained here.](backing.md) 

We can think of TVL backing phUSD as split between TVL_vault and TVL_amm. Right now TVL_vault is split between USDC and Dola. TVL_AMM is sUSDS.
The multiple source backing works best when the TVL is distributed between the vaults and the AMM. If it skews in one direction, we enter a suboptimal equilibirum. The two extremes are [explored in this article.](skewedTVL.md).

## The attack
When the price of Dola dropped to 1c, someone minted just under 7000 phUSD at a personal cost of about 7000 Dola, costing only $70. They then sold that for about $6500, incurring a profit well over $6000. the net result is that our Balancer pool, being concentrated liquity, traded out of range and filled up entirely with phUSD.

As soon as the Dola price recovered, the vault TVL jumped by about $7000.

### The immediate effect
Looking at overall TVL as TVL_vault + TVL_amm, there wasn't much change. It just all skewed vault. The problem with this outcome is that stakers of phUSD and other holders would now be unable to sell their tokens or their phUSD staking rewards. Fortunately, the USDC rewards would still roll in and in fact would increase. But their staked positions would now be transformed from staked capital into rights to earn yield.

Another effect is that part of phUSD's price growth comes from it being paired to a yield bearing stablecoin. As sUSDS grows in price, so does its paired token, phUSD. Since there are no external AMMs and no floating whale wallets, there's no way for arbitrage traders to sell and reduce the price of phUSD. Once phUSD exceeds $1, it becomes profitable to mint and sell in the AMM.

If all the sUSDS is drained, not only can the phUSD price not naturally grow but there's no way to profit from mint-and-sell behaviour. This arrests our primary source of TVL_vault growth. And so the whole system grinds to a halt.

## Robust by design
One of the benefits of splitting TVL is that phUSD is backed by multiple protocols. On the token front, we have Sky (USDS and sUSDS), Inverse Finance (Dola) and Circle (USDC). On the TVL storage front, we have Tokemak, Balancer and Uniswap, as well as Crv and Convex.

If one protocol fails, we can use one of the other pools of TVL to act as a rescue fund.

### Exploring the result of Dola never recovering
Suppose Dola had failed entirely and never recoverd. Our response could have been to have withdrawn 7000 USDC from the USDC vault. Currently the vault contains $11.8k. So although this would represent a significant reduction, it wouldn't be the end of the vault. Then using the USDC we could purchase sUSDS and then purchase phUSD on Balancer, bringing the price and liquidity back into the centre of the range. The purchased phUSD would then be burnt.

The yield on staked phUSD would then drop to about 10% overall (still above market average).

In this scenario, the result of the attack would have been to leave vault_TVL unchanged while draining liquidity. By withdrawing $7k from the vaults, to rebalance the AMM, we're shifting the composition back to a balanced position in order to keep the dynamics of phUSD alive, at the expense of reduced staking yield.

From there, we choose an alternative to Dola and begin rebuilding as our overall TVL has falled by $7k without reducing the obligations to stakers.

### Dola's recovery: antifragile
Since Dola recovered its peg, our overall TVL didn't shrink at all. It temporarily shrunk but when Dola recovered, the vault TVL grew by the attack size.

This is a remarkable result in itself. Much of DeFi suffered permanent outflows because of the depeg. For Phoenix, all that occured was a redistribution from liquidity to vault_TVL.

The fix then was an easy one. Simply withdraw the surplus $7k from the vaults, purchase phUSD on Balancer and burn the purchased phUSD.

Because the AMM experienced a massive sell followed by a massive buy, the net result for LP providers was quite a spike in fee revenue. As for the rest of phUSD, the result is unchanged vs prior to the attack. 

The whole shock actually increased overall liquidity and TVL slightly. This is antifragility in action.

## Increasing Resilience for the future
Even though the attack left Phoenix unscathed, there have been some lessons for the future. There's something about real life fire drills that always bring a degree of learning that can't be planned for.

### What has not changed
As before, we will continue to seek new protocols and tokens for minting and yield bearing. There are a number of priorities in development but this one has been bumped to number 1.

### Some things worth considering
When PhUSD traded out of range, certain mechanics of phUSD halted as mentioned above. Had the liquidity been stored in a classic infinite range xy=k style AMM, we would have experienced the rebound effect as laid out in the original documentation. Instead of all sUSDS being drained, there would have been a remnant, creating a price floor of phUSD. Form there, any new entrants into PhUSD would get impressively large APY on the staking module.

The downside to pure unconcentrated liquidity is that it requires much bigger TVL in order to get the same liquidity during ordinary operations. As such, it seems ideal to have a combo where typical range trading happens in a concentrated range but a fallback full range pool exists for when crises strike. This would balance efficiency and antifragility quite nicely. In time, trading fees would naturally strengthen the entire system without requiring additional incentives. This approach to mixed liquidity will continue to be explored.



