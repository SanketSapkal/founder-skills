# founder-skills

Adversarial idea interrogation followed by structured business modeling — in one chained pipeline.

Every existing startup skills repo is generative: you bring an idea and it helps you fill it out. This repo starts by trying to **kill** the idea first, then builds out the survivors.

```
Existing repos:   Interrogate OR Model
This repo:        Interrogate THEN Model
```

## The Key Differentiator

`/verdict` — a synthesis skill that reads all prior outputs and returns an explicit **BUILD / KILL / PIVOT** judgment with structured reasoning. No other skills repo has this.

## Pipeline

```
/pressure-test ──┬──> /scope-mode ──────> /startup-canvas
                 │                            │
                 ├──> /customer-archetype ──┬──┤
                 │                         │  ├──> /assumption-map ──> /pretotype
                 │                         │  └──> /battle-cards
                 └─────────────────────────┴──> /market-size ──> /assumption-map

All outputs ──────────────────────────────────────> /verdict
/verdict (BUILD) ──┬───────────────────────────────> /build-brief → coding agent
                   ├───────────────────────────────> /pitch-deck, /investor-lens, /elevator-pitch, /objection-map
                   └───────────────────────────────> /gtm-plan, /oneliner, /cold-outreach, /content-strategy
/verdict (KILL/PIVOT) ─────────────────────────────> /pivot-paths
```

Every skill writes a structured output file to `./founder-outputs/`. Downstream skills read those files. `/verdict` reads all of them.

## Quick Start

1. Install the plugin (see below)
2. Open a project in Claude Code
3. Say "I have an idea" or run `/pressure-test`
4. Follow the pipeline — each skill recommends the next step

## Installation

### As a Claude Code plugin (recommended)

```bash
claude plugin add /path/to/founder-skills
```

### Manual install (symlink)

```bash
git clone https://github.com/YOUR_USERNAME/founder-skills.git
cd founder-skills
./setup --global   # installs to ~/.claude/skills/
# or
./setup --local    # installs to ./.claude/skills/ in current project
```

## Skills Reference

| Skill | Purpose | Reads | Writes |
|---|---|---|---|
| `/pressure-test` | Adversarial interrogation — kill bad ideas early | — | `pressure-test-output.md` |
| `/scope-mode` | Calibrate ambition: EXPAND / SELECTIVE / HOLD / REDUCE | pressure-test | `scope-output.md` |
| `/customer-archetype` | Force precise customer definition | pressure-test | `customer-archetype-output.md` |
| `/market-size` | Bottom-up TAM / SAM / SOM | pressure-test, archetype | `market-size-output.md` |
| `/startup-canvas` | Business model + value proposition | pressure-test, archetype, scope | `startup-canvas-output.md` |
| `/battle-cards` | Competitive intelligence + positioning | archetype, canvas | `battle-cards-output.md` |
| `/assumption-map` | Surface and prioritize riskiest assumptions | canvas, market-size | `assumption-map-output.md` |
| `/pretotype` | Design validation experiments | assumption-map | `pretotype-output.md` |
| `/verdict` | **BUILD / KILL / PIVOT** synthesis | ALL outputs | `verdict-output.md` |
| `/pivot-paths` | 3 concrete pivot directions | verdict + all outputs | `pivot-paths-output.md` |
| `/10x-why-now` | Thiel's "why now" formalized | pressure-test, battle-cards | `why-now-output.md` |
| `/analogous-cos` | Structurally similar companies in other markets | pressure-test, canvas | `analogous-cos-output.md` |
| `/build-brief` | Structured handoff for coding agents | ALL outputs (BUILD verdict) | `build-brief-output.md` |
| **Investment Pitch** | | | |
| `/pitch-deck` | Sequoia narrative arc from all outputs | ALL outputs | `pitch-deck-output.md` |
| `/investor-lens` | Score through seed angel, Series A, corporate VC lenses | verdict, canvas, market-size | `investor-lens-output.md` |
| `/elevator-pitch` | 30-sec, 2-min, 10-min pitch versions | canvas, archetype, battle-cards | `elevator-pitch-output.md` |
| `/objection-map` | 8-10 hardest investor questions with answers | verdict, assumption-map | `objection-map-output.md` |
| **Sales & Marketing** | | | |
| `/gtm-plan` | Bullseye framework — rank 19 channels, test top 3 | canvas, archetype | `gtm-plan-output.md` |
| `/oneliner` | One-sentence value prop with scoring criteria | canvas, archetype, battle-cards | `oneliner-output.md` |
| `/cold-outreach` | Personalized 3-email sequences from archetype | archetype, canvas | `cold-outreach-output.md` |
| `/content-strategy` | 30-day content plan matched to archetype sources | archetype, canvas, battle-cards | `content-strategy-output.md` |

## CLAUDE.md Snippet

Add this to your project's `CLAUDE.md` to give Claude pipeline awareness:

```markdown
## Founder Skills Pipeline

This project uses the founder-skills pipeline for idea validation.

### Output Directory
All skill outputs are saved to `./founder-outputs/`. Each skill reads
prior outputs from this directory to build on earlier analysis.

### Pipeline Sequence
1. `/pressure-test` — Adversarial interrogation (run first)
2. `/scope-mode` — Calibrate ambition level
3. `/customer-archetype` — Define the specific customer
4. `/market-size` — Bottom-up TAM/SAM/SOM
5. `/startup-canvas` — Business model + value proposition
6. `/battle-cards` — Competitive intelligence
7. `/assumption-map` — Risk prioritization
8. `/pretotype` — Validation experiments
9. `/verdict` — BUILD / KILL / PIVOT judgment
```

## Books Referenced

| Book | Author | Used By |
|---|---|---|
| *The Mom Test* | Rob Fitzpatrick | `/pressure-test`, `/customer-archetype` |
| *Zero to One* | Peter Thiel | `/pressure-test`, `/scope-mode`, `/10x-why-now` |
| *Competing Against Luck* | Clayton Christensen | `/pressure-test`, `/customer-archetype`, `/startup-canvas` |
| *Lean Analytics* | Croll & Yoskovitz | `/market-size` |
| *The Lean Startup* | Eric Ries | `/startup-canvas`, `/pretotype`, `/scope-mode` |
| *Business Model Generation* | Osterwalder | `/startup-canvas` |
| *$100M Offers* | Alex Hormozi | `/startup-canvas` |
| *Continuous Discovery Habits* | Teresa Torres | `/assumption-map` |
| *Obviously Awesome* | April Dunford | `/battle-cards` |
| *Crossing the Chasm* | Geoffrey Moore | `/battle-cards`, `/10x-why-now` |
| *Pretotype It* | Alberto Savoia | `/pretotype` |
| *The Hard Thing About Hard Things* | Ben Horowitz | `/verdict` |
| *Shape Up* | Basecamp | `/build-brief` |
| *Inspired* | Marty Cagan | `/build-brief` |
| *Venture Deals* | Feld & Mendelson | `/investor-lens`, `/pitch-deck` |
| *The Fundraising Rules* | Mark MacLeod | `/objection-map` |
| *Traction* | Weinberg & Mares | `/gtm-plan` |
| *$100M Leads* | Alex Hormozi | `/gtm-plan`, `/cold-outreach`, `/content-strategy` |
| *Predictable Revenue* | Ross & Tyler | `/cold-outreach` |
| *Secrets of Sand Hill Road* | Scott Kupor | `/verdict` |
