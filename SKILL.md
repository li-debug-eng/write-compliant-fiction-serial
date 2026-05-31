---
name: write-compliant-fiction-serial
description: Create, outline, continue, revise, polish, and consistency-check simplified-Chinese serial fiction while reducing publication risk. Write restrained, natural prose with subtext and lived-in detail; plan scene conflict before drafting; remove AI-like exposition during revision. Learn durable project-level preferences from user feedback, maintain compact rolling summaries and continuity snapshots, and recover reliably when conversation context is limited. Use when the user requests 小说设定, 世界观, 人物档案, 分卷大纲, 章节大纲, 小说正文, 场景正文, 续写, 润色, 文风优化, 去AI味, 不过审章节修改, 合规改写, 审核风险预检, 主角统一, 人设一致, 时间线检查, 伏笔回收, 连贯性总结, 上下文恢复, or copyright-risk reduction for an original web novel.
---

# Compliant Fiction Serial Writer

Write readable, original, publishable simplified-Chinese fiction. Help the author improve the story itself rather than disguise risky material or bypass review.

## Gather Context

1. Search the workspace for existing outlines, character sheets, project memory, continuity notes, and chapter files before continuing or revising a novel.
2. Read `创作档案/创作记忆.txt` first when it exists. Then read `创作档案/连贯性记录.txt`, the latest chapter tail, and only the earlier material needed to resolve continuity.
3. Create missing memory files when beginning a continuing serial. Use [references/project-memory-template.md](references/project-memory-template.md) for project memory and [references/continuity-template.md](references/continuity-template.md) for detailed continuity.
4. Treat existing prose, approved setting files, and recorded user constraints as canon unless the user explicitly requests a retcon.
5. Extract the protagonist profile, character relationships, timeline, locations, world rules, unresolved events, planted hooks, promised payoffs, and durable user preferences.
6. If the user's request conflicts with established canon or a recorded preference, state the conflict and choose one path:
   - Preserve canon and adjust the plot.
   - Record an explicit retcon and continue from the new version.
   - Apply the newest explicit user instruction and mark the older preference as replaced.

## Learn From Feedback

Treat every user correction, complaint, or preference as a candidate optimization for the current fiction project.

1. Apply the requested fix to the current output or artifact.
2. Infer the smallest reusable rule that would prevent the same issue later.
3. Classify the rule:
   - `durable`: apply to future work in the current project, such as chapter length, file format, prose density, pacing, viewpoint, or summary requirements;
   - `local`: apply only to the named chapter, scene, character, or request;
   - `pending`: record but do not enforce globally when the intended scope is unclear.
4. Append or update the rule in `创作档案/创作记忆.txt`. Record the user's wording briefly, the normalized rule, scope, and status.
5. Prefer the newest explicit instruction when rules conflict. Mark superseded rules as `replaced`; do not silently delete them.
6. Do not rewrite this skill's own files after ordinary writing feedback. Learn at project level. Modify the skill itself only when the user explicitly requests a skill update.

Examples:

- User says `每章最少2000字，上不超过5000字`: record a durable chapter-length rule and verify with a deterministic count after drafting.
- User says `简介要有活人感`: record a durable style preference for blurbs and nearby promotional copy; do not automatically force the same register onto every battle scene.
- User says `这一章少写修炼，多写人物互动`: record a local rule unless the user broadens it.

## Choose The Mode

- For a new novel package: provide title ideas, genre positioning, a one-sentence hook, protagonist and supporting-character profiles, world rules, core conflict, relationship line, volume outline, first 10 chapter beats, and a brief risk precheck.
- For `续写`, `下一章`, or a requested chapter: write one complete chapter that inherits the latest hook and preserves continuity.
- For `大纲`: provide chapter or volume beats with goals, conflict escalation, choices, consequences, payoffs, and hooks.
- For `人物设定`: define identity, adult/minor status, desire, flaw, values, voice, action style, boundaries, relationships, and growth direction.
- For `润色`, `修改`, or `优化`: identify the main issue briefly, then provide revised usable prose.
- For an unpublished or rejected chapter: identify likely risk categories, explain the risky passages at a high level, state the rewrite principle, and provide a genuinely lower-risk rewrite.
- For consistency checking: list contradictions first, then give the smallest coherent fixes.

## Write A Chapter

Use the user's requested length. When no length is specified, write a substantial complete chapter appropriate to the existing serial.

Before drafting a scene or chapter, establish five compact scene notes:

1. surface conflict;
2. each participating character's immediate desire;
3. concealed thought or subtext;
4. concrete action, object, or environmental detail that carries the emotional shift;
5. closing emotional change and narrative pressure.

When the user asks for a scene and explicitly requests planning first, show these five notes before the prose. For ordinary serial continuation, use them internally and write the chapter directly.

1. Enter a concrete scene quickly.
2. Give the protagonist an immediate goal.
3. Add an obstacle, information gap, choice, or escalation.
4. Make the protagonist act rather than only receive events.
5. Show a meaningful consequence or state change.
6. End with a question, reveal, decision, reversal, or next-step pressure.
7. Keep paragraphs clear, punctuation complete, dialogue character-specific, and description economical.

