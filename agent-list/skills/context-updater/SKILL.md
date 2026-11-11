---
name: context-updater
description: Review and update existing engineering context at a Developer Lead's request, comparing foundation, design or standards changes and checking authorized enterprise Security and PII sources for changes. Use for context maintenance, not automatic policy certification or code implementation.
---

# Context Updater

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Read [the context contract](references/context-contract.md). Resolve the project root and requested scope; select the application for application-scoped changes, not for enterprise-only updates. Preserve unrelated user edits and approved history.

## Modes
- **Application change:** accept the Dev Lead's proposed foundation, design, scope or engineering-standard changes, then compare against the current app and enterprise baseline.
- **Enterprise source check:** check the recorded authorized Security/PII sources and compare with the last reviewed source revisions. This is a one-time check unless recurring work is separately requested and supported.
- Combine modes when requested; do not turn a single-app edit into an enterprise-wide rewrite.

## Review
1. Read the selected enterprise baseline, source register and available Git diff/status; also read current app context for application-scoped changes. Identify the baseline under review before making proposals.
2. Retrieve relevant source content through available authorized access. Compare requirements, applicability and effective dates, not only website timestamps. Capture changed source revision/section. If no prior comparable evidence exists, report `baseline missing`, not `unchanged`.
3. Classify each source as `changed`, `unchanged (checked)`, `inaccessible`, `not checked`, or `baseline missing`. A partial retrieval means only retrieved coverage was checked. Record latest attempt separately from last successful check.
4. Prepare a change report: old/new requirement or decision, source evidence, impact, affected files/apps (known list only), conflicts, compatibility/migration implications, proposed edits, unresolved questions and reviewer. A single-app request may require notifying the user of enterprise impact, not modifying other apps.
5. Produce a proposed patch or separately named draft. Distinguish Dev Lead-requested choices from source-mandated changes. Show the diff and request the applicable owner review before replacing approved context. Enterprise baseline changes need the designated enterprise owner, not merely an app owner's assumed authority.
6. On authorized application, update affected documents, their Latest Update, source-check records and baseline reference only when the corresponding review occurred. Do not bump untouched files. Preserve prior approved content in recoverable history; do not commit or push unless requested.

## Completion
Report applied versus proposed files, verified source checks versus blocked checks, baseline revision, unresolved conflicts and next owner action. Do not claim `up to date`, `compliant`, or `no changes` when relevant sources were unavailable. Downstream implementation changes are a separate task.
