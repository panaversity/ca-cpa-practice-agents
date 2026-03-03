# Fraud Monitoring

## Overview

Continuous transaction monitoring workflow for fraud detection, running weekly on the entity's transaction ledger. Applies three detection layers — Benford's Law first-digit analysis, duplicate transaction detection, and threshold-based anomaly scoring — to identify transactions requiring investigation. Produces a prioritized alert report with case documentation templates for each flagged item.

## Schedule

- **Frequency**: Weekly (every Monday at 06:00)
- **Trigger**: Automated scheduled task
- **Duration**: ~30 minutes execution; investigation time varies by alert volume

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (`/reconciliation` for cross-referencing)
- **Data inputs**: General ledger transaction extract (current week + rolling 12-month history), vendor master file, employee master file, approved signatory list
- **SKILL.md extensions**: `grc-advisory` (escalation thresholds, reporting obligations), `client-entity` (entity-specific risk areas, known related parties)
- **Cowork global instruction**: Set entity context, materiality thresholds for fraud reporting, escalation contacts

## Steps

### Step 1: Transaction Extraction and Preparation

```
Read the general ledger transaction extract from /data/fraud-monitoring/gl-extract-[YYYY-WW].csv.
Prepare the data for analysis:
(1) Validate completeness — verify sequential transaction numbering with no gaps
(2) Standardize vendor/payee names (trim whitespace, normalize case)
(3) Tag each transaction with: amount band (under 10K, 10-50K, 50-500K, over 500K PKR),
    day of week, time of day, approver
(4) Merge with vendor master and employee master for enrichment
(5) Flag any transactions posted outside business hours (before 08:00 or after 20:00)

Save prepared dataset to /output/fraud-monitoring/[YYYY-WW]/01-prepared-transactions.csv.
```

**Expected output**: Enriched transaction dataset with standardized names, amount bands, timing tags, and after-hours flags
**Human checkpoint**: Review any gaps in transaction numbering — these may indicate deleted transactions. Verify data completeness against ERP control totals.

### Step 2: Benford's Law Analysis

```
Apply Benford's Law first-digit analysis to the transaction dataset:
(1) Extract the first digit of every transaction amount
(2) Calculate the observed frequency distribution of first digits (1-9)
(3) Compare to the expected Benford's distribution:
    1=30.1%, 2=17.6%, 3=12.5%, 4=9.7%, 5=7.9%, 6=6.7%, 7=5.8%, 8=5.1%, 9=4.6%
(4) Calculate chi-squared statistic for overall conformity
(5) Flag digit groups where observed frequency deviates more than 2 standard
    deviations from expected (potential manipulation indicator)
(6) Perform second-digit analysis on flagged first-digit groups for deeper investigation

Save to /output/fraud-monitoring/[YYYY-WW]/02-benfords-analysis.md.
```

**Expected output**: First-digit frequency table with expected vs observed comparison, chi-squared result, flagged digit groups with deviation magnitude
**Human checkpoint**: Interpret Benford's results in context. Some legitimate business patterns produce non-conforming distributions (e.g., standardized monthly charges). Investigate flagged digit groups — are these genuine anomalies or explainable patterns?

### Step 3: Duplicate and Near-Duplicate Detection

```
Scan the rolling 12-month transaction history for duplicates:
(1) Exact duplicates — same vendor, same amount, same date (excluding
    legitimate recurring payments identified in the vendor master)
(2) Near-duplicates — same vendor, same amount, different dates within 7 days
(3) Split transactions — multiple transactions to the same vendor on the same
    day that individually fall below the approval threshold but aggregate above it
(4) Round-number concentration — transactions at exactly PKR 49,000, 99,000, 499,000
    (just below common approval thresholds of 50K, 100K, 500K)
(5) Sequential vendor payments — same vendor paid more than 3 times in a week

For each flagged item, calculate a risk score: High (exact duplicate or split
pattern), Medium (near-duplicate or round-number), Low (sequential payments).

Save to /output/fraud-monitoring/[YYYY-WW]/03-duplicate-detection.md.
```

**Expected output**: Duplicate detection report with each flagged transaction, match details, and risk score (High/Medium/Low)
**Human checkpoint**: Review all High-risk flags immediately. For exact duplicates, verify against source documents — is this a genuine duplicate payment or a legitimate repeat transaction? For split patterns, verify whether the splitting bypasses an approval authority.

### Step 4: Threshold and Anomaly Analysis

```
Apply threshold-based anomaly detection:
(1) Unusual amount analysis — transactions exceeding 3 standard deviations from
    the vendor's historical average transaction size
(2) New vendor analysis — payments to vendors added in the last 30 days,
    especially if total payments exceed PKR 200,000
(3) Dormant vendor reactivation — payments to vendors with no activity in the
    prior 6 months
(4) Employee expense anomalies — expense claims exceeding departmental average
    by more than 2x
(5) Related party proximity — transactions with vendors sharing addresses, phone
    numbers, or bank accounts with employees (cross-reference master files)
(6) Weekend/holiday transactions — any transactions posted on non-business days

Score each anomaly: Critical (related party match), High (new vendor + large amount),
Medium (statistical outlier), Low (timing anomaly only).

Save to /output/fraud-monitoring/[YYYY-WW]/04-anomaly-analysis.md.
```

