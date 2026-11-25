---
name: digital-evidence-documentation
description: Use when digital evidence (screenshots, call logs, messages, files, device images) needs to be preserved and documented so it holds up in an Indian court — chain of custody, hash verification, and the Section 65B certificate under the Indian Evidence Act / BSA.
license: MIT
---

# Digital Evidence Documentation (India)

Documents digital evidence to the standard an Indian court actually
requires, rather than the standard a layperson assumes is enough (a
screenshot alone). This is a process and paperwork aid for whoever is
collecting the evidence — a victim, an investigating officer, or an
organisation's own compliance/legal team — not a substitute for a
forensic expert where the case genuinely needs one.

## When to use this skill

- Preserving evidence of cyber fraud, harassment, defamation, or any
  incident where the proof lives on a phone, computer, or online
  platform
- Preparing evidence that will be submitted with a police complaint,
  an internal inquiry (e.g. a POSH Internal Committee), or a court
  filing
- Checking whether evidence already collected meets the legal standard
  for admissibility before it's relied on

## The core legal requirement most people miss

Under the Indian Evidence Act's Section 65B (and its equivalent under
the Bharatiya Sakshya Adhiniyam, 2023, which replaced it), **electronic
records are not automatically admissible just because they're real**.
A certificate under Section 65B(4) — identifying the device that
produced the record, confirming it was functioning properly, and
stating the output accurately reflects the original — is required for
the electronic evidence to be admissible *as evidence*, independent of
whether the content itself is genuine. A perfectly real, unedited
screenshot can be challenged and excluded for want of this certificate.
This is the single most common gap in evidence that otherwise looks
solid.

## Workflow

### 1. Capture with context, not just content
A bare screenshot of a message proves less than the same screenshot
with its surrounding context: the full conversation thread (not just
the one message), timestamps visible in the capture, the sender's
profile/number/handle visible, and — where the platform allows it — a
screen recording of scrolling through the thread rather than a single
static frame, since a recording is harder to credibly dispute as
selectively cropped.

### 2. Preserve the original, don't just keep the copy
Where possible, keep the original file/device/account accessible
rather than only a screenshot of it — a screenshot is a derivative;
the original message still live on WhatsApp, the original email still
in the inbox, the original file on the device, is the primary record.
If the original risks being deleted (e.g. a harassing account that may
be taken down, or a platform that auto-deletes messages), prioritise
capturing it immediately, but note in the documentation that the
original should also be preserved/exported through the platform's own
export tools where available (e.g. WhatsApp chat export, email
download as .eml).

### 3. Hash the file at the point of preservation
For evidence transferred into a file (an exported chat, a downloaded
image, a screen recording), generate a cryptographic hash (SHA-256 is
the common standard) of the file immediately after export and record
it alongside the file. This hash is what later proves the file wasn't
altered between the moment it was collected and the moment it's
produced — re-hash it before submission and confirm the values match.

### 4. Build the chain of custody record
For each piece of evidence, record: who collected it, exactly when
(date and time, not just "earlier"), from what device/account/source,
how it was transferred (e.g. "exported from WhatsApp on Device X,
transferred via USB to Laptop Y"), and who has had access to it since.
A gap in this chain — evidence that passed through an unaccounted
step — is the most common way otherwise-genuine evidence gets
successfully challenged.

### 5. Prepare the Section 65B certificate
Draft the certificate identifying: the device/system that produced the
electronic record, a statement that the device was operating properly
at the relevant time, and a statement that the output is an accurate
reproduction of the electronic record. This certificate needs to be
signed by a person occupying a responsible official position in
relation to the device/system (for an individual's own phone, this is
typically the individual themselves, as the person in control of and
familiar with the device's proper functioning) — have the right person
sign it, not whoever happens to be drafting the case.

### 6. Organise for submission
Produce an index: each piece of evidence, its hash, its chain-of-
custody summary, and whether its 65B certificate is attached — so
whoever receives the evidence package (police, an Internal Committee,
a court) can verify completeness at a glance rather than hunting
through a folder of loose files.

## What this skill does not do

- It does not perform forensic device imaging or recovery of deleted
  data — that requires a qualified forensic examiner and specialised
  tooling; this skill covers documentation of evidence that's already
  accessible.
- It does not give a legal opinion on whether a specific piece of
  evidence will be admitted or how persuasive it will be — that is for
  the presiding authority (court, IC, tribunal) to determine; this
  skill only gets the preservation and paperwork to the standard that
  gives it the best chance.
- It is not a substitute for an advocate's advice on building a case
  strategy around the evidence once collected.

## Reference

- Indian Evidence Act, 1872, Section 65B (electronic records)
- Bharatiya Sakshya Adhiniyam, 2023 (the Evidence Act's successor,
  carrying forward the equivalent electronic-record certification
  requirement)
