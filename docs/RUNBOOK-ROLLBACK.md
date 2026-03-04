# RUNBOOK-ROLLBACK.md

Last updated: 2026-03-03

## Goal

Get the home stable again in minutes.

## Option A: Restore a Snapshot (Fastest, Preferred)

1. Open HA Backups or Snapshots UI.
2. Select last known good snapshot.
3. Restore.
4. Validate critical flows (below).

## Option B: Git Revert and Redeploy

Use when snapshot is not available.

1. Identify the breaking commit.
2. Revert the commit on a branch.
3. Merge to main.
4. Deploy the reverted state.
5. Validate.

## Critical Validations

- Mobile app connects
- Lights work
- Locks behave correctly
- HVAC mode and setpoints are sane
- Any security system does not false-trigger
