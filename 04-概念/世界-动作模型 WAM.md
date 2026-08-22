---
type: concept
aliases: [WAM, World-Action Model, 世界动作模型]
tags: [概念, WAM, 世界模型, 视频预测]
---

# 世界—动作模型 WAM

WAM 在同一接口中预测未来观察和机器人动作。相较只输出动作的 VLA，它提供显式未来 rollout，可把物体运动、接触结果和视角变化作为控制先验。

## 评估层次

1. 开环视频：MSE、PSNR、SSIM、LPIPS。
2. 开环动作：MSE、MAE、轨迹误差。
3. 闭环任务：成功率与完成时间。
4. 过程鲁棒性：协调、位移扰动、静止保持和恢复。

只做到第 1 层不足以证明控制价值。

## 关联论文

- [[03-论文/2026 - DECOWAM]]
- [[03-论文/2026 - What Matters for Latent Actions in Robot Learning]]
