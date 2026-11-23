---
title: MC² — 微观–介观耦合蒙特卡洛仿真框架
date: 2024-09-01
tags:
  - C/C++
  - Monte Carlo
  - HgCdTe
  - Avalanche Photodiodes
  - Device Simulation
---

面向窄带隙半导体雪崩过程的微观–介观耦合蒙特卡洛仿真框架，已完成与实验增益及过剩噪声因子（ENF）数据的定量校验。

基于 C++ 自主开发，结合 MPI/OpenMP 并行计算与 SQLite 载流子输运轨迹数据库，核心特性包括：

- 纳入非抛物线能带色散、中性杂质散射、碰撞电离、俄歇复合与极性光学声子散射等微观物理机制
- 揭示由空间标准差 $\sigma$ 与平均自由程 $\ell$ 构成的二维参数空间对雪崩链统计的主导作用
- 定量分析 Auger、带间隧穿（BBT）、声子与过剩噪声的多机制竞争关系
- 提出加速介观晶格（AML）结构，实现信噪比显著提升（AML −4.2 dB vs. ML −8.5 dB）

相关成果发表于 *IEEE Transactions on Electron Devices* (2026) 与 *Optics Letters* (2025)，并获国家软件著作权（登记号 `2023SR0426369`）。

<!--more-->
