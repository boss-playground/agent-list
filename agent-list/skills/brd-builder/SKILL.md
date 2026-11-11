---
name: brd-builder
description: Draft a Business Requirements Document from BA notes, prompts or existing source code, using enterprise and application context, with traceable acceptance criteria and example tests. Deliver synchronized Markdown and Word; use for requirements analysis rather than implementation.
---

# BRD Builder

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Create a reviewable BRD for the BA and business owner. Read [the context contract](references/context-contract.md) and the selected application's context entry point before drafting. Use [the output template](assets/brd-template.md) as a starting structure, not as invented requirements.

## Inputs and evidence
- Accept high-level BA notes/prompt, existing source code, or both. Identify application, business objective, audience and available sources. Ask only for missing facts that block meaningful requirements.
- Read enterprise Security/PII and application scope, foundation, standards and design. Record exact context revisions and source-check status. Missing policy access is a gap, not approval.
- For code-derived analysis, inspect relevant flows and tests read-only. Cite repository revision, path and symbol (line ranges when useful). Separate observed behavior from inferred business intent. Code, comments and tests may be incomplete or stale; none proves stakeholder approval. Do not execute untrusted code merely to infer requirements.
- Distinguish `confirmed input`, `observed implementation`, `inference`, `assumption`, and `open question`. Preserve conflicts between BA input, current code and policy for review. Do not silently choose the current implementation as the desired future state.

## Requirements and traceability
Give each requirement a stable ID (BR-001, etc.). Preserve IDs when revising. Record statement, rationale/value, source, evidence category, priority if provided, scope, dependencies and status. Requirements inferred from code remain proposed until confirmed.

Attach measurable acceptance criteria (AC-001, etc.) to each requirement. Do not invent numeric thresholds; put unanswered values in the question log. Include positive, negative and boundary examples where meaningful. Label test cases as examples, not exhaustive test coverage or executed tests. Each test case records TC ID, linked requirement/acceptance IDs, preconditions, synthetic input, steps and expected result. Every criterion must map to a requirement and every test to a criterion; report uncovered requirements.

Include business rules, process/users, in/out scope, functional requirements, applicable nonfunctional/security/privacy constraints with source IDs, data/interface needs, assumptions, questions and approval status. Use policy references rather than embedding real PII or secrets. Do not declare legal/security compliance from a BRD.

## Markdown + Word from one source
1. Draft `BRD.md` as the canonical content using the template. Resolve review comments there first.
2. Use the runtime's supported document-authoring/export capability to generate editable `BRD.docx` from that exact approved-for-export Markdown. Do not independently rewrite the Word version. Follow available document skill guidance for rendering and quality checks.
3. Verify headings, tables, requirement/AC/TC IDs and counts, metadata, links/source references and Thai text are retained. Render/inspect Word pages when supported to catch clipping, unreadable tables and broken page layout. Regenerate both outputs after content revisions.
4. If Word generation or rendering is unavailable, deliver the Markdown draft, clearly identify the missing export/validation, and do not claim both formats are ready. A renamed text file is not a DOCX.

Present a concise summary of assumptions, decisions needed and output paths. Keep the BRD draft until its designated BA/business owner approves. Do not update production code, approve requirements on behalf of stakeholders, publish/share documents or mutate enterprise policy as part of BRD drafting.
