# Git Implementation Modules

## Overview
This directory contains modular **Version Control Protocols** designed to plug into any Passive Prompt Pattern (Basic, Adversarial, etc.).

Since different teams have different Git workflows (Trunk-based, Git Flow, Stacked Diffs), we decouple the "Coding Logic" (Worker/Foreman) from the "Saving Logic" (Git).

## How to Use
1.  **Choose a Strategy** below that matches your team's workflow.
2.  **Copy** the file to your project's `_work/` directory.
3.  **Rename** it to `git.md`.
4.  **Update** your `worker.md` or `foreman.md` to reference it (most patterns do this by default).

---

## Available Strategies

### 1. `git-feature-branch.md` (Standard)
* **Best for:** Most teams and professional workflows.
* **Workflow:** One short-lived branch per iteration, merge back via PR / squash merge.

### 2. `git-stacked-diffs.md` (Advanced)
* **Best for:** Complex features, Senior/Junior pairings, High-velocity teams.
* **Workflow:** Breaks large features into a "Stack" of dependent branches (e.g., Schema -> Backend -> UI).
* **Trigger:** The AI manages `_work/stack.md` to keep branches rebased and synchronized.
* **Requires:** A higher context window, as the AI must understand branch dependencies.

## Planned Strategies

### `git-flow.md` (Traditional)
* **Best for:** Enterprise environments with strict release cycles.
* **Workflow:** Feature branches (`feat/xxx`) merging into `develop`.
* *(Coming Soon)*