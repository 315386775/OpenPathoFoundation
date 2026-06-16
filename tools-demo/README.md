# 🛠 实用工具 & Demo平台 — 开箱即用

收集并分类展示病理AI研发全流程的开源工具，覆盖从 WSI 读取、预处理、标注、模型训练到临床部署的完整链路。

---

## 工具分类总览

| 工具类别 | 代表性工具 | 核心功能 | 适用场景 |
|---------|-----------|---------|---------|
| **全流程分析平台** | QuPath, HistoColAi, ASAP, Cytomine | WSI可视化+标注+分析+AI集成 | 病理医生日常分析、团队协作 |
| **AI辅助标注平台** | HistoColAi, nuclei.io, PHARAOH | 人机协同标注、弱监督学习 | 快速构建高质量训练数据集 |
| **编程开发框架** | TIAToolbox, DLUP, LazySlide, PathML, CLAM, ahcore | Python接口，构建自定义分析流程 | AI研究员开发新模型 |
| **轻量预处理工具** | PySlyde, histolab, DeepLIIF | WSI读写、切块、染色归一化、特征提取 | 数据预处理流水线 |
| **特征提取/基础模型** | UNI, CONCH, GPFM, TITAN | 病理图像特征抽取 | 下游任务迁移学习 |
| **细胞分割与分类** | HoVerNet, cellseg_models.pytorch, StarDist, Cellpose | 核分割与细胞表型分类 | 细胞级别定量分析 |
| **AI Copilot** | PathChat+, nuclei.io | 多模态对话诊断、主动学习 | 临床辅助决策 |
| **数据获取管理** | TCGA-Tools, Patho-Bench | 数据集下载、标注提取、基准管理 | 数据工程 |

---

## 重点工具详解

### 全流程分析平台

