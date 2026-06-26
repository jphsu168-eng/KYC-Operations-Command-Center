# KYC Case Bottleneck Resolver

A rule-based KYC operations tool that simulates document gap checks, beneficial ownership completeness review, screening triage, customer risk profiling, trigger event review, case readiness assessment, follow-up actions, analyst review notes, and audit-friendly decision trails.

The project is presented as a 2026 RegTech-style dashboard UI with a dark fintech interface, glassmorphism cards, KPI summaries, bottleneck diagnosis outputs, analyst work-note generation, audit trail simulation, and a collapsed Explainability Center.

## Problem Statement

Modern KYC reviews are not delayed only by missing documents. Cases often become blocked because customer risk profiles are incomplete, beneficial ownership information is unclear, evidence quality is weak, trigger events require customer refresh, screening results require escalation, and analyst notes are inconsistent.

This project simulates a workflow that helps identify why a KYC case is blocked and what action should happen next.

## Important Disclaimer

This is an educational portfolio project. It does not perform real sanctions screening, OFAC checks, adverse media searches, identity verification, customer verification, transaction monitoring, or bank decisioning.

This tool supports analyst workflow simulation. Final review, escalation, and customer decisioning require human compliance review.

## UI / Product Design Direction

The interface uses a 2026 RegTech-inspired dashboard style with a dark fintech layout, glassmorphism cards, compact KPI panels, status badges, and an explainability center. The design goal is to make complex KYC workflow information easier to scan while keeping risk decisions transparent and audit-friendly.

## Why This Matters In Banking KYC Operations

KYC teams need fast, consistent triage. A case may appear simple until a missing ownership chart, unresolved screening hit, aging SLA, or incomplete beneficial ownership detail blocks completion.

This tool demonstrates how rule-based workflow automation can help analysts identify bottlenecks, explain risk drivers, assign follow-up actions, and produce consistent review notes without relying on external systems.

## Features

- Case intake section with case ID, customer profile, relationship type, expected activity, and SLA dates
- Premium 2026 RegTech-style dashboard UI with dark fintech styling, glassmorphism panels, responsive bento layout, and top KPI cards
- Review type support for New Onboarding, Periodic Review, Trigger Event Review, and Ongoing Monitoring Alert
- Trigger event reason tracking for ownership changes, control person changes, address changes, country exposure changes, adverse media, new product/service, unusual activity, expired documents, periodic refresh, and other events
- KYC refresh assessment with refresh reason and required update documents
- Case aging indicator:
  - `0-3 days`: On Track
  - `4-7 days`: Attention Needed
  - `8+ days`: Overdue
  - Target date passed: Past Due
- Document gap checker with required documents by entity type
- Received, missing, key missing, and evidence-quality document outputs
- Evidence quality review for Current, Expired, Incomplete, Inconsistent, Missing, and Not applicable evidence
- Beneficial ownership completeness check
- Source of Funds and Source of Wealth documentation checks
- Customer risk profile categories for customer type, country, industry, ownership, activity, screening, and documentation risk
- Screening hit triage helper
- 0-100 rule-based risk score
- Low, Medium, High, and Critical risk levels
- Bottleneck diagnosis categories
- Collapsed Explainability Center with compact rule categories, trigger conditions, results, and rationale
- KPI cards for risk score, case readiness, SLA status, and open bottlenecks
- Case Queue Prioritizer with urgency score, priority level, and priority reasons
- Follow-up action generator with owner, priority, and reason
- RM Follow-Up Email Generator with recipient type and tone options
- Final case readiness status
- Recommended decision governance: Proceed, Proceed with conditions, Request more information, Escalate to Compliance, or Do not proceed until cleared
- Professional KYC analyst review note
- Audit trail summary with timestamp, triggered rules, risk points, final decision, and follow-up owners
- Copy buttons for analyst note and audit trail
- Copy button for RM follow-up email draft
- Runs by double-clicking `index.html`

## Workflow

1. Enter case intake details.
2. Select the entity type.
3. Check which required documents were received.
4. Complete beneficial ownership fields.
5. Select the review type and trigger event reason if applicable.
6. Complete document evidence quality, beneficial ownership, SOF/SOW, and screening triage fields.
7. Select additional risk indicators.
8. Click **Generate Case Review**.
9. Review refresh requirements, customer risk profile, evidence quality issues, bottlenecks, follow-up actions, analyst note, and audit trail.
10. Copy the generated RM follow-up email draft if follow-up is needed.

