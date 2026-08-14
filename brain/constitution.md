---
type: constitution
title: Constitution
description: Immutable laws for agents and humans working in this repository.
tags: [ndxppp, brain]
---

# Constitution

These laws apply to every iteration. If a request would violate them, stop. Ask the Architect (human) to update this file or [architecture.md](architecture.md) first, then continue under the new text.

## Laws

1. **Do not invent requirements.** Implement the current iteration’s spec (or the OpenSpec change it points at). Ambiguity is a question, not a license.
2. **Smallest safe change.** Prefer the edit that satisfies the spec without extra architecture, dependencies, or drive-by refactors.
3. **Structural integrity.** [architecture.md](architecture.md) must not contradict this constitution. Work that needs a different structure updates architecture (and this file if needed) *before* the code or docs change.
4. **Human git gate.** Follow the active git module. This repo’s default is [human-gated](../git/human-gated.md): do not `git commit`, `git push`, or tag unless the human asks. Propose a message instead.
5. **Human archive gate.** Agents never move or rename an iteration into [work/archive/](../work/README.md). Only the human signs off.
6. **No silent product claims.** Documentation that describes this OS must match the files that exist. If you change layout or contracts, update the docs in the same iteration.
7. **Secrets stay out.** Do not commit credentials, tokens, or private host specifics that do not belong in a public-ish process repo.

## Quality bar (Foreman-enforced)

- Spec satisfied; no extra features.
- At least one automated validation command was run, or `summary.md` explains why none can exist and the Foreman finds that convincing.
- Constitution and architecture still hold after the change.
- Iteration artifacts use the contracts in [process.md](process.md).

## Relationship to other brain files

- [mission.md](mission.md) is the why. It does not override these laws.
- [architecture.md](architecture.md) is the success-state blueprint. It defers here on safety and process.
- [process.md](process.md) is the state machine. It may not weaken laws 4–6.
