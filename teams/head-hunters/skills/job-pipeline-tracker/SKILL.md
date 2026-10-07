---
name: job-pipeline-tracker
description: Use when creating or updating the job-search pipeline — every role, its status, CV version, contacts, next action and follow-up date — and producing this week's actions and a weekly review.
---

# Job Pipeline Tracker

## Roles sheet (one row per opportunity)
| ID | Company | Role | Link | Source (board / referral / recruiter / direct) | Fit score | CV version | Date applied | Status | Next action | Due | Contact(s) | Pay range | Notes |

Statuses (in order): Saved → Applied → Screening → Interviewing → Offer → Accepted;
closed: Rejected · Withdrawn · No response · Closed (posting removed).

## Contacts sheet (networking)
| Name | Company | Role | How connected | Channel | Last touch | Next touch | Stage (to contact / messaged / replied / chatted / referred) | Notes |

## Rules
- CV versions named `Lastname-CV-<company>-<yyyy-mm-dd>`; keep the job description saved with it.
- Follow up once 7–10 days after applying if no response; then mark No response at 3 weeks.
- Networking: one polite follow-up after ~7 days; after a chat, thank-you within 24 h and a
  light touch every 6–8 weeks.
- Every open row has a next action and a due date; nothing open without one.
- Interviews: add the date/time with time zone (ET/PT) and link the prep doc.
- Ontario employers (25+ staff) must tell interviewed candidates the decision within 45 days —
  set a check date.
- Never store passwords, SIN, passport or bank numbers in the tracker.

## This week (generated every Monday)
| Action | Company/role | Due | Owner (scout / networker / writer / coach / candidate) |
Order: interviews to prep → follow-ups due → applications with deadlines → outreach.

## Weekly review (every Friday)
- Funnel: Saved → Applied → Screening → Interviewing → Offer, with counts.
- Response rate = (Screening or later) ÷ Applied, by source and by CV version.
- Networking: messages sent, reply rate, chats held, referrals gained.
- One change to try next week (only one), and why. Celebrate one win.

## Output
The updated tables (markdown or CSV), this week's actions, the weekly review. Rates must be
arithmetically correct; show numerator/denominator.

## Anti-patterns
Tracking without acting · many follow-ups · changing everything after a bad week · rows with no
next step · losing the job description after the posting closes.

Adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/application-tracker (MIT).
