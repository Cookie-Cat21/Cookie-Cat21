### Ovindu Karunaratne

Aspiring **data engineer**. I build ingestion systems and data products from messy public / market sources — mostly Sri Lanka.

Looking for **Data Engineering** roles where I can own pipelines end-to-end: extract → model → serve → keep them honest.

[Portfolio](https://cookie-cat21.vercel.app) · [LinkedIn](https://www.linkedin.com/in/ovindu-karunaratne-b0983b2a0/) · [Email](mailto:karunaratneovindu@gmail.com) · [Ardeno Studio](https://ardeno-studio-website.vercel.app/)

---

### Flagship projects

#### 1. [PropertyLK](https://github.com/ArdenoStudio/sri-lanka-property-price-intelligence-platform) · [live](https://propertylk-one.vercel.app)

**Sri Lanka real-estate price intelligence**

Scrapes listings, cleans and geocodes them, aggregates market signals, and serves deal scoring / heatmaps.

| | |
|---|---|
| **Proves** | Messy multi-source ingestion, cleaning, geocoding, scheduled pipelines, serving layer |
| **Stack** | Python · FastAPI · PostgreSQL · Playwright · React |
| **Why it matters** | Real local market data with a usable product on top — not a tutorial dataset |

#### 2. [Octane](https://github.com/ArdenoStudio/octane) · [live](https://octane-smoky.vercel.app)

**Fuel price tracker + open API for Sri Lanka**

Scheduled scrapes for CPC / LIOC prices, history, trip cost calculator, email alerts, public API.

| | |
|---|---|
| **Proves** | Recurring ingestion, source fragility, API design, alerting, CI around scrapers |
| **Stack** | TypeScript · FastAPI · Fly.io · Vercel |
| **Why it matters** | Narrow scope, ships continuously, and survives real source-website breakage |

#### 3. [Vega](https://github.com/Cookie-Cat21/Vega)

**Streaming lakehouse playground**

Kafka → Kafka Connect → Flink → Iceberg on Azure AKS, with connectors, Terraform, and tests.

| | |
|---|---|
| **Proves** | Streaming / lakehouse mechanics I am actively learning in depth |
| **Stack** | Java 21 · Kafka · Flink · Iceberg · AKS · Terraform · dbt |
| **Honest note** | Strongest infra project, still a portfolio system — not claiming production SLAs |

---

### Also worth a look

- [**cse-api-docs**](https://github.com/Cookie-Cat21/cse-api-docs) — Unofficial Colombo Stock Exchange API map, live-probed weekly ([docs](https://cookie-cat21.github.io/cse-api-docs/))
- [**DataFlow**](https://github.com/Cookie-Cat21/Data-flow) — Kafka → Spark → Delta → dbt → Airflow medallion pipeline (Olist)
- [**Koel**](https://github.com/ArdenoStudio/Koel) — Telegram alerts for CSE price moves ([live](https://koel-cse.vercel.app))

I also maintain a set of reverse-engineered Sri Lanka API notes (banks, utilities, markets). Useful for local data work; not the hiring pitch. [Browse](https://github.com/Cookie-Cat21?tab=repositories&q=docs).

---

### Stack I actually use

`Python` · `SQL` · `Java` · `TypeScript`  
`Kafka` · `Flink` · `Spark` · `Iceberg` / `Delta` · `dbt` · `Airflow`  
`PostgreSQL` · `Docker` · `Terraform` · `GitHub Actions` · `FastAPI`

---

### How I work

- Prefer **one honest pipeline** over ten demos
- Document **source provenance, freshness, and known gaps**
- Care about **retries, idempotency, and tests** — still leveling these up on every project
- Bias toward **local market data** where public sources are messy and under-documented

---

Open to Data Engineering roles / internships. Happy to walk through architecture, failure modes, and what I would harden next on any of the projects above.
