# End-to-End Outbound GTM System: AURA Kenya

> Designed from `context/icp/icp.md`, `context/icp/personas.md`, `context/icp/signal-matrix.md`, and `context/docs/research/`. Modelled on the Reliance HMO end-to-end architecture and verified against the four GTM system pillars. Checked 2026-11-13.

---

## Visual System Flow (Node-by-Node Architecture)

```text
[1A Context OS (GitHub / CLAUDE.md)]
        │
        ▼
[1B Buying Signals: S1 Sister-Entity, S2 Rider Safety, S3 Rescue.co Overlap, S4 New Leader]
        │
        ▼
[1C Find Companies: Clay + Apify / IRA & CBK Lists]
        │
        ▼
[1D Enrich Company: Clay + Crawl4AI / Website & App Check]
        │
        ▼
   <1E ICP Fit?> ── No ──► [Drop / Log Exclusion in Clay]
        │ Yes
        ▼
   <1F Segment?>
   ├── Tier 1A: Banks & Multi-Entity Insurers ──► [1G Sister-Entity / Bancassurance Track]
   ├── Tier 1B: Mobility, Logistics & Gig ──────► [1H Rider & Fleet Safety Track]
   └── Tier 2: Corporate Employee Wellness ─────► [1I Duty-of-Care Track]
        │
        ▼
   <1J Existing Assistance Provider? (from Site / Press / Rescue.co List)>
   ├── Names Rescue.co (Roadside-Only) ──────────► [2A Security + Unified API Consolidation Angle]
   ├── Has Motor/General Rescue Only (Insurer) ──► [2B Sister-Entity Cross-Sell Angle (Health/SME/Bank)]
   └── No Emergency Provider Mentioned ──────────► [2C First-Time White-Label Launch Angle (Post-922 Gap)]
        │
        ▼
[2D Find People: Clay "Find People" + Apollo / LinkedIn Sales Nav (Champion, Economic Buyer, Influencer)]
        │
        ▼
[2E Find & Verify Email: Clay Waterfall (Prospeo / Apollo / LeadMagic / ZeroBounce)]
        │
        ▼
   <2F Email Valid?> ── No ──► [Fallback: LinkedIn DM / Connection Sequence via HeyReach or Expandi]
        │ Yes
        ▼
   <2G Already Active in CRM (HubSpot)?> ── Yes ──► [Exclude / Suppress Duplicate Outreach]
        │ No
        ▼
[2H Personalise Opener: Claygent reads Signal + Angle + Personas -> writes 1-line hook]
        │
        ▼
[3A Multi-Channel Sequence: Smartlead / Instantly (Email) + HeyReach (LinkedIn), 3-4 touches over 10 days]
        │
        ▼
[3B Reply Handling: n8n + LLM Intent Classifier]
   ├── Interested / Demo Request ──────► [Create Deal in HubSpot + Slack Alert to AURA Kenya BD]
   ├── Future Budget / Renewal Date ───► [Create HubSpot Task 60 Days Prior + Re-queue at 1B]
   ├── Wrong Person / Referral ────────► [Route Back to 2D with Referred Contact Name]
   ├── Unsubscribe / Not Relevant ─────► [Global Suppression List in HubSpot + Smartlead + Clay]
   └── No Reply After Sequence ────────► [Cool-Down 60 Days -> Re-enter at 1B on Next Signal]
        │
        ▼
[3C CRM Pipeline (HubSpot): Meeting Booked -> API/Staging Scoping -> Pilot Proposal -> Live Partner]
        │
        ▼
[3D Weekly Feedback Loop (Friday Review -> Updates 1A Context OS & work-log/2026-W46.md)]
```

---

## Step-by-Step Specification (Tools, Actions & Decision Branches)

