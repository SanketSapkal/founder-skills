---
name: market-size
description: This skill should be used when the user says "how big is this market", "market size", "TAM", "SAM", "SOM", "total addressable market", "market opportunity", "how many potential customers", or needs bottom-up market sizing with real data sources rather than top-down guesses.
version: 0.1.0
---

# Market Size

TAM/SAM/SOM with real-world data, not made-up multiples. Bottom-up first — count real customers and multiply by price. Top-down is a sanity check, not the primary method.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `pressure-test-output.md` — demand evidence, workaround details
- `customer-archetype-output.md` — specific customer definition, company size, industry

If `customer-archetype-output.md` is missing, the market sizing will be generic. Recommend the user run `/customer-archetype` first.

## Frameworks

- *Lean Analytics* (Croll & Yoskovitz) — one metric that matters. Realistic market framing for early stage. Do not build castles on inflated TAM numbers. SOM is what matters for the next 3 years.

## Methodology

1. **Privacy gate.** Before searching the web for market data, confirm with the user: "I'll search for market data on [industry/category]. This will use general terms only — no proprietary details. Proceed?" Wait for confirmation.

2. **Bottom-up TAM.** Count the total number of potential customers who have the problem. Use:
   - Industry databases and reports (search for "[industry] market size [year]")
   - Public company filings and earnings calls
   - Census data, bureau of labor statistics, trade associations
   - LinkedIn searches for the target role (from archetype)
   - Calculate: `number of potential customers × annual revenue per customer`
   - Clearly label each data point as **cited** (with source) or **estimated** (with reasoning)

3. **Top-down sanity check.** Find a broader market number from analyst reports. Calculate what percentage this product would need to capture. If the bottom-up and top-down numbers are wildly different, investigate why.

4. **SAM (Serviceable Addressable Market).** Narrow TAM to the segment this product can actually serve given:
   - Geographic constraints (US only? Global?)
   - Company size constraints (from archetype)
   - Industry vertical constraints
   - Technical requirements (need internet? specific OS? API access?)

5. **SOM (Serviceable Obtainable Market).** What is realistically capturable in 3 years given:
   - Go-to-market approach (from canvas if available)
   - Sales cycle length
   - Competitive dynamics
   - Team size and funding constraints
   - Typical penetration rates for similar products (1-5% of SAM is common for year 3)

6. **Confidence assessment.** Rate overall confidence:
   - **HIGH** — multiple corroborating data sources, bottom-up and top-down align
   - **MEDIUM** — some data sources, reasonable estimates, minor gaps
   - **LOW** — mostly estimates, limited data, significant assumptions

7. **Write full output** to `./founder-outputs/market-size-output.md`. Display a concise summary in chat: TAM/SAM/SOM numbers, confidence level, key data sources, and note that full output is saved to the file.

## Red Flags

- **Top-down only.** "It's a $50B market and we just need 1%" is not analysis. The 1% assumption hides all the hard questions.
- **No data sources cited.** Every number should have a source or be explicitly labeled as an estimate.
- **TAM conflation.** The TAM for "enterprise software" is not the TAM for "shipment reconciliation tools for mid-market logistics companies." Be precise about what market is actually being sized.
- **Hockey stick SOM.** If SOM assumes 20%+ market penetration in 3 years with no distribution advantage, challenge it.

## Output

Write full output to `./founder-outputs/market-size-output.md`. Display concise summary in chat.

File format:

```markdown
# Market Size Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Total Addressable Market (TAM)
**Bottom-up estimate:** $[amount]
**Calculation:** [number of customers] × [revenue per customer] = [TAM]
**Top-down sanity check:** $[amount] (source: [report/filing])
**Alignment:** [Bottom-up and top-down agree / diverge — explain]

### Data Sources
| Data Point | Value | Source | Type |
|---|---|---|---|
| [Data point] | [Value] | [Source] | Cited / Estimated |

## Serviceable Addressable Market (SAM)
**SAM:** $[amount]
**Narrowing factors:**
- Geographic: [constraint]
- Company size: [constraint]
- Industry: [constraint]
- Technical: [constraint]

## Serviceable Obtainable Market (SOM)
**SOM (3-year):** $[amount]
**Assumptions:**
- Penetration rate: [%] of SAM
- GTM approach: [method]
- Sales cycle: [length]
- Competitive dynamics: [summary]

## Confidence Assessment
**Overall:** [HIGH / MEDIUM / LOW]
**Gaps:** [What data is missing]
**Key assumptions:** [What could be wrong]

## Pipeline Status
**Opportunity:** [LARGE / MEDIUM / SMALL / UNPROVEN]
**Recommended Next:** /startup-canvas or /assumption-map
```
