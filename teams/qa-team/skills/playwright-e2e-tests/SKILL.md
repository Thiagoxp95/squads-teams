---
name: playwright-e2e-tests
description: Use when writing, fixing, de-flaking or reviewing Playwright end-to-end tests for a web app.
---

# Playwright E2E Tests

## Before writing
Read `playwright.config.*` (testDir, baseURL, projects, retries, trace), existing specs, fixtures,
page objects and auth setup (`storageState`). Match project conventions (TS vs JS, POM, fixtures).
E2E covers critical user journeys only; push logic checks down to unit/integration.

## Writing rules
- Structure: `test.describe('<feature>')` → `test('should <behaviour>')` → Arrange / Act / Assert.
- Locator priority: `getByRole` → `getByLabel` → `getByText` → `getByPlaceholder` → `getByTestId`.
  CSS/XPath only as a last resort.
- Web-first assertions that auto-retry: `await expect(locator).toBeVisible()/toHaveText()/toHaveURL()`.
- Navigate relative to baseURL: `page.goto('/settings')`.
- Every Playwright call awaited. Each test independent: own data via API/fixture, unique IDs.
- Include at least one error/edge case per happy path.
- Page object when a page uses 5+ locators; fixture for shared setup (auth via storageState).
- Never: `waitForTimeout`, `page.$`/`$$`, `expect(await el.textContent())`, `networkidle` as a
  correctness wait, shared mutable state, test-order dependencies.

## Verify a new test
`npx playwright test <file> --reporter=list` → green, then `--repeat-each=10` → 10/10.
Fails? Fix the test; if the app is wrong, file a bug instead of bending the test.

## Fixing failing/flaky tests
1. Reproduce: run once; if green, `--repeat-each=20`, then `--fully-parallel --workers=4`.
2. Capture a trace: `--trace=on --retries=0`; read actions, network and console.
3. Classify and fix:
| Class | Signal | Fix |
|---|---|---|
| Timing/async | fails intermittently everywhere | web-first assertions, await the specific response, add missing awaits |
| Isolation | fails in suite, passes alone | per-test data, remove shared state, clean up |
| Environment | CI only | match viewport/locale/timezone/fonts, pin browser, check env vars |
| Infrastructure | random browser errors | fewer workers (OOM), install deps, raise CI timeouts |
4. Confirm 10/10 on repeat. Retries (`retries: 2` in CI) and `trace: 'on-first-retry'` are
   diagnostics, never the fix.

## Review checklist (score each file 1–10)
Critical: waitForTimeout · non-web-first assertions · hard-coded URLs · CSS/XPath where a role
exists · missing await · shared state · order dependence.
Warning: tests > 50 lines · generic names · magic strings · missing negative cases · `page.evaluate`
for locator work · describe nesting > 2.
Info: missing POM/fixtures · inline data · no a11y check (`@axe-core/playwright`) · console errors unchecked.

## Output
Spec file(s) + supporting POM/fixtures, run result (incl. repeat run), behaviours now covered,
and gaps remaining.

Adapted from https://github.com/alirezarezvani/claude-skills/tree/main/engineering-team/playwright-pro (MIT).
