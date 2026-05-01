---
name: unit-economics
description: This skill should be used when the user says "unit economics", "CAC", "LTV", "payback period", "gross margin", "contribution margin", "is this profitable", "do the math", "make the numbers work", "cost per customer", "lifetime value", or needs to validate whether the business model can sustain itself per customer. Walks through CAC, LTV, payback, gross margin, and contribution margin with specific numbers and viability ratings.
version: 0.1.0
---

# Unit Economics

Validate whether the business model works on a per-customer basis. Many ideas with strong demand and a real customer fail on math the founder never did. This skill forces the calculation before building so broken margins are discovered now, not after burning runway.

Posture: numerate skeptic. Demand specific numbers, not ranges. Flag when an assumption is doing too much work.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — pricing model, cost structure (required)
- `customer-archetype-output.md` — workaround cost (sets price ceiling)
- `market-size-output.md` — SOM and customer count (sizing total opportunity)
- `gtm-plan-output.md` — channel CAC estimates (if available)

If `startup-canvas-output.md` is missing, tell the user to run `/startup-canvas` first — there is no pricing or cost structure to do unit economics on.

## Frameworks

- *Lean Analytics* (Croll & Yoskovitz) — the metrics that matter at each stage. For pre-revenue: validation. For revenue: unit economics. For scale: cohort retention. The numbers that lie at each stage are different.
- *$100M Offers* (Hormozi) — the value equation. Price should be 10x the cost-to-serve at minimum. If pricing barely covers costs, the offer is broken before any growth strategy can save it.
- *Predictable Revenue* (Ross & Tyler) — for B2B/SaaS, CAC is dominated by sales motion. Self-serve, inside sales, and field sales have order-of-magnitude different CAC and require different pricing.

## Methodology

1. **Establish revenue per customer.** From the canvas:
   - Pricing model (subscription, usage, one-time, hybrid)
   - Average contract value (ACV) — annualized if subscription
   - Expansion revenue assumption (upsell, seat growth) — flag if optimistic
   - **Output: Revenue per customer per year ($X)**

2. **Calculate cost of goods sold (COGS).** What does it cost to serve one customer per year:
   - Hosting/infrastructure per customer
   - Third-party APIs per customer (LLM costs, payment processing, etc.)
   - Customer support cost (allocated)
   - Onboarding/implementation cost (amortized)
   - **Output: COGS per customer per year ($Y)**

3. **Calculate gross margin.**
   - Gross margin = (Revenue - COGS) / Revenue
   - **Healthy:** SaaS >70%, marketplace >50%, hardware >30%
   - **Red flag:** below the threshold for the business type means scale won't help
   - **Output: Gross margin %**

4. **Estimate customer acquisition cost (CAC).** From GTM plan or first-principles:
   - Sales costs per customer (SDR/AE salary × deals closed per rep)
   - Marketing spend per customer (channel CAC from gtm-plan)
   - Tools and software allocated
   - **Self-serve CAC:** typically $50-$500
   - **Inside sales CAC:** typically $1K-$10K
   - **Field sales CAC:** typically $20K-$200K
   - **Output: Blended CAC ($Z)**

5. **Calculate lifetime value (LTV).**
   - LTV = (Revenue × Gross margin %) / Churn rate
   - For pre-revenue: estimate churn from analogous companies (`/analogous-cos` if available)
   - Conservative default: 5% monthly churn for SMB SaaS, 1% for enterprise, 10% for consumer
   - **Output: LTV ($W)**

6. **Calculate the LTV:CAC ratio.**
   - **3:1 or better** — Healthy. Build.
   - **1:1 to 3:1** — Marginal. Pricing or CAC must improve.
   - **Below 1:1** — Broken. You lose money on every customer. No volume fixes this.
   - **Output: LTV:CAC ratio**

7. **Calculate CAC payback period.**
   - Payback = CAC / (Monthly revenue × Gross margin)
   - **Under 12 months** — Healthy. Capital-efficient.
   - **12-24 months** — Acceptable for funded startups. Requires patient capital.
   - **Over 24 months** — Concerning. Tied to long sales cycles or weak retention.
   - **Output: Payback period in months**

