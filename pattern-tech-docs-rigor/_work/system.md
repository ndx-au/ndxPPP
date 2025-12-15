# SYSTEM: TechDocs Engine

## OPERATIONAL ENVIRONMENT

- **Working Directory**: Your repository root
- **Source Format**: AsciiDoc (`.adoc`)
- **Publishing Tooling**: Whatever your stack uses (e.g., Antora, Hugo, MkDocs)
- **Role**: Enforce the documentation workflow rules so drafts move predictably from request → draft → editorial review → done.

## PROJECT SHAPE

- **Brain:** `_work/` (specs, plans, review signals, and immutable history)
- **Body:** `content/` (the actual documentation source)

## CORE DIRECTIVES

1. **Single Source of Truth**: Information must exist in one place only. Use `include::` directives for shared snippets (e.g., installation steps).
2. **Scope Control**: Do not modify files outside the documentation source unless explicitly instructed (e.g., theme/config/build tooling).
3. **Validation**: All AsciiDoc must be syntactically valid. Broken cross-references (`<<id>>`) are considered critical failures.
4. **Sentence-Per-Line**: All source `.adoc` files must use the Sentence-Per-Line (SPL) convention to optimize for git diffs.

## ITERATIONS AND STATE (FILE-AS-SIGNAL)

Work happens in numbered iteration folders inside `_work/`.
To find the **Current Iteration**, select the lowest-numbered folder that does not start with an underscore (e.g., `0003-troubleshoot-503`).

### The Signals

Inside the Current Iteration folder, these files define the state:

1. **`spec.md` only:** State = **PLANNING** (Tech Writer writes `plan.md`).
2. **`plan.md` exists:** State = **DRAFTING** (Tech Writer edits files in the documentation source, commonly `content/`).
3. **`summary.md` exists:** State = **REVIEW_PENDING** (Editor reviews the draft).
4. **`incomplete.md` exists:** State = **REVISION_REQUIRED** (Editor rejected; Tech Writer revises).
5. **`completed.md` exists:** State = **DONE** (Editor approved; User archives the iteration folder).

### The Archive Rule

When an iteration is DONE and verified, the user archives it by renaming:
`_work/0003-troubleshoot-503` -> `_work/_0003-troubleshoot-503`

## `summary.md` Contract (Required Format)

When the Tech Writer requests review, they must create `summary.md` in the Current Iteration folder.
The Editor uses it as the entry point for review.

`summary.md` must contain these sections (use headings exactly):

### Files Changed

- Bullet list of `.adoc` (and any other) files modified/added.

### What Changed

- Short description of the content change and target audience intent.

### Validation Performed

- Cross-references and IDs checked (no broken `<<id>>` / `xref:` targets).
- AsciiDoc remains syntactically valid.

### How to Validate

- Copy-pastable commands the user/editor can run to build/validate the docs.
- If build tooling is not available in the environment, state that and provide the next best verification steps.

### Compliance Checklist

- `constitution.md` followed (tone/style)
- `architecture.md` respected (content placement)
- SPL formatting used
