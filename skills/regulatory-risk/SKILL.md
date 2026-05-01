---
name: regulatory-risk
description: This skill should be used when the user says "regulatory risk", "compliance", "legal risk", "GDPR", "HIPAA", "SOC 2", "licensing", "regulated industry", "is this legal", "FDA", "PCI", "data privacy", "fintech regulation", "healthtech compliance", or is building in a regulated space (fintech, healthtech, legal, defense, energy, food, education). Surfaces compliance burdens and licensing requirements that can kill a product late if not addressed early.
version: 0.1.0
---

# Regulatory Risk

Surface regulatory, legal, and compliance headwinds before they become blockers. Some markets require licenses (financial services, healthcare, alcohol, cannabis, telecom), some require certifications (SOC 2, HIPAA, PCI-DSS, ISO 27001), and some require data handling protocols (GDPR, CCPA, HIPAA). A great product killed by a 12-month compliance process is a common late-stage failure.

Posture: pragmatic risk-mapper. Not all regulation is fatal. The goal is to surface what applies, what it costs, and what's a deal-breaker — early.

## Input Dependencies

Read from `./founder-outputs/` before proceeding:
- `startup-canvas-output.md` — what the product does and how data flows
- `customer-archetype-output.md` — who uses it and where they operate
- `market-size-output.md` — geographic and industry scope

If `startup-canvas-output.md` is missing, tell the user to run `/startup-canvas` first — without knowing what the product does and what data it handles, the risk surface is undefined.

## Methodology

1. **Privacy gate.** Before searching the web for regulatory data, confirm with the user: "I'll search for regulatory requirements in [industry/jurisdiction]. This will use general terms like '[industry] compliance', '[data type] regulations'. Proceed?" Wait for confirmation.

2. **Identify regulatory exposure dimensions.** Map across these axes:

   **Industry-specific regulation:**
   - **Financial services** — Money transmission licenses (state-by-state in US), broker-dealer registration (FINRA), banking partner requirements, KYC/AML, lending licenses, securities laws
   - **Healthcare** — HIPAA (PHI handling), FDA (medical devices, diagnostics, software-as-medical-device), state telemedicine licensing, billing/CMS rules
   - **Legal services** — Unauthorized practice of law (UPL), attorney advertising rules, multi-state bar requirements
   - **Education** — FERPA (student records), COPPA (under-13), accreditation, Title IV (federal student aid)
   - **Insurance** — State-by-state licensing, NAIC standards
   - **Cannabis/Alcohol** — State and local licensing, federal banking restrictions, DEA scheduling
   - **Defense/Government** — ITAR/EAR (export control), CMMC, FedRAMP
   - **Energy/Utilities** — FERC, NERC CIP, state PUC requirements
   - **Food** — FDA, USDA, state health departments, labeling rules
   - **Telecom** — FCC licensing, CALEA, robocall rules

   **Data and privacy regulation:**
   - **GDPR** (EU + EEA) — applies if any EU resident data is processed, regardless of company location
   - **CCPA/CPRA** (California) — applies to companies with California residents above thresholds
   - **HIPAA** (US healthcare) — covered entities and business associates
   - **GLBA** (US financial) — financial data privacy
   - **PIPEDA** (Canada), **LGPD** (Brazil), **PDPA** (Singapore), **APPI** (Japan)
   - **Children's privacy** — COPPA (US), Age-Appropriate Design Code (UK)

   **Security certifications expected by buyers:**
   - **SOC 2 Type II** — table stakes for B2B SaaS; 6-12 month audit
   - **ISO 27001** — international equivalent
   - **PCI-DSS** — required for handling card data
   - **FedRAMP** — required for US federal government customers
   - **HITRUST** — healthcare-specific
   - **HIPAA BAA** — required when handling PHI

3. **Determine which regulations apply.** Based on the product, customer, and geography:
   - What industry is this in?
   - What jurisdictions does it serve?
   - What data does it touch (financial, health, personal, children, government)?
   - What kind of customers does it sell to (consumers, businesses, government)?
   - For each potential regulation, mark: APPLIES / DOES NOT APPLY / NEEDS LEGAL REVIEW

4. **For each applicable regulation, quantify:**
   - **Cost to comply:** initial setup ($5K-$500K+), ongoing ($1K-$100K/year)
   - **Time to comply:** weeks (basic privacy policy) vs. months (SOC 2) vs. years (FDA approval, banking license)
   - **Required expertise:** in-house counsel, fractional CCO, external auditor, regulatory consultant
   - **Blocking severity:** can ship without it / blocks enterprise sales / blocks the product entirely

5. **Identify deal-breakers.** Flag regulations that fundamentally change the business model:
   - Banking licenses for fintech (1-2 year timeline, $1M+ in legal/regulatory)
   - FDA Class II/III medical device approval (1-3 years, $500K-$10M+)
   - State-by-state insurance licensing (12-24 months for full US coverage)
   - State-by-state money transmission licensing (12-36 months, $250K+ surety bonds per state)

