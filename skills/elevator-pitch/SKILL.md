---
name: elevator-pitch
description: This skill should be used when the user says "elevator pitch", "30 second pitch", "how do I describe this", "explain my startup", "pitch in one sentence", "two minute pitch", "quick pitch", or needs to generate 30-second, 2-minute, and 10-minute pitch versions from existing founder-outputs. Forces clarity on the one sentence that matters most.
version: 0.1.0
---

# Elevator Pitch

Generate the 30-second, 2-minute, and 10-minute versions of the pitch from the same source material. The core discipline: if the founder cannot say what this is in one sentence, they do not understand it well enough.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — UVP, problems, solution (required)
- `customer-archetype-output.md` — who the customer is
- `pressure-test-output.md` — demand evidence and JTBD
- `market-size-output.md` — market opportunity
- `battle-cards-output.md` — positioning statement
- `pitch-deck-output.md` — narrative arc (if available)

If `startup-canvas-output.md` is missing, tell the user to run `/startup-canvas` first — the pitch needs a UVP to anchor on.

## Methodology

1. **Extract the core elements.** From all available outputs, identify:
   - The customer (from archetype — specific, not generic)
   - The problem (from pressure-test — the pain, not the category)
   - The solution (from canvas — the mechanism, not the feature list)
   - The differentiation (from battle-cards — what is unlike anything else)
   - The evidence (from pressure-test — why this is real, not hypothetical)

2. **Generate the 30-second version (3-4 sentences).**
   Structure: Problem → Solution → For whom → Why different.
   - Sentence 1: The problem (make the listener feel it)
   - Sentence 2: What this product does about it (one sentence, no feature list)
   - Sentence 3: Who it is for (specific customer from archetype)
   - Sentence 4: Why this wins (one differentiator from battle-cards)

   Test: read it aloud. If it takes more than 30 seconds, cut words.

3. **Generate the 2-minute version (adds evidence and model).**
   Expand the 30-second version with:
   - Demand evidence (one data point from pressure-test)
   - Market size (one number — SOM, not TAM)
   - Business model (how it makes money, one sentence)
   - Traction or validation (if any exists)
   - The ask or next step

4. **Generate the 10-minute version (full narrative).**
   Follow the Sequoia arc from the pitch deck output if available:
   Problem → Solution → Why Now → Market → Product → Model → Competition → Traction → Team → Ask.
   Each section gets 1 minute. The 10-minute pitch is not the 2-minute pitch repeated 5 times — it adds depth at each stage.

5. **Extract the one sentence.** From the 30-second pitch, extract the single sentence that captures everything. Test it against:
   - Does it name the customer? (Not "people" or "users")
   - Does it name the outcome? (Not the feature)
   - Does it make a falsifiable claim? (Can it be proven wrong?)
   - Would a stranger understand it without context?
   - Is it under 20 words?

6. **Generate 3 alternative framings.** Present the one-sentence pitch in three different frames:
   - **Job-to-be-done frame:** "Helps [customer] [achieve outcome] when [situation]"
   - **Competitive frame:** "Unlike [alternative], [product] [differentiator]"
   - **Outcome frame:** "[Product] turns [current pain] into [desired state] for [customer]"

   Ask the user which framing resonates most.

7. **Write full output** to `./founder-outputs/elevator-pitch-output.md`. Display all three pitch versions in chat and note that full output is saved to the file.

## Red Flags

- **Cannot get to one sentence.** If the product requires a paragraph to explain, the concept may be too complex or unfocused.
- **The one sentence describes a feature, not an outcome.** "AI-powered document analyzer" is a feature. "Finds the clause that costs you money before you sign" is an outcome.
- **Different pitch lengths tell different stories.** The 30-second, 2-minute, and 10-minute versions must be the same story at different zoom levels, not three different pitches.

## Output

Write full output to `./founder-outputs/elevator-pitch-output.md`. Display concise summary in chat.

File format:

```markdown
# Elevator Pitch Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## The One Sentence
> [Under 20 words, names customer and outcome]

## Alternative Framings
- **JTBD:** [framing]
- **Competitive:** [framing]
- **Outcome:** [framing]

## 30-Second Pitch
[3-4 sentences. Problem → Solution → Customer → Differentiator]

## 2-Minute Pitch
[Expands 30-second with evidence, market, model, ask]

## 10-Minute Pitch Outline
1. **Problem** (1 min) — [Key points]
2. **Solution** (1 min) — [Key points]
3. **Why Now** (1 min) — [Key points]
4. **Market** (1 min) — [Key points]
5. **Product** (1 min) — [Key points]
6. **Business Model** (1 min) — [Key points]
7. **Competition** (1 min) — [Key points]
8. **Traction** (1 min) — [Key points]
9. **Team** (1 min) — [Key points]
10. **Ask** (1 min) — [Key points]

## Pipeline Status
**Pitch Ready:** YES
**Recommended Next:** /objection-map
```
