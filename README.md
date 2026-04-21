# Personal Skills

这是一个个人维护的 skills 仓库，用来保存、同步和复用在 Codex / Agents 工作流中常用的自定义 skill。

每个 skill 都是一个独立目录，目录中至少包含一个 `SKILL.md` 文件。`SKILL.md` 描述触发场景、使用目标、工作流程、输出要求和质量检查规则；如果某个 skill 需要更详细的模板、参考标准或 agent 配置，也会放在该 skill 自己的子目录中，避免和其他 skill 产生隐式依赖。

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
└── xiaohongshu-markdown-cards/
    └── SKILL.md
```

## Skills 列表

| Skill 名称 | 用途 | 目录 |
| --- | --- | --- |
| `ai-daily-interviews` | 生成系统化的 AI / 程序员面试学习笔记和深度问答，并保存为适合 Obsidian 的 Markdown 文件。 | `ai-daily-interviews/` |
| `xiaohongshu-markdown-cards` | 将 Markdown、笔记、文章、课程内容、技术说明或知识文档转成小红书风格的图文卡片方案、发布文案，必要时生成竖版 PNG 卡片。 | `xiaohongshu-markdown-cards/` |

## Skill 说明

### `ai-daily-interviews`

这个 skill 面向“每日技术面试学习”工作流，适合把一个后端、AI 应用、系统设计或工程基础知识点整理成可复习、可沉淀、可面试表达的 Markdown 笔记。

主要能力：

- 默认用中文输出，面向中高级后端或平台工程师的面试准备场景。
- 生成 Obsidian 友好的 Markdown 文件，包含 YAML frontmatter、知识图谱、系统讲解、源码/实现视角、生产场景、优化方向、深度面试 Q&A、延伸阅读和复习清单。
- 默认文件名使用 `interview-<topic>.md`，如果同名文件已存在，会追加数字后缀，避免覆盖旧笔记。
- 覆盖 Python、Java / JVM、Node.js、Agent / LLM 应用、MySQL、Redis、网络、操作系统、并发、消息队列、缓存和存储等常见面试主题。
- 通过 `references/answer-standard.md` 固化输出模板和深度标准，保证生成内容不仅是定义罗列，而是包含机制、边界、故障和工程权衡。

适合场景：

- 每天生成一个技术知识点的面试复习笔记。
- 准备 Python、Java、Node.js、MySQL、Redis、系统设计或 Agent 应用相关面试。
- 把零散知识点整理成可以长期沉淀到 Obsidian 的学习材料。
- 训练“直接结论 + 机制拆解 + 生产案例 + 面试追问”的答题结构。

示例请求：

```text
使用 ai-daily-interviews，讲清楚 Redis 缓存穿透、击穿和雪崩，并生成面试问答。
```

```text
帮我生成一篇 Node.js event loop 的中高级面试学习笔记。
```

### `xiaohongshu-markdown-cards`

这个 skill 面向“小红书图文卡片”工作流，适合把结构化或半结构化知识内容压缩成更适合手机阅读和发布的视觉化卡片。

主要能力：

- 将 Markdown、学习笔记、文章、课程转录稿、技术解释等内容拆解成 5-9 张小红书卡片。
- 默认使用中文输出。
- 默认竖版尺寸为 `1242x1660`，也可以按需使用 `1080x1440`。
- 产出卡片脚本、视觉方向、发布标题、正文、话题标签和首评/置顶评论。
- 在需要生成实际图片时，要求保持统一网格、字体层级、色彩系统和移动端可读性。

适合场景：

- 技术文章转小红书知识卡片。
- 读书笔记、课程笔记、学习总结可视化。
- 面试知识点整理。
- AI 应用开发、产品策略、工程实践等专业内容的图文发布。

示例请求：

```text
使用 xiaohongshu-markdown-cards，把下面的 Markdown 笔记做成小红书图文卡片方案。
```

```text
根据这份技术文章，生成小红书发布文案和 7 张卡片脚本。
```

## 安装方式

### 方式一：克隆整个仓库

```bash
git clone git@github.com:soonfy/skills.git
cd skills
```

克隆后可以按需复制某个 skill 目录到本机的个人 skills 目录。

### 方式二：安装到 Codex 个人 skills 目录

macOS / Linux 示例：

```bash
mkdir -p ~/.codex/skills
cp -R ./ai-daily-interviews ~/.codex/skills/
cp -R ./xiaohongshu-markdown-cards ~/.codex/skills/
```

Windows PowerShell 示例：

```powershell
New-Item -ItemType Directory -Force $env:USERPROFILE\.codex\skills
Copy-Item -Recurse .\ai-daily-interviews $env:USERPROFILE\.codex\skills\
Copy-Item -Recurse .\xiaohongshu-markdown-cards $env:USERPROFILE\.codex\skills\
```

### 方式三：安装到 Agents 个人 skills 目录

macOS / Linux 示例：

```bash
mkdir -p ~/.agents/skills
cp -R ./ai-daily-interviews ~/.agents/skills/
cp -R ./xiaohongshu-markdown-cards ~/.agents/skills/
```

Windows PowerShell 示例：

```powershell
New-Item -ItemType Directory -Force $env:USERPROFILE\.agents\skills
Copy-Item -Recurse .\ai-daily-interviews $env:USERPROFILE\.agents\skills\
Copy-Item -Recurse .\xiaohongshu-markdown-cards $env:USERPROFILE\.agents\skills\
```

## 使用方式

安装完成后，在支持 skills 的环境中直接提出与触发场景匹配的请求即可。也可以显式点名 skill，减少歧义。

```text
使用 ai-daily-interviews，生成一篇 MySQL MVCC 的深度面试笔记。
```

```text
把这篇 Markdown 笔记做成一组小红书图文卡片方案。
```

```text
使用 xiaohongshu-markdown-cards，把这段课程转录稿整理成可发布的小红书卡片和文案。
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
