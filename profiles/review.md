---
type: protocol
title: Profile — review
description: Default overlay. Foreman must approve before human sign-off.
tags: [ndxppp, profile]
---

# Profile: review

**Default for this OS.** Accuracy over speed. The critic loop is the point.

## Overlay

- After `summary.md`, state is **REVIEW_PENDING**. Worker stops.
- **Foreman is required.** Human sign-off is invalid (agents must refuse to treat the iteration as done) until `completed.md` exists.
- `incomplete.md` returns the Worker to revision. Foreman re-audits after `incomplete.md` is deleted.
- Prefer a same-session Foreman. Use a fresh `code-reviewer` / `security-review` subagent when the human asks for a hard review.

## When to use

Daily driver. Anything you will live with. Anything that can drift the architecture.

## Declare

In `AGENTS.md`:

```markdown
- **Profile:** review
```
