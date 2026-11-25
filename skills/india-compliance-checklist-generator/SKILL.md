---
name: india-compliance-checklist-generator
description: Use when a business needs a dated, sourced compliance checklist spanning multiple Indian regulatory frameworks (FEMA, Companies Act, SEBI, RBI) relevant to its specific structure — not a generic checklist, but one scoped to what actually applies.
license: MIT
---

# India Compliance Checklist Generator

Produces a compliance checklist scoped to a specific business's actual
structure and activity — not a generic "Indian business compliance"
list that includes obligations that don't apply and omits ones that do.
This skill's value is almost entirely in the **scoping step**: working
out which of the many possible Indian regulatory frameworks actually
touch this business, before listing a single obligation.

## When to use this skill

- A new business needs to know what compliance actually applies to it,
  across company law, FEMA, sector-specific regulation, and tax-
  adjacent filings
- An existing business has changed structure (taken foreign investment,
  started an NBFC activity, listed on an exchange) and needs its
  checklist updated for the new obligations that now apply
- Producing a dated reference checklist for a board or investor that
  needs to see compliance is being tracked systematically

## The scoping questions to ask first

Before generating anything, establish:

1. **Entity type** — private limited, public limited, LLP, OPC,
   section 8 (non-profit)? Each carries a different compliance set
   under the Companies Act (see `companies-act-compliance` for the
   private-limited baseline).
2. **Foreign involvement** — any foreign shareholding, foreign
   director, external commercial borrowing, or cross-border
   transaction? This triggers **FEMA** obligations (FC-GPR/FC-TRS
   filings for foreign investment, annual FLA return, sector-specific
   FDI route checks — automatic vs. government approval route
   depending on the sector) that a purely domestic company doesn't
   have at all.
3. **Regulated activity** — is the business itself an NBFC, a payment
   aggregator, an insurance intermediary, a stockbroker? Each pulls in
   its own regulator (RBI, SEBI, IRDAI) with its own licensing and
   ongoing compliance layer, entirely separate from general company
   law.
4. **Listed or pre-IPO** — any listing on a stock exchange brings in
   **SEBI LODR** obligations (disclosures, board composition rules,
   insider trading code) that a private company does not carry.
5. **Sector-specific licensing** — does the business need any
   sector-specific license or registration beyond general incorporation
   (e.g. specific approvals for certain regulated sectors)? Flag this
   as a scoping question rather than assuming the general checklist
   covers it, since sector licensing is the most business-specific
   layer and the least generalisable.

## Workflow

### 1. Scope first, list second
Run the business through the scoping questions above and produce a
short "applies / does not apply" summary per framework (FEMA,
Companies Act baseline, SEBI, RBI, sector-specific) before generating
the detailed checklist — this summary is itself valuable, since it
tells the business *why* certain items are on or off its list, not
just what the list contains.

### 2. Generate the checklist with sources and dates
For each applicable obligation: what it is, which section/circular/
rule it comes from (not just "FEMA" in the abstract — the specific
rule or master direction), the recurring deadline if any, and the date
this checklist item was last verified against the actual regulation.
Dating every item matters because Indian regulatory frameworks change
circulars and thresholds fairly often — an undated checklist implicitly
and falsely claims to be permanently current.

### 3. Cross-reference the specialist skills where they exist
Where a checklist item is covered in depth by another skill in this
catalog (Companies Act items → `companies-act-compliance`; RBI
circular changes → `rbi-circular-tracker`; POSH → `posh-compliance`),
reference that skill rather than duplicating its full depth here — this
skill's job is the cross-framework scoping and assembly, not
re-explaining what's already covered elsewhere in more depth.

### 4. Flag re-scoping triggers
Note explicitly which future events would change the business's
applicable-framework set (taking foreign investment, crossing a
revenue/asset threshold that changes entity classification, starting a
new regulated activity) so the checklist isn't treated as a one-time
artifact but as something to regenerate when the business's own
structure changes.

## What this skill does not do

- It does not give a legal opinion on edge-case applicability (e.g.
  whether a specific cross-border arrangement triggers FEMA approval-
  route requirements) — flag genuinely ambiguous scoping questions to
  qualified counsel rather than guessing.
- It does not track deadlines in real time — see `rbi-circular-tracker`
  and `companies-act-compliance` for the recurring-calendar tracking
  layer; this skill produces the checklist, those track it over time.
- It is not a substitute for a chartered accountant or company
  secretary's sign-off on actual filings — it tells the business what
  applies and roughly when; the filings themselves need a qualified
  professional's certification where the law requires one.

## Reference

- Companies Act, 2013
- Foreign Exchange Management Act, 1999 (FEMA) and RBI/FEMA
  regulations and master directions
- SEBI (Listing Obligations and Disclosure Requirements) Regulations
- RBI master directions applicable to the entity's regulatory category
