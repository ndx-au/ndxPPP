# ndxPPP: Passive Prompt Patterns
**A Framework for State-Based, Tool-Agnostic AI Development**

## Abstract
**ndxPPP** (Passive Prompt Patterns) explores a methodology for **Sustainable AI-Assisted Software Engineering**. It proposes a shift away from rigid, proprietary "agent frameworks" toward a file-system-centric approach where the project's state, rules, and mission are encoded in standardized, passive text files.

This repository serves as a reference library of **architectural patterns** that enable developers to guide stochastic Large Language Models (LLMs) through complex, multi-stage application builds without relying on specific tooling (e.g., specific CLI agents or IDE extensions).

---

## 1. The Problem: "Context Rot" and Tool Lock-In
The current landscape of AI-assisted development faces two primary structural failures when scaling beyond simple scripts to complex applications:

### A. Stochastic Degradation ("Context Rot")
In traditional "chat-based" coding, the context window is a leaky bucket. As a session lengthens, early architectural decisions are forgotten or hallucinated away. The AI loses the "why" behind the "what," leading to circular refactoring and regression loops.

### B. The "Active Agent" Trap
Most current solutions (proprietary CLI agents, specialized IDEs) attempt to solve this by building rigid, "Active" systems—hidden prompt chains, proprietary "skill" definitions, and opaque state management. This creates:
* **Vendor Lock-in:** Workflows break if the tool is deprecated.
* **Opaque Logic:** Developers cannot easily inspect or modify the agent's decision-making heuristics.
* **Friction:** High adoption cost requiring installation of complex binaries or ecosystems.

---

## 2. The Solution: Passive Prompt Patterns
We propose an inversion of control: **The File System is the State.**

A "Passive Pattern" is a directory structure and set of markdown files that require no special software to execute. They simply sit in the repository, "waiting" to be read. When an AI agent (be it OpenCode, Cursor, or a raw LLM API) is pointed at these files, the pattern *induces* the correct behavior.

### Core Principles
1.  **Tool Agnosticism:** These patterns work with `vi`, `vscode`, `cursor`, `opencode`, or a web browser paste. They depend only on the universal standard of **Markdown**.
2.  **Iterative Containment:** Development is broken into discrete "state containers" (iterations). Each container includes its own Spec, Plan, and Retrospective (Diff), minimizing the context required for the AI to function effectively.
3.  **Constitutional Guardrails:** High-level project ethics and coding standards are decoupled from implementation details, residing in "Constitution" files that persistently guide the AI's "personality."

---

## 3. Repository Structure
This repository is organized by **Pattern Complexity**. Developers should select the pattern that matches their project's scale and team size.

### `📂 pattern-basic/`
*The fundamental unit of Iterative Spec-Driven Development (ISDD).*
* **Use Case:** Small tools, scripts, or solo MVP development.
* **Key Concept:** The **Iteration Loop**.
* **Structure:**
    * `constitution.md`: The immutable rules (idioms, error handling).
    * `mission.md`: The project's soul (values, UX goals).
    * `docs/iterations/01-mvp/`: A contained workspace for the first sprint.

### `📂 pattern-stacked-diffs/`
*Advanced workflow for complex features requiring interdependent review cycles.*
* **Use Case:** Production-grade applications, team environments, or features too large for a single context window.
* **Key Concept:** The **Stack Manifest**.
* **Structure:**
    * `stack_manifest.md`: A governance file instructing the AI how to manage git branches and rebase dependencies.
    * `docs/stacks/feature-x/layer-01-schema/`: The database layer.
    * `docs/stacks/feature-x/layer-02-logic/`: The business logic layer (dependent on 01).

### `📂 pattern-adversarial-basic/` (Coming Soon)
*A dual-agent pattern for high-reliability systems.*
* **Use Case:** Security-critical components or complex algorithmic implementations.
* **Key Concept:** **The Critic**.
* **Structure:** Explicit separation of "Builder" prompts and "Critic/QA" prompts, where one agent generates code and a second agent (using a distinct `critic_persona.md`) attempts to break it.

---

## 4. Usage Guide
**Do not clone this repository.**
This is a pattern library, not a dependency. To use these patterns:

1.  **Select a Pattern:** Browse the folders above to find the complexity level that suits your project.
2.  **Bootstrap Your Agent:** Copy the file structure or simply prompt your AI agent to scaffold it for you.
    > *Example Prompt:* "I want to start a new project using the 'Basic Passive Pattern'. Please generate a `constitution.md`, `mission.md`, and a directory structure for `docs/iterations/01-setup` based on the principles of Iterative Spec-Driven Development."
3.  **Iterate:** Follow the workflow defined in the pattern's `README`.

---

### Contribution
This is an open scientific inquiry into the interaction between human intent and stochastic intelligence. We welcome pull requests that introduce new patterns or refine existing ones based on empirical evidence.