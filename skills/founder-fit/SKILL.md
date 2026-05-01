---
name: founder-fit
description: This skill should be used when the user says "founder-market fit", "am I the right person", "founder fit", "why me", "why am I building this", "founder qualification", "domain expertise", "skin in the game", or needs to assess whether the founder/team is uniquely positioned to win this market. A major investor concern that the rest of the pipeline does not surface explicitly.
version: 0.1.0
---

# Founder Fit

Assess founder-market fit. A great idea in a market the founder does not understand is a worse bet than a mediocre idea where the founder has 10 years of domain context. This skill interrogates whether the founder/team has the unfair advantage that makes them the right people to build this — or whether they are a generalist chasing a trend.

Posture: skeptical mentor. Push back on resume-padding and surface-level credentials. Demand evidence of *real* domain immersion.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `pressure-test-output.md` — the problem and demand evidence
- `customer-archetype-output.md` — the customer (helps gauge proximity)

If pressure-test output exists, use the JTBD framing as the anchor for "is the founder positioned for this job?"

## Frameworks

- *The Hard Thing About Hard Things* (Horowitz) — founders need to make hard calls under uncertainty. Domain expertise is what gives them the right priors. Without it, they are flying blind.
- *Zero to One* (Thiel) — the contrarian truth. Why does *this* founder believe something about *this* market that others don't? If there is no specific founder-market insight, the idea is generic.
- *Founders at Work* (Livingston) — pattern recognition: most successful founders had either deep personal experience with the problem, deep domain expertise, or both. Pure outsider success is rare.

## Methodology

1. **Probe personal connection to the problem.** Ask:
   - "Have you personally experienced this problem? When? In what role?"
   - "If yes — what did you do about it? If no — how did you encounter it?"
   - **Strong signal:** founder lived the problem (e.g., ran ops at a logistics company before building logistics software)
   - **Weak signal:** founder read about the problem in a TechCrunch article or noticed it from VC pattern matching

2. **Probe domain expertise.** Ask:
   - "How long have you worked in this industry?"
   - "Who are the top 5 players you respect, and why?"
   - "What is one thing about this market that only an insider would know?"
   - **Strong signal:** can name specific industry dynamics, regulatory quirks, vendor relationships
   - **Weak signal:** vague answers, can only name the obvious players

3. **Probe customer proximity.** Ask:
   - "How many of the target customer archetype do you personally know?"
   - "When did you last spend a day with one?"
   - "Can you name 3 customers by name (real or composite from interviews) and what they care about?"
   - **Strong signal:** has a network of target customers, regularly talks to them
   - **Weak signal:** customer is hypothetical, no real conversations on record

4. **Probe skin in the game.** Ask:
   - "What are you giving up to work on this? (Job, salary, equity in another company)"
   - "How much of your own money is in this?"
   - "What is your runway to figure this out before you have to stop?"
   - **Strong signal:** quit a stable role, invested savings, committed multi-year horizon
   - **Weak signal:** working on this part-time, optionality preserved, no real cost of failure

5. **Probe team composition.** If there is a co-founder or team:
   - "What does each person bring that you can't?"
   - "Who covers technical, business, and domain?"
   - "Where is the gap?"
   - **Strong signal:** complementary skills, clear division of expertise, prior collaboration
   - **Weak signal:** redundant skill sets, missing critical functions, untested team dynamics

6. **Probe the contrarian insight.** From the pressure-test contrarian truth question:
   - "What is the specific belief you have about this market that most people would dismiss?"
   - "Where does that belief come from? Personal experience or analysis?"
   - **Strong signal:** belief grounded in lived experience that outsiders cannot easily replicate
   - **Weak signal:** belief is consensus contrarian (everyone in tech says it), or pure analysis without ground truth

