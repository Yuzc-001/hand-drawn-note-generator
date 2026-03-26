# Hand-Drawn Note Generator — Project Definition

## One-line

Turn any content into a visual summary image — hand-drawn sketchnote, infographic, whiteboard diagram, or XHS narrative card. No configuration required.

---

## What this project is actually for

This project should feel like handing your content to a skilled visual thinker who **just gets it** and draws something useful.

Not: "fill out this form to generate a prompt."
Not: "here are 5 style options, which one do you want?"

Real job:

> **Read the content. Understand the intent. Produce a real visual immediately.**

---

## What "real" means

Real means the user gets something they can actually use:
- A generated image (when Gemini / image tools are available)
- A sketch-style SVG with genuine hand-drawn character (when image tools are unavailable)
- A portable prompt that works in Midjourney / FLUX / Ideogram (always)

The user should never leave the interaction with only a text description of what the image would look like.

---

## The two output families this skill covers

### Sketchnote (手绘笔记)
Personal, expressive, notebook-feel visuals. Black ink + accent color. Icons and characters welcome. For XHS Story, WeChat Knowledge, and General content.

### Infographic (信息图)
Structured, hierarchy-clear, diagram-driven visuals. Clean line work, labeled nodes. For Academic and Technical Whiteboard content.

These are not fixed outputs — they are ends of a spectrum. Good content sensing means choosing the right point on this spectrum for each piece of content.

---

## The five audience modes

| Mode | Trigger | Output feel |
|---|---|---|
| XHS Story | 小红书, 情感, 分享 | Warm narrative, characters, flowing |
| Academic | 论文, 学术, 导师 | Clean infographic, restrained |
| WeChat Knowledge | 公众号, 干货, 教程 | Knowledge card, organized, savable |
| Technical Whiteboard | 架构, 流程, 系统 | Whiteboard diagram, precise |
| General | (no signal) | Classic sketchnote, direct |

---

## Interaction philosophy

**Read, don't ask.**

The skill should infer from content signals and generate immediately. It should only ask the user something when the content is genuinely ambiguous between two meaningful interpretations. Even then, it should offer one short line and generate the most likely option immediately, not block on confirmation.

The confirmation pattern is one line:
```
→ [mode]: [style] · [ratio] · [count] · generating...
```

Iteration happens through natural language after the first result.

---

## What "visual distillation" means

v0.3 keeps the v0.2 principle: distill before you draw.

- Identify the one-sentence message
- Find the 3–6 nodes that matter most
- Choose the structure that makes the relationship obvious
- Remove everything that creates visual noise

But v0.3 goes further:
- The distillation is now **mode-aware** (academic distillation ≠ XHS distillation)
- The output is now **always real** (image or SVG, not just a prompt)
- The interaction is now **zero-friction** (infer from signals, generate immediately)

---

## What the project is NOT

- Not a design system
- Not a marketing poster generator
- Not a generic summary tool that ignores visual composition
- Not a prompt template pack that requires the user to understand its parameter system

It is specifically:

> **A visual distillation layer that produces real, usable visual output from any content, adapting to the user's audience and platform without making them configure anything.**

---

## v0.3 success criteria

This project feels real when:
- A user pastes any content and gets a real image within one exchange
- A user who types "小红书风格" gets XHS-appropriate output without further questions
- A user without image generation tools still gets a usable, sketch-style SVG
- A user can iterate with natural language: "more academic", "split into 2", "vertical"
- The outputs look genuinely different across the five modes (not just style-name changes)
