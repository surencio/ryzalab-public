# Atomic_Tasks.md
Last updated: 2026-03-03

## How to use this
Run in order. Each task ends with:
- a commit
- a short commit message stating intent
- a quick self-check (does the repo still make sense?)

## 0. Initialize
1. Create new repo (suggested: ha-gitops-starter) with RyzaLab License (see LICENSE).
2. Default branch: main.

## 1. Structure
3. Add folders: config/, docs/, templates/, .github/workflows/.
4. Add .gitignore for Home Assistant.
5. Add README.md with purpose, quickstart, boundaries, and safety rules.

## 2. Governance
6. Add docs/GOVERNANCE.md.
7. Add PR template: .github/pull_request_template.md.
8. Add templates/ADR-template.md.
9. Add templates/CHANGELOG-template.md.

## 3. Runbooks
10. Add docs/RUNBOOK-BACKUP-RESTORE.md.
11. Add docs/RUNBOOK-DEPLOY.md.
12. Add docs/RUNBOOK-ROLLBACK.md.
13. Add docs/SECURITY.md.

## 4. CI (optional but recommended)
14. Add .github/workflows/yamllint.yml.
15. Add .yamllint config.
16. Update README with CI section.

## 5. Examples (optional)
17. Add config/packages/examples/ with one minimal package example.
    Clearly label as example only.

## 6. Cursor Agent handoff
18. Add docs/CURSOR-AGENT-PROMPT.md.
19. Final scan: ensure no proprietary RyzaLab scripts, internal gates, or private URLs.

## Definition of done
- Repo reads cleanly end-to-end.
- No secrets in git.
- Runbooks are usable by a non-engineer.
