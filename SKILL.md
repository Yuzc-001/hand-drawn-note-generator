---
name: hand-drawn-note-generator
version: 0.3.0
description: >
  Turn any content into a visual summary image. Supports hand-drawn sketchnotes,
  infographics, whiteboard diagrams, and XHS-style narrative visuals.
  Outputs real images (Gemini), sketch SVG (fallback), and portable prompts.
  No configuration required. Reads content signals and generates immediately.
  Use when the user wants content turned into any kind of visual knowledge image.
---

# Hand-Drawn Note Generator

## Philosophy: Read, Don't Ask

The core rule is:

> **Infer from content and request signals. Generate immediately. Let the user iterate with natural language.**

Never make the user fill out a form before seeing a result.
Never ask about style, ratio, or layout unless the content is genuinely ambiguous between two useful interpretations — and even then, generate the most likely interpretation immediately.

The interaction should feel like handing content to a skilled visual thinker who just **gets it** and draws something useful.

---

## Step 0 — Detect the Output Path

First, check what tools are available:

```
Image generation available (e.g. Gemini generate_image)?
├── YES → Image Path  (generate real image + portable prompt)
└── NO  → SVG Path   (generate sketch-style SVG + portable prompt)
```

User override exceptions:
- User says "SVG" → SVG path even if image generation is available
- User says "只给我 prompt" / "give me the prompt" → Prompt-only path (no image or SVG)

See `references/output-paths.md` for full path logic.

---

## Step 1 — Read the Content

Understand:
- What is the one-sentence message of this content?
- What is the relationship type? (flow / concept / comparison / story / problem-solution / hierarchy / showcase)
- How many nodes actually matter? Can it fit in one image?
- If the content is very long (500+ words): identify the 2–3 natural phases or themes and plan multiple images accordingly. Do not force long content into one image.

See `references/content-signals.md` for relationship type detection and image count heuristics.

**Do not start from style choices. Start from: what does this content need to say?**

---

## Step 2 — Detect Mode and Make All Decisions (Silently)

