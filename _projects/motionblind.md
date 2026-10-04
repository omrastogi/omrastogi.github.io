---
layout: page
title: MotionBlind
description: Contrastive minimal-pairs benchmark showing that Video-LLMs fail to read the speed, magnitude, and direction of motion
img: assets/img/publication_preview/motionblind.png
github: https://github.com/ostadabbas/MotionBlind
importance: 1.5
category: research
---

**MotionBlind: Probing the Illusion of Motion Understanding in Video-LLMs** is a benchmark from the Augmented Cognition Lab, Northeastern University, under review at the NeurIPS 2026 Workshop on World Models in Physical AI.

## Abstract

A video large language model can watch two clips of the same person in the same room and name every object in both, yet fail to tell you which one moves faster, which way a hand travels, or how hard a door is shut. That gap matters because Video-LLMs are increasingly the perceptual front end of world models: auto-labeling state transitions, acting as reward and success detectors for model-based RL, grounding instructions in what an agent sees. Each of those roles presupposes a competence at reading motion that, we show, these models do not have. MotionBlind is a contrastive, minimal-pairs benchmark of self-recorded clip pairs that are near-identical except in motion, each paired with two complementary yes/no questions, so a model must answer all four items correctly (Instance Accuracy, I_Acc) to score the instance. Single-frame, appearance and language-only shortcuts all collapse toward the 6.25% chance floor. It complements TimeBlind with physically grounded categories (speed, magnitude, direction) that are hard to source and label from uncontrolled internet video but are precisely the variables a world model must predict. Across two suites we run a controlled study of six open Video-LLMs and two frontier models over frame budgets 1-24 and four frame-selection strategies. Open models sit near the chance floor; a larger model does no better; and neither more frames nor dynamic selection, which changes which frames are seen and not whether motion is read, closes the gap. The task genuinely needs video in the right order: removing it zeroes every model, and shuffling frames collapses accuracy to chance. Only Gemini 3.1 Pro clears the benchmark overall, yet it too fails on the purely rate-defined categories.

{% include figure.liquid loading="eager" path="assets/img/publication_preview/motionblind.png" title="MotionBlind minimal-pair example" class="img-fluid rounded z-depth-1" %}

<div class="caption">
  A MotionBlind instance: the same room, person, and objects, with only the direction of motion changed. A model must answer all four yes/no items correctly to score the instance.
</div>

## Links

- **Website:** [ostadabbas.github.io/motionblind.github.io](https://ostadabbas.github.io/motionblind.github.io/)
- **Code:** [github.com/ostadabbas/MotionBlind](https://github.com/ostadabbas/MotionBlind)
<!-- TODO: add the paper link (arXiv or OpenReview) once public. -->

## My role

Co-author (7th of 10 authors), Augmented Cognition Lab, Northeastern University, advised by Prof. Sarah Ostadabbas.

<!-- TODO: describe my specific contribution to MotionBlind (not found in the repo). -->

**Authors:** Dhairya Bhatia, Bishoy Galoaa, Oliver Fritsche, Shahid Kamal, Muhammad Obaidullah Abdul Salam, Umer Saleem, Om Rastogi, Frania Felix Chettiar, Nesli Erdoğmuş, Sarah Ostadabbas