| Step | Stage Name | What Happens | Tool(s) | Decision & Where Each Answer Leads |
|---|---|---|---|---|
| **1A** | **Context OS** | Reads `CLAUDE.md`, `icp.md`, `personas.md`, `signal-matrix.md`, and `voice.md` to enforce Kenya ICP rules, compliance caveats (no guaranteed response times), and zero-em-dash style. | **GitHub + Claude Code / VS Code (`CLAUDE.md`)** | Feeds approved segments, persona titles, and message angles into **1B** and **2H**. |
| **1B** | **Buying Signals** | Always-on monitors detect priority triggers: **S1** (sister-entity expansion after motor rescue), **S2** (rider/fleet road safety pressure), **S3** (Rescue.co roadside-only overlap), **S4** (new Product/Claims/VAS/Ops/HR leader in 90-180 days), plus compound triggers **S7** (post-922 security/roadside gap) and **S8** (heavy rains). | **Crawl4AI (`tools/crawl4ai`), Apify, n8n (`tools/n8n`), Clay** | Detected signal + company domain passes to **1C** (or directly to **1D** if account is already known). |
| **1C** | **Find Companies** | Pulls net-new Kenyan lookalike accounts matching Tier 1A (IRA-licensed insurers, CBK-licensed banks), Tier 1B (delivery, ride-hailing, logistics, fleet apps), and Tier 2 (mid-to-large corporates). | **Clay ("Find Companies") + Apify / Kenyan Directories** | Raw company list passes to **1D** for firmographic and technographic enrichment. |
| **1D** | **Enrich Company** | Enriches Kenya headcount, urban presence (Nairobi/Mombasa/40+ towns), mobile app availability, existing rescue/roadside partners, and PSRA/compliance context. | **Clay Enrich + Crawl4AI (`tools/crawl4ai`)** | Enriched account record moves to decision gate **1E**. |
| **1E** | **ICP Fit Check** | Evaluates enriched company against `icp.md` criteria (enterprise/mid-to-large B2B2C base, urban coverage fit, non-SMB, non-D2C, non-unlicensed vendor). | **Clay Formula / AI Gate** | **Yes:** Proceed to **1F**. **No:** Drop and tag exclusion reason in Clay (`Not a Fit`). |
| **1F** | **Routing by Segment** | Routes qualified Kenyan accounts into their specific vertical track based on industry and user base type. | **Clay Router** | **Tier 1A (Banks & Insurers):** Route to **1G**. **Tier 1B (Mobility, Logistics & Gig):** Route to **1H**. **Tier 2 (Corporate Wellness):** Route to **1I**. |
| **1G-1I** | **Sub-Segment Track** | Assigns segment-specific proof points: **1G** (Old Mutual/SanlamAllianz proof, bancassurance/sister-entity bundling), **1H** (Glovo/Uber proof, live GPS rider tracking), **1I** (duty-of-care & PSRA-vetted staff safety). | **Clay** | All three tracks proceed to provider check **1J**. |
| **1J** | **Current Provider Check** | Checks scraped site/press data for existing emergency or roadside partners (such as Rescue.co or internal motor rescue). | **Clay + Crawl4AI** | **Names Rescue.co (roadside-only):** Route to **2A** (Security + unified API consolidation angle). **Has motor rescue only:** Route to **2B** (Sister-entity cross-sell to health/SME/banking). **No provider mentioned:** Route to **2C** (First-time white-label launch angle beyond 922 medical-only scope). |
| **2D** | **Find People** | Identifies 2 to 3 buying-committee contacts per account from `personas.md`: **Champion** (Head of Product, Claims, Care, VAS, Ops, or HR), **Economic Buyer** (CFO, CEO/MD, COO, CHRO), and **Influencer** (Chief Innovation Officer, Head of Legal, CTO, CRO). | **Clay ("Find People") + Apollo / LinkedIn Sales Navigator** | Matched contacts with LinkedIn URLs and titles move to **2E**. |
| **2E** | **Find & Verify Emails** | Runs multi-provider email enrichment and SMTP verification waterfall for each matched contact. | **Clay Waterfall (Prospeo, Apollo, LeadMagic, ZeroBounce)** | Passes verification status to decision gate **2F**. |
| **2F** | **Email Valid Check** | Checks whether a verified, deliverable corporate email was found. | **Clay Conditional Gate** | **Yes:** Proceed to CRM deduplication check **2G**. **No:** Route contact to **LinkedIn-only DM sequence** (skipping email in **3A**). |
| **2G** | **CRM Deduplication Check** | Queries CRM to check if the account or contact is already an active AURA partner (e.g., Old Mutual, SanlamAllianz, ICEA Lion, Uber, Glovo, Greenwheels), open deal, or suppressed contact. | **HubSpot CRM Lookup via Clay** | **Yes (Already in CRM/Active):** Exclude/suppress to prevent channel conflict. **No (Net-New / Unserved Sister Entity):** Proceed to **2H**. |
| **2H** | **Personalise Opener** | AI agent reads the exact signal (**1B**), angle (**2A/2B/2C**), and persona role (**2D**) to generate a concise, compliant opening line (no unverified ROI claims or guaranteed response times). | **Claygent (LLM Enrichment in Clay)** | Populates custom fields (`opener`, `signal_ref`, `angle_tag`) and pushes lead to **3A**. |
| **3A** | **Outbound Sequence** | Executes coordinated 3-to-4-touch sequence over 10 business days tailored by persona (Champion = operational visibility & claims audit trail; CFO/MD = predictable per-user economics; Legal/CTO = PSRA compliance & API ease). | **Smartlead / Instantly (Email) + HeyReach (LinkedIn)** | Sends outreach and streams all replies/bounces to **3B**. |
| **3B** | **Reply Handling** | Automatically classifies reply intent and triggers the exact next action without manual triage lag. | **n8n (`tools/n8n`) + LLM Classifier + Slack** | **Interested:** Create deal in HubSpot (**3C**) + instant Slack alert to Kenya BD. **Future Renewal/Budget:** Create HubSpot task 60 days prior + re-queue at **1B**. **Wrong Person:** Extract referred name and loop back to **2D**. **Unsubscribe:** Suppress across HubSpot, Smartlead, and Clay. **No Reply:** 60-day cool-down, then re-enter **1B** on next signal. |
| **3C** | **CRM Pipeline** | Tracks enterprise B2B2C deal progression: `Meeting Booked` -> `Discovery & Use-Case Scoping` -> `Aura Panic API / Staging Sandbox Review` -> `Commercial & Legal Sign-Off` -> `Live Partner`. | **HubSpot CRM** | Logs win/loss reasons, actual deal cycle length, and persona engagement for **3D**. |
| **3D** | **Weekly Feedback Loop** | Every Friday, exports reply rates, meeting rates, objection patterns, and win/loss data by signal (`S1-S8`), segment (`Tier 1A/1B/2`), and persona (`Champion/EB/Influencer`) back into the Context OS. | **n8n + Google Sheets / Notion + GitHub (`work-log/2026-W46.md`, `icp.md`, `personas.md`, `signal-matrix.md`)** | Updates signal weights, adds real Kenyan buyer quotes to `personas.md`, resolves Open Questions in `icp.md`, and updates **1A Context OS** for Monday's run. |

---

## Four-Pillar Architecture Audit (Slide 10 Checklist)

| Pillar | How AURA Kenya's GTM System Satisfies It |
|---|---|