## Document Gap Rules

| Entity Type | Required Documents |
| --- | --- |
| Private Company | Certificate of Incorporation, Business Registration, Ownership Chart, Beneficial Owner ID, W-9 or W-8, Address Proof, Source of Funds Explanation |
| Public Company | Annual Report or 10-K, Stock Exchange Listing Evidence, Authorized Signer Information, W-9 or W-8 |
| Individual | Government ID, Address Proof, Source of Funds Explanation |
| Non-profit | Registration Certificate, Mission Statement or Website, Authorized Signer Information, Source of Funds Explanation |
| Financial Institution | Banking License or Regulatory Registration, AML Policy Summary, Wolfsberg Questionnaire, Authorized Signer Information |

## Risk Scoring Methodology

The risk score is rule-based and capped at 100.

| Risk Factor | Points |
| --- | --- |
| PEP involvement | +25 |
| Sanctions or watchlist concern | +40 |
| Adverse media | +20 |
| High-risk country | +20 |
| Complex ownership structure | +15 |
| BO incomplete | +15 |
| Missing key documents | +10 |
| High expected activity | +10 |
| Financial institution customer | +10 |
| Case overdue | +5 |
| Evidence quality issue | +10 |
| Missing Source of Funds | +10 |
| Missing Source of Wealth for higher-risk customer | +10 |
| Weak SOF/SOW explanation | +5 |

Risk levels:

| Score | Risk Level |
| --- | --- |
| 0-24 | Low |
| 25-49 | Medium |
| 50-74 | High |
| 75-100 | Critical |

## Bottleneck Diagnosis Rules

The app can identify these bottlenecks:

- Missing Documents
- Evidence Quality Issues
- SOF/SOW Follow-Up Needed
- KYC Refresh Required
- Beneficial Ownership Incomplete
- Screening Clearance Needed
- Adverse Media Review Needed
- High-Risk Escalation Needed
- Case Aging / SLA Risk
- Ready for Review

## Case Queue Prioritizer

The tool calculates an urgency score from `0-100` to help analysts understand which cases should be handled first.

Urgency factors include:

- Risk level
- Case aging
- Target completion date
- Sanctions/watchlist concern
- Missing key documents
- Relationship type

Priority levels:

| Urgency Score | Priority |
| --- | --- |
| 0-24 | Low |
| 25-49 | Medium |
| 50-74 | High |
| 75-100 | Urgent |

Examples:

- Sanctions/watchlist concern adds high urgency.
- Past-due target date adds high urgency.
- Critical risk adds high urgency.
- New onboarding with missing key documents is prioritized when the target date is close.
- Overdue periodic reviews are flagged.

## Explainability Center

The dashboard includes a collapsed Explainability Center so users can understand the rule logic without making the main workflow feel cluttered. Rule categories include:

- Document Rules
- Risk Scoring Rules
- Screening Triage Rules
- Beneficial Ownership Rules
- Case Readiness Rules
- Trigger Event Rules
- Evidence Quality Rules
- Source of Funds / Source of Wealth Rules
- Review Decision Governance Rules
- Escalation Rules

Each expanded rule shows:

- Rule name
- Trigger condition
- Result
- Why it matters

Triggered rules are also included in the audit trail summary to make the output more explainable and audit-friendly.

## RM Follow-Up Email Generator

The app can generate a professional follow-up email draft for:

- Relationship Manager
- Customer
- Compliance Officer

Tone options:

- Standard
- Urgent
- Final Reminder

The email draft can include missing documents, beneficial ownership gaps, screening or adverse media clarification needs, target completion date, and a clear action request. If sanctions or watchlist concern is marked `Yes`, the draft routes the issue to the Compliance Officer and does not ask the customer to clear the alert directly.

## Example Use Case

A KYC analyst receives a private company onboarding case. The ownership chart and beneficial owner ID are missing, the case is past its SLA target, and screening has a potential match.

The tool can show:

