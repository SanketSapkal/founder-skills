---
name: problem-statement
description: This skill should be used when the user says "problem statement", "define the problem", "what's the problem", "articulate the problem", "what am I solving", "frame this problem", or has a vague problem in mind that needs structured articulation. Forces precise articulation of the problem before any solution work.
version: 0.1.0
---

# Problem Statement

Force precise articulation of the problem before any solution work. Vague problem statements produce vague products. This skill demands structure: who, when, what, what changed, what it costs.

Posture: editor, not generator. Push back on vague language. Demand specifics.

## Input Dependencies

Read from `./founder-outputs/` if available:
- `problem-discovery-output.md` — top candidate problems and discovery findings (use as starting material if it exists)

If no problem-discovery output exists, gather the problem from scratch.

## Frameworks

- *The Mom Test* (Fitzpatrick) — every claim about the problem must be grounded in observed behavior, not founder hypothesis. Push back when the founder says "I think users want..."
- *Competing Against Luck* (Christensen) — JTBD framing. Force the problem into: "When [situation], [who] is trying to [motivation], so they can [outcome] — but [obstacle]."

## Methodology

1. **Capture the rough statement.** Ask: "In one sentence, what's the problem you're trying to solve?" Take the response as raw material.

2. **Force the JTBD structure.** Rewrite as: "When [specific situation], [specific who] is trying to [specific motivation], so they can [specific outcome] — but [specific obstacle that exists today]." Push back on every vague word.

3. **Test specificity.** For each element, challenge:
   - **Who** — "SMBs" is not a who. "Operations managers at logistics companies with 50-500 employees" is.
   - **When** — "always" is not a when. "Every Friday during weekly reconciliation" is.
   - **Motivation** — "they want efficiency" is not a motivation. "They want to close the books by EOD so they can leave on time" is.
   - **Outcome** — "save time" is not an outcome. "Avoid the 2-hour weekend reconciliation work" is.
   - **Obstacle** — "it's hard" is not an obstacle. "Data lives in 3 systems that don't talk; pulling it manually takes 4 hours" is.

4. **Test scope.** Ask: "Is this one problem or three problems hidden under one label?" Common compound problems:
   - "Onboarding is broken" = (a) discoverability + (b) configuration + (c) activation
   - "Customer support is slow" = (a) ticket routing + (b) knowledge access + (c) response writing
   - If compound, force a choice: which sub-problem matters most?

5. **Test boundary.** Ask: "What's NOT this problem? What might look like this problem but is actually something else?" If the founder cannot draw a clear boundary, the statement is too broad.

6. **Surface what changed.** Why is this problem solvable now when it wasn't before? Tech change, regulatory change, behavior change, cost change — name the unlock. (Not required, but feeds `/10x-why-now` downstream.)

7. **Quantify the cost of the current state.** What does the problem cost today (time, money, errors, missed opportunities)? Specific numbers.

8. **Surface the bias warning.** State explicitly to the user that this conversation has refined the problem statement and is now primed to validate it. The next step (`/pressure-test`) is meant to be adversarial — running it in this same conversation undercuts that.

9. **Write full output** to `./founder-outputs/problem-statement-output.md`. Display a concise summary in chat: the polished JTBD statement and the bias warning.

## Red Flags

- **"It's a problem of awareness."** Awareness is not a problem people pay to solve. Marketing budgets address awareness, not products.
- **"Users don't realize they have this problem."** Almost always means the problem isn't real. People with real problems are aware of them.
- **"Everyone has this problem."** Universal problems usually have universal solutions already. Force the founder to identify the specific segment for whom this is acute.
- **Vague workaround.** If the founder cannot describe what users do today, the problem is theoretical. Either find users to observe or downgrade confidence.

## Output

Write full output to `./founder-outputs/problem-statement-output.md`. Display concise summary in chat.

File format:

```markdown
# Problem Statement Output
**Generated:** [date]
**Domain:** [Domain]

## JTBD Problem Statement
**When** [specific situation], **[specific who]** is trying to **[specific motivation]**, so they can **[specific outcome]** — but **[specific obstacle today]**.

## Element Specificity Check
| Element | Statement | Specificity |
|---|---|---|
| Who | [...] | [Specific / Vague — push back if vague] |
| When | [...] | [Specific / Vague] |
| Motivation | [...] | [Specific / Vague] |
| Outcome | [...] | [Specific / Vague] |
| Obstacle | [...] | [Specific / Vague] |

## Cost of the Current State
**Time cost:** [Hours per [unit]]
**Money cost:** [Dollars per [unit]]
**Other costs:** [Errors, missed revenue, frustration, etc.]

## Scope Test
**One problem or several?** [Single / Compound — if compound, list sub-problems]
**If compound, the prioritized sub-problem is:** [Sub-problem]

## Boundary Test
**This problem IS:** [What's in scope]
**This problem is NOT:** [What's out of scope, even if related]

## What Changed (Why Now)
[The unlock that makes this solvable now, or "Not yet identified"]

## Bias Warning
This conversation refined the problem statement. The agent is now primed to validate it. **Run `/pressure-test` in a fresh Claude Code conversation** to get a genuinely adversarial review. `/pressure-test` is built with explicit skeptic posture — running it in the same session that just produced this statement reduces that adversarial stance.

## Pipeline Status
**Statement quality:** [SHARP / VAGUE / COMPOUND]
**Recommended Next:** `/pressure-test` (in a fresh conversation to avoid bias)
```
