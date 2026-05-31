# Memory Update

## Responsibility

Read, create, and update project recovery files. Persist durable preferences, recent summaries, changed canon, and the next writing handoff. Do not write chapter prose or perform a full continuity audit.

## Required Inputs

- Existing `创作档案/创作记忆.txt` and `创作档案/连贯性记录.txt` when available.
- `changed_facts`, accepted retcons, recent chapter summaries, active hooks, next handoff, and output verification.
- User feedback that may become a durable, local, or pending preference.

## Read Recovery

When conversation context is incomplete:

1. Read `创作记忆.txt` first.
2. Read `连贯性记录.txt`.
3. Return a compact recovery payload for downstream components.

## Learn From Feedback

For each user correction or preference:

1. Apply the requested fix to the current artifact through the relevant component.
2. Infer the smallest reusable rule preventing recurrence.
3. Classify it:
   - `durable`: future work in this project;
   - `local`: named chapter, scene, character, or request only;
   - `pending`: scope unclear, record without broad enforcement.
4. Prefer the newest explicit instruction when rules conflict.
5. Mark older conflicting rules as `replaced`; do not silently delete them.
6. Keep learning project-level. Modify the router or components only when the user explicitly requests a skill update.

## Write Recovery Files

Maintain:

```text
创作档案/
├── 创作记忆.txt
└── 连贯性记录.txt
```

Keep `创作记忆.txt` compact:

```text
书名与更新时间
最新正文
快速恢复摘要
输出契约
用户偏好与自动优化
不可破坏规则
当前阶段摘要
最近章节摘要
待回收线索
下一次续写交接
```

Keep `连贯性记录.txt` detailed:

```text
更新时间
主角档案
能力规则
主要人物
已发生事件
未解线索
硬设定
文风执行规则
下一章衔接
```

Summarize older chapters by arc. Keep only recent chapters in detail. Do not copy full prose into recovery files.

## Output Contract

Return:

```text
recovery_payload:
memory_patch:
continuity_record_patch:
durable_preferences:
replaced_preferences:
next_handoff:
files_updated:
```
