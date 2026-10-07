---
name: ui-design-and-design-systems
description: Use when designing or reviewing UI screens, choosing visual direction, writing interface copy, or creating/maintaining design tokens and component guidelines for a design system.
---

# UI Design & Design Systems

## 1. Ground it in the product
Before designing, state: subject/product, audience, the screen's primary job, and the existing
design system (reuse it if one exists). Use real content, not lorem ipsum.

## 2. Two-pass process
Pass 1 — plan a compact token set:
- Color: 4–6 named hex values with roles (surface, text, accent, feedback states).
- Type: 1–2 families with clear roles and a type scale; body lines < 80 characters.
- Layout: grid, spacing scale (e.g. 4/8 px base), alignment rule; sketch options in ASCII.
- Principles: 2–3 sentences on what makes this product's UI its own.
Then review the plan against the brief: anything that reads as a generic default (identical
rounded cards with grey shadows, gradient washes, ALL-CAPS eyebrow labels on every heading,
decorative 01/02/03 numbering for non-sequences) gets revised. Then build.
Pass 2 — critique your own render (screenshots if available) and remove one unnecessary element.

## 3. Quality floor (non-negotiable)
Responsive to 320 px · visible keyboard focus · respects reduced motion · text contrast ≥ 4.5:1
(3:1 for large text/UI parts) · touch targets ≥ 24×24 px (44 px preferred on mobile) · states
designed: empty, loading, error, success, disabled, long content.

## 4. Interface copy
- Name things by what users understand ("Notifications", not "Webhook config").
- Buttons say exactly what happens: "Save changes", not "Submit". Keep the verb consistent
  through the flow (Publish → "Published").
- Errors: what happened + how to fix it; no apologies, no vagueness. Empty states invite action.
- Sentence case, plain verbs, no filler.

## 5. Motion
Use motion to show what changed after a user action. Avoid scattered entrance animations; one
deliberate moment beats many.

## 6. Design tokens
- Three tiers: primitive (`blue-600`) → semantic (`text-primary`, `surface-elevated`,
  `interactive-primary`) → component (`button-bg`). Components use semantic/component tokens only.
- Name by purpose, never by appearance (`text-secondary`, not `grey-dark`).
- Theme via CSS custom properties; light/dark and high-contrast swap semantic values only.
- Version tokens like an API (semver); deprecate with a migration note, never silently delete.
- Watch for: token sprawl, hard-coded values in components, missing dark-mode mappings.

## 7. Component spec (per component)
Purpose · anatomy · variants and sizes · states · keyboard/ARIA behaviour · content rules ·
do/don't examples · tokens used.

## Output
Token plan + rationale, annotated screens/flows covering all states, copy deck, and any new
components specified for the design system.

Adapted from https://github.com/anthropics/skills/tree/main/skills/frontend-design (Apache-2.0; condensed and modified) and https://github.com/wshobson/agents/tree/main/plugins/ui-design/skills/design-system-patterns (MIT).
