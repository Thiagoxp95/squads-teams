---
name: user-stories-and-acceptance-criteria
description: Use when turning a feature idea, epic, or stakeholder request into INVEST user stories with testable Given/When/Then acceptance criteria, or when splitting an epic into sprint-sized stories.
---

# User Stories & Acceptance Criteria

## Workflow
1. Name the persona (who benefits) — use a real segment, not "the user" when you can.
2. State the capability and the value: `As a <persona>, I want <capability>, so that <outcome>.`
3. Write acceptance criteria in Given/When/Then; one observable outcome per criterion.
4. Cover the AC categories below; add non-functional AC only when they matter for this story.
5. Run the INVEST check; split anything that fails "Small" or "Testable".
6. Record open questions and assumptions under the story — never bury them in AC.

## Story types
| Type | Template |
|---|---|
| Feature | As a <persona>, I want <action> so that <benefit> |
| Improvement | As a <persona>, I need <capability> to <goal> |
| Bug | As a <persona>, I expect <behaviour> when <condition> |
| Enabler | As a developer, I need <technical task> to enable <capability> |

## AC categories (check each)
- Happy path — `Given valid input, When submitted, Then <specific result>`
- Validation — what is rejected, with the exact message
- Error handling — behaviour when a dependency fails
- Permissions/roles — who can and cannot do it
- Performance — only with a number ("within 2 s at p95")
- Accessibility — keyboard-operable, labelled, announced to screen readers

Minimum AC by size: 1–2 pts → 3–4 AC · 3–5 pts → 4–6 · 8 pts → 5–8 · 13+ → split.

## INVEST check
| | Pass if |
|---|---|
| Independent | No blocking dependency on an uncommitted story |
| Negotiable | Says what/why, not how |
| Valuable | The "so that" names a user or business outcome |
| Estimable | Team understands it well enough to size |
| Small | ≤ 8 points / fits one sprint |
| Testable | Every AC is observable and verifiable |

## Splitting an epic
| Technique | Example |
|---|---|
| Workflow step | Checkout → add to cart / pay / confirm |
| Persona | Dashboard → admin view / member view |
| Data type | Import → CSV / Excel |
| Operation (CRUD) | Manage users → create / edit / deactivate |
| Happy path first | Basic flow → errors → edge cases |
Each slice must deliver user-visible value on its own (vertical, not "backend story" + "frontend story").

## Anti-patterns
- "As a system…" stories with no human benefit.
- AC that restate the story ("user can export") instead of the observable result.
- Vague words: "fast", "intuitive", "properly" — replace with a measurable outcome.
- Solution-dictating stories ("add a dropdown") when the need is unclear.

## Output
Story card: title · story statement · AC list · size · priority · assumptions/open questions · dependencies.

Adapted from https://github.com/alirezarezvani/claude-skills/tree/main/product-team/agile-product-owner/skills/agile-product-owner (MIT).
