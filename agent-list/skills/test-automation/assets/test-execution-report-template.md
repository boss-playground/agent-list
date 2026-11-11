# [Application / Feature] — Test Execution Report

Latest Update: [ISO 8601 with timezone]
Owner: [QA / execution owner]
Status: [complete within scope / partial / blocked]
Run ID: [identifier]
QA-reviewed case revision / reviewer: [reference]
Requirement / spec / context revisions: [references]
Implementation / automation revisions: [references]
Environment: [authorized nonproduction environment label; no secrets]
Authorized target/action scope: [scope]
Run timestamp / commands / exit status: [actual evidence]

## 1. Readiness and coverage
Reviewed cases: [count]
Discovered automated cases: [count]
Pass / fail / blocked / manual: [counts that reconcile to case inventory]
Flaky / partial cases: [IDs, may overlap counts]
Skipped / not attempted: [IDs and reasons; not passes]
Scope exclusions: [items]

## 2. Case-level results
| TC / AC IDs | Script/test name | Result | Assertions or steps covered | Expected vs actual / blocker | Safe evidence | Manual remainder / next action |
|---|---|---|---|---|---|---|
| [TC / AC] | [path/test] | [pass/fail/blocked/manual] | [coverage] | [finding] | [artifact / log reference] | [remaining work] |

## 3. Attempts, flaky behavior and triage
| Case | Attempts / results | Likely cause / uncertainty | Investigation evidence | Next owner |
|---|---|---|---|---|
| [TC] | [outcomes] | [product / environment / unknown] | [evidence] | [owner] |

## 4. Safe data and cleanup
Synthetic fixtures / run-owned records: [description]
External side effects: [disabled / authorized scope]
Cleanup attempted / outcome: [exact actions and results]
Residual test data / required follow-up: [items]
Evidence redaction checked: [actual result / blocked sharing]

## 5. Optional ZAP
Executed: no [unless explicitly authorized and actually run]
Explicit approved scope / mode / limits: [none / details]
Results and limitations: [unvalidated findings separate from confirmed issues]

## 6. Gaps and next actions
[Uncovered cases/assertions, manual checks, blocked setup, unresolved failures and owners]

Production deployment / code push / PR / Jira changes: not performed
Full security or compliance certification: not performed
