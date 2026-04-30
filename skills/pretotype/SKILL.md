---
name: pretotype
description: This skill should be used when the user says "how do I validate this", "what's the MVP", "test before building", "validation experiment", "pretotype", "how do I test this assumption", "minimum viable experiment", or needs to design the smallest possible experiment to test high-risk assumptions before building anything.
version: 0.1.0
---

# Pretotype

Design the smallest possible experiment to test the riskiest assumptions before writing a line of code. A pretotype is not an MVP — it is a fake-it-before-you-make-it test that validates demand with minimal investment.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `assumption-map-output.md` — Priority 1 assumptions to test (most critical)
- `customer-archetype-output.md` — who to test with (if available)
- `pressure-test-output.md` — demand signals to validate (if available)

If `assumption-map-output.md` is missing, recommend the user run `/assumption-map` first. Without knowing which assumptions are riskiest, the experiment design is unfocused.

## Frameworks

- *Pretotype It* (Savoia) — the source methodology. "Make sure you are building the right it before you build it right." Pretotypes test market demand, not product quality. The question is "would anyone want this?" not "can we build it well?"
- *The Lean Startup* (Ries) — validated learning. Every experiment must produce learning, not just data. Define the hypothesis, the metric, and the decision criteria *before* running the experiment.

## Pretotype Types

For each assumption, select the most appropriate pretotype type:

| Type | How It Works | Best For |
|---|---|---|
| **Mechanical Turk** | Fake automation with humans behind the curtain. Customer thinks it is automated; founder does it manually. | Testing demand for an automated service before building the automation |
| **Pinocchio** | Non-functional version that looks real. A physical or digital mockup with no backend. | Testing whether customers engage with the interface/concept |
| **Landing Page** | Fake door test with a sign-up or purchase button. Measures clicks, signups, or attempted purchases. | Testing demand at scale with minimal investment |
| **Impersonator** | Use an existing product to simulate yours. Combine existing tools to deliver the value proposition manually. | Testing the value proposition without building anything new |
| **Infiltrator** | Put the product into an existing flow without announcing it. Observe whether it gets adopted organically. | Testing adoption in context without marketing bias |
| **One Night Stand** | Do it manually once for one customer. Deliver the full service by hand to one real person. | Testing whether the value proposition actually works in practice |

## Methodology

1. **Select top assumptions.** From the assumption map, take the Priority 1 assumptions (High Impact + High Uncertainty). Focus on 1-3 assumptions — more than that dilutes the effort.

2. **For each assumption, design an experiment:**

   a. **State the hypothesis.** "We believe [assumption]. If true, [consequence]. If false, [consequence]."

   b. **Select the pretotype type.** Choose based on what the assumption is testing:
      - Demand → Landing Page or One Night Stand
      - Willingness to pay → Landing Page with pricing or Mechanical Turk
      - Usability → Pinocchio
      - Value delivered → One Night Stand or Impersonator
      - Adoption in context → Infiltrator

   c. **Define the experiment.** Specific steps to execute:
      - What to build/create (keep it under 1 week of effort)
      - Who to show it to (from archetype)
      - How to deliver it (channel)
      - Timeline (1-2 weeks max)

   d. **Define success metrics.** Quantitative:
      - What to measure (signups, clicks, purchases, time spent, retention)
      - **Success threshold** — the minimum number that validates the assumption
      - **Failure threshold** — the number below which the assumption is invalidated
      - Sample size needed for statistical significance (if applicable)

   e. **Define the decision.** Before running the experiment, commit:
      - If success threshold is met → [next action]
      - If failure threshold is met → [pivot or kill decision]
      - If results are ambiguous → [what additional test to run]

3. **Sequence the experiments.** If testing multiple assumptions, order them by:
   - Dependency (test upstream assumptions first)
   - Speed (fastest experiments first to learn quickly)
   - Cost (cheapest experiments first)

4. **Write full output** to `./founder-outputs/pretotype-output.md`. Display a concise summary in chat: experiments designed, pretotype types chosen, success metrics, and note that full output is saved to the file.

## Red Flags

- **Experiment takes more than 2 weeks.** It is too complex. Simplify ruthlessly.
- **No failure threshold defined.** An experiment without a kill criterion is not a test — it is a demonstration. Define what "failure" looks like before starting.
- **Testing features instead of demand.** Pretotypes test "would anyone want this?" not "do they prefer blue or green buttons?"
- **Only asking friends.** Friendly feedback is worthless for validation. Test with strangers who match the archetype.

## Output

Write full output to `./founder-outputs/pretotype-output.md`. Display concise summary in chat.

File format:

```markdown
# Pretotype Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Assumptions Being Tested
[List of Priority 1 assumptions from assumption map]

## Experiment 1: [Assumption Name]

### Hypothesis
"We believe [assumption]. If true, [consequence]. If false, [consequence]."

### Pretotype Type
**[Type]** — [Why this type was selected]

### Experiment Design
- **What to create:** [Specific deliverable]
- **Effort required:** [Time estimate, under 1 week]
- **Who to test with:** [From archetype]
- **Channel:** [How to reach them]
- **Timeline:** [Start to finish]

### Success Metrics
| Metric | Success Threshold | Failure Threshold |
|---|---|---|
| [Metric] | [Minimum for validation] | [Below this = invalid] |

### Decision Criteria
- **If success:** [Next action]
- **If failure:** [Pivot or kill]
- **If ambiguous:** [Additional test]

## Experiment 2: [Assumption Name]
[Same structure]

## Experiment Sequence
1. [Experiment] — [Timeline] — tests [assumption]
2. [Experiment] — [Timeline] — tests [assumption]

## Total Validation Timeline
**Estimated:** [Total weeks]
**Total cost:** [Estimated budget]

## Pipeline Status
**Validation Path:** [CLEAR / UNCLEAR]
**Recommended Next:** /verdict
```
