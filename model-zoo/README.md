# 🏆 模型ZOO — 选型指南

收录已开源的病理基础模型（PFMs）与专用模型，通过可筛选、可横向对比的总表，帮助用户快速锁定候选模型。

---

## 模型总表

| 模型名称 | 发布机构 | 发表时间 | 核心任务 | 参数量 | 训练数据规模 | 算法架构 | 开源情况 | 推荐场景 |
|---------|---------|---------|---------|--------|------------|---------|---------|---------|
| **TITAN** | Mahmood Lab / Harvard | 2025.11 *Nat Med* | 多模态WSI特征 | 48.5M | 335K WSI + 183K 病理报告 | ViT + ALiBi + CoCa | 代码+权重 | 全切片级多模态、罕见病、零样本检索 |
| **MOOZY** | Atlas Analytics | 2026.03 *arXiv* | 患者优先表征 | 85.77M | 77K WSI + 56公开数据集 | ViT + Case Transformer + iBOT | pip / HF | 跨切片患者级别、参数高效 |
| **MUSK** | 斯坦福等 | 2025.01 *Nature* | 视觉-语言精准肿瘤 | 675M | 50M 图像 + 1B tokens + 1M 图文对 | ViT-L + BEiT3 统一掩码 | 代码+权重 | 多模态检索/VQA、预后预测、免疫治疗 |
| **KEEP** | 上海交大 / 上海AI Lab | 2026.02 *Cancer Cell* | 知识增强VL诊断 | — | 14K+ WSI + 11K疾病知识图谱 | VL对比学习 + 语义层次对齐 | 代码+权重 | 罕见癌种零样本检测、知识驱动诊断 |
| **GPFM** | 港科大 SmartX Lab | 2025.09 *Nat BME* | 通用病理视觉特征 | — | 190M patches / 72K WSI / 34组织 | 统一知识蒸馏（专家+自蒸馏） | 代码+权重 | 横扫72项任务，通用下游迁移 |
| **PRISM / PRISM2** | MSKCC | 2025.06 *arXiv* | 对话式WSI问答 | 4.6B | 700K标本 / 2.3M切片 / 14M QA对 | Virchow2 + Perceiver + Phi-3 | 代码+权重 | 临床级癌症检测、对话式病理报告 |
| **Virchow / Virchow2** | Paige / MSKCC | 2023.09 / 2024.08 | 泛癌种分析 | 632M | 3.1M WSI（Virchow2） | ViT-H/14 + DINOv2 | 代码+权重 | 大规模强泛化、生物标志物预测 |
| **Prov-GigaPath** | Providence / Microsoft | 2024.05 *Nature* | 全切片空间建模 | 1.1B | 1.3B tiles / 171K WSI / 31组织 | ViT-G + DINOv2 + LongNet | 代码+权重(Apache 2.0) | 超大参数、空间架构感知 |
| **CHIEF** | Harvard / 多家 | 2024.09 *Nature* | 弱监督WSI通用 | — | 60K WSI / 19解剖位点 / 44TB | CTransPath + CLIP风格WSI预训练 | 代码+权重 | 癌症检测AUC 0.94、突变预测 |
| **UNI / UNI 2** | Mahmood Lab | 2023.08 / 2025.01 | 通用视觉特征 | 303M / 681M | 100K+ WSI / 350K WSI（UNI 2） | DINOv2 ViT-L / ViT-H | 代码+权重 | 经典通用特征、下游任务微调首选 |
| **H-Optimus-0 / 1** | 法国 Owkin | 2024.08 / 2025.02 | 通用视觉特征 | 1.1B | 法国内部大规模数据 | ViT-G/14 + DINOv2 | 代码+权重 | PathoBench顶级、大规模参数 |
| **CONCH** | Mahmood Lab | 2024 | 视觉-语言多模态 | ~306M | 1.1M+ 图文对 | ViT-L/16 + CoCa (CLIP) | 代码+权重 | 图像+文本联合推理、生物标志物预测 |
| **PLIP** | — | 2023.08 | 视觉-语言预训练 | — | 病理图文对（Twitter/X + PubMed） | ViT-B/32 + CLIP | 代码+权重 | 图文检索入门、快速原型 |
| **Phikon** | 法国 Owkin | 2023.07 | 自监督视觉特征 | — | TCGA等公开数据 | ViT-B + iBOT | 代码+权重 | 轻量级视觉特征提取 |
| **Hibou-L** | — | 2024.06 | 自监督视觉特征 | — | — | ViT + DINOv2 | 代码+权重 | 轻量级视觉编码 |
| **mSTAR** | — | 2024.07 | 多模态(病理+基因组) | 303M | — | ViT-L + 跨模态融合 | 代码+权重 | 病理+基因组联合分析 |
| **RuiPath** | 瑞金医院 + 华为 | 2025 | 临床级病理诊断 | — | 百万级中国癌种WSI | ViT + DINOv2 | 需申请 | 中国人群癌种、临床诊断场景 |

