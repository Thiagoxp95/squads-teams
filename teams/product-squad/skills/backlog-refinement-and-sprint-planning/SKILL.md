---
name: backlog-refinement-and-sprint-planning
description: Use when grooming or prioritizing a product backlog, checking stories for sprint-readiness, or planning a sprint's scope against team capacity and a sprint goal.
---

# Backlog Refinement & Sprint Planning

## Healthy backlog standard
- Next 2 sprints: detailed, estimated, meet Definition of Ready.
- Following 2–3 sprints: roughly sized, clear intent.
- Beyond: directional only. Buckets: Now · Next · Later · Icebox · Won't Do (with reason).
- No item older than 90 days without a decision — archive, re-justify, or move to Icebox.

## Refinement session (60–90 min, every sprint)
1. Hygiene (20 min): merge duplicates, archive stale items, flag items "ready" for 3+ sprints.
2. Refine top 5–8 items (40 min): read aloud → AC testable? → unknowns → dependencies → estimate.
3. Priority review (10–20 min): does the order reflect current strategy and this week's news?

## Definition of Ready
- [ ] AC clear and testable  - [ ] Design available (if UI)  - [ ] Dependencies resolved or scheduled
- [ ] Estimated by the team  - [ ] Fits one sprint            - [ ] Test scenarios drafted with QA

## Prioritization
Score each candidate 1–5 and weight: Business value 40% · User impact (reach × frequency) 30% ·
Risk/dependency reduction 15% · Effort (inverse) 15%. Break ties with cost of delay.
Priority levels: Critical (data loss, security, blocked users → now) · High (this sprint) ·
Medium (next 2–3 sprints) · Low (backlog). Always write one line of rationale per top-10 item.

## Estimation
Fibonacci points (1,2,3,5,8,13); 13+ = split. Planning poker: simultaneous reveal, outliers
explain, re-vote, reach consensus (never average). T-shirt sizes for roadmap-level items only.

## Sprint planning
1. Capacity = average velocity (last 3–5 sprints) × availability factor
   (1.0 full team · 0.9 one person half out · 0.8 holiday · 0.7 several out).
2. Write a one-sentence sprint goal tied to an outcome, agreed with stakeholders.
3. Commit to 80–85% of capacity; add 10–15% clearly marked stretch.
4. Pull only Ready items in priority order; check dependencies and risks.
5. Break committed stories into tasks (≤ 1 day each).

Template:
    Sprint goal: <outcome>
    Capacity: <n> pts   Committed: <≤85%>   Stretch: <10–15%>
    COMMITTED: [H] US-12 <title> (5) … 
    STRETCH:   [L] US-19 <title> (2) …
    Risks/dependencies: …

## Health metrics
Velocity stable ±10% · commitment reliability > 85% · mid-sprint scope change < 10% · carryover < 15%.

## Definition of Done (default)
Code reviewed · tests passing in CI · AC verified by QA · docs updated · deployed to staging ·
PO accepted · no open critical bugs.

## Output
Groomed backlog (Now/Next/Later), ready vs. needs-work list, archive candidates, sprint plan.

Adapted from https://github.com/VoltAgent/awesome-claude-code-subagents/blob/main/categories/08-business-product/backlog-grooming.md and https://github.com/alirezarezvani/claude-skills/tree/main/product-team/agile-product-owner/skills/agile-product-owner (MIT).
