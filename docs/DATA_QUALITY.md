# Data quality and status definitions

| Status | Meaning |
| --- | --- |
| `LIVE` | The specific metric or dataset passed freshness and validation checks |
| `COMPLETE` | Defined historical scan scope completed and reconciled |
| `PARTIAL` | Known incomplete coverage; show fraction and missing scope |
| `STALE` | Last timestamp fails the configured freshness rule |
| `SOURCE UNAVAILABLE` | Required source cannot currently be queried |
| `NOT INDEXED` | Source exists, but required scan has not been performed |
| `NO DATA` | No trustworthy measurement is available |
| `0` | Actual validated measurement returned zero |

`COMPLETE` is about historical coverage; `LIVE` is about freshness. They are not interchangeable.

## Validation checks

- Chain tip timestamp freshness and source agreement.
- Correct numeric units, precision and timestamp timezone.
- Monotonic live chain tip; separate reverse-backfill cursor.
- Consistent scan coverage and row totals.
- Healthy standalone feed preferred for its own metrics, with verified diagnostic metadata retained from its authoritative source.
- Atomic persistence and rollback-safe state updates where implemented and tested.
- UI element existence, response schema and runtime error handling.
- Repeat refresh tests to catch inconsistent snapshots.

## No silent fallback

If a new collection attempt fails, preserve the last-known-good result **with its original timestamp and STALE status**; never relabel it LIVE. Maintain provenance per field when data comes from multiple feeds.

## Publication integrity

Public metrics are reproducible summaries, not proof of an independent live audit. Attach source references and observation times to published reports whenever feasible.
