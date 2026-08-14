---
type: reference
title: Engineer spec reference
description: Spec template, quality bar, and iteration types for the Engineer role.
tags: [ndxppp, role]
---

# Engineer reference

## Spec structure

```markdown
---
type: spec
title: Iteration NNNN — Title
description: One-line summary.
tags: [ndxppp, iteration]
openspec: optional-change-name
---

# Iteration NNNN — Title

## Summary
One paragraph: what this iteration delivers and why it matters.

## Goals
Numbered, specific objectives.

## Non-Goals
Explicit boundaries for this iteration.

## User Stories
As a <user>, I want <action> so that <benefit>. Omit if not useful.

## Technical Requirements
Per-feature requirements, edge cases, constraints.

## Implementation Constraints
Limits, compatibility, performance. Not a play-by-play of the patch.

## Success Criteria
Testable conditions.

## Dependencies
What must already exist.

## Validation Requirements
How Foreman will verify, including automated checks.

## File Structure Changes
Expected adds/edits/deletes.

## Integration Points
How this connects to what already exists.

## Future Considerations
Out of scope, recorded so they are not smuggled in.
```

## Quality bar

A spec is done when it is unambiguous, scoped, testable, and actionable without a second discovery pass.

Fix before handoff: vague verbs (“handle”, “support”), missing error cases, no validation path, assumed knowledge not in the spec, scope that bleeds into the next iteration.

## Iteration types

- **Feature** — user workflow, entry/exit, success criteria.
- **Bug fix** — reproduce, expected vs actual, regression check.
- **Refactor** — no behavior change; tests that prove equivalence.
- **Docs / process** — which files are source of truth; what “accurate” means.
- **Infrastructure** — impact, compatibility, rollback if relevant.

## Other roles

- Human approves the spec.
- Worker plans from it and may ask questions; answer in-role without rewriting history silently — edit `spec.md` if the human agrees.
- Foreman verifies against success criteria you wrote. Unclear specs get rejected; learn from that.
