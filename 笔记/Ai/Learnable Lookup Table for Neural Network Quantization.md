# Learnable Lookup Table for Neural Network Quantization

## Abstract
- 模型量化目的是为了减少权重和激活值的bit数来增加计算效率
- 线性量化不能很好的满足所有形状的分布，所以很多方法使用了预训练带有可学习参数的方式来建立量化关系
- 本文中，我们将量化过程作为一个简单的查找操作，将可学习的查找表作为量化器
- 我们的查找表可以以端到端的方式训练，并且有这非常小的计算成本

## Introduction
- 深度卷积神经网络在很多领域都取得了很好的效果。然而在边缘设备上有着高的计算量的花费和内存占用限制。许多方式都在努力解决这个问题，比如蒸馏、设置高效的网络结构等。但是在工业界，量化被广泛的运用
- 模型量化分为均匀和非均匀，本文采用均匀分布的方式
- 本文提出LLT将浮点值映射到量化值

## Related Work

### Network Quantization

#### Uniform Quantization

## Applications
- 超分辨率
- 点云分类

## Method
1. 对于一个网络，LLT表首先被建立；
2. 执行查找操作将全精度权重和激活映射到低位
3. 在训练时，软化查找表，便于进行联合优化；在推理期间，硬化查找表获得低位网络

### Preliminaries

$$
y = 
\begin{cases}
    \hat{w} = clip(\frac{w}{s_w})\\
    \hat{a} = clip(\frac{a}{s_a})
\end{cases}
\tag{1}
$$

$$
y = 
\begin{cases}
    \overline{w} = s_w \cdot \mathbb{Q}(\hat{w},Q_w) \\
    \overline{a} = s_a \cdot \mathbb{Q}(\hat{a},Q_a)
\end{cases}
\tag{2}
$$


- 量化过程表示为查找操作，LLT作为量化器

### Lookup Table Construction
#### Motivation
- e.g.g:2-bit 量化,{$0,\frac{1}{3},\frac{2}{3},1$}
- 直接学习这种llt表是具有挑战性的，因为他们不可微分；因此我们简化了llt表
- 将LLT表分成3个子表，每一个子表代表每一个越迁函数
- 对于每一个子表，可以用K个辅助函数来建模，然后累加这些参数
- 因此，每一个LLT表可以被形式化为三个one-hot分布

#### Implementation

### Differentiable Lookup OPeration
1. 根据公式1计算
2. 根据公式2寻找相应的量化等级
3. 使用$\overline{a}$进行前向传播
4. 在反向传播期间，STE被用于计算梯度来更新LLT表

### Training Strategies
在这一部分，介绍查找表提高收敛性的方式

#### Exponential Formulation of Scale Parameter
- scale parameters会使训练不容易收敛，为了解决这个问题，使用了附加的参数$e_w$ 和 $e_a$

$$
\begin{cases}
    s_w = exp(e_w)\\
    s_a = exp(e_a)
\end{cases}
\tag{6}
$$

#### 逐渐缩放


#### Temperature Scheduler
- 以一个高的T开始，逐渐下降

### Evolution of Lookup Tables
1. 激活值的变化速度比权重快
2. 对于权重，邻近1的收敛速度比0快
3. 表的演变从浅层开始，逐渐向深层进入

### 粒度效应
- 查找表的粒度决定了初始量化级别的数量
