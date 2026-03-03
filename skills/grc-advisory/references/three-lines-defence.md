# Three Lines of Defence Reference

## The Three Lines Model (IIA 2020 Update)

The Institute of Internal Auditors updated the model in 2020 from "Three Lines of Defence" to "Three Lines Model" to emphasise collaboration over siloed defence. The principles remain the same.

## Structure

### First Line: Management and Operational Functions

**Role**: Own and manage risk on a day-to-day basis.

Responsibilities:

- Implement and operate internal controls
- Identify, assess, and manage risks within their operations
- Ensure compliance with policies and procedures
- Report on risk and control status to second line

**AI agent role in first line**: Embedded in operational systems (ERP, CRM). Automates transaction processing, flags anomalies in real time, enforces business rules. The human role shifts from executing controls to monitoring agent execution.

### Second Line: Risk Management and Compliance Functions

**Role**: Set policy, define risk appetite, and monitor first line effectiveness.

Responsibilities:

- Develop risk management framework and policies
- Define and communicate risk appetite
- Monitor compliance with policies and regulations
- Provide oversight, guidance, and challenge to first line
- Report to governance body on risk and compliance position

**AI agent role in second line**: Automates continuous monitoring, compliance checking, and policy gap analysis. The human role shifts from periodic testing to reviewing agent alerts and making judgment calls on complex compliance questions.

### Third Line: Internal Audit

**Role**: Provide independent assurance to the governing body.

Responsibilities:

- Independently assess effectiveness of governance, risk management, and controls
- Report to the audit committee/board
- Maintain objectivity and organisational independence
- Follow IIA Standards for professional practice

**AI agent role in third line**: Automates transaction testing, population analysis (not sampling), anomaly detection, and working paper preparation. The human role shifts from executing audit procedures to interpreting findings and forming conclusions.

## Governing Body Role

The board and its committees (audit committee, risk committee) sit above all three lines:

- Set organisational objectives and risk appetite
- Receive assurance from all three lines
- Ensure appropriate structures and resources
- Hold management accountable

## Key Principle: Independence

- First line reports to operational management
- Second line reports to senior management (functionally independent of first line)
- Third line reports to the audit committee (organisationally independent of management)
- AI agents in each line must respect these reporting boundaries — a second-line monitoring agent does not direct first-line operations, it reports findings to the appropriate governance level

## Application to Agent Design

When designing GRC agents, map each agent's function to a specific line:

- An agent that processes transactions and enforces business rules = first line
- An agent that monitors compliance and reports exceptions = second line
- An agent that tests controls and produces assurance reports = third line

Never mix lines in a single agent — this compromises the independence that makes the model effective.
