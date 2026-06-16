# 实用工具 & Demo平台 — 开箱即用

收集并分类展示病理AI研发全流程的开源工具，部分工具提供在线 Demo 试用。

## 工具分类总览

| 工具类别 | 代表性工具 | 核心功能 | 适用场景 |
|---------|-----------|---------|---------|
| **全流程分析平台** | QuPath, HistoColAi, ASAP, Cytomine | WSI可视化+标注+分析+AI集成 | 病理医生日常分析、团队协作 |
| **AI辅助标注平台** | HistoColAi, nuclei.io, PHARAOH | 人机协同标注、弱监督学习 | 快速构建高质量训练数据集 |
| **编程开发框架** | TIAToolbox, PathML, SlideFlow, CLAM | Python接口，构建自定义分析流程 | AI研究员开发新模型 |
| **特征提取/基础模型** | UNI, CONCH, PLIP | 病理图像特征抽取 | 下游任务迁移学习 |
| **图像处理与可视化** | OpenSlide, histolab, DeepLIIF | WSI读写、切块、染色归一化 | 数据预处理 |
| **细胞分割与分类** | HoVerNet-PanNuke, StarDist | 核分割与细胞表型分类 | 细胞级别定量分析 |

## 重点工具详解

### HistoColAi

开源 Web 平台，支持 WSI 可视化、协同标注、AI 模型预测集成。已在实际病理诊断场景（Spitzoid 皮肤肿瘤）中验证，代码和训练模型公开。可在本地 XAMPP 环境部署试用。

### QuPath

最成熟的开源生物图像分析软件，支持荧光和多通道数据，可集成 StarDist、Cellpose 等深度学习模型做细胞检测和分类。适合病理医生日常使用，无需编程基础。

### nuclei.io

斯坦福团队开发的本地 AI 病理标注平台，病理医生可在 1 小时内定制自己的 AI 模型，AI 辅助将子宫活检诊断时间从 209 秒缩短至 79 秒。

### ASAP

支持 TIFF、DICOM、JPEG2000、OpenSlide 等多种格式，提供颜色去卷积、细胞核检测、组织分割等高级功能。

### PHARAOH

基于弱监督 + 人机协同的 WSI 分析平台，通过图像特征聚类将组织分为形态学均匀的区域，专家只需标注少量聚类标签即可训练定制模型。

### TIAToolbox

计算病理学 Python 工具箱，提供 WSI 读取、预处理、特征提取、模型训练等完整流水线的编程接口。

## 快速选择建议

- **不需要编程** → QuPath, HistoColAi, ASAP
- **需要快速标注数据** → nuclei.io, PHARAOH
- **构建自定义 AI 流程** → TIAToolbox, PathML, CLAM
- **细胞级别分析** → HoVerNet-PanNuke, StarDist

## 贡献

欢迎推荐新的病理AI开源工具/平台（附项目链接和功能简介）。
