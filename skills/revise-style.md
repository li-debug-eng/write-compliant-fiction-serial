# Revise Style

## Purpose

Polish existing prose without changing its intended plot function. Mature the voice, reduce AI-like habits, compress repetition, improve subtext, and preserve factual continuity.

## Use When

- The user requests 润色, 去AI味, 文风成熟化, expression compression, or a cleaner final draft.
- A newly drafted or safely rewritten chapter needs prose-level refinement.

## Required Context

- `novel_id` and the revision bundle from `memory-manager` for an existing novel.
- `source_text_or_latest_hook` or `draft`.
- Requested tone, length, viewpoint, and formatting.
- Facts, outcomes, lines, or scene functions that must remain.

## Optional Context

- User feedback describing disliked writing habits.
- `issue-log.md` and `optimization-log.md` from the resolved novel project.
- `canon_snapshot` for fact-sensitive scenes.
- `count_chinese_chars(text)` when a length bound remains active.

## Procedure

1. Read [../references/mature-fiction-style.md](../references/mature-fiction-style.md).
2. Preserve events, relationships, viewpoint, and required outcome.
3. Replace direct emotional explanation with action, pause, object use, environment, or dialogue mismatch where possible.
4. Shorten dialogue that explains too much. Allow evasion, interruption, and partial answers.
5. Delete repeated interpretation after an already-clear action or line.
6. Remove decorative detail that does not affect information, pressure, relationship, choice, or rhythm.
7. Remove generic lyrical phrasing, mechanical contrast patterns, adjective stacks, and moralizing endings.
8. Read once for repetitive sentence shapes and unnatural rhythm.
9. Recheck length when the user set a range.

## Output Contract

Return:

```text
revised_text:
preserved_facts:
possible_fact_changes:
durable_style_preferences:
issue_updates:
optimization_updates:
chinese_char_count:
optional_edit_note:
```

Output only revised prose unless the user requests notes or comparison.

## Handoff To Other Components

- Send `possible_fact_changes` to `continuity-check`.
- Send durable user preferences, recurring issues, and verified project-specific strategies to `memory-update`.
- Return risky content to `compliance-review` when polish alone cannot make it safe.
- Ask `memory-manager` for the revision bundle before revising an established novel.

## Do Not Do

- Do not add new plot events merely to make prose more dramatic.
- Do not erase deliberate ambiguity.
- Do not imitate a living author's distinctive style.
- Do not apply one novel's optimization log to another novel.
