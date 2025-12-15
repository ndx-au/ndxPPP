# Pattern: Standard (Feature Branch)

## Concept
This pattern is the "daily driver" for most professional teams.
It keeps `main` clean and deployable by doing all work on a short-lived feature branch per iteration.

## Roles
Single agent.

## Git Strategy
Feature Branch (one branch per iteration; squash merge back to `main`).

## How to Use
1. Copy `pattern-standard/_work/` into your project root as `_work/`.
2. Edit `_work/mission.md`, `_work/architecture.md`, and `_work/constitution.md` to fit your project.
3. Create your first iteration folder (e.g., `_work/0001-setup/`) with a `spec.md`.
4. Prompt your agent:
   > "I am starting iteration 0001. Read `_work/system.md` and execute the workflow."

## Notes
- To change Git behavior, copy a module from `git-implementations/` into your `_work/` folder and rename it to `git.md`.
