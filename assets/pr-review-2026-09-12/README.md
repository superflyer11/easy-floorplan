# PR visual evidence

Captured from the repository's development Home Assistant container, running Home Assistant 2026.9.2, in headless Chromium 151 with a light theme and device scale factor 2. These are direct browser screenshots of a real Lovelace dashboard. The dashboard uses synthetic room geometry and the development container's template sensors; no personal home configuration is included.

- Before: upstream `3f89501`.
- Overlay after: `197c502` (`codex/overlay-min-width`). Viewport 540 × 470 CSS pixels.
- Room labels after: `6f692d8` (`codex/room-label-centroid`). Viewport 1000 × 760 CSS pixels.

`dashboard.json` contains both Lovelace views. JSON is valid YAML and can be pasted into a new dashboard's raw configuration editor in the dev instance. The overlay view has `overlayMinWidth: 800` on both builds; upstream ignores that unsupported option. The room-label view contains an L-shaped kitchen and a rectangle with extra collinear vertices along its top edge.

To reproduce, install dependencies, build the selected revision and start the development Home Assistant instance as described in `docker/README.md`. Create a dashboard with the supplied configuration. Turn off `input_boolean.history_generator`, set `input_number.living_temperature` to 21.5 and `input_number.living_humidity` to 45, then load the relevant view at the stated viewport. Refresh with a new resource URL after each build to avoid HA's bundle cache. The captured run used the same image, environment, ports and bind mounts as `docker/docker-compose.yml` via `docker run` because Compose was unavailable on the host.

`measurements.json` records computed label sizes and positions from the mounted card, along with browser page errors (none). The 540px overlay view changes room-label font size from 7.71429px to 11.4286px. The labels view moves the kitchen's x position from 300 to approximately 247.14 canvas units and centres the study at (725, 270).
