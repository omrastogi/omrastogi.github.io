---
layout: page
title: AdShot
description: MLLM benchmark for advertisement video clipping — evaluating temporal reasoning at production scale
img: assets/img/projects/adshot/method.png
importance: 1
category: research
---

## Abstract

AdShot is a benchmark for evaluating multimodal large language models on advertisement video clipping, the task of shortening a 30-second ad to a 15-second cut while preserving brand messaging and narrative coherence. It comprises 823 video pairs across 194 brands sourced from real advertisement archives, with an automated evaluation harness scoring temporal coherence, brand retention, and narrative quality across models including Qwen-Omni, MiniCPM-o, and Aria.

## Overview

- **823 video pairs** across **194 brands**, sourced from real advertisement archives
- Models evaluated: Qwen-Omni, MiniCPM-o, Aria
- Covers diverse ad formats: product demos, narrative arcs, celebrity endorsements

## My role

Second author (Wen Xie, Om Rastogi, Sai Siddhartha Vivek Dhir Rangoju, Gijs Overgoor, Yakov Bart, Sarah Ostadabbas). My contributions:

- Built the **inference pipeline** for MLLM video clipping evaluation, handling multi-modal inputs and temporal window selection
- Designed the **evaluation harness** with automated scoring across temporal coherence, brand retention, and narrative quality metrics
- Built **AdNotator**, a human annotation system used to construct ground-truth clipping decisions for the benchmark

## Links

<!-- TODO: add paper (OpenReview or arXiv), code, and website links once public. -->

The paper is listed on the [publications]({{ '/publications/' | relative_url }}) page.

## Status

Accepted at **NeurIPS 2026** (Datasets & Benchmarks Track).

**Venue:** Augmented Cognition Lab, Northeastern University
**Advisor:** Prof. Sarah Ostadabbas

## Stack

Python · PyTorch · Qwen-Omni · MiniCPM-o · Aria · SLURM (Northeastern Discovery cluster)

{% include figure.liquid loading="eager" path="assets/img/projects/adshot/method.png" title="AdShot evaluation pipeline" class="img-fluid rounded z-depth-1" %}

<div class="caption">
  AdShot inference and evaluation pipeline for MLLM video clipping.
</div>

{% include figure.liquid loading="eager" path="assets/img/projects/adshot/table.png" title="AdShot benchmark results" class="img-fluid rounded z-depth-1" %}

<div class="caption">
  Benchmark results across evaluated MLLMs.
</div>
