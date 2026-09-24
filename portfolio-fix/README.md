# Portfolio hardening pack (owner notes)

These files are **for Ovindu**, not for the public profile.

If you merge PR #1 to update `README.md`, either:

- delete this `portfolio-fix/` folder before merge, or
- merge then delete it in a follow-up commit

## Order of operations

1. Read [`00-DO-THIS-NOW.md`](./00-DO-THIS-NOW.md) — bio + pins (manual)
2. Run prompts **one repo at a time** in Cursor:

| Priority | File | Repo |
|---|---|---|
| P0 | [`01-vega.md`](./01-vega.md) | `Cookie-Cat21/Vega` |
| P0 | [`09-propertylk-ride-or-die.md`](./09-propertylk-ride-or-die.md) | **PropertyLK ride-or-die flagship harden** |
| P0 | [`02-propertylk.md`](./02-propertylk.md) | PropertyLK lighter README pass (superseded by 09) |
| P0 | [`03-octane.md`](./03-octane.md) | `ArdenoStudio/octane` |
| P1 | [`04-dataflow.md`](./04-dataflow.md) | `Cookie-Cat21/Data-flow` |
| P1 | [`07-cse-api-docs.md`](./07-cse-api-docs.md) | `Cookie-Cat21/cse-api-docs` |
| P2 | [`05-temporal-feature-engine.md`](./05-temporal-feature-engine.md) | `Cookie-Cat21/Temporal-Feature-Engine` |
| P2 | [`06-fraud-detection-pipeline.md`](./06-fraud-detection-pipeline.md) | `Cookie-Cat21/fraud-detection-pipeline` |
| P2 | [`08-ardeno-sprawl.md`](./08-ardeno-sprawl.md) | ArdenoStudio org metadata |

## Why this agent didn’t just do the other repos

The cloud token for this run can push to `Cookie-Cat21/Cookie-Cat21` only.
Pushes to Vega / Octane / PropertyLK returned `Permission denied to cursor[bot]`.
GitHub bio + pins require user oauth scopes this agent does not have.
