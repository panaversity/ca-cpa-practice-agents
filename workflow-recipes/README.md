# Workflow Recipes

Natural language scheduling templates for Cowork's `/schedule` command. Each recipe describes a multi-step workflow that chains Anthropic plugin commands with your domain knowledge.

## How to Use

1. Open a recipe file (e.g., `month-end-close.md`)
2. Read the workflow steps and adapt for your practice
3. Copy the scheduling text into Cowork's `/schedule` command

Example:

```
/schedule "On the 1st business day of each month at 7:00 AM:
Run the month-end close sequence — reconcile bank, debtors,
and creditors; post depreciation and accrual journals; generate
the income statement; flag any reconciliation difference above
the configured threshold."
```

## Available Recipes

| Recipe                     | Domain                | Frequency      | What It Does                                                       |
| -------------------------- | --------------------- | -------------- | ------------------------------------------------------------------ |
| `month-end-close.md`       | Accounting            | Monthly        | Reconcile, journal, income statement, variance analysis            |
| `board-pack.md`            | Management Accounting | Monthly        | Management accounts, variance bridge, Excel + PowerPoint output    |
| `tax-computation.md`       | Tax                   | As needed      | Tax liability computation with jurisdiction-specific rules         |
| `audit-programme.md`       | Assurance             | Per engagement | Risk assessment, materiality, sample selection                     |
| `compliance-monitoring.md` | GRC                   | Weekly         | Scan obligations, calculate days until due, flag Red zone items    |
| `fraud-monitoring.md`      | GRC                   | Weekly         | Duplicate payments, ghost vendors, threshold-adjacent transactions |

## Customization

Each recipe includes Pakistan-default thresholds and references. Replace with your jurisdiction's values before scheduling.
