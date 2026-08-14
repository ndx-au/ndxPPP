---
type: guide
title: Anti-patterns
description: Ceremony versus discipline. What to prune, what never to skip.
tags: [ndxppp, anti-patterns]
---

# Anti-patterns

The v2 bet: **keep the gates, drop the theater.** If a ritual does not prevent invented requirements, architectural drift, or a fake “done,” delete it.

## Discipline (do not skip)

- Spec before plan before body, unless you wrote the spec yourself and said so.
- Plan approval before implementation.
- File-as-signal in `work/` (no parallel tracker that agents will ignore).
- Foreman on the **review** profile, with at least one real validation command.
- Human archive. Not a chat LGTM. Not the Worker renaming a folder “to be helpful.”
- Update constitution/architecture **before** work that would violate them.
- Docs that describe the OS match the tree ([constitution](../brain/constitution.md) law 6).

## Ceremony (prune under load)

- Reading every brain file every turn. Use [AGENTS.md](../AGENTS.md) “load when.”
- Auto-commit, auto-push, auto-tag. Default git is [human-gated](../git/human-gated.md).
- PATCH = iteration number, unless you opted into [iteration-semver](../git/iteration-semver.md).
- Duplicate pattern trees (v1). Use [profiles](../profiles/review.md).
- ACME / toy product filler inside the brain. The brain is *this* project.
- Quality-score theater without running the tests.
- A second spec in chat that is not written into `spec.md`.
- OpenSpec **and** a full duplicate `spec.md` in the same iteration.
- MCP or a vendor memory as the source of truth for in-flight work.
- Skills that restate the entire process.md. Point; don’t fork.

## Failure modes this OS is for

| Failure | Counter |
|---|---|
| Agent invents a requirement | Spec + Foreman compliance checklist |
| Architecture drifts in the diff | Structural integrity stop |
| Session ends, context dies | Files in git |
| “It’s done” but nothing was reviewed | `completed.md` + archive gate |
| Process docs lie | Law 6, Operator hygiene |

If you find a step that does not serve one of those, it is a candidate for [evolving.md](evolving.md).
