# Content Signals

Use this file to auto-detect audience mode, relationship type, aspect ratio, and image count from content and request phrasing.

---

## Core rule

> Read signals from both the user's request AND the content itself. Content signals take priority when the request has no explicit target.

---

## Signal Detection Table

### From Request Phrasing

| User says | Mode | Style | Ratio |
|-----------|------|-------|-------|
| "小红书" / "种草" / "xhs" | XHS Story | Warm hand-drawn narrative | 3:4 |
| "公众号" / "微信" | WeChat Knowledge | Knowledge card sketchnote | 1:1 or 4:3 |
| "学术" / "论文" / "导师" / "汇报" | Academic | Clean infographic | 16:9 |
| "架构" / "系统" / "流程" / "技术" | Technical | Whiteboard diagram | 16:9 |
| "slide" / "PPT" / "演示" | Presentation | Whiteboard / infographic | 16:9 |
| "分享" / "情感" / "日记" / "故事" | XHS Story | Warm hand-drawn narrative | 3:4 |
| "知识" / "干货" / "教程" / "checklist" | WeChat Knowledge | Knowledge card sketchnote | 4:3 or 1:1 |
| nothing specific | General | Classic sketchnote | 4:3 |

### From Content Characteristics

| Content type | Mode | Signal strength |
|---|---|---|
| Personal narrative, first-person, emotional arc | XHS Story | Strong |
| Academic paper, system description, framework definition | Academic | Strong |
| Tutorial steps, numbered list, how-to | WeChat Knowledge | Strong |
| Code, API, architecture diagram, technical flow | Technical | Strong |
| Product intro with pain points and features | General / Technical | Medium |
| Mixed concept + some emotion | General | Weak (use General default) |

---

## Relationship Type Detection

After detecting mode, identify the relationship type to choose the right layout.

| Content structure | Relationship type | Best layout |
|---|---|---|
| One idea with branches | Concept | Center-radial |
| Step A → Step B → Step C | Flow | Linear flow |
| X vs Y | Comparison | Left-right split |
| Problem → Solution | Problem-Solution | P→S split |
| Many items / examples | Showcase | Grid |
| Top-down categories | Hierarchy | Tree |
| Root causes → one issue | Diagnosis | Fishbone / cause map |
| Emotional arc across time | Story | Timeline narrative |

Use `references/layout-guide.md` for detailed layout selection per relationship type.

---

## Image Count Heuristics

| Content volume | Relationship complexity | Recommended count |
|---|---|---|
| ≤ 5 main nodes, one relationship | Simple | 1 image |
| 5–8 nodes, or two distinct phases | Moderate | 2 images |
| 8+ nodes, or three clearly different phases | Complex | 3 images |
| XHS series format explicitly requested | Platform-driven | 3–5 images |

### Split rules

Split into 2 when:
- The content has two different jobs (e.g. problem framing + solution detail)
- The same image would require the reader to switch reading mode mid-image

Split into 3 when:
- Background → Process → Outcome structure
- The story has three distinct emotional or logical phases

Never split just to look thorough. Split only when clarity is materially better.

---

## Ambiguity Resolution

If content matches two modes equally strongly, do not ask a long question. Use this one-line pattern:

```
这内容可以做成 [Mode A] 或 [Mode B]，我先用 [Mode A]，不满意可以说换。
```

Example:
```
这内容可以做成小红书故事风或知识干货卡，我先用知识卡片风，不满意可以说换。
```

Then generate immediately. Let the user react.

---

## When Signals Conflict

If the request says one mode but the content clearly belongs to another:
- Respect the explicit request signal first
- Note briefly in the status line if the content seems to suggest a different mode

Example:
```
→ 按你的要求用小红书风（内容偏学术，如需切换可以说）
```
