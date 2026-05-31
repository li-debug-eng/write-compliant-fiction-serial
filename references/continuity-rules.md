# Continuity Rules

Use these shared rules when checking, planning, continuing, revising, or persisting a serial-fiction project.

## Project Isolation

Resolve one `novel_id` before reading canon. Use only that novel project's records. Never merge characters, relationships, rules, hooks, issues, optimization strategies, or preferences across novels.

## Canon Priority

Apply this order:

1. newest explicit user instruction;
2. explicit retcon recorded by the user or accepted in project memory;
3. published or workspace prose;
4. approved outlines and setting files;
5. project memory and continuity records;
6. inference.

When sources conflict, report the conflict. Preserve canon or record an explicit retcon. Do not silently overwrite history.

## Required Consistency Dimensions

### Protagonist

- identity, age, adult/minor status, appearance keywords, and voice;
- values, concrete needs, flaws, and habitual response under pressure;
- ability rules, costs, hard limits, injuries, resources, items, and power level;
- current location, relationship state, and unfinished obligations.

### Characters And Relationships

- identity, voice, current goal, and relationship to the protagonist;
- location and timeline participation;
- adult/minor status when relevant;
- before-and-after relationship state for each meaningful scene;
- knowledge boundary: what a character knows, when they learned it, and what remains hidden.

### Timeline And Location

- event order and elapsed time;
- travel feasibility;
- day, season, deadline, and recovery time when relevant;
- each important character's location before and after a scene;
- the exact handoff from the preceding chapter to the next chapter.

### World Rules

- institutions, factions, professions, schools, families, and hierarchy;
- power progression, resource economy, technology, magic, or system limits;
- hard rules that later convenience must not contradict.

### Hooks And Payoffs

Track each hook with:

```text
hook:
planted_in:
current_status: open | advanced | paid_off | retconned
expected_payoff:
payoff_window:
knowledge_holders:
```

Do not confuse unresolved mystery with contradiction. Advance hooks in partial steps and preserve promised payoff logic.

## Repair Priority

When a contradiction exists, prefer the smallest coherent repair:

1. clarify wording without changing facts;
2. adjust a local action, line, or transition;
3. repair a record that was summarized incorrectly;
4. propose an explicit retcon only when local repair cannot work.

Do not rewrite unrelated scenes merely because a smaller fix feels less dramatic.

## Compact Canon Snapshot

For downstream components, prefer:

```text
novel_id:
latest_chapter:
latest_handoff:
current_location:
protagonist_state:
relationship_state:
ability_limits:
current_resources:
active_hooks:
knowledge_boundaries:
hard_world_rules:
next_pressure:
```

Keep the snapshot task-local. Retrieve earlier chapters only when verification requires them.
