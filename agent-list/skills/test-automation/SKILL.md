---
name: test-automation
description: Turn QA-reviewed test cases into automation and execute feasible cases in an authorized test environment, defaulting to Playwright for UI/API with case-level evidence. Use for test execution and reporting; security scanning requires separate explicit scope authorization.
---

# Test Automation

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Read [the context contract](references/context-contract.md) and use [the execution report template](assets/test-execution-report-template.md). Inputs are the QA-reviewed cases, their review revision, BRD/AC, technical specification, application/enterprise context, implementation revision and a specified test environment. Keep case IDs stable from design through script and report.

## Confirm readiness and safe scope
Verify which cases QA reviewed and which revisions of requirements, code and test data they target. Unreviewed or conflicting cases remain blocked pending review; do not silently rewrite expected results to make tests pass. Inspect repository test instructions, existing test harness, scripts and working-tree changes before editing or running anything.

Identify and verify the authorized nonproduction base URL/environment, exact allowed applications/accounts/resources, permitted test actions, dedicated test roles, synthetic fixtures, reset/cleanup method and execution limits. Do not assume a reachable URL is authorized. If test environment, access, data ownership or mutation scope is unclear, ask for the missing authorization before execution. Read-only inspection and drafting scripts can continue independently. Never target production or third-party systems by default.

Use dedicated test accounts and synthetic data; do not request plaintext secrets in chat or embed credentials/PII in scripts, screenshots, traces, logs or reports. Use approved local secret/configuration mechanisms. Disable or stub external email/SMS/payment/other real-world side effects unless explicitly authorized for this exact test scope. Isolate generated records with a run ID. Cleanup is limited to records this run created and authorized cleanup actions; never bulk-delete shared data or unrelated artifacts.

## Build automation
Default to Playwright for browser UI and API checks, using the repository's established language/configuration when suitable. Reuse a working existing harness rather than replacing it gratuitously. If Playwright is unavailable, report setup requirements or use another already approved appropriate harness; do not invent a run or silently install unexpected software.

Create maintainable scripts grouped by journey/API/resource, mapping test names/metadata directly to reviewed TC IDs and source AC IDs. Use role-aware fixtures, deterministic synthetic data, robust selectors, condition-based waits and explicit assertions. Include setup/teardown boundaries and capture enough safe evidence to reproduce failures. Avoid arbitrary sleeps and tests that pass by ignoring assertions or swallowing errors.

Classify each reviewed case as automatable now, blocked by prerequisites or requiring manual judgment. A partial automation of a case is not full case coverage: identify covered steps/assertions and what remains manual. Do not claim automation of subjective UX/accessibility or external systems without a real method and evidence.

## Execute and capture evidence
Run only the cases within the verified execution scope. Use bounded timeouts/retries and control concurrency to avoid load beyond the authorized environment. Capture command, environment label, source/code/test revisions, timestamp, run ID, duration and exit status. Record safe assertion output, sanitized screenshots/traces or request/response summaries as appropriate; evidence may contain secrets or personal data, so inspect/redact before sharing.

For each case report one of:
- `pass`: the reviewed expected assertions for this case actually ran and passed on this run; link evidence.
- `fail`: an executed assertion/behavior failed; capture expected versus actual and evidence. Do not automatically attribute every failure to product code.
- `blocked`: execution did not start or could not complete because of environment, access, data, unresolved requirements or other prerequisites; name the reason. Keep queued/not-attempted cases visible rather than counting them as pass.
- `manual`: the case needs human execution/judgment; describe remaining steps and why. This is not a pass.

Identify mixed/manual remainder explicitly. If retries disagree, record every relevant attempt and mark the case flaky/unresolved instead of presenting an uncomplicated pass. A suite-level green exit is not proof that skipped or undiscovered cases passed. Reconcile the reviewed case inventory with discovered tests and report missing/skipped/blocked/manual coverage.

## Optional ZAP boundary
ZAP is optional, not part of default execution. **Do not run or start ZAP scanning unless the user explicitly authorizes its concrete target scope and scan behavior.** Confirm target ownership/authorization, exact URLs/hosts/path boundaries, passive versus active mode, accounts, allowed checks, rate/time limits, exclusions and potential state-changing effects. Do not treat QA case approval or permission for Playwright tests as permission for ZAP. If scope is missing or a target redirects outside it, stop that part and report. Keep scanner findings separate from confirmed vulnerabilities; avoid production targets and destructive/flooding activity.

## Finish
Deliver automation scripts/configuration plus `TEST-EXECUTION-REPORT.md` and safe evidence artifacts. Report case counts by pass/fail/blocked/manual, any flaky or partial cases, planned versus actual coverage, defects versus suspected environment issues, cleanup outcomes and next actions. Preserve unrelated files and user changes. Do not push, open a PR, deploy, alter Jira or publish reports externally without separate authorization. Do not claim complete acceptance, full security coverage or compliance from this run.
