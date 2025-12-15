# ndxPPP: Passive Prompt Patterns
**A Framework for State-Based, Tool-Agnostic AI Development**

## Abstract
**ndxPPP** (Passive Prompt Patterns) explores a methodology for **Sustainable AI-Assisted Software Engineering**. It proposes a shift away from rigid, proprietary "agent frameworks" toward a file-system-centric approach where the project's state, rules, and mission are encoded in standardized, passive text files.

This repository serves as a reference library of **architectural patterns** that enable developers to guide stochastic Large Language Models (LLMs) through complex, multi-stage application builds without relying on specific tooling. Whether you use `opencode`, Cursor, or raw LLM APIs, the file system remains the single source of truth.

---

## 1. The Problem: "Context Rot" and Tool Lock-In
The current landscape of AI-assisted development faces two primary structural failures when scaling beyond simple scripts to complex applications:

### A. Stochastic Degradation ("Context Rot")
In traditional "chat-based" coding, the context window is a leaky bucket. As sessions lengthen, early architectural decisions are forgotten or hallucinated away. The AI loses the "why" behind the "what," leading to circular refactoring loops.

### B. The "Active Agent" Trap
Current solutions often rely on hidden prompt chains and proprietary "skill" definitions. This creates:
* **Vendor Lock-in:** Workflows break if the tool is deprecated.
* **Opaque Logic:** Developers cannot easily inspect the agent's decision-making heuristics.
* **Friction:** High adoption cost requiring complex binary installations.

---

## 2. The Solution: Passive Prompt Patterns
We propose an inversion of control: **The File System is the State.**

A "Passive Pattern" is a directory structure that requires no special software to execute. When an AI agent is pointed at these files, the pattern *induces* the correct behavior through four core primitives located in a top-level `_work/` directory.

### The "Context Trifecta" + System
Every project relies on four static files to bootstrap the AI's context:

1.  **`_work/system.md` (The Manual):** The meta-protocol. It teaches the AI how to navigate the folder structure, how to identify the current task, and how to archive completed work.
2.  **`_work/constitution.md` (The Law):** Immutable negative constraints. It defines what is *forbidden* (e.g., "No external dependencies," "No use of `panic`").
3.  **`_work/mission.md` (The Soul):** High-level values and creative direction. It defines the "vibe" and UX goals (e.g., "Radical Simplicity," "Speed is a Feature").
4.  **`_work/architecture.md` (The Blueprint):** The declarative "Success State." It defines the final stack, component relationships, and the definition of "Done."

---

## 3. The Global Protocol (Naming Conventions)
To maintain order, all patterns in this repository adhere to the **NDX Iteration Standard**.

### The "Brain" vs. The "Body"
* **The Brain (`_work/`):** Contains all context, specs, plans, and history. The AI "thinks" here.
* **The Body (Project Root):** Contains the actual source code. The AI "acts" here.

### Iteration Management
Work is broken into discrete folders within `_work/` using a strict naming algorithm:

1.  **Active Iterations:** `NNNN-feature-name` (e.g., `0005-add-search`).
    * *Logic:* The AI identifies the current task by finding the folder with the **lowest number that does not start with an underscore**.
2.  **Archived Iterations:** `_NNNN-feature-name` (e.g., `_0001-setup`).
    * *Logic:* Once a feature is complete and verified, the user renames the folder by prepending an underscore. This signals to the AI that the content is now **Immutable History**.

---

## 4. Repository Structure
This repository is organized by **Pattern Complexity**.

### `📂 pattern-basic/`
*The fundamental unit of Iterative Spec-Driven Development (ISDD).*
* **Use Case:** Small tools, scripts, or solo MVP development.
* **Structure:**
    * `_work/system.md`
    * `_work/constitution.md`
    * `_work/mission.md`
    * `_work/architecture.md`
    * `_work/0001-init/spec.md`

### `📂 pattern-stacked-diffs/`
*Advanced workflow for complex features requiring interdependent review cycles.*
* **Use Case:** Teams using Git-flow, requiring multiple dependent PRs for a single feature.
* **Key Addition:** `stack_manifest.md` which instructs the AI on how to manage git branches, rebase dependencies, and handle "stacked" PRs.

### `📂 pattern-adversarial/` (Coming Soon)
*A dual-agent pattern for high-reliability systems.*
* **Use Case:** Security-critical components.
* **Structure:** Explicit separation of "Builder" prompts and "Critic/QA" prompts.

---

## 5. Usage Guide
**Do not clone this repository.**
This is a pattern library. To use these patterns:

1.  **Select a Pattern:** Browse the folders to find the complexity level that suits your project.
2.  **Bootstrap Your Agent:** Prompt your AI to scaffold the `_work` directory for you.
    > *Example Prompt:* "I am starting a new project using the NDX 'Basic' pattern. Please generate the `_work/` folder structure, including `system.md`, `constitution.md`, `mission.md`, and `architecture.md`. My project is a Go-based SaaS for..."
3.  **Start Iterating:** Create your first folder `_work/0001-setup` and add a `spec.md`.
4.  **Run the Loop:** Tell your agent: *"Read `_work/system.md` and execute the current iteration."*

---

### Contribution
This is an open scientific inquiry into the interaction between human intent and stochastic intelligence. We welcome pull requests that introduce new patterns or refine existing ones based on empirical evidence.