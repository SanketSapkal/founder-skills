---
name: investor-lens
description: This skill should be used when the user says "how would an investor see this", "investor perspective", "what would a VC think", "seed angel", "Series A lens", "strategic investor", "investor scorecard", or needs to understand how different investor types would evaluate the same idea. Re-reads the verdict through seed angel, Series A fund, and corporate VC perspectives.
version: 0.1.0
---

# Investor Lens

Different investors score the same idea on completely different dimensions. A seed angel cares about founder grit and optionality. A Series A fund cares about repeatable GTM and unit economics. A corporate strategic cares about ecosystem fit. Knowing which game you are playing changes what you emphasize.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `verdict-output.md` — dimension scores (required)
- `startup-canvas-output.md` — business model and pricing
- `market-size-output.md` — TAM/SAM/SOM
- `battle-cards-output.md` — competitive position
- `pitch-deck-output.md` — narrative structure (if available)

If `verdict-output.md` is missing, tell the user to run `/verdict` first.

## Frameworks

- *Secrets of Sand Hill Road* (Kupor) — how institutional VCs evaluate deals: team, market, product, go-to-market, and financial model. What moves from "interesting" to "funded" is pattern-matching on these dimensions.
- *Venture Deals* (Feld & Mendelson) — the mechanics behind different investor types and what they optimize for at each stage.

## Methodology

1. **Score through three investor lenses.** Re-read the verdict and all available outputs through each perspective:

   **Lens A: Seed Angel ($25K-$250K check)**
   - Weights heavily: founder-market fit, personal conviction, optionality
   - Weights lightly: unit economics, competitive moat, TAM precision
   - Key question: "Is this founder obsessed with this problem and do I believe they will figure it out?"
   - Dealbreakers: no domain expertise, no skin in the game, idea feels like a side project

   **Lens B: Series A Fund ($2M-$10M check)**
   - Weights heavily: repeatable GTM motion, unit economics, market size, competitive defensibility
   - Weights lightly: founder backstory, vision breadth
   - Key question: "Is there evidence of a repeatable acquisition channel with positive unit economics?"
   - Dealbreakers: no evidence of GTM fit, CAC > LTV, market too small for fund math

   **Lens C: Corporate Strategic**
   - Weights heavily: ecosystem fit, strategic value to parent company, data/IP value
   - Weights lightly: standalone financial returns, founder independence
   - Key question: "Does this strengthen our core business or give us access to a market we cannot reach organically?"
   - Dealbreakers: no strategic fit, competitive with parent's roadmap

2. **For each lens, produce a scorecard:**
   - Score each of the 6 verdict dimensions (Demand, Market, Model, Risk, Competition, Validation) on a 1-5 scale weighted by that investor type's priorities
   - Identify the #1 strength and #1 concern from that investor's perspective
   - State the likely decision: FUND / PASS / CONDITIONAL (with conditions)
   - Draft the one-line internal memo note the investor would write

3. **Identify the best investor fit.** Based on the three scorecards, recommend:
   - Which investor type is the best fit for this idea at this stage
   - What to emphasize in the pitch for that investor type
   - What to de-emphasize or preemptively address

4. **Write full output** to `./founder-outputs/investor-lens-output.md`. Display a concise summary in chat: the three verdicts, best fit recommendation, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/investor-lens-output.md`. Display concise summary in chat.

File format:

```markdown
# Investor Lens Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Lens A: Seed Angel

### Scorecard
| Dimension | Score (1-5) | Weight | Notes |
|---|---|---|---|
| Demand | [score] | High | [note] |
| Market | [score] | Low | [note] |
| Model | [score] | Low | [note] |
| Risk | [score] | Medium | [note] |
| Competition | [score] | Low | [note] |
| Validation | [score] | Medium | [note] |

**#1 Strength:** [What excites this investor]
**#1 Concern:** [What gives them pause]
**Likely Decision:** [FUND / PASS / CONDITIONAL]
**Internal Memo Note:** "[One sentence they'd write to partners]"

## Lens B: Series A Fund
[Same structure with different weights]

## Lens C: Corporate Strategic
[Same structure with different weights]

## Best Investor Fit
**Recommended type:** [Seed Angel / Series A / Corporate Strategic]
**Why:** [2-3 sentences]
**Emphasize in pitch:** [What to lead with]
**Address preemptively:** [What to get ahead of]

## Pipeline Status
**Best Fit:** [Investor type]
**Recommended Next:** /objection-map, /elevator-pitch
```
