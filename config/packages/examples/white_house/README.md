# White House Example Package

Example Home Assistant package for the "High-Anxiety Security Perimeter" demo.

## Loading This Package

Add to your `configuration.yaml`:

```yaml
homeassistant:
  packages:
    !include_dir_named packages
    examples:
      white_house: !include_dir_merge_named packages/examples/white_house
```

Or copy the files into your main `packages/` folder and adapt the include.

## Files

- `helpers.yaml` – input_booleans, input_numbers, notify group
- `automations.yaml` – departure guard, leak alert, night path
- `sonos.yaml` – morning music script, quiet hours
- `copresence.yaml` – copresence sensor and nudge automation
- `breaking_bad.yaml` – fun-mode automations (roof pizza, basement air)

## Before Use

Replace all PLACEHOLDER entity IDs with your own. See each file for inline notes.
