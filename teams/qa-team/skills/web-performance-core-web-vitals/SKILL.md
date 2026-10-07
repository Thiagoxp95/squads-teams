---
name: web-performance-core-web-vitals
description: Use when testing or improving web page performance — Core Web Vitals (LCP, INP, CLS), page weight, performance budgets and regressions — using field and lab evidence.
---

# Web Performance & Core Web Vitals

## Measure before optimizing
1. Field data first: CrUX / PageSpeed Insights / Search Console at p75 (page-level; origin as a
   labelled fallback) or first-party RUM via the `web-vitals` library.
2. Lab trace under stated conditions (device class, CPU throttle, network): Chrome DevTools
   Performance panel or Lighthouse/PSI lab.
3. Analyse only the insights tied to the failing metric; then inspect the implicated code/resources.
4. Re-measure in the lab after a fix under the same conditions. Never claim a field improvement until
   new real-user data arrives (CrUX is a 28-day window).
No runtime evidence → you may list likely causes, not declare a metric failing.

## Thresholds (p75 of visits)
| Metric | Good | Needs work | Poor |
|---|---|---|---|
| LCP (loading) | ≤ 2.5 s | ≤ 4 s | > 4 s |
| INP (responsiveness) | ≤ 200 ms | ≤ 500 ms | > 500 ms |
| CLS (visual stability) | ≤ 0.1 | ≤ 0.25 | > 0.25 |

## LCP checklist
- [ ] TTFB < 800 ms (CDN, caching, faster backend)
- [ ] LCP element in the initial HTML, not rendered by client JS
- [ ] LCP image discoverable early with `fetchpriority="high"`; preload only if the trace shows late discovery
- [ ] Image sized correctly, AVIF/WebP, not lazy-loaded
- [ ] No render-blocking JS in `<head>`; critical CSS small; fonts use `font-display: swap`

## INP checklist
- [ ] Break up long tasks (> 50 ms); yield to the main thread (`scheduler.yield()`/`setTimeout`)
- [ ] Split input delay / processing / presentation delay in the trace and fix the largest
- [ ] Defer or remove heavy third-party scripts; code-split; avoid huge re-renders (React `useTransition`, memoisation)
- [ ] Avoid layout thrashing (batch DOM reads before writes)

## CLS checklist
- [ ] `width`/`height` or `aspect-ratio` on images, video, iframes, ads, embeds
- [ ] Reserve space for late content (banners, consent bars, async widgets); insert below the viewport
- [ ] Animate `transform`/`opacity`, not layout properties
- [ ] Font fallback metrics matched (`size-adjust`) to avoid swap shifts
Identify the element that moved and the trigger; the shifted element is often not the cause.

## Budgets & regression testing
Set budgets per key page, e.g. JS ≤ 170 KB gzip on mobile, LCP ≤ 2.5 s on mid-range Android at
4G, no long task > 200 ms on load. Enforce in CI with Lighthouse CI assertions or bundle-size
checks; compare against the main-branch baseline, not a single run (take the median of 3–5).

## Report
Page · conditions · field p75 vs. lab values (never mixed as one sample) · failing metric and its
attributed cause (element, script, request) · fix · before/after lab evidence · follow-up to
confirm in field data.

Adapted from https://github.com/addyosmani/web-quality-skills/tree/main/skills/core-web-vitals and https://github.com/addyosmani/web-quality-skills/tree/main/skills/performance (MIT).
