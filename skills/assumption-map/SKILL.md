---
name: assumption-map
description: This skill should be used when the user says "what are my assumptions", "what could go wrong", "riskiest bets", "risk assessment", "assumption testing", "what's the biggest risk", "what if I'm wrong", or needs to surface and prioritize the riskiest assumptions before building anything. Uses an Impact x Uncertainty matrix across 8 risk categories.
version: 0.1.0
---

# Assumption Map

Surface and prioritize the riskiest assumptions before building anything. Every startup is a bundle of assumptions — this skill identifies which ones are load-bearing and which would be fatal if wrong.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — business model assumptions (problems, UVP, pricing, channels)
- `market-size-output.md` — market assumptions (TAM/SAM/SOM, data confidence)
- `customer-archetype-output.md` — customer assumptions (if available)
- `pressure-test-output.md` — demand assumptions (if available)

If `startup-canvas-output.md` is missing, tell the user to run `/startup-canvas` first — assumption mapping without a business model is guesswork.

## Frameworks

- *Continuous Discovery Habits* (Torres) — Opportunity Solution Trees and assumption mapping methodology. Categorize assumptions, rate them on impact and uncertainty, and prioritize the highest-risk ones for testing first. The riskiest assumption is the one that kills the business if wrong AND that has the least evidence supporting it.

## Methodology

1. **Extract assumptions from prior outputs.** Read through all available output files and extract every implicit or explicit assumption. Look for:
   - Statements presented as facts without evidence
   - "We believe...", "Users will...", "The market is..."
   - Pricing assumptions (customers will pay $X)
   - Channel assumptions (customers can be reached via Y)
   - Technical assumptions (this can be built with Z)

2. **Categorize each assumption.** Place each into one of 8 categories:

   | Category | Question |
   |---|---|
   | **Value** | Does this solve a real problem worth paying for? |
   | **Usability** | Can customers actually use it without hand-holding? |
   | **Viability** | Can we build a sustainable business at this price and cost? |
   | **Feasibility** | Can we actually build this with available resources and technology? |
   | **Go-to-Market** | Can we reach and convert customers through identified channels? |
   | **Strategy** | Is this the right approach vs. alternatives? |
   | **Team** | Do we have the skills, capacity, and domain expertise? |
   | **Timing** | Is now the right moment — not too early, not too late? |

3. **Rate each assumption.** For each:
   - **Impact** (H/M/L) — how badly does the business fail if this assumption is wrong?
   - **Uncertainty** (H/M/L) — how much evidence exists to support or refute this assumption?

4. **Prioritize using Impact × Uncertainty matrix.**
   - **Priority 1 (Test Immediately):** High Impact + High Uncertainty — these kill the business if wrong and have the least evidence
   - **Priority 2 (Test Soon):** High Impact + Medium Uncertainty, or Medium Impact + High Uncertainty
   - **Priority 3 (Monitor):** Medium Impact + Medium Uncertainty
   - **Priority 4 (Accept):** Low Impact or Low Uncertainty — not worth testing explicitly

5. **Suggest experiments for Priority 1 assumptions.** For each Priority 1 assumption, suggest:
   - What experiment could test this assumption
   - What data to collect
   - What result would validate vs. invalidate the assumption
   - Link to `/pretotype` for detailed experiment design

6. **Identify the kill assumption.** Name the single assumption that, if wrong, makes the entire idea unviable. This feeds directly into `/verdict`.

7. **Write full output** to `./founder-outputs/assumption-map-output.md`. Display a concise summary in chat: top 3 riskiest assumptions, the kill assumption, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/assumption-map-output.md`. Display concise summary in chat.

File format:

```markdown
# Assumption Map Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Kill Assumption
**[The single assumption that kills this if wrong]**
[Why it's fatal, and what evidence exists for/against it]

## Assumption Matrix

| # | Assumption | Category | Impact | Uncertainty | Priority |
|---|---|---|---|---|---|
| 1 | [Assumption] | [Category] | H/M/L | H/M/L | 1-4 |
| 2 | [Assumption] | [Category] | H/M/L | H/M/L | 1-4 |
| ... | ... | ... | ... | ... | ... |

## Priority 1: Test Immediately

### [Assumption 1]
- **Category:** [Category]
- **Impact if wrong:** [What breaks]
- **Current evidence:** [What exists for/against]
- **Suggested experiment:** [How to test]
- **Validation signal:** [What result confirms the assumption]
- **Invalidation signal:** [What result refutes the assumption]

### [Assumption 2]
[Same structure]

## Priority 2: Test Soon
[List with category and brief rationale]

## Priority 3: Monitor
[List with category]

## Priority 4: Accept
[List with category]

## Risk Distribution
**Categories with most risk:** [Which of the 8 categories have the most Priority 1 items]
**Risk concentration:** [Is risk concentrated in one category or distributed?]

## Pipeline Status
**Risk Profile:** [Concentrated in [category] / Distributed]
**Recommended Next:** /pretotype
```
