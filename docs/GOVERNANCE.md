# GOVERNANCE.md

Last updated: 2026-03-03

## TL;DR

- Git is the source of truth for YAML you own.
- The HA UI is allowed, but you must document UI-only changes and avoid committing .storage.
- Every deploy has a backup and a rollback plan.

## Principles

1. Reversible over clever
2. Small changes over big changes
3. Backup before deploy
4. Explain changes in plain English (so a household co-owner can review)

## What Goes in Git

**Yes:** automations, scripts, templates (YAML), dashboards (YAML mode where possible), packages you author, documentation and runbooks

**No:** secrets.yaml real values, config/.storage/, databases, logs, backups

## Branching Model (Simple)

- main is the stable deployed state.
- For changes, create a feature branch: feat/<short-name>, fix/<short-name>, chore/<short-name>
- Merge via PR using the checklist.

## Change Levels (Risk)

- **Low:** renames, comments, descriptions
- **Medium:** new automation, new script, new template, dashboard wiring
- **High:** anything that could lock someone out, affect HVAC, alarms, door locks, network, or core integrations

High-risk changes require: confirmed backup, explicit rollback steps, a quick household test.

## Definition of Done (for a PR)

- YAML parses and HA can restart or reload cleanly
- PR template is filled out
- Backup has been taken (or explicitly noted why not)
- Rollback plan is written
- Post-deploy validation steps listed and completed

## UI Changes Policy

If you make a UI change that is not reflected in YAML: capture a note in the PR description under "UI changes"; consider exporting YAML equivalent if available; do not commit .storage to "make it look versioned."

## If Something Breaks

No heroics. Roll back first, investigate second. See docs/RUNBOOK-ROLLBACK.md.
