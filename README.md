# hand-drawn-note-generator

**English** | [中文](#中文)

A skill for turning dense content into hand-drawn sketch-note image briefs.

Its job is not just to make things look hand-drawn.
Its job is to make a message visually clear before image generation.

```
Input: raw text, notes, article, explanation, process, comparison
  ↓
Distill message → choose layout → reduce overload → write portable prompt
  ↓
Output: one or more sketch-note image briefs or ready-to-use prompts
```

---

## What this skill is for

This skill helps an agent convert content into a sketch-note style visual summary that is:
- clearer
- lighter
- more structured
- easier to share

The product center is:

# visual distillation

That means the skill should decide:
- what the image is actually trying to say
- what should be removed
- what layout best fits the message
- whether one image is enough
- how to express the result in a portable prompt

---

## What it is not

This project is not:
- a generic infographic engine
- a full design tool
- a style pack for every visual need
- a summary tool that ignores layout judgment

It is specifically:

# a visual-distillation skill for sketch-note and knowledge-sharing visuals

---

## Core capabilities

- distill dense content into 3–6 visual claims per image
- choose layout by message structure
- prevent overloaded images
- produce portable English prompts with Chinese visible text
- keep output usable across image tools instead of coupling to one model
- split content into multiple images when clarity requires it

---

## Typical use cases

- project introduction cards
- concept explanation diagrams
- process/workflow sketch notes
- tutorial step visuals
- comparison visuals
- portfolio/showcase summary boards

---

## How it works

1. identify the real message
2. extract only the highest-value nodes
3. choose layout that matches the relationship
4. cap overload by splitting when needed
5. confirm or choose style family and aspect ratio
6. write the prompt in a portable visual format
7. generate the image if the environment supports image generation

---

## File structure

```text
hand-drawn-note-generator/
├── SKILL.md
├── PROJECT.md
├── CHANGELOG.md
├── VERSION
├── hand-drawn-note-generator.skill
└── references/
    ├── prompt-guide.md
    └── layout-guide.md
```

---

## Current version

- `v0.2.0`

---

## License

MIT

---

# 中文

[English](#hand-drawn-note-generator) | **中文**

一个把密集内容压缩成手绘笔记图简报的技能。

它的重点不只是“画成手绘风格”，
而是：

# 先把内容变清楚，再进入出图

```
输入：原始文字、说明、文章、流程、教程、对比内容
  ↓
提炼主信息 → 选布局 → 控制信息密度 → 编写可迁移 Prompt
  ↓
输出：1 张或多张手绘笔记图简报，或可直接复用的 Prompt
```

---

## 这个技能真正解决什么

它帮助 agent 把内容转成更容易理解、传播、复用的手绘笔记图。

产品中心不是“手绘风格本身”，
而是：

# visual distillation / 视觉蒸馏

也就是先判断：
- 这张图到底要表达什么
- 什么该删掉
- 用哪种布局最合适
- 是否必须拆成多张
- 怎样写成可迁移的 Prompt

---

## 它不是什么

它不是：
- 通用信息图生成器
- 完整设计系统
- 替代设计师的工具
- 只会摘要、不管版式的总结器

它是：

# 面向 sketchnote 的视觉蒸馏技能

---

## 核心能力

- 把密集内容压成每张图 3–6 个高价值视觉节点
- 根据内容关系选择布局
- 主动防止一张图塞太满
- 输出英文 Prompt，图中可见文字用中文
- 不绑定单一模型，尽量保持 Prompt 可迁移
- 当一张图不够清楚时主动拆图

---

## 适合的任务

- 项目介绍图
- 概念解释图
- 流程说明图
- 教程步骤图
- 对比分析图
- 作品/案例回顾图

---

## 当前版本

- `v0.2.0`

---

## 开源协议

MIT

## 开源协议

MIT
流程说明图
- 教程步骤图
- 对比分析图
- 作品/案例回顾图

---

## 当前版本

- `v0.2.0`

---

## 开源协议

MIT

## 开源协议

MIT
