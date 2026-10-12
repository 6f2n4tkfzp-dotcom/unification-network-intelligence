# Security policy

## Public repository safety

Do **not** commit production secrets, API keys, access tokens, wallet private keys, authentication configuration, internal endpoints, private runtime JSON, databases, logs, or backups. Never include real user-specific wallet monitoring data or session details.

A `.gitignore` file is only a convenience. It does not prevent intentional uploads, force GitHub to hide committed files, or remove secrets from Git history.

## Responsible reporting

Do not post credentials or exploit instructions for a live deployment in a public issue. Contact the repository owner privately using an appropriate GitHub channel.

## Before releasing code

Review dependencies and licenses, scan source and history for secrets, use synthetic fixtures, check all API access boundaries, and verify that public views do not fetch private files.

## Scope

This repository does not authorize testing, scanning or attempting to bypass authentication on any live site.
