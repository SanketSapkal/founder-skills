---
name: build-brief
description: This skill should be used when the user says "what should I build", "implementation plan", "build brief", "hand off to engineering", "product spec", "what do I build first", "pass this to a coding agent", or has received a BUILD verdict and needs a structured handoff document for a coding agent. Reads all founder-outputs and produces a single file that any coding agent (gstack, Claude Code, Cursor, etc.) can consume.
version: 0.1.0
---

# Build Brief

Translate a validated idea into a structured implementation handoff. Not a full PRD — a scoped brief covering what to build, in what order, with what data, and how to know it works. One file, everything a coding agent needs, nothing it does not.

This skill bridges the gap between "should I build this?" (founder-skills pipeline) and "build this" (coding agent). The output is designed to be handed directly to gstack `/autoplan`, Claude Code, or any other implementation agent.

## Input Dependencies

Read ALL files from `./founder-outputs/` before proceeding:
- `verdict-output.md` — must show BUILD (required)
- `startup-canvas-output.md` — problems, UVP, features, pricing, key metric
- `customer-archetype-output.md` — who uses this, their workflow, their pain
- `scope-output.md` — what is in/out of scope
- `assumption-map-output.md` — riskiest assumptions to validate first
- `pretotype-output.md` — validation experiments and success criteria
- `pressure-test-output.md` — demand evidence and JTBD framing
- `battle-cards-output.md` — competitive positioning

If `verdict-output.md` is missing or does not show BUILD, tell the user to run `/verdict` first. If it shows KILL or PIVOT, recommend `/pivot-paths` instead.

## Frameworks

- *Shape Up* (Basecamp) — appetite-driven scoping. Define the appetite (how much time to invest) before defining the solution. A 2-week appetite produces a different product than a 6-week appetite. The brief should scope to an appetite, not to a feature list.
- *Inspired* (Cagan) — product spec discipline. Separate the problem from the solution. The brief defines what success looks like; the coding agent decides how to implement it.
- *The Lean Startup* (Ries) — validated learning loops. The first build cycle should test the riskiest assumption, not build the full product.

## Methodology

1. **Confirm the verdict.** Read `verdict-output.md`. If the verdict is not BUILD, stop and explain. Proceeding to implementation on a KILL or PIVOT verdict wastes engineering time.

2. **Define the appetite.** Ask the user: "How much time do you want to invest in the first build cycle?" Options:
   - **1 week** — bare minimum to test one assumption
   - **2 weeks** — smallest usable version for one customer
   - **4 weeks** — v0.1 with core loop working end-to-end
   - **8 weeks** — v1.0 ready for early adopters

3. **Extract core user flows.** From the startup canvas (problems + solution) and customer archetype (current workflow), identify the 3-5 user flows that make the value proposition real. Each flow should be:
   - Stated as: "[User] does [action] to achieve [outcome]"
   - Mapped to a ranked problem from the canvas
   - Traceable to evidence from the pressure test

4. **Build the feature list.** Split features into three tiers:
   - **Must-have at launch** — features required to deliver the core value prop. If any of these is missing, the product does not work. Typically 3-5 features.
   - **Important but deferrable** — features that improve the experience but are not required for first validation. Build these after validating core assumptions.
   - **Explicitly out of scope** — features the founder or team will be tempted to build but should not. Name them and explain why they are deferred.

5. **Define core data entities.** Identify the 4-6 entities the product needs to store and manage. For each:
   - Entity name and description
   - Key attributes (not a full schema — just the load-bearing fields)
   - Relationships to other entities
   - What needs to be queryable fast (drives index decisions)
   - Where the revenue model lives in the data (pricing, billing, metering)

6. **Sequence the build.** Map features to the appetite timeline:
   - **Week 1-2:** The one thing that tests the riskiest assumption (from assumption map). This is not the most impressive feature — it is the one where being wrong is most costly.
   - **Week 3-4:** The smallest thing that delivers end-to-end value to one real customer.
   - **Month 2:** What v0.1 looks like — core loop complete, ready for feedback.
   - **Month 3:** What to add based on initial feedback (leave this section as placeholders).

7. **Define success criteria.** From the pretotype output and assumption map, extract:
   - The key metric that matters (from canvas)
   - What number validates the riskiest assumption
   - What number invalidates it
   - What qualitative signals to watch for (user quotes, behavior patterns)

8. **Write the handoff block.** Include a ready-to-paste prompt for the coding agent:
   ```
   I have a validated idea and implementation plan.
   Read founder-outputs/build-brief-output.md
   Start with [week 1-2 scope]. Build only what's specified — nothing more.
   ```

9. **Write full output** to `./founder-outputs/build-brief-output.md`. Display a concise summary in chat: appetite, top 3 features, first build target, key success metric, and note that full output is saved to the file.

## Red Flags

- **Building the full product in week 1.** The first cycle should test one assumption, not ship a polished product.
- **No success criteria defined.** Building without knowing what "working" looks like is coding in the dark.
- **Features not tied to problems.** Every must-have feature should trace to a ranked problem from the canvas. Orphan features are scope creep.
- **Data model has more than 8 entities at launch.** Complexity kills early-stage products. Fewer entities, fewer bugs, faster iteration.

## Output

Write full output to `./founder-outputs/build-brief-output.md`. Display concise summary in chat.

File format:

```markdown
# Build Brief Output
**Generated:** [date]
**Idea:** [one-sentence restatement]
**Verdict:** BUILD
**Appetite:** [1 week / 2 weeks / 4 weeks / 8 weeks]

## Core User Flows
1. **[Flow name]** — [User] does [action] to achieve [outcome]
   - Maps to Problem #[N] from canvas
   - Evidence: [from pressure test]
2. [...]

## Feature List

### Must-Have at Launch
| Feature | Solves Problem | User Flow | Complexity |
|---|---|---|---|
| [Feature] | #[N] | [Flow] | S/M/L |

### Important but Deferrable
- [Feature] — [Why it can wait]

### Explicitly Out of Scope
- [Feature] — [Why not now]

## Core Data Entities
| Entity | Key Attributes | Relationships | Query Needs |
|---|---|---|---|
| [Entity] | [Fields] | [Relations] | [What's queried] |

**Revenue in the data:** [Where billing/pricing/metering lives]

## Build Sequence
### Week 1-2: Test the Riskiest Assumption
**Assumption:** [From assumption map]
**Build:** [Specific scope]
**Validate by:** [Metric and threshold]

### Week 3-4: First Customer Value
**Deliver:** [What the customer gets]
**To whom:** [From archetype]

### Month 2: v0.1
**Scope:** [Core loop complete]

### Month 3: Post-Feedback
**TBD based on:** [What signals to watch]

## Success Criteria
**Key metric:** [From canvas]
**Validates if:** [Number/signal]
**Invalidates if:** [Number/signal]
**Watch for:** [Qualitative signals]

## Coding Agent Handoff
```
I have a validated idea and implementation plan.
Read founder-outputs/build-brief-output.md
Start with week 1-2 scope. Build only what's specified.
```

## Pipeline Status
**Handoff Ready:** YES
**Recommended Next:** Hand off to coding agent, then /gtm-plan
```
