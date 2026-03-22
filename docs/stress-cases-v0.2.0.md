# hand-drawn-note-generator v0.2.0 — Stress Cases

日期：2026-03-22  
目标：验证当前 v0.2.0 重构后，这个 skill 是否真的围绕 visual distillation 站住，而不是重新滑回固定画风 prompt 工具。

重点压测：
- style lock-in
- layout mismatch
- content overload
- prompt bloat
- ratio rigidity
- premature style questioning

---

## Test rubric

每个案例按这 4 项判断：
1. **Pressure point** 这个案例在逼什么错误暴露
2. **Expected behavior** 当前 skill 应采取什么动作
3. **Pass / Partial / Fail** 当前 contract 是否足够支撑
4. **Reason** 原因

---

## Case 1 — User only wants content distillation first
- Pressure point: premature style questioning
- Scenario: 用户说“先帮我把这篇文章拆成适合出图的结构”，并没有要求立刻出图。
- Expected behavior: 先做 message distillation / layout proposal，不急着问 style。
- Result: PASS
- Reason: `SKILL.md` 已把 style/ratio 放到结构之后。

## Case 2 — User explicitly wants research-style output
- Pressure point: style lock-in
- Scenario: 用户明确说“我想要科研风示意图，不要太像随手绘笔记”。
- Expected behavior: 使用 research / academic preset，不把 output 拉回 casual sketchnote。
- Result: PASS
- Reason: `style-options.md` 已把 user preference 置于 preset 之上。

## Case 3 — User wants vertical mobile-sharing output
- Pressure point: ratio rigidity
- Scenario: 用户说要发小红书 / 手机端长图。
- Expected behavior: 推荐 `3:4` / `4:5` 等更合适比例，而不是默认 `4:3`。
- Result: PASS
- Reason: ratio 已被降为可调参数。

## Case 4 — Dense article with too many concepts
- Pressure point: content overload
- Scenario: 一篇长文同时有背景、原理、方法、案例、结论。
- Expected behavior: 拆图，不强行一张塞完。
- Result: PASS
- Reason: anti-overload 与 split logic 已写入 layout guide / SKILL.

## Case 5 — Good-looking style but weak structure
- Pressure point: pretty-but-unclear failure
- Scenario: 用户给了很强风格偏好，但原内容结构仍然混乱。
- Expected behavior: 先稳定 message / layout，再写风格 prompt。
- Result: PASS
- Reason: 新核心规则是 structure first, style second。

## Case 6 — User says “just pick a style for me”
- Pressure point: default behavior under low preference
- Scenario: 用户不在意风格，只想尽快出结果。
- Expected behavior: skill 可以自行选合理默认，但应保持简短说明。
- Result: PASS
- Reason: style-options 允许 default choice when user does not care。

## Case 7 — Comparison content accidentally routed to concept layout
- Pressure point: layout mismatch
- Scenario: 输入本质是 A vs B 对比，但表面关键词不明显。
- Expected behavior: 依据 relationship type 选 comparison layout，而不是只看关键词。
- Result: PASS
- Reason: layout guide 已从 signal-word mapping 升级为 relationship-first。

## Case 8 — Prompt grows because content was not distilled
- Pressure point: prompt bloat
- Scenario: agent 试图把原文大量原句塞进 prompt。
- Expected behavior: 回到上游 distillation，减少节点和标签。
- Result: PASS
- Reason: prompt-guide 已把“prompt 越写越长通常是上游问题”写死。

## Case 9 — User asks for clean knowledge card, not sketch mess
- Pressure point: style diversity
- Scenario: 用户想要更适合知识分享平台的清爽卡片感。
- Expected behavior: 使用 clean knowledge card preset，而不是强推手绘小人/对话框。
- Result: PASS
- Reason: style presets 已分离 playful vs clean。

## Case 10 — User wants almost no color
- Pressure point: old color assumptions
- Scenario: 用户明确要极简黑白，最多一点灰色。
- Expected behavior: 走 minimal monochrome diagram preset，不强加彩色强调。
- Result: PASS
- Reason: monochrome preset 已存在。

## Case 11 — Style varies, but hierarchy must remain readable
- Pressure point: style overpowering clarity
- Scenario: 用户不断修改 style，但内容层级容易被冲散。
- Expected behavior: 始终保住 title > nodes > support hierarchy。
- Result: PASS
- Reason: prompt-guide 的 universal layer 先保 hierarchy。

## Case 12 — Two-image series needs consistency but not total rigidity
- Pressure point: over-constraining series style
- Scenario: 同一篇内容拆成两张，但第二张内容类型略有变化。
- Expected behavior: 保持 visual language continuity，但不要把 prompt 限死得毫无弹性。
- Result: PASS
- Reason: consistency rule 已改成 softer continuity language。

## Case 13 — User asks for prompt only, no generation
- Pressure point: model dependency
- Scenario: 当前环境没有 image tool，用户只想拿 prompt 自己去别处生成。
- Expected behavior: 交付 prompt + layout + ratio/style recommendation。
- Result: PASS
- Reason: skill 始终保留 portable prompt path。

## Case 14 — The task is really a hierarchy, not a flow
- Pressure point: surface wording trap
- Scenario: 用户输入里提到“步骤”，但实际是层级框架，不是操作流。
- Expected behavior: 选 hierarchy tree，不机械选 linear flow。
- Result: PASS
- Reason: relationship-first layout logic。

## Case 15 — User wants style freedom after structure is confirmed
- Pressure point: style preset dominance
- Scenario: 结构已经确定后，用户临时想从 casual 改成 academic。
- Expected behavior: 允许覆盖 style layer，不要求重做整个 skill identity。
- Result: PASS
- Reason: style is downstream parameter now.

---

## Score

- **Pass:** 15
- **Partial pass:** 0
- **Fail:** 0

---

## Bottom line

The current v0.2.0 contract already holds up much better against the most likely failure of this project:

# mistaking one nice-looking hand-drawn style for the real value of the skill

The reset toward visual distillation appears directionally correct.
What still remains for later is stronger example coverage and possibly a larger evaluator-like case set.
