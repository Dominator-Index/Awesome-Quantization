# Understanding Quantization-Aware Training: Gradients at Quantized Weights Bias to the Low-Loss Basin

**主分类：** 损失设计与优化景观。

**关联标签：** 理论分析、STE偏差、PTQ与QAT。

## 核心认知

在部署的量化权重上评估梯度，有机会感知损失谷壁并引导后续量化点返回低损失区域。

## 方法怎么做

建立局部损失盆地的几何框架，解释某些PTQ失败与STE-QAT恢复现象。

[PDF](arXiv2026-QAT-LowLossBasin.pdf)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在[metadata.json](metadata.json)；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
