# System Architecture: ACME Hello World Landing Page

Declare the target success state. The Foreman audits against this file.

## Goals (v1 foundations)

- A simple landing page that:
  - Renders a **hero** section with a headline and short description.
  - Includes a single, obvious **call-to-action** (CTA) (e.g., "Contact us" or "Get started").
  - Works in modern browsers and is usable without JavaScript.
  - Is easy for a new user to replace with their own branding/content.

## Recommended Structure (best-judgment)

Keep the product minimal and obvious:

- `index.html` (required)
- `assets/` (optional)
  - `styles.css` (optional)
  - `script.js` (optional; only if needed)
  - `images/` (optional)

### Why this structure

- Works without a framework.
- Easy to customize for any project.
- Keeps change sets small per iteration.

## Constraints

- **Target host:** modern web browsers.
- **Dependencies:** prefer none; add tooling only if the spec explicitly introduces it.
- **Cross-platform:** Windows/macOS/Linux (development) and major browsers (runtime).
- For immutable safety/network rules, defer to `_work/proj_constitution.md`.

## Core Components

- **HTML content**
  - Semantic structure (header, main, footer)
  - Hero + CTA

- **Styling**
  - Simple, readable defaults
  - Responsive layout where needed

- **(Optional) JavaScript**
  - Only for progressive enhancement (e.g., simple form interaction)

## Runtime Invariants (recommended)

- The page should render with no runtime errors.
- The primary message (headline + CTA) must be visible without scrolling on common desktop viewports.
- Content should remain usable with CSS disabled (legible document order).
- No network calls (analytics, tracking pixels, third-party scripts) unless explicitly specced.

## Invariants

This architecture is designed to comply with the immutable rules in `_work/proj_constitution.md`.

If any part of this architecture contradicts the Constitution, the Architect (human) must be prompted to update the Constitution or this Architecture to restore structural integrity.

## Vocabulary (canonical)

- **Landing page:** A single page focused on one message and one CTA.
- **CTA:** Call-to-action (button/link that leads to the next step).
- **Progressive enhancement:** Page works without JS; JS adds convenience.
