# AI Daily Interviews Answer Standard

Use this reference to generate high-signal programmer knowledge lessons and interview preparation material, then save the result as an Obsidian-friendly Markdown file in the current working directory and also provide the generated content in chat.

## Default Audience

- Backend or platform engineer preparing for mid-to-senior interviews.
- Assume the reader can code but needs systematic knowledge, internals, tradeoffs, and production reasoning.
- Default language: Chinese.

## Artifact Structure

Use this structure in the saved Markdown file and chat response unless the user requests a different format:

```markdown
---
title: <中文知识点标题>
author:
  - soonfy
date: YYYY-MM-DD
description: <这是内容摘要。>
tags:
  - <标签1>
  - <标签2>
reading_time: 30
---

# <知识点>

## 1. 学习定位
- 一句话定义
- 为什么大厂爱问
- 需要掌握到什么程度

## 2. 知识图谱
- 核心概念
- 底层机制
- 工程实践
- 常见坑
- 面试高频追问

## 3. 系统讲解
### 3.1 基础概念
### 3.2 核心原理
### 3.3 源码/实现视角
### 3.4 实际应用场景
### 3.5 常见故障与边界条件
### 3.6 优化方向

## 4. 面试问答
### Q1. <深度问题>
- 考察点：
- 系统回答：
- 原理：
- 源码/实现：
- 场景：
- 优化：
- 常见误区：
- 追问：

## 5. 推荐相关知识点

1. <相关知识点 1>：<为什么建议学>
2. <相关知识点 2>：<为什么建议学>
3. <相关知识点 3>：<为什么建议学>

## 6. 引用与延伸阅读

- [<可靠来源名称>](<URL>)：<引用原因>

## 7. 复习清单
```

## Obsidian Metadata Rules

- Put YAML frontmatter at the top of the Markdown file.
- Include `title`, `author`, `date`, `description`, `tags`, and `reading_time` exactly as top-level metadata keys.
- `title` should match the final note title.
- `author` must be a YAML list containing `soonfy`.
- Use the current date in `YYYY-MM-DD` format for `date`.
- `description` should be a concise one-sentence summary of the note.
- `tags` should be inferred from the topic and written as a YAML block list. Preserve important Chinese terms when they are the natural study tags, for example `redis`, `穿透`, `击穿`, `雪崩`.
- `reading_time` should be an integer estimate of study time in minutes. Use 20-30 minutes for short focused notes, 35-50 minutes for standard deep notes, and 60+ minutes for broad multi-topic notes.

## File Writing Requirements

- Save the generated artifact to the current working directory as Markdown.
- Default filename pattern: `interview-<topic-slug>.md`.
- Build `<topic-slug>` from the primary topic using lowercase ASCII words separated by hyphens, for example `mysql-mvcc`, `redis-distributed-lock`, `python-gil`, or `nodejs-event-loop`.
- If the file exists, create the next available suffix: `-2`, `-3`, and so on. Do not overwrite existing notes unless the user explicitly requests overwrite.
- The saved file must contain the full artifact, not only a summary.
- The final chat response should point to the saved file and include the generated content directly unless the user explicitly asks for file-only output.

## Depth Rubric

For every important topic, cover these layers:

1. API/usage layer: what developers see and how it behaves.
2. Runtime/storage/protocol layer: what actually happens underneath.
3. Source/implementation layer: major data structures, algorithms, modules, or classes.
4. Concurrency/failure layer: races, locks, ordering, durability, memory, timeouts, retries, split brain, or partial failure.
5. Production layer: observability, tuning knobs, capacity, incident patterns, and rollback strategy.
6. Interview layer: what the interviewer is really testing and what follow-up pressure reveals.

## Question Design Rules

- Generate 5-8 questions for a focused topic, 8-12 for broad interview prep.
- Make at least half of the questions scenario-based or tradeoff-based.
- Include one source-code/internals question, one production troubleshooting question, and one optimization/design question.
- Questions should be answerable without memorizing obscure line numbers, but the answers should mention concrete implementation details.
- Avoid questions whose answer is only a definition.

## Related Knowledge Recommendations

Add exactly 3 related knowledge points after the interview Q&A. Choose topics that naturally deepen the user's understanding, such as adjacent internals, production failure modes, or design patterns. For each recommendation, include:

- Topic name.
- Why it is related.
- What question it helps answer next.

Example for Redis cache penetration/breakdown/avalanche:

1. Redis 分布式锁：理解击穿治理中的互斥重建和锁安全释放。
2. Redis 持久化与主从复制：理解缓存层故障、恢复和数据丢失窗口。
3. 服务限流熔断降级：理解缓存雪崩时如何保护数据库和核心链路。

## References Section

Add a references section named `## 引用与延伸阅读`.

