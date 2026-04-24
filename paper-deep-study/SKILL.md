---
name: paper-deep-study
description: Use when the user provides a research paper, technical article, arXiv or other paper URL, PDF file, or .docx file and wants a deep beginner-friendly explanation, the paper's core thesis, author information, a structured Markdown study note saved to disk, and when the input is a URL, a saved original PDF.
---

# Paper Deep Study

## Purpose

Turn one paper or technical article into a beginner-friendly deep study note.

The skill should help a computer science beginner understand:

- What problem the paper solves
- Why the problem matters
- What the authors are proposing
- How the method or system works
- What the experiments or results actually prove
- What the paper's strengths, limits, and suitable use cases are

The final deliverable is a Markdown learning note saved to the current working directory. When the input is a URL and the source has a downloadable PDF, also save the original PDF to the working directory.

## Input Types

This skill supports:

- Paper or article URL
- PDF file
- `.docx` file

Use the appropriate helper skill when needed:

- If the input is a PDF, use the `pdf` skill to extract and inspect the content.
- If the input is a Word document, use the `docx` skill to read the content.
- If the input is a URL, fetch the page and prefer the original PDF when one exists.

## Workflow

1. Identify the source type: URL, PDF, or `.docx`.
2. Obtain the paper content:
   - URL: open the source page, extract title, abstract, section structure, and download/save the original PDF when available.
   - PDF: extract text and structure.
   - `.docx`: extract text and structure.
3. Read enough of the source to understand:
   - title
   - abstract or summary
   - authors and affiliations
   - main sections
   - proposed method, framework, or argument
   - experiments, evaluation, or conclusions if present
4. Before drafting, read `references/answer-standard.md`.
5. Use `references/example-answer-self-evolving-agents-survey.md` as the style benchmark when you need to calibrate depth, tone, and structure.
6. Produce a Markdown note that teaches the material from easy to hard, assuming the reader is a computer science beginner unless the user asks for a more advanced audience.
7. Save the Markdown note to the current working directory.
8. If the source input is a URL and a source PDF is available, save that PDF too.
9. In the final response, report the saved file path(s) and include a concise summary of what was produced.

## Output Contract

The Markdown note must:

- Use Chinese by default unless the user requests another language.
- Be complete and educational, not just a short summary.
- Explain the paper in layers from intuitive understanding to deeper technical details.
- Include author information as a dedicated section.
- Clearly separate what the paper claims from your interpretation.
- Explicitly state uncertainty when source details are missing or ambiguous.

Save the Markdown file in the current working directory using a lowercase ASCII filename with the prefix `paper-study-`.

Example filenames:

- `paper-study-transformer.md`
- `paper-study-redis-cache-design.md`
- `paper-study-self-evolving-agents-survey.md`

If the target filename already exists, do not overwrite it unless the user explicitly asks. Append a numeric suffix such as `paper-study-transformer-2.md`.

## Author Information Requirements

The output must include a section covering:

- author names
- affiliations or institutions when available
- the likely research area or context of the authors
- why these authors or institutions matter for interpreting the paper, when that can be inferred safely

Do not invent biographies. If the paper page only provides names and affiliations, report only that and label broader context as an inference when needed.

## PDF Preservation Rules

- URL input: save the original source PDF when available.
- PDF input: no need to create a second PDF copy unless the user asks.
- `.docx` input: do not force conversion to PDF unless the user explicitly asks.

If URL PDF download is unavailable, say so clearly and still complete the Markdown note.

## Quality Bar

The note should let a beginner answer all of these after reading:

- What is this paper about?
- Why was this paper written?
- What is the key idea?
- How does the proposed method or system roughly work?
- What evidence supports the claim?
- What are the paper's limitations?
- In what scenarios is this paper useful?

Avoid shallow restatement of the abstract. Prefer:

- plain-language intuition
- layered explanation
- concrete examples
- distinctions between concept, mechanism, experiment, and conclusion

## Resources

- `references/answer-standard.md`: required answer structure and quality rules
- `references/example-answer-self-evolving-agents-survey.md`: a full benchmark answer showing the expected tone, density, and beginner-friendly explanation style
