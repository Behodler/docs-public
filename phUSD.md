# What is phUSD

## TL;DR

- **Phoenix** is the latest dApp from Behodler, part of the roadmap leading up to Behodler 3.  
- Designed to fuel Behodler 3’s success with imported yield.  
- Phoenix mints **phUSD**, a new kind of stablecoin which siphons external yield into the ecosystem.  
- **phUSD** is a high-yield stablecoin backed by protocol-owned liquidity.  
- Sustainable and safe yield from stacking multiple sources, not rented liquidity; Liquidity can't leave once it arrives  
- **staked phUSD = thriftcoin:** stable, appreciating, high yield.  
- Yields are sustainably above market-rate for wider DeFi due to yield-stacking innovation.  
- Phoenix will launch phUSD into orbit through automatic stages, each boosting velocity, similar to rocket stage separation.
---

<img width="400" height="400" alt="Enhanced Phoenix Behodler monster" src="https://github.com/user-attachments/assets/e27d91f4-fa5d-47b6-8342-0e612b4d54b4" />


## From ReFlax to Phoenix: The Evergreen Vision

From the very beginning, the vision to realise **Behodler 3** has been clear: import yield from across DeFi and use it to power an ecosystem that grows stronger with time. Rather than try to ignite our own flywheels, we wish to light a fire of continual TVL growth using yield sources from the rest of DeFi.

> **The breakthrough came with **protocol-owned liquidity** combined with **yield stacking**.**
>
> 


ReFlax was always a working name for the project to highlight the nature of reinvestment inherent in the design. ReFlax went through several iterations — each exploring how to bring external yield into the protocol and use it to strengthen the Behodler ecosystem. The vision of importing DeFi yield is strong but the challenge lies in retaining that yield. Ultimately an app that pays stakers who leave as soon as they arrive may end up paying valuabel reward tokens in exchange for practically no value. This valueless transfer shows up as inflation. Ultimately this is unsustainable as every price shock weakens the ecosystem as fickle users flee, taking their staked capital with them.

This is at odds with the **antifragile** impulse that has always animated Behodler. Antifragility, a term coined by Nassim Nicholas Taleb, describes systems that don’t just survive shocks, but actually *benefit* and grow stronger from volatility, randomness, and stress.

The breakthrough which gave us the confidence to move from working name (ReFlax) into production came with the shift to **protocol-owned liquidity** combined with **yield stacking**. Instead of renting yield, we will capture it permanently. Instead of fragile dependence on outside actors, yield compounds inside the system itself — deepening liquidity, expanding backing, and reinforcing stability over time. Ironically, preventing fickle assets from abruptly leaving ultimately results in higher yields for all participants.

This is the foundation of what we are now calling **Phoenix**, the dapp which mints **phUSD: the first Evergreen Stablecoin.** A design that doesn’t just hold the peg at $1, but becomes impossible to fail in the long run, because every arbitrage, every cycle of volatility, and every yield stream feeds into a stronger, more resilient base.

---

## What Phoenix Achieves

1. **Paves the way for a new kind of stablecoin — an Evergreen Stablecoin.**  
2. **Imports yield from the wider DeFi ecosystem into Behodler, powering up Limbo.**  
3. **Yield amplification — two sources of yield are imported and their combined heft is stacked.**  
4. **Tokenized staked phUSD is a fully realised thriftcoin** with some of the best yields in DeFi.  

---

## Categories of Stablecoins

So far, three categories dominate the market:

- **Fiat-backed (custodial):** USDT, USDC — backed by off-chain reserves.  
- **Crypto-collateralized (on-chain):** DAI, LUSD — backed by user-deposited collateral and liquidations.  
- **Algorithmic (reflexive):** TerraUSD (UST), IRON Finance — stabilized by arbitrage incentives, but can collapse under stress. The larger algorithmic stables grow, the more vulnerable they become — their size makes them prime attack targets and magnifies confidence shocks.  

Each design comes with tradeoffs. Custodial stables are centralized. On-chain collateralized stables are capital-inefficient and prone to liquidation spirals. Algorithmic stables grow explosively but unravel when incentives break.

It’s time to introduce a new category: **the Evergreen Stablecoin.**

---

## What Makes a Stablecoin Evergreen?

An **Evergreen Stablecoin (EGS)** is a stablecoin pegged to $1 whose backing doesn’t just hold steady — it grows stronger over time through protocol-owned yield.

**Key traits:**

