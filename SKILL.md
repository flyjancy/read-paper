---
name: read-paper
description: "Academic paper PDF reading and analysis tool. Provides deep Chinese analysis of papers and adds an engineering summary for each paper covering its bottleneck, architecture or training method, and implications for chip architecture, RTL, and verification. Supports /read-paper and /compare-papers commands."
---

# Read Paper

学术论文 PDF 阅读与分析工具。所有输出使用中文，结构化 Markdown 格式。

## 额外总结：每篇论文三问

在原有的深度分析、实验、局限性和个人点评等内容之后，为每篇论文追加一个“工程化三问”总结。三问内容固定为：

1. **它解决了什么瓶颈？** 说明应用场景、核心瓶颈、现有方法为什么不足，以及论文用什么证据证明问题得到缓解。
2. **用了什么结构或训练方法？** 说明模型/系统结构、关键模块、数据流，以及训练目标、损失函数、数据策略或优化方法。
3. **对芯片架构、RTL、验证有什么启发？** 分别讨论可落到芯片架构、RTL 实现和验证计划的启发；无法从论文确定的内容标记为 `TBD` 或“推测”。

三问总结是对原有分析的补充，不替代原有章节。实验数字、消融结果和局限性仍按原模板输出，也可以在三问总结中作为证据或限定条件再次引用。

## 命令

### /read-paper `<pdf路径>`

深度分析单篇论文。读取 [references/deep-analysis.md](references/deep-analysis.md) 获取输出模板和阅读流程。

### /compare-papers `<pdf路径1>` `<pdf路径2>` ...

对比分析多篇论文。读取 [references/compare-papers.md](references/compare-papers.md) 获取输出模板和对比流程。

多篇比较时，保留原有的总览、方法、实验和综合评价内容，并在每篇论文的分析中追加三问总结；最后可以围绕三问做横向对照。

## PDF 阅读策略

### 分批读取

PDF 通过 Read 工具读取，每次最多 20 页。

- **短论文（≤15页）**：一次读完全部内容
- **长论文（>15页）**：分批读取
  - 第一批：第 1-10 页（标题、摘要、引言、方法前半）
  - 第二批：第 11-20 页（方法后半、实验）
  - 按需继续读取剩余页

### 信息提取要点

- **数学公式**：PDF 提取的公式可能不完整，根据上下文推断含义，用自然语言解释而非强行还原 LaTeX
- **图表**：Read 工具可以看到 PDF 中的图表（多模态），关注图表标题和内容
- **表格数据**：重点提取实验结果表格中的数字，保留关键对比数据
- **双栏排版**：注意文本提取顺序，如果内容跳跃，结合上下文重新整理

## 输出规范

- 全部使用中文输出
- 使用结构化 Markdown 格式
- 论文术语首次出现时标注英文原文，如"注意力机制（Attention Mechanism）"
- 每篇论文在原有分析之后必须追加三个问题，顺序固定为“瓶颈 → 结构或训练方法 → 芯片架构/RTL/验证启发”
- 三问总结应引用原分析中的实验数字、消融结果和作者局限，并说明它们是论文证据还是分析推断
- 第三个问题必须明确区分芯片架构、RTL 和验证三个层次；论文没有直接覆盖的层次应标注推断边界
- 直接输出到对话中
- 保持客观，避免把未经论文支持的硬件结论写成事实
