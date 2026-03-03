---
name: chart-of-accounts
description: |
  Extension encoding chart of accounts structure: account codes, groupings,
  documentation requirements, and intercompany account mappings.
  Ships with IFRS-compliant PKR template. Adapt for your entity.
license: Apache-2.0
metadata:
  author: panaversity
  version: "1.0"
  chapter: "19"
  domain: "extension-2"
---

# Chart of Accounts Extension

## Purpose

This extension encodes a chart of accounts structure as standing instructions for the accounting-reporting agent. When loaded, the agent maps every journal entry and reconciliation output to the correct account codes, ensuring entries slot directly into the entity's accounting system without manual recoding. The template ships with an IFRS-compliant PKR chart of accounts. Practitioners must customise the account codes, descriptions, and documentation requirements to match their entity's actual chart.

## Instructions

### Account Code Structure

When processing or generating journal entries, apply this account code hierarchy:

- **1000-1999**: Assets
  - 1000-1099: Cash and bank accounts
  - 1100-1199: Trade receivables and other receivables
  - 1200-1299: Inventories
  - 1300-1399: Prepayments and advances
  - 1400-1499: Property, plant and equipment (net)
  - 1500-1599: Intangible assets
  - 1600-1699: Right-of-use assets (IFRS 16)
  - 1700-1799: Investment properties
  - 1800-1899: Financial assets (investments, derivatives)
  - 1900-1999: Deferred tax assets and other non-current assets

- **2000-2999**: Liabilities
  - 2000-2099: Trade payables
  - 2100-2199: Accrued expenses and other payables
  - 2200-2299: Short-term borrowings and current portion of long-term debt
  - 2300-2399: Tax payable (income tax, sales tax, WHT)
  - 2400-2499: Provisions (warranty, litigation, restructuring)
  - 2500-2599: Long-term borrowings
  - 2600-2699: Lease liabilities (IFRS 16)
  - 2700-2799: Employee benefit obligations
  - 2800-2899: Deferred tax liabilities
  - 2900-2999: Other non-current liabilities

- **3000-3999**: Equity
  - 3000-3099: Share capital
  - 3100-3199: Share premium
  - 3200-3299: Retained earnings
  - 3300-3399: Other reserves (revaluation, hedging, translation)
  - 3400-3499: Non-controlling interests

- **4000-4999**: Revenue
  - 4000-4099: Revenue from contracts with customers (IFRS 15)
  - 4100-4199: Other operating income
  - 4200-4299: Finance income
  - 4300-4399: Share of profit of associates and joint ventures

- **5000-5999**: Cost of Sales and Direct Costs
  - 5000-5099: Raw materials consumed
  - 5100-5199: Direct labour
  - 5200-5299: Manufacturing overheads
  - 5300-5399: Purchases (trading entities)
  - 5400-5499: Contract costs

- **6000-6999**: Operating Expenses
  - 6000-6099: Employee costs (salaries, benefits, social charges)
  - 6100-6199: Depreciation and amortisation
  - 6200-6299: Rent and occupancy (non-IFRS 16 leases)
  - 6300-6399: Professional fees and consulting
  - 6400-6499: Travel and entertainment
  - 6500-6599: IT and communications
  - 6600-6699: Marketing and business development
  - 6700-6799: Insurance
  - 6800-6899: Other administrative expenses

- **7000-7999**: Finance Costs
  - 7000-7099: Interest on borrowings
  - 7100-7199: Interest on lease liabilities
  - 7200-7299: Bank charges and fees

- **8000-8999**: Tax
  - 8000-8099: Current tax expense
  - 8100-8199: Deferred tax expense/benefit

- **9000-9999**: Intercompany and Suspense
  - 9000-9099: Intercompany receivables
  - 9100-9199: Intercompany payables
  - 9200-9299: Intercompany revenue
  - 9300-9399: Intercompany cost recharges
  - 9900-9999: Suspense accounts (must be cleared before period close)

### Documentation Requirements by Account Type

When posting journal entries, enforce these documentation requirements:

- **Cash and bank (1000-1099)**: Bank statement or payment voucher required for every entry.
- **Trade receivables (1100-1199)**: Invoice reference required. Write-offs require credit committee approval document.
- **PPE (1400-1499)**: Capital expenditure approval form for additions. Disposal authorisation for removals.
- **Provisions (2400-2499)**: Management memo with calculation basis and assumptions.
- **Share capital (3000-3099)**: Board resolution required for any movement.
- **Revenue (4000-4099)**: Contract reference or sales order number required. Revenue recognition memo for non-standard arrangements.
- **Intercompany (9000-9399)**: Matching confirmation from the counterparty entity required before period close.
- **Suspense (9900-9999)**: Suspense entries must include a clearance deadline and the responsible person.

### Intercompany Account Rules

When processing intercompany transactions:

1. Every intercompany entry must have a mirror entry in the counterparty entity's books. Flag any unmatched intercompany balance.
2. Intercompany accounts use a sub-code structure: 9XXX-EEE where EEE is the entity number (e.g., 9000-001 = intercompany receivable from Entity 001).
3. Intercompany netting: At period end, net intercompany receivables and payables by entity pair. Report the net position to the user.
4. Elimination entries for consolidation: Generate elimination entries for all intercompany balances and transactions when the user is preparing consolidated statements.

### Accounts Requiring Senior Approval

The following accounts may NEVER be posted to without the user confirming senior approval:

- Suspense accounts (9900-9999) — all entries require explanation and clearance plan.
- Provisions (2400-2499) — creation or release of provisions requires management judgment.
- Share capital and reserves (3000-3399) — requires board resolution.
- Write-offs against receivables (1100 series credit entries) — requires credit committee approval.
- Related party transaction accounts — requires disclosure review.

### Pakistan SECP Requirements

For entities regulated by the Securities and Exchange Commission of Pakistan (SECP):

- The chart of accounts must align with the Fourth Schedule of the Companies Act 2017 for presentation of financial statements.
- Statutory reserves (e.g., general reserve per banking company requirements) must be separately identifiable.
- Account codes used for XBRL filing must map to the SECP taxonomy.

## Domain Context

This extension is loaded alongside the accounting-reporting agent skill (Domain 1). The chart of accounts structure follows the IFRS presentation model with Pakistan-specific additions for SECP compliance. The companion asset file `coa-template.csv` provides the base template in importable format. Practitioners must customise: add entity-specific accounts, remove irrelevant categories, adjust the intercompany entity numbering, and add any industry-specific accounts required by their operations.

## Constraints

- NEVER create journal entries using account codes not in the loaded chart — flag unmapped transactions for the user
- NEVER post to suspense accounts as a permanent resolution — every suspense entry must have a clearance plan
- NEVER remove documentation requirements — if evidence is missing, flag it rather than posting without support
- NEVER assume the intercompany entity numbering — confirm with the user before using sub-codes
- This chart is a TEMPLATE — the user must verify it matches their entity's actual accounting system before use
