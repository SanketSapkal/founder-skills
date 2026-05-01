---
name: founder-pipeline
description: This skill should be used when the user says "I have a startup idea", "help me evaluate this idea", "run the full pipeline", "what should I run next", "where am I in the pipeline", or presents any new product or business concept for the first time. Provides pipeline awareness, recommends the next founder-skills step based on which output files already exist, and explains the overall interrogation-to-verdict flow.
version: 0.1.0
---

# Founder Skills Pipeline

An adversarial idea interrogation pipeline that pressure-tests startup ideas before modeling them. Every skill writes a structured output file to `./founder-outputs/`; downstream skills read those files. The pipeline ends with an explicit BUILD / KILL / PIVOT verdict.

## Pipeline Sequence

```
1.  /pressure-test      ──> Adversarial interrogation (run first, always)
2.  /customer-archetype ──> Define the specific customer (upstream of modeling)
3.  /founder-fit        ──> Assess founder-market fit and unfair advantage
4.  /scope-mode         ──> Calibrate ambition: EXPAND / SELECTIVE / HOLD / REDUCE
5.  /market-size        ──> Bottom-up TAM / SAM / SOM
6.  /startup-canvas     ──> Business model + value proposition
7.  /unit-economics     ──> CAC / LTV / payback / gross margin
8.  /regulatory-risk    ──> Compliance exposure (run if regulated industry)
9.  /battle-cards       ──> Competitive intelligence
10. /assumption-map     ──> Surface and prioritize riskiest assumptions
11. /pretotype          ──> Design validation experiments
12. /verdict            ──> BUILD / KILL / PIVOT synthesis (reads all outputs)
```

After verdict:
- `/build-brief` — if BUILD, produce a structured handoff for coding agents
- `/pivot-paths` — if KILL or PIVOT, generate 3 concrete pivot directions
- `/10x-why-now` — formalize Thiel's "why now" question (run anytime)
- `/analogous-cos` — find structurally similar companies in other markets (run anytime)

Investment pitch (after BUILD verdict):
- `/pitch-deck` — Sequoia narrative arc from all outputs
- `/investor-lens` — score through seed angel, Series A, and corporate VC lenses
- `/elevator-pitch` — 30-second, 2-minute, and 10-minute versions
- `/objection-map` — 8-10 hardest investor questions with draft answers

Sales & marketing (after BUILD verdict):
- `/gtm-plan` — Bullseye framework, rank 19 channels, test top 3
- `/oneliner` — obsessive one-sentence value proposition refinement
- `/cold-outreach` — personalized 3-email sequences from archetype
- `/content-strategy` — 30-day content plan matched to archetype sources

## Dependency Graph

```
pressure-test ──> customer-archetype ──┬──> founder-fit
                                       ├──> scope-mode ──> startup-canvas ──> unit-economics
                                       │                         │
                                       ├──> market-size ─────────┤
                                       │                         ├──> regulatory-risk (if regulated)
                                       │                         ├──> battle-cards
                                       │                         └──> assumption-map ──> pretotype
                                       └───────────────────────────────────────────────────────┘
                                                                                               ↓
All outputs ──────────────────────────────────────────────────────────────────────────> verdict
verdict (BUILD) ──┬────────────────────────────> build-brief → coding agent
                  ├────────────────────────────> pitch-deck, investor-lens, elevator-pitch, objection-map
                  └────────────────────────────> gtm-plan, oneliner, cold-outreach, content-strategy
verdict (KILL/PIVOT) ──────────────────────────> pivot-paths
```

## How to Route

1. Check which files exist in `./founder-outputs/`.
2. Identify the next skill whose dependencies are satisfied but whose output is missing.
3. Recommend that skill to the user.
4. If all outputs exist, recommend `/verdict`.

## Output Files Reference

