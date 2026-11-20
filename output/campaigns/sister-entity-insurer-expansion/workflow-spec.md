# Workflow Spec: Multi-Entity Insurer & Bancassurance Sister-Line Expansion (`W1`)

**Status:** STRUCTURE-APPROVED 2026-11-13 · amended and re-approved 2026-11-20 (5-touch cadence, `{{social_proof}}`, C9 angle) · COPY-APPROVED 2026-11-20 (E1, DM1, E2, DM2, E3) · amended and re-approved 2026-11-20 for Clay readiness (Step 1 review: ICP filter numbers, Clay-reachable sources, trigger fix, role routing, qualification checks, variables contract, single-pass cadence)

## 0. Candidate Workflow Selection & Strategic Overrides

Three candidate workflows were evaluated from `context/icp/signal-matrix.md` before locking **W1**:

1. **W1 (Selected) - Multi-Entity Insurer & Bancassurance Sister-Line Expansion (`Signal S1`, Score: 18/20):**
   - **Mother Intent:** *New product launches* / *Website content mentions*.
   - **Target Segment & Personas:** Tier 1A Kenyan insurers and retail banks/bancassurance groups, targeting Divisional Insurance Champions (**Head of Medical Insurance**, **Head of General Insurance**, **Head of Life Insurance**, **Head of Claims**, **Customer Care Lead**, **Head of Product**, **Head of VAS/Bancassurance**), Economic Buyers (**Managing Director**, **CEO**, **CFO**), and Influencers (**Chief Innovation Officer**, **Head of Legal**, **CTO**, **CRO**).
   - **Data Source & Volume:** IRA and CBK licensed lists (imported as CSV) plus insurer/bank product pages read in **Clay** (website scrape feeding Use AI columns) (`15-30` accounts/month, `INFERRED`, **Low-Medium** difficulty).
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
- **Trigger Statement:** A licensed Kenyan multi-entity insurer or retail bank/bancassurance group runs or promotes a sister division (medical, health, life, SME, or digital banking/bancassurance lines). Whether it already has a motor or general rescue product, and who provides it, is read separately by `existing_assistance_provider` and routes the angle; it is not part of the trigger (amended 2026-11-20, so cells C9 to C12 can fire). This is a state, not a dated launch: the scan is a single pass for this build and has no launch-date field (`signals.md`, `icp.md`, `competitors.md`).

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
  - **Recipients in this Clay build (amended 2026-11-20):** champion titles only. The copy routes on division role alone, so Economic Buyer and Influencer titles have no copy lines and are not searched in this build. A title that matches no champion role is `unmatched` and held.
- **Exclude:**
  - **Insurance brokers and independent agents:** Brokers do not own the underlying policyholder relationship or underwriting balance sheet, making per-user monthly API fees and technical integration unviable (`INFERRED`). Detected from the IRA licence category in the imported list; where the category is missing, an AI check on the website decides, with an evidence field (amended 2026-11-20).
  - **Active Kenyan AURA divisions already live:** Specific business lines already contracted with AURA (e.g., **Old Mutual General Insurance**, **SanlamAllianz General Insurance**, **ICEA Lion** motor lines where active), while keeping unserved sister divisions eligible (`customers.md`, `signals.md`). **Handled as a flag, not a domain exclusion (amended 2026-11-20):** a domain match would drop the whole group, so these accounts sit in the Exclusions table with Type = `existing_aura_partner`; the `existing_aura_partner` check holds those rows for manual review of which division is live. Domains come from `customers.md`; leave a domain blank rather than guess it.
  - **Out-of-scope profiles:** Individual retail consumers (D2C), standalone SMBs, unlicensed security/medical vendors, and non-Kenyan entities (`icp.md`).


### Clay search filters (added 2026-11-20)

Starting values for the free Clay search. Read the count before importing, record it in the work log and adjust (build step 4).

