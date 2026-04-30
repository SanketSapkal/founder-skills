---
name: oneliner
description: This skill should be used when the user says "one liner", "tagline", "how do I describe this in one sentence", "value prop", "headline", "positioning statement", "what do I say on the landing page", "how do I explain this", or needs obsessive refinement of the one-sentence value proposition with explicit conversion criteria. Most founders have a bad one-liner and do not know it.
version: 0.1.0
---

# Oneliner

Obsessive focus on the one-sentence value proposition that actually converts. Not a brainstorm of 20 options — a disciplined process that produces one sentence, tested against explicit criteria, with the reasoning visible.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — UVP, problems, solution (required)
- `customer-archetype-output.md` — customer language, pain description
- `pressure-test-output.md` — JTBD framing, demand evidence
- `battle-cards-output.md` — positioning statement, competitive differentiation

If `startup-canvas-output.md` is missing, tell the user to run `/startup-canvas` first.

## Frameworks

- *Obviously Awesome* (Dunford) — positioning defines the frame. The one-liner must place the product in a market category the customer recognizes, against alternatives they know about.
- *$100M Offers* (Hormozi) — the value equation: Dream Outcome × Perceived Likelihood of Achievement ÷ (Time Delay × Effort & Sacrifice). A great one-liner maximizes the numerator and minimizes the denominator.

## Methodology

1. **Extract the raw ingredients.** From prior outputs, identify:
   - The customer (from archetype — their exact title and context)
   - The pain (from pressure-test — in the customer's language, not founder's jargon)
   - The outcome (from canvas — what changes for the customer)
   - The mechanism (from canvas — how the product delivers the outcome)
   - The differentiator (from battle-cards — what makes this unlike alternatives)

2. **Generate 5 candidate one-liners.** Each using a different frame:
   - **Outcome frame:** "[Product] [outcome] for [customer]"
   - **Pain frame:** "Stop [pain]. [Product] [mechanism]."
   - **JTBD frame:** "When [situation], [product] helps [customer] [outcome]"
   - **Versus frame:** "Unlike [alternative], [product] [differentiator]"
   - **Metric frame:** "[Product] [quantified improvement] for [customer]"

3. **Score each candidate against 7 criteria.** Rate each 1-5:

   | Criterion | Test |
   |---|---|
   | **Names the customer** | Would the target archetype self-identify? Not "businesses" — "ops managers at logistics companies." |
   | **Names the outcome** | Does it state what changes, not what the product does? Not "AI-powered analysis" — "finds the clause that costs you money." |
   | **Falsifiable claim** | Can this be proven wrong? "Better experience" cannot. "Cuts reconciliation time from 8 hours to 20 minutes" can. |
   | **Under 15 words** | Brevity forces clarity. If it needs more words, the concept is muddled. |
   | **No jargon** | Would a stranger in the target industry understand it without explanation? |
   | **Creates urgency** | Does it imply a cost of inaction? Not just "this is nice" but "you're losing [thing] without this." |
   | **Memorable** | Could someone repeat it to a colleague from memory after hearing it once? |

4. **Select the winner.** The candidate with the highest total score. If multiple tie, prefer the one that is most falsifiable — specificity converts better than cleverness.

5. **Stress-test the winner.** Apply three tests:
   - **The stranger test:** Read it to someone outside the industry. Do they understand what it does?
   - **The so-what test:** After reading it, does the customer's reaction include "I need that" or "tell me more"? Or is it "that's nice"?
   - **The competitor test:** Could a competitor use the same sentence? If yes, the differentiator is missing.

6. **Produce variants for different contexts:**
   - **Landing page headline** (5-8 words, maximum impact)
   - **Email subject line** (creates curiosity, under 50 characters)
   - **LinkedIn/bio description** (one sentence with context)
   - **Investor one-liner** (includes market size or traction signal)

7. **Write full output** to `./founder-outputs/oneliner-output.md`. Display the winning one-liner and the scorecard in chat, and note that full output is saved to the file.

## Red Flags

- **Describes a feature, not an outcome.** "AI-powered document analyzer" is a feature. "Finds the clause that costs you money before you sign" is an outcome.
- **Uses internal jargon.** If the customer would not use this word, neither should the one-liner.
- **Could describe any competitor.** If swapping in a competitor's name still makes the sentence true, the differentiator is missing.
- **Longer than 15 words.** Complexity is not depth. Cut until it hurts.

## Output

Write full output to `./founder-outputs/oneliner-output.md`. Display concise summary in chat.

File format:

```markdown
# Oneliner Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## The Oneliner
> [The winning one-liner, under 15 words]

## Scorecard
| Candidate | Customer | Outcome | Falsifiable | Brevity | No Jargon | Urgency | Memorable | Total |
|---|---|---|---|---|---|---|---|---|
| [Candidate 1] | [1-5] | [1-5] | [1-5] | [1-5] | [1-5] | [1-5] | [1-5] | [/35] |
| [Candidate 2] | ... | ... | ... | ... | ... | ... | ... | [/35] |
| ... | ... | ... | ... | ... | ... | ... | ... | ... |

## Why This One Wins
[2-3 sentences explaining the selection]

## Stress Test Results
- **Stranger test:** [Pass/Fail — explanation]
- **So-what test:** [Pass/Fail — explanation]
- **Competitor test:** [Pass/Fail — explanation]

## Context Variants
- **Landing page:** [5-8 word headline]
- **Email subject:** [Under 50 characters]
- **LinkedIn/bio:** [One sentence with context]
- **Investor version:** [Includes market/traction signal]

## Pipeline Status
**Oneliner Quality:** [STRONG / NEEDS WORK]
**Recommended Next:** /cold-outreach, /content-strategy
```
