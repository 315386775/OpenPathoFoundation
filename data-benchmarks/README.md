# 📊 数据与基准 — 评测基石

模型和数据是硬币的两面。本板块收录高质量病理数据集及标准化基准测试，帮助用户验证模型泛化能力、公平对比算法性能。

---

## 收录标准

- 具有明确学术引用
- 已被领域广泛使用或为最新权威来源
- 明确标注获取方式和使用许可

---

## 数据集总表

| 数据集名称 | 发表时间 | 任务类型 | 规模 | 癌种/组织 | 说明 | 获取方式 |
|-----------|---------|---------|------|----------|------|---------|
| **Camelyon+** | 2025 | 淋巴结转移检测+基准 | 1,350 WSI | 乳腺癌 | 清理 Camelyon-16/17 低质量图像和错误标签；四分类（阴性/微转移/宏转移/ITC）；12 种 MIL × 12 编码器基准 | [ScienceDB](https://doi.org/10.57760/sciencedb.16442) |
| **Patho-Bench** | 2025 | 多任务基准 | 33 数据集 / 95 任务 | 多癌种 | Mahmood Lab；覆盖形态亚型/微环境/分级/分子亚型/突变/疗效/生存 7 类任务；标准化 YAML/TSV | [HF](https://huggingface.co/datasets/MahmoodLab/Patho-Bench) · [Code](https://github.com/MahmoodLab/Patho-Bench) |
| **STARC-9** | 2025 | 结直肠癌组织分类 | 630K tiles / 9 类别 | 结直肠癌 | NeurIPS 2025；Stanford 发布；DeepCluster++ 半自动标注框架；含 CNNs+Transformers+FM 基准 | [HF](https://huggingface.co/datasets/Path2AI/STARC-9) · [Code](https://github.com/Path2AI/STARC-9) |
| **BEETLE** | 2025 | 乳腺癌分割 | 587 切片 | 乳腺癌 | 4 类语义分割（浸润上皮/非浸润上皮/坏死/其他）；3 中心 + 2 公开集；7 种扫描仪 | [arXiv](https://arxiv.org/abs/2510.02037) |
| **RuiPath 泛癌种评测** | 2025 | 病理诊断分类 | 700 WSI / 7 癌种 | 多癌种 | 瑞金医院；含乳腺/肺/结直肠/甲状腺/胃/胰腺/前列腺癌；专家级标签 | 填写申请表→contact@shdmic.com |
| **HepatoBench** | 2026 | 肝癌组织量化 | 7 组织类别 | 肝细胞癌 | 含 HepatoQuant 端到端工具；开放分类+分割模型 | [arXiv](https://arxiv.org/abs/2604.22858) |
| **BRCA-QuPath-Annot** | 2026 | 乳腺癌恶性/良性分类 | 50 WSI / 2,256 标注区 | 乳腺癌 | TCGA-BRCA；双重病理学家标注（99.95% 一致）；覆盖 Luminal A/B/HER2+/TNBC 亚型 | [figshare](https://doi.org/10.6084/m9.figshare.30256354) · [Code](https://github.com/uefcancer/Malignant_Non-malignant_BRCA-QuPath-Annot_Dataset) |
| **Cross-Cancer 21** | 2026 | 跨癌种分割泛化 | 7,616 ROI / 21 癌种 | 多癌种 | TCGA 21 癌种；评估分割模型跨癌种泛化能力；统一 0.5 µm/px 分辨率 | [Zenodo](https://zenodo.org/records/18668580) |
| **PatchCamelyon (PCam)** | 2018 | 淋巴结转移检测 | 327,680 图像块 | 乳腺癌 | 深度学习分类任务经典入门基准；Kaggle 竞赛可用 | 公开 |
| **BACH** | 2018 | 乳腺癌组织学分类 | 400 显微图像 | 乳腺癌 | 正常/良性/原位癌/浸润性癌 4 分类；ICIAR 2018 挑战赛 | 公开 |
| **Pan-Nuke** | 2020 | 核分割与分类 | 7,904 图像 / 19 组织类型 | 泛癌 | 细胞核实例分割+分类（肿瘤/炎症/结缔/坏死/上皮 5 类）；CC BY-NC-SA 4.0 | 公开 |
| **BRACS** | 2021 | 乳腺癌亚型分类 | 547 WSI + 4,539 ROI | 乳腺癌 | 乳腺肿瘤亚型分类（良性/非典型/恶性 7 亚型） | 公开 |

---

## 标准化基准测试平台

### Patho-Bench（2025）
- **发布方**: Mahmood Lab (Harvard / BWH)
- **规模**: 33 个公共数据集，95 个任务，7 大任务家族
- **任务类型**:
  | 任务族 | 任务数 | 示例 |
  |--------|--------|------|
  | 形态学亚型 | 11 | 乳腺癌亚型、肾癌亚型 |
  | 微环境表征 | 16 | 肿瘤浸润淋巴细胞、间质评分 |
  | 肿瘤分级 | 9 | Gleason 评分、Nottingham 分级 |
  | 分子亚型 | 6 | 管腔/基底、IDH 突变 |
  | 突变预测 | 34 | TP53、PIK3CA、KRAS |
  | 治疗反应 | 7 | 新辅助化疗反应 |
  | 生存预测 | 12 | 总生存、无病生存 |
- **格式**: 标准化 YAML/TSV 训练/验证/测试分割
- **用途**: 系统评估 patch 编码器与 slide 编码器
- **链接**: [Hugging Face](https://huggingface.co/datasets/MahmoodLab/Patho-Bench) · [GitHub](https://github.com/MahmoodLab/Patho-Bench)

### Camelyon+（2025）
- **升级内容**: 清理 Camelyon-16/17 低质量图像和错误标签
- **规模**: 1,350 WSI（871 阴性 / 174 微转移 / 251 宏转移 / 54 ITC）
- **基准**: 12 种 MIL 方法 × 12 种特征提取器（ResNet/ViT/PLIP/CONCH/UNI/GigaPath/Virchow/CTransPath/CHIEF/PRISM/TITAN/CONCHv1.5）
- **特性**: 预提取特征提供 `.pt` 和 `.h5` 格式
- **链接**: [ScienceDB](https://doi.org/10.57760/sciencedb.16442)

### DALPHIN（2026）
- **首个开放式多中心病理 AI Copilot 基准**
- **规模**: 1,236 图像 / 300 病例 / 130 诊断 / 6 国 / 14 亚专科
- **受试者**: 31 位病理医生 vs GPT-5 vs Gemini 2.5 Pro vs PathChat+
- **结论**: PathChat+ 在 4/6 诊断任务上与专家无显著差异
- **链接**: [arXiv](https://arxiv.org/abs/2605.03544)

---

## 数据使用注意事项

| 注意项 | 说明 |
|--------|------|
| **许可合规** | 各数据集请遵守其各自的 License 声明 |
| **限制性许可** | 部分数据集（如 RuiPath Benchmark）采用 CC-BY-NC-ND，仅限非商业研究使用 |
| **隐私法规** | 涉及患者数据的请确保遵循相关隐私法规（GDPR/HIPAA/个人信息保护法） |
| **染色差异** | 跨机构数据因染色/扫描仪差异可能导致模型性能下降，建议进行染色归一化 |
| **标签质量** | 注意数据集标签的可靠性——例如 HISTAI 独立审计发现仅 ~21% 病例标签一致 |
| **数据泄露** | 确保测试数据在训练时完全隔离，避免数据泄露导致性能虚高 |

---

## 贡献

欢迎提交病理相关数据集（附获取方式和使用条款）。收录标准：具有明确学术引用、标注清晰、获取方式透明。
