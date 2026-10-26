# Team rollout guide

## 1. Pick the starter set
| Team role | Start with |
|---|---|
| Campaign engineers | `acc-v8-campaign-qa`, `crm-ops-troubleshooter`, `stensul-troubleshooter` |
| Campaign / ops managers | `campaign-manager`, `chat-thread-analyzer`, `campaign-performance-report` |
| Leads & leadership reporting | `crm-evidence-report-pro`, `workload-assessment-builder`, `crm-explainer-video` |

## 2. Fill the Market Context once
Agree one version of each `Market Context` block for the team (markets, ID pattern, escalation path, benchmarks) and commit it to a private fork. Keep the public repo generic.

## 3. Install
- **Claude.ai (Team/Enterprise)**: an owner uploads the zipped skill folders so everyone gets them.
- **Individual**: Settings → Capabilities → Skills → Upload skill.
- **Claude Code**: copy `skills/*` to `~/.claude/skills/` or the project's `.claude/skills/`.

## 4. Pilot (2 weeks)
Run every pre-launch QA through `acc-v8-campaign-qa` in parallel with the normal checklist. Track: findings caught, false positives, minutes saved per campaign.

## 5. Feed it back
Each new incident becomes a known-issue entry (Symptoms → Root cause → Fix → Prevention) via pull request.
