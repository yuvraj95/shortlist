# Known Limitations — Shortlist v0.1

This is an honest account of what is not production-ready in the current prototype. Shipping fast means making tradeoffs. These are the ones I made consciously.

---

## Current Limitations

**No automated tests**
Manual QA only. Not suitable for production without a test suite.

**Scraper fragility**
Job ingestion uses Apify actors to scrape LinkedIn. LinkedIn frequently changes its UI and rate-limits scraping. The ingestion pipeline can break without warning when LinkedIn updates. A production version would need a more resilient multi-source ingestion strategy with monitoring and fallback handling.

**Heuristic match scoring**
Match scores are rule-based heuristics, not ML-calibrated. They provide a reasonable signal but are not semantically sophisticated. A production scorer would use embeddings or a fine-tuned ranker to better understand contextual fit between a resume and a job description.

**No background jobs**
Job ingestion is user-triggered. There is no scheduled background process to keep the feed fresh automatically. Users need to manually trigger a refresh to see new postings.

**No notifications**
No email or push notification system. Users must return to the app to see new high-match jobs.

**No multi-resume support**
A single resume per user. Active seekers applying across multiple role families cannot maintain separate profiles.

**No apply workflow**
Shortlist helps you find and triage jobs but does not assist with the application itself beyond draft storage. One-click apply and autofill on third-party sites are out of scope for v0.1.

**No password reset**
Password recovery is not implemented in v0.1. Users who forget their password cannot currently recover access.

---

## Why I Shipped Anyway

A prototype with known limitations that solves a real problem is more valuable than a perfect product that never ships. These limitations are documented, prioritised, and mapped to the roadmap. The core loop — sign up, upload, score, filter, triage — works. That is what v0.1 needed to prove.