- **Find Companies:** Country = Kenya. Any Kenyan office qualifies, including groups headquartered in South Africa (owner decision 2026-11-20). Industry = insurance (insurer track) and banking (CBK track), as two segments. Employees = 51 to 5,000 (`INFERRED` starting band for "mid-to-large"; confirm against the real count). Exclude the domains in the Exclusions table.
- **Imported lists:** IRA licensed insurers and CBK licensed banks as a CSV with Company Name, Domain, Company Type (`insurer` or `bank`) and the IRA or CBK category. Domains left blank rather than guessed.
- **Find People:** Country = Kenya. Job title contains any of: Medical, Health, General Insurance, Motor, Life, Claims, Customer Care, Member Experience, Product, VAS, Value Added, Bancassurance. Head, director or manager level. Up to 3 people per company.
- **Test size:** import 25 to 50 rows first with auto-run off; the target is at least 20 fully enriched rows.
- **Volume:** `15-30` qualifying accounts a month (`INFERRED`); replace with the real search count once read.

---

## 3. Sources `[ENGINE]`
Every source below is reachable from Clay (amended 2026-11-20). Local tools such as Crawl4AI cannot be called from Clay; if used, they run outside Clay and the output is imported as a CSV.

- **Account Universe & Regulatory Lists:** Insurance Regulatory Authority (IRA) Kenya licensed insurer list and Central Bank of Kenya (CBK) licensed bank list, imported into **Clay** as a CSV (optionally gathered outside Clay with **Crawl4AI (`tools/crawl4ai`) / Apify**), alongside the free **Find Companies** search (`gtm-system.md`).
- **Trigger & Competitor Read:** each company's website content from Clay's website scrape (or a Claygent step where the scrape is blocked), read by Use AI columns for the sister-division and existing-provider signals, and by a formula for app links (`signals.md`, `competitors.md`).
- **People & Contact Verification:** **Clay "Find People"** for the champion titles, followed by the **Clay email waterfall (about four providers, validation on and strict)**. HubSpot deduplication only if the HubSpot integration is connected in Clay; the Exclusions table covers existing customers either way (`gtm-system.md`).

---

## 4. Signals Table `[ENGINE]`
Every data source below can be reached from Clay: a search filter, an enrichment, a Use AI column or a formula (amended 2026-11-20).

