# Git Strategy: Feature Branch (Standard)

## Overview
The **Feature Branch** strategy (GitHub Flow) is the industry standard for most teams.
* **Rule:** `main` is always deployable.
* **Process:** We create a short-lived branch for every iteration, and we only merge back to `main` via a Pull Request (PR) or a specific merge command after the Foreman approves.

---

## 1. The Protocol (Copy-Paste this)

To adopt this strategy, create `_work/git.md` and paste the following content into it.

````markdown

# GIT PROTOCOL: Feature Branch

## 1. Branch Naming Convention
* **Format:** `feat/NNNN-description` or `fix/NNNN-description`.
* **Example:** `feat/0004-add-login`

## 2. Worker Protocols (The Builder)

### Phase A: Setup
**Trigger:** Start of an iteration.
**Action:**
1. Ensure you are on `main` and up to date.
    * `git checkout main && git pull origin main`
2. Create your feature branch.
    * `git checkout -b feat/NNNN-name`

### Phase B: Committing
**Trigger:** Completion of a task in `plan.md`.
**Action:**
1. Commit with a conventional message.
    * `git commit -am "feat: implement user schema"`
2. Push to origin (so remote backup exists).
    * `git push -u origin feat/NNNN-name`

## 3. Foreman Protocols (The Reviewer)

### Phase A: The Audit
**Trigger:** When `summary.md` is generated.
**Action:**
1. You review the code **inside the branch**.
2. If changes are needed, you update `incomplete.md`. The Worker continues on this same branch.

### Phase B: The Merge
**Trigger:** When you generate `completed.md`.
**Action:**
1. Checkout `main`.
2. Merge the feature branch (Squash is preferred to keep history clean).
    * `git merge --squash feat/NNNN-name`
3. Commit the squash.
    * `git commit -m "feat(NNNN): completed iteration"`
4. Push `main`.
    * `git push origin main`
5. Delete the local feature branch.
    * `git branch -D feat/NNNN-name`

````