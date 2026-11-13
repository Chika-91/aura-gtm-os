# Workflow Spec: Multi-Entity Insurer & Bancassurance Sister-Line Expansion (`W1`)

**Status:** STRUCTURE-APPROVED 2026-11-13 · copy pending
## 0. Candidate Workflow Selection & Strategic Overrides

Three candidate workflows were evaluated from `context/icp/signal-matrix.md` before locking **W1**:

1. **W1 (Selected) - Multi-Entity Insurer & Bancassurance Sister-Line Expansion (`Signal S1`, Score: 18/20):**
   - **Mother Intent:** *New product launches* / *Website content mentions*.
   - **Target Segment & Personas:** Tier 1A Kenyan insurers and retail banks/bancassurance groups, targeting Divisional Insurance Champions (**Head of Medical Insurance**, **Head of General Insurance**, **Head of Life Insurance**, **Head of Claims**, **Customer Care Lead**, **Head of Product**, **Head of VAS/Bancassurance**), Economic Buyers (**Managing Director**, **CEO**, **CFO**), and Influencers (**Chief Innovation Officer**, **Head of Legal**, **CTO**, **CRO**).
   - **Data Source & Volume:** IRA and CBK licensed directories plus insurer/bank product pages scraped via **Crawl4AI / Apify + Clay** (`15-30` accounts/month, `INFERRED`, **Low-Medium** difficulty).
   - **Why Selected:** Highest Kenyan social proof (`Old Mutual`, `SanlamAllianz`, `ICEA Lion`), low-friction API embedding across existing policyholder bases, and clear exclusion of **Insurance Brokers**.

2. **W2 - Mobility & Logistics Geographic Expansion, Security Incident & Partnership Play (`Signal S2`, Score: 18/20):**
   - **Mother Intent:** *Companies in hypergrowth (hiring velocity)* / *Niche-specific play*.
   - **Strategic Override:** Refined from generic website text mentions to detect **new Kenyan town expansion**, **security or road-incident press** (where combined armed security + medical + roadside rescue protects riders and cargo), and **fleet/payment/telematics partnerships** (`40-80` accounts/month, `INFERRED`, **Medium** difficulty).

3. **W3 - Roadside-Only Competitor Security Consolidation Wedge (`Signal S3`, Score: 17/20):**
   - **Mother Intent:** *Competitor customers (compound)*.
   - **Scope & Volume:** Targets publicly identifiable Rescue.co accounts missing private armed security dispatch (`10-25` accounts/month, `INFERRED`, **Low** difficulty).

> Built with `build-workflow-spec` from `context/icp/icp.md`, `context/icp/personas.md`, `context/icp/signal-matrix.md`, `context/docs/gtm-system.md`, and `context/docs/research/`. Every claim traces to verified research or is marked `INFERRED`. Zero copy is written in this file.

---

## 1. Mother Intent (Trigger) `[ENGINE]`
- **Catalog Match (`workflow-anatomy.md`):** **New product launches** / **Website content mentions** (paired with **Competitor customers** as a routing layer).
- **Trigger Statement:** A licensed Kenyan multi-entity insurer or retail bank/bancassurance group already operates a motor or general rescue product and promotes or expands medical, health, life, SME, or digital banking lines without unified armed security, medical, and roadside dispatch (`signals.md`, `icp.md`, `competitors.md`).

---

## 2. Inclusion / Exclusion `[ICP]`
- **Include (`[ICP]`):**
  - **Geography & Market:** Kenya (operating across Nairobi, Mombasa, and 40+ Kenyan towns where AURA cites urban coverage; `company.md`, `icp.md`).
  - **Industry & Size:** Mid-to-large licensed Kenyan multi-entity/composite insurance groups (General, Medical/Health, Life) and licensed retail banks / bancassurance subsidiaries (`icp.md`, `customers.md`).
  - **Trigger Condition:** Publicly offers a motor/general rescue product or digital banking/policyholder portal, and operates at least one unserved sister division (Medical/Health, Life, SME, or Retail Banking/Bancassurance) (`signals.md`, `icp.md`).
  - **Recipients (`personas.md`):**
    - *Primary Champions:* **Head of Medical / Health Insurance**, **Head of General Insurance**, **Head of Life Insurance**, **Head of Claims**, **Customer Care / Member Experience Lead**, **Head of Product**, and **Head of VAS / Bancassurance** (focused on life-saving speed, loss/claims fraud reduction via full audit trails, and eliminating manual phone-chasing logistical overhead for emergency care teams).
    - *Economic Buyers:* **Managing Director (Medical / General / Life Entity)**, **Group CEO**, and **CFO**.
    - *Influencers:* **Chief Innovation Officer / Head of Innovation**, **Head of Legal**, **CTO / Head of Engineering**, and **Chief Risk Officer**.
