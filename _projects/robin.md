---
layout: page
title: Robin
description: Voice assistant for a post-operative care study — "Hey Robin" on an Android tablet, a Parakeet → LLM → Kokoro cascade on a self-hosted GPU server, joined by one WebSocket
img: assets/img/projects/robin/thumb.jpg
importance: 2
category: research
---

**Robin** is the voice assistant for the RECOVER post-operative study at Northeastern's [PARCS Lab](https://parcslab.fyi/). It runs on a Samsung Galaxy Tab A9+ in a patient's home: say "Hey Robin", ask a question or set a timer, and it answers in its own voice. The server can also open a turn on its own — a medication reminder, a fridge door left open — which the tablet speaks aloud and renders as a reminder card.

<div class="row justify-content-center">
    <div class="col-md-8">
        {% include video.liquid path="assets/img/projects/robin/theme.mp4" class="img-fluid rounded z-depth-1" width="100%" muted=true loop=true autoplay=true %}
    </div>
</div>
<div class="caption">
  The tablet surface: a pond whose palette follows the time of day, active timers top-left, and Robin the jellyfish, who animates while listening and speaking.
</div>

## Architecture

Three tiers, drawn as edge → server → LLM:

- **Tablet (edge)** — an always-on **openWakeWord** detector listens for "Hey Robin" behind the hardware echo canceller. A detection arms a turn and 16 kHz PCM streams up over a WebSocket only while the turn is open; the detector keeps running during Robin's reply, which is how barge-in works. Timers and alarms ring locally on the device.
- **Server (FastAPI · GPU)** — the cascade. **Silero VAD** decides end-of-utterance, with hysteresis, onset debounce, a pre-speech ring buffer so first syllables aren't clipped, and a hangover tuned against post-op patients who pause mid-sentence. Then **Parakeet TDT 0.6B v3** speech-to-text → LLM → **Kokoro-82M** text-to-speech, streamed back down the same socket as one 24 kHz WAV per sentence. Barge-in cancels the in-flight reply. Profiles (voice, rate, context) and turn history persist in Postgres. Every turn is instrumented from turn-start to first TTS frame.
- **LLM (remote)** — an OpenAI-compatible chat call to the lab's Gemma gateway (gemma4:12b) or GPT-4o-mini. The Robin persona is a port of the RECOVER Alexa skill's conversation logic: a health-support prompt with hard safety rails — never diagnoses or prescribes, routes emergencies out, defers to a clinician when unsure.

## Wake word

The "Hey Robin" head is custom-trained on openWakeWord: a ~200k-parameter classifier over a frozen Google speech-embedding backbone, fed a 1.28 s window.

- **Training data** — 440k synthetic positives (piper-sample-generator over LibriTTS-R and en-GB VCTK speakers) against ~2,000 h of ACAV100M negatives, split by speaker and acoustic condition.
- **Two benchmarks disagreed.** Held-out synthetic speech ranked v1 first (AUC 0.96); ~100 real clips from 10 speakers, scored through the production streaming path with hard negatives like "hey rabbit" and "hey jarvis", ranked it last (recall 0.32). The synthetic eval was measuring fit to the TTS generator.
- **Shipped v3** — real-voice AUC 0.954, precision 0.92, recall 0.68. A speaker-level bootstrap puts P(v3 > v1) at 0.998.
- **Per-user adaptation** — a rank-4 LoRA on the head, trained on 82 clips from one speaker, lifts that speaker's recall from 0.68 to 0.83 and exports as a 205 KB drop-in.

## Contributions

- Built the full system: the server cascade, the tablet app, and the WebSocket protocol between them
- Trained and benchmarked the "Hey Robin" wake word, including the real-voice benchmark that overturned the synthetic ranking
- Tuned VAD end-of-utterance against real post-op patients and instrumented per-turn latency
- Ported the RECOVER Alexa conversation logic into a transport-agnostic persona with safety rails

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
  Left: a server-opened proactive turn — "the fridge door is left open" — followed by a spoken exchange. Right: a live conversation — small talk, a weather question, a two-minute timer. Unmute for audio.
</div>

## Status

Ongoing at PARCS Lab. Shipped: wake word, echo cancellation, barge-in, timers and alarms, proactive reminders. Next: streaming partial transcripts on the tablet path.

**Venue:** [PARCS Lab](https://parcslab.fyi/), Northeastern University

## Stack

Python · FastAPI · NeMo Parakeet · Kokoro · Silero VAD · openWakeWord · onnxruntime · Postgres · React Native · WSL2 / CUDA
