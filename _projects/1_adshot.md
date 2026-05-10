---
layout: page
title: AdShot
description: MLLM benchmark for advertisement video clipping — evaluating temporal reasoning at production scale
img: assets/img/projects/adshot/thumb.jpg
importance: 1
category: research
---

**AdShot** is a benchmark for evaluating Multimodal Large Language Models on advertisement video clipping — the task of shortening a 30-second ad to a 15-second cut while preserving brand messaging and narrative coherence.

## Overview

- **823 video pairs** across **194 brands**, sourced from real advertisement archives
- Models evaluated: Qwen-Omni, MiniCPM-o, Aria
- Covers diverse ad formats: product demos, narrative arcs, celebrity endorsements

## Contributions

- Built the **inference pipeline** for MLLM video clipping evaluation, handling multi-modal inputs and temporal window selection
- Designed the **evaluation harness** with automated scoring across temporal coherence, brand retention, and narrative quality metrics
- Built **AdNotator**, a human annotation system used to construct ground-truth clipping decisions for the benchmark

## Status

Under review at **IJCAI 2026**.

**Venue:** Augmented Cognition Lab, Northeastern University
**Advisor:** Prof. Sarah Ostadabbas

## Stack

Python · PyTorch · Qwen-Omni · MiniCPM-o · Aria · SLURM (Northeastern Discovery cluster)

{% include figure.liquid loading="eager" path="assets/img/projects/adshot/thumb.jpg" title="AdShot benchmark overview" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  Placeholder — add benchmark overview figure here.
</div>
