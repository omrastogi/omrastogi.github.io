---
layout: page
title: Production CV Deployments at Collablens
description: Built and deployed computer vision systems for ITC freight monitoring and Smartivity defect detection
img: assets/img/projects/collablens/thumb.jpg
importance: 3
category: industry
---

I joined Collablens in Dec 2022 as the founding senior research engineer and worked there until Jan 2024. Over 14 months, I built and deployed two production computer vision systems for industrial clients: a truck-loading monitoring system for ITC's freight operations, and a defect detection system for Smartivity's assembly line.

---

## ITC Freight Damage Mitigation

A near-real-time monitoring system installed at ITC loading bays to detect rough handling of freight bags during truck loading.

- Trained a YOLO detector to recognize impact patterns on superimposed video frames, a technique that compresses temporal motion into a single image so the model can learn what "rough handling" looks like visually
- Tuned the pipeline to operate at 70% recall on rough-handling events while keeping false positives under 5%, which was the threshold ITC needed to act on alerts without alert fatigue
- Built a parallel bag detection module that counted bags and classified bag types as they entered the loading zone, used for reconciliation against shipment manifests
- Integrated three independent vision modules (impact detection, bag counting, bag classification) into a single deployed pipeline running in near real-time on factory floor hardware

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/pipeline.png" title="Factory deployment" class="img-fluid rounded z-depth-1" %}
    </div>
    <!-- <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/metrics_ui.jpg" title="Lab testing with metrics UI" class="img-fluid rounded z-depth-1" %}
    </div> -->
</div>
<div class="caption">
  Left: deployed system at ITC loading bay. Right: lab testing interface showing real-time detection metrics.
</div>

---

## Smartivity Defect Detection

A vision-based quality control system for Smartivity's laser-cut MDF assembly kits, replacing manual inspection on the production line.

- Built a classifier to detect missing parts in assembled units, comparing against a reference layout per SKU; reached 97% accuracy on the production dataset
- Reduced per-unit inspection time from around 10 seconds (manual) to about 2 seconds (automated), enabling line-rate inspection
- Designed a millimeter-precision deviation detection module using homography transformations to align captured images with reference templates before pixel-level comparison
- Iterated on the physical rig (lighting, camera placement, enclosure) until detection was robust to factory floor conditions including variable ambient light and conveyor vibration

The system went through six iterations between the first sketch and the final production rig. The progression below walks through design, prototype, development, first on-site deployment, debugging under factory conditions, and the two final production modules.

<div class="row justify-content-center">
    <div class="col-md-7">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/design.jpg" title="Design sketch" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>Design.</strong> Initial dimensional sketches and component layout, drafted before fabrication.
</div>

<div class="row justify-content-center">
    <div class="col-md-5">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/prototype.jpg" title="PVC prototype" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>Prototype.</strong> First physical build — PVC enclosure with mounted Raspberry Pi Camera Module 3.
</div>

<div class="row align-items-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/dev1.jpg" title="Development — bench testing" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/dev2.jpg" title="Development — integrated rig" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>Development.</strong> Bench-testing the imaging and inference pipeline before factory installation.
</div>

<div class="row justify-content-center">
    <div class="col-md-4">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/first_deployment.jpg" title="First on-site deployment" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>First Deployment.</strong> Rig installed at the Smartivity assembly line for the first on-site test.
</div>

<div class="row align-items-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/debug.jpg" title="On-site debugging" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/debug2.jpg" title="On-site debugging — lighting and alignment" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>Debugging.</strong> Iterating on lighting, camera placement, and conveyor alignment under factory floor conditions.
</div>

<div class="row align-items-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/missing_parts_detection.jpg" title="Missing parts detection" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/collablens/milimeter_defects.jpg" title="Millimeter-precision defect detection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  <strong>Final Deployments.</strong> Left: missing-parts detection running on the production line. Right: millimeter-precision defect detection comparing captured frames against the reference template.
</div>

---

## Stack

Python, YOLO, OpenCV, Raspberry Pi (edge inference), AWS, GCP, homography-based image alignment, custom PVC and aluminum-extrusion rig fabrication.