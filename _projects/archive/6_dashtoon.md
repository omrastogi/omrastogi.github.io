---
layout: page
title: Production Diffusion Pipelines at Dashtoon
description: Flux LoRA adapters for 20+ characters, Hidream-l1 MoE integration, Bollywood bias mitigation, and Google Veo 2 evaluation
img: assets/img/projects/dashtoon/thumb.jpg
importance: 6
category: industry
---

As a **Research Engineer at Dashtoon** (Mar 2025 – Aug 2025), I built and shipped production-grade diffusion pipelines for animated character generation at 2048 resolution, spanning LoRA training, model integration, dataset curation, and video generation evaluation.

## Flux LoRA Adapters

- Trained and shipped **Flux LoRA adapters for 20+ characters** across **8 animation styles**
- Production inference optimized with **FP16, batching, and caching**, validated at 2048 resolution
- Improved character consistency, prompt alignment, and style fidelity across a diverse cast

## Hidream-l1 (MoE) Integration

- Integrated **Hidream-l1**, a Mixture-of-Experts diffusion model, into the animated character pipeline during early development
- Adapted inference and post-processing to deliver smoother 2048 resolution outputs with improved prompt alignment
- Hardened pipeline reliability around high-resolution generation, model switching, and output consistency

## Regional Bias Mitigation Dataset

- Built a **targeted dataset of 10,000+ images from 100+ Bollywood movies** via automated extraction pipeline
- Goal: reduce regional bias in image generation for South Asian character representation
- Pipeline covered automated clip extraction, frame selection, quality filtering, and metadata tagging

## Google Veo 2 & Frameo AI

- Worked hands-on with **Google Veo 2** during early access/POC to evaluate video generation quality and workflow fit for character animation
- Partnered with the **GCP team** to integrate the Veo 2 workflow into the new **Frameo AI platform**, aligning API usage, input/output formats, and reliability requirements for production

## Stack

Python · PyTorch · Flux · LoRA · Hidream-l1 (MoE) · Google Veo 2 · GCP · FP16 · Diffusion Models

{% include figure.liquid loading="eager" path="assets/img/projects/dashtoon/thumb.jpg" title="Dashtoon animated character pipeline" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  Placeholder — add pipeline diagram or character generation samples here.
</div>
