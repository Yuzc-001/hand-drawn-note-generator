# Output Paths

Use this file to decide which output path to use and what to deliver.

---

## Core rule

> The user should always receive something real and usable. Never exit with only text description.

Output priority:
1. Real image (if generation tool available)
2. Sketch SVG code (if no image tool)
3. Always ALSO deliver a portable prompt

---

## Path Decision Tree

```
Is image generation available?
├── YES → Image Path
│         → generate_image with constructed prompt
│         → also output portable prompt text
│
└── NO  → SVG Path
          → generate sketch-style SVG code inline
          → also output portable prompt text
```

**User override exceptions:**
- "只给我 prompt" / "give me the prompt" → Prompt-only path (skip generation)
- "SVG" → SVG path (even if image generation is available)
- "生成图" / "画出来" with image generation available → Image path

---

## Image Path

**Use when:** `generate_image` tool is available.

**Steps:**
1. Build image prompt using `references/prompt-guide.md`
2. Call `generate_image` with the constructed prompt
3. After image is shown, output the portable prompt in a collapsible block or labeled section

**Portable prompt delivery format:**
```
📋 可移植 Prompt（可用于 Midjourney / FLUX / Ideogram）
---
[English prompt here]
---
```

---

## SVG Path

**Use when:** No image generation tool is available, or user explicitly requests SVG.

**Steps:**
1. Determine layout and content nodes
2. Generate hand-drawn sketch style SVG (see `references/svg-guide.md`)
3. Output SVG code in a fenced code block
4. After SVG, output the portable prompt

**SVG output format:**
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600">
  <!-- sketch-style hand-drawn visual -->
</svg>
```

The SVG should feel hand-drawn, not perfectly geometric. Follow `references/svg-guide.md` for how to achieve sketch character without a rendering library.

---

## Prompt-Only Path

**Use when:** User explicitly says "给我 prompt" / "只要提示词" / "I'll generate it myself."

**Steps:**
1. Determine mode, style, layout as usual
2. Output: one-line status + the full portable prompt
3. Optional: brief note on which style preset was chosen and why

**No image or SVG generation in this path.**

---

## Always Deliver

Regardless of path, always include:
- A real output (image OR SVG) — unless user asked for prompt-only
- The portable English prompt — always
- A one-line iteration invitation — always

### Iteration invitation examples
- `调整可以说：更学术 / 分成两张 / 竖版 / 字少点`
- `To adjust: say "more academic" / "split into 2" / "less text" / "vertical"`
