# AI Daily Interviews Answer Standard

Use this reference to generate high-signal programmer knowledge lessons and interview preparation material, then save the result as an Obsidian-friendly Markdown file in the current working directory and also provide the generated content in chat.

## Default Audience

- Backend or platform engineer preparing for Big Tech P7/P8+ interviews.
- Assume the reader can code and has project experience, but needs systematic knowledge, internals, tradeoffs, production reasoning, and high-pressure interview expression.
- Default language: Chinese.

## Target Depth

The artifact should help the user answer like a senior engineer, not a keyword memorizer.

Target level:

- P7: can independently own important production modules, explain design tradeoffs, debug incidents, and connect implementation details to business-facing reliability.
- P8+: can reason across architecture, scale, failure domains, capacity, consistency, maintainability, and organizational cost; can push back on unsafe assumptions in an interview.

For broad topics such as Redis, MySQL, JVM, operating systems, networks, or message queues, the output must be closer to a complete interview preparation guide than a short note.

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
- 完整回答：
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

For broad domains, insert these sections before `## 4. 面试问答`:

```markdown
## 4. 阶段化学习路径
### 第一阶段：基础使用
### 第二阶段：核心机制
### 第三阶段：高并发与分布式
### 第四阶段：源码/底层原理
### 第五阶段：实战项目与面试表达

## 5. 高频面试地图

## 6. 冲刺计划
### Day 1 ...
```

Then continue with deep Q&A and adjust numbering naturally.

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

## P7/P8+ Depth Rubric

A P7/P8+ answer must include more than "what it is":

1. Conclusion: answer the question directly in the first 1-2 sentences.
2. Mechanism: explain the invariant or execution path underneath.
3. Implementation: mention concrete data structures, algorithms, modules, files, protocols, or configuration knobs when known.
4. Production: describe at least one real scenario, including symptom, diagnosis, mitigation, and residual risk.
5. Tradeoff: say why this solution is chosen and what it costs.
6. Metrics: name observable signals such as p95/p99 latency, cache hit rate, slowlog, CPU, memory fragmentation, replication lag, lock wait, GC pause, queue depth, or error rate.
7. Follow-up defense: include how to answer the likely next question from the interviewer.

If an answer only contains definitions or bullets without explanation, it fails this standard.

## Question Design Rules

- Generate 5-8 questions for a focused topic, 8-12 for broad interview prep.
- Make at least half of the questions scenario-based or tradeoff-based.
- Include one source-code/internals question, one production troubleshooting question, and one optimization/design question.
- Questions should be answerable without memorizing obscure line numbers, but the answers should mention concrete implementation details.
- Avoid questions whose answer is only a definition.
- For broad topics, include a learning-path section and a sprint-plan section before the Q&A.
- For every Q&A item, write a complete answer. Do not leave "考察点/原理/场景/优化" as labels without full content.
- Make Q&A progressively harder: warm-up, internals, production incident, system design, tradeoff challenge, and follow-up pressure.

## Complete Answer Contract

Every interview answer must use this contract unless the user requests a shorter format:

```markdown
### Q1. <问题>

- 考察点：<面试官真正想验证什么能力。>
- 完整回答：
  <先给直接结论，再用 2-5 段把机制、边界和场景讲完整。内容要像 1-3 分钟口述回答，而不是关键词清单。>
- 原理展开：
  1. <关键机制 1>
  2. <关键机制 2>
  3. <关键机制 3>
- 源码/实现视角：
  <提到典型数据结构、模块、算法、协议或配置；不确定版本时说明依赖版本。>
- 生产场景：
  <给出真实工程场景：流量、症状、风险、排查路径、治理方案。>
- 优化与监控：
  <列出优化手段和可观测指标。>
- 常见误区：
  <指出候选人容易答错或答浅的点。>
- 追问：
  <给出 2-3 个面试官可能继续追的问题。>
```

The `完整回答` field is mandatory and must be substantive.

## Broad Topic Playbook

When the user asks only for a broad domain, such as "Redis", "MySQL", "JVM", "操作系统", or "计算机网络", do not jump directly into scattered Q&A. Produce a complete path:

1. 学习全景图：explain what mastery means.
2. 阶段化学习路径：divide into 4-6 phases with time suggestions.
3. 每阶段必须掌握：concepts, internals, common commands/APIs, and interview expressions.
4. 高频面试题：group by basics, internals, high concurrency, distributed systems, production troubleshooting, and system design.
5. 实战项目：recommend at least one project or production scenario that proves ability.
6. 冲刺计划：for interview prep, provide a 7-day or 14-day plan with daily goals and answer templates.
7. Deep Q&A：write complete answers for the most important questions.

Example expectations for Redis:

- Include five layers: basics, core data structures, high concurrency/distributed features, internals/source perspective, production scenarios/interview expression.
- Cover SDS, dict, incremental rehash, quicklist/listpack, skiplist, single-threaded command execution, IO multiplexing, Redis 6+ IO threading, RDB/AOF, replication, Sentinel, Cluster slots, eviction, expiration, big key, hot key, cache penetration/breakdown/avalanche, distributed locks, delay queues, rate limiting, streams, and leaderboard scenarios when relevant.
- Include a sprint plan such as Day 1 "Redis 为什么快", Day 2 "数据结构", Day 3 "缓存问题", Day 4 "持久化", Day 5 "主从/哨兵", Day 6 "Cluster", Day 7 "分布式锁/实战", then deepen with memory, big key/hot key, source, project, and mock interviews if using a 14-day plan.
- Every high-frequency question needs a complete answer, not only a topic list.

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
- P7/P8-level tradeoff analysis: explain why this approach works, what it costs, and when it breaks.
- A defensible answer to the likely next follow-up.

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

For a broad Redis request, include:

- A 0-to-interview learning map with five levels: basic usage, data structures, high concurrency/distributed features, internals/source perspective, and production/interview expression.
- A staged path with suggested timing and explicit "必须掌握" items.
- A high-frequency interview map covering fundamentals, internals, high concurrency, distributed systems, production incidents, and design scenarios.
- A sprint plan, preferably 14 days when the user wants interview preparation.
- Complete answers for core questions such as:
  - Redis 为什么快？
  - Redis 真的是单线程吗？
  - SDS 为什么不用 C 字符串？
  - 跳表为什么适合 Redis ZSet？
  - 缓存穿透、击穿、雪崩、热 key 怎么治理？
  - RDB、AOF、混合持久化如何选择？
  - 主从复制、哨兵和 Cluster 的故障切换风险是什么？
  - 分布式锁如何保证安全释放？锁过期怎么办？
  - 大 key 和热 key 如何发现、拆分和治理？

Each Redis answer should connect concept -> data structure/protocol -> production symptom -> mitigation -> monitoring signal.

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
- Does every Q&A include a substantive `完整回答` section?
- For broad topics, did the artifact include a learning path, interview map, and sprint plan?
- Would the answer satisfy a P7/P8 interviewer, including follow-up pressure and production tradeoffs?
