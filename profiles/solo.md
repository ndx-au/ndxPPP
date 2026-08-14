---
type: protocol
title: Profile — solo
description: Overlay for throwaway work. Foreman is on demand.
tags: [ndxppp, profile]
---

# Profile: solo

Speed is the priority. The state machine still exists. The critic is optional.

## Overlay

- After `summary.md`, the Worker may request human sign-off **without** `completed.md`.
- Human may still invoke Foreman. If they do, Foreman files apply as in [review](review.md).
- Plan approval still waits for the human. Archive is still human-only.
- Inventing requirements is still forbidden.

## When to use

Prototypes, scripts, one-off tools, spikes you expect to delete. Not for anything with a constitution you care about.

If solo work graduates into a real project, switch the `AGENTS.md` line to **review** and run Foreman on the next iteration.

## Declare

```markdown
- **Profile:** solo
```
