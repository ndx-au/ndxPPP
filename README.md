---
type: overview
title: ndxPPP
description: Personal operating system for file-system-centric, human-gated AI coding work.
tags: [ndxppp]
---

# ndxPPP

A personal operating system for agent work. Rules, architecture, and iteration state live as ordinary markdown in the repo — versioned, inspectable, and gated by a human. Chat is the engine. These files are the rails.

This is not a framework to install and not a product to evangelize. It is the process substrate you copy into a repo and then evolve.

**Why files beat chat:** [docs/philosophy.md](docs/philosophy.md). **What changed in 2026:** [docs/changelog.md](docs/changelog.md).

## 60-second start

1. Read [brain/mission.md](brain/mission.md) and [brain/constitution.md](brain/constitution.md). They describe *this* repo. In another project, you replace them.
2. Point your agent at [AGENTS.md](AGENTS.md).
3. Start an iteration: ask the Engineer for a spec, or create `work/NNNN-short-slug/spec.md` yourself.
4. Worker writes `plan.md`, waits for you, then implements and writes `summary.md`.
5. Foreman writes `completed.md` or `incomplete.md`.
6. You sign off by moving the folder to `work/archive/`. Agents cannot do this step.

```
spec.md → plan.md → summary.md → completed.md | incomplete.md → you archive
```

## Layout

| Path | Role |
|---|---|
| [AGENTS.md](AGENTS.md) | Agent bootloader (always on) |
| [brain/](brain/constitution.md) | Law, why, success state, process |
| [work/](work/README.md) | Iterations; `archive/` is human-only |
| [skills/](skills/ndxppp-engineer/SKILL.md) | Engineer, Worker, Foreman, Operator |
| [profiles/](profiles/review.md) | Overlays: review (default), solo, docs |
| [git/](git/human-gated.md) | Swappable git protocol |
| [templates/](templates/spec.md) | Iteration artifact skeletons |
| [docs/](docs/philosophy.md) | The human manual |

The **brain** is durable project intelligence. The **body** is everything else in the repo (in this repo, the OS files *are* the product).

## Pick a profile

Declare profile + git module in `AGENTS.md`. This repo uses **review** + **human-gated**.

| Profile | When |
|---|---|
| [review](profiles/review.md) | Default. Foreman must approve before you archive. |
| [solo](profiles/solo.md) | Throwaway / prototype. Foreman on demand. |
| [docs](profiles/docs.md) | Technical writing. Writer/Editor names on the same loop. |

Git defaults to [human-gated](git/human-gated.md) (agents propose, you commit). [feature-branch](git/feature-branch.md), [stacked-diffs](git/stacked-diffs.md), and [iteration-semver](git/iteration-semver.md) are opt-in.

## Documentation map

- [Philosophy](docs/philosophy.md) — the argument
- [Anatomy](docs/anatomy.md) — files and folders
- [Workflow](docs/workflow.md) — state machine and the human gate
- [Roles](docs/roles.md) — who may do what
- [Tools](docs/tools.md) — Cursor, Claude Code, OpenSpec, MCP
- [Ontology](docs/ontology.md) — YAML frontmatter / OKF
- [Adopting](docs/adopting.md) — copy this OS into another repo
- [Evolving](docs/evolving.md) — change the rails on purpose
- [Anti-patterns](docs/anti-patterns.md) — ceremony vs discipline
- [Changelog](docs/changelog.md) — v1 → v2

## Using it here

This repository dogfoods the OS. The first real iteration is [work/0001-modernize-v2](work/0001-modernize-v2/spec.md).
