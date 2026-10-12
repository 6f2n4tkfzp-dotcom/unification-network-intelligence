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

## GitHub change workflow

1. Create a dedicated branch for each documentation or source change. Do not work directly on `main`.
2. Review each changed file and the full diff before opening a pull request. Confirm that no credentials, private wallet annotations, runtime JSON, server paths, logs or private API details are included.
3. Run relevant checks. For documentation, verify links and factual statements. For code, include syntax checks, schema tests, sanitized fixtures and reproducible evidence.
4. Open a pull request describing the purpose, changed files, checks performed, rollback implications and any remaining deployment tests.
5. Review and merge the pull request only after the checks pass. Keep production deployment a separate, explicit step.
6. Never publish a complete production webroot, collector package, backup archive or raw runtime dataset in this public repository.

### Recommended branch protection (repository owner action)

In GitHub, open **Settings → Branches** or **Settings → Rules → Rulesets** (the location depends on GitHub's current interface). Protect `main` with a pull-request requirement and prevent force pushes/deletions. Require status checks only after actual CI checks have been configured; otherwise changes could be blocked without a way to satisfy the requirement. These settings must be confirmed by the repository owner; they are not enabled by this documentation update.

### Defensive ignore rules

The root `.gitignore` reduces accidental staging of private files. It is not a security boundary: explicit forced adds, direct uploads and files already in Git history can still expose information. Review the complete diff and history before making changes public.

## Historical project notes

The public dashboard had a known stable recovery reference **v10.0.8 PUBLIC**. Private and public version sequences are independent; do not treat their numeric versions as equivalent. These are historical project references, **not** proof of current deployment status.

## Secrets review

Review both file contents **and Git history** before making a repository public. `.gitignore` does not protect secrets that are already committed. Rotate any credential that was ever exposed.
