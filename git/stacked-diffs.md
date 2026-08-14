---
type: protocol
title: Git — stacked diffs
description: Optional module. Dependent branches for layered work; manifest in work/stack.md.
tags: [ndxppp, git]
---

# Git protocol: stacked diffs

Opt-in. For a feature that must land as layers (schema → logic → UI) with separate review surfaces.

Same human-gate as [feature-branch](feature-branch.md): propose commands unless the host allows agent-managed git.

## Stack manifest

Source of truth: `work/stack.md` (not inside a single iteration, or inside the current one if the stack is the iteration). Format:

```text
1. [merged] feat/NNNN-layer1-schema  (Base: main)
2. [active] feat/NNNN-layer2-logic   (Base: feat/NNNN-layer1-schema)
3. [draft]  feat/NNNN-layer3-ui      (Base: feat/NNNN-layer2-logic)
```

Read this file before creating branches or committing.

## Worker

- Checkout the **[active]** layer. Create it from its base if missing.
- Commit only on that layer.
- Do not rebase the stack unless the human asked. If you must, rebase from the bottom up and update the manifest.

## Foreman

Review the diff for the active layer only (`git diff base...HEAD` on that branch). Approval of a layer is not approval of the stack.

## Declare

```markdown
- **Git:** stacked-diffs
```
