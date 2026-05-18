# Hermes 英语陪练

[English version →](README_en.md)

一个基于 AI 的英语对话陪练 Skill，专为 [Hermes Agent](https://hermes-agent.nousresearch.com) 设计。

## 功能概述

把 Hermes 变成一个耐心、地道的英语陪练伙伴。通过自然重述纠错，根据你的水平动态调整难度（i+1 原则），在对话中无感地复习你常犯的语法问题和近期接触的生词。

## 核心特性

- **自然纠错** — 在对话中通过示范正确说法来纠错，不打断节奏
- **记忆模型** — 词汇和语法像记忆一样管理：高频的留在窗口里被反复复习，已内化的自然淘汰
- **自适应难度** — 句子复杂度始终略高于你当前水平，优先复用近期常用词
- **语音合成** — 所有英文回复自带语音（Edge TTS），每段 2-3 句自然断句
- **语法问题追踪** — 识别高频语法错误和非词汇类语言问题，按出现频率排序

## 安装配置

1. 将本 Skill 复制到 `~/.hermes/skills/creative/english-learning/`
2. `user_level.md` 会自动生成和更新，无需手动创建
3. 确保 Edge TTS 已在 Hermes 配置中启用

## `user_level.md` 学习档案

这是一个英语记忆文件，由 AI 动态维护，用户无需编辑。

```yaml
---
estimated_cefr: ""
estimated_vocabulary: ""
last_updated: ""
---

# 英语水平档案

## 水平概述
（AI 自动评估）

## 近期词汇
- word1
- word2

## 语法问题记录
- 问题描述
```

硬上限 2000 字符。词汇区优先淘汰生僻/低频词，语法区按出现频率排序，低频的自然垫底。

## 使用方式

说 **「英语模式」** 或 **「English mode」** 激活，说 **「退出英语模式」** 退出。
