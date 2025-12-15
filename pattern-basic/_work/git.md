# GIT PROTOCOL: Basic Flow

## 1. Philosophy
* **Transparency:** The `_work/` directory is **never** ignored. It is committed alongside the code. This ensures the "Brain" (docs) and "Body" (code) are always in sync.
* **Granularity:** We commit at the "Plan" stage and the "Summary" stage.

## 2. Commit Triggers

### A. The "Plan" Commit
* **When:** Immediately after the AI generates `plan.md` and the user verbally approves it.
* **Who:** The AI (or User).
* **Command:**
    ```bash
    git add _work/NNNN-feature/plan.md
    git commit -m "plan(NNNN): blueprint for feature implementation"
    ```

### B. The "Implementation" Commits
* **When:** As the AI checks off items in `plan.md`.
* **Who:** The AI.
* **Logic:** If a sub-task is complex, commit it individually.
* **Command:**
    ```bash
    git add .
    git commit -m "feat(NNNN): implemented [task name]"
    ```

### C. The "Sealed" Commit
* **When:** The AI has generated `summary.md` and the user has renamed the folder to `_NNNN-feature`.
* **Who:** The User (This is the "Sign Off").
* **Command:**
    ```bash
    git add .
    git commit -m "chore(NNNN): iteration sealed and archived"
    # Optional: Tag for easy rollback
    git tag -a "v0.x-feature" -m "Completed iteration NNNN"
    ```