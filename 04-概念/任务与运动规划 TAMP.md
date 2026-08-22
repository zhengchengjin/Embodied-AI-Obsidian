---
type: concept
aliases: [TAMP, Task and Motion Planning, 任务与运动规划]
tags: [概念, TAMP, 规划]
---

# 任务与运动规划 TAMP

TAMP 同时处理离散任务结构和连续几何/运动约束。例如“把胡萝卜放进锅里”既要决定开柜、抓取、移动等符号步骤，也要为每一步找到无碰撞、可达的轨迹。

## 与 VLM 的互补

- VLM：擅长自然语言、常识和高层子目标，但可能产生无观测依据的对象与步骤。
- TAMP：能验证运动可行性，但依赖相对完整和正确的世界状态。
- 主动感知：通过行动补齐隐藏状态，连接两者。

## 关联论文

- [[03-论文/2026 - Evidence-Gated Task and Motion Planning with VLMs]]