Using signals from the content and the user's phrasing, decide:
- **Audience mode** (XHS Story / Academic / WeChat Knowledge / Technical Whiteboard / General)
- **Visual style** (from the mode's default in `references/audience-modes.md`)
- **Aspect ratio** (from the mode's default)
- **Image count** (1, 2, or 3)
- **Layout type** (from `references/layout-guide.md` by relationship type)

Signal quick reference:

| Signal | Mode | Style | Ratio |
|--------|------|-------|-------|
| "小红书" / "种草" / emotional story | XHS Story | Warm narrative sketchnote | 3:4 |
| "论文" / "学术" / "导师" / abstract concept | Academic | Clean infographic | 16:9 |
| "公众号" / "干货" / "教程" / tips | WeChat Knowledge | Knowledge card sketchnote | 1:1 or 4:3 |
| "架构" / "流程" / "系统" / technical process | Technical Whiteboard | Whiteboard diagram | 16:9 |
| nothing specific | General | Classic sketchnote | 4:3 |

**Do this silently. Do not present a menu.**

**Track the key signal:** Note the one word or phrase from the content that most strongly triggered the mode decision. You will use it in the Step 3 status line so the user can immediately confirm or deny the reading.

**On ambiguity:** If the content matches two modes equally, **generate the most likely one immediately**. Add a note AFTER (not before) the status line:
```
（内容也可以做成 [alternative mode] 风格，想切换可以说）
```
Never block on ambiguity. Always generate something first.

---

## Step 3 — Status Line (Show the Signal), Then Generate Immediately

Show this format before generating:

```
→ 读到：[key signal] → [mode] · [style] · [ratio] · [N]张 · 生成中...
```

The `[key signal]` is the 2–5-word evidence phrase from the content that triggered the mode. Showing this lets the user immediately confirm or correct the reading — without needing to understand the mode system. If the user sees the signal is wrong, they can say so before the image is done.

Examples:
```
→ 读到：步骤流程+代码词汇 → 白板技术图 · 16:9 · 1张 · 生成中...
→ 读到：情感叙事+时间线 → 小红书叙事风 · 3:4 · 2张 · 生成中...
→ 读到：论文摘要+框架对比 → 学术信息图 · 16:9 · 1张 · generating...
→ 读到：无明确信号 → 通用手绘 · 4:3 · 1张 · 生成中...
```

**For 2+ images only:** Add one more line immediately after the status, declaring the split plan:
```
→ 计划：图1 [what image 1 covers]，图2 [what image 2 covers]。生成中...
```
Example:
```
→ 计划：图1 讲问题背景和痛点，图2 讲解决方案框架。生成中...
```
This is a declaration, not a question. Generate immediately. If the user objects to the split, they can say so and the plan will be adjusted.

**Generate immediately. Do not ask for confirmation. Do not wait.**

---

## Step 4 — Generate

### Image Path (Gemini `generate_image` tool available)

1. Build the image prompt using `references/prompt-guide.md`
   - Write as natural English prose (not a labeled form)
   - Include: style opener → subject description → layout/spatial → key nodes → style finish → aspect ratio
   - Keep prompt under ~120 words

2. Call `generate_image` with the prompt

3. For multiple images:
   - Generate image 1 first
   - For image 2+: use the same style parameters and append "Same visual language, line style, and color palette as image 1 of this series"
   - Report progress after each image: `→ 图 1/2 完成...`

4. After all images: output the portable prompt(s) in a labeled block:
   ```
   📋 Portable Prompt (works in Midjourney / FLUX / Ideogram)
   [English prompt here]
   ```

### SVG Path (no image generation tool)

1. Determine layout template and key nodes
2. Generate sketch-style SVG directly in the response
   - Follow `references/svg-guide.md` (rough paths, handwriting fonts, sketch icons)
   - Output as fenced SVG code block
3. After SVG: output the portable prompt

---

## Step 5 — Context-Aware Correction Hints

After all outputs, write **2–3 short correction hints that reflect what was just generated**. Do not use a fixed generic list every time.

The hints should:
- Tell the user what the obvious alternative directions are **for this specific output**
- Use concrete, natural language — not parameter names or mode labels
- Help the user articulate "what's wrong" even if they can't name it

**Template:**
```
如果不对：
→ 说 "[concrete description of the problem]" → [what will change]
→ 说 "[alternative direction]" → 换成 [alternative style/mode]
→ 说 "[specific element]" → 调整细节
```

**By mode — use the pattern that matches what was just generated:**

After **Technical Whiteboard**:
```
如果不对：
→ 说 "不是流程，这是概念介绍" → 换成中心辐射布局
→ 说 "想要彩色信息图的感觉（像 Ilya 那张）" → 换成学术信息图风格
→ 说 "节点太多了" → 帮你拆成两张
```

After **XHS Story**:
```
如果不对：
→ 说 "太个人化，我要知识干货版" → 换成公众号卡片风
→ 说 "把人物去掉" → 做更简洁的版本
→ 说 "改成横版" → 换成 4:3
```

After **Academic**:
```
如果不对：
→ 说 "太干了，想要更有温度" → 换成通用手绘风
→ 说 "信息太多，看不清" → 拆成两张
→ 说 "加一个节点：[XXX]" → 补充内容
```

After **WeChat Knowledge**:
```
如果不对：
→ 说 "想要更学术一点的风格" → 换成信息图
→ 说 "内容再多一些" → 加到 6 个要点
→ 说 "竖版" → 换成 3:4
```

After **General**:
```
如果不对：
→ 说 "小红书风格" 或 "学术图" → 换对应模式
→ 说 "重来，更简洁一点" → 重新蒸馏节点
→ 说 "竖版" → 换成 3:4
```

---

## Iteration: Natural Language Always Works

| User says | Action |
|---|---|
| "更小红书" | Switch to XHS Story mode, regenerate |
| "更学术" | Switch to Academic mode, regenerate |
| "分成两张" | Re-plan as 2 images, regenerate |
| "竖版" | Switch to 3:4, regenerate |
| "字少点" | Reduce to 3 nodes max, regenerate |
| "换 SVG" | Output SVG instead of generated image |
| "只给我 prompt" | Output prompt only, no image |
| "重来" | Regenerate with variation |
| "公众号风" | Switch to WeChat Knowledge mode |
| "技术图" | Switch to Technical Whiteboard mode |

Never require the user to learn mode names or parameter flags.

---

## Failure Guards

Actively prevent:
- **Asking before generating** — infer from signals, generate first, always
- **Content overflow** — max 5–6 nodes per image; split if more
- **Pretty but unreadable** — visual hierarchy must be immediately clear
- **Long content in one image** — if 500+ words, plan multiple images in Step 1
- **Prompt bloat** — if prompt exceeds ~120 words, content wasn't distilled enough
- **Empty output when image tools fail** — always fall back to SVG

---

## References

| File | When to use |
|------|-------------|
| `references/content-signals.md` | Step 1–2: detect mode, relationship, image count |
| `references/audience-modes.md` | Step 2: full visual profile per mode |
| `references/layout-guide.md` | Step 2: layout by relationship type |
| `references/style-options.md` | Step 4: style ingredients for prompt construction |
| `references/prompt-guide.md` | Step 4: how to write the image prompt |
| `references/svg-guide.md` | Step 4 (SVG path): how to generate sketch SVG |
| `references/output-paths.md` | Step 0: output path decision logic |
