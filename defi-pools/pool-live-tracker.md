---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# Live Pool Data

LiquidX monitors on-chain pool data in real time to evaluate liquidity deployment opportunities.

This page explains the key metrics used to assess a pool's activity and profitability — and how to read them.

## Core pool metrics

### TVL (Total Value Locked)

The total USD value of assets deposited in a pool by all LPs combined.

TVL indicates the depth of available liquidity. A low TVL pool is easier to move with large trades, which can increase IL for existing LPs. A high TVL pool is more stable but may offer lower fee yields per dollar deployed.

### 24h Volume

The total USD value of swaps through the pool in the past 24 hours.

Volume is the primary driver of fee income. Without volume, LPs earn nothing. High volume relative to TVL (high volume-to-TVL ratio) is the efficiency signal.

### 24h Fees

The total fees distributed to LPs over the past 24 hours.

Fees = Volume × Fee Tier

A pool with $1,000,000 volume and a 0.3% fee generates $3,000 in daily fees. LPs share those fees proportionally to their share of the pool.

### Fee / TVL Ratio (Daily)

The most important efficiency metric.

If a pool has $100,000 TVL and generates $3,000 in 24h fees, the fee/TVL ratio is 3% per day — approximately 1,095% annualized.

This ratio identifies which pools are generating the most fee income per dollar of capital deployed.

### APR / APY

Annualized return estimate based on recent fee data.

APR = (24h Fees / TVL) × 365 × 100

This figure changes daily as volume and TVL shift. A high APR today may collapse to near zero tomorrow if volume drops. It is a snapshot, not a forecast.

### Fee Tier

The percentage of each swap charged as a fee, split between LPs and the protocol.

Higher fee tiers earn more per trade but may deter volume if cheaper pools exist for the same pair. The optimal fee tier depends on the pair's volatility and competitive landscape.

## Volume-to-TVL ratio

This ratio is the clearest signal of a pool's efficiency.

| Volume/TVL | Interpretation |
|---|---|
| Below 0.1x | Low activity. Minimal fee income. |
| 0.1x – 0.5x | Moderate activity. Normal fee yield. |
| 0.5x – 2x | Active pool. Good fee generation. |
| 2x – 10x | High activity. Strong fee opportunity. |
| Above 10x | Extreme activity. Typically seen in first hours of a new memecoin launch. |

For stablecoin pairs, a volume/TVL ratio of 0.5x at a 0.01% fee tier may still generate competitive yields. For memecoin pools, ratios above 5x at 1% fee tiers can generate extraordinary short-term fee income.

## How to read a pool in real time

When evaluating a pool for capital deployment, the following sequence applies:

**Step 1 — Check current volume trajectory.** Is volume rising or declining over the past hour? A pool with $500,000 volume in hour one and $50,000 in hour three is losing momentum. A pool with rising hourly volume is in an active phase.

**Step 2 — Calculate projected daily fee income for your position.** Estimate your share of the pool's TVL after your deposit. Multiply that share by the 24h fee total. This is your projected daily fee income — before IL.

**Step 3 — Estimate IL exposure.** How volatile is the pair? Has price moved significantly since pool creation? If you are entering a pool after a 5x pump, the IL from the pump is already locked in for earlier LPs. What additional IL risk exists from here?

**Step 4 — Define an exit threshold.** Before entering, decide at what point you exit. Common approaches: exit if volume drops below a defined threshold per hour, or exit after a fixed time window regardless of performance.

## Data sources

Pool data for Solana protocols is available through:

* **DexScreener** — Aggregated pair data for Raydium, Orca, Meteora, and all major Solana DEXes. Shows volume, price, liquidity, and fee estimates for any token pair.
* **Raydium API** — Official API (api-v3.raydium.io) providing pool TVL, 24h volume, 24h fees, APR, and fee tier for all Raydium pools.
* **Meteora** — Pool data accessible through the Meteora app (app.meteora.ag) and its data API layer.
* **Orca** — Pool performance metrics via the Orca app (orca.so) and the Orca Whirlpool SDK.
* **DefiLlama** — Protocol-level TVL, volume, and fee aggregation across all protocols.

LiquidX may integrate live pool data directly into its operational monitoring to inform capital allocation decisions.

---

*Capital at risk. Pool APR figures are based on recent historical data and are not predictive of future performance. Not financial advice. Official bot: [@LiquidX\_official\_bot](https://t.me/LiquidX_official_bot)*
