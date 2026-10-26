# Showcase — what you type, what you get

All data below is fictional and shows output **shape**, not real results.

---

## 1. Pre-launch QA → GO / NO-GO in minutes
**Skill:** `acc-v8-campaign-qa` · **Manual:** ~90 min · **With skill:** ~30 min

**You type**
```
Review this ACC v8 campaign before tomorrow's 09:00 CET send.
Attached: workflow export, delivery properties, proof screenshots (HR, SI, EN).
Brief: Market A loyalty email, opted-in members active in last 180 days.
```

**You get**
> **Verdict: NO-GO** — 1 Blocker, 2 High, 1 Medium
>
> | # | Stage | Severity | Finding | Evidence | Fix | Owner |
> |---|---|---|---|---|---|---|
> | 1 | Targeting | Blocker | No consent filter in the query activity | Workflow export, query step | Add marketing opt-in filter | Campaign engineer |
> | 2 | Content | High | `<%= recipient.firstName %>` has no fallback; renders blank in SI proof | SI proof screenshot | Add fallback "Dear customer" | Campaign engineer |
> | 3 | Content | High | EN locale missing — brief lists 3 locales, workflow has 2 deliveries | Brief vs workflow | Add EN delivery or confirm de-scope | Campaign manager |
> | 4 | Delivery | Medium | Subject 74 chars, truncates on mobile | Delivery properties | Shorten to ≤50 | Campaign engineer |
>
> **Not verified:** dark-mode rendering (no screenshots supplied); seed list (not attached).
> **Automation:** add a pre-send workflow alert when the consent filter is absent.

---

## 2. Raw stats → client-ready report + emails
**Skill:** `campaign-performance-report` · **Manual:** ~2 h · **With skill:** ~20 min

**You type**
```
Here are the ACC delivery stats for W43_20261021_MKTA_EM_pl_onb. Build the report
and two email drafts for the market team.
[paste delivery, reception, domain and segment tables]
```

**You get**
- A formatted **DOCX**: delivery summary, KPI boxes, domain and segment tables, 5–9 observations
- **Two email drafts**: *Formal report share* and *Short & punchy*
- Observations such as: *"Engaged segment open rate 2.4× non-engaged; Gmail 89% of volume; 0 complaints; 0 transactions — confirm purchase tracking was expected."*
- Any metric not in your paste is reported as missing, never estimated

---

## 3. Messy thread → owners and blockers
**Skill:** `chat-thread-analyzer` · **Manual:** ~45 min · **With skill:** ~10 min

**You type**
```
[paste 40-message Teams thread about a delayed voucher send]
Who owes what and what's blocking the send?
```

**You get**
> **Summary:** Send blocked since 14:10 — voucher file on SFTP is encrypted; requester re-upload pending.
>
> | Time | Who | What |
> |---|---|---|
> | 13:02 | Requester | Uploads voucher file |
> | 13:40 | Engineer | Import fails: file unreadable |
> | 14:10 | Engineer | Asks for unencrypted CSV — **no reply for 2h 05m** |
>
> **Open actions:** Requester → re-upload as plain CSV (inferred deadline: before 18:00 send) · Engineer → re-run import and confirm row count
> **Draft reply:** ready to paste — not sent.

---

## 4. Incident → evidence-backed postmortem
**Skill:** `crm-evidence-report-pro` · **Manual:** ~6 h · **With skill:** ~2 h

Every finding carries **Status** (FACT / HYPOTHESIS / ASSUMPTION / UNKNOWN), **Access** (read-directly / summary-only / system-data / reasoning) and a **Source**. Root cause needs two independent sources. The report opens with a coverage line stating what was *not* searched, so "no approval found" can't be mistaken for "no approval exists".

---

## 5. "We're overloaded" → a case leadership can approve
**Skill:** `workload-assessment-builder` · **Manual:** ~3 days · **With skill:** ~4 h

Upload a Jira export and get a 10-sheet Excel model: demand profile, urgency analysis, capacity overload %, systemic root causes (Briefing-Iteration Spiral, Urgency Normalisation Trap, Capacity Compression Cycle), risks and a one-page leadership brief with explicit asks.
