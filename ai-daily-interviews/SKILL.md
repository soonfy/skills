---
name: ai-daily-interviews
description: Generate systematic daily AI/programmer interview study notes and deep interview Q&A, save the result as an Obsidian-friendly Markdown file in the current working directory, and also reply with the generated content in chat. Use when the user asks to learn, explain, summarize, prepare interviews for, or generate knowledge points about Python, Java, Node.js, agents/LLM applications, MySQL, Redis, operating systems, networks, concurrency, JVM, CPython, V8, Spring, async runtimes, message queues, caching, storage, or other software engineering fundamentals.
---

# AI Daily Interviews

## Overview

Create a rigorous Obsidian-friendly Markdown learning artifact for one or more programmer topics: metadata, a topic map, systematic explanation, implementation/source-code perspective, production scenarios, optimization guidance, deep Big Tech-style interview Q&A, related knowledge recommendations, and reliable references. Save the artifact to the current working directory, then also provide the generated content in chat.

## Workflow

1. Identify the target topic(s), seniority level, and interview direction from the user request. If unspecified, assume backend engineer, mid-to-senior level, and production interview depth.
2. Read `references/answer-standard.md` before drafting the artifact.
3. If the user requests multiple broad domains, split them into a prioritized learning path and generate one focused artifact per topic or a concise matrix when space is limited.
4. Prefer depth over trivia. Explain invariants, tradeoffs, failure modes, source-code mechanisms, and production consequences.
5. Include interview questions that test reasoning under constraints. Avoid shallow definitions unless they are used as warm-up questions.
6. Include 3 related knowledge points the user should study next.
7. Include a references section with reliable sources such as official documentation, source repositories, RFCs, PEPs, JEPs, design docs, or authoritative project docs. Browse or verify current official links when source accuracy matters and network access is available.
8. Write the final artifact to a Markdown file in the current working directory. After writing, respond with the saved file path and the generated content, unless the user explicitly asks for file-only output.

## Topic Selection

When the user does not provide an exact topic, propose or choose a high-value topic from:

- Python: GIL, GC, coroutine/event loop, descriptor, import system, dict internals, multiprocessing, memory model.
- Java/JVM: class loading, JMM, synchronized/AQS, GC, JIT, thread pools, Spring transaction/proxy, Netty.
- Node.js: event loop, libuv, V8 GC/JIT, streams, cluster/worker_threads, backpressure, npm package design.
- Agents/LLM apps: tool calling, planning, memory, RAG, context engineering, evaluation, guardrails, multi-agent coordination.
- MySQL: B+Tree indexes, MVCC, locks, transaction isolation, redo/undo/binlog, optimizer, replication, sharding.
- Redis: dict/skiplist/quicklist, persistence, eviction, cluster, distributed locks, cache breakdown/penetration/avalanche.
- Systems: TCP, HTTP, Linux IO, epoll, containers, consistency, idempotency, distributed transactions, queues.

## Output Contract

Use Chinese by default unless the user asks otherwise. Produce the following content in the Markdown file and in the chat response:

1. Obsidian YAML frontmatter metadata.
2. Knowledge point title and learning positioning.
3. A structured topic map.
4. Systematic explanation from basic concept to core mechanism.
5. Source-code or implementation perspective, naming concrete modules/classes/files/functions when known and marking uncertain details as implementation-version dependent.
6. Production scenarios, failure modes, and design tradeoffs.
7. Optimization strategies with measurable signals.
8. Deep interview Q&A, each with question intent, complete answer, principle, source/implementation angle, real-world scenario, optimization/follow-up, and common traps.
9. Three related knowledge point recommendations.
10. Reliable references.
11. A short study checklist.

## Obsidian Metadata

Place YAML frontmatter at the very top of the Markdown file:

```yaml
---
title: <Chinese topic title>
author:
  - soonfy
date: YYYY-MM-DD
description: <One-sentence content summary>
tags:
  - tag1
  - tag2
reading_time: 30
---
```

- Use the current date in `YYYY-MM-DD` format.
- `title` is the final content title, for example `Redis 缓存穿透、击穿、雪崩`.
- Always set `author` as a YAML list containing `soonfy`.
- `description` is a concise one-sentence summary of the note.
- `tags` should be inferred from the topic and written as a YAML list. Preserve important Chinese topic words when useful, for example `redis`, `穿透`, `击穿`, `雪崩`.
- `reading_time` is the estimated reading/study time in minutes as an integer.

## File Output Rules

- Save the complete generated artifact as a `.md` file in the current working directory.
- Use a lowercase ASCII filename derived from the topic with the required `interview-` prefix, for example `interview-mysql-mvcc.md`.
- If the target filename already exists, do not overwrite it unless the user explicitly asks. Append a numeric suffix such as `interview-mysql-mvcc-2.md`.
- Keep the chat response useful after saving: include the absolute or workspace-relative file path, then include the generated Markdown content directly.
- If filesystem writes are unavailable, provide the full Markdown content in chat and clearly state that saving failed.

## Quality Bar

- Make answers senior-level: connect API behavior to runtime/storage/network internals and production incidents.
- Include concrete examples, pseudocode, SQL, or config snippets when they clarify the mechanism.
- Avoid hallucinating exact source paths for versions that may differ. Say "typical implementation includes..." or "in common versions..." when needed.
- If the user asks for interview prep, make questions progressively harder and include follow-up probes.
- If the user asks for a daily/random topic, choose one topic and state why it is worth learning.

## Resources

- `references/answer-standard.md`: detailed output template, interview question rubric, and domain-specific depth prompts.
