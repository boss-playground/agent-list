---
name: context-builder
description: Create an application's shared engineering context with its Developer Lead, including scope, foundation, technical design, greenfield or brownfield constraints and references to enterprise Security and PII standards. Use when initializing context, not for implementation or certification.
---

# Context Builder

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Produce reviewable Markdown context usable by both Codex and Claude. Read [the context contract](references/context-contract.md) first. Ask for the workspace/context root if it cannot be identified. Preserve existing files and follow repository instructions.

## Intake
Collect only missing decisions from the Dev Lead, grouping related questions:
- Application name/ID, purpose, owner, stakeholders, in-scope/out-of-scope work, success criteria.
- Greenfield or brownfield. For brownfield: current system/repository, interfaces, dependencies, compatibility obligations, migration/coexistence and rollback constraints. For greenfield: constraints and architectural choices still open.
- Preliminary architecture, components, data stores, interfaces, integrations and deployment environments.
- Foundation: stack and versions, repository/build/test conventions, runtime/deployment and operational requirements.
- Application-specific engineering standards and nonfunctional requirements, including unresolved decisions.
- Authorized internal Security and PII source URLs/files and their policy owners. Ask for sources, not credentials or real personal records.

Missing nonblocking detail may be marked `TBD` with owner and next action. Never fill a consequential missing decision as fact.

## Build
1. Inspect any existing enterprise baseline and application context before writing. Reuse the shared enterprise baseline. Do not modify it as a side effect of creating an app.
2. Read accessible authorized sources and record provenance. If enterprise context does not yet exist, propose draft Security, PII and source-register files from the available evidence. Mark inaccessible sources and missing policy content explicitly.
3. Create application files `context.md`, `scope.md`, `foundation.md`, `standards.md`, and `design.md` under `context/applications/<app-id>/`. The packaged `_template` demonstrates the sections; if not present, generate equivalent sections using this contract. Keep scope and design distinct from enterprise policy.
4. `context.md` is the entry point: metadata, app ID/type, relative links to app documents and enterprise baseline, reviewed baseline revision, assumptions, unresolved issues and reviewer status.
5. Check conflicting requirements, all relative links, metadata, and brownfield constraints. Show a concise file list and decisions needed for approval. State what source checks actually succeeded.

Create drafts when requested; do not certify compliance, implement the app, publish files, commit/push, or replace an approved baseline without corresponding authorization. Leave already approved content unchanged if only a draft is requested.
