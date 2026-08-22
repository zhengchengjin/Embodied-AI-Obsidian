---
type: concept
aliases: [潜在动作, Latent Action, LAM]
tags: [概念, 潜在动作, 表征学习]
---

# 潜在动作 Latent Action

潜在动作是从相邻观察的状态变化中学习出的低维变量，用来近似导致转移的物理动作。它让无动作标签视频也能提供“如何改变世界”的训练信号。

## 常见范式

- **IDM–FDM**：inverse dynamics 从当前/未来帧编码 latent，forward dynamics 用当前帧和 latent 重建未来。
- **帧差自编码**：压缩像素差、语义特征差或光流。
- **离散/连续瓶颈**：VQ-VAE 强调可复用动作原语；VAE 等连续 latent 更适合细粒度控制。

## 风险

IDM 看到了未来帧，可能发生 causal leakage，把未来图像内容直接编码进 latent，而非学到真实转移动力学。代理重建指标也不一定预测闭环策略性能。

## 关联论文

- [[03-论文/2026 - What Matters for Latent Actions in Robot Learning]]