- **Exclude:**
  - **Insurance brokers and independent agents:** Brokers do not own the underlying policyholder relationship or underwriting balance sheet, making per-user monthly API fees and technical integration unviable (`INFERRED`).
  - **Active Kenyan AURA divisions already live:** Specific business lines already contracted with AURA (e.g., **Old Mutual General Insurance**, **SanlamAllianz General Insurance**, **ICEA Lion** motor lines where active), while keeping unserved sister divisions eligible (`customers.md`, `signals.md`).
  - **Out-of-scope profiles:** Individual retail consumers (D2C), standalone SMBs, unlicensed security/medical vendors, and non-Kenyan entities (`icp.md`).

---

## 3. Sources `[ENGINE]`
- **Account Universe & Regulatory Lists:** Insurance Regulatory Authority (IRA) Kenya licensed insurer directory and Central Bank of Kenya (CBK) licensed commercial bank directory scraped via **Crawl4AI (`tools/crawl4ai`) / Apify** into **Clay** (`gtm-system.md`).
- **Trigger & Competitor Scrape:** Insurer/bank divisional product pages, press releases, and Rescue.co partner pages scraped via **Crawl4AI (`tools/crawl4ai`) / Apify** with keyword/regex extraction in **Clay** (`signals.md`, `competitors.md`).
- **People & Contact Verification:** **Clay "Find People" + Apollo / LinkedIn Sales Navigator** for divisional titles, followed by **Clay Email Waterfall (Prospeo, Apollo, LeadMagic, ZeroBounce)** and **HubSpot CRM** deduplication (`gtm-system.md`).

---

## 4. Signals Table `[ENGINE]`

| # | Signal | Role | How it's read (boolean / count / regex) | Output |
|---|---|---|---|---|
| **1** | `has_sister_entity_expansion` | `trigger` | Regex/keyword match on insurer/bank product pages & press for active motor/general rescue PLUS active Medical/Health, Life, SME, or Bancassurance divisions (`boolean`) | `true` / `false` (fires workflow when `true`) |
| **2** | `existing_assistance_provider` | `router` | Keyword/regex match on scraped product pages & press for `"Rescue.co"` / `"Flare"`, internal motor rescue (`"OM Rescue"`, `"Emergency Assist"`), or no emergency partner mentioned (`enum`) | `rescue_co_roadside` / `internal_motor_only` / `none_detected` |
| **3** | `target_division_role` | `router` | Regex match on contact job title from Apollo/LinkedIn (`Medical|Health`, `General|Motor`, `Life`, `Claims|Care`, `Bancassurance|VAS|Product`) (`enum`) | `medical_health` / `general_life` / `claims_care` / `bancassurance_vas` |
| **4** | `has_mobile_customer_app` | `context-clause` | Google Play / App Store package check or website app link match (`boolean` - never routes; adds 1 line of API/white-label color) | `true` / `false` |
| **5** | `post_922_macro_context` | `context-clause` | Static Kenya market flag (August 2026 national 922 medical-only ambulance launch; `boolean` - never routes) | `true` (highlights armed security + roadside + audit trail gap) |

---

## 5. Routing & Angle Matrix `[ENGINE]`
- **Axis 1 (`existing_assistance_provider`):** `3` values (`rescue_co_roadside`, `internal_motor_only`, `none_detected`).
- **Axis 2 (`target_division_role`):** `4` values (`medical_health`, `general_life`, `claims_care`, `bancassurance_vas`).
- **Combined Matrix:** `3 x 4 = 12` stacked cells.

