# write-compliant-fiction-serial

一个用于简体中文连载小说创作、续写、修订与连贯性维护的 Codex Skill。

它面向长期创作，而不是只生成一次性正文。技能会根据用户反馈沉淀项目级规则，维护可恢复的剧情摘要，并在写作后自动清理常见的 AI 腔表达。

## 功能

- 创建原创小说设定、人物档案、世界观、分卷大纲和章节大纲。
- 续写或修订已有连载，保留人物状态、时间线、伏笔和能力边界。
- 根据用户反馈持续优化当前项目，例如章节长度、文件格式、节奏和文风。
- 使用克制、自然、有潜台词的叙事方式，减少直白情绪解释和模板化结尾。
- 在上下文不足或对话被压缩时，从项目记忆和连贯性记录恢复写作状态。
- 对高风险内容进行预检，并提供真正降低风险的改写方案。

## 核心写作原则

技能默认采用“成熟小说作者”式工作流：

1. 写作前先确认场景冲突、人物欲望、潜台词、承载情绪的物件或动作，以及结尾变化。
2. 用动作、停顿、环境和对话错位表现情绪，避免反复解释人物感受。
3. 让人物保留没有说出口的部分，不把真实想法一次讲满。
4. 每段推动信息、压力、关系、选择或节奏。
5. 写完后静默删除空泛修辞、重复解释、模板化转折和总结主题的句子。

详细规则见：

- [`references/mature-fiction-style.md`](references/mature-fiction-style.md)
- [`references/risk-review.md`](references/risk-review.md)

## 安装

将仓库克隆到 Codex 的技能目录：

```powershell
git clone https://github.com/li-debug-eng/write-compliant-fiction-serial.git `
  "$HOME\.codex\skills\write-compliant-fiction-serial"
```

如果目录已经存在，可以在技能目录中更新：

```powershell
git pull
```

安装或更新后，建议新建 Codex 对话或重启当前客户端，使技能列表重新加载。

## 使用方式

显式调用技能：

```text
$write-compliant-fiction-serial 帮我创建一部东方玄幻升级小说。
```

继续已有小说：

```text
$write-compliant-fiction-serial 按照已有设定继续写后续 10 章，每章 2000-5000 字。
```

请求单独场景，并先查看场景设计：

```text
$write-compliant-fiction-serial
场景：两名旧友在雨夜重逢，其中一人隐瞒了离开的真正原因。
人物关系：曾经并肩做事，如今彼此提防。
情绪基调：克制、压抑。
字数：1200 字。

先用 5 条说明冲突、欲望、潜台词和结尾变化，再写正文。
```

修订文风：

```text
$write-compliant-fiction-serial 润色这一章。减少直白情绪解释，让对话更有潜台词，删掉像 AI 写作的句子。
```

检查连贯性：

```text
$write-compliant-fiction-serial 检查当前小说的人物状态、时间线和未回收伏笔。
```

## 项目记忆

对于持续连载，技能会在小说项目中维护两份文件：

```text
创作档案/
├── 创作记忆.txt
└── 连贯性记录.txt
```

`创作记忆.txt` 用于快速恢复：

- 当前剧情摘要；
- 输出格式与章节长度；
- 用户已经确认的长期偏好；
- 最近章节变化；
- 下一次续写停点。

`连贯性记录.txt` 用于保存更完整的设定：

- 主角和配角状态；
- 事件顺序；
- 世界观硬规则；
- 未解线索；
- 伏笔与回收计划。

当对话上下文不足时，技能会优先读取这两份文件和最新章节，再继续创作。

对应模板：

- [`references/project-memory-template.md`](references/project-memory-template.md)
- [`references/continuity-template.md`](references/continuity-template.md)

## 根据反馈自动优化

用户提出修改意见后，技能会将反馈分类：

- `durable`：当前作品长期适用，例如每章长度、文件格式和整体节奏。
- `local`：只适用于指定章节、场景或人物。
- `pending`：范围不明确，记录但不自动扩大影响。

新规则会写入当前作品的 `创作记忆.txt`。技能不会因为一次局部意见而擅自修改所有项目，也不会自动重写自身文件。只有用户明确要求更新 Skill 时，才应修改仓库中的技能规范。

## 目录结构

```text
write-compliant-fiction-serial/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── continuity-template.md
    ├── mature-fiction-style.md
    ├── project-memory-template.md
    └── risk-review.md
```

## 适用范围

适合：

- 原创网文、长篇小说和系列故事；
- 东方玄幻、都市成长、悬疑调查、现实题材等连续叙事；
- 章节续写、剧情整理、伏笔检查、文风润色和风险预检。

不用于：

- 规避平台审核；
- 仿写受保护作品或复刻特定作者文风；
- 生成露骨色情内容；
- 仅替换敏感词而保留原有高风险核心。

## License

当前仓库尚未添加开源许可证。公开可见不等于自动授予复制、修改或再分发许可。需要开放复用时，请根据预期用途补充合适的 `LICENSE` 文件。
