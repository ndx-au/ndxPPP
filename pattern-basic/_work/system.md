# SYSTEM PROTOCOL: Passive Prompt Pattern (NDX-PPP)
This file is the bootloader for agents.

## 1. The Environment
You are operating within an **NDX Passive Prompt Pattern** repository.
Your "Brain" is located in the `_work/` directory.
The "Body" (the actual codebase) lives in the project root, outside of `_work/`.

## 2. Directory Structure & State
The state of this project is strictly defined by the folder structure within `_work/`.

### The Global Context (Read-Only)
* `_work/constitution.md`: **The Law.** Hard rules on coding style, safety, and ethics.
* `_work/mission.md`: **The Soul.** The high-level vision and creative values.
* `_work/system.md`: **The Manual.** This file.

### The Timeline (Iterations)
Work is divided into discrete "Iterations". Each iteration is a folder inside `_work/`.

* **Active Iterations:** Format `NNNN-feature-name` (e.g., `0002-auth-login`).
* **Completed Iterations:** Format `_NNNN-feature-name` (e.g., `_0001-setup`).

**CRITICAL LOGIC:**
To find your current task, look at the folders in `_work/`.
1.  Ignore any folder starting with an underscore `_`.
2.  Sort the remaining folders numerically.
3.  **The folder with the lowest number is the CURRENT_ITERATION.**
4.  All folders starting with `_` represent **Immutable History** and should be treated as read-only context.

## 3. The Workflow Loop
When you are activated, perform this routine:

### Phase 1: Context Loading
1.  Identify the **CURRENT_ITERATION** folder (e.g., `_work/0005-add-search`).
2.  Read `_work/constitution.md` and `_work/mission.md`.
3.  Read the `spec.md` inside the **CURRENT_ITERATION** folder.
4.  *(Optional)* Read the `future_tasks.md` from the *previous* iteration (the highest numbered folder starting with `_`) for continuity.

### Phase 2: Planning (The Brain)
1.  If `plan.md` does not exist in **CURRENT_ITERATION**, generate it based on the `spec.md`.
2.  The plan must outline step-by-step changes to the codebase.
3.  **Wait for User Approval** of the plan before editing code.

### Phase 3: Execution (The Body)
1.  Execute the steps in `plan.md`.
2.  Update `plan.md` (checking off items) as you progress.
3.  All code changes happen in the **Project Root**, not inside `_work/` (unless editing the workflow itself).

### Phase 4: Termination
1.  Once the `spec.md` is satisfied:
2.  Generate `_work/CURRENT_ITERATION/summary.md` (what changed).
3.  Generate `_work/CURRENT_ITERATION/future_tasks.md` (what was skipped/deferred).
4.  **Instruction to User:** "Iteration complete. Please rename `_work/0005-add-search` to `_work/_0005-add-search` to archive it."