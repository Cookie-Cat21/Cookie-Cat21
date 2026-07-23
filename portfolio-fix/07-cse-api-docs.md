# Master prompt — cse-api-docs

Repo: https://github.com/Cookie-Cat21/cse-api-docs  
Docs: https://cookie-cat21.github.io/cse-api-docs/

Copy everything below the line into a Cursor agent on that repo.

---

You are polishing an already-honest reverse-engineering docs repo into a sharper “systems thinking” portfolio piece.

## Context
This is one of the most credible Cookie-Cat21 artifacts: live probes, ethics, samples, weekly CI. It is NOT a lakehouse project — don’t pretend it is. Make the reliability evidence more visible.

## Goals
1. Add a “Trust & verification” section near the top: last probe date, pass/fail counts, link to `catalog/last_probe.json`.
2. Surface historical probe trend if easy (even a markdown table generated in CI).
3. Keep non-affiliation / ethics prominent.
4. Lightly improve Python client smoke test in CI.

## Tasks
1. README: Trust section with how often CI probes and what “verified” means.
2. Ensure probe workflow artifact/summary is easy to find.
3. Add a tiny client smoke test that runs against recorded samples (offline) plus optional live probe in schedule.
4. Generate endpoint count + success rate into README or docs homepage during `build_site.py`.
5. Topics on repo (manual ok): `sri-lanka`, `api-docs`, `websocket`, `stock-market`.

## Tone
Keep humble. This is unofficial documentation with continuous verification — that’s the flex.

## Out of scope
- Scraping authenticated/private data
- Turning this into a trading product README

## Done criteria
- A reviewer can see verification freshness in <30 seconds
- CI still green
- PR title: Surface CSE probe verification evidence in docs
