---
name: crm-ops-troubleshooter
description: |
  Troubleshoot and resolve CRM operations issues in Adobe Campaign Classic v8, email builders, SFTP workflows, voucher processes and data pipelines. Use whenever the user mentions Adobe Campaign errors, proof failures, regex issues, SFTP upload problems, voucher extraction, template rendering issues, MSO conditional image problems, pipe symbol errors, delivery or workflow failures, typology rule issues, soft-deleted records, data-warehouse connectivity, push frequency caps, or GDPR/PII classification of campaign data. Also trigger for Adobe Campaign error codes (XSV-350122, XML-110018, etc.). DO NOT fire for pure Stensul provisioning or migration questions (use stensul-troubleshooter) or for pre-launch QA reviews (use acc-v8-campaign-qa).
---

# CRM Operations Troubleshooter

PRECEDENCE: runtime errors and broken data flows route here; structured pre-launch review routes to `acc-v8-campaign-qa`; Stensul-only issues route to `stensul-troubleshooter`.

## Purpose
Diagnose and resolve technical issues across a multi-market CRM stack: Adobe Campaign v8, email builders, SFTP, voucher workflows, data pipelines and compliance questions.

## Market Context (edit for your organisation)
```
Markets in scope:      <Market A, Market B, ...>
Data pipeline:         <source> → <warehouse> → Adobe Campaign → <downstream>
SFTP root per market:  <path pattern — no real paths in shared copies>
Approval portal(s):    <data-extraction approval route>
Push frequency policy: <cap, uncap rule, policy owner role>
Ticketing:             <Jira project keys>
```

## Known Issues & Solutions

### 1. Regex Catastrophic Backtracking in Link/CID Generation
**Symptoms**: Proof generation hangs; Adobe Campaign times out on proof send
**Root cause**: Nested quantifiers in a custom link-processing function cause exponential backtracking on some HTML structures
**Fix**: Replace with a non-nested pattern such as `/<a[^>]*>/g`; test against the slowest template before release

### 2. Proof Label Prefix Too Long
**Symptoms**: Proof fails with a label-length error
**Root cause**: Delivery label limit; proofs prepend "Proof - "
**Fix / prevention**: Keep delivery labels under 100 characters

### 3. Pipe Symbol Rendering
**Fix**: Replace `|` with `&#124;`; use HTML entities for special characters

### 4. MSO Conditional Image (Outlook)
**Workaround**: Host the MSO fallback image separately and reference its CDN URL directly in the conditional block; record both URLs in handoff notes

### 5. Encrypted Voucher File on SFTP
**Symptoms**: Uploaded voucher file cannot be read by Adobe Campaign
**Root cause**: File is password-protected; the import expects plain CSV
**Fix**: Requester re-uploads as unencrypted CSV to the agreed path; confirm row count after import

### 6. Typology Rule Excludes Recipients Unexpectedly
**Investigation**: Check NmsTypologyRule and exclusion logs; compare target count before and after typology
**Fix**: Review rule configuration with the platform owner; consider market-specific rules

### 7. Soft-Deleted Records in Target Lists
**Investigation**: Query the `@status` field on the recipient table
**Fix**: Re-extract the target excluding soft-deleted records

### 8. BI vs Adobe Campaign Count Discrepancies
**Root cause**: Differences in opt-in filtering, channel flags, deduplication and engagement windows
**Resolution**: Document the delta field by field; agree one definition with the BI team

### 9. Data-Warehouse Downtime
**Symptoms**: Warehouse maintenance drops connections to Adobe Campaign and downstream platforms
**Impact**: Campaign server reachable, data-dependent workflows fail
**Mitigation**: Schedule data-dependent workflows outside the window; notify market teams in advance

### 10. Data-Extraction Approval Gate
**Context**: Some extractions need an approval ticket before the platform team can process them
**Rule**: Never start an extraction without the approval reference recorded in the ticket

### 11. Adobe Campaign Error XSV-350122 / XML-110018
**Symptoms**: Delivery preparation or analysis fails
**Investigation**: Workflow logs for source query errors, broken joins or empty target mappings
**Common cause**: Downstream schema change or a dropped enrichment table
**Fix**: Validate the source query, re-map enrichment if the table was rebuilt, re-run analysis

### 12. Push Notification Frequency Cap
**Policy pattern**: Weekly per-user cap; uncap only for pre-approved campaigns
**Impact assessment needed when**: Overlapping campaigns target the same audience in the same week
**Resolution**: Request uncap through the policy owner; agree send sequencing with the affected markets

### 13. Product Model Code Decoding
Some product catalogues encode model year as a letter at a fixed position in the model code. Confirm the mapping with the data owner before filtering; prefer a registration-date field when one exists.

## GDPR & PII Quick Reference
**PII — do not email**: recipient emails, name + email combinations, account IDs linked to personal data, device IDs tied to individuals, purchase history with identifiers.
**Not PII — safe to share**: unassigned voucher codes, aggregated statistics, configuration details (segment/workflow names), template HTML.
**Routing**: voucher-code lookups → operations check; personal-data queries → formal GDPR channel.

## Troubleshooting Methodology
1. **Symptom** — exact error message, expected vs actual
2. **Known issues** — check the list above
3. **Isolate the layer** — template, data, configuration or infrastructure
4. **Timing** — maintenance window, deployment, migration window
5. **Owner** — CRM team, platform team, provisioning owner, requester
6. **Document** in the ticket
7. **Communicate** — draft the stakeholder update (draft only)

## Rules
- Never invent error codes, counts, paths or owners. Missing = ask.
- Recommend automation (alerts, pre-send checks) whenever a failure could recur.
