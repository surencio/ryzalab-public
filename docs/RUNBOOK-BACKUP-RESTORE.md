# RUNBOOK-BACKUP-RESTORE.md

Last updated: 2026-03-03

## Goal

Make backups boring and reliable so you can experiment without fear.

## Backup Types (Home Assistant)

- **Snapshot (HA OS / Supervisor):** quick, convenient. Great for pre-deploy safety.
- **Full backup:** includes add-ons and more state. Better before big upgrades.

Exact UI labels change by version. Follow your HA UI for "Backups" or "Snapshots".

## Minimum Rule

Before any Medium or High risk deploy:

1. Create a backup snapshot
2. Write down the timestamp and what change it corresponds to
3. Store it somewhere you can access if HA is down (cloud drive, NAS, external disk)

## Where to Store Backups

- Best: a second device or cloud drive
- Good: NAS share
- Avoid: only storing on the HA host drive

## Restore Checklist

1. Identify last known good backup.
2. Restore snapshot.
3. Confirm HA boots.
4. Validate critical flows: phone app connects, core lights respond, locks behave, HVAC mode is correct.

## Validation After Restore

- Check logs for obvious integration failures
- Confirm automations are enabled as expected
