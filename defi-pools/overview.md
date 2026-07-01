---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# On-Chain DeFi Pools — Overview

Solana hosts some of the most active decentralized liquidity pools in crypto.

LiquidX monitors and may allocate capital into on-chain pools where liquidity demand is real, fees are measurable, and volume is live. This section explains how those pools work, what protocols power them, and why they matter for liquidity operations.

## What is an on-chain liquidity pool?

A liquidity pool is a smart contract holding two assets.

When a trader wants to swap Token A for Token B, they use the pool instead of a traditional order book. The pool provides liquidity. In return, liquidity providers (LPs) who deposited assets into the pool earn a share of every trade fee.

The core logic:

* A user deposits two assets into a pool in a set ratio.
* Traders swap through that pool.
* Every swap generates a fee.
* Fees accumulate inside the pool.
* The LP earns a proportional share of those fees.

The size of the fee, the amount of trading volume, and the LP's share of the pool determine how much they earn.

## Why Solana?

Solana's architecture enables:

* **Sub-second finality** — trades settle in under 400 milliseconds.
* **Ultra-low fees** — transaction costs under $0.001.
* **High throughput** — capable of tens of thousands of transactions per second.
* **Deep DeFi infrastructure** — Orca, Meteora, Raydium, and Jupiter have processed billions in volume.

These properties make Solana suitable for active liquidity operations, including volatile memecoin markets where speed and cost matter.

## The three main protocols

| Protocol | Type | Best For |
|---|---|---|
| **Meteora DLMM** | Discrete Liquidity Market Maker | Memecoins, volatile pairs, new launches |
| **Orca Whirlpools** | Concentrated Liquidity (CLMM) | Major pairs, stablecoins, established tokens |
| **Raydium** | Standard AMM + CLMM + LaunchLab | All-purpose, token launches, pump.fun migrations |

Each protocol uses a different mechanism to concentrate or distribute liquidity across price ranges. The choice of protocol, fee tier, and strategy determines how much a liquidity provider earns — and how much risk they take.

## How fees are generated

Every swap through a pool charges a fee, typically expressed as a percentage of the trade size.

Examples:

* A pool with a 1% fee earns $1,000 in fees for every $100,000 in volume.
* A pool with a 0.3% fee earns $300 for every $100,000 in volume.
* A pool with $500,000 TVL and $1,000,000 daily volume at 0.3% generates $3,000 in daily fees.
* If your deposit represents 5% of that pool's TVL, your daily fee share is $150.

Fee income scales with volume. In high-traffic memecoin pools, daily volume can exceed the pool's TVL by 5x to 20x, producing very high short-term fee yields.

## The key risk: impermanent loss

Liquidity provision is not the same as holding.

When the price of one asset in the pool moves significantly relative to the other, the LP's position becomes worth less than if they had simply held the two assets separately. This difference is called **impermanent loss (IL)**.

IL is most severe:

* When price moves sharply in one direction.
* When liquidity is concentrated in a narrow range (more efficient, but higher IL exposure).
* When a memecoin pumps 10x or dumps 90%.

Fee income may partially or fully offset IL in high-volume periods. In low-volume or high-volatility periods, IL can exceed total fees earned.

## How LiquidX may use on-chain pools

LiquidX may allocate capital into on-chain pools as part of its broader liquidity engine.

Possible uses include:

* Providing liquidity in established stablecoin pairs for consistent fee generation.
* Allocating into high-volume memecoin pools during peak activity phases.
* Using dynamic fee tiers to capture elevated fees during volatile market conditions.
* Rotating capital across protocols based on volume metrics, fee-to-TVL ratios, and liquidity demand.

Users do not manage pool positions directly. Capital allocation, strategy selection, range management, and fee collection are handled at the LiquidX level. Users track activity, projected performance, and rewards through the dashboard.

---

*Capital at risk. Performance variable. Impermanent loss is a real risk in all liquidity pool strategies. Not financial advice. Official bot: [@LiquidX\_official\_bot](https://t.me/LiquidX_official_bot)*
