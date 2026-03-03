# Board Pack

## Overview

Cross-application workflow automating board pack preparation from Excel financial data through PowerPoint presentation. Extracts financial results, computes KPIs, generates variance commentary, and produces a board-ready slide deck — compressing what typically requires several hours of skilled work into a single Cowork orchestration with practitioner review at each stage.

## Schedule

- **Frequency**: Quarterly (or monthly if board meets monthly)
- **Trigger**: Month-end close completion (depends on `month-end-close` workflow)
- **Duration**: ~1.5 hours execution + review; replaces ~6 hours of manual preparation

## Prerequisites

- **Plugins**: `finance@knowledge-work-plugins` (`/variance-analysis`, `/income-statement`), Claude in Excel, Claude in PowerPoint
- **Data inputs**: Management accounts (from month-end close output), annual budget file (Excel), prior year comparatives, KPI target definitions, board pack template (PowerPoint)
- **SKILL.md extensions**: `client-entity` (entity KPI definitions, board reporting preferences), `management-accounting` (variance thresholds, commentary standards)
- **Cowork global instruction**: Set entity context, board meeting date, reporting period, currency, presentation brand guidelines
- **Requirements**: Mac users on Max, Team, or Enterprise plan with Claude in Excel and Claude in PowerPoint installed

## Steps

### Step 1: Data Extraction and Validation

```
Read the management accounts from /output/month-end/[YYYY-MM]/05-financial-statements/
and the annual budget from /data/board-pack/budget-[YEAR].xlsx.

Extract and validate:
(1) Income statement — actual, budget, prior year, prior month
(2) Balance sheet — current and prior period
(3) Cash flow statement — current period
(4) Verify all figures tie to the month-end close output (cross-cast check)

Save extracted data to /output/board-pack/[YYYY-MM]/01-data-extract.md.
```

**Expected output**: Structured data extract with all four comparative columns validated and cross-referenced to source files
**Human checkpoint**: Confirm data ties to approved management accounts. Verify budget figures match the latest approved budget (not a superseded version). Check prior year figures match audited financial statements.

### Step 2: KPI Dashboard Computation

```
Using the extracted data (Step 1), compute the entity's KPI dashboard:

Financial KPIs:
(1) Revenue — actual vs budget vs prior year (absolute and %)
(2) Gross margin % — actual vs budget vs prior year
(3) EBITDA and EBITDA margin — actual vs budget
(4) Net profit margin — actual vs budget
(5) Operating cash flow — actual vs forecast

Operational KPIs:
(6) Receivables days (DSO) — current vs target vs prior period
(7) Payables days (DPO) — current vs target vs prior period
(8) Inventory days (if applicable) — current vs target
(9) Current ratio — current vs prior period
(10) Net debt / EBITDA — current vs covenant threshold

Traffic light each KPI: Green (within 5% of target), Amber (5-15% variance),
Red (>15% variance or covenant breach risk).

Save to /output/board-pack/[YYYY-MM]/02-kpi-dashboard.md.
```

**Expected output**: KPI dashboard with 10 metrics, traffic light status, and trend arrows (improving/deteriorating vs prior period)
**Human checkpoint**: Review traffic light assignments. Override any where the automated threshold does not capture the business context (e.g., a planned investment causing temporary cash flow deterioration should not be flagged red). Add any entity-specific KPIs not in the standard set.

### Step 3: Variance Analysis and Commentary

```
/variance-analysis monthly
```

```
Using the variance analysis output, prepare board-level commentary:
(1) Top 5 favourable variances — ranked by absolute PKR impact
(2) Top 5 adverse variances — ranked by absolute PKR impact
(3) For each variance, draft a 2-3 sentence explanation covering:
    - What happened (the fact)
    - Why it happened (the driver)
    - What is being done about it (the action — mark [PRACTITIONER INPUT] if unknown)
(4) Revenue bridge: budget → volume → price → mix → actual
(5) Cost bridge: budget → inflation → volume → efficiency → actual

Save to /output/board-pack/[YYYY-MM]/03-variance-commentary.md.
```

**Expected output**: Structured variance commentary for top 10 variances with bridge decompositions; action items marked for practitioner input
**Human checkpoint**: This is the highest-value step. The practitioner adds business context that the agent cannot know: why a customer order was delayed, which cost savings initiative drove the improvement, what management action is planned for adverse variances. Complete all `[PRACTITIONER INPUT]` sections.

### Step 4: Executive Summary

