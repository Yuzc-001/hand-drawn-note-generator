# hand-drawn-note-generator v0.2.0 — Stress Cases (Batch 2)

日期：2026-03-22  
目标：继续用更狠的案例压测 v0.2.0，确认这个 skill 不会在“风格自由化”之后失去结构判断力，也不会在“结构优先”之后忽视真实使用场景。

重点压测：
- style ambiguity under real publishing context
- structure vs style conflict
- ratio-driven layout pressure
- multi-image split boundary
- fake clarity in research / knowledge-card modes

---

## Test rubric

每个案例按这 4 项判断：
1. **Pressure point** 这个场景在逼什么错误暴露
2. **Expected behavior** 当前 skill 应采取什么动作
3. **Pass / Partial / Fail** 当前 contract 是否足够支撑
4. **Reason** 原因

---

## Case 16 — User style vague, platform very clear
- Pressure point: style ambiguity with strong destination constraints
- Scenario: 用户只说“做一张知识分享图”，没说风格，但明确要发小红书。
- Expected behavior: 先依据发布场景优先考虑移动端友好比例与清晰分块，再做最小风格确认或默认选择。
- Result: PASS
- Reason: style-options 已允许 context-sensitive style/ratio choice，而不是盲问风格大全。

## Case 17 — User wants research style for content that is mostly onboarding
- Pressure point: style overpowering task function
- Scenario: 内容本质是新手入门说明，但用户说“做得科研一点”。
- Expected behavior: 接受更克制风格，但不能牺牲 onboarding clarity；仍应保留明显顺序和可读节点。
- Result: PASS
- Reason: universal prompt requirements 把 hierarchy / readability 放在 style 之上。

## Case 18 — User wants “very clean card style” for a root-cause analysis
- Pressure point: style flattening analytical structure
- Scenario: 根因分析内容想做成干净卡片风，容易把因果结构冲平。
- Expected behavior: 保留 cause-map / fishbone 逻辑，不因 style 变 clean 就丢掉 diagnosis structure。
- Result: PASS
- Reason: layout still follows relationship type first.

## Case 19 — One-image request should actually become three
- Pressure point: user request versus overload reality
- Scenario: 用户嘴上说“做一张图”，但内容明显包含背景、方法、案例三层任务。
- Expected behavior: 建议拆 2–3 张，并说明一张会过载。
- Result: PASS
- Reason: anti-overload rules permit override of naive one-image request.

## Case 20 — Three-image split would actually hurt comprehension
- Pressure point: unnecessary sophistication
- Scenario: 内容只有一个概念和三个支持点，但为了“更专业”想拆成三张。
- Expected behavior: 拒绝形式化拆分，保留一张强图。
- Result: PASS
- Reason: split exists for clarity, not for sophistication.

## Case 21 — Research style turns into cold, unreadable output
- Pressure point: fake seriousness
- Scenario: agent 把“科研风”理解成标签更长、色彩更少、结构更硬，结果更难看懂。
- Expected behavior: research style should mean cleaner and more analytical, not denser or colder by itself.
- Result: PASS
- Reason: prompt-guide now treats style as expression layer, not permission for clutter.

## Case 22 — Knowledge card style becomes “tidy wall of text”
- Pressure point: fake cleanliness
- Scenario: 用户要 clean knowledge card，agent 只是把文字排整齐，但没有视觉节点和 hierarchy。
- Expected behavior: 仍要保持 node-based composition, not text block beautification.
- Result: PASS
- Reason: universal layer requires short labels and visible hierarchy.

## Case 23 — User says “you decide,” but article is highly technical
- Pressure point: lazy default selection on hard content
- Scenario: 用户不指定风格，内容高度技术化，且最终读者偏专业。
- Expected behavior: 默认选择更克制、更分析型的 style family，而不是总落回 casual sketchnote。
- Result: PASS
- Reason: style defaults may adapt to content and audience context.

## Case 24 — User wants playful hand-drawn style for executive summary
- Pressure point: style desire versus audience fit
- Scenario: 用户自己偏爱手绘感，但受众是偏正式汇报场景。
- Expected behavior: 至少提醒 playful style may reduce formal fit, or offer a cleaner variant.
- Result: PASS
- Reason: style confirmation can include minimal fit warning when it materially affects outcome.

## Case 25 — Aspect ratio change breaks layout logic
- Pressure point: ratio-driven structural distortion
- Scenario: 原本适合横向比较的内容被强制做成竖版手机图。
- Expected behavior: 重排 layout，而不是只把横版内容挤进竖版。
- Result: PASS
- Reason: ratio is now part of prompt construction, not post-hoc decoration.

## Case 26 — Vertical ratio with too many branches
- Pressure point: ratio mismatch with radial concept map
- Scenario: 一个 5 分支中心辐射图被要求做成狭长竖版。
- Expected behavior: 改布局或拆图，而不是勉强塞进 narrow frame。
- Result: PASS
- Reason: layout/ratio fit should be jointly judged.

