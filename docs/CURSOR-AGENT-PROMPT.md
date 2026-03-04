# CURSOR-AGENT-PROMPT.md

Last updated: 2026-03-03

## Purpose

You are Cursor Agent. Implement a public "Home Assistant GitOps Starter" repo that provides MVP value.

## Non-negotiable Constraints

- Do NOT copy proprietary RyzaLab scripts or internal governance gates.
- Do NOT include any secrets, tokens, or internal URLs.
- You MAY reference internal repo patterns only conceptually (folder layout, documentation style), but you must re-write content for public use.

## Required Prompt Tags

Use these in every Cursor Agent prompt:

- @PRD-ryzalab-public.md
- @Tasks-ryzalab-public.md
- @docs/HANDOFF.md

If the agent cannot restate scope and constraints from the PRD, it should stop.

## Inputs

- PRD-ryzalab-public.md
- Tasks-ryzalab-public.md
- Atomic_Tasks.md

## Output Requirements

Create or update these files:

**Root:** README.md, .gitignore, LICENSE, PRD-ryzalab-public.md, Tasks-ryzalab-public.md, Atomic_Tasks.md

**Docs:** docs/GOVERNANCE.md, docs/RUNBOOK-BACKUP-RESTORE.md, docs/RUNBOOK-DEPLOY.md, docs/RUNBOOK-ROLLBACK.md, docs/SECURITY.md, docs/AI_GOVERNANCE.md, docs/HANDOFF.md

**Templates:** templates/ADR-template.md, templates/CHANGELOG-template.md

**GitHub:** .github/pull_request_template.md, .github/workflows/yamllint.yml, .yamllint

**Optional:** config/packages/examples/ – clearly label examples as examples only.

## Quality Checks

- Ensure .gitignore covers config/.storage/ and config/secrets.yaml.
- Docs must be accurate, executable, and not overengineered.
- Keep language simple, avoid enterprise buzzwords.
- No references to private RyzaLab repos or tooling.
