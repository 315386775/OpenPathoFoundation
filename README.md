</h1>
<div align="center">
    <h1>🧬 PathoAI-Hub</h1>
    <p><strong>计算病理学开源生态入口</strong></p>
    <p>聚合 · 导览 · 连接 —— 帮你在最短时间内找到针对某个任务应该用什么模型、工具、数据</p>
</div>

<p align="center">
  <a href="https://github.com/315386775/OpenPathoFoundation/stargazers"><img src="https://img.shields.io/github/stars/315386775/OpenPathoFoundation.svg?style=popout-square" alt="GitHub stars"></a>
  <a href="https://github.com/315386775/OpenPathoFoundation/issues"><img src="https://img.shields.io/github/issues/315386775/OpenPathoFoundation.svg?style=popout-square" alt="GitHub issues"></a>
  <a href="https://github.com/315386775/OpenPathoFoundation/forks"><img src="https://img.shields.io/github/forks/315386775/OpenPathoFoundation.svg?style=popout-square" alt="GitHub forks"></a>
</p>

---

## 🎯 我们的愿景

GitHub 上病理AI的优秀开源项目已经很多，但分散在不同仓库、不同团队手中。**PathoAI-Hub 的价值在于"入口"而非"仓库"**——我们帮你筛选、分类、对比，让你在最短时间内找到所需资源并开始使用。

如果本项目能给您带来一点点帮助，麻烦点个 ⭐️ 吧～同时也欢迎大家贡献本项目未收录的开源模型、应用、数据集等。

![Open PathoFoundation](assets/model.png)

---

## 📚 四大核心板块

### 🏆 [模型ZOO — 选型指南](model-zoo/)

> "我的任务该用哪个模型？一张表告诉你答案。"

**你能在这里找到：**
- 🔬 UNI、Virchow、CONCH、RuiPath 等 **10+** 开源病理基础模型
- 📊 可横向对比的模型总表：参数量、训练数据、架构、开源情况一目了然
- 🎯 按场景推荐：通用特征提取 → UNI · 大参数泛化 → Virchow · 多模态推理 → CONCH · 中国人群 → RuiPath

[→ 进入模型ZOO，找到你的模型 →](model-zoo/)

---

### 🛠 [实用工具 & Demo — 开箱即用](tools-demo/)

> "不需要从头造轮子，这里有你需要的全流程工具。"

**你能在这里找到：**
- 🖥 **全流程平台**：QuPath、HistoColAi、ASAP —— 无需编程即可上手
- 🏷 **AI标注工具**：nuclei.io 将诊断时间从 209 秒缩短至 **79 秒**（-62%）
- 🐍 **开发框架**：TIAToolbox、PathML、CLAM —— Python 接口，灵活构建
- 🔬 **细胞分析**：HoVerNet-PanNuke、StarDist 开箱即用

[→ 进入工具库，发现趁手利器 →](tools-demo/)

---

### 📖 [前沿论文 — 风向标](papers/)

> "站在技术最前沿，看清病理AI的下一步走向。"

**你能在这里找到：**
- 🔥 **病理基础模型**：UNI、Virchow、CONCH、GPFM 等核心论文追踪
- 🧬 **多模态融合**：病理+基因组/转录组联合分析最新进展
- 🏥 **临床转化**：从实验室到诊室，真实临床验证研究
- 🔗 **与模型ZOO双向联动**：ZOO新增模型 → 论文同步解读；论文宏观趋势 → 反哺模型选型理解

[→ 进入论文库，把握技术脉搏 →](papers/)

---

### 📊 [数据与基准 — 评测基石](data-benchmarks/)

> "没有好数据，再强的模型也是空中楼阁。"

**你能在这里找到：**
- 🗂 **6+** 高质量病理数据集：从 PatchCamelyon（32万张图像）到 RuiPath（700张WSI / 7癌种）
- 🏅 标准化基准测试：公平对比算法性能，验证模型泛化能力
- 📋 清晰获取方式：公开下载 / 申请获取，许可条款一目了然
- ⚠️ 使用注意事项：CC-BY-NC-ND 等限制性许可提醒

[→ 进入数据馆，找到评测基石 →](data-benchmarks/)

---

## 🚀 快速开始

- **🔬 病理医生**：从 [实用工具](tools-demo/) 的 QuPath 或 HistoColAi 开始，无需编程，开箱即用
- **💻 AI研究员**：从 [模型ZOO](model-zoo/) 选预训练模型，用 [数据与基准](data-benchmarks/) 的数据集微调评测
- **📋 产品经理/决策者**：从 [前沿论文](papers/) 把握技术趋势，从 [数据与基准](data-benchmarks/) 评估技术成熟度

---

## 🤝 贡献指南

我们持续收集优质开源资源。欢迎通过 Issue 或 PR 提交：

- 新发布的病理基础模型（附论文链接和开源地址）
- 病理AI开源工具/平台
- 病理相关数据集（附获取方式和使用条款）
- 前沿论文解读

---

## 📄 许可

本仓库的元数据（资源索引）采用 [MIT License](LICENSE)。各资源本身的许可请参考其各自的 License 声明。部分数据集（如 RuiPath Benchmark）采用 CC-BY-NC-ND 等限制性许可，使用时请遵守对应条款。
