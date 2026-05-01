---
name: startup-canvas
description: This skill should be used when the user says "business model", "lean canvas", "value prop", "how do I make money", "business model canvas", "revenue model", "pricing model", "unit economics", or needs to structure a complete business model. Combines Lean Canvas and Business Model Canvas into one structured output with problems, segments, UVP, solution, channels, revenue, costs, metrics, and unfair advantage.
version: 0.1.0
---

# Startup Canvas

Business model and value proposition in one structured output. Synthesizes prior pipeline outputs into a coherent model — or exposes where the model breaks.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `pressure-test-output.md` — demand evidence, JTBD framing, red flags
- `customer-archetype-output.md` — specific customer, workaround cost, decision role
- `scope-output.md` — scope calibration (if exists)

If `pressure-test-output.md` or `customer-archetype-output.md` are missing, tell the user to run those first — the canvas will be generic without them.

## Frameworks

- *The Lean Startup* (Ries) — Build-Measure-Learn loop. The canvas is a hypothesis, not a plan. Every cell is an assumption to be tested.
- *Business Model Generation* (Osterwalder) — BMC nine building blocks adapted for early-stage: problems replace "value proposition exploration", and unfair advantage replaces "key partnerships" at this stage.
- *Competing Against Luck* (Christensen) — JTBD value proposition framing. The UVP must answer the job-to-be-done, not describe features.
- *$100M Offers* (Hormozi) — value proposition sharpness. The offer must be specific, measurable, and feel like a steal at the price point.

## Methodology

1. **Problem stack.** Identify the top 3 problems, ranked by severity. For each: state the problem, who has it (from archetype), and what the current workaround costs. Pull directly from pressure-test and archetype outputs. If the problems are vague, push back.

2. **Customer segments.** Define from the archetype output. Include primary segment and any secondary segment. Each segment needs: who they are, how many exist, and whether they are the buyer, user, or champion.

3. **Unique value proposition.** Write one sentence: "[Product] helps [specific customer] [achieve outcome] by [mechanism], unlike [alternative] which [limitation]." Test against Hormozi's criteria: is it specific, measurable, and does it feel like a steal?

4. **Solution.** Top 3 features that directly address the top 3 problems. One-to-one mapping. If a feature does not map to a ranked problem, question whether it belongs.

5. **Channels.** How to reach the customer. Pull from archetype's information sources. Distinguish between:
   - **Awareness channels** — how they discover you (content, communities, ads)
   - **Acquisition channels** — how they sign up or buy (direct sales, self-serve, marketplace)
   - **Activation channels** — how they get first value (onboarding, integration)

6. **Revenue streams and pricing.** Define:
   - Pricing model (subscription, usage-based, one-time, freemium)
   - Price point and justification (anchored to workaround cost from archetype)
   - Revenue per customer per year
   - Expansion potential (upsell, cross-sell, seat expansion)

7. **Cost structure.** Identify the top 3-5 cost categories. Distinguish fixed vs. variable. Flag any costs that scale faster than revenue — that is a structural problem.

8. **Key metrics.** Identify the one metric that matters at this stage. Not a dashboard of 20 metrics. One number that tells you whether the business is working. Typically: activation rate, weekly retention, or revenue per customer.

9. **Unfair advantage.** What cannot be easily copied or bought? Acceptable: proprietary data, network effects, switching costs, regulatory moats, founder-market fit with deep domain expertise. Not acceptable: "first mover advantage" (rarely durable), "our team" (vague), "our technology" (unless truly novel).

10. **Unit economics sanity check.** Before declaring coherence, run the basic math:
    - **Gross margin estimate.** Revenue per customer minus estimated COGS (hosting, third-party APIs, support, onboarding). If gross margin is below 50% for SaaS or 30% for marketplace, flag it.
    - **CAC vs. price.** If the sales motion required to acquire a customer (self-serve / inside sales / field sales) costs more than 1/3 of first-year revenue, the business starts upside-down.
    - **Payback sanity.** At current pricing and cost, how many months until CAC is recovered? Over 24 months is a structural problem.
    - Surface any red flags here. A full unit economics calculation is available via `/unit-economics`.

11. **Coherence check.** Review the complete canvas for internal consistency:
    - Do the problems match the customer?
    - Does the UVP address the #1 problem?
    - Does pricing align with workaround cost?
    - Do channels match where the customer actually is?
    - Does the cost structure support the pricing?
    Flag any gaps or contradictions.

12. **Write full output** to `./founder-outputs/startup-canvas-output.md`. Display a concise summary in chat: UVP, pricing model, key metric, coherence rating, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/startup-canvas-output.md`. Display concise summary in chat.

File format:

```markdown
# Startup Canvas Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Problems (Ranked)
1. **[Problem]** — [Who has it] — Workaround cost: [amount]
2. **[Problem]** — [Who has it] — Workaround cost: [amount]
3. **[Problem]** — [Who has it] — Workaround cost: [amount]

## Customer Segments
**Primary:** [Segment from archetype]
**Secondary:** [If applicable]

## Unique Value Proposition
[One sentence: product + customer + outcome + mechanism + differentiation]

## Solution
1. [Feature] → solves Problem #1
2. [Feature] → solves Problem #2
3. [Feature] → solves Problem #3

## Channels
**Awareness:** [How they discover]
**Acquisition:** [How they buy]
**Activation:** [How they get first value]

## Revenue Streams
**Model:** [Subscription / Usage / One-time / Freemium]
**Price:** [Amount and justification]
**Revenue per customer:** [$/year]
**Expansion:** [Upsell / cross-sell path]

## Cost Structure
| Category | Type | Estimate |
|---|---|---|
| [Category] | Fixed / Variable | [Amount] |

## Key Metric
**The one metric that matters:** [Metric and target]

## Unfair Advantage
[What cannot be easily copied, with explanation]

## Unit Economics Sanity Check
**Estimated gross margin:** [X]%  — [Healthy / Marginal / Red flag]
**CAC vs. first-year revenue:** [CAC is X% of ACV — sustainable / concerning]
**Estimated payback period:** [X months — healthy / concerning]
**Flags:** [List any structural issues, or "None — run /unit-economics for full analysis"]

## Coherence Check
**Rating:** [COHERENT / GAPS / BROKEN]
**Issues found:** [List or "None"]

## Pipeline Status
**Coherence:** [COHERENT / GAPS / BROKEN]
**Recommended Next:** /assumption-map or /battle-cards
```
