# AURA ICP (Kenya focus)

Built only from `context/docs/research/` (sources checked 2026-11-13). Source tags show file and section. INFERRED = my link, no source states it. Open questions are listed at the end, not guessed.

## Who the ICP is

Kenyan businesses that have a base of customers, staff, drivers or riders and want to add security, medical and roadside response under their own brand. AURA sells embedded response through partners, not to individuals (company.md > What they sell).

## Layer 1: Firmographic

| Attribute | What the research supports | Source |
|---|---|---|
| Industry (proven in Kenya) | Insurers (Old Mutual, SanlamAllianz, ICEA Lion); ride-hailing and delivery platforms (Uber, Glovo); mobility and vehicle rental (Greenwheels) | customers.md > Named customers in Kenya |
| Industry (listed by AURA, no named Kenyan buyer) | Facility and property management, construction, alarm monitoring centres, telematics, security and guarding, consumer apps, handheld devices, employee wellness, medical insurer, ATM protection, financial services, lone worker | customers.md > Industries AURA targets; Not found list |
| Size | Not published. Named accounts are insurers and platforms (INFERRED mid to large) | customers.md > Company sizes |
| Geography | Kenya. AURA cites 40+ cities and towns and about 70% of major urban areas with full device tech. Nairobi and Mombasa were the launch cities | company.md > Markets and footprint |
| Business model | Has an end-user base to distribute to. Partner pays per user per month, and can offer the service free or as a paid value-added service | company.md > Pricing model |
| Brand control | Wants end users to see the partner's brand, not AURA's | company.md > What they sell |

### Segment tiers

| Tier | Segment | What the research supports | Gap or INFERRED | Source |
|---|---|---|---|---|
| 1A | Banks and multi-entity insurers (financial services) | Old Mutual launched on motor and its page now lists medical and SME health; Old Mutual said it would extend beyond motor. SanlamAllianz promotes Emergency Assist across motor, home, WIBA, SME and personal accident, and formed as a joint venture in 2025 with separate general and life CEOs. AURA lists financial services, medical insurer and ATM protection as industries | No Kenyan bank is named as a customer. INFERRED: retail banking and bancassurance bundling. INFERRED: sister-entity cross-sell from motor and general insurance into health, medical and SME lines, mirroring Old Mutual's motor-to-medical expansion. Insurance regulator rules on value-added services: Not found | customers.md > Named customers in Kenya, Not found; signals.md #1, #2, New leaders; market.md section 4; company.md > Products and services |
| 1B | Mobility, logistics, gig delivery and ride-hailing platforms | Uber (in-app emergency button), Glovo (rider cover, June 2026), Greenwheels. Rescue.co also targets drivers, fleets, insurers and businesses. AURA lists telematics as an industry | Logistics operators and fleets are not named AURA customers in Kenya (INFERRED fit). Contested: Glovo and ICEA Lion appear with both AURA and Rescue.co. The named accounts are existing AURA partners, so new targets must be lookalikes; a lookalike list is Not found | customers.md > Named customers in Kenya; competitors.md > Rescue.co; signals.md #3, #4 |
| 2 | Corporate employee wellness and lone-worker programmes | Both are listed on AURA's site as industries. IHS gives a testimonial on staff and premises security | No named Kenyan logo (customers.md says Not found). INFERRED: HR-led purchase | company.md > Products and services; customers.md > Testimonials, Not found |

Order reflects evidence, not size: insurers and gig platforms have named Kenyan proof; the bank half of Tier 1A and all of Tier 2 do not.


## Layer 2: Technographic

| Signal | Evidence | Source |
|---|---|---|
| Has or will build a customer app | SanlamAllianz Emergency Assist app; Uber in-app emergency button | customers.md > Named customers in Kenya |
| Can integrate by API or accept a white-label app | Panic API (customers, subscriptions, callouts, webhooks); white-label app; production needs AURA sign-off | company.md > Products and services |
| Runs vehicle tracking or telematics | Tracker is a telematics customer (South Africa); telematics is listed as an AURA industry | customers.md > Named case studies; company.md > Products and services |
| Runs a monitoring or control-room platform | DSOC integrated via Sentinel CMS (UK) | customers.md > Named case studies |
| Alarm or IoT devices | Property Protect is AURA's verified alarm response product; integrations can cover panic buttons and selected device or gateway flows | company.md > What they sell, Products and services |
| Kenyan prospects' actual tech stacks | Not found | n/a |

## Layer 3: Intent signals

