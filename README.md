# write-compliant-fiction-serial

一个用于简体中文连载小说创作、续写、修订、审查与长期维护的模块化 Codex Skill。

它不是把所有规则堆在一个提示词里，而是使用：

```text
主 Skill 路由
  -> 按任务选择专家组件
  -> 组件之间通过明确契约交接
  -> 按需读取共享 references
```

目标是让长篇创作更稳定：需要续写时专注续写，需要润色时专注文风，需要审查时专注风险，不无脑串联全部流程。

## 功能

- 创建原创小说设定、人物档案、章节大纲和分卷规划。
- 续写已有连载，保持人物状态、能力边界、时间线和伏笔一致。
- 将正文调整为克制、自然、有潜台词的成熟中文小说表达。
- 删除常见 AI 腔：重复解释、空泛修辞、模板转折和总结式结尾。
- 进行发布前风险预检，并提供真正降低风险的改写方案。
- 记录用户长期偏好，在上下文不足时从项目档案恢复创作状态。

## 模块化结构

```text
write-compliant-fiction-serial/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
├── skills/
│   ├── continue-chapter.md
│   ├── revise-style.md
│   ├── compliance-review.md
│   ├── continuity-check.md
│   ├── memory-update.md
│   └── outline-planning.md
└── references/
    ├── mature-fiction-style.md
    ├── risk-review.md
    └── continuity-rules.md
```

### 主路由

[`SKILL.md`](SKILL.md) 只负责：

- 判断用户意图；
- 选择一个或多个专家组件；
- 传递必要上下文；
- 按任务需要组合流程；
- 执行全局安全边界和输出验证。

### 专家组件

| 组件 | 职责 |
| --- | --- |
| [`continue-chapter.md`](skills/continue-chapter.md) | 续写、接章、场景正文 |
| [`revise-style.md`](skills/revise-style.md) | 润色、去 AI 味、表达压缩、成熟文风 |
| [`compliance-review.md`](skills/compliance-review.md) | 风险识别、拒稿改写、发布前预检 |
| [`continuity-check.md`](skills/continuity-check.md) | 人物、时间线、设定、地点、伏笔与知识边界 |
| [`memory-update.md`](skills/memory-update.md) | 创作档案、恢复摘要、用户长期偏好 |
| [`outline-planning.md`](skills/outline-planning.md) | 章节规划、节奏设计、冲突和伏笔安排 |

### 共享规则

| Reference | 用途 |
| --- | --- |
| [`mature-fiction-style.md`](references/mature-fiction-style.md) | 成熟中文小说表达规则 |
| [`risk-review.md`](references/risk-review.md) | 合规审查分类与安全边界 |
| [`continuity-rules.md`](references/continuity-rules.md) | Canon 优先级、时间线、知识边界和伏笔状态 |

## 编排原则

主路由只选择真正需要的组件：

- 单纯润色一段文本：只使用 `revise-style`。
- 检查人物矛盾：只使用 `continuity-check`。
- 续写已有连载：先恢复档案并检查关键连续性，再续写、润色，最后更新档案。
- 拒稿章节改写：先识别风险，再安全改写；只有事实改变时才追加连贯性更新。

组件之间通过紧凑 handoff 交接：

```text
task:
canon_snapshot:
user_constraints:
source_text_or_latest_hook:
planned_beats:
draft:
continuity_findings:
risk_findings:
changed_facts:
durable_preferences:
memory_patch:
```

每个组件会声明自己需要的输入和产生的输出。下游只读取有用字段。

## 示例工作流

### 1. 续写已有连载

用户请求：

```text
$write-compliant-fiction-serial 按照已有设定继续写后续 10 章，每章 2000-5000 字。
```

编排：

```text
memory-update/read recovery
  -> continuity-check
  -> continue-chapter
  -> revise-style
  -> compliance-review（仅在存在风险时）
  -> memory-update/write recovery
```

### 2. 润色并去除 AI 味

用户请求：

```text
$write-compliant-fiction-serial 润色这一章。减少直白情绪解释，让对话更有潜台词。
```

编排：

```text
revise-style
  -> continuity-check（仅在润色可能改变事实时）
  -> memory-update（仅在形成长期偏好时）
```

### 3. 被拒稿章节安全改写

用户请求：

```text
$write-compliant-fiction-serial 这章被拒稿了。说明风险原因，并改成可发布版本。
```

编排：

```text
compliance-review
  -> revise-style
  -> continuity-check（仅在剧情事实或关系变化时）
  -> memory-update（仅在后续写作需要记录时）
```

### 4. 规划后续二十章

用户请求：

```text
$write-compliant-fiction-serial 根据已有正文规划后续二十章，标出伏笔和回收点。
```

编排：

```text
memory-update/read recovery
  -> continuity-check
  -> outline-planning
  -> memory-update/write recovery
```

## 项目记忆

持续连载时，技能会在小说项目中维护：

```text
创作档案/
├── 创作记忆.txt
└── 连贯性记录.txt
```

`创作记忆.txt` 保存快速恢复信息：

- 当前剧情摘要；
- 输出格式与章节长度；
- 用户长期偏好；
- 最近章节变化；
- 下一次续写停点。

`连贯性记录.txt` 保存较详细 Canon：

- 主角与配角状态；
- 能力规则；
- 事件顺序；
- 未解线索；
- 世界观硬规则；
- 下一章衔接。

当上下文不足时，主路由先调用 `memory-update` 恢复项目状态，再选择后续组件。

## 成熟文风

正文默认遵循这些原则：

1. 用动作、停顿、物件、环境和对话错位表现情绪。
2. 对话保留潜台词，不把真实想法一次讲满。
3. 生活化细节必须推动人物、关系或压力。
4. 删除重复解释、空泛修辞和套路化总结。
5. 场景结尾落在动作、物件、未答完的话或新压力上。

## 安装

克隆到 Codex 技能目录：

```powershell
git clone https://github.com/li-debug-eng/write-compliant-fiction-serial.git `
  "$HOME\.codex\skills\write-compliant-fiction-serial"
```

更新：

```powershell
git -C "$HOME\.codex\skills\write-compliant-fiction-serial" pull
```

安装或更新后，建议新建 Codex 对话或重启客户端，使技能列表重新加载。

## 使用示例

```text
$write-compliant-fiction-serial 帮我创建一部东方玄幻升级小说。
```

```text
$write-compliant-fiction-serial 检查当前小说的人物状态、时间线和未回收伏笔。
```

```text
$write-compliant-fiction-serial
场景：两名旧友在雨夜重逢，其中一人隐瞒了离开的真正原因。
人物关系：曾经并肩做事，如今彼此提防。
情绪基调：克制、压抑。
字数：1200 字。

先用 5 条说明冲突、欲望、潜台词和结尾变化，再写正文。
```

## 边界

本 Skill 不用于：

- 规避平台审核；
- 通过换词保留高风险核心；
- 仿写受保护作品或复刻在世作者的独特风格；
- 生成露骨色情内容；
- 性化未成年人；
- 将血腥暴力作为主要卖点。

## License

当前仓库尚未添加开源许可证。公开可见不等于自动授予复制、修改或再分发许可。
