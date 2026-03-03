# Compliance Monitoring

## Overview

Automated weekly compliance calendar monitoring workflow that scans upcoming regulatory filing deadlines across all applicable bodies (FBR, SECP, SBP, EOBI, PESSI), checks filing and document preparation status, generates preparation reminders with required information checklists, and assesses penalty risk for any deadlines at risk of being missed.

## Schedule

- **Frequency**: Weekly (every Monday at 07:00)
- **Trigger**: Automated scheduled task
- **Duration**: ~20 minutes execution; review ~15 minutes

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (for cross-referencing financial data when preparing filings)
- **Data inputs**: Regulatory compliance calendar (CSV with all filing obligations), prior filing status log, entity registration details (NTN, company registration number, SBP license details if applicable)
- **SKILL.md extensions**: `compliance-calendar` (Pakistan regulatory obligations, penalty matrices, filing requirements), `pakistan-tax-jurisdiction` (FBR filing calendar and penalty provisions)
- **Cowork global instruction**: Set entity type, applicable regulatory bodies, financial year end, alert lead time preferences

## Steps

### Step 1: Deadline Scanning (30-Day Forward Window)

```
Read the regulatory compliance calendar from
skills/compliance-calendar/assets/regulatory-calendar.csv.

Scan for all deadlines within the next 30 days:
(1) FBR deadlines — monthly withholding tax statements (7th of following month),
    sales tax returns (15th), advance tax instalments (quarterly), annual return
(2) SECP deadlines — annual return filing, Form A/Form 29 changes, beneficial
    ownership declarations, annual general meeting notice
(3) SBP deadlines (if applicable) — prudential returns, foreign exchange reports,
    currency transaction reports
(4) EOBI deadlines — monthly contribution remittance (15th of following month)
(5) PESSI deadlines — monthly contribution remittance (provincial schedule)

For each deadline, extract: regulatory body, filing type, due date, days remaining,
penalty for late filing, responsible person.

Save to /output/compliance/[YYYY-WW]/01-upcoming-deadlines.md.
```

**Expected output**: Table of all deadlines within 30-day window, sorted by due date, with days remaining and penalty exposure for each
**Human checkpoint**: Review deadline list for completeness. Confirm no new regulatory requirements have been introduced since the calendar was last updated. Flag any deadlines that fall on public holidays (filing may be due on the preceding business day).

### Step 2: Filing Status Check

```
Cross-reference the upcoming deadlines (Step 1) against the prior filing status log
from /data/compliance/filing-status-[YEAR].csv.

For each upcoming deadline, determine status:
(1) Filed — confirmation number and date recorded
(2) In Progress — preparation started, estimated completion date
(3) Not Started — preparation has not begun
(4) Overdue — deadline has passed without filing (CRITICAL ALERT)

Also check the prior 30 days for any deadlines that were marked "In Progress"
but have not been updated to "Filed" — these may be stale.

Save to /output/compliance/[YYYY-WW]/02-filing-status.md.
```

**Expected output**: Filing status dashboard showing each deadline with current status, traffic light (Green = Filed, Amber = In Progress, Red = Not Started or Overdue)
**Human checkpoint**: Verify "Filed" statuses have valid confirmation numbers. Investigate any "Not Started" items with fewer than 14 days remaining — these are at risk. Escalate any "Overdue" items immediately.

### Step 3: Document Preparation Checklists

```
For each deadline with status "Not Started" or "In Progress" from Step 2,
generate a preparation checklist:

For FBR monthly WHT statement:
- [ ] WHT deduction register for the month
- [ ] CPR numbers of all deductees verified
- [ ] Challan payment confirmation from bank
- [ ] E-filing portal credentials available
- [ ] Supporting schedule by WHT section (148, 149, 151, 153, etc.)

For SECP annual return:
- [ ] Audited financial statements
- [ ] Board resolution for filing authorization
- [ ] Updated Form A (registered office details)
- [ ] Beneficial ownership register current
- [ ] Filing fee calculated and payment arranged
- [ ] eServices portal credentials available

Generate similar checklists for SBP, EOBI, and PESSI filings as applicable.

Save to /output/compliance/[YYYY-WW]/03-preparation-checklists.md.
```

**Expected output**: Filing-specific preparation checklists with all required documents and information items listed; items that can be auto-verified marked as complete/incomplete
**Human checkpoint**: Work through each checklist. Identify any missing documents that require action from other departments (e.g., audited financials from external auditor, board resolution from company secretary). Assign responsibility and deadline for each incomplete item.

### Step 4: Penalty Risk Assessment

