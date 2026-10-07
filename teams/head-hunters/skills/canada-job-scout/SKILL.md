---
name: canada-job-scout
description: Use when searching for product-management job openings in Canada — LinkedIn, Indeed.ca, Job Bank, startup boards and company career pages — and scoring which ones are worth applying to.
---

# Canada Job Scout (Product Management)

## Channels and how to search them
| Channel | How |
|---|---|
| LinkedIn Jobs | Title search + location (city or "Canada" + Remote); filters: date posted (past week), experience level; save searches with alerts. Prefer roles < 7 days old. |
| Indeed.ca | `title:("product manager" OR "product owner") -intern -marketing`; location city; sort by date; alerts. |
| Job Bank (jobbank.gc.ca) | Government board; search by title and city; "Create an alert with this search" for daily emails; Job Match profile ranks fit. Good for public sector and employers open to newcomers. |
| Startup boards | Work In Tech / Communitech (national startup board), Wellfound, YC "Work at a Startup" (filter Canada), BuiltIn-style city boards, Eluta.ca (aggregates employer sites). |
| Career pages | Target-company list from the strategist; check "Careers" pages weekly (Greenhouse, Lever, Ashby, Workday). Many roles appear here first. |
| Google X-ray | `site:boards.greenhouse.io OR site:jobs.lever.co OR site:jobs.ashbyhq.com "product manager" (Toronto OR Vancouver OR "Remote - Canada")` |
| Recruiters/agencies | Tech recruiters in Toronto/Vancouver post on LinkedIn; track them as contacts, not jobs. |

## Search terms
Titles: "product manager", "senior product manager", "product owner", "technical product manager",
"group product manager". Add domain words (fintech, payments, B2B SaaS, marketplace, growth).
Exclude: intern, co-op, marketing product manager (if not wanted), "product specialist" (sales).
French-language roles: "gestionnaire de produit", "chef de produit" (Montréal) — only if French is viable.

## Read the posting
- Location model: on-site / hybrid (days per week) / remote-Canada (province limits are common).
- Work authorization: "must be legally entitled to work in Canada" is a lawful question; note any
  sponsorship mention.
- Ontario (employers with 25+ staff, from 2026-01-01): public postings must show expected pay
  (range ≤ $50k wide, unless > $200k), disclose AI screening, say whether the vacancy exists, and
  may not require "Canadian experience". BC also requires pay ranges. Missing pay = ask early.
- Freshness and volume: > 30 days old or reposted repeatedly → lower priority.

## Fit score (0–100, log the breakdown)
Must-haves met (40) · domain/industry match (20) · seniority match (15) · location/work-model fit
(10) · salary in range (10) · warm contact available (5).
≥ 70 apply + network · 50–69 apply only with a contact or strong angle · < 50 skip (note why).

## Daily/weekly routine
Daily (20 min): check alerts, add new roles ≥ 50 to the pipeline with the job description saved
(postings disappear). Weekly: scan target career pages, refresh X-ray searches, report a
summary to the strategist: new roles, top 5 by score, any market signals (who is hiring, layoffs).

## Output per role
Company · title · link · location/model · pay range · posted date · fit score + breakdown · key
keywords for the résumé writer · possible contacts for the networker · deadline.

## Guardrails
Never apply on the candidate's behalf without approval. Don't scrape behind logins or break
site terms; respect LinkedIn limits. Flag scam signs (pay to apply, upfront fees, chat-only
interviews, requests for SIN/bank details before an offer).

Original skill, informed by https://www.jobbank.gc.ca/findajob, https://www.ontario.ca/document/your-guide-employment-standards-act-0, https://betakit.com/communitech-takes-over-canadian-tech-startup-job-board-prospect/; X-ray/Boolean technique adapted from https://github.com/mohitagw15856/pm-claude-skills/tree/main/skills/boolean-search-builder (MIT).
