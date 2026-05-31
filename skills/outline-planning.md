# Outline Planning

## Purpose

Plan chapters, arcs, pacing, conflict escalation, choices, consequences, hooks, and payoff timing without drafting full prose.

## Use When

- The user requests 章节大纲, 分卷大纲, 节奏规划, hook planning, payoff planning, or pacing repair.
- A new serial needs an original premise and opening direction.

## Required Context

- `novel_id` and the planning bundle from `memory-manager` for an existing novel.
- User goal: scope, genre, tone, chapter range, relationship emphasis, and desired pacing.
- For an existing serial: `canon_snapshot`, active hooks, knowledge boundaries, world limits, and current stage.

## Optional Context

- Recovery payload from `memory-update`.
- Targeted canon search results from `continuity-check`.
- User priorities for specific conflicts, relationships, or payoffs.

## Procedure

1. For a new novel, establish an original protagonist, supporting cast, world rules, core conflict, relationship line, volume direction, and opening beats.
2. For an existing serial, preserve fixed canon and retrieve unresolved questions before planning.
3. Define the stage goal and the protagonist's concrete short-term need.
4. Break the range into beats with goal, pressure, action, consequence, and closing hook.
5. Alternate pressure with functional breathing room. Let daily life reveal cost, relationship, resources, or future pressure.
6. Advance planted hooks gradually. Do not pay off every mystery immediately.
7. Respect power progression and knowledge boundaries.
8. Mark new hooks, payoff windows, and answers that should remain deferred.

## Output Contract

Return:

```text
scope:
stage_goal:
chapter_beats:
new_hooks:
advanced_hooks:
payoff_windows:
deferred_answers:
canon_questions:
durable_changes_for_memory_update:
  Long-range outline, hook, volume, arc, pacing, stage, or payoff decisions
  that may need durable project memory updates if accepted by the user.
  These are not final memory patches.
optimization_updates:
```

## Handoff To Other Components

- Send selected beats, pacing intent, payoff timing, and closing pressure to `continue-chapter`.
- Send `durable_changes_for_memory_update` to `memory-update` when the user
  accepts long-range direction, new hooks, payoff windows, deferred answers,
  volume structure, stage summaries, pacing rules, or durable outline decisions.
- Ask `continuity-check` to resolve canon questions before planning around them.
- Ask `memory-manager` for the planning bundle before planning an established novel.

## Do Not Do

- Do not draft full chapters inside this component.
- Do not generate the final `memory_patch`; send durable candidates to `memory-update`.
- Do not silently change established canon.
- Do not make every chapter a climax or resolve every hook immediately.
- Do not reuse another novel's pacing strategy unless the user explicitly requests it.
