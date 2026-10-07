---
name: bug-report
description: Use when filing a defect or turning "it's broken" into a reproducible, actionable bug ticket a developer can fix without follow-up questions.
---

# Bug Report

## Before filing
1. Reproduce it at least twice; note frequency (always / ~X of Y / once).
2. Minimise: remove steps and data until the bug stops reproducing; keep the shortest path.
3. Search for duplicates; if found, add your evidence there instead.
4. Check it's not environment noise (cache, stale build, test data) — retry on a clean session.

## Template
    Title: <what breaks> in <where> when <key condition>
           e.g. "CSV export fails for > 1,000 rows on Safari 17"
    Severity: Critical | High | Medium | Low   (impact)
    Priority: P1–P4                            (urgency — set by PO if unsure)
    Environment: app version/build · URL/env · OS · browser/device + version · account/role ·
                 relevant data state · feature flags · locale/time zone
    Preconditions: starting state (logged in as X, cart has Y)
    Steps to reproduce:
      1. …
      2. …
    Expected result: …
    Actual result: … (exact error text, wrong value, crash — the observable failure)
    Frequency: always / intermittent (n/m)
    Evidence: screenshot or recording, console errors, failed network request (URL, status,
              response), logs, request/correlation ID, timestamp with time zone
    Notes: workaround · first seen / last known good build · suspected cause (marked HYPOTHESIS)

## Severity guide
Critical: data loss/corruption, security exposure, crash, core flow blocked, no workaround.
High: major function broken or wrong results; painful workaround.
Medium: function impaired; reasonable workaround.
Low: cosmetic, typo, minor layout.

## Rules
- One defect per ticket; link related ones.
- Facts separate from guesses; never present a suspected cause as fact.
- Never invent logs or errors — mark "attach console log" if missing.
- Write for someone with no context: no "the usual flow", no "it".
- Accessibility bugs: cite the WCAG criterion and the assistive tech/browser used.
- Performance bugs: include the metric, the conditions (device, network) and the measurement tool.

## Quality checks
- [ ] Title identifies the bug at a glance
- [ ] Steps start from a known state and reproduce it
- [ ] Expected and actual are separate and explicit
- [ ] Environment captured (the #1 cause of "can't reproduce")
- [ ] Severity and priority distinct; evidence attached or listed

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/bug-report (MIT).
