---
layout: page
title: AdSelect
description: Fine-tuning multimodal LLMs for advertisement shot selection — a set-prediction approach to editing ads like professionals
img: assets/img/projects/adselect/adcraft_loss.svg
importance: 0
category: research
---

**AdSelect** frames advertisement editing as a **set-prediction problem** — mapping shots from a focal (long) video to the subset retained in the target (short) edit. We introduce a large-scale paired dataset and **AdCraft**, a fine-tuning method that fixes the over-selection failures of zero-shot MLLMs by combining LoRA with explicit complement-shot supervision.

- **~4,800 long–short ad pairs** (4,000 train / 800 benchmark), mined from ~4M YouTube videos across **17 industries**
- **AdCraft** (LoRA + complement-set objective on Qwen3-VL-8B) reaches **0.771 precision** and **0.688 IoU**
- Key finding: in zero-shot MLLMs, **selection is not understanding**

Full paper and interactive results: [**adselect.github.io**](https://omrastogi.github.io/adselect.github.io/)

{% include figure.liquid loading="eager" path="assets/img/projects/adselect/adcraft_loss.svg" title="AdCraft training method" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  AdCraft, trained with the complement-set objective, tracks the editor's ground-truth keep set on an example ad.
</div>

{% include figure.liquid loading="eager" path="assets/img/projects/adselect/results.png" title="Precision vs IoU on the AdSelect benchmark" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  <strong>Selection is not understanding.</strong> On the 800-pair benchmark, zero-shot, frontier, and training-free models sit inside or below a simple heuristic band on precision and IoU. AdCraft (ours) is the only method that clears the floor on both.
</div>

## Status

Under review at **AAAI 2027**.

Companion benchmark: [**AdShot**]({{ '/projects/1_adshot/' | relative_url }}) — the MLLM ad-clipping benchmark this method builds on.

## Stack

Python · PyTorch · Qwen3-VL · LoRA · complement-set supervision
