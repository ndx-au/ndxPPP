---
type: protocol
title: Git — iteration SemVer
description: Optional module. PATCH equals the last archived iteration number. Not the default.
tags: [ndxppp, git]
---

# Git protocol: iteration SemVer

Opt-in. Used in v1 Terence. **Not default.** Only enable if you want tags to track signed-off iterations.

Requires a human (or an explicit agent-managed-git override) to create tags. Combine with [human-gated](human-gated.md) or [feature-branch](feature-branch.md).

## Version

Tags: `vMAJOR.MINOR.PATCH`.

- `MAJOR.MINOR` are human-controlled.
- `PATCH` equals the highest archived iteration number (`work/archive/NNNN-*` → `NNNN` as integer).

Keep one version source of truth (`VERSION`, `package.json`, or equivalent) aligned with the tag.

## Preflight (when entering a new iteration)

1. Highest `work/archive/NNNN-*` → `PATCH`.
2. Read `MAJOR.MINOR` from the version file.
3. If tag `vMAJOR.MINOR.PATCH` is missing, **propose** (do not silently run): bump the version file, annotated tag, push tag — only after the working tree reflects that archived iteration.

If nothing is archived yet, skip.

## Worker commits

Still follow the active write policy. Suggested messages:

- `feat(NNNN): implementation for review`
- `fix(NNNN): addressed foreman feedback`
- `chore(release): bump version to MAJOR.MINOR.PATCH`

## Foreman

Does not tag.

## Declare

```markdown
- **Git:** human-gated
- **Git extra:** iteration-semver
```
