# Campaign Strategy: AURA Kenya

Date: 2026-11-20. Built from CLAUDE.md, everything in context/ (ICP, personas, signal matrix, positioning, messaging, brand, case studies, facts, research), and knowledge-base/playbooks/workflow-anatomy.md. No web research was run. `meetings/` and `knowledge-base/learnings/` are empty.

Conventions: facts cite a research file. INFERRED means no source states it. Volume is new accounts entering per month and is INFERRED everywhere unless a source is shown, so validate in Clay before building. Mother Intent names come from the workflow-anatomy catalog.

**Target audience (given):** Kenyan businesses with an end-user base (customers, staff, drivers, riders) that want security, medical and roadside response under their own brand (icp.md).
**Core value proposition:** one platform and one API for security, medical and roadside response, white-label, with vetted responders and an incident audit trail (company.md, positioning.md).
**Key differentiators:** breadth versus Rescue.co's add-on model; security response that 922 does not cover; partner-brand model (competitors.md, company.md).

## Customer Discovery Analysis

| Company | Industry | Key metric | Problem solved |
|---|---|---|---|
| Old Mutual (Kenya) | Insurance | OM Rescue Plus launched 29 Jan 2025, now motor, medical, SME health | Safety and well-being of customers |
| SanlamAllianz (Kenya) | Insurance | Emergency Assist app across 5 lines | Cross-line emergency cover |
| ICEA Lion (Kenya) | Insurance | Named client, also on Rescue.co list | Not stated |
| Glovo Kenya | Gig delivery | Announced 16 Jun 2026, incident tracking | Rider road safety and welfare |
| Uber (Kenya, SA) | Ride-hailing | In-app emergency button | Not stated |
| Greenwheels (Kenya) | Vehicle rental | Better efficiency and customer experience | Not stated |
| Tracker (SA) | Telematics | "90,000+" users, "~3 x" ROI | Revenue-driving value-added service |
| OUTsurance (SA) | Insurance | "+148 lives" in 2025, audit trail portal | Visibility and short response |
| StarFM, DSOC, OCS, SmartWatch, StopIt, Namola, Samsung | Monitoring, security, apps | 45% controller time saved (StarFM), 7-minute response (Namola) | Control room load, rapid dispatch |

**Patterns:**
- Insurers and platforms dominate in Kenya. Telematics and monitoring centres dominate outside Kenya.
- Buyers are mid to large firms with a mobile app or policy base (size is INFERRED).
- Recurring needs: easy integration, incident visibility, a branded value-added service.

**Targeting recommendation:**
- Keep Tier 1A (insurers) and Tier 1B (platforms) as the core, since they have named Kenyan proof.
- Treat banks and corporate wellness as unproven. No Kenyan logo exists.
- Research supports two audiences outside the stated ICP:
  - Resellers: monitoring centres and security companies, which company.md lists as channel partners.
  - Telematics firms: Tracker is an AURA customer in South Africa.
- Rescue.co's partner list names accounts AURA does not yet serve: Bolt, JW Seagon and micro-insurers (competitors.md).

**Best lookalike seeds:** Old Mutual, SanlamAllianz (insurers); Glovo, Uber (platforms); Greenwheels (rental).

**Copy constraint:** no list of customer names authorised for outbound copy exists in the repo. Get AURA's approval before any copy names a customer.

## Campaign Ideas (ranked)

Score = signal strength (1 to 5) + data ease (1 to 5), max 10. Ties are broken by signal strength. Scores for ranks 1 to 8 come from signal-matrix.md. The rest are my judgement (INFERRED). Value tags: MM make money, TS save time, SM save money, MR mitigate risk.

