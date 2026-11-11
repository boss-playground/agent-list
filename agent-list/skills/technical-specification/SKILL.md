---
name: technical-specification
description: Turn a BRD and enterprise/application context into a technical specification and clickable HTML prototype, mapping screens and interactions to business logic, data, APIs, validation, Security/PII and requirement IDs. Use for design handoff, not production implementation.
---

# Technical Specification

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Produce a reviewable technical design and an interactive, simulated prototype. Read [the context contract](references/context-contract.md) and use [the specification template](assets/technical-specification-template.md). Preserve an existing design or source of truth rather than inventing a replacement.

## Inputs and evidence
Read the BRD and its requirement/acceptance IDs, enterprise Security/PII baseline, and the application's scope, foundation, standards and preliminary design. Inspect existing source code only when provided/accessible and relevant. Record file paths/symbols, repository revisions, policy source IDs and review status.

Identify missing BRD details and gaps that block a meaningful flow; ask focused questions or mark assumptions visibly. Distinguish `existing evidence`, `proposed design`, `unconfirmed`, and `conflict` in every mapping. Current code demonstrates implementation, not approved business intent. An inaccessible source is not evidence of compliance. Never invent actual endpoints, schema constraints or policy requirements as facts.

## Design and traceability
1. Enumerate in-scope user journeys and actor/permission boundaries from the BRD. Give screens stable SC IDs and interactions IN IDs. Preserve existing BR/AC identifiers; flag missing requirements rather than generating fictitious traceability.
2. For each screen, describe purpose, actor, entry/exit paths, visible fields, data display, state transitions and related BR/AC IDs. Cover relevant loading, empty, success, validation/error, unauthorized and cancellation states, not just a happy-path picture.
3. For each interaction, map the trigger to preconditions, business logic, frontend/server responsibility, data reads/writes, API contract, validation, permission/security/PII constraints, failure behavior and BR/AC IDs. Mark absent backend behavior as proposed. Include retry/idempotency and transaction boundaries when the operation warrants them.
4. Define data structures and API contracts at the needed detail: types, mandatory/optional fields, constraints, errors, ownership, relationships and classification. Distinguish server enforcement from prototype-only validation. Reference enterprise requirement IDs rather than inventing retention, masking or authorization policies.
5. Surface contradictions among BRD, source code and enterprise/application context. Keep unresolved decisions with their owner and affected IDs. Do not silently weaken enterprise standards or treat a Dev Lead proposal as enterprise approval.

## Clickable HTML prototype
Create `prototype/index.html` plus local CSS/JavaScript/assets only as needed. Use synthetic fixtures and deterministic in-memory behavior; no real credentials, PII, external API calls, analytics or production writes. Label the interface prominently “Prototype — simulated data and behavior”. Do not load third-party resources by default.

Make the agreed journey actually clickable: navigation, forms, validation feedback, buttons, dialogs, success/error simulations, cancellation and Back/reset behavior. Link screen and interaction IDs to the specification, with a prototype legend or map when useful. A mock save may update in-memory fixtures, but must not claim that a production record was saved. Do not add backend deployment, authentication integration or paid services to make a prototype appear real.

Keep keyboard focus, labels, readable contrast and usable mobile layout. If a control or state is intentionally out of scope, label it rather than leaving a misleading dead end. Document how to open the prototype and its limitations. Prefer a self-contained local prototype; if tooling needs a server, provide its run command and dependencies without silently installing or publishing anything.

## Prototype feedback and synchronized revisions
When the user reviews the prototype, collect each feedback item with a stable FB ID, source/date, affected SC/IN/BR/AC IDs and its intended outcome. Evaluate whether it changes presentation only, behavior, scope, business rules, data/API contracts, acceptance criteria or policy assumptions. Do not silently turn ambiguous feedback into a requirement. Confirm material ambiguity, contradictions with approved requirements, or policy conflicts with the appropriate owner before applying them.

**Mandatory human approval gate for every feedback change:** Before updating any BRD Markdown, BRD Word, prototype or technical specification, present the feedback change proposal and its material effects for explicit human approval. This applies even to clear feedback, minor visual changes and previously discussed ideas. A review comment or request for a change proposal is not approval to apply it. Keep proposed edits separate and leave the existing artifacts unchanged until the user approves the concrete proposal or clearly identified batch. If the proposal materially changes after approval, obtain approval again.

After that approval, apply the coherent revision across the prototype, technical specification and canonical `BRD.md`. Preserve requirement IDs and record added/changed/retired items without reusing IDs. If the feedback would change approved requirements beyond the request's authority, propose the BRD diff for BA/business-owner review rather than replacing the approved version. Do not modify enterprise policies to make a requested UI change fit.

After BRD Markdown changes, regenerate its Word counterpart from that same content using the supported document export workflow. Update traceability, acceptance criteria and example test cases impacted by the feedback. Keep a change history linking each FB item to the before/after decision, affected artifact revisions, reviewer/approval state and validation results. Record the current revision across the artifact set so reviewers can identify matching versions.

Recheck the changed flow and its relevant neighboring behavior, not only the edited screen. Deliver the synchronized set together. If Word export or another step fails, preserve the previous approved artifacts, deliver clearly labeled drafts where useful and explicitly list which files are stale or pending. Never claim the BRD, Word file, prototype and specification are synchronized when one was not regenerated or verified. Do not erase rejected feedback; record its disposition and reason.

## Deliver and verify
Deliver `TECHNICAL-SPEC.md`, clickable prototype files, and a short validation record. Use the template as an outline, adapting to the project's actual scope.

- Check every screen/interaction maps to existing BR/AC IDs or an explicit proposed/out-of-scope item; check that requirement mappings cover the scoped journeys. Keep the spec and prototype consistent after changes.
- Test navigation and relevant form behavior, errors, dialogs, repeated actions, Cancel, Back and reset; verify no unintended network calls or real data persistence.
- Open and inspect the prototype when browser tooling is available. Record flows/states checked and meaningful failures. If only static inspection is possible, say browser interaction was not tested; never claim clickability was verified by reading source alone.
- Check source and policy references, evidence categories, assumptions and conflicts. Describe all blocked verification and implementation gaps.

Keep outputs draft until reviewed by the designated owners. The prototype is a design artifact, not a production application, completed API integration, security test or compliance certification. Do not publish, deploy, change production code, or share outside the authorized audience without corresponding permission.
