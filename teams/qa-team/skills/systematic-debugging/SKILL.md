---
name: systematic-debugging
description: Use when encountering any bug, failing test, build failure, flaky behaviour or performance problem, before proposing a fix.
---

# Systematic Debugging

## Iron law
NO FIXES WITHOUT ROOT-CAUSE INVESTIGATION FIRST. Symptom patches are failures. Use this
especially under time pressure or when a "quick fix" seems obvious.

## Phase 1 — Root cause investigation
1. Read the full error and stack trace: file, line, error code. Warnings too.
2. Reproduce reliably. Write down exact steps and frequency. Can't reproduce → gather data, don't guess.
3. Check recent changes: `git log`, `git diff`, dependency bumps, config, environment.
4. Multi-component systems (UI → API → service → DB, CI → build → deploy): add temporary
   logging at each boundary — what enters, what exits, which config/env is visible — run once,
   and locate the layer where good data turns bad.
5. Trace bad values backwards up the call chain to their origin. Fix at the source.

## Phase 2 — Pattern analysis
- Find similar code in the repo that works. List every difference from the broken code,
  however small; don't assume a difference "can't matter".
- If following a reference implementation or docs, read them completely.
- Identify hidden dependencies: settings, env vars, ordering, shared state, time.

## Phase 3 — Hypothesis
- Write one hypothesis: "X is the root cause because Y."
- Test it with the smallest possible change, one variable at a time.
- Wrong? Form a new hypothesis — never stack fixes.
- Don't know? Say "I don't understand X" and research or ask.

## Phase 4 — Fix
1. Write a failing test that reproduces the bug (see test-driven-development).
2. Make one fix addressing the root cause. No bundled refactors.
3. Verify: the test passes, the full suite passes, the original symptom is gone.
4. Fix didn't work → back to Phase 1 with the new evidence.
5. Three fixes failed → STOP. Repeated failures usually signal a wrong design or wrong
   assumption. Write up what you know and discuss the architecture before attempt four.

## Flaky tests
Classify first: timing/async (reproduces with repeat runs) · isolation (fails in suite, passes
alone) · environment (CI only) · infrastructure (random, browser/runner errors). Fix the class;
never add sleeps or blanket retries as the fix.

## Report
Symptom · reproduction · root cause (with evidence) · fix · test that guards it · what else
might share the same cause.

## Red flags
"Let me just try…", changing several things at once, fixing where the error surfaced instead
of where the bad value originated, claiming "fixed" without re-running the reproduction.

Adapted from https://github.com/obra/superpowers/tree/main/skills/systematic-debugging (MIT).
