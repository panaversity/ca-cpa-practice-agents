# Audit Programme

## Overview

Full external audit programme workflow from engagement acceptance through opinion formation, structured per International Standards on Auditing (ISA). Covers planning (risk assessment, materiality, audit strategy), fieldwork (substantive testing, controls testing with `/sox-testing`), and completion (misstatement evaluation, opinion drafting, management letter). Designed for a mid-size entity audit engagement.

## Schedule

- **Frequency**: Annually (with interim procedures at half-year if applicable)
- **Trigger**: Engagement letter signed + client financial year end
- **Duration**: Planning phase ~2 hours; Fieldwork phase ~4 hours; Completion phase ~2 hours (elapsed across multiple sessions)

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (`/sox-testing`, `/reconciliation`)
- **Data inputs**: Prior year audit file, current year trial balance, prior year financial statements, entity risk profile, management representation letter template
- **SKILL.md extensions**: `audit-methodology` (materiality thresholds, sampling parameters, documentation standards), `client-entity` (entity profile, industry risks, prior year findings)
- **Cowork global instruction**: Set engagement context — entity name, financial year, reporting framework (IFRS), applicable auditing standards (ISA)

## Steps

### Phase 1: Planning

### Step 1: Preliminary Analytical Procedures

```
Read the current year trial balance from /data/audit/trial-balance-[YEAR].csv
and prior year financial statements from /data/audit/prior-year-fs-[YEAR-1].csv.
Perform preliminary analytical procedures:
(1) Year-on-year movement analysis for all material account balances
(2) Ratio analysis — gross margin, current ratio, debt-to-equity, receivables days
(3) Trend analysis — 3-year revenue and cost trends (if prior data available)
(4) Flag balances with movements exceeding 15% for further investigation
Save to /output/audit/[YEAR]/01-preliminary-analytics.md.
```

**Expected output**: Analytical procedures report with movement analysis, ratio dashboard, and flagged balances requiring investigation during fieldwork
**Human checkpoint**: Review flagged balances. Add engagement partner's knowledge of the entity and industry context. Identify any expected movements that are absent (potentially more concerning than unexpected movements).

### Step 2: Materiality Calculation

```
Calculate materiality per ISA 320:
(1) Overall materiality — 2% of revenue (or 5% of PBT if profit-making, 1% of
    total assets if loss-making). State the benchmark used and rationale.
(2) Performance materiality — 75% of overall materiality
(3) Trivial threshold — 5% of overall materiality (below which misstatements
    are clearly trivial)
(4) Component materiality (if group audit) — allocated based on component significance
Document the rationale for benchmark selection.
Save to /output/audit/[YEAR]/02-materiality.md.
```

**Expected output**: Materiality calculation with benchmark selection rationale, three materiality levels documented
**Human checkpoint**: Approve materiality levels. Confirm benchmark is appropriate for the entity (revenue for revenue-driven businesses, total assets for asset-heavy entities). Adjust if engagement-specific factors warrant different thresholds.

### Step 3: Risk Assessment

```
Using the analytical procedures (Step 1) and entity profile from
skills/client-entity/SKILL.md, perform risk assessment per ISA 315:
(1) Identify significant accounts — balances exceeding performance materiality
(2) For each significant account, assess inherent risk (High/Medium/Low) with
    rationale based on complexity, subjectivity, and susceptibility to misstatement
(3) Assess control risk based on prior year findings and known control environment
(4) Determine combined risk level and planned audit response
(5) Identify presumed fraud risks per ISA 240 (revenue recognition, management override)
(6) Identify significant risks requiring special audit consideration
Save to /output/audit/[YEAR]/03-risk-assessment.md.
```

**Expected output**: Risk assessment matrix for all significant accounts with inherent risk, control risk, combined risk, and planned response; fraud risk identification
**Human checkpoint**: Review risk assessments with engagement team. Confirm fraud risk identification is complete. Validate that planned responses are proportionate to assessed risk levels. Add any risks from engagement partner's entity knowledge.

### Step 4: Audit Strategy and Programme

```
Based on the risk assessment (Step 3), draft the audit programme:
For each significant account, specify:
(1) Audit assertion(s) to test (existence, completeness, valuation, rights, presentation)
(2) Nature of procedure (substantive analytical, test of details, test of controls)
(3) Timing (interim or final)
(4) Extent (sample size per ISA 530, population-based for analytics)
(5) Staff assignment (senior/junior/specialist)
Compile into audit programme matrix.
Save to /output/audit/[YEAR]/04-audit-programme.md.
```

