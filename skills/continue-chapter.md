# Continue Chapter

## Responsibility

Draft new simplified-Chinese serial-fiction prose: the next chapter, a requested chapter range, or a standalone scene. Do not perform a full continuity audit, publication-risk review, or memory rewrite inside this component.

## Required Inputs

- User request: chapter count, target length, format, tone, and delivery location when specified.
- `canon_snapshot`: protagonist state, current location, active relationships, ability limits, relevant world rules, latest hook, and active unresolved threads.
- `user_constraints`: durable project rules and request-local instructions.
- Optional `planned_beats` from outline planning.

If the serial context is insufficient, return a short missing-context list. Do not invent established facts.

## Drafting Method

Before drafting each scene, establish internally:

1. surface conflict;
2. each participating character's immediate desire;
3. concealed thought or subtext;
4. concrete action, object, or environmental detail carrying the shift;
5. closing emotional change and narrative pressure.

Show these five notes only when the user explicitly requests planning before prose.

Write the chapter:

1. Enter a concrete scene quickly.
2. Give the protagonist an immediate goal.
3. Add an obstacle, information gap, choice, or escalation.
4. Make the protagonist act rather than only receive events.
5. Change the story state: resource, relationship, knowledge, risk, location, or next pressure.
6. End on an action, reveal, incomplete reply, decision, reversal, or new pressure.
7. Use [../references/mature-fiction-style.md](../references/mature-fiction-style.md).

For multi-chapter requests, give each chapter its own immediate goal and state change. Avoid stretching one scene across chapters merely to meet length.

## Output Contract

Return:

```text
draft:
chapter_titles:
changed_facts:
new_hooks:
advanced_hooks:
next_handoff:
workspace_files_written:
verification_needed:
```

Pass `draft` and immutable facts to style revision. Pass changed facts, recent summaries, and the next handoff to memory update after the prose is accepted or written to workspace.
