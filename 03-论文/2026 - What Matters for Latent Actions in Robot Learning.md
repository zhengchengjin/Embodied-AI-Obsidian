---
type: paper
title: What Matters for Latent Actions in Robot Learning
authors: [Xizhou Bu, Qingda Hu, Lei Zhou, Lingfeng Zhang, Yingbo Tang, Zihao Liu, Xinyi Tao, Zhiqiang Ma, Qingqiu Huang, Chufeng Tang, Hongbo Wang, Jing Zhang, Jiayi Ma, Hangjun Ye, Wei Li, Xiaoshuai Hao]
year: 2026
published: 2026-08-20
venue: arXiv preprint
arxiv: 2608.19613
status: 速读
rating: 4.7
topics: [潜在动作, LAM, VLA, 表征学习, 机器人操作]
tags: [paper, 潜在动作, VLA, 机器人学习]
---

# What Matters for Latent Actions in Robot Learning

## 一句话

在统一框架下系统比较 41 个潜在动作设计选择，结论是：可靠的中训练初始化和适当的下游集成，比追逐复杂的新 LAM 结构更重要。

## 研究问题

无动作标注视频规模巨大，但机器人动作标签昂贵。[[04-概念/潜在动作 Latent Action|潜在动作模型]]试图从相邻帧变化中提取动作代理表征，可现有论文的训练管线、正则和集成方式不统一，难以判断性能提升究竟来自哪里。

## 方法

论文把流程拆成三阶段：① 从相邻帧自监督学习 LAM；② 用 LAM 自动标注视频并微调 VLM；③ 用少量真实动作数据训练物理策略。作者在 IDM–FDM 与帧差自编码两类范式中，对建模方式、AE/VAE/VQ-VAE/Sparsity/SIGReg 正则、潜在维数、归一化和五种物理动作头共 41 个配置进行统一比较。

## 关键结果

- 经典 LAPO 在原始数据上仍是很强的默认基线，简单的 DINOv2 语义特征差分同样有竞争力。
- 连续潜在动作下，选对正则强度比选择哪种正则更重要；作者建议默认从 VAE 开始。
- VQ-VAE 在 LIBERO-Plus 的分布偏移上有优势，但在 LIBERO 和 RoboTwin2.0 并不稳定领先，说明离散化带来鲁棒性的同时牺牲连续控制灵活度。
- 32 维潜在动作在 7-DoF 单臂和 14-DoF 双臂上整体最好；合适正则下额外归一化不是必需。
- FDM 的未来帧重建指标比另训 probe 更适合代理评估，但只能粗粒度筛选，无法稳定挑出最佳下游策略。
- 直接动作预测（DAP）利用潜在动作最弱；把 latent 作为并行辅助目标、同时保留物理动作对完整 VLM 特征的访问（JAP）更稳妥。

## 我的判断

这是一篇“领域校准”型论文，价值高于单点 SOTA。它提醒我们：潜在动作不必被神化为唯一控制语言。当前更可信的角色是提供动作感知的预训练信号，并在后训练中作为结构化辅助目标。对工程实践而言，先复现 LAPO/ΔDINO + 32 维 + 轻度 VAE，再验证真实闭环收益，可能比直接采用复杂模块更划算。

## 局限与待验证

- 主要基于现有机械臂数据和基准，尚未验证灵巧手、四足与人形平台。
- 尚未真正使用 YouTube 等大规模野外视频证明规模规律。
- 代理指标与闭环表现相关性有限，模型选择最终仍需策略训练或真实评估。
- 41 个选择虽多，但共享同一基础模型与训练范式，外推到其他 VLM/WAM 仍需复现。

## 可复用启发

1. 新 LAM 方法至少要对 LAPO 和语义特征差分做统一预算比较。
2. 报告正则系数扫描，不能只报告正则类型。
3. 代理指标用于砍掉明显差模型，不应用来宣布细粒度排名。
4. 下游最好保留物理动作分支对高层特征的直接访问。

## 资源

- [arXiv 摘要](https://arxiv.org/abs/2608.19613)
- [HTML 全文](https://arxiv.org/html/2608.19613v1)
- [项目页](https://carldegio.github.io/latent_action.github.io/)

## 关联

- [[01-主题索引/视觉-语言-动作模型 VLA]]
- [[01-主题索引/世界模型与视频预测]]
- [[02-周报/2026-W34 具身智能与机器人论文周报]]
