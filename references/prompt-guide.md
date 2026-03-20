# Prompt Guide

## Prompt 骨架

```text
Hand-drawn sketch note style illustration on pure white background, [topic description] in Chinese:

- MAIN TITLE: [main title text]
- TOP AREA: [content and placement]
- LEFT / CENTER / RIGHT AREA: [content and placement]
- BOTTOM AREA: [content and placement]
- ICONS: [list specific icons, e.g. lightbulb, arrow, gear, checkmark]
- CONNECTIONS: [arrows, lines, numbering to guide reading order]
- CHINESE LABELS: [short callout texts]
- COLOR ACCENTS: red on [X], green on [Y], blue on [Z], yellow on [W]
- CHARACTERS (optional): stick figure person at [position], [action/pose, e.g. pointing right / scratching head / giving thumbs up]
- SPEECH BUBBLES (optional): speech bubble from [character/area], containing Chinese text: "[文字内容]"

Style: Clean hand-drawn lines, sketch note aesthetic, simple icons, handwritten Chinese text, black ink primary with red/green/blue/yellow accents, minimalist, pure white background, high contrast, no gradients, no shadows, playful but professional
```

## 必填风格关键词（每个 prompt 必须包含）

- `Hand-drawn sketch note style`
- `pure white background`
- `black ink primary lines`
- `simple icons and illustrations`
- `handwritten Chinese text`
- `high contrast, no gradients, no shadows`
- `minimalist and clean`

## Prompt 编写规则

- **语言**：Prompt 用英文，图中可见文字写 `in Chinese` 或 `handwritten Chinese text`
- **位置**：明确写出每个元素的位置（top / left / center / right / bottom），不写抽象概念
- **连接**：明确箭头方向、编号顺序、连线关系
- **强调**：明确哪部分用哪种颜色突出
- **用词**：短句，避免含糊词（`nice`、`beautiful`、`cool` 等）
- **手绘人物**：有场景感或人物角色时，加入 stick figure + speech bubble，让图更生动

## 颜色约定

| 颜色 | 用途 |
|------|------|
| 黑色 | 主线条、主要文字 |
| 红色 | 问题、风险、警告、重要强调 |
| 绿色 | 解决方案、成功结果、正向反馈 |
| 蓝色/紫色 | 中性信息、技术概念 |
| 黄色/橙色 | 提示、补充说明、注意事项 |

## 禁止在 Prompt 中要求

- 真实照片质感
- 3D 渲染
- 渐变背景
- 阴影和复杂光效
- 大段密集文字
- 花哨装饰边框

## 多张图一致性尾缀

第 2 张及以后的图，在 prompt 末尾追加：

```
Keep the same hand-drawn sketch style, line weight, and color palette as the first image in this series.
```

## 任务类型 Prompt 模式

### 项目介绍
```text
... [project name] introduction sketch note in Chinese:
- MAIN TITLE: [project name] at top center, large, black ink
- LEFT AREA: problem/pain points with red icons (3 bullet points)
- RIGHT AREA: solutions/features with green checkmarks (3 bullet points)
- CENTER: large right-pointing arrow connecting left to right
- BOTTOM AREA: key result or benefit, yellow highlight box
- ICONS: warning triangle (red), rocket (green), star
- CHARACTERS: stick figure person at bottom-left, scratching head (showing confusion about the problem)
- SPEECH BUBBLES: bubble from character, containing Chinese text: "[用户痛点短句]"
```

### 概念解释
```text
... [concept] explanation sketch note in Chinese:
- MAIN TITLE: [concept] at top, large, underlined
- CENTER: large simple icon representing the concept
- SURROUNDING: 4-5 branches radiating outward, each with icon + short label
- CONNECTIONS: curved arrows from center to each branch
- COLOR: blue/purple for technical terms, black for main labels
```

### 流程说明
```text
... [process name] workflow sketch note in Chinese:
- MAIN TITLE: [process] at top center
- STEPS: numbered 1-N from left to right (or top to bottom)
- Each step: simple icon above, short Chinese label below, circle/box border
- ARROWS: right-pointing arrows between steps
- BOTTOM: final result/outcome in a rounded box, green accent
```

### 对比说明
```text
... [A] vs [B] comparison sketch note in Chinese:
- MAIN TITLE: [A] vs [B] at top center
- LEFT HALF: [A] with icon, 3-4 characteristics, red/orange accent
- RIGHT HALF: [B] with icon, 3-4 characteristics, green/blue accent
- CENTER DIVIDER: vertical dashed line
- BOTTOM: conclusion or recommendation, yellow highlight
```

### 教程步骤
```text
... [tutorial name] step-by-step sketch note in Chinese:
- MAIN TITLE: [tutorial] at top
- STEP CARDS: 3-5 cards arranged in grid or linear flow
- Each card: step number (circle), icon, short action label
- ARROWS: sequential flow arrows between cards
- BOTTOM: final result or tip box, green accent
```

### 作品回顾
```text
... [collection name] showcase sketch note in Chinese:
- MAIN TITLE: [name] at top
- GRID: 2x2 or 2x3 card layout
- Each card: item name, simple icon, 1-2 tag labels
- BORDERS: light dashed box for each card
- BOTTOM: summary or next-step note, yellow/orange accent
```
