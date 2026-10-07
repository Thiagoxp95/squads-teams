---
name: code-review
description: Use when reviewing a pull request or diff against its story/plan, or before merging, to find bugs, design problems and test gaps and give a clear verdict.
---

# Code Review

## Before reading code
1. Read the PR description, linked story/AC, and any design doc or ADR.
2. Check size: > 400 changed lines of logic → ask to split (unless mechanical).
3. Check CI: failing tests or lint = stop and say so.
4. Review read-only: inspect with `git diff base..head`, `git show`; never change the author's branch.

## Pass 1 — high level
- Does it implement what the story/plan asked? Anything missing or beyond scope?
- Is there a simpler approach, or existing code that already does this?
- Does it fit existing patterns and architecture? New dependency justified?
- Are tests proving behaviour, at the right level?

## Pass 2 — line by line
- Correctness: edge cases (empty, null, max, unicode), off-by-one, race conditions, time zones.
- Errors: failures handled, surfaced, not swallowed; no data loss paths.
- Security: input validated at trust boundaries, parameterised queries, authz checked on every
  path, no secrets or PII in code/logs, safe output encoding.
- Performance: N+1 queries, unbounded lists, blocking I/O in hot paths, missing indexes.
- Maintainability: clear names, single-purpose functions, no dead code, no magic numbers.
- Tests: assert real behaviour (not mocks), cover negatives and edges, would fail if the code broke.
- Production readiness: migrations reversible, backward compatible, flags/rollout, docs.

The spec is a vision document: if behaviour the spec doesn't mention would surprise a reasonable
user, it is still a finding. List anything you deliberately set aside as out of scope.

## Feedback style
- Specific and actionable: what, why it matters, suggested fix.
- About the code, never the person. Ask questions when unsure ("What happens if X is empty?").
- Label non-blocking comments `nit:`. Leave formatting to linters.
- Acknowledge what is done well — accurate praise makes the rest credible.

## Output format
    ### Strengths
    ### Issues
    #### Critical (must fix) — bugs, security, data loss, broken functionality
    #### Important (should fix) — design problems, missing requirements, test gaps, poor error handling
    #### Minor (nice to have) — style, small refactors, docs
    (each: file:line · what's wrong · why it matters · how to fix)
    ### Declined to judge — items set aside, with reason
    ### Verdict: Approve | Approve with fixes | Request changes — one-sentence reasoning

## Rules
- Never "LGTM" without reading every changed line.
- Don't mark nits Critical; don't bury a Critical among nits.
- If the plan itself is wrong, say so separately from the implementation.

Adapted from https://github.com/obra/superpowers/blob/main/skills/requesting-code-review/code-reviewer.md and https://github.com/wshobson/agents/tree/main/plugins/developer-essentials/skills/code-review-excellence (MIT).
