---
name: battle-cards
description: This skill should be used when the user says "who are my competitors", "competitive landscape", "how am I different", "competitive analysis", "positioning", "competitive advantage", "what else is out there", or needs competitive intelligence with real competitor data, feature matrices, pricing landscapes, and positioning analysis.
version: 0.1.0
---

# Battle Cards

Competitive intelligence — who else is doing this and how do you win. Uses web search to find real competitors, not imagined ones.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `customer-archetype-output.md` — who the customer is and what they use today
- `startup-canvas-output.md` — UVP, solution features, pricing model

If `customer-archetype-output.md` is missing, recommend the user run `/customer-archetype` first — competitive analysis without a defined customer is unfocused.

## Frameworks

- *Obviously Awesome* (Dunford) — position against competitive alternatives, not features. The positioning statement format: "For [target customer] who [need], [product] is the [category] that [key benefit], unlike [competitor] which [limitation]." The market category defines the frame of reference — choose it deliberately.
- *Crossing the Chasm* (Moore) — positioning for the early majority requires a whole product. Identify what is missing from the current solution that the mainstream market requires.

## Methodology

1. **Privacy gate.** Before searching the web, confirm with the user: "I'll search for competitors in [category/industry]. This will use general terms like '[industry] software', '[problem] tools', etc. — no proprietary details. Proceed?" Wait for confirmation.

2. **Identify competitive alternatives.** Search for what customers use today. Include all five categories:
   - **Direct competitors** — products that solve the same problem the same way
   - **Indirect competitors** — products that solve the same problem differently
   - **Adjacent solutions** — products that solve a related problem and could expand
   - **DIY/manual workarounds** — spreadsheets, manual processes, hiring people
   - **Do nothing** — the status quo; often the strongest competitor

3. **Research top 3-5 competitors.** For each direct/indirect competitor, gather:
   - Company name and URL
   - Founding year, funding, team size (if available)
   - Core product description (one sentence)
   - Target customer segment
   - Pricing (specific tiers and amounts)
   - Key features
   - Strengths and weaknesses
   - Customer reviews/complaints (search "[company] reviews", "[company] complaints")

4. **Build feature matrix.** Create a comparison table: this product vs. top 3-5 alternatives across the features that matter most to the target customer (from archetype). Use checkmarks, not subjective ratings.

5. **Map the pricing landscape.** Show where each competitor sits on price. Identify:
   - Price floor (cheapest option)
   - Price ceiling (most expensive)
   - Where this product would sit and why
   - Pricing model differences (per seat vs. usage vs. flat)

6. **Identify positioning gaps.** What combinations of features, price points, or customer segments are unclaimed? Where can this product own a position that no competitor occupies?

7. **Write positioning statement.** Use Dunford's format: "For [target customer] who [need], [product] is the [category] that [key benefit], unlike [competitor] which [limitation]." Test it: does the category make sense? Would the customer recognize it?

8. **Write full output** to `./founder-outputs/battle-cards-output.md`. Display a concise summary in chat: top 3 competitors, positioning statement, key gap identified, and note that full output is saved to the file.

## Red Flags

- **"We have no competitors."** Everything has competition — even if it is "do nothing" or "hire an intern." No competitors usually means no market or insufficient research.
- **Feature-centric positioning.** Features can be copied. Position on the job-to-be-done, the customer segment served, or the business model innovation.
- **Ignoring "do nothing."** For many B2B products, the biggest competitor is inertia. If the switching cost exceeds the pain, customers will keep doing nothing.

## Output

Write full output to `./founder-outputs/battle-cards-output.md`. Display concise summary in chat.

File format:

```markdown
# Battle Cards Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Competitive Alternatives

### Direct Competitors
| Competitor | Founded | Funding | Target Customer | Price | Key Strength |
|---|---|---|---|---|---|
| [Name] | [Year] | [Amount] | [Segment] | [Price] | [Strength] |

### Indirect Competitors
[Same format]

### DIY / Manual Workarounds
[What customers do today without a dedicated tool]

### Do Nothing
[Why customers might not act, and the cost of inaction]

## Feature Matrix
| Feature | This Product | [Comp 1] | [Comp 2] | [Comp 3] |
|---|---|---|---|---|
| [Feature] | [Status] | [Status] | [Status] | [Status] |

## Pricing Landscape
| Competitor | Model | Entry Price | Mid Price | Enterprise |
|---|---|---|---|---|
| [Name] | [Model] | [Price] | [Price] | [Price] |

**This product's position:** [Where and why]

## Positioning Gaps
[What combinations of features, price, or segments are unclaimed]

## Positioning Statement
> For [target customer] who [need], [product] is the [category] that [key benefit], unlike [competitor] which [limitation].

## Competitive Moat Assessment
**Current defensibility:** [Strong / Moderate / Weak]
**Moat sources:** [What cannot be easily replicated]
**Vulnerability:** [Where competitors could catch up]

## Pipeline Status
**Position:** [DIFFERENTIATED / CROWDED / UNCLEAR]
**Recommended Next:** /assumption-map
```
