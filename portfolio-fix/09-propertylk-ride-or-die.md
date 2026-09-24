# Master prompt — PropertyLK ride-or-die (give to another agent)

**Repo:** https://github.com/ArdenoStudio/sri-lanka-property-price-intelligence-platform  
**Live:** https://propertylk-one.vercel.app/  
**Default branch:** `master`

Copy **everything below the line** into a Cursor / Cloud agent opened on that repo.

---

You are turning PropertyLK into Ovindu Karunaratne’s **ride-or-die Data Engineering portfolio flagship** — the one project a senior DE should trust enough to interview him.

## Mission

Harden the existing PropertyLK system into a **production-minded Sri Lanka real-estate data platform** with clear evidence of:

- multi-source ingestion
- raw → clean → enrich → marts
- dedupe / listing history
- geocoding quality
- data quality + freshness
- API + pipeline status
- tests + CI
- honest limitations + failure case study

This is **not** a greenfield rewrite. The repo already has scrapers, API, dashboard, migrations, tests, and source-api docs. **Deepen and prove.** Do not invent a new product.

## Non-goals (do NOT build)

- AI price oracle / chatbot expansion (ChatWidget/Groq can stay, but do not make them the pitch)
- “National intelligence platform” language
- Kafka / Flink / Spark / Iceberg theater for a daily scrape product
- Full frontend redesign
- 10 new dashboards
- Fake scale claims or synthetic “millions of listings” marketing
- Commit-count / agentic-factory nonsense

## Current repo map (use this)

| Area | Paths |
|---|---|
| Scrapers | `scraper/` (`ikman.py`, `ikman_api.py`, `lpw.py`, `lpw_api.py`, `onlineproperty.py`, `cleaner.py`, `geocoder.py`, `metrics.py`, …) |
| Orchestration | `orchestrator.py`, `run_*.py`, `scheduler/`, `.github/workflows/*scrape*`, `aggregate.yml`, `clean.yml`, `geocode.yml` |
| DB | `db/models.py`, `db/migrations/`, `db/connection.py` |
| API | `api/main.py`, `api/estimate_logic.py` |
| Dashboard | `dashboard/` (Vercel) |
| Tests | `tests/` + `tests/fixtures/` |
| Source docs | `docs/source-apis/` (ethics, observability, samples) |
| Ops docs | `RUN_SCRAPERS_README.md`, `SCRAPER_GUIDE.md`, `QUICK_START.md` |

Inspect reality before changing anything. Prefer extending existing patterns over inventing parallel systems.

---

## Target architecture (document + implement gaps)

```text
Sources: ikman / LPW / house.lk / onlineproperty (+ others if already present)
        │
        ▼
Ingestion (source scrapers, rate limits, retries)
        │
        ▼
Raw store (payloads + scrape_runs metadata)
        │
        ▼
Normalize (price/area/type/beds canonical schema)
        │
        ▼
Entity resolution + listing history (dedupe / SCD-style history if feasible)
        │
        ▼
Enrichment (geocode + confidence + district normalization)
        │
        ▼
Quality layer (freshness, nulls, outliers, duplicate rate, source health)
        │
        ▼
Analytics marts (district benchmarks, trends, deal scores, comparables)
        │
        ▼
Products: FastAPI + dashboard + /pipeline/status freshness surface
```

If some layers already exist under different names, **map them in docs** and fill only the missing production signals.

---

## Phase plan (execute in order, commit often)

### Phase 0 — Audit (no feature fluff)

1. Map actual data flow from scrape → DB → API → dashboard.
2. Inventory tables/models in `db/models.py` + migrations.
3. Inventory existing metrics (`scraper/metrics.py`, workflows, any status UI).
4. Inventory tests and CI (`.github/workflows/ci.yml`).
5. Write `docs/CASE_STUDY.md` outline: what exists, what’s missing, what’s overclaimed in README today.
6. Open a working branch: `cursor/propertylk-de-flagship-<suffix>`

Deliverable: short audit section at top of `docs/DATA_PLATFORM.md`.

### Phase 1 — Production metrics that are TRUE

Expose real numbers (query DB / logs / scrape_runs — do not invent):

- raw listings collected
- canonical listings after dedupe (or explain if dedupe is weak/absent)
- sources active
- geocode success rate
- duplicate rate (or “not measured yet” if true — then implement)
- scrape success rate over last N runs
- last successful scrape timestamp **per source**
- median / last pipeline runtime if available

Add:

1. DB/query helpers or API endpoint(s), e.g.:
   - `GET /pipeline/status`
   - `GET /pipeline/metrics`
2. Persist scrape run metadata if incomplete (`scrape_runs`: source, started_at, finished_at, rows_ok, rows_failed, error, duration).
3. Surface these on README and optionally a small pipeline status view if one already exists (`docs/design/pipeline-status-bw.md` suggests UI intent).

### Phase 2 — Data reliability hardening

Implement or harden, in priority order:

