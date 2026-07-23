# Master prompt — DataFlow

Repo: https://github.com/Cookie-Cat21/Data-flow

Copy everything below the line into a Cursor agent on that repo.

---

You are turning DataFlow from a “production-grade” scaffold into an honest, reproducible DE portfolio project — or clearly marking what’s unfinished.

## Context (brutal)
Claimed stack: Kafka → Spark → Delta → dbt → Airflow → Next.js on Olist.  
Reality check from prior audit: thin file count, little/no CI, missing tests, EmptyOperators in Airflow, dbt_utils without packages.yml, heavy cloud assumptions. “Production-grade” is currently unjustified.

## Decision (do this first)
Choose ONE path and state it at the top of README:

**Path A (preferred):** Local reproducible mini-pipeline  
Redpanda/Kafka + Spark local + local Delta/MinIO + dbt + Airflow DAG parse + dashboard build, all runnable via Docker Compose + CI.

**Path B:** Honest cloud lab notes  
Keep Confluent/Databricks references but remove “production-grade”; document exact setup; add DAG parse tests + dbt compile in CI with stubs.

If Path A is too large for one PR, do a credible Path B now and open issues for Path A.

## Required README changes
1. Delete or replace “production-grade” claims.
2. Add status badge language: `Portfolio lab — reproducible locally` or `Incomplete cloud lab`.
3. Architecture diagram kept, but label what is implemented vs stubbed.
4. How to run (one command path).
5. What is tested in CI.
6. Trade-offs: why Olist replay, why each tool exists, what you’d drop at small scale.
7. Dataset license note (already present — keep).

## Engineering tasks (minimum bar)
1. Add GitHub Actions: at least
   - Python lint/tests if any transform code
   - `dbt deps` + `dbt compile` (fix packages.yml for dbt_utils)
   - Airflow DAG import/parse check
   - Dashboard `npm ci` + build
2. Remove or replace Airflow `EmptyOperator` placeholders with real operators OR label them clearly as stubs in code + README.
3. Add `packages.yml` for dbt.
4. Add `.env.example` with every required var.
5. Add at least a few pytest tests for any Python transform/producer logic.

## Forbidden
- Adding more tools to look impressive
- Claiming Databricks/Confluent production without run evidence
- Fake screenshots

## Done criteria
- Claim-to-proof ratio is honest
- CI exists and passes on the checks you claim
- PR title: Make DataFlow honest and CI-reproducible
