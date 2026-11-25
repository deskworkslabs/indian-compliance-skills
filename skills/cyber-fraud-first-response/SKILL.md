---
name: cyber-fraud-first-response
description: Use when a cyber-fraud victim or a cyber-cell officer needs to act in the first hours after an incident (UPI/bank fraud, account takeover, phishing) — bank freezing, the 1930 helpline and NCRP complaint, and evidence preservation, in the right order.
license: MIT
---

# Cyber-Fraud First Response (India)

Walks a victim, or the person helping them, through the first 24–48
hours after a cyber-financial fraud in India — the window in which
speed decides whether money can actually be recovered. This is a
process checklist, not legal representation; for anything beyond the
first response (disputes with the bank, filing a formal FIR narrative
in a complex case) the victim should also involve a lawyer or
approach the cyber cell directly.

## When to use this skill

- A victim has just discovered an unauthorised UPI/bank transaction,
  a card fraud, an account takeover, or a phishing-link compromise
- A cyber-cell constable or officer is triaging an incoming complaint
  and needs the right first-response sequence
- Someone is asking "what do I do right now" within minutes to hours
  of noticing the fraud — this skill is explicitly optimised for speed
  over completeness

## Why order matters here

Recovery odds in digital-payment fraud drop sharply with time — banks
can usually only hold or reverse funds that haven't yet moved out of
the receiving account. The single highest-leverage action in any
cyber-fraud case is **freezing the money before it disperses further**,
which is why this skill puts that step first, ahead of filing
paperwork that feels more official but buys no time.

## The sequence

### 1. Call 1930 immediately (the National Cyber Crime Helpline)
This is the single fastest lever: 1930 connects directly to the banking
ecosystem's fraud-reporting network and can trigger a hold request on
the receiving account before the money moves further downstream. Do
this **before** anything else, including filing the NCRP complaint —
the call itself can initiate the freeze; the online complaint that
follows formalises it.

What to have ready before calling: approximate time of the transaction,
amount, the UPI transaction ID / UTR or the debited account's last 4
digits, and the mode (UPI, net banking, card, IMPS).

### 2. File on the National Cyber Crime Reporting Portal (cybercrime.gov.in)
File the complaint within the same window, ideally same day. The
portal generates an acknowledgment number — record this immediately,
it's the reference used in every subsequent follow-up with the bank,
the helpline, or the local police station. For financial fraud
specifically, use the portal's dedicated financial-fraud reporting
flow rather than the general cybercrime category, since it routes
faster to the banking-fraud response chain.

### 3. Contact the victim's own bank directly, in parallel
Don't rely on 1930/NCRP alone — call the bank's fraud/customer-care
line directly to report the unauthorised transaction and request an
account-level block if account credentials (not just a single
transaction) were compromised. RBI's limited-liability framework for
customers (for unauthorised electronic transactions reported promptly)
makes the **timing of this report** material to how much liability the
customer bears — reporting within the bank's stated window (commonly
referenced as "within 3 working days" for zero liability in many
cases, though this varies by circumstance and the bank's own policy)
is worth stating explicitly to whoever is filing it.

### 4. Preserve evidence before it's gone
Screenshot, don't just note down: the transaction record/SMS, any
phishing message or fake app/website involved, the UPI collect
request if that was the vector, and any call-log entry if a phone call
was part of the fraud (a classic pattern: a call impersonating bank
support just before the transaction). See the companion
`digital-evidence-documentation` skill for how to preserve this so it
holds up later — chain of custody and hash verification matter even
for a victim's own phone screenshots if the case proceeds further.

### 5. Change credentials and check for further compromise
Once the immediate reporting is done: change the UPI PIN, net-banking
password, and any password reused elsewhere if a phishing link was
involved (credential reuse means one phished password can compromise
multiple accounts). Check for unauthorised standing instructions,
auto-pay mandates or linked accounts that may have also been touched.

### 6. Follow up — don't file and forget
Track the NCRP acknowledgment number and the bank's complaint/ticket
number; follow up with the bank on fund-hold/reversal status and with
the local cyber cell if the case needs to escalate to an FIR for a
larger amount or an organised pattern. Recovery, when it happens, is
rarely immediate — set the expectation that this is a tracked process
over days to weeks, not a same-day resolution.

## For a cyber-cell officer using this skill

Use it as a fast intake script with a victim who is often in distress
and unfamiliar with the process: confirm what's already been done (has
1930 been called? NCRP filed?) before repeating steps, prioritise
getting the bank-side freeze request moving if it hasn't started, and
capture the acknowledgment/reference numbers from every channel the
victim has already used so they aren't duplicated or lost.

## What this skill does not do

- It does not guarantee fund recovery — the freeze-and-report sequence
  improves the odds; it cannot promise an outcome, which depends on
  whether funds have already moved out of the first receiving account.
- It does not replace filing an FIR where the amount or pattern
  warrants one, or legal counsel for a dispute with the bank over
  liability.
- It does not itself file anything — it is a sequence and checklist
  for the victim or officer to execute through the real channels
  (1930, cybercrime.gov.in, the bank's own fraud line).

## Reference

- National Cyber Crime Reporting Portal: cybercrime.gov.in
- National Cyber Crime Helpline: 1930
- RBI's customer-liability circular for unauthorised electronic
  banking transactions