| # | Signal | Role | How it's read in Clay | Output |
|---|---|---|---|---|
| **1** | `has_sister_division` | `trigger` | **Use AI** column on the website content from the Clay website scrape. Asks which sister divisions (medical or health, life, SME, bancassurance or digital banking) the company runs or promotes. JSON: `has_sister_division` (`yes` / `no` / `unclear`), `sister_line_name` (a clean line name, not a page title), `evidence`. Run condition: Pass is true. Prove on 2 to 3 rows first. | `true` when yes (fires the workflow), `false` when no, `unclear` is held for manual review |
| **2** | `existing_assistance_provider` | `router` | **Use AI** column on the same scraped content. Looks for Rescue.co or Flare, an internal motor or general rescue program, or no emergency partner. JSON: `provider` (`rescue_co_roadside` / `internal_motor_only` / `none_detected` / `unclear`), `program_name` (the program's own name, blank if none), `evidence`. `unclear` when the scrape is empty or fails, so a failed scrape is never read as `none_detected`. | `rescue_co_roadside` / `internal_motor_only` / `none_detected`; `unclear` is held |
| **3** | `target_division_role` | `router` | **Formula** on the contact's job title (case-insensitive, whole words), first match wins in this order: (1) Claims, Customer Care, Member Experience or Customer Experience gives `claims_care`; (2) Medical or Health gives `medical_health`; (3) Bancassurance, VAS or Value Added gives `bancassurance_vas`; (4) Product gives `bancassurance_vas` when `company_type` is `bank`, otherwise `general_life`; (5) General, Motor or Life gives `general_life`. No match gives `unmatched`. A companion `division_name` formula returns `Medical`, `General`, `Life`, `Claims & Care` or `Bancassurance` from the same match. | `medical_health` / `general_life` / `claims_care` / `bancassurance_vas`; `unmatched` is held |
| **4** | `has_mobile_customer_app` | `context-clause` | **Formula** on the scraped homepage HTML: true when it contains a link to `play.google.com` or `apps.apple.com`. Check 3 rows by hand that the app is customer-facing. Never routes; adds one line of API or white-label colour. | `true` / `false` |
| **5** | `post_922_macro_context` | `context-clause` | **Formula** returning the constant text of `{{macro_922_context}}` (August 2026 national 922 medical-only ambulance launch). Never routes. | The same text on every row |

### Qualification checks (free formulas and lookups, not signals; added 2026-11-20)

| Check | How it's read in Clay | Result |
|---|---|---|
| `is_licensed_insurer_or_bank` | Lookup on domain against the imported IRA and CBK list. The licence category excludes brokers and agents. Where the category is missing, a Use AI check on the website decides, with an evidence field. | `true` / `false` |
| `size_in_band` | Formula on the Clay company headcount against the band in the section 2 filters. | `true` / `false` |
| `has_domain` | Domain column not blank, URL type. | `true` / `false` |
| `existing_aura_partner` | Lookup on domain against the `existing_aura_partner` rows in the Exclusions table. | `true` / `false` |

`Pass` is true when `is_licensed_insurer_or_bank`, `size_in_band` and `has_domain` are all true. `Ready to Contact?` is true only when `Pass` is true, Signal 1 is `true`, Signal 2 is not `unclear`, Signal 3 is not `unmatched` and `existing_aura_partner` is false. A true `existing_aura_partner` holds the row; it does not drop it.

---

## 5. Routing & Angle Matrix `[ENGINE]`
- **Axis 1 (`existing_assistance_provider`):** `3` values (`rescue_co_roadside`, `internal_motor_only`, `none_detected`).
- **Axis 2 (`target_division_role`):** `4` values (`medical_health`, `general_life`, `claims_care`, `bancassurance_vas`).
- **Combined Matrix:** `3 x 4 = 12` stacked cells.
- **Held states (amended 2026-11-20):** `unclear` on Signal 1 or 2, and `unmatched` on Signal 3, are not cells. Those rows stay in the table with Ready to Contact? false and are reviewed by hand; no fallback copy is written.
- **Angles are meaning only:** phrases such as "armed security", "zero control-room capex" and "faster dispatch" in the cells below are not approved claims. Copy uses only claims in `context/messaging/facts.md`.
- **Copy routing:** Email 1, Email 2 and DM 1 route on the two axes separately through the copy-line variables (section 6). The cell selects the angle and the report tag; it does not have its own copy.

| Cell | Deterministic Read (`provider` x `division_role`) | What It Tells Us (Inferred Situation) | The Angle It Earns (Meaning Only - No Copy) |
|---|---|---|---|
| **C1** | `rescue_co_roadside` x `medical_health` | Insurer pays Rescue.co for roadside/medical evacuation on motor, leaving medical policyholders without private armed security or unified white-label dispatch (`competitors.md`, `INFERRED`). | Consolidate medical and personal safety under the insurer's own brand with PSRA-vetted armed security and medical response in one API, filling what single-service or multi-bundle vendors and Kenya's 922 medical-only line leave uncovered. |
| **C2** | `rescue_co_roadside` x `general_life` | General/Life division uses a single-service or multi-bundle vendor for vehicle breakdowns, leaving personal safety and life-event emergency protection unaddressed (`competitors.md`, `INFERRED`). | Upgrade general and life policies from single-service or multi-bundle assistance to full 24/7 personal armed security, medical, and roadside protection under one white-label partner without managing separate vendors. |
| **C3** | `rescue_co_roadside` x `claims_care` | Claims and Care teams deal with fragmented roadside dispatch logs and manual follow-ups when incidents escalate beyond a tow (`customers.md`, `INFERRED`). | Eliminate manual phone-chasing overhead for emergency care teams and give Claims a single customer-facing portal with a full incident audit trail and customised reporting to verify scenes and curb claims leakage. |
| **C4** | `rescue_co_roadside` x `bancassurance_vas` | Bank or composite insurer bundles single-service or multi-bundle perks into select tiers but lacks a unified multi-hazard safety product across retail accounts and SMEs (`competitors.md`, `INFERRED`). | Embed white-label armed security, medical, and roadside response across retail banking and bancassurance tiers via one API, turning the bank or insurer app into an everyday safety network. |
| **C5** | `internal_motor_only` x `medical_health` | Group already runs motor rescue on its general arm (mirroring Old Mutual's motor launch) and can cross-sell into its sister Medical/Health entity (`signals.md`, `INFERRED`). | Replicate the group's motor assistance success inside the Medical/Health division with zero control-room capex, giving members faster Nairobi ambulance/security dispatch and relieving care desks from manual responder coordination. |
| **C6** | `internal_motor_only` x `general_life` | General division has basic motor rescue, while Life or non-motor general lines lack tangible everyday living benefits for policyholders (`signals.md`, `INFERRED`). | Turn Life and non-motor general policies from passive annual payouts into everyday tangible protection with white-label personal safety and medical response across 40+ Kenyan towns. |
| **C7** | `internal_motor_only` x `claims_care` | General motor desk handles emergency calls manually, creating heavy logistical phone-chasing overhead and inconsistent incident records for Claims (`customers.md`, `INFERRED`). | Offload manual emergency call-chasing from internal care teams to automated 24/7 dispatch while equipping Claims with real-time incident visibility and auditable reporting across divisions. |
| **C8** | `internal_motor_only` x `bancassurance_vas` | Insurer group has proven motor rescue on one line and now wants a packaged value-added service for bancassurance or digital distribution (`signals.md`, `INFERRED`). | Package white-label security, medical, and roadside protection as a low-friction bancassurance add-on using existing API/white-label architecture ("relatively easy to integrate"). |
| **C9** | `none_detected` x `medical_health` | Medical/Health insurer has no public embedded emergency response partner, relying on member reimbursements or public 922 evacuation (`market.md`, `INFERRED`). | Differentiate medical plans in a price-driven market by embedding 24/7 private medical and armed security response under the insurer's own brand, without building a dispatch network (amended 2026-11-20: the unverified 20 to 60 minute delay comparison is removed). |
| **C10** | `none_detected` x `general_life` | General or Life insurer offers traditional cover without real-time emergency response, competing mainly on price (`customers.md`, `INFERRED`). | Stand out beyond price in Kenyan general and life insurance by embedding white-label security, medical, and roadside protection with predictable per-user monthly unit economics. |
| **C11** | `none_detected` x `claims_care` | Claims and Customer Care teams handle post-incident reports reactively with no live scene visibility or automated dispatch (`customers.md`, `INFERRED`). | Shift Claims and Care from reactive post-incident paperwork to real-time emergency intervention with a full digital audit trail that lowers claim severity and lightens care-team phone overhead. |
| **C12** | `none_detected` x `bancassurance_vas` | Retail bank or bancassurance unit has digital customer distribution but no embedded emergency protection tier (`icp.md`, `INFERRED`). | Launch a differentiated white-label emergency protection tier across retail banking/bancassurance accounts via API or turnkey white-label app without building dispatch infrastructure from scratch. |

---

## 6. Variables Contract `[ENGINE]`
| Variable | Source in Clay | Exists in Branches |
|---|---|---|
| `{{first_name}}` | Find People first name, cleaned by formula | All (`C1` - `C12`) |
| `{{company_name}}` | Clay company name, cleaned by formula (legal suffixes such as Ltd, Limited and PLC removed) | All (`C1` - `C12`) |
| `{{division_name}}` | Formula on the job title, same match as Signal 3 (`Medical`, `General`, `Life`, `Claims & Care`, `Bancassurance`) | All (`C1` - `C12`) |
| `{{existing_rescue_program}}` | Signal 2 Use AI field `program_name` | `C1` - `C8` only (never referenced in `C9` - `C12`) |
| `{{sister_line_detected}}` | Signal 1 Use AI field `sister_line_name`: a clean line name such as "Medical Insurance", never a raw page title | All (`C1` - `C12`) |
| `{{app_platform_clause}}` | Formula from Signal 4: "Since you have a customer app, the response can sit inside it." when true, otherwise blank | Only when `has_mobile_customer_app = true` |
| `{{macro_922_context}}` | Constant formula text from Signal 5 | All (`C1` - `C12`) |
| `{{social_proof}}` | Constant text from `context/messaging/facts.md` (Old Mutual and SanlamAllianz; one line, no routing; added 2026-11-20) | All (`C1` - `C12`) |
| `{{e1l1}}` | Copy-line formula, routes on `existing_assistance_provider`; text in the Copy section; guarded by Ready to Contact? | All (`C1` - `C12`) |
| `{{e1l2}}` | Copy-line formula, routes on `target_division_role`; guarded by Ready to Contact? | All (`C1` - `C12`) |
| `{{e2l1}}` | Copy-line formula, routes on `target_division_role`; guarded by Ready to Contact? | All (`C1` - `C12`) |
| `{{dm1}}` | Copy-line formula, routes on `target_division_role`; guarded by Ready to Contact? | All (`C1` - `C12`) |
| `{{sender_name}}`, `{{sender_title}}`, `{{sender_email}}` | Filled per inbox in the sequencer; not Clay columns | All (`C1` - `C12`) |

Spintax in braces (for example `{Worth a short conversation?|Open to a short conversation on it?}`) stays in the sequencer and is never built as a Clay formula.

---

## 7. Cadence & Channel `[ENGINE]`
- **Periodicity:** Single pass for this build (amended 2026-11-20): one search, one enrichment run and one website read per company. The weekly Monday scan and quarterly IRA/CBK sweeps in `gtm-system.md` are parked until the table is proven, because they need scheduled re-runs (`gtm-system.md`).
- **Channels & Touch Cadence:** Multi-channel **Email (`Smartlead` / `Instantly`) + LinkedIn (`HeyReach`)**, **5 touches over 10 days** (amended 2026-11-20): `Day 1`: Email 1 (signal-anchored) -> `Day 3`: empty connection request + DM 1 -> `Day 6`: Email 2 (role-specific value follow-up [audit trail and care-team phone overhead for Claims & Care; sister-line differentiation for Division Heads]) -> `Day 8`: DM 2 -> `Day 10`: Email 3 (low-friction close, referral ask).


---

## Copy

### Email 1 (Day 1) - APPROVED 2026-11-20

**Subject (static, one per send):** `{{company_name}} + emergency cover` | `emergency response idea` | `rescue cover question`

**Body:**
```
{{first_name}},

{{e1l1}}

{{e1l2}}

{AURA runs|We run} security, medical and roadside response that insurers and banks {offer|give} their customers under their own brand.

{{social_proof}}

{Worth a short conversation?|Open to a short conversation on it?|Is that worth a quick chat?}

{{sender_name}}
{{sender_title}}
```

**`{{e1l1}}` (route: `existing_assistance_provider`, exhaustive, no fallback):**
- `+ rescue_co_roadside:` You have {{existing_rescue_program}} for roadside, and {{sister_line_detected}} is its own line.
- `+ internal_motor_only:` You already have {{existing_rescue_program}} on the motor side, and {{sister_line_detected}} is a separate line.
- `+ none_detected:` I couldn't find an emergency response partner on your {{sister_line_detected}} page, though I may have missed it.

**`{{e1l2}}` (route: `target_division_role`, exhaustive, no fallback):**
- `+ medical_health:` And I imagine the {{division_name}} team gets the call when a member needs an ambulance or a guard to reach them quickly.
- `+ general_life:` And I imagine {{division_name}} is always looking for ways to stay useful to members between renewals.
- `+ claims_care:` And I imagine the {{division_name}} team gets pulled in when an emergency call needs a responder arranged and the incident written up.
- `+ bancassurance_vas:` And I imagine the {{division_name}} team is always looking for a benefit account holders use, not just hold.

**`{{social_proof}}` (one line, no routing):** Old Mutual and SanlamAllianz already offer this to customers in Kenya, as OM Rescue Plus and Emergency Assist.

**Assembled sample (C5, illustrative names):**

> Subject: acme insurance + emergency cover
>
> Jane,
>
> You already have Acme Rescue on the motor side, and Acme Health Cover is a separate line.
>
> And I imagine the Medical team gets the call when a member needs an ambulance or a guard to reach them quickly.
>
> AURA runs security, medical and roadside response that insurers and banks offer their customers under their own brand.
>
> Old Mutual and SanlamAllianz already offer this to customers in Kenya, as OM Rescue Plus and Emergency Assist.
>
> Worth a short conversation?
>
> {{sender_name}}
> {{sender_title}}

### DM 1 (Day 3, after an empty connection request) - APPROVED 2026-11-20

No subject, no signature. Route: `target_division_role` (exhaustive, no fallback).
```
Hi {{first_name}},
{{dm1}}
```
- `+ medical_health:` How does the {{division_name}} team arrange an ambulance or a guard for a member who needs one?
- `+ general_life:` Do {{division_name}} members get anything they use day to day, or is it mostly at claim time?
- `+ claims_care:` When a member has an emergency, how does the {{division_name}} team get a responder to them and record what happened?
- `+ bancassurance_vas:` Is there an emergency benefit account holders get through {{company_name}} today, or is that still open?

### Email 2 (Day 6, same thread, subject `Re:` the same subject) - APPROVED 2026-11-20

```
{{first_name}},

{{e2l1}}

{{macro_922_context}}

{{app_platform_clause}}

{AURA's stated|Our stated} Nairobi averages are about 10 minutes for security and 10 to 15 for ambulances, depending on responder availability.

{Has your team looked at something like this before?|Is this something your team has looked at?}

{{sender_name}}
{{sender_title}}
```

**`{{e2l1}}` (route: `target_division_role`, exhaustive, no fallback):**
- `+ medical_health:` Your {{division_name}} team can follow each incident on AURA's platform while AURA's control room dispatches the ambulance or guard.
- `+ general_life:` A {{division_name}} policy could carry a benefit members actually use: security, medical or roadside help, dispatched by AURA's control room under your brand.
- `+ claims_care:` Each incident on AURA's platform comes with a full audit trail your {{division_name}} team can open, and AURA's control room handles the responder coordination.
- `+ bancassurance_vas:` For {{division_name}}, it can go in as an add-on to existing accounts or policies, with the response run by AURA's control room under your brand.

**`{{macro_922_context}}` (static, all leads):** Kenya's 922 line, launched in August 2026, covers medical evacuation only, so security and roadside sit outside it.

**`{{app_platform_clause}}` (only when `has_mobile_customer_app = true`, otherwise the line is dropped):** Since you have a customer app, the response can sit inside it.

**Assembled sample (C5, with an app, illustrative names):**

> Re: acme insurance + emergency cover
>
> Jane,
>
> Your Medical team can follow each incident on AURA's platform while AURA's control room dispatches the ambulance or guard.
>
> Kenya's 922 line, launched in August 2026, covers medical evacuation only, so security and roadside sit outside it.
>
> Since you have a customer app, the response can sit inside it.
>
> AURA's stated Nairobi averages are about 10 minutes for security and 10 to 15 for ambulances, depending on responder availability.
>
> Has your team looked at something like this before?
>
> {{sender_name}}
> {{sender_title}}

### DM 2 (Day 8, static) - APPROVED 2026-11-20

```
{Hi|Hello} {{first_name}},
{For context|Quick context}: AURA runs security, medical and roadside response that Old Mutual and SanlamAllianz {offer|give} their customers in Kenya under their own brand. {Would it be useful to see how it works?|Is that something worth a look?}
```

### Email 3 (Day 10, same thread, static) - APPROVED 2026-11-20

```
{{first_name}},

{I'll leave it here after this note|This is my last note on it}, {as|since} I may be writing to the wrong person.

If {{division_name}} doesn't own this, {who should I speak to|who would you point me to} at {{company_name}}?

{{sender_name}}
{{sender_title}}
```
