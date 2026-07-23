# Do this now (manual — this agent cannot)

This Cursor cloud agent only has write access to `Cookie-Cat21/Cookie-Cat21`.
It **cannot** update your GitHub bio, pins, or push to Vega / Octane / PropertyLK / etc.

## 1. Update GitHub profile fields

Go to: https://github.com/settings/profile

Set:

| Field | Value |
|---|---|
| **Name** | `Ovindu Karunaratne` |
| **Bio** | `Aspiring data engineer · real-time pipelines & Sri Lanka market data products · Co-Founder @ Ardeno Studio` |
| **Pronouns** | (optional) |
| **URL** | `https://cookie-cat21.vercel.app` |
| **Social accounts** | LinkedIn if available |

Remove anything that says only “Data Science student / AI enthusiast” without DE.

## 2. Pin exactly these 3 repos

Go to: https://github.com/Cookie-Cat21 → **Customize your pins**

Pin **only**:

1. `ArdenoStudio/sri-lanka-property-price-intelligence-platform` (PropertyLK)
2. `ArdenoStudio/octane`
3. `Cookie-Cat21/Vega`

Unpin:

- `Temporal-Feature-Engine`
- `mini-claude-code`
- `fraud-detection-pipeline`

(Those can stay public; they just should not be the first thing a senior sees.)

## 3. Merge the profile README PR

PR: https://github.com/Cookie-Cat21/Cookie-Cat21/pull/1

Before or after merge: delete the `portfolio-fix/` folder from `main` if you do not want these owner notes public. Keep a local copy of the master prompts.

## 4. Run the master prompts (one repo at a time)

Open each target repo in Cursor / Cloud Agent and paste the matching prompt from:

- `01-vega.md`
- `02-propertylk.md`
- `03-octane.md`
- `04-dataflow.md`
- `05-temporal-feature-engine.md`
- `06-fraud-detection-pipeline.md`
- `07-cse-api-docs.md`
- `08-ardeno-sprawl.md`

Run **Vega first**. It has the worst trust damage.
