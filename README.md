# Indian Compliance Skills

Free, open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) for
compliance and operations work specific to India — the kind of process
knowledge that doesn't come pre-loaded into a general-purpose AI assistant,
because it's jurisdiction-specific and usually locked inside someone's head
or a law firm's template library.

Built and maintained by [Ethan Hakim](https://ethanhakim.in) — part of a
wider catalog of AI skills and connectors at
[ethanhakim.in/skills](https://ethanhakim.in/skills/).

## What's here

| Skill | What it does |
|---|---|
| [`posh-compliance`](skills/posh-compliance/SKILL.md) | Internal Committee setup, POSH policy drafting, complaint-handling structure and annual reporting under the POSH Act, 2013 |
| [`upi-payment-matching`](skills/upi-payment-matching/SKILL.md) | Reconcile UPI payments against orders/invoices with no payment gateway — matching, short-payment and duplicate-payment detection |
| [`aml-transaction-monitoring`](skills/aml-transaction-monitoring/SKILL.md) | AML red-flag screening, STR drafting support and KYC/CDD review under India's PMLA framework |
| [`cyber-fraud-first-response`](skills/cyber-fraud-first-response/SKILL.md) | The right first-24-hours sequence after UPI/bank fraud — 1930 helpline, NCRP filing, bank freeze, evidence preservation, in order |
| [`digital-evidence-documentation`](skills/digital-evidence-documentation/SKILL.md) | Preserve digital evidence to the standard an Indian court needs — chain of custody, hashing, and the Section 65B certificate |
| [`workplace-harassment-report-system`](skills/workplace-harassment-report-system/SKILL.md) | Design/review a confidential harassment-reporting intake system — disclosure tiers, encryption scope, the risks of public aggregate reporting |
| [`indian-bank-statement-reader`](skills/indian-bank-statement-reader/SKILL.md) | Parse inconsistent SBI/ICICI/HDFC/BoM statement exports (PDF or spreadsheet) into one clean, consistent transaction schema |
| [`rbi-circular-tracker`](skills/rbi-circular-tracker/SKILL.md) | Filter RBI circulars/Master Directions to what actually applies to a specific entity type, and summarise what changed and what's due |
| [`shebox-integration`](skills/shebox-integration/SKILL.md) | Align an organisation's POSH process with the Government's SHe-Box complaint portal as an intake channel into the same IC process |
| [`companies-act-compliance`](skills/companies-act-compliance/SKILL.md) | Private limited company's annual filing calendar — board meeting 120-day rule, AOC-4/MGT-7 deadlines, DIN KYC, statutory registers |
| [`india-compliance-checklist-generator`](skills/india-compliance-checklist-generator/SKILL.md) | Scope which of FEMA/Companies Act/SEBI/RBI actually apply to a specific business, then generate a dated, sourced checklist |

Each skill is a single `SKILL.md` file — plain markdown with a short
frontmatter header (`name`, `description`, `license`). That's the entire
format: no build step, no dependencies, nothing to install.

## Using these skills

**With Claude (claude.ai, Claude Code, or the API):** point Claude at a
`SKILL.md` file, or drop the `skills/<name>/` folder into a project where
Claude's skill-loading is enabled, and Claude will follow it the next time
a matching task comes up.

**With anything else:** these are plain markdown. Read one, adapt it, paste
relevant sections into your own prompts or internal documentation — there's
no lock-in.

## Why these, first

They're the compliance problems that actually show up for Indian
businesses and professionals day to day, and that generic AI assistants
routinely get wrong or vague on because the thresholds, timelines and
terminology are India-specific (₹10 lakh CTR thresholds, 7-working-day STR
filing clocks, POSH's 90-day inquiry window and 120-day board-meeting gap,
UPI's lack of a built-in order reference, the Section 65B certificate most
people don't know they need). More skills will be added here over time.

## Contributing

Issues and pull requests are welcome — especially corrections from anyone
who actually sits on an Internal Committee, runs AML monitoring, or
reconciles UPI payments for a living. If a rule, threshold or timeline
here is wrong or has changed, please open an issue.

## Disclaimer

These skills are process and documentation aids, not legal advice. Nothing
here should be relied on as a substitute for qualified legal counsel,
a licensed compliance officer, or your organisation's own Principal
Officer where the law requires one. See each `SKILL.md` for its own
"what this skill does not do" section.

## License

MIT — see [LICENSE](LICENSE). Use it, fork it, build on it.
