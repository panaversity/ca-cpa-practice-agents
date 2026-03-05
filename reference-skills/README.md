# Reference Skills

These five SKILL.md files are **reference implementations** using Pakistan defaults. They demonstrate the structure and instruction format for CA/CPA domain extensions.

**Do not install these as plugins.** Instead, study them and then build your own extensions for your jurisdiction, firm, and clients during Lessons 9-10 of Chapter 19.

## The Five Extensions

| Extension                    | What It Encodes                                                | Lesson |
| ---------------------------- | -------------------------------------------------------------- | ------ |
| `pakistan-tax-jurisdiction/` | Tax rates, filing deadlines, penalty provisions, WHT schedules | L09    |
| `chart-of-accounts/`         | Account codes, documentation rules, restricted accounts        | L09    |
| `audit-methodology/`         | Materiality benchmarks, sample sizes, escalation conditions    | L10    |
| `client-entity/`             | Business model, seasonality, risk areas, CFO preferences       | L10    |
| `compliance-calendar/`       | Regulatory obligations, deadlines, penalty matrices            | L10    |

## Assets

Two extensions include machine-readable data files in `assets/`:

- `chart-of-accounts/assets/coa-template.csv` — account code mapping
- `compliance-calendar/assets/regulatory-calendar.csv` — filing dates and frequencies

These are operational inputs the agent reads at runtime, not educational references.

## Instruction Format

Every instruction follows the pattern: **When [condition], [action]**

```
When computing corporate income tax for a non-banking company,
apply the standard corporate rate of 29% under ITO 2001 Section 18.
```

The condition determines when the agent activates the instruction. The action determines what it does. Precision in the condition clause is what makes the extension useful.
