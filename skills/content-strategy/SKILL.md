---
name: content-strategy
description: This skill should be used when the user says "content strategy", "content marketing", "what should I write about", "blog strategy", "social media plan", "how do I build an audience", "thought leadership", "inbound marketing", or needs a content plan matched to the customer archetype's information sources and buyer journey. Not "do content marketing" — a specific plan tied to where the customer actually reads and what they need to hear at each stage.
version: 0.1.0
---

# Content Strategy

Given the positioning and customer archetype, what content earns trust with this specific buyer? Where do they actually read? What format? What topics move them from unaware to ready-to-buy? Avoids the "we'll do content marketing" vagueness.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `customer-archetype-output.md` — information sources, communities, what they read (required)
- `startup-canvas-output.md` — UVP, problems, positioning
- `battle-cards-output.md` — competitor content gaps, positioning
- `oneliner-output.md` — core messaging (if available)
- `gtm-plan-output.md` — channel ranking (if available)

If `customer-archetype-output.md` is missing, tell the user to run `/customer-archetype` first — content without a defined audience is noise.

## Frameworks

- *Obviously Awesome* (Dunford) — positioning defines the content category. Content should reinforce the market category the product owns, not scatter across random topics.
- *$100M Leads* (Hormozi) — content as a lead generation engine. Every piece of content should either teach (build trust), show results (build proof), or provoke (build attention). Entertainment without conversion intent is a hobby, not a strategy.

## Methodology

1. **Map the buyer journey content needs.** Define what the archetype needs to hear at each stage:

   | Stage | Customer State | Content Goal | Content Type |
   |---|---|---|---|
   | **Unaware** | Does not know the problem has a better solution | Name the pain, make it visible | Blog posts, social, short-form |
   | **Problem-aware** | Knows the problem, exploring options | Educate on approaches, not products | Guides, frameworks, comparisons |
   | **Solution-aware** | Evaluating specific solutions | Build trust and differentiate | Case studies, demos, ROI calculators |
   | **Decision** | Ready to choose | Reduce risk, make it easy | Free trials, testimonials, migration guides |

2. **Identify the content channels.** From the archetype's information sources, determine where content should be published:
   - Where do they read? (Specific publications, newsletters, blogs)
   - Where do they discuss? (Specific Slack groups, Discord servers, Reddit subs, forums)
   - Where do they scroll? (LinkedIn, Twitter/X, specific platforms)
   - Where do they watch/listen? (YouTube, podcasts, webinars)
   - Rank channels by archetype engagement, not founder preference.

3. **Identify content gaps from competitors.** From battle-cards output, analyze:
   - What topics competitors cover well (do not compete here initially)
   - What topics competitors ignore or cover poorly (own these)
   - What positioning angle is underserved in existing content

4. **Generate a 30-day content plan.** Produce 12 specific content pieces (3 per week):
   - **Title** (specific, not "blog about X")
   - **Format** (post, thread, guide, video, newsletter)
   - **Channel** (where to publish)
   - **Buyer stage** (which stage it serves)
   - **Hook** (first sentence or angle that earns the click)
   - **CTA** (what the reader should do next — subscribe, try, share)

5. **Define the content pillar.** Identify the one topic this brand should own — the category-defining theme that all content ladders up to. This is not "AI" or "productivity." It is specific: "shipment reconciliation for mid-market logistics" or "compliance automation for fintech startups."

6. **Specify success metrics.** Not vanity metrics:
   - **Leading indicators:** email subscribers, content-attributed sign-ups, direct replies
   - **Lagging indicators:** content-attributed revenue, SQLs from content
   - **Avoid:** follower count, likes, impressions (unless selling ads)

7. **Write full output** to `./founder-outputs/content-strategy-output.md`. Display a concise summary in chat: the content pillar, top 3 content pieces, primary channel, and note that full output is saved to the file.

## Red Flags

- **Publishing where the founder hangs out, not the customer.** The founder's Twitter following is not the customer's information source.
- **All content is product-focused.** Problem-aware and unaware stages need educational content, not product pitches.
- **No CTA on any content.** Content without a conversion path is brand awareness that cannot be measured.
- **"We'll post 3x a day."** Frequency without quality and targeting is noise. Better to publish 3 excellent pieces per week in the right channel than 3 mediocre posts per day everywhere.

## Output

Write full output to `./founder-outputs/content-strategy-output.md`. Display concise summary in chat.

File format:

```markdown
# Content Strategy Output
**Generated:** [date]
**Idea:** [one-sentence restatement]

## Content Pillar
**The one topic to own:** [Specific theme]
**Why this pillar:** [Ties to positioning and archetype needs]

## Buyer Journey Content Map
| Stage | Content Need | Format | Channel | Frequency |
|---|---|---|---|---|
| Unaware | [Need] | [Format] | [Channel] | [Freq] |
| Problem-aware | [Need] | [Format] | [Channel] | [Freq] |
| Solution-aware | [Need] | [Format] | [Channel] | [Freq] |
| Decision | [Need] | [Format] | [Channel] | [Freq] |

## Competitor Content Gaps
- **They cover well:** [Topics to avoid initially]
- **They ignore:** [Topics to own]
- **Underserved angle:** [Positioning gap in content]

## 30-Day Content Plan
| Week | Title | Format | Channel | Stage | Hook | CTA |
|---|---|---|---|---|---|---|
| 1 | [Title] | [Format] | [Channel] | [Stage] | [Hook] | [CTA] |
| 1 | [Title] | [Format] | [Channel] | [Stage] | [Hook] | [CTA] |
| 1 | [Title] | [Format] | [Channel] | [Stage] | [Hook] | [CTA] |
| 2 | [Title] | [Format] | [Channel] | [Stage] | [Hook] | [CTA] |
| ... | ... | ... | ... | ... | ... | ... |

## Success Metrics
**Leading:** [Specific metrics with targets]
**Lagging:** [Revenue-attributed metrics]
**Do NOT track:** [Vanity metrics to ignore]

## Pipeline Status
**Content Clarity:** [CLEAR / NEEDS REFINEMENT]
**Recommended Next:** Start with Week 1 content pieces
```
