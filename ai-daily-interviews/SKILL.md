---
name: ai-daily-interviews
description: Use when the user asks to learn, explain, summarize, prepare interviews for, or generate deep interview Q&A about Python, Java, Node.js, agents/LLM applications, MySQL, Redis, operating systems, networks, concurrency, JVM, CPython, V8, Spring, async runtimes, message queues, caching, storage, architecture, or other software engineering fundamentals.
---

# AI Daily Interviews

## Overview

Create a rigorous Obsidian-friendly Markdown learning artifact for one or more programmer topics at Big Tech P7/P8+ interview depth: metadata, learning path, topic map, systematic explanation, implementation/source-code perspective, production scenarios, optimization guidance, complete deep interview Q&A, related knowledge recommendations, and reliable references. Save the artifact to the current working directory, then also provide the generated content in chat.

Core standard: the output must train the user to answer like a senior engineer who can design systems, explain internals, debug production incidents, and defend tradeoffs under follow-up pressure. Do not produce outline-only answers.

## Workflow

1. Identify the target topic(s), seniority level, and interview direction from the user request. If unspecified, assume backend/platform engineer, Big Tech P7/P8+ interview depth, and production/system-design orientation.
2. Read `references/answer-standard.md` before drafting the artifact.
3. Classify the request:
   - Broad domain, such as `Redis`, `MySQL`, `JVM`, `操作系统`, or `计算机网络`: produce a complete study path plus high-frequency interview system.
   - Focused topic, such as `Redis 分布式锁` or `MySQL MVCC`: produce a deep single-topic note.
   - Daily/random request: choose one high-value topic and explain why it is worth studying today.
4. For broad domains, include an executable learning path, stage goals, high-frequency questions, practical project/application scenarios, and a 7/14/30-day sprint plan when useful.
5. Prefer depth over trivia. Explain invariants, tradeoffs, failure modes, source-code mechanisms, and production consequences.
6. Include interview questions that test reasoning under constraints. Avoid shallow definitions unless they are used as warm-up questions.
7. Every interview question must include a complete answer. Do not stop at bullets such as "考察点/原理/场景" without writing the actual senior-level answer.
8. Include 3 related knowledge points the user should study next.
9. Include a references section with reliable sources such as official documentation, source repositories, RFCs, PEPs, JEPs, design docs, or authoritative project docs. Browse or verify current official links when source accuracy matters and network access is available.
10. Write the final artifact to a Markdown file in the current working directory. After writing, respond with the saved file path and the generated content, unless the user explicitly asks for file-only output.

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

For broad domains, also include:

- Learning panorama: what "mastery" means at P7/P8+ level.
- Stage-based learning path: what to learn first, what to skip, and what must be drilled.
- High-frequency Big Tech interview map.
- Practical project or production scenario recommendations.
- Sprint plan, usually 7 or 14 days, with daily goals and expected interview expressions.

## P7/P8+ Answer Depth

Every important explanation and every interview answer must reach this bar:

- Start with a direct conclusion, not a vague preface.
- Explain from API/usage behavior down to runtime/storage/network/source-level mechanism.
- Name concrete data structures, algorithms, protocols, modules, or configuration knobs when known.
- Include a production scenario: traffic shape, failure symptom, incident cause, diagnosis path, and mitigation.
- State tradeoffs and boundaries: when the answer works, when it fails, and what risk remains.
- Include measurable signals: p95/p99 latency, cache hit rate, slowlog, CPU, memory fragmentation, replication lag, connection count, error rate, or queue depth as applicable.
- Include interviewer follow-ups and how to defend the answer under pressure.

If an answer can be answered in under 30 seconds, expand it until it becomes a 1-3 minute senior-level interview answer.

## Complete Q&A Requirement

For each question, write the full answer content. A valid answer is not:

```markdown
- 考察点：Redis 为什么快
- 原理：内存 + 单线程 + IO 多路复用
- 场景：高并发缓存
```

A valid answer must include:

```markdown
- 考察点：面试官想确认你是否能把 Redis 的性能优势讲到网络模型、执行模型、数据结构和瓶颈边界。
- 完整回答：
  Redis 快首先不是因为某一个点，而是多个设计叠加的结果...
- 原理展开：
  1. 内存访问避免磁盘随机 IO...
  2. 单线程命令执行避免锁竞争...
  3. IO 多路复用让一个线程管理大量连接...
- 生产场景：
  在秒杀库存缓存中...
- 追问与防守：
  如果面试官追问 Redis 6 多线程...
```

Do not compress complete answers into placeholder labels.

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

- Make answers P7/P8+ senior-level: connect API behavior to runtime/storage/network internals, source-code mechanisms, system design, and production incidents.
- Include concrete examples, pseudocode, SQL, or config snippets when they clarify the mechanism.
- Avoid hallucinating exact source paths for versions that may differ. Say "typical implementation includes..." or "in common versions..." when needed.
- If the user asks for interview prep, make questions progressively harder and include follow-up probes.
- If the user asks for a daily/random topic, choose one topic and state why it is worth learning.
- If the user asks for a broad domain such as Redis, MySQL, JVM, or operating systems, produce a learning path plus interview drill plan before the Q&A.
- If any Q&A item lacks a complete answer, revise before finalizing.

## Resources

- `references/answer-standard.md`: detailed output template, interview question rubric, and domain-specific depth prompts.
