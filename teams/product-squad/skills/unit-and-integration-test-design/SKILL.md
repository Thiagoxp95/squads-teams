---
name: unit-and-integration-test-design
description: Use when designing or reviewing unit and integration tests — choosing the test level, deciding what to mock, and making sure each test would actually catch a regression.
---

# Unit & Integration Test Design

## Pick the level (cheapest level that can catch the break)
| Behaviour | Level |
|---|---|
| Pure logic, parsing, calculations, branching | Unit |
| Your code's contract with DB, queue, HTTP API, file system | Integration (real dependency in a container or test instance) |
| Contract between your services | Contract tests (consumer-driven) |
| A user journey across UI + backend | E2E (few, critical only) |
Aim for many fast unit tests, fewer integration tests, a handful of E2E.

## Rule 1 — every test names the break it catches
Before writing the body, answer: what production change would make this fail? Can't name one →
redesign the test around observable behaviour.
- Expected values are literals or hand-checked fixtures. Never compute the expectation with the
  code under test (mirror assertions always pass).
- No change detectors: don't assert a constant's value or exact private structure; assert the
  behaviour that depends on it ("6th retry never happens", not `MAX_RETRIES === 5`).
- Test your contract, not the framework's (don't test that the router calls a handler).
- Table-driven tests for input variations: `[input, want]` rows with literal wants.

## Rule 2 — exercise the real thing
- Mock only what is slow, external or nondeterministic (network, clock, randomness, payment gateway).
- Never assert that a mock exists or was called unless the call *is* the contract (e.g. "email
  sent once with this payload") — then assert arguments and count precisely.
- Learn a dependency's side effects before mocking it; mock at the lowest level that keeps what
  the test depends on real.
- Give each branch (success, error, malformed response, timeout) its own fixture.
- Keep test-only helpers in test utilities, never in production classes.

## Integration test checklist
- [ ] Real DB/queue in a container; schema from real migrations
- [ ] Each test owns its data (transactions rolled back or unique keys); runs in any order
- [ ] Covers failure modes: timeout, 4xx/5xx, constraint violation, retry/idempotency
- [ ] Clock and randomness injected and controlled
- [ ] No sleeps; poll for a condition with a timeout instead

## Coverage
Use coverage to find untested branches, not as the goal. 100% lines with mock-only assertions
protects nothing; mutation testing (e.g. Stryker, mutmut) shows whether tests catch breaks.

## Review questions
For each test: what bug does it catch? Would it fail if the code returned a hard-coded value?
Is anything asserted that only the mock controls? Does it run alone, in parallel, in CI?

Adapted from https://github.com/obra/superpowers/blob/main/skills/test-driven-development/writing-good-tests.md (MIT).
