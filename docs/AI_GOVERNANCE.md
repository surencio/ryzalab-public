# AI Governance (Public)

Default posture: trust but verify.

## Allowed Actions (AI)

**Allowed:**
- Create and edit markdown docs
- Create and edit YAML examples
- Draft a PR description

**Not allowed:**
- Running commands that change your operating system
- Deploying to a real Home Assistant instance
- Writing or requesting secrets
- Making irreversible changes without a rollback plan

## Prompt Tags (Required)

Use these in every Cursor Agent prompt:

- @PRD-ryzalab-public.md
- @Tasks-ryzalab-public.md
- @docs/HANDOFF.md

If the agent cannot restate scope and constraints from the PRD, it should stop.

## Human Gates

- **Gate A:** Review the diff
- **Gate B:** Validate YAML (yamllint)
- **Gate C:** Backup then deploy
- **Gate D:** Smoke test dashboard and one automation

## Stop Conditions

Stop if the agent:
- Adds tooling that can touch live Home Assistant without you asking
- Introduces cloud dependencies without saying so clearly
- Expands scope beyond Tasks
- Proposes committing secrets, tokens, or personal identifiers
