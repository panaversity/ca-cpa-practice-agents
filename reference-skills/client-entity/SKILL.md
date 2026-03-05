---
name: client-entity
description: |
  Template extension for encoding client-specific entity knowledge:
  business model, seasonal patterns, risk areas, key personnel,
  and historical engagement context. Clone and customize per client.
license: Apache-2.0
metadata:
  author: panaversity
  version: "1.0"
  chapter: "19"
  domain: "extension-4"
---

# Client Entity Knowledge Extension (Template)

## Purpose

This extension encodes client-specific entity knowledge as standing instructions that apply to all agent work for a particular client. When loaded, the agent automatically applies the client's business context, seasonal patterns, key risks, and management preferences to every analysis, report, or working paper it produces. Clone this template and customise it for each significant client engagement. The instructions below use a hypothetical textile exporter as an example — replace every section with your actual client's information.

## Instructions

### How to Use This Template

1. Copy this entire SKILL.md file into a new directory: `skills/client-[client-name]/SKILL.md`
2. Update the YAML frontmatter: change `name` to `client-[client-name]` and update the description.
3. Replace every section below with your client's actual information.
4. Review and update at least annually, or when significant changes occur (new contract, change of ownership, regulatory change).
5. Load this extension alongside the relevant domain agent skill(s) when working on this client's engagement.

### Entity Overview

**[REPLACE THIS SECTION WITH YOUR CLIENT'S INFORMATION]**

Example (hypothetical textile exporter):

- **Legal name**: Karachi Textiles (Private) Limited
- **Entity type**: Private limited company incorporated under the Companies Act 2017
- **Industry**: Textile manufacturing and export
- **Principal activities**: Spinning, weaving, dyeing, and export of cotton textiles
- **Revenue (latest year)**: PKR 2.8 billion
- **Total assets**: PKR 1.9 billion
- **Employees**: 1,200 (800 factory, 400 office/management)
- **Fiscal year end**: June 30
- **Accounting framework**: IFRS as adopted in Pakistan
- **Auditor**: [Your firm name]
- **Key management**: CEO (founding family member), CFO (qualified CA), Production Director

### Revenue Streams and Seasonal Patterns

**[REPLACE WITH YOUR CLIENT'S PATTERNS]**

Example:

- **Export revenue** (70% of total): Orders peak in Q1 (Jul-Sep) for Northern Hemisphere winter collections. Shipments concentrated in Q1 and Q2. Revenue recognition per IFRS 15 at the point of shipment (FOB basis).
- **Local market revenue** (30% of total): Relatively stable across quarters with a 15% uplift in Q4 (Apr-Jun) for Eid season.
- **Seasonal working capital impact**: Inventory build-up in Q4 of prior year (raw cotton purchases at harvest). Receivables peak in Q2 after Q1 shipments. Cash position lowest in Q4, highest in Q3.
- **Effect on financial ratios**: Current ratio drops below 1.0 in Q4 (inventory-heavy, pre-shipment). EBITDA margin varies from 8% (Q4) to 16% (Q2). Annualised ratios from interim periods are misleading — always use trailing 12 months.

### Related Party Relationships

**[REPLACE WITH YOUR CLIENT'S RELATIONSHIPS]**

Example:

- **Shareholder family**: The Ahmed family holds 85% of shares through a holding company. The CEO, Production Director, and one non-executive director are family members.
- **Related party transactions**: Raw cotton purchased from Ahmed Farms (family-owned) — approximately PKR 180 million per year. Arm's length pricing to be verified annually. Warehouse leased from Ahmed Properties at PKR 2.4 million per month.
- **Accounting implications**: IAS 24 disclosures required. Audit procedures must include arm's length price testing on the cotton purchases and the warehouse lease.

### Known Risk Areas

**[REPLACE WITH YOUR CLIENT'S RISKS]**

Example:

1. **Foreign currency exposure**: 70% of revenue in USD, costs predominantly in PKR. PKR depreciation is favourable for revenue but creates volatility. Forward contracts used selectively (IFRS 9 hedge accounting applied — verify designation documentation each period).
2. **Export rebate receivable**: Government export rebates (DLTL scheme) are subject to delayed payment. Receivable of PKR 95 million outstanding >180 days. Recoverability requires assessment each period — engage management for latest status.
3. **Labour compliance**: Factory operations subject to provincial labour laws. Minimum wage compliance, social security contributions, and EOBI contributions must be verified. Any non-compliance could result in penalties and reputational risk.
4. **Inventory valuation**: Raw cotton prices are volatile. NRV testing required at each reporting date. Obsolescence provision for greige fabric held >12 months (historically 3-5% of inventory value).
5. **Debt covenant**: Term loan from HBL with DSCR covenant of 1.2x. Current DSCR is 1.35x. Monitor quarterly and flag if EBITDA trends suggest a breach.

### Management Reporting Preferences

**[REPLACE WITH YOUR CLIENT'S PREFERENCES]**

Example:

- **CFO preferences**: Wants variance analysis with volume/price/mix decomposition for revenue. Prefers commentary that distinguishes between controllable and uncontrollable variances. Board pack format: executive summary first, detail in appendices. Traffic-light KPI dashboard on page 1.
- **Reporting frequency**: Monthly management accounts by the 10th working day. Quarterly board pack. Annual statutory accounts.
- **Key KPIs monitored**: Revenue per meter, cost per kg of yarn, EBITDA margin %, DSO, DPO, inventory days, DSCR, USD realisation rate (PKR per USD achieved vs SBP rate).

### Engagement History

**[REPLACE WITH YOUR CLIENT'S HISTORY]**

Example:

- **FY2024 audit**: Unmodified opinion. Key audit matter: valuation of export rebate receivable. Management letter: 3 findings (2 resolved, 1 carried forward — lack of formal policy on related party pricing).
- **FY2024 tax**: Corporate tax return filed September 2024. WHT reconciliation identified PKR 1.2 million under-deduction on services payments — corrected and paid with surcharge.
- **Recurring issues**: Related party pricing documentation has been flagged in 2 consecutive years. Cotton purchase prices need benchmarking against market rates at each period end.

## Domain Context

This extension is loaded alongside any domain agent skill (Domains 1-5) when working on the specific client's engagement. It provides the entity-specific context that transforms generic agent outputs into client-relevant analysis. The quality of this extension directly determines the quality of the agent's output — a well-populated client entity extension produces analyses that surface the right risks and apply the right context, while a generic one produces generic outputs that miss client-specific considerations.

## Constraints

- NEVER share this extension's contents with anyone outside the engagement team — it contains confidential client information
- NEVER use information from this extension for any purpose other than the client's engagement
- NEVER assume the information in this extension is current — verify key facts (ratios, covenant positions, related party transactions) at each engagement
- NEVER treat the example content in this template as real client data — it is hypothetical
- This is a TEMPLATE — every section marked [REPLACE] must be populated with actual client information before use
- Update this extension whenever significant changes occur — do not rely on stale client knowledge
