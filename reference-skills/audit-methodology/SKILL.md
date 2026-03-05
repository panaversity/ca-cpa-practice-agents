---
name: audit-methodology
description: |
  Extension encoding audit methodology standards: materiality calculation,
  sampling methodology, documentation requirements, escalation procedures,
  and quality control per ISA standards.
license: Apache-2.0
metadata:
  author: panaversity
  version: "1.0"
  chapter: "19"
  domain: "extension-3"
---

# Audit Methodology Extension

## Purpose

This extension encodes a firm's audit methodology standards as standing instructions for the assurance agent. When loaded, the agent applies these specific methodology choices — materiality benchmarks, sampling approaches, documentation standards, and escalation triggers — instead of generic audit procedures. Practitioners must customise this extension to match their firm's actual methodology manual.

## Instructions

### Materiality Calculation Methodology

When calculating materiality for an audit engagement, apply the following framework:

**Step 1 — Select the benchmark:**

- For-profit entities: Pre-tax profit from continuing operations (primary benchmark).
- If pre-tax profit is volatile (coefficient of variation > 30% over 3 years), use revenue as the benchmark instead.
- Loss-making entities: Revenue (primary) or total assets (secondary, for asset-intensive entities).
- Not-for-profit entities: Total expenses or total revenue, whichever is more stable.
- Public interest entities: Use the lower of two benchmark calculations to reflect heightened user expectations.

**Step 2 — Apply the percentage:**

- Pre-tax profit benchmark: 5% (standard), 3-4% (public interest entities or higher-risk engagements).
- Revenue benchmark: 0.5% to 1% (use the lower end for entities with tight margins).
- Total assets benchmark: 1% to 2%.
- Document the rationale for the specific percentage chosen within the range.

**Step 3 — Calculate performance materiality:**

- 65% of overall materiality (standard engagements).
- 50-60% of overall materiality (higher-risk engagements — first year audit, history of adjustments, weak internal controls).
- Document the risk factors that determined the percentage.

**Step 4 — Set the trivial threshold (Clearly Trivial):**

- 5% of overall materiality.
- Misstatements below this threshold are not accumulated unless they are qualitatively significant (e.g., related party, management remuneration, fraud).

**Step 5 — Document and review:**

- Materiality must be documented at the planning stage and reconsidered at completion when final financial results are available.
- If the final materiality is lower than the planning materiality, evaluate whether additional audit procedures are required for the affected areas.

### Sampling Methodology

When selecting items for testing, apply these minimum sample sizes:

**Statistical sampling (for substantive tests of details):**

| Population Size | Low Risk  | Medium Risk | High Risk |
| --------------- | --------- | ----------- | --------- |
| < 50 items      | All items | All items   | All items |
| 50-250 items    | 10        | 15          | 25        |
| 251-500 items   | 15        | 25          | 40        |
| 501-1000 items  | 20        | 30          | 50        |
| > 1000 items    | 25        | 40          | 60        |

**Non-statistical sampling (for tests of controls):**

- Controls operating daily: Minimum 25 items (one per working day for a month, extended if exceptions found).
- Controls operating weekly: Minimum 5 items.
- Controls operating monthly: Minimum 2 items.
- Controls operating quarterly: All 4 occurrences.
- Controls operating annually: The single occurrence plus the supporting documentation.

**When exceptions are found:**

- 1 exception in sample: Increase sample by 50% and investigate the root cause.
- 2+ exceptions in sample: Consider the control or balance unreliable. Escalate to the engagement manager/partner and redesign the audit approach.

### Documentation Standards

Every audit working paper must contain:

1. **Working paper reference**: Unique identifier cross-referenced to the audit programme.
2. **Preparer and date**: Who prepared the working paper and when.
3. **Reviewer and date**: Who reviewed it and when (leave blank for the reviewer to complete).
4. **Objective**: The specific audit objective this working paper addresses.
5. **Source of data**: Where the data tested came from (client system, confirmation, bank statement).
6. **Work performed**: Step-by-step description of the procedure, sufficient for an experienced auditor to understand what was done without needing supplementary explanation.
7. **Results**: Findings stated factually — what was found, not what was expected.
8. **Exceptions**: Each exception listed with: item reference, nature of exception, financial impact (actual and projected), and disposition (adjust/reclassify/waive with rationale).
9. **Conclusion**: Whether the objective was achieved, with cross-reference to the assertion and risk being addressed.

**Sign-off requirements:**

- All working papers must be prepared and reviewed before the audit report is signed.
- Working papers for significant risk areas must be reviewed by the engagement partner, not only the manager.
- Any working paper with unresolved exceptions must be escalated before sign-off.

### Escalation Triggers

The following conditions require immediate escalation to the engagement partner (do not continue procedures without partner direction):

1. **Fraud indicators**: Unusual journal entries (post-closing, round amounts, unusual accounts), management override of controls, unexplained adjustments, tips or allegations.
2. **Going concern doubt**: Net current liability position exceeding 50% of net assets, recurring operating losses for 2+ years, covenant breach or approaching covenant limits, loss of major customer or key personnel.
3. **Scope limitations**: Client refuses access to records, key personnel unavailable, inability to attend inventory count, limitations on confirmation procedures.
4. **Material misstatements**: Any individual misstatement exceeding performance materiality. Aggregate misstatements exceeding 75% of overall materiality.
5. **Significant estimates**: Fair value measurements with high uncertainty, litigation provisions, impairment of goodwill or intangibles, expected credit loss models with significant judgment.
6. **Independence threats**: Any new relationship, financial interest, or business transaction identified during the engagement.
7. **Disagreement with management**: On accounting treatment, disclosure adequacy, or going concern assessment.

### Independence and Rotation

- Confirm independence declarations are on file for all engagement team members before commencing fieldwork.
- For listed entity audits: engagement partner rotation required every 5 years (3 years cooling-off). Key audit partners rotation per local regulations.
- Document any new independence threats identified during the engagement and the safeguards applied.

## Domain Context

This extension is loaded alongside the assurance agent skill (Domain 3). It encodes a firm's specific methodology choices that go beyond the minimum requirements of ISA. The materiality benchmarks, sampling tables, and escalation triggers in this template are based on common practice across mid-tier firms — large firms (Big Four) may have different thresholds, and smaller firms may apply simplified approaches for smaller engagements. Practitioners must verify these parameters match their firm's methodology manual.

## Constraints

- NEVER reduce sample sizes below the minimums specified in this extension, even if the agent assesses risk as low
- NEVER skip the escalation triggers — if a condition is met, escalation is mandatory regardless of the agent's assessment of severity
- NEVER sign off working papers — the preparer and reviewer fields are for the human audit team
- NEVER adjust the materiality threshold downward during the engagement without recalculating and documenting the rationale
- This extension is a TEMPLATE — firms must replace these parameters with their own methodology before use in live engagements
