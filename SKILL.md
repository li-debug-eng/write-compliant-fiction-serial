---
name: write-compliant-fiction-serial
description: "Route and orchestrate modular workflows for original simplified-Chinese serial fiction: continuation, mature-style revision, publication-risk review, continuity checking, per-novel project-memory management, task-end memory updates, and outline planning. Preserve readable, publishable prose; isolate each novel's canon and preferences; reduce AI-like explanation; recover from compacted context; and refuse review-evasion or close imitation. Use for 小说正文, 续写, 接章, 润色, 去AI味, 文风成熟化, 合规审查, 风险改写, 拒稿修改, 连贯性检查, 设定检查, 时间线检查, 伏笔检查, 创作记忆, 单部小说记忆, 上下文恢复, 章节大纲, 分卷大纲, 节奏规划, or long-form original web-fiction maintenance."
---

# Modular Fiction Serial Router

Write original, readable, publishable simplified-Chinese serial fiction. Act as an orchestrator: identify the novel project, identify the task, load only the needed expert components and references, pass compact handoffs, and verify the requested artifact.

## Isolate Every Novel Project

Treat memory as project-level data, never as global model memory. Resolve one `novel_id` before reading or writing durable memory:

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

Use [skills/memory-manager.md](skills/memory-manager.md) to identify the current novel and load the correct project files. If the novel cannot be inferred safely, ask the user to choose or create a project. Never mix characters, canon, issue logs, optimization strategies, or preferences between novels.

## Route The Request

| User intent | Primary component | Add only when needed |
| --- | --- | --- |
| Continue a serial, write the next chapter, or draft a scene | [skills/continue-chapter.md](skills/continue-chapter.md) | For an existing serial, ask `memory-manager` for the continuation bundle and run continuity checking first. Run style revision after drafting. Run compliance review only when risk is present. Build a memory patch after accepted or workspace-written changes. |
| Polish prose, compress expression, mature the voice, or remove AI-like writing | [skills/revise-style.md](skills/revise-style.md) | Ask `memory-manager` for preferences, issue log, and optimization log. Check continuity only when facts may shift. Build a memory patch only for durable learning or canon changes. |
| Review risk, rewrite rejected material, or preflight publication | [skills/compliance-review.md](skills/compliance-review.md) | Ask `memory-manager` for the review bundle. Revise style after a safe rewrite. Check continuity and build a memory patch when plot, relationship, or setting facts change. |
| Check characters, timeline, setting, locations, hooks, or knowledge boundaries | [skills/continuity-check.md](skills/continuity-check.md) | Ask `memory-manager` for the canon bundle. Build a memory patch for accepted retcons, record repairs, or repeated issues. |
| Consolidate task-end canon, preferences, issues, or optimization learning | [skills/memory-update.md](skills/memory-update.md) | Pass the final patch to `memory-manager` for correct-project persistence or copyable fallback output. |
| Identify a novel project, recover context, manage project files, or persist a patch | [skills/memory-manager.md](skills/memory-manager.md) | Use as a support component before or after other work. |
| Plan chapters, arcs, pacing, conflicts, hooks, or payoffs | [skills/outline-planning.md](skills/outline-planning.md) | Ask `memory-manager` for the planning bundle. For an existing serial, check continuity first. Build a memory patch for accepted long-range decisions. |

Use one component when one component is enough. Do not run every component by default.

## Recover Context

For an existing serial:

1. Use `memory-manager` to resolve `novel_id` and `novel_name`.
2. Ask `memory-manager` for the task-specific memory bundle.
3. Read the latest chapter tail when continuation requires it.
4. Retrieve older canon only when the selected component needs it.
5. Treat existing prose, approved setting files, and recorded durable preferences as canon unless the user requests a retcon.
6. If necessary context cannot be retrieved, ask a concise question. Do not invent established facts.

When no MCP tool layer is available, inspect workspace files only when local file access is actually available. Otherwise return a copyable memory patch. Use [references/novel-project-template.md](references/novel-project-template.md), [references/project-memory-template.md](references/project-memory-template.md), and [references/continuity-template.md](references/continuity-template.md) when creating or repairing records.

## Use Optional MCP Tools

If a fiction-serial MCP server exposes compatible tools, use it as a retrieval and append-only persistence layer:

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

Optional prose-support tools may also be used when exposed:

```text
get_latest_chapter_tail(novel_id, chars)
count_chinese_chars(text)
```

