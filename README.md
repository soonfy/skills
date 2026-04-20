# Personal Skills

这是我个人维护的 skills 仓库，用来保存、同步和复用在 Codex / Agents 工作流中常用的自定义 skill。

每个 skill 都是一个独立目录，目录中至少包含一个 `SKILL.md` 文件。`SKILL.md` 负责描述 skill 的触发场景、使用目标、工作流程、输出要求和质量检查规则。

## 目录结构

```text
skills/
├── README.md
├── .gitignore
└── xiaohongshu-markdown-cards/
    └── SKILL.md
```

## Skills 列表

| Skill 名称 | 用途 | 目录 |
| --- | --- | --- |
| `xiaohongshu-markdown-cards` | 将 Markdown、笔记、文章、课程内容、技术说明或知识文档转成小红书风格的图文卡片方案、发布文案，必要时生成竖版 PNG 卡片。 | `xiaohongshu-markdown-cards/` |

## Skill 说明

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

## 安装方式

### 方式一：克隆整个仓库

```bash
git clone git@github.com:soonfy/skills.git
```

克隆后可以按需复制某个 skill 目录到本机的个人 skills 目录。

### 方式二：安装到 Codex 个人 skills 目录

Windows 示例：

```powershell
Copy-Item -Recurse .\xiaohongshu-markdown-cards $env:USERPROFILE\.codex\skills\
```

macOS / Linux 示例：

```bash
cp -R ./xiaohongshu-markdown-cards ~/.codex/skills/
```

### 方式三：安装到 Agents 个人 skills 目录

Windows 示例：

```powershell
Copy-Item -Recurse .\xiaohongshu-markdown-cards $env:USERPROFILE\.agents\skills\
```

macOS / Linux 示例：

```bash
cp -R ./xiaohongshu-markdown-cards ~/.agents/skills/
```

> 如果目标目录不存在，请先创建对应的 `skills` 目录。

## 使用方式

安装完成后，在支持 skills 的环境中直接提出与 skill 触发场景匹配的请求即可。

示例：

```text
把这篇 Markdown 笔记做成一组小红书图文卡片方案。
```

```text
根据这份技术文章，生成小红书发布文案和 7 张卡片脚本。
```

```text
把这段课程转录稿整理成小红书风格的知识卡片，并输出可直接发布的标题、正文和标签。
```

也可以显式点名 skill：

```text
使用 xiaohongshu-markdown-cards，把下面的内容做成小红书卡片。
```

## 新增 Skill 规范

新增 skill 时，建议遵循以下结构：

```text
skill-name/
└── SKILL.md
```

`SKILL.md` 建议包含：

- `name`：skill 的唯一名称。
- `description`：触发场景和能力说明。
- `Purpose`：这个 skill 解决什么问题。
- `Workflow`：执行步骤。
- `Output`：默认输出格式。
- `Quality Checklist`：完成前的质量检查。

## 维护方式

常用维护流程：

```bash
git status
git add .
git commit -m "Add or update skill: <skill-name>"
git push
```

更新 skill 时，优先保持目录独立，避免让多个 skill 共享隐式依赖。这样后续复制、安装、删除和版本管理都会更简单。

## 仓库地址

```text
git@github.com:soonfy/skills.git
```
