# AURA GTM Context OS

## Company
AURA is a B2B emergency response platform, founded in 2017, that lets businesses embed security, medical and roadside response into their products, operating in South Africa, Kenya, the UK and the US. (Source: https://www.aurasos.com/en-ke/about)

## How this folder works
- `.claude/skills/`: reusable skills. Read the matching SKILL.md before any repeatable task.
  - `agent-browser`: browser automation for clicking, form filling and data extraction
  - `build-clay`: build, audit or repair a Clay outbound workbook
  - `build-workflow-spec`: turn one campaign play into a full outbound workflow spec
  - `calculate-costs`: report dollar spend and credit usage of a Clay table
  - `campaign-contract`: write the Markdown build sheet for one Clay campaign
  - `campaign-copy`: gated process for writing and reviewing cold email and LinkedIn DM copy
  - `campaign-qa`: QA a Clay table or sending campaign against its workflow spec
  - `campaign-strategy`: generate 15 to 25 cold outbound campaign ideas
  - `crawl4ai`: crawl pages or sites into clean Markdown or JSON, free and local
  - `design-clay-table-json`: write the Clay table JSON blueprint from a campaign contract
  - `export-tables`: export Clay tables to local CSV files
  - `import-clay-table`: import a Clay table JSON into the workspace with auto-run off
  - `inbox-placement-test`: run an inbox placement test on the cold email sending setup
  - `miro-gtm-flowchart`: draw a GTM system as an editable Miro flowchart
  - `prompt-builder`: build or repair per-row prompts for Clay AI columns
  - `save-clay-schema`: save an approved Clay table to the local table registry
  - `signal-matrix`: build ICP and signal matrices from product and buyer understanding
  - `workspace-cost-audit`: report a whole Clay workspace's monthly spend
- `context/icp/`: ICP (icp.md), buyer personas (personas.md), and scored signal matrix (signal-matrix.md). Read before choosing targets or writing copy.
- `context/positioning/`: positioning docs. Read before any messaging work.
- `context/messaging/`: approved messaging and proof points. Read before drafting copy.
- `context/brand-kit/`: voice, tone and style. Read before anything customer-facing.
- `context/docs/research/`: raw research with sources. Read when you need a fact.
- `knowledge-base/playbooks/`: copy rules and frameworks, signal matrix, workflow anatomy, Clay. Read before running a workflow.
- `knowledge-base/learnings/`: what worked and what did not. Read before repeating an approach.
- `meetings/`: meeting notes. Read for decisions and open actions.
- `output/campaigns/`: finished campaign assets. Write deliverables here.
- `tools/`: scripts and tool notes. Read before building something that may exist.
- `weekly-priorities/`: one file per ISO week. Read at the start of every session.
- `work-log/`: one file per ISO week. Write to it after every change.

## Rules
- Cite a source (URL or file path) for every company fact.
- Never invent numbers. If a figure is unknown, say so.
- No em dashes in any copy.
- Ask before sending or publishing anything.
- Log every change in this week's work log (`work-log/YYYY-Www.md`).

## Tools
- Clay
- HubSpot
- n8n
- `tools/agent-browser`: browser automation scripts
- `tools/crawl4ai`: local web crawler
- `tools/rex`: unofficial Clay toolkit (by Leszek Lammel, MIT) that works in Clay through your browser session. Read GETTING_STARTED.md first.
