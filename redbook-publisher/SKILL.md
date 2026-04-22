---
name: redbook-publisher
description: Use when turning Markdown, notes, articles, course transcripts, technical explanations, or knowledge documents into Xiaohongshu/Redbook-style image cards, social media carousel posts, vertical PNG cards, publish-ready Chinese visual summaries, or Xiaohongshu/Redbook post copy.
---

# Redbook Publisher

## Purpose

Create publish-ready Xiaohongshu-style image card plans, direct-to-publish post copy, and when requested, the actual card images. Prioritize clear knowledge compression, strong Chinese copywriting, coherent visual systems, and vertical mobile-first layouts.

Use this skill for Markdown-to-card workflows, including technical notes, learning summaries, interview knowledge, tutorials, reading notes, course transcripts, and long-form articles.

## Default Output

Unless the user specifies otherwise, produce a complete carousel package:

- 5-9 cards.
- Vertical format: `1242x1660` by default. Use `1080x1440` if the user requests a lighter export.
- Chinese copy by default.
- Card roles: cover, problem hook, key ideas, structured breakdown, example or contrast, common mistakes, actionable summary, closing call-to-action.
- Short, scannable text. Avoid paragraph-heavy cards.
- A consistent visual system across all cards.
- A Markdown file containing direct-to-publish Xiaohongshu copy when the user asks for files, complete deliverables, or publish-ready output.

## Workflow

1. Read the source Markdown and identify the audience, topic, promise, central argument, supporting points, and any examples.
2. Decide the carousel narrative before designing individual cards. The sequence should feel like a guided explanation, not isolated screenshots.
3. Deduplicate repeated ideas, but preserve all distinct knowledge points.
4. Convert the source into card-level content: one clear message per card, with a headline, short body, emphasis phrase, and optional example.
5. Create a visual direction that matches the subject. Technical content should feel precise, intelligent, and premium, not childish or generic.
6. Write Xiaohongshu publish copy that matches the cards: title, body, hashtags, optional first comment, and publishing notes.
7. If generating images, create all cards with the same grid, spacing, typography rules, palette, and recurring motif.
8. Verify every card for readability on mobile: no tiny dense paragraphs, no edge-clipped text, no low-contrast labels, no accidental overlap.

## Content Strategy

Each card should have a job:

- Cover: make the reader stop. Use a concrete promise, tension, or outcome.
- Context: explain why the topic matters.
- Framework: organize the knowledge into a memorable structure.
- Deepening: unpack the most valuable ideas with examples or contrasts.
- Error correction: show misconceptions, traps, or interview pitfalls when relevant.
- Summary: compress the lesson into memorable takeaways.
- Closing: invite saving, reviewing, or applying the framework without sounding spammy.

For technical and professional content:

- Prefer accurate, high-signal explanations over exaggerated marketing.
- Preserve precise terms, but explain them in plain Chinese when needed.
- Use diagrams, comparison blocks, layered cards, matrices, or mini flows when they reduce cognitive load.
- For interview content, include "面试官真正想听什么" or "答题结构" only when it genuinely helps.
- Do not invent unsupported facts. If the source is ambiguous, state the assumption briefly.

## Copywriting Rules

Write for Xiaohongshu, but keep intellectual honesty.

- Headlines should be specific, useful, and curiosity-driven.
- Avoid empty clickbait such as "太绝了", "封神", "一定要看" unless the user explicitly wants that tone.
- Prefer concrete hooks: "把 X 讲清楚，只需要这 4 层", "很多人答错 Y，是因为漏了 Z".
- Body copy should be compressed into bullets, labels, short contrast pairs, or numbered steps.
- Keep one main idea per card.
- Use bold emphasis sparingly when outputting Markdown plans.
- Use natural Chinese punctuation and rhythm.
- For publish-ready Xiaohongshu post body copy, target about 400 Chinese characters. A good range is 350-450 Chinese characters; do not exceed 500 unless the user explicitly asks for a longer post.
- Add tasteful emojis to the publish-ready post body when appropriate. Use about 3-6 emojis total, no more than one emoji in a short paragraph, and prefer functional cues such as `✅`, `👇`, `📌`, `✨`, `🧠`, `🚀`, `🔍`, `💡`.
- Emojis should guide rhythm and readability, not decorate every sentence. For technical or senior-professional content, keep emojis restrained and do not insert them inside technical terms, code, API names, or precise concepts.

