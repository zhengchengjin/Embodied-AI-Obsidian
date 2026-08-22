---
type: paper
title: Evidence-Gated Task and Motion Planning with Vision-Language Models
authors: [Tsunehiko Tanaka, Matthew Stephenson, Alistair Macvicar, Edgar Simo-Serra]
year: 2026
published: 2026-08-20
venue: arXiv preprint
arxiv: 2608.20084
status: 速读
rating: 4.3
topics: [TAMP, VLM, 部分可观测, 主动感知, 可靠性]
tags: [paper, TAMP, VLM, 主动感知]
---

# Evidence-Gated Task and Motion Planning with VLMs

## 一句话

不让 VLM 直接把常识当成环境事实，而是先规划可逆探索、获取视觉证据，再决定正式规划、继续探索或停止。

## 问题

在“做鸡汤”之类长程任务中，VLM 会根据常识补出盐、胡椒或胡萝卜等对象，但这些物体可能藏在柜中，也可能根本不存在。若 [[04-概念/任务与运动规划 TAMP|TAMP]] 直接执行 VLM 子目标，就会反复规划不可行操作。

## 方法

EAFG 包含三段：Evidence Acquisition 由 VLM 提出打开柜门、移动遮挡物、查看容器内部等可逆探索子目标；TAMP 将其落实为几何与运动可行的动作；Feasibility Gate 根据按时间排列的证据图像，输出 ready_to_plan、acquire_more 或 halt。正式任务动作在证据充分后才生成。实验限制最多 5 轮取证，每个取证子目标最多重规划 3 次，并禁止探索阶段提前执行加热或投料等不可逆任务动作。

## 关键结果

- 未明确提盐和胡椒时，完整配方完成率：GPT-5.5 从 0.05 升到 0.40；Gemini-3.5-Flash 从 0 升到 0.20。
- 明确要求但实际缺少胡萝卜时，GPT-5.5 合理停止率从 0.45 升到 0.90，无效缺失物体尝试从 4.00 降到 0.55。
- Gemini-3.5-Flash 的停止率从 0.40 升到 1.00，无效尝试从 2.40 降到 0。
- 当指令明确且对象都存在时，EAFG 对 GPT-5.5 提高完整完成率，但对 Gemini 略有下降，说明取证并非无成本。

## 我的判断

论文的接口设计比绝对成功率更重要：VLM 的先验适合产生“验证假设的行动”，不适合直接声明当前世界状态。把停止作为一等决策，并报告 missing-object attempt count，是比普通成功率更能反映可靠性的评估方式。

## 局限

- 取证子目标仍依赖 TAMP 成功执行；若开柜或移障失败，gate 可能基于不足证据误判。
- 实验集中在单一厨房做汤场景，每条件 20 次，任务和机器人多样性有限。
- 最多五轮取证与人工定义的可逆操作集合，尚未覆盖开放世界中的探索成本和风险估计。
- 证据拼图随任务长度增长可能超出 VLM 的视觉上下文和注意力稳定性。

## 可复用启发

1. 将“观测到”与“常识推测”分开记录。
2. 主动探索尽量限制为可逆、低风险动作。
3. 可靠性指标加入 halt success、无效尝试数和取证成本。
4. 下一步应加入 manipulation recovery，并对证据不充分进行显式置信度建模。

## 资源

- [arXiv 摘要](https://arxiv.org/abs/2608.20084)
- [HTML 全文](https://arxiv.org/html/2608.20084v1)

## 关联

- [[01-主题索引/任务与运动规划 TAMP]]
- [[04-概念/证据门控 Evidence Gating]]
- [[02-周报/2026-W34 具身智能与机器人论文周报]]
