# Labs Themes for Home Assistant

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://hacs.xyz)
[![Validate](https://github.com/mckay115/labs-ha-themes/actions/workflows/validate.yml/badge.svg)](https://github.com/mckay115/labs-ha-themes/actions/workflows/validate.yml)
[![GitHub Release](https://img.shields.io/github/v/release/mckay115/labs-ha-themes)](https://github.com/mckay115/labs-ha-themes/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A collection of clean, modern themes for [Home Assistant](https://www.home-assistant.io/),
installable via [HACS](https://hacs.xyz). All themes ship in a single file and appear
individually in the Home Assistant theme picker.

## Themes

| Theme | Description |
| --- | --- |
| `labs-basic` | A simple, clean, sci-fi minimal theme — deep-space backgrounds with electric cyan accents. Supports both light and dark modes automatically. |
| `homeworld-command` | Stargate Atlantis / Homeworld Command inspired — Lantean console aesthetics with deep ocean-blue backgrounds, glowing teal primaries, and gate-amber active states. Light and dark modes. |
| `overwatch` | Palantir/Anduril inspired tactical interface — stark graphite neutrals, sharp corners, neutral gray borders, and pumpkin-orange signal colors. Light and dark modes. |

## Prerequisites

Home Assistant must be configured to load themes from the `themes` directory.
Add this to your `configuration.yaml` (if it isn't there already), then restart:

```yaml
frontend:
  themes: !include_dir_merge_named themes
```

## Installation

### HACS (recommended)

1. In HACS, open the overflow menu (⋮) → **Custom repositories**.
2. Add `https://github.com/mckay115/labs-ha-themes` with type **Theme**.
3. Search for **Labs Themes** in HACS and install it.
4. Reload themes: go to **Developer Tools → Actions** and run `frontend.reload_themes`
   (or restart Home Assistant).

### Manual

1. Download [`themes/labs.yaml`](themes/labs.yaml).
2. Copy it into the `themes` folder of your Home Assistant configuration directory.
3. Reload themes or restart Home Assistant.

## Usage

- **Per user:** open your profile (bottom of the sidebar) and pick the theme.
  Choose *Auto* for light/dark to follow your device, or force a mode.
- **Via automation/action:** use the `frontend.set_theme` action:

  ```yaml
  action: frontend.set_theme
  data:
    name: labs-basic
  ```

## Labs Cards integration

These themes define extra CSS variables consumed by
[Labs Cards](https://github.com/mckay115/labs-ha-cards) to give each theme its
own card personality (glow effects, heading treatments):

| Variable | Purpose |
| --- | --- |
| `labs-glow` | Box-shadow applied to active/energized card elements (amber glow on `homeworld-command`, cyan on `labs-basic`, none on `overwatch`) |
| `labs-heading-transform` | Heading text-transform (`uppercase` on `homeworld-command` and `overwatch`) |
| `labs-heading-spacing` | Heading letter-spacing (widest on `overwatch` for the tactical look) |

The cards fall back to standard theme variables when these are absent, so they
work with any theme — these hooks just make them look their best with ours.

## Screenshots

_Coming soon._

## Contributing

New themes are added as new top-level keys in [`themes/labs.yaml`](themes/labs.yaml)
(HACS manages a single theme file per repository). PRs and issues welcome.

## License

[MIT](LICENSE)
