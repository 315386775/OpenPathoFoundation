# 📖 前沿论文 — 风向标

追踪病理AI领域最新论文动态与技术演进脉络。

> **与模型ZOO的联动**：当 ZOO 新增一个模型时，论文板块同步更新该模型核心技术论文的解读；论文板块追踪的宏观趋势（如从"任务专用"到"基础模型"，从"纯视觉"到"多模态融合"）反过来帮助理解 ZOO 的价值。

---

## 论文分类维度

| 类别 | 说明 | 追踪方向 |
|------|------|---------|
| 病理基础模型 | 大规模预训练病理视觉/视觉-语言模型 | TITAN、MUSK、KEEP、GPFM、mSTAR 等 |
| 多模态融合 | 病理+基因组/转录组/文本联合分析 | PathGen、spEMO、SurvPath、TANGLE 等 |
| AI Copilot & Agent | 对话式诊断辅助系统 | PathChat+、DeepRare、SlideSeek、PathAgent |
| 临床转化 | 人机协同诊断、临床验证研究 | nuclei.io HAI、DALPHIN 基准、RuiPath 临床验证 |
| 数据集与基准 | 新数据集发布、基准测试 | Camelyon+、Patho-Bench、STARC-9、BEETLE |

---

## 一、病理基础模型

### 2025

