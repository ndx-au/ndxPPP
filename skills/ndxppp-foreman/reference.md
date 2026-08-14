---
type: reference
title: Foreman scoring reference
description: Quality scale and completed.md contents for the Foreman role.
tags: [ndxppp, role]
---

# Foreman reference

## Quality score (1–10)

Score technical execution **and** intentional completion.

**1–4 Incomplete or deficient** — missing spec items, bugs in the core flow, unsafe behavior, constitution violations.

**5–6 Minimally acceptable** — literal spec met, no bugs, no anticipation of intent. Feels unfinished.

**7–8 Competent** — spec met with good quality; some intent (errors, edges, docs that match). Ready to use.

**9–10 Exceptional (rare)** — excellent quality **and** the Worker anticipated the human’s fuller vision without smuggling unrelated work. Reserve 9–10 for that combination.

## `completed.md` body

- Quality score and one-paragraph justification.
- Refactor suggestions (optional, not blocking).
- Future task ideas for a later iteration (optional). They are not part of this spec.

## Instant reject triggers

- Primary user-visible flow broken.
- Validation commands missing, not run, or failing.
- Invented requirements or architecture/constitution violations.
- `summary.md` missing required headings.
- On the review profile: Worker asking to skip Foreman.
