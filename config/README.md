# Config

This folder is intended as the Home Assistant config root. Copy it into your HA instance (or cherry-pick packages and dashboards).

## Loading the White House Example

Add to your `configuration.yaml`:

```yaml
homeassistant:
  packages:
    !include_dir_named packages
    examples:
      white_house: !include_dir_merge_named packages/examples/white_house
```

Replace all PLACEHOLDER entity IDs in the example files before use.