- Missing key documents
- BO Incomplete or BO Requires Escalation
- Screening Clearance Needed
- Case Aging / SLA Risk
- Risk score and risk level
- Urgency score and queue priority
- Triggered policy rules in the audit trail
- Follow-up actions assigned to Analyst, Relationship Manager, Customer, or Compliance Officer
- A professional RM/customer/compliance follow-up email draft
- Final readiness status, such as `Needs More Documents`, `Escalation Required`, or `Do Not Proceed Until Cleared`

Example output excerpt:

```text
KYC CASE BOTTLENECK REVIEW NOTE

Case Summary
Case ID: KYC-2026-0142
Customer Legal Name: Northstar Payments LLC
Entity Type: Private Company
Relationship Type: New Onboarding
Expected Activity: High

Case Aging Status
Days Pending: 8
Aging Status: Overdue

Beneficial Ownership Result
BO Requires Escalation

Screening Triage Result
Potential True Match - Name similarity is High and both country and DOB/registration indicators match.

Bottleneck Diagnosis
- Missing Documents
- Beneficial Ownership Incomplete
- Screening Clearance Needed
- High-Risk Escalation Needed
- Case Aging / SLA Risk
```

## Limitations

- This is a rule-based educational portfolio project.
- It is not production-ready.
- It does not perform real sanctions screening, OFAC checks, adverse media searches, identity verification, customer verification, transaction monitoring, or bank decisioning.
- It does not connect to OFAC, sanctions databases, watchlist tools, adverse media tools, bank systems, customer systems, or AI APIs.
- It does not store cases because there is no backend or database.
- It does not send emails; it only drafts copyable text.
- It should not be used for real compliance decisions.
- Final review, escalation, and customer decisioning require human compliance review.

## Future Improvements

- Add editable follow-up actions.
- Add editable Explainability Center rules for different simulated compliance programs.
- Add a sortable case queue if multiple sample cases are added.
- Add editable email templates.
- Add downloadable PDF or print output.
- Add local-only saved drafts using browser storage.
- Add separate maker/checker quality-control status.
- Add configurable trigger-event workflows by customer segment.
- Add more detailed evidence-quality reason codes.
- Add separate human reviewer sign-off fields if the project later supports local storage.
- Add more granular country and industry risk inputs.
- Add validation for required fields.
- Add unit tests if the project later uses a test setup.

## Resume Bullet Points

### KYC Analyst

- Built a rule-based KYC case bottleneck dashboard that identifies missing documents, beneficial ownership gaps, screening blockers, case aging issues, and readiness status.
- Created an analyst work-note generator that summarizes document gaps, risk drivers, bottlenecks, and follow-up actions in a consistent KYC review format.
- Added an RM follow-up email generator to draft professional requests for missing documents, beneficial ownership gaps, and escalation items.

### Compliance Analyst

- Designed a simulated compliance workflow that converts KYC risk indicators into explainable risk scoring, escalation triggers, and audit-friendly decision trails.
- Added an Explainability Center and triggered-rule audit summary to improve explainability and review traceability.
- Modeled rules for sanctions/watchlist concern, PEP involvement, adverse media, beneficial ownership completeness, and high-risk escalation.

### AML Analyst

- Developed a screening triage helper that documents potential false positive, potential true match, and compliance review outcomes using identifier match logic.
- Created a rule-based risk model that highlights AML-relevant drivers such as PEP exposure, adverse media, sanctions concern, and complex ownership.

### FinTech Operations Analyst

- Built a static operations dashboard that helps triage onboarding and review cases by SLA age, missing documentation, owner assignment, and follow-up priority.
- Added a case queue prioritizer that scores urgency from risk level, aging, target date, sanctions concern, missing key documents, and relationship type.
- Created rule-based follow-up email drafts for Relationship Manager, customer, and Compliance Officer workflows.
- Demonstrated how workflow automation can reduce manual case review friction without relying on backend systems or external data sources.

### AI Automation Role

- Created a beginner-friendly workflow automation prototype using plain JavaScript decision rules to generate risk summaries, bottleneck diagnoses, follow-up actions, analyst notes, and audit trails.
- Demonstrated responsible automation positioning by clearly documenting that the tool is educational, rule-based, and not connected to real screening or bank systems.

## Disclaimer

This project is for education and portfolio demonstration only. It does not perform real sanctions screening, OFAC checks, adverse media searches, identity verification, customer verification, or bank decisioning. It is not connected to real OFAC data, sanctions databases, adverse media tools, bank systems, AI APIs, or customer systems.
