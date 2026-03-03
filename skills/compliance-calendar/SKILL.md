---
name: compliance-calendar
description: |
  Extension encoding regulatory compliance calendar: filing deadlines,
  information checklists, penalty matrices, and automated monitoring
  schedules. Ships with Pakistan regulatory obligations (FBR, SECP, SBP).
license: Apache-2.0
metadata:
  author: panaversity
  version: "1.0"
  chapter: "19"
  domain: "extension-5"
---

# Regulatory Compliance Calendar Extension

## Purpose

This extension encodes a regulatory compliance calendar as standing instructions for automated compliance monitoring. When loaded alongside the grc-advisory agent or any domain agent, it enables scheduled deadline tracking: the agent checks upcoming obligations, confirms preparation status, and alerts the practitioner when lead time is insufficient. This template ships with Pakistan regulatory obligations (FBR, SECP, SBP). Adapt for your jurisdiction by replacing the obligations, deadlines, and penalty provisions.

## Instructions

### Filing Obligations by Entity Type

When monitoring compliance for an entity, first confirm the entity type to determine which obligations apply:

**Public Listed Company (listed on PSX):**
All obligations below apply. Additionally: PSX listing regulations, quarterly reporting to PSX, annual general meeting within specified timeframe, and XBRL filing to SECP.

**Private Limited Company:**
FBR obligations (income tax, sales tax, WHT), SECP annual filings (annual return, financial statements), and employer-related obligations (EOBI, social security).

**Association of Persons (AOP):**
FBR income tax obligations only. No SECP filing requirements.

**Individual (sole proprietor or professional):**
FBR income tax return. Professional body requirements (ICAP CPD, renewal) where applicable.

### FBR (Federal Board of Revenue) Obligations

| Obligation                    | Frequency | Deadline                       | Lead Time       | Information Required                                                            |
| ----------------------------- | --------- | ------------------------------ | --------------- | ------------------------------------------------------------------------------- |
| Corporate income tax return   | Annual    | Sep 30 (for July-June FY)      | 45 working days | Final accounts, tax computation, WHT certificates, depreciation schedule        |
| Individual income tax return  | Annual    | Sep 30                         | 20 working days | Salary certificates, bank statements, property details, investment certificates |
| Advance tax (quarterly)       | Quarterly | Sep 15, Dec 15, Mar 15, Jun 15 | 10 working days | Estimated taxable income, prior year liability                                  |
| WHT monthly statement         | Monthly   | 15th of following month        | 5 working days  | Payroll data, vendor payments, contract details                                 |
| Annual WHT reconciliation     | Annual    | Within 2 months of FY end      | 15 working days | Complete WHT deduction records, annual payroll summary                          |
| Sales tax return (federal)    | Monthly   | 18th of following month        | 5 working days  | Sales and purchase invoices, input/output tax summaries                         |
| Sales tax return (provincial) | Monthly   | 15th-18th (varies by province) | 5 working days  | Province-wise service revenue, input tax claims                                 |

### SECP (Securities and Exchange Commission of Pakistan) Obligations

| Obligation                      | Frequency    | Deadline                                                      | Lead Time            | Information Required                                      |
| ------------------------------- | ------------ | ------------------------------------------------------------- | -------------------- | --------------------------------------------------------- |
| Annual return (Form A)          | Annual       | Within 30 days of AGM                                         | 10 working days      | Shareholder register, director details, registered office |
| Annual financial statements     | Annual       | File within 30 days of AGM                                    | Per audit completion | Audited financial statements, directors' report           |
| Annual general meeting          | Annual       | Within 120 days of FY end (public), within 180 days (private) | 30 working days      | Notice, agenda, audited accounts, proxy forms             |
| Change of directors (Form 29)   | Event-driven | Within 15 days of change                                      | 3 working days       | Board resolution, new director's particulars, consent     |
| Beneficial ownership (Form 45)  | Event-driven | Within 30 days of obtaining info                              | 5 working days       | Beneficial owner details per SECP regulations             |
| Quarterly accounts (listed cos) | Quarterly    | Within 30 days of quarter end                                 | 15 working days      | Reviewed quarterly financial statements                   |

### SBP (State Bank of Pakistan) Obligations

Applicable to banking companies and entities with foreign exchange transactions:

