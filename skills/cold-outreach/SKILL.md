---
name: cold-outreach
description: This skill should be used when the user says "cold email", "outbound", "cold outreach", "email sequence", "reach out to prospects", "sales emails", "how do I contact customers", or needs personalized cold email sequences derived from the customer archetype. Not generic templates — sequences built from the archetype's title, pain, promotion criteria, and workaround cost.
version: 0.1.0
---

# Cold Outreach

Generate personalized cold email sequences for the specific customer archetype. The differentiation from generic email templates: the archetype file provides the title, the pain, what gets them promoted, and their current workaround — enabling emails that feel researched, not blasted.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `customer-archetype-output.md` — title, pain, promotion criteria, communities, workaround cost (required)
- `startup-canvas-output.md` — UVP, pricing
- `oneliner-output.md` — the one-liner (if available)
- `battle-cards-output.md` — competitive alternatives the prospect may use

If `customer-archetype-output.md` is missing, tell the user to run `/customer-archetype` first. Generic cold emails to undefined customers have near-zero conversion.

## Frameworks

- *Predictable Revenue* (Ross & Tyler) — cold outbound methodology. Short, specific, asks for a conversation not a sale. The subject line earns the open; the first sentence earns the read; the CTA earns the reply.
- *$100M Leads* (Hormozi) — lead generation mechanics. Cold outreach is one of four core channels. It works when the message is so specific the recipient thinks it was written just for them.

## Methodology

1. **Build the prospect profile from the archetype.** Extract:
   - Their exact title and seniority
   - What they are measured on (promotion criteria)
   - Their current workaround and its cost
   - What they read and where they hang out (for reference points)
   - Their decision role (buyer, user, champion, blocker)

2. **Generate a 3-email sequence.** Each email has a distinct purpose:

   **Email 1: The Pain Email (Day 1)**
   - Subject line: reference their specific pain or metric (not the product)
   - Opening: demonstrate understanding of their world (1 sentence, no "I" or "we")
   - Pain point: name the workaround cost in their terms (hours, dollars, frustration)
   - Bridge: one sentence on what changes
   - CTA: ask for 15 minutes, not a demo. Low commitment.
   - Length: under 100 words total.

   **Email 2: The Evidence Email (Day 3-4)**
   - Subject line: "Re:" the first email (keeps the thread)
   - Opening: reference a specific data point or story (social proof, case study, metric)
   - Value: what a similar person achieved (outcomes, not features)
   - CTA: repeat the ask with a specific time suggestion
   - Length: under 80 words.

   **Email 3: The Breakup Email (Day 7-8)**
   - Subject line: short, casual ("quick question" or "closing the loop")
   - Opening: acknowledge they are busy (1 sentence)
   - Value restate: one sentence of the core benefit
   - CTA: binary choice — "Should I follow up next quarter, or is now better?"
   - Length: under 60 words.

3. **Apply personalization layers.** For each email:
   - **Company personalization:** reference something specific about their company (recent news, job postings, product launches)
   - **Role personalization:** reference their specific responsibilities
   - **Timing personalization:** tie to a relevant trigger (quarter end, budget cycle, industry event)
   - Mark each personalization point with `[PERSONALIZE: research their company's X]` for the user to fill in.

4. **Generate subject line variants.** For Email 1, provide 3 subject line options:
   - Pain-focused: references their specific problem
   - Metric-focused: references a number they care about
   - Curiosity-focused: creates an open loop

5. **Specify targeting criteria.** Based on the archetype, define:
   - LinkedIn Sales Navigator search filters
   - Company size, industry, and geography
   - Title keywords to target
   - Title keywords to exclude
   - Estimated pool size (from market-size output if available)

6. **Write full output** to `./founder-outputs/cold-outreach-output.md`. Display the 3-email sequence in chat with subject lines, and note that full output is saved to the file.

## Red Flags

- **Email talks about the product before the pain.** The prospect does not care about the product. They care about their problem.
- **Email is over 150 words.** Long cold emails do not get read. Ruthlessly cut.
- **CTA asks for too much.** "Schedule a 60-minute demo" from a stranger is a hard no. "15 minutes to see if this is relevant" is a soft yes.
- **No personalization hooks.** If removing the company name makes the email work for anyone, it is not personalized enough.
- **Sending to the wrong role.** If the archetype is a user but not the buyer, the sequence should ask for an introduction to the buyer, not pitch the product.

## Output

Write full output to `./founder-outputs/cold-outreach-output.md`. Display concise summary in chat.

File format:

```markdown
# Cold Outreach Output
**Generated:** [date]
**Idea:** [one-sentence restatement]
**Target Archetype:** [Name, title, company type from archetype]

## Targeting Criteria
**Title keywords:** [Include]
**Exclude:** [Titles to skip]
**Company size:** [Range]
**Industry:** [Verticals]
**Geography:** [Region]
**Estimated pool:** [Number of prospects]
**LinkedIn Sales Navigator filters:** [Specific filters]

## Email 1: The Pain Email (Day 1)

### Subject Line Options
1. [Pain-focused]
2. [Metric-focused]
3. [Curiosity-focused]

### Body
```
[Full email, under 100 words, with [PERSONALIZE: ...] markers]
```

## Email 2: The Evidence Email (Day 3-4)

### Subject Line
Re: [Email 1 subject]

### Body
```
[Full email, under 80 words]
```

## Email 3: The Breakup Email (Day 7-8)

### Subject Line
[Short, casual]

### Body
```
[Full email, under 60 words]
```

## Personalization Guide
| Email | Personalization Point | How to Research |
|---|---|---|
| 1 | [Point] | [Where to find this info] |
| 2 | [Point] | [Where to find this info] |

## Expected Metrics
- **Open rate target:** 40-60% (good subject lines + targeting)
- **Reply rate target:** 5-15% (good personalization + relevant pain)
- **Meeting rate target:** 2-5% of total sends

## Pipeline Status
**Outreach Ready:** [YES / NEEDS PERSONALIZATION]
**Recommended Next:** /content-strategy
```