Use MCP calls conservatively:

1. Resolve `novel_id` before retrieving or persisting project data.
2. Use `search_novel_memory(novel_id, query, limit)` only for a specific uncertainty. Keep the query narrow.
3. Use `append_memory_patch(novel_id, patch, reason)` only after canon, character state, timeline, hooks, long-range direction, repeated issues, verified optimizations, or durable project preferences actually change.
4. Use `count_chinese_chars(text)` when the user sets chapter-length bounds. If unavailable, use a deterministic local count.
5. Never use MCP as a prose generator.
6. Never delete, overwrite, publish, or commit through an MCP tool unless the user explicitly requests that operation and the tool contract supports it.

If MCP is unavailable, output a copyable `## Memory Patch`. Do not claim that memory was persisted unless an actual local file operation succeeds.

## Pass Explicit Handoffs

Pass only fields needed downstream:

```text
task:
novel_id:
novel_name:
memory_bundle:
canon_snapshot:
user_constraints:
source_text_or_latest_hook:
planned_beats:
draft:
continuity_findings:
risk_findings:
changed_facts:
durable_preferences:
issue_updates:
optimization_updates:
memory_patch:
next_handoff:
```

Common handoffs:

- `memory-manager -> continuity-check | continue-chapter | revise-style | compliance-review | outline-planning`: `novel_id` and the smallest task-specific memory bundle.
- `continuity-check -> continue-chapter`: canon snapshot, contradictions to avoid, active hooks, and knowledge boundaries.
- `outline-planning -> continue-chapter`: selected beats, pacing intent, payoff timing, and closing pressure.
- `continue-chapter -> revise-style`: draft, immutable facts, requested tone, and length target.
- `compliance-review -> revise-style`: safe rewrite, preserved plot function, and remaining author decisions.
- `continue-chapter | revise-style | compliance-review | continuity-check | outline-planning -> memory-update`: durable changes, issue updates, optimization updates, recent summary, and next handoff.
- `memory-update -> memory-manager`: structured memory patch, target `novel_id`, and persistence reason.

## Orchestrate Common Workflows

### 1. Continue Existing Chapters

`memory-manager/select+read continuation bundle -> continuity-check -> continue-chapter -> revise-style -> compliance-review only when needed -> memory-update/build patch -> memory-manager/persist or copyable fallback`

### 2. Polish Existing Prose

`memory-manager/select+read revision bundle -> revise-style -> continuity-check only when facts may shift -> memory-update only when durable learning or canon changes -> memory-manager/persist or copyable fallback`

### 3. Rewrite Rejected Material

`memory-manager/select+read review bundle -> compliance-review -> revise-style -> continuity-check when facts change -> memory-update when future writing must reflect the rewrite -> memory-manager/persist or copyable fallback`

### 4. Audit Continuity

`memory-manager/select+read canon bundle -> continuity-check -> memory-update after accepted fixes or repeated issues -> memory-manager/persist or copyable fallback`

### 5. Plan An Arc

`memory-manager/select+read planning bundle -> continuity-check -> outline-planning -> memory-update for accepted long-range decisions -> memory-manager/persist or copyable fallback`

## Shared References

Load only the references required by selected components:

- [references/mature-fiction-style.md](references/mature-fiction-style.md): shared mature-fiction prose rules.
- [references/risk-review.md](references/risk-review.md): shared publication-risk taxonomy and rewrite boundaries.
- [references/continuity-rules.md](references/continuity-rules.md): shared canon, timeline, relationship, hook, and knowledge-boundary rules.
- [references/continuity-template.md](references/continuity-template.md): continuity-record structure.
- [references/project-memory-template.md](references/project-memory-template.md): compact project-recovery structure.
- [references/novel-project-template.md](references/novel-project-template.md): isolated per-novel directory and file templates.

## Global Boundaries

- Write original fiction. Do not closely imitate a living author's distinctive style or reproduce protected material.
- Improve publishability without helping evade review, conceal prohibited meaning, or preserve a risky core through word substitution.
- Keep intimate material restrained and adult-only. Keep violence non-graphic.
- Prefer concrete prose, subtext, and lived-in detail over generic explanation and moralizing conclusions.
- Keep every novel's memory isolated under its own `novel_id`.
- Verify output contracts such as encoding, filename pattern, chapter count, and requested min/max length after writing files.
