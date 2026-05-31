# Continuity Check

## Responsibility

Audit consistency across protagonist state, character knowledge, timeline, locations, world rules, resources, relationships, planted hooks, and promised payoffs. Do not draft a new chapter or silently retcon canon.

## Required Inputs

- Existing project memory and continuity records when available.
- Latest chapter tail and the relevant earlier chapters or outline segments.
- Proposed draft, rewrite, or plan when checking future text.
- User-requested retcons, if any.

## Check Method

Read [../references/continuity-rules.md](../references/continuity-rules.md).

1. Build a compact canon snapshot needed for the current task.
2. Compare proposed or existing text against fixed canon and recent state changes.
3. Check who knows each fact and when they learned it.
4. Check location, resource, item, relationship, and power progression.
5. Check hook state: `open`, `advanced`, `paid off`, or `retconned`.
6. Distinguish contradiction from unresolved mystery.
7. Recommend the smallest coherent fix. Do not rewrite unrelated material.

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
```

Pass `canon_snapshot`, active hooks, and knowledge boundaries to continuation or outline planning. Pass accepted fixes and record patches to memory update.
