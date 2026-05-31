# Novel Project Template

Use one isolated directory per novel. Replace `{novel-id}` with a stable identifier. Never store two novels in one directory.

```text
projects/
└─ {novel-id}/
   ├─ project-memory.md
   ├─ continuity-record.md
   ├─ character-state.md
   ├─ chapter-index.md
   ├─ issue-log.md
   ├─ optimization-log.md
   └─ user-preferences.md
```

## project-memory.md

```md
# Project Memory

Novel ID:
Novel Name:
Updated At:

## Identity
- Genre:
- Subject:
- Main Line:
- Viewpoint:
- Core Selling Points:

## Immutable Canon
- ...

## Current Stage
- ...

## Long-Term Direction
- ...

## Next-Time Instructions
- ...
```

## continuity-record.md

Use [continuity-template.md](continuity-template.md). Record relationships, timeline, locations, world rules, resources, hooks, unresolved events, and accepted retcons.

## character-state.md

```md
# Character State

Novel ID:
Updated At:

| Character | Identity | Location | Goal | Relationship State | Knowledge Boundary | Resources or Injuries | Last Change |
| --- | --- | --- | --- | --- | --- | --- | --- |
```

## chapter-index.md

```md
# Chapter Index

Novel ID:
Updated At:

| Chapter | Title | File | Summary | State Changes | New or Advanced Hooks | Direct Handoff |
| --- | --- | --- | --- | --- | --- | --- |
```

## issue-log.md

```md
# Issue Log

Novel ID:
Updated At:

| ID | Issue Type | Symptom | Location | Severity | Fixed | Avoidance Rule |
| --- | --- | --- | --- | --- | --- | --- |
```

Record user-reported issues and repeated issues found during checking. Keep one-time wording edits out unless they reveal a reusable problem.

## optimization-log.md

```md
# Optimization Log

Novel ID:
Updated At:

| ID | Strategy Type | Verified Strategy | Evidence or User Feedback | Applies To | Status |
| --- | --- | --- | --- | --- | --- |
```

Use strategy types such as `style`, `pacing`, `character`, `relationship`, and `chapter-ending`. Keep only verified or explicitly preferred strategies active.

## user-preferences.md

```md
# User Preferences

Novel ID:
Updated At:

| ID | Preference | Scope: durable / local / pending | Status: active / replaced | Source |
| --- | --- | --- | --- | --- |
```

Store project-specific preferences. Do not turn one-time requests into durable rules.
