---
name: gtm-plan
description: This skill should be used when the user says "go to market", "GTM", "how do I get customers", "acquisition strategy", "growth channels", "marketing plan", "distribution", "how do I sell this", or needs a structured go-to-market strategy. Uses the Bullseye framework to rank 19 channels and design cheap tests for the top 3. Reads canvas + archetype for channel-customer fit.
version: 0.1.0
---

# GTM Plan

Go-to-market strategy derived from the startup canvas and customer archetype. Not "we'll do content marketing" — a ranked channel strategy with specific experiments.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — channels, pricing, key metric (required)
- `customer-archetype-output.md` — information sources, communities, decision role (required)
- `battle-cards-output.md` — competitor channels, positioning gaps
- `market-size-output.md` — SOM and customer count

If `customer-archetype-output.md` is missing, tell the user to run `/customer-archetype` first — a GTM plan without a defined customer is guesswork.

## Frameworks

- *Traction* (Weinberg & Mares) — Bullseye framework. List all 19 traction channels, rank them for this specific business, run cheap experiments on the top 3. Most founders default to the channel they personally use, not the one their customer uses.
- *$100M Leads* (Hormozi) — lead generation mechanics. The four core ways to get customers: warm outreach, cold outreach, content, paid ads. Each has a free version and a paid version.
- *Predictable Revenue* (Ross & Tyler) — outbound sales methodology. Cold outbound only works with extreme specificity on the target. The archetype output provides that specificity.

## Methodology

1. **Score all 19 traction channels.** For each channel, rate fit on a 1-5 scale based on the customer archetype's behavior:

   | Channel | Description |
   |---|---|
   | Targeting blogs | Guest posts on industry blogs the archetype reads |
   | PR/publicity | Press coverage in publications the archetype trusts |
   | Unconventional PR | Stunts, viral content, controversial takes |
   | Search engine marketing | Paid search on terms the archetype searches |
   | Social/display ads | Paid ads on platforms the archetype uses |
   | Offline ads | Physical ads in places the archetype goes |
   | Search engine optimization | Ranking for terms the archetype searches |
   | Content marketing | Creating content the archetype wants to consume |
   | Email marketing | Newsletters/sequences to the archetype's inbox |
   | Engineering as marketing | Free tools that demonstrate value |
   | Viral marketing | Built-in sharing/referral mechanics |
   | Business development | Partnerships with adjacent products |
   | Sales | Direct outbound to archetype companies |
   | Affiliate programs | Paying others to send customers |
   | Existing platforms | Marketplaces, app stores, directories the archetype browses |
   | Trade shows | Events the archetype attends |
   | Offline events | Meetups, workshops, dinners |
   | Speaking engagements | Conferences where the archetype is in the audience |
   | Community building | Creating a community the archetype wants to join |

2. **Select the top 3 channels.** Choose based on:
   - Where the archetype actually spends time (from archetype output)
   - What competitors are NOT doing well (from battle-cards)
   - What can be tested cheaply in 1-2 weeks
   - What the founder can personally execute (no channel works without effort)

3. **Design a cheap test for each top channel.** For each:
   - **Experiment:** specific action to take (not "try content marketing" — "publish 3 posts on [specific topic] in [specific community]")
   - **Budget:** under $500 or free
   - **Timeline:** 1-2 weeks
   - **Success metric:** specific number (e.g., "10 sign-ups from this channel" or "2 demo requests")
   - **Decision:** if success metric is hit, double down. If not, move to next channel.

4. **Define the GTM sequence.** Order the channel experiments:
   - **Week 1-2:** Test channel #1 (cheapest, fastest feedback)
   - **Week 3-4:** Test channel #2 (parallel if possible)
   - **Week 5-6:** Test channel #3
   - **Week 7+:** Double down on the winner

5. **Estimate unit economics for each channel.** For the top 3:
   - Estimated customer acquisition cost (CAC)
   - Expected lifetime value (LTV) from canvas pricing
   - CAC payback period
   - Flag any channel where CAC > LTV

6. **Write full output** to `./founder-outputs/gtm-plan-output.md`. Display a concise summary in chat: top 3 channels, first experiment, and note that full output is saved to the file.

## Red Flags

- **Defaulting to the founder's favorite channel.** "We'll grow through Twitter" because the founder uses Twitter, not because the customer does.
- **No experiment designed.** A channel strategy without experiments is a wish list.
- **CAC > LTV.** If acquiring a customer costs more than they are worth, the channel does not work at this price.
- **Relying on a single channel.** The plan should have 3 channels tested, with the understanding that 1-2 will fail.

## Output

Write full output to `./founder-outputs/gtm-plan-output.md`. Display concise summary in chat.

File format:

```markdown
# GTM Plan Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Channel Ranking (All 19)
| Rank | Channel | Fit (1-5) | Rationale |
|---|---|---|---|
| 1 | [Channel] | [Score] | [Why it fits the archetype] |
| 2 | [Channel] | [Score] | [Why] |
| ... | ... | ... | ... |

## Top 3 Channel Experiments

### Channel #1: [Name]
**Why this channel:** [Archetype behavior that supports it]
**Experiment:** [Specific action]
**Budget:** [$ amount or free]
**Timeline:** [1-2 weeks]
**Success metric:** [Specific number]
**Decision rule:** Hit metric → double down. Miss → move to #2.
**Estimated CAC:** [$X]
**LTV:** [$X from canvas]
**Payback:** [Months]

### Channel #2: [Name]
[Same structure]

### Channel #3: [Name]
[Same structure]

## GTM Sequence
- Week 1-2: [Channel #1 experiment]
- Week 3-4: [Channel #2 experiment]
- Week 5-6: [Channel #3 experiment]
- Week 7+: Double down on winner

## Unit Economics Summary
| Channel | CAC | LTV | CAC:LTV | Viable? |
|---|---|---|---|---|
| [Channel] | [$] | [$] | [Ratio] | [Yes/No/TBD] |

## Pipeline Status
**GTM Clarity:** [CLEAR / NEEDS TESTING / UNCLEAR]
**Recommended Next:** /cold-outreach, /content-strategy
```
