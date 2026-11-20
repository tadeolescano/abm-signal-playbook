# 03 · Signal library

Capturing signals is easy. Activation is most of the work. Every signal below has a defined action and an owner.

## First-party (your own surfaces)

| Signal | Action | Owner | SLA |
|---|---|---|---|
| Discovery call booked | Auto-create deal, alert team channel | System | Instant |
| Reply to outbound email or LinkedIn | Alert owner, unenrol from sequences | System + rep | Same day |
| Content / newsletter subscription | Nurture sequence (day 1, 7, 14) | Marketing | Automated |
| Event or webinar registration | Event follow-up track; score bump | Marketing | Automated |
| Self-serve signup | Trial workflow; rep task at day 7 if activation is low | Rep | Day 7 |
| High-intent page visit (pricing, comparison) by a known account | Rep task if Tier 1 or 2 | Rep | 48 hours |

## Second-party (activity on platforms you share with the buyer)

| Signal | Action | Owner | SLA |
|---|---|---|---|
| Profile view of a sender | Start DM sequence | System | Automated |
| Connection accepted | DM on day 0 | System | Automated |
| Engagement with your posts | Add to warm audience; rep task if Tier 1 | Rep | 48 hours |

## Third-party (public or data-provider signals)

| Signal | Action | Owner | SLA |
|---|---|---|---|
| New decision-maker hire (last 90 days) | Enrol Tier 1/2 leadership-hire sequence | Rep / system | 7 days |
| Funding round (last 60 days) | Enrol funding sequence; score bonus | System | 7 days |
| Hiring spike in the buyer's function | Enrol hiring-spike sequence | System | 7 days |
| Competitor tool detected | Switch to displacement copy variant | System | Next send |
| Follows a competitor | Competitor-follower lane | System | Next send |

## Awareness stages

| Stage | Entry criteria |
|---|---|
| Identified | On the TAL, no engagement |
| Aware | Website visit or meaningful ad exposure |
| Interested | Positive reply, event attendance, content subscription |
| Considering | Demo request or discovery booked |
| Selecting | Active deal |

Track movement **and regression**. Accounts sliding back from Interested to Aware are pipeline leaks.
