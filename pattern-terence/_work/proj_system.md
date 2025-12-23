# SYSTEM PROTOCOL: ACME Hello World Landing Page Process + Environment

## 1. The Environment

- **Root:** `_work/` contains the brain (process docs, iteration folders).
- **Body:** Project root contains the product code.

### Development Setup (mandatory context)

- You are building a simple, generic **Hello World landing page** for **ACME**.
- The landing page should be runnable locally with minimal setup.
- Preferred feedback loop:
  - Run a lightweight local server (or open the HTML file directly if appropriate).
  - Validate with at least one automated command (see Testing Law).

## 2. Global State Detection

To determine project status, look at the **lowest numbered** folder in `_work/` that does **not** start with an underscore (e.g., `_work/0003-library-ui`).

Exceptional condition (requires human intervention):

- If the Current Iteration folder contains `completed.md`, the Foreman has approved the iteration but it has not been signed off.
- Agents MUST stop and request that the human signs off by renaming the folder with a leading underscore (e.g., `_work/_0003-library-ui/`).
- Agents MUST NOT proceed to a later iteration while this condition exists.
- While blocked, agents MUST include a sign-off request at the beginning of each response summary until the condition is resolved.

### The Signals

Inside that Current Iteration folder, the presence of specific files dictates the Global State:

1. **`spec.md` only:** State = **PLANNING** (Worker writes `plan.md`).
2. **`plan.md` exists:** State = **BUILDING** (Worker is executing).
3. **`summary.md` exists:** State = **REVIEW_PENDING** (Worker is done, waiting for Foreman).
4. **`incomplete.md` exists:** State = **REVISION_REQUIRED** (Foreman rejected work; Worker must fix).
5. **`completed.md` exists:** State = **DONE** (Foreman approved; Human signs off by archiving/underscore rename).

## 3. Core Laws (Immutable)

- **Constitution:** `_work/proj_constitution.md` applies to ALL code.
- **Mission:** `_work/proj_mission.md` applies to ALL design decisions.
- **Architecture:** `_work/proj_architecture.md` applies to ALL structure.

## 4. Testing Law (Project-appropriate)

Every iteration that affects code must include **at least one** Foreman-runnable automated validation command.

Acceptable examples:

- Static checks / tests (pick what's appropriate to the repo):
  - `npm test`
  - `npm run lint`
  - `python -m pytest`
  - `dotnet test`
  - `go test ./...`

Notes:

- If automated checks are genuinely not possible for an iteration, `plan.md` must explain why, and the Foreman should default to rejection unless the constraint is convincing.

## 5. Iteration Naming Convention

- Iteration folders must start with a 4-digit number, then a short slug.
  - Example: `_work/0001-scaffold-landing-page/`
- Each iteration folder must contain at least `spec.md`.

## 6. `summary.md` Contract (Required Format)

When the Worker is done, they must create `summary.md` in the Current Iteration folder.

`summary.md` must contain these sections (use headings exactly):

### Files Changed

- Bullet list of modified/added/deleted files.

### What Changed

- Short description of what was implemented and why.

### How to Validate

- Copy-pastable commands to run smoke checks/tests.
- **At least one automated command is mandatory.**

### Compliance Checklist

- `proj_constitution.md` followed
- `proj_architecture.md` respected
- No invented requirements beyond `spec.md`

### Product Checklist (when applicable)

- Page loads without errors (no broken imports/paths)
- No console errors on load (where applicable)
- Basic accessibility and content correctness (as specified)
- No tracking/analytics/network calls unless explicitly specced
