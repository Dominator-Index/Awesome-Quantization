# 低精度权重与训练状态

处理实际存储精度、master weights、舍入误差和低精度更新停滞。

[返回总目录](../README.md)

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [ICML2026-ECO](ICML2026-ECO/README.md) | 去掉高精度master weights后，需要补偿直接低精度更新产生的舍入误差。 | 直接更新量化权重，将量化误差反馈进已有优化器动量，避免额外master副本。 | [PDF](ICML2026-ECO/ICML2026-ECO.pdf) |
| [ICML2026-M+Adam](ICML2026-M+Adam/README.md) | 低精度下，加性与乘性更新会在不同权重尺度遇到停滞。 | 结合Adam加性更新与Madam乘性更新，改善低精度权重优化。 | [PDF](ICML2026-M+Adam/ICML2026-M+Adam.pdf) · [解读](ICML2026-M+Adam/analysis.md) |
