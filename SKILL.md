---
name: read-paper
description: "Read, deeply analyze, and compare academic papers or technical documents in PDF or DOCX format. Use for /read-paper and /compare-papers requests. Produces structured Chinese Markdown reports plus an engineering summary covering bottlenecks, architecture or training methods, and implications for chip architecture, RTL, and verification; single-document analysis also renames the source and saves the report by title."
---

# Read Paper

学术论文与技术文档 PDF/DOCX 阅读分析工具。所有输出使用中文，采用结构化 Markdown。

## 额外总结：每篇论文三问

在原有的深度分析、实验、局限性和个人点评等内容之后，为每篇论文追加一个“工程化三问”总结。三问内容固定为：

1. **它解决了什么瓶颈？** 说明应用场景、核心瓶颈、现有方法为什么不足，以及论文用什么证据证明问题得到缓解。
2. **用了什么结构或训练方法？** 说明模型/系统结构、关键模块、数据流，以及训练目标、损失函数、数据策略或优化方法。
3. **对芯片架构、RTL、验证有什么启发？** 分别讨论可落到芯片架构、RTL 实现和验证计划的启发；无法从论文确定的内容标记为 `TBD` 或“推测”。

三问总结是对原有分析的补充，不替代原有章节。实验数字、消融结果和局限性仍按原模板输出，也可以在三问总结中作为证据或限定条件再次引用。

## 命令

### /read-paper `<pdf或docx路径>`

深度分析单篇论文。读取 [references/deep-analysis.md](references/deep-analysis.md) 获取输出模板、阅读流程和文件命名规则。

### /compare-papers `<pdf或docx路径1>` `<pdf或docx路径2>` ...

对比分析多篇论文。读取 [references/compare-papers.md](references/compare-papers.md) 获取输出模板和对比流程。

多篇比较时，保留原有的总览、方法、实验和综合评价内容，并在每篇论文的分析中追加三问总结；最后可以围绕三问做横向对照。

## 文档读取策略

### 格式处理

- **PDF**：使用可用的 PDF 阅读工具提取文本并查看图表；扫描件先做 OCR。记录页码以便核对引用。
- **DOCX**：优先使用结构化 DOCX 读取工具；否则按 OOXML 结构提取正文、标题、表格、脚注与媒体。长文按标题或章节分块，图片和图表单独检查，不能只读取纯文本。
- 若文件损坏、加密或关键内容无法提取，明确说明缺失范围，不猜测内容。

### 分批读取

PDF 每批最多读取 20 页；DOCX 按标题或章节分批读取。

- **短文档（PDF ≤15页或篇幅相当的 DOCX）**：一次读完全部内容
- **长文档**：先扫描目录与章节结构，再分批覆盖全文
  - 第一批：第 1-10 页（标题、摘要、引言、方法前半）
  - 第二批：第 11-20 页（方法后半、实验）
  - 后续批次继续覆盖剩余章节、局限性与结论
  - DOCX 使用语义章节代替固定页码分批

### 信息提取要点

- **数学公式**：提取的公式可能不完整，根据上下文解释含义，不强行还原 LaTeX
- **图表**：使用可查看页面或媒体的工具检查图表，关注标题、坐标、图例和内容
- **表格数据**：重点提取实验结果表格中的数字，保留关键对比数据
- **双栏排版**：注意文本提取顺序，如果内容跳跃，结合上下文重新整理
- **非实验型文档**：没有数据集、基线或消融实验时标记为“不适用”，改为提取论据、案例、量化估算和反方观点，不虚构实验结果

## 输出规范

- 全部使用中文输出
- 使用结构化 Markdown 格式
- 论文术语首次出现时标注英文原文，如"注意力机制（Attention Mechanism）"
- 每篇论文或文档必须在完整分析、局限性和个人点评之后追加三个问题，顺序固定为“瓶颈 → 结构或训练方法 → 芯片架构/RTL/验证启发”
- 三问总结应引用原分析中的实验数字、消融结果和作者局限，并说明它们是论文证据还是分析推断
- 第三个问题必须明确区分芯片架构、RTL 和验证三个层次；论文没有直接覆盖的层次应标注推断边界
- `/read-paper` 按单篇分析模板将完整报告写入原文所在目录，并在对话中返回重命名后的原文路径和报告路径
- `/compare-papers` 直接输出到对话中
- 保持客观，避免把未经论文支持的硬件结论写成事实
