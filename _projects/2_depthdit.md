---
layout: page
title: DepthDiT
description: Diffusion Transformer for monocular depth estimation — adapting PixArt-Alpha and PixArt-Sigma for dense prediction
img: assets/img/projects/depthdit/comparison.png
github: https://github.com/omrastogi/DepthDiT
importance: 3
category: research
---

**DepthDiT** is a Diffusion Transformer architecture for monocular depth estimation, developed at the Vision and AI Lab, Indian Institute of Science (IISc) over 14 months.

## Abstract

DepthDiT adapts text-to-image Diffusion Transformers to monocular depth estimation. Starting from PixArt-Alpha and PixArt-Sigma backbones, the denoising pipeline is modified to predict dense depth maps instead of RGB outputs. The model is trained on 30,000 curated images from MatrixCity, a synthetic urban dataset spanning street-level to aerial viewpoints, and a masked diffusion loss targets mirror-like reflective surfaces. The best checkpoint reaches AbsRel 0.107 and δ1 0.88 at 40k steps.

## My role

I worked on DepthDiT as a Project Associate at the Vision and AI Lab, IISc. I trained the Diffusion Transformer, adapting the PixArt-Alpha and PixArt-Sigma backbones for depth prediction. I built the automated pipeline to curate and QA 30,000 MatrixCity images, designed the masked diffusion loss for reflective surfaces, and implemented the DreamBooth and RealFill-inspired inpainting workflows.

## Links

- **Code:** [github.com/omrastogi/DepthDiT](https://github.com/omrastogi/DepthDiT)
- **Reflection inpainting code:** [github.com/omrastogi/inpainting_reflections](https://github.com/omrastogi/inpainting_reflections)
<!-- TODO: add paper and website links if the work is published. -->

## Architecture

- Adapted **PixArt-Alpha** and **PixArt-Sigma** Diffusion Transformer backbones for pixel-level depth prediction
- Replaced the generation objective with a depth prediction head trained using diffusion loss
- Designed a **masked diffusion loss** to better model mirror-like reflective surfaces, reducing artifacts in specular regions

## Dataset

- Built an automated pipeline to curate and QA **30,000 images from MatrixCity** for depth training
- Pipeline covered: scene filtering, depth validity checks, sampling diversity, and metadata tracking

## Results

| Metric | Value |
| ------ | ----- |
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
