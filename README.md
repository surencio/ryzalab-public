# RyzaLab Public: Home Assistant GitOps Starter (MVP)

## TL;DR

This repo is a lightweight starter kit to manage Home Assistant configuration with Git:

- clearer changes
- safer deployments
- easier rollback
- basic documentation and checklists

It is not the full RyzaLab internal system and it intentionally excludes proprietary automation.

## Who This Is For

- You run Home Assistant and you are tired of "what changed?" moments.
- You want a simple Git workflow without turning your home into a DevOps religion.

## What You Get

- Opinionated folder structure under config/
- Runbooks for backup, deploy, rollback
- Minimal governance (PR checklist)
- Optional GitHub Actions YAML linting

## The White House Demo

Fans call it "the White House." On the surface, it is a normal 2000s Albuquerque ranch. Under the hood, it is a high-anxiety security perimeter: privacy, local control, and reliable automation are not optional.

**Why it works as a demo:** relatable layout, high-stakes use case, maps to RyzaLab values (local-first, boringly reliable).

**Tagline:** Local control. No cloud. No witnesses.

- **Docs:** [docs/examples/white-house/README.md](docs/examples/white-house/README.md)
- **Example config:** [config/packages/examples/white_house/](config/packages/examples/white_house/)
- **Dashboard:** [config/dashboards/examples/white_house_command_center.yaml](config/dashboards/examples/white_house_command_center.yaml)

**Image rights:** Do not commit copyrighted images. Add your own to `assets/white-house/` per [assets/white-house/README.md](assets/white-house/README.md).

## What You Do Not Get

- Proprietary RyzaLab scripts (entity renaming, advanced enforcement, etc.)
- Enterprise release engineering
- Guarantees that UI-only state is versioned

## Quickstart (30 to 60 minutes)

1. Clone the repo.
2. Read: docs/GOVERNANCE.md and docs/RUNBOOK-BACKUP-RESTORE.md.
3. Decide how you will sync config/ into your Home Assistant instance (Samba, VS Code add-on, SSH).
4. Copy your current HA config into config/ (be careful with secrets).
5. Commit your initial state.
6. Make a tiny change via a feature branch plus PR template.
7. Take a backup snapshot.
8. Deploy and validate.

## Boundaries: What Git Can and Cannot Track

Home Assistant stores some state in config/.storage/ which is UI-managed and can include tokens. This repo assumes:

- YAML files you own go in git.
- config/.storage/ does not go in git.

Details: docs/GOVERNANCE.md.

## Suggested Repo Structure

- config/ – intended as HA config root
- docs/ – runbooks and governance
- templates/ – decision records and changelog templates
- .github/ – PR template and optional CI workflows

## CI (Optional)

PRs trigger yamllint on YAML files. Run locally: `yamllint -c .yamllint .`

## Safety First

Before any deploy:

- take a backup
- know your rollback plan

See: docs/RUNBOOK-DEPLOY.md and docs/RUNBOOK-ROLLBACK.md.

## AI Governance

If an AI agent touches this repo, it must follow docs/AI_GOVERNANCE.md. Required prompt tags: @PRD-ryzalab-public.md, @Tasks-ryzalab-public.md, @docs/HANDOFF.md.

## License

RyzaLab License – See [LICENSE](LICENSE) file.
