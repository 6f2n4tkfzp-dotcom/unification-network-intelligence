# Data sources and measurement method

## FUND primary controls

- [Unification blocks](https://explorer.unification.io/u/block): visual confirmation of height, timestamp and Transactions per block.
- [Unification transactions](https://explorer.unification.io/u/tx): inspection of messages, fees and transaction detail.
- Official Unification RPC/REST (and gRPC where supported): raw machine-readable verification.
- A documented alternative provider such as Chainmasters: independent cross-check when responsive.

**Hard freshness gate:** Accept a chain measurement only if its latest block timestamp is current at the measurement time. An endpoint that responds successfully but reports an old chain tip is **STALE**, not LIVE. Record observed time, source, height and timestamp.

## Daily block accounting (UTC)

1. Choose the first complete block strictly after 00:00:00 UTC.
2. Choose the last complete block strictly before the following 00:00:00 UTC.
3. Sum the actual `Transactions` count of **every** block in the inclusive height range.
4. Spot-check sampled blocks and individual transactions against transaction detail or raw RPC/REST data.
5. Publish start/end block, block count, transaction count, tx/block and tx per 4.8 minutes.

Use the same treatment of boundary seconds across all days. Never substitute a theoretical throughput estimate for measured transactions.

## Formulas

- `block_count = end_height - start_height + 1` when the range is contiguous and fully verified.
- `tx_per_block = total_transactions / block_count`.
- `tx_per_4_8_min = total_transactions * 4.8 / duration_minutes`.
- `weekly_total = sum(verified_daily_totals)`.
- `daily_average = weekly_total / number_of_complete_verified_days`.

The historical **25 tx per 4.8 minutes** value is a benchmark only.

## Fees and FUND usage

Read each real on-chain fee in **nund**. Convert using `1 FUND = 1,000,000,000 nund` where the native denomination is confirmed. Do **not** assume each transaction costs 1 FUND. Distinguish transaction fees paid, fee distribution and provable burned/consumed supply: these are not interchangeable concepts.

## Comparison baselines

Weekly comparisons use the previous fully verified week and a separately labelled Day 0 baseline of **2026-09-11**. Never backfill unverified values with estimates or carry-forward values disguised as new observations.
