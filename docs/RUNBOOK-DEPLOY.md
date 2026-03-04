# RUNBOOK-DEPLOY.md

Last updated: 2026-03-03

## Goal

Deploy changes safely with minimal downtime.

## Pre-deploy Checklist

- PR merged to main
- Backup snapshot taken (for medium or high risk)
- You know how to roll back

## How to Sync Repo to Home Assistant

Choose one:

1. **VS Code add-on:** edit directly in HA environment
2. **Samba share:** mount config folder and sync from your machine
3. **SSH or SFTP:** copy files to HA

Keep it simple. The key is consistency.

## Deploy Steps (Typical)

1. Sync config/ contents into HA config directory.
2. In HA UI, run "Check configuration" (if available).
3. Restart HA or reload affected components (restart for broad changes, reload for smaller targeted changes when safe).
4. Monitor logs for 5 to 10 minutes.

## Post-deploy Validation (2 minutes)

- Open HA mobile app and confirm connection
- Trigger one safe automation to confirm engine works
- Validate one critical path relevant to your change (locks, HVAC, alarms)

## Stop Conditions

If any of these happen, roll back:

- Repeated restart loops
- Missing core integrations
- Unexpected behavior in locks or HVAC
