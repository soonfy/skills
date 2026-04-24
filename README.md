# Personal Skills

这是一个个人维护的 skills 仓库，用来保存、同步和复用我在 Codex / Agents 工作流中常用的自定义 skill。

每个 skill 都是一个独立目录，目录中至少包含一个 `SKILL.md` 文件。`SKILL.md` 描述触发场景、使用目标、工作流程、输出要求和质量检查规则；如果某个 skill 需要更详细的模板、参考标准、agent 配置或其他资源，也会放在该 skill 自己的子目录中，避免和其他 skill 产生隐式依赖。

## 项目结构

```text
skills/
├── README.md
├── .gitignore
├── ai-daily-interviews/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       └── answer-standard.md
├── p7p8-interview-qa/
│   ├── SKILL.md
│   └── agents/
│       └── openai.yaml
├── paper-deep-study/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── answer-standard.md
│       └── example-answer-self-evolving-agents-survey.md
├── redbook-publisher/
│   └── SKILL.md
└── wechat-publisher/
    └── SKILL.md
```

## Skills 列表

| Skill 名称 | 用途 | 目录 |
| --- | --- | --- |
| `ai-daily-interviews` | 生成系统化的技术面试学习笔记，默认达到大厂 P7/P8+ 深度，并保存为 Obsidian 友好的 Markdown 文件。 | `ai-daily-interviews/` |
| `p7p8-interview-qa` | 围绕一个软件工程知识点生成 3 个递进式大厂 P7/P8 面试问题、完整回答和一个贯穿生产场景，并保存为 `interview-*.md` 文件。 | `p7p8-interview-qa/` |
| `paper-deep-study` | 读取论文 URL、PDF 或 `.docx`，生成面向计算机新人的深度 Markdown 学习笔记；当输入为 URL 时，同时保存原文 PDF。 | `paper-deep-study/` |
| `redbook-publisher` | 将 Markdown、笔记、文章、课程内容或知识文档转成小红书 / Redbook 风格图文卡片方案、发布文案或竖版 PNG 卡片。 | `redbook-publisher/` |
| `wechat-publisher` | 将 Markdown、笔记、文章、课程内容或知识文档转成微信公众号发布包，包括标题、摘要、正文、配图方案、发布检查清单和 Word 文档。 | `wechat-publisher/` |

## Skill 说明

### `ai-daily-interviews`

面向“每日技术面试学习”工作流，适合把一个后端、AI 应用、系统设计或工程基础知识点整理成可复习、可沉淀、可面试表达的 Markdown 笔记。

主要能力：

- 默认中文输出，面向后端 / 平台工程师的大厂 P7/P8+ 面试准备。
- 生成 Obsidian 友好的 Markdown 文件，包含 YAML frontmatter、学习定位、知识图谱、系统讲解、源码 / 实现视角、生产场景、优化方向、深度 Q&A、延伸阅读和复习清单。
- 对 Redis、MySQL、JVM、操作系统、计算机网络等广域主题，会先生成学习路径、高频面试地图和冲刺计划，再进入深度问答。
- 强制每个面试问题给出完整回答，避免只输出提纲。
- 通过 `references/answer-standard.md` 固化输出模板和 P7/P8+ 深度标准。

适合场景：

- 每天生成一个技术知识点的面试复习笔记。
- 准备 Python、Java、Node.js、MySQL、Redis、系统设计或 Agent 应用相关面试。
- 把零散知识点整理成可以长期沉淀到 Obsidian 的学习材料。
- 训练“直接结论 + 机制拆解 + 生产案例 + 面试追问”的答题结构。

示例请求：

```text
使用 ai-daily-interviews，讲清楚 Redis，并生成 P7/P8 深度面试学习路径和问答。
```

```text
帮我生成一篇 Node.js event loop 的中高级面试学习笔记。
```

### `p7p8-interview-qa`

面向“单个知识点的高强度面试训练”工作流。相比 `ai-daily-interviews`，它更聚焦：围绕一个知识点生成 3 个递进问题，并用同一个真实生产场景串起来。

主要能力：

- 默认中文输出，面向阿里、腾讯、美团等大厂 P7/P8 面试准备。
- 精确生成 3 个主问题：机制题、权衡题、场景题。
- 每个问题都要求完整 senior-level answer，覆盖结论、机制、实现、生产场景、监控指标、常见误区和追问。
- 生成一个贯穿 3 个问答的真实生产场景，帮助把知识点讲成工程能力。
- 保存完整内容到 `interview-*.md` 文件。