1. **Idempotent ingestion** — rerunning a scrape must not explode duplicates.
2. **Canonical schema docs** — `docs/DATA_MODEL.md` with key tables + field meanings.
3. **Dedupe / entity resolution** — document current key; improve if weak; add tests.
4. **Listing history** — if migrations already have history tables, wire/document them; otherwise add minimal SCD2/history for price/status changes.
5. **Geocode confidence** — store/expose success + confidence/failure reasons.
6. **Quality checks** — implement a small quality module or SQL checks:
   - freshness SLA per source
   - null rates on price/area/location
   - outlier price guards
   - duplicate rate
7. **Backfill commands** — document `reprocess_data.py` / clean / geocode / aggregate re-runs as first-class ops.
8. **Runbook** — `docs/RUNBOOK.md`:
   - source HTML/API changed
   - geocoder rate-limited
   - scrape failed partially
   - how to backfill
   - how to verify freshness

### Phase 3 — Analytics marts (keep lean)

Do **not** add a fake warehouse stack unless Postgres marts already fit.

Prefer:

- SQL views / tables for district benchmarks, property-type trends, comparables, deal-score inputs
- OR a tiny `dbt/` project on Postgres **only if** it cleanly fits and CI can `dbt parse`/`dbt test`

Document methodology for deal score + medians in `docs/METHODOLOGY.md` (bedroom/district/type comparables — match real code in `api/estimate_logic.py` / aggregations).

### Phase 4 — Tests + CI (hiring signal)

Raise the proof bar:

1. Fixture-based scraper/mapping tests for each major source (extend `tests/fixtures/`).
2. Cleaner / normalize unit tests.
3. Dedupe tests with known duplicate pairs.
4. API tests for `/pipeline/status` and one listings/trends path.
5. CI must run unit tests on PR; keep scrape workflows separate.
6. Add CI badge to README **only** for the real test workflow.

### Phase 5 — README rewrite for senior DE scrutiny

Replace marketing splash with a DE case-study README.

Required structure:

1. One-sentence problem
2. Live demo + API links
3. Architecture diagram (mermaid)
4. **Current production metrics** (real numbers)
5. Data sources table (cadence, method, fragility)
6. Pipeline stages → code paths
7. Data model summary
8. Data quality & freshness
9. Failure handling & backfills
10. Tests/CI
11. How to run locally (docker-compose / env)
12. Ethics / rate limits / PDPA notes (link `docs/source-apis/ETHICS.md`, existing PDPA tests)
13. Known limitations
14. Link to `docs/CASE_STUDY.md` (“what broke, what we fixed, tradeoffs, 10x scale”)

Tone rules:

- No “An Ardeno Studio Production” hero flex at the top
- No “national platform”
- Prefer: scheduled ingestion, source breakage, dedupe keys, geocode miss rate, freshness

Suggested H1:

`PropertyLK — Sri Lanka property listing data platform`

Suggested tagline:

`Multi-source scrape → clean → geocode → quality checks → market marts → API`

### Phase 6 — Case study doc (interview gold)

Write `docs/CASE_STUDY.md` with 3–5 real engineering stories from the repo/git history/workflows if possible:

- captcha / blocked scrape / API cutover (`tests/API_SCRAPER_CUTOVER_CHECKLIST.md`, ikman API mapping)
- geocoder failures / Nominatim limits
- duplicate listings across sources
- schema drift in source payloads
- partial pipeline runs

For each: symptom → root cause → fix → prevention.

---

## Presentation / GitHub metadata

1. Soften repo description if needed to:
   `Sri Lanka real-estate data platform: multi-source scraping, cleaning, geocoding, quality checks, market analytics API`
2. Ensure homepage remains the live app.
3. Topics (if editable): `data-engineering`, `scraping`, `postgresql`, `fastapi`, `sri-lanka`, `real-estate`, `data-quality`
4. Do not add trophy/profile-view badges.

---

## Engineering quality bar

- Prefer small, reviewable commits with clear messages
- No secrets in git; keep `.env.example` complete
- Don’t break live scrape workflows casually; feature-flag risky changes
- If something can’t be measured yet, say so and implement measurement — never fake metrics
- Match existing code style

---

## Done criteria (all required)

- [ ] `/pipeline/status` (or equivalent) shows last success per source + key health metrics
- [ ] README leads with architecture + real metrics + limitations
- [ ] `docs/DATA_PLATFORM.md`, `docs/DATA_MODEL.md`, `docs/METHODOLOGY.md`, `docs/RUNBOOK.md`, `docs/CASE_STUDY.md` exist and are accurate
- [ ] Dedupe/history/geocode/quality behavior documented and tested where claimed
- [ ] CI runs tests and is linked from README
- [ ] No hype language; no new Kafka/AI theater
- [ ] PR opened titled: `Harden PropertyLK into DE flagship data platform`

## Final PR description must include

1. Before/after credibility changes
2. Exact metrics now shown and how they’re computed
3. Tests added
4. Remaining gaps (honest)
5. Suggested pin text for Ovindu’s GitHub profile (2 lines)

Be ruthless. Depth beats novelty. This repo should feel operated, not demoed.
