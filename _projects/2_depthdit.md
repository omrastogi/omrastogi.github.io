---
layout: page
title: DepthDiT
description: Diffusion Transformer for monocular depth estimation — adapting PixArt-Alpha and PixArt-Sigma for dense prediction
img: assets/img/projects/depthdit/comparison.png
importance: 2
category: research
---

**DepthDiT** is a Diffusion Transformer architecture for monocular depth estimation, developed at the Vision and AI Lab, Indian Institute of Science (IISc) over 14 months.

## Architecture

- Adapted **PixArt-Alpha** and **PixArt-Sigma** Diffusion Transformer backbones for pixel-level depth prediction
- Replaced the generation objective with a depth prediction head trained using diffusion loss
- Designed a **masked diffusion loss** to better model mirror-like reflective surfaces, reducing artifacts in specular regions

## Dataset

- Built an automated pipeline to curate and QA **30,000 images from MatrixCity** for depth training
- Pipeline covered: scene filtering, depth validity checks, sampling diversity, and metadata tracking

## Results

| Metric | Value |
|--------|-------|
| AbsRel | 0.107 |
| δ1     | 0.88  |
| Steps  | 40k   |

## Reflection Inpainting

Implemented **DreamBooth** and **RealFill**-inspired inpainting workflows to improve reflection coherence and consistency across generated scenes.

**Venue:** Vision and AI Lab, Indian Institute of Science (IISc), Bengaluru
**Duration:** Jan 2024 – Feb 2025

## Stack

Python · PyTorch · PixArt-Alpha · PixArt-Sigma · MatrixCity · DreamBooth · RealFill

{% include figure.liquid loading="eager" path="assets/img/projects/depthdit/comparison.png" title="DepthDiT depth prediction examples" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  Qualitative comparison against DepthAnything v2 and Lotus — DepthDiT (ours, right) on glass, netting, and specular surfaces.
</div>
