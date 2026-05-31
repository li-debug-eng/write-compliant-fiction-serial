# Memory Manager

## Purpose

Manage isolated long-term memory for one novel project at a time. Resolve the
target novel, provide task-specific memory bundles, and persist or return
structured patches without mixing projects.

## Use When

- Any existing serial task needs recovery context.
- A new novel project must be created.
- `memory-update` produces a structured patch.
- The user asks to inspect, repair, or maintain a novel's creative memory.

## Required Context

- User request and available conversation context.
- Available novel projects from MCP or workspace files.
- A resolved `novel_id` before reading or writing durable memory.

## Optional Context

- Explicit novel name from the user.
- Current novel project from `get_current_novel_project()`.
- [../references/novel-project-template.md](../references/novel-project-template.md) for local project creation.
- Structured patch from `memory-update`.

## Procedure

### Resolve One Novel Project

1. Use the explicit novel name or `novel_id` when the user provides it.
2. Otherwise inspect the current context and current project.
3. If exactly one project is a safe match, use it.
4. If no safe match exists, ask the user to select an existing project or create a new one.
5. Never read from one novel and write to another.

Each novel uses:

```text
projects/{novel-id}/
├─ project-memory.md
├─ continuity-record.md
├─ character-state.md
├─ chapter-index.md
├─ issue-log.md
├─ optimization-log.md
└─ user-preferences.md
```

### Read The Smallest Task Bundle

For continuation, read:

```text
project-memory.md
continuity-record.md
chapter-index.md
issue-log.md
optimization-log.md
```

For ordinary style revision, read:

```text
user-preferences.md
issue-log.md
optimization-log.md
continuity-record.md only when facts may shift
```

For compliance review, read:

```text
project-memory.md
continuity-record.md
issue-log.md
```

For outline planning, read:

```text
project-memory.md
continuity-record.md
chapter-index.md
optimization-log.md
```

For continuity auditing, read:

```text
project-memory.md
continuity-record.md
character-state.md
chapter-index.md
issue-log.md
```

### Maintain Project Memory

Store only project-level information:

- work name, genre, subject, main line, viewpoint, and core selling points;
- immutable canon and accepted retcons;
- character state, relationship shifts, timeline, locations, world rules, hooks, unresolved events, and pending payoffs;
- durable writing preferences explicitly requested for this novel;
- recurring problems in `issue-log.md`;
- verified effective strategies in `optimization-log.md`.

Every issue entry includes:

```text
issue_type:
symptom:
location:
severity:
fixed: yes | no
avoidance_rule:
```

Optimization entries may cover prose style, pacing, character handling,
relationship handling, and chapter endings. Prioritize proven project-specific
strategies during later continuation, revision, and planning.

### Use MCP When Available

Use compatible MCP tools when exposed:

```text
get_novel_projects()
get_current_novel_project()
create_novel_project(novel_name)
get_project_memory(novel_id)
get_continuity_record(novel_id)
get_issue_log(novel_id)
get_optimization_log(novel_id)
append_memory_patch(novel_id, patch, reason)
search_novel_memory(novel_id, query, limit)
```

Call `search_novel_memory` only for a narrow uncertainty. Use `append_memory_patch` only for a patch built by `memory-update`.

### Persist Or Return A Patch

1. Validate that the patch includes the resolved `novel_id` and matches the selected project.
2. If MCP append persistence exists, call `append_memory_patch(novel_id, patch, reason)`.
3. If actual workspace editing is explicitly available and used, report the exact files written.
4. If MCP is unavailable and no local write actually succeeds, output the copyable `## Memory Patch`.
5. Never imply persistence merely because a patch was generated.

### Fallback Memory Use

When MCP tools and local file writes are unavailable:

1. Do not claim that memory was saved.
2. Output a copyable `## Memory Patch`.
3. Tell the user to save that patch in their project files or paste it at the start of the next related task.
4. If the user later provides a previous Memory Patch, treat it as temporary project memory for the current session.
5. If multiple patches are provided, apply the newest explicit user instruction first, then merge durable canon updates, issue-log updates, and optimization-log updates.
6. Do not merge patches across different `novel_id` values.
7. If a patch lacks `novel_id`, ask for the target novel unless the current project is unambiguous.

## Output Contract

For reads, return:

```text
novel_id:
novel_name:
task_bundle_type:
memory_bundle:
missing_context:
retrieval_source:
```

For writes, return:

```text
novel_id:
novel_name:
persistence_status: mcp_appended | local_files_written | copyable_patch_only
files_updated:
memory_patch:
```

## Handoff To Other Components

- Send the smallest task-specific bundle to `continue-chapter`, `revise-style`, `compliance-review`, `continuity-check`, or `outline-planning`.
- Receive `novel_id`, structured patch, and reason from `memory-update`.

## Do Not Do

- Do not use global cross-novel memory.
- Do not merge settings, characters, preferences, issues, or optimizations from different novels.
- Do not persist one-time requests or speculative facts.
- Do not claim persistence unless MCP append or an actual local file write succeeds.
