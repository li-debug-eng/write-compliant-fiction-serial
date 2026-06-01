# Continue Chapter

## Purpose

Draft new simplified-Chinese serial-fiction prose: the next chapter, a requested chapter range, or a standalone scene. Preserve existing canon and move the story state forward.

## Use When

- The user requests 正文, 续写, 接章, a new scene, or multiple new chapters.
- An outline beat must become publishable prose.

## Required Context

- `novel_id`, `novel_name`, and the continuation memory bundle from `memory-manager`.
- User constraints: chapter count, target length, tone, viewpoint, format, and delivery path when specified.
- `canon_snapshot`: protagonist state, location, relationships, ability limits, resources, active hooks, knowledge boundaries, and next pressure.
- Latest chapter tail or scene handoff.
- Relevant durable project preferences.

If the existing serial context is insufficient, return a short missing-context list. Do not invent established facts.

## Optional Context

- `planned_beats` from outline planning.
- Earlier chapters retrieved for a specific canon question.
- Latest chapter tail retrieved for the resolved `novel_id`.

## Procedure

1. Recover the compact context required for the requested range.
2. Read [../references/mature-fiction-style.md](../references/mature-fiction-style.md).
3. Before each scene, establish internally: surface conflict, each participant's immediate desire, subtext, the concrete carrier of the shift, and the closing emotional change. Show these notes only when requested.
4. Enter a concrete scene quickly. Do not open with an exposition dump.
5. Give the protagonist an immediate goal and an obstacle, information gap, choice, or escalation.
6. Make the protagonist act. Change at least one story state: resource, relationship, knowledge, risk, location, or next pressure.
7. End on an action, reveal, incomplete reply, decision, reversal, or new pressure. Do not summarize the theme.
8. For multi-chapter requests, give each chapter its own immediate goal and state change.
9. Not every breathing scene needs a major reversal. A scene may earn its place by revealing how a character eats, waits, lies, avoids, saves face, misjudges, repairs, bargains, remembers, or handles a small practical problem under pressure.
10. Do not make every protagonist action feel perfectly optimized. Allow reasonable hesitation, incomplete information, emotional avoidance, class-limited choices, fatigue, small mistakes, or face-saving behavior when they deepen character and do not break canon.
11. A low-action scene is acceptable when it changes the reader's understanding of a character, relationship, setting, threat, resource constraint, or future decision.
12. Verify requested length with `count_chinese_chars(text)` when available, otherwise use a deterministic local count.

## Output Contract

Return:

```text
draft:
chapter_titles:
changed_facts:
new_hooks:
advanced_hooks:
issue_updates:
optimization_updates:
next_handoff:
chinese_char_count:
workspace_files_written:
verification_needed:
```

## Handoff To Other Components

- Send `draft`, immutable facts, tone, and length target to `revise-style`.
- Send risky material to `compliance-review` only when needed.
- Send changed facts, recent summaries, hooks, issues, verified optimizations, and next handoff to `memory-update` after accepted or workspace-written changes.
- Pass `optimization_updates` to `memory-update` only when the drafting session proves or confirms a reusable project-specific strategy, such as a chapter ending pattern, a relationship-escalation method, or a way of introducing clues through practical sensory detail. Do not persist one-off scene beats as optimization strategies.
- Ask `continuity-check` for a targeted pass before drafting when canon is unclear.
- Ask `memory-manager` for the continuation bundle before writing an existing serial.

## Do Not Do

- Do not perform a full continuity audit, risk review, or memory rewrite inside this component.
- Do not pad chapters with repeated interpretation or atmospheric description that changes nothing.
- Do not silently retcon established facts.

## Breathing Scene Boundary

Acceptable breathing scenes include:

- a character eating while revealing poverty, habit, or guardedness;
- a character waiting and reading the room through practical experience;
- a character repairing something that exposes skill, origin, or past work;
- a character avoiding one sentence and exposing relationship pressure;
- a character making an imperfect but in-character small choice.

Unacceptable filler scenes include:

- repeating known setting information;
- purposeless idle talk;
- large blocks of abstract psychology used to delay the story;
- scenes that change no character, relationship, pressure, resource, information, or rhythm.
