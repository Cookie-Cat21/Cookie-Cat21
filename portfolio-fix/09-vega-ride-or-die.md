# Master prompt — Vega detox + DE credibility (give to another agent)

**Repo:** https://github.com/Cookie-Cat21/Vega  
**Default branch:** `main`  
**Stack claim:** Java 21 · Kafka KRaft · Kafka Connect · Flink · Iceberg · Azure AKS · dbt · Terraform

Copy **everything below the line** into a Cursor / Cloud agent opened on that repo.

---

You are rehabilitating **Vega** so it becomes a credible supporting Data Engineering portfolio project for Ovindu Karunaratne.

## Mission

Vega has real streaming-lakehouse engineering (connectors, Flink jobs, Iceberg, tests, Compose, Terraform). It is currently damaged by **1,000,000-commit / agentic-factory theater**. Your job:

1. **Delete all commit-count / agentic-loop theater** from the working tree
2. **Rewrite the README** as an honest portfolio / learning streaming lakehouse
3. **Make reproducibility the flex** — one clear local path that proves data moved
4. Keep real Java/Kafka/Flink/Iceberg code; do not invent fake production SLAs

Vega is **supporting pin material**, not the #1 flagship (PropertyLK is). Still must look serious.

## Non-goals

- Do not continue, rename, or hide the million-commit loop under a new brand
- Do not rewrite git history / force-push
- Do not claim AKS/Databricks/ADLS production without run evidence
- Do not add profile badges, trophies, skill icons
- Do not expand into new product features or AI agents
- Do not turn this into another “national intelligence” app

## Brutal context for the agent

Hiring managers will open README, see “1,000,000 commits”, and bounce.  
Real assets to preserve:

- `connectors/wikimedia`, `connectors/eonet`, `connectors/slnews` (Kafka Connect sources + tests)
- `flink-jobs/` (stream processing + tests)
- `iceberg/`, `dbt/`, `docker-compose.yml`, `terraform/`, `k8s/`, `helm/`
- CI under `.github/workflows/` especially `test-all.yml`

Theater to destroy:

- `MILLION_COMMIT_PLAN.md`
- `IMPROVEMENT_PLAN.md` (if million-loop oriented)
- `MASTER_PROMPT.md` (commit-farming orchestration)
- `docs/adr/0001-million-commit-loop.md`
- `scripts/million/` (entire tree)
- `progress/` (entire tree: PROGRESS.json, HANDOFF, eras, campaigns, factories, ledger, milestones)
- Makefile targets: `million-progress`, `million-validate-*`, `million-sync`
- Any README sections advertising the agentic million-commit loop

Search the repo for: `million`, `1000000`, `1,000,000`, `agentic loop`, `commit N/`, `factory loop`, `HANDOFF`, `NEXT_BATCH`. Remove public-facing hits. Git history can keep old commits.

---

## Phase plan (execute in order, commit often)

### Phase 0 — Audit

1. Confirm which million/progress files still exist.
2. Skim README, Makefile, CI workflows, `make up` path.
3. Note what local demo can actually prove today vs what needs Azure secrets.
4. Branch: `cursor/vega-de-detox-<suffix>`

Write findings into `docs/AUDIT.md` (short).

### Phase 1 — Delete theater

Delete (prefer delete from tree; do not leave a cute archive that still advertises the loop):

- `MILLION_COMMIT_PLAN.md`
- `IMPROVEMENT_PLAN.md`
- `MASTER_PROMPT.md`
- `docs/adr/0001-million-commit-loop.md`
- `scripts/million/`
- `progress/`

Clean Makefile:

- Remove million-* targets and `.PHONY` entries
- Keep real targets: `up`, `down`, `test`, `build`, monitoring, etc.

Grep again; zero public references to the million-commit campaign should remain in docs/README/Makefile/scripts.

Commit: `Remove million-commit agentic theater from Vega`

### Phase 2 — README rewrite (senior DE tone)

Replace README with a calm portfolio README:

