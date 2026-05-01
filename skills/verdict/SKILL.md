---
name: verdict
description: This skill should be used when the user says "should I build this", "give me a verdict", "is this worth it", "final verdict", "go or no-go", "make the call", "what's the verdict", "kill or build", or has completed multiple founder-skills pipeline steps and wants a synthesis. Reads all founder-outputs files and produces an explicit BUILD / KILL / PIVOT judgment with structured reasoning. No other skills repo has this capability.
version: 0.1.0
---

# Verdict

Synthesize all prior skill outputs into an explicit BUILD / KILL / PIVOT judgment. This is the endpoint of the founder-skills pipeline — not a suggestion, not a hedge, but a decision with structured reasoning.

Posture: honest, direct, calibrated. Do not soften a KILL to be polite. Do not inflate a BUILD to be encouraging. Call it as the evidence demands.

## Input Dependencies

Read ALL files from `./founder-outputs/` before proceeding:
- `pressure-test-output.md` — demand evidence and red flags
- `scope-output.md` — scope calibration
- `customer-archetype-output.md` — customer specificity
- `market-size-output.md` — TAM/SAM/SOM and data quality
- `startup-canvas-output.md` — business model coherence
- `battle-cards-output.md` — competitive position
- `assumption-map-output.md` — risk concentration
- `pretotype-output.md` — validation path clarity
- `founder-fit-output.md` — founder-market fit (if run)
- `unit-economics-output.md` — unit economics viability (if run)
- `regulatory-risk-output.md` — regulatory exposure (if run)

If some outputs are missing, proceed with available data but note the gaps and reduce confidence accordingly. The minimum required input is `pressure-test-output.md` — if that does not exist, tell the user to run `/pressure-test` first.

## Frameworks

- *The Hard Thing About Hard Things* (Horowitz) — distinguish between hard problems (solvable with effort and persistence) and fatal problems (structural flaws that no amount of execution can fix). A KILL verdict means the problem is fatal, not merely hard.
- *Secrets of Sand Hill Road* (Kupor) — apply the institutional investor lens: team-market fit, market size and timing, defensibility, capital efficiency, and path to liquidity. Score like a partner evaluating a seed deck.

## Methodology

1. **Read all available output files.** Scan `./founder-outputs/` and read every file present. Note which files exist and which are missing.

2. **Score seven dimensions.** For each dimension, assign a discrete rating based on the evidence in the output files:

   | Dimension | Source | Ratings |
   |---|---|---|
   | Demand Reality | `pressure-test-output.md` | STRONG / WEAK / UNCLEAR |
   | Market Opportunity | `market-size-output.md` | LARGE / MEDIUM / SMALL / UNPROVEN |
   | Model Coherence | `startup-canvas-output.md` | COHERENT / GAPS / BROKEN |
   | Risk Concentration | `assumption-map-output.md` | Name the single assumption that kills this if wrong |
   | Competitive Position | `battle-cards-output.md` | DIFFERENTIATED / CROWDED / UNCLEAR |
   | Validation Path | `pretotype-output.md` | CLEAR / UNCLEAR |
   | Founder-Market Fit | `founder-fit-output.md` | STRONG / MODERATE / WEAK / UNSCORED |

   Additional inputs when available:
   - `unit-economics-output.md` — flag if BROKEN; a broken unit model downgrades Model Coherence
   - `regulatory-risk-output.md` — flag if HIGH or BLOCKING; a BLOCKING regulatory risk can override a BUILD verdict

   If a source file is missing, mark the dimension as UNSCORED and note it.

3. **Identify the kill assumption.** From the assumption map, identify the single riskiest assumption. State it plainly: "If [this assumption] is wrong, the entire idea fails because [reason]."

4. **Render the verdict.** Apply these decision rules:
   - **BUILD** — Demand is STRONG, model is COHERENT or has only minor GAPS, no fatal risk concentration, and at least a CLEAR validation path. Evidence supports proceeding to build.
   - **PIVOT** — The core insight or market is valid, but the current form, customer, or model has structural problems. Must specify *what* to pivot: the customer segment, the business model, the product form, or the go-to-market approach.
   - **KILL** — Fundamental demand, market, or feasibility problem that cannot be pivoted around. The problem is fatal, not hard. No amount of execution fixes a market that does not exist or a customer who does not care.

5. **State three specific reasons.** Not generic ("the market is challenging"). Specific ("the only named customer workaround costs $200/month, which sets a price ceiling below the cost to serve").

6. **State what would change the verdict.** What new evidence, pivot, or condition would flip the verdict? Be specific: "If you found 10 companies currently paying >$500/month for manual workarounds, that would shift demand from WEAK to STRONG."

7. **Write full output** to `./founder-outputs/verdict-output.md`. Display a concise summary in chat: the verdict, three reasons, what would change it, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/verdict-output.md`. Display concise summary in chat.

File format:

```markdown
# Verdict Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Data Completeness
**Files read:** [list of files found]
**Files missing:** [list of files not found, or "None"]
**Confidence adjustment:** [Full / Reduced — explain if reduced]

## Dimension Scores

| Dimension | Rating | Key Evidence |
|---|---|---|
| Demand Reality | [rating] | [one-line evidence] |
| Market Opportunity | [rating] | [one-line evidence] |
| Model Coherence | [rating] | [one-line evidence] |
| Risk Concentration | [named assumption] | [why it's fatal if wrong] |
| Competitive Position | [rating] | [one-line evidence] |
| Validation Path | [rating] | [one-line evidence] |
| Founder-Market Fit | [STRONG / MODERATE / WEAK / UNSCORED] | [one-line evidence or "Not run"] |

## Kill Assumption
**[The single assumption that kills this if wrong]**
[2-3 sentences explaining why]

## Verdict
# [BUILD / PIVOT / KILL]

### Three Reasons
1. [Specific reason with evidence]
2. [Specific reason with evidence]
3. [Specific reason with evidence]

### What Would Change This Verdict
[Specific evidence, pivot, or condition that would flip the verdict]

## Pipeline Status
**Verdict:** [BUILD / KILL / PIVOT]
**Recommended Next:** [/pivot-paths if KILL or PIVOT, otherwise "Proceed to build"]
```