```
For each deadline at risk (status "Not Started" with fewer than 14 days remaining,
or status "Overdue"), calculate penalty exposure:

FBR penalties (Income Tax Ordinance 2001):
- Late filing: PKR 2,500 per day for WHT statements
- Non-filing: Additional tax at KIBOR + 3% on tax payable
- Sales tax late filing: PKR 5,000 + PKR 100/day

SECP penalties (Companies Act 2017):
- Annual return late: PKR 50 per day (Level 3 default penalty)
- Failure to file Form A changes: PKR 25,000 + PKR 500/day

SBP penalties:
- Late prudential returns: SBP discretionary fine per BPRD circular

For each at-risk deadline, provide:
(1) Current penalty exposure (if already overdue, calculate accumulated penalty)
(2) Projected penalty if filed by [today + 7 days] vs [today + 14 days] vs [today + 30 days]
(3) Maximum penalty cap (if applicable)
(4) Recommended action priority: Immediate / This Week / Can Wait

Save to /output/compliance/[YYYY-WW]/04-penalty-risk.md.
```

**Expected output**: Penalty exposure schedule showing current and projected penalties for each at-risk deadline, with recommended action priority
**Human checkpoint**: Review penalty projections. For any item with penalty exposure exceeding PKR 100,000, escalate to senior management. Authorize expedited preparation for all "Immediate" priority items. Document any strategic decisions to accept penalties (rare, but sometimes commercially rational for very minor filings).

### Step 5: Weekly Compliance Status Report

```
Compile the weekly compliance status report:
(1) Executive summary — total obligations tracked, filings completed this week,
    filings due next 7 days, at-risk items
(2) 30-day forward calendar — visual timeline of upcoming deadlines
(3) Status dashboard — all obligations with traffic light status
(4) Penalty exposure summary — total current + projected exposure
(5) Action items — assigned responsibilities with deadlines
(6) Trend: compare this week's at-risk count to prior 4 weeks (improving/deteriorating)

Save to /output/compliance/[YYYY-WW]/05-weekly-status-report.md.
```

**Expected output**: One-page weekly compliance status report suitable for management review, with trend analysis
**Human checkpoint**: Review and distribute to relevant stakeholders. Update the filing status log with any completions from the past week. Ensure action items have been acknowledged by assigned personnel.

### Step 6: Calendar Update and Next-Week Preparation

```
Update the compliance calendar with:
(1) Mark any filed obligations as complete with confirmation details
(2) Roll forward any recurring obligations to their next due date
(3) Check for any new regulatory circulars or notifications that may
    introduce new filing obligations (flag for human review)
(4) Generate next week's preview — deadlines falling in days 8-14

Save updated calendar to /data/compliance/filing-status-[YEAR].csv.
Save next-week preview to /output/compliance/[YYYY-WW]/06-next-week-preview.md.
```

**Expected output**: Updated filing status log and next-week preview enabling proactive preparation
**Human checkpoint**: Review next-week preview. Initiate preparation for any complex filings due in weeks 2-3. Confirm that the calendar reflects any new regulatory requirements from recent circulars.

## Output Artifacts

- `/output/compliance/[YYYY-WW]/01-upcoming-deadlines.md` — 30-day forward deadline scan
- `/output/compliance/[YYYY-WW]/02-filing-status.md` — Filing status dashboard with traffic lights
- `/output/compliance/[YYYY-WW]/03-preparation-checklists.md` — Filing-specific document checklists
- `/output/compliance/[YYYY-WW]/04-penalty-risk.md` — Penalty exposure assessment
- `/output/compliance/[YYYY-WW]/05-weekly-status-report.md` — Weekly compliance status report
- `/output/compliance/[YYYY-WW]/06-next-week-preview.md` — Next-week deadline preview

## Quality Checks

- All regulatory bodies applicable to the entity are included in the calendar (no gaps)
- Filing status log updated weekly (no stale "In Progress" items older than 30 days)
- Penalty calculations reference current penalty rates (verify annually when rates change)
- At-risk items escalated within 24 hours of identification
- Preparation checklists cover all required documents (verified against regulatory portal requirements)
- Week-over-week trend shows sustained improvement (at-risk count declining over time)
- Calendar covers full financial year cycle (no deadlines missing from annual scan)

## Customize This

| Variable             | Default (Pakistan)                              | What to change                                      |
| -------------------- | ----------------------------------------------- | --------------------------------------------------- |
| Jurisdiction         | Pakistan (FBR, SECP, SBP, EOBI, PESSI)          | Your jurisdiction's regulatory bodies               |
| Currency             | PKR                                             | Your reporting currency                             |
| Regulatory bodies    | FBR, SECP, SBP, EOBI, PESSI                     | Your applicable regulators (IRS, SEC, HMRC, etc.)   |
| Filing deadlines     | Pakistan statutory calendar                     | Your jurisdiction's filing calendar                 |
| Penalty rates        | ITO 2001 / Companies Act 2017 rates             | Your jurisdiction's penalty provisions              |
| Alert lead time      | 30 days forward scan, 14 days at-risk threshold | Your firm's early warning policy                    |
| Monitoring frequency | Weekly (Monday 07:00)                           | Your compliance calendar granularity                |
| Escalation threshold | PKR 100,000 penalty exposure                    | Your entity's materiality for compliance escalation |
| E-filing portals     | FBR IRIS, SECP eServices                        | Your jurisdiction's electronic filing systems       |
