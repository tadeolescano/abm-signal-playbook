# 04 · Scoring and tiers

A 0 to 100 composite. Default weights below; the canonical version is [`config/scoring-model.yaml`](../config/scoring-model.yaml).

## Fit · up to 40 points

| Criterion | Points |
|---|---|
| Function headcount in the sweet-spot band (`{{band}}`) | 20 |
| Vertical in the priority list | 10 |
| Stage in the target range | 10 |

## Behaviour · up to 30 points (decays)

| Criterion | Points |
|---|---|
| High-intent web visit (known account) | 10 |
| Content or newsletter subscription | 10 |
| Event or webinar attendance | 10 |

## Engagement · up to 30 points (decays)

| Criterion | Points |
|---|---|
| Email reply (non-negative) | 15 |
| LinkedIn reply (non-negative) | 15 |

## Signal bonus · +10, capped at 100

New decision-maker hire, funding round, or competitor tool detected in the last 90 days.

## Decay

Behaviour and engagement points halve after 30 days and expire after 90. Fit does not decay. Without decay, last year's webinar keeps an account in Tier 1 forever.

## Tiers and routing

| Tier | Rule | Treatment |
|---|---|---|
| **T1** | Score 80+, vertical fit confirmed, sweet-spot size, at least one live signal | Manual, one-to-one. Rep queue + team alert |
| **T2** | Score 55 to 79 | Automated email + LinkedIn sequences with signal copy |
| **T3** | Score 30 to 54 | Automated email with segment copy; retargeting ads |
| **Unqualified** | AI-disqualified, do-not-contact, wrong vertical, below 30 | Excluded from all outreach |

Score recalculates whenever an input changes. Tier changes create a task, not just a property update.

## Calibration

Quarterly: for every meeting booked in the period, look at which inputs were present in the 7 and 30 days before. Raise the weight of inputs that precede meetings, lower the rest. Keep the change log in the YAML.
