# QA Findings – feat/white-house-example

_Paste this into the PR as a comment._

---

## Summary

| Check | Result |
|-------|--------|
| yamllint | Pass |
| Links | All valid |
| Diff review | Looks good; package include structure should be validated in HA |
| CI | Workflow updated: runs only on changed YAML files; skips when no YAML changed |

---

## 1. yamllint – PASS

`yamllint -c .yamllint .` exits 0; no issues.

---

## 2. Links – PASS

All referenced paths exist:

- `docs/examples/white-house/README.md`
- `config/packages/examples/white_house/`
- `config/dashboards/examples/white_house_command_center.yaml`
- `assets/white-house/README.md`
- `LICENSE`
- `PRD-ryzalab-public.md`, `Tasks-ryzalab-public.md`
- `docs/GOVERNANCE.md`, `AI_GOVERNANCE.md`, runbooks, `SECURITY.md`
- `.github/workflows/yamllint.yml`
- `docs/examples/white-house/README.md`

**Note:** `assets/white-house/README.md` references `white-house-front.webp` as an example; that file is intentionally absent (placeholder instructions).

---

## 3. Diff Review – Minor Notes

**Good:**
- Clear PLACEHOLDER comments for entity IDs
- Safe defaults (notify-only, no lock toggling)
- Consistent structure across YAML files
- `.yamllint` truthy rules allow `on`/`off` (common in HA)
- `.gitignore` excludes `secrets.yaml`, `.storage/`, etc.

**Potential issue – package include structure**

The package uses:

```yaml
white_house: !include_dir_merge_named packages/examples/white_house
```

With `!include_dir_merge_named`, each file becomes a top-level key (e.g. `helpers`, `automations`, `sonos`). HA expects domain keys like `input_boolean`, `automation`, `script`, etc. That can produce invalid top-level keys (`helpers`, `automations`, etc.) instead of the expected domains.

**Recommendation:** Run “Check configuration” in a dev HA instance with this package loaded. If it fails, the package may need a different include pattern (e.g. a single entry file that includes the others, or restructuring so each file uses domain keys directly).

---

## 4. CI Change

yamllint workflow now:
- Runs only on changed `.yml` and `.yaml` files
- Skips entirely if the PR touches only Markdown, docs, or other non-YAML files
