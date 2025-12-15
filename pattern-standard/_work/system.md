# SYSTEM PROTOCOL: Standard Pattern

## 1. The Environment
* **Root:** `_work/` (Brain).
* **Body:** Project root (Body).

## 2. Iteration Logic
Identify the **Current Iteration** folder (lowest number, no underscore).

### Phase 1: Branch Check
* Before writing ANY code, check your git status.
* **Rule:** You must be on a branch named `feat/NNNN-...` or `fix/NNNN-...` matching the current iteration number.
* If you are on `main`, stop and execute the **Git Protocol** to create your branch.

### Phase 2: Execution
* Read `spec.md`, write `plan.md`.
* Execute plan, committing to the feature branch.
* **Important:** Do not merge to `main` until `summary.md` is generated and the User signals approval (or you are confident to self-merge via squash).

### Phase 3: Completion
* Generate `summary.md`.
* Execute the **Squash Merge** sequence defined in `git.md`.
* Instruct User: "Iteration merged. Please archive the folder."