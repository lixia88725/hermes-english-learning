# Hermes English Learning

[中文版本 →](README_zh.md)

An AI-powered English conversation companion skill for [Hermes Agent](https://hermes-agent.nousresearch.com).

## What it does

Turns Hermes into a patient, native-level English practice partner. It corrects grammar through natural recasts (not lectures), tracks your vocabulary growth, and adapts difficulty to your CEFR level using i+1 progression.

## Features

- **Natural Recast** — corrects mistakes by modeling the right form in conversation
- **Vocabulary Tracking** — monitors which words you're learning and when they're mastered
- **Adaptive Difficulty** — keeps sentences slightly above your current level
- **TTS Integration** — all English output includes voice (Edge TTS)
- **Grammar Blind Spot Detection** — identifies recurring error patterns

## Setup

1. Copy this skill into `~/.hermes/skills/creative/english-learning/`
2. Create your own `user_level.md` (see template below)
3. Make sure Edge TTS is configured in `~/.hermes/config.yaml`

## `user_level.md` Template

```yaml
---
estimated_cefr: ""    # Leave empty — the skill auto-estimates after ~10 rounds
estimated_vocabulary: ""
last_updated: ""
---

# English Level Profile

## Vocabulary Tracking

| Word | Status | First Contact | Last Activity |
|------|--------|---------------|---------------|
|      |        |               |               |

## Grammar Blind Spots

| Grammar Point | Status | First Found | Last Activity | Typical Error |
|---------------|--------|-------------|---------------|---------------|
|               |        |             |               |               |

## Update Log

-
```

## Usage

Say **"English mode"** to activate, **"退出英语模式"** to exit. The skill handles the rest.
