---
type: spec
title: Iteration 0001 — Modernize ndxPPP into a personal agent OS
description: Collapse the 2025 pattern library into one OS with brain, work, skills, and docs as the product.
tags: [ndxppp, iteration]
---

# Iteration 0001 — Modernize ndxPPP into a personal agent OS

## Summary

Replace the v1 copy-paste pattern library (`_work/` + five pattern trees + ACME filler) with a single personal operating system: durable `brain/`, git-native `work/` timeline with human `archive/`, role Skills, thin profiles, human-gated git, and documentation strong enough to be the product. Dogfood the new loop in this folder.

## Goals

1. One canonical OS (Terence lineage) in the repo root; no pattern menu.
2. Split durable intelligence (`brain/`) from iteration state (`work/`).
3. Human sign-off via `work/archive/` (agents must not perform the move).
4. Progressive disclosure: short `AGENTS.md`, roles as Skills, brain loaded on demand.
5. OKF frontmatter (`type:` required) on brain, docs, profiles, git modules, templates, iteration artifacts, and skills.
6. Default profile **review**; default git **human-gated**.
7. OpenSpec documented as a peer; MCP documented as capabilities-not-memory; no MCP server.
8. Remove v1 trees after their ideas live in v2 files.

## Non-Goals

- Installing this OS into Sentinel, Ontos, or other product repos.
- Live EKG ingest, CLI, runtime, or CI.
- An ndxPPP MCP server.
- Agent auto-commit / auto-push / auto-tag as default.
- Keeping v1 `_work/` or underscore-lock as a supported dual convention.

## User Stories

- As the Architect, I want rails I can read in git so a new session does not invent requirements or skip review.
- As an agent, I want a short bootloader that tells me what to load when, and hard limits I must not cross.
- As a future host-repo user, I want an adopting guide that is copy-files-and-tailor, not a framework install.

## Technical Requirements

- Layout matches `brain/architecture.md`.
- Skills canonical in `skills/`; Cursor mirrors as symlinks in `.cursor/skills/`.
- Profiles: `review` (default), `solo`, `docs`.
- Git modules: `human-gated` (default), `feature-branch`, `stacked-diffs`, `iteration-semver` (opt-in).
- Templates for spec, plan, summary, completed, incomplete.
- Docs: philosophy, anatomy, workflow, roles, tools, ontology, adopting, evolving, anti-patterns, changelog.

## Implementation Constraints

- Markdown (and skill symlinks) only.
- Do not edit the Cursor plan file.
- Do not invent a status database; file-as-signal only.

## Success Criteria

- Root README and AGENTS.md describe v2, not the pattern menu.
- `brain/` describes ndxPPP, not ACME.
- `pattern-*` and `git-implementations/` are gone.
- Every intended markdown file has parseable frontmatter with non-empty `type:`.
- This iteration has spec, plan, and summary.

## Dependencies

- The v2 design (Architect-approved plan in Cursor).

## Validation Requirements

- Automated: scan markdown files for OKF `type:` (script or inline Python).
- Smoke: tree listing matches architecture; AGENTS.md hard limits present; archive rule documented in `work/README.md` and `brain/process.md`.

## File Structure Changes

- Add `brain/`, `work/`, `skills/`, `profiles/`, `git/`, `templates/`, `docs/`, `.cursor/skills/`, `AGENTS.md`, `CLAUDE.md`; rewrite `README.md`.
- Delete `pattern-basic/`, `pattern-standard/`, `pattern-adversarial/`, `pattern-terence/`, `pattern-tech-docs-rigor/`, `git-implementations/`.

## Integration Points

- Cursor skill auto-invocation via `.cursor/skills/` symlinks.
- Host repos via `docs/adopting.md` only.

## Future Considerations

- Run the OS on a real product repo (Sentinel/Ontos or similar) as a later iteration.
- EKG ingest of `brain/` + `docs/` + archived work.