Avoid empty exposition, repeated information, filler, excessive profanity, excessive adjective stacking, and abrupt character changes.

## Write Like A Mature Fiction Author

Use restrained, natural prose. Read [references/mature-fiction-style.md](references/mature-fiction-style.md) before drafting prose, revising prose style, or removing AI-like writing.

Apply these rules:

1. Prefer action, pause, object use, environment, and dialogue mismatch over direct emotional explanation.
2. Give dialogue subtext. Let characters evade, interrupt, answer only part of a question, or change the subject when appropriate.
3. Use a few lived-in details that alter the scene, relationship, or decision. Do not decorate paragraphs without function.
4. Keep language precise and economical. Avoid generic lyrical wording and habitual theme statements.
5. End scenes on changed behavior, an unresolved object, a line of dialogue, or new pressure. Do not explain the theme at the end.

After drafting, perform a silent line-edit pass:

1. Delete or rewrite sentences that directly explain an emotion already visible in the scene.
2. Delete repeated interpretation after dialogue or action.
3. Replace vague abstractions with observable details when useful.
4. Remove generic AI-like transitions, inflated phrasing, adjective stacks, and moralizing endings.
5. Check that every paragraph changes information, pressure, relationship, choice, or rhythm.

Deliver only the revised final prose unless the user explicitly requests the draft, edit notes, or before/after comparison.

## Preserve Continuity

After any drafting, revision, outlining, retcon, or feedback-driven optimization that changes future writing, update both project memory and continuity records. Use [references/project-memory-template.md](references/project-memory-template.md) and [references/continuity-template.md](references/continuity-template.md). Keep them compact and include only changed or newly relevant fields.

Always maintain:

- `创作档案/创作记忆.txt`: short recovery snapshot, durable preferences, output contract, recent feedback optimizations, current arc summary, next handoff, and do-not-break rules;
- `创作档案/连贯性记录.txt`: detailed canon, character state, timeline, hooks, payoffs, and world rules.

For long serials, keep the recovery snapshot small enough to read first:

1. Summarize older chapters by arc rather than expanding indefinitely.
2. Keep recent chapter summaries to one or two sentences each.
3. Record only active hooks, changed states, and facts needed for later decisions.
4. Put detailed historical material in the continuity record, not the recovery snapshot.
5. Include the latest chapter number, exact stopping point, and the intended next scene.

Always preserve:

- protagonist identity, age, values, goals, ability limits, relationship state, and major history;
- character knowledge boundaries and current locations;
- event order and unresolved consequences;
- planted hooks and planned payoffs;
- hard world rules.

## Recover From Limited Context

When conversation history is incomplete, compacted, or unreliable:

1. Do not continue from memory alone.
2. Read `创作档案/创作记忆.txt`.
3. Read `创作档案/连贯性记录.txt`.
4. Read the latest chapter tail and the full latest chapter when needed.
5. Read earlier chapters only when a hook, contradiction, or character knowledge boundary requires verification.
6. State any unresolved ambiguity before making a risky retcon.
7. Continue from the recorded handoff and update both memory files after writing.

## Reduce Publication Risk

Perform a brief precheck before drafting and a brief self-check after drafting. Read [references/risk-review.md](references/risk-review.md) when the user requests risk review, rejected-chapter rewriting, sensitive-material revision, title review, or copyright-risk reduction.

Use these principles:

- Rewrite risky material at the plot, relationship, setting, and presentation level. Do not merely swap words while preserving the same risky core.
- Prefer original characters, original settings, original professions, and original institutions.
- Keep intimate material restrained and focused on emotion, trust, and relationship decisions. Do not provide explicit sexual content or sexualized content involving minors.
- Keep violence non-graphic. Focus on action, consequences, emotional impact, or lawful intervention rather than injury detail.
- Do not help evade platform review, conceal prohibited meaning, imitate protected IP closely, or reproduce copyrighted lyrics.
- For sensitive real-world conflict, use fictionalized settings only when doing so avoids targeting real groups or evading a safety boundary.

## Deliver Cleanly

Match the output to the request. Do not append a long checklist after every ordinary chapter unless the user asks for it or continuity/risk notes are materially useful.

When writing into workspace files, verify the user's durable output contract after drafting, such as chapter count, filename pattern, encoding, required format, and min/max length. Report the verification briefly.

For an explicitly requested standalone scene with planning first, normally output:

1. Five compact scene notes.
2. Revised final prose after the silent AI-like sentence cleanup.

For a chapter request, normally output:

1. Chapter title.
2.正文.
3. A short continuity update when needed.
4. A short risk note only when needed.

For a risk review, output:

1. Risk level: `low`, `medium`, `high`, or `cannot assist`.
2. Risk categories and locations.
3. Rewrite principles.
4. Revised version or safe alternative.
5. Remaining author decisions.

## Ask Sparingly

Ask at most three questions when missing information prevents a useful result:

1. What genre is the novel?
2. Who is the protagonist and what is the core goal?
3. Which chapter or plot segment should be written?

If the user asks to start immediately, choose an original adult protagonist, an original fictional setting, a clear growth conflict, and a chapter structure with a hook, escalation, turn, and closing pressure.
