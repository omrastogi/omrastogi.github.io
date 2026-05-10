---
layout: page
title: Production CV Deployments at Menmitsu
description: Founding senior engineer — shipped YOLO-based freight damage detection and defect inspection for ITC and Smartivity
img: assets/img/projects/menmitsu/thumb.jpg
importance: 3
category: industry
---

As the **founding senior research engineer** at Menmitsu Private Limited (Dec 2022 – Jan 2024), I led the zero-to-one development and production deployment of two computer vision systems: one for ITC's freight damage mitigation and one for Smartivity's defect detection automation.

---

## ITC Freight Damage Mitigation

A truck-loading monitoring system to detect rough handling of freight in near real-time.

- Enhanced rough-handling detection using a **YOLO model on superimposed video frames**, achieving **70% accuracy** with **fewer than 5% false detections**
- Implemented robust bag detection algorithms tracking bag count and types
- Led integration and deployment of **3 complex intelligent modules** operating in near real-time capacity

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/menmitsu/factory_hero.jpg" title="Factory deployment" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/menmitsu/metrics_ui.jpg" title="Lab testing with metrics UI" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Left: factory deployment setup. Right: lab testing interface with real-time metrics. (Placeholder — replace with actual deployment photos.)
</div>

---

## Smartivity Defect Detection

Research-focused automation for detecting missing parts in assembled products.

- Advanced missing-part detection to **97% accuracy**, reducing inspection time from **10 to 2 seconds** (5x speedup)
- Developed a **millimeter-precision deviation detection system** using homography transformation techniques

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/menmitsu/pvc_prototype.jpg" title="PVC prototype with Pi camera" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/menmitsu/dimensional_sketch.jpg" title="Dimensional sketch" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/menmitsu/pi_camera.jpg" title="Pi camera close-up" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Left: PVC prototype with Pi camera. Center: dimensional sketch. Right: Pi camera setup. (Placeholder — replace with actual hardware photos.)
</div>

---

## Stack

Python · YOLO · OpenCV · AWS · GCP · Raspberry Pi · Homography · Deep Learning
