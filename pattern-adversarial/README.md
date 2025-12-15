# Pattern: Adversarial (Worker/Foreman)

## Concept
This pattern splits the "Agency" into two distinct roles to prevent "Context Rot" and "Optimism Bias."
* **The Worker:** Focused on output, speed, and passing tests.
* **The Foreman:** Focused on correctness, security, and architectural alignment.

## The State Machine
Instead of a linear path, this pattern creates a **Quality Loop**:

1.  **Worker** builds -> `summary.md`
2.  **Foreman** reviews `summary.md` + Code
    * *If Bad:* Creates `incomplete.md` -> **Worker** fixes -> Deletes `incomplete.md` -> Loop.
    * *If Good:* Creates `completed.md`.

## How to Use
1. Copy `pattern-adversarial/_work/` into your project root as `_work/`.
2. Edit `_work/mission.md`, `_work/architecture.md`, and `_work/constitution.md` to fit your project.
3. Create your first iteration folder (e.g., `_work/0001-setup/`) with a `spec.md`.

## How to Run This
You will need two separate agent sessions (or prompts).

### Step 1: The Build (Run the Worker)
Prompt your agent:
> "Act as the **Worker**. Read `_work/worker.md` and execute the next step."

### Step 2: The Audit (Run the Foreman)
When the Worker stops (because it generated a Summary), open a new context or prompt:
> "Act as the **Foreman**. Read `_work/foreman.md` and audit the current iteration."