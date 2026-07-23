# Master prompt — fraud-detection-pipeline

Repo: https://github.com/Cookie-Cat21/fraud-detection-pipeline

Copy everything below the line into a Cursor agent on that repo.

---

You are reframing this as an honest synthetic ML + serving demo, and tightening engineering basics.

## Context
Coherent small project: synthetic data → XGBoost → FastAPI → optional Kafka → Streamlit.  
Overclaims “real-time fraud detection” when labels are rule-generated synthetics and Kafka is not even in docker-compose. Fine as a learning demo; bad as a senior DE flagship. Keep public, unpin from profile.

## Goals
1. Rewrite README positioning: synthetic fraud scoring demo.
2. Put Kafka behind an optional profile; docker-compose should match claims.
3. Add GitHub Actions CI (train smoke or use committed artifacts + API tests).
4. Publish honest metrics section (and leakage note: model learns the generator rules).

## README must say near top
> Synthetic transaction fraud scoring demo. Labels come from hand-written generator rules, so model metrics measure recovery of those rules — not real-world fraud performance.

## Tasks
1. Align docker-compose with docs (add Kafka/Redpanda service OR demote Kafka in README).
2. Add CI: pytest + API tests; fail on broken imports.
3. Document how to train, where artifacts go, how to score.
4. Add confusion matrix / metrics output from training into `artifacts/` or README snippet.
5. Soften “live deployment” unless health URLs are verified; if live, link them.

## Out of scope
- Becoming the profile flagship
- Adding Flink/Iceberg to impress

## Done criteria
- Positioning is impossible to misread as production fraud
- Compose and README agree
- CI green
- PR title: Honest synthetic fraud demo framing + CI
