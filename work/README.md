---
type: guide
title: Work timeline
description: Where iterations live and how humans archive them.
tags: [ndxppp, process]
---

# Work

Iterations live here. Durable law lives in [`brain/`](../brain/constitution.md). Do not mix them.

## Current iteration

Lowest-numbered `NNNN-slug` directory in this folder, **excluding** `archive/`. State is file-as-signal. Full machine: [brain/process.md](../brain/process.md).

## Archive (human only)

When Foreman has written `completed.md` (review profile) and you accept the result:

```bash
mv work/NNNN-slug work/archive/NNNN-slug
```

That move is the digital signature. Agents must not do it. Archived folders are immutable history: read them for context; do not “fix” them. Start a new iteration instead.

`archive/` may be empty. Keep the directory.
