# 梯度估计与可微量化

处理硬量化的反向传播，或用可微前向与退火保留有效梯度。

[返回总目录](../README.md)

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2026-StableQAT](arXiv2026-StableQAT/README.md) | 硬量化反向的代理梯度可以比恒等STE更平滑、稳定。 | 从舍入算子的离散Fourier分析构造轻量代理梯度族，STE是其特例。 | [PDF](arXiv2026-StableQAT/arXiv2026-StableQAT.pdf) |
| [MLSys2026-CAGE](MLSys2026-CAGE/README.md) | STE梯度可以加入与量化损失和局部曲率有关的校正。 | 从多目标QAT视角推导曲率校正，并用Adam统计量实现高效近似。 | [PDF](MLSys2026-CAGE/MLSys2026-CAGE.pdf) |
| [arXiv2026-JacQuant](arXiv2026-JacQuant/README.md) | 可学习的局部敏感性代理可用于改善低精度模型的更新。 | 学习对角或分块Jacobian敏感性代理，结合方差缩减优化；不改变前向量化器。 | [PDF](arXiv2026-JacQuant/arXiv2026-JacQuant.pdf) |
| [NeurIPS2026-HESTIA](NeurIPS2026-HESTIA/README.md) | 训练早期保留软分配梯度，再逐步逼近硬量化，有助于缓解过早离散化。 | 使用温度控制的softmax量化松弛，并以Hessian相关信息引导训练与退火。 | [PDF](NeurIPS2026-HESTIA/NeurIPS2026-HESTIA.pdf) · [解读](NeurIPS2026-HESTIA/analysis.md) |
