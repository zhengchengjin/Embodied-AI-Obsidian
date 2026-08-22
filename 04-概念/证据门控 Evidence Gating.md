---
type: concept
aliases: [Evidence Gating, 证据门控]
tags: [概念, 主动感知, 可靠性]
---

# 证据门控 Evidence Gating

证据门控是在高层规划或不可逆执行之前检查：当前结论来自真实观测，还是模型先验？当证据不足时，系统选择追加探索；当目标不可确认或不可行时，系统选择停止。

## 三态接口

- `ready_to_plan`：证据足以进入任务规划。
- `acquire_more`：继续执行低风险、可逆的取证动作。
- `halt`：目标无法确认或不可行，停止无效尝试。

## 适合的指标

- 缺失对象时的合理停止率。
- 对不存在对象的平均执行尝试数。
- 获取证据所需动作数、时间和风险。
- 错停与漏停的代价。

## 关联论文

- [[03-论文/2026 - Evidence-Gated Task and Motion Planning with VLMs]]
