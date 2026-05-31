# MVP vs Roadmap — Shortlist

## What v0.1 Solves

The MVP focuses on the single most valuable loop: sign up, upload a resume, get a scored feed, triage it cleanly, and search freely. Everything else is noise until this core loop is validated.

---

## v0.1 — In Scope

| Feature | Status |
|---|---|
| Email and password authentication (min 8 chars, email validation) | Included |
| Resume upload and parsing (PDF, max 5 MB) | Included |
| Job ingestion via LinkedIn (Apify) | Included |
| Heuristic match scoring 0 to 100 | Included |
| Filterable dashboard (keyword, location, remote, date, salary) | Included |
| Hide jobs permanently | Included |
| Save jobs for later | Included |
| Universal Search (keyword and location, no resume required) | Included |
| Application drafts with autosave | Included |
| Responsive UI (375px to 1440px+) | Included |

---

## Roadmap — Post v0.1

### Phase 2 — Smarter Scoring and Automation

| Feature | Rationale |
|---|---|
| Background ingestion on a schedule | Currently user-triggered — automation removes friction |
| Embeddings-based ranker to replace heuristic scoring | More accurate fit signal, less rule-based |
| Email digest of high-match jobs | Brings the product to the user instead of requiring them to return |

### Phase 3 — Apply Assistance

| Feature | Rationale |
|---|---|
| LLM-generated cover letters per job | High-demand feature — reduces the most painful part of applying |
| One-click save from LinkedIn via browser extension | Removes platform switching from the workflow entirely |
| Autofill assistance on third-party apply pages | Completes the end-to-end job application workflow |

### Phase 4 — Power User Features

| Feature | Rationale |
|---|---|
| Multi-resume support, one per role family | Active seekers apply to different role types with different resumes |
| Application tracking (status, notes, interview stages) | Closes the loop from discovery to outcome |
| Salary benchmarking per role and location | Adds negotiation context to the job discovery experience |
| Company research panel inline | Reduces context switching for research during triage |
