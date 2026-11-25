---
name: workplace-harassment-report-system
description: Use when designing or reviewing a workplace harassment reporting system — encrypted/confidential submission, anonymous aggregate reporting, and the rules for when and how a company can be named — for an organisation or platform building this capability.
license: MIT
---

# Workplace Harassment Report System (India)

Design and review guidance for building a workplace-harassment
reporting system — whether an internal tool for one organisation or a
platform intended to serve many. This complements (and should be built
alongside) `posh-compliance`, which covers the Internal Committee
process the reports ultimately feed into: this skill is about the
*intake and reporting system* itself — how a report gets in safely,
and how aggregate data can responsibly be shown — not the inquiry
process that follows.

## When to use this skill

- Designing a confidential/anonymous intake channel for harassment
  complaints, separate from or feeding into a formal IC process
- Deciding what can and can't be shown publicly or in aggregate (e.g.
  "how many reports does Company X have") without creating legal or
  ethical exposure
- Reviewing an existing reporting tool for confidentiality gaps before
  it goes live

## The core tension this skill manages

A good reporting system has to satisfy two needs that pull against
each other: it must be **safe enough that people actually use it**
(confidentiality, no fear of retaliation, a real option to stay
anonymous), while the organisation (or society, if this is a
public-facing platform) still needs **enough signal to act** — a
completely anonymous report with zero identifying information can be
impossible to investigate at all. Every design decision below is about
where to sit on that spectrum deliberately, rather than defaulting to
one extreme without noticing the trade-off.

## Design principles

### 1. Offer tiers of disclosure, not a binary
- **Fully anonymous**: no identifying information captured at all.
  Useful for pattern-detection (e.g. "multiple reports naming the same
  department") but cannot usually support a formal inquiry, since POSH
  process requires identifying the parties for a fair hearing.
- **Confidential, identity withheld from the respondent**: the
  complainant is known to the IC/system but not disclosed beyond what
  Section 16 of the POSH Act already requires to stay confidential.
  This is the tier that actually supports a formal inquiry while
  giving the complainant real protection from direct retaliation.
- **Named, formal complaint**: full identification, the standard IC
  complaint path.

Let the reporter choose the tier, and be explicit up front about what
each tier can and can't lead to — an anonymous report that can only
inform patterns, not trigger a named inquiry, should say so at the
point of submission, not leave the reporter assuming otherwise.

### 2. Encrypt at rest and in transit, and minimise who can decrypt
If the system stores identifying details, encrypt them, and restrict
decryption access to the minimum necessary (the IC's Presiding Officer
and whoever administers the system) — not the whole HR team by
default. The confidentiality obligation under Section 16 of the POSH
Act is a legal requirement, not just good practice, and a breach of it
is itself punishable.

### 3. Separate the "report exists" signal from the "report content"
A system can let relevant people know a report has come in — to start
the clock on IC timelines — without exposing its content to everyone
who sees that signal. Design the notification layer and the content
layer as genuinely separate permission levels.

### 4. Public/aggregate reporting — tread very carefully
If the system (especially a platform-level one, not a single
company's internal tool) is considering showing **aggregate counts
publicly**, e.g. "Company X has N reports filed," this needs explicit
legal review before building, not after:
- An unverified count naming a specific employer risks defamation
  exposure if reports are unsubstantiated, retracted, or from bad-faith
  actors — "number of reports filed" is not the same claim as "number
  of substantiated findings," and conflating the two in a public
  display is a real legal risk.
- Aggregate numbers without context (no denominator — company size,
  time period) can also be genuinely misleading rather than merely
  risky, and misleading-but-technically-true displays carry their own
  reputational and legal exposure for whoever publishes them.
- If building this feature at all, the safer shape is: substantiated-
  finding counts only (post-inquiry, not raw report counts), with
  clear time windows and company-size context, and a right-of-reply or
  correction mechanism for the named organisation.

### 5. Build in retaliation-monitoring, not just intake
A reporting system's job doesn't end at intake — flag follow-up
check-ins with the reporter (where they've consented to continued
contact) to catch retaliation separately from the harassment
complaint itself, since retaliation is its own violation under most
frameworks and often goes unreported if nobody asks.

## Workflow for reviewing an existing system

1. Map which tier (anonymous / confidential / named) each intake path
   actually offers, and check the UI is honest about what each tier
   can lead to.
2. Check encryption and access-control scope — who can decrypt
   identifying data, and is that the minimum necessary set of people.
3. If any public/aggregate display exists, check it against the
   defamation-risk principles above before treating it as safe to ship.
4. Confirm the system's output format is compatible with what the IC
   actually needs for Section 21/Rule 14 annual reporting (see
   `posh-compliance`) — a reporting system that captures great detail
   but can't produce the statutory annual-report numbers creates
   duplicate work downstream.

## What this skill does not do

- It does not conduct the harassment inquiry itself — that's the IC's
  statutory role (see `posh-compliance`).
- It does not give a definitive legal clearance for a public
  company-naming feature — that needs a qualified lawyer's sign-off
  given the defamation exposure involved, this skill only flags where
  that review is non-negotiable.
- It does not replace a security audit of the actual encryption
  implementation — it tells you what the access-control design should
  achieve, not how to implement cryptography correctly.
