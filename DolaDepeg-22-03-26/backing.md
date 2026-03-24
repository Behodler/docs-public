# PhUSD Backing
PhUSD can be thought to be backed by two primary sources, the vault TVL (vault_TVL) and the AMM TVL (AMM_TVL).

While it may be intuitive for AMM TVL backs PhUSD, it may not be as clear as to why vault TVL provides a backing.

## Backing: stock vs flow
In a traditional redeemable vault, the backing would simply be its redemption value. That is, you'd be able to mint phUSD by supplying a stablecoin at 1:1 and when you wish to cash in, you trade in your phUSD for the original stable.

In Phoenix, we intentionally make it a 1 way mint.

Instead of providing a fixed stock of redemption capital, we put the capital to work in external DeFi vaults and use the incoming yield to provide a backing.

We do this by providing a standard staking farm incentive. This locks up phUSD, reducing sell pressure. If enough users stake, the AMM is able to absorb the sell pressure of the remaining phUSD. So in this way, the staking module amplifies the effectiveness of the AMM in its ability to back PhUSD.

### Why can't you have both?
It is very tempting to try to get both outcomes, to allow minters to stake and redeem and simply to skim off the yield for staking incentives. This would seemingly benefit from having PhUSD be fully backed by redemptions. However, this actually turns PhUSD into a staking farm in disguise. If users can mint and redeem at any point, this is equivalent to staking/unstaking. 
Under DeFi norms and expectations, when you stake, you expect to be able to unstake your full capital at any point in time. 

The problem is that most modern vaults experience short term impermanent loss. This creates the situation where the capital backing phUSD temporarily drops below its stated value. If users redeem during these dips, how do we prioritize the redemption? Either we allow the redemption value to dip or we give users their full backing and hope that no bank run situation occurs. If we allow the redemption value to dip, then someone may deposit $100 and only unstake $95 the next day. 

On the other hand, if we give full backing, it may be the case that 90% of users can unstake but the remaining long term holders are left high and dry. 

An alternative solution is to only use vaults that explicitly retain their value relative to the token. USDS/sUSDS is an example of such a vault. The problem here is that our scope of available DeFi narrows dramatically. High yield liquidity positions are now off the table, even if they're low risk.

It also means we have to restrict ourselves to stablecoins forever. With the current mint only approach, we leave open the future possibility of opening to all manner of tokens.

### Is this stable?
One might look at this arrangement of using staking incentives to lock phUSD and grow nervous at the prospect of fickle stakers suddenly unstaking to sell in the AMM.

However, when you encompass the full picture of Phoenix, a remarkable picture of stability emerges. Instead of fixed redemption contracts, we have create a  a stable equilibrium, an attractor. Anything outside of the equilibrium is unstable and forced to collapse back into stability.

Consider the scenario where users stakers suddenly unstake their PhUSD and sell onto the AMM?

The immediate effect is that APY on the staking module sky rockets. Why is this? The majority of incentives in the staking module is comprised of externally sourced stablecoins. This means that the flow of value to stakers is independent of the current phUSD price. In other words, if the current total yield is $100 per month and the price of phUSD halves, it remains $100 per month.

The yield is divided by stakers. Suppose 1000 phUSD is staked and the annual yield is $100. This results in an APY of 10%. If half of the staked phUSD leaves, the APY immediately jumps to 20%.

If the half that left sell onto the AMM and the price of phUSD halves then effective APY in dollar terms for stakers doubles to 40%.

It may not feel that way to the remaining stakers. For them, the rewards probably still feel like 20% (which is still double the original 10%).

However, for newcomers, the 40% figure is real. If they mint phUSD and stake, they'll partake of this high yield.

What if the price continues to drop?
Where would the phUSD used to drop the price further come from? The vast majority that is outside of the AMM is in the staking module. As users unstake, the staking APY rises and the avaialable quantity of phUSD to sell dwindles. This creates a price floor combined with a massive staking APY. 

At some point, the incentive to stake becomes overwhelming as the equilibrium of unstaked phUSD becomes increasingly unstable. 

To make this more unstable, the paired token in the AMM is a yield bearing stablecoin, meaning that the price floor is now growing at the rate of growth of the yield bearing stablecoin.

New stakers can either buy on the AMM or mint and stake. However, purchasing on the AMM will be much cheaper. And so the intial outflow of staking to the AMM collapses and is reversed.

What about a reverse situation where PhUSD is excessively purchased on the AMM and staked, driving down staking yields.

In this scenario, the price of phUSD would rise above $1. As soon as it does, arbitrage trading bots mint PhUSD and sell onto the AMM. This both reduces the current market price and raises vault_TVL which increases yield flowing to the staking module, creating room for the new stakers. Under this equilibrium, a surge in demand for staking creates its own yield.

This is another novel result. In most other DeFi farms, there is a limit for new stakers. In Phoenix, new stakers create their own capacity. The upper limit for stakers has nothing to do with the PhUSD market cap and is only bounded by DeFi's total size.

Phoenix can effectively swallow infinite demand.

So returning to the question: "is this stable?" On a block to block basis, it can be potentially more volatile than a 1:1 backing but the sheer gravitational force binding the $1 price in place means that what it loses in momentary predictability, it makes up for in *singularity*.