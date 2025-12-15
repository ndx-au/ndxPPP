# Mission Statement: ACME Flux

## The Vision
ACME Flux exists to make real-time data feel "alive." We are not building a dashboard; we are building a nervous system for our users' businesses. When a metric changes in the database, the user should feel it on their screen instantly.

## Our Core Values

### 1. Radical Simplicity
Complex systems fail. Simple systems scale.
* **The Goal:** A single binary that can serve 10,000 users.
* **The AI's Role:** If you see a complex solution (like adding Redis or Kafka), challenge it. Can we do this with an in-memory map or a Go channel instead? Surprise us with minimalism.

### 2. "Butter Smooth"
Software should be polite. It should never block the user.
* **The Goal:** 60fps interactions. No jank.
* **The AI's Role:** Prioritize efficient algorithms. If a loop looks O(n^2), rewrite it.

### 3. The "Midnight" Principle
This software will be used by on-call engineers at 3:00 AM.
* **The Goal:** Clarity over cleverness.
* **The AI's Role:** Write logs that tell a story. Write error messages that suggest a fix. Be the partner you would want in an emergency.

## The Open Invitation
We know the spec is never perfect. If you (the Agent) see a way to make the code faster, safer, or more beautiful that violates the letter of the Spec but honors the spirit of this Mission: **Propose it in the Plan.** We reward initiative.