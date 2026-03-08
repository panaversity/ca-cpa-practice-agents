# Exercise Data Files

This directory contains data files used by the practice exercises in Chapter 19.

## Folder Structure

| Directory           | Contents                                                                      | Used By                   |
| ------------------- | ----------------------------------------------------------------------------- | ------------------------- |
| `trial-balances/`   | PKR IFRS trial balance data — June 2025 (year-end) and May 2025 (prior month) | Exercises 1, 6, 8-11      |
| `bank-statements/`  | National Bank of Pakistan statement with reconciling items                    | Exercise 6                |
| `budgets/`          | Annual and monthly budget with variance analysis and root causes              | Exercise 6                |
| `ar-aging/`         | Aged receivables schedule with ECL assessment                                 | Exercise 6, 12            |
| `source-documents/` | Invoices, receipts                                                            | Exercise 8                |
| `working-papers/`   | Audit notes, testing results                                                  | Exercises 15-17           |
| `entity-profiles/`  | Hypothetical company profiles (manufacturing co, textile exporter)            | Exercises 3, 6, 12-14, 22 |
| `consolidation/`    | Parent + subsidiary data for multi-entity consolidation                       | Exercise 11               |

## Crescent Textiles Data Set

The core exercise data centres on **Crescent Textiles (Pvt) Ltd**, a Pakistani textile manufacturer (FY 2024-25, year-end 30 June 2025). The data set includes:

- **Entity profile** — company overview, financials, group structure, intercompany transactions
- **Year-end trial balance** (June 2025) — 57-line IFRS-compliant chart of accounts
- **Prior month trial balance** (May 2025) — enables month-over-month variance analysis
- **Bank statement** (June 2025) — 16 transactions with 5 reconciling items (3 outstanding cheques, 1 deposit in transit, bank charges not in GL)
- **Budget** (FY 2024-25) — annual and June monthly budget vs actual, with 5 key variance root causes
- **AR aging schedule** (June 2025) — 16 invoices across 10 customers with ECL assessment by aging bucket

All files are internally consistent — the bank reconciliation balances to zero, the AR aging ties to the TB, and the budget variances have documented root causes.

## Setup

If you installed via the Claude plugin marketplace, these files are already available to Cowork.

If you downloaded the ZIP manually, point Cowork at this `exercises/` directory when prompted for exercise data.

## Data Format

All financial data uses:

- **Currency**: PKR (Pakistani Rupee), amounts in thousands
- **Standards**: IFRS-compliant chart of accounts
- **Entity type**: Hypothetical companies (no real company data)

Adapt the currency and chart of accounts for your jurisdiction as needed.
