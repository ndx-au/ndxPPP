# ndxPPP: Passive Prompt Patterns

**Sustainable, State-Based Workflows for AI-Assisted Engineering**

## 1\. Abstract

**ndxPPP** (Passive Prompt Patterns) is an open-source methodology for maintaining context, intent, and architectural integrity in AI-assisted software projects.

It proposes a shift away from "Active" agent frameworks (which hide state in temporary chat windows or proprietary databases) toward a **File-System-Centric** approach. By encoding the project's state, rules, and mission into standardized, passive text files, we create workflows that are:

1.  **Tool Agnostic:** Works with `opencode`, Cursor, Windsurf, or raw LLM APIs.
2.  **Context-Rot Resistant:** History is preserved in the repo, not the chat session.
3.  **Human-Gated:** The AI is the engine; you are the steering wheel.

-----

## 2\. The Pattern Menu

Choose the workflow that matches your team size and risk tolerance.

| Pattern | Complexity | Safety | Git Strategy | Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **[Basic](https://www.google.com/search?q=./pattern-basic)** | ⭐ | ⭐ | Trunk-Based | **Prototyping / Scripts.** Speed is the priority. Great for solo MVPs. |
| **[Standard](https://www.google.com/search?q=./pattern-standard)** | ⭐⭐ | ⭐⭐⭐ | Feature Branch | **Daily Driver.** The industry standard. Safe, clean history, professional hygiene. |
| **[Adversarial](https://www.google.com/search?q=./pattern-adversarial)** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Any | **High Assurance.** Two agents (Worker + Foreman). Use for crypto, payments, or security-critical code. |

-----

## 3\. The Core Anatomy

Regardless of which pattern you choose, every `ndxPPP` project relies on a strict separation between "Thinking" and "Doing."

### A. The "Brain" (`_work/`)

This folder contains the project's intelligence. **It is never `.gitignore`'d.**

  * **`_work/system.md`:** The "Operating System." Teaches the AI how to navigate folders.
  * **`_work/constitution.md`:** The "Law." Immutable negative constraints (e.g., "No external deps").
  * **`_work/mission.md`:** The "Soul." High-level values and "vibe" (e.g., "Speed is a feature").
  * **`_work/architecture.md`:** The "Blueprint." The definition of the final Success State.

### B. The "Body" (Project Root)

The root directory contains your actual source code. The AI reads from the **Brain** to decide how to modify the **Body**.

-----

## 4\. The Workflow Loop

Work is broken into discrete units called **Iterations**. Each iteration lives in a numbered folder inside `_work/`.

### 1\. The Seed (Human)

You create a new folder `_work/0005-add-search/` and add a `spec.md`.

> *Note:* You define the requirement. The AI does not invent work.

### 2\. The Execution (AI)

The AI reads the spec, creates a `plan.md`, and implements the code. It iterates until it produces a `summary.md`.

### 3\. The Sign-Off (Human)

**This is the most critical step.** The AI cannot "finish" an iteration; only you can.

1.  **Review:** You check the `summary.md` and the code.
2.  **Approve:** You rename the folder from `0005-add-search` to `_0005-add-search`.

**The Leading Underscore `_`:**
This is your digital signature. It signals to the AI: *"This context is now Immutable History. Do not attempt to fix it. Move on."*

-----

## 5\. Detailed Pattern Breakdown

### `📂 pattern-basic/` (The Speedboat)

  * **Roles:** Single Agent.
  * **Logic:** Reads Spec → Writes Code → Commits to Main.
  * **Ideal for:** Hackathons, scripts, one-off tools.

### `📂 pattern-standard/` (The Sedan)

  * **Roles:** Single Agent.
  * **Logic:** Reads Spec → **Creates Branch** → Writes Code → **Squash Merge**.
  * **Ideal for:** Most professional software projects. Keeps `main` clean and deployable.

### `📂 pattern-adversarial/` (The Tank)

  * **Roles:** Dual Agents (**Worker** & **Foreman**).
  * **Logic:**
    1.  **Worker** builds and submits `summary.md`.
    2.  **Foreman** audits code against the `constitution.md`.
    3.  If flaws are found, Foreman creates `incomplete.md`.
    4.  Worker must fix issues to delete `incomplete.md`.
  * **Ideal for:** Teams where accuracy matters more than speed.

-----

## 6\. Modular Git Strategies

While the patterns come with defaults, you can swap the **Version Control Protocol** by copying a file from `git-implementations/` into your `_work/` folder and renaming it to `git.md`.

  * **`git-trunk.md`:** Direct commits to main.
  * **`git-feature-branch.md`:** (Standard) Branch per iteration, squash merge.
  * **`git-stacked-diffs.md`:** (Advanced) For managing chains of dependent branches (Layer 1 -\> Layer 2 -\> Layer 3).

-----

## 7\. Usage Guide

**Do not clone this repository.** This is a reference library.

1.  **Pick a Pattern:** Copy the `_work` folder from your chosen pattern into your project root.
2.  **Bootstrap:** Edit `mission.md` and `architecture.md` to fit your new project.
3.  **Prompt:**
    > "I am starting iteration 0001. Read `_work/system.md` and execute the workflow."

### Contribution

This is an open scientific inquiry into the interaction between human intent and stochastic intelligence. We welcome pull requests that introduce new patterns or refine existing ones based on empirical evidence.