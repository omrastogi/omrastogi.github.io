---
layout: page
title: Twinsee at C10 Labs
description: Infant monitoring for Twinsee at C10 Labs — semi-supervised YOLO on pseudo-labelled video, infant posture classification, and a phone capture prototype that turns one recording into metric 3D, depth and camera trajectory
img: assets/img/projects/twinsee/thumb.jpg
importance: 3.5
category: industry
---

ML/CV Graduate Co-op at **C10 Labs**, Boston, on **Twinsee**, a camera-based infant monitor (Sep 2026 – present).

- **Semi-supervised detection** — YOLO trained on video frames pseudo-labelled by Grounding DINO, YOLO and ByteTrack: precision 38% → 93%.
- **Infant posture classification** — from DINO features, infant pose, and the gravity direction estimated by GeoCalib.

## Phone capture prototype

How much can one phone recording give, before any extra hardware? An Android recorder on a Samsung Galaxy S25 captures wide + ultrawide video (1080p30 each, stabilization and distortion correction off, exposure locked) with every motion sensor on the same clock, plus the factory calibration and per-frame camera metadata. Everything below is computed offline from one 16-second orbit of a glass cup on a desk — a deliberately hard scene: transparent glass, a glossy black desk and monitor, motion blur.

The full demo report is below: what the phone records (sensor and camera dashboard), then gravity, north and height; the metric SfM cloud; planes and object measurement; stereo + Depth Pro depth fusion and its accuracy; a Gaussian splat; a MapAnything dense cloud; and the MegaSaM trajectory fixed with phone scale. The 3D viewers are live: drag to orbit, scroll to zoom.

<a class="btn btn-sm z-depth-0" role="button" href="{{ '/assets/twinsee-demo/index.html' | relative_url }}" target="_blank" rel="noopener">Open the report full screen</a>

<iframe id="twinsee-report" src="{{ '/assets/twinsee-demo/index.html' | relative_url }}" title="Twinsee capture demo report" style="width: 100%; height: 2400px; border: 0; margin-top: 1rem" onload="const f = this, b = f.contentDocument.body; new ResizeObserver(() => (f.style.height = b.offsetHeight + 'px')).observe(b)"></iframe>