```
Draft a one-page executive summary for the board chair:
(1) Headline: "[Period] financial performance — [one sentence verdict]"
(2) Three key positives (with PKR quantification)
(3) Three key concerns (with PKR quantification and management response)
(4) Cash position and forecast — current month-end cash, 3-month forward view
(5) Outlook statement placeholder: [PRACTITIONER INPUT — management's forward view]

Keep language non-technical. Board members may not be financial professionals.
Save to /output/board-pack/[YYYY-MM]/04-executive-summary.md.
```

**Expected output**: One-page executive summary in plain language with quantified highlights and a practitioner input placeholder for the outlook
**Human checkpoint**: Review tone and emphasis. Ensure positives and concerns are balanced and accurately represent management's view. Complete the outlook statement. Verify that the summary is consistent with the detailed variance commentary.

### Step 5: Slide Generation (Cross-App)

```
Take the following outputs and create a board presentation in PowerPoint:

Slide 1 — Title slide: "[Entity Name] — Board Update [Period]"
Slide 2 — Executive Summary (from Step 4)
Slide 3 — P&L: Actual vs Budget table with variance column (from Step 1)
Slide 4 — KPI Dashboard with traffic lights (from Step 2)
Slide 5 — Top 5 variance drivers with bridge chart (from Step 3)
Slide 6 — Rolling 12-month revenue and EBITDA trend (line chart)
Slide 7 — Cash flow bridge: opening → operating → investing → financing → closing
Slide 8 — Key risks and actions (from variance commentary actions)

Use the board pack template from /data/board-pack/template.pptx for branding.
Save to /output/board-pack/[YYYY-MM]/05-board-pack.pptx.
```

**Expected output**: 8-slide PowerPoint deck formatted to entity branding, with charts, tables, and commentary populated from prior steps
**Human checkpoint**: Review every slide for: (1) accuracy of figures, (2) chart readability, (3) appropriate level of detail for board audience, (4) branding compliance. Adjust any auto-generated charts that do not render clearly. Add any supplementary slides requested by the board chair.

### Step 6: Supporting Schedules Pack

```
Compile supporting schedules for board members who want detail beyond the slides:
(1) Full income statement with 4 comparative columns
(2) Full balance sheet with comparative
(3) Cash flow statement
(4) Detailed variance analysis (all accounts, not just top 10)
(5) Aged receivables summary
(6) Capital expenditure tracker vs approved budget

Save to /output/board-pack/[YYYY-MM]/06-supporting-schedules.md.
```

**Expected output**: Comprehensive supporting schedules document that backs up every figure in the slide deck
**Human checkpoint**: Verify figures are consistent between slides and supporting schedules. Confirm supporting schedules are formatted for readability. Package slides + supporting schedules for distribution.

## Output Artifacts

- `/output/board-pack/[YYYY-MM]/01-data-extract.md` — Validated data extract from management accounts
- `/output/board-pack/[YYYY-MM]/02-kpi-dashboard.md` — KPI dashboard with traffic lights
- `/output/board-pack/[YYYY-MM]/03-variance-commentary.md` — Variance analysis with bridge decomposition
- `/output/board-pack/[YYYY-MM]/04-executive-summary.md` — One-page executive summary
- `/output/board-pack/[YYYY-MM]/05-board-pack.pptx` — Board presentation slides
- `/output/board-pack/[YYYY-MM]/06-supporting-schedules.md` — Detailed supporting schedules

## Quality Checks

- All figures in slides tie to supporting schedules (zero tolerance for discrepancies)
- KPI traffic lights reflect current period performance (not stale targets)
- Variance commentary covers at least top 5 favourable and top 5 adverse variances
- Executive summary is comprehensible to a non-financial board member
- All `[PRACTITIONER INPUT]` placeholders completed before distribution
- Board pack distributed at least 5 business days before the board meeting

## Customize This

| Variable                | Default (Pakistan)                            | What to change                                |
| ----------------------- | --------------------------------------------- | --------------------------------------------- |
| Jurisdiction            | Pakistan (SECP)                               | Your corporate governance regulator           |
| Currency                | PKR                                           | Your reporting currency                       |
| Board meeting frequency | Quarterly                                     | Your entity's board calendar                  |
| KPI framework           | SECP reporting requirements + entity-specific | Your governance code's required disclosures   |
| Variance thresholds     | Green <5%, Amber 5-15%, Red >15%              | Your entity's materiality thresholds          |
| Presentation template   | Standard Cowork format                        | Your firm's branded PowerPoint template       |
| Slide count             | 8 slides                                      | Your board's preferred pack length            |
| Distribution lead time  | 5 business days before meeting                | Your board charter's distribution requirement |
| Comparative periods     | Budget + prior year + prior month             | Your board's preferred comparatives           |
