---
name: 10x-why-now
description: This skill should be used when the user says "why now", "is the timing right", "what's changed", "why didn't this exist before", "why is this possible now", "what's the tailwind", or needs to formalize whether there is a structural timing advantage for this idea — not just "AI is taking off."
version: 0.1.0
---

# 10x Why Now

Thiel's "why now" question formalized. What changed in the last 2-3 years — regulatory, technical, behavioral, market — that makes this viable today but not 5 years ago? If the answer is weak, the idea may be too early, too late, or not differentiated by timing.

## Input Dependencies

Read from `./founder-outputs/` if available:
- `pressure-test-output.md` — demand evidence and contrarian truth
- `battle-cards-output.md` — competitive landscape (why haven't competitors solved this?)
- `market-size-output.md` — market dynamics

No files are strictly required — this skill can run standalone.

## Frameworks

- *Zero to One* (Thiel) — the "why now" question. The best startups exploit a specific, recent change that makes something newly possible. If the founder cannot name the change, the idea may address a problem that has existed forever and will continue to not be solved — or that someone already solved.
- *Crossing the Chasm* (Moore) — timing in the adoption curve. Is the technology/behavior mature enough for the early majority, or is this still an innovator toy? Early is not the same as right.

## Methodology

1. **Ask the "why now" question directly.** "What changed in the last 2-3 years that makes this idea viable today when it was not viable before?" Demand specifics, not vague trends.

2. **Probe across four dimensions:**

   **Technical shifts:**
   - New technology that is now mature enough (not just announced — actually usable)
   - Cost curves that crossed a threshold (compute, storage, bandwidth, devices)
   - Infrastructure that now exists (APIs, platforms, standards)
   - Open-source tools or models that remove build cost

   **Regulatory shifts:**
   - New regulations that create requirements (compliance, reporting, access)
   - Deregulation that opens markets previously blocked
   - Policy changes that create urgency (deadlines, mandates, penalties)

   **Behavioral shifts:**
   - Consumer or enterprise behavior that changed recently
   - Pandemic-accelerated behaviors that stuck
   - Generational shifts in expectations or tool adoption
   - New workflows or processes that emerged

   **Market shifts:**
   - Incumbent weaknesses newly exposed (platform risk, pricing, trust)
   - Category creation by adjacent companies (market education done for you)
   - New funding/budget availability in the target segment
   - Industry consolidation or fragmentation creating gaps

3. **Challenge weak answers.** Apply these red flag tests:
   - **"AI is taking off."** Necessary but not sufficient. Every company can say this. What specific AI capability became viable in the last 12 months that enables *this specific product*?
   - **"Remote work is growing."** This has been true for years. What changed *recently* that your product specifically exploits?
   - **"The market is big and growing."** Growth is not timing. Name the inflection point.
   - **No change identified.** If nothing specific changed, this idea could have been built 5 years ago. Why was it not? That question often reveals the real answer.

4. **Assess timing strength.** Rate the timing advantage:
   - **STRONG** — a specific, recent, irreversible change that directly enables this product. Clear evidence.
   - **MODERATE** — a real trend, but not unique to this product. Others will see it too.
   - **WEAK** — generic trends, no specific inflection point, or the change happened too long ago to be a timing advantage.
   - **TOO EARLY** — the change is real but has not yet reached the tipping point for the target customer.

5. **Write full output** to `./founder-outputs/why-now-output.md`. Display a concise summary in chat: the timing thesis, strength rating, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/why-now-output.md`. Display concise summary in chat.

File format:

```markdown
# Why Now Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Timing Thesis
[One paragraph: what changed and why it matters for this specific product]

## Timing Factors

### Technical
- [Specific change] — [How it enables this product] — [When it happened]

### Regulatory
- [Specific change] — [Impact] — [When]

### Behavioral
- [Specific change] — [Impact] — [When]

### Market
- [Specific change] — [Impact] — [When]

## Red Flags Checked
- [Any generic answers that were challenged and what replaced them]

## Timing Strength
**[STRONG / MODERATE / WEAK / TOO EARLY]**
[2-3 sentences explaining the rating]

## What Would Strengthen the Timing Case
[Specific evidence or events that would make the timing stronger]

## Pipeline Status
**Timing:** [STRONG / MODERATE / WEAK / TOO EARLY]
**Recommended Next:** /verdict (if not yet run) or continue pipeline
```
