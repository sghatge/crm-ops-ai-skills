---
name: workload-assessment-builder
description: |
  Build workload assessment workbooks, capacity models and leadership-ready operational reports for CRM operations teams. Use whenever the user asks for a "workload assessment", "capacity model", "demand vs capacity", "leadership report", "operational analysis", "team sustainability", "burnout risk", "MoM report", "monthly operational intelligence", an Excel workbook with multiple analysis sheets, Jira ticket analysis for workload patterns, SLA or intake governance proposals, or a "make the case for more resources" document. DO NOT fire for a single campaign's performance stats (use campaign-performance-report).
---

# Workload Assessment Builder

PRECEDENCE: team-level demand and capacity analysis routes here; single-campaign KPIs route to `campaign-performance-report`.

## Purpose
Create leadership-grade workbooks that quantify demand, capacity gaps, delivery risk and team sustainability for CRM operations.

## Market Context (edit for your organisation)
```
Markets in scope:        <Market A, Market B, ...>
Execution team:          <role — hours/week> (roles, not names, in shared copies)
Productive hrs per FTE:  <per period, after leave/holidays>
Escalation audience:     <leadership role>
Peak periods:            <launch weeks, migration windows>
```

## Campaign Type Reference (default effort model — replace with actuals)
| # | Campaign Type | Avg Effort (hrs) | Typical Urgency |
|---|---|---|---|
| 1 | Email campaign build | 8 | Medium |
| 2 | SMS setup | 5 | Medium |
| 3 | WhatsApp campaign | 5 | High |
| 4 | Push notification setup | 4 | Medium |
| 5 | Voucher extraction & re-upload | 7 | High (SFTP dependency) |
| 6 | Data extract / SFTP workflow | 6 | Medium-High |
| 7 | Proof review & QA | 3 | High (blocks sends) |
| 8 | Tracking/reporting data jobs | 8 | Low-Medium |
| 9 | Infrastructure / downtime comms | 4 | Reactive |
| 10 | Ad hoc / urgent requests | 6 | Critical (<24h) |
| 11 | Email-builder template builds | 4-6 | Medium (higher during migration) |
| 12 | GDPR / compliance queries | 3 | Medium |
| 13 | Resend campaigns | 4 | High |
| 14 | Platform migration coordination | 6-10 | High (time-bound) |

Every default is an ASSUMPTION until replaced with ticket data. Label it as such in the workbook.

## Reinforcing-Loop Patterns
Use these to explain *why* demand outpaces capacity, not just show the gap.
- **Briefing-Iteration Spiral** — incomplete brief → build on partial info → gap spotted mid-build → scope change → rework → repeat. Measure: scope-change comments per ticket.
- **Urgency Normalisation Trap** — everything urgent → team absorbs → requesters learn urgency works → no slack for real emergencies. Measure: % tickets with <24h deadline.
- **Capacity Compression Cycle** — fixed go-live + growing scope + flat capacity → quality trade-offs → rework → more compression. Measure: overtime hours, proof-rejection rate.

## Workbook Structure (10-sheet standard)
Load the xlsx skill before building.
1. **Executive Summary** — title bar, 4 KPI boxes (Total Requests, Effort hrs, Capacity hrs, Overload %), 3 colour-coded headlines, capacity-vs-demand table
2. **Demand Profile** — type × quarter volumes, share, effort, total hours, priority rank, totals row, top-2 drivers callout
3. **Time & Urgency** — avg TAT, % <24h, % <48h, peak-load risk, peak-period notes
4. **Capacity Model** — assumptions block, demand model, Overload = (Demand − Capacity) / Capacity × 100; GREEN <80%, AMBER 80–100%, RED >100%
5. **Requester Pressure Signals** — % tickets with follow-ups, scope changes, <24h deadlines, out-of-hours; 5 anonymised scenarios with pattern labels
6. **Root Causes (systemic)** — no SLA governance; unstructured intake; approval delays; mid-execution scope change; no prioritisation framework; external dependencies without SLA
7. **Business Risk** — Delivery, Quality, Team Sustainability
8. **Recommendations** — Immediate (0–2 wks), Mid-term (2–6 wks), Long-term (6+ wks)
9. **Executive Table** — one-page summary slide
10. **Leadership Brief** — opening statement, 3 evidence-backed headlines, explicit asks (SLA authority, prioritisation authority, capacity recognition)

## Formatting Standards
Navy #1F3864, mid blue #2E5F9E, accent #4472C4, red #C00000, orange #E36C09 · Arial 10/11/16pt · alternating white / #F2F2F2 rows · thin #BFBFBF borders · gridlines hidden · RAG always paired with a text label.

## Data Handling
- Ticket export supplied → use actual data
- Described verbally → use as input, mark as stated
- Nothing supplied → realistic assumptions, every one flagged, offer to replace with actuals

## Tone
Executive and data-led. "This is an operational design problem, not a team performance problem." Never attribute blame to individuals; describe requester behaviour as a pattern, anonymised.
