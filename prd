# PRD — Shortlist
**Version:** 0.1 (prototype)  
**Status:** Working prototype. Built with Lovable. Not production hardened.  
**Author:** Yuvraj Gulati  
**Last updated:** 2026-05-31

---

## 1. Objective

Replace generic job board scrolling with a resume-scored, filterable, persistent job discovery feed — giving job seekers a clear fit signal, noise-free triage, and a unified view across sources.

---

## 2. Goals

1. Replace generic job board scrolling with a resume-scored, filterable feed
2. Give every job a clear "how well does this fit me" signal
3. Remember user decisions (hide, save) so the same noise never returns
4. Offer a fast resume-independent search for casual browsing

---

## 3. Out of Scope — v0.1

- Team or recruiter workflows
- One-click apply or autofill on third-party sites
- Native mobile apps
- Email or push alerts
- ML-trained ranking — scoring is a transparent heuristic in v0.1

---

## 4. User Stories

**Resume Upload**
1. Upload a PDF resume directly from the dashboard
2. Re-upload to replace the parsed profile

**Feed**
3. See jobs scored against my resume, newest first
4. Filter by keyword, location, remote type, date posted, salary
5. Hide a job and never see it again
6. Save a job and find it later
7. Open the original posting in a new tab

**Universal Search**
8. Search the live job market by keyword and location, without a resume

**Drafts**
9. Draft application answers per job, with autosave

---

## 5. Functional Requirements

### Resume Upload and Parsing
- PDF only, max 5 MB
- Parsed into structured fields: headline, skills, years of experience, work history, education
- Re-upload overwrites the prior parse atomically
- No login or signup required — resume upload happens directly on the dashboard

### Job Ingestion
- Primary source: LinkedIn via Apify actor
- Live fallback scrapers run when LinkedIn returns too few results
- Deduplicated on (company, title, location) before insert

### Match Scoring

Heuristic score from 0 to 100 stored on `jobs.match_score`:

| Score | Label |
|---|---|
| null | Unscored |
| 90 to 100 | Excellent match |
| 80 to 89 | Strong match |
| 70 to 79 | Good match |
| 50 to 69 | Weak match |
| 0 to 49 | Low match |

### Dashboard Filters
- Search box: matches title, company, description, remote type, required experience, keywords
- Location: free-text contains match
- Remote type: On-site, Hybrid, Remote
- Date posted: 24h, Week, Month, Any
- Salary: min and max sliders
- Easy apply: toggle
- Sort: Best match, Newest, Salary

### Hide and Save
- Hidden jobs disappear from the feed permanently for that user
- Saved jobs removed from unprocessed feed and stored for later review

### Universal Search
- Route: `/search`
- Inputs: keyword, location, remote-only checkbox
- Deduplicated by role and company, sorted newest first, capped at 100 results
- Resume match score not shown on this page

### Application Drafts
- Per-job draft container with question and answer rows
- Autosave on blur

---

## 6. Non-Functional Requirements

| Area | Target |
|---|---|
| Performance | Dashboard first paint under 1.5s on 4G |
| Accessibility | WCAG AA: semantic HTML, keyboard nav, visible focus |
| Responsive | 375px to 1440px+ |
| Errors | Every route has error and not-found boundaries |
| SEO | Unique title and meta per route, single H1 |

---

## 7. Data Model

| Table | Purpose |
|---|---|
| `profiles` | One row per user, parsed resume snapshot |
| `work_experiences` | Resume jobs |
| `education` | Resume education |
| `jobs` | Ingested postings with match_score, hidden_at, saved_at |
| `runs` | Ingestion audit log |
| `application_drafts` | Per-job draft container |
| `application_answers` | Q and A inside a draft |

Row-Level Security enforced on every user-scoped table. Roles in a separate `user_roles` table.
