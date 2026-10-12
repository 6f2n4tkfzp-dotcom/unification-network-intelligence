# Wallet and holder intelligence

## Separate networks and economic meanings

Report native FUND MainNet addresses, Ethereum ERC-20 FUND addresses and xFUND addresses **separately**. Address counts are not counts of unique people or beneficial owners. Contracts, custodians, bridges and exchange addresses can represent many owners.

Native visible holdings may include liquid FUND plus bonded delegations; make the balance model explicit and avoid counting a delegator's bonded amount twice. Ethereum representations of FUND must **not** be added to native economic supply as newly minted economic FUND without proof.

## Distribution metrics

When full, fresh coverage is verified, publish:

- Holder address count and covered balance.
- Mean, median and trimmed mean (with clearly specified trimming rule).
- Top 10, Top 50 and Top 100 concentration, using the same supply/balance denominator consistently.
- Top 100 address, visible amount, percentage of defined supply and evidence-based classification.
- Week-over-week change, with matching snapshot timestamps and coverage rules.

If a scan is incomplete, show the percentage scanned and label the metrics `PARTIAL` rather than `COMPLETE`.

## Entity labels

Only classify a wallet as a DEX pool, exchange, bridge, validator or enterprise when verified by a public authoritative source or unambiguous on-chain contract metadata. Unverified transfers are **not** automatically buys or sells. A DEX liquidity pool must not be presented as one individual investor.

## Privacy

Publish only chain-public addresses and justified public entity labels. Do not expose internal annotations, user-specific monitoring lists, login data or private API responses.
