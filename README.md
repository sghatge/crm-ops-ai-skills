# CRM Ops AI Skills

**An evidence-first AI operating layer for multi-market CRM & Marketing Operations teams.**

Ten Claude Agent Skills that codify how a senior Marketing Ops team runs Adobe Campaign Classic v8 and Stensul operations: pre-launch QA, troubleshooting, performance reporting, lifecycle tracking, postmortems and capacity cases — with one non-negotiable rule:

> **The AI never invents a campaign ID, date, count, owner or approval.** Every finding is labelled FACT / HYPOTHESIS / ASSUMPTION / UNKNOWN and traced to its source. Missing evidence is reported as missing.

---

## Why this exists

Generic AI assistants are fluent but unsafe for campaign operations: they fill gaps with plausible numbers, merge campaigns, and guess timelines. In CRM ops one wrong recipient count or invented approval is an incident.

These skills turn tribal knowledge into a repeatable, governed pipeline:

| Problem | What the skills enforce |
|---|---|
| Inconsistent pre-launch QA across markets | One 7-stage review with a severity scale and GO / NO-GO verdict |
| Same incidents rediscovered by each engineer | A known-issues database with root cause → fix → prevention |
| Reports that take hours to format | Raw Adobe Campaign stats → DOCX report + stakeholder email drafts |
| Postmortems built on hearsay | 2+ independent sources for any root cause; coverage log of what was *not* searched |
| "We need more people" with no numbers | A 10-sheet capacity model with systemic root causes |

## The skills

| Skill | Use it when you… | Output |
|---|---|---|
| `campaign-manager` | need go/no-go, lifecycle status, risk scans, audience validation, chasers | Classified findings + labelled recommendations |
| `acc-v8-campaign-qa` | review an ACC v8 build before launch, or diagnose a bad send | Verdict + findings table (stage, severity, evidence, fix, owner) |
| `crm-ops-troubleshooter` | hit an Adobe Campaign error, SFTP/voucher issue, typology or data-pipeline problem | Layer-isolated diagnosis from a known-issues database |
| `stensul-troubleshooter` | run Stensul builds, provisioning, or a migration off a legacy builder | Fixes, archival process, UAT mapping, comms templates |
| `campaign-performance-report` | paste raw delivery/open/click stats | DOCX report + 2 email draft variants |
| `chat-thread-analyzer` | paste a Teams/Jira/email thread | Timeline, accountability map, blockers, draft reply |
| `crm-evidence-analyst` | need an evidence-only postmortem or Jira summary | FACT/HYPOTHESIS/ASSUMPTION/UNKNOWN findings |
| `crm-evidence-report-pro` | need a leadership-grade audit with source-access labels | Coverage log, evidence matrix, action-titled sections |
| `workload-assessment-builder` | need to quantify demand vs capacity | 10-sheet Excel capacity model + leadership brief |
| `crm-explainer-video` | need a 1–2 min stakeholder explainer | HyperFrames MP4 storyboard + render |

## Design principles

1. **Evidence before fluency.** Facts are sourced; recommendations are labelled; the two never mix.
2. **Disjoint triggers.** Each skill keys off a different input shape and carries an explicit `DO NOT fire when…` block and a `PRECEDENCE` line, so the right skill fires.
3. **Market-agnostic core, editable context.** Every skill has a `Market Context` block — fill in your markets, owners and conventions; the method stays the same.
4. **Root cause before recommendation.** Every diagnostic skill ends symptom → cause → fix → prevention.
5. **Automation bias.** When a manual check fails and could recur, the skill recommends an alert, rule or pre-send gate.
6. **Drafts only.** No skill sends email or messages on anyone's behalf.

## Install

### Claude.ai / Claude desktop
1. Zip a skill folder (e.g. `skills/acc-v8-campaign-qa/`).
2. Settings → Capabilities → Skills → **Upload skill**.
3. Repeat for each skill your team needs. Org admins can provision them for the whole team.

### Claude Code
```bash
git clone https://github.com/<your-username>/crm-ops-ai-skills.git
mkdir -p ~/.claude/skills
cp -r crm-ops-ai-skills/skills/* ~/.claude/skills/
```
Or per project: copy into `.claude/skills/` in the repo.

### First-run setup
Open each `SKILL.md` and fill in the **Market Context** block (markets, campaign ID pattern, escalation path, benchmarks). Leave anything unknown as `TBC` — the skills will ask rather than guess.

## Example prompts

```
Review this ACC v8 workflow export and proof screenshots for Market A — go or no-go?
Here are the delivery stats for W43 onboarding email. Build the report and two email drafts.
Proof generation hangs on send — here's the workflow log.
Paste: 40-message Teams thread. Who owes what, and what's blocking the send?
Build a workload assessment from this Jira export for Q3.
```

## Repository layout
```
skills/
  <skill-name>/SKILL.md
docs/
  INSTALL.md
CONTRIBUTING.md
LICENSE
```

## Contributing
Add a known issue, a benchmark range or a new play via pull request. See [CONTRIBUTING.md](CONTRIBUTING.md). Never commit real customer data, recipient lists, internal paths or colleague names.

## Author
Built by **Sangram Ghatge** — Marketing Ops & CRM Technology lead (Adobe Campaign Classic v8, Stensul, Salesforce, AI operating models).
[LinkedIn](https://www.linkedin.com/in/sangram-g-2369705b) · [GitHub](https://github.com/sghatge)

## License
MIT — see [LICENSE](LICENSE).
