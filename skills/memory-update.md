# Memory Update

## Purpose

At the end of a concrete task, consolidate durable changes from selected components into one structured per-novel memory patch. This component builds the patch; it does not choose the novel project or claim persistence.

## Use When

- Drafting, planning, rewriting, continuity repair, or accepted retcons change durable project state.
- User feedback should become a reusable project preference, issue record, or verified optimization strategy.
- The user explicitly says `以后都这样写`, `记住这个问题`, or `下次避免这种写法`.

Do not run for ordinary sentence-level polish with no durable learning.

## Required Context

- `novel_id` and `novel_name` resolved by `memory-manager`.
- Durable changes produced by the completed task: canon, character state, timeline, hooks, long-range direction, preferences, repeated issues, verified optimizations, recent summary, or next handoff.

## Optional Context

- Existing task-specific memory bundle from `memory-manager`.
- User correction history from the current task.
- Accepted retcons and output verification results.

## Procedure

1. Reject the update if `novel_id` is missing. Ask `memory-manager` to resolve the project first.
2. Include only durable changes:
   - canon, character state, relationship state, timeline, location, rules, resources, hooks, or chapter index changes;
   - accepted long-range direction;
   - durable user preferences;
   - repeated or explicitly remembered problems;
   - optimization strategies that were effective or explicitly preferred;
   - next-time instructions needed for continuation.
3. Exclude ordinary wording edits and one-time request-local constraints.
4. For user feedback, infer the smallest reusable rule. Classify it as `durable`, `local`, or `pending`.
5. Mark superseded preferences as `replaced`; do not silently delete them.
6. Format a single structured patch.
7. Pass the patch and a concise reason to `memory-manager`.

## Output Contract

Return:

```md
## Memory Patch

Novel ID:
Novel Name:

### Project Memory Updates
- ...

### Continuity Updates
- ...

### Character State Updates
- ...

### Chapter Index Updates
- ...

### User Preference Updates
- ...

### Issue Log Updates
- ...

### Optimization Log Updates
- ...

### Next-Time Instructions
- ...
```

Also return:

```text
patch_reason:
update_required: yes | no
excluded_short_term_items:
```

## Handoff To Other Components

- Receive durable changes from `continue-chapter`, `revise-style`, `compliance-review`, `continuity-check`, or `outline-planning`.
- Send `novel_id`, `memory_patch`, and `patch_reason` to `memory-manager`.

## Do Not Do

- Do not choose a novel project by guesswork.
- Do not write chapter prose or perform a full continuity audit.
- Do not persist speculative facts, one-time requests, or ordinary wording changes as long-term memory.
- Do not claim that files or MCP memory were updated.
