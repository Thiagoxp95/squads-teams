---
name: web-accessibility-audit
description: Use when auditing or fixing a web page, component or flow for WCAG 2.2 AA accessibility — automated scan plus manual keyboard and screen-reader checks, with prioritized findings.
---

# Web Accessibility Audit (WCAG 2.2 AA)

## Workflow
1. Automated scan of the rendered page (Lighthouse a11y, axe DevTools, `@axe-core/playwright`).
   Automation finds roughly 30–50% of issues; a score of 100 is not conformance.
2. Use failing nodes to locate the component/template; fix at the source.
3. Manual checks (below) on each key flow, not just the home page.
4. Re-run the same scan and manual steps to verify; add an automated a11y assertion to e2e tests.

## Manual checks
- Keyboard only: everything reachable with Tab/Shift+Tab, operable with Enter/Space/arrows,
  logical order, no traps, Escape closes dialogs, focus returns to the trigger.
- Focus visible on every interactive element (2.4.7) and not hidden behind sticky headers/
  cookie bars (2.4.11).
- Skip link to main content (2.4.1); one `<h1>`; headings don't skip levels; landmarks present.
- Screen reader (VoiceOver + Safari, NVDA + Firefox/Chrome): names, roles, states announced;
  form errors and toasts announced (live regions); images have meaningful alt or `alt=""` if decorative.
- Zoom to 200% and reflow at 320 px width without horizontal scroll (1.4.10).
- Contrast: text ≥ 4.5:1, large text ≥ 3:1, UI components and focus indicators ≥ 3:1.
- Color never the only signal (errors, status, charts).
- Target size ≥ 24×24 CSS px (2.5.8); dragging has a single-pointer alternative (2.5.7).
- Forms: visible `<label>` for every field (placeholder isn't a label), errors identified in text
  with how to fix (3.3.1/3.3.3), no re-entering data already given (3.3.7), login without
  cognitive tests — allow paste and password managers (3.3.8).
- Motion respects `prefers-reduced-motion`; nothing flashes > 3×/s; auto-playing media can be paused.
- `<html lang>` set; consistent navigation and help location (3.2.3, 3.2.6).

## Common fixes
| Problem | Fix |
|---|---|
| `<div onClick>` | native `<button>`/`<a href>` |
| Icon-only button | `aria-label` or visually hidden text; `aria-hidden` on the SVG |
| `outline: none` | `:focus-visible` style with ≥ 3:1 contrast |
| ARIA everywhere | native HTML first; ARIA only for custom widgets (follow WAI-ARIA APG) |
| `display:none` for SR text | `.sr-only` class |
| Custom select/menu/dialog | APG keyboard pattern, focus management, `aria-expanded`/`aria-modal` |

## Severity & SLA
Critical (blocks a user group: no keyboard access, missing labels on key controls) → fix before
release · Major (contrast, missing error text) → this sprint · Minor (redundant ARIA, heading
order) → within 2 sprints.

## Report
Per finding: WCAG criterion · severity · page/component · steps (incl. AT + browser) · expected vs.
actual · fix with code. Summary: pass/fail per criterion, top 5 fixes, what was not tested.

Adapted from https://github.com/addyosmani/web-quality-skills/tree/main/skills/accessibility and https://github.com/alirezarezvani/claude-skills/tree/main/engineering-team/a11y-audit (MIT).
