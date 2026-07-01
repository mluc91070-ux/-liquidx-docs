---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# Orca Whirlpools

Orca is one of the longest-running and most trusted DEXes on Solana.

Its **Whirlpools** product is a concentrated liquidity AMM (CLMM) that allows LPs to deploy capital within custom price ranges, earning fees only when the market price is within their chosen range.

Orca Whirlpools are particularly strong for established pairs: SOL/USDC, BTC/USDC, ETH/USDC, and stablecoin pairs. They are also used for mid-cap tokens with consistent volume.

## How Whirlpools work

Whirlpools use a **tick-based** architecture.

Price is divided into discrete ticks. An LP selects a lower tick and an upper tick, defining the range where their capital is active. All liquidity within those ticks earns fees proportionally whenever a trade passes through that price range.

This is similar in concept to Meteora DLMM bins, but with a continuous curve mechanic inside each tick range rather than discrete equal-price bins.

Key concepts:

* **Tick** — A discrete price point. The tick spacing determines how granular price ranges can be.
* **Tick spacing** — Linked to the fee tier. Lower fee tiers have tighter tick spacing (more precise ranges possible).
* **Position** — An NFT representing your LP deposit, lower tick, and upper tick. Your position is unique and transferable.
* **In-range** — Your capital earns fees when market price is between your lower and upper ticks.
* **Out-of-range** — Your capital earns no fees and sits entirely in one asset.

## Fee tiers

Orca Whirlpools offer several fee tier options at pool creation:

| Fee Tier | Best For |
|---|---|
| 0.01% | Stablecoin pairs (USDC/USDT) |
| 0.05% | Pegged assets, tight-spread pairs |
| 0.3% | Standard token pairs (SOL/USDC) |
| 1% | Volatile or lower-liquidity tokens |
| 2% | High-risk, speculative pairs |

The fee tier is fixed at pool creation. A higher fee tier earns more per trade but may attract less volume if cheaper alternatives exist.

## Fixed vs adaptive fees

Orca supports two fee models depending on pool configuration:

**Fixed fees** — Standard model. The fee percentage is constant regardless of market conditions. Predictable for LPs.

**Adaptive fees** — A dynamic model where the fee percentage adjusts based on volatility. Higher volatility triggers higher fees, compensating LPs for increased impermanent loss risk during sharp price moves. This is similar in intent to Meteora's dynamic fee surge.

## Price range selection

The price range an LP selects directly determines their risk and return profile.

**Full range**: Depositing across the entire possible price range. This behaves like a traditional constant-product AMM (no concentration). Maximum range coverage, minimum efficiency, low IL risk. Suitable for LPs who want exposure without active management.

**Concentrated range**: Depositing across a narrow range near the current price. Maximum fee efficiency per dollar deployed. High IL risk if price exits the range. Requires monitoring and re-positioning as price moves.

**Wide but not full**: A practical middle ground. Covers a realistic expected price corridor (e.g., ±30% from current price). Captures most activity without requiring constant management.

## Rewards (Aquafarms)

In addition to base swap fees, certain Orca Whirlpools offer additional token rewards through **Aquafarms**.

Protocols that want to incentivize liquidity in their Orca pool can deposit reward tokens. LPs in qualifying pools earn these rewards on top of standard fees.

This can meaningfully boost the effective APR of a position — but reward streams are temporary and depend on each protocol's ongoing emissions program.

## Creating an Orca Whirlpool

Creating a new Whirlpool requires:

* Two SPL token mint addresses.
* Selection of a fee tier.
* Initial liquidity for both assets.
* A Solana wallet with SOL for network fees.

Pool creation is permissionless. Any token pair can have an Orca Whirlpool.

Once a pool is initialized with the correct tick spacing and fee tier, it becomes available for LPs to deposit and for traders to route swaps through aggregators like Jupiter.

## Monitoring a Whirlpool position

Active Whirlpool LPs track:

| Metric | Purpose |
|---|---|
| **Current price vs range** | Is your position in range and earning fees? |
| **Fees earned** | Accumulated fees claimable at any time |
| **TVL** | Total liquidity in the pool |
| **24h volume** | Recent trading activity |
| **Fee APR** | Annualized estimate based on 24h fees |
| **Additional APR** | Aquafarm token rewards, if applicable |

## Key risks

* **Out-of-range positions earn nothing** — If price moves outside your range, fee accumulation stops entirely.
* **Re-positioning costs** — Moving a position requires closing it (collecting fees, receiving assets) and opening a new one. Network fees apply but are low on Solana.
* **Concentrated IL** — Narrow ranges amplify impermanent loss when price moves.
* **Token reward risk** — Aquafarm rewards may be discontinued, delayed, or the reward token may decline in value.

---

*Capital at risk. Concentrated liquidity positions carry impermanent loss and management risk. Not financial advice. Official bot: [@LiquidX\_official\_bot](https://t.me/LiquidX_official_bot)*
