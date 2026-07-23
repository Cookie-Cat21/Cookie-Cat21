# Master prompt — Temporal Feature Engine

Repo: https://github.com/Cookie-Cat21/Temporal-Feature-Engine

Copy everything below the line into a Cursor agent on that repo.

---

You are detoxing this repo’s hype language and making it a credible streaming/fraud-features learning project.

## Context (brutal)
Interesting pieces exist (PyFlink, Redis, Memgraph, Presidio, docker-compose, some tests).  
But README says “Elite-Tier”, “absolute data sovereignty”, “Autonomous Ring Hunter”, and uses broken `file:///c:/Users/...` links. That reads as LLM-generated theater. Also should NOT be pinned on the GitHub profile anymore.

## Goals
1. Rewrite README with calm, precise language.
2. Fix all local file:// links to repo-relative paths.
3. Add repo description on GitHub via README title clarity (description field may need manual set).
4. Document what is proven by tests vs aspirational.
5. Optional: rename display title away from “v1.0.4-sovereign” cosplay.

## README tone (required)
Use something like:

> Experimental streaming feature/fraud-graph sandbox. Demonstrates temporal features, graph linkage, and PII masking. Not a commercial fraud platform.

Forbidden: Elite-Tier, absolute, autonomous platform, sovereign (unless explaining a concrete policy mechanism without mythology).

## README sections
1. What it is / what it is not
2. Architecture mermaid (keep, clean)
3. Components and folders
4. Quick start (`docker compose up`, how to produce sample events)
5. Tests: what `test_pii` and streaming tests actually prove
6. Known risks: string-built Cypher, LLM string-matching decisions, hardcoded MinIO creds in compose — fix or document
7. Trade-offs and next steps (benchmark with deterministic fixture)

## Engineering tasks (priority)
1. Fix README links.
2. Set a normal `README` H1: Temporal Feature Engine.
3. Add/adjust CI if needed; keep tests running.
4. Reduce hardcoded secrets in compose to env vars.
5. Add a deterministic fixture + assertion path if feasible (even small).
6. Add GitHub repo description (if API allows): `Experimental Flink + graph fraud-feature sandbox with PII masking`.

## Out of scope
- Building a real bank-grade fraud system
- LangGraph feature expansion for the resume

## Done criteria
- No elite/sovereign hype in README
- No file:// links
- Honest experimental framing
- PR title: Remove hype; document Temporal Feature Engine as experimental sandbox
