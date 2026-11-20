# 02 · Enrichment and data model

## Company properties

| Property | Type | Values / notes |
|---|---|---|
| `function_headcount` | number | People in the buyer's function |
| `size_band` | enum | `SMB`, `MID`, `ENT` |
| `vertical` | enum | `{{verticals}}` |
| `geo_region` | enum | `{{regions}}` |
| `competitor_tech` | multi-enum | `{{competitor_a}}`, `{{competitor_b}}`, ... detected via technographic data |
| `icp_score` | number 0 to 100 | Composite, recalculated on change |
| `abm_tier` | enum | `T1`, `T2`, `T3`, `UNQUALIFIED` |
| `awareness_stage` | enum | `IDENTIFIED`, `AWARE`, `INTERESTED`, `CONSIDERING`, `SELECTING` |
| `last_signal_type` / `last_signal_at` | enum / date | Most recent signal |
| `enriched_at` | date | Last enrichment run |
| `parent_company` | association | Portfolio or group mapping for investor-led plays |

## Contact properties

| Property | Type | Values |
|---|---|---|
| `committee_role` | enum | `DECISION_MAKER`, `CHAMPION`, `INFLUENCER`, `OTHER` (AI-classified from title) |
| `last_engagement_at` | date | Any reply, meeting, event or content action |

## Product properties (if you have self-serve)

| Property | Type |
|---|---|
| `activation_score` | number |
| `first_integration_connected_at` | date |

## Automation

1. **On create:** company created in CRM -> webhook to enrichment tool -> enrich -> write back -> set `enriched_at`.
2. **Annual refresh:** if `enriched_at` is older than 12 months, re-enrol.
3. **On-demand:** a button or task on the company record: "find stakeholders at this company".
4. **Score recalculation:** on any change to a scoring input.

Do not score on a property you cannot populate for most of the TAL. Missing data silently becomes zero points.
