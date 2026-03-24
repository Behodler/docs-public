# Distributed TVL
The ideal situation for PhUSD is to have TVL distributed between the AMM and the vaults. Currently, this is fairly balanced with about $10k of sUSDS in Balancer and $20k in the vaults.

The easiest way to build an intuition for this is to explore the scenarios where TVL is either skewed all in the AMM or all in the vaults. We'll see how this can occur, what this results in and how it can be fixed.

## Vaults only
### How this occurs
The Dola Depeg resulted in this scenario unfolding. Here, a user was able to mint excessive PhUSD (about $7k) for a cost of $70.

The resulting minted PhUSD was all sold onto Balancer, draining the position of all its sUSDS.

When the Dola price recovered, the vault TVL jumped by $7k.

The net result was effectively that $7k jumped out of the AMM and into the vaults.

### Results
Since sUSDS exited the AMM, we no longer had phUSD growing in price at the same rate of sUSDS. The skewing effectively shuts off a source of future minting.
In addition, stakers and other holders can no longer sell PhUSD. All they can do is continue to earn yield on staked PhUSD.

For these two reasons, leaving it in this position halts future minting.

### Fixes
One way to fix this is through governance action: Withdraw the additional $7k from the vaults, use it to buy phUSD on Balancer and burn the PhUSD. This entirely reverses the effect of the skewing. This is the approach we took. 

An organic fix, that is allowing the equilibrium to naturally re-establish would have required some liquidity to trade on an infinite range. Under this scenario, when the primary concentrated liquidity moved out of range, traders would have had to rely on fall back UniswapV2 style liquidity. The price would have fallen off a cliff at this point. However, the benefit of this approach is that once the price floor is established, the AMM would still contain sUSDS. Combined with the now enormous staking APY, the only direction for phUSD from here would be up. Speculators would do very well to jump in at this point. This is the rebound effect. 

## AMM only
### How this occurs
This can't happen without deliberate governance action. Here governance would withdraw all TVL from the vaults and pool it all into the AMM.

### Results
This would kill the staking APY. However the AMM liquidity could now handle much bigger sells. There would still be price growth pressure but this would come exclusively from sUSDS price growth.

### Fixes
Governance can of course revese this course of action. However, let's explore if this situation naturally fixes itself.

As noted, the price continues to grow at the same rate as sUSDS. If no one sells, eventually the price will crest $1. At this point mint-and-sells occurs, causing vault TVL to begin recovering. Staking APY picks up from zero. In time, very gradually, the TVL will rebalance and restore itself.

Suppose all the stakers panic sell. Depending on how liquidity is set up, either the price will drop or slippage on new purchases will rise. If liquidity is managed on a traditional xy=k AMM then the price drops. At this point, we have to wait for the price to naturally rise to above $1, driven by sUSDS growth. This could take years!

The high slippage outcome is similar and would be the result of concentrated liquidity. Here instead of the price falling off a cliff, liquidity falls off a cliff. We'd need the price to rise well above $1 in order to justify the large slippage from mint-and-sells. This would likely also take years.

Without vault TVL, the rebound effect still exists but is glacial. The vault with TVL and yield independent of phUSD is what drives the elastic snap back of PhUSD prices. 
Therefore the only risk of this occuring and remaining this way is bad governance.

We must therefore be very careful in not creating a governance attack vector when expanding the usefullness of EYE.