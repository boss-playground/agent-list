---
name: implementation-planner
description: Convert reviewed requirements, technical specifications and application context into an ordered implementation plan and proposed Jira stories/tasks with dependencies and traceability. Use for planning and approved Jira creation, not implementation or automatic ticket publishing.
---

# Implementation Planner

Latest Update: 2026-11-08T16:18:59Z

## Optional knowledge graph
When Graphify has been explicitly enabled for this project, read [the optional graph lifecycle](references/graphify-lifecycle.md). Query only the authorized scope, verify original sources, then save canonical outputs and queue the correct approved code/semantic refresh. If unavailable/stale, use targeted original files. Never install, scan, upload or manually mutate a graph merely because this skill runs.

## Guided intake
Follow [the guided intake contract](references/guided-intake.md): inspect known inputs first, ask concise role-appropriate questions only for missing required decisions, then summarize and confirm choices before treating them as decided. Keep assumptions, gaps and review gates explicit. This skill does not automatically launch other skills.

## Input/output path contract
Before resolving inputs or writing outputs, read [the project-relative path contract](references/artifact-paths.md). Select the project root, application only for application-scoped work, and work set only for feature artifacts; use this skill's required/optional input row and canonical outputs. Bare output filenames below are basenames within that contract, not paths relative to the skill folder. Preserve required approvals and never overwrite an existing artifact implicitly.

Read [the context contract](references/context-contract.md), the selected application's context, enterprise baseline, BRD, technical specification, prototype map and any feedback/change history. Use [the plan template](assets/implementation-plan-template.md). Identify the exact artifact revisions and approval state; do not plan from mismatched BRD/spec/prototype revisions without flagging the gap.

## Build an executable plan
1. Confirm application, implementation scope, delivery constraints and intended Jira destination when available. Read relevant current code and existing backlog only within authorized access. Record evidence, assumptions, open questions and unreviewed inputs separately.
2. Decompose the work into ordered, reviewable slices with business outcomes. Cover necessary foundation work, data/API/UI changes, tests, security/privacy requirements, migration/rollout and operational work where applicable. Avoid adding unsupported scope, invented estimates or arbitrary technology changes.
3. Give each plan item a stable local ID, such as PLAN-001. Map it to BR/AC IDs, spec screen/interaction/API/data IDs and relevant enterprise constraints. Preserve existing IDs and note any untraceable technical enabler with its rationale and owner decision.
4. Record prerequisites, explicit dependency IDs, blocking decisions, suggested sequence/parallel work, deliverable and definition of done. Check for dependency cycles, missing prerequisite work and coverage gaps. For brownfield work, preserve compatibility, migration and rollback constraints.
5. Propose Jira issue types and decomposition appropriate to the actual Jira project's hierarchy. Do not assume that every project supports Epic/Story/Task/Sub-task or an identical workflow. A proposed story/task contains a summary, description, business outcome, source IDs, acceptance/verification criteria, dependencies and assumptions. Estimates, assignees, priorities, sprints and dates remain proposed or unset unless supplied/authorized.

## User-approved Kanban defaults
Use these as proposed planning defaults: `To Do` → `In Progress` → `Review` → `Done`. A Story carries the business goal, acceptance criteria and BRD link. A Task carries implementation details, dependency IDs/links and the technical specification link. Keep requirement/spec IDs in addition to links so the relationship survives file relocation.

These defaults are not proof of the target Jira configuration. Read the actual project's issue types, workflow statuses and allowed fields, then map the proposed plan to them. Flag material mismatches for review rather than creating statuses or changing a board/workflow. Approval of these defaults does not authorize board changes, workflow configuration, issue transitions or ticket creation; the concrete-batch approval gate still applies.

## Mandatory Jira approval gate
Prepare the plan and ticket batch for review first. **Require explicit human approval of the concrete batch before creating any Jira issues**, even when the initial request includes “plan and create tickets”. Show the Jira project, issue count/types, summaries, substantive descriptions/acceptance criteria, dependency links and consequential field choices. Record the approval and the exact batch revision it covers. A review comment or request to revise a draft is not creation approval. Material changes to that batch require renewed approval.

Before asking for approval, identify the real Jira project ID/key and its required fields through the connected Jira capability when available. Resolve required custom fields, permitted issue types, parent requirements and other creation requirements. Do not guess project IDs, field IDs or options. If access is unavailable, deliver the proposed plan/batch and name the missing connection or project details; do not imply tickets were created. Reading a backlog does not authorize changing existing tickets.

## Safe creation and retry
After explicit approval, create only the approved issues and links using the available Jira capability. Use a supported idempotency key when available; otherwise include a stable approved batch ID + local item ID in an appropriate field or description marker, and retain a local creation ledger. Check existing issues for those markers and substantively matching tickets before creation. If a possible duplicate cannot be resolved, stop that item and report it instead of creating another.

Create parents/prerequisites before dependent children where Jira requires it. Keep each confirmed returned issue key/URL immediately. If a response times out or the outcome is uncertain, look up the marker/key and inspect whether creation took effect before retrying. Never rerun the entire batch blindly. If duplicate detection cannot establish the outcome, mark the item `uncertain` and request resolution instead of retrying it.

Treat issue creation and dependency-link creation as separate outcomes. If issues succeed but links fail, retry only the known failed links after verifying existing links. Do not recreate successful issues. Do not delete or rewrite successfully created issues to hide a partial failure. Scope changes, unsupported required fields or new permission/authorization requirements are blockers, not reasons to improvise.

## Deliver and verify
Produce `IMPLEMENTATION-PLAN.md` and `JIRA-BATCH.md` and `JIRA-LEDGER.md` with the same IDs and revision. Before creation, list approval as pending and actual issue keys as none. In `JIRA-LEDGER.md`, after authorized creation, record the ledger mapping each PLAN ID to confirmed Jira key/URL, status (`created`, `existing match`, `failed`, `uncertain`, `not attempted`) and link status, without claiming that existing matches were newly created.

Report the ordered plan, dependencies, requirement/spec coverage, assumptions and decisions needed. For partial execution, give exact confirmed successes and remaining failed/uncertain/not-attempted items and what can safely continue. Do not claim the whole batch succeeded from an overall tool acceptance. Planning does not implement code, schedule ongoing monitoring, move issues to Done, or authorize edits beyond the approved Jira batch.