| Signal | Status | Source |
|---|---|---|
| Insurer launches or widens a value-added emergency service (Old Mutual said it would extend beyond motor) | Observed | signals.md #1 |
| Insurer merger or joint venture (SanlamAllianz formed 2025) | Observed; need INFERRED | signals.md #2 |
| Gig or delivery platform adds rider safety (Glovo, June 2026) | Observed | signals.md #3 |
| Competitor wins a shared account (Glovo and ICEA Lion appear with both AURA and Rescue.co) | Observed | signals.md #4 |
| Private security regulation tightening (draft rules 25 Aug 2026, wage enforcement, firm closures) | Observed; effect on buyers INFERRED | signals.md #6, market.md section 3 |
| Public tender asks for verified security vendors (Kenya Railways, Oct 2026) | Observed | signals.md #7 |
| Heavy rains season | Observed | signals.md #9 |
| Election 2027 countdown | Observed; relevance INFERRED | signals.md #10 |
| Hiring, funding or new leaders at target accounts | Not found | signals.md > Hiring, Funding, New leaders |

## Layer 4: Persona

Three roles. Detail in `personas.md`.

| Role | Titles seen in research |
|---|---|
| Champion | Head of Operations, Operations Manager, Chief Operating Officer. Added (INFERRED, no research source names these roles): Head of Product, Head of Claims, Customer Care or Member Experience Lead, Head of VAS or Bancassurance, HR Director or Head of People and Culture |
| Economic buyer | CEO, Managing Director. Added (INFERRED): Chief Financial Officer, Chief Operating Officer, Chief Human Resources Officer |
| Influencer | Senior Manager, Security Operations; integration owner (title Not found). Added (INFERRED): Chief Innovation Officer or Head of Innovation, Head of Legal, CTO or Head of Engineering, Chief Risk Officer |

## Layer 5: Engagement readiness

| Readiness test | Evidence | Source |
|---|---|---|
| Accepts that response times are not guaranteed | AURA's terms say availability depends on responders in the area | company.md > Products and services |
| Can run a staging integration then go live with AURA sign-off | Docs say production access needs AURA sign-off after staging tests | company.md > Products and services |
| Users sit in covered urban areas | About 70% of major urban areas fully equipped | company.md > Markets and footprint |
| Decides free versus paid value-added service | Both are supported | company.md > Pricing model |
| Open to a demo or partner call | AURA's calls to action are "book a demo" and join the network | voice.md > Headlines and taglines |
| Needs claims evidence (audit trail, reporting) | An OUTsurance testimonial says AURA gave it a portal with a full audit trail and customised reporting. Photo or video capture: Not found | customers.md > Testimonials; open question below |
| Preferred outreach channel, buying cycle, budget owner | Not found | n/a |

## Not a fit

| Who | Why | Source |
|---|---|---|
| Individual consumers | AURA sends individuals to an AURA-powered partner | company.md > What they sell |
| Buyers who need a guaranteed response time | Terms do not guarantee times | company.md > Products and services |
| Buyers whose users are mainly outside covered areas | Coverage claims cover major urban areas; rural coverage Not found (fit INFERRED) | company.md > Markets and footprint |
| Security or ambulance firms as buyers | They are the supply side. Route to network onboarding | customers.md > Kenya response network |
| Unlicensed security firms | AURA requires PSRA accreditation, a security licence and public liability cover | company.md > Markets and footprint |
| Accounts in South Africa, the UK or the US | Out of scope for this Kenya ICP | company.md > Markets and footprint |

Unproven, not excluded: fintech, banking, ATM, employee wellness and lone-worker buyers in Kenya. AURA lists them, but no named Kenyan customer was found.

## Open questions

- Price per user, and any minimum volume or fee for API access.
- Size thresholds for a viable account.
- How AURA positions against the 922 line (no public mention found; market.md and competitors.md flag it).
- Which accounts use both AURA and Rescue.co, and how they split work.
- Kenya data-protection rules for location and health data.
- Who owns the budget and how long a deal takes.
- Whether AURA's responder app supports photo/video media capture for claims evidence (full audit trail and customised reporting are verified in customers.md).
- Whether the added titles (Head of Claims, Head of VAS or Bancassurance, CFO, CHRO, CRO, Head of Legal and others) exist and hold a say at Kenyan accounts. No research file names them.
- Whether any Kenyan bank or corporate wellness programme already uses AURA (customers.md says Not found).
- Whether fleets and logistics operators in Kenya are served by AURA today.