- Prefer official documentation, source repositories, standards, RFCs, PEPs, JEPs, engineering blogs from the owning project/vendor, and authoritative design docs.
- Include GitHub links for source-code-level topics when available, for example CPython, OpenJDK, Node.js, Redis, MySQL, or framework repositories.
- Include official docs for user-facing behavior and configuration.
- Do not cite low-quality reposts, SEO farms, or unsourced summaries when reliable primary sources exist.
- When browsing is available and the user asks for citations or source links, verify current official URLs before finalizing.
- Each reference should include a short note explaining why it is useful.

## Answer Requirements

Each answer should include:

- Direct conclusion first.
- Layered explanation from concept to mechanism.
- Concrete data structures, algorithms, or source modules when known.
- Practical example from production.
- Optimization and monitoring signals.
- Common mistakes and interviewer follow-ups.

## Domain Prompts

### Python

Probe CPython implementation when relevant: GIL scheduling, bytecode, reference counting plus cyclic GC, dict/hash table layout, descriptors, MRO, coroutine state machine, event loop scheduling, import lock, multiprocessing serialization cost.

Good interview directions:
- Why CPU-bound Python threads do not scale and when they still help.
- How `asyncio` differs from threads and why blocking calls poison the event loop.
- Why Python dict is fast and what happens during resize/hash collision.
- How generators/coroutines preserve execution state.

### Java/JVM

Probe JVM internals: JMM happens-before, biased/lightweight/heavy locks where applicable by version, AQS queueing, thread pool state machine, class loading, GC roots, generational collection, JIT, escape analysis, Spring proxy/transaction boundaries.

Good interview directions:
- `volatile` vs `synchronized` vs CAS/AQS.
- Why thread pools can still take down a service.
- How GC tuning connects to latency SLOs.
- Why Spring transactions fail on self-invocation.

### Node.js

Probe V8 and libuv: event loop phases, microtasks, timers, poll/check, thread pool, streams and backpressure, Buffer memory, worker_threads, cluster, V8 hidden classes and GC.

Good interview directions:
- Why Node.js handles high concurrency but not CPU-heavy work by default.
- How Promise microtasks can starve IO.
- How stream backpressure prevents memory explosion.
- When to use worker_threads vs child_process vs cluster.

### Agent/LLM Applications

Probe architecture and reliability: tool calling schema, planner/executor loops, context window limits, memory design, RAG retrieval quality, evaluation harnesses, guardrails, prompt injection, idempotent tools, human-in-the-loop, multi-agent coordination.

Good interview directions:
- How to design a reliable tool-using agent for a production workflow.
- How RAG fails and how to measure retrieval quality separately from generation quality.
- How to prevent prompt injection from tool outputs or retrieved documents.
- Why multi-agent systems can amplify errors and how to bound them.

### MySQL

Probe InnoDB: B+Tree indexes, clustered index, secondary index back-to-table lookup, MVCC read views, undo/redo logs, binlog, doublewrite buffer, locks/gap locks/next-key locks, isolation levels, optimizer, replication lag.

Good interview directions:
- Why an index can fail or become slower than a full scan.
- How MVCC implements repeatable read and what phantom prevention really means in InnoDB.
- How redo, undo, and binlog cooperate in crash recovery and replication.
- How to diagnose slow SQL from plan, cardinality, and lock waits.

### Redis

Probe internals: single-threaded command execution model, IO threading in newer versions, dict incremental rehash, SDS, ziplist/listpack/quicklist, skiplist, persistence RDB/AOF, eviction, replication, Sentinel/Cluster, Lua atomicity.

Good interview directions:
- Why Redis is fast and where it is not fast.
- How cache penetration, breakdown, and avalanche differ and how to mitigate each.
- Why distributed locks are hard and when Redlock is or is not enough.
- How persistence settings affect latency and data loss windows.

## Optimization Checklist

Tie optimization advice to measurable signals:

- Latency: p50/p95/p99, queueing time, GC pauses, slow query logs.
- Throughput: QPS, event-loop lag, thread pool saturation, CPU run queue.
- Resource: memory fragmentation, heap usage, connection count, file descriptors.
- Correctness: duplicate processing, stale reads, lost updates, lock timeout, retry storms.
- Cost: over-indexing, cache hit rate, cold starts, unnecessary serialization.

## Final Quality Pass

Before responding, check:

- Did the Markdown start with valid Obsidian-friendly YAML frontmatter containing `title`, `author`, `date`, `description`, `tags`, and `reading_time`?
- Does the saved filename start with `interview-`?
- Did the response still include the generated content directly, not only the file path?
- Did the answer explain "why" and "how", not just "what"?
- Did it include source or implementation perspective without pretending version-specific certainty?
- Did every interview answer include scenario, optimization, and common traps?
- Did it include exactly 3 related knowledge recommendations?
- Did it include reliable references with official/GitHub sources where possible?
- Are the questions difficult enough for mid-to-senior Big Tech interviews?
- Is the content organized so the user can study from it directly?
