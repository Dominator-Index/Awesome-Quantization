# 损失设计与优化景观

研究量化目标的几何、正则化、平滑以及训练停滞的干预。

[返回总目录](../README.md)

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [ICLR2025-CSReg](ICLR2025-CSReg/README.md) | 可微正则项能够推动连续参数形成离散结构。 | 用Cauchy–Schwarz不等式构造正则项；三值结构是其应用之一，也研究其他向量和矩阵结构。 | [PDF](ICLR2025-CSReg/ICLR2025-CSReg.pdf) |
| [arXiv2026-QAT-LowLossBasin](arXiv2026-QAT-LowLossBasin/README.md) | 在部署的量化权重上评估梯度，有机会感知损失谷壁并引导后续量化点返回低损失区域。 | 建立局部损失盆地的几何框架，解释某些PTQ失败与STE-QAT恢复现象。 | [PDF](arXiv2026-QAT-LowLossBasin/arXiv2026-QAT-LowLossBasin.pdf) |
| [ICML2026-WinQ](ICML2026-WinQ/README.md) | QAT训练慢可能来自鞍点附近大量小曲率方向，而非训练已经收敛。 | 周期性将连续权重向量化权重插值重置，并在加噪权重上评估梯度。 | [PDF](ICML2026-WinQ/ICML2026-WinQ.pdf) · [解读](ICML2026-WinQ/analysis.md) |
| [NeurIPS2026-LOTION](NeurIPS2026-LOTION/README.md) | 可通过改变目标的平滑方式，处理分段常数量化损失的优化困难。 | 以随机舍入噪声下的期望构造平滑损失，并分析其极小点与优化性质。 | [PDF](NeurIPS2026-LOTION/NeurIPS2026-LOTION.pdf) |
