---
name: pivot-paths
description: This skill should be used when the user says "how should I pivot", "what are my pivot options", "the verdict was kill", "the verdict was pivot", "what else could I do with this", "salvage this idea", or has received a KILL or PIVOT verdict and needs concrete alternative directions. Generates 3 structured pivot paths — not vague advice.
version: 0.1.0
---

# Pivot Paths

When `/verdict` returns KILL or PIVOT, this skill generates 3 concrete pivot directions. Does not say "consider pivoting" and stop — produces specific, actionable alternatives grounded in the evidence from the pipeline.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `verdict-output.md` — the verdict and its reasoning (required)
- `pressure-test-output.md` — what demand evidence exists
- `customer-archetype-output.md` — who was the original customer
- `startup-canvas-output.md` — what business model was proposed
- `battle-cards-output.md` — competitive landscape

If `verdict-output.md` is missing or shows BUILD, inform the user this skill is designed for KILL or PIVOT verdicts. Offer to run `/verdict` first.

## Methodology

1. **Diagnose the failure point.** From the verdict, identify what specifically failed:
   - **Demand failure** — no evidence of customer pull → pivot the customer or the problem
   - **Market failure** — market too small or too competitive → pivot the market or the positioning
   - **Model failure** — unit economics or pricing broken → pivot the business model
   - **Feasibility failure** — cannot be built with available resources → pivot the product form
   - **Timing failure** — too early or too late → pivot the timing or the wedge

2. **Generate 3 pivot paths.** Each pivot must be a different type:

   **Path A: Adjacent Market.** Keep the core technology/capability but target a different customer segment or industry. Use battle cards to identify underserved segments.

   **Path B: Different Customer, Same Problem.** The problem is real but the current target customer is wrong. Who else has this problem with more urgency, higher willingness to pay, or easier access?

   **Path C: Different Business Model.** Keep the customer and problem but change how value is delivered and captured. Examples: SaaS → marketplace, product → service, B2C → B2B, one-time → recurring.

3. **For each pivot path, provide:**
   - One-sentence description
   - Why this direction addresses the specific failure point
   - New target customer (specific, not vague)
   - What changes vs. what stays the same
   - Key assumption to validate first
   - Rough experiment to test it (one sentence)
   - Risk level relative to the original idea

4. **Rank the paths.** Order by viability given the evidence at hand. State which path has the most evidence supporting it and which is the biggest leap.

5. **Write full output** to `./founder-outputs/pivot-paths-output.md`. Display a concise summary in chat: the 3 paths ranked, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/pivot-paths-output.md`. Display concise summary in chat.

File format:

```markdown
# Pivot Paths Output
**Generated:** [date]
**Original Idea:** [one-sentence restatement]
**Verdict:** [KILL / PIVOT]
**Failure Point:** [What specifically failed]

## Path A: Adjacent Market
**Direction:** [One sentence]
**Addresses:** [Which failure point this fixes]
**New Target Customer:** [Specific]
**What Changes:** [List]
**What Stays:** [List]
**Key Assumption:** [What to validate first]
**Quick Test:** [One-sentence experiment]
**Risk Level:** [Lower / Similar / Higher than original]

## Path B: Different Customer
[Same structure]

## Path C: Different Model
[Same structure]

## Recommended Path
**[Path letter]** — [Why this has the most evidence / lowest risk]

## Pipeline Status
**Pivot Direction:** [A / B / C selected or user to decide]
**Recommended Next:** Run /pressure-test on the chosen pivot direction
```
