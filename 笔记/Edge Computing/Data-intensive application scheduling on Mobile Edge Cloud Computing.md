# Abstract
- 移动云计算帮助将有挑战性的计算任务迁移到有高性能的云平台上
- 然而，涌入的数据密集型任务会造成高延迟、高花费等问题
- 因此，本文提出了一种应用卸载优化模型-Mobile Edge Cloud Computing,
- 模型是一种mixed integer linear programming模型，将成本和能量花费作为优化目标

# Introduction
- MCC限制：
  1. 长距离
  2. 资源不足
- 采用MEC限制：
  1. 计算资源
  2. 效率

- 采用MECC
- 提出了多目标数据集中型移动应用调度和分配策略

- 本文贡献：
  1. 多目标优化策略，优化能量和成本花费，在能量限制和任务完成时间的限制下
  2. 使用MILP的多用户移动应用联合任务卸载和资源分配
  3. 基于期限和多用户的多角度分析密集型数据应用优化

# System archiecture
![img](./Data-intensive%20application%20scheduling%20on%20Mobile%20Edge%20Cloud%20Computing.assets/1.png)
- 组件：
  - 应用层处理：能量使用分析、移动网络监测信息、应用执行时的网络和带宽信息
  - 资源处理：用于收集用户设备的能量和边缘资源状态信息
  - 排队估计：G/G/1
  - 花费估计
  - 任务管理：根据计划协调资源调度
  - 决策：用于生成计划，并选择最优

# Application model
- 这是一个三层系统：移动设备、边缘端、云端

## Task model
![img](Data-intensive%20application%20scheduling%20on%20Mobile%20Edge%20Cloud%20Computing.assets/t1.png)
- 假定数据密集型移动应用A时系列任务包（BoT）,n 是任务的数量
$$
A = \{t_1, t_2, t_3, ..., t_n\}
$$
- 任务t建模：
$$
t_i = \{L_i,s_i,I_i,\sigma_i\}
$$

## System model
- 系统假定三个计算环境：公有云，M个边缘结点，N个移动设备
- 假定给定一个时间槽，一个移动设备可以请求应用执行，一些任务会本地执行，其他的会远端执行；
- 假定云和移动资源是可获得的并且预分配的
- 采用队列模型来等待资源
- 一个移动设备可以建模：
$$
P_m = \{\beta,\beta_{cost},d_m,e_m,w_m\}
$$
- 一个远端计算结点（边缘或者云）：
$$
P_r = \{\beta,\beta_{cose},p,w_r\}
$$

- 找到应用的执行计划，需要三个值：任务执行时间、总的能量消耗、成本花费

## Task execution time model
$$
D_i = D^P_i + D^C_i + D^W_i \\
D^P = \frac{I_i}{w_{target}} + (s_i\cdot \omega_i) \\
D^P_i = \frac{s_i}{\beta} + l \\
D^W_i = \frac{L_q}{\lambda}
$$

## Mobile device energy model

# The proposed offloading algorithm
- $t_i$的二进制卸载变量：
$$
x_i = (x^l_i,x^f_{iM},\dots,x^f_{iM},x^c_i)
$$
- $x^l_i$,$x^f_{ij}$,$x^c_i$分别代表任务在本地设备、边缘结点、云服务处理
- 只有一个位置被设置成1
- 任务i的执行时间：
$$
D_i = c^T_ix_i
$$
- 优化函数：
$$
P_0 = min(E\cdot{C})
$$

# 性能评估



