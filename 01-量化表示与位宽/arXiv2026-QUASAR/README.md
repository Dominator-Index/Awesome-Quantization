# QUASAR: Lowering the Loss Floor of Quantization-Aware Training with Loss-Aware Reconstruction

**主分类：** 量化表示、重建与位宽。

**关联标签：** 损失感知重建、裁剪、二阶矩统计。

## 核心认知

训练中的权重与重要性会变化，量化重建也应随之调整。

## 方法怎么做

用梯度平方EMA估计重要性，搜索裁剪范围，以加权最小二乘拟合仿射反量化器。

[PDF](arXiv2026-QUASAR.pdf) · [官方代码](https://github.com/vincentcounathe/quasar-qat.git)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在`metadata.json`（本地文件）；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
