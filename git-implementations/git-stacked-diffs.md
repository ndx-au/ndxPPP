# Git Strategy: Stacked Diffs

## Overview
The **Stacked Diffs** strategy is designed for complex features that need to be broken down into smaller, dependent units of work. Instead of a single massive "Feature Branch," we create a vertical stack of branches where each layer depends on the one below it.

**The Stack:**
3. `feat/ui` (Top: The Button)
2. `feat/api` (Middle: The Endpoint)
1. `feat/schema` (Bottom: The Database)

This strategy allows for faster code reviews (reviewing just the schema vs. the whole app) and parallel development.

---

## 1. The Protocol (Copy-Paste this)

To adopt this strategy, create `_work/git.md` and paste the following content into it.

```markdown
# GIT PROTOCOL: Stacked Diffs

## 1. The Stack Manifest
The "Source of Truth" for our branching structure is `_work/stack.md`.
* **Rule:** You must read this file before creating branches or committing code.
* **Format:**
    ```text
    1. [merged] feat/NNNN-layer1-schema (Base: main)
    2. [active] feat/NNNN-layer2-logic  (Base: feat/NNNN-layer1-schema)
    3. [draft]  feat/NNNN-layer3-ui     (Base: feat/NNNN-layer2-logic)
    ```

## 2. Worker Protocols (The Builder)

### Phase A: Branch Selection
**Trigger:** Start of a task.
**Action:**
1. Read `_work/stack.md`.
2. Identify the **[active]** layer.
3. Checkout that branch.
    * *Command:* `git checkout feat/NNNN-layer2-logic`
    * *If it doesn't exist:* `git checkout -b feat/NNNN-layer2-logic feat/NNNN-layer1-schema` (Create it from its BASE).

### Phase B: Committing
**Trigger:** Completion of a sub-task in `plan.md`.
**Action:**
1. Check that you are on the correct branch.
2. Commit with scope.
    * *Command:* `git commit -am "feat(layer2): [description of work]"`

## 3. Foreman Protocols (The Maintainer)

### Phase A: The "Restack" (Rebasing)
**Trigger:** If the User or Reviewer modifies a lower layer (e.g., Layer 1 changed).
**Action:** You must update the dependent layers.
1. Checkout the active layer.
2. Rebase onto the base layer.
    * *Command:* `git rebase feat/NNNN-layer1-schema`
3. Resolve conflicts (ask User if unsure).
4. Force push the update.
    * *Command:* `git push origin HEAD --force-with-lease`

### Phase B: The Hand-Off
**Trigger:** When `summary.md` is generated for a layer.
**Action:**
1. Update `_work/stack.md` to mark the current layer as `[pending_review]`.
2. Push the branch.
    * *Command:* `git push -u origin HEAD`