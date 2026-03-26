# Prompt Guide (v0.3)

Use this file to turn a distilled visual idea into an image prompt.

**This file is for expression, not for deciding content.**
Content structure and audience mode should already be determined before reaching this file.

---

## Core rule

> Write the prompt as flowing English prose, not as a labeled form.

Gemini and most modern image generation models respond better to natural description than to structured labels.

**Weak (form-style):**
```
MAIN MESSAGE: System architecture overview
LAYOUT: Linear flow
TOP: Title
KEY NODES: Input, Process, Output, Monitor, Deploy
```

**Strong (prose-style):**
```
Hand-drawn whiteboard diagram showing a 5-step technical pipeline: Input → Process → Output → Monitor → Deploy. Each step in a rough sketch box with a directional arrow. Bold title "System Architecture" at top center. Black marker lines on white background. One orange accent on the final Deploy box. Simple, clean, readable at a glance.
```

---

## Prompt Construction

### Layer 1 — Style opener (from audience mode)

Start with the style description from `references/style-options.md` for the detected mode.

| Mode | Style opener |
|------|-------------|
| XHS Story | `Warm hand-drawn illustration, narrative sketchnote style, soft pastel colors, expressive character doodles,` |
| Academic | `Clean academic sketch diagram, restrained line work, minimal color accent, structured infographic composition,` |
| WeChat Knowledge | `Clean knowledge-sharing sketchnote, organized visual sections, handwritten-style icons, light color highlights,` |
| Technical Whiteboard | `Technical whiteboard sketch diagram, clean black marker lines, directional arrows, labeled system components,` |
| General | `Hand-drawn sketch note illustration, black ink, simple icons, light color accents, playful but readable,` |

### Layer 2 — Subject description

One or two sentences describing what the image shows. Be specific and spatial.

Good patterns:
- "showing [N] [relationship type]: [node 1] → [node 2] → ..."
- "comparing [A] on the left versus [B] on the right"
- "centered on [main concept] with [N] branches: [label 1], [label 2], ..."
- "a narrative flow from [start state] to [end state] with [N] key moments"

### Layer 3 — Layout and spatial guidance

Specify where things are. Use concrete placement words:
- top center / bottom row / left panel / right side / center hub
- above / below / connected by arrow / branching from

Avoid: "well arranged", "nicely balanced", "beautiful composition"

### Layer 4 — Key content (concise)

Name the 3–6 key nodes or labels that must appear. Keep them short (1–3 words each).

If Chinese visible text is needed:
```
Include visible Chinese text: "[label 1]", "[label 2]", "[label 3]"
```

### Layer 5 — Style finish

Close with 1–2 sentences of visual clarity instructions:
- "White background, high contrast, no gradients."
- "Strong reading hierarchy: title largest, nodes medium, sub-labels small."
- "Minimal decoration — every element carries information."

### Layer 6 — Aspect ratio

Append aspect ratio as the final line if the generation tool supports it:
```
Aspect ratio: 16:9
```

---

## Full Prompt Examples

### Example: Technical Whiteboard (Academic / Technical mode)

```
Technical whiteboard sketch diagram showing a 4-step deployment pipeline: Build → Test → Stage → Deploy. Each step in a rough rectangular box, connected by thick directional arrows. Bold title "CI/CD Pipeline" at top center in large marker-style text. Red warning icon next to Test step. Black marker lines on white background, one orange accent on Deploy. Simple labeled components, no decoration, strong left-to-right reading flow.
Aspect ratio: 16:9
```

### Example: XHS Narrative (XHS Story mode)

```
Warm hand-drawn illustration, narrative sketchnote style. A personal story timeline moving top to bottom: "初见" at the top with two simple cartoon figures meeting, then "争吵" in the middle with jagged energy lines, then "和好" at the bottom with a soft heart icon. Soft coral and warm yellow accents. Handwritten-style Chinese labels. Flowing layout with light cream background. Feels personal, emotional, shareable.
Aspect ratio: 3:4
```

### Example: Knowledge Card (WeChat Knowledge mode)

```
Clean knowledge-sharing sketchnote. Title "5个提效技巧" in bold at the top. Five numbered items arranged vertically, each with a simple icon to the left: 1-lightbulb, 2-clock, 3-checkmark, 4-gear, 5-star. Black ink primary, yellow highlight on key words, red accent for item numbers. Organized section blocks, readable at small size. White background, no decoration beyond icons.
Aspect ratio: 1:1
```

---

## Prompt Quality Checks

Before generating, verify:
- [ ] Does the prompt read as natural English prose (not a form)?
- [ ] Is the layout type explicit (not implied)?
- [ ] Are spatial positions named concretely?
- [ ] Are there 3–6 key content nodes, not more?
- [ ] Is the title/hierarchy mentioned?
- [ ] Is the aspect ratio appended?
- [ ] Is the total length under ~120 words? If longer, the content wasn't distilled enough.

---

## Multi-Image Consistency

For image 2 and beyond in a series, append:
```
Same visual language, line style, and color palette as image 1 of this series.
```

---

## Anti-bloat rule

If writing the prompt requires more than ~120 words, stop.
The problem is upstream: too much content, wrong split point, or insufficient distillation.
Fix the structure before fixing the prompt.
