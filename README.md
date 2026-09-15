<div align="center">

# Read Paper

**深度阅读与分析 PDF/DOCX 论文，并生成中文工程化总结的 Pi skill**<br>
**A Pi skill for deep analysis of PDF/DOCX papers with Chinese engineering summaries**

<p>
  <a href="#中文">中文</a> · <a href="#english">English</a>
</p>

</div>

---

<a id="中文"></a>

## 中文

Read Paper 用于深度阅读单篇论文或技术文档。它覆盖问题定义、核心方法、实验结果、局限性与个人点评，并从芯片架构和 RTL 两个层面补充工程化分析。

支持 PDF 与 DOCX。输出统一使用中文；无法从原文确认的信息会明确标记为推测、`TBD` 或不适用。

### 核心能力

| 能力 | 作用 |
| --- | --- |
| 单篇深度分析 | 梳理研究动机、方法、创新点、实验、局限性与启发 |
| 完整文档阅读 | 分批覆盖长文档，并检查公式、图表、表格、脚注和附录 |
| 工程化三问 | 总结瓶颈、结构或训练方法，以及对芯片架构和 RTL 的启发 |
| 证据边界 | 区分论文原始结论与工程推断，避免把缺失信息当作事实 |
| 规范化交付 | 按文档标题重命名单篇原文，并将完整分析保存为 Markdown |

### 快速开始

克隆到 Pi skills 目录：

```bash
git clone https://github.com/flyjancy/read-paper.git ~/.pi/agent/skills/read-paper
```

分析 PDF 或 DOCX：

```text
/skill:read-paper <pdf或docx路径>
```

本 skill 遵循 Agent Skills 标准，Codex 等其他 harness 克隆到各自的 skills 目录也可以使用同一份文件。

### 输出

skill 根据正文标题规范化原文文件名，并在原目录保存报告：

```text
<标题>.<pdf|docx>
<标题>-summary.md
```

如果目标文件已经存在，skill 会停止操作，不覆盖文件，也不自动添加序号。

### 报告结构

- 基本信息与一句话总结
- 研究动机、问题定义与核心方法
- 实验结果、消融分析或证据论证
- 局限性、未来方向与个人点评
- 工程化三问：瓶颈、结构或训练方法、芯片架构/RTL 启发

详细模板见 [`references/deep-analysis.md`](references/deep-analysis.md)。

---

<a id="english"></a>

## English

Read Paper deeply analyzes a single academic paper or technical document. It covers problem definition, core methods, experiments, limitations, and critical commentary, then adds an engineering-oriented analysis for chip architecture and RTL.

The skill supports PDF and DOCX input and writes all reports in Chinese. Information that cannot be verified from the source is explicitly marked as inference, `TBD`, or not applicable.

### What It Provides

| Capability | Purpose |
| --- | --- |
| Single-document analysis | Explain motivation, methods, contributions, experiments, limitations, and implications |
| Complete document review | Read long documents in batches and inspect formulas, figures, tables, footnotes, and appendices |
| Three engineering questions | Summarize the bottleneck, architecture or training method, and implications for chip architecture and RTL |
| Evidence boundaries | Separate claims supported by the paper from engineering inference |
| Predictable delivery | Rename a single source from its document title and save the full analysis as Markdown |

### Quick Start

Clone the skill into your Pi skills directory:

```bash
git clone https://github.com/flyjancy/read-paper.git ~/.pi/agent/skills/read-paper
```

Analyze a PDF or DOCX file:

```text
/skill:read-paper <path-to-pdf-or-docx>
```

The skill follows the Agent Skills standard, so other harnesses (including Codex) can use the same files by cloning into their own skills directory.

### Output

The skill normalizes the source filename from its title and writes the report beside it:

```text
<title>.<pdf|docx>
<title>-summary.md
```

If either destination already exists, the skill stops without overwriting files or adding a numeric suffix.

### Report Structure

- Metadata and one-sentence summary
- Motivation, problem definition, and core method
- Experimental results, ablations, or supporting evidence
- Limitations, future directions, and critical commentary
- Three engineering questions: bottleneck, architecture or training method, and chip architecture/RTL implications

See [`references/deep-analysis.md`](references/deep-analysis.md) for the complete template.
