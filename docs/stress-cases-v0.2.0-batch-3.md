# hand-drawn-note-generator v0.2.0 — Stress Cases (Batch 3)

日期：2026-03-22
目标：继续用更极端、更贴近真实发布压力的场景压测当前 v0.2.0。

这批重点不是再验证“风格可以自定义”，而是验证：

# 当风格、平台、比例、参考图、用户审美偏好同时拉扯时，这个 skill 还能不能守住 message center？

重点压测：
- reference-image overfitting
- cross-platform adaptation
- prompt-only shortcut failure
- multi-style series coherence
- aesthetic drift away from content
- text-wall relapse

---

## Test rubric

每个案例按这 4 项判断：
1. **Pressure point** 这个场景在逼什么错误暴露
2. **Expected behavior** 当前 skill 应采取什么动作
3. **Pass / Partial / Fail** 当前 contract 是否足够支撑
4. **Reason** 原因

---

## Case 41 — User gives a beautiful reference image, but the content relationship is different
- Pressure point: reference-image overfitting
- Scenario: 用户给了一张很喜欢的图，但参考图是中心辐射结构，而当前内容本质是流程说明。
- Expected behavior: 吸收 style vibe，但不能照抄 reference layout；layout 仍应服从内容关系。
- Result: PASS
- Reason: layout-guide 已明确 relationship-first，style/ref 不能覆盖结构判断。

## Case 42 — User says “just make it look like this” and gives an overloaded sample
- Pressure point: bad reference normalizing clutter
- Scenario: 参考图本身信息过满、可读性一般，但用户觉得“好看”。
- Expected behavior: 不机械复刻拥挤感；保留想要的 style language，但继续执行 anti-overload judgment。
- Result: PASS
- Reason: visual distillation is the product center, not imitation fidelity alone.

## Case 43 — Same content needs three platform versions
- Pressure point: cross-platform adaptation
- Scenario: 同一份内容要同时发小红书、PPT、Twitter/X 卡片。
- Expected behavior: 结构层尽量稳定，但比例、信息密度和 style expression 应按平台适配。
- Result: PASS
- Reason: ratio/style 已变成下游参数，而结构层可以复用。

## Case 44 — User wants prompt only and says “don’t explain”
- Pressure point: prompt-only shortcut failure
- Scenario: 用户只要最终 prompt，不要过程解释。
- Expected behavior: 内部仍做 distillation / layout judgment，只是不展开长说明；交付 prompt 时保持结构正确。
- Result: PASS
- Reason: output can be short, but contract does not allow skipping upstream reasoning.

## Case 45 — Prompt-only request with ambiguous destination
- Pressure point: hidden ambiguity under compressed interaction
- Scenario: 用户只说“给我 prompt”，但没说是竖版知识卡还是横版演示图。
- Expected behavior: 仍问最小必要问题，或给出一版默认并明确可替换 ratio/style。
- Result: PASS
- Reason: minimal clarification remains valid even under terse-output preference.

## Case 46 — User keeps changing style every round
- Pressure point: aesthetic drift
- Scenario: 第一轮要学术风，第二轮要更像白板，第三轮又想偏知识卡。
- Expected behavior: 保持 message / layout 核心稳定，只让 style layer 演化，不让结构层跟着乱漂。
- Result: PASS
- Reason: style is downstream parameter now.

## Case 47 — User wants a highly branded aesthetic, but content is still under-distilled
- Pressure point: branding pressure against clarity
- Scenario: 用户更在意“像某博主/某品牌”，但内容本身节点还没收干净。
- Expected behavior: 先继续压缩内容，再谈 aesthetic mimicry。
- Result: PASS
- Reason: structure first, style second.

## Case 48 — Multi-image series with mixed roles
- Pressure point: series coherence vs role separation
- Scenario: 同一组输出里，封面图负责吸引，后续图负责解释。
- Expected behavior: 保持系列视觉家族感，但允许 cover 与 content panels 在 layout/styling 上有控制地差异化。
- Result: PASS
- Reason: consistency is useful, not absolute religion.

## Case 49 — User wants “more complete,” image begins turning into a text poster
- Pressure point: text-wall relapse
- Scenario: 多轮补充后，可见文字越来越多，图开始失去视觉摘要感。
- Expected behavior: 守住 label compression；必要时拆图，而不是继续把细节塞进同一张图。
- Result: PASS
- Reason: prompt-guide universal layer + anti-bloat rules jointly prevent this.

