# write-compliant-fiction-serial

一个用于简体中文连载小说创作、续写、润色、审查与长期维护的模块化 Codex Skill。

它采用“主 Skill 路由 + 专家组件 + 共享 references + 单部小说独立记忆”的结构。主路由只加载当前任务需要的组件，不会无条件串联全部流程。

## 目录结构

```text
write-compliant-fiction-serial/
├─ SKILL.md
├─ README.md
├─ agents/
│  └─ openai.yaml
├─ skills/
│  ├─ continue-chapter.md
│  ├─ revise-style.md
│  ├─ compliance-review.md
│  ├─ continuity-check.md
│  ├─ memory-update.md
│  ├─ memory-manager.md
│  └─ outline-planning.md
└─ references/
   ├─ mature-fiction-style.md
   ├─ risk-review.md
   ├─ continuity-rules.md
   ├─ continuity-template.md
   ├─ project-memory-template.md
   └─ novel-project-template.md
```

## 组件职责

| 组件 | 职责 |
| --- | --- |
| `continue-chapter` | 续写、接章、场景正文 |
| `revise-style` | 润色、表达压缩、去 AI 味、成熟文风 |
| `compliance-review` | 风险识别、拒稿改写、发布前预检 |
| `continuity-check` | 人物、关系、时间线、地点、设定、伏笔和知识边界检查 |
| `memory-update` | 一次具体任务结束后，汇总应写入长期记忆的结构化补丁 |
| `memory-manager` | 识别单部小说、读取任务所需记忆、隔离项目并持久化补丁 |
| `outline-planning` | 章节规划、节奏、冲突、伏笔与回收安排 |

每个组件使用同一套契约：

```text
# Component Name
## Purpose
## Use When
## Required Context
## Optional Context
## Procedure
## Output Contract
## Handoff To Other Components
## Do Not Do
```

## 单部小说独立记忆

每部小说使用独立 `novel-id`：

```text
projects/
└─ {novel-id}/
   ├─ project-memory.md
   ├─ continuity-record.md
   ├─ character-state.md
   ├─ chapter-index.md
   ├─ issue-log.md
   ├─ optimization-log.md
   └─ user-preferences.md
```

`memory-manager` 会先识别当前小说，再按任务读取最小必要文件。不同小说不会共用设定、人物、偏好、问题日志或优化策略。

`memory-update` 只负责生成补丁。它不会自行猜测小说项目，也不会假装文件已经写入。

## 可选 MCP 工具层

当未来接入 `fiction-serial-mcp` 时，`memory-manager` 可以使用：

```text
get_novel_projects()
get_current_novel_project()
create_novel_project(novel_name)
get_project_memory(novel_id)
get_continuity_record(novel_id)
get_issue_log(novel_id)
get_optimization_log(novel_id)
append_memory_patch(novel_id, patch, reason)
search_novel_memory(novel_id, query, limit)
```

MCP 只负责检索与追加式记录，不负责生成正文。没有 MCP 且没有实际本地写入时，Skill 会输出可复制的 `## Memory Patch`。

## Memory Patch

```md
## Memory Patch

Novel ID:
Novel Name:

### Project Memory Updates
- ...

### Continuity Updates
- ...

### Character State Updates
- ...

### Chapter Index Updates
- ...

### User Preference Updates
- ...

### Issue Log Updates
- ...

### Optimization Log Updates
- ...

### Next-Time Instructions
- ...
```

普通语句润色不默认写入长期记忆。只有 canon、人物状态、时间线、伏笔、长期方向、长期偏好、反复问题或已验证优化策略变化时，才生成补丁。

### 无法写入时如何复用

当 MCP 和本地文件写入都不可用时，Skill 只会输出可复制的 `## Memory Patch`，不会声称已经保存。

用户可以把补丁保存到对应小说项目文件中，或在下一次相关任务开始时贴回。再次收到补丁后，Skill 会把它作为当前会话的临时项目记忆，并按照 `novel_id` 合并。不同小说的补丁不会混用；缺少 `novel_id` 且无法判断目标小说时，会先询问用户。

## 示例工作流

### 1. 续写已有连载

```text
memory-manager/select+read continuation bundle
  -> continuity-check
  -> continue-chapter
  -> revise-style
  -> compliance-review（仅存在风险时）
  -> memory-update/build patch
  -> memory-manager/persist or copyable fallback
```

### 2. 普通润色

```text
memory-manager/select+read revision bundle
  -> revise-style
  -> continuity-check（仅事实可能变化时）
  -> memory-update（仅形成长期学习或设定变化时）
  -> memory-manager/persist or copyable fallback
```

### 3. 拒稿章节安全改写

```text
memory-manager/select+read review bundle
  -> compliance-review
  -> revise-style
  -> continuity-check（仅剧情事实、关系或设定变化时）
  -> memory-update（仅后续写作需要记录时）
  -> memory-manager/persist or copyable fallback
```

### 4. 连贯性审查

```text
memory-manager/select+read canon bundle
  -> continuity-check
  -> memory-update（接受修复或发现反复问题后）
  -> memory-manager/persist or copyable fallback
```

### 5. 后续大纲规划

```text
memory-manager/select+read planning bundle
  -> continuity-check
  -> outline-planning
  -> memory-update（长期方向变化后）
  -> memory-manager/persist or copyable fallback
```

## 成熟文风默认规则

- 用动作、停顿、物件、环境和对话错位承载情绪。
- 对话保留潜台词，不把人物真实想法一次讲满。
- 生活化细节必须推动人物、关系、压力或节奏。
- 删除重复解释、空泛修辞、模板化转折和总结式结尾。
- 不模仿在世作者的独特风格，不复刻受保护作品。

## 发布边界

本 Skill 不帮助规避平台审核，不通过换词保留高风险核心，不生成露骨色情内容，不性化未成年人，也不把血腥暴力作为卖点。

## Agent Configuration

`agents/openai.yaml` 是可选的 agent 配置入口。它用于让支持该入口的客户端展示 Skill，并提供与主路由一致的默认提示词。

该文件不承载独立的写作、合规、记忆或路由规则，也不应覆盖模块化组件。更新时应保持以下原则：

- 使用模块化路由；
- 每部小说使用独立 `novel_id`；
- 访问持久记忆前先经过 `memory-manager`；
- 使用 `memory-update` 生成最终记忆补丁；
- 不默认运行全部组件；
- MCP 仅作为可选的读取、搜索、统计与追加式持久化工具层，不用于生成正文。

## 安装

```powershell
git clone https://github.com/li-debug-eng/write-compliant-fiction-serial.git `
  "$HOME\.codex\skills\write-compliant-fiction-serial"
```

更新：

```powershell
git -C "$HOME\.codex\skills\write-compliant-fiction-serial" pull
```
