# Master prompt — PropertyLK

Repo: https://github.com/ArdenoStudio/sri-lanka-property-price-intelligence-platform

Copy everything below the line into a Cursor agent on that repo.

---

You are hardening PropertyLK for a Data Engineering job hunt.

## Context
This is the strongest real-world messy-data project for Ovindu’s DE profile. Seniors care about ingestion reliability, cleaning rules, geocoding, freshness, and serving — not “Ardeno Studio Production” marketing.

Live app: https://propertylk-one.vercel.app

## Goals
1. Rewrite README to lead with the data pipeline story, not brand splash.
2. Document provenance, schedule, failure modes, and data quality checks.
3. Add/clarify reproducibility (local run or scraper fixture tests).
4. Keep product UI secondary.

## README structure
1. Title: PropertyLK — Sri Lanka property listing intelligence pipeline
2. One sentence: scrapes → cleans → geocodes → aggregates → serves deal scores/heatmaps
3. Problem / user
4. Architecture diagram (sources → raw → clean → geo → marts/API → dashboard)
5. Data sources table: ikman / LPW / house.lk — method, cadence, known fragility
6. Pipeline stages with folders/commands
7. Data model / key tables
8. Data quality and tests (list actual tests; add a few if missing)
9. Freshness: how to see last successful scrape per source
10. How to run locally
11. Trade-offs and limitations (scraping ethics/ToS, Nominatim limits, coverage gaps)
12. Stack table (no giant badge wall)

## Tone rules
- No “An Ardeno Studio Production” hero framing at the top
- No “national platform” language
- Prefer: scheduled ingestion, source breakage, dedupe keys, geocode miss rate, median methodology

## Engineering tasks (priority)
1. CI badge only for real workflows
2. Scraper tests against HTML fixtures for at least one source
3. Document dedupe key and deal-score formula in README or docs/METHODOLOGY.md
4. Document last_success timestamps per job
5. Complete .env.example if weak

## Out of scope
- New ML models
- Full frontend rewrite
- Adding Kafka/Spark theater this pipeline does not need

## Done criteria
- Senior DE understands pipeline in one README screen
- Provenance + cadence + limitations explicit
- One automated test path obvious
- PR title: Harden PropertyLK README and data-pipeline credibility signals
