---
name: objection-map
description: This skill should be used when the user says "investor questions", "tough questions", "objection handling", "what will investors ask", "prepare for due diligence", "hardest questions", "Q&A prep", or needs to pre-generate the 8-10 hardest questions an investor will ask and draft honest answers. The questions are predictable — most founders just are not prepared.
version: 0.1.0
---

# Objection Map

Pre-generate the 8-10 hardest questions an investor will ask and draft honest answers. These questions are highly predictable — they map to the standard dimensions investors evaluate. The goal is not to have perfect answers but to have *thought about them* before the meeting.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `verdict-output.md` — dimension scores and weak spots (required)
- `pressure-test-output.md` — demand evidence and red flags
- `market-size-output.md` — TAM/SAM/SOM and confidence level
- `startup-canvas-output.md` — business model and unit economics
- `battle-cards-output.md` — competitive landscape
- `assumption-map-output.md` — riskiest assumptions
- `investor-lens-output.md` — investor-specific concerns (if available)

If `verdict-output.md` is missing, tell the user to run `/verdict` first.

## Frameworks

- *Secrets of Sand Hill Road* (Kupor) — the standard VC evaluation framework. Investors ask predictable questions across 6 dimensions: team, market, product, go-to-market, financial model, and risks. Knowing the framework makes the questions predictable.
- *The Fundraising Rules* (MacLeod) — tactical fundraising discipline. The investor is not trying to be mean — they are trying to find the reason to say no. Help the founder find that reason first.

## Methodology

1. **Identify weak spots from prior outputs.** Read the verdict dimension scores. Every score below the top rating is a question the investor will ask. Read the investor lens output if available — each lens identifies a #1 concern.

2. **Generate the standard question set.** Every investor meeting includes some version of these. Generate the specific version for this idea:

   **Demand questions:**
   - "How do you know people actually want this?" (Weak pressure-test evidence triggers this)
   - "What's your evidence of willingness to pay?"
   - "Who are your first 10 customers by name?"

   **Market questions:**
   - "How big is this really?" (Top-down-only market sizing triggers this)
   - "Why hasn't someone already built this?"
   - "What happens when [incumbent] adds this feature?"

   **Model questions:**
   - "What are your unit economics?"
   - "How does this scale without linearly adding costs?"
   - "What's your path to profitability?"

   **Team questions:**
   - "Why are you the right person to build this?"
   - "What's your unfair advantage in this market?"

   **Risk questions:**
   - "What's the one thing that kills this?"
   - "What assumptions are you most uncertain about?"

   **Timing questions:**
   - "Why now? Why not two years ago?"
   - "Are you too early or too late?"

3. **Select the 8-10 hardest for this specific idea.** Not all questions apply equally. Choose the ones where the evidence is weakest or the answer is hardest. Rank by difficulty.

4. **Draft honest answers.** For each question:
   - **The honest answer** — what the evidence actually shows. Do not spin. If the evidence is weak, say so.
   - **The bridge** — after acknowledging the weakness, bridge to a strength. "We don't have paying customers yet, but we've validated demand through [specific pretotype result]."
   - **The proof point** — the single strongest data point that supports the bridge.
   - **What would make this answer stronger** — specific evidence or milestone that would improve the answer.

5. **Identify the "kill question."** The one question where a bad answer ends the meeting. This usually maps to the kill assumption from the assumption map. Prepare this answer most carefully.

6. **Write full output** to `./founder-outputs/objection-map-output.md`. Display a concise summary in chat: the top 5 toughest questions with one-line answers, the kill question flagged, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/objection-map-output.md`. Display concise summary in chat.

File format:

```markdown
# Objection Map Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Kill Question
**"[The question that ends the meeting if answered badly]"**
- **Honest answer:** [What the evidence shows]
- **Bridge:** [Redirect to strength]
- **Proof point:** [Strongest data point]
- **Would be stronger with:** [What evidence to gather]

## Question 1: "[Question]"
**Category:** [Demand / Market / Model / Team / Risk / Timing]
**Difficulty:** [1-10]
- **Honest answer:** [...]
- **Bridge:** [...]
- **Proof point:** [...]
- **Would be stronger with:** [...]

## Question 2: "[Question]"
[Same structure]

[...through Question 8-10]

## Preparation Priorities
1. [Question to prepare most for — and what evidence to gather before the meeting]
2. [...]
3. [...]

## Pipeline Status
**Prep Level:** [READY / GAPS — with specific gaps listed]
**Recommended Next:** Practice the kill question answer out loud
```
