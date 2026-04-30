---
name: pitch-deck
description: This skill should be used when the user says "pitch deck", "investor deck", "fundraising deck", "Sequoia format", "put together a deck", "I need to pitch", or needs to assemble all founder-outputs into a structured investor pitch narrative. Follows the Sequoia narrative arc and enforces logical coherence between slides.
version: 0.1.0
---

# Pitch Deck

Assemble all founder-outputs into a structured investor pitch narrative using the Sequoia format. Pitch decks fail not because slides are ugly but because the narrative logic breaks down — this skill enforces the logic.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `verdict-output.md` — must show BUILD (required)
- `pressure-test-output.md` — problem validation and demand evidence
- `customer-archetype-output.md` — who the customer is
- `market-size-output.md` — TAM/SAM/SOM
- `startup-canvas-output.md` — business model, UVP, pricing
- `battle-cards-output.md` — competitive positioning
- `why-now-output.md` — timing thesis (if available)

If `verdict-output.md` is missing or shows KILL/PIVOT, recommend running `/verdict` first. A pitch deck for a killed idea is a waste of time.

## Frameworks

- *Secrets of Sand Hill Road* (Kupor) — what VCs actually evaluate: team-market fit, market size and timing, defensibility, capital efficiency, path to liquidity.
- *Venture Deals* (Feld & Mendelson) — the mechanics of term sheets and what investors optimize for at each stage.

## Methodology

1. **Verify the narrative inputs.** Check which output files exist. Flag gaps — a pitch deck with missing market data or no competitive analysis has visible holes.

2. **Build the Sequoia narrative arc.** Each slide maps to a founder-output:

   | Slide | Content Source | Key Question |
   |---|---|---|
   | **Problem** | `pressure-test-output.md` | What pain exists and who feels it? |
   | **Solution** | `startup-canvas-output.md` | How does this product solve it? |
   | **Why Now** | `why-now-output.md` or pressure-test | What changed that makes this viable today? |
   | **Market** | `market-size-output.md` | How big is the opportunity (bottom-up)? |
   | **Product** | `startup-canvas-output.md` | What does the product actually do (3 features)? |
   | **Business Model** | `startup-canvas-output.md` | How does it make money? |
   | **Competition** | `battle-cards-output.md` | Why will this win? (positioning, not features) |
   | **Traction** | User-provided or pressure-test | What evidence of demand exists today? |
   | **Team** | Ask the user | Why is this team uniquely positioned? |
   | **Ask** | Ask the user | How much capital, for what milestones? |

3. **For each slide, produce:**
   - **Headline** — one sentence that makes the key claim
   - **Supporting points** — 3-4 bullets with data from founder-outputs
   - **Narrative bridge** — one sentence connecting this slide to the next (the "so what" that maintains flow)
   - **Weak spot flag** — if the evidence is thin, flag it honestly

4. **Test narrative coherence.** Read the slide sequence end-to-end. Check:
   - Does the problem lead logically to the solution?
   - Does the "why now" explain why incumbents have not solved this?
   - Does the market size justify the investment ask?
   - Does the competitive analysis support the positioning?
   - Does the traction validate the demand claim?
   Flag any logical breaks.

5. **Ask the user** for the two slides that require user input: Team and Ask. For Team: "Who is on the team and what makes them uniquely qualified?" For Ask: "How much are you raising and what milestones will it fund?"

6. **Write full output** to `./founder-outputs/pitch-deck-output.md`. Display a concise summary in chat: the 10 slide headlines in sequence, any weak spots flagged, and note that full output is saved to the file.

## Red Flags

- **Solution before problem.** The problem slide must make the audience feel the pain before the solution is revealed.
- **Top-down market sizing on the market slide.** Investors see through "$50B market, we just need 1%." Use the bottom-up numbers from `/market-size`.
- **"No competition" slide.** Every idea has competition. Showing awareness of competition builds credibility. Use the positioning gap from `/battle-cards`.
- **Ask without milestones.** "We're raising $2M" is incomplete. "We're raising $2M to reach [milestone] by [date]" is a real ask.

## Output

Write full output to `./founder-outputs/pitch-deck-output.md`. Display concise summary in chat.

File format:

```markdown
# Pitch Deck Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Slide 1: Problem
**Headline:** [One sentence]
**Supporting points:**
- [Data point from pressure-test]
- [Data point from pressure-test]
- [Data point from archetype]
**Narrative bridge:** [Connection to next slide]
**Weak spot:** [Flag or "None"]

## Slide 2: Solution
[Same structure]

## Slide 3: Why Now
[Same structure]

## Slide 4: Market
[Same structure]

## Slide 5: Product
[Same structure]

## Slide 6: Business Model
[Same structure]

## Slide 7: Competition
[Same structure]

## Slide 8: Traction
[Same structure]

## Slide 9: Team
[Same structure]

## Slide 10: Ask
[Same structure]

## Narrative Coherence Check
**Overall flow:** [COHERENT / GAPS / BROKEN]
**Weakest slide:** [Which slide and why]
**Strongest slide:** [Which slide and why]

## Pipeline Status
**Deck Ready:** [YES / GAPS — list missing data]
**Recommended Next:** /investor-lens, /objection-map, /elevator-pitch
```