| Rank | Campaign | Level | Mother Intent | Tier | Segment and persona | Signal and data source | Angle | Volume/mo (INFERRED) | Difficulty | Score |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Sister-line expansion (S1) | Niche | New product launches | Tier 1: strongest Kenyan proof, clean data, already specced as W1 | Tier 1A composite insurers. Champion: Head of Medical, General, Life, Claims, Product, VAS. Buyer: MD, CEO, CFO | Insurer runs motor or general rescue and promotes medical, SME or life lines. IRA directory plus product pages via Crawl4AI and Clay | "Your motor customers have rescue, your health members do not." Claygent names the unserved line. MM, MR | 15 to 30 (W1 spec) | Low to Medium | 10 |
| 2 | Rider and driver safety (S2) | Niche | Website content mentions | Tier 1: Glovo proof, mobile apps ready | Tier 1B delivery, ride-hailing, logistics. Champion: Head of Operations. Buyer: COO, CEO | Road safety pressure, new town launches, incident press. Press RSS, app listings, LinkedIn Jobs via Apify and Clay | "Every incident visible, every rider covered." Claygent finds their rider app and latest expansion. MR, TS | 40 to 80 (W2 spec) | Medium | 9 |
| 3 | Rescue.co partner consolidation (S3) | Niche | Competitor customers | Tier 1: named accounts, small but specific | Bolt, JW Seagon, micro-insurers. Champion: ops or VAS lead | Rescue.co launch coverage and partner pages. Crawl4AI and Clay | "Roadside is covered. Armed security and medical sit elsewhere." One platform, one API, one audit trail. MR, SM | 10 to 25 (W3 spec) | Low | 9 |
| 4 | Post-922 security and roadside gap (S7) | Broad | Regulatory changes | Tier 1: high volume, but a compound layer | Tier 1A and 1B. Champion: Claims, Care, Ops | 922 launched 5 Aug 2026, medical evacuation only. News, no tooling | "922 moves the patient. Who covers the guard and the tow truck?" Static copy. MR | 100 to 200 | Low | 9 |
| 5 | New product, claims, VAS or ops leader (S4) | Focused | New leadership (past 90/180 days) | Tier 1: reliable start dates, repeatable | All tiers. Head of Product, Claims, VAS, Ops, People | Start date under 180 days. Apollo or Sales Navigator via Clay | "New in role, first quick win." Claygent pulls previous employer and inherited remit. MM, TS | 20 to 40 | Medium | 8 |
| 6 | Hiring integration, claims or fleet safety roles (S6) | Niche | Hiring specific roles | Tier 2: good signal, thin Kenyan job data | Tier 1A and 1B. Hiring manager | Mobile PM, Claims Manager, Fleet Safety Lead roles. BrighterMonday, LinkedIn Jobs via Apify and Clay | "You are hiring for X, here is the shortcut." TS | 15 to 30 | Medium | 8 |
| 7 | PSRA compliance squeeze (S5) | Focused | Regulatory changes | Tier 2: rules observed, buyer effect inferred | Corporates buying guards; security operations leads | PSRA closures and draft rules. PSRA notices, news via n8n | "Tighter rules on guard vendors. AURA responders hold PSRA accreditation." MR | 30 to 60 | Low to Medium | 8 |
| 8 | Heavy rains duty of care (S8) | Focused | Niche-specific play | Tier 2: seasonal | Fleets and corporates. Ops, HSE | Rains forecast, AURA Kenya lead's advice. News RSS via n8n | "Rains are forecast. Is your emergency plan ready?" MR | 30 to 60 in season | Low | 8 |
| 9 | Lookalike of insurer references | Focused | Lookalike of customers | Tier 2: weaker signal, easy data | Other Kenyan insurers like Old Mutual and SanlamAllianz | IRA directory, Clay lookalike. Exclude existing clients | "Insurers like yours already offer this." Names only with approval. MM | 15 to 30 | Low | 8 |
| 10 | Tender compliance trigger | Niche | Regulatory changes | Tier 2: one observed case | Public bodies issuing security tenders. Procurement, Legal | Kenya Railways tender warning, Oct 2026. Tender portals | "Your tender asks for verified vendors. Here is the PSRA, licence and insurance checklist." MR | 5 to 15 | Medium | 7 |
| 11 | Fleet safety or HSE title present | Niche | Have/don't have specific team | Tier 2: volume unproven | Logistics and rental fleets. Fleet Safety, HSE Manager | Title on LinkedIn via Clay | "Fleet safety needs an incident record, not a phone call." MR, TS | 10 to 25 | Medium | 7 |
| 12 | Lookalike of platform references | Focused | Lookalike of customers | Tier 2: overlaps rank 3 on Bolt | Firms like Glovo, Uber, Greenwheels | Clay lookalike, app listings. Dedupe against rank 3 | "Platforms like Glovo protect riders this way." Names only with approval. MR | 15 to 30 | Low | 7 |
| 13 | Resellers (Creative, non-ICP) | Niche | Niche-specific play | Tier 2: sold this way elsewhere, none proven in Kenya | Alarm monitoring centres and security companies. MD, BD lead | PSRA licence lists, Google Maps via Clay | "Add medical and roadside to your guarding contracts." MM | 10 to 25 | Medium | 7 |
| 14 | Creative Ideas (3 use cases) | Broad | Niche-specific play | Tier 2: no signal, fast build | Tier 1A and 1B base list. Champion | Website read by Claygent | "I had an idea for {{company}}": 3 use cases from their site. MM, TS | 50 to 100 | Low | 7 |
| 15 | Bank bancassurance and VAS | Niche | Niche-specific play | Tier 3: no Kenyan bank reference | Retail banks. Head of VAS, Bancassurance | CBK directory, product pages | "Give account holders emergency cover under the bank's brand." MM | 5 to 15 | Medium | 6 |
| 16 | Past-partner alumni | Niche | Lookalike of customers (warm path) | Tier 3: small, hard to find | Ex Old Mutual, SanlamAllianz, Glovo, Uber staff at target accounts | LinkedIn past employer via Clay | "You saw this work at {{past employer}}." Needs approval. MM | 5 to 15 | High | 6 |
| 17 | Telematics providers (Creative, non-ICP) | Niche | Niche-specific play | Tier 3: SA proof only | Vehicle tracking firms. Product head, COO | BuiltWith plus company lists via Clay | "Tracker turned emergency response into a value-added service." Needs approval. MM | 5 to 15 | Medium | 6 |
| 18 | Election 2027 duty of care | Focused | Niche-specific play | Tier 3: demand link not sourced | Corporates with field staff. People, HSE | Election countdown, news | Time-boxed security readiness message. MR | 20 to 40 | Low | 5 |
| 19 | Brokers as referrers (Creative, non-ICP) | Niche | Niche-specific play | Tier 3: brokers excluded as buyers in icp.md | Insurance brokers. Principal | IRA broker list | Referral angle only, no per-user buy. MM | 5 to 15 | Medium | 5 |

