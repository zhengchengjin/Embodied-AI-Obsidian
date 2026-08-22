---
type: concept
aliases: [VLA, Vision-Language-Action Model]
tags: [概念, VLA, 机器人基础模型]
---

# 视觉-语言-动作模型 VLA

VLA 将视觉观察、自然语言指令和机器人动作放在统一策略接口中。典型模型使用预训练 VLM 获取语义先验，再用机器人轨迹训练离散动作 token、连续 action chunk 或 flow-matching action expert。

## 主要难点

- 机器人数据远少于图文数据。
- 不同 embodiment 的关节、夹爪、相机和控制频率不一致。
- 少量下游微调容易造成灾难性遗忘和视觉捷径。
- 语义理解强不等于接触、动力学和停止时机可靠。

## 本库例子

- [[03-论文/2026 - Fine-Tuning VLAs with Self-Demonstrated Generative Control]]
- [[03-论文/2026 - What Matters for Latent Actions in Robot Learning]]
- [[03-论文/2026 - DECOWAM]]