1. **Title:** Vega — streaming lakehouse sandbox
2. **One sentence:** correlates natural events (NASA EONET), Wikimedia edit spikes, and Sri Lanka news through Kafka → Flink → Iceberg
3. **Honest scope callout near the top (required):**

   > Portfolio / learning system. Demonstrates streaming lakehouse mechanics locally (and Azure scaffolding). Not a production SLA product.

4. Architecture mermaid (keep/improve existing)
5. Tech stack table
6. Data sources table (Wikimedia SSE, EONET REST, SL RSS) with cadence
7. Project structure (no million/progress)
8. **Quick start** that matches Makefile/compose reality
9. **How to verify** — exact checks:
   - Kafka UI shows topics/messages
   - Flink UI shows running jobs
   - Iceberg/MinIO or documented sink path has data
   - optional dbt compile
10. **Tests & CI** — link `test-all.yml` and what it covers
11. **Trade-offs / known gaps** (required):
    - cloud deploy needs secrets
    - dbt env var naming issues if present (`DBT_DATABRICKS_*` vs `DATABRICKS_*`)
    - which tests are shallow
    - what is not end-to-end asserted in CI
12. **Next hardening** — max 3 realistic bullets
13. License (MIT)

Forbidden README language:

- Elite, autonomous factory, 1,000,000 commits, agentic improvement loop
- “Production-grade” / “enterprise-ready” without proof
- Fake throughput/SLA metrics

### Phase 3 — Reproducibility (the actual flex)

Highest engineering priority after detox:

1. Document a single happy path:

```bash
cp .env.example .env
make up
# build connectors + flink jobs (document exact commands)
# register connectors
# submit jobs
# verify
```

2. If local Iceberg/MinIO path is incomplete, either:
   - **Preferred:** add minimal local sink path + `make demo` that runs a bounded dataset and asserts row counts, OR
   - Document honestly what works today and what requires Azure

3. Add/adjust CI:
   - Keep unit tests green (`test-all`)
   - If feasible, add a smoke job that builds modules + validates compose config
   - Fix or clearly skip broken dbt-compile env var mismatches (don’t leave silent lies)

4. Prefer one bounded fixture/generator over “hit live Wikimedia forever” for demo assertions.

### Phase 4 — Credibility docs (short, useful)

Add only if they stay accurate:

- `docs/ARCHITECTURE.md` — only if README would become too long; otherwise keep one README
- `docs/FAILURE_MODES.md` — duplicates, late events, connector DLQ (`DeadLetterPublisher`), restart/checkpoints
- `docs/LOCAL_DEMO.md` — step-by-step verification with screenshots optional

Remove leftover ADR that only existed for the million loop; if other ADRs are useful, keep them.

### Phase 5 — GitHub metadata

1. Description (keep close to truth):

   `Streaming lakehouse sandbox: Kafka Connect → Flink → Iceberg (Java 21). Portfolio / learning system.`

2. Topics if editable: `kafka`, `flink`, `iceberg`, `data-engineering`, `kafka-connect`, `java`, `lakehouse`
3. No homepage required unless there is a real hosted demo

---

## Engineering quality bar

- Small reviewable commits
- Do not break Java module builds
- Run / fix tests after deletions
- No secrets committed
- Match existing code style
- If Azure deploy workflows fail for missing secrets, document that — don’t pretend they pass

---

## Done criteria (all required)

- [ ] Zero million-commit / progress / scripts/million / agentic-loop files in tree
- [ ] Makefile has no million-* targets
- [ ] README understandable in 60 seconds; honest portfolio framing
- [ ] Quick start + verification steps match reality
- [ ] CI test workflow still meaningful/green, or failures documented with fixes attempted
- [ ] Trade-offs / known gaps section present
- [ ] PR opened titled: `Remove commit-count theater; harden Vega for DE hiring`

## Final PR description must include

1. Exact files/dirs deleted
2. What local demo proves now
3. What still requires cloud secrets
4. Test/CI status
5. Suggested 2-line blurb if pinned on GitHub profile:

   > Vega — Kafka → Flink → Iceberg streaming lakehouse sandbox (portfolio).  
   > Focus: connectors, stream jobs, local reproducibility — not production SLAs.

Be ruthless. Deleting hype > explaining hype. Reproducibility > buzzwords.