**Expected output**: Audit programme matrix with procedures mapped to accounts, assertions, and risk levels; resource and timing plan
**Human checkpoint**: Review programme for completeness — every significant account has at least one procedure addressing each relevant assertion. Confirm sample sizes are appropriate for risk levels. Approve timing of interim vs final procedures.

### Phase 2: Fieldwork

### Step 5: Substantive Testing — Revenue and Receivables

```
Using the audit programme from Step 4, execute substantive procedures for
revenue and receivables:
(1) Revenue cut-off testing — verify transactions around period end are recorded
    in the correct period (sample 15 transactions either side of year end)
(2) Receivables confirmation — draft confirmation letters for top 20 debtors
    by balance; document expected vs confirmed amounts
(3) Receivables aging analysis — identify balances over 90 days, assess
    impairment provision adequacy
(4) Revenue analytical review — compare monthly revenue to budget and prior year
Document each test: objective, population, sample, results, conclusion.
Save to /output/audit/[YEAR]/05-revenue-receivables-testing.md.
```

**Expected output**: Test documentation for each procedure with sample details, findings, and conclusions on each assertion
**Human checkpoint**: Review all exceptions identified in testing. Determine whether exceptions indicate systemic issues or isolated errors. Assess impact on audit opinion.

### Step 6: Substantive Testing — PPE and Depreciation

```
Execute substantive procedures for property, plant, and equipment:
(1) Additions testing — vouch a sample of additions to supporting invoices,
    verify capitalisation criteria met, confirm correct asset class
(2) Disposals testing — verify proceeds, confirm derecognition, check gain/loss
(3) Depreciation recalculation — recalculate depreciation for a sample of
    asset classes, compare to client's computation
(4) Impairment assessment — identify indicators of impairment per IAS 36,
    document assessment
Save to /output/audit/[YEAR]/06-ppe-testing.md.
```

**Expected output**: PPE test documentation with sample selections, vouching results, depreciation recalculation, and impairment assessment
**Human checkpoint**: Review capitalisation decisions for borderline items. Confirm depreciation recalculation differences are within tolerable limits. Assess any impairment indicators identified.

### Step 7: Controls Testing

```
/sox-testing revenue-cycle
/sox-testing procurement-cycle
/sox-testing payroll-cycle
```

**Expected output**: Control testing documentation for each cycle — control description, testing objective, sample selected, test results, operating effectiveness conclusion
**Human checkpoint**: Review control exceptions. Determine whether exceptions represent design deficiency or operating failure. Assess impact on control risk assessment and whether additional substantive procedures are needed.

### Step 8: Other Substantive Procedures

```
Execute remaining procedures per the audit programme (Step 4):
(1) Bank confirmations — compare confirmed balances to reconciled book balances
(2) Creditors circularisation — confirm key supplier balances
(3) Inventory observation checklist (if applicable)
(4) Related party transaction verification — cross-reference to entity's RPT register
(5) Provisions and contingencies — review legal counsel confirmation letter
Document each procedure with ISA-compliant working paper format.
Save to /output/audit/[YEAR]/08-other-substantive.md.
```

**Expected output**: Working papers for each additional procedure with sample details, results, and conclusions
**Human checkpoint**: Review bank confirmation differences. Verify completeness of related party disclosures. Assess provision adequacy and contingent liability disclosures.

### Phase 3: Completion

### Step 9: Misstatement Evaluation

```
Compile all misstatements identified during fieldwork (Steps 5-8):
(1) List all identified misstatements — factual, judgmental, and projected
(2) Aggregate uncorrected misstatements
(3) Compare aggregate to performance materiality and overall materiality
(4) Assess whether uncorrected misstatements are material individually or
    in aggregate per ISA 450
(5) Draft summary of audit differences for management
Save to /output/audit/[YEAR]/09-misstatement-evaluation.md.
```

**Expected output**: Schedule of unadjusted differences with individual and aggregate assessment against materiality thresholds
**Human checkpoint**: Evaluate whether management should be requested to adjust material misstatements. Assess impact of unadjusted misstatements on audit opinion. Document rationale for any misstatements considered immaterial.

### Step 10: Opinion Drafting

