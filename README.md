# Read Paper

Codex skill for reading, analyzing, and comparing academic papers and technical documents in PDF or DOCX format, with Chinese output.

## Contents

- `SKILL.md`: skill instructions, PDF reading strategy, and output requirements.
- `references/deep-analysis.md`: single-paper deep analysis template.
- `references/compare-papers.md`: multi-paper comparison template.

## Output Focus

The skill keeps the original deep-analysis sections and adds an engineering summary for each paper:

1. What bottleneck does the paper solve?
2. What architecture or training method does it use?
3. What does it imply for chip architecture, RTL, and verification?

For `/read-paper`, the source PDF or DOCX is renamed from its document title and the complete report is saved beside it as `summary-<title>.md`. Title whitespace and punctuation are normalized to hyphens, and existing files are never overwritten. `/compare-papers` continues to return its comparison in the conversation.

## Installation

Copy this directory into your Codex skills directory, for example:

```text
%USERPROFILE%\\.codex\\skills\\read-paper
```
