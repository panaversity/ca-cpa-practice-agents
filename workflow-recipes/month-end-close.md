# Month-End Close

## Overview

Automated month-end close workflow that compresses a typical 3-day, 4-person close process into a 2-day cycle with one CA/CPA plus Cowork. Scheduled reconciliations run at Day 1 open, freeing the practitioner to focus on exception review, judgment-intensive adjustments, and management commentary.

## Schedule

- **Frequency**: Monthly (1st and 2nd business day after period end)
- **Trigger**: Calendar — 1st business day of each month at 07:00
- **Duration**: Day 1 automated tasks ~45 min execution; Day 2 manual review + finalization ~3 hours

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (`/journal-entry`, `/reconciliation`, `/income-statement`, `/variance-analysis`)
- **Data inputs**: Trial balance export (CSV/XLSX from ERP), bank statements (CSV), prior month management accounts, annual budget file
- **SKILL.md extensions**: `chart-of-accounts` (account mapping), `client-entity` (entity-specific accrual templates, depreciation schedules)
- **Cowork global instruction**: Set manufacturing/service context, reporting currency, financial year end

## Steps

### Step 1: Trial Balance Extraction and Validation

```
Read the trial balance export from /data/month-end/trial-balance-[YYYY-MM].csv.
Validate: (1) debits equal credits, (2) all account codes map to the chart of accounts
in skills/chart-of-accounts/assets/coa-template.csv, (3) no account balances have
changed sign from prior month without explanation. Flag any validation failures.
Save validated trial balance to /output/month-end/[YYYY-MM]/01-validated-tb.csv.
```

**Expected output**: Validated trial balance CSV with validation status column; exception log listing any unmapped accounts or balance anomalies
**Human checkpoint**: Review exception log. Investigate any unmapped accounts or unexpected sign changes before proceeding.

### Step 2: Bank and Ledger Reconciliations (Automated — Scheduled 07:00)

```
/reconciliation bank
/reconciliation debtors
/reconciliation creditors
/reconciliation intercompany
```

**Expected output**: Four reconciliation reports saved to `/output/month-end/[YYYY-MM]/02-reconciliations/`. Each report lists matched items, unmatched items, and reconciling differences with aging.
**Human checkpoint**: Review unmatched items and reconciling differences. Approve or investigate each exception. Target: 30 minutes for exception review versus 3 hours for full manual reconciliation.

### Step 3: Standard Journal Entries

```
/journal-entry depreciation
/journal-entry accruals
/journal-entry prepayments
```

**Expected output**: Three draft journal entry files with account codes, amounts, and narrative descriptions. Journals reference the depreciation schedule, accrual template, and prepayment register from the `client-entity` SKILL.md extension.
**Human checkpoint**: Review journal amounts against supporting schedules. Approve or adjust any entries where the agent's calculation differs from expectation. Sign off each journal.

### Step 4: Non-Standard Adjustments

```
Review the reconciliation exception reports from Step 2. For each unresolved
reconciling item above PKR 50,000, draft a proposed adjusting journal entry with:
(1) account codes, (2) amounts, (3) narrative explaining the adjustment rationale,
(4) supporting reference. Save to /output/month-end/[YYYY-MM]/04-adjustments.md.
```

**Expected output**: List of proposed adjusting entries with full narratives and cross-references to reconciliation exceptions
**Human checkpoint**: This is the primary judgment step. The practitioner decides which adjustments to post, modifies amounts where needed, and documents the rationale for any rejected adjustments.

### Step 5: Financial Statement Drafting

```
/income-statement monthly
```

```
Using the adjusted trial balance (post Steps 3-4), draft:
(1) Management income statement — actual vs budget vs prior month
(2) Balance sheet as at period end
(3) Cash flow statement (indirect method)
Save all three to /output/month-end/[YYYY-MM]/05-financial-statements/.
```

**Expected output**: Three draft financial statements in markdown format with comparative columns
**Human checkpoint**: Review for presentation accuracy. Verify that adjusting entries have been correctly reflected. Check classification of items between operating/financing/investing in cash flow.

