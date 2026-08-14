---
type: guide
title: Anatomy
description: What each part of the ndxPPP tree is for, and when an agent should load it.
tags: [ndxppp, anatomy]
---

# Anatomy

ndxPPP is a handful of directories with strict jobs. Humans start at [README.md](../README.md). Agents start at [AGENTS.md](../AGENTS.md).

## Brain vs body

- **Brain** (`brain/`) — durable project intelligence: law, why, success state, process. Never gitignored. Edited when the *rules* change, not when a feature ships.
- **Body** — everything the brain is about. In a product repo that is application code. In *this* repo the body is the OS itself (docs, skills, templates).

Work state is neither brain nor body. It is the **timeline** (`work/`).

## The pieces

| Path | Audience | Job |
|---|---|---|
| `AGENTS.md` | Agents | Always-on bootloader: profile, git module, when to load what, hard limits |
| `CLAUDE.md` | Claude Code | Pointer at `AGENTS.md` |
| `README.md` | Humans | Why, 60-second start, map |
| `brain/constitution.md` | Both | Immutable laws |
| `brain/mission.md` | Both | Why this project exists |
| `brain/architecture.md` | Both | Target success-state structure |
| `brain/process.md` | Both | State machine and artifact contracts |
| `work/NNNN-slug/` | Both | One unit of work; file-as-signal |
| `work/archive/` | Humans write; agents read | Signed-off history |
| `skills/` | Agents | Role contracts (canonical) |
| `.cursor/skills/` | Cursor | Symlinks to `skills/` for auto-invocation |
| `profiles/` | Both | Overlays on the default loop |
| `git/` | Both | Swappable save protocol |
| `templates/` | Agents | Skeletons for iteration files |
| `docs/` | Humans (Operator when repairing) | The manual |

## Progressive disclosure

Do not load the whole tree every turn.

```
AGENTS.md
    ├─ constitution          (if you will change files)
    ├─ process               (if you will start, advance, or review work)
    ├─ mission + architecture (if you are scoping or the request smells like a structural conflict)
    └─ one role skill        (when that role is invoked or implied)
```

Skills point at the brain. They do not replace it. Conflict → brain wins → fix the skill.

## What v1 called `_work/`

v1 kept brain files and iteration folders in one `_work/` directory and archived by renaming `0001-foo` to `_0001-foo`. v2 splits **brain** (durable) from **work** (timeline) and archives by moving into `work/archive/`. Same gate, clearer glob. See [changelog.md](changelog.md).
