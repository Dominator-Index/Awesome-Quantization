# 优化器与预条件

研究更新方向、矩阵白化与二阶矩适应；本组含通用优化器背景论文。

[返回总目录](../README.md)

| 论文 | 核心认知 | 方法 | 材料 |
|---|---|---|---|
| [arXiv2026-Muon2](arXiv2026-Muon2/README.md) | 正交化前改善动量矩阵的条件，可以降低求近似极分解的负担。 | 在Muon正交化之前加入Adam式二阶矩预条件，改善谱条件与迭代效率。 | [PDF](arXiv2026-Muon2/arXiv2026-Muon2.pdf) |
| [NeurIPS2025-OPT-MatrixWhitening](NeurIPS2025-OPT-MatrixWhitening/README.md) | 矩阵白化的收益不能只用奇异值是否足够一致解释，还需考察方差适应。 | 在统一调参下比较矩阵白化优化器并拆解关键组件；它是分析与消融研究。 | [PDF](NeurIPS2025-OPT-MatrixWhitening/NeurIPS2025-OPT-MatrixWhitening.pdf) |
