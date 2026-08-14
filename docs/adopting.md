---
type: guide
title: Adopting
description: How to copy this OS into another repository and tailor it.
tags: [ndxppp, adopting]
---

# Adopting

This OS is useful when a real project runs it. This repository is the source of the rails, not the only place they may live.

Do not vendor a runtime. Copy files, then take ownership.

## What to copy

Minimum:

1. `brain/` — you will rewrite mission, architecture, and most of constitution.
2. `skills/` — role contracts. Keep process links working or retarget them.
3. `templates/` — iteration skeletons.
4. `profiles/` and `git/` — or only the ones you declare.
5. An `AGENTS.md` snippet (below).
6. Optionally symlink `skills/` into `.cursor/skills/` (and `.claude/skills/` if you use Claude Code).

Do not copy this repo’s `docs/` unless you want the manual in the host. Linking here is enough.

Do not copy this repo’s `work/0001-modernize-v2/` — that iteration is about ndxPPP.

## AGENTS.md snippet

```markdown
## ndxPPP

- **Profile:** review
- **Git:** human-gated
- Brain: `brain/`
- Current iteration: lowest-numbered `work/NNNN-*` excluding `work/archive/`
- Roles: skills under `skills/ndxppp-*` (or `.cursor/skills/`)
- Agents do not archive. Human: `mv work/NNNN-slug work/archive/NNNN-slug`
- If work would violate `brain/constitution.md` or `brain/architecture.md`, update those files first.
```

Point at [brain/process.md](../brain/process.md) rather than restating the state machine.

## Tailor before the first iteration

Replace placeholder brain content (in a host repo you write *that product’s* mission and architecture; constitution keeps the gates and drops ndxPPP-specific doc laws you do not want).

Create `work/archive/` (empty is fine).

Create `work/0001-your-first-task/spec.md` — or ask Engineer to.

## OpenSpec hosts

If the repo already uses OpenSpec, keep it. Add `openspec: <change>` on the ndxPPP spec and use Foreman + archive as the acceptance gate. See [tools.md](tools.md).

## What not to do

- Do not keep v1 `_work/` and v2 `brain/`+`work/` in parallel “just in case.”
- Do not enable [iteration-semver](../git/iteration-semver.md) or agent-managed git unless you mean it.
- Do not install this into Sentinel/Ontos as a drive-by of some other task. Adopt it as its own iteration.