```
Based on the misstatement evaluation (Step 9) and overall audit findings:
(1) Determine appropriate opinion type per ISA 700/705:
    - Unmodified (clean) — if no material misstatement or limitation
    - Qualified — if material but not pervasive misstatement or limitation
    - Adverse — if material and pervasive misstatement
    - Disclaimer — if material and pervasive limitation on scope
(2) Draft the auditor's report including: opinion paragraph, basis for opinion,
    key audit matters (ISA 701), responsibilities sections
(3) Draft management letter with control deficiencies and recommendations
Save report to /output/audit/[YEAR]/10-audit-report.md.
Save management letter to /output/audit/[YEAR]/10-management-letter.md.
```

**Expected output**: Draft auditor's report with opinion, key audit matters, and responsibilities; management letter with prioritized recommendations
**Human checkpoint**: This is the highest-judgment step. The engagement partner must: (1) confirm the opinion type is correct, (2) review key audit matters for appropriateness and completeness, (3) review management letter for accuracy and tone. Only the engagement partner signs the report.

### Step 11: Audit File Compilation

```
Compile the final audit file:
(1) File index — all working papers cross-referenced
(2) Engagement completion checklist per ISQM 1
(3) Independence confirmation
(4) Analytical review of final financial statements
(5) Subsequent events review through date of report
(6) Going concern assessment documentation
(7) Quality control review notes (if applicable)
Save to /output/audit/[YEAR]/11-audit-file-index.md.
```

**Expected output**: Audit file index with cross-references, completion checklist with status of each required procedure
**Human checkpoint**: Engagement quality reviewer (if applicable) reviews the file. Confirm all ISA requirements addressed. Verify file assembly deadline compliance (ISA 230 — 60 days after report date). Archive the completed audit file.

## Output Artifacts

- `/output/audit/[YEAR]/01-preliminary-analytics.md` — Analytical procedures and flagged balances
- `/output/audit/[YEAR]/02-materiality.md` — Materiality calculation and rationale
- `/output/audit/[YEAR]/03-risk-assessment.md` — Risk assessment matrix
- `/output/audit/[YEAR]/04-audit-programme.md` — Detailed audit programme
- `/output/audit/[YEAR]/05-revenue-receivables-testing.md` — Revenue and receivables test results
- `/output/audit/[YEAR]/06-ppe-testing.md` — PPE and depreciation test results
- `/output/audit/[YEAR]/07-controls-testing/` — SOX/controls test documentation
- `/output/audit/[YEAR]/08-other-substantive.md` — Other substantive procedure results
- `/output/audit/[YEAR]/09-misstatement-evaluation.md` — Schedule of unadjusted differences
- `/output/audit/[YEAR]/10-audit-report.md` — Draft auditor's report
- `/output/audit/[YEAR]/10-management-letter.md` — Management letter
- `/output/audit/[YEAR]/11-audit-file-index.md` — File index and completion checklist

## Quality Checks

- Every significant account has at least one substantive procedure addressing each relevant assertion
- All fraud risks per ISA 240 are documented with specific responses
- Materiality calculated and approved before fieldwork begins
- All misstatements evaluated individually and in aggregate against materiality
- Audit opinion supported by documented evidence for each significant finding
- File assembly completed within 60 days of report date (ISA 230)
- Engagement quality review completed (if applicable per ISQM 1)

## Customize This

| Variable                | Default (Pakistan)                        | What to change                                   |
| ----------------------- | ----------------------------------------- | ------------------------------------------------ |
| Jurisdiction            | Pakistan (SECP)                           | Your local company regulator                     |
| Currency                | PKR                                       | Your reporting currency                          |
| Auditing standards      | ISA (International Standards on Auditing) | PCAOB (US), or local auditing standards          |
| Reporting framework     | IFRS                                      | US GAAP, FRS 101/102, or local GAAP              |
| Materiality benchmark   | 2% of revenue                             | Your firm's benchmark policy (5% PBT, 1% assets) |
| Performance materiality | 75% of overall materiality                | Your firm's policy (typically 50-75%)            |
| Trivial threshold       | 5% of overall materiality                 | Your firm's trivial amount policy                |
| File assembly deadline  | 60 days per ISA 230                       | Your firm/jurisdiction's assembly period         |
| Quality review          | ISQM 1 requirements                       | Your firm's quality control procedures           |
| Controls framework      | COSO / ISA 315                            | SOX Section 404 (if US-listed entity)            |