| Skill | Output File | Key Rating |
|---|---|---|
| `/pressure-test` | `pressure-test-output.md` | Demand: STRONG / WEAK / UNCLEAR |
| `/customer-archetype` | `customer-archetype-output.md` | Specificity: SHARP / VAGUE |
| `/founder-fit` | `founder-fit-output.md` | Fit: STRONG / MODERATE / WEAK |
| `/scope-mode` | `scope-output.md` | Mode: EXPAND / SELECTIVE / HOLD / REDUCE |
| `/market-size` | `market-size-output.md` | Opportunity: LARGE / MEDIUM / SMALL / UNPROVEN |
| `/startup-canvas` | `startup-canvas-output.md` | Coherence: COHERENT / GAPS / BROKEN |
| `/unit-economics` | `unit-economics-output.md` | Viability: VIABLE / MARGINAL / BROKEN |
| `/regulatory-risk` | `regulatory-risk-output.md` | Risk: LOW / MEDIUM / HIGH / BLOCKING |
| `/battle-cards` | `battle-cards-output.md` | Position: DIFFERENTIATED / CROWDED / UNCLEAR |
| `/assumption-map` | `assumption-map-output.md` | Risk: concentrated / distributed |
| `/pretotype` | `pretotype-output.md` | Validation path: CLEAR / UNCLEAR |
| `/verdict` | `verdict-output.md` | Verdict: BUILD / KILL / PIVOT |
| `/build-brief` | `build-brief-output.md` | Handoff ready: YES / NO |
| `/pivot-paths` | `pivot-paths-output.md` | Recommended path: A / B / C |
| `/10x-why-now` | `why-now-output.md` | Timing: STRONG / MODERATE / WEAK / TOO EARLY |
| `/analogous-cos` | `analogous-cos-output.md` | Analog strength: STRONG / MODERATE / WEAK |
| `/pitch-deck` | `pitch-deck-output.md` | Deck ready: YES / GAPS |
| `/investor-lens` | `investor-lens-output.md` | Best fit: Seed / Series A / Strategic |
| `/elevator-pitch` | `elevator-pitch-output.md` | Pitch ready: YES |
| `/objection-map` | `objection-map-output.md` | Prep level: READY / GAPS |
| `/gtm-plan` | `gtm-plan-output.md` | GTM clarity: CLEAR / NEEDS TESTING / UNCLEAR |
| `/oneliner` | `oneliner-output.md` | Quality: STRONG / NEEDS WORK |
| `/cold-outreach` | `cold-outreach-output.md` | Outreach ready: YES / NEEDS PERSONALIZATION |
| `/content-strategy` | `content-strategy-output.md` | Content clarity: CLEAR / NEEDS REFINEMENT |

## Framework Ownership

| Framework | Primary Skill | Book |
|---|---|---|
| Mom Test (disappear bar) | `/pressure-test` | *The Mom Test* (Fitzpatrick) |
| JTBD framing | `/pressure-test`, `/customer-archetype` | *Competing Against Luck* (Christensen) |
| Contrarian truth | `/pressure-test` | *Zero to One* (Thiel) |
| Monopoly / niche thinking | `/scope-mode` | *Zero to One* (Thiel) |
| Lean Canvas / BMC | `/startup-canvas` | *Business Model Generation* (Osterwalder) |
| Bottom-up TAM/SAM/SOM | `/market-size` | *Lean Analytics* (Croll & Yoskovitz) |
| Assumption mapping (OST) | `/assumption-map` | *Continuous Discovery Habits* (Torres) |
| April Dunford positioning | `/battle-cards` | *Obviously Awesome* (Dunford) |
| Pretotype methodology | `/pretotype` | *Pretotype It* (Savoia) |
| Investor scoring lens | `/verdict`, `/investor-lens` | *Secrets of Sand Hill Road* (Kupor) |
| Appetite-driven scoping | `/build-brief` | *Shape Up* (Basecamp) |
| Sequoia narrative arc | `/pitch-deck` | *Secrets of Sand Hill Road* (Kupor) |
| Bullseye framework | `/gtm-plan` | *Traction* (Weinberg & Mares) |
| Value equation | `/oneliner` | *$100M Offers* (Hormozi) |
| Cold outbound methodology | `/cold-outreach` | *Predictable Revenue* (Ross & Tyler) |