| Cell | Deterministic Read (`provider` x `division_role`) | What It Tells Us (Inferred Situation) | The Angle It Earns (Meaning Only - No Copy) |
|---|---|---|---|
| **C1** | `rescue_co_roadside` x `medical_health` | Insurer pays Rescue.co for roadside/medical evacuation on motor, leaving medical policyholders without private armed security or unified white-label dispatch (`competitors.md`, `INFERRED`). | Consolidate medical and personal safety under the insurer's own brand with PSRA-vetted armed security and medical response in one API, filling what roadside-only vendors and Kenya's 922 medical-only line leave uncovered. |
| **C2** | `rescue_co_roadside` x `general_life` | General/Life division uses a roadside-only vendor for vehicle breakdowns, leaving personal safety and life-event emergency protection unaddressed (`competitors.md`, `INFERRED`). | Upgrade general and life policies from breakdown-only assistance to full 24/7 personal armed security, medical, and roadside protection under one white-label partner without managing separate vendors. |
| **C3** | `rescue_co_roadside` x `claims_care` | Claims and Care teams deal with fragmented roadside dispatch logs and manual follow-ups when incidents escalate beyond a tow (`customers.md`, `INFERRED`). | Eliminate manual phone-chasing overhead for emergency care teams and give Claims a single customer-facing portal with a full incident audit trail and customised reporting to verify scenes and curb claims leakage. |
| **C4** | `rescue_co_roadside` x `bancassurance_vas` | Bank or composite insurer bundles roadside-only perks into select tiers but lacks a unified multi-hazard safety product across retail accounts and SMEs (`competitors.md`, `INFERRED`). | Embed white-label armed security, medical, and roadside response across retail banking and bancassurance tiers via one API, turning the bank or insurer app into an everyday safety network. |
| **C5** | `internal_motor_only` x `medical_health` | Group already runs motor rescue on its general arm (mirroring Old Mutual's motor launch) and can cross-sell into its sister Medical/Health entity (`signals.md`, `INFERRED`). | Replicate the group's motor assistance success inside the Medical/Health division with zero control-room capex, giving members faster Nairobi ambulance/security dispatch and relieving care desks from manual responder coordination. |
| **C6** | `internal_motor_only` x `general_life` | General division has basic motor rescue, while Life or non-motor general lines lack tangible everyday living benefits for policyholders (`signals.md`, `INFERRED`). | Turn Life and non-motor general policies from passive annual payouts into everyday tangible protection with white-label personal safety and medical response across 40+ Kenyan towns. |
| **C7** | `internal_motor_only` x `claims_care` | General motor desk handles emergency calls manually, creating heavy logistical phone-chasing overhead and inconsistent incident records for Claims (`customers.md`, `INFERRED`). | Offload manual emergency call-chasing from internal care teams to automated 24/7 dispatch while equipping Claims with real-time incident visibility and auditable reporting across divisions. |
| **C8** | `internal_motor_only` x `bancassurance_vas` | Insurer group has proven motor rescue on one line and now wants a packaged value-added service for bancassurance or digital distribution (`signals.md`, `INFERRED`). | Package white-label security, medical, and roadside protection as a low-friction bancassurance add-on using existing API/white-label architecture ("relatively easy to integrate"). |

| **C9** | `none_detected` x `medical_health` | Medical/Health insurer has no public embedded emergency response partner, relying on member reimbursements or public 922 evacuation (`market.md`, `INFERRED`). | Differentiate medical plans in a price-driven market by embedding 24/7 private medical and armed security response under the insurer's own brand, delivering faster care than 20 to 60 minute public delays without building a dispatch network. |
| **C10** | `none_detected` x `general_life` | General or Life insurer offers traditional cover without real-time emergency response, competing mainly on price (`customers.md`, `INFERRED`). | Stand out beyond price in Kenyan general and life insurance by embedding white-label security, medical, and roadside protection with predictable per-user monthly unit economics. |
| **C11** | `none_detected` x `claims_care` | Claims and Customer Care teams handle post-incident reports reactively with no live scene visibility or automated dispatch (`customers.md`, `INFERRED`). | Shift Claims and Care from reactive post-incident paperwork to real-time emergency intervention with a full digital audit trail that lowers claim severity and lightens care-team phone overhead. |
| **C12** | `none_detected` x `bancassurance_vas` | Retail bank or bancassurance unit has digital customer distribution but no embedded emergency protection tier (`icp.md`, `INFERRED`). | Launch a differentiated white-label emergency protection tier across retail banking/bancassurance accounts via API or turnkey white-label app without building dispatch infrastructure from scratch. |

---

## 6. Variables Contract `[ENGINE]`

| Variable | Source Field | Exists in Branches |
|---|---|---|
| `{{first_name}}` | `apollo_contact.first_name` | All (`C1` - `C12`) |
| `{{company_name}}` | `clay_account.company_name` | All (`C1` - `C12`) |
| `{{division_name}}` | `clay_contact.inferred_division` (`Medical`, `General`, `Life`, `Claims & Care`, `Bancassurance`) | All (`C1` - `C12`) |
| `{{existing_rescue_program}}` | `crawl4ai_scrape.rescue_program_name` | `C1` - `C8` only (never referenced in `C9` - `C12`) |
| `{{sister_line_detected}}` | `crawl4ai_scrape.sister_division_url_title` | All (`C1` - `C12`) |
| `{{app_platform_clause}}` | `play_store_check.context_clause` | Only when `has_mobile_customer_app = true` |
| `{{macro_922_context}}` | `static_flag.post_922_clause` | All (`C1` - `C12`) |

---

## 7. Cadence & Channel `[ENGINE]`
- **Periodicity:** Always-on weekly trigger scan (Monday morning Crawl4AI/Apify refresh + Clay enrichment) paired with quarterly IRA/CBK directory sweeps (`gtm-system.md`).
- **Channels & Touch Cadence:** Multi-channel **Email (`Smartlead` / `Instantly`) + LinkedIn (`HeyReach`)**, **4 touches over 10 business days** (`Day 1`: Signal-anchored email -> `Day 3`: LinkedIn connection/note -> `Day 6`: Role-specific value follow-up [audit trail and care-team phone overhead for Claims & Care; sister-line differentiation for Division Heads] -> `Day 10`: Low-friction demo/scoping close).

