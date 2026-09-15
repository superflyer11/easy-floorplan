# Overlay sizing in 3D on a narrow card (issue #261)

Rendered from `docker/config/floorplan-demo.yaml` at a 420px card width — the
width of the screenshots in TruthOf42's report — with the repository's
screenshot harness and stubbed Home Assistant elements.

| Variant | Plan box | Badge width |
| --- | --- | --- |
| 2D, `overlayScale: fixed` (today's default) | 420×252 | 36px |
| 3D, `overlayScale: fixed` | 420×263 | 36px |
| 3D, `overlayScale: plan` | 420×263 | 12px |

The drawing is about 72% of its flat linear size in 3D, because the rooms turn
45° and the projected box is wider than the plan. Fixed-pixel badges do not
follow it down, which is what reads as clutter.
