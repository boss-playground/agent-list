# Project-relative artifact path contract

Latest Update: 2026-11-08T16:19:25Z
Owner: Dev Lead / artifact owner (to be assigned)
Status: proposed workspace convention

## Resolve the root and select the application first
All paths below are relative to the **verified project root**, not the skill installation directory, the model's current directory or a machine-specific home folder. Identify the root from the user's selected repository/workspace and repository instructions; verify its existing `context/` structure. If more than one root is plausible, ask. For a new workspace, ask the user to identify the intended root before writing. Never create a second project tree merely because an expected directory is absent.

Select an application only for application-scoped work. An enterprise-only Context Updater run needs no `app-id` or `work-id` and must not create application/work-set folders. Context Builder needs an `app-id` but no `work-id` until feature artifacts are requested.

Select `app-id` from the explicit request or a uniquely identified existing application entry. If several apps exist or the request is ambiguous, ask; never use the first folder or `_template` as the real application. For new apps, confirm a stable lowercase-hyphenated ID with the Dev Lead. Reuse that ID across all skills.

Select `work-id` only for each feature, story group or BRD/spec artifact set; ordinary application-context creation/update does not require one. Reuse its existing ID from the request or artifact index; ask when multiple sets match. For a new set propose a stable lowercase-hyphenated ID before writing. `run-id` identifies one execution (UTC timestamp plus disambiguator), and `change-id` one proposed revision. IDs must be path-safe single segments: no slashes, traversal, drive names or absolute paths. Verify resolved destinations remain inside the selected root, including symlinks. Do not derive paths from arbitrary ticket text.

Notation used below (not literal folder names or environment variables):
- `E` = `context/enterprise`
- `C` = `context/applications/<app-id>`
- `A` = `artifacts/applications/<app-id>/<work-id>`

## Canonical locations
| Purpose | Project-root-relative path |
|---|---|
| Shared enterprise baseline | `E/security.md`, `E/pii.md`, `E/sources.md` |
| Application entry and context | `C/context.md`, `C/scope.md`, `C/foundation.md`, `C/standards.md`, `C/design.md` |
| Context update review | `C/changes/<change-id>/CHANGE-REPORT.md`; enterprise-only scope uses `E/changes/<change-id>/CHANGE-REPORT.md` |
| Work-set index | `A/ARTIFACT-INDEX.md` |
| Optional authorized input snapshots | `A/inputs/` (for supplied BA notes/Jira exports/source manifests; do not save secrets or unnecessary internal copies) |
| Requirements | `A/requirements/BRD.md`, `A/requirements/BRD.docx` |
| Detailed technical specification | `A/design/TECHNICAL-SPEC.md` |
| Prototype | `A/design/prototype/index.html` plus local assets beneath that directory |
| Implementation planning | `A/planning/IMPLEMENTATION-PLAN.md`, `A/planning/JIRA-BATCH.md`, `A/planning/JIRA-LEDGER.md` |
| Implementation handoff | `A/implementation/IMPLEMENTATION-SUMMARY.md` |
| QA-reviewed test cases | `A/testing/TEST-CASES.md` |
| New automation harness default | `A/testing/automation/`; preserve an existing repository harness and record its actual relative paths in the index instead |
| One execution report / evidence | `A/testing/runs/<run-id>/TEST-EXECUTION-REPORT.md`, `A/testing/runs/<run-id>/evidence/` |
| Proposed downstream changes | `A/proposals/<change-id>/` with the affected canonical subpaths mirrored inside |

`C/design.md` is the app-wide preliminary design; `A/design/TECHNICAL-SPEC.md` is a feature/work-set specification. They are not interchangeable. Source code belongs in its verified existing repository layout, not in the artifact tree. Record source/test locations relative to the project root in the index; do not invent `src/` or relocate an existing harness.

## Required versus optional inputs by skill
Here, **required** means needed for a complete trusted result; missing items may allow a clearly incomplete draft but never a fabricated/approved final result. `Context` means the chosen `C/context.md` and its relevant linked app files plus `E/security.md`, `E/pii.md`, `E/sources.md`, with status and baseline revision checked.

