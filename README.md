# Read Paper

Codex skill for reading, analyzing, and comparing academic paper PDFs in Chinese.

## Contents

- `SKILL.md`: skill instructions, PDF reading strategy, and output requirements.
- `references/deep-analysis.md`: single-paper deep analysis template.
- `references/compare-papers.md`: multi-paper comparison template.

## Output Focus

The skill keeps the original deep-analysis sections and adds an engineering summary for each paper:

1. What bottleneck does the paper solve?
2. What architecture or training method does it use?
3. What does it imply for chip architecture, RTL, and verification?

## Installation

Copy this directory into your Codex skills directory, for example:

```text
%USERPROFILE%\\.codex\\skills\\read-paper
```

