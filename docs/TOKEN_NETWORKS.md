# FUND, eFUND and xFUND

## Native FUND

The native token on the Unification MainNet. Dashboard areas include network transactions, fees, supply, validators, delegation and holder distribution.

## ERC-20 FUND representations

Representations of FUND on Ethereum or other networks must be tracked by their own chain, contract, holder count and transfer activity. They are not automatically additional economic supply on top of native FUND.

## eFUND

Track enterprise/utility accounting only where the source and units are verified. Distinguish locked allocations, spent amounts, actual transaction fees and inferred consumption. Missing enterprise attribution must remain unlabelled; never fabricate organization names.

## xFUND

Track independently for each supported network (e.g. Ethereum, Shibarium, Polygon only where verified): token contract, indexed supply, holders, transfers, concentration and liquidity. Verify whether a network deployment represents bridged tokens before aggregating supply. Do not sum contract supplies across networks without accounting for bridges and locking.

Oracle/OOO usage, integration activity, staking and utility require independently verifiable events or official evidence. Price, market capitalization, volume and liquidity must include source, quote currency and observation time. An `Indexed` badge does not imply every metric has complete coverage.

## No fabricated metrics

If a network is known but not indexed, show `NOT INDEXED`. If a provider fails, show `SOURCE UNAVAILABLE`. If the last valid observation is old, show `STALE`. Only show zero after a complete measurement that actually found zero.
