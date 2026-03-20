# hand-drawn-note-generator

**English** | [中文](#中文)

A skill that transforms any content — project introductions, concept explanations, process diagrams, tutorials, comparisons — into clean hand-drawn sketch-note style images.

```
Input: raw text, article, outline, bullet points
  ↓
Extract key points → Choose layout → Write prompt → Generate image
  ↓
Output: 4:3 sketch-note, white background, black ink, color accents
```

---

## Features

- Distills complex content into a clear, shareable visual summary
- Supports 6 content types: project intro, concept explanation, process flow, tutorial steps, comparison, portfolio review
- Provides 6 layout templates: problem→solution, radial, linear flow, step cards, left-right comparison, grid showcase
- Auto-selects layout via keyword signals (e.g. "vs" → comparison, "steps" → linear flow)
- Enforces hand-drawn sketch-note style: white background, black ink, red/green/blue/yellow accents
- Supports stick figure characters and speech bubbles for a lively, expressive feel
- **Outputs the full English prompt in the conversation** — copy it to Midjourney, FLUX, Ideogram, or share with prompt engineers
- Maintains visual consistency across multi-image series
- Splits into 1–3 images automatically based on content density
- Works without a specific model — uses the best available image generation tool in the environment

---

## Installation

This is a general-purpose AI agent skill. It works with any agent platform that supports a `SKILL.md` convention (e.g. Claude Code, OpenClaw, Cursor, or any agent that reads skill files).

**Option A — Copy the folder**

Copy the `hand-drawn-note-generator/` folder into your agent's skills directory:

```bash
# Claude Code default
~/.claude/skills/hand-drawn-note-generator/

# Or wherever your agent loads skills from
```

**Option B — Use the packaged file**

```bash
# Place hand-drawn-note-generator.skill in your skills directory
# Your agent will load it automatically on next session
```

**Option C — Paste directly**

Copy the contents of `SKILL.md` into your agent's system prompt or custom instructions.

---

## Usage

Trigger the skill naturally in conversation:

```
帮我把这个项目做成手绘笔记图
将以下内容画成 sketchnote
生成一张手绘风格的流程说明图
visualize this as a sketch note
```

The skill will:
1. Extract key points and confirm with you
2. Select the best layout for your content type
3. Write a detailed English prompt with Chinese text
4. Generate the image (if `imageGenerate` is available) or deliver a ready-to-use prompt

---

## File Structure

```
hand-drawn-note-generator/
├── SKILL.md                        # Core skill — workflow and response rules
├── hand-drawn-note-generator.skill # Packaged distributable
└── references/
    ├── prompt-guide.md             # Prompt skeleton, style rules, color conventions, 6 task patterns
    └── layout-guide.md             # 8 layout types, ASCII diagrams, composition principles
```

---

## Output Style

| Property | Value |
|----------|-------|
| Aspect ratio | 4:3 |
| Background | Pure white |
| Primary lines | Black ink |
| Accents | Red / Green / Blue / Yellow |
| Visible text | Chinese (handwritten style) |
| Prompt language | English |
| Key points per image | 3–6 |

---

## License

MIT

---

---

# 中文

[English](#hand-drawn-note-generator) | **中文**

一个 Claude 技能，将项目介绍、概念说明、流程图、教程、对比分析、作品回顾等内容转化为手绘笔记风格图片。

```
输入：原始文字、文章、大纲、要点
  ↓
提炼关键信息 → 选择布局 → 编写 Prompt → 生成图片
  ↓
输出：4:3 手绘笔记图，纯白背景，黑线主色，彩色重点强调
```

---

## 功能

- 将复杂内容压缩为一眼能懂的可分享视觉摘要
- 支持 6 种内容类型：项目介绍、概念解释、流程说明、教程步骤、对比分析、作品回顾
- 提供 6 种布局模板：问题→方案、中心辐射、线性流程、步骤卡片、左右对比、网格展示
- 信号词自动识别布局（如"vs/对比"→左右对比，"步骤/流程"→线性流程）
- 严格遵循手绘笔记风格：纯白背景、黑线为主、红/绿/蓝/黄彩色点缀
- 支持手绘小人（stick figure）和对话气泡，让图更生动有表达力
- **对话中直接展示完整英文 Prompt** —— 可复制给 Midjourney、FLUX、Ideogram 等工具，或发给提示词工程师优化
- 多张图自动保持视觉风格一致性
- 根据内容密度自动拆分为 1–3 张图
- 不依赖特定模型，自动使用当前环境中最优的图像生成工具

---

## 安装

这是一个**通用 AI Agent Skill**，兼容任何支持 `SKILL.md` 约定的 Agent 平台（如 Claude Code、OpenClaw、Cursor 或其他能读取 skill 文件的 Agent）。

**方式 A — 复制文件夹**

将 `hand-drawn-note-generator/` 文件夹复制到你的 Agent 技能目录：

```bash
# Claude Code 默认位置
~/.claude/skills/hand-drawn-note-generator/

# 或你的 Agent 加载 skill 的任意路径
```

**方式 B — 使用打包文件**

```bash
# 将 hand-drawn-note-generator.skill 放入技能目录
# Agent 下次启动时自动加载
```

**方式 C — 直接粘贴**

将 `SKILL.md` 的内容复制到你的 Agent 系统提示词或自定义指令中即可使用。

---

## 使用方式

在对话中自然触发：

```
帮我把这个项目做成手绘笔记图
将以下内容画成 sketchnote
生成一张手绘风格的流程说明图
visualize this as a sketch note
```

技能会：
1. 提炼关键信息并与你确认
2. 根据内容类型选择最合适的布局
3. 编写含中文可见文字的英文 Prompt
4. 生成图片（如果环境支持 `imageGenerate`），或直接交付可用 Prompt

---

## 文件结构

```
hand-drawn-note-generator/
├── SKILL.md                        # 核心技能文件 — 工作流与响应规则
├── hand-drawn-note-generator.skill # 打包好的可分发文件
└── references/
    ├── prompt-guide.md             # Prompt 骨架、风格规则、颜色约定、6 种任务模式
    └── layout-guide.md             # 8 种布局类型、ASCII 结构图、版式原则
```

---

## 输出规格

| 属性 | 值 |
|------|----|
| 画面比例 | 4:3 |
| 背景 | 纯白色 |
| 主线条 | 黑色油墨 |
| 强调色 | 红 / 绿 / 蓝 / 黄 |
| 可见文字 | 中文（手写风格） |
| Prompt 语言 | 英文 |
| 每张图关键点 | 3–6 个 |

---

## 开源协议

MIT
