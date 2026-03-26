# Changelog

## v0.3.0 — 2026-03-25

**Full philosophy and architecture rewrite.**

Core shift: from "visual distillation skill" to "zero-friction visual output layer."

### What changed

**Interaction philosophy reset**
- Previous: infer → confirm options → generate
- v0.3: infer → one-line status → generate immediately → iterate with natural language
- No forms. No parameter menus. No blocking confirmations.

**Audience mode system (new)**
- Replaced generic "style families" with 5 audience modes:
  XHS Story / Academic / WeChat Knowledge / Technical Whiteboard / General
- Each mode is a complete output profile: style, layout, ratio, density, tone
- Modes are detected from content signals and request phrasing automatically
- New file: `references/audience-modes.md`

**Content signal detection (new)**
- Formal signal table: maps request keywords and content characteristics to modes
- Relationship type detection for layout selection
- Image count heuristics
- Ambiguity resolution pattern (one-line, generate anyway)
- New file: `references/content-signals.md`

**SVG fallback path (new)**
- When no image generation tool is available, generate hand-drawn sketch SVG directly
- Full SVG guide: rough path techniques, handwriting font stack, sketch icon library, layout templates
- SVG feels genuinely hand-drawn: imperfect paths, irregular edges, warm near-black ink
- New file: `references/svg-guide.md`

**Output path logic (new)**
- Three paths: Image (Gemini) / SVG (fallback) / Prompt-only (user override)
- Always deliver something real — image or SVG, never just text
- Always also deliver a portable English prompt
- New file: `references/output-paths.md`

**Style options expanded**
- Rewritten around two style families: Sketchnote vs Infographic
- Five mode-specific style presets with full image prompt ingredients
- Preserved: portable prompt structure, anti-overload rules

**Layout guide unchanged**
- `references/layout-guide.md` retained from v0.2 (still valid)

---

## v0.2.0

- Reset product center around visual distillation instead of generic hand-drawn prompting
- Added project definition and version surface
- Added layout guide, style options, prompt guide references

## v0.1.0

- Initial skill release
