---
type: summary
title: Summary — Iteration 0001
description: v2 OS is in the tree; v1 pattern library removed; OKF frontmatter passes.
tags: [ndxppp, iteration]
---

# Summary — Iteration 0001

## Files Changed

Added:

- `README.md` (rewritten), `AGENTS.md`, `CLAUDE.md`
- `brain/{constitution,mission,architecture,process}.md`
- `docs/{philosophy,anatomy,workflow,roles,tools,ontology,adopting,evolving,anti-patterns,changelog}.md`
- `skills/ndxppp-{engineer,worker,foreman,operator}/` (Foreman and Engineer include `reference.md`)
- `.cursor/skills/ndxppp-*` (symlinks to `skills/`)
- `profiles/{review,solo,docs}.md`
- `git/{human-gated,feature-branch,stacked-diffs,iteration-semver}.md`
- `templates/{spec,plan,summary,completed,incomplete}.md`
- `work/README.md`, `work/archive/.gitkeep`
- `work/0001-modernize-v2/{spec,plan,summary}.md`

Modified:

- `LICENSE` — copyright year `2025–2026`

Deleted:

- `pattern-basic/`, `pattern-standard/`, `pattern-adversarial/`, `pattern-terence/`, `pattern-tech-docs-rigor/`, `git-implementations/`

## What Changed

ndxPPP is now a single personal agent OS instead of a five-pattern copy-paste library. Durable intelligence lives in `brain/` (this repo, not ACME). Iterations live in `work/` with human-only `work/archive/`. Roles are Skills with progressive disclosure from `AGENTS.md`. Default profile is **review**; default git is **human-gated**. Documentation is the product. OpenSpec is documented as a peer; MCP is capabilities, not memory. The first real iteration is this folder.

## How to Validate

```bash
python3 - <<'PY'
import os, sys
root = os.path.abspath('.')
skip_parts = {'.git'}
reserved = {'index.md', 'log.md'}
missing, malformed = [], []
for dirpath, dirnames, filenames in os.walk(root):
    dirnames[:] = [d for d in dirnames if d not in skip_parts]
    for name in filenames:
        if not name.endswith('.md') or name in reserved:
            continue
        rel = os.path.relpath(os.path.join(dirpath, name), root)
        text = open(os.path.join(dirpath, name), encoding='utf-8').read()
        if not text.lstrip().startswith('---'):
            missing.append(rel); continue
        body = text.lstrip()[3:]
        end = body.find('\n---')
        if end < 0:
            malformed.append(rel); continue
        fm = body[:end]
        if not any(line.startswith('type:') and line.split(':',1)[1].strip() for line in fm.splitlines()):
            missing.append(rel)
if missing or malformed:
    print('FAIL', missing, malformed); sys.exit(1)
print('OKF type: pass')
PY
test ! -d pattern-basic && test ! -d git-implementations && test -d work/archive && test -L .cursor/skills/ndxppp-engineer
grep -q 'mv work/NNNN-slug work/archive/NNNN-slug' brain/process.md work/README.md
```

Smoke:

- Tree matches `brain/architecture.md` (brain, work, skills, profiles, git, templates, docs, AGENTS.md).
- `AGENTS.md` declares profile **review** and git **human-gated**, and forbids archive.
- No v1 pattern directories remain.

Commands above were run successfully during this iteration (OKF: 38 markdown files with `type:` before `summary.md`; 39 after).

## Compliance Checklist

- [x] `brain/constitution.md` followed
- [x] `brain/architecture.md` respected
- [x] No invented requirements beyond `spec.md`
