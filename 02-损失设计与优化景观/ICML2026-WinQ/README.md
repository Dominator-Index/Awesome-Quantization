# WinQ: Accelerating Quantization-Aware Training of Language Models Around Saddle Points

**主分类：** 损失设计与优化景观。

**关联标签：** 鞍点、权重重置、噪声注入。

## 核心认知

QAT训练慢可能来自鞍点附近大量小曲率方向，而非训练已经收敛。

## 方法怎么做

周期性将连续权重向量化权重插值重置，并在加噪权重上评估梯度。

[PDF](ICML2026-WinQ.pdf) · [已有解读](analysis.md) · [官方代码](https://github.com/facebookresearch/WinQ.git)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在`metadata.json`（本地文件）；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
