---
name: rbi-circular-tracker
description: Use when monitoring RBI circulars, master directions and notifications for relevance to a specific regulated entity type, and summarising what changed and what action it requires.
license: MIT
---

# RBI Circular Tracker

Monitors Reserve Bank of India circulars, Master Directions, and
notifications, and filters them down to what's actually relevant to a
specific entity — a bank, an NBFC, a payment aggregator, a co-operative
bank — rather than treating every RBI publication as equally applicable
to everyone it reaches.

## When to use this skill

- Keeping a compliance function current on regulatory changes without
  manually reading everything RBI publishes
- Triaging a new circular: does this apply to us, and if so, what do
  we actually need to do and by when
- Building a change log of what's changed in a given area (KYC, digital
  lending, payment aggregators) over a period

## Why filtering matters more than monitoring

RBI publishes a high volume of circulars, many narrowly scoped to
entity types that don't apply to a given organisation (a circular
amending co-operative bank licensing norms is irrelevant to a payment
aggregator, and vice versa). The real value of this skill isn't
"here's everything RBI published" — that's just noise at scale — it's
**correctly identifying the subset that actually applies**, which
requires understanding how RBI scopes its own circulars.

## How RBI scopes applicability (the signals to check)

1. **The addressee line** — every circular opens by naming exactly
   which entities it applies to ("All Scheduled Commercial Banks",
   "All Non-Banking Financial Companies", "All Payment System
   Operators and Payment System Participants", etc.). This is the
   single most reliable filter — match the organisation's actual
   regulatory category against this line before reading further.
2. **Master Direction vs. circular vs. notification** — a Master
   Direction consolidates and supersedes prior instructions on a topic
   into one standing document (meant to be the current reference,
   updated in place); a circular is typically a specific instruction or
   amendment; a notification often relates to a specific regulatory
   action. Track which Master Direction a new circular amends, since
   the circular alone, read in isolation, can miss context the Master
   Direction provides.
3. **Effective date vs. issue date** — flag both; a circular is often
   issued with a future effective date or a phased compliance timeline,
   and the action deadline is what actually matters operationally, not
   the publication date.

## Workflow

### 1. Entity-type filter
Given the organisation's regulatory category (e.g. "NBFC — Investment
and Credit Company", "Payment Aggregator", "Scheduled Commercial Bank"),
filter incoming circulars to those whose addressee line matches, before
doing any deeper analysis.

### 2. Summarise what changed, not just what was published
For each applicable circular: what specifically changed versus the
prior position (cite the specific Master Direction section being
amended where identifiable), what action it requires (a process
change, a reporting update, a board approval, a one-time filing), and
the effective/compliance date.

### 3. Flag conflicts or ambiguity rather than resolving them silently
Where a new circular appears to partially overlap with or seem to
conflict with an existing Master Direction provision, flag this
explicitly for the compliance team's own legal review rather than
picking an interpretation — RBI circular interpretation in genuinely
ambiguous cases is a legal judgement call, not something to resolve
by assumption.

### 4. Maintain a running change log
Keep a dated log per topic area (KYC/CDD, digital lending, payment
aggregators, etc.) of what's changed and when, so a point-in-time
question ("what were the KYC requirements as of March") can be
answered without re-reading every historical circular from scratch.

## What this skill does not do

- It does not provide a legal opinion on how to implement a change —
  it identifies what changed and flags the action required; the
  implementation plan is the compliance team's own work.
- It does not replace subscribing to RBI's official circular feed as
  the source of truth — it's a filtering and summarisation layer on
  top of circulars actually published by RBI, not an independent source.
- It does not track SEBI, IRDAI, or other regulators' circulars — this
  is RBI-specific; an entity regulated by multiple regulators needs the
  equivalent tracking built per regulator.

## Reference

- RBI circulars and Master Directions: rbi.org.in