## Case 50 — Comparison image where one side has much more material
- Pressure point: fake symmetry
- Scenario: A/B 对比里 A 只有 2 点，B 有 6 点，强行左右对称会误导。
- Expected behavior: 调整 hierarchy 或拆图，不能为了“整齐”伪造对称。
- Result: PASS
- Reason: layout should reveal the true relationship, not cosmetic balance.

## Case 51 — User wants “exact same style as this creator,” but licensing or exact mimicry is undesirable
- Pressure point: style imitation boundary
- Scenario: 用户要高度模仿某具体创作者视觉语言。
- Expected behavior: 可吸收方向性特征，但不应把 skill 退化成 exact-copy engine；应转成 style-family level guidance。
- Result: PASS
- Reason: current preset/override structure supports style family guidance over exact clone identity.

## Case 52 — Highly technical content for a broad audience
- Pressure point: clarity under abstraction compression
- Scenario: 内容专业性高，但目标读者是泛知识受众。
- Expected behavior: 压缩术语密度、保留核心关系、选更友好的 explanatory layout，而不是直接简化成错误说法。
- Result: PASS
- Reason: distillation is compression without conceptual betrayal.

## Case 53 — Simple content, but user asks for a three-panel carousel
- Pressure point: user format request vs unnecessary split
- Scenario: 内容本来一张图最强，但用户想做 3 张轮播。
- Expected behavior: 可以服务该发布形式，但每张必须各有明确角色，不能把一个简单概念硬切成三片空图。
- Result: PASS
- Reason: split must still serve clarity and publishing logic.

## Case 54 — User wants one giant poster from a long article
- Pressure point: scope denial
- Scenario: 一篇长文章希望“全部浓缩到一张海报”。
- Expected behavior: 明确指出单图会过载，提供 multi-image 或 hierarchical summary alternative。
- Result: PASS
- Reason: anti-overload remains a hard guardrail.

## Case 55 — User provides a perfect structure already, but asks for “optimize it”
- Pressure point: unnecessary intervention
- Scenario: 输入本身已是清晰的 4-step flow + 3 key notes。
- Expected behavior: 少改结构，多做 visual tightening；不能为了体现 skill 价值而硬改框架。
- Result: PASS
- Reason: distillation should clarify, not perform cleverness.

## Case 56 — User wants a style family that conflicts with visible text density
- Pressure point: style-density conflict
- Scenario: 用户想要极简极冷风，但内容标签很多。
- Expected behavior: 要么继续压缩内容，要么提示该 style 下需更多拆分；不能同时保留高密度和极简假象。
- Result: PASS
- Reason: style cannot erase density constraints.

## Case 57 — User asks for a side-by-side comparison, but final goal is recommendation
- Pressure point: comparison not equal to neutrality
- Scenario: 表面是对比，真实任务是帮助选择。
- Expected behavior: 保留 comparison layout，但 bottom-line 或 emphasis 应体现 recommendation logic。
- Result: PASS
- Reason: message goal outranks template purity.

## Case 58 — Platform wants 16:9, but content is modular showcase
- Pressure point: ratio-content mismatch
- Scenario: 展示型内容天然适合 grid，而用户又要 16:9 横版。
- Expected behavior: 调整为横向网格或分栏 showcase，不是简单拉宽原方卡结构。
- Result: PASS
- Reason: ratio should drive recomposition, not stretching.

## Case 59 — User only wants “something visually impressive”
- Pressure point: spectacle replacing meaning
- Scenario: 用户表达目标很虚，只说想“更惊艳一点”。
- Expected behavior: 仍需抓回最小 message core，不能直接把任务变成 decorative prompt stacking。
- Result: PASS
- Reason: the skill’s value is visual distillation, not empty visual escalation.

## Case 60 — Final output looks styled correctly, but the main takeaway is still unclear
- Pressure point: false success by aesthetic correctness
- Scenario: prompt 命中了用户喜欢的风格，比例也对，但读者还是看不出这张图到底要说什么。
- Expected behavior: 判定为失败的 output direction，回到 message distillation / layout correction，而不是把 style hit 当成功。
- Result: PASS
- Reason: product center explicitly prioritizes message clarity over aesthetic match.

---

## Score

- **Pass:** 20
- **Partial pass:** 0
- **Fail:** 0

---

## Bottom line

Batch 3 suggests the v0.2.0 reset is holding under a sharper real-world test:

- reference images do not dominate structure
- platform adaptation does not destroy message center
- prompt-only requests do not excuse lazy structure judgment
- multi-style freedom does not dissolve coherence
- aesthetic success is not mistaken for communication success
