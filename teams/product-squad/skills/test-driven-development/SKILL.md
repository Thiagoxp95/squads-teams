---
name: test-driven-development
description: Use when implementing any feature, bug fix, refactor or behaviour change, before writing implementation code.
---

# Test-Driven Development

## Iron law
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST. Wrote code before the test? Delete it and
start from the test. (Exceptions only with the human's OK: throwaway prototypes, generated
code, pure config.)

## Red → Green → Refactor
1. RED — write one minimal test for one behaviour. Clear name describing the behaviour; real
   code, mocks only for slow/external dependencies.
2. VERIFY RED (mandatory) — run it. It must FAIL (not error) for the expected reason: the
   feature is missing, not a typo. Passes immediately? You're testing existing behaviour — fix the test.
3. GREEN — write the simplest code that passes. No extra options, no "while I'm here".
4. VERIFY GREEN (mandatory) — run the test AND the project's full suite. Output clean (no
   warnings). Test fails → fix code, not the test.
5. REFACTOR — only when green: remove duplication, improve names, extract helpers. Stay green.
6. Repeat with the next behaviour.

## Good tests
- One behaviour per test; "and" in the name → split it.
- Before writing, name the production change that would make it fail.
- Expected values are literals or hand-checked fixtures, never computed by the code under test.
- Assert observable behaviour, never that a mock was called (unless the call *is* the contract).
- Hard to test = hard to use: simplify the interface instead of piling on mocks.

## Bug fixes
Reproduce the bug as a failing test first. Watch it fail. Fix. Watch it pass. For regression
proof: revert the fix → test must fail → restore.

## Excuses that mean "start over"
| Excuse | Reality |
|---|---|
| "Too simple to test" | Simple code breaks; the test takes 30 seconds |
| "I'll test after" | Tests written after pass immediately and prove nothing |
| "Already tested manually" | Not repeatable, not recorded |
| "Keep the code as reference" | You'll adapt it — that's testing after |
| "Need to explore first" | Fine — throw the spike away, then TDD |

## Done checklist
- [ ] Every new function/behaviour has a test that was seen failing first
- [ ] Each failure was for the expected reason
- [ ] Minimal code written to pass
- [ ] Full suite passes; output pristine
- [ ] Edge and error cases covered
- [ ] Any failing test you saw (even unrelated) is reported by name

Adapted from https://github.com/obra/superpowers/tree/main/skills/test-driven-development (MIT).
