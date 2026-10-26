---
name: stensul-troubleshooter
description: |
  Troubleshoot Stensul email platform issues and coordinate a migration from a legacy email builder (e.g. Taxi for Email) to Stensul. Use whenever the user mentions Stensul template builds, preview, brand kit, modules, brand lock, approvals or send-tests; Stensul access or provisioning blockers; the MSO conditional image workaround; seedlist QA for Stensul-authored templates; HTML archiving of non-migrated legacy templates; UAT workbook questions; Stensul-to-Adobe Campaign export handoff; or stakeholder updates about the migration. DO NOT fire for Adobe Campaign workflow or delivery errors with no Stensul involvement (use crm-ops-troubleshooter).
---

# Stensul Troubleshooter & Migration Coordinator

PRECEDENCE: Stensul-specific issues route here first; Adobe Campaign-side failures route to `crm-ops-troubleshooter`.

## Purpose
One skill for Stensul platform operations: access and provisioning, template build issues, migration from a legacy email builder, seedlist QA, UAT and stakeholder communication.

## Market Context (edit for your organisation)
```
Markets in scope:        <Market A, Market B, ...>
Stensul go-live date:    <YYYY-MM-DD>
Legacy tool + sunset:    <tool name> — <YYYY-MM-DD>
Users being provisioned: <count>
Provisioning owner:      <role / team>
Partner/vendor access:   <portal or route>
Template build owners:   <role per market>
```
Never fill these from guesswork. If a value is missing, ask for it or mark it `TBC`.

## When This Skill Triggers
- Stensul template build, preview, module or brand-kit issues
- Stensul access/provisioning requests or blockers
- Legacy-tool-to-Stensul migration coordination
- MSO conditional image upload problem
- Seedlist QA for Stensul-authored templates
- HTML archive requests for non-migrated legacy templates
- UAT workbook questions
- Stensul-to-Adobe Campaign export handoff
- Stakeholder comms about the migration

## Provisioning Flow
1. Confirm the user is on the approved provisioning list for this rollout.
2. Check whether an access retrigger request has gone to the provisioning owner, with date.
3. If the user is external/vendor, confirm the partner-onboarding step is complete.
4. Document any delay with dated email evidence before escalating.

**Access chaser template**: "Hi {provisioning owner}, following up on Stensul access for {user list}. Retrigger request sent on {date}. Flagging because go-live is {date}. Can you confirm current status?"

## Known Issues & Solutions

### 1. MSO Conditional Image Upload Workaround
**Symptoms**: Outlook desktop does not render the MSO fallback image
**Root cause**: The default upload flow stores the primary image but may not produce a separately hosted MSO variant that MSO conditional comments can reference
**Workaround**: Upload the MSO fallback image separately via the asset library; reference the CDN URL directly in the MSO conditional block rather than relying on the visual editor
**Documentation**: Capture both primary and MSO image URLs in the template handoff notes

### 2. Template Not Appearing After Build
- Confirm the template is saved (not just autosaved)
- Confirm the brand/market tag matches the user's access scope
- Check approval state — some templates need brand-lock release before they are visible for export

### 3. Brand Kit / Module Missing
**Likely cause**: User's brand or market not assigned correctly during provisioning
**Fix**: Raise to the provisioning owner for access review

### 4. Export to Adobe Campaign Failed / Misrendered
- Confirm the template passed Stensul's internal preview
- Check dynamic blocks use Adobe Campaign-compatible personalization tokens, not Stensul-internal placeholders
- Re-run export; if a pipe symbol `|` appears in content, replace it with `&#124;` before export

### 5. Seedlist QA Failing on First Production Send
Required before the first production send:
- Render across Outlook (desktop + web), Gmail (web + mobile), Apple Mail, Yahoo
- Check the MSO fallback image (Issue #1)
- Verify the unsubscribe link inherits the market-correct typology
- Verify personalization with both populated and null values
- Validate tracking parameters on every click URL

## Legacy Decommission — Archival Process
For every legacy template **not** being migrated:
1. Export the HTML
2. Name it `{market}_{campaign}_{YYYYMMDD}_legacy-archive.html`
3. Store it with its referenced image assets
4. Log it in the migration tracker (template, original URL, archive location, decision: archive / migrate / retire)
5. Finish all archiving before the sunset date

## UAT Workbook Categories
Access and login · Brand kit and modules · Template creation and saving · Preview and rendering (incl. MSO) · Approval workflow · Export to Adobe Campaign · Seedlist and QA · Permissions and brand-lock · Known workarounds.
When the user cites a UAT question, find the category first, then match the scenario.

## Stakeholder Communication
Write to roles, not personalities: firm and factual with dates and email-trail references for escalations; supportive with clear next-step ownership for day-to-day contacts; collaborative with a concrete ask for market approvers.

### Access retrigger (to provisioning owner)
> Subject: Stensul access retrigger — {user list} — go-live {date}
> Hi {name}, flagging pending Stensul access for {list} ahead of the {date} go-live. Original request sent {date}. Please confirm status or tell me what you need from my side. Thanks, {sender}

### Market progress update
> Subject: Stensul migration — {market} progress update
> Access: {X of Y users provisioned} · Templates migrated: {count} · Archived: {count} · UAT: {summary} · Open items: {list with owners}

### Go-live readiness check
> Subject: Stensul go-live — {market} readiness check
> Users provisioned: {list} · UAT coverage: {summary} · First production template: {name / date}

## Rules
- Never invent user counts, dates, template counts or owners. Missing = `TBC`.
- Drafts only; never send on the user's behalf.

## Post-Go-Live Extensions
Module authoring patterns, brand kit version control, approval workflow tuning, migration KPIs (templates/week, defect rate, time-to-publish).
