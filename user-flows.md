# User Flows — Shortlist

**Live Prototype:** [shortlist-job.lovable.app](https://shortlist-job.lovable.app/signup)

---

## Flow 1 — Sign Up and Resume Upload

**Actor:** New user  
**Goal:** Create an account, upload a resume, and see a personalised scored feed

1. User lands on Shortlist and clicks Sign Up
2. Enters email and password (minimum 8 characters, email format validated)
3. Lands on the dashboard
4. Uploads a PDF resume (max 5 MB)
5. Resume is parsed into structured profile: headline, skills, experience, education
6. Feed populates with scored job postings
7. Match scores visible on each job card immediately

---

## Flow 2 — Sign In

**Actor:** Returning user  
**Goal:** Access existing feed, saved jobs, and drafts

1. User lands on Shortlist and clicks Sign In
2. Enters email and password
3. Lands on dashboard — feed, saved jobs, and drafts all intact from last session

---

## Flow 3 — Browse and Triage the Feed

**Actor:** Active job seeker  
**Goal:** Find relevant jobs and clean up noise quickly

1. User opens dashboard — sees job cards sorted by best match or newest
2. Each card shows: job title, company, location, remote type, salary, match score label
3. User applies filters: keyword, location, remote type, date posted, salary range
4. Feed updates to show matching results
5. For irrelevant jobs: clicks Hide — job disappears permanently from the feed
6. For interesting jobs: clicks Save — job moves to Saved view for later
7. To view full details: clicks job card — original posting opens in a new tab
8. Feed gets progressively cleaner as more jobs are hidden over time

---

## Flow 4 — Universal Search

**Actor:** Passive browser or signed-in user  
**Goal:** Search the live job market without resume scoring

1. User navigates to `/search`
2. Enters keyword and location
3. Optionally toggles remote-only checkbox
4. Live results fetched — deduplicated by role and company, newest first, capped at 100
5. No match score shown — results are unscored
6. User browses results and opens postings in new tabs

---

## Flow 5 — Resume Re-upload

**Actor:** Active seeker who has updated their resume  
**Goal:** Refresh profile so match scores reflect the updated resume

1. User navigates to Profile settings
2. Uploads a new PDF resume
3. New parse overwrites the prior profile atomically
4. Match scores on existing jobs recalculate against the updated profile
5. Feed refreshes with updated scores

---

## Flow 6 — Application Drafting

**Actor:** Active seeker preparing to apply  
**Goal:** Draft and save application answers per job without losing work

1. User opens a saved job from the Saved view
2. Opens the Application Draft panel for that job
3. Adds a question (e.g., "Why do you want to work here?")
4. Types an answer — autosaved on blur
5. Adds more Q and A rows as needed
6. Returns to the draft at any time — all answers persist
