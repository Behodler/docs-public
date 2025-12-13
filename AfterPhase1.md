# Recap

phUSD is a new brand of stablecoin, an evergreen coin which draws in a growing stream of liquidity from external DeFi — an antifragile token that derives its stability from the very same volatility of AMM trading that so many tokens struggle to overcome.

Achieving this vision is a multi-step process, broken up into distinct phases, each establishing important foundations to ensure the Phoenix system works as intended.

A side effect of phUSD is to inject new liquidity into the entire Behodler ecosystem, and indeed the first phase is a demonstration of the B3 AMM technology.

So whether you’re a long-term Behoblin or just someone new looking for an early-adopter opportunity, you’ve minted phUSD on phusd.behodler.io at a discount (if you haven’t, go do it now). This is **Phase 1**, the initial capitalization.

<img width="725" height="181" alt="UI" src="https://github.com/user-attachments/assets/ab6f88e6-4188-43d1-a912-8ead9efb12bb" />


Phase 1 is the ignition round where we raise the initial seed capital used to ignite the cycle of perpetual liquidity growth. After this phase concludes, we enter a phase of stabilization. This is where we take the capital raised in Phase 1 and split it into two separate components of growth. Astute readers may notice that we initially go from 100% capitalization of phUSD on the bonding curve of Ignition to an under-capitalized version immediately after, where some of the capital is put in an AMM and the rest in a growth vault.

This can prompt two fears:
1. Are early adopters at risk of a panic dump causing the price to drop?
2. Are there any opportunities to earn any form of yield from phUSD?

The first concern surrounds immediate loss and the second, opportunity cost for holding phUSD. This article will address both concerns with not just words but with a set of smart contracts which are about to be deployed. The good news is that we put the interests of early adopters front and centre, and both concerns are well handled.

## What happens to the capital raised in Phase 1?

First we need to understand the core of Phoenix after the Ignition Phase. The capital from phUSD minting is split immediately after the Ignition Phase into an AMM and a yield-bearing vault. The token in the AMM is paired with phUSD. Rather than a regular stablecoin, it will be a wrapped stable that grows relative to its base — for instance, sUSDS, the staked version of USDS which earns a yield reflected as perpetual price growth. This introduces the first vector of price growth for phUSD.

Why? Consider a pair of phUSD/sUSDS on Uniswap.  
We seed the pair with 100/100 of each token and assume for this example that the price of sUSDS is $1. After some time, sUSDS grows in price to $1.1. If the balance of phUSD in the pair remains unchanged, its price automatically rises to $1.1. Since there are no other pairs or exchanges containing phUSD for now, this is a safe assumption to make.

The remaining capital is in a vault. The effect of this vault is second-order: here, the yield is siphoned off and used to grow the price of phUSD.

### Why not put all the capital in the AMM?

To understand the power of splitting, an example will help. Suppose we’ve split the capital such that there is $100 in the vault, earning 10% APY, and $100 in Uniswap as sUSDS paired with 100 phUSD.

Let’s say that the price of phUSD suddenly drops to 50c. Using the numbers above, we end up with a pair of about 70 sUSDS and 140 phUSD.

What happens to relative yield? In the AMM, if the price of sUSDS rises by 10% from now on, the price of phUSD will rise by 10%. This means the relative effect on price from the yield of the AMM token remains unchanged.

What about the vault yield?  
Previously, the vault was producing $10 in yield per year. Suppose we use $10 to purchase phUSD *before* the price dropped. Plugging in the numbers:

```
xy = k
100 × 100 = 10000
110 × x = 10000
=> x = 90.9
=> price of x = 110 / 90.9 = 1.21
```

Price grows by 21%.

Now consider the effect of the very same amount of yield on the price of phUSD *after* the price drop to 50c:

```
xy = k
140 × 70 = 9800  // rounded numbers give slightly different k
x × 80 = 9800
=> x = 122.5
price of x = 65c
```

The price grew from 50c to 65c, a 30% rise.

Note that since the vault yield remains steady in absolute value, its relative effect on the price of phUSD rises as the phUSD price falls. This counter-cyclical effect is what we’re calling the _rebound_ effect. It means that phUSD becomes more attractive to hold for new buyers the more the price drops. Eventually it becomes irresistible to buy, since the growth moves off the charts. Think of price dropping as an elastic stretching, the snap back of which is more dramatic, the bigger the stretch.