| Obligation                      | Frequency         | Deadline                                         | Lead Time       | Information Required                               |
| ------------------------------- | ----------------- | ------------------------------------------------ | --------------- | -------------------------------------------------- |
| Foreign exchange reporting      | Transaction-based | Per SBP timeline (varies)                        | 3 working days  | FE transaction details, purpose, supporting docs   |
| Export proceeds realisation     | Per shipment      | Within 120 days of shipment (textiles: 180 days) | Monitor ongoing | GD, bill of lading, bank credit advice             |
| Borrowing from abroad reporting | Event-driven      | Prior approval required                          | 20 working days | Loan agreement, terms, purpose, repayment schedule |

### Employer-Related Obligations

| Obligation                          | Frequency          | Deadline                | Lead Time      | Information Required                             |
| ----------------------------------- | ------------------ | ----------------------- | -------------- | ------------------------------------------------ |
| EOBI contribution                   | Monthly            | 15th of following month | 5 working days | Employee register, salary data                   |
| Provincial social security          | Monthly            | 15th of following month | 5 working days | Employee register, salary data, coverage details |
| Professional tax (where applicable) | Annual/Semi-annual | Per provincial schedule | 5 working days | Employee headcount by salary bracket             |

### Penalty Matrix

When assessing the cost of non-compliance, apply these penalty provisions:

**FBR Penalties:**

- Late filing of income tax return: PKR 40,000 or 0.1% of tax payable per day, whichever is higher.
- Late payment of tax: Default surcharge at KIBOR + 3% per annum.
- Late filing of WHT statement: PKR 2,500 per day of default.
- Late filing of sales tax return: Higher of PKR 5,000 or 0.1% of tax due per day.

**SECP Penalties:**

- Late filing of annual return: PKR 100 per day (up to PKR 50,000 for private companies).
- Failure to hold AGM: Fine up to PKR 1 million and PKR 25,000 per day of continuing default.
- Late filing of Form 29: PKR 500 per day.
- Non-filing of beneficial ownership: Fine up to PKR 10 million.

**SBP Penalties:**

- Failure to realise export proceeds: SBP may impose penalties and restrict future FE facilities.
- Non-compliance with foreign borrowing conditions: Loan may be treated as unauthorised.

### Automated Monitoring Schedule

When running scheduled compliance checks (weekly recommended):

1. **Calculate days remaining** for each upcoming obligation within the next 60 days.
2. **Compare against lead time**: If days remaining < lead time required, generate an alert.
3. **Check preparation status**: For each upcoming obligation, confirm with the user whether the required information is available. If not, list the missing items.
4. **Priority classification**:
   - RED: Deadline within lead time and information incomplete — immediate action required.
   - AMBER: Deadline within 2x lead time — preparation should begin.
   - GREEN: Deadline beyond 2x lead time — no action required yet.
5. **Generate compliance report**: List all obligations by priority (RED first), with deadline, days remaining, preparation status, and required actions.

### Escalation Conditions

Flag to the user for immediate attention when:

- Any obligation is in RED status (deadline within lead time, information incomplete).
- A filing requires a complex position (e.g., income tax return with uncertain deductions, contested assessments).
- A deadline has been missed — compute the penalty exposure and recommend remediation steps.
- New regulatory requirements have been announced that create additional obligations (new SROs, amendments to Companies Act).
- The entity type has changed (e.g., conversion from private to public) which triggers new obligations.

## Domain Context

This extension is loaded alongside the grc-advisory agent (Domain 5) or any domain agent that needs compliance awareness. Pakistan's regulatory environment involves three primary regulators (FBR, SECP, SBP) with overlapping and sometimes inconsistent filing requirements. Provincial variations apply for sales tax on services and employer obligations. This calendar covers federal and major provincial obligations — practitioners in specific provinces should add province-specific deadlines. The companion asset file `regulatory-calendar.csv` provides the obligations in importable format for scheduling tools.

## Constraints

- NEVER file returns or submit documents on behalf of the user — monitoring and preparation only
- NEVER present these deadlines as guaranteed current — regulatory deadlines are subject to extension by government notification
- NEVER assume the entity type — always confirm before applying the relevant obligation set
- NEVER ignore provincial variations — sales tax, social security, and professional tax vary by province
- NEVER treat a GREEN status obligation as "no action needed" — it means no action needed YET
- This extension is a TEMPLATE — practitioners must verify all deadlines against current regulations before relying on them in practice
