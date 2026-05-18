# Hermes English Learning

[中文版本 →](README.md)

An AI-powered English conversation companion skill for [Hermes Agent](https://hermes-agent.nousresearch.com).

## What it does

Turns Hermes into a patient, native-level English practice partner. It corrects grammar through natural recasts, adapts difficulty to your level (i+1), and seamlessly weaves your common grammar issues and recent vocabulary into conversation for effortless review.

## Features

- **Natural Recast** — corrects mistakes by modeling the right form, never interrupting the flow
- **Memory Model** — vocabulary and grammar managed like memory: high-frequency items stay in the review window, internalized ones fade out naturally
- **Adaptive Difficulty** — keeps sentences slightly above your current level, prioritizing commonly used words from your recent list
- **TTS Integration** — all English output includes voice (Edge TTS), 2–3 sentences per segment with natural breaks
- **Grammar Issue Tracking** — identifies high-frequency grammar errors and non-vocabulary language problems, sorted by occurrence frequency

## Setup

1. Copy this skill into `~/.hermes/skills/creative/english-learning/`
2. `user_level.md` is auto-generated and maintained by the AI — no manual setup needed
3. Make sure Edge TTS is configured in Hermes

## `user_level.md` Profile

An English memory file maintained dynamically by the AI. Users don't need to edit it.

```yaml
---
estimated_cefr: ""
estimated_vocabulary: ""
last_updated: ""
---

# English Level Profile

## Level Overview
(AI auto-assessed)

## Recent Vocabulary
- word1
- word2

## Grammar Issues
- issue description
```

Hard cap: 2000 characters. Rare words are evicted first from the vocabulary section; grammar issues are sorted by frequency, low-frequency ones naturally sink to the bottom.

## Usage

Say **"English mode"** to activate, **"退出英语模式"** to exit.
