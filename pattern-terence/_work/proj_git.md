# GIT PROTOCOL: Direct-to-Main + Iteration-Patched SemVer (Template)

## 1. Philosophy
- Commit frequently to preserve state.
- Keep commits reviewable (avoid mixing unrelated refactors with feature work).
- Prefer conventional commit prefixes: `feat:`, `fix:`, `chore:`, `docs:`.

## 2. Version Tags (Rule)
We use tags: `vMAJOR.MINOR.PATCH`, where:
- `MAJOR.MINOR` are human-controlled.
- `PATCH` must equal the **last approved iteration number** (the highest `_work/_NNNN-*` folder).

### Recommended source of truth
- Keep the project version in a single, obvious place aligned with the git tag version.
  Acceptable examples (pick one per repo):
  - `VERSION`
  - `package.json` (`version`)
  - `pyproject.toml` / `__init__.__version__`

## 3. Worker Protocols

### A) Tag/Version preflight (required)
Trigger: every time the Worker enters a new iteration folder.

Algorithm:
1. Find the highest-numbered signed-off folder: `_work/_NNNN-*`.
2. Convert `NNNN` → `PATCH` (base-10 integer).
3. Determine `MAJOR.MINOR` from the project's version source of truth.
4. Verify a tag exists matching `vMAJOR.MINOR.PATCH`.
5. If missing:
   - **FIRST: Ensure working directory is clean**
     - Check `git status` for uncommitted changes
     - If uncommitted changes exist:
       - Read the `summary.md` from the most recent signed-off iteration `_work/_NNNN-*/summary.md` to understand what was delivered
       - Create logical commit(s) which incorporates that summary information. (e.g., `feat(NNNN): <description from summary>`)
       - Push commits: `git push origin HEAD`
   - Update the version source of truth to `MAJOR.MINOR.PATCH` and commit.
     Example if using `VERSION`:
     - `git add VERSION`
     - `git commit -m "chore(release): bump version to MAJOR.MINOR.PATCH"`
     - `git push origin HEAD`
   - Create an annotated tag:
     - `git tag -a "vMAJOR.MINOR.PATCH" -m "Release vMAJOR.MINOR.PATCH (signed-off _NNNN)"`
   - Push the tag:
     - `git push origin "vMAJOR.MINOR.PATCH"`

If there is no signed-off folder yet, skip preflight.

### B) Normal commits
Trigger: after generating or updating `summary.md`.

Examples:
- First submission for the iteration:
  - `feat(NNNN): implementation for review`
- Fixes after `incomplete.md` feedback:
  - `fix(NNNN): addressed foreman feedback`

## 4. Foreman Protocols
- Foreman does NOT commit.
- Foreman does NOT push.
- Foreman does NOT create tags.
- Foreman signals approval via `completed.md`.

Human sign-off:
- The human seals an iteration by renaming the folder with a leading underscore (e.g. `_work/_0008-done/`).
