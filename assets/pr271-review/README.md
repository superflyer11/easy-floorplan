# PR #271: roller-shutter sunlight review evidence

Direct screenshots of the revised `docker/config/floorplan-demo.yaml` in the development Home Assistant container (Home Assistant 2026.9.2, Chromium 151). The browser viewport was 1280 × 1020 CSS pixels at device scale factor 2; screenshots contain the complete floorplan card.

- Before: upstream `3f89501`, using the same revised demo configuration.
- After: PR head `7537d2f`.
- The sun bearing is fixed at 0 degrees and `sunDimming` is disabled, as documented in `docker/README.md`. `sunlight` stays enabled.
- `grid_options: { columns: full, rows: auto }` gives the card the full section width for readable screenshots. No room geometry or opening configuration was changed for capture beyond the committed demo changes.
- The history generator and lamps are off. The real demo cover is moved through `cover.set_cover_position` and its reported position is checked before capture. These are live Home Assistant states, not mocked rendering inputs.

The target is `o1`, the opening at the centre of the top wall, bound to `cover.living_room_window`. The other top window continues admitting sunlight and is unchanged.

| Build | Cover position | Target sunlight opening |
| --- | --- | --- |
| Before | 0% | 140 units (incorrectly fully clear) |
| After | 100% | 140 units |
| After | 50% | 70 units |
| After | 0% | No target patch |

`measurements.json` records the cover's reported position and actual SVG sunlight polygons; no browser page errors were observed. `dashboard.json` is the capture configuration and can be pasted as valid YAML into the development dashboard's raw configuration editor.

The development instance used the same Home Assistant image, environment, ports and mounts as the repository's Compose configuration, started with `docker run` because Compose is unavailable on this host. No personal home configuration is included.
