---
name: companies-act-compliance
description: Use when tracking annual filings, board meeting schedules, statutory registers and ROC deadlines for an Indian private limited company under the Companies Act, 2013.
license: MIT
---

# Indian Companies Act Compliance Tracker

Tracks the recurring statutory calendar every Indian private limited
company must meet under the **Companies Act, 2013** — annual filings,
board meeting frequency, statutory registers, and Registrar of
Companies (ROC) deadlines. Built for a small-to-mid private limited
company's own compliance tracking, not for listed companies, which
carry significant additional SEBI-layer obligations beyond this scope.

## When to use this skill

- Building or reviewing a company's annual compliance calendar
- Checking whether board meeting frequency and statutory registers are
  up to date
- Working out what's due, and by when, around financial year-end
- Catching a missed filing before it compounds into a larger penalty
  or disqualification risk

## The core annual obligations

1. **Board meetings** — minimum **4 meetings per calendar year**, with
   a maximum gap of **120 days** between two consecutive meetings (a
   company holding exactly 4 meetings but bunched together, leaving a
   long gap elsewhere, fails this requirement even though the headcount
   looks compliant — check the gap, not just the count).
2. **Annual General Meeting (AGM)** — for most private companies, held
   within **6 months of financial year-end** (so by 30 September for a
   31 March year-end), and within 9 months for the very first AGM after
   incorporation.
3. **Financial statements and Board's Report** — approved at the AGM,
   filed with ROC via **Form AOC-4** within **30 days of the AGM**.
4. **Annual Return** — filed via **Form MGT-7** (or MGT-7A for small
   companies/OPCs) within **60 days of the AGM**.
5. **Statutory registers** — maintained on an ongoing basis, not just
   at filing time: Register of Members, Register of Directors and KMP,
   Register of Charges, Register of Contracts in which directors are
   interested, and others as applicable — these must be kept current
   as events happen (a new director appointed, a charge created), not
   reconstructed retroactively at year-end.
6. **DIN KYC (DIR-3 KYC)** — every director with a DIN must complete
   annual KYC by **30 September** each year; missing this deactivates
   the DIN, which then blocks the director from being validly appointed
   or continuing on filings until reactivated.
7. **Auditor appointment/ratification** — tracked separately from the
   AGM cycle itself; a first auditor appointment has its own timeline
   from incorporation, and subsequent appointments align with AGM
   cycles under the current (post-2017 amendment) framework, which no
   longer requires annual ratification but does require tracking the
   auditor's term.

## Workflow

### 1. Build the calendar backward from financial year-end
Starting from the company's financial year-end date, calculate: AGM
deadline (+6 months), AOC-4 deadline (+30 days from AGM), MGT-7
deadline (+60 days from AGM), DIR-3 KYC deadline (fixed 30 September
regardless of the company's own year-end), and the board-meeting
schedule needed to stay within the 120-day maximum gap across the year.

### 2. Cross-check board meeting history against the 120-day rule
Given the dates of board meetings already held, calculate the gap
between each consecutive pair and flag any gap approaching or
exceeding 120 days **before** it's breached, not after — the whole
value of tracking this is catching it with enough runway to schedule
a meeting in time.

### 3. Register currency check
For each statutory register, check whether the last recorded update
date aligns with known events (a new director appointment, a share
transfer, a charge registered) — a register that hasn't been touched
despite a known triggering event is the flag to raise, more useful
than a generic "review your registers" reminder.

### 4. Filing status tracker
Maintain a simple due/filed/overdue status per filing (AOC-4, MGT-7,
DIR-3 KYC per director) per financial year, so a single glance shows
what's outstanding rather than having to reconstruct status from ROC's
own portal each time.

### 5. Flag DIN deactivation risk early
Specifically surface any director whose DIR-3 KYC deadline is
approaching, since a deactivated DIN has knock-on effects (blocks
filings naming that director) well beyond the KYC requirement itself —
this is worth flagging earlier and more insistently than other
deadlines given its cascading effect.

## What this skill does not do

- It does not file anything with the ROC — all filings go through the
  company's own MCA portal access and the company secretary/practising
  professional who certifies them where required.
- It does not cover listed-company obligations (SEBI LODR, insider
  trading code compliance, etc.) — this is scoped to private limited
  company obligations under the Companies Act alone.
- It does not give a legal opinion on a specific transaction's
  compliance treatment (e.g. related-party transaction approval
  requirements for a specific deal) — flag those to the company's
  practising company secretary or legal counsel.

## Reference

- Companies Act, 2013, and the Rules made thereunder
- MCA (Ministry of Corporate Affairs) filing portal: mca.gov.in
