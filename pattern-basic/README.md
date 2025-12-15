# Pattern: Basic (Trunk-Based)

This is the smallest ndxPPP pattern: one agent, one loop, direct commits to `main`.
For the full methodology overview, see [../README.md](../README.md).

## Concept
- **Roles:** Single agent.
- **Workflow:** Read spec -> write plan -> implement -> write summary.
- **State:** Iteration folders inside `_work/` (state signals and naming rules are defined in `_work/system.md`).

## Best For
- Prototyping and scripts
- Solo MVPs
- Fast iteration where clean branching is not the priority

## Structure
Copy this folder's `_work/` directory into your project root.

## How to Use
1. Copy `pattern-basic/_work/` into your project root as `_work/`.
2. Edit `_work/mission.md`, `_work/architecture.md`, and `_work/constitution.md` to fit your project.
3. Create your first iteration folder (e.g., `_work/0001-setup/`) with a `spec.md`.
4. Prompt your agent:
   > "I am starting iteration 0001. Read `_work/system.md` and execute the workflow."

## Notes
- If you want PR-based hygiene, use the Standard pattern or swap in a Git protocol from `git-implementations/`.