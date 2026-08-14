---
type: guide
title: Evolving
description: How to change the OS on purpose without silent drift.
tags: [ndxppp, evolving]
---

# Evolving

The rails are meant to be forked per project and edited as you learn. Unowned process files rot. Owned ones get shorter.

## Who may change what

| File | Agent may draft | Requires explicit human approval |
|---|---|---|
| `brain/mission.md` | Operator, Engineer | Yes if it changes purpose |
| `brain/constitution.md` | Operator | **Yes** |
| `brain/architecture.md` | Operator, Engineer | **Yes** |
| `brain/process.md` | Operator | **Yes** |
| `skills/`, `templates/`, `docs/` | Operator | Yes if they change a gate |
| `profiles/`, `git/` | Operator | Yes if `AGENTS.md` still points at the old ones |
| `AGENTS.md` profile/git lines | Operator | **Yes** (that is how the host declares the overlay) |

Worker and Foreman do not “fix” the OS in passing while shipping a feature. If the feature needs a new law, stop and take an Operator/Architect pass.

## How to change a gate

1. Name the friction (ceremony vs a real failure mode). See [anti-patterns.md](anti-patterns.md).
2. Draft the brain edit.
3. Human approves.
4. Update skills and `docs/` in the **same** iteration so constitution law 6 holds.
5. Run one iteration under the new rule before copying it to another repo.

## Per-project forks

A host repo’s `brain/` will diverge. That is success. Do not merge host constitution back here unless the change is truly about the OS.

This repository evolves through the same loop it defines (`work/NNNN-slug/`).

## Skills vs brain

If a skill grows a new hard limit that the brain does not have, you added a shadow constitution. Put the law in `brain/constitution.md` or `brain/process.md`, then point the skill at it.
