---
layout: page
title: GVHMR Multi-Person Extension
description: Extending global-frame human motion recovery to multi-person scenes for IARPA MOVES
img: assets/img/projects/gvhmr/thumb.jpg
importance: 4
category: research
---

**GVHMR** (Global-frame Video Human Mesh Recovery) is extended here to handle **multi-person scenarios**, enabling simultaneous recovery of multiple individuals' full-body SMPL meshes in a consistent global reference frame.

## Motivation

The original GVHMR handles single-person scenes. Real-world surveillance and activity analysis (e.g., IARPA MOVES) require tracking and recovering mesh poses for multiple people simultaneously, with scene-consistent global coordinates.

## Technical Approach

- **Scene detection**: identify scene cuts and transitions to avoid cross-clip motion contamination
- **Visual Odometry patching**: stabilize global frame estimates across frames with significant camera motion
- **SMPL mesh overlay rendering**: render multi-person SMPL meshes onto video with consistent world-frame coordinates
- **YOLO tracking**: integrate YOLO-based multi-person detection and temporal ID assignment to handle occlusions and entries/exits

## Compute

Experiments run on the **Northeastern Discovery HPC cluster** using SLURM job scheduling.

## Context

Supporting an **IARPA MOVES pre-proposal** at the Augmented Cognition Lab, Northeastern University, advised by Prof. Sarah Ostadabbas.

## Stack

Python · PyTorch · GVHMR · SMPL · YOLO · Visual Odometry · SLURM

{% include figure.liquid loading="eager" path="assets/img/projects/gvhmr/thumb.jpg" title="Multi-person SMPL mesh overlay" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  Placeholder — add multi-person mesh overlay visualization here.
</div>
