# The Rebound Effect: phUSD Stability in Action

## Introduction
phUSD is designed around a simple principle: **$1 is its anchor price — its centre of gravity.**  
Whenever phUSD trades away from $1 — either above or below — it becomes unstable.  

This instability is not a flaw; it is the feature that drives phUSD back to equilibrium while simultaneously strengthening it.  
**Any deviation is unstable by definition — because the further it goes, the stronger the restoring force gets.**  

We call this reflexive dynamic the **Rebound Effect**.  

<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/591d9e56-5ebb-4638-9b93-2e639366d173" />

---

## Below $1: Elastic Tension

### Mechanics
To understand the rebound below peg, it’s important to distinguish two systems:

- **Liquidity Pool (LP):** Where phUSD trades against a yield-bearing token. This sets the market price.  
- **Yield Vault:** Holds the yield-bearing token. Its size is fixed in token terms and does not shrink when LP price changes.  

When phUSD trades below $1:  
- The LP base shrinks as the pricing token falls.  
- The Yield Vault, however, stays constant, so its yield represents a *larger share* relative to the LP base.  
- APY stretches like an **elastic band** — the further phUSD falls, the tighter the pull.  

### A Simple Numeric Example
To see why the rebound grows stronger as phUSD falls below $1, consider this example:  

**Step 1. Baseline**  
- LP base = 100  
- Vault yield = 10  
- APY = 10 ÷ 100 = **10%**  

**Step 2. LP base shrinks 20%**  
- New LP base = 80  
- Vault yield still = 10 (unchanged)  
- APY = 10 ÷ 80 = **12.5%**  

**Step 3. Compare**  
- Original APY = 10%  
- New APY = 12.5%  

**Step 4. Relative increase**  
- APY has risen by (12.5 − 10) ÷ 10 = **25%**  

> **Effect:** A 20% drop in liquidity base leads to a 25% increase in APY.  
> This is the elastic rebound: the deeper the drop, the stronger the pull back to $1.  

### Elastic Rebound Sensitivity
The relationship between LP shrinkage and APY increase is nonlinear —  
the deeper the drop, the stronger the rebound force.  

| LP base drop (%) | New APY increase (%) |
|------------------|-----------------------|
| 10%              | +11.1%               |
| 20%              | +25%                 |
| 30%              | +42.9%               |
| 40%              | +66.7%               |
| 50%              | +100%                |

This accelerating force is what makes phUSD *antifragile* below $1.  

<img width="1242" height="947" alt="Image" src="https://github.com/user-attachments/assets/94f6fd42-cb81-4dce-9bdc-d1d6e5669822" />

This incentivises a rush of buying.  

As price rebounds toward $1, the “elastic band” slackens — APY incentives normalise.  
But because the LP counter-token is itself a yield-bearing thriftcoin (e.g. sUSDe), the slack is absorbed as continuous yield growth in that asset. This means system strength compounds even as phUSD stability is restored.  

---

## Above $1: Profit Pressure Release
As phUSD rises above peg (due to the yielding token in the LP pair and buy pressure from the Yield Vault), profit pressure builds:

Arbitrageurs step in:  
1. Mint new phUSD directly at $1.  
2. Sell this phUSD into the LP where it trades above $1.  
3. Pocket the difference as profit.  
4. The selling pressure restores the price back toward $1.  

Meanwhile:  
- The Yield Vault expands as newly minted phUSD increases Yield Vault backing.  
- This permanently grows the protocol’s strength.  

> **Effect:** Above peg, phUSD fuels growth of the Yield Vault backing, strengthening the system for the next cycle.  

---

## The Stabilizer: Uniswap Fees
Uniswap fees in the liquidity pool provide another stabilizing force:  

- As phUSD oscillates around $1, the back-and-forth rebounds create trading volume in the LP.  
- Each trade pays Uniswap fees.  
- Those fees are reinvested into the pool, growing its depth.  

This phenomenon is well documented in stablecoin pools: **volatility around the peg accelerates liquidity growth.**  
The more the system rebounds, the faster liquidity compounds.  

- Bigger liquidity = stronger support for sell volume in the future.  
- Over time, deviations from the $1 peg reduce until phUSD becomes a highly liquid, highly stable dollar anchor.  

> **Effect:** Uniswap fees mean phUSD is *antifragile* — stress strengthens the system and accelerates recovery.  

---

## Long-Term Dynamics
1. **Early phase:** Lower liquidity means larger deviations and sharper, more elastic rebounds.  
   This is highly profitable for both:  
   - **Traders:** who capture arbitrage opportunities.  
   - **Liquidity providers:** who earn big fees from high volume, with zero impermanent loss (stable-to-stable pair).  

2. **Growth phase:** Uniswap fees deepen liquidity → dampened volatility.  

3. **Mature phase:** phUSD distribution has widened, rebounds have dampened, and price stabilises tightly at $1.  
   At this stage, growth shifts gears:  
   - As the Yield Vault grows and liquidity deepens, volatility contributes less to the cycle.  
   - New yield now converts almost 1:1 into new phUSD supply.  
   - Example: $100 of yield output = ~100 new phUSD minted.  

   The result is accelerating total supply growth.  

<img width="1248" height="832" alt="Image" src="https://github.com/user-attachments/assets/4f29f4ac-2c69-4df3-bdc6-9c9887fbae0b" />

---

## Conclusion
phUSD doesn’t rely on over-collateralisation that risks liquidations, nor on centralised banks vulnerable to intervention or collapse. Unlike algorithmic stablecoins, it cannot spiral to zero.  

Instead, phUSD stabilises itself with a simple, powerful feedback loop:  

- **Below $1:** Elastic rebound → stronger APY snap-back.  
- **Above $1:** Pressure release → Yield Vault expansion and stronger collateral backing.  
- **Over time:** Liquidity deepens, distribution widens, and stability strengthens.  

> **This is the Rebound Effect — Evergreen stability. phUSD is not just stable; it grows stronger with every cycle.**
