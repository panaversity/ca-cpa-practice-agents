# CA/CPA Domain Agents

Companion repository for **Chapter 19: AI Transformation of CA/CPA Practice Areas** from [The AI Agent Factory](https://learn.panaversity.org) by Panaversity.

Domain-specific AI agents, workflow recipes, and exercise data for chartered accountancy and CPA practice areas — covering all five CA/CPA domains.

---

## Quick Start

### Option A: Download ZIP (Recommended for learners)

1. Go to the [Releases page](https://github.com/panaversity/ca-cpa-domain-agents/releases/latest)
2. Download the zip you need:

| Download                            | What's Inside                            | Use With                           |
| ----------------------------------- | ---------------------------------------- | ---------------------------------- |
| **`ca-cpa-domain-agents-full.zip`** | Everything below                         | Exercise 24 (full deployment)      |
| `ca-cpa-skills-only.zip`            | 10 SKILL.md agent files                  | Lessons 9-10 (building extensions) |
| `ca-cpa-workflow-recipes.zip`       | 6 workflow recipes                       | Lessons 7-8 (Cowork workflows)     |
| `ca-cpa-exercise-data.zip`          | Trial balances, invoices, working papers | Lessons 11-14 (practice labs)      |
| `ca-cpa-references.zip`             | Domain quick reference table             | Anytime (lookup)                   |

3. Unzip into your project:

```bash
# Full setup (for Exercise 24)
unzip ca-cpa-domain-agents-full.zip -d my-practice/

# Or just the skills (for Lessons 9-10)
unzip ca-cpa-skills-only.zip -d .claude/
```

### Option B: Clone the repo

```bash
git clone https://github.com/panaversity/ca-cpa-domain-agents.git
cd ca-cpa-domain-agents
```

### Option C: Claude Plugin Marketplace

```bash
claude plugin marketplace add panaversity/ca-cpa-domain-agents
```

---

## What's in This Repo

```
ca-cpa-domain-agents/
├── skills/                  # 10 Agent Skills (agentskills.io spec)
│   ├── accounting-reporting/    # Domain 1: Accounting & Financial Reporting
│   ├── tax-advisory/            # Domain 2: Tax & Non-Assurance Advisory
│   ├── assurance/               # Domain 3: Assurance Services
│   ├── management-accounting/   # Domain 4: Management Accounting
│   ├── grc-advisory/            # Domain 5: GRC Advisory
│   ├── pakistan-tax-jurisdiction/# Extension: Jurisdiction tax rules (Pakistan)
│   ├── chart-of-accounts/       # Extension: IFRS chart of accounts encoding
│   ├── audit-methodology/       # Extension: ISA audit methodology
│   ├── client-entity/           # Extension: Client knowledge (template)
│   └── compliance-calendar/     # Extension: Regulatory filing calendar
├── workflow-recipes/        # 6 Cowork scheduled task specs
│   ├── month-end-close.md       # Accounting domain
│   ├── tax-computation.md       # Tax domain
│   ├── audit-programme.md       # Assurance domain
│   ├── board-pack.md            # Management accounting domain
│   ├── fraud-monitoring.md      # GRC domain
│   └── compliance-monitoring.md # GRC domain
├── exercises/               # Practice lab data (PKR-denominated)
│   ├── trial-balances/          # Crescent Textiles trial balance (CSV)
│   ├── source-documents/        # Sales/purchase invoices, bank statements
│   ├── entity-profiles/         # Crescent Textiles + Karachi Foods profiles
│   ├── working-papers/          # Audit planning + revenue testing templates
│   └── consolidation/           # Parent-subsidiary elimination data
├── references/              # Quick-reference materials
│   └── domain-quick-reference.md
├── .claude-plugin/          # Plugin metadata for marketplace
├── README.md
└── LICENSE                  # Apache-2.0
```

---

## How Each Folder Maps to Chapter 19 Lessons

| Folder                                         | Chapter 19 Lessons                     | What You Do                                          |
| ---------------------------------------------- | -------------------------------------- | ---------------------------------------------------- |
| `skills/` (5 domain agents)                    | L02-L06 (domain analysis)              | Read these to understand what each domain agent does |
| `skills/` (5 extensions)                       | L09-L10 (building extensions)          | Customize these for your jurisdiction and clients    |
| `workflow-recipes/`                            | L07-L08 (plugin ecosystem + workflows) | Adapt the "Customize This" section for your practice |
| `exercises/`                                   | L11-L14 (practice labs)                | Use as input data for lab exercises                  |
| `exercises/` + `skills/` + `workflow-recipes/` | L15-L16 (capstones)                    | Combine everything for full practice deployment      |
| `references/`                                  | All lessons                            | Quick lookup for domain-to-plugin mapping            |

---

## Customizing for Your Jurisdiction

All materials ship with **Pakistan defaults** (FBR, SECP, ITO 2001, PKR). Every workflow recipe and extension skill includes a **"Customize This"** section listing the variables to adapt:

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

## Plugin Dependencies

This repository works alongside these Anthropic plugins (install separately):

```bash
claude plugin install finance@knowledge-work-plugins
claude plugin marketplace add anthropics/financial-services-plugins
claude plugin marketplace add panaversity/idfa-financial-architect
```

## License

Apache-2.0. See [LICENSE](LICENSE) for details.

---

_Built as part of [The AI Agent Factory](https://learn.panaversity.org) — teaching domain experts to build sellable AI agents._
