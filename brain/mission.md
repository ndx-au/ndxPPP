---
type: mission
title: Mission
description: Why this repository exists and what it optimizes for.
tags: [ndxppp, brain]
---

# Mission

ndxPPP is a **personal operating system for agent work**.

It exists so that AI-assisted building stays inspectable: durable rules, an auditable iteration timeline, role contracts, and a human signature at the end of each unit of work. Chat sessions are disposable. These files are not.

## Product

This repository *is* the OS: markdown rails, not a runtime. The interface is documentation. The loop is files in `work/`. Success is that you can drop the brain and skills into another repo, tailor three files, and get a gated workflow without adopting a framework.

## Users

- You, running agents on real projects.
- Future-you, recovering intent from git rather than from a dead chat.
- An agent that has only this repo and [AGENTS.md](../AGENTS.md).

## Values (ranked)

1. **Inspectability** — a stranger (or a new session) can reconstruct what was decided and what is in flight.
2. **Human control** — agents propose and implement; you accept architecture changes and you archive iterations.
3. **Lightness** — load what the turn needs. Do not require a ceremony that does not prevent drift or invention.
4. **Tool humility** — files outlive Cursor, Claude Code, and whatever replaces them.
5. **Honesty in docs** — the manual describes the tree that is actually here.

## Non-goals (until explicitly specced)

- A public framework, CLI, or MCP server.
- Vendor lock-in to one agent product.
- Live EKG ingest or ontology runtime in this repo.
- Installing this OS into Sentinel, Ontos, or other product repos as part of a default iteration.
