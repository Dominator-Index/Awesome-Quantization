# Awesome Quantization：QAT与低精度优化

原始归档：2026-10-06；分类与迁移更新：2026-10-15。共 15 篇论文，每篇一个子目录，PDF 使用与目录相同的文件名。


## 按研究问题分类

15篇已放入5个实体分类目录。每篇README给出核心认知、具体方法与关联标签；同一方法可以关联多个方向，主目录按主要研究问题归档。

| 分类 | 数量 | 主要问题 |
|---|---:|---|
| [量化表示、重建与位宽](01-量化表示与位宽/README.md) | 3 | 选择怎样的离散表示、量化映射和位宽，以及如何重建低比特权重。 |
| [损失设计与优化景观](02-损失设计与优化景观/README.md) | 4 | 研究量化目标的几何、正则化、平滑以及训练停滞的干预。 |
| [梯度估计与可微量化](03-梯度估计与可微量化/README.md) | 4 | 处理硬量化的反向传播，或用可微前向与退火保留有效梯度。 |
| [优化器与预条件](04-优化器与预条件/README.md) | 2 | 研究更新方向、矩阵白化与二阶矩适应；本组含通用优化器背景论文。 |
| [低精度权重与训练状态](05-低精度权重与训练状态/README.md) | 2 | 处理实际存储精度、master weights、舍入误差和低精度更新停滞。 |

[结构化分类](classification.json) · [CSV索引](论文分类.csv) · [代码索引](CODE_INDEX.md)

**阅读边界：** Muon²、MatrixWhitening是通用优化器背景，CSReg是通用正则化方法；收录用于量化研究对照，不把通用训练结果直接当作QAT增益。ECO去掉master weights，也不代表所有optimizer states都已低精度化。新增摘要概览不等于所有15篇已全文精读。

### 量化表示、重建与位宽

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2016-TWN](01-量化表示与位宽/arXiv2016-TWN/README.md) | 三值表示需要同时处理离散值与缩放系数，不能只对全精度权重直接取符号。 | 用带缩放的三值权重近似连续权重，并用阈值规则近似求解量化映射。 | [PDF](01-量化表示与位宽/arXiv2016-TWN/arXiv2016-TWN.pdf) · [解读](01-量化表示与位宽/arXiv2016-TWN/analysis.md) |
| [arXiv2026-QUASAR](01-量化表示与位宽/arXiv2026-QUASAR/README.md) | 训练中的权重与重要性会变化，量化重建也应随之调整。 | 用梯度平方EMA估计重要性，搜索裁剪范围，以加权最小二乘拟合仿射反量化器。 | [PDF](01-量化表示与位宽/arXiv2026-QUASAR/arXiv2026-QUASAR.pdf) |
| [NeurIPS2025-ParetoQ](01-量化表示与位宽/NeurIPS2025-ParetoQ/README.md) | 不同位宽对应不同表示变化和训练需求，需要统一条件下比较大小与精度。 | 统一比较1、1.58、2、3、4 bit，并优化各位宽的量化函数与训练配方。 | [PDF](01-量化表示与位宽/NeurIPS2025-ParetoQ/NeurIPS2025-ParetoQ.pdf) · [解读](01-量化表示与位宽/NeurIPS2025-ParetoQ/analysis.md) |

### 损失设计与优化景观

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [ICLR2025-CSReg](02-损失设计与优化景观/ICLR2025-CSReg/README.md) | 可微正则项能够推动连续参数形成离散结构。 | 用Cauchy–Schwarz不等式构造正则项；三值结构是其应用之一，也研究其他向量和矩阵结构。 | [PDF](02-损失设计与优化景观/ICLR2025-CSReg/ICLR2025-CSReg.pdf) |
| [arXiv2026-QAT-LowLossBasin](02-损失设计与优化景观/arXiv2026-QAT-LowLossBasin/README.md) | 在部署的量化权重上评估梯度，有机会感知损失谷壁并引导后续量化点返回低损失区域。 | 建立局部损失盆地的几何框架，解释某些PTQ失败与STE-QAT恢复现象。 | [PDF](02-损失设计与优化景观/arXiv2026-QAT-LowLossBasin/arXiv2026-QAT-LowLossBasin.pdf) |
| [ICML2026-WinQ](02-损失设计与优化景观/ICML2026-WinQ/README.md) | QAT训练慢可能来自鞍点附近大量小曲率方向，而非训练已经收敛。 | 周期性将连续权重向量化权重插值重置，并在加噪权重上评估梯度。 | [PDF](02-损失设计与优化景观/ICML2026-WinQ/ICML2026-WinQ.pdf) · [解读](02-损失设计与优化景观/ICML2026-WinQ/analysis.md) |
| [NeurIPS2026-LOTION](02-损失设计与优化景观/NeurIPS2026-LOTION/README.md) | 可通过改变目标的平滑方式，处理分段常数量化损失的优化困难。 | 以随机舍入噪声下的期望构造平滑损失，并分析其极小点与优化性质。 | [PDF](02-损失设计与优化景观/NeurIPS2026-LOTION/NeurIPS2026-LOTION.pdf) |

