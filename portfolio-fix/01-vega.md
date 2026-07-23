# Master prompt — Cookie-Cat21/Vega

Copy everything below the line into a Cursor agent on the **Vega** repo.

---

You are hardening https://github.com/Cookie-Cat21/Vega for senior data-engineer hiring scrutiny.

## Context (brutal)
Vega has real Java/Kafka/Flink/Iceberg work, but the README and repo currently advertise a “1,000,000 commit agentic factory loop.” That is résumé poison. A senior will bounce before reading the connectors. Your job is to remove all commit-count theater, keep the real engineering, and make credibility come from reproducibility + tests + honest scope.

## Goals
1. Remove million-commit / agentic-factory theater from the public surface.
2. Rewrite README as a serious streaming-lakehouse portfolio project (honest: learning/portfolio system, not “we run prod SLAs”).
3. Add or improve a single reproducible local demo path and document it.
4. Do NOT invent fake production metrics, users, or uptime.

## Required deletions / quarantine
Delete these from the default branch (or move under `archive/internal/` if you must keep history for yourself — prefer delete from tree):

- `MILLION_COMMIT_PLAN.md`
- `IMPROVEMENT_PLAN.md` (if it only exists for the million-commit loop)
- `MASTER_PROMPT.md` (agent orchestration for commit farming)
- `docs/adr/0001-million-commit-loop.md`
- `scripts/million/` (entire directory)
- `progress/` (entire directory: PROGRESS.json, HANDOFF, eras, campaigns, factories, etc.)

Also remove Makefile targets: `million-progress`, `million-validate-batch`, `million-validate-loop`, `million-sync` and any `.PHONY` entries for them.

Search the whole repo for: `million`, `1000000`, `1,000,000`, `agentic loop`, `commit N/`, `factory loop`. Remove or rewrite every public-facing hit. Commit messages in git history can stay (don’t rewrite history).

## README rewrite requirements
Replace README with a clean DE portfolio README:

1. One-sentence summary: what Vega does (correlate natural events + wiki reactions + SL news through a streaming lakehouse).
2. Architecture diagram (keep/improve the mermaid).
3. Honest scope callout near the top:

   > Portfolio / learning system. Demonstrates streaming lakehouse mechanics locally and on Azure. Not a production SLA product.

4. Tech stack table (brief).
5. Data sources table with refresh style.
6. Project structure (no million/progress mentions).
7. **Quick start** that actually works: `make up`, build connectors, submit jobs, how to verify data moved.
8. **How to verify** section: exact commands/UI checks (Kafka UI topic messages, Flink job running, Iceberg/table or MinIO path, dbt compile if possible).
9. **Tests & CI** section: link existing workflows; note what is covered vs not.
10. **Trade-offs / known gaps** (required): e.g. cloud deploy needs secrets; dbt env var naming; what is mocked; what is not end-to-end asserted yet.
11. **Next hardening** (3 realistic bullets max).
12. License.

Forbidden words/phrases in README:
- Elite, autonomous factory, 1,000,000 commits, agentic improvement loop, production-grade (unless you can prove deploy + monitoring + run evidence)
- “Enterprise-ready” without evidence

## Engineering improvements (do if feasible in this pass)
Priority order:

1. Fix any obvious README/docs lying about current state.
2. If there is no local Iceberg/MinIO demo path, add a minimal `make demo` or document the closest real path and what it proves.
3. Ensure `test-all` CI still passes after deletions.
4. If dbt workflow env vars are wrong (`DBT_DATABRICKS_*` vs `DATABRICKS_*`), fix or document clearly.
5. Add a short `docs/ARCHITECTURE.md` only if README would become too long — otherwise keep one README.

## Out of scope
- Do not start a new million-commit system under another name.
- Do not add profile badges, trophies, or skill icons.
- Do not expand into new product features.
- Do not force-push or rewrite git history.

## Done criteria
- Repo tree has zero million-commit orchestration files.
- README can be understood in 60 seconds by a senior DE.
- CI still green (or you document exact failures you couldn’t fix and why).
- Open a PR titled: `Remove commit-count theater; harden README for DE hiring`

Be ruthless. Prefer deleting hype over explaining it.
