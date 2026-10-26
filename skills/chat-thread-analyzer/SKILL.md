---
name: chat-thread-analyzer
description: |
  Analyze team chat conversations, Jira ticket threads and email chains to extract timeline, accountability, blockers and next steps. Use whenever the user pastes timestamped chat messages (e.g. "[Name] MM-DD-YYYY HH:MM"), Jira comment threads ("added a comment - date") or multi-person email threads, or asks to "explain who did what", "find the blocker", "show the timeline", "summarize the conversation", "draft a Jira comment" or "what's the action item". DO NOT fire when the user wants a formal evidence-classified postmortem (use crm-evidence-analyst or crm-evidence-report-pro).
---

# Chat Thread Analyzer

PRECEDENCE: quick thread triage routes here; formal postmortems route to the evidence skills.

## Purpose
Turn multi-person threads into structured intelligence: timeline, roles, issues, blockers, pressure signals and actions.

## Market Context (edit for your organisation)
```
Business hours / timezone: <e.g. 09:00–18:00 CET>
Internal team roles:       <role list — map names at runtime from the thread>
Requester roles:           <client / market roles>
```
Do not store personal behaviour profiles of named people in this file. Infer roles from the thread itself each time.

## Input Formats
```
[Person Name] MM-DD-YYYY HH:MM
message text
```
```
Person Name added a comment - YYYY-MM-DD HH:MM
comment text
```
```
From: Name <email>
Sent: date
Subject: ...
```

## Analysis Framework
1. **Timeline** — every action with exact timestamp; table Time | Who | What; response gaps >30 min on urgent threads; out-of-hours activity.
2. **Role mapping** — who requested, who executed, who approved, who blocked — from the thread only.
3. **Issues** — what went wrong (factual), systemic root cause (brief gap, scope change, dependency, timing), owner of the fix, impact.
4. **Pressure signals** — repeated follow-ups within 30 min, scope change after approval, out-of-hours "ASAP", compressed timelines, delay attributed to the wrong party.
5. **Action items** — owner, action, deadline (stated or marked inferred), status, blocker.

## Output
**Default**: one-line summary → timeline table → issues with root cause → accountability map → open actions → recommended reply (draft).
**On request — pressure report**: each urgency instance with timestamp; per-person pattern; quantified (X follow-ups in Y minutes, Z post-approval scope changes).
**On request — draft response**: variants matched to the recipient's role; context without over-explaining. Drafts only.

## Rules
- Factual and systemic, never personal blame. Say "gap on {role}'s side", not "fault".
- If the team executed correctly on approved specs, say so plainly.
- Flag requirements that arrived after execution started.
- Evaluate the user's own proposed solution objectively, with gaps.
- Mark any inferred deadline or owner as inferred.
