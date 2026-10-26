# Contributing

Thanks for improving the skills. Keep every change safe to publish.

## Before you open a pull request
- [ ] No real customer data, recipient lists, voucher codes or exports
- [ ] No colleague, client or vendor-contact names — use roles ("market approver", "platform owner")
- [ ] No internal paths, hostnames, ticket keys, list IDs or portal names
- [ ] No company-confidential benchmarks — mark ranges as placeholders
- [ ] Frontmatter is valid YAML (`name` matches the folder; long `description` uses `|`)
- [ ] Trigger changes keep skills disjoint: update the `DO NOT fire when` and `PRECEDENCE` lines

## What makes a good addition
- **Known issue**: Symptoms → Root cause → Fix → Prevention
- **New play**: input it needs, steps, output shape, what it must never invent
- **Benchmark**: clearly labelled as an example, with the metric definition

## Evidence rule
Any new skill must keep the core contract: never invent IDs, dates, counts, owners, filenames or approvals; label findings FACT / HYPOTHESIS / ASSUMPTION / UNKNOWN.
