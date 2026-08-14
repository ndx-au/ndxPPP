---
type: guide
title: Roles
description: Architect, Engineer, Worker, Foreman, Operator — contracts and invocation.
tags: [ndxppp, roles]
---

# Roles

Five postures. One of them is you.

## Architect (human)

You own the project. You decide tradeoffs. You change constitution and architecture. You archive iterations.

“Ask the Architect” means the agent asks **you**. There is no Architect skill.

## Engineer

Discovery and `spec.md`. Invoke at the start of an iteration, in Plan mode, or when a request may violate the brain.

Skill: [skills/ndxppp-engineer/SKILL.md](../skills/ndxppp-engineer/SKILL.md)

Must not implement the body in this role. Must not archive.

## Worker

`plan.md` → wait → implement → `summary.md`. Fixes `incomplete.md`.

Skill: [skills/ndxppp-worker/SKILL.md](../skills/ndxppp-worker/SKILL.md)

Must not archive. Must not commit unless the git module and you allow it.

## Foreman

Audit spec / plan / summary / code. Run validation. Write `incomplete.md` or `completed.md`.

Skill: [skills/ndxppp-foreman/SKILL.md](../skills/ndxppp-foreman/SKILL.md)

Must not commit. Must not archive. Must not approve unvalidated work.

## Operator

Meta-process: sequencing, scaffolding, doc and skill hygiene. Proposes brain edits; you approve constitution / architecture / process.

Skill: [skills/ndxppp-operator/SKILL.md](../skills/ndxppp-operator/SKILL.md)

Must not archive. Must not quietly ship product features.

## Invocation

Cursor auto-invokes from skill `description` fields (mirrored in `.cursor/skills/`).

Aliases, still valid:

```text
Engineer, draft a spec for …
Worker, the plan is approved — implement.
Foreman, audit the current iteration.
Operator, the docs disagree with the tree.
```

If no role is named: Engineer for new work; Worker when an approved plan already exists. See [AGENTS.md](../AGENTS.md).

## What nobody may do except you

| Action | Who |
|---|---|
| Archive `work/NNNN-slug/` → `work/archive/` | Human |
| Change constitution / architecture / process | Human (Operator may draft) |
| Declare the work “done” in git history | Human, via whatever git module you chose |
