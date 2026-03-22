# Style Options

Use this file when the main question is:

# what visual style should this content use?

The skill should not hard-code one drawing style as the only valid output.
The main job is content distillation.
Style should be chosen with the user when it materially affects the result.

---

## Core rule

# the user owns style preference

Default behavior:
- distill the content first
- then confirm style and aspect ratio if they are not already clear
- then build the prompt

Do not pretend one fixed style is best for all knowledge-sharing content.

---

## Recommended style families

### 1. Casual hand-drawn sketchnote
Use when the user wants:
- lively
- friendly
- expressive
- creator-style knowledge cards

Typical traits:
- black ink lines
- colored highlights
- playful icons
- stick figures / speech bubbles optional

### 2. Research / academic sketch style
Use when the user wants:
- more serious
- cleaner
- more diagram-like
- less playful

Typical traits:
- restrained accents
- cleaner lines
- less cartoon energy
- more emphasis on structure and labeling

### 3. Whiteboard explainer style
Use when the user wants:
- teaching clarity
- tutorial style visuals
- workshop / lesson board feel

Typical traits:
- strong sequencing
- clear arrows
- simplified instructional composition

### 4. Clean knowledge card style
Use when the user wants:
- social-share knowledge graphics
- polished but still lightweight visuals
- cleaner composition with less “messy sketch” energy

Typical traits:
- tighter spacing discipline
- clearer section blocks
- fewer playful elements

### 5. Minimal monochrome diagram style
Use when the user wants:
- maximum clarity
- low decoration
- almost no color dependence

Typical traits:
- black / gray primary
- very sparse accents or none
- structure over mood

---

## Aspect ratio options

The skill should not force `4:3` by default in all cases.

Common choices:
- `1:1` for social cards / compact concept notes
- `4:3` for classic sketch-note boards
- `16:9` for presentation / slide-style knowledge visuals
- `3:4` or `4:5` for mobile-friendly vertical sharing
- custom ratio if the user explicitly wants one

---

## When to ask

Ask a style/aspect question when:
- the user clearly cares about visual tone
- the platform or usage context affects composition
- different styles would materially change prompt construction
- aspect ratio affects readability or posting destination

Do not ask if:
- the user already specified style and ratio
- the task is only asking for content distillation first
- one default is temporarily fine and the user said “just pick one”

---

## Minimal confirmation pattern

Use short confirmation, not a style survey.

Example:
- `我先把内容拆清楚。风格你要偏：轻松手绘 / 科研示意 / 白板讲解 / 知识卡片？比例要 1:1、4:3、16:9 还是竖版？`

If the user does not care, choose a reasonable default and say so briefly.

---

## Bottom line

Content structure is the core of the skill.
Style and aspect ratio should be adjustable output parameters, not the product center.
