---
type: moc
topic: VLA
updated: 2026-08-23
tags: [MOC, VLA, 机器人基础模型]
---

# 视觉-语言-动作模型 VLA

## 领域坐标

- [[01-主题索引/领域前沿与 SOTA 总览|领域前沿与 SOTA 总览]]：跟踪 LIBERO、RoboTwin、真实 OOD 与跨本体结果。

## 核心问题

- 如何把互联网尺度的视觉—语言先验转化为连续控制？
- 换机器人、换相机或换夹爪后，如何低成本缩小 embodiment gap？
- 微调新技能时，如何避免遗忘原有指令跟随与行为先验？
- 如何利用无动作标注视频扩展可训练数据？

## 本库论文

- [[03-论文/2026 - Fine-Tuning VLAs with Self-Demonstrated Generative Control|Fine-Tuning VLAs with Self-Demonstrated Generative Control]]：让冻结的基础策略在目标机器人上生成 rehearsal 数据，缓解灾难性遗忘。
- [[03-论文/2026 - What Matters for Latent Actions in Robot Learning|What Matters for Latent Actions]]：系统比较 41 个潜在动作设计选择，为 VLA 中训练和后训练提供经验规则。
- [[03-论文/2026 - DECOWAM|DECOWAM]]：把移动底盘、机械臂与相机自运动显式分解，连接 VLA 与世界模型路线。

## 相关概念

- [[04-概念/视觉-语言-动作模型 VLA|VLA 概念卡]]
- [[04-概念/潜在动作 Latent Action|潜在动作]]
- [[04-概念/世界-动作模型 WAM|WAM]]
