---
type: paper
title: Fine-Tuning VLAs with Self-Demonstrated Generative Control for Multi-Task Manipulation
authors: [Prachi Garg, Steve Xing, Prahit Yaugand, Saurabh Gupta, Derek Hoiem]
year: 2026
published: 2026-08-19
venue: arXiv preprint
arxiv: 2608.19490
status: 速读
rating: 4.6
topics: [VLA, 持续学习, 生成式回放, 机器人操作, ALOHA]
tags: [paper, VLA, 自监督, 灾难性遗忘]
---

# Fine-Tuning VLAs with Self-Demonstrated Generative Control

## 一句话

让冻结的基础 VLA 在目标机器人上生成自己的控制轨迹，将其作为回放数据与少量专家演示混合微调，从而同时缩小 embodiment gap 和缓解灾难性遗忘。

## 问题

[[04-概念/视觉-语言-动作模型 VLA|VLA]] 换到相机位置、夹爪或关节配置略有不同的新机器人后，零样本性能可能骤降；只用目标机器人专家数据微调虽然能学会新任务，却会遗忘原有指令跟随和放置、推动等先验行为。

## 方法

作者使用 π0.5 作为基础策略。先冻结它，在目标机器人和目标环境中针对多种文本指令在线 rollout，记录图像、状态和策略输出的连续动作块，作为 self-demonstrations；再与专家数据以 1:1 采样混合进行 imitation fine-tuning。它类似生成式回放，但生成器就是基础策略本身，且数据是在目标 embodiment 上通过物理交互产生，因此没有旧机器人到新机器人的域差。

## 关键结果

- 真实 ALOHA 上仅用约 14 分钟专家遥操作数据。纯专家多任务微调在红/绿方块拾取上成功率 65%，加入自演示后达到 90%。
- 对没有专家 place 演示的 pick-and-place，纯专家微调为 0%，加入自演示达到 55%；更难的衣物入篮 partial success 为 40%。
- 新物体拾取成功率从纯专家微调的 50% 升至 55%，并保持更好的文本敏感性。
- RoboTwin 综合均值从 43.3% 升至 56.8%，提高 13.5 个百分点，接近能够访问旧中训练数据的 frame-wise rehearsal oracle（57.0%）。
- 一个反直觉结果是：不少 self-demo 最终失败，但其状态覆盖与动作目标仍能保留行为先验。

## 我的判断

论文把“预训练模型”从初始化器升级成了目标机器人上的数据生成器。这个视角很重要：当原始预训练数据不可得时，策略本身仍可近似提供 rehearsal target。它非常适合相机换位、夹爪替换和个性化机器人，但不能把 self-demo 当成天然正确的伪标签。

## 局限与风险

- 只验证 π0.5，尚不清楚对其他 VLA 的稳健性。
- self-demo prompt 需人工选择，危险或古怪轨迹也需人工过滤。
- 会继承基础策略的伪影，例如夹爪卡住篮沿、重复拾放和错误停止行为。
- 在线 rollout 有硬件成本；连续数据飞轮还需要自动安全筛选、失败分类和停止条件。

## 可复用启发

1. 同一视觉场景中使用多条不同文本指令，迫使策略依赖语言而非视觉捷径。
2. 先从 expert:self-demo = 1:1 做混合比例基线。
3. 数据飞轮应保留“失败但信息丰富”的轨迹，同时过滤机械危险和系统性坏习惯。
4. 评估应拆成专家任务、旧技能、新物体与新技能组合，而不只报告平均成功率。

## 资源

- [arXiv 摘要](https://arxiv.org/abs/2608.19490)
- [HTML 全文](https://arxiv.org/html/2608.19490v1)
- [项目与视频](https://self-supervised-control.pages.dev/)

## 关联

- [[01-主题索引/视觉-语言-动作模型 VLA]]
- [[04-概念/潜在动作 Latent Action]]
- [[02-周报/2026-W34 具身智能与机器人论文周报]]
