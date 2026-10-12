# Release and deployment process

## Separate environments

- **Private operations:** authenticated collector, API, runtime files and diagnostics.
- **Public dashboard:** approved server-side snapshot and static presentation assets.
- **GitHub:** reviewed documentation and, only after approval, sanitized source code.

A public repository must never be used as a backup of the raw production webroot.

## Release gate

1. Identify the real defect using source files, reproducible behavior and current runtime evidence.
2. Preserve the last known-good private and public rollback versions and runtime data.
3. Make a minimal, scoped change; do not refactor unrelated collector logic.
4. Check syntax, static references, response schema, memory usage and data preservation.
5. Test with representative sanitized fixtures, including stale source, missing data, verified zero, refresh and partial index cases.
6. Document what was tested locally and what still requires live deployment verification.
7. Deploy separately to the intended private or public location; do not overwrite JSON/history.
8. Validate after repeated refreshes; roll back on regression.

## Historical project notes

The public dashboard had a known stable recovery reference **v10.0.8 PUBLIC**. Private and public version sequences are independent; do not treat their numeric versions as equivalent. These are historical project references, **not** proof of current deployment status.

## Secrets review

Review both file contents **and Git history** before making a repository public. `.gitignore` does not protect secrets that are already committed. Rotate any credential that was ever exposed.
