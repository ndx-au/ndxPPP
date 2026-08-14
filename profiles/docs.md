---
type: protocol
title: Profile — docs
description: Writer/Editor overlay of the review loop for technical writing.
tags: [ndxppp, profile]
---

# Profile: docs

Same loop as [review](review.md). Names change. The body is documentation source.

## Overlay

| Review profile | Docs profile |
|---|---|
| Worker | **Tech Writer** (still use the Worker skill unless you duplicate it) |
| Foreman | **Editor** (Foreman skill) |
| Project body | `content/` or `docs/` as declared in the host architecture |
| Code validation | Doc validation |

## Extra laws (Editor-enforced)

- **Single source of truth.** Shared steps live in one place and are included, not copied.
- **Do not edit outside the documentation source** unless the spec says so (theme, config, build).
- **Sentence-per-line (SPL)** for long-form source that is meant to be diffed (AsciiDoc, or markdown you treat as source). One sentence per line.
- Broken cross-references are a critical failure.

## `summary.md` extras

Add under How to Validate (or a **Validation Performed** section):

- Cross-references checked.
- Build or lint command for the doc toolchain, or an explicit why-not.
- SPL used if the spec required it.

## When to use

Guides, runbooks, manuals, information-architecture work. Not a separate OS.

## Declare

```markdown
- **Profile:** docs
```
