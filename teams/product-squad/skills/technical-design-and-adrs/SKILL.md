---
name: technical-design-and-adrs
description: Use when a feature needs a technical design, an architecture decision must be recorded (ADR), or an approved spec must be broken into reviewable, testable implementation tasks.
---

# Technical Design, ADRs & Task Breakdown

## 1. When to write what
| Situation | Artifact |
|---|---|
| New framework/DB/service, API pattern, security or integration architecture | ADR |
| Feature touching >1 component or with real trade-offs | Design doc (1–3 pages) |
| Bug fix, minor upgrade, config change, implementation detail | Neither — PR description |

## 2. Design doc outline
1. Context & goal (link the story/spec; one-sentence goal)
2. Constraints & non-goals (explicit)
3. Proposed design: components, data flow, interfaces/contracts, data model changes
4. Alternatives considered (at least two, including "do nothing / simplest thing")
5. Risks & mitigations; migration + rollback plan; observability (logs, metrics, alerts)
6. Test strategy: which behaviours are proven at unit / integration / e2e level
7. Open questions with an owner each
Prefer the simplest design that meets the requirements; reuse what the codebase already has.

## 3. ADR (lightweight MADR)
    # ADR-NNNN: <decision in imperative form>
    Status: Proposed | Accepted | Deprecated | Superseded by ADR-XXXX
    Date / Deciders:
    Context: the forces and requirements, facts only.
    Decision drivers: must-haves and should-haves.
    Options: each with pros / cons (≥ 2 real options).
    Decision: "We will …"
    Consequences: positive, negative, risks + mitigation.
One-liner alternative (Y-statement): "In the context of <X>, facing <Y>, we decided for <A> and
against <B>, to achieve <Z>, accepting <cost>."
Rules: ADRs are immutable once accepted — supersede, don't edit. Number sequentially; store in
`docs/adr/`. Record rejected options; they stop the same debate recurring.

## 4. Task breakdown (from an approved design)
- Map files first: which files are created/modified, one responsibility each.
- A task = the smallest unit with its own test cycle that a reviewer could reject independently.
  Fold setup/config/docs into the task that needs them.
- Each task lists: Files (exact paths) · Interfaces consumed/produced (exact names and types) ·
  the failing test to write first · the command to run it · expected result · commit message.
- Steps are single actions: write failing test → run (expect FAIL) → implement minimum →
  run (expect PASS) → commit.
- Add a "Review focus" list: inputs/conditions the spec is silent on that a reasonable user
  would still expect to work (empty, huge, concurrent, offline, unauthorised). Give each a test.
- Order tasks so the system works end-to-end as early as possible (walking skeleton first).

## Quality checks
- [ ] Every significant decision has an ADR or a design section with alternatives
- [ ] Rollback path exists for schema/infra changes
- [ ] Every task names its test and an independently verifiable deliverable
- [ ] No speculative abstractions (YAGNI) — each component has a current consumer

Adapted from https://github.com/wshobson/agents/tree/main/plugins/documentation-generation/skills/architecture-decision-records and https://github.com/obra/superpowers/tree/main/skills/writing-plans (MIT).
