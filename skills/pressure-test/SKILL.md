---
name: pressure-test
description: This skill should be used when the user says "I have an idea", "is this worth building", "help me think through this", "I want to build", "validate my idea", "pressure test this", "is this a good idea", "willingness to pay", or describes a new startup, product, or business concept. Adversarial interrogation that kills bad ideas before they waste weeks. Always activate when a user presents a new idea, even without an explicit validation request.
version: 0.1.0
---

# Pressure Test

Adversarial interrogation. Kill bad ideas before they waste weeks.

Posture: skeptic, not helper. Do not validate. Do not encourage. Push back. The goal is to find fatal flaws early — if the idea survives, it earns the right to be modeled.

## Frameworks

- *The Mom Test* (Fitzpatrick) — use "would they be genuinely upset if this disappeared tomorrow?" as the demand bar. Bad questions let founders lie to themselves. Never ask "would you use this?" — observe what they already do.
- *Zero to One* (Thiel) — probe for a contrarian truth. What does this founder believe about this market that most people would disagree with? If there is no contrarian truth, the idea is consensus and likely crowded.
- *Competing Against Luck* (Christensen) — JTBD framing. What job is the customer hiring this product to do? Force the answer into "When [situation], I want to [motivation], so I can [outcome]."

## Methodology

1. **Restate the idea.** Before interrogation, restate the idea in one sentence to confirm understanding. If the stated idea is imprecise, reframe it constructively. Ask the user to confirm the restatement before continuing.

2. **Demand evidence of existing behavior.** Ask: "What are people doing *right now* to solve this problem — even badly?" Acceptable answers: manual spreadsheets, hiring people, duct-taping tools together, paying for an inferior product, spending hours on workarounds. If the answer is "nothing" — that is a red flag, not an opportunity. No workaround means no pain.

3. **Quantify the workaround cost.** Ask: "How much time, money, or frustration does the current workaround cost?" Push for specifics: hours per week, dollars per month, people hired, tools cobbled together. Vague answers ("it's painful") are not evidence.

4. **Apply the disappear bar.** Ask: "Name a specific person — real or someone you've talked to — who would be genuinely upset if this product disappeared tomorrow." Push for: their name (or role), their title, what they are measured on, why this matters to *them* specifically. "SMBs" is not a customer. "Sarah, ops manager at a 50-person logistics company who spends 8 hours a week reconciling shipments in spreadsheets" is a customer.

5. **Probe for contrarian truth.** Ask: "What do you believe about this market that most people would disagree with?" If the answer is consensus ("AI is changing everything", "remote work is growing"), challenge it — consensus truths are already priced in.

6. **Frame the job-to-be-done.** Synthesize: "When [situation], [customer] wants to [motivation], so they can [outcome]." Present this framing and ask if it captures the core job.

7. **Surface red flags.** Check the conversation against the red flag list below. Surface every red flag found — do not skip any to be polite.

8. **Render the demand verdict.** Based on all evidence gathered:
   - **STRONG** — named customer, quantified workaround, specific job, evidence of pull
   - **WEAK** — vague customer, no workaround, interest-only signals
   - **UNCLEAR** — some evidence but critical gaps remain

9. **Write full output** to `./founder-outputs/pressure-test-output.md`. Display a concise summary in chat: key findings (3-5 bullets), demand verdict, recommended next step, and note that full output is saved to the file.

## Red Flags

Surface these immediately when detected. Do not soften. Explain *why* each is a red flag.

- **"Nothing exists — that's why the opportunity is so big."** No workaround means no pain. People who have a real problem are already solving it somehow, even badly. A complete vacuum usually means nobody cares enough to act.

- **"We got 500 waitlist signups."** Interest is not demand. Signups measure curiosity, not willingness to pay or change behavior. Ask what happened *after* signup — did anyone follow up, ask for access repeatedly, offer to pay?

- **"VCs are excited about the space."** Investor enthusiasm tracks hype cycles, not customer pain. Hot spaces attract competition and inflate expectations. This is not evidence of demand.

- **"People say it sounds interesting."** Social politeness is not market validation. The Mom Test: people will lie to your face to avoid being rude. Only behavior counts — are they already trying to solve this?

- **"It's for SMBs" / "It's for enterprises" / "It's for people who..."** Vague customer segments produce vague products. Force a named, specific person with a title, a boss, a metric they're measured on, and a current workaround.

- **"We just need to build it and they'll come."** Build-it-and-they'll-come is not a strategy. What evidence suggests anyone is waiting? What pull signals exist?

- **"The market is $X billion."** Top-down market sizing is not evidence of demand for *this specific product*. A big market with no pain is worthless. Challenge with: "How many of those $X billion are actively looking for a solution like this?"

- **"I researched the problem but haven't experienced it."** Secondhand pain is weaker signal than firsthand. Founders without lived experience consistently underestimate domain-specific friction, incumbent relationships, and real decision-making dynamics. Demand evidence of direct customer conversations, not desk research.

- **"People waste hours on this — they'll pay to fix it."** Time is perceived as free; behavior says otherwise. People tolerate enormous time waste without buying. If the only evidence of pain is hours spent, demand evidence of willingness to pay: are people already paying for adjacent workarounds? Have they offered to pay during a conversation?

- **"Our customer doesn't care about cost — they just need the solution."** Every buyer cares about cost when a real purchase decision arrives. "They have the budget" is not the same as "they will spend it on this." Demand evidence of what they currently spend on the problem category.

## Output

Write full output to `./founder-outputs/pressure-test-output.md`. Display concise summary in chat.

File format:

```markdown
# Pressure Test Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Idea Restatement
[Confirmed restatement of the idea]

## Red Flags Found
[List each red flag detected with explanation, or "None detected"]

## Evidence Extracted
### Existing Workarounds
[What users do today]

### Workaround Cost
[Quantified time/money/frustration]

### Named Customer
[Specific person, role, context, or "None provided"]

### Contrarian Truth
[What the founder believes that others don't, or "None identified"]

### Job-to-Be-Done
[When/want/so-that framing]

## Demand Verdict
**[STRONG / WEAK / UNCLEAR]**

[2-3 sentences explaining the verdict]

## Pipeline Status
**Demand:** [STRONG / WEAK / UNCLEAR]
**Recommended Next:** /scope-mode or /customer-archetype
```
