---
type: plan
title: Plan — Iteration 0001
description: Implementation steps for the v2 OS. Human-approved via the Cursor plan.
tags: [ndxppp, iteration]
---

# Plan — Iteration 0001

## Approach

Build the destination tree first (docs spine, brain, skills, profiles, git, templates), then the remaining manual, then this iteration’s artifacts, then delete v1 trees. Validate with an OKF frontmatter scan.

## Steps

- [x] 1. Write README, AGENTS.md, CLAUDE.md, docs/philosophy.md, docs/changelog.md
- [x] 2. Author brain/constitution.md, mission.md, architecture.md, process.md
- [x] 3. Add four role skills, reference files, `.cursor/skills/` symlinks
- [x] 4. Add profiles, git modules, templates
- [x] 5. Write remaining docs (anatomy, workflow, roles, tools, ontology, adopting, evolving, anti-patterns)
- [x] 6. Add work/README.md and work/archive/.gitkeep
- [x] 7. Write this spec.md and plan.md
- [x] 8. Delete pattern-* and git-implementations/
- [x] 9. OKF-lint markdown; write summary.md

## Validation

```bash
python3 - <<'PY'
# OKF: non-reserved .md files must start with --- and contain a non-empty type: in the first frontmatter block
import os, sys
root = os.path.abspath('.')
skip_parts = {'.git'}
reserved = {'index.md', 'log.md'}
missing = []
malformed = []
for dirpath, dirnames, filenames in os.walk(root):
    dirnames[:] = [d for d in dirnames if d not in skip_parts]
    for name in filenames:
        if not name.endswith('.md'):
            continue
        if name in reserved:
            continue
        path = os.path.join(dirpath, name)
        rel = os.path.relpath(path, root)
        text = open(path, encoding='utf-8').read()
        if not text.lstrip().startswith('---'):
            missing.append(rel)
            continue
        body = text.lstrip()[3:]
        end = body.find('\n---')
        if end < 0:
            malformed.append(rel)
            continue
        fm = body[:end]
        ok = False
        for line in fm.splitlines():
            if line.startswith('type:'):
                val = line.split(':', 1)[1].strip()
                if val:
                    ok = True
                    break
        if not ok:
            missing.append(rel)
if missing or malformed:
    print('MISSING type:', *missing, sep='\n  ')
    print('MALFORMED:', *malformed, sep='\n  ')
    sys.exit(1)
print('OKF type: pass')
PY
```

Smoke:

- `find` layout vs `brain/architecture.md`
- Archive rule present in `work/README.md` and `brain/process.md`
