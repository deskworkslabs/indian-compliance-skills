---
name: shebox-integration
description: Use when an organisation's POSH complaint-handling process needs to connect to the Government of India's SHe-Box portal — understanding what SHe-Box is, what it requires of employers, and how an internal IC process should align with it.
license: MIT
---

# SHe-Box Integration (India)

Explains and helps an organisation align its internal POSH process with
**SHe-Box** (Sexual Harassment electronic-Box), the Government of
India's centralised online complaint portal for workplace sexual
harassment, run by the Ministry of Women and Child Development. This
skill is a process-alignment guide, not a technical API integration —
SHe-Box does not currently offer a public API for organisations to
connect their own systems to; "integration" here means **ensuring an
organisation's own process correctly interoperates with how SHe-Box
routes and expects complaints**, not a software integration.

## When to use this skill

- Understanding what SHe-Box actually is and whether an organisation's
  own complaints could also surface through it
- Making sure an organisation's registered Internal Committee details
  are correctly reflected wherever SHe-Box or its linked registries
  expect them
- Explaining to employees how SHe-Box relates to — and does not
  replace — filing a complaint with the organisation's own IC

## What SHe-Box actually is

SHe-Box provides a single online window for a woman to file a sexual
harassment complaint, applicable to both organised and unorganised
sector workplaces — a complaint filed there is then routed to the
employer's Internal Committee (for organisations required to have one)
or to the district Local Committee (for workplaces without one, or
below the 10-employee IC threshold). It is a **routing and visibility
layer** on top of the IC/LC process the POSH Act already establishes —
not a separate inquiry mechanism with its own independent process.

## Key implications for an organisation

1. **A complaint can arrive via SHe-Box instead of, or in addition to,
   direct submission to the IC.** The organisation's process needs a
   defined path for receiving and logging a SHe-Box-routed complaint
   with the same rigor as one filed directly — same timeline tracking
   (90-day inquiry window, the filing-date clock), same confidentiality
   obligations, same annual-report inclusion. Treat it as another
   intake channel feeding the same IC process, not a parallel process
   with its own rules.
2. **IC details should be consistent wherever they're published.**
   Where an organisation's IC composition, contact details or
   presiding officer are referenced for SHe-Box or any linked
   government registry purpose, these must match what's displayed
   internally (on the workplace notice board, in the POSH policy) —
   inconsistency here is itself a compliance gap, since Section 4
   compliance includes the IC actually being reachable and correctly
   identified wherever employees might look for it, including through
   government-facilitated channels.
3. **SHe-Box does not change substantive IC obligations.** The 90-day
   inquiry window, the confidentiality requirement under Section 16,
   and the annual reporting duty all apply exactly the same to a
   SHe-Box-routed complaint as to one filed directly — there is no
   separate, lighter-touch process just because the complaint arrived
   through the government portal.

## Workflow

### 1. Confirm intake readiness
Check whether the organisation has a defined internal process step for
"a complaint has arrived via SHe-Box" — who receives the routing
notification, how it's logged alongside directly-filed complaints, and
whether the same case-numbering/tracking system applies to both intake
paths.

### 2. Audit published IC details for consistency
Compare IC composition and contact details as displayed internally
(policy document, notice board) against anywhere they may also be
referenced for SHe-Box or related government-facing purposes, and flag
any mismatch (a lapsed IC member's name, an outdated contact) for
correction.

### 3. Build employee-facing clarity
Produce employee communication that explains SHe-Box as *one of the
ways* to file a complaint (alongside direct submission to the IC), not
a separate or additional complaint process — avoiding the common
confusion of employees thinking they need to file twice, once via
SHe-Box and again with HR/the IC.

## What this skill does not do

- It does not provide a software integration or API connection to
  SHe-Box — no such public integration surface currently exists for
  organisations to connect to.
- It does not file a complaint on SHe-Box on anyone's behalf — filing
  is done directly by the complainant through the government portal.
- It does not replace `posh-compliance` for the substantive IC process
  — this skill specifically addresses the SHe-Box routing layer on top
  of that process.

## Reference

- SHe-Box portal: shebox.wcd.gov.in (Ministry of Women and Child
  Development, Government of India)
