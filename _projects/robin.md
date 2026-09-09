---
layout: page
title: Robin
description: Home voice assistant — a streaming speech pipeline (VAD → STT → LLM → TTS) on a self-hosted server, driving an Android tablet companion over WebRTC
img: assets/img/projects/robin/thumb.jpg
importance: 2
category: research
---

**Robin** is a voice assistant for the home. It lives on an Android tablet: say "Hey Robin", ask for the weather or set a timer, and it talks back. It also surfaces events in the home — like a fridge door left open — as spoken and on-screen alerts.

<div class="row justify-content-center">
    <div class="col-md-8">
        {% include video.liquid path="assets/img/projects/robin/theme.mp4" class="img-fluid rounded z-depth-1" width="100%" muted=true loop=true autoplay=true %}
    </div>
</div>
<div class="caption">
  The tablet UI: an ambient aquarium with active timers at the top, the "Hey Robin" wake prompt, and the jellyfish that animates while Robin listens and speaks.
</div>

## Architecture

Two systems joined by WebRTC, using Pipecat's RTVI protocol:

- **Tablet (edge)** — captures mic audio, runs voice-activity detection and wake-word spotting on device, streams speech up, plays synthesized speech down, and renders the conversation UI.
- **Server** — [Pipecat](https://github.com/pipecat-ai/pipecat) orchestrates the streaming loop: server-side VAD and end-of-utterance detection, speech-to-text (**NVIDIA Parakeet TDT 0.6B**), the LLM, and text-to-speech (**Kokoro-82M**), with barge-in so the user can interrupt Robin mid-sentence. The cascade is built on NVIDIA's Nemotron Voice Agent Blueprint.
- **Transport** — one bidirectional Opus media track (mic up, TTS down) plus a data channel for control events: transcripts, bot-started/stopped-speaking, and interruption signals.

## Contributions

- Built the full system: the server-side cascade pipeline, the Android tablet app, and the WebRTC/RTVI integration between them
- Designed the always-listening edge path — VAD → keyword spotting → stream — so the server only receives speech meant for Robin
- Evaluated STT candidates (Parakeet, Canary-Qwen, Whisper Large v3, Qwen3-ASR, Kyutai) and TTS candidates (Kokoro, Chatterbox-Turbo, Piper, Dia2, Fish Audio) for the cascade

## Demo

<div class="row align-items-center justify-content-center">
    <div class="col-md-4 mt-3 mt-md-0">
        {% include video.liquid path="assets/img/projects/robin/demo1.mp4" class="rounded z-depth-1" width="100%" controls=true muted=true autoplay=true %}
    </div>
    <div class="col-md-8 mt-3 mt-md-0">
        {% include video.liquid path="assets/img/projects/robin/demo2.mp4" class="rounded z-depth-1" width="100%" controls=true muted=true autoplay=true %}
    </div>
</div>
<div class="caption">
  Left: a fridge door left open triggers an alert on the tablet, followed by a spoken exchange. Right: a live conversation — small talk, a weather query, and setting a two-minute timer. Unmute for audio.
</div>

## Status

Ongoing at PARCS Lab. In progress: on-device "Hey Robin" wake word (OpenWakeWord / sherpa-onnx), edge VAD gating, and acoustic echo cancellation.

**Venue:** [PARCS Lab](https://parcslab.fyi/), Northeastern University

## Stack

Python · Pipecat · NVIDIA Nemotron Voice Agent Blueprint · Parakeet TDT · Kokoro · Silero VAD · sherpa-onnx · WebRTC / RTVI · Android
