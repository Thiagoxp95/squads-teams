---
name: exploratory-test-charters
description: Use when planning or running exploratory testing on a feature or release — writing risk-prioritized session charters, choosing tactics and oracles, and reporting session results.
---

# Exploratory Test Charters (Session-Based)

Given only a feature name, still write charters: infer risks, label assumptions, prioritize.

## 1. Risk overview
List the 3–6 areas most worth exploring and why: new/changed, complex, high-impact (money, data,
security), integration-heavy, historically buggy, heavily used.

## 2. Charter format (one per 60–90 min session)
    Charter: Explore <area> with <resources/tactics/data> to discover <information about a risk>.
    Areas: specific screens, flows, inputs, states
    Tactics: (pick from heuristics below)
    Oracles: how you'll recognise a problem
    Setup/data: accounts, roles, flags, devices, seed data
    Timebox & priority: 60/90 min · P1/P2
Write 3–6 charters, highest risk first. Charters give focus, not scripts.

## 3. Test heuristics (tactics)
- Boundaries: empty, 1, max, max+1, negative, decimals, huge files, long/unicode/emoji/RTL text.
- Interruptions: back button, refresh mid-submit, double-click, close tab, sleep/wake, lose network.
- State: expired session, two tabs, stale data, undo/redo, partial save, deleted dependency.
- Roles & permissions: lowest role, removed access mid-flow, direct URL to forbidden pages.
- Data: duplicates, special characters, injection-shaped strings, time zones, DST, locale formats
  (dates, decimals, currency), leap day.
- Concurrency: two users editing the same record; rapid repeated actions.
- Environment: mobile viewport, zoom 200%, slow 3G, dark mode, keyboard only, other browsers.
- CRUD tour: create → read → update → delete → recreate the same thing.

## 4. Oracles (how you know it's wrong)
Spec/AC · consistency with the rest of the product · comparable products · user expectations
("would a user be annoyed or confused?") · data integrity (does the DB/API agree with the UI?) ·
console/network errors · accessibility basics · claims in docs/marketing.

## 5. Session sheet (fill during/after)
    Charter · Tester · Date · Duration (setup / testing / bug investigation %)
    Covered: …        Not covered: …
    Bugs: IDs (one bug report each — see bug-report skill)
    Issues/questions: things that may be bugs or need a decision
    New risks → follow-up charters

## 6. Debrief (5–10 min with the PO/dev)
What was found, what wasn't covered, how confident are we, which follow-up charters next.

## Anti-patterns
"Explore the app" with no mission · no oracles · scripted step lists disguised as charters ·
open-ended sessions · not recording coverage · bugs reported only in chat.

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/exploratory-test-charter (MIT).
