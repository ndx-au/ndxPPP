---
type: guide
title: Tools
description: How ndxPPP maps onto Cursor, Claude Code, OpenSpec, and MCP.
tags: [ndxppp, tools]
---

# Tools

The OS is files. Tools are how you read and write them. If a tool vanishes, the rails remain.

## Cursor

- **Always on:** [AGENTS.md](../AGENTS.md). Cursor loads it.
- **Skills:** [skills/](../skills/ndxppp-engineer/SKILL.md) mirrored as symlinks in `.cursor/skills/` so they auto-invoke.
- **Plan mode** ≈ Engineer (spec, conflicts with architecture).
- **Agent mode** ≈ Worker (execute an approved plan).
- **Hard Foreman:** Task subagents `code-reviewer` and `security-review` on the diff, then the Foreman skill writes `completed.md` or `incomplete.md`. Same-session Foreman is the default.

You do not need extra `.cursor/rules/` if `AGENTS.md` is accurate. Add rules only for host-repo coding standards, not to fork this process.

## Claude Code

[CLAUDE.md](../CLAUDE.md) points at `AGENTS.md`. Copy skills into `.claude/skills/` in a host repo if you want auto-invocation there; or rely on `AGENTS.md` paths.

## OpenCode and others

Anything that will read markdown from the workspace can run the loop. Paste the [AGENTS.md](../AGENTS.md) bootloader. Role aliases (`Worker, …`) still work when skill discovery does not.

## OpenSpec (peer, not replacement)

| OpenSpec | ndxPPP |
|---|---|
| Change artifacts: proposal, design, specs, tasks | Durable brain + role contracts |
| `openspec/changes/` + archive | `work/` + `work/archive/` |
| Schema for *what to build* | Gate for *whether it is accepted* |

A project may use both. In that case:

- Keep the ndxPPP iteration folder (state machine and Foreman files).
- Set `openspec: <change-name>` in `spec.md` frontmatter.
- Do not duplicate proposal/design/tasks into `spec.md`. Point at them.
- Human archive of the ndxPPP folder is independent of `openspec archive` unless you decide to do both in one sitting.

ndxPPP does not require the OpenSpec CLI.

## MCP

MCP servers are **capabilities** (docs search, browser, bindings). They are not project memory.

Do not store iteration state, constitution, or sign-off in an MCP resource. If a knowledge graph (EKG, ndx-software-kg) is connected, query it for *cross-repo facts*; still write *this repo’s* decisions into `brain/` and `work/`.

This repository does not ship an MCP server.
