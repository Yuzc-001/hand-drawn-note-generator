# Hand-Drawn Note Generator — Project Definition

## One-line

A visual-distillation skill that turns dense content into hand-drawn sketch-note image briefs that are clearer, lighter, and easier to share.

## What this project is actually for

This project should not be understood as “a prompt template for drawing pretty notes.”

Its real job is:

# compress meaning before image generation

That means it should help an agent take:
- a messy project intro
- a concept explanation
- a process flow
- a tutorial
- a comparison
- a portfolio / showcase summary

and turn it into:
- the right core message
- the right visual structure
- the right amount of content
- the right prompt for image generation

## Product center

The center is not one fixed image style.
The center is:

# visual distillation

Style matters, but style is downstream and user-adjustable.
First the skill must decide:
- what the picture is trying to say
- what should be left out
- what layout carries the message best
- when one image is enough and when multiple are required

Then it should adapt the final prompt to:
- the user’s preferred visual style
- the user’s preferred aspect ratio
- the actual publishing or usage context

## Main failure modes this project should fight

### 1. Content overload
Too much text or too many concepts get stuffed into one image.

### 2. Layout mismatch
The image structure does not match the content relationship.

### 3. Pretty but unclear output
The result looks decorative but the message is not immediately understandable.

### 4. Prompt without visual judgment
The prompt describes many elements but does not produce a strong visual hierarchy.

### 5. Model-specific dependency
The skill becomes tied to one image model instead of producing portable output.

## v0.2 success criteria

This project should feel real when it can reliably do the following:
- reduce dense content into a small number of visual claims
- choose layout based on message structure, not keyword superstition alone
- prevent overloaded images
- produce portable prompts that can be used across image tools
- explain its visual choices briefly when helpful
- stay light enough to use during real work, not only as a novelty demo

## v0.2 boundary

This project is not:
- a general infographic generator for every style
- a full design system
- a replacement for human graphic design
- a generic summary tool that ignores visual composition

It is specifically:

# a sketch-note oriented visual distillation layer

## What needs rebuilding

To become a real skill repo, this project needs:
- a sharper `SKILL.md` centered on visual distillation and anti-overload judgment
- clearer reference separation between layout choice and prompt construction
- top-level release/version surface
- examples / stress cases later, so the project can show it handles hard content, not only easy demos