- **Peg + Expanding Backing:** phUSD holds at $1 while Phoenix’s yield base compounds.  
- **Protocol-Owned Liquidity:** No mercenary LPs. Liquidity belongs to the protocol permanently.  
- **Stabilization + Permanent Base:** Arbitrage maintains the peg, while yielding assets provide a growing foundation.  

In short: phUSD stays pegged while its roots deepen with time.   

---

## The Stablecoin Trilemma

Every stablecoin design wrestles with three competing goals:

1. **Decentralization** – no reliance on banks or off-chain custodians.  
2. **Capital Efficiency** – minting doesn’t require oversized collateral.  
3. **Stability** – the peg holds even under stress.  

So far, no category has solved all three:

| Model                                | Decentralized | Capital-Efficient | Stable Peg | What’s sacrificed |
|--------------------------------------|:-------------:|:-----------------:|:----------:|-------------------|
| **Fiat-backed (USDC/USDT)**          | ⚠️            | ✅                | ✅         | Decentralization  |
| **On-chain collateralized (DAI/LUSD)**| ✅            | ⚠️                | ✅         | Efficiency        |
| **Algorithmic (UST / IRON)**         | ✅            | ✅                | ⚠️         | Stability — *and the larger they grow, the more fragile they become, as size amplifies attack incentives and confidence shocks.* |

**phUSD is the first design that aims to escape this trilemma:**

- **Decentralized:** All assets live on-chain, with protocol-owned liquidity instead of rented LPs.  
- **Capital Efficient:** phUSD always mints at $1, no overcollateralized CDPs or liquidation ladders required. When staked, it stacks multiple yield streams while distributing risk — producing some of the strongest yields in DeFi.  
- **Stable:** Arbitrage keeps price near $1, while protocol-owned yield compounds in the background, creating an ever-growing cushion of support.  

---

## How Evergreen Stabilization Works

- **Mint at $1:** Users can always mint phUSD for $1.  
- **Permanent, Protocol-owned Asset Base:** Minted assets are split between:  
  - phUSD liquidity on Uniswap V2 (**TVL_LP**). This is the _backing_ of the token, the liquidity in an appreciating stablecoin token such as sUSDe.
  - Phoenix’s yield vault farming external DeFi strategies (**TVL_V**). Yield from this vault market buys phUSD, continually pushing up the price. 

Yield from both these sources pushes phUSD’s price above $1 but in different ways. **TVL_LP** raises the price by appreciating and **TVL_V** raises the price by directing yield into market buying phUSD from the LP.

That triggers an **arbitrage loop:**

- Arbitrageurs mint phUSD at $1 using Dola.  
- They sell into the premium in the LP in which the price is higher than $1.
- Dola from minting is staked directly in the yield vault rather than going to the LP.
- Yield from the vault grows and flows directly into strengthening the phUSD Uniswap Liquidity Pool.
- This expands the TVL in both the Uniswap Liquidity Pool and the Phoenix Yield Vault, increasing phUSD backing while pulling price back to $1.  

This is the **Evergreen loop:** yield creates premiums → arbitrage expands supply → backing compounds.   

**TVL_LP** is the liquid backing of phUSD. It’s an LP token which determines the price/liquidity of phUSD.  

**TVL_V** is a constant source of price growth. It’s like an invisible army of buyers — a perpetual bull market that gets more bullish the more the external market gets bearish.  

Phoenix innovates by allowing the APY of **TVL_V** and **TVL_LP** to be **additive.** This is **yield stacking.** It hypercharges the yield offering, ensuring Phoenix offers some of the best yield in DeFi.  

<img width="400" height="400" alt="phUSD infographic" src="https://github.com/user-attachments/assets/9b273834-fa4c-498b-a886-9da57de11aec" />


---

## Why Evergreen Matters

- **Sustainability:** Yield is owned by the protocol, not rented liquidity.  
- **Security:** Backing comes from two independent bases — vault + LP — both would need to fail simultaneously for collapse.  
- **Antifragility:** Volatility strengthens phUSD. Each mint cycle grows yield and deepens backing.  
- **Inevitability:** The longer phUSD operates, the harder it becomes to destabilize.  

Phoenix’s phUSD isn’t just another stablecoin. It’s the first of a new category — one where the peg is reinforced by compounding yield, not fragile promises or custodial trust.  

Unlike other models, phUSD doesn’t weaken with age. **It gets stronger.**  

**Evergreen Stablecoins are stability that grows.**


<img width="512" height="754" alt="Evergreeninfographic" src="https://github.com/user-attachments/assets/34564c4b-958d-4c3e-97e5-5879ccb7273e" />

