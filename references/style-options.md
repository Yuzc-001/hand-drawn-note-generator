# Style Options

Use this file when selecting visual style ingredients for image prompt construction.

---

## Core rule

> Style is downstream of mode. Always determine audience mode first, then use this file to build the style layer of the prompt.

Style should express the content — not replace the content.

---

## The Two Style Families

Understanding this distinction prevents the most common confusion:

### Sketchnote (手绘笔记)

**Definition**: A visual note that looks like a smart person's notebook. Feels personal, handmade, expressive. Text and drawing are mixed freely.

**Best for**: General, XHS Story, WeChat Knowledge modes.

**Visual DNA:**
- Black ink lines with loose, imperfect character
- Short text labels, not full sentences
- Icons: lightbulbs, arrows, stars, speech bubbles, simple faces
- Color: accent highlighting, not filled blocks
- Layout: compositional, not rigid grid

### Infographic (信息图)

**Definition**: A structured visual diagram that prioritizes information hierarchy and readability. Feels designed, not handmade. Data and relationships are primary.

**Best for**: Academic, Technical Whiteboard modes.

**Visual DNA:**
- Cleaner, more controlled lines (but still sketch-feel, not CAD-perfect)
- Labeled components with clear hierarchy
- Structured layout: boxes, lanes, nodes with connectors
- Color: for differentiation and emphasis, not decoration
- Layout: grid or diagram structure first

The Ilya Sutskever infographic in your reference images is a great example of the infographic family done with a hand-drawn warm style. It's structured (two-column, labeled nodes) but has illustration energy (character portrait, wavy trees, cartoon icons). This is the sweet spot for Academic mode.

---

## Style Preset A — Warm Narrative Sketchnote (XHS Story)

**Use for:** XHS Story mode.

**Image prompt ingredients:**
```
Warm hand-drawn illustration, sketchnote narrative style, soft pastel color palette,
expressive character doodles in simple line style, flowing composition,
handwritten-style labels, light warm background (#faf8f0 or white),
emotional storytelling visual layout, cartoon-adjacent but not childish
```

**Color palette notes:**
- Background: warm off-white or light cream
- Accent 1: warm yellow or peach
- Accent 2: soft coral or rose
- Ink: near-black (#1a1a1a), not pure black
- Optional soft teal or olive for secondary items

**Avoid:**
- Cold colors (pure blue, grey palettes)
- Rigid grid structure
- Too many labeled boxes

---

## Style Preset B — Clean Academic Infographic (Academic)

**Use for:** Academic / Research mode.

**Image prompt ingredients:**
```
Clean academic sketch diagram, white background, restrained line work,
minimal color accent (one blue or one teal only), precise label placement,
structured visual hierarchy, analytical infographic composition,
scientific illustration feel, clear node-connector labeling,
no cartoon decorations, strong structural clarity
```

**Color palette notes:**
- Background: pure white
- Primary: near-black ink for all structure
- Accent: one calm blue (#4a90d9) or deep teal (#2e8b8b)
- No warm tones

**Avoid:**
- Playful icons (lightbulbs, stars, speech bubbles)
- Warm color palette
- Loose, messy composition

---

## Style Preset C — Knowledge Card Sketchnote (WeChat Knowledge)

**Use for:** WeChat Knowledge mode.

**Image prompt ingredients:**
```
Clean knowledge-sharing sketchnote, hand-drawn illustration style, white background,
black ink primary with yellow and red accent highlights, organized visual sections,
numbered steps or checkmarks, icons: lightbulb, document, magnifier, checkmark,
readable at small sizes, slightly polished sketch feel (less messy than casual),
balanced composition, educational and trustworthy tone
```

**Color palette notes:**
- Background: white
- Ink: near-black
- Accent 1: warm yellow (highlight)
- Accent 2: red (warning / emphasis)
- Accent 3: optional light blue (info)

**Avoid:**
- Personal / emotional layout
- Too many characters or story elements

---

## Style Preset D — Technical Whiteboard (Technical)

**Use for:** Technical Whiteboard mode.

**Image prompt ingredients:**
```
Technical whiteboard sketch diagram, clean black marker-style lines on white background,
monochrome primary palette, directional arrows with clear flow,
labeled system components in rectangular boxes, no decorative elements,
every element is information-bearing, strong reading order from left to right or top to bottom,
marker-on-whiteboard aesthetic, precise but hand-drawn feel
```

**Color palette notes:**
- Background: pure white
- Primary: near-black for all elements
- Single accent: one color allowed for differentiation (deep orange or blue)
- No warm tones, no playful colors

**Avoid:**
- Characters, faces, speech bubbles
- Decorative flourishes
- Warm palette

---

## Style Preset E — Classic Sketchnote (General)

**Use for:** General mode (default when no signal detected).

**Image prompt ingredients:**
```
Hand-drawn sketch note illustration, white background, black ink primary lines,
simple icons and doodles, handwritten-style labels, light color accents for key points,
playful but readable, high contrast, no gradients or shadows,
knowledge-sharing visual style, clean and energetic composition
```

**Color palette notes:**
- Background: white or very light
- Ink: near-black
- Accent: 2 colors max (warmest being key color)

**Avoid:**
- Over-designing the style layer before the content is structured

---

## Aspect Ratio Options

| Ratio | Use case | Mode match |
|-------|----------|------------|
| 1:1 | WeChat thumbnail, social square | WeChat Knowledge |
| 4:3 | Classic sketchnote, article image | General, WeChat |
| 16:9 | Slides, presentations, technical diagrams | Academic, Technical |
| 3:4 | XHS standard, mobile-first | XHS Story |
| 4:5 | Instagram / XHS extended | XHS Story |

---

## User Override

If the user gives a style preference, it overrides the preset. Natural language always works:
- "更卡通" → increase character/illustration energy
- "更干净" → reduce icons and decoration
- "更学术" → switch to Preset B
- "彩色版" → add more color saturation
- "黑白就好" → drop all color accents, monochrome

Never force the preset back after the user has explicitly changed direction.
