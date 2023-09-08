# TKN -Transformer-based Keypoint Prediction Network For Real-time Video Prediction

## Background

视频预测的传统方法过分强调准确性而忽略了效率。这往往因为模型结构复杂、学习过多冗余信息导致的。此外，传统的方法大多是按顺序(逐帧)预测帧，因此很难加速。因此文章提出了一种基于transformer的关键点预测神经网络-TKN

## Problem

- 现有方法为了提高精度，提取了复杂的特征，导致了过多的浮点运算
- 他们浪费大量的时间学习相似的背景信息，通常由连续帧共享
- 它们使用顺序预测过程，下一帧的输入依赖于前一帧的输出。

## Contribution

- TKN融合了Keypoint和Transformer结构的优点，以保证高预测精度，快速的训练和测试，以及低内存消耗。为了准确预测包含频繁变化的视频，我们另外提出了TKN的顺序变化，称为TKN- sequential。
- 与现有方法相比，TKN的预测速度提高了11倍，GPU内存消耗降低了17.4%。因此，TKN为未来的实时多媒体技术奠定了基础。