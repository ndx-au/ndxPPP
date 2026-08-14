---
type: process
title: Process
description: Iteration state machine, naming, summary contract, and human sign-off.
tags: [ndxppp, brain]
---

# Process

This is the state machine. Roles implement it; they do not replace it.

## Current iteration

Look in `work/` (not `work/archive/`). Ignore `README.md` and any non-`NNNN-*` entries. Sort remaining directories by the four-digit prefix. The **lowest number** is the current iteration.

If none exist, there is no current iteration. The Engineer (or the human) creates `work/NNNN-slug/` with `spec.md`.

## Naming

- Folder: `NNNN-short-slug` (four digits, hyphen, slug). Example: `work/0001-modernize-v2/`.
- Next number is last used number (active or archived) plus one.
- Each iteration folder contains at least `spec.md`.

## State signals

Presence of files in the current iteration folder:

| Files | State | Who acts |
|---|---|---|
| `spec.md` only | **PLANNING** | Worker writes `plan.md`, then waits |
| `plan.md` exists, no `summary.md` | **BUILDING** | Worker executes after human approval of the plan |
| `summary.md` exists, no `incomplete.md` / `completed.md` | **REVIEW_PENDING** | Foreman (required on the review profile) |
| `incomplete.md` exists | **REVISION_REQUIRED** | Worker fixes, updates `summary.md`, deletes `incomplete.md` |
| `completed.md` exists | **DONE** | Human archives; agents stop |

`plan.md` existing does not authorize implementation until the human has approved the plan. If the human has not approved, stay in PLANNING even if the file is present.

## Blocking sign-off

If the current iteration contains `completed.md` and still lives under `work/` (not `work/archive/`):

1. Agents **stop**.
2. Agents **do not** start a later iteration.
3. Every response starts with a request that the human sign off by moving the folder:

```text
Please sign off: mv work/NNNN-slug work/archive/NNNN-slug
```

Only the **human** performs that move. That is the archive gate. Agents must not `mv`, `git mv`, or otherwise relocate iteration folders into `archive/`.

## Structural integrity

If the requested work violates [constitution.md](constitution.md) or [architecture.md](architecture.md):

1. Stop.
2. Tell the Architect which file conflicts and what would need to change.
3. After the human updates the brain, continue under the new text.

Do not “just this once.”

## `spec.md` contract

Use [templates/spec.md](../templates/spec.md). Required sections: Summary, Goals, Non-Goals, Success Criteria, Validation. Optional: User Stories, Technical Requirements, Dependencies, File Structure Changes, Integration Points, Future Considerations, `openspec:` frontmatter.

The human approves the spec before the Worker plans, unless the human wrote the spec themselves.

## `plan.md` contract

Use [templates/plan.md](../templates/plan.md). Atomic, checkable steps. Include at least one Foreman-runnable automated validation command, or explain why the iteration cannot have one.

Wait for human approval before executing.

## `summary.md` contract

Use [templates/summary.md](../templates/summary.md). Headings exactly:

### Files Changed

- Bullet list of modified, added, or deleted files.

### What Changed

- Short description of what was implemented and why.

### How to Validate

- Copy-pastable commands.
- At least one automated command is mandatory, unless this section explains why none can exist.

### Compliance Checklist

- `brain/constitution.md` followed
- `brain/architecture.md` respected
- No invented requirements beyond `spec.md` (or the OpenSpec change named in frontmatter)

## Foreman artifacts

- Reject: [templates/incomplete.md](../templates/incomplete.md) — concrete fix list. Do not edit `summary.md`.
- Approve: delete `incomplete.md` if present; write [templates/completed.md](../templates/completed.md) with quality score, optional refactors, optional future tasks.

Foreman does not commit. Foreman does not archive.

## Architect

The Architect is the human. “Ask the Architect” means ask the user. Agents do not sign off, do not silently change constitution/architecture/process, and do not treat a chat “LGTM” as archive.