## Minting

We now have an upward push on phUSD but no mechanism for growing TVL. This is where fixed-price minting comes in. We have a contract which accepts stablecoins and mints phUSD at 1:1 or $1. The proceeds of the mint flow directly into the yield vault.

Why would anyone mint? Precisely because combining an ever-increasing price pressure on phUSD with fixed-price minting means you can mint low and sell high for a profit.

Suppose, for instance, that the price rises to $1.2 on the AMM. You mint at $1 and sell into the AMM until the price falls back down to $1, pocketing the profit.  
The yield vault capitalization has now increased, meaning more yield flowing back to pumping up the phUSD price. This gives more force to the next rebound snap back, making any future price either last for a shorter duration or able to absorb a bigger sell off for the same time of recovery. 

*LP provider sidenote: you may notice that this initially wild oscillation around a stable price is the perfect storm for very high LP fee earning potential.*

## Price growth mechanism equivalence

It was mentioned that we could use the vault yield to buy phUSD on the AMM. However, there’s no need for the Phoenix ecosystem to purchase on the AMM itself — indeed this introduces all sorts of extra complexity involving oracles, all of which increases security risks and slows down development time.

Instead it is good enough to simply provide an incentive for users to buy on the AMM themselves. An easy, low-risk approach is to offer the yield from the vault as a phUSD burn incentive: burn phUSD and earn Dola, for instance. Users who wish to participate can purchase the phUSD themselves, inducing the price rise.

Imagine a simple UI with an exchange rate of Dola for phUSD. Users who send in their phUSD are immediately given Dola, like a simple AMM swap. It would almost feel like they're minting Dola or redeeming phUSD. Behind the scenes the phUSD is burnt and the source of Dola is the vault yield.

Users either supply their holdings of phUSD or they buy from Uniswap in order to burn at a profit. In this way, the buying on Uniswap happens without us having to write any sophisticated oracle driven code.

The benefit of this approach is that the supply of phUSD falls and the price rises, so that the vault yield is transformed into an engine of vault growth, creating a virtuous cycle and rewarding phUSD holders with a source of yield (burning).

## Problems with burning on day 1: the threat of early adopters

Again, using numbers, we can illustrate a potential issue with adopting this approach on day 1.

Suppose after Phase 1, we mint 2500 phUSD at a price of 79c. This implies 1975 Dola. We split the Dola 80:20 where we place 1580 into the AutoDola vault, earning 8% APY.  
The remaining 395 is converted into sUSDS and placed in Uniswap with 395 phUSD minted fresh, implying a starting phUSD price of $1.

At 8%, the amount of Dola generated from 1580 is 126.4. This can be used to purchase sUSDS on Uniswap. Assuming sUSDS is $1 in this example, the effect is:

```
xy = k
395² = 156025
(395 + 126.4) × x = 156025
=> x = 299
=> phUSD price is now $1.74
```

This is an amazing result. An 8% APY from the vault translates into a 74% price rise!

There’s just one problem: the early adopters. In the above example, the 74% price growth takes a year to unfold. In the meantime, the early adopters are sitting with 2500 phUSD which they can dump at any time. Suppose they do decide to dump immediately:

```
xy = k
(395 + 2500) × y = 156025
=> y = 53
phUSD price is now 53 / 2895 ≈ 0.18c
```

Before we panic, recall the rebound effect: because the vault yield is unchanged, the relative APY of the vault on phUSD will skyrocket after this dump.

Unfortunately, early adopters who do not immediately sell will lose out in this scenario and will have to wait for the price to recover.  
With such a large early-adopter base, the burn incentive is just too small to provide a viable form of yield.

# Solution: from buying to staking

Instead of a burn incentive, we can create a farm. Suppose we use the vault yield as a stake incentive: stake phUSD and receive Dola yield. This has two major advantages:

1. Immediate yield opportunity for early adopters
2. Rewards in pre-existing stablecoin

Recall that the yield is $126.4. The early-adopter batch of phUSD at market price is $2500.  
Therefore the yield is 5%. This is less than the % APY they could get by staking in AutoDola.

We wish instead for the yield to be better than AutoDola and potentially the best of all stablecoins. So in addition to the Dola yield, we introduce a phUSD yield of a fixed APY (e.g. 5%). This brings the total APY to 10%.