### Step 6: Variance Analysis

```
/variance-analysis monthly
```

**Expected output**: Variance analysis bridge showing actual vs budget and actual vs prior month, decomposed into volume, price, and mix components where applicable. Top 5 variances ranked by absolute value.
**Human checkpoint**: Review the three largest variances. Add management commentary explaining the business drivers — this is the step where practitioner knowledge of the business is irreplaceable.

### Step 7: Disclosure Preparation

```
Based on the financial statements and variance analysis, draft the following
disclosure notes: (1) Accounting policies (confirm no changes from prior period),
(2) Related party transactions summary, (3) Contingent liabilities update,
(4) Subsequent events check. Save to /output/month-end/[YYYY-MM]/07-disclosures.md.
```

**Expected output**: Draft disclosure notes referencing IFRS requirements, with placeholders marked `[PRACTITIONER INPUT REQUIRED]` where entity-specific judgment is needed
**Human checkpoint**: Complete all practitioner input placeholders. Verify related party disclosures against the entity's related party register. Confirm contingent liability assessments.

### Step 8: Review and Sign-Off Package

```
Compile a close review package containing:
(1) Completion checklist — all steps with status (complete/pending/exception)
(2) Summary of all journals posted (Steps 3-4)
(3) Reconciliation status summary (Step 2)
(4) Financial statement package (Step 5)
(5) Variance commentary (Step 6)
(6) Disclosure notes (Step 7)
Save to /output/month-end/[YYYY-MM]/08-review-package.md.
```

**Expected output**: Single review package document with table of contents and cross-references to all supporting files
**Human checkpoint**: Final review and sign-off. Confirm all exceptions resolved, all journals approved, financial statements tie to adjusted trial balance. Distribute management accounts.

## Output Artifacts

- `/output/month-end/[YYYY-MM]/01-validated-tb.csv` — Validated trial balance
- `/output/month-end/[YYYY-MM]/02-reconciliations/` — Bank, debtors, creditors, intercompany reconciliation reports
- `/output/month-end/[YYYY-MM]/03-journals/` — Depreciation, accruals, prepayment journal entries
- `/output/month-end/[YYYY-MM]/04-adjustments.md` — Non-standard adjusting entries
- `/output/month-end/[YYYY-MM]/05-financial-statements/` — Income statement, balance sheet, cash flow statement
- `/output/month-end/[YYYY-MM]/06-variance-analysis.md` — Variance bridge with commentary placeholders
- `/output/month-end/[YYYY-MM]/07-disclosures.md` — Draft disclosure notes
- `/output/month-end/[YYYY-MM]/08-review-package.md` — Close review and sign-off package

## Quality Checks

- Trial balance debits equal credits (zero tolerance)
- All account codes mapped to chart of accounts (100% coverage)
- Reconciliation differences net to zero after approved adjustments
- Financial statements tie to adjusted trial balance (cross-cast check)
- All `[PRACTITIONER INPUT REQUIRED]` placeholders completed before distribution
- Close completed within 2 business days of period end

## Customize This

| Variable                | Default (Pakistan)                                | What to change                              |
| ----------------------- | ------------------------------------------------- | ------------------------------------------- |
| Jurisdiction            | Pakistan (FBR, SECP)                              | Your local tax authority + regulator        |
| Currency                | PKR                                               | Your reporting currency                     |
| Filing deadlines        | Sep 30 (corporate), Dec 31 (individual)           | Your jurisdiction's deadlines               |
| Materiality threshold   | PKR 50,000 (adjustments); 2% of revenue (overall) | Your firm's materiality policy              |
| Close calendar          | Day 1-2 cycle (1st-2nd business day)              | Your firm's close schedule                  |
| Reporting standards     | IFRS                                              | US GAAP, FRS 101/102, or local GAAP         |
| Depreciation method     | Straight-line per IFRS useful life tables         | Your entity's depreciation policy           |
| Reconciliation schedule | 07:00 automated on Day 1                          | Your preferred automation time              |
| Comparative periods     | Budget + prior month                              | Budget + prior month + prior year, or other |
