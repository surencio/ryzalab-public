# White House Example Package

Example Home Assistant package for the "High-Anxiety Security Perimeter" demo.

## Loading This Package

Add to your `configuration.yaml`:

```yaml
homeassistant:
  packages:
    white_house: !include_dir_merge_named packages/examples/white_house
```

This folder is domain-keyed for `!include_dir_merge_named` (one YAML file per HA domain).

## Files

- `automation.yaml` – all example automations
- `history_stats.yaml` – copresence hours sensor
- `input_boolean.yaml` – helper toggles
- `input_number.yaml` – copresence threshold helper
- `notify.yaml` – household notify group
- `script.yaml` – Sonos morning routine
- `template.yaml` – copresence binary sensor

## Before Use

Replace all PLACEHOLDER entity IDs with your own. See each file for inline notes.
