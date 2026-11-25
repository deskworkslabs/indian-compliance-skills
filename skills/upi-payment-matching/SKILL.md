---
name: upi-payment-matching
description: Use when reconciling UPI payments against orders, invoices or a ledger — matching UTRs to expected amounts, flagging short/excess/duplicate payments, and producing a reconciliation report for an Indian small business or vendor.
license: MIT
---

# UPI Payment Matching (India)

Matches incoming UPI payments to the orders, invoices, or dues they are
meant to settle, for a business that takes payment by UPI (GPay,
PhonePe, Paytm, BHIM, or a bank's own UPI handle) rather than a
payment gateway. Built for the common Indian small-business reality:
no payment gateway, no webhook, just a bank statement or a UPI app's
transaction history to reconcile by hand every day.

## When to use this skill

- End-of-day or end-of-week reconciliation of UPI collections against
  what was actually owed
- Chasing a **short payment** (customer paid less than the invoice,
  often by mistake or a bank/UPI-app rounding quirk)
- Spotting a **duplicate payment** (customer paid twice, e.g. retried
  after a UPI app showed a false failure)
- Matching a payment with **no clear reference** (UPI note field left
  blank, or filled with something generic like "payment")
- Producing a clean reconciliation report for the vendor or
  bookkeeper rather than a flat bank-statement dump

## The core matching problem

A UPI statement line typically gives: date/time, a UTR (Unique
Transaction Reference — a 12-digit number, the authoritative ID for
that transaction), the payer's VPA or masked name, the amount, and
whatever free-text note the payer typed (often blank or unhelpful).
There is usually **no reliable order ID in the payment itself** unless
the business asked the customer to put one in the note — and most
customers don't. The skill's job is closing that gap using the signals
that are actually available:

1. **Exact-amount match** — if only one open invoice/order has exactly
   this amount outstanding, match on amount + same-day timing alone.
   Flag as "confident match."
2. **Payer identity match** — if the VPA or masked name has been seen
   against a customer before (keep a running payer→customer map that
   grows over time as the business confirms matches), use it to
   break ties when two open invoices share the same amount.
3. **Note-field match** — if the note contains anything usable (a
   name, a partial order number, a phone number), use it as a
   tie-breaker, not as the sole signal — notes are typed by customers
   and frequently wrong or stale.
4. **Short payment** — if the amount is close to but less than an
   open invoice (common causes: customer subtracted a discount they
   assumed, a ₹1–5 UPI rounding difference, or a part-payment),
   surface it separately as "short by ₹X against invoice Y" rather
   than silently matching or silently ignoring it.
5. **Excess payment** — amount exceeds any single open invoice but
   matches the sum of two or more open invoices; offer that as a
   candidate match before treating it as a genuine overpayment/advance.
6. **No match found** — amount doesn't correspond to anything open;
   list it as unmatched rather than guessing, and ask whether it is
   an advance, a new order not yet entered, or a wrong account.

## Workflow

### 1. Intake
Accept the day's UPI transaction list (from a bank statement export,
or pasted from the UPI app's history) and the list of currently open
invoices/orders with amount due. Both are just data the vendor already
has — this skill does not require integrating with a payment gateway
or bank API.

### 2. Match pass
Run every incoming payment through the signal order above (exact
amount → payer history → note field → short/excess detection). Each
line ends in exactly one of: confident match, probable match (state
which signal and why), short payment against a named invoice, excess
payment, or unmatched.

### 3. Report
Produce a short reconciliation report grouped by outcome — matched
total, short-payment list (with the shortfall amount each), excess/
advance list, and unmatched list — rather than one long undifferentiated
table. This is the thing the vendor or bookkeeper actually needs:
what to chase, not a raw transaction dump they have to re-sort.

### 4. Learn the payer map
When the vendor confirms an uncertain match, record the VPA/masked-name
→ customer link so the next payment from that same payer resolves
automatically. This is the single highest-leverage improvement over
time — most repeat customers pay from the same UPI handle every time.

### 5. Flag, never auto-resolve, ambiguity
Never silently apply a payment to an invoice when two or more
invoices are equally plausible matches — surface the ambiguity and the
competing candidates, and let the vendor decide. A wrong auto-match is
worse than an unmatched line, because it hides a real discrepancy
behind a false "reconciled" status.

## What this skill does not do

- It does not connect to a bank or UPI API to pull transactions
  automatically — it works from whatever export or paste the vendor
  already has access to.
- It does not issue refunds, send payment requests, or take any
  action on the money itself — it only reconciles and reports.
- It does not replace GST invoice matching (HSN codes, tax
  components) — it matches gross payment amounts to orders/invoices;
  tax-ledger reconciliation is a separate concern.