> 表内 "—" 表示未公开或待确认的指标。

---

## 收录模型详解

### 1. TITAN — 多模态全切片病理基础模型

- **论文**: [A multimodal whole-slide foundation model for pathology](https://www.nature.com/articles/s41591-025-03982-3) · *Nature Medicine*, 2025.11
- **代码**: [github.com/mahmoodlab/TITAN](https://github.com/mahmoodlab/TITAN) · [Hugging Face](https://huggingface.co/MahmoodLab/TITAN)
- **亮点**: 首个在**全切片级别**操作的多模态视觉-语言病理基础模型。三阶段预训练（纯视觉 → ROI多模态 → 切片级多模态），使用 PathChat 生成的合成文本增强训练。在 62+ 临床任务上评估，比 PRISM 平均提升 8.4%。支持长上下文外推、零样本分类和跨模态检索。

---

### 2. MOOZY — 患者优先计算病理学基础模型

- **论文**: [MOOZY: A Patient-First Foundation Model for Computational Pathology](https://arxiv.org/abs/2603.27048) · *arXiv*, 2026.03
- **代码**: [Hugging Face](https://huggingface.co/AtlasAnalyticsLab/MOOZY) · `pip install moozy`
- **亮点**: 首个以**患者病例**（而非单张切片）为表征基本单元的病理模型。通过专用 Case Transformer 在预训练阶段显式建模同一患者所有切片间的依赖关系。完全基于公开数据训练，参数量仅为 GigaPath 的 1/14。在冻结特征探针评估中，比 TITAN 加权 F1 提升 7.37%，比 PRISM 提升 8.83%。支持 `.svs`、`.tiff`、`.ndpi` 等多种格式。

---

### 3. MUSK — 视觉-语言精准肿瘤学基础模型

- **论文**: [A vision-language foundation model for precision oncology](https://www.nature.com/articles/s41586-024-08508-6) · *Nature*, 2025.01
- **亮点**: 统一掩码建模框架，在 50M 病理图像 + 1B 文本 tokens 上预训练，再用 1M+ 图文对对比学习。跨模态检索比 CONCH 提升 7.1%，VQA 准确率 73.2%。可预测 HER2 生物标志物（AUC 0.826）、黑色素瘤复发（AUC 0.833）、免疫治疗反应（AUC 0.77，远超 PD-L1 的 0.61）。内置可解释性注意力图和语言归因。

---

### 4. KEEP — 知识增强病理视觉-语言基础模型

- **论文**: [Knowledge-enhanced Pretraining for Vision-language Pathology Foundation Model on Cancer Diagnosis](https://www.cell.com/cancer-cell/abstract/S1535-6108(26)00103-0) · *Cancer Cell*, 2026.02
- **代码**: [github.com/MAGIC-AI4Med/KEEP](https://github.com/MAGIC-AI4Med/KEEP)
- **亮点**: 引入包含 11,454 种疾病、139,143 个属性的疾病知识图谱，将百万级噪声病理图文对重组为 **143,000 个语义结构化组**。在 18 个公开基准（14K+ WSI）+ 4 个机构级罕见癌症数据集（926 例）上评估，零样本癌症检测平均灵敏度 **89.8%**，在罕见癌症亚型上显著优于 CONCH、PLIP、UNI。

---

### 5. GPFM — 统一知识蒸馏预训练框架

- **论文**: [A generalizable pathology foundation model using a unified knowledge distillation pretraining framework](https://www.nature.com/articles/s41551-025-01488-4) · *Nature Biomedical Engineering*, 2025.09
- **代码**: [github.com/birkhoffkiki/GPFM](https://github.com/birkhoffkiki/GPFM)
- **亮点**: 通过"专家知识蒸馏 + 自知识蒸馏 + 掩码图像建模"三重框架，从 UNI、CONCH、Phikon 等多个教师模型联合学习。在 **72 项临床任务**（WSI 分类、生存分析、ROI 分类、检索、VQA、报告生成）中平均排名 **1.6**，42 项任务排名第一。基于 190M patches（72K WSI / 34 组织类型）训练。

---

### 6. PRISM / PRISM2 — 对话式病理AI

- **论文**: [Towards a clinically-accessible multimodal foundation model for pathology](https://arxiv.org/abs/2506.13063) · *arXiv*, 2025.06
- **亮点**: MSKCC 发布，**4.6B 参数**，训练数据含约 70 万标本、230 万张切片、1400 万 QA 对。基于 Virchow2 tile 编码器 + slide perceiver 聚合器 + Phi-3-Mini 语言模型。首个达到**临床级别癌症检测**性能的对话式基础模型，全癌症检测 diagnostic embedding AUC 0.976。支持直接对话式问答完成 CAP 病理报告模板。

---

### 7. Virchow / Virchow2 — 大规模病理视觉基础模型

- **论文**: [Virchow2: Scaling Self-Supervised Learning to 3.1 Million Whole Slide Images](https://arxiv.org/abs/2408.00738) · *arXiv*, 2024.08
- **亮点**: Virchow2 在 **3,134,922 张 WSI** 上以 DINOv2 自监督训练（ViT-H/14，632M 参数），覆盖 IHC 等多染色数据。在 PathoBench 基准中与 CONCH、H-Optimus-1 并列为顶级模型。在乳腺淋巴结宏转移检测（AUC 0.999）、CDH1 突变预测（AUC 0.986）等任务上表现优异。

---

### 8. Prov-GigaPath — 十亿级全切片预训练

- **论文**: [A whole-slide foundation model for pathology from real-world data](https://www.nature.com/articles/s41586-024-07441-w) · *Nature*, 2024.05
- **代码**: [Hugging Face](https://huggingface.co/prov-gigapath/prov-gigapath)
- **亮点**: 在 **13 亿 tile**（171K WSI / 31 组织类型）上预训练，比 TCGA 大 5–10 倍。双组件架构（ViT-G/14 + DINOv2 + LongNet 膨胀注意力）建模全切片空间依赖。原创论文中 25/26 任务最优，2025 年后续研究在 BRAF 突变预测（AUC 0.824）等任务上达到新 SOTA。Apache 2.0 开源。

---

### 9. CHIEF — 弱监督全切片通用基础模型

- **论文**: [A general-purpose WSI foundation model for pathology](https://www.nature.com/articles/s41586-024-07894-z) · *Nature*, 2024.09
- **亮点**: 在 60,530 张 WSI（19 解剖位点，44TB 数据）上用 CLIP 风格弱监督预训练。癌症检测宏观平均 AUC 0.94（11 种癌症类型/15 数据集），肿瘤来源识别 AUC 0.95–0.99，IDH 突变预测 AUC 0.91。比任务特定方法提升最高 **36.1%**。

---

### 10. UNI / UNI 2 — 经典通用病理视觉特征提取器

- **论文**: [UNI: Towards a General-Purpose Foundation Model for Computational Pathology](https://www.nature.com/articles/s41591-024-02857-w) · *Nature Medicine*, 2024.03
- **代码**: [github.com/mahmoodlab/UNI](https://github.com/mahmoodlab/UNI)
- **亮点**: 基于 DINOv2 在 100K+ WSI 上预训练，是病理基础模型的"经典之作"。UNI 2（2025.01）扩展至 681M 参数（ViT-H/14）、35 万 WSI + GTEx 数据，少样本学习能力大幅增强。适合作为下游任务微调的默认起点。

---

### 11. H-Optimus-0 / H-Optimus-1

- **论文**: [H-Optimus-0 / H-Optimus-1](https://github.com/bioptimus/h-optimus) · 法国 Owkin
- **亮点**: 基于 ViT-G/14 + DINOv2，在法国内部大规模病理数据上训练。H-Optimus-1（1.1B 参数，2025.02）在 PathoBench/PathBench 基准中与 Virchow2、CONCH 并列为第一梯队顶级模型。

---

### 12. CONCH — 病理视觉-语言多模态

- **论文**: [A visual-language foundation model for computational pathology](https://www.nature.com/articles/s41591-024-02856-x) · *Nature Medicine*, 2024.03
- **代码**: [github.com/mahmoodlab/CONCH](https://github.com/mahmoodlab/CONCH)
- **亮点**: 基于 CoCa（CLIP）架构，在 1.1M+ 病理图文对上训练。视觉-语言对齐能力出色，适用于图文检索、零样本分类、生物标志物预测等任务。在跨模型泛化评估中表现最优。

---

### 13. PLIP — 病理图文预训练入门

- **论文**: [PLIP: Pathology Language-Image Pre-training](https://www.nature.com/articles/s41591-023-02504-1) · *Nature Medicine*, 2023.08
- **代码**: [github.com/PathologyFoundation/PLIP](https://github.com/PathologyFoundation/PLIP)
- **亮点**: 利用 Twitter/X 和 PubMed 上的病理图文对进行 CLIP 风格预训练。轻量级 ViT-B/32 架构，适合快速原型验证和图文检索入门场景。

---

### 14. Phikon — 轻量级自监督视觉特征

- **论文**: [Phikon: A self-supervised learning framework for pathology image analysis](https://arxiv.org/abs/2307.11518) · *arXiv*, 2023.07
- **亮点**: 基于 iBOT 自蒸馏框架 + ViT-B，在 TCGA 等公开数据集上训练。轻量、易用，适合计算资源有限的场景。

---

### 15. Hibou-L — 轻量级病理视觉编码

- **亮点**: 基于 ViT + DINOv2，轻量级视觉编码器，适合嵌入移动端或边缘计算部署。

---

### 16. mSTAR — 病理+基因组多模态

- **论文**: [mSTAR: Multimodal Self-supervised Training for Pathology and Genomics](https://www.nature.com/articles/s41591-024-03269-3) · *Nature Medicine*, 2024.07
- **亮点**: 将病理图像与基因组/转录组数据联合建模，跨模态对齐，用于生存预测和分子亚型分析。

---

### 17. RuiPath — 临床级中国人群病理诊断

- **亮点**: 瑞金医院与华为联合发布，基于百万级中国癌种 WSI 训练，专门针对中国人群的病理诊断场景优化。外部使用者需申请获取模型权重。配套发布 RuiPath Benchmark 泛癌种评测数据集（700 张 WSI / 7 癌种）。

---

## 如何选择模型

| 你的需求 | 推荐模型 |
|---------|---------|
| **通用下游任务微调（首选经典方案）** | UNI / UNI 2、CHIEF、GPFM |
| **大参数量、最强泛化能力** | Virchow2、H-Optimus-1、Prov-GigaPath |
| **视觉-语言多模态推理** | CONCH、MUSK、KEEP |
| **全切片级多模态 + 零样本检索** | TITAN |
| **患者级别跨切片建模** | MOOZY |
| **知识驱动、罕见癌症诊断** | KEEP |
| **对话式交互、临床报告生成** | PRISM2 |
| **病理+基因组联合分析** | mSTAR |
| **中国人群/临床诊断场景** | RuiPath? |
| **轻量级快速原型** | Phikon、PLIP、Hibou-L |

---

## 贡献

欢迎通过 Issue 或 PR 提交新模型（附论文链接和开源地址）。收录标准：具有正式发表论文或广泛学术引用，代码/权重可获取。
