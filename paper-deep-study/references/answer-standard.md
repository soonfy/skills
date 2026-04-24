# Paper Deep Study Answer Standard

Use this standard whenever `paper-deep-study` is invoked.

The goal is not merely to summarize a paper. The goal is to help a beginner truly learn it.

## Standard Reference Case

Use this prior case as the canonical style reference for depth and structure:

- Source URL: `https://arxiv.org/abs/2507.21046`
- Source PDF: `https://arxiv.org/pdf/2507.21046`
- Example answer file: `references/example-answer-self-evolving-agents-survey.md`

The example answer is the benchmark for:

- section structure
- Chinese teaching tone
- beginner-friendly explanation
- balance between paper summary and interpretation
- explicit discussion of strengths, limitations, and learning takeaways

## Required Output Structure

The output Markdown file should use this structure unless the user asks for a different one:

```markdown
---
title: <Chinese study note title>
author:
  - soonfy
date: YYYY-MM-DD
description: <One-sentence Chinese summary>
tags:
  - paper
  - <topic>
  - <domain>
reading_time: <integer minutes>
---

# <Study Note Title>

## 0. 论文信息
- 论文标题
- 来源
- 版本或年份
- 类型
- 论文链接
- PDF 链接或本地 PDF 路径（若有）

## 1. 作者与机构信息
- 作者名单
- 所属机构
- 作者可能的研究方向或背景
- 为什么这些作者或机构值得关注

## 2. 先用一句话讲清这篇论文

## 3. 这篇论文的主旨

## 4. 背景知识：一个新人需要先知道什么

## 5. 从浅到深讲解论文

## 6. 论文的方法、系统、流程、公式或核心机制

## 7. 实验、案例或结果到底说明了什么

## 8. 这篇论文的优点

## 9. 这篇论文的局限

## 10. 如果你是新人，应该怎样理解和使用这篇论文

## 11. 术语表

## 12. 你可以直接背下来的总结

## 13. 学习检查清单

## 14. 参考资料
```

## Author Information Rules

The author section is mandatory.

Always try to extract:

- author names from the paper page or first page
- affiliations from the paper header or metadata
- paper venue or organization context if available

When adding higher-level author context:

- keep it short
- prefer directly supported facts
- if you infer likely research direction from affiliations or publication history, label it as inference

Good examples:

- `作者来自某高校和某工业研究院，说明这篇工作可能兼具学术研究和工程视角。`
- `从机构背景看，这篇论文更像一篇领域综述而不是单点模型论文。`

Bad examples:

- inventing career history
- claiming major achievements without evidence
- pretending affiliation context is verified when it is only guessed

## Explanation Standard

The note must teach in layers:

1. One-sentence essence
2. Plain-language intuition
3. Structured explanation
4. Deeper mechanism
5. Evidence and conclusions
6. Practical interpretation

Use plain Chinese first, then introduce technical terms.

When the paper is mathematically heavy:

- explain what the formula is trying to accomplish before explaining symbols
- describe intuition before derivation
- say which parts a beginner can safely skip on first read

When the paper is a survey:

- explain the survey's classification framework
- say what problem the survey is trying to organize
- separate "the authors' taxonomy" from "the field itself"

When the paper is a systems or engineering paper:

- explain the system objective
- walk through the architecture
- describe tradeoffs and bottlenecks
- explain evaluation in practical terms

## Result Interpretation Rules

Do not merely repeat metrics.

Explain:

- what the experiments tested
- what the baseline comparison means
- whether the results support the claim strongly or only partially
- what the reader should and should not conclude

Useful questions:

- Is the gain large or marginal?
- Is the evaluation realistic?
- Is the benchmark narrow?
- Does the paper prove causality or only correlation/performance association?

## Beginner-Friendly Standards

Assume the reader may be new to:

- machine learning
- systems
- databases
- networking
- formal mathematical notation

Therefore:

- define terms before using them heavily
- use analogies carefully
- avoid hiding meaning behind jargon
- prefer "这一步是在做什么" over "该模块执行语义对齐"

The reader should finish with a usable mental model, not just vocabulary exposure.

## File Output Rules

- Save the study note as `paper-study-<topic>.md`.
- Use lowercase ASCII for filenames.
- If the filename exists, append `-2`, `-3`, and so on.
- If the source input is a URL and a downloadable PDF exists, save the original PDF in the same working directory.
- In the final response, include the saved path to the Markdown file and, when applicable, the saved PDF path.

## Quality Checklist

Before finishing, check:

- Does the note clearly explain the paper's main problem and core claim?
- Is there a dedicated author-information section?
- Is the explanation layered from beginner level to deeper detail?
- Are experiments or evidence interpreted, not just copied?
- Are limitations honestly stated?
- Could a beginner explain the paper back after reading this?
