---
cover: ../.gitbook/assets/gitbook-cover.png
coverY: 0
---

# OTC Volume Operations

OTC means over-the-counter.

An OTC transaction happens directly between parties instead of through a public exchange order book.

## Why OTC exists

Large-volume transactions can be difficult to execute on public order books without moving the market.

OTC desks may help buyers and sellers access size, negotiate execution, settle directly, and reduce visible market impact.

OTC demand can come from:

* Large crypto holders.
* Funds and trading desks.
* Exchanges and brokers.
* Market makers.
* Stablecoin operators.
* Businesses moving large balances.
* Participants needing specific settlement terms.

## Where liquidity is needed

An OTC desk needs liquidity to execute large transactions.

That liquidity may support:

* Buy-side demand.
* Sell-side demand.
* Short-term settlement needs.
* Stablecoin movement.
* Cross-venue balancing.
* Quote fulfillment.
* Market depth support.

## How LiquidX may participate

LiquidX may allocate capital into selected OTC-related liquidity flow when internal rules, risk controls, counterparties, and market conditions allow.

If liquidity is used to support eligible OTC activity, performance may come from fees, spreads, or other compensation linked to liquidity demand.

This is conditional. LiquidX should not be understood as guaranteeing access to every OTC opportunity or guaranteeing that OTC activity will always generate profit.

## RFQ process (Request for Quote)

OTC transactions at LiquidX follow a structured RFQ protocol:

1. **Quote Request** — The client specifies the asset pair (e.g. BTC/USDT), desired volume, and direction (buy or sell).
2. **Price Provision** — The LiquidX Desk analyzes market conditions and provides a firm bid or ask price with a defined validity period.
3. **Price Acceptance** — The client has a limited window (typically 30 to 120 seconds) to accept the price. Once the window expires, a new quote must be requested.
4. **DVP Settlement** — Upon acceptance, delivery of the digital asset and payment occur simultaneously (Delivery vs. Payment), eliminating counterparty settlement risk.
5. **Confirmation** — A written confirmation is issued summarizing the pair, volume, executed price, fees, timestamp, and unique transaction identifier.

Minimum transaction volume is set at the equivalent of **USD 25,000**. LiquidX reserves the right to adjust this threshold at any time.

## Fee structure

Transaction fees are embedded in the spread (the difference between bid and ask price) communicated at the time of the RFQ quote.

* No hidden fees are applied.
* The effective commission is stated in the transaction confirmation.
* Settlement is made in AED, USD, or USDC/USDT depending on the pair traded.
* Settlement times: instant for stablecoins, T+0 to T+1 for bank transfers in AED/USD.
* Gas and blockchain network fees are borne by the client unless explicitly agreed otherwise.

## OTC risks

OTC activity may involve:

* Counterparty risk.
* Settlement risk.
* Pricing risk.
* Execution risk.
* Dispute risk.
* Compliance risk.
* Timing risk.
* Liquidity mismatch.
* Operational failure.

Large private transactions can be complex. Even when demand exists, execution can fail or produce lower-than-expected results.

---

> **Risk notice:** LiquidX does not guarantee returns. Performance is variable. Capital is at risk. Dashboard projections and monthly targets are illustrative, not promises. Nothing in this documentation is financial advice. Use only the official LiquidX bot: **@LiquidXBot**.
