# hand-drawn-note-generator

**English** | [中文](#中文)

Turn any content into a visual summary image — immediately, without configuration.

```
Input: article / notes / paper / process / concept / story
  ↓
Read signals → detect mode → build prompt → generate
  ↓
Output: real image (Gemini) or sketch SVG (fallback) + portable prompt
```

---

## What this skill does

It reads your content, picks the right visual form for it, and generates something real.

No style menus. No parameter forms. No waiting for confirmation.

The five output modes:

| Content type | Mode | Output feel |
|---|---|---|
| Personal story, XHS, emotional | **XHS Story** | Warm narrative, characters, flowing |
| Research, paper, academic concept | **Academic** | Clean infographic, structured |
| Tutorial, tips, "干货", WeChat | **WeChat Knowledge** | Knowledge card, organized, savable |
| Architecture, pipeline, code flow | **Technical Whiteboard** | Precise whiteboard diagram |
| Anything else | **General** | Classic hand-drawn sketchnote |

---

## Output options

| Environment | What you get |
|---|---|
| Gemini / image generation available | Real generated image + portable prompt |
| No image generation | Sketch-style SVG (hand-drawn feel) + portable prompt |
| You say "只给我 prompt" | Portable prompt only |

You always get a portable English prompt that works in Midjourney, FLUX, and Ideogram.

---

## How to use

**Simplest**: just paste your content. The skill reads it and generates.

**With a hint**: add a word about where the output goes:
- "做成小红书的" → XHS warm narrative style
- "给导师看的分析图" → Academic infographic
- "公众号干货图" → WeChat knowledge card
- "技术架构图" → Technical whiteboard
- "给我 SVG" → SVG output even if image tools are available
- "只要 prompt" → Output prompt only

**Iteration**: after you see the first result, use natural language:
- "更学术" / "更小红书" / "分成两张" / "竖版" / "字少点"

---

## File structure

```
hand-drawn-note-generator/
├── SKILL.md                          # Main skill — read this first
├── PROJECT.md                        # Product vision and principles
├── CHANGELOG.md                      # Version history
├── VERSION                           # Current: v0.3.0
└── references/
    ├── content-signals.md            # Signal → mode detection table
    ├── audience-modes.md             # 5 mode profiles (style, ratio, density)
    ├── layout-guide.md               # Layout by relationship type
    ├── style-options.md              # Style presets per mode
    ├── prompt-guide.md               # How to write image prompts (prose-style)
    ├── svg-guide.md                  # How to generate sketch-style SVG
    └── output-paths.md               # Image / SVG / Prompt-only decision logic
```

---

## Current version

`v0.3.0` — Full redesign: zero-friction interaction, 5 audience modes, SVG fallback, Gemini-optimized prompting.

[Changelog](CHANGELOG.md)

---

## License

MIT

---

# 中文

[English](#hand-drawn-note-generator) | **中文**

把任何内容变成视觉摘要图——不需要配置，直接生成。

```
输入：文章 / 笔记 / 论文 / 流程 / 概念 / 故事
  ↓
读取信号 → 判断模式 → 构建 Prompt → 生成
  ↓
输出：真实图片（Gemini）或草图 SVG（备选）+ 可移植 Prompt
```

---

## 这个 skill 做什么

它读懂你的内容，自动选择合适的视觉形式，直接生成真实的图。

不需要选择风格，不需要填写参数，不需要等确认。

五种输出模式：

| 内容类型 | 模式 | 视觉感受 |
|---|---|---|
| 个人故事、小红书、情感内容 | **XHS 叙事** | 温暖手绘，有人物，流动感 |
| 学术论文、研究框架、复杂概念 | **学术信息图** | 干净结构，清线，有层级 |
| 干货教程、公众号内容、Tips | **知识卡片** | 有组织，可收藏，清晰分区 |
| 架构、流程、技术系统 | **白板技术图** | 黑线箭头，精准标注 |
| 其他 / 无明确信号 | **通用手绘** | 经典 sketchnote，直接生成 |

---

## 输出选项

| 环境 | 你得到什么 |
|---|---|
| 有图像生成能力（如 Gemini）| 真实图片 + 可移植 Prompt |
| 无图像生成能力 | 草图风 SVG（手绘感）+ 可移植 Prompt |
| 你说"只给我 prompt" | 仅输出 Prompt |

每次都输出可以在 Midjourney / FLUX / Ideogram 里直接用的英文 Prompt。

---

## 使用方式

**最简单**：直接粘贴内容，skill 自动读取并生成。

**加一个提示词**：
- "做成小红书的" → XHS 温暖叙事风
- "给导师看的分析图" → 学术信息图
- "公众号干货图" → 知识卡片风
- "技术架构图" → 白板技术图
- "给我 SVG" → 输出 SVG
- "只要 prompt" → 仅输出 Prompt

**迭代**：看到第一张图之后，用自然语言说：
- "更学术" / "更小红书" / "分成两张" / "竖版" / "字少点"

---

## 当前版本

`v0.3.0` — 全面重设计：零摩擦交互、5 种受众模式、SVG 备选路径、Gemini 优化 Prompt。

[更新日志](CHANGELOG.md)

---

## 开源协议

MIT