### 梯度估计与可微量化

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2026-StableQAT](03-梯度估计与可微量化/arXiv2026-StableQAT/README.md) | 硬量化反向的代理梯度可以比恒等STE更平滑、稳定。 | 从舍入算子的离散Fourier分析构造轻量代理梯度族，STE是其特例。 | [PDF](03-梯度估计与可微量化/arXiv2026-StableQAT/arXiv2026-StableQAT.pdf) |
| [MLSys2026-CAGE](03-梯度估计与可微量化/MLSys2026-CAGE/README.md) | STE梯度可以加入与量化损失和局部曲率有关的校正。 | 从多目标QAT视角推导曲率校正，并用Adam统计量实现高效近似。 | [PDF](03-梯度估计与可微量化/MLSys2026-CAGE/MLSys2026-CAGE.pdf) |
| [arXiv2026-JacQuant](03-梯度估计与可微量化/arXiv2026-JacQuant/README.md) | 可学习的局部敏感性代理可用于改善低精度模型的更新。 | 学习对角或分块Jacobian敏感性代理，结合方差缩减优化；不改变前向量化器。 | [PDF](03-梯度估计与可微量化/arXiv2026-JacQuant/arXiv2026-JacQuant.pdf) |
| [NeurIPS2026-HESTIA](03-梯度估计与可微量化/NeurIPS2026-HESTIA/README.md) | 训练早期保留软分配梯度，再逐步逼近硬量化，有助于缓解过早离散化。 | 使用温度控制的softmax量化松弛，并以Hessian相关信息引导训练与退火。 | [PDF](03-梯度估计与可微量化/NeurIPS2026-HESTIA/NeurIPS2026-HESTIA.pdf) · [解读](03-梯度估计与可微量化/NeurIPS2026-HESTIA/analysis.md) |

### 优化器与预条件

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2026-Muon2](04-优化器与预条件/arXiv2026-Muon2/README.md) | 正交化前改善动量矩阵的条件，可以降低求近似极分解的负担。 | 在Muon正交化之前加入Adam式二阶矩预条件，改善谱条件与迭代效率。 | [PDF](04-优化器与预条件/arXiv2026-Muon2/arXiv2026-Muon2.pdf) |
| [NeurIPS2025-OPT-MatrixWhitening](04-优化器与预条件/NeurIPS2025-OPT-MatrixWhitening/README.md) | 矩阵白化的收益不能只用奇异值是否足够一致解释，还需考察方差适应。 | 在统一调参下比较矩阵白化优化器并拆解关键组件；它是分析与消融研究。 | [PDF](04-优化器与预条件/NeurIPS2025-OPT-MatrixWhitening/NeurIPS2025-OPT-MatrixWhitening.pdf) |

### 低精度权重与训练状态

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [ICML2026-ECO](05-低精度权重与训练状态/ICML2026-ECO/README.md) | 去掉高精度master weights后，需要补偿直接低精度更新产生的舍入误差。 | 直接更新量化权重，将量化误差反馈进已有优化器动量，避免额外master副本。 | [PDF](05-低精度权重与训练状态/ICML2026-ECO/ICML2026-ECO.pdf) |
| [ICML2026-M+Adam](05-低精度权重与训练状态/ICML2026-M+Adam/README.md) | 低精度下，加性与乘性更新会在不同权重尺度遇到停滞。 | 结合Adam加性更新与Madam乘性更新，改善低精度权重优化。 | [PDF](05-低精度权重与训练状态/ICML2026-M+Adam/ICML2026-M+Adam.pdf) · [解读](05-低精度权重与训练状态/ICML2026-M+Adam/analysis.md) |

## 命名与版本