## Case 27 — User asks for prompt only, then later wants another style version
- Pressure point: portability across style revisions
- Scenario: 第一次只要学术风 prompt，第二次想要同结构的轻松手绘版。
- Expected behavior: 保留结构层稳定，只替换 style layer 和必要 prompt expression。
- Result: PASS
- Reason: style is downstream parameter now.

## Case 28 — Article has both comparison and workflow elements
- Pressure point: mixed relationship types
- Scenario: 内容前半是 A/B 对比，后半是具体落地流程。
- Expected behavior: 判断是否双图更清楚，而不是强行在一张图里混双关系。
- Result: PASS
- Reason: split logic explicitly supports mixed jobs.

## Case 29 — User keeps asking for “more style,” clarity starts dropping
- Pressure point: style escalation degrading readability
- Scenario: 多轮修改后 prompt 越来越强调氛围感和 aesthetic 标签。
- Expected behavior: hold the line on clarity and note when added style is reducing readability.
- Result: PASS
- Reason: universal prompt requirements cap style excess.

## Case 30 — Audience is children, but content is technical
- Pressure point: audience adaptation versus conceptual precision
- Scenario: 解释技术概念给低龄读者，风格需更友好，但内容不能失真。
- Expected behavior: style can become friendlier, but concept simplification must remain faithful.
- Result: PASS
- Reason: distillation means compressing meaning, not distorting it.

## Case 31 — User provides exact style ref but poor content structure
- Pressure point: style reference dominating the whole task
- Scenario: 用户发来一张很喜欢的图风，但原文内容很乱。
- Expected behavior: 先拆结构，再对齐 style ref；不能反过来从 style 图直接硬套内容。
- Result: PASS
- Reason: structure first remains core rule.

## Case 32 — User wants “same style as before,” but new task is totally different
- Pressure point: style continuity wrongly overriding task fit
- Scenario: 上次是流程图，这次是概念框架，但用户说保持同风格。
- Expected behavior: 保持 visual family continuity if useful, but still re-evaluate layout for the new task.
- Result: PASS
- Reason: style continuity does not freeze layout choice.

## Case 33 — Visual hierarchy survives, but labels are still too long
- Pressure point: text compression failure
- Scenario: 整体结构没错，但图中文字仍接近短句段落。
- Expected behavior: continue compressing labels; image should not become text poster.
- Result: PASS
- Reason: prompt-guide repeatedly enforces short labels.

## Case 34 — User asks for “more detailed,” agent starts adding more nodes instead of clarifying nodes
- Pressure point: detail request causing overload
- Scenario: 用户想更完整，agent 通过增加节点数量来回应。
- Expected behavior: add precision where needed, not indiscriminately add nodes; split if necessary.
- Result: PASS
- Reason: detail and overload are not the same thing.

## Case 35 — Comparison requested, but actual decision criterion is asymmetric
- Pressure point: forced balance in unbalanced comparison
- Scenario: A 与 B 不是同权重比较，A 只是过渡方案，B 才是推荐方案。
- Expected behavior: comparison layout can still work, but hierarchy should show recommendation asymmetry.
- Result: PASS
- Reason: layout should reveal the real relationship, not fake symmetry.

## Case 36 — User asks for maximum portability across image tools
- Pressure point: tool-agnostic prompt discipline
- Scenario: 用户明确要在 Midjourney、FLUX、Ideogram 之间复用 prompt。
- Expected behavior: keep style wording portable, avoid model-specific hacks.
- Result: PASS
- Reason: portability is now a stated success criterion.

## Case 37 — User wants exact ratio but content fit is poor
- Pressure point: hard ratio constraint versus readability
- Scenario: 用户坚持用 `1:1`，但内容明显更适合横向流程。
- Expected behavior: respect the ratio request but adjust layout or suggest splitting, rather than silently degrading clarity.
- Result: PASS
- Reason: user owns ratio, but skill still owns readability judgment.

## Case 38 — Style freedom tempts the skill into endless options listing
- Pressure point: choice explosion
- Scenario: 用户只问“做成图”，agent 想列 8 种风格给他选。
- Expected behavior: keep confirmation minimal and decision-relevant.
- Result: PASS
- Reason: style-options explicitly forbids style survey behavior.

## Case 39 — Article is already highly structured; skill tries to re-invent structure anyway
- Pressure point: needless restructuring
- Scenario: 输入本身就是很清晰的 3-step flow。
- Expected behavior: preserve the existing strong structure, only tighten for visual use.
- Result: PASS
- Reason: distillation should compress and clarify, not rewrite for vanity.

## Case 40 — User wants one style for cover image, another for content panels
- Pressure point: multi-style series handling
- Scenario: 同一组输出中封面图想更吸引眼球，内容图想更清晰克制。
- Expected behavior: allow controlled variation if it serves the publishing use case.
- Result: PASS
- Reason: consistency is useful, but not an absolute religion.

---

## Score

- **Pass:** 25
- **Partial pass:** 0
- **Fail:** 0

---

## Bottom line

Batch 2 suggests the v0.2.0 reset is holding under a more realistic pressure set:

- style is no longer the product center
- but style is also not being ignored
- structure still leads
- context now matters
- ratio is treated as real composition pressure instead of a decorative afterthought
