# Tax Computation

## Overview

End-to-end corporate tax computation workflow from adjusted trial balance to filed return. Covers income classification under the Income Tax Ordinance 2001, allowable and disallowable deduction analysis, rate application per FBR schedules, minimum tax and alternative corporate tax checks, and return preparation with supporting schedules.

## Schedule

- **Frequency**: Annually (with quarterly provisional estimates)
- **Trigger**: Financial year end + 30 days (allows for audit adjustments)
- **Duration**: Full computation ~3 hours; quarterly provisional estimate ~45 minutes

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (`/journal-entry` for tax provision entries)
- **Data inputs**: Audited/adjusted trial balance, prior year tax return, advance tax payment schedule, fixed asset register, related party transaction log
- **SKILL.md extensions**: `pakistan-tax-jurisdiction` (ITO 2001 rates, WHT sections, filing calendar), `chart-of-accounts` (tax-adjusted account mapping)
- **Cowork global instruction**: Set entity type (company/AOP/individual), tax year, NTN number context

## Steps

### Step 1: Income Classification

```
Read the adjusted trial balance from /data/tax/trial-balance-[TAX-YEAR].csv.
Classify all revenue and income accounts into ITO 2001 categories:
(1) Income from business (Section 18) — operating revenue, cost of sales, operating expenses
(2) Income from property (Section 15) — rental income, property gains
(3) Income from capital gains (Section 37A) — asset disposals
(4) Income from other sources (Section 39) — interest, dividends, miscellaneous
Produce a classified income schedule showing each account mapped to its ITO head.
Save to /output/tax/[TAX-YEAR]/01-income-classification.md.
```

**Expected output**: Income classification schedule with each trial balance account mapped to its ITO 2001 head of income, with section references
**Human checkpoint**: Verify classification of borderline items (e.g., one-off gains that could be business income or capital gains). Confirm treatment of any novel income streams.

### Step 2: Deduction Analysis

```
For each head of income from Step 1, analyze all expense accounts and classify as:
(1) Allowable deductions — with ITO section reference (Sections 20-27)
(2) Disallowable deductions — with disallowance reason and section reference
(3) Partial deductions — percentage allowable with calculation basis

Key disallowance checks:
- Section 21: Personal expenses of non-business nature
- Section 21(c): Entertainment exceeding prescribed limits
- Section 21(l): Payments to unapproved retirement funds
- Section 22: Depreciation vs tax depreciation rates (Third Schedule)
- Section 23: Payments without withholding tax deduction

Save to /output/tax/[TAX-YEAR]/02-deduction-analysis.md.
```

**Expected output**: Three-column deduction schedule (allowable/disallowable/partial) with ITO section references and computation notes
**Human checkpoint**: Review all disallowances for accuracy. Verify depreciation rates against Third Schedule. Confirm WHT compliance on major payments.

### Step 3: Tax Depreciation Computation

```
Read the fixed asset register from /data/tax/fixed-assets-[TAX-YEAR].csv.
Compute tax depreciation using ITO 2001 Third Schedule rates:
(1) Opening WDV for each asset class
(2) Additions and disposals during the year
(3) Depreciation at prescribed rates (initial + normal allowance)
(4) Closing WDV
Compare tax depreciation to accounting depreciation and calculate the timing
difference. Save to /output/tax/[TAX-YEAR]/03-tax-depreciation.md.
```

**Expected output**: Tax depreciation schedule by asset class with WDV movement, timing difference reconciliation to accounting depreciation
**Human checkpoint**: Verify asset classifications against Third Schedule categories. Confirm initial allowance eligibility for new additions. Check disposal proceeds against WDV for gain/loss computation.

### Step 4: Taxable Income and Rate Application

```
Compute taxable income:
(1) Start with accounting profit before tax
(2) Add back disallowable deductions (Step 2)
(3) Deduct additional allowable deductions (tax depreciation difference from Step 3)
(4) Apply any brought-forward losses (verify 6-year limitation per Section 57)
(5) Compute taxable income under each head

Apply FBR corporate tax rate for the current tax year.
Also compute:
- Minimum tax under Section 113 (1.25% of turnover)
- Alternative Corporate Tax under Section 113C (17% of accounting income)
Determine which computation produces the highest liability.

Save to /output/tax/[TAX-YEAR]/04-taxable-income.md.
```

