# Muon2: Boosting Muon via Adaptive Second-Moment Preconditioning

**主分类：** 优化器与预条件。

**关联标签：** 通用优化器、二阶矩适应、矩阵正交化。

## 核心认知

正交化前改善动量矩阵的条件，可以降低求近似极分解的负担。

## 方法怎么做

在Muon正交化之前加入Adam式二阶矩预条件，改善谱条件与迭代效率。

[PDF](arXiv2026-Muon2.pdf)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在[metadata.json](metadata.json)；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