This has the immediate benefit of providing a high yield for phUSD holders on day 1.

Let’s consider best- and worst-case scenarios from this approach.

### Best-case scenario: everyone stakes

Suppose all 2500 phUSD is staked. The AMM pair now has zero sell pressure, meaning the price will grow with sUSDS. Suppose sUSDS grows 10%. This will take the price of phUSD to $1.1.

Let’s say someone comes along and mints 100 phUSD at a cost of 100 Dola. They sell 20 phUSD to push the price back down to $1. They stake the remaining 80 phUSD.

The vault has increased by 100 Dola but the staked phUSD has only increased by 80. This means that the Dola yield for stakers rises.  
In this example, the yield now rises to 134.4. The staked amount of phUSD rises to 2580.  
The new Dola yield is now 5.2%, up from 5%. Total staking yield is now 10.2%.

This means that every time a mint takes place, if all the phUSD not sold for profit is staked, the relative Dola yield rises! The incentive for early adopters to dump falls.

What’s more, the buying and selling on the AMM from these cycles incurs fees, increasing liquidity. Over time, the liquidity will be large enough to absorb all of the early adopters selling. So the mixed-yield farm acts to indirectly eliminate the threat of early-adopter dumping and acts to protect early-adopter holdings as time proceeds.

### Worst-case scenario: big dump occurs

Suppose we introduce this yield farm but half of the early adopters dump their holdings nonetheless. Firstly, let’s consider the price of phUSD after the dump:

```
xy = k
(395 + 1250) × y = 156025
=> y = 156025 / 1645 ≈ 94.84
=> price of phUSD ≈ 5.7c
```

Suppose the remaining phUSD holders stake their 1250 (now worth $70).  
The relative Dola yield alone is 126.4 / 70 = 180%, which is clearly much higher than 10%.

This means that as the price of phUSD falls, the APY on the yield farm rises! This is quite different from governance-token yield farms where the dollar yield falls when the protocol token falls. This is because we’re rewarding in a fixed yield of an external stablecoin. The rebound effect occurs regardless of how yield is distributed.

An obvious objection is that if you held 1250 before the price dropped, it would be worth $1250 but now it is only worth $70. This is true, but consider the case for new holders buying in at 5c. For them, the 180% APY is real. Therefore, the effect of early adopters dumping is to provide a massive incentive for new buyers to restore the price back to $1 as fast as possible. Until they do, the yield will be well above 10% in a real stablecoin, not a hopeful token. The _elastic_ is very taught when the price is 5c.

## Why have a phUSD emission?

Note that as the price of phUSD drops, the contribution from phUSD emissions evaporates and the reward collapses into pure Dola. However, the total APY skyrockets. In other words, a loss of confidence in phUSD leads to a backstop of pure Dola rewards.

So what is the purpose of phUSD emissions in the yield farm?  
Recall that at a price of $1, initially the Dola yield is less than 8%, leading to an opportunity cost for phUSD stakers who could rather get 8% on AutoDola.

The phUSD reward is meant to bridge this gap so that sUSDS growth in the AMM can push phUSD over $1 and lead to more minting.

However, we can do one better. Suppose we set the phUSD emission to 6% so that, combined, the Dola and phUSD reward at a phUSD price of $1 is 11%. This may create enough incentive for yield hunters to actually mint phUSD just to earn yield through staking, leading to an increase in vault TVL.

## Wen?

The contracts have been written for the yield farm that we’re codenaming **phLimbo**. 

<img width="503" height="500" alt="phlimbo" src="https://github.com/user-attachments/assets/1ce1225d-9f08-43e3-a0e4-10c77bcda1b9" />


Silly names are just for contracts. The UI will present a straightforward interface. The minter contract has also been written. What remains is some security reviewing and the UI. Phlimbo is in the final stages of post audit fixing. After that, phUSD holders can immediately start earning high yield on their phUSD minted in the Ignition Phase.

Now is your last chance to mint at a price below $1.

# Conclusion

The separation of TVL into liquidity and yield generation is the cornerstone of rebound economics. Using this approach, we can ensure that phUSD hits the ground running and that early adopters are not only safeguarded against short-term panics but are in fact able to immediately earn very high APY on phUSD staking.

And this is just the beginning. In future phases, the yield on phUSD will increase and SCX, EYE and Flax will all get in on the action.

Stay tuned for more.
