# 量化表示、重建与位宽

选择怎样的离散表示、量化映射和位宽，以及如何重建低比特权重。

[返回总目录](../README.md)

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2016-TWN](arXiv2016-TWN/README.md) | 三值表示需要同时处理离散值与缩放系数，不能只对全精度权重直接取符号。 | 用带缩放的三值权重近似连续权重，并用阈值规则近似求解量化映射。 | [PDF](arXiv2016-TWN/arXiv2016-TWN.pdf) · [解读](arXiv2016-TWN/analysis.md) |
| [arXiv2026-QUASAR](arXiv2026-QUASAR/README.md) | 训练中的权重与重要性会变化，量化重建也应随之调整。 | 用梯度平方EMA估计重要性，搜索裁剪范围，以加权最小二乘拟合仿射反量化器。 | [PDF](arXiv2026-QUASAR/arXiv2026-QUASAR.pdf) |
| [NeurIPS2025-ParetoQ](NeurIPS2025-ParetoQ/README.md) | 不同位宽对应不同表示变化和训练需求，需要统一条件下比较大小与精度。 | 统一比较1、1.58、2、3、4 bit，并优化各位宽的量化函数与训练配方。 | [PDF](NeurIPS2025-ParetoQ/NeurIPS2025-ParetoQ.pdf) · [解读](NeurIPS2025-ParetoQ/analysis.md) |
