# Prompt Guide

Use this file when the main question is:

# how do I turn a distilled visual idea into a portable image prompt without locking the user into one fixed style?

This file is not for deciding the message.
That should already be done.
This file is for expressing the message clearly in prompt form.

---

## Core rule

# preserve structure first, then express style

A weak prompt bundle starts from aesthetic keywords.
A strong prompt bundle starts from:
- the message
- the relationship
- the layout
- the density limit
- the user’s chosen style and aspect ratio

---

## Layer 1 — universal prompt requirements

These are the cross-style requirements.
They should survive even when the user changes the visual style.

Every prompt should preserve:
- a clear one-sentence visual goal
- explicit layout commitment
- explicit spatial placement
- readable visual hierarchy
- short visible labels
- low clutter
- portable wording that is not tied to one model

These matter more than any single aesthetic phrase.

---

## Layer 2 — base prompt skeleton

```text
[style description], about [topic], with [visible text language if needed].

MAIN MESSAGE: [one-sentence visual goal]
LAYOUT: [layout type]
TOP / LEFT / CENTER / RIGHT / BOTTOM: [what appears where]
KEY NODES: [3–6 short items]
ICONS: [simple concrete icon list]
CONNECTIONS: [arrows / numbering / dividers / branches]
COLOR ACCENTS: [only if useful]
OPTIONAL CHARACTER: [only if it helps]
OPTIONAL SPEECH BUBBLE: [only if it helps]

Style instructions: [clarity / line / spacing / contrast / composition instructions matching the chosen style]
Aspect ratio: [ratio if the generation tool or workflow supports it]
```

---

## Layer 3 — style presets

Use these as starting bundles, not as global hard requirements.

### A. Casual hand-drawn sketchnote
Use when the user wants:
- lively
- friendly
- expressive
- creator-style knowledge sharing

Recommended style description:
- `Hand-drawn sketch note style illustration on a pure white background`

Recommended style instructions:
- black ink primary lines
- simple icons and illustrations
- handwritten Chinese text if needed
- playful but readable
- high contrast
- no gradients, no shadows
- light color accents for emphasis

### B. Research / academic sketch style
Use when the user wants:
- more serious
- cleaner
- more diagram-like
- less playful energy

Recommended style description:
- `Clean academic sketch diagram on a white background`

Recommended style instructions:
- restrained line work
- precise labels
- limited accents
- strong structure
- minimal decorative elements
- clear analytical composition

### C. Whiteboard explainer style
Use when the user wants:
- teaching clarity
- workshop / classroom feel
- tutorial readability

Recommended style description:
- `Whiteboard explainer illustration with clean marker-style lines`

Recommended style instructions:
- strong directional arrows
- instructional sequencing
- readable labeled steps
- simple icon support
- clean contrast

### D. Clean knowledge card style
Use when the user wants:
- social-share graphics
- polished knowledge-sharing visuals
- less sketch mess, more clean blocks

Recommended style description:
- `Clean knowledge-sharing card illustration with lightweight diagram elements`

Recommended style instructions:
- tidy section blocks
- light but clear visual grouping
- restrained icon set
- cleaner spacing discipline
- social-friendly composition

### E. Minimal monochrome diagram
Use when the user wants:
- maximum clarity
- low decoration
- mostly structure over style

Recommended style description:
- `Minimal monochrome explanatory diagram on a white background`

Recommended style instructions:
- black and gray primary
- almost no decorative accents
- high readability
- sparse, precise composition

---

## User override rule

If the user gives a visual preference, that preference outranks the preset.

Examples:
- more academic
- more playful
- more like a whiteboard lesson
- more like a clean Xiaohongshu knowledge card
- vertical mobile-friendly ratio
- 16:9 slide ratio

Do not force the preset back in after the user has chosen.

---

## Prompt writing rules

### Keep visible text short
Prefer:
- short labels
- short node names
- short callouts

Avoid:
- sentence-heavy boxes
- paragraph-style explanation inside the image

### Use concrete placement words
Prefer:
- top center
- left side
- bottom row
- center branch
- right panel

Avoid vague wording like:
- `well arranged`
- `nicely balanced`
- `beautiful composition`

### Use concrete icon language
Prefer:
- lightbulb
- arrow
- gear
- document
- magnifier
- checkmark
- warning triangle

Avoid abstract prompt fluff.

### Keep hierarchy visible
The title should be strongest.
Primary nodes should be more prominent than supporting notes.
The prompt should reflect that.

---

## Anti-bloat rules

If the prompt needs:
- too many areas
- too many labels
- too many arrows
- too many icon types
- too many color roles

then the real problem is probably upstream:
- too much content
- wrong layout
- or insufficient splitting

Fix the structure first.
Do not compensate with longer prompting.

---

## Multi-image consistency

For image 2 and beyond, append a consistency line only if the images are truly one series.

Example:

```text
Keep the same overall visual language, line style, and color discipline as the first image in this series.
```

Do not over-constrain if variation between images is useful.

---

## Failure signs

A prompt is probably weak when:
- it reads like a raw checklist of everything the user mentioned
- the title is not clearly primary
- the reading order is implicit instead of guided
- the prompt uses many adjectives but few spatial instructions
- the style is very specific but the message remains vague
- the prompt gets longer because the content was not distilled first
- the style preset is being treated like a mandatory global identity

---

## Bottom line

The prompt should carry distilled structure into image generation.
Style should shape the final expression, not replace the thinking.
