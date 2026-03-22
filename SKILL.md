---
name: hand-drawn-note-generator
description: >
  Turn dense content into visual-distilled image briefs for sketch-note and knowledge-sharing visuals.
  Use when the user wants a project, concept, workflow, tutorial, comparison,
  or showcase content turned into a hand-drawn / whiteboard / knowledge-card style visual.
  Prioritize content distillation, layout fit, anti-overload judgment, and user-owned style choices.
---

# Hand-Drawn Note Generator

Use this skill when the user wants content turned into a visual summary image or prompt.

The real center is not one fixed drawing style.
The real center is:

# visual distillation

This skill should first make the content visually clear, then adapt style and aspect ratio to the user's preference.

## Core rule

# content structure first, style second

Do not start from decorative style choices.
Start from:
- the message
- the few nodes that matter most
- the relationship between them
- the lightest layout that can carry them clearly

Then confirm or choose:
- visual style
- aspect ratio
- any platform-specific output preference

## When to use

Use this skill when the task is about turning content into:
- a hand-drawn note
- a sketchnote
- a whiteboard-style visual summary
- a research-style visual explanation
- a knowledge-sharing card
- a project intro visual
- a concept explanation image
- a workflow/tutorial/comparison sketch

Do not use this skill when the user wants:
- photorealistic images
- polished marketing posters as the main goal
- dense document pages rendered as images
- generic design advice without a visual output target

## Active path

### Step 1 — Distill the visual message

Identify:
- the one-sentence message of the image
- the 3–6 highest-value nodes
- the relationship type: concept / flow / comparison / problem-solution / showcase / hierarchy
- what must be removed to keep the image readable
- whether this should be one image or multiple

If the content is too dense for one image, split it.
Do not force everything into one frame.

If user intent is unclear, ask the smallest question that changes layout or image count.

### Step 2 — Choose layout by relationship

Use `references/layout-guide.md`.

Choose layout by message structure, not by surface keyword alone.
The real test is:

# does the layout make the relationship immediately legible?

### Step 3 — Confirm style and aspect ratio when needed

Use `references/style-options.md`.

If the user already has a style preference, follow it.
If the user clearly cares about output vibe, ask briefly before prompting.
If the user does not care, choose a sensible default and say so shortly.

Style is adjustable.
It is not the product center.

### Step 4 — Build a portable prompt

Use `references/prompt-guide.md`.

The prompt should:
- be in English
- specify visible Chinese text when needed
- specify placement clearly
- reflect the chosen style
- reflect the chosen aspect ratio
- avoid overloaded wording
- remain portable across image tools

### Step 5 — Show the prompt before generation

Before generating, show the prompt in the conversation unless the user explicitly says not to.

If the environment has image generation available, generate after showing the prompt.
If not, deliver:
- the prompt
- the chosen layout
- image count recommendation
- style choice
- aspect ratio recommendation

### Step 6 — Close with usable output

Return the smallest complete package that lets the user continue immediately:
- one ready-to-use prompt
- or multiple prompts for split images
- plus a short note on layout choice / style choice when that helps

Do not add long process explanation unless the user asks.

## Response rules

- Prefer clarity over decoration
- Prefer one strong visual claim over many weak ones
- Prefer splitting over overload
- Prefer portable prompts over model-specific tricks
- Prefer short visible labels in the image
- Avoid dense paragraphs inside the visual
- Avoid pretending one image can carry too much
- Treat style and aspect ratio as adjustable parameters

## Failure guards

Actively prevent these failures:
- too many nodes in one image
- layout mismatch
- “pretty but unclear” output
- prompt bloat without visual hierarchy
- needless dependence on one image model
- locking the user into one style without asking
- forcing one aspect ratio regardless of use case

## Output style

Be brief and practical.

Default output should be:
1. distilled message
2. chosen layout
3. image count
4. chosen or confirmed style
5. chosen or confirmed aspect ratio
6. prompt(s)
7. optional generation result

Do not turn the interaction into a long design lecture.
