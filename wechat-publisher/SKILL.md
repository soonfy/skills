---
name: wechat-publisher
description: "Use when turning Markdown, notes, articles, course transcripts, technical explanations, or knowledge documents into WeChat Official Account publish packages, including titles, cover image concepts or files, article body, abstract, inline image plans or generated images, publish-ready Chinese copy, and a final Word document."
---

# WeChat Publisher

## Purpose

Create publish-ready WeChat Official Account packages from Markdown or long-form source material. Optimize for Chinese long-form reading, strong title conversion, credible expertise, coherent article structure, and cover/inline images that match the article topic.

Use this skill for Markdown-to-WeChat workflows, including technical articles, AI application notes, learning summaries, course transcripts, interview knowledge, tutorials, personal IP posts, product thinking, and professional essays.

## Default Deliverables

Unless the user specifies otherwise, produce a complete publish package:

- A Markdown file named `wechat-publish-package.md`.
- A Word document named `wechat-publish-package.docx` containing the same final publish package content.
- 5-8 title options with different angles.
- 1 recommended final title.
- 1 WeChat article abstract.
- A polished article body suitable for pasting into a WeChat editor.
- 1 cover image brief, and when requested, 1 generated cover image.
- Several inline image briefs, and when requested, generated inline images.
- A publishing checklist covering title, cover, abstract, body rhythm, image placement, and call-to-action.

## Workflow

1. Read the source Markdown and identify the topic, audience, account positioning, core promise, main argument, supporting points, examples, and emotional tone.
2. Deduplicate repeated material, but preserve every distinct knowledge point that matters to the article.
3. Choose the article angle: tutorial, deep analysis, personal growth, industry observation, technical breakdown, case study, or opinion essay.
4. Build the article outline before writing. WeChat articles need a clear opening hook, progressive argument, section rhythm, and a satisfying close.
5. Generate title options across multiple strategies, then pick the strongest one for the package.
6. Write the abstract after the article angle is clear. It should make readers understand why the article is worth opening.
7. Write or rewrite the body in polished Chinese, keeping paragraphs short and mobile-friendly.
8. Design a visual system for the cover and inline images that matches the article topic.
9. If generating images, create exactly one cover image and as many inline images as the article needs.
10. Create the Markdown package first, then create the Word document from the same final content without changing the article content.
11. Verify that the final package can be pasted into a WeChat editor with minimal rewriting and that the Word document opens as a polished `.docx`.

## Article Structure

Default structure:

- Opening: one sharp problem, observation, story, or contradiction.
- Promise: tell the reader what they will understand or gain.
- Body sections: 3-6 sections with meaningful subheadings.
- Examples: use concrete examples, comparisons, mini cases, or diagrams when they clarify the idea.
- Summary: compress the article into memorable takeaways.
- Closing: invite reflection, saving, sharing, or following without sounding desperate.

For technical content:

- Preserve precise terms and explain them clearly in Chinese.
- Prefer "problem -> principle -> mechanism -> example -> takeaway".
- Use diagrams, comparison tables, architecture sketches, workflow maps, or decision trees when they reduce cognitive load.
- Avoid pretending uncertain claims are facts. If the source is ambiguous, state the assumption briefly.

For personal IP content:

- Keep a consistent voice: sincere, useful, reflective, and grounded.
- Avoid exaggerated self-branding.
- Let experience, examples, and practical insight build trust.

## Title Strategy

Generate 5-8 title options. Cover several angles:

- Direct benefit: reader gains a concrete method or understanding.
- Pain point: reader recognizes a common confusion or problem.
- Curiosity gap: reader wants to know the hidden mechanism.
- Contrarian insight: gently challenges a common misunderstanding.
- Professional credibility: signals depth, structure, or practical value.
- Series/title brand: fits an ongoing account column if relevant.

Good title traits:

- Specific rather than vague.
- Useful without being clickbait.
- Clear enough to understand in one glance.
- Suitable for the account's long-term credibility.
- Usually 14-28 Chinese characters, unless a longer title is clearly stronger.

Avoid empty title tricks such as "太炸裂了", "封神了", "看完惊呆了", or "必须收藏" unless the user explicitly asks for a more viral style.

## Abstract Rules

The abstract should be 40-120 Chinese characters by default.

It should answer:

- What is this article about?
- Why should the reader care now?
- What useful perspective or method will they get?

Do not make the abstract a generic summary. Make it a compact opening reason.

## Body Writing Rules

Write for WeChat, not for a paper.

- Use short paragraphs.
- Use meaningful subheadings.
- Use lists only when they improve scanning.
- Keep transitions smooth between sections.
- Explain dense ideas with examples or analogies.
- Keep the tone credible and human.
- Do not overuse slogans, exclamation marks, or forced emotional language.

