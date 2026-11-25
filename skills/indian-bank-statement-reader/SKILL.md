---
name: indian-bank-statement-reader
description: Use when parsing an Indian bank statement (PDF, CSV, or Excel export from SBI, ICICI, HDFC, Bank of Maharashtra, or similar) into clean structured transactions — handling the inconsistent formats, narration codes, and balance columns each bank uses differently.
license: MIT
---

# Indian Bank Statement Reader

Parses a bank statement export into clean, structured transaction rows
— date, narration, debit, credit, running balance, and a best-effort
category — handling the fact that **every Indian bank formats its
statement exports differently**, often inconsistently even within the
same bank across account types or export formats (PDF vs. CSV vs. the
net-banking portal's own Excel export).

## When to use this skill

- Converting a downloaded statement (PDF or spreadsheet) into usable
  structured data for reconciliation, bookkeeping, or the
  `upi-payment-matching` skill's input
- Reviewing a statement for unusual activity or categorising a period's
  transactions
- Normalising **statements from multiple banks** into one consistent
  schema before combining them

## The core parsing problem

Unlike a single-format API response, a bank statement export has no
guaranteed structure:
- **PDF exports** are the hardest case — tables are often not real PDF
  tables but visually-aligned text, so column boundaries have to be
  inferred from spacing/position, not parsed from markup. Multi-line
  narrations (a long UPI reference wrapping to a second line) are a
  frequent source of misaligned rows if handled naively.
- **CSV/Excel exports** vary by bank in column order, header names
  (`Txn Date` vs `Value Date` vs `Date`), and whether debit/credit are
  one signed column or two separate columns.
- **Narration text** is where the real transaction meaning lives but is
  bank-specific shorthand: UPI references often encode payer VPA
  fragments, IMPS/NEFT references encode a different pattern again, and
  POS/card transactions show merchant codes rather than merchant names.
  A generic "clean this text" approach misses what's actually
  extractable from each code format.

## Workflow

### 1. Detect the source format and bank
Before parsing content, identify: PDF or tabular file; if tabular,
which bank's known column layout it matches (keep a small growing
library of column-header signatures per bank rather than re-detecting
from scratch each time — SBI, ICICI, HDFC and Bank of Maharashtra
layouts recur and are worth hardcoding once confirmed).

### 2. Extract rows, handling bank-specific quirks
- Two-column debit/credit banks: treat a populated debit cell as
  negative, credit as positive, for a consistent signed-amount
  convention in the output regardless of the source format.
- Multi-line narrations in PDFs: detect continuation lines by the
  absence of a new date/amount pattern, and merge them into the
  preceding row's narration rather than treating them as new,
  malformed transactions.
- Running balance column: use it as a consistency check — reconstruct
  the implied balance from the opening balance plus signed amounts,
  and flag any row where the reconstructed balance doesn't match the
  stated balance, since this usually means a row was mis-parsed
  (merged, split, or an amount misread) rather than a genuine bank
  error.

### 3. Decode narration where the pattern is known
- UPI: typical pattern includes a UPI reference number and often a
  payer/payee VPA fragment or masked name — extract what's there
  without inventing structure the narration doesn't actually contain.
- NEFT/IMPS/RTGS: typically carry a UTR and the counterparty bank/
  account reference in a different format from UPI's.
- POS/card: typically a merchant code and location rather than a
  clean merchant name — flag these as lower-confidence for
  categorisation rather than guessing a merchant name from a partial
  code.

### 4. Categorise, conservatively
Apply categorisation (salary, utility, transfer, POS purchase, etc.)
only where the narration pattern gives real signal, and mark anything
else as "uncategorised" rather than forcing every row into a category.
A statement with 70% correctly categorised and 30% honestly
uncategorised is more useful than one with 100% categorised but a
meaningful share silently wrong.

### 5. Output a consistent schema regardless of source bank
Date, narration (cleaned), debit, credit, balance, category
(nullable), and a `source_confidence` flag per row for anything parsed
from a visually-inferred PDF table rather than real tabular data — so
downstream use (e.g. feeding into `upi-payment-matching`) can treat
low-confidence rows with appropriate caution rather than trusting every
row equally.

## What this skill does not do

- It does not connect to a bank's API or scrape net-banking directly —
  it works from an export the account holder already has in hand.
- It does not guarantee perfect parsing of every PDF layout — flagging
  low-confidence rows honestly is the design goal, not claiming 100%
  accuracy on an inherently messy input format.
- It does not perform tax categorisation (GST input/output matching) —
  it produces clean transaction data; tax-specific categorisation is a
  separate downstream step.