## Publish Copy Markdown File

When the user asks for publish-ready output, complete deliverables, or generated files, create a Markdown file named `xiaohongshu-publish-copy.md` unless the user provides another name. If producing multiple posts, use descriptive names such as `xiaohongshu-publish-copy-01.md`.

The Markdown file should contain copy the user can paste directly into Xiaohongshu:

```markdown
# 小红书发布文案

## 标题
[20-28 字优先，清楚、有钩子、不夸张]

## 正文
[约 400 字，建议 350-450 字；开头 1-2 句抓住痛点或收益，可加入 1 个自然表情符号]

[分段说明核心内容，每段短，适合手机阅读；全文适当加入 3-6 个表情符号，例如 ✅、👇、📌、✨、🧠、🚀、🔍、💡]

[结尾引导收藏、复盘、评论或行动；语气自然，不要硬广]

## 话题标签
#标签1 #标签2 #标签3 #标签4 #标签5

## 首评/置顶评论
[补充资料、互动问题、系列预告，任选其一]

## 发布检查
- 图片顺序：
- 封面标题：
- 适合发布时间：
- 备注：
```

For technical content, the publish copy should sound like a senior practitioner sharing hard-won clarity, not like a marketing account. Good patterns:

- "这篇把 X 拆成 4 层，面试和实战都能用。"
- "很多人以为 X 的关键是 A，其实真正拉开差距的是 B。"
- "如果你在做 AI 应用开发，建议把这个问题想清楚。"

Keep the post body aligned with the generated cards. Do not introduce major claims that are not represented in the carousel.

Before finalizing publish copy, roughly estimate the body length. If it is far below 350 Chinese characters, add one useful example, contrast, or takeaway. If it is above 500 Chinese characters, compress repeated explanation and keep only the strongest points.

## Visual Direction

Choose one clear visual language per carousel. Good default directions:

- Premium technical editorial: calm background, precise grid, restrained accent color, structured diagrams.
- Knowledge magazine: strong cover typography, modular content blocks, small annotations, elegant hierarchy.
- Product strategy notebook: paper texture, tabs, side notes, framework cards, subtle markers.
- AI/application engineering: dark neutral or warm off-white base, signal lines, node diagrams, code-like accents.

Avoid generic AI aesthetics:

- No default purple gradient unless the topic strongly justifies it.
- No centered title plus bullet list repeated on every card.
- No cramped text walls.
- No random decorative icons that do not clarify meaning.
- No inconsistent fonts, spacing, or colors between cards.

## Image Generation Requirements

When the user asks to generate actual images:

- Produce PNG cards unless another format is requested.
- Use a vertical mobile-first canvas.
- Keep safe margins on all sides.
- Make text legible at phone preview size.
- Use a recurring element such as a section label, index number, motif line, or corner marker to create series continuity.
- Prefer real layout craft over decorative abundance.
- Inspect or reason through final cards for clipping, overlap, contrast, hierarchy, and consistency.

If the environment supports HTML/CSS screenshots better than direct image drawing, it is acceptable to build card layouts as HTML and export screenshots, as long as the final result is PNG cards.

## Recommended Response Format

For planning-only requests, output:

```markdown
# 小红书图文方案

## 主题定位
[一句话说明主题、受众、读者收益]

## 视觉方向
[色彩、字体气质、版式语言、系列元素]

## 卡片脚本

### 01 封面
- 标题：
- 副标题：
- 视觉：

### 02 ...
- 标题：
- 正文：
- 强调：
- 视觉：
```

For image-generation requests, also include the generated file paths after creating the images.

For publish-ready file requests, create the Markdown file and include its path in the final response.

## Quality Checklist

Before finishing, check:

- The carousel has a clear beginning, middle, and end.
- Every distinct source knowledge point is represented somewhere.
- Repeated ideas are merged rather than duplicated.
- Each card can be understood in 3-5 seconds.
- The cover has a strong reason to click or save.
- The visual system is consistent across cards.
- Text is concise enough for a real Xiaohongshu image.
- The publish copy Markdown can be pasted directly into Xiaohongshu without rewriting.
- The publish-ready post body is about 400 Chinese characters, preferably 350-450 and not above 500 unless requested.
- The post body uses a few appropriate emojis to improve rhythm, without harming professionalism.
- The title, body, hashtags, and first comment match the actual carousel content.
- The result feels publishable, not like a document screenshot.
