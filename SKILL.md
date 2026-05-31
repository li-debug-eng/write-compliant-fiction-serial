---
name: write-compliant-fiction-serial
description: "Route and orchestrate modular workflows for simplified-Chinese serial fiction: continuation, mature-style revision, publication-risk review, continuity checking, project-memory maintenance, and outline planning. Preserve original, readable, publishable prose; reduce AI-like explanation; learn project-level preferences; recover from compacted context; and refuse review-evasion or close imitation. Use for 小说正文, 续写, 接章, 润色, 去AI味, 文风成熟化, 合规审查, 风险改写, 拒稿修改, 连贯性检查, 设定检查, 时间线检查, 伏笔检查, 创作记忆, 上下文恢复, 章节大纲, 分卷大纲, 节奏规划, or long-form original web-fiction maintenance."
---

# Modular Fiction Serial Router

Write original, readable, publishable simplified-Chinese serial fiction. Act as a router: select only the components required by the request, pass explicit handoffs between them, and avoid loading unrelated instructions.

## Route The Request

| User intent | Required component | Add components only when needed |
| --- | --- | --- |
| Continue, write the next chapter, or draft a scene | [skills/continue-chapter.md](skills/continue-chapter.md) | Add continuity checking before drafting for an existing serial; add style revision after drafting; add memory update after accepted workspace changes; add compliance review only when content raises risk |
| Polish, compress, mature the prose, or remove AI-like writing | [skills/revise-style.md](skills/revise-style.md) | Add continuity checking when edits may alter facts; add memory update when a durable preference or canon fact changes |
| Review risk, rewrite rejected material, or preflight publication | [skills/compliance-review.md](skills/compliance-review.md) | Add style revision after safe rewriting; add continuity checking when plot or relationship facts change |
| Check characters, timeline, world rules, locations, hooks, or knowledge boundaries | [skills/continuity-check.md](skills/continuity-check.md) | Add memory update after an accepted retcon or record repair |
| Update summaries, recover context, or persist user preferences | [skills/memory-update.md](skills/memory-update.md) | Use as a supporting component after drafting, revision, outlining, or retcon |
| Plan chapters, arcs, pacing, conflict, or payoff placement | [skills/outline-planning.md](skills/outline-planning.md) | Add continuity checking before planning an existing serial; add memory update after the plan is accepted or stored |

If one component fully solves the request, use one. Do not chain every component by default.

## Recover Context Before Routing

For an existing serial:

1. Search the workspace for outlines, chapter files, `创作档案/创作记忆.txt`, and `创作档案/连贯性记录.txt`.
2. Read `创作记忆.txt` first when it exists.
3. Read `连贯性记录.txt`, the latest chapter tail, and only the earlier material required by the selected components.
4. Treat existing prose, approved setting files, and recorded durable preferences as canon unless the user requests a retcon.
5. If required context is missing, retrieve it from workspace files or ask a concise question. Do not invent established facts.

## Use Explicit Handoffs

Pass a compact handoff object between components. Include only fields needed downstream:

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

Common handoffs:

- `continuity-check -> continue-chapter`: canon snapshot, contradictions to avoid, active hooks, character knowledge boundaries.
- `outline-planning -> continue-chapter`: selected beats, escalation, payoff timing, closing pressure.
- `continue-chapter -> revise-style`: draft, facts that must remain unchanged, requested tone and length.
- `compliance-review -> revise-style`: safe rewritten text, plot function to preserve, remaining author decisions.
- `continue-chapter | revise-style | outline-planning | continuity-check -> memory-update`: changed facts, durable preferences, recent summary, next handoff.

## Orchestrate Common Workflows

Use these as defaults, then omit unnecessary stages:

### Continue A Serial

`memory-update/read recovery -> continuity-check -> continue-chapter -> revise-style -> compliance-review when needed -> memory-update/write recovery`

### Polish Existing Prose

`revise-style -> continuity-check when facts may shift -> memory-update when a durable rule changes`

### Rewrite Rejected Material

`compliance-review -> revise-style -> continuity-check when the rewrite changes facts -> memory-update when future writing changes`

### Audit Continuity

`continuity-check -> memory-update after accepted fixes`

### Plan An Arc

`memory-update/read recovery -> continuity-check -> outline-planning -> memory-update/write recovery`

## Shared References

Load only the references required by selected components:

- [references/mature-fiction-style.md](references/mature-fiction-style.md): shared prose standards.
- [references/risk-review.md](references/risk-review.md): shared publication-risk taxonomy and safety boundaries.
- [references/continuity-rules.md](references/continuity-rules.md): shared canon, timeline, hook, and knowledge-boundary rules.

## Global Boundaries

- Write original fiction. Do not closely imitate a living author's distinctive style or reproduce protected material.
- Improve publishability without helping evade review, conceal prohibited meaning, or preserve a risky core through word substitution.
- Keep intimate material restrained and adult-only. Keep violence non-graphic.
- Prefer concrete prose, subtext, and lived-in detail over generic explanation and moralizing conclusions.
- Verify workspace output contracts such as encoding, filename pattern, chapter count, and requested min/max length after writing files.
