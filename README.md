# ABM Signal Playbook

A signal-based account-based marketing playbook for B2B SaaS teams with a constrained, well-defined market: how to map the target account list, enrich it, capture buying signals, score and tier accounts, run a different play per tier, and report on whether any of it is working.

Patterns I built and ran in production at an AI startup, rewritten as a generic playbook with placeholders.

---

## The problem

Most "ABM" programs are a static list and a bigger ad budget. Accounts get tiered once by firmographics, every tier gets roughly the same sequence, and the success metric is MQL count. Three things go wrong:

1. **Fit without timing.** A perfect-fit account with no reason to act this quarter gets the same intensity as one that just hired a new buyer.
2. **Signals captured, not activated.** Teams wire up intent data, then nothing happens when a signal fires. Capturing is easy; activation is most of the work.
3. **The wrong north star.** MQLs and total pipeline go up while pipeline from the accounts you actually want stays flat.

## How it works

```
TAM map -> enrichment -> signal library -> scoring -> tiers -> plays -> reporting
                ^                                                         |
                └──────────────── every channel feeds the score ──────────┘
```

| Layer | What it does | Doc |
|---|---|---|
| TAM map | ICP, buying committee, firmographic gates, target account list from several sources, deduplicated | [01-tam-and-icp.md](playbook/01-tam-and-icp.md) |
| Enrichment | CRM properties that must exist, automated enrichment on create, annual refresh | [02-enrichment-and-data-model.md](playbook/02-enrichment-and-data-model.md) |
| Signals | First-, second- and third-party signals, each with a defined action | [03-signal-library.md](playbook/03-signal-library.md) |
| Scoring | A 0 to 100 composite: fit + behaviour + engagement + signal bonus | [04-scoring-and-tiers.md](playbook/04-scoring-and-tiers.md) |
| Plays | Channel mix and intensity per tier | [05-plays-by-tier.md](playbook/05-plays-by-tier.md) |
| Reporting | One north star and a short set of operating reports | [06-reporting.md](playbook/06-reporting.md) |

The scoring model and signal library are also provided as config ([`config/scoring-model.yaml`](config/scoring-model.yaml), [`config/signals.yaml`](config/signals.yaml)) so they can be versioned and implemented in a CRM, an enrichment tool or a script.

### The core rules

- **Tier on fit, act on signals.** Fit decides which tier an account belongs to. Signals decide when to act.
- **Every signal has an owner and an action.** A signal with no action is noise in a dashboard.
- **Do not fear "burning the TAM".** Re-engage on a schedule and layer signal-based micro-campaigns on top. Silence is what burns accounts.
- **North star: ICP pipeline created month over month.** Not MQLs, not total pipeline.

## Structure

```
abm-signal-playbook/
├── playbook/
│   ├── 01-tam-and-icp.md
│   ├── 02-enrichment-and-data-model.md
│   ├── 03-signal-library.md
│   ├── 04-scoring-and-tiers.md
│   ├── 05-plays-by-tier.md
│   └── 06-reporting.md
├── config/
│   ├── scoring-model.yaml     # weights, thresholds, decay
│   └── signals.yaml           # signal definitions, source type, action, SLA
└── site/
    └── index.html             # standalone one-page version, open in any browser
```

## How to use it

1. Replace every `{{placeholder}}` with your values: verticals, buyer roles, company-size bands, competitors, channels.
2. Build the TAM list from at least two independent sources and deduplicate before scoring.
3. Create the CRM properties listed in the data model. Do not score on fields you cannot populate.
4. Implement the scoring model from the YAML. Start with the default weights, then recalibrate quarterly against which signals actually preceded meetings.
5. Wire each signal to its action and owner. Test each one with a fake record.
6. Launch the plays per tier. Report weekly and monthly.
7. Open `site/index.html` for a shareable one-page overview (no build step, no external requests).

## What this is not

- **Not an intent-data vendor comparison.** Tools are referred to by category.
- **Not a fixed weighting.** The default weights are a starting point. Your own closed-won history should reshape them.
- **Not a volume play.** ABM for a constrained market is about timing and relevance, not reach.
- **Not finished until reporting runs.** If nobody looks at the signal-influence report, the scoring model never improves.

## License

MIT. See [LICENSE](LICENSE).

---

Built by Tadeo Lescano, GTM Engineer. [LinkedIn](https://www.linkedin.com/in/tadeo-lescano/) · [GitHub](https://github.com/tadeolescano)
