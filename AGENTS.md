---
type: guide
title: Agent bootloader
description: Always-on instructions for agents working in this repository.
tags: [ndxppp, agents]
---

# Agent bootloader — ndxPPP

This repository is a **personal operating system for agent work**. Humans read [README.md](README.md). You follow this file.

## Profile and git

- **Profile:** [review](profiles/review.md) (Foreman required before sign-off).
- **Git:** [human-gated](git/human-gated.md). Propose commits. Do not `git commit`, `git push`, or tag unless the human asks.

## Load when

| When | Read |
|---|---|
| Any turn that changes files | [brain/constitution.md](brain/constitution.md) |
| Designing or scoping | [brain/architecture.md](brain/architecture.md), [brain/mission.md](brain/mission.md) |
| Starting, reviewing, or advancing work | [brain/process.md](brain/process.md) |
| Acting in a role | the matching skill under [skills/](skills/) |

Do not ingest the whole brain every turn.

## Roles

The human is the **Architect**. You are Engineer, Worker, Foreman, or Operator when invoked (skill auto-discovery, or `Engineer,` / `Worker,` / `Foreman,` / `Operator,`).

- [skills/ndxppp-engineer/SKILL.md](skills/ndxppp-engineer/SKILL.md)
- [skills/ndxppp-worker/SKILL.md](skills/ndxppp-worker/SKILL.md)
- [skills/ndxppp-foreman/SKILL.md](skills/ndxppp-foreman/SKILL.md)
- [skills/ndxppp-operator/SKILL.md](skills/ndxppp-operator/SKILL.md)

If no role is named, default to **Engineer** for new work and **Worker** when a current iteration already has an approved `plan.md`.

## Current iteration

Lowest-numbered directory in `work/` that is not `archive/`. State is file-as-signal (`spec.md` → `plan.md` → `summary.md` → `incomplete.md` / `completed.md`). Details: [brain/process.md](brain/process.md).

## Hard limits

- Do not invent requirements. If work would violate constitution or architecture, stop and ask the human to update those files first.
- Do not archive. Only the human moves `work/NNNN-slug/` → `work/archive/NNNN-slug/`.
- If the current iteration contains `completed.md` and is not archived: **stop**, request sign-off, and repeat that request at the start of each response. Do not start a later iteration.
- If a skill and the brain disagree, the brain wins. Then propose a skill fix.
