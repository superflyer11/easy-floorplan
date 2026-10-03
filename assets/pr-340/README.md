# PR #340 screenshots

Captured from the production bundle at commit 64cd1393fcdc4cd55441d81a88e28f1098ae0544, using a local editor preview, a synthetic SVG floorplan and simulated Home Assistant context. These are not screenshots of a live Home Assistant installation.

- `01-trace-template.png`: image template underneath the drawn walls.
- `02-calibrate-two-points.png`: A/B calibration against a 60-unit doorway.
- `03-floor-below.png`: ground-floor walls shown under the first floor.

The browser check also applied a 90-unit calibration (1.5x scale), switched back to wall drawing, preserved thickness 6 after clearing its input, and checked that trace data stayed out of the saved config.
