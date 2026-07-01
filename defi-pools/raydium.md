---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# Raydium

Raydium is one of Solana's largest and most established DeFi protocols.

It powers a significant share of Solana's on-chain liquidity, particularly for newly launched tokens. Raydium offers both a standard constant-product AMM and a concentrated liquidity product, making it accessible to a wide range of LPs.

## Products

### Standard AMM (CPMM)
The original Raydium pool model. Uses the constant-product formula x × y = k, distributing liquidity across all prices simultaneously. No range selection required. Simpler to use and does not go out of range. Less capital efficient than concentrated liquidity, but easier to manage passively.

### CLMM (Concentrated Liquidity)
Raydium's concentrated liquidity product. Similar in mechanics to Orca Whirlpools. LPs select a price range, capital is concentrated within that range, and fees are earned only when market price is active in the range. Higher efficiency; higher management complexity.

### PumpSwap
Raydium's dedicated swap interface for pump.fun-originated tokens. When a memecoin on pump.fun completes its bonding curve (approximately $69,000 market cap), a pool is automatically created — often on Raydium or Meteora. PumpSwap is optimized for the high-volume, short-lifecycle nature of these tokens.

### LaunchLab
A token launch platform built on Raydium. Projects can use LaunchLab to initialize a token, create an initial pool, and distribute to early buyers in a structured way. Designed to reduce bot front-running and improve fair launch mechanics.

## Fee structure

**Standard AMM (CPMM) fees:**

| Recipient | Percentage |
|---|---|
| Liquidity Providers | 0.25% per trade |
| Raydium Protocol | 0.03% per trade |
| RAY token buyback | 0.02% per trade |

Total swap fee for standard pools: 0.30%

**CLMM fees:**

Fee tier is selected at pool creation. Options typically range from 0.01% to 1%. Allocation between LPs and protocol follows a similar structure to standard AMM, with the majority going to LPs.

**Pool creation fees:**
Creating a Standard AMM pool costs 0.15 SOL to prevent spam. CLMM pool creation has no additional protocol fee beyond Solana network costs.

## Pool types summary

| Product | Mechanic | Management | Best For |
|---|---|---|---|
| Standard AMM | x×y=k, full range | Passive | Simple LP, established pairs |
| CLMM | Tick-based range | Active | Efficient LP, concentrated capital |
| PumpSwap | Auto-created, memecoin | Varies | Post-pump.fun launch pools |
| LaunchLab | Structured launch | Project-managed | New token listings |

## Memecoin flow on Raydium

Raydium receives significant memecoin volume through the pump.fun migration pipeline.

When a pump.fun token hits the bonding curve threshold:

1. A liquidity pool is seeded with a portion of the bonding curve funds.
2. The pool goes live on Raydium or Meteora (routing depends on current pump.fun configuration).
3. Public trading begins immediately.
4. Volume in the first 15–60 minutes can be 5x to 50x the initial pool TVL.

LPs who provide additional liquidity to these pools immediately after launch can earn significant fees — but face severe impermanent loss risk if the token price collapses rapidly after the initial pump.

## Key metrics

When evaluating a Raydium pool, the standard metrics apply:

| Metric | Meaning |
|---|---|
| **TVL** | Total value locked in the pool |
| **24h Volume** | Swap volume in the last 24 hours |
| **24h Fees** | Fees distributed to LPs in the past day |
| **APR** | Annualized estimate based on recent 24h activity |
| **Fee Tier** | Percentage of each trade taken as fee |

The Raydium API (api-v3.raydium.io) provides live data for all pools including TVL, volume, fees, and APR. This data can be queried programmatically or viewed through the Raydium app interface.

## Risks

* **Impermanent loss** — Standard AMM and CLMM both expose LPs to IL. CLMM carries higher IL risk within narrow ranges.
* **Rug pull risk** — Newly listed memecoins can be abandoned, causing total capital loss for LPs.
* **Smart contract risk** — Although Raydium is audited and has operated for years, smart contract vulnerabilities remain a theoretical risk.
* **Low volume periods** — Fee income drops to near zero if a pool loses trading activity. Capital remains locked in the pool until withdrawn.
* **Protocol risk** — Protocol-level incidents (exploits, governance failures) can affect all pools.

---

*Capital at risk. Performance variable. Not financial advice. Official bot: [@LiquidX\_official\_bot](https://t.me/LiquidX_official_bot)*
