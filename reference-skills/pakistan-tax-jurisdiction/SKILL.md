---
name: pakistan-tax-jurisdiction
description: |
  Jurisdiction extension encoding Pakistan tax rules: Income Tax Ordinance 2001,
  FBR rates and slabs, filing deadlines, penalty provisions, and withholding
  tax schedules. Adapt this template for your local tax authority.
license: Apache-2.0
metadata:
  author: panaversity
  version: "1.0"
  chapter: "19"
  domain: "extension-1"
---

# Pakistan Tax Jurisdiction Extension

## Purpose

This extension encodes Pakistan's tax rules as standing instructions for the tax-advisory agent. When loaded, the agent automatically applies Pakistani tax law (Income Tax Ordinance 2001, as amended) to all tax computations and research. Adapt this template for other jurisdictions by replacing the rates, thresholds, deadlines, and statutory references with your local tax authority's requirements.

## Instructions

### Corporate Tax Rates

When computing corporate tax liabilities for Pakistani entities, apply these rates:

- **Public companies** (listed on PSX): 29% of taxable income.
- **Private companies** (not listed): 29% of taxable income.
- **Small companies** (as defined under ITO 2001, section 2(59A) — paid-up capital up to PKR 50 million, annual turnover up to PKR 250 million, employees up to 250): Reduced rate as per current Finance Act.
- **Banking companies**: 39% on taxable income up to PKR 5 billion; 44% on taxable income exceeding PKR 5 billion.
- **Association of Persons (AOP)**: Progressive slab rates per First Schedule, Part I, Division I.

When the entity type is not specified, ask before applying a rate.

### Individual Tax Slabs

For individual taxpayers (salaried and non-salaried), apply the slab rates from the First Schedule, Part I, Division I of ITO 2001 as amended by the latest Finance Act. The slabs are progressive — apply each rate only to the income falling within that bracket.

Always compute and compare:

- Normal tax liability per slab rates.
- Minimum tax under section 113 (turnover-based) — if the minimum tax exceeds the normal tax, the minimum tax applies.

### Withholding Tax (WHT) Schedules

When any transaction involves a payment, check whether WHT applies:

- **Salary payments** (section 149): Deduct tax per the applicable slab rates on projected annual salary.
- **Payments to non-residents** (section 152): Deduct at the rate applicable to the nature of payment (royalties, technical services, dividends) or the treaty rate if a Double Tax Treaty applies — use the lower rate.
- **Dividends** (section 150): 15% for filers, 30% for non-filers.
- **Profit on debt/interest** (section 151): 15% for filers, 30% for non-filers.
- **Contracts and services** (section 153): Rates vary by nature — goods supply (4.5% filer / 9% non-filer), services (8% filer / 16% non-filer), contracts (7% filer / 14% non-filer).
- **Property transactions** (section 236C/236K): Apply rates per the applicable schedule.

Always distinguish between filer and non-filer status — rates differ significantly.

### Filing Deadlines

When advising on filing obligations, apply these deadlines:

- **Corporate tax return**: September 30 following the end of the tax year (July-June). Extension available on application to the Commissioner.
- **Individual tax return (salaried)**: September 30.
- **Individual tax return (non-salaried/business)**: September 30.
- **Advance tax instalments**: Quarterly — September 15, December 15, March 15, June 15 (each 25% of estimated tax for the year).
- **Withholding tax statements**: Monthly (by the 15th of the following month) and annual reconciliation.
- **Sales tax return**: Monthly by the 18th of the following month (Federal and provincial).

### Penalty Provisions

When computing potential penalties for non-compliance:

- **Late filing of return** (section 182): PKR 40,000 or 0.1% of tax payable per day of default, whichever is higher. Maximum: assessed by Commissioner.
- **Late payment of tax** (section 205): Default surcharge at KIBOR + 3% per annum on the unpaid amount.
- **Failure to deduct WHT** (section 161/162): The person failing to deduct is treated as the assessee in default. Tax amount plus default surcharge recoverable from the person who failed to deduct.
- **Concealment of income** (section 111): Unexplained income or assets treated as income from undisclosed sources. Additional penalty up to 100% of tax evaded.

### Common Disallowed Deductions

When preparing tax computations, apply add-backs for these commonly disallowed items:

- Provisions and reserves not based on actual liability (section 21(m)).
- Personal expenses and entertainment above prescribed limits (section 21(k)).
- Payments made to unapproved retirement funds.
- Depreciation in excess of prescribed rates (Third Schedule).
- Any expenditure not supported by documentation where the amount exceeds PKR 50,000 and is paid otherwise than by crossed cheque or digital means (section 21(l)).

### Statutory Regulatory Orders (SROs)

When the user references an SRO, treat it as a notification that may modify the standard rates or provisions. SROs are issued by FBR and have the force of law. Always note the SRO number and its effective date when applying modified rates.

## Domain Context

This extension is loaded alongside the tax-advisory agent skill (Domain 2). Pakistan's tax system is administered by the Federal Board of Revenue (FBR) under the Income Tax Ordinance 2001. The tax year runs from July 1 to June 30 (standard) but companies may apply for a different fiscal year. Provincial sales tax (Punjab Revenue Authority, Sindh Revenue Board, etc.) applies separately for services rendered within each province. This extension covers federal income tax only — sales tax and provincial levies require separate jurisdiction extensions.

## Constraints

- NEVER present rates as current without noting that they are subject to annual revision by the Finance Act
- NEVER apply treaty rates without confirming the existence and applicability of the specific Double Tax Treaty
- NEVER assume filer status — always ask or require the user to confirm
- NEVER compute provincial sales tax under this extension — it covers federal income tax only
- NEVER treat SRO provisions as permanent law — they may be withdrawn or modified
- This extension is a TEMPLATE — practitioners must verify rates against the latest Finance Act before using in live engagements
