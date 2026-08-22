---
type: paper
title: "DECOWAM: Decoupled Whole-Body World-Action Model for Legged Mobile Manipulation"
authors: [Siyuan Ma, Boshi Zhang, Yutian Zhang, Qinglian Wu, Jiaqi Zhai, Dong Wei, Qiaojun Yu]
year: 2026
published: 2026-08-20
venue: arXiv preprint
arxiv: 2608.20114
status: 速读
rating: 4.4
topics: [WAM, 世界模型, 移动操作, 四足机器人, 视频预测]
tags: [paper, WAM, 移动操作, 四足]
---

# DECOWAM

## 一句话

通过显式分离底盘、机械臂和相机自运动，构建能同时预测未来视频与全身动作的腿式移动操作世界—动作模型。

## 问题

固定底座机械臂中，图像变化主要来自机械臂和物体；移动操作中，底盘运动会带来强烈相机自运动。若视频分支被迫仅从像素猜测自运动，并把底盘与臂动作压进同一 latent，预测和控制都会纠缠。

## 方法

DECOWAM 冻结适配后的 FastWAM 主干，只训练残差 adapter；通过由特权未来观察蒸馏出的 action-equivalent future bottleneck 连接未来场景与控制；用带 gradient reversal 的 base/arm 双 latent 分离导航尺度和操作尺度信号；再把当前归一化底盘速度作为视频分支显式条件。作者还提供 ARMDOG 数据：四足底盘 + 6-DoF 机械臂，217 段、27 个任务文件夹、56,041 个同步帧，包含 15 Hz RGB、14 维全身状态/动作和语言。

## 关键结果

- 相对最佳 FastWAM 初始化，未来帧 MSE 降低 15.03%，动作 MSE 降低 21.71%。
- 第二阶段只训练 25.95M 参数，而 FastWAM 对照更新约 6.021B，约缩小 232 倍。
- 同时预测 48 步、14 维全身动作和 8 帧 384×320 RGB；动作误差不及专用 X-VLA，但处于强 VLA 区间。
- 每种方法 79 次真实机器人试验：任务成功率 58.2%，略高于 FastWAM 的 57.0%，但完成时间从 65 秒降到 49 秒。
- 相比 FastWAM，全身协调率提高 10.1 个百分点，底盘位移鲁棒性提高 17.7 个百分点；恢复率也最高。

## 我的判断

论文最有说服力的部分不是 1.2 个百分点的最终成功率差，而是中间行为：移动靠近、抓取后搬运、底盘静止保持和受扰恢复。这些指标正好对应因自运动与机械臂运动纠缠而产生的失败。它说明世界模型的闭环价值应通过“未来感知是否改善协调”验证，而不仅是视频 PSNR。

## 局限与待验证

- ARMDOG 当前只有 217 段，规模和任务多样性有限。
- 真实任务最终成功率与强 FastWAM 基线接近，优势主要集中在效率和过程鲁棒性。
- 与不同 VLA/WAM 的训练预算、输出分辨率并非完全一致，横向排名需谨慎。
- 论文未单列 limitation；长期运行、跨场景与跨平台迁移仍需验证。

## 可复用启发

1. 移动操作模型应把相机自运动作为显式条件，而非全部交给像素建模。
2. 除 end-to-end success 外，报告 docking、coordination、displacement robustness 和 recovery。
3. 冻结大视频先验、只学习 embodiment adapter，是数据较少时的合理默认。

## 资源

- [arXiv 摘要](https://arxiv.org/abs/2608.20114)
- [HTML 全文](https://arxiv.org/html/2608.20114v1)

## 关联

- [[01-主题索引/世界模型与视频预测]]
- [[04-概念/世界-动作模型 WAM]]
- [[02-周报/2026-W34 具身智能与机器人论文周报]]
