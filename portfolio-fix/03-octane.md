# Master prompt — Octane

Repo: https://github.com/ArdenoStudio/octane  
Live: https://octane-smoky.vercel.app

Copy everything below the line into a Cursor agent on that repo.

---

You are hardening Octane so it reads as a credible data product for DE hiring, not only a polished consumer app.

## Context
Octane is already one of the most “real” projects (scheduled scrapes, CI, alerts, API). Improve the DE signals: freshness, source reliability, schema/API contracts, failure modes. Do not turn it into fake Kafka/Flink theater.

## Goals
1. Add a Data reliability section to README (or docs/DATA_RELIABILITY.md linked from README).
2. Document scrape cadence, sources (CPC/LIOC), what happens on source HTML changes.
3. Document public API contract and versioning stance.
4. Keep product marketing, but put engineering truth near the top for technical readers.

## Add to README (near top after short product blurb)
### Data pipeline
- Sources and schedule (5x daily etc. — verify from workflows, don’t guess)
- Storage / history model
- Alert dispatch path
- Failure modes: scrape miss, partial parse, conflicting CPC vs LIOC
- How to see last successful scrape timestamp

### API
- Base URL
- Key endpoints
- Rate limits
- Stability promise (best-effort unofficial public data)

### Reliability
- Link CI + scrape workflow badges (keep)
- Note fixture-based scraper tests if present; add if missing

## Engineering tasks
1. Verify workflow schedules in `.github/workflows/` and document accurately.
2. If missing, add a small `/health` or docs section exposing last scrape success per source (or document where operators see it today).
3. Ensure scraper tests use fixtures; add one regression fixture if gaps exist.
4. Soften unverifiable AI claims (“AI revision outlook”) with methodology or “experimental” label.
5. Add LICENSE if missing.

## Tone
- No overclaiming “official” fuel data
- Emphasize unofficial scraping + best-effort freshness
- This is a focused data product; that focus is a strength

## Out of scope
- Rewriting the whole frontend
- Adding Spark/Kafka unless there is a real need

## Done criteria
- Technical reader can explain freshness + failure handling in 1 minute
- API contract is obvious
- PR title: Document Octane data reliability and API contract for DE scrutiny