#### QuPath
- **地址**: [github.com/qupath/qupath](https://github.com/qupath/qupath)
- **简介**: 最成熟的开源生物图像分析软件，支持荧光和多通道数据，可集成 StarDist、Cellpose 等深度学习模型做细胞检测和分类。适合病理医生日常使用，无需编程基础。内置 MONAI Label 插件支持 AI 辅助标注。

#### HistoColAi
- **论文**: [An open-source web platform for collaborative digital histology image annotation with AI-driven predictive integration](https://www.sciencedirect.com/science/article/abs/pii/S0169260724005704) · *Computer Methods and Programs in Biomedicine*, 2024
- **亮点**: 开源 Web 平台，支持 WSI 可视化、协同标注、AI 模型预测集成。已在实际病理诊断场景（Spitzoid 皮肤肿瘤）中验证，代码和训练模型公开。可在本地 XAMPP 环境部署试用。

#### ASAP
- **地址**: [github.com/computationalpathologygroup/ASAP](https://github.com/computationalpathologygroup/ASAP)
- **亮点**: 支持 TIFF、DICOM、JPEG2000、OpenSlide 等多种格式，提供颜色去卷积、细胞核检测、组织分割等高级功能。

#### Cytomine
- **地址**: [cytomine.org](https://cytomine.org)
- **亮点**: Web 端协作式多吉像素 WSI 标注平台，支持团队协作与项目管理。

---

### AI 辅助标注平台

#### nuclei.io
- **论文**: [A pathologist–AI collaboration framework for enhancing diagnostic accuracies and efficiencies](https://www.nature.com/articles/s41551-024-01223-5) · *Nature Biomedical Engineering*, 2024.06
- **代码**: [huangzhii.github.io/nuclei-HAI](https://huangzhii.github.io/nuclei-HAI)
- **亮点**: 斯坦福大学开发，主动学习 + 人机协同框架。病理医生可在 1 小时内定制自己的 AI 模型。关键临床验证：
  - 子宫内膜活检：诊断时间从 **209 秒 → 79 秒**（-62%）
  - 前列腺癌：每位病例平均诊断时间**减少 62%**
  - 结直肠癌淋巴结转移：微转移检出率显著提升

#### PHARAOH
- **亮点**: 基于弱监督 + 人机协同的 WSI 分析平台，通过图像特征聚类将组织分为形态学均匀的区域，专家只需标注少量聚类标签即可训练定制模型。

---

### 编程开发框架

#### TIAToolbox
- **地址**: [github.com/TissueImageAnalytics/tiatoolbox](https://github.com/TissueImageAnalytics/tiatoolbox)
- **亮点**: 计算病理学最成熟的 Python 工具箱之一，提供 WSI 读取、染色归一化（Macenko/Reinhard/Vahadane）、语义分割、细胞核实例分割、WSI 配准等完整流水线。与 NCI Imaging Data Commons（>70,000 切片 / >45TB）深度集成。

#### DLUP — Deep Learning Utilities for Pathology
- **地址**: [github.com/NKI-AI/dlup](https://github.com/NKI-AI/dlup) · v0.8.0 (2026.01)
- **亮点**: 荷兰癌症研究所（NKI）开发。支持任意分辨率 WSI 读取（金字塔层级间无缝插值）、多后端（OpenSlide/fastslide/自定义）、PyTorch Dataset 类、多种标注格式 I/O（GeoJSON/V7 Darwin/HALO/ASAP）。被 ahcore 框架底层使用。`pip install dlup`

#### LazySlide
- **地址**: [github.com/rendeirolab/LazySlide](https://github.com/rendeirolab/LazySlide) · v0.11.1 (2026.05)
- **亮点**: 深度集成 **scverse 生态**（SpatialData/scanpy/anndata/squidpy）的 WSI 分析框架。原生支持 UNI、CONCH、GigaPath、Virchow 等基础模型特征提取，组织分割+特征提取仅需 ~7 秒。支持零样本分类和图文描述生成。`uv add lazyslide`

#### ahcore
- **地址**: [github.com/NKI-AI/ahcore](https://github.com/NKI-AI/ahcore)
- **亮点**: NKI 开发的 PyTorch Lightning 库，专为计算病理学设计。底层使用 DLUP 处理 WSI I/O，提供标准化的模型训练和评估接口。

#### PathML
- **地址**: [github.com/Dana-Farber/PathML](https://github.com/Dana-Farber/PathML)
- **亮点**: Dana-Farber 癌症研究所开发，聚焦预处理和图像处理的标准化流水线。

#### CLAM
- **地址**: [github.com/mahmoodlab/CLAM](https://github.com/mahmoodlab/CLAM)
- **亮点**: Mahmood Lab 的经典多实例学习（MIL）框架，基于注意力机制的 WSI 分类。被广泛用于下游任务迁移学习。

#### PySlyde
- **论文**: [PySlyde: A lightweight, open-source toolkit for pathology WSI preprocessing](https://www.sciencedirect.com/science/article/pii/S2949820125004837) · *ESMO Real World Data*, 2025
- **亮点**: 轻量级、统一高层 API 封装 OpenSlide。支持多格式标注导入（QuPath/ImageJ/ASAP/JSON/CSV）、掩码生成/组织检测/染色归一化、灵活切块、**基础模型嵌入提取**（FeatureGenerator），可导出 LMDB/RocksDB。

#### TCGA-Tools
- **地址**: [github.com/LUMCPathAI/TCGA-Tools](https://github.com/LUMCPathAI/TCGA-Tools)
- **亮点**: 模块化 Python 包，从 NCI GDC、TCIA、Patho-Bench (HuggingFace) 批量下载 WSI 数据集及临床/分子/报告/诊断标注。`tcga-tools download --source gdc --dataset TCGA-BRCA --datatype WSI`

---

### AI Copilot

#### PathChat / PathChat+
- **论文**: [A Multimodal Generative AI Copilot for Human Pathology](https://www.nature.com/articles/s41586-024-07618-3) · *Nature*, 2024.06
- **升级版**: PathChat+ 训练数据扩展至 1M+ 指令样本 / 5.5M QA 轮次（2025），引入 SlideSeek 多智能体推理系统
- **关键里程碑**:
  - **2025.01**: PathChat DX 获 **FDA Breakthrough Device Designation**
  - **2026.05**: DALPHIN 基准（31 位病理医生 / 10 国 / 300 病例）— PathChat+ 在 **4/6 诊断任务上无显著差异于专家水平**
  - **2026**: SlideSeek 可在吉像素 WSI 上自主导航进行鉴别诊断
- **代码**: Mahmod Lab / Modella AI

#### HistAI Pathology Datahub Skillsets
- **地址**: [github.com/histai/skillsets](https://github.com/histai/skillsets)
- **亮点**: AI 编码智能体（Claude Code、OpenAI Codex、Gemini CLI）的病理技能仓库。提供病例搜索、WSI 可视化、AI 模型训练/监控等能力。

---

### 细胞分割与分析

#### cellseg_models.pytorch（2025 统一生态）
- **地址**: [github.com/okunator/cellseg_models.pytorch](https://github.com/okunator/cellseg_models.pytorch)
- **亮点**: **最重要的 2025 年开发**——统一的 PyTorch 库，实现 6 种主流细胞分割架构（HoVer-Net / Cellpose / Omnipose / StarDist / CPP-Net / CellViT-SAM），一致的 API 和预训练权重（HuggingFace Hub）。支持 SWSI 滑动窗口推理和 GeoDataFrame 导出。

#### HoVer-Net / HoVer-UNet（2025 更新）
- **亮点**: 密集细胞核分割+分类的金标准。HoVer-UNet（2025）将多分支架构蒸馏为单 UNet + MixViT 骨干，推理速度 **3×** 提升，PanNuke 性能相当。

#### StarDist
- **地址**: [github.com/stardist/stardist](https://github.com/stardist/stardist)
- **亮点**: 基于星凸多边形距离图的快速细胞核分割，圆形细胞核推理极快。

#### Cellpose
- **地址**: [github.com/MouseLand/cellpose](https://github.com/MouseLand/cellpose)
- **亮点**: 通用细胞分割算法，基于向量流场预测，适合不规则形态细胞。

---

### 图像处理与可视化

| 工具 | 地址 | 说明 |
|------|------|------|
| **OpenSlide** | [openslide.org](https://openslide.org) | WSI 格式读写的事实标准，支持 SVS/NDPI/MRXS 等 |
| **DeepLIIF** | [github.com/nadeemlab/DeepLIIF](https://github.com/nadeemlab/DeepLIIF) | IHC 染色反卷积与虚拟多重染色 |
| **histolab** | [github.com/histolab/histolab](https://github.com/histolab/histolab) | WSI 组织切片预处理和切块工具 |
| **TRACE** | [github.com/jlevy44/trace_app](https://github.com/jlevy44/trace_app) | 多模态空间共配准 Web 应用（WSI + 元素成像），*Bioinformatics Advances* 2025 |

---

## 快速选择建议

| 你的角色 | 推荐工具 |
|---------|---------|
| **病理医生（零编程）** | QuPath、HistoColAi、ASAP、Cytomine |
| **需要快速标注数据** | nuclei.io、PHARAOH、QuPath + MONAI Label |
| **Python 全流程开发** | TIAToolbox + DLUP + LazySlide |
| **轻量预处理+特征提取** | PySlyde、histolab |
| **WSI 数据集管理** | TCGA-Tools |
| **细胞级别分析** | cellseg_models.pytorch（统一入口） → HoVer-Net / StarDist / Cellpose |
| **AI 辅助临床诊断** | PathChat+（AI Copilot）、nuclei.io |

---

## 贡献

欢迎推荐新的病理AI开源工具/平台（附项目链接和功能简介）。
