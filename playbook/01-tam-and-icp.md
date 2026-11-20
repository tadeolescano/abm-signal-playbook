# 01 · TAM map and ICP

## ICP definition

| Element | Definition |
|---|---|
| Verticals | `{{vertical_1}}`, `{{vertical_2}}`, `{{vertical_3}}` |
| Company size | `{{min}}` to `{{max}}` people in the buyer's function |
| Stage | `{{e.g. Series A to Series C}}` |
| Business model | `{{e.g. B2B SaaS, regulated financial services}}` |
| Regions | `{{priority regions}}` |
| Exclusions | Services or consultancies, no in-house team in the buyer's function, pre-product companies, existing customers, do-not-contact |

## Buying committee

| Role | Typical titles | Job in the deal |
|---|---|---|
| Decision maker | `{{e.g. CTO, VP of the function, technical founder}}` | Owns budget and the final call |
| Champion | `{{e.g. Director, Head of Platform, Manager}}` | Feels the pain daily, sells internally |
| Influencer | `{{e.g. senior practitioners, leads}}` | Evaluates, can veto |

Write one pain statement per role. They are different people with different criteria.

## Building the target account list (TAL)

Combine sources to reach high coverage of the real market. A single database rarely covers niche verticals or regions.

| Source type | Use for |
|---|---|
| Primary B2B database | Companies with a solid online footprint |
| Scraped directories (industry associations, accelerators, event exhibitor lists) | Verticals the primary database covers poorly |
| Social-network sales tools | Regions or verticals where database coverage is thin |

Then:

1. Deduplicate across sources on normalised domain and company name.
2. Run an AI qualification pass per company: read the website and classify `QUALIFIED`, `NOT_QUALIFIED` or `INSUFFICIENT_DATA`, with a one-line reason.
3. Send `INSUFFICIENT_DATA` to manual review, not to outreach.
4. Load into the CRM with source and qualification date.

Target: a deduplicated list of `{{N}}` qualified accounts. In a constrained market, coverage and accuracy matter more than size.
