---
name: customer-archetype
description: This skill should be used when the user says "who is my customer", "define my user", "customer profile", "target customer", "buyer persona", "who am I selling to", "who would buy this", or needs to define a specific customer before market sizing, canvas, or competitive analysis. Forces precise customer definition upstream of all modeling skills.
version: 0.1.0
---

# Customer Archetype

Force precise customer definition upstream of all modeling skills. Generic customer descriptions ("SMBs", "enterprises", "millennials") produce generic models. This skill demands specificity: a named person with a title, a boss, a metric, and a workaround.

## Input Dependencies

Read from `./founder-outputs/` if available:
- `pressure-test-output.md` — demand evidence, named customer hints, workaround details

If pressure-test output exists, use its evidence as the starting point. If not, gather the same information from scratch.

## Frameworks

- *The Mom Test* (Fitzpatrick) — specificity discipline. No hypothetical customers. Every attribute must be grounded in observed or stated behavior, not imagined preferences. If the founder says "I think they would..." — push back. What have they *seen*?
- *Competing Against Luck* (Christensen) — define the customer by the job they are hiring the product to do, not by demographics. Two people with identical demographics may have completely different jobs-to-be-done.

## Methodology

1. **Start with a real person.** Ask: "Name a specific person — real or someone you've talked to — who has this problem." If the founder cannot name anyone, that is a signal. Push for at least a realistic composite: "Sarah, ops manager, 50-person logistics company."

2. **Extract role and context.** Demand:
   - Full title and seniority level
   - Company size and industry
   - Who they report to
   - Team size they manage (if any)

3. **Extract goals and pressures.** Ask:
   - "What gets this person promoted?"
   - "What does their boss measure them on?"
   - "What keeps them up at night about their job?"
   - These questions reveal whether the problem is a priority or a nice-to-have.

4. **Map current behavior.** Ask:
   - "How does this person solve the problem today?"
   - "How many hours per week do they spend on the workaround?"
   - "What tools are they duct-taping together?"
   - "How much does the workaround cost (time, money, frustration)?"

5. **Identify information sources.** Ask:
   - "What does this person read? What podcasts, newsletters, communities?"
   - "Where do they go to find new tools?"
   - "Who do they trust for recommendations?"
   - This directly informs go-to-market channels downstream.

6. **Classify decision role.** Determine whether the archetype is:
   - **Buyer** — has budget authority
   - **User** — daily operator, may not have budget authority
   - **Champion** — internal advocate who pushes for adoption
   - **Blocker** — person who can kill the deal (IT, legal, procurement)
   - One person can hold multiple roles. Identify the primary role.

7. **Generate hypothetical quotes.** Write 2-3 specific quotes this person would say about the problem. Not generic ("this is frustrating") — specific ("I spend every Friday afternoon reconciling shipment data across three spreadsheets, and I still miss errors that cost us $2K a month in chargebacks").

8. **Write full output** to `./founder-outputs/customer-archetype-output.md`. Display a concise summary in chat: archetype name, role, key pain, decision role, and note that full output is saved to the file.

## Red Flags

- **Demographic-only description.** "25-35 year old professionals" is not a customer. What job are they hiring this to do?
- **Multiple archetypes with nothing in common.** If the founder names 4 completely different archetypes, the product is unfocused. Push to pick one primary archetype to start.
- **No current workaround.** If the archetype has no workaround, they may not have the problem.
- **"Everyone" is the customer.** A product for everyone is a product for no one.

## Output

Write full output to `./founder-outputs/customer-archetype-output.md`. Display concise summary in chat.

File format:

```markdown
# Customer Archetype Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Primary Archetype
**Name:** [Fictional but specific name]
**Title:** [Role and seniority]
**Company:** [Size, industry, context]
**Reports to:** [Boss's role]

## Goals and Pressures
**Gets promoted by:** [What matters to their career]
**Measured on:** [Boss's metrics]
**Biggest frustration:** [Job-related pain]

## Current Behavior
**Workaround:** [How they solve it today]
**Time cost:** [Hours per week/month]
**Money cost:** [Dollars per month/year]
**Tools used:** [Current stack]

## Information Sources
**Reads:** [Publications, newsletters]
**Communities:** [Slack groups, forums, events]
**Trusted sources:** [Who they ask for recommendations]

## Decision Role
**Primary:** [Buyer / User / Champion / Blocker]
**Budget authority:** [Yes / No / Shared]
**Other stakeholders:** [Who else is involved in the decision]

## Hypothetical Quotes
> "[Specific quote about the problem]"
> "[Specific quote about the workaround]"
> "[Specific quote about what they wish existed]"

## Pipeline Status
**Specificity:** [SHARP / VAGUE]
**Recommended Next:** /market-size or /startup-canvas
```
