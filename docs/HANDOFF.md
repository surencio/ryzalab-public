# HANDOFF.md

Last updated: 2026-03-03

## What Changed (White House Example Implementation)

### Added

- **docs/examples/white-house/README.md** – Marketing narrative, persona ("High-Anxiety Security Perimeter"), use case, tagline, disclaimer
- **assets/white-house/README.md** – Placeholder instructions (do not commit copyrighted images)
- **config/packages/examples/white_house/** – Example HA package:
  - helpers.yaml (input_booleans, input_numbers, notify group)
  - automations.yaml (departure guard, leak alert, night path)
  - sonos.yaml (morning music script, quiet hours)
  - copresence.yaml (Esther Perel–inspired copresence nudge)
  - breaking_bad.yaml (roof pizza, basement air – safe humor)
  - README.md (how to load the package)
- **config/dashboards/examples/white_house_command_center.yaml** – Command center dashboard
- **docs/AI_GOVERNANCE.md** – Allowed actions, stop conditions, human gates, prompt tags
- **docs/CURSOR-AGENT-PROMPT.md** – Updated with required prompt tags (@PRD, @Tasks, @HANDOFF)

### Modified

- None (additive only; existing PRD, Tasks, Atomic_Tasks, LICENSE preserved)

### Also Added (Full Skeleton)

- README.md – White House demo section, quickstart, links
- .gitignore – HA exclusions
- docs/INDEX.md, GOVERNANCE.md, RUNBOOK-*, SECURITY.md
- docs/AI_GOVERNANCE.md, CURSOR-AGENT-PROMPT.md, HANDOFF.md
- .github/pull_request_template.md, .github/workflows/yamllint.yml (CI on main)
- .yamllint, templates/ADR-template.md, templates/CHANGELOG-template.md
- config/README.md – how to load White House package

### Not Added (By Design)

- Copyrighted images (Breaking Bad house photos) – use placeholders per assets/white-house/README.md
- Lock toggling automations – notify only, safe by default
- Secrets, tokens, internal URLs, camera RTSP, addresses

## What Is Next

1. Merge PR (feat/white-house-example → main)
2. Rollback note: revert merge and remove docs/examples/white-house/, config/packages/examples/white_house/, config/dashboards/examples/

## CI

yamllint workflow is on main. PRs trigger lint on YAML changes.
