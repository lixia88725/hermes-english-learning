# Hermes English Learning / Hermes 英语陪练

An AI-powered English conversation companion skill for [Hermes Agent](https://hermes-agent.nousresearch.com).

一个基于 AI 的英语对话陪练 Skill，专为 [Hermes Agent](https://hermes-agent.nousresearch.com) 设计。

## What it does / 功能概述

Turns Hermes into a patient, native-level English practice partner. It corrects grammar through natural recasts (not lectures), tracks your vocabulary growth, and adapts difficulty to your CEFR level using i+1 progression.

把 Hermes 变成一个耐心、地道的英语陪练伙伴。通过自然重述（而非说教）纠正语法、追踪词汇增长、根据你的 CEFR 水平动态调整对话难度（i+1 原则）。

## Features / 核心特性

- **Natural Recast / 自然纠错** — corrects mistakes by modeling the right form in conversation / 在对话中通过示范正确说法来纠错
- **Vocabulary Tracking / 词汇追踪** — monitors which words you're learning and when they're mastered / 追踪学习中的词汇，记录从「初接触」到「已掌握」的完整过程
- **Adaptive Difficulty / 自适应难度** — keeps sentences slightly above your current level / 句子复杂度始终略高于你当前水平
- **TTS Integration / 语音合成** — all English output includes voice (Edge TTS) / 所有英文回复自带语音
- **Grammar Blind Spot Detection / 语法盲区检测** — identifies recurring error patterns / 识别反复出现的语法错误模式

## Setup / 安装配置

1. Copy this skill into `~/.hermes/skills/creative/english-learning/` / 将本 Skill 复制到上述路径
2. Create your own `user_level.md` (see template below) / 创建你自己的学习档案（模板见下方）
3. Make sure Edge TTS is configured in `~/.hermes/config.yaml` / 确保 Edge TTS 已在 Hermes 配置中启用

## `user_level.md` Template / 学习档案模板

```yaml
---
estimated_cefr: ""    # Leave empty — the skill auto-estimates after ~10 rounds
                      # 留空即可，约 10 轮对话后自动评估
estimated_vocabulary: ""
last_updated: ""
---

# English Level Profile / 英语水平档案

## Vocabulary Tracking / 词汇追踪

| Word / 词汇 | Status / 状态 | First Contact / 首次接触 | Last Activity / 最近活动 |
|-------------|---------------|-------------------------|-------------------------|
|             |               |                         |                         |

## Grammar Blind Spots / 语法盲区

| Grammar Point / 语法点 | Status / 状态 | First Found / 首次发现 | Last Activity / 最近活动 | Typical Error / 典型错误 |
|------------------------|---------------|----------------------|-------------------------|------------------------|
|                        |               |                      |                         |                        |

## Update Log / 更新日志

-
```

## Usage / 使用方式

Say **"English mode"** to activate, **"退出英语模式"** to exit. The skill handles the rest.

说 **「English mode」** 或 **「英语模式」** 激活，说 **「退出英语模式」** 退出。剩下的交给 Skill。
