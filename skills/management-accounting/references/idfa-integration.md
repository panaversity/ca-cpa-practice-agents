# IDFA Integration Reference

## Intent-Driven Financial Architecture (Chapter 18)

The IDFA methodology provides a structured approach to financial model design using Named Ranges and strict naming conventions. This reference documents how the management-accounting agent integrates with IDFA.

## Naming Conventions

| Prefix  | Purpose                            | Example                                                  |
| ------- | ---------------------------------- | -------------------------------------------------------- |
| `Inp_`  | Input assumptions (user-defined)   | `Inp_RevenueGrowthRate`, `Inp_CorporateTaxRate`          |
| `Calc_` | Calculated values (formula-driven) | `Calc_GrossProfit`, `Calc_EBITDA`                        |
| `Out_`  | Output values (final results)      | `Out_NetProfit`, `Out_CashBalance`                       |
| `Ref_`  | Reference data (lookup tables)     | `Ref_TaxSlabs`, `Ref_DepreciationRates`                  |
| `Chk_`  | Check/validation values            | `Chk_BalanceSheetBalances`, `Chk_CashFlowReconciliation` |

## Model Structure

An IDFA-compliant financial model follows this sheet structure:

1. **Inputs**: All `Inp_` variables with clear labels and source documentation
2. **Calculations**: All `Calc_` formulas referencing `Inp_` values — no hardcoded numbers
3. **Outputs**: Summary sheets pulling `Out_` values for presentation
4. **Checks**: Validation sheet with `Chk_` formulas confirming model integrity

## Variance Analysis Integration

When performing variance analysis using IDFA conventions:

- Budget assumptions are `Inp_Budget_[metric]` (e.g., `Inp_Budget_Revenue`)
- Actual values are `Inp_Actual_[metric]` (e.g., `Inp_Actual_Revenue`)
- Variance calculations are `Calc_Var_[metric]` (e.g., `Calc_Var_Revenue`)
- Decomposition uses `Calc_Var_Volume_[metric]`, `Calc_Var_Price_[metric]`, `Calc_Var_Mix_[metric]`

## What-If Scenario Framework

IDFA scenarios are structured as alternative `Inp_` sets:

- `Inp_Base_[metric]` — base case assumptions
- `Inp_Upside_[metric]` — optimistic assumptions
- `Inp_Downside_[metric]` — pessimistic assumptions

A scenario switch variable (`Inp_ActiveScenario`) controls which set drives the calculations.

## Board Pack Output Mapping

When preparing board packs from IDFA models:

- Executive summary KPIs pull from `Out_` values
- Variance bridges reference `Calc_Var_` values
- Forecast updates replace `Inp_Budget_` with `Inp_Forecast_` for remaining periods
- Sensitivity tables cycle through `Inp_` values programmatically

## Key Rule

Every number in an IDFA model must trace back to either an `Inp_` value (user-controlled assumption) or a `Calc_` formula (transparent computation). No magic numbers. No embedded constants in formulas. This is the discipline that makes the model auditable and the agent's outputs reproducible.
