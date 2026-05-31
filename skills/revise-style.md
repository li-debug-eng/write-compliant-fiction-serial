# Revise Style

## Responsibility

Polish existing prose without changing its intended plot function. Mature the voice, remove AI-like explanation, compress repetition, improve subtext, and preserve factual continuity.

## Required Inputs

- `source_text_or_latest_hook` or `draft`.
- Requested tone, length, viewpoint, and formatting.
- Facts, outcomes, lines, or scene functions that must remain.
- Optional user feedback describing disliked habits.

## Revision Method

Read [../references/mature-fiction-style.md](../references/mature-fiction-style.md).

Revise in this order:

1. Preserve events, relationships, viewpoint, and required outcome.
2. Replace direct emotional explanation with action, pause, object use, environment, or dialogue mismatch where possible.
3. Shorten dialogue that explains too much. Leave room for evasion, interruption, and partial answers.
4. Delete repeated interpretation after an already-clear action or line.
5. Remove decorative detail that does not affect information, pressure, relationship, choice, or rhythm.
6. Remove generic lyrical phrasing, mechanical contrast patterns, adjective stacks, and moralizing endings.
7. Read once for sentence-shape repetition and natural rhythm.

## Output Contract

Return:

```text
revised_text:
preserved_facts:
possible_fact_changes:
durable_style_preferences:
optional_edit_note:
```

Output only revised prose unless the user asks for edit notes or comparison. Route `possible_fact_changes` to continuity checking. Route durable user preferences to memory update.
