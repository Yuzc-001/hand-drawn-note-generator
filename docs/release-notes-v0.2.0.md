# hand-drawn-note-generator v0.2.0 Release Notes

## Summary

v0.2.0 is the release where this project stops being understood as a fixed hand-drawn prompt bundle and starts becoming a visual-distillation skill.

Earlier work already made it possible to turn content into sketch-note style outputs.
But the center was still too close to one specific aesthetic:
- one dominant hand-drawn style
- one dominant aspect ratio
- one prompt identity treated as the product itself

v0.2.0 resets that.

The new center is:

# visual distillation

Meaning:
- first decide what the image needs to say
- then decide what to remove
- then choose the right layout
- then adapt the final prompt to the user’s preferred style and ratio

---

## What changed

### Product-center reset
This project is no longer defined primarily as “a hand-drawn note prompt generator.”

It is now defined as:

# a visual-distillation skill for sketch-note and knowledge-sharing visuals

That change matters because the real value is not locked inside one aesthetic.
The real value is the ability to:
- compress dense content
- choose structure well
- prevent overload
- produce portable prompts across styles and tools

---

### Style was demoted from identity to parameter
The old framing implicitly treated one casual hand-drawn sketch-note style as the default identity.

v0.2.0 changes that.

Style is now:
- user-adjustable
- context-sensitive
- secondary to content structure

A new `references/style-options.md` file now supports multiple style families, including:
- casual hand-drawn sketchnote
- research / academic sketch style
- whiteboard explainer style
- clean knowledge card style
- minimal monochrome diagram style

---

### Aspect ratio is no longer hard-coded
The project no longer assumes one fixed ratio for every output.

It now treats ratio as part of output fit.
Common options include:
- `1:1`
- `4:3`
- `16:9`
- `3:4`
- `4:5`
- custom ratios when the user explicitly wants one

---

### The skill body was rebuilt around visual clarity
`SKILL.md` was rewritten around this active path:
1. distill the visual message
2. choose layout by relationship
3. confirm style and aspect ratio when needed
4. build a portable prompt
5. show the prompt before generation
6. close with usable output

This makes the skill much less like a decorative prompt pack and much more like a lightweight visual reasoning layer.

---

### References were rebuilt around judgment, not templates
The references were rewritten to support:
- layout judgment by relationship type
- anti-overload splitting logic
- prompt construction that preserves hierarchy
- style presets without style lock-in

That means the repo is now less about “which phrase to include” and more about “what visual decision should happen here.”

---

## What v0.2.0 means

v0.2.0 is not just a documentation cleanup.
It is a product reset.

The project should now be understood as a skill that helps agents turn dense content into clearer visual communication, while leaving room for the user to decide the final aesthetic direction.

---

## What did not change

The project still values:
- clean hand-drawn / knowledge-sharing outputs
- portable prompt delivery
- simple icons and readable composition
- lightweight visual summaries instead of dense image clutter

What changed is that these are no longer treated as one frozen aesthetic package.

---

## Outcome

v0.2.0 is the first version that starts to feel like a real skill repo instead of an initial prompt bundle.

It still needs stress cases and further examples to prove how well it handles difficult content.
But the product center is now much sharper, and the style layer is finally in the right place: downstream of content structure, not upstream of it.
