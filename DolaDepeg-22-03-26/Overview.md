# Background
On March 22, an exploit in Resolv's USR stablecoin sent ripple effects throughout DeFi including a token Phoenix relies on, Dola by Inverse finance. The reasons and nature of the exploit are not the purpose of this article. More info can be ([found here](https://x.com/omeragoldberg/status/2035772805812453759)).

The effect on Dola was for it to briefly lose its $1 peg and drop as low as 1c. This lasted for a very short time but in DeFi, all it takes is one block for havoc to spread.

## Recap: Phoenix High Level view
If you know how phUSD works, you can skip this section. But having a basic understanding here will help understand both the attack and the solution.

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
The multiple source backing works best when the TVL is distributed between the vaults and the AMM. If it skews in one direction, we enter a suboptimal equilibirum. The two extremes are [explored in this article.](skewedTVL.md)





