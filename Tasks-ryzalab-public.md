# Tasks-ryzalab-public.md
Repo: ryzalab-public (public starter)
Last updated: 2026-03-03

## TL;DR
Build a public "GitOps Starter Kit" for Home Assistant that includes:
- a repo skeleton,
- minimal governance (PR checklist plus release plus backup discipline),
- runbooks (backup, restore, deploy, rollback),
- optional CI (YAML lint),
while explicitly excluding proprietary RyzaLab automation.

## Delivery Approach
Phase 0: Skeleton (must-have)
- Create repo layout
- Add docs and templates
- Add .gitignore for HA
- Add sample config placeholders

Phase 1: Guardrails (should-have)
- Add PR template plus checklist
- Add release and rollback runbooks
- Add optional GitHub Actions (yamllint)

Phase 2: Nice extras (could-have)
- Add sample packages example module
- Add lightweight pre-commit hooks (optional)
- Add dev-instance guide (optional)

## Epic A: Create repo structure
Tasks
- A1. Create base folders:
  - /config/ (intended HA config root)
  - /docs/
  - /.github/ (optional workflows and templates)
  - /templates/ (ADR, changelog, checklists)
- A2. Add .gitignore tuned for HA:
  - ignore .storage, secrets.yaml, *.db, backups, logs
- A3. Add README.md:
  - what this repo is
  - what it is not
  - quickstart steps
  - boundaries between YAML and UI
- A4. Add license (RyzaLab License – see LICENSE)

Acceptance criteria
- New user can clone repo and understand next steps in 10 minutes.
- Repo does not encourage committing secrets or .storage.

## Epic B: Minimum viable governance
Tasks
- B1. Create docs/GOVERNANCE.md:
  - branching model: main plus feature branches
  - PR checklist
  - backup before deploy rule
  - definition of done
- B2. Add .github/pull_request_template.md with checklist:
  - what changed
  - risk level
  - backup taken
  - rollback plan
  - impacted subsystems
- B3. Add templates/ADR-template.md:
  - context, decision, alternatives, consequences

Acceptance criteria
- A change can be reviewed by a non-engineer using the template.
- Rollback plan is captured every time.

## Epic C: Runbooks
Tasks
- C1. docs/RUNBOOK-BACKUP-RESTORE.md
- C2. docs/RUNBOOK-DEPLOY.md
- C3. docs/RUNBOOK-ROLLBACK.md
- C4. docs/SECURITY.md

Acceptance criteria
- Runbooks are executable by someone without GitOps knowledge.
- Runbooks include verification and stop conditions.

## Epic D: Optional CI checks (MVP)
Tasks
- D1. GitHub Actions workflow for yamllint on PR
- D2. .yamllint config tuned for HA YAML
- D3. README section: how CI works, how to run lint locally

Acceptance criteria
- PRs show pass or fail checks.
- Workflow does not require secrets.

## Epic E: Cursor Agent handoff
Tasks
- E1. docs/CURSOR-AGENT-PROMPT.md with constraints:
  - exclude proprietary scripts
  - no internal repo URLs
  - public-safe docs only

Acceptance criteria
- Prompt is copy-paste usable and produces the intended repo.

## Out of scope (explicit)
- Entity rename tooling
- Proprietary RyzaLab governance gates
- Any keys, tokens, or production secrets
