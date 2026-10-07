---
name: story-test-design
description: Use when a user story is being refined or handed to QA — to sharpen its acceptance criteria, derive executable test cases (happy, edge, negative), and define the data, environment and scope needed to test it.
---

# Story Test Design (in-squad QA)

## 1. Shift left — at refinement ("three amigos": PO + dev + QA)
- Read each AC and ask: how would I prove this? What would make it fail?
- Push back on untestable AC ("fast", "intuitive") until they are observable.
- Ask the edge questions early: empty, max length, duplicates, permissions, offline, concurrency,
  time zones/locale, mid-flow navigation, feature-flag off.
- Agree which checks are automated (unit/integration/e2e) vs. manual/exploratory.

## 2. Derive test cases
| ID | Title | Type | Preconditions | Steps | Test data | Expected result | AC | Priority |
- Types to cover deliberately: happy path · boundary (min, max, just over/under) · negative
  (invalid input, wrong state, unauthorised) · business rules · error/dependency failure.
- Steps are numbered and exact; two testers must execute them identically.
- One expected, observable result per case ("error 'Email required' shown under field"), never
  "works correctly".
- Atomic cases: one check each, traceable to an AC.

## 3. Ready-for-QA handoff (from the dev's actual change, not the story's wish)
- Build/PR reference and what actually changed (incl. shared code touched).
- Setup: environment · accounts/roles · feature flags · seed data.
- Risk areas: shared components, fragile neighbours, recent bug history → targeted regression.
- Out of scope: what QA should not spend time on for this change.

## 4. Execute and close the loop
- Run P0/P1 cases first; then a short timeboxed exploratory pass on the riskiest area.
- Every failure → bug report (see bug-report skill), linked to the story.
- Mark each AC Verified / Failed / Blocked with evidence (screenshot, log, test run link).
- Propose regression cases worth automating (stable, high value, repeated each release).

## Output
Coverage table (AC → cases → status), case list, setup notes, risks, out-of-scope list,
bugs filed, automation candidates.

## Quality checks
- [ ] Every AC has ≥ 1 case; every case maps to an AC (or is flagged as an implicit expectation)
- [ ] Edge and negative cases present, not just happy path
- [ ] Data/env/flag setup specified for reproducibility
- [ ] Expected results specific and verifiable
- [ ] Scope bounded; nearby regression risks named

## Anti-patterns
Happy-path only · "test the story" with no setup · re-testing the whole app for a one-line change ·
cases written from the story text while the build differs · bloated multi-check cases.

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/test-case-writer and https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/qa-handoff-package (MIT).