适合场景：

- 针对一个知识点做面试专项训练。
- 把“会背概念”升级成“能讲原理、能讲线上问题、能讲取舍”。
- 快速准备一个可反复口述练习的 P7/P8 面试材料。

示例请求：

```text
使用 p7p8-interview-qa，把 Redis 分布式锁整理成 3 道 P7/P8 面试题。
```

```text
用 p7p8-interview-qa 生成 MySQL MVCC 的大厂面试问答。
```

### `paper-deep-study`

面向“论文 / 技术文章深度学习”工作流，适合把论文 URL、PDF 文件或 `.docx` 文档转成一份从浅到深、对计算机新人友好的 Markdown 学习笔记。

主要能力：

- 支持输入论文 URL、PDF 和 `.docx` 文件。
- 输出结构化的 `paper-study-*.md` 学习笔记。
- 当输入是 URL 且可下载 PDF 时，会顺手保存原文 PDF。
- 固定包含作者与机构信息、论文主旨、背景知识、由浅入深讲解、方法 / 系统 / 实验解释、优点与局限、术语表和学习清单。
- 通过 `references/answer-standard.md` 固化输出结构与质量标准。
- 通过 `references/example-answer-self-evolving-agents-survey.md` 提供正式示例答案，约束输出风格和深度。

适合场景：

- 精读一篇 arXiv 论文并生成学习笔记。
- 把 PDF 论文整理成适合新手阅读的中文讲解。
- 读取 Word 格式的技术白皮书、研究稿件或长文说明，并输出学习笔记。
- 为后续分享、复习、面试或知识沉淀生成可复用 Markdown 文档。

示例请求：

```text
使用 paper-deep-study，读这个论文 URL，生成 Markdown 学习笔记和原文 PDF。
```

```text
使用 paper-deep-study，读取这个 PDF，帮我从浅到深讲清楚，并保存成 Markdown 文件。
```

### `redbook-publisher`

面向“小红书 / Redbook 图文卡片”工作流，适合把结构化或半结构化知识内容压缩成更适合手机阅读和发布的视觉化卡片。

主要能力：

- 将 Markdown、学习笔记、文章、课程转录稿、技术解释等内容拆解成 5-9 张图文卡片。
- 默认中文输出，默认竖版尺寸为 `1242x1660`，也可以按需使用 `1080x1440`。
- 产出卡片脚本、视觉方向、发布标题、正文、话题标签和首评 / 置顶评论。
- 发布文案默认控制在适合小红书阅读的长度，并可适度使用功能性 emoji。
- 在需要生成实际图片时，要求保持统一网格、字体层级、色彩系统和移动端可读性。

适合场景：

- 技术文章转小红书知识卡片。
- 读书笔记、课程笔记、学习总结可视化。
- 面试知识点整理成社交媒体卡片。
- AI 应用开发、产品策略、工程实践等专业内容的图文发布。

示例请求：

```text
使用 redbook-publisher，把下面的 Markdown 笔记做成小红书图文卡片方案。
```

```text
根据这份技术文章，生成 Redbook 发布文案和 7 张卡片脚本。
```

### `wechat-publisher`

面向“微信公众号发布包”工作流，适合把长文、课程内容、技术文章或知识文档改写成适合微信公众号阅读和发布的成品材料。

主要能力：

- 生成 `wechat-publish-package.md`。
- 生成同内容的 `wechat-publish-package.docx` Word 文档。
- 提供 5-8 个标题选项，并推荐最终标题。
- 生成微信公众号摘要、正文、封面图 brief、正文配图 brief 和发布检查清单。
- 正文强调移动端阅读节奏、段落层次、可信表达和清晰论证。
- 技术内容会保留准确术语，并优先使用“问题 -> 原理 -> 机制 -> 例子 -> 结论”的结构。

适合场景：

- 将技术文章改写成公众号文章。
- 将课程笔记、学习总结或访谈内容整理成可发布长文。
- 为个人 IP、产品思考、AI 应用实践或专业观点文章生成发布包。
- 需要同时拿到 Markdown 和 Word 文档的发布材料。

示例请求：

```text
使用 wechat-publisher，把这篇 Markdown 改写成微信公众号发布包。
```

```text
根据这份 AI 应用开发笔记，生成公众号标题、摘要、正文和配图方案。
```

