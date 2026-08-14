---
type: protocol
title: Git — human-gated
description: Default git module. Agents propose commits; humans run git writes.
tags: [ndxppp, git]
---

# Git protocol: human-gated

Default for this OS. Matches how the Architect actually works: agents do not commit unless asked.

## Rules

1. Do **not** run `git commit`, `git push`, `git tag`, `git merge`, or `git rebase` unless the human explicitly asked in this turn (or a standing instruction in the host `AGENTS.md` overrides this module).
2. You **may** run read-only git (`status`, `diff`, `log`, `show`) to write an accurate `summary.md`.
3. When work is ready to save, **propose** a conventional commit message (`feat:`, `fix:`, `docs:`, `chore:`) and list the files. Stop.
4. Do not mix unrelated refactors into the proposed commit.
5. Iteration archive (`mv` into `work/archive/`) is still not a git action you perform.

## Worker

After `summary.md` (and after Foreman on the review profile), propose the commit. Do not create it.

## Foreman

Foreman never commits, even if the human asked the Worker to. Review is not a save.

## Override

If the human says “commit this”, do it, then return to the gate. If they say “use feature-branch”, switch modules for that repo — do not silently keep committing to `main` after the experiment.
