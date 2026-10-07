---
name: test-strategy-and-regression-plan
description: Use when defining the QA approach for a feature, release or product — test strategy, risk-based test plan, coverage targets, regression tiers and entry/exit criteria.
---

# Test Strategy & Regression Plan

## Inputs (infer and label if missing)
Feature/system spec · tech stack · existing coverage and tools · release cadence · risk level ·
timeline · who tests (devs, QA, both).

## 1. Scope
In scope (functions, integrations, user flows) · Out of scope (≥ 1 explicit exclusion + why) ·
Assumptions (mocks, data, environments).

## 2. Risk assessment — drives everything else
| Area | Likelihood | Impact | Why | Priority |
|---|---|---|---|---|
| Payments | Med | High | money movement, regulatory | P0 exhaustive |
| Auth | Med | High | security boundary | P0 exhaustive |
| Notifications | Med | Med | external dependency | P1 happy + key failures |
| Copy changes | Low | Low | reversible | P2 smoke |
Risk signals: new/changed code, complexity, integrations, money/data/security, bug history, usage volume.

## 3. Test levels (name a concrete tool for each)
- Unit (devs): logic and edge cases; coverage target on new code (e.g. 80% lines, 100% critical paths).
- Integration/API: contracts, DB, third parties (e.g. Supertest, pytest + testcontainers, Pact).
- E2E: top 3–5 critical journeys only (e.g. Playwright).
- Exploratory: chartered sessions on the top risks.
- Non-functional when a risk row calls for it: performance (k6, targets like p95 < 300 ms at N rps),
  security (OWASP ZAP, authz checks), accessibility (WCAG 2.2 AA), compatibility (browser/device matrix).

## 4. Prioritized test outline
P0 must pass before merge · P1 must pass before release · P2 may ship with tracked known issues.
Every P0 risk row has ≥ 1 P0 test case.

## 5. Regression tiers
| Tier | When | Scope |
|---|---|---|
| Smoke | every build/deploy | critical paths only, < 10 min |
| Targeted | each change | changed area + direct dependencies + shared components |
| Full | major/risky release | broad core coverage |
State what is de-scoped and the residual risk. Automate stable, high-value, repetitive cases first;
keep flaky or rarely-run checks manual until stabilized. Prune the suite every quarter.

## 6. Environments & data
Environments per level · test accounts by role/state · seed data · stubs · PII-safe data.

## 7. Entry / exit criteria
Entry: build deployed to test env, smoke green, stories meet Definition of Ready.
Exit (measurable): all P0/P1 pass · no open Critical/High · coverage target met · performance/
security/a11y checks done where in scope · known issues documented with owners.

## 8. Metrics to report
Pass rate by priority · defects by severity and area · escaped defects · flaky-test rate ·
automation coverage of regression · cycle time to verify a fix.

## Anti-patterns
Generic coverage targets with no risk table · blank out-of-scope · "some framework" · DoD = "QA is
happy" · running everything every time · silently dropping coverage.

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/test-strategy-doc and https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/regression-test-plan (MIT).
