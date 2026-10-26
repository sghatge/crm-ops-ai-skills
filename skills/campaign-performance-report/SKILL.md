---
name: campaign-performance-report
description: |
  Generate professional campaign performance reports from raw Adobe Campaign statistics. Use whenever the user pastes raw campaign data (delivery stats, open/click rates, domain breakdowns, segment counts, tracking indicators), asks for a "performance report", "campaign report", "stats report" or "KPI summary", mentions delivery rate / open rate / CTR / reactivity, or wants to share campaign results with stakeholders by email. Covers Email, SMS, WhatsApp and Push campaigns. DO NOT fire for team workload or capacity analysis (use workload-assessment-builder).
---

# Campaign Performance Report Generator

PRECEDENCE: single-campaign or campaign-batch KPIs route here.

## Purpose
Turn raw Adobe Campaign v8 statistics into a client-ready DOCX report and stakeholder email drafts.

## Market Context (edit for your organisation)
```
Markets in scope:     <Market A, Market B, ...>
Naming convention:    W{week}_{YYYYMMDD}_{market}_{lang}_{country}_{channel}_{type}_{campaign}-{segment}-{variant}
Benchmarks:           <your own ranges, per market — defaults below are placeholders>
Report footer:        "Generated from Adobe Campaign v8 | {Team name}"
Brand colour:         <hex>
```

## Input Recognition
- **Delivery**: messages to deliver, success, errors, new quarantines
- **Reception**: distinct opens, sum of opens, opt-outs, forwards
- **Domains**: Gmail, Microsoft, Yahoo, AOL, others — sent/opens/clicks
- **Segments**: names with population, open and click rates
- **Tracking**: opens / clicks / transactions flags
- **Campaign name** matching the naming convention

## Workflow

### Step 1: Parse & Calculate
Delivery summary · Reception KPIs · Click performance (distinct clicks, CTR, reactivity) · Domain table · Segment table · Web tracking (flag zero transactions) · 5–9 key observations.

### Step 2: Insights to Always Check
- Engaged vs non-engaged segment gap (engaged segments often outperform 2–3×)
- Top segment by open rate AND by reactivity (often different)
- Gmail share of volume and its effect on overall rates
- Zero complaints = clean sender reputation
- Zero transactions = was purchase tracking expected?
- Opt-out rate against the market's own benchmark
- Country-level variance on multi-country sends; report absolute numbers next to percentages for small bases

### Step 3: DOCX Report
Load the docx skill first. Sections: Title block · Delivery summary · Reception · Click streams · Domain performance · Segment performance (totals row) · Country breakdown (optional) · Key observations · Footer.

### Step 4: Stakeholder Email Drafts
Two variants: **Formal report share** (full summary) and **Short & punchy** (key numbers only). Structure: campaign ID + send date, 5–6 metrics, 2–3 highlights, reference to the attached report, sign-off from the Market Context. Match tone to the recipient's role (leadership: structured with clear ownership; marketing contacts: supportive; approvers: action-oriented). Drafts only — never send.

### Step 5: Present
Deliver the DOCX and show the email drafts inline.

## Default Benchmarks (placeholders — replace with your own)
| Metric | Good | Average | Needs Attention |
|---|---|---|---|
| Delivery rate | >97% | 95–97% | <95% |
| Distinct open rate | >15% | 10–15% | <10% |
| CTR | >0.2% | 0.1–0.2% | <0.1% |
| Reactivity | >1% | 0.5–1% | <0.5% |
| Opt-out rate | <0.03% | 0.03–0.1% | >0.1% |

## Rules
- Every number comes from the pasted data. Never fill a missing metric.
- Show calculation basis (numerator/denominator) when a rate is derived.
