# CA/CPA Practice Agents — Companion Repository

Companion repository for **Chapter 19: AI Transformation of CA/CPA Practice Areas** from [The AI Agent Factory](https://learn.panaversity.org) by Panaversity.

Exercise data, reference SKILL.md implementations, and workflow recipe templates for chartered accountancy and CPA practice areas.

---

## Quick Start

### Option A: Download exercise data (recommended for learners)

1. Go to the [Releases page](https://github.com/panaversity/ca-cpa-practice-agents/releases/latest)
2. Download `ca-cpa-exercise-data.zip` — trial balances, entity profiles, source documents, and working paper templates for Exercises 1-24
3. Unzip into your working folder

### Option B: Clone the repo (for reference skills + workflow recipes too)

```bash
git clone https://github.com/panaversity/ca-cpa-practice-agents.git
cd ca-cpa-practice-agents
```

---

## What's in This Repo

```
ca-cpa-practice-agents/
├── exercises/               # Practice lab data (PKR-denominated)
│   ├── trial-balances/          # Crescent Textiles trial balance (CSV)
│   ├── source-documents/        # Sales/purchase invoices, bank statements
│   ├── entity-profiles/         # Crescent Textiles + Karachi Foods profiles
│   ├── working-papers/          # Audit planning + revenue testing templates
│   └── consolidation/           # Parent-subsidiary elimination data
├── reference-skills/        # 5 reference SKILL.md files (Pakistan defaults)
│   ├── pakistan-tax-jurisdiction/  # Jurisdiction tax rules
│   ├── chart-of-accounts/        # IFRS chart of accounts + assets/coa-template.csv
│   ├── audit-methodology/        # ISA audit methodology
│   ├── client-entity/            # Client knowledge (template)
│   └── compliance-calendar/      # Regulatory calendar + assets/regulatory-calendar.csv
├── workflow-recipes/        # 6 natural language scheduling templates
│   ├── month-end-close.md       # Accounting domain
│   ├── tax-computation.md       # Tax domain
│   ├── audit-programme.md       # Assurance domain
│   ├── board-pack.md            # Management accounting domain
│   ├── fraud-monitoring.md      # GRC domain
│   └── compliance-monitoring.md # GRC domain
├── README.md
└── LICENSE                  # Apache-2.0
```

### This is NOT a plugin

This repository provides exercise data and reference materials. It is not an installable Cowork plugin. Students build their own SKILL.md extensions locally during Lessons 9-10 using the Method A interview framework from Chapter 16.

---

## How Each Folder Maps to Chapter 19 Lessons

| Folder              | Chapter 19 Lessons                                  | What You Do                                                                       |
| ------------------- | --------------------------------------------------- | --------------------------------------------------------------------------------- |
| `exercises/`        | L02-L06 (domain exercises), L11-L14 (practice labs) | Download and use as input data for exercises                                      |
| `reference-skills/` | L09-L10 (building extensions)                       | Study these Pakistan-default examples, then build your own for your jurisdiction  |
| `workflow-recipes/` | L07-L08 (workflows), L16 (deployment)               | Copy recipe text into Cowork's `/schedule` command, adapting for your practice    |
| Everything          | L15-L16 (capstones)                                 | Combine exercise data + your custom skills + workflow recipes for full deployment |

---

## Customizing for Your Jurisdiction

All materials ship with **Pakistan defaults** (FBR, SECP, ITO 2001, PKR). The reference skills demonstrate the structure — you replace the values for your jurisdiction:

| Variable             | Pakistan Default               | Your Value             |
| -------------------- | ------------------------------ | ---------------------- |
| Currency             | PKR                            | _your currency_        |
| Tax authority        | FBR (Federal Board of Revenue) | _your tax authority_   |
| Corporate regulator  | SECP                           | _your regulator_       |
| Tax code             | Income Tax Ordinance 2001      | _your tax code_        |
| Accounting standards | IFRS (as adopted in Pakistan)  | _your standards_       |
| Audit standards      | ISA (ICAP adoption)            | _your audit standards_ |
| Fiscal year          | July 1 - June 30               | _your fiscal year_     |

---

## Prerequisites

Complete Chapters 14-18 of The AI Agent Factory before using this repository:

- Enterprise agentic landscape (Ch 14)
- Cowork plugin anatomy and SKILL.md structure (Ch 15)
- Knowledge extraction methodology (Ch 16)
- Finance domain agents and cross-app workflows (Ch 17)
- Intent-Driven Financial Architecture / IDFA (Ch 18)

## Anthropic Plugin Dependencies

Chapter 19 uses these Anthropic plugins (install separately via Cowork):

```bash
claude plugin install finance@knowledge-work-plugins
claude plugin marketplace add anthropics/financial-services-plugins
claude plugin marketplace add panaversity/idfa-financial-architect
```

## License

Apache-2.0. See [LICENSE](LICENSE) for details.

---

_Built as part of [The AI Agent Factory](https://learn.panaversity.org) — teaching domain experts to build sellable AI agents._
