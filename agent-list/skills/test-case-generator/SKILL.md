---
name: test-case-generator
description: Generate QA-reviewable UI end-to-end, API, security/privacy, negative/boundary and regression test cases from a BRD, acceptance criteria, technical specification and project context. Use for test design only, not test execution.
---

# Test Case Generator

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Produce a reviewable test-case set and coverage map, not execution results. Read [the context contract](references/context-contract.md) and use [the test-case template](assets/test-cases-template.md).

## Sources and scope
Read the selected BRD and acceptance criteria, technical specification, enterprise Security/PII baseline, application context, prototype notes, and available implementation handoff/untested-risk list. Inspect code read-only if supplied and relevant; cite source revision/path/symbol and distinguish observed behavior from intended requirements. Confirm the feature/story scope and exact source revisions. Do not silently redesign requirements to make them testable.

Record evidence categories: confirmed requirement, existing implementation evidence, proposed test assumption, open question and conflict. Missing or inaccessible policy is not an excuse to invent a mandatory rule. When specification, code and BRD disagree, identify the conflict and mark affected expected outcomes pending QA/business review.

## Design coverage
Generate cases for applicable risks, not an arbitrary fixed count. Include:
- **UI E2E:** complete scoped user journeys, navigation, forms, transitions, loading/empty/error states, cancellation/Back/reset and role-dependent views. Distinguish prototype simulation from real system behavior.
- **API:** request/response contracts, required/optional fields, status/errors, schema validation and authorization; idempotency, pagination, concurrency or rate behavior only when applicable and specified. Guessed endpoints are proposed/unconfirmed, not existing.
- **Security, authorization and PII:** relevant role/resource access boundaries, negative authorization, input handling and source-backed privacy controls such as masking/logging/retention where defined. Use dedicated test accounts and synthetic records. Document missing policy decisions. Do not equate these cases with a penetration test or compliance certification.
- **Edge/negative:** invalid/missing/out-of-range data, boundary values, duplicate/repeated actions, dependency failures and recovery where relevant. Unknown numeric limits become questions or symbolic test parameters, not invented business thresholds.
- **Regression:** existing behavior at risk from the change, shared components, interfaces and brownfield compatibility/migration constraints. Use code/implementation evidence to identify risk without treating current behavior as approved future intent.

## Case format and traceability
Assign stable TC IDs; preserve IDs during revisions and mark retired cases instead of reusing IDs. Every case includes title/objective, category, proposed priority and rationale, story/BR/AC/spec IDs, preconditions/environment, test-role requirements, safe synthetic test data, ordered steps, expected result, cleanup/reset requirements, dependencies and assumptions/gaps. Priority remains proposed unless supplied by QA/business. If no relevant BR/AC exists, label the case a proposed risk-based case and give its evidence and approval question rather than fabricating an ID.

Expected results must be specific and observable. Map key steps to expected outcomes when that improves reproducibility. Separate success, negative and role variants when they have materially different prerequisites or outcomes. Define API inputs and response assertions without embedding real secrets. Security cases must state a controlled nonproduction setup and safe boundaries; do not propose unauthorized probing of production or third-party systems.

Produce a coverage matrix from each in-scope requirement/AC to its test cases and categories. Report uncovered requirements, untestable criteria, missing expected values, source conflicts and coverage assumptions. Do not call a set exhaustive merely because every requirement has one linked case.

## Review and deliver
Deliver `TEST-CASES.md` with its coverage/gap section. Check uniqueness of IDs, valid traceability references, reproducible preconditions, synthetic data, observable expected results, risk-based priority and consistency with the latest reviewed artifacts. A QA reviewer must be able to approve, revise or reject cases and assumptions.

**Generate cases only. Do not execute them.** Do not launch browsers to run scenarios, call application APIs for testing, run test scripts, create records/accounts, mutate data or Jira, scan systems, publish results, or mark cases Passed/Failed as part of this skill. Read-only source inspection is allowed. Keep `Execution status: not executed` for generated cases, and separate design validation from test execution. If a later execution skill is used, it must establish its own environment, authorization and safe-data scope.
