---
type: guide
title: Changelog
description: Honest account of ndxPPP v1 (December 2025) to v2 (August 2026).
tags: [ndxppp, changelog]
---

# Changelog

## v2 — August 2026

Personal operating system for agent work. Documentation is the product. The copy-paste pattern library is gone.

### Kept

- Durable brain: constitution, mission, architecture, process.
- File-as-signal iteration loop, including Foreman `incomplete.md` / `completed.md`.
- Human sign-off as a hard gate.
- Structural integrity: update constitution or architecture before violating them.
- Multi-role posture from the Terence pattern (Architect / Engineer / Worker / Foreman / Operator).
- Git strategy as a swappable module.

### Changed

- **One OS, not five patterns.** Basic, Standard, Adversarial, Terence, and Tech-Docs-Rigor collapsed into this tree plus thin [profiles](../profiles/review.md).
- **`brain/` and `work/` split.** v1 mixed process docs and iteration folders in `_work/`. Brain is durable; work is the timeline.
- **`work/archive/` instead of underscore-lock.** v1 renamed `0001-foo` → `_0001-foo`. That collided with “hidden” conventions and made globs awkward. The human still performs a folder move; agents still must not.
- **Progressive disclosure.** Agents read [AGENTS.md](../AGENTS.md) always, then the skill and brain files the turn needs. They do not ingest the whole brain every session.
- **Human-gated git is the default.** The Terence template auto-committed, pushed, and tagged (`PATCH` = last signed-off iteration). That fights how this machine is actually used. Agent-managed git is now an opt-in module.
- **OKF frontmatter** on brain, docs, and iteration artifacts (`type:` required) so the corpus is EKG-ingestible later. No live graph in this repo.
- **OpenSpec is a peer.** Iterations may point at an OpenSpec change instead of duplicating a spec. ndxPPP does not replace OpenSpec and does not require it.

### Removed

- ACME Hello World as the example product. This repo’s brain describes ndxPPP.
- Four duplicated `_work/` trees and `git-implementations/` as a parallel copy kit.
- Auto-commit / auto-push / auto-tag as default protocol.
- “Coming soon: git-flow”.
- Landing-page-specific Engineer chapters.
- Open-source “scientific inquiry / pick a pattern” framing.

### Why the underscore-lock became `archive/`

The leading underscore was a clever digital signature: only the human renamed the folder, and agents treated `_NNNN-*` as immutable history. It worked. It was also easy to miss in listings, easy to confuse with ignored files, and heavier than the archive folder every adjacent tool (including OpenSpec) already uses.

The gate is the same. The move is `work/NNNN-slug/` → `work/archive/NNNN-slug/`.

## v1 — December 2025

Passive Prompt Patterns. Five copy-paste patterns (`pattern-basic`, `pattern-standard`, `pattern-adversarial`, `pattern-terence`, `pattern-tech-docs-rigor`), a shared `_work/` anatomy, numbered iterations, underscore-lock sign-off, and swappable git modules. Built in a concentrated burst and parked. It predated the mainstreaming of `AGENTS.md` / Skills; the process layer did not.
