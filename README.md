# ndxPPP: Passive Prompt Patterns
**Sustainable, State-Based Workflows for AI-Assisted Engineering**

## 1. The Core Philosophy
**ndxPPP** is a reaction against "Black Box" AI development.

Most AI coding tools hide their logic, state, and prompts inside temporary chat windows or proprietary databases. When the chat closes, the context is lost ("Context Rot").

**Passive Prompt Patterns** invert this:
1.  **The File System is the State:** All context, plans, and history live in a visible `_work/` directory.
2.  **Tool Agnostic:** These patterns work with any AI—`opencode`, Cursor, Windsurf, or raw LLM APIs.
3.  **Human-in-the-Loop:** The AI is the engine, but you are the steering wheel.

---

## 2. The "Brain" vs. The "Body"
Every project using these patterns has a distinct anatomical separation:

* **The Body (Project Root):** Contains your source code (`main.go`, `src/`, etc.). This is what you ship.
* **The Brain (`_work/`):** Contains the intelligence. This is never `.gitignore`'d.

### Why commit the `_work` folder?
By committing the Brain, anyone looking at your repo can instantly answer:
* *What is being worked on right now?* (Look for the un-underscored folder).
* *Why did we make that decision 3 weeks ago?* (Look at `_work/_0002-database/spec.md`).
* *What are the rules?* (Look at `_work/constitution.md`).

---

## 3. The Human's Role: The "Sign-Off"
In these patterns, the AI does not have "Infinite Agency." It cannot invent work endlessly. The workflow enforces a strict **Handshake Protocol** between Human and Machine:

### Step 1: The Seed (Human)
You define the `spec.md` for a new iteration. You brainstorm with the AI, but *you* write the final requirement.

### Step 2: The Loop (AI)
The AI reads the spec, creates a plan, and implements the code. It iterates until it believes the job is done, generating a `summary.md`.

### Step 3: The Sign-Off (Human)
This is the critical control mechanism.
* **Review:** You check the `summary.md` and the code.
* **Reject:** If it's wrong, you ask for a fix (or use the Adversarial Pattern's `incomplete.md`).
* **Approve:** You rename the folder from `0004-feature` to `_0004-feature`.

**The leading underscore `_` is your signature.** It tells the AI: *"This history is now immutable. Move on."*

---

## 4. Pattern Library

### `📂 pattern-basic/`
*The "Solo Pilot" Workflow.*
A streamlined loop for individual developers. One agent role handles planning and execution. Perfect for MVPs and scripts.

### `📂 pattern-adversarial/`
*The "Worker & Foreman" Workflow.*
A high-reliability loop. Splits the AI into two personas:
* **Worker:** Optimizes for speed and output.
* **Foreman:** Optimizes for security, correctness, and architectural compliance.
* *The Foreman blocks the Worker until quality standards are met.*

### `📂 git-implementations/`
A collection of modular Git strategies (Trunk-based, Stacked Diffs, GitHub Flow) that can be plugged into any of the patterns above.

---

## 5. Getting Started
1.  **Pick a Pattern:** Copy the `_work` folder from `pattern-basic` or `pattern-adversarial` into your project root.
2.  **Define Your World:** Edit `mission.md` (your values) and `architecture.md` (your stack).
3.  **Start Iteration 0001:** Create `_work/0001-setup/spec.md`.
4.  **Prompt Your AI:** *"Read `_work/system.md` and execute the current iteration."*