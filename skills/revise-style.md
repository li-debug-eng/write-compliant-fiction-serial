# Revise Style

## Purpose

Polish existing prose without changing its intended plot function. Mature the
voice, reduce AI-like habits, compress repetition, improve subtext, and preserve
factual continuity.

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
6. Remove purely ornamental detail, but preserve lived-in detail when it builds
   social texture, bodily reality, class background, routine, embarrassment,
   fatigue, taste, relationship pressure, or character habit.
7. Before deleting a small detail, ask whether it reveals habit, class, fatigue,
   taste, relationship pressure, embarrassment, local life, or bodily reality.
   If yes, preserve or sharpen it rather than removing it.
8. Do not automatically delete hesitation, repeated gestures, evasive phrasing,
   small talk, unfinished sentences, or awkward pauses. Compress them only when
   they repeat information, flatten tension, or fail to reveal character.
9. Remove generic lyrical phrasing, mechanical contrast patterns, adjective stacks, and moralizing endings.
10. When revising for maturity, do not make every sentence equally polished.
    Allow controlled roughness when it belongs to the viewpoint character,
    social setting, fatigue, fear, class background, or emotional avoidance.
11. Do not polish every character into the same mature narrative voice. Preserve
    differences in education, class background, temperament, fatigue,
    confidence, evasiveness, bluntness, and local speech rhythm.
12. When improving dialogue, do not make every line perfectly direct.
    Characters may dodge, answer the wrong part, repeat a phrase, change the
    subject, use practical excuses, or speak in half-sentences when it fits the
    relationship and scene pressure.
13. Read once for repetitive sentence shapes and unnatural rhythm.
14. Recheck length when the user set a range.

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
- Send durable user preferences, recurring issues, and verified
  project-specific strategies to `memory-update`.
- Pass `issue_updates` to `memory-update` only for repeated, user-identified,
  or review-discovered revision problems that should affect future work on the
  resolved novel project; do not pass one-off sentence fixes as issues.
- Pass `optimization_updates` only when the revision surfaces a reusable
  project-specific strategy that worked or was explicitly preferred by the user,
  such as preserving lived-in details, handling relationship subtext, or shaping
  chapter endings. Do not pass one-off wording choices or generic style advice
  as optimization updates.
- Return risky content to `compliance-review` when polish alone cannot make it safe.
- Ask `memory-manager` for the revision bundle before revising an established novel.

## Do Not Do

- Do not add new plot events merely to make prose more dramatic.
- Do not erase deliberate ambiguity.
- Do not imitate a living author's distinctive style.
- Do not apply one novel's optimization log to another novel.
- Do not remove all ordinary friction, hesitation, local texture, or character roughness merely because the text is being made cleaner.

## Final Human Texture Check

- Did the revision preserve at least one concrete sensory or practical anchor where appropriate?
- Did it keep useful hesitation, avoidance, small talk, or imperfect rhythm when it reveals character?
- Did it avoid making every sentence equally efficient and every action perfectly optimized?
- Did it remove only generic filler rather than lived-in detail?
- Did it preserve distinct character voice rather than smoothing everyone into the same tone?
- Did any new `optimization_updates` describe reusable project-specific strategy rather than one-off plot beats?
- Does every durable Output Contract field used in this revision have a clear Handoff path?
