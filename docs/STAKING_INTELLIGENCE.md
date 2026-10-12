# FUND staking intelligence

Staking is a first-class dashboard subsystem, not a single yield number.

## Three complementary views

### 1. On-chain staking transactions

Show timestamp, transaction hash, wallet, validator, amount and message type for:

- `DELEGATE`
- `UNDELEGATE`
- `REDELEGATE`
- `WITHDRAW_REWARD`

Rewards must be decoded from actual transaction events and denominated correctly. Delegation messages and rewards are different kinds of evidence.

### 2. Net staking flow

For a verified interval, report gross delegated, gross undelegated and net bonded-stake change separately. A useful transaction-flow metric is `delegated - undelegated` subject to chain-specific effects and validated message coverage. A snapshot metric is `bonded_end - bonded_start`. These are **not necessarily identical**, and redelegations generally move stake between validators without changing network-wide bonded stake.

A verified `0 FUND/min` net snapshot change can coexist with active staking transactions. When snapshots are missing or stale, display `NO DATA` rather than zero.

### 3. Total staking position

Report verified bonded FUND, staking ratio, active validators, delegator addresses, relationships and concentration. Define the supply denominator used for staking ratio; different supply definitions yield different ratios.

## REStake and compounding

Automatic restaking can increase the principal that earns future rewards. To quantify actual growth, use dated balances, reward records, any deposits/withdrawals and fees. Do not infer that every balance increase is a reward. Separate **gross rewards**, **fees**, **net position growth** and **incremental compounding effect**.

For a user-provided reference position of **242,070.90 FUND**, compute subsequent growth only from user-authorized, timestamped balances. Previously described reward frequency (approximately twice daily, roughly 30 FUND each) is anecdotal and **not a live rate or guaranteed return**.

## Network Activity → Staking Yield Correlation

Compare verified network transactions, bonded stake, validator changes and time-aligned reward observations. Report sample size and limitations. **Correlation does not imply causation.** Do not claim a causal yield effect from transaction growth without evidence.

## Quality requirements

Each metric needs its own source, timestamp, status and coverage. Avoid marking the whole staking module LIVE because one subfeed refreshed successfully.
