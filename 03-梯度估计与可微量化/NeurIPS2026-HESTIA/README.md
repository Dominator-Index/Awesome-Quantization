# HESTIA: A Hessian-Guided Differentiable Quantization-Aware Training Framework for Extremely Low-Bit LLMs

**主分类：** 梯度估计与可微量化。

**关联标签：** 软量化、温度退火、Hessian。

## 核心认知

训练早期保留软分配梯度，再逐步逼近硬量化，有助于缓解过早离散化。

## 方法怎么做

使用温度控制的softmax量化松弛，并以Hessian相关信息引导训练与退火。

[PDF](NeurIPS2026-HESTIA.pdf) · [已有解读](analysis.md) · [官方代码](https://github.com/hestia2026/Hestia.git)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在[metadata.json](metadata.json)；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