**Required types covered:**
- Creative Ideas: rank 14.
- New Hire: rank 5.
- Lookalike: ranks 9 and 12.
- Creative non-ICP: ranks 13, 17 and 19.
- Stretch: ranks 3, 10, 11 and 16.
- Golden ICP (what a rep would send after ten minutes of research): rank 1.

## Tier 1 overviews (copywriter handoff)

1. **Sister-line expansion.**
   - Hook: a named insurer line with rescue and a named line without.
   - Personalised: product page for each line.
   - Proof: Old Mutual extended beyond motor private.
   - CTA: a 20 minute call.
2. **Rider and driver safety.**
   - Hook: their rider or driver app plus a recent expansion or incident.
   - Proof: Glovo incident tracking. The "full transparency" quote is from AURA's own lead, not Glovo.
   - CTA: ask who owns rider safety today.
3. **Rescue.co consolidation.**
   - Hook: roadside is handled, and armed security and medical sit elsewhere.
   - Do not attack its ambulance numbers.
   - CTA: how the two services split today (Not found in research).
4. **Post-922 gap.**
   - Hook: 922 covers medical evacuation only.
   - Do not claim any 922 link. AURA's stance is Not found.
5. **New leader.**
   - Hook: new role, 90 day mandate.
   - Proof: Tracker "relatively easy to integrate".

## No-AI campaigns
- **Post-922 gap (rank 4), static.** One verifiable public fact, tight segment, no research needed. Message: 922 covers the patient only, we cover security, medical and roadside under your brand, worth 20 minutes?
- **Heavy rains (rank 8), static.** One sentence on the forecast, one on the emergency plan review AURA's Kenya lead recommended, one question.

## Front-end offers
All need AURA's approval. None promises price or response times.
1. **Coverage check:** map their user cities against AURA's stated footprint of 40+ cities and towns. Needs AURA's coverage data.
2. **Staging integration walkthrough:** 30 minutes on the Panic API and white-label app. Suits Influencers.
3. **Sample incident report:** a redacted audit trail and reporting view. Whether a shareable sample exists is Not found.

## Next
Rank 1 already has an approved spec at output/campaigns/sister-entity-insurer-expansion/workflow-spec.md. Next candidates by rank are 2 (rider safety), then 3 (Rescue.co consolidation). Run `/build-workflow-spec` on one at a time.