For AI, programming, and engineering content, the article should feel like a senior practitioner patiently making the hard part clear.

## Visual System

Choose one coherent visual direction per article. Match the theme, audience, and account voice.

Good default directions:

- AI application engineering: dark neutral or warm off-white background, node diagrams, clean technical lines, controlled accent color.
- Technical deep dive: precise grid, architecture blocks, code-like annotations, low-noise diagram style.
- Personal growth with AI: warm editorial style, human notes, subtle wave or journey motif.
- Industry analysis: magazine-like cover, bold title hierarchy, abstract data texture, restrained professional palette.
- Tutorial/how-to: clean instructional layout, step markers, flow arrows, visual checkpoints.

Avoid:

- Random decorative images unrelated to the topic.
- Generic technology glow, meaningless robot icons, or default purple gradients.
- Cover and inline images using unrelated styles.
- Text-heavy images that duplicate the article body.
- Low-contrast typography or cramped layouts.

## Cover Image

Create exactly one cover image when image generation is requested.

Default cover requirements:

- Topic-aligned, visually strong, and readable in a feed preview.
- Clear title or short cover phrase, not a full paragraph.
- Use the same visual system as the inline images.
- Default to a WeChat-friendly wide cover ratio. If exact platform constraints are unknown, use a 2.35:1 wide composition such as `900x383`, or ask the user if they need a specific size.
- Keep important text and visual focus away from edges.

The cover should make the article feel worth opening, but must not overpromise beyond the article.

## Inline Images

Generate inline images only when they help the article.

Use inline images for:

- Framework diagrams.
- Architecture or workflow maps.
- Before/after comparisons.
- Concept maps.
- Key takeaway cards.
- Process steps.
- Tables that would be hard to read as plain text.

Default inline image count:

- Short article: 1-2 images.
- Medium article: 2-4 images.
- Long or technical article: 4-6 images.

When generating files, name them:

- `cover.png`
- `inline-image-01.png`
- `inline-image-02.png`
- Continue in reading order.

Inline images should be readable on mobile. Prefer portrait, square, or 16:9 depending on the content, but keep a consistent style.

## Publish Package Markdown File

When the user asks for publish-ready output, complete deliverables, generated files, or a WeChat package, create `wechat-publish-package.md` unless the user provides another file name.

Also create `wechat-publish-package.docx` unless the user explicitly asks not to generate Word output. The Word document must preserve the same content and order as the Markdown package: recommended title, alternative titles, abstract, cover plan, body, image plan, closing guidance, and publishing checklist. Do not change or summarize the content differently for Word; treat the Word file as a formatted document version of the Markdown package.

Use this structure:

```markdown
# 微信公众号发布包

## 推荐标题
[最终推荐标题]

## 备选标题
1. [标题]
2. [标题]
3. [标题]

## 摘要
[可直接粘贴到公众号摘要栏]

## 封面
- 文件名：[cover.png 或待生成]
- 封面文案：
- 视觉风格：
- 构图说明：

## 正文
[可直接粘贴到微信公众号编辑器的正文]

## 配图规划

### 配图 01
- 插入位置：
- 文件名：
- 图片主题：
- 画面内容：
- 配图作用：

### 配图 02
- 插入位置：
- 文件名：
- 图片主题：
- 画面内容：
- 配图作用：

## 结尾引导
[关注、留言、收藏、分享或下一篇预告]

## 发布检查
- 标题是否具体：
- 封面是否匹配主题：
- 摘要是否有打开理由：
- 正文是否适合手机阅读：
- 配图是否真的帮助理解：
- 是否有夸张或 unsupported claim：
```

## Image Generation Requirements

When generating actual images:

- Produce PNG files unless another format is requested.
- Generate one cover only.
- Generate inline images in reading order.
- Keep the same palette, typography tone, motif, and visual density across all images.
- Prefer diagrams and editorial graphics over stock-photo-like filler.
- Verify text readability, contrast, margins, and no clipping or overlap.

If HTML/CSS screenshots provide better layout control, it is acceptable to build the cover and inline visuals as HTML and export screenshots, as long as the final output is PNG images.

## Quality Checklist

Before finishing, check:

- The package includes title options, final title, abstract, cover plan, body, inline image plan, and publishing checklist.
- The package includes both `wechat-publish-package.md` and `wechat-publish-package.docx` unless the user explicitly declined Word output.
- The Word document preserves the same content and order as the Markdown package.
- The article has a clear opening hook and logical section flow.
- Every important source knowledge point is represented.
- Repeated ideas are merged.
- The cover matches the article's core promise.
- Inline images clarify the article instead of decorating it.
- The writing feels credible, useful, and publishable.
- The final Markdown can be pasted into a WeChat editor with minimal rewriting.
