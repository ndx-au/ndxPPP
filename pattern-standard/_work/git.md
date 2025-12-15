# GIT PROTOCOL: Standard Flow (Feature Branches)

## 1. Philosophy
* **Safety First:** We never commit directly to `main`.
* **Atomic History:** We squash feature branches into single, clean commits on `main`.

## 2. The Workflow
1.  **Start:** Checkout `main`, pull, create `feat/NNNN-name`.
2.  **Work:** Commit frequently to the branch (save points).
3.  **Finish:** Squash merge to `main`, delete branch.

## 3. Worker Protocols
* **Trigger (Plan Approved):** `git checkout -b feat/NNNN-name main`
* **Trigger (Task Done):** `git commit -am "feat: ..."`
* **Trigger (Iteration Done):**
    1. `git checkout main`
    2. `git merge --squash feat/NNNN-name`
    3. `git commit -m "feat(NNNN): completed iteration"`
    4. `git branch -D feat/NNNN-name`