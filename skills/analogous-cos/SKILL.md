---
name: analogous-cos
description: This skill should be used when the user says "what's the analog", "who did this in another market", "similar companies", "comparable company", "what can I learn from", "who solved this before", or needs to find 3-5 companies that solved a structurally similar problem in a different market to extract lessons.
version: 0.1.0
---

# Analogous Companies

Find 3-5 companies that solved a structurally similar problem in a different market. Not direct competitors — structural analogs. "Uber for X" is a cliche, but the pattern of marketplace liquidity, trust mechanisms, and pricing dynamics that Uber solved is a real structural pattern that repeats across markets.

## Input Dependencies

Read from `./founder-outputs/` if available:
- `pressure-test-output.md` — core problem and JTBD framing
- `startup-canvas-output.md` — business model structure
- `battle-cards-output.md` — competitive landscape (to avoid listing direct competitors)

No files are strictly required — this skill can run standalone.

## Methodology

1. **Privacy gate.** Before searching, confirm with the user: "I'll search for companies that solved similar structural problems in other markets. This will use terms like '[problem pattern] company', '[business model] marketplace', etc. Proceed?" Wait for confirmation.

2. **Identify the structural pattern.** Extract the core structural problem from prior outputs or from the user's description. Examples of structural patterns:
   - Matching supply and demand in a fragmented market (marketplace)
   - Aggregating fragmented data into a single source of truth (aggregator)
   - Replacing manual processes with automated workflows (automation)
   - Bringing transparency to opaque pricing (price transparency)
   - Unbundling a monolithic incumbent (unbundling)
   - Creating a platform for third-party providers (platform)
   - Applying a new technology to an old industry (tech transfer)

3. **Search for analogs.** For each structural pattern, search for companies in *different* industries or markets that solved the same structural problem. Look for:
   - Companies that are 3-10 years ahead on the same curve
   - Companies that tried and failed (failure lessons are more valuable)
   - Companies that started with the same wedge and expanded
   - Companies in adjacent markets that faced the same GTM challenges

4. **For each analog (3-5 companies), extract:**
   - Company name and what they do
   - The structural similarity (what problem pattern they share with this idea)
   - What they got right (specific tactics, not generic "they executed well")
   - What they got wrong or what failed (specific mistakes)
   - The timing lesson (when did they start? Was it too early, too late, or just right?)
   - Market context differences (what is different about this idea's market that changes the playbook)
   - Key metric or milestone (how they validated demand — the data point, not the story)

5. **Extract cross-cutting lessons.** Across all analogs, identify:
   - Common success patterns (things that worked for most/all analogs)
   - Common failure patterns (things that killed or nearly killed most analogs)
   - The "timing lesson" — when did the window open and why?
   - The "sequencing lesson" — what did successful analogs do first?

6. **Write full output** to `./founder-outputs/analogous-cos-output.md`. Display a concise summary in chat: the 3-5 analogs with one-line descriptions, the key cross-cutting lesson, and note that full output is saved to the file.

## Red Flags

- **Analogs are all direct competitors.** This skill finds structural analogs in *other* markets, not competitors in the same market. Use `/battle-cards` for direct competitors.
- **Cherry-picked success stories only.** Include at least one analog that failed. Failure patterns are often more instructive than success patterns.
- **"We're like [famous company] but for [niche]."** The pitch format is fine, but dig deeper — what specifically about that company's approach is transferable to this market?

## Output

Write full output to `./founder-outputs/analogous-cos-output.md`. Display concise summary in chat.

File format:

```markdown
# Analogous Companies Output
**Generated:** [date]
**Idea:** [one-sentence restatement]
**Structural Pattern:** [The core structural problem being solved]

## Analog 1: [Company Name]
**What they do:** [One sentence]
**Structural similarity:** [What pattern they share]
**What they got right:** [Specific tactics]
**What they got wrong:** [Specific mistakes]
**Timing lesson:** [When they started, whether timing was right]
**Market difference:** [What's different about your market]
**Key metric:** [How they validated demand]

## Analog 2: [Company Name]
[Same structure]

## Analog 3: [Company Name]
[Same structure]

## Analog 4: [Company Name] (if applicable)
[Same structure]

## Analog 5: [Company Name] (if applicable)
[Same structure]

## Cross-Cutting Lessons
**Common success pattern:** [What worked across analogs]
**Common failure pattern:** [What killed or nearly killed analogs]
**Timing lesson:** [When did the window open]
**Sequencing lesson:** [What did successful analogs do first]

## Implications for This Idea
[2-3 specific, actionable takeaways for this idea based on the analog analysis]

## Pipeline Status
**Analog Strength:** [STRONG / MODERATE / WEAK] (how informative were the analogs?)
**Recommended Next:** /verdict (if not yet run) or continue pipeline
```
