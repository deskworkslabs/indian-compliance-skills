---
name: aml-transaction-monitoring
description: Use when reviewing transactions or customer activity for anti-money-laundering (AML) red flags under India's PMLA framework — pattern checks, STR (Suspicious Transaction Report) drafting support, and KYC/customer due-diligence review for a regulated entity.
license: MIT
---

# AML Transaction Monitoring (India)

Supports a regulated entity's AML programme under India's **Prevention
of Money Laundering Act, 2002 (PMLA)** and the rules issued under it,
as applied by the relevant regulator (RBI for banks/NBFCs, SEBI for
brokers/intermediaries, IRDAI for insurers, FIU-IND's reporting
requirements across all of them). This is a pattern-detection and
documentation aid for a compliance team — it does not replace a
Principal Officer's judgement, and it does not file anything with
FIU-IND directly.

## When to use this skill

- Screening a batch of transactions for known red-flag patterns
  before human review
- Drafting the internal escalation note that supports a decision on
  whether to file a **Suspicious Transaction Report (STR)**
- Reviewing **KYC/CDD (Customer Due Diligence)** completeness against
  what PMLA Rules require, including **Enhanced Due Diligence (EDD)**
  triggers
- Checking **Cash Transaction Report (CTR)** and **Cross-Border Wire
  Transfer** thresholds have been correctly applied to a transaction
  set
- Building or reviewing the risk-categorisation logic behind a
  customer risk-rating model (low/medium/high)

## Core thresholds and triggers

1. **Cash Transaction Report (CTR)** — all cash transactions (and a
   series of integrally connected cash transactions within a month)
   **of ₹10 lakh or more** must be reported, whether in a single
   transaction or value aggregated.
2. **Suspicious Transaction Report (STR)** — no monetary threshold;
   triggered by the *nature* of the transaction, not its size. Red
   flags this skill checks for include:
   - Structuring: multiple transactions just below a reporting
     threshold, especially repeated on the same or consecutive days
   - Transactions with no clear economic or lawful purpose, or
     inconsistent with the customer's known profile/declared income
   - Rapid movement of funds in and out of an account with little or
     no genuine business rationale ("pass-through" / layering pattern)
   - Use of multiple accounts to receive and then consolidate funds
   - Transactions involving jurisdictions flagged as high-risk by
     FATF or domestic regulatory advisories
   - A customer reluctant to provide KYC information, or providing
     documents that appear inconsistent or altered
   - Activity inconsistent with the stated purpose of the account at
     onboarding (e.g. a "salary account" receiving large, irregular
     business-style credits)
3. **Non-Profit Organisation (NPO) transactions** — PMLA Rules require
   closer monitoring of NPO/trust accounts given their historical use
   in layering; apply EDD by default rather than standard due
   diligence.
4. **Politically Exposed Persons (PEPs)** — mandatory Enhanced Due
   Diligence, including source-of-funds verification and senior
   management sign-off on onboarding and continued relationship.
5. **STR filing timeline** — once suspicion is formed, the Principal
   Officer must file the STR with FIU-IND **within 7 working days** of
   concluding that a transaction is suspicious (and the underlying
   grounds, not just the raw transaction, is what gets evaluated —
   "tipping off" the customer that an STR is contemplated is itself
   an offence under Section 12 and must never happen).

## Workflow

### 1. Pattern screen
Given a transaction set (dates, amounts, counterparties, account
numbers), run it against the red-flag list above and return each hit
tagged with which pattern it matched and why — e.g. "₹9.8L cash
deposit, repeated on 3 consecutive days, same branch: structuring
pattern below CTR threshold." Never present a pattern match as a
finding of wrongdoing — it is a reason for a human reviewer to look
closer, nothing more.

### 2. Customer profile cross-check
Where customer profile data is available (declared occupation,
declared income band, account purpose at onboarding), flag
transactions inconsistent with that profile as a distinct, higher-
priority category from pure pattern matches.

### 3. CTR aggregation check
Aggregate same-customer cash transactions across the reporting period
and flag any customer whose aggregate crosses ₹10 lakh even where no
single transaction does, since CTR obligations are based on
aggregated "integrally connected" transactions, not just single large
ones.

### 4. STR escalation note (drafting support only)
For a transaction or pattern a human reviewer has decided to escalate,
draft the internal note: what was observed, which red flag(s) it
matches, what in the customer's KYC/profile makes it inconsistent (or
notably consistent, if the reviewer wants that documented too), and
the date suspicion was formed — this date starts the 7-working-day
filing clock, so get it right and flag it clearly. The actual
suspicion determination, and the decision to file, rests with the
Principal Officer alone.

### 5. KYC/CDD completeness check
Given a customer file, check for the baseline PMLA Rules requirements
(identity proof, address proof, where applicable PAN, beneficial
ownership declaration for non-individual entities) and flag any EDD
trigger (PEP, NPO, high-risk jurisdiction exposure, high-risk
business category) where only standard due diligence was recorded.

## What this skill does not do

- It does not file an STR, CTR, or any report with FIU-IND — all
  filings go through the entity's own Principal Officer and FINnet
  system login.
- It does not make a legal determination that a customer is
  laundering money — it surfaces patterns and inconsistencies for a
  qualified compliance officer to evaluate.
- It never discloses to a customer, directly or indirectly, that
  their activity is under review or that an STR is being considered
  — this would constitute "tipping off," an offence under PMLA
  Section 12.

## Reference

- Prevention of Money Laundering Act, 2002
- Prevention of Money Laundering (Maintenance of Records) Rules, 2005
- FIU-IND reporting guidelines for reporting entities
