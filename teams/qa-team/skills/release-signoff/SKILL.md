---
name: release-signoff
description: Use when deciding whether a release is ready to ship — producing a QA go/no-go report from test results, open defects, coverage and residual risk.
---

# QA Release Sign-off

## Inputs (mark unknowns as risks; never invent results)
Release version/scope and date · what was tested (areas, levels) with results · what was NOT
tested · open defects with severity/workarounds · rollback/feature-flag options · exit criteria.

## Defect triage rubric
| Severity | Meaning | Default blocker? |
|---|---|---|
| Critical | data loss, security hole, crash, core flow unusable, no workaround | Yes |
| High | major feature broken or wrong results; workaround painful | Usually |
| Medium | feature impaired, reasonable workaround | No — fix next |
| Low | cosmetic/minor | No |
Severity = impact; priority = urgency. Record both. Re-test every fix and its neighbours.

## Decision rules
- No-go: any open Critical; any P0 test failing; exit criteria unmet with no agreed exception.
- Go with conditions: only High/Medium open with workarounds, rollback or flag available, and
  named owners/dates for each condition.
- Go: exit criteria met, residual risk accepted by the product owner.
A thin-coverage area is a risk to state, not a reason to stay silent.

## Report format
    ## QA Sign-off: <release> — <date>
    **Recommendation:** Go | Go with conditions | No-go — <headline reason>
    **Scope:** what ships
    **Testing summary:** areas × levels, pass/fail counts and rate, automation run links
    **Not tested:** areas and why (time, env, out of scope)
    **Open defects:**
    | ID | Severity | Area | Impact | Workaround | Blocker? | Owner |
    **Coverage & residual risk:** well-covered vs. thin areas; honest risk of shipping now
    **Conditions to ship:** concrete, checkable items with owners
    **Rollback / mitigation:** rollback steps or flag, monitoring to watch (errors, key metrics), hotfix path
    **Sign-off:** who recommends, what they attest to, who accepts the residual risk

## Post-release
Watch error rates and key business metrics for the agreed window (e.g. 24–48 h); log escaped
defects and feed them into the next regression plan.

## Quality checks
- [ ] Recommendation is up front with the reason
- [ ] Tested and untested areas both listed
- [ ] Every open defect has severity, impact and blocker status
- [ ] Conditions are checkable, with owners
- [ ] Rollback/mitigation present
- [ ] No result, pass rate or test run is invented

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/qa-release-signoff (MIT).
