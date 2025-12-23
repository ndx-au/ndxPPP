# Project Constitution: ACME Hello World Landing Page

## Immutable Rules

- Follow the current iteration's `spec.md`; do not invent requirements or UX.
- Prefer the smallest safe change that satisfies the iteration.
- Do not introduce new dependencies unless they clearly reduce complexity and are justified in `plan.md`.
- Local-first by default: should run without required external services.
- No telemetry/analytics/network calls unless a spec explicitly adds them.
- Avoid breaking changes to structure/content without a spec.
- The architecture (`_work/proj_architecture.md`) must not contradict this Constitution.
- If the human asks for work that violates this Constitution or the Architecture, request that the human update the relevant document first.

## Quality Bar (Foreman-enforced)

- Page loads/renders without runtime errors.
- No broken links or missing assets (as applicable).
- Basic accessibility expectations are met (semantic HTML, keyboard navigation where relevant).
- No unnecessary complexity or premature abstraction.

## Security & Safety Bar

- Do not add tracking/analytics/third-party scripts unless explicitly specced.
- Treat any user-provided content (if introduced) as untrusted input and handle it safely.

## Versioning Discipline

- Keep versioning consistent with `_work/proj_git.md`.
