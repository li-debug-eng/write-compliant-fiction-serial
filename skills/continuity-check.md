# Continuity Check

## Purpose

Audit consistency across protagonist state, characters, relationships, timeline, locations, world rules, resources, knowledge boundaries, planted hooks, and promised payoffs.

## Use When

- The user requests 连贯性检查, 设定检查, 时间线检查, 伏笔检查, or contradiction repair.
- Continuation or planning depends on existing serial canon.
- A rewrite may alter facts.

## Required Context

- `novel_id` and the canon bundle from `memory-manager`.
- Existing project memory and continuity record when available.
- Latest chapter tail and the relevant earlier chapters or outline fragments.
- Proposed draft, rewrite, or plan when checking future text.

## Optional Context

- User-requested retcons.
- Narrow retrieval through `search_novel_memory(novel_id, query, limit)` for a specific uncertainty.
- [../references/continuity-template.md](../references/continuity-template.md) when repairing a record.

## Procedure

1. Read [../references/continuity-rules.md](../references/continuity-rules.md).
2. Build the smallest canon snapshot needed for the current task.
3. Compare proposed or existing text against fixed canon and recent state changes.
4. Check who knows each fact and when they learned it.
5. Check location, timeline, resources, items, injuries, relationships, and power progression.
6. Track each hook as `open`, `advanced`, `paid_off`, or `retconned`.
7. Distinguish contradiction from unresolved mystery.
8. Recommend the smallest coherent fix. Do not rewrite unrelated material.
9. When a problem repeats or the user asks to remember it, create an `issue_update` for this novel's `issue-log.md`.

## Output Contract

Return:

```text
canon_snapshot:
findings:
severity:
smallest_fixes:
active_hooks:
knowledge_boundaries:
retcon_required:
record_patch:
issue_updates:
```

## Handoff To Other Components

- Send the canon snapshot, active hooks, and knowledge boundaries to `continue-chapter` or `outline-planning`.
- Send accepted fixes, record patches, and repeated issue updates to `memory-update`.
- Return fact-sensitive prose to `revise-style` only when wording repairs are needed.
- Ask `memory-manager` for the canon bundle before checking an established novel.

## Do Not Do

- Do not draft a new chapter inside this component.
- Do not silently retcon canon.
- Do not treat an intentionally unresolved mystery as a contradiction.
- Do not search or write memory outside the resolved `novel_id`.
