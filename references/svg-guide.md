# SVG Guide — Sketch-Style Hand-Drawn SVG

Use this file when image generation is unavailable and the output path is SVG.

---

## Core rule

> The SVG should look like a human drew it quickly with pen on paper — not like a computer-generated diagram.

The goal is sketch character, not pixel perfection.

---

## Fundamental Techniques

### 1. Imperfect Paths (模拟抖动线条)

Replace straight lines and perfect curves with slightly irregular paths.

Instead of:
```svg
<line x1="100" y1="100" x2="300" y2="100" stroke="black"/>
```

Use a path with slight wobble:
```svg
<path d="M100,102 C150,98 200,103 300,100" stroke="#1a1a1a" stroke-width="2" fill="none"/>
```

For boxes, use path instead of rect:
```svg
<!-- Sketch-feel box instead of perfect rectangle -->
<path d="M50,50 C51,49 149,51 150,50 C151,50 151,149 150,150 C149,151 51,149 50,150 C49,150 49,51 50,50Z"
  stroke="#1a1a1a" stroke-width="2" fill="none"/>
```

### 2. Sketch Stroke Style

Always use:
```svg
stroke="#1a1a1a"
stroke-width="2"
stroke-linecap="round"
stroke-linejoin="round"
fill="none"
```

For emphasis lines (underlines, boxes), increase to `stroke-width="3"`.
For secondary lines (grid, background guides), use `stroke-width="1"` and `stroke="#aaaaaa"`.

### 3. Handwritten Font Simulation

When embedding text, use a handwriting-style font stack. Even without a custom font loaded, use:
```svg
font-family="'Segoe Print', 'Comic Sans MS', cursive"
```

For Chinese content, add:
```svg
font-family="'Ma Shan Zheng', 'ZCOOL XiaoWei', 'Segoe Print', cursive"
```

Note: Ma Shan Zheng and ZCOOL XiaoWei are Google Fonts. If the SVG will be embedded in an HTML page with internet access, add this to the SVG `<defs>`:
```svg
<defs>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Ma+Shan+Zheng&amp;family=ZCOOL+XiaoWei&amp;display=swap');
  </style>
</defs>
```

### 4. Color Palette

Use a warm, limited palette:
- Primary ink: `#1a1a1a` (near-black, not pure black)
- Background: `#ffffff` or `#fafaf7` (slightly warm white)
- Accent 1 (highlight): `#f5c842` (warm yellow)
- Accent 2 (emphasis): `#e05a4e` (brick red)
- Accent 3 (info): `#4a90d9` (calm blue)
- Soft fill: `#fef9e7` (light cream, for box fills)

Never use more than 2 accent colors in one image.

For Academic mode: reduce to `#1a1a1a` + one soft blue accent only.
For XHS Story mode: use warmer palette (`#f9a825`, `#e57373`, `#81c784`).

### 5. Arrow Style

Sketch-feel arrows with hand-drawn arrowhead:
```svg
<!-- Arrow shaft -->
<path d="M100,200 C150,198 200,202 250,200" stroke="#1a1a1a" stroke-width="2" fill="none" stroke-linecap="round"/>
<!-- Arrowhead (hand-drawn feel) -->
<path d="M240,193 L252,200 L240,207" stroke="#1a1a1a" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
```

### 6. Highlight / Underline Emphasis

For keyword emphasis, add a slightly wobbly yellow underline:
```svg
<path d="M50,185 C75,188 125,183 175,186" stroke="#f5c842" stroke-width="6" fill="none" opacity="0.6"/>
<text x="50" y="183" font-family="'Segoe Print', cursive" font-size="16" fill="#1a1a1a">Key Term</text>
```

---

## SVG Layout Templates

### Template A: Center-radial (Concept)

```
Central label in the middle.
3–5 branch labels connected by curved lines radiating out.
Each branch can have a small icon approximation (simple shape).
```

Canvas: `viewBox="0 0 700 500"`
Center: `(350, 250)`
Branch distance: 180–200px from center

### Template B: Linear Flow (Process)

```
3–5 boxes arranged left to right (or top to bottom for vertical ratio).
Sketch arrows connecting them.
Labels inside boxes.
Step numbers in small circles above each box.
```

Canvas: `viewBox="0 0 800 400"`
Box width: 130px, height: 70px
Spacing: 40px gap between boxes

### Template C: Left-Right Comparison

```
Vertical divider line (slightly wobbly) in the center.
Left side: label + 3 items.
Right side: label + 3 items.
Title at top.
```

Canvas: `viewBox="0 0 700 500"`

### Template D: Problem → Solution Split

```
Left panel: problem zone (slightly distressed, maybe red accent).
Large arrow or separator in center.
Right panel: solution zone (calm, green or blue accent).
```

Canvas: `viewBox="0 0 800 450"`

### Template E: Story / XHS Narrative

```
Top: hook title in large hand-drawn style.
Three to four moments arranged vertically.
Each moment: small scene illustration (stick figures ok) + short label.
Bottom: takeaway / feeling line.
```

Canvas: `viewBox="0 0 450 700"` (portrait)

---

## Sketch Icon Library (Simple SVG Approximations)

These are minimal path-based icons that look hand-drawn:

**Lightbulb:**
```svg
<circle cx="20" cy="16" r="10" stroke="#1a1a1a" stroke-width="2" fill="none"/>
<path d="M15,26 L25,26 M16,28 L24,28" stroke="#1a1a1a" stroke-width="2" stroke-linecap="round"/>
```

**Arrow right:**
```svg
<path d="M0,10 L18,10 M12,4 L18,10 L12,16" stroke="#1a1a1a" stroke-width="2" fill="none" stroke-linecap="round"/>
```

**Checkmark:**
```svg
<path d="M2,12 L8,18 L20,4" stroke="#1a1a1a" stroke-width="2.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
```

**Warning triangle:**
```svg
<path d="M10,3 L20,19 L0,19 Z" stroke="#e05a4e" stroke-width="2" fill="none" stroke-linejoin="round"/>
<text x="10" y="16" text-anchor="middle" font-size="9" fill="#e05a4e">!</text>
```

**Gear:**
```svg
<circle cx="12" cy="12" r="4" stroke="#1a1a1a" stroke-width="1.5" fill="none"/>
<path d="M12,2 L12,6 M12,18 L12,22 M2,12 L6,12 M18,12 L22,12 M4.9,4.9 L7.8,7.8 M16.2,16.2 L19.1,19.1 M19.1,4.9 L16.2,7.8 M7.8,16.2 L4.9,19.1" stroke="#1a1a1a" stroke-width="1.5" stroke-linecap="round"/>
```

---

## Quality Checks

Before outputting SVG:
- Are any paths perfectly straight / rectangular? Add wobble.
- Is any font `Arial` or `sans-serif`? Switch to handwriting stack.
- Are there more than 2 accent colors? Reduce.
- Is the layout too symmetric / mechanical? Introduce slight offsets (2–4px variation).
- Does text fit inside its containers? Check approximate character widths.
- Is there a title? It should be the strongest visual element (largest font, boldest).

---

## What SVG Cannot Do

Be honest about SVG path limits:
- Complex photographic textures: not possible
- Real paper grain: use opacity tricks at best
- Complex face illustrations: use simple stick figure approximations
- Chinese font rendering: depends on browser / environment support

For content that genuinely requires photo-realistic or complex illustration style, note in the output that the SVG is a structural sketch and recommend using the portable prompt in a real image generation tool.
