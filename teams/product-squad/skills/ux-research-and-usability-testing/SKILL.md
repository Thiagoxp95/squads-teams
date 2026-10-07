---
name: ux-research-and-usability-testing
description: Use when planning or synthesizing user research — interviews, usability tests, personas, journey maps — or turning research findings into prioritized design recommendations.
---

# UX Research & Usability Testing

## 1. Frame the research
Turn vague goals into testable questions:
| Vague | Testable |
|---|---|
| "Is it easy to use?" | "Can first-time users complete checkout in < 3 min without help?" |
| "Do users like it?" | "Do users choose design A or B for weekly reporting, and why?" |
Pick the method: interviews (why/needs, 5–8 people) · moderated usability (deep insight, 5–8,
45–60 min) · unmoderated (quick validation, 10–20, 15–20 min) · guerrilla (3–5, 5–10 min) ·
survey (how many — only after you know what to ask) · analytics/funnels (what, not why).

## 2. Interview guide
Warm-up → "Walk me through the last time you…" → probe ("What happened next?", "Why was that
hard?") → workarounds and tools → wrap-up. Ask about past behaviour, not hypothetical futures.
Never ask "Would you use X?" or lead ("Wasn't that confusing?").

## 3. Usability test plan
- Task format: SCENARIO (realistic context) · GOAL (what to achieve, no UI words) · SUCCESS (observable end state).
- Order: warm-up → core tasks → secondary → edge case → free exploration.
- Moderator: think-aloud instructions, neutral prompts ("What are you looking for?"), don't rescue.
- Metrics: completion > 80% · time on task < 2× expert time · error rate < 15% · satisfaction ≥ 4/5 (or SUS ≥ 68).
- Severity per issue: 4 blocks task · 3 major delay · 2 minor friction · 1 cosmetic.

## 4. Synthesis
1. Tag raw notes: [GOAL] [PAIN] [BEHAVIOR] [CONTEXT] [QUOTE].
2. Affinity-cluster into themes; count participants per theme (X/Y), not mentions.
3. For each finding: statement · evidence (quotes, data) · frequency · business impact · recommendation.
4. Prioritize opportunities: frequency × severity × breadth × solvability (each 1–5).

## 5. Personas & journey maps (only when grounded in data)
- Persona: goals, behaviours, frustrations (with counts), context, design implications, sample size.
  Validate with 3–5 real users and support tickets. No invented demographics.
- Journey map: persona + goal + start trigger + end state. For each stage: actions, touchpoints,
  emotion (1–5), pain points, opportunities.

## Output
Research plan (questions, method, participants, script) → findings report (top 3–5 insights first,
evidence, severity, recommendations, open questions) → updated backlog items for the PO.

## Anti-patterns
Leading questions · treating opinions as behaviour · n=1 conclusions · personas from imagination ·
reports with no recommendation · testing only with colleagues.

Adapted from https://github.com/alirezarezvani/claude-skills/tree/main/product-team/skills/ux-researcher-designer (MIT).
