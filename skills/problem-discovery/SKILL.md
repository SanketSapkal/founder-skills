---
name: problem-discovery
description: This skill should be used when the user says "I want to work in [domain]", "I'm interested in [space]", "looking for problems to solve", "problem discovery", "find a problem", "I don't have an idea yet but", or has a domain interest but no specific problem identified. Helps surface candidate problems before any idea formation.
version: 0.1.0
---

# Problem Discovery

For founders who have a domain interest but no specific problem yet. Guides through observation, customer proximity, and candidate problem identification — output is a ranked list of problems worth investigating, not a startup idea.

Posture: explorer, not solutioner. Resist the urge to converge on "an idea." The job here is to surface problems with evidence, not invent solutions.

## Frameworks

- *The Mom Test* (Fitzpatrick) — go observe behavior, do not ask hypotheticals. The earliest signal is what people *do*, not what they *say* they need.
- *Competing Against Luck* (Christensen) — JTBD framing for discovery. What jobs are people hiring suboptimal solutions to do? Bad workarounds = candidate problems.
- *Inspired* (Cagan) — discovery is its own discipline. Most ideas die because they solve problems no one cares about.

## Methodology

1. **Map the domain.** Ask:
   - "What domain or industry are you drawn to?"
   - "Why this space? What experience or curiosity brought you here?"
   - "Who do you know personally who works in this space today?"

2. **Identify problem zones.** Within the domain, probe:
   - Where do people work around tools rather than with them?
   - Where do workflows require human judgment that could be supported?
   - Where do specialists spend time on tasks that are not their highest-value work?
   - What is done in spreadsheets that probably should not be?
   - What is still done by hand?

3. **Surface 5-7 candidate problems.** Each should be one sentence: "[Who] currently does [task] in a way that [costs / frustrates / limits them]." Push for breadth before depth.

4. **Score each candidate** on:
   - **Pain severity** — how much does it cost (time, money, frustration)?
   - **Pain frequency** — daily, weekly, monthly, rare?
   - **Customer proximity** — how easily can the founder access these customers for interviews?
   - **Existing workarounds** — what are people doing today (evidence of pain)?
   - **Founder fit signal** — does the founder have a credible angle here?

5. **Rank top 3.** Identify which 3 are most worth investigating further. Be specific about why each made the cut.

6. **Recommend the discovery action.** For each top-3 problem, the next step is usually: "Talk to 5-10 [target customer] about how they handle [problem]. Do not pitch a solution. Listen for workarounds." The founder must do this work in the real world — the skill cannot validate problems by reasoning alone.

7. **Surface the bias warning.** State explicitly to the user that this conversation is now primed with these candidates and downstream skills should run in a fresh conversation.

8. **Write full output** to `./founder-outputs/problem-discovery-output.md`. Display a concise summary in chat: top 3 candidates, the next discovery action for each, and the bias warning.

## Red Flags

- **"I want to do AI in [domain]."** Tech-first framing. Technology is not a problem. Push back: what problem in [domain] are you investigating?
- **"There must be problems with [process]."** Speculation. Push for direct observation or conversation evidence before listing candidates.
- **Founder has zero customers in network.** If the founder cannot reach a customer for an interview without a cold email, problem discovery will be slow. Flag this and suggest building customer access before refining problem candidates.
- **Premature solutioning.** When the founder starts proposing how to solve a candidate problem, redirect — the goal here is to find problems worth solving, not invent solutions.

## Output

Write full output to `./founder-outputs/problem-discovery-output.md`. Display concise summary in chat.

File format:

```markdown
# Problem Discovery Output
**Generated:** [date]
**Domain of interest:** [Domain]

## Founder's Connection to the Domain
**Why this space:** [Founder's stated reason]
**Customer access:** [Strong / Moderate / Weak — how easy to interview people in this space]

## Candidate Problems Surfaced
[5-7 candidate problems, each one sentence]

## Ranked Top 3 Candidates

### 1. [Problem]
**Who has it:** [Specific role/segment]
**Severity:** [High / Medium / Low — with rationale]
**Frequency:** [Daily / Weekly / Monthly / Rare]
**Workaround evidence:** [What people do today]
**Recommended discovery action:** [Specific — e.g., "Interview 5 ops managers about Friday reconciliation. Listen for workarounds, don't pitch."]

### 2. [Problem]
[Same structure]

### 3. [Problem]
[Same structure]

## Bias Warning
This conversation surfaced these candidates and is now primed toward them. To avoid confirmation bias in downstream skills (`/problem-statement`, `/pressure-test`), run them in a **fresh Claude Code conversation** after doing customer interviews. The agent in this session will tend to validate these candidates rather than genuinely challenge them.

## Pipeline Status
**Discovery state:** CANDIDATES IDENTIFIED — need real-world validation
**Recommended Next:** Talk to customers, then run `/problem-statement` in a new conversation.
```
