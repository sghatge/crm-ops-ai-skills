---
name: crm-explainer-video
description: 'Build a short stakeholder video (HyperFrames, MP4) that explains a CRM or campaign topic: a process walkthrough, a campaign status or postmortem recap, an AI operating model pitch, a platform migration update (Stensul, Adobe Campaign, Infobip) or a handover overview. Use whenever the user wants an internal explainer, walkthrough or recap video about campaign operations, even if they only say "make a video for the team" or "turn this report into a video".'
---

# CRM / campaign explainer video

Goal: leadership or a regional team understands the point in under two minutes without reading the source document. Rendering and composition rules belong to the official HyperFrames skills; this skill decides the story and keeps the facts honest.

Start from `/hyperframes` (router), then use `/faceless-explainer` as the creation workflow. Use `/hyperframes-core` before writing HTML and `/hyperframes-cli` for lint, check and render. If the HyperFrames skills are not installed, run `npx hyperframes skills update`.

## Story structure (one idea per scene, 5-8 seconds)

1. Outcome in one sentence (the answer first, as an executive summary).
2. What happened, or what is proposed.
3. Root cause or mechanism, before any recommendation.
4. Recommendation, framed in terms of stability, scalability and governance.
5. Risks and dependencies, stated plainly.
6. Next steps with owner and date.

A table-style scene (market by status, before/after) is often clearer than prose. Keep text on screen to a short headline plus at most three supporting lines.

## Evidence discipline

Every number, campaign ID, date, count, owner and approver on screen must come from material the user supplied. If something is missing, show a visible placeholder (for example "[count TBC]") and list it in the hand-off. Never invent identifiers or figures. When the source is ambiguous or conflicting, say so in the hand-off instead of choosing one silently.

## Visual defaults

Calm dark or light business palette, one accent colour for the key number, diagrams and flow boxes instead of system screenshots, a small "Internal draft" tag in a corner. Leave out customer personal data. Put all figures in one data object at the top of the composition so corrections need one edit and a re-render.

## Hand-off

Deliver the MP4 (if Chrome was available to render it) plus the project folder. If rendering was not possible, say so and give the commands to render locally. List placeholders and assumptions, and offer one next step: narration or a 9:16 cut for sharing.