## 安装方式

### 方式一：克隆整个仓库

```bash
git clone git@github.com:soonfy/skills.git
cd skills
```

克隆后可以按需复制某个 skill 目录到本机的个人 skills 目录。

### 方式二：安装全部 skill 到 Codex

macOS / Linux 示例：

```bash
mkdir -p ~/.codex/skills
cp -R ./ai-daily-interviews ~/.codex/skills/
cp -R ./p7p8-interview-qa ~/.codex/skills/
cp -R ./paper-deep-study ~/.codex/skills/
cp -R ./redbook-publisher ~/.codex/skills/
cp -R ./wechat-publisher ~/.codex/skills/
```

Windows PowerShell 示例：

```powershell
New-Item -ItemType Directory -Force $env:USERPROFILE\.codex\skills
Copy-Item -Recurse .\ai-daily-interviews $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\p7p8-interview-qa $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\paper-deep-study $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\redbook-publisher $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\wechat-publisher $env:USERPROFILE\.codex\skills\
```

### 方式三：安装全部 skill 到 Agents

macOS / Linux 示例：

```bash
mkdir -p ~/.agents/skills
cp -R ./ai-daily-interviews ~/.agents/skills/
cp -R ./p7p8-interview-qa ~/.agents/skills/
cp -R ./paper-deep-study ~/.agents/skills/
cp -R ./redbook-publisher ~/.agents/skills/
cp -R ./wechat-publisher ~/.agents/skills/
```

Windows PowerShell 示例：

```powershell
New-Item -ItemType Directory -Force $env:USERPROFILE\.agents\skills
Copy-Item -Recurse .\ai-daily-interviews $env:USERPROFILE\.agents\skills\
Copy-Item -Recurse .\p7p8-interview-qa $env:USERPROFILE\.agents\skills\
Copy-Item -Recurse .\paper-deep-study $env:USERPROFILE\.agents\skills\
Copy-Item -Recurse .\redbook-publisher $env:USERPROFILE\.agents\skills\
Copy-Item -Recurse .\wechat-publisher $env:USERPROFILE\.agents\skills\
```

### 方式四：只安装单个 skill

把命令里的目录名替换成需要的 skill 即可。

```powershell
Copy-Item -Recurse .\p7p8-interview-qa $env:USERPROFILE\.agents\skills\
```

## 使用方式

安装完成后，在支持 skills 的环境中直接提出与触发场景匹配的请求即可。也可以显式点名 skill，减少歧义。

```text
使用 ai-daily-interviews，生成一篇 Redis 的 P7/P8 面试学习路径。
```

```text
使用 p7p8-interview-qa，围绕 JVM GC 生成 3 道大厂面试题和完整回答。
```

```text
使用 paper-deep-study，读这篇论文 URL，生成 Markdown 学习笔记和原文 PDF。
```

```text
使用 redbook-publisher，把这篇 Markdown 笔记做成小红书图文卡片方案。
```

```text
使用 wechat-publisher，把这份技术文章整理成微信公众号发布包。
```

## 新增 Skill 规范

新增 skill 时，建议遵循以下结构：

```text
skill-name/
└── SKILL.md
```

如果需要额外材料，可以放在 skill 目录内部：

```text
skill-name/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   └── example-reference.md
├── scripts/
│   └── helper-script.py
└── assets/
    └── template.png
```

`SKILL.md` 建议包含：

- `name`：skill 的唯一名称。
- `description`：触发场景和能力说明。
- `Purpose` / `Overview`：这个 skill 解决什么问题。
- `Workflow`：执行步骤。
- `Output` / `Output Contract`：默认输出格式。
- `Quality Checklist` / `Quality Bar`：完成前的质量检查。
- `Resources`：依赖的参考文件、脚本或模板。

## 维护方式

常用维护流程：

```bash
git status
git add .
git commit -m "Update personal skills"
git push
```

维护建议：

- 更新 README 时，同步检查目录结构和 skills 列表是否准确。
- 更新 skill 时，优先保持目录独立，避免多个 skill 共享隐式依赖。
- 需要模板、参考标准或辅助脚本时，放在对应 skill 的子目录中。
- 新增输出文件规则时，明确是否允许覆盖已有文件。
- 修改触发描述后，检查是否足够具体，避免和其他 skill 互相误触发。

## 仓库地址

```text
git@github.com:soonfy/skills.git
```