8. **Identify the sensitive variables.** Which assumption, if wrong by 20%, breaks the model?
   - Common load-bearing assumptions: churn rate, expansion revenue, CAC
   - Run sensitivity analysis: what happens to LTV:CAC if churn doubles? If pricing drops 20%?
   - **Output: Top 2 sensitive variables and their break-points**

9. **Benchmark against the workaround cost.** The customer's current workaround cost (from archetype) sets the price ceiling. If the price exceeds the workaround cost, customers won't pay. If pricing is far below, leaving money on the table.

10. **Render viability rating.**
    - **VIABLE** — Gross margin healthy, LTV:CAC ≥3:1, payback <12 months
    - **MARGINAL** — One metric broken, others healthy. Specific fix required.
    - **BROKEN** — Multiple metrics broken. Pricing, cost, or model needs structural change.

11. **Write full output** to `./founder-outputs/unit-economics-output.md`. Display a concise summary in chat: ACV, gross margin, LTV:CAC, payback period, viability rating.

## Red Flags

- **"Costs will come down at scale."** Sometimes true, often not. Most SaaS COGS are dominated by per-customer costs (LLM tokens, third-party APIs) that scale linearly. Demand evidence.
- **"Our churn will be 1% monthly."** Without retention data, this is a guess. Use analog company benchmarks. SMB SaaS averages 3-7% monthly.
- **CAC estimated only from paid channels.** Founders often forget sales rep salaries, content production, conference costs, time spent in meetings.
- **LTV calculation uses revenue, not gross profit.** Common error. LTV must use the *margin*, not the *revenue*. Otherwise you're discounting what doesn't reach the bottom line.
- **No sensitivity analysis.** If a single optimistic assumption (like 90% net retention) breaks the model when adjusted, the math is too fragile.
- **Pricing exceeds workaround cost.** If the customer's manual workaround costs $200/month and the product is priced at $500, they'll keep doing it manually.

## Output

Write full output to `./founder-outputs/unit-economics-output.md`. Display concise summary in chat.

File format:

```markdown
# Unit Economics Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Revenue per Customer
**Pricing model:** [Subscription / Usage / One-time / Hybrid]
**Average contract value (annualized):** $[X]
**Expansion assumption:** [+X% in year 2]

## Cost of Goods Sold
| Cost Category | $ per customer per year |
|---|---|
| Infrastructure | $[amount] |
| Third-party APIs | $[amount] |
| Support (allocated) | $[amount] |
| Onboarding (amortized) | $[amount] |
| **Total COGS** | **$[Y]** |

## Gross Margin
**Gross margin:** [X]%
**Benchmark:** [Healthy/Marginal/Broken for business type]

## Customer Acquisition Cost
**Sales motion:** [Self-serve / Inside sales / Field sales]
**Blended CAC:** $[Z]
**Breakdown:**
- Sales: $[amount]
- Marketing: $[amount]
- Tools: $[amount]

## Lifetime Value
**Churn rate assumption:** [X]% monthly
**LTV:** $[W]
**Calculation:** ($[Revenue] × [GM]%) / [Churn]

## Key Ratios
| Metric | Value | Verdict |
|---|---|---|
| LTV:CAC ratio | [X]:1 | [Healthy / Marginal / Broken] |
| Payback period | [X] months | [Healthy / Acceptable / Concerning] |
| Gross margin | [X]% | [Healthy / Marginal / Broken] |

## Sensitivity Analysis
**Top sensitive variable:** [Variable]
**Break-point:** If [variable] worsens by [X]%, LTV:CAC drops to [Y]:1

**Second sensitive variable:** [Variable]
**Break-point:** [Same]

## Workaround Cost Benchmark
**Customer workaround cost (from archetype):** $[amount/month]
**Our pricing:** $[amount/month]
**Verdict:** [Below ceiling / At ceiling / Above ceiling — over-priced]

## Viability Rating
**[VIABLE / MARGINAL / BROKEN]**

[2-3 sentences explaining the rating with specific numbers]

## Required Fixes (if MARGINAL or BROKEN)
1. [Specific change to pricing, cost, or model]
2. [Specific change]

## Pipeline Status
**Unit Economics:** [VIABLE / MARGINAL / BROKEN]
**Recommended Next:** /assumption-map (if VIABLE) or fix the math first
```
