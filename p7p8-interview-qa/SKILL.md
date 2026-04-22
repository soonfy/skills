---
name: p7p8-interview-qa
description: "Use when the user provides one software engineering knowledge point and wants Alibaba, Tencent, Meituan, or other Big Tech P7/P8-level interview preparation. Generate exactly 3 progressively deeper interview questions, complete senior-level answers, one realistic production scenario that connects the 3 Q&A items, and save the complete content to a Markdown file whose filename starts with interview-."
---

# P7/P8 Interview Q&A

Generate a focused Chinese interview drill from one knowledge point. The output must help the user answer like a senior engineer who can connect concepts, implementation details, production incidents, tradeoffs, and measurable signals.

The complete generated content must be written to a Markdown file. The chat response should report the saved file path and a concise summary, not paste the entire article unless the user explicitly asks.

## Input Handling

- Treat the user's knowledge point as the center topic.
- If the user only gives a broad domain, choose a high-value subtopic and state the choice briefly.
- Assume backend/platform engineering, Big Tech P7/P8 depth, and production/system-design orientation unless the user specifies another role.
- Write the generated interview content in Chinese by default.
- Do not generate more or fewer than 3 main questions unless the user explicitly asks.

## File Output Rules

- Save the complete generated interview drill as a `.md` file in the current working directory unless the user specifies another output directory.
- The filename must start with `interview-`.
- Use a lowercase ASCII slug derived from the knowledge point after the `interview-` prefix, for example:
  - `interview-redis-distributed-lock.md`
  - `interview-mysql-mvcc.md`
  - `interview-jvm-gc.md`
- If the target filename already exists, do not overwrite it unless the user explicitly asks. Append a numeric suffix such as `interview-redis-distributed-lock-2.md`.
- After saving, respond with the absolute file path and a short summary of what was generated.
- If filesystem writes fail, provide the complete Markdown content in chat and clearly state that saving failed.

## Generated File Metadata

Every generated Markdown file must begin with YAML frontmatter metadata. Put the frontmatter at the very top of the file before the title heading.

Use this schema:

```yaml
---
title: <Chinese title for the interview drill>
author:
  - soonfy
date: YYYY-MM-DD
description: <One-sentence Chinese summary of the generated interview drill>
tags:
  - <topic tag>
  - <domain tag>
  - <interview tag>
reading_time: <integer minutes>
---
```

Metadata rules:

- `title`: use the final Chinese article title, usually `<knowledge point>: P7/P8 Big Tech Interview 3 Questions and Answers` translated naturally into Chinese.
- `author`: always use a YAML list with the single value `soonfy`.
- `date`: use the current date in `YYYY-MM-DD` format.
- `description`: write one concise Chinese sentence describing the interview drill.
- `tags`: infer 4-7 useful tags from the topic and domain. Prefer lowercase English technical tags when standard, and Chinese tags when they are clearer, such as `redis`, `缓存`, `分布式系统`, `面试`, `高并发`.
- `reading_time`: estimate the reading/study time as an integer number of minutes.
- Keep the metadata content aligned with the generated file. Do not reuse unrelated examples.

## Question Design

Design the 3 questions as a progression:

1. Mechanism question: test whether the candidate can explain the core mechanism, invariants, data structures, protocols, or runtime behavior.
2. Tradeoff question: test whether the candidate can compare alternatives, state boundaries, identify failure modes, and defend design choices.
3. Scenario question: test whether the candidate can apply the topic in a real production problem, including diagnosis, mitigation, and long-term governance.

Make the questions feel like Alibaba/Tencent/Meituan senior interviews:

- Alibaba style: scale, stability, cost, architecture evolution, data correctness.
- Tencent style: high concurrency, latency, user experience, availability, multi-region or large traffic operations.
- Meituan style: O2O/business peak traffic, transactions, cache/queue/storage consistency, incident response, operational metrics.

## Answer Standard

For each question, include these fields in Chinese:

- Question.
- Interviewer intent.
- P7/P8 complete answer.
- Key follow-up probes.
- Common traps.

Each complete answer must include:

- Concrete mechanisms, such as data structures, algorithms, protocols, transaction models, runtime modules, source-level concepts, configuration knobs, or operational controls when relevant.
- A production example with traffic shape, symptom, root cause, diagnosis path, and mitigation.
- Tradeoffs and boundaries: when the answer works, when it fails, and what residual risk remains.
- Measurable signals such as p95/p99 latency, QPS, error rate, slowlog, lock wait, CPU, memory, queue depth, cache hit rate, replication lag, GC pause, or connection count.
- Defensive phrasing for follow-up pressure: explain why the chosen approach is reasonable under constraints.

If an answer can be finished in under 30 seconds, expand it until it becomes a 1-3 minute senior-level answer.

## Scenario Thread

After the 3 Q&A items, write one realistic production scenario that connects them:

- Use one realistic business scenario, not three unrelated examples.
- Make the scenario concrete: business background, traffic profile, architecture components, failure symptom or design challenge.
- Map the scenario to the 3 questions in order:
  - Q1 explains the underlying mechanism.
  - Q2 explains the design tradeoff.
  - Q3 explains the production handling or architecture decision.
- End with a short interview speaking-flow paragraph that shows how a candidate can connect the three answers naturally.

## Markdown Structure

Use this structure in the saved file:

```markdown
---
title: <Chinese title>
author:
  - soonfy
date: YYYY-MM-DD
description: <Chinese one-sentence summary>
tags:
  - <tag>
reading_time: <integer>
---

# <knowledge point>: P7/P8 Big Tech Interview 3 Questions and Answers

## 1. Interview Positioning
<Why this topic matters at P7/P8 level>

## 2. Three Questions and Complete Answers

### Question 1: <mechanism title>
- **Question**:
- **Interviewer Intent**:
- **P7/P8 Complete Answer**:
- **Key Follow-ups**:
- **Common Traps**:

### Question 2: <tradeoff title>
...

### Question 3: <scenario title>
...

## 3. One Real Production Scenario Connecting the 3 Q&A Items
<Scenario narrative and mapping>

## 4. Interview Speaking Flow
<A compact answer flow the user can speak aloud>
```

The headings may be translated into Chinese in the actual generated file.

## Quality Checks

Before finalizing, verify:

- A Markdown file was created and its filename starts with `interview-`.
- The Markdown file starts with valid YAML frontmatter containing `title`, `author`, `date`, `description`, `tags`, and `reading_time`.
- Exactly 3 main questions are present.
- Every question has a complete answer, not only bullet labels.
- The scenario connects all 3 questions in one story.
- The content reaches P7/P8 depth: mechanisms, tradeoffs, failure modes, metrics, and follow-ups are all present.
- Avoid hallucinating exact source-code paths or version-specific behavior. When uncertain, say that typical implementations or specific versions may differ.
