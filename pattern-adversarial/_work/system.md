# SYSTEM PROTOCOL: Shared Physics (Adversarial Pattern)

## 1. The Environment
* **Root:** `_work/` contains the brain (docs/state).
* **Body:** Project root contains the code.

## 2. Global State Detection
To determine the project status, look at the **lowest numbered folder** in `_work/` that does **not** start with an underscore (e.g., `0003-auth`).

### The Signals
Inside that Current Iteration folder, the presence of specific files dictates the Global State:

1.  **`spec.md` only:** State = **PLANNING** (Worker needs to write `plan.md`).
2.  **`plan.md` exists:** State = **BUILDING** (Worker is executing).
3.  **`summary.md` exists:** State = **REVIEW_PENDING** (Worker is done, waiting for Foreman).
4.  **`incomplete.md` exists:** State = **REVISION_REQUIRED** (Foreman rejected work; Worker must fix).
5.  **`completed.md` exists:** State = **DONE** (Foreman approved; User must archive folder).

## 3. Core Laws (Immutable)
* **Constitution:** `_work/constitution.md` applies to ALL code.
* **Mission:** `_work/mission.md` applies to ALL design decisions.
* **Architecture:** `_work/architecture.md` applies to ALL structure.