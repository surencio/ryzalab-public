# PRD-ryzalab-public.md
Title: RyzaLab Public GitOps Starter for Home Assistant
Status: Draft (MVP)
Owner: RyzaLab
Last updated: 2026-03-03

## TL;DR
RyzaLab Public is a lightweight, non-proprietary starter repo that helps a Home Assistant user:
1) organize configuration in a Git-friendly structure,
2) ship changes with a simple PR checklist,
3) avoid common footguns (secrets, backups, rollbacks),
4) optionally add basic CI (YAML linting).

It is intentionally not the full RyzaLab "Golden Master" system and excludes proprietary automation and governance tooling.

## Problem
Home Assistant grows organically. Config sprawl and UI-only edits make it hard to:
- understand what changed and why
- roll back safely
- share setups across homes
- collaborate with a spouse, friend, or contractor
- avoid breaking automations at the worst time

Users want GitOps outcomes (history, review, rollback) without enterprise ceremony.

## Users and Jobs To Be Done
Primary users
- Home Assistant power user (HA OS or Container) who wants reliability.
- Household co-owner who wants confidence changes will not break the home.

JTBD
- "When I change my HA config, I want a safe workflow so I can deploy improvements without breaking core automations."
- "When something breaks, I want a rollback plan that works in minutes."
- "When I share control with another person, I want clear rules for changes."

## Goals
- Provide an opinionated repo structure that works for HA YAML configuration.
- Provide a minimal Git workflow a non-software engineer can follow.
- Provide runbooks for backup, restore, and safe release.
- Provide optional CI checks that catch dumb errors early (YAML lint).
- Make it easy to adopt: copy repo, replace placeholders, start committing.

## Non-Goals
- No proprietary scripts (for example entity rename pipelines, advanced enforcement).
- No attempt to cover every HA install mode or add-on.
- No hard requirement for GitHub Actions, Docker, Kubernetes, or complex infra.
- No promise of full UI-state versioning (some state lives in `.storage`).

## Success Metrics (MVP)
- Time to first commit: under 60 minutes after cloning.
- A user can complete a change via PR and deploy with a backup in under 15 minutes.
- A rollback can be executed in under 10 minutes using documented steps.
- CI catches common YAML mistakes before deployment (when enabled).

## Key Decisions
### What to commit (and what not to)
Commit:
- YAML configuration you own (automations, scripts, templates, dashboards in YAML mode when possible)
- packages and blueprints you maintain
- documentation, runbooks, and checklists

Do not commit:
- secrets (real values), tokens, API keys
- `.storage` (UI-managed state, sometimes tokens)
- backups/snapshots (store externally, document process)

### YAML-first, UI-realistic
We support both, but the repo is optimized for YAML-first changes:
- Prefer YAML for automations and scripts when practical.
- Document UI-only changes and do not commit `.storage` to simulate versioning.

## MVP Scope
Repo artifacts
- README.md with quickstart
- docs/ governance and runbooks
- config/ folder layout suitable for HA
- .gitignore for HA-specific exclusions
- Optional: .github/workflows for yamllint and basic checks
- Templates: PR checklist, changelog template, ADR template

Workflows
1) Change workflow (daily)
   - create branch
   - edit YAML
   - open PR using checklist
   - backup snapshot
   - deploy
   - monitor
2) Release workflow (weekly or as-needed)
   - tag release
   - write short changelog
   - store snapshot reference
3) Rollback workflow
   - restore snapshot or revert git commit, redeploy, confirm core functions

## Principles
- Boring, documented, and reversible.
- Clear boundaries: "this lives in git" vs "this lives in HA UI".
- Prefer checklists over clever automation.
- Friendly to Cursor Agent (clear file names, explicit tasks).

## Risks and Mitigations
| Risk | Why it matters | Mitigation |
|---|---|---|
| Users assume everything is versioned | `.storage` and UI state are not in git | Clear Boundaries section + guidance |
| Secrets leakage | Integrations require tokens | secrets.yaml pattern + .gitignore + SECURITY.md |
| Overengineering | GitOps can become heavy | Keep MVP small, optional CI |
| Breaking the home | Automations can lock someone out | Backup-before-deploy checklist + rollback runbook |

## Dependencies
- GitHub account (or other Git remote)
- HA install with file access (Samba add-on, VS Code add-on, or SSH)
- Optional: local tooling (yamllint) for checks

## Open Questions
- Optional "dev instance" pattern: include as guidance only?
- Include a minimal packages example, or keep repo empty by default?