6. **Identify mitigation paths.** For each blocking risk:
   - **Bank-as-a-Service (BaaS) partners** — Plaid, Synapse, Unit, Treasury Prime offer licensed banking infrastructure
   - **Compliance-as-a-Service** — Vanta, Drata, Secureframe automate SOC 2/HIPAA prep
   - **Embedded finance** — partner with a licensed entity rather than getting your own license
   - **Geographic phasing** — launch in friendly jurisdictions first (e.g., one US state for cannabis, EU pilot before US expansion)
   - **Customer phasing** — launch B2C before B2B if SOC 2 is gating, or vice versa

7. **Render risk rating:**
   - **LOW** — standard data privacy obligations only (GDPR, CCPA). Manageable with off-the-shelf tools.
   - **MEDIUM** — industry certifications required (SOC 2, HIPAA). Cost is real but timeline is months, not years.
   - **HIGH** — licensing or product approval required (FDA, banking, insurance, money transmission). Multi-year, multi-million dollar paths.
   - **BLOCKING** — current product approach is illegal or impossible without partnership. Must restructure.

8. **Write full output** to `./founder-outputs/regulatory-risk-output.md`. Display a concise summary in chat: top 3 applicable regulations, rating, and recommended mitigation path.

## Red Flags

- **"We'll figure out compliance later."** In regulated industries, "later" is too late. Compliance often requires architectural decisions (where data is stored, how it flows, who accesses it) that are expensive to retrofit.
- **"We're not technically a [bank/healthcare/insurance company]."** If the product does the things a regulated entity does, regulators will likely treat it as one. The "not technically" defense rarely holds up.
- **"Our terms of service will protect us."** Terms of service do not preempt regulation. GDPR, HIPAA, FDA rules apply regardless of what users agreed to.
- **Building in a regulated space without a compliance advisor.** Founders often discover requirements 6 months in. Hire a fractional advisor in week 1 — costs less than the rebuild.
- **"Operating in a gray area."** Gray areas eventually become enforced areas. Crypto, cannabis, and gig economy companies have all learned this. Build for the regulation that is coming, not just the one currently enforced.
- **No data residency strategy.** Customers in regulated industries (especially healthcare, government, EU enterprises) often require data to stay in specific jurisdictions. Cloud architecture decisions baked in early.

## Output

Write full output to `./founder-outputs/regulatory-risk-output.md`. Display concise summary in chat.

File format:

```markdown
# Regulatory Risk Output
**Generated:** [date]
**Idea:** [one-sentence restatement]
**Industry:** [Primary industry]
**Geography:** [Jurisdictions served]

## Applicable Regulations

### Industry-Specific
| Regulation | Applies? | Severity | Notes |
|---|---|---|---|
| [Regulation] | YES / NO / REVIEW | LOW / MED / HIGH / BLOCKING | [Brief] |

### Data Privacy
| Regulation | Applies? | Severity | Notes |
|---|---|---|---|
| GDPR | [Y/N/R] | [Severity] | [Notes] |
| CCPA/CPRA | [Y/N/R] | [Severity] | [Notes] |
| HIPAA | [Y/N/R] | [Severity] | [Notes] |
| Other | ... | ... | ... |

### Security Certifications Expected
| Certification | Required by Customer Segment | Timeline | Cost |
|---|---|---|---|
| SOC 2 Type II | [Yes/No] | [Months] | $[Range] |
| HIPAA BAA | [Yes/No] | [Months] | $[Range] |
| Other | ... | ... | ... |

## Compliance Cost & Timeline Summary

| Item | One-time Cost | Annual Cost | Timeline |
|---|---|---|---|
| [Item] | $[amount] | $[amount] | [duration] |

**Total estimated compliance burden:**
- One-time: $[X]
- Annual: $[Y]
- Time to fully compliant: [Z months]

## Deal-Breakers (if any)
[List of regulations that fundamentally block the current approach, or "None"]

## Mitigation Paths
1. [Specific mitigation — e.g., "Use Synapse as BaaS partner instead of acquiring banking license. Saves 18 months and $1M+. Tradeoff: 30-50% margin compression."]
2. [Mitigation 2]
3. [Mitigation 3]

## Required Expertise
**Hire/contract:** [Lawyer / Compliance officer / Auditor / Regulatory consultant]
**When:** [Now / Before fundraise / Before launch / Post-launch]
**Estimated cost:** $[amount/month or one-time]

## Risk Rating
**[LOW / MEDIUM / HIGH / BLOCKING]**

[2-3 sentences explaining the rating with the most material risks]

## Pipeline Status
**Regulatory Risk:** [LOW / MEDIUM / HIGH / BLOCKING]
**Recommended Next:** /assumption-map (regulatory becomes a Priority 1 assumption if HIGH/BLOCKING)
```
