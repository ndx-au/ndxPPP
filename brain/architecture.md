---
type: architecture
title: Architecture
description: Success-state layout of the ndxPPP operating system.
tags: [ndxppp, brain]
---

# Architecture

Declare the target success state. The Foreman audits work against this file. If implementation needs a different shape, the Architect updates this file first.

## Goals

- One canonical OS (Terence lineage), not a menu of copy-paste patterns.
- Progressive disclosure: [AGENTS.md](../AGENTS.md) is always on; skills and brain files load on demand.
- Durable intelligence in `brain/`; ephemeral-but-versioned work in `work/`; human-only history in `work/archive/`.
- Profiles as overlays, not forks. Git as a swappable module.
- Documentation accurate enough to be the product.

## Tree (v2)

```
ndxPPP/
  README.md                 # humans
  AGENTS.md                 # agents
  CLAUDE.md                 # pointer at AGENTS.md
  LICENSE
  brain/                    # durable intelligence
  work/                     # iterations; archive/ is human-only
  skills/                   # role contracts (canonical)
  .cursor/skills/           # mirrors for Cursor auto-invocation
  profiles/                 # review | solo | docs
  git/                      # human-gated | feature-branch | stacked-diffs | iteration-semver
  templates/                # spec, plan, summary, completed, incomplete
  docs/                     # philosophy, anatomy, workflow, roles, tools, ontology, adopting, evolving, anti-patterns, changelog
```

## Progressive disclosure

| Layer | When it loads |
|---|---|
| `AGENTS.md` | Every agent session |
| Role `SKILL.md` | When that role is invoked or implied |
| `brain/constitution.md` | Any turn that changes files |
| `brain/architecture.md`, `brain/mission.md` | Scoping, design, structural conflict |
| `brain/process.md` | Starting, advancing, or reviewing an iteration |
| `docs/` | Humans, and Operator when repairing the manual |

Skills must not duplicate the brain. They point at it. If they drift, the brain wins.

## Profiles are overlays

[profiles/review.md](../profiles/review.md) is the default (Foreman required). [solo](../profiles/solo.md) and [docs](../profiles/docs.md) change who must act and what extra checks apply. They do not copy the tree.

## Iteration artifacts

Each `work/NNNN-slug/` folder uses file-as-signal:

| File | Meaning |
|---|---|
| `spec.md` | What the human asked (or Engineer drafted and human approved) |
| `plan.md` | How the Worker will do it (human approves before code) |
| `summary.md` | What was delivered and how to validate |
| `incomplete.md` | Foreman rejection; Worker must fix |
| `completed.md` | Foreman approval; human must archive |

Contracts live in [process.md](process.md). Skeletons live in [templates/](../templates/spec.md).

Optional frontmatter key `openspec:` may point at a host-repo OpenSpec change instead of duplicating a spec. See [docs/tools.md](../docs/tools.md).

## Body vs brain

- **Brain:** `brain/*` — process intelligence for this repo.
- **Body:** the rest of the tree. In this repository the body *is* the OS (docs, skills, templates). In a product repo the body is application code; ndxPPP files sit beside it.

## Invariants

- No runtime, CLI, or MCP server belongs in this repo unless constitution and this file are updated first.
- `.cursor/skills/` mirrors `skills/` (symlinks or identical copies). Canonical authoring path is `skills/`.
- Markdown in `brain/`, `docs/`, `profiles/`, `git/`, `templates/`, `work/**`, `README.md`, `AGENTS.md`, and `CLAUDE.md` carries OKF frontmatter with a non-empty `type:`. Skill `SKILL.md` files include `type: skill` in addition to Cursor `name` / `description`.
- This architecture complies with [constitution.md](constitution.md). Conflicts are resolved by the human editing one or both files.

## Vocabulary

- **Architect:** the human.
- **Current iteration:** lowest-numbered directory in `work/` excluding `archive/`.
- **Archive:** human move of that directory into `work/archive/`.
- **Profile:** overlay on the default review loop.
- **Git module:** overlay on how (or whether) agents touch git.
