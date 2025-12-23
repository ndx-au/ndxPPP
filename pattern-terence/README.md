# `_work/` User Guide (Human)

This folder is a **passive prompt pattern** system: a small set of documents that you own, which define roles, rules, and workflow - so an AI assistant can reliably help you run a project.

You (the human) are the **Architect** and the owner of the project and its architecture.

## 1) One-time Initialization (required)

Before you start using the system on a project, **initialize it by tailoring the project docs**:

This pattern ships with a deliberately-generic example project (“ACME Hello World Landing Page”). Replace any ACME-specific placeholder content in the `_work/proj_*.md` files with your real project.

1. Update `_work/proj_architecture.md` with your project’s:
   - Unique design constraints and structure
   - Real usage cases and target workflows
   - Concrete success criteria (how you’ll know it’s “done”)
   - Any important invariants that are *not* laws (i.e., design choices)

2. Review and tailor the other project docs to match how you want to work:
   - `_work/proj_system.md` (process, iteration state machine, summary contract)
   - `_work/proj_constitution.md` (immutable laws)
   - `_work/proj_git.md` (tagging/versioning expectations)
   - `_work/proj_mission.md` (product purpose and values)

You must **take ownership** of these documents and evolve them as your process evolves (and reuse/adapt them across projects).

## 2) How to Start a Session (recommended)

At the outset of a new session (or when context is stale), prompt the AI assistant:

- Ask it to **read all markdown files in the root of `_work/`**.
- Then instruct it to **assume the Engineer role**.

This ensures the assistant re-loads the “rules of the game” before writing a spec or making changes.

## 3) Role Invocation Syntax

After initialization, begin prompts with the role name followed by a comma:

- `Engineer, ...`
- `Worker, ...`
- `Foreman, ...`
- `Operator, ...`

The assistant should respond in that role’s posture and follow the relevant rules.

## 4) When to Invoke Each Role

### Architect (you, the human)

You are always the Architect. “Ask the Architect” means “ask the human.”

Invoke yourself by deciding:

- What matters, what doesn’t, and what tradeoffs are acceptable
- When the Constitution/Architecture should be changed to resolve conflicts
- When to sign off an approved iteration (see Sign-off below)

### Engineer

Invoke **Engineer** when:

- You are starting a new iteration
- You need ambiguities resolved and a crisp, testable `spec.md`
- You suspect the request may violate the Constitution or Architecture and needs document updates first

Deliverable: a precise `spec.md` in the iteration folder, ready for Worker planning.

### Worker

How to invoke the **Worker**:

- When there is a ready `spec.md`, address the worker and tell them it's their turn.
- The worker reads the spec and creates a plan of action, then waits for the Architect (you) to review the plan.
- You update the plan, or tell the worker to update the plan until you are happy with it.
- When you are satisfied with the plan, then tell the worker to go ahead and make the changes to the project files.
- Once it completes the changes, it generates a summary of all the work that was done (and reasoning) and asks you to invoke the Foreman.
- You might want to do some testing of your own at this point, and tell the worker to fix/change things before invoking the foreman.

Deliverables: `plan.md` and `summary.md`, plus code changes that satisfy the spec.

### Foreman

Invoke **Foreman** when:

- A Worker has produced `summary.md`, you're happy with the work done, and you want strict review

Deliverables:

- `completed.md` if approved
- `incomplete.md` if rejected (with concrete fix list)

When the Foreman approves, you should probably do a micro user-acceptance testing of the results before moving to sign off and begin a new iteration folder.

### Operator

Invoke **Operator** when:

- You want help with meta-process, sequencing, or documentation hygiene
- You want exceptional actions taken (tooling, scaffolding, doc maintenance) that aren’t core feature implementation

Important: Operator may assist with spec drafting or iteration provisioning **only if you explicitly request it**, and still cannot sign off iterations.

## 5) Iterations, Approval, and Human Sign-off

- “Current Iteration” is the **lowest numbered** `_work/NNNN-*` folder that does **not** start with an underscore.
- The **Foreman approves** an iteration by creating `completed.md`.
- Only the **human signs off** an approved iteration by renaming the folder to add a leading underscore (e.g., `_work/_0003-something/`).

### Blocking rule (important)

If the Current Iteration contains `completed.md` but is not underscored yet:

- Agents must **stop** and request human sign-off.
- Agents must not proceed to later iterations.
- While blocked, agents must repeat the sign-off request at the beginning of each response summary.

## 6) Structural Integrity (Constitution vs Architecture)

- `_work/proj_constitution.md` contains immutable laws.
- `_work/proj_architecture.md` contains the designed system structure.

If your desired work violates the Constitution or the Architecture, the correct move is to:

1) Update the relevant document(s) first (you have full authority), then
2) Continue with the iteration under the updated rules.

This system only works if the documents remain consistent and you actively maintain them.
