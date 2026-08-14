---
type: guide
title: Philosophy
description: Why ndxPPP keeps agent rules and work-state in ordinary versioned files under human control.
tags: [ndxppp, philosophy]
---

# Philosophy

ndxPPP is a **file-system-centric, passive, human-gated** operating system for AI-assisted work.

The important state does not live in a chat transcript, a vendor memory store, or an agent framework. It lives in ordinary markdown files in the repository, versioned with the product, readable without the tool that wrote them.

## The problem

Agents are powerful and amnesiac. A session invents requirements, drifts from the architecture, and then disappears. The next session inherits none of that discipline unless you put it somewhere durable.

By 2026 the industry has accepted the simple form of the fix: persistent instruction files (`AGENTS.md`, `CLAUDE.md`, Cursor rules, Skills). Those files tell an agent *how to behave in this repo*. They do not, by themselves, tell you *what work is in flight, whether it was reviewed, or whether a human accepted it*.

Context rot, architectural drift, and invented requirements are still the failure modes that matter once agents become more autonomous.

## What this OS adds

A lightweight, git-native process layer on top of those instruction files:

1. **A durable brain** — constitution, mission, architecture, process. Law, why, success state, and how. Updated in the open before work is allowed to violate them.
2. **An iteration state machine** — `spec.md` → `plan.md` → `summary.md` → Foreman `completed.md` / `incomplete.md` → human archive. State is the presence of files, not a database.
3. **Role separation** — the human is Architect. Agents act as Engineer, Worker, Foreman, or Operator under explicit contracts.
4. **A hard human gate** — agents can propose and review. Only the human archives an iteration. That move is the digital signature.

The OS is **passive**: you lay the files down; any capable agent reads them. It is **tool-agnostic** in principle and mapped onto Cursor, Claude Code, and OpenSpec in practice. It is **not** a runtime, a framework, or a product to evangelize.

## Passive vs active

| Active agent frameworks | ndxPPP |
|---|---|
| State in the session or a vendor store | State in the repo |
| The tool owns the workflow | You own the files |
| Review is optional commentary | Review is a signal file |
| Done when the agent says so | Done when the human archives |

Skills and `AGENTS.md` are the on-ramp. They are not a substitute for the brain. If the brain and the skill disagree, the brain wins, and then you fix the skill.

## What we refuse

- Inventing requirements that are not in the spec (or in an explicit brain update).
- Proceeding past a constitution or architecture conflict without editing those files first.
- Archiving an iteration as an agent.
- Treating a green chat as a substitute for `summary.md` and a Foreman verdict.

Ceremony that does not protect those refusals should be pruned. Discipline that does should stay. See [anti-patterns.md](anti-patterns.md).
