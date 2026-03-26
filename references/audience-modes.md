# Audience Modes

The skill supports 5 audience modes. Each mode is a complete output profile: it defines the visual language, layout preference, node density, aspect ratio, and tone.

---

## Core rule

> Mode determines everything downstream. Choose it first — from content signals, not from a menu.

---

## Mode 1: XHS Story (小红书叙事风)

**When to use:**
- Personal narrative, emotional content, relationship / life experience
- User mentions "小红书", "种草", "分享", "日记"
- Content has a personal arc or before / after structure

**Visual characteristics:**
- Warm, hand-drawn illustration feel
- Characters optional but welcome (stick figures, simple faces)
- Soft color palette: warm tones, pastel accents
- Speech bubbles, emoticons, hand-lettered text common
- Flowing layout, not rigid grid
- Feels personal, relatable, shareable

**Layout preferences:**
- Narrative flow (top to bottom, page-scroll feel)
- Timeline or story arc
- Loose comparison (before / after life)

**Aspect ratio:** 3:4 or 4:5 (mobile-first, XHS standard)
**Node density:** Low to medium (3–5 key moments, not packed)
**Image count:** 1–3 (series of shareable cards)

**Prompt flavor:**
> "Warm hand-drawn illustration, narrative sketchnote style, soft pastel tones, expressive character doodles, flowing layout..."

---

## Mode 2: Academic / Research (学术信息图)

**When to use:**
- Research papers, system architecture, academic concepts
- User mentions "论文", "学术", "导师", "研究", "汇报"
- Content is abstract framework, technical comparison, or evidence-based argument

**Visual characteristics:**
- Clean, restrained line work
- Strong structure: clear labeling, precise placement
- Limited color: 1–2 accent colors only
- No cartoon energy, no playful icons
- Feels rigorous, credible, analytical
- Like a diagram from a Nature paper or a well-designed conference slide

**Layout preferences:**
- System architecture, hierarchy, cause map, structured comparison
- Center-radial for framework overview
- Left-right for A vs B theoretical positions

**Aspect ratio:** 16:9 (presentation / slide format)
**Node density:** Medium to high (can carry 5–8 labeled nodes)
**Image count:** 1–2 (usually one strong diagram)

**Prompt flavor:**
> "Clean academic sketch diagram, precise label placement, minimal color accent, structured infographic composition, white background..."

---

## Mode 3: WeChat Knowledge Card (公众号知识图)

**When to use:**
- Knowledge sharing, tutorial, checklist, "dry goods" content
- User mentions "公众号", "知识", "干货", "教程", "tips"
- Content is structured information that people want to save and re-use

**Visual characteristics:**
- Slightly cleaner than casual sketchnote
- More organized blocks, clearer visual sections
- Black ink primary with color highlights for key points
- Checkmarks, numbered steps, icons common
- Readable in small size on WeChat share card
- Feels like "knowledge worth saving"

**Layout preferences:**
- Step cards, grid showcase, checklist
- Flow for tutorials
- Problem → solution for tips / mistake avoidance

**Aspect ratio:** 1:1 (WeChat thumbnail) or 4:3 (article image)
**Node density:** Medium (4–6 clean, readable points)
**Image count:** 1–2

**Prompt flavor:**
> "Clean knowledge card sketch illustration, organized section blocks, handwritten-style icons, high contrast readable labels, light color highlights..."

---

## Mode 4: Technical Whiteboard (技术白板图)

**When to use:**
- System architecture, API flow, code explanation, technical comparison
- User mentions "架构", "流程", "系统", "代码", "pipeline"
- Content is a process that needs sequence and component clarity

**Visual characteristics:**
- Black-ink whiteboard marker feel
- Strong directional arrows, numbered steps
- Monochrome primary (can add one accent color for differentiation)
- Box-and-arrow structure
- No decorative elements — all elements are information-bearing
- Feels like an expert drawing on a whiteboard to explain a system

**Layout preferences:**
- Linear flow, component architecture tree, before/after tech comparison
- Anti-pattern: center-radial (too soft for technical clarity)

**Aspect ratio:** 16:9 (screen, presentation, documentation)
**Node density:** High (can carry 6–10 labeled components)
**Image count:** 1–3 (complex systems welcome splitting)

**Prompt flavor:**
> "Technical whiteboard sketch diagram, clean black marker lines on white, directional arrows, labeled system components, monochrome with minimal accent color..."

---

## Mode 5: General Sketchnote (通用手绘笔记)

**When to use:**
- No strong platform or audience signal detected
- Mixed content that doesn't clearly belong to another mode
- User just says "做成图" with no further context

**Visual characteristics:**
- Classic hand-drawn sketchnote aesthetic
- Black ink primary, colored highlights
- Playful but readable
- Flexible: can include icons, characters, speech bubbles as needed
- Feels like a smart person's notebook page

**Layout preferences:**
- Choose from any layout type based on content relationship
- Defaults to center-radial or linear flow

**Aspect ratio:** 4:3 (classic sketchnote default)
**Node density:** Medium (3–5 nodes standard)
**Image count:** 1 (default), split if content warrants

**Prompt flavor:**
> "Hand-drawn sketch note illustration, white background, black ink, simple icons, handwritten labels, colored highlights, clean readable layout..."

---

## Mode Switching

The user can switch modes at any time by saying:
- "更小红书" → XHS Story
- "更学术" → Academic
- "公众号风" → WeChat Knowledge
- "技术图" → Technical Whiteboard
- "普通手绘就好" → General Sketchnote

The skill should accept these as natural language commands, not as formal parameter changes.
