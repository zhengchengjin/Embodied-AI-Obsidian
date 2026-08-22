---
type: paper
title: "ADEPT: Accelerating Dexterity via Pre-Training and Post-Training using Reinforcement Learning"
authors: [Jayjun Lee, Jessica Yin, Asif Rana, Nicholas Blauch, Sam Mady, Mohak Bhardwaj, Nima Fazeli, Nathan Ratliff, Karl Van Wyk, Ankur Handa]
year: 2026
published: 2026-08-19
venue: arXiv preprint
arxiv: 2608.19182
status: 速读
rating: 4.6
topics: [灵巧操作, 强化学习, 触觉, Sim2Real, 后训练]
tags: [paper, 灵巧操作, 强化学习, 触觉]
---

# ADEPT

## 一句话

先在通用物体重定向任务上学习可复用的“基础灵巧性”，再用稳定的 RL 后训练配方把它迁移到长程、接触丰富的真实任务。

## 问题

23–29 自由度手臂—手系统从零探索代价极高。通用 reposing 策略已经会抓取、抬升、手内重定向和搬运，但直接对插入任务做 PPO 微调，会因奖励、观察和 critic 分布变化迅速遗忘这些能力。

## 方法

预训练阶段在 16 种随机尺寸的基本形状上，用 PPO、自动域随机化和种群式超参搜索学习完整 reposing。后训练分三步：① 行为克隆把预训练 actor 蒸馏到带新观察量的下游 actor；② 冻结 actor，以新奖励预热全新 critic；③ 用低学习率、较保守的 PPO 更新学习插入等新行为。部署时再用 DAgger 将状态 teacher 蒸馏为 RGB 或 RGB+五指触觉 student。关节空间 Geometric Fabric 负责关节限位、碰撞和速度稳定，并在仿真与实机中共享。

## 关键结果

- 预训练只见基本形状，但 Kuka-Allegro 在 152 个 VisDex 对象上 reposing 成功率 0.77，与分布内 0.73 相当。
- 直接 PPO 微调很快把已会的 reposing 降到 0；ADEPT 的 5/5 个种子到达最终 ADR 难度。
- 消融表明低 actor 学习率是避免崩塌的必要项；critic 预热带来约 +17.6 个成功率点，BC 把到达最终难度的时间从 35.2 小时降到 19.9 小时。
- 真实 Flexiv-Sharpa 的方/圆销任务：只用视觉最终插入 3/10，加入五指视觉触觉后达到 8/10。
- 两种实体系统覆盖 Kuka-Allegro 23-DoF 与 Flexiv-Sharpa 29-DoF，并展示抓取、重定向、运输和插入的长程链条。

## 我的判断

论文最强的贡献是把“后训练为何毁掉预训练能力”拆成可操作诊断：新奖励让旧 critic 失配，错误 advantage 驱动大策略更新，随后数据分布继续恶化。先冻结 actor 校准 critic 的思想，不只适用于灵巧手，也值得在具身策略的 RL 后训练中测试。

## 局限

- 预训练 8B 环境步、单个下游后训练约 3B 环境步，计算成本高；只有多个下游任务共享先验时才容易摊薄。
- 实机失败主要来自遮挡下的物体姿态估计与抓取接触面积不足。
- 当前预训练对象偏规则，工具使用、杂乱场景、双手协同和更多触觉平台尚未覆盖。
- 视觉—触觉 student 的成功仍依赖仿真域随机化质量。

## 可复用启发

1. RL 迁移先诊断 critic，而不只给 actor 加 KL。
2. 新 observation space 出现时，用 BC 完成 actor 接口迁移，再开始 RL。
3. 触觉特征应与指尖空间位置对齐，而非简单拼接。
4. 安全控制层可稳定探索并缩小 sim-to-real 控制器差异。

## 资源

- [arXiv 摘要](https://arxiv.org/abs/2608.19182)
- [HTML 全文](https://arxiv.org/html/2608.19182v1)
- [项目页](https://adept-dexterity.github.io/)

## 关联

- [[01-主题索引/灵巧操作与触觉]]
- [[04-概念/灵巧操作与触觉]]
- [[02-周报/2026-W34 具身智能与机器人论文周报]]
