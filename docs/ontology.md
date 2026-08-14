---
type: guide
title: Ontology
description: OKF YAML frontmatter on ndxPPP files, suggested types, and later EKG ingest.
tags: [ndxppp, ontology]
---

# Ontology

Brain, docs, profiles, git modules, templates, and iteration artifacts start with YAML frontmatter. The required field is `type:` (Open Knowledge Format / OKF, as used by EKG). Other keys are optional. Consumers must tolerate unknown keys.

This repo does **not** run EKG. Frontmatter makes the corpus ingestible later without a rewrite.

## Document shape

```yaml
---
type: constitution
title: Constitution
description: Immutable laws for agents and humans working in this repository.
tags: [ndxppp, brain]
---
```

- Frontmatter is the first bytes of the file (opening `---` line).
- `type` is a non-empty string.
- Reserved OKF names `index.md` and `log.md` must **not** use this leading block if you add them. This repo does not use those reserved files.

## Suggested `type` values

| type | Used for |
|---|---|
| `overview` | Root README |
| `guide` | `docs/*`, `AGENTS.md`, `CLAUDE.md`, `work/README.md` |
| `constitution` | `brain/constitution.md` |
| `mission` | `brain/mission.md` |
| `architecture` | `brain/architecture.md` |
| `process` | `brain/process.md` |
| `protocol` | `profiles/*`, `git/*` |
| `spec` | `work/**/spec.md`, `templates/spec.md` |
| `plan` | `work/**/plan.md`, `templates/plan.md` |
| `summary` | `work/**/summary.md`, `templates/summary.md` |
| `review` | `completed.md`, `incomplete.md` |
| `reference` | Skill `reference.md` |
| `skill` | `SKILL.md` (in addition to Cursor `name` / `description`) |

## Skill files

Cursor requires `name` and `description`. Add `type: skill` so OKF and Cursor share one block:

```yaml
---
name: ndxppp-engineer
description: >
  …
type: skill
title: Engineer
tags: [ndxppp, role]
---
```

## Iteration extras

Optional keys on `spec.md`:

```yaml
openspec: change-name-in-host-repo
```

Do not invent a parallel status field. State is file presence ([workflow.md](workflow.md)).

## Later EKG ingest

If you copy `brain/` + `docs/` + archived `work/` into an ERE `doctree/`:

- These files already satisfy core OKF (`type` present).
- Add folder `frontmatter.yaml` in the ERE if you want folder nodes (EKG extension). Not maintained here.
- `tags: [ndxppp, …]` is a coarse filter.

Until then, frontmatter is also just good manners: title and description show up in search and in agent listings.