**Expected output**: Anomaly report with each flagged transaction, anomaly type, and risk score; related party proximity matches highlighted separately
**Human checkpoint**: Review all Critical and High scores. Related party proximity matches require immediate investigation — these may indicate ghost vendor schemes. New vendor + large payment combinations warrant verification of vendor onboarding procedures.

### Step 5: Alert Generation and Prioritization

```
Consolidate all flags from Steps 2-4 into a single prioritized alert report:
(1) Deduplicate — if the same transaction is flagged by multiple detection methods,
    merge into a single alert with combined risk factors
(2) Rank by composite risk score:
    - Critical: Related party match OR exact duplicate over PKR 500,000
    - High: Multiple detection methods flagged OR single flag over PKR 500,000
    - Medium: Single detection method flagged, PKR 50,000 - 500,000
    - Low: Single detection method flagged, under PKR 50,000
(3) For each alert, provide: transaction details, detection method(s), risk score,
    suggested investigation action
(4) Summary statistics: total transactions scanned, total alerts by priority,
    PKR value at risk

Save to /output/fraud-monitoring/[YYYY-WW]/05-alert-report.md.
```

**Expected output**: Prioritized alert report with composite scoring, investigation recommendations, and summary statistics
**Human checkpoint**: Triage the alert report. Assign Critical and High alerts for immediate investigation. Review Medium alerts for patterns across multiple weeks. Dismiss Low alerts with documented rationale or escalate if a pattern emerges.

### Step 6: Case Documentation

```
For each Critical and High alert from Step 5, generate a case documentation template:
(1) Case reference: FRAUD-[YYYY-WW]-[NNN]
(2) Transaction details: date, amount, vendor, description, approver
(3) Detection method and risk factors
(4) Investigation steps required:
    - Source document verification
    - Vendor existence confirmation
    - Approver interview (if split pattern)
    - Bank account ownership verification (if related party match)
(5) Status: Open / Under Investigation / Resolved — No Issue / Resolved — Finding
(6) Outcome and action taken: [TO BE COMPLETED BY INVESTIGATOR]

Save individual case files to /output/fraud-monitoring/[YYYY-WW]/cases/.
Save case tracker summary to /output/fraud-monitoring/[YYYY-WW]/06-case-tracker.md.
```

**Expected output**: Individual case files for each Critical/High alert with pre-populated investigation templates; consolidated case tracker
**Human checkpoint**: Review case documentation for completeness. Assign investigators. Set investigation deadlines (Critical: 48 hours, High: 5 business days). Report findings to audit committee if any case confirms fraud.

## Output Artifacts

- `/output/fraud-monitoring/[YYYY-WW]/01-prepared-transactions.csv` — Enriched transaction dataset
- `/output/fraud-monitoring/[YYYY-WW]/02-benfords-analysis.md` — Benford's Law conformity analysis
- `/output/fraud-monitoring/[YYYY-WW]/03-duplicate-detection.md` — Duplicate and split transaction report
- `/output/fraud-monitoring/[YYYY-WW]/04-anomaly-analysis.md` — Threshold-based anomaly report
- `/output/fraud-monitoring/[YYYY-WW]/05-alert-report.md` — Consolidated prioritized alert report
- `/output/fraud-monitoring/[YYYY-WW]/cases/` — Individual case documentation files
- `/output/fraud-monitoring/[YYYY-WW]/06-case-tracker.md` — Case investigation tracker

## Quality Checks

- Transaction numbering sequence validated (no unexplained gaps)
- Benford's analysis covers full dataset (no transactions excluded without documented reason)
- Duplicate detection covers rolling 12-month window (not just current week)
- All Critical and High alerts have case documentation generated
- Related party cross-referencing uses current master file data (not stale extract)
- Week-over-week trend tracked — persistent Medium alerts escalated after 3 consecutive appearances
- Alert false positive rate monitored — if >80% of alerts are dismissed, recalibrate thresholds

## Customize This

| Variable                      | Default (Pakistan)                                | What to change                                     |
| ----------------------------- | ------------------------------------------------- | -------------------------------------------------- |
| Jurisdiction                  | Pakistan (SECP, FBR)                              | Your local regulator and fraud reporting authority |
| Currency                      | PKR                                               | Your reporting currency                            |
| Monitoring frequency          | Weekly (Monday 06:00)                             | Your risk appetite and transaction volume          |
| Escalation thresholds         | PKR 500,000 individual / PKR 2,000,000 cumulative | Your entity's materiality for fraud reporting      |
| Approval thresholds           | PKR 50,000 / 100,000 / 500,000                    | Your entity's delegation of authority limits       |
| Regulatory reporting          | SECP / FBR suspicious transaction requirements    | Your jurisdiction's fraud reporting obligations    |
| Benford's deviation threshold | 2 standard deviations                             | Your firm's statistical significance threshold     |
| Investigation deadlines       | Critical: 48 hours, High: 5 business days         | Your entity's investigation response policy        |
| Related party register        | Entity's RPT register + employee master           | Your entity's conflict of interest declarations    |