**Expected output**: Taxable income computation with line-by-line reconciliation from accounting profit, three-way comparison (normal/minimum/ACT), final tax liability determination
**Human checkpoint**: Verify loss carry-forward eligibility and expiry dates. Confirm correct tax rate applied (check for any special rate applicable to entity type). Review minimum tax and ACT calculations.

### Step 5: Advance Tax Reconciliation

```
Read advance tax payment records from /data/tax/advance-tax-[TAX-YEAR].csv.
Reconcile:
(1) Quarterly advance tax payments (Section 147)
(2) WHT credits — tax deducted at source on payments received (Sections 148-156)
(3) WHT credits — tax collected on sales/imports
(4) Any tax already paid with provisional return

Compute: Final tax liability minus total advance tax and WHT credits = tax payable
or refundable. Save to /output/tax/[TAX-YEAR]/05-advance-tax-reconciliation.md.
```

**Expected output**: Advance tax reconciliation showing each payment/credit with date, section reference, and amount; net payable/refundable position
**Human checkpoint**: Verify all WHT certificates are genuine and match amounts claimed. Confirm advance tax payment dates and amounts against bank statements. Flag any potential penalties for late/insufficient advance tax.

### Step 6: Return Preparation

```
Compile the complete tax return package:
(1) Tax computation summary (Steps 1-5 consolidated)
(2) Supporting schedules: income classification, deduction analysis, depreciation,
    advance tax reconciliation
(3) Required annexures: related party transactions, foreign payments,
    prescribed person disclosures
(4) Filing checklist with all required attachments listed
(5) Due date confirmation and penalty exposure if late

Format as the standard FBR corporate income tax return structure.
Save to /output/tax/[TAX-YEAR]/06-return-package/.
```

**Expected output**: Complete return package with computation, all supporting schedules, annexures, and filing checklist
**Human checkpoint**: Final review of entire computation. Verify mathematical accuracy end-to-end. Confirm all required annexures complete. Sign off before filing. Note: actual e-filing on IRIS portal is performed by the practitioner.

## Output Artifacts

- `/output/tax/[TAX-YEAR]/01-income-classification.md` — Income classification by ITO head
- `/output/tax/[TAX-YEAR]/02-deduction-analysis.md` — Allowable/disallowable deduction schedule
- `/output/tax/[TAX-YEAR]/03-tax-depreciation.md` — Tax depreciation and timing differences
- `/output/tax/[TAX-YEAR]/04-taxable-income.md` — Taxable income computation with three-way comparison
- `/output/tax/[TAX-YEAR]/05-advance-tax-reconciliation.md` — Advance tax and WHT credit reconciliation
- `/output/tax/[TAX-YEAR]/06-return-package/` — Complete filing package with schedules and annexures

## Quality Checks

- Taxable income computation reconciles from accounting profit (no unexplained gaps)
- All deduction disallowances cite specific ITO section references
- Tax depreciation ties to fixed asset register movements
- Advance tax credits reconcile to WHT certificates and bank records
- Minimum tax and ACT computations both performed (three-way comparison documented)
- Return package includes all mandatory FBR annexures

## Customize This

| Variable              | Default (Pakistan)              | What to change                                                |
| --------------------- | ------------------------------- | ------------------------------------------------------------- |
| Jurisdiction          | Pakistan (FBR)                  | Your local tax authority (IRS, HMRC, etc.)                    |
| Currency              | PKR                             | Your reporting currency                                       |
| Tax legislation       | Income Tax Ordinance 2001       | Your tax code (IRC, ITA 2007, etc.)                           |
| Corporate tax rate    | FBR current year rate           | Your jurisdiction's corporate rate                            |
| Minimum tax           | Section 113 (1.25% of turnover) | Your jurisdiction's minimum/alternative tax                   |
| Depreciation schedule | ITO Third Schedule rates        | Your tax depreciation rates (MACRS, capital allowances, etc.) |
| Filing deadline       | Sep 30 (corporate)              | Your jurisdiction's corporate filing deadline                 |
| Advance tax           | Quarterly per Section 147       | Your jurisdiction's instalment schedule                       |
| WHT sections          | Sections 148-156                | Your jurisdiction's withholding provisions                    |
| Loss carry-forward    | 6 years per Section 57          | Your jurisdiction's loss utilization rules                    |