| 论文 | 期刊 | 亮点 | 链接 |
|------|------|------|------|
| **A multimodal whole-slide foundation model for pathology** (TITAN) | *Nature Medicine* 2025.11 | 首个全切片级多模态视觉-语言模型；335K WSI + 183K 报告 + 423K 合成描述训练；62+ 临床任务评估，比 PRISM 提升 8.4% | [DOI](https://www.nature.com/articles/s41591-025-03982-3) · [Code](https://github.com/mahmoodlab/TITAN) |
| **A generalizable pathology foundation model using a unified knowledge distillation pretraining framework** (GPFM) | *Nature Biomedical Engineering* 2025.09 | 港科大；统一知识蒸馏（专家+自蒸馏）；72 项临床任务平均排名 1.6，42 项第一 | [DOI](https://www.nature.com/articles/s41551-025-01488-4) · [Code](https://github.com/birkhoffkiki/GPFM) |
| **A vision-language foundation model for precision oncology** (MUSK) | *Nature* 2025.01 | 斯坦福；统一掩码建模（50M 图像 + 1B tokens）；跨模态检索/VQA/免疫治疗预测；比 CONCH 检索提升 7.1% | [DOI](https://www.nature.com/articles/s41586-024-08378-w) |
| **A multimodal knowledge-enhanced whole-slide pathology foundation model** (mSTAR) | *Nature Communications* 2025 | 三模态融合（WSI+报告+基因表达）；26K 切片对/116M patches；97 项临床任务；分子预测 +2.6% Macro-AUC | [DOI](https://www.nature.com/articles/s41467-025-66220-x) |
| **Towards a clinically-accessible multimodal foundation model for pathology** (PRISM2) | *arXiv* 2025.06 | MSKCC；4.6B 参数；对话式病理报告；全癌症检测 AUC 0.976 | [arXiv](https://arxiv.org/abs/2506.13063) |

### 2026

| 论文 | 期刊 | 亮点 | 链接 |
|------|------|------|------|
| **Knowledge-enhanced Pretraining for Vision-language Pathology Foundation Model on Cancer Diagnosis** (KEEP) | *Cancer Cell* 2026.02 | 上海交大；11K 疾病知识图谱 + 143K 语义结构化组；零样本灵敏度 89.8%；罕见癌症显著优于 CONCH/PLIP/UNI | [DOI](https://www.cell.com/cancer-cell/abstract/S1535-6108(26)00103-0) · [Code](https://github.com/MAGIC-AI4Med/KEEP) |
| **MOOZY: A Patient-First Foundation Model for Computational Pathology** | *arXiv* 2026.03 | 首个患者优先（跨切片）病理基础模型；Case Transformer 建模切片间依赖；比 TITAN 加权 F1 提升 7.37% | [arXiv](https://arxiv.org/abs/2603.27048) · [HF](https://huggingface.co/AtlasAnalyticsLab/MOOZY) |

---

## 二、多模态融合

| 论文 | 期刊 | 亮点 | 链接 |
|------|------|------|------|
| **Generating crossmodal gene expression from cancer histopathology improves multimodal AI predictions** (PathGen) | *Nature Communications* 2026 | 扩散模型从 H&E WSI 生成转录组数据；合成特征与真实特征性能统计等效；含共形预测不确定性量化 | [DOI](https://www.nature.com/articles/s41467-025-66961-9) |
| **Leveraging multi-modal foundation models for analysing spatial multi-omic and histopathology data** (spEMO) | *Nature Biomedical Engineering* 2026 | 病理 FM 嵌入 + LLM 嵌入统一框架；空间组学分析；多细胞交互推断 | [DOI](https://www.nature.com/articles/s41551-025-01602-6) |
| **PathomicFusion** | — | 病理+基因组融合预测生存预后 | — |
| **SurvPath** | — | 可解释多模态生存分析 | — |
| **TANGLE** | — | 病理+转录组跨模态对齐 | — |

---

## 三、AI Copilot & Agent

| 论文 | 期刊 | 亮点 | 链接 |
|------|------|------|------|
| **A Multimodal Generative AI Copilot for Human Pathology** (PathChat) | *Nature* 2024.06 | 基础版：456K 视觉-语言指令微调；诊断题准确率 ~89.5% | [DOI](https://www.nature.com/articles/s41586-024-07618-3) |
| **PathChat+ & SlideSeek** (升级版) | — 2025–2026 | 1M+ 指令 / 5.5M QA 训练；多图理解；SlideSeek 在吉像素 WSI 上自主导航鉴别诊断 | — |
| **An agentic system for rare disease diagnosis with traceable reasoning** (DeepRare) | *Nature* 2026.02 | 上海交大；首个可追溯推理罕见病 AI 诊断；识别 2,919 种罕见病；召回超 10 年资深专家；推理报告专家认可率 95.4% | [平台](https://deeprare.cn) |
| **DALPHIN: Benchmarking Digital Pathology AI Copilots Against Pathologists** | *arXiv* 2026.05 | 首个开放式多中心基准；31 位病理医生 / 10 国 / 300 病例 / 130 诊断；PathChat+ 在 4/6 任务无显著差异于专家 | [arXiv](https://arxiv.org/abs/2605.03544) |
| **Evidence-based diagnostic reasoning with multi-agent copilot for human pathology** | *arXiv* 2025.06 | 多智能体证据驱动诊断推理框架 | [arXiv](https://arxiv.org/abs/2506.20964) |

---

## 四、临床转化

| 论文 | 期刊 | 亮点 | 链接 |
|------|------|------|------|
| **A pathologist–AI collaboration framework for enhancing diagnostic accuracies and efficiencies** (nuclei.io) | *Nature Biomedical Engineering* 2024.06 | 斯坦福；主动学习人机协同；诊断时间 209s→79s；前列腺癌诊断时间 -62% | [DOI](https://www.nature.com/articles/s41551-024-01223-5) · [Code](https://huangzhii.github.io/nuclei-HAI) |
| **Boosting pathology foundation models via few-shot prompt-tuning for rare cancer subtyping** (PathPT) | *Nature Communications* | 冻结 FM + Prompt-Tuning；罕见癌症少样本学习 | — |
| **RuiPath 临床级病理诊断验证** | — | 百万级中国癌种 WSI 验证；中国人群针对性优化 | — |

---

## 五、数据集与基准

| 论文 | 期刊/年份 | 亮点 | 链接 |
|------|----------|------|------|
| **Camelyon+** | *Scientific Data* 2025 | 清理 Camelyon-16/17 标签；1,350 WSI 四分类；12 MIL × 12 编码器基准测试 | [DOI](https://doi.org/10.57760/sciencedb.16442) |
| **Patho-Bench** | Mahmod Lab 2025 | 33 数据集 / 95 公共任务 / 7 任务族；标准化 YAML/TSV 格式 | [HF](https://huggingface.co/datasets/MahmoodLab/Patho-Bench) · [Code](https://github.com/MahmoodLab/Patho-Bench) |
| **STARC-9** | NeurIPS 2025 | 630K tiles / 9 类 CRC 组织；DeepCluster++ 半自动管理框架 | [HF](https://huggingface.co/datasets/Path2AI/STARC-9) |
| **BEETLE** | *arXiv* 2025.10 | 587 乳腺癌切片；4 类语义分割；3 中心 + 2 公开集多中心评估 | [arXiv](https://arxiv.org/abs/2510.02037) |
| **HepatoBench** | *arXiv* 2026.04 | 肝癌 HCC 7 组织分类 + HepatoQuant 工具 | [arXiv](https://arxiv.org/abs/2604.22858) |
| **BRCA-QuPath-Annot** | *Scientific Data* 2026.03 | 50 WSI 乳腺癌恶性/良性标注；双病理学家 99.95% 一致 | [DOI](https://doi.org/10.1038/s41597-026-07106-5) |

---

## 技术趋势概览

| 趋势 | 说明 | 代表工作 |
|------|------|---------|
| **从 Patch → Slide → Patient** | 建模粒度从 patch 级演进到患者级 | TITAN、MOOZY、PRISM2 |
| **从纯视觉 → 多模态融合** | 病理+文本+基因组+空间组学联合建模 | MUSK、mSTAR、PathGen、spEMO |
| **从任务专用 → AI Copilot** | 对话式交互替代单一任务模型 | PathChat+、DeepRare、PRISM2 |
| **从黑箱 → 可解释** | 注意力图 + 语言归因 + 共形预测 | MUSK、DeepRare、PathGen |
| **从模型发布 → 基准化评测** | 标准化基准成为模型评估基础设施 | Patho-Bench、Camelyon+、DALPHIN |
| **合成数据驱动扩展** | 生成式 AI 扩充训练数据 | TITAN (PathChat 合成描述)、PathGen (合成转录组) |

---

## 贡献

欢迎通过 Issue 或 PR 提交前沿论文解读（附论文链接和一句话要点）。
