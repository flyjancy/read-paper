<div align="center">

# Read Paper

**深度阅读、分析与对比 PDF/DOCX 论文，并生成中文工程化总结的 Codex skill**<br>
**A Codex skill for deep analysis and comparison of PDF/DOCX papers with Chinese engineering summaries**

<p>
  <a href="#中文">中文</a> · <a href="#english">English</a>
</p>

</div>

---

<a id="中文"></a>

## 中文

Read Paper 用于深度阅读单篇论文或对比多篇论文与技术文档。它覆盖问题定义、核心方法、实验结果、局限性与个人点评，并从芯片架构、RTL 和验证三个层面补充工程化分析。

支持 PDF 与 DOCX。输出统一使用中文；无法从原文确认的信息会明确标记为推测、`TBD` 或不适用。

### 核心能力

| 能力 | 作用 |
| --- | --- |
| 单篇深度分析 | 梳理研究动机、方法、创新点、实验、局限性与启发 |
| 多篇横向对比 | 对比问题定义、技术路线、设计选择、实验条件与适用场景 |
| 完整文档阅读 | 分批覆盖长文档，并检查公式、图表、表格、脚注和附录 |
| 工程化三问 | 总结瓶颈、结构或训练方法，以及对芯片架构、RTL、验证的启发 |
| 证据边界 | 区分论文原始结论与工程推断，避免把缺失信息当作事实 |
| 规范化交付 | 按文档标题重命名单篇原文，并将完整分析保存为 Markdown |

### 快速开始

克隆到 Codex skills 目录：

```bash
git clone https://github.com/flyjancy/read-paper.git ~/.codex/skills/read-paper
```

分析单篇 PDF 或 DOCX：

```text
/read-paper <pdf或docx路径>
```

对比多篇文档：

```text
/compare-papers <路径1> <路径2> ...
```

### 输出

单篇分析会根据正文标题规范化原文文件名，并在原目录保存报告：

```text
<标题>.<pdf|docx>
summary-<标题>.md
```

如果目标文件已经存在，skill 会停止操作，不覆盖文件，也不自动添加序号。多篇对比结果直接返回到对话中。

### 报告结构

- 基本信息与一句话总结
- 研究动机、问题定义与核心方法
- 实验结果、消融分析或证据论证
- 局限性、未来方向与个人点评
- 工程化三问：瓶颈、结构或训练方法、芯片架构/RTL/验证启发

详细模板见 [`references/deep-analysis.md`](references/deep-analysis.md) 和 [`references/compare-papers.md`](references/compare-papers.md)。

---

<a id="english"></a>

## English

Read Paper deeply analyzes a single paper or compares multiple academic papers and technical documents. It covers problem definition, core methods, experiments, limitations, and critical commentary, then adds an engineering-oriented analysis for chip architecture, RTL, and verification.

The skill supports PDF and DOCX input and writes all reports in Chinese. Information that cannot be verified from the source is explicitly marked as inference, `TBD`, or not applicable.

### What It Provides

| Capability | Purpose |
| --- | --- |
| Single-document analysis | Explain motivation, methods, contributions, experiments, limitations, and implications |
| Multi-document comparison | Compare problem framing, technical approaches, design choices, experimental conditions, and use cases |
| Complete document review | Read long documents in batches and inspect formulas, figures, tables, footnotes, and appendices |
| Three engineering questions | Summarize the bottleneck, architecture or training method, and implications for chip architecture, RTL, and verification |
| Evidence boundaries | Separate claims supported by the paper from engineering inference |
| Predictable delivery | Rename a single source from its document title and save the full analysis as Markdown |

### Quick Start

Clone the skill into your Codex skills directory:

```bash
git clone https://github.com/flyjancy/read-paper.git ~/.codex/skills/read-paper
```

Analyze one PDF or DOCX file:

```text
/read-paper <path-to-pdf-or-docx>
```

Compare multiple documents:

```text
/compare-papers <path-1> <path-2> ...
```

### Output

For a single document, the skill normalizes the source filename from its title and writes the report beside it:

```text
<title>.<pdf|docx>
summary-<title>.md
```

If either destination already exists, the skill stops without overwriting files or adding a numeric suffix. Multi-document comparisons are returned directly in the conversation.

### Report Structure

- Metadata and one-sentence summary
- Motivation, problem definition, and core method
- Experimental results, ablations, or supporting evidence
- Limitations, future directions, and critical commentary
- Three engineering questions: bottleneck, architecture or training method, and chip architecture/RTL/verification implications

See [`references/deep-analysis.md`](references/deep-analysis.md) and [`references/compare-papers.md`](references/compare-papers.md) for the complete templates.
