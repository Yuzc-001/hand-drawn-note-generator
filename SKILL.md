---
name: hand-drawn-note-generator
description: >
  将项目介绍、概念解释、流程说明、教程步骤、对比分析、作品回顾等内容转化为手绘笔记风格图片。
  Use when user asks for 手绘笔记、sketchnote、手绘图、笔记图、项目介绍图、概念解释图、流程图、教程图，
  or wants content visualized as a minimalist sketch-note image with white background, black ink lines, and color highlights.
  Trigger phrases include 帮我做一张手绘图、生成笔记图、画成手绘笔记、sketchnote this、visualize as sketch note.
---

# Hand-Drawn Note Generator

将复杂内容压缩成一眼能懂的手绘笔记图：纯白背景、黑线为主、彩色重点强调、4:3 比例。

## Workflow

### Step 1: 提炼核心信息

从输入中提取：
- **主题**：一句话概括这张图要表达什么
- **关键节点**：3-6 个最值得展示的概念、步骤或要点
- **逻辑关系**：并列 / 递进 / 流程 / 因果 / 对比
- **视觉重点**：哪些信息需要重点强调
- **布局判断**：根据逻辑关系，对照 [layout-guide.md](references/layout-guide.md) 中的信号词映射，初步确定每张图的布局类型

拆图决策：
- **1 张**：主题单一，3-5 个关键点
- **2 张**：包含"背景 + 方案"或"概念 + 示例"
- **3 张**：背景问题 + 流程步骤 + 结果案例

完成提炼后确认：`我理解核心是【主题】，包含【关键点】，用【X】张图呈现，第 1 张用【布局类型】布局。是否调整？`

如果用户明确要求"直接生成"，跳过确认，直接进入 Step 2。

### Step 2: 选择布局

根据内容关系选布局，参考 [layout-guide.md](references/layout-guide.md) 中的信号词 → 布局映射表。

核心原则：
- 主标题最大，放顶部或视觉中心
- 箭头、编号、连线引导阅读顺序
- 足够留白，避免拥挤
- 图标和插图承担主要表达，文字做补充
- 如有合适场景，加入手绘小人（stick figure）和对话气泡增加生动感

### Step 3: 编写 Prompt 并生成图片

按 [prompt-guide.md](references/prompt-guide.md) 的骨架和规则写 Prompt（必须用英文，图中可见文字用中文）。

**多张图的视觉一致性**：
- 第 1 张正常生成
- 第 2 张起，在 prompt 末尾加上：`Keep the same hand-drawn sketch style, line weight, and color palette as the first image in this series.`

**生成前必须先展示 prompt**：

每张图生成前，先在对话中输出完整 prompt：

````
📋 **Prompt（可复制用于其他工具或优化）**

```
[此处为完整英文 prompt]
```
````

然后再调用图像生成工具，参数：
```
aspect_ratio: "4:3"
```

使用当前环境可用的图像生成工具（imageGenerate 或其他）；不要硬编码 model 名称，优先使用质量最高的可用模型。

### Step 4: 完成汇总

所有图片生成完毕后，输出以下汇总：

```
✅ 生成完成

📌 主题：[主题]
🖼 共 [X] 张图，布局：[布局1] / [布局2] / ...

💡 Prompt 已在上方展示，可直接：
  - 复制给其他图像工具（Midjourney、FLUX、Ideogram 等）重新生成
  - 发给提示词工程师优化风格
  - 留存备用，下次同类内容可直接复用

如需调整，告诉我要改哪一项：
布局 / 文字内容 / 颜色强调 / 元素增减 / 拆图张数 / 图标风格 / 加手绘人物
```

## Response Rules

- 先提炼信息并确认，再生成图片（除非用户要求直接生成）
- 一张图信息超载时主动拆图，不强行塞满
- 如果平台没有 `imageGenerate`，产出高质量 Prompt + 布局说明 + 张数建议作为交付物
- 用户给大段文字时，先压缩信息，不原样塞进图里
- 用户给流程/框架/文章时，提炼成图标 + 短标签，不用长句段落
- **每次生成前都要展示完整 prompt，不可跳过**
