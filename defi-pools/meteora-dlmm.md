---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# Meteora DLMM

Meteora is the leading liquidity protocol on Solana for dynamic, concentrated liquidity pools.

Its DLMM (Dynamic Liquidity Market Maker) architecture is particularly well-suited for memecoin trading, new token launches, and high-volatility pairs where volume spikes are common and fee opportunities are significant.

## How DLMM works: bins

Unlike traditional AMMs that spread liquidity across an infinite price curve, Meteora DLMM organizes liquidity into **discrete price bins**.

Each bin represents a specific price point. Liquidity in a bin is only active — and therefore earning fees — when the market price is inside that bin.

Key concepts:

* **Active bin** — The bin where the current market price sits. Only this bin earns fees at any given moment.
* **Bin step** — The price width between bins, expressed in basis points (1 bps = 0.01%). A bin step of 25 means each bin represents a 0.25% price move. Lower bin steps = finer price granularity.
* **Bin range** — The set of bins an LP deposits into. Wider ranges mean the position stays in range longer; narrower ranges earn more fees when price stays within them.

When a trade executes, it moves across bins from the current price toward the trade's target price. Every bin the trade crosses earns fees for the LPs positioned in that bin.

## Fee structure

Meteora DLMM uses a **dynamic fee** model.

The base fee is set at pool creation. On top of this, Meteora applies a **volatility surge multiplier**: when price moves sharply and rapidly, the dynamic fee increases automatically. This means LPs earn higher fees during the volatile periods that are most risky for their positions — partially offsetting impermanent loss.

Typical fee ranges:

| Pool Type | Base Fee |
|---|---|
| Stablecoin pairs | 0.01% – 0.05% |
| Major pairs (SOL/USDC) | 0.2% – 0.5% |
| Memecoins, new launches | 0.5% – 2%+ |

Protocol fee: Meteora takes approximately 5% of the dynamic fee generated. The remainder goes to LPs.

## Liquidity strategies

When creating or adding to a Meteora DLMM position, three distribution strategies are available:

### Spot
Liquidity is spread uniformly across the selected bin range. Suitable for pairs where price is expected to move within a defined corridor. Simple to manage. Lower peak fee efficiency than Curve.

### Curve
Liquidity is concentrated near the current price using a bell-curve distribution. More capital sits in bins closest to the active bin, maximizing fee capture when price stays stable. Efficient but more sensitive to price movement.

### Bid-Ask
Liquidity is split on either side of the active bin with less in the center. This mimics a market-maker approach — quoting both sides. Useful for range-bound markets or for collecting fees during oscillating price action.

## Creating a pool on Meteora

Anyone can create a DLMM pool on Meteora permissionlessly.

What is required:

* Two SPL token mint addresses (e.g., a new memecoin + USDC or SOL).
* Initial liquidity for both sides.
* Selection of bin step (price granularity).
* Selection of base fee percentage.
* A Solana wallet with SOL to cover network fees.

Once created, the pool is live. Other LPs can add liquidity. Traders can swap through it immediately.

## Alpha Vault

Meteora's **Alpha Vault** is a mechanism designed for new token launches.

It allows users to deposit USDC ahead of a pool going live. Deposits are queued and enter the pool at the opening price, preventing front-running bots from capturing all early liquidity.

Alpha Vault is used by projects that want a fair, bot-resistant launch. LPs using Alpha Vault are positioned before public trading begins.

## Memecoin pools on Meteora

Meteora has become a primary destination for post-launch memecoin liquidity on Solana.

When a token on pump.fun reaches its bonding curve threshold (approximately $69,000 market cap), a portion of that capital is used to seed a liquidity pool — frequently on Meteora.

These new pools often see:

* **Extremely high volume-to-TVL ratios** in the first hours after launch.
* Fee APRs that can exceed 1,000% annually on a 24-hour basis during peak activity.
* Sharp price moves that can cause significant impermanent loss if the price does not return to the entry range.

The opportunity: high fees. The risk: high impermanent loss and potential rapid price collapse.

## Key metrics to monitor

When evaluating a Meteora pool:

| Metric | What It Tells You |
|---|---|
| **TVL** | Total capital in the pool |
| **24h Volume** | Trading activity in the last 24 hours |
| **Fee / TVL ratio** | How much fee is generated per dollar of liquidity |
| **24h Fees** | Total fees distributed to LPs in the past day |
| **APR / APY** | Annualized return estimate based on recent fees |
| **Active bin** | Whether current price is within your position range |
| **Bin step** | Price precision of the pool |

A high fee/TVL ratio indicates the pool is actively used relative to its size. This is the primary efficiency metric for DLMM positions.

## Risks specific to DLMM

* **Out-of-range risk** — If price moves outside your bin range, your position earns zero fees until price returns.
* **One-sided exposure** — When price exits your range on one side, your position converts entirely to the depreciated asset.
* **Narrow range amplification** — Concentrated positions earn more when in range but suffer more IL when price moves.
* **New token risk** — Memecoin pools created at launch may rug, lose all volume, or collapse within hours.

---

*Capital at risk. DLMM liquidity positions carry impermanent loss and out-of-range risk. Not financial advice. Official bot: [@LiquidX\_official\_bot](https://t.me/LiquidX_official_bot)*
