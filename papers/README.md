# 前沿论文 — 风向标

追踪病理AI领域最新论文动态与技术演进脉络。

> **与模型ZOO的联动**：当 ZOO 新增一个模型时，论文板块同步更新该模型核心技术论文的解读；论文板块追踪的宏观趋势（如从"任务专用"到"基础模型"的演进）反过来帮助理解 ZOO 的价值。

## 论文分类维度

| 类别 | 说明 | 追踪方向 |
|------|------|---------|
| 病理基础模型 | 大规模预训练病理视觉/视觉-语言模型 | UNI、Virchow、CONCH、RuiPath 等论文 |
| 多模态融合 | 病理+基因组/转录组联合分析 | PathomicFusion、SurvPath、TANGLE 等 |
| 临床转化 | 人机协同诊断、临床验证研究 | nuclei.io HAI 框架、RuiPath 临床验证 |
| 数据集与基准 | 新数据集发布、基准测试 | Camelyon+、RuiPath Benchmark 等 |

## 病理基础模型

| 论文 | 模型 | 亮点 |
|------|------|------|
| A Generalizable Pathology Foundation Model Using a Unified Knowledge Distillation Pretraining Framework (2025) | GPFM | 港科大发布，统一知识蒸馏策略横扫 72 项任务，效果碾压 UNI、CHIEF |

## 多模态融合

| 论文 | 方向 | 亮点 |
|------|------|------|
| PathomicFusion | 病理+基因组融合 | 多模态生存预测 |
| SurvPath | 病理+基因组融合 | 可解释生存分析 |
| TANGLE | 病理+转录组 | 跨模态对齐 |

## 临床转化

| 论文 | 方向 | 亮点 |
|------|------|------|
| nuclei.io HAI Framework | 人机协同 | 诊断时间从 209s → 79s |
| RuiPath 临床验证 | 临床级病理诊断 | 百万级中国癌种 WSI 验证 |

## 数据集与基准

| 论文 | 内容 | 亮点 |
|------|------|------|
| Camelyon+ | 基础模型基准测试 | 清理 Camelyon-16/17，12 种主流模型特征 |
| RuiPath Benchmark | 泛癌种评测 | 700 张 WSI，7 种癌种 |

## 贡献

欢迎通过 Issue 或 PR 提交前沿论文解读（附论文链接和一句话要点）。
