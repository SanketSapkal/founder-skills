---
name: scope-mode
description: This skill should be used when the user says "think bigger", "expand scope", "is this ambitious enough", "what's the right scope", "scope down", "narrow focus", "reduce scope", "should I go bigger", "what's the wedge", "smallest version", or needs to calibrate the ambition level of an idea between EXPAND, SELECTIVE, HOLD, and REDUCE modes after pressure-testing.
version: 0.1.0
---

# Scope Mode

After pressure-test passes, calibrate the scope before modeling begins. Too broad kills focus; too narrow limits potential. This skill forces an explicit scope decision with rationale.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `pressure-test-output.md` — demand verdict and evidence (recommends scope mode based on findings)
- `customer-archetype-output.md` — customer specificity (SHARP archetype enables EXPAND; VAGUE archetype forces REDUCE)

If both outputs exist, recommend a scope mode based on the combined signal:
- STRONG demand + SHARP archetype → consider EXPAND or SELECTIVE
- STRONG demand + VAGUE archetype → recommend HOLD (nail the customer before expanding)
- WEAK demand → recommend REDUCE regardless of archetype specificity (find the wedge)
- UNCLEAR demand → recommend HOLD (clarify before expanding)

## Frameworks

- *Zero to One* (Thiel) — monopoly thinking. Start small and dominate a niche before expanding. "It's much better to be the last mover — to make the last great development in a specific market." The best startups own a small market completely before going big.
- *The Lean Startup* (Ries) — minimum viable scope. What is the smallest thing that delivers complete value to one customer segment? Not a feature subset — a complete solution for a narrow problem.

## Scope Modes

| Mode | When to Use | Posture |
|---|---|---|
| **EXPAND** | Demand is strong, market is large, founder has unique insight that enables a bigger play | Dream big. What is the 10-star version? What does this become in 10 years? Where is the platform opportunity? |
| **SELECTIVE** | Core idea is solid but one or two adjacent opportunities are too good to ignore | Hold the core scope but cherry-pick high-value expansions. Add only what strengthens the core — not "wouldn't it be cool if..." features. |
| **HOLD** | Demand is real but the right scope is unclear, or the founder is tempted to add too much | Maximum rigor on the current scope. No scope creep. Defend every feature against "does this serve the #1 customer?" test. |
| **REDUCE** | Demand is weak or unclear, or the idea is trying to do too many things | Strip to the smallest possible wedge. What is the one thing this does better than anything else? If the product could only do one thing, what would it be? |

## Methodology

1. **Review pressure-test results.** Read the demand verdict and evidence. Identify whether the idea's scope is currently too broad, too narrow, or well-calibrated.

2. **Recommend a mode.** Based on the evidence, recommend one of the four modes with a specific rationale. Present the recommendation and ask the user to confirm or override.

3. **Apply the selected mode:**

   **If EXPAND:**
   - Identify the 10-star version (what would make customers insanely, irrationally happy?)
   - Map the platform opportunity (what else can be built on top of the core?)
   - Identify the 10-year vision (what does full market dominance look like?)
   - Ground the expansion in the demand evidence — expansion without evidence is fantasy

   **If SELECTIVE:**
   - List 3-5 potential expansions
   - Score each on: customer demand evidence, competitive advantage, implementation complexity
   - Select 1-2 that strengthen the core without diluting focus
   - Explicitly reject the rest with reasons

   **If HOLD:**
   - Restate the current scope precisely
   - List every feature/capability and test it against: "Does this directly serve the #1 customer's #1 problem?"
   - Remove anything that fails the test
   - Define the "not doing" list — what is explicitly out of scope and why

   **If REDUCE:**
   - Identify the single most valuable wedge
   - Apply the "one-thing test": if this product could only do one thing, what would it be?
   - Define the absolute minimum that delivers complete value
   - Identify the beachhead customer — the single narrowest segment that needs this most

4. **Define scope boundaries.** Regardless of mode, produce a clear scope definition:
   - **In scope:** specific capabilities and customers
   - **Out of scope:** explicit exclusions with rationale
   - **Future scope:** what comes later if the core succeeds

5. **Write full output** to `./founder-outputs/scope-output.md`. Display a concise summary in chat: selected mode, what is in/out, and note that full output is saved to the file.

## Output

Write full output to `./founder-outputs/scope-output.md`. Display concise summary in chat.

File format:

```markdown
# Scope Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Selected Mode
**[EXPAND / SELECTIVE / HOLD / REDUCE]**

## Rationale
[Why this mode was selected, grounded in pressure-test evidence]

## Scope Definition

### In Scope
- [Capability / customer / market that is included]

### Out of Scope
- [Capability / customer / market explicitly excluded] — [why]

### Future Scope (if core succeeds)
- [What to add later]

## Mode-Specific Output
[Depends on mode selected — 10-star version for EXPAND, selected expansions for SELECTIVE, pruned feature list for HOLD, wedge definition for REDUCE]

## Pipeline Status
**Mode:** [EXPAND / SELECTIVE / HOLD / REDUCE]
**Recommended Next:** /customer-archetype
```