- 已核实会议归属：`会议年份-名称缩写/会议年份-名称缩写.pdf`。
- Workshop 单独注明 `OPT`，例如 `NeurIPS2025-OPT-MatrixWhitening`，不代表主会论文。
- 尚未核实会议或投稿归属：`arXiv首次发布年份-名称缩写`。此标记不表示未投稿；未公开的投稿信息无法核实。
- MatrixWhitening、QAT-LowLossBasin 是便于整理的描述性简称，不是作者命名的方法缩写。
- PDF 保留原始归档时下载的版本，本次迁移未更换论文内容；Muon2 按所给链接保留 v1。TWN 首次发表于 2016 年，下载版本为 2022 年的 v3。
- 用户写作 Quassar，论文正式名称为 QUASAR。
- M+Adam：原链接是 NeurIPS 2025 OPT workshop 版本，标题为 *M+Adam: Stable Low-Precision Training with Combined Adam--Madam Updates*。本目录保存同作者团队的 ICML 2026 扩展版 *M+Adam: Low-Precision Training via Additive-Multiplicative Optimization*；原链接与版本关系保存在元数据中。

## 版本、会议与原始阅读备注

| 目录 / PDF | 完整标题 | 会议或状态 | 原始阅读备注 | 归属依据 |
| --- | --- | --- | --- | --- |
| [arXiv2016-TWN](01-量化表示与位宽/arXiv2016-TWN/arXiv2016-TWN.pdf) | Ternary Weight Networks | arXiv2016（会议归属未确认） | quantization formulation | [来源1](https://arxiv.org/abs/1605.04711) |
| [arXiv2026-QUASAR](01-量化表示与位宽/arXiv2026-QUASAR/arXiv2026-QUASAR.pdf) | QUASAR: Lowering the Loss Floor of Quantization-Aware Training with Loss-Aware Reconstruction | arXiv2026（会议归属未确认） | better mapping | [来源1](https://arxiv.org/abs/2608.13966) |
| [ICML2026-WinQ](02-损失设计与优化景观/ICML2026-WinQ/ICML2026-WinQ.pdf) | WinQ: Accelerating Quantization-Aware Training of Language Models Around Saddle Points | ICML2026 | saddle points and low magnitude eigenvalues slow training | [来源1](https://arxiv.org/abs/2605.17471) |
| [arXiv2026-StableQAT](03-梯度估计与可微量化/arXiv2026-StableQAT/arXiv2026-StableQAT.pdf) | StableQAT: Stable Quantization-Aware Training at Ultra-Low Bitwidths | arXiv2026（会议归属未确认） | gradient surrogate | [来源1](https://arxiv.org/abs/2601.19320) |
| [NeurIPS2025-ParetoQ](01-量化表示与位宽/NeurIPS2025-ParetoQ/NeurIPS2025-ParetoQ.pdf) | ParetoQ: Improving Scaling Laws in Extremely Low-bit LLM Quantization | NeurIPS2025 | scaling laws for low bit training | [来源1](https://arxiv.org/abs/2502.02631) |
| [arXiv2026-Muon2](04-优化器与预条件/arXiv2026-Muon2/arXiv2026-Muon2.pdf) | Muon²: Boosting Muon via Adaptive Second-Moment Preconditioning | arXiv2026（会议归属未确认） | adaptive second-moment preconditioning | [来源1](https://arxiv.org/abs/2604.09967) |
| [NeurIPS2025-OPT-MatrixWhitening](04-优化器与预条件/NeurIPS2025-OPT-MatrixWhitening/NeurIPS2025-OPT-MatrixWhitening.pdf) | What Really Matters in Matrix-Whitening Optimizers? | NeurIPS2025 OPT workshop | Empirically we have seen that variance adaptation is very useful in low bit QAT (user observation). | [来源1](https://opt-ml.org/papers/2025/paper20.pdf) |
| [MLSys2026-CAGE](03-梯度估计与可微量化/MLSys2026-CAGE/MLSys2026-CAGE.pdf) | CAGE: Curvature-Aware Gradient Estimation For Accurate Quantization-Aware Training | MLSys2026 | curvature aware gradient estimation | [来源1](https://arxiv.org/abs/2510.18784) |
| [arXiv2026-JacQuant](03-梯度估计与可微量化/arXiv2026-JacQuant/arXiv2026-JacQuant.pdf) | JacQuant: STE-Free Quantization-Aware Training via Learned Jacobian Surrogates | arXiv2026（会议归属未确认） | learned Jacobian to replace STE | [来源1](https://arxiv.org/abs/2605.25469) |
| [arXiv2026-QAT-LowLossBasin](02-损失设计与优化景观/arXiv2026-QAT-LowLossBasin/arXiv2026-QAT-LowLossBasin.pdf) | Understanding Quantization-Aware Training: Gradients at Quantized Weights Bias to the Low-Loss Basin | arXiv2026（会议归属未确认） | gradients at quantized weights bias to low-loss basin | [来源1](https://arxiv.org/abs/2606.09012) |
| [ICLR2025-CSReg](02-损失设计与优化景观/ICLR2025-CSReg/ICLR2025-CSReg.pdf) | Cauchy-Schwarz Regularizers | ICLR2025 | regularizer for ternary distribution | [来源1](https://arxiv.org/abs/2503.01639) |
| [NeurIPS2026-HESTIA](03-梯度估计与可微量化/NeurIPS2026-HESTIA/NeurIPS2026-HESTIA.pdf) | HESTIA: A Hessian-Guided Differentiable Quantization-Aware Training Framework for Extremely Low-Bit LLMs | NeurIPS2026 | Hessian guided QAT; user: dont really like this | [来源1](https://arxiv.org/abs/2601.20745)、[来源2](https://neurips.cc/virtual/2026/poster/148592) |
| [NeurIPS2026-LOTION](02-损失设计与优化景观/NeurIPS2026-LOTION/NeurIPS2026-LOTION.pdf) | LOTION: Smoothing the Optimization Landscape for Quantized Training | NeurIPS2026 | smooth quantized loss landscape; user: dont really like this | [来源1](https://openreview.net/pdf/b4398426538fb06a883d6a87b73d01d250cbb65c.pdf)、[来源2](https://neurips.cc/virtual/2026/poster/150892) |
| [ICML2026-ECO](05-低精度权重与训练状态/ICML2026-ECO/ICML2026-ECO.pdf) | ECO: Quantized Training without Full-Precision Master Weights | ICML2026 | master weights in lower precision / no full-precision master weights | [来源1](https://arxiv.org/abs/2601.22101)、[来源2](https://proceedings.mlr.press/v306/nikdan26a.html) |
| [ICML2026-M+Adam](05-低精度权重与训练状态/ICML2026-M+Adam/ICML2026-M+Adam.pdf) | M+Adam: Low-Precision Training via Additive-Multiplicative Optimization | ICML2026 | Expanded ICML2026 version of the supplied NeurIPS2025 OPT workshop paper, formerly titled M+Adam: Stable Low-Precision Training with Combined Adam--Madam Updates. | [来源1](https://neurips.cc/virtual/2025/loc/san-diego/124344)、[来源2](https://arxiv.org/abs/2607.10611) |

## 用户提出的研究方向

以下是用户的研究观察与方向，保留为阅读笔记，不视为经过本次归档验证的文献结论。

1. 面向量化训练设计优化器：现有相关工作也涉及降低 master weights 精度或移除 full-precision master weights，参考 ECO 和 M+Adam。
2. 低比特训练的预训练及后训练稳定性。
3. 实验观察：variance adaptation 对低比特 QAT 很有用。

HESTIA 与 LOTION 保留用户备注 “dont really like this”，并照常归档。

## 下载与校验

全部保存为原生论文 PDF。`manifest.jsonl` 记录来源、版本、会议证据、文件大小及 SHA-256；`download_summary.json` 记录校验结果；各论文目录内有 `metadata.json`。

校验包括 PDF 文件头、`pdfinfo`、前两页标题匹配、SHA-256 与临时文件检查。

## 仓库与本地入口

GitHub仓库：[Dominator-Index/Awesome-Quantization](https://github.com/Dominator-Index/Awesome-Quantization)。实际目录为`/usr/data/Awesome-Quantization`，原工作区的`Quantizatized-Aware-Training`已改为指向整个仓库的软链接。

10个已有代码checkout保留在`/usr/data`，各论文的`code`软链接用于本机阅读，不嵌套提交第三方代码库。公开代码URL见[代码索引](CODE_INDEX.md)，本机链接见[local-links.json](local-links.json)。本次未重新搜索此前未确认的5个官方代码地址，保留原核对日期与状态。

迁移与分类路径映射见[migration-20261015.json](migration-20261015.json)，原论文PDF的SHA256保持不变。
