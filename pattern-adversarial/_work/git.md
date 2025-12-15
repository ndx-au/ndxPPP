# GIT PROTOCOL: Direct-to-Main (Minimal)

## 1. Philosophy
* **Local First:** We commit frequently to save state locally.
* **Gatekeeper Push:** We only Push to remote when an Iteration is "Sealed" by the Foreman.
* **Format:** We use conventional commits (e.g., `feat:`, `fix:`, `chore:`).

## 2. Worker Protocols (The Committer)
* **Trigger:** Immediately after generating or updating `summary.md`.
* **Logic:**
    1.  Stage all changes.
    2.  If this is the first submission for this iteration:
        * `git commit -m "feat(NNNN): implementation for review"`
    3.  If this is a fix based on `incomplete.md` feedback:
        * `git commit -m "fix(NNNN): addressed foreman feedback"`

## 3. Foreman Protocols (The Publisher)
* **Trigger:** Immediately after generating `completed.md`.
* **Logic:**
    1.  Stage the state change (the new `completed.md`).
    2.  Commit the seal:
        * `git commit -m "chore(NNNN): iteration sealed"`
    3.  Tag the release:
        * `git tag -a "iter-NNNN" -m "Sealed iteration NNNN"`
    4.  Sync to upstream:
        * `git push origin HEAD --tags`