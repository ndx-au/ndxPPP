---
type: protocol
title: Git — feature branch
description: Optional module. One short-lived branch per iteration; squash merge after approval.
tags: [ndxppp, git]
---

# Git protocol: feature branch

Opt-in. `main` stays deployable. One branch per iteration.

This module **does not** waive [human-gated](human-gated.md) unless the host `AGENTS.md` says agents may run git writes. Default: propose the commands; the human runs them. If the host explicitly allows agent-managed git, the Worker may execute the same steps.

## Branch name

`feat/NNNN-slug` or `fix/NNNN-slug`, matching the iteration folder.

## Worker

**Setup (start of BUILDING):** on up-to-date `main`, create/checkout `feat/NNNN-slug`.

**Commits:** conventional messages, scoped to the plan. Push the branch only if the human asked, or if agent-managed git is on.

**Do not merge to `main`.** Merge happens after Foreman `completed.md` (review profile) or after human say-so (solo).

## Foreman

Review on the branch. Do not merge. Do not commit.

## Merge (human, or agent if explicitly allowed)

After `completed.md` (review) and before or after archive, as the human prefers:

```bash
git checkout main
git pull
git merge --squash feat/NNNN-slug
git commit -m "feat(NNNN): <summary headline>"
git push origin main
git branch -d feat/NNNN-slug
```

## Declare

```markdown
- **Git:** feature-branch
```
