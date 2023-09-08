# Attention is all you need

## Background

​		现在的序列模型都是由编码器和解码器的复杂递归或卷积神经网络堆叠起来的。作者提出了一种完全基于attention机制的网络结构，免除了递归和卷积的复杂操作

## Introduction

1. ### transformer模型架构

   <img src="C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\image-20230614214815272.png" alt="image-20230614214815272" style="zoom: 50%;" />

2. ### 位置编码

   <img src="C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\image-20230614215021269.png" alt="image-20230614215021269" style="zoom:80%;" />

3. ### 自注意力机制

   <img src="C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\image-20230614214855529.png" alt="image-20230614214855529" style="zoom:67%;" />

   

   <img src="C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\image-20230614214933236.png" alt="image-20230614214933236" style="zoom:80%;" />

## Contradiction

- 更少的训练时间，具有更高的并行性

例子：The **animal** didn't cross the **street**, because **it** was too wide.

​			I like cat.[3,1,2]   [0,1,2] q= wx+b

u ;ike

![img](C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\1102791-20210423161158499-558475133.jpg)

![img](C:\Users\ASUS\Desktop\笔记\papers\笔记\Attention is all you need.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTU3Nzg2NA==,size_16,color_FFFFFF,t_70.png)