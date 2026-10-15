# CAGE: Curvature-Aware Gradient Estimation For Accurate Quantization-Aware Training

**主分类：** 梯度估计与可微量化。

**关联标签：** STE校正、曲率、优化器无关。

## 核心认知

STE梯度可以加入与量化损失和局部曲率有关的校正。

## 方法怎么做

从多目标QAT视角推导曲率校正，并用Adam统计量实现高效近似。

[PDF](MLSys2026-CAGE.pdf) · [官方代码](https://github.com/IST-DASLab/CAGE.git)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在`metadata.json`（本地文件）；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