7. **Stress test the unfair advantage.** Ask:
   - "If 10 generic, well-funded teams started building this tomorrow, what stops them from beating you?"
   - "What can you do faster, better, or cheaper because of who you are?"
   - **Strong signal:** specific durable advantage (relationships, data, expertise that takes years to build)
   - **Weak signal:** "we'll execute better" (every founder says this)

8. **Surface red flags.** Apply the red flag list below.

9. **Render founder-market fit rating.**
   - **STRONG** — direct problem experience, deep domain knowledge, customer network, real skin in the game, durable unfair advantage
   - **MODERATE** — partial fit. Founder has 2-3 of: experience, expertise, customer access, commitment. Gaps are addressable.
   - **WEAK** — generalist applying to a specialty. No personal connection. No domain context. Customer is hypothetical. Treat with caution; consider co-founder with domain depth.

10. **Write full output** to `./founder-outputs/founder-fit-output.md`. Display a concise summary in chat: fit rating, strongest evidence, biggest gap, recommended action.

## Red Flags

- **"I noticed this problem from observation."** Observation is weaker than experience. Founders who watched the problem rarely understand it as well as those who lived it.
- **"My friend who works in [industry] said this is a problem."** Secondhand pain. The friend should be the founder, or the friend should be a co-founder.
- **"AI/blockchain/SaaS in [industry]."** Tech-first framing. The founder is bringing technology to a market they don't understand. Common path to failure when the market has its own dynamics.
- **No customers in the founder's network.** If the founder cannot get to a customer for an interview without a cold email, they are too far from the problem.
- **Working on this part-time while keeping another job.** Optionality is fine for exploration. But once committed, the lack of skin in the game shows up in slow decisions and weak conviction.
- **"Our team has done this before."** Vague claims about prior experience. Demand specifics: which company, what role, what outcome.
- **Solo technical founder building for a non-technical buyer.** Common B2B failure pattern. Engineer building for ops/sales/finance buyers without a co-founder who lives in that buyer's world.

## Output

Write full output to `./founder-outputs/founder-fit-output.md`. Display concise summary in chat.

File format:

```markdown
# Founder Fit Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Personal Connection to the Problem
**Direct experience:** [Yes / Indirect / No]
**Evidence:** [Specific story or "None provided"]

## Domain Expertise
**Years in this market:** [X]
**Insider knowledge demonstrated:** [Specific examples]
**Industry network:** [Strength: deep / surface / none]

## Customer Proximity
**Target customers in personal network:** [Number]
**Last meaningful conversation with one:** [When]
**Can name specific customers:** [Yes / Hypothetical only]

## Skin in the Game
**Full-time on this:** [Yes / Part-time]
**Personal capital invested:** [Yes / No / Amount]
**What was given up:** [Job, equity, other commitments]
**Runway to figure it out:** [Months]

## Team Composition
**Solo / Co-founders:** [Status]
**Coverage:** [Technical / Business / Domain — note gaps]
**Prior collaboration:** [Yes / No]

## Contrarian Insight
**The contrarian belief:** [What the founder believes that others don't]
**Source:** [Lived experience / Analysis / Pattern matching]
**Durability:** [How hard is this insight for outsiders to replicate?]

## Unfair Advantage
**Specific advantage:** [What this founder has that others don't]
**Durability:** [Months to replicate / Years / Effectively impossible]

## Red Flags Found
[List each red flag detected with explanation, or "None detected"]

## Founder-Market Fit Rating
**[STRONG / MODERATE / WEAK]**

[2-3 sentences with specific evidence]

## Strongest Evidence
[The single piece of evidence that most supports the rating]

## Biggest Gap
[The most important missing piece — and how to address it]

## Recommended Action
- **STRONG:** Proceed. Lean into the unfair advantage in pitch and positioning.
- **MODERATE:** Address the gap before raising. Specifically: [recommendation]
- **WEAK:** Find a co-founder with domain depth, or pivot to a market where you do have fit.

## Pipeline Status
**Founder Fit:** [STRONG / MODERATE / WEAK]
**Recommended Next:** /scope-mode or /market-size
```
