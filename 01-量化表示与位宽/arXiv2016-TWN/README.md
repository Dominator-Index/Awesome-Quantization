# Ternary Weight Networks

**主分类：** 量化表示、重建与位宽。

**关联标签：** 三值表示、量化映射、缩放系数。

## 核心认知

三值表示需要同时处理离散值与缩放系数，不能只对全精度权重直接取符号。

## 方法怎么做

用带缩放的三值权重近似连续权重，并用阈值规则近似求解量化映射。

[PDF](arXiv2016-TWN.pdf) · [已有解读](analysis.md) · [官方代码](https://github.com/Thinklab-SJTU/twns.git)

分类依据为PDF摘要及已有阅读笔记；本次新增概览不代表重新完成全文精读或复现实验。版本、会议证据及原始阅读备注保留在`metadata.json`（本地文件）；代码核对记录见[code-status.md](code-status.md)。

[本类目录](../README.md) · [全部分类](../../README.md)
