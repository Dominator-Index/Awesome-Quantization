# ECO: Quantized Training without Full-Precision Master Weights

**主分类：** 低精度权重与训练状态。

**关联标签：** master weights、误差反馈、动量。

## 核心认知

去掉高精度master weights后，需要补偿直接低精度更新产生的舍入误差。

## 方法怎么做

直接更新量化权重，将量化误差反馈进已有优化器动量，避免额外master副本。

[PDF](ICML2026-ECO.pdf)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在`metadata.json`（本地文件）；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