| Skill | Required input | Optional input | Output contract |
|---|---|---|---|
| Context Builder | Selected root/app, Dev Lead scope, greenfield/brownfield choice, foundation/design/standards decisions; authoritative enterprise sources or an approved baseline for verified policy content | Existing code/design/BA notes; additional nonblocking decisions can be explicit TBDs | Create draft `C` files and source-based `E` proposals only when needed/authorized. Do not overwrite an existing baseline as an app side effect. Link work sets from `C/context.md` when created. |
| Context Updater | Current selected baseline (`E` for enterprise-only; relevant `C`/`E` for app scope) and change request; accessible current source for any claim that policy freshness was checked | Git history, code, application impact inventory | Change report in the context change directory; proposed context files under its `proposed/` subfolder. Canonical `C`/`E` updates only after required approval. |
| BRD Builder | Context and at least one BA note/prompt or source-code input; selected work set | Existing BRD, supporting Jira/source snapshots, prototype feedback | `A/requirements/BRD.md` and matching `BRD.docx`; index records export status and source revision. |
| Technical Specification | Context and selected `A/requirements/BRD.md` with AC and review state | Code, prior spec/prototype, feedback | `A/design/TECHNICAL-SPEC.md`, prototype directory; approved feedback revisions also synchronize requirements Markdown/Word. |
| Implementation Planner | Context and matching selected BRD/spec revisions; scoped deliverables | Prototype, code/backlog, reviewed test cases | Plan and proposed Jira batch in `A/planning/`; ledger created/updated to record approved execution or pending status. Verified Jira destination/fields and batch approval additionally required before external creation. |
| Implementation Builder | Selected stories/tasks (live or authorized export), Context, matching BRD/spec, selected writable repository and AC | Plan/prototype, existing tests, prior handoff | Scoped local code/unit-test changes at existing repository paths; summary at `A/implementation/IMPLEMENTATION-SUMMARY.md`. No push/PR. |
| Test Case Generator | Context, selected BRD/AC and matching spec | Code, prototype, implementation summary/untested-risk handoff | `A/testing/TEST-CASES.md` with coverage/gaps; no execution. |
| Test Automation | QA-reviewed `A/testing/TEST-CASES.md`, relevant Context/BRD/spec, implementation revision and explicit safe execution environment/scope | Existing harness, implementation summary, approved scan scope | Scripts in existing harness or default automation path; unique per-run report/evidence. Without execution authorization, draft scripts only and report blocked execution. |

Live Jira/SharePoint content may supply the authorized input directly; a file snapshot is not required. Record provenance without fabricating a local filename. An existing artifact at a different project-relative path may be used through an explicit mapping in the index; do not duplicate or silently move it. If a required input exists outside the selected root, request an authorized project-relative import/mount or user-selected root/mapping before writing; never embed machine absolute paths in this portable contract.

## Missing files, index and version identity
- Inspect the selected paths before writing. Missing app context: refer to Context Builder or request it. Missing BRD/spec/cases: identify the producer and exact missing relative path. Do not run an upstream skill or invent output as though it already exists without user authorization.
- An unreadable file, unfilled template, failed export, stale revision or inaccessible external source is not a valid substitute. Report the gap; independent drafting can continue with blockers visible. Test Automation cannot execute unreviewed/missing cases.
- Create/update `A/ARTIFACT-INDEX.md` with `Latest Update`, app/work IDs, artifact-set revision, each actual project-relative path, content revision/source, status (`draft`, `proposed`, `approved`, `stale`, `blocked`, `missing`), reviewer/approval reference and links to dependencies. Do not list nonexistent Word/prototype/evidence files as ready.
- Document-local Markdown links must be calculated relative to the containing file; the index's recorded paths are explicitly project-root-relative. Never insert `A/` or `C/` literally as a machine path.
- Latest Update records an actual edit, not every read. Source-check dates remain separate. Git revisions are preferred when available; an artifact-set revision labels a coherent review batch, not a claim that a Git commit occurred.

## Overwrite, proposals and approval
Initial authorized generation may create new files marked draft. Never overwrite an existing file merely because its canonical name matches. Inspect its revision/status and user edits first. For changes, show the affected files and proposal, preserve unrelated work and retain a recoverable previous revision (existing Git history or an explicitly labeled local history snapshot) before an approved replacement. Do not assume uncommitted files are recoverable from Git.

Context proposals live in the relevant `changes/<change-id>/proposed/` directory; other artifact proposals use `A/proposals/<change-id>/`. Do not promote proposed content by changing its path or status without the applicable review. Enterprise baseline replacement needs its designated owner's approval. Every prototype feedback change proposal needs explicit human approval before updating BRD Markdown/Word, prototype or spec. Every concrete Jira creation batch needs explicit human approval. These gates are unchanged by choosing a path.

Preserve one coherent revision across BRD Markdown/Word and synchronized spec/prototype changes. If export or validation fails, mark that output stale/blocked in the index, keep the previous approved version identifiable and report the mismatch. Execution reports/evidence use a new run directory and are not overwritten by later runs. Do not commit, push, publish, create Jira issues or change permissions merely to establish file history or paths.

## Concrete path example
For application `crm` and work set `lead-assignment`, read `context/applications/crm/context.md` and the shared `context/enterprise/` baseline. The BRD is `artifacts/applications/crm/lead-assignment/requirements/BRD.md`; the prototype is `artifacts/applications/crm/lead-assignment/design/prototype/index.html`. These are example paths, not a claim those files have already been generated.

## Optional knowledge graph paths
When Graphify is explicitly enabled, its documented default output is `graphify-out/graph.json`. Governance records are `knowledge/GRAPH-STATUS.md`, `knowledge/GRAPH-SOURCES.md`, and `knowledge/GRAPH-REFRESH-QUEUE.md`; these are Agent List records, not Graphify config. No graph is created by this package. Resolve approved alternate graph locations through project-relative mappings and follow the optional graph lifecycle for source permissions, code/document freshness and fallback.
