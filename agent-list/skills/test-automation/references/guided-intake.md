# Guided intake and review contract

Latest Update: 2026-11-08T16:14:34Z
Owner: skill operator / designated reviewer
Status: workflow convention

## Purpose
Help a person use a skill without needing advanced prompting. This is a guided conversation for the selected skill, not an autonomous orchestrator. Do not invoke upstream/downstream skills, change the requested objective, or create external side effects simply because an input is missing.

## Inspect before asking
Read the relevant conversation, selected application/work-set index when applicable and accessible required files under the path contract. Preserve the user's latest corrections. Identify what is known, confirmed, inferred, assumed, missing or conflicting and its source. Do not repeat a question already answered unless conflicting evidence materially changes it. Do not treat an old template, code behavior or an inaccessible document as a confirmed requirement.

## Ask small useful batches
Ask only for required decisions still missing after inspection. Group related questions into a short batch appropriate to the person's role; start with blockers that affect the output most. Use plain language and give concrete examples/options when they help. Explain why a question matters if it is not obvious. Offer “unknown / decide later” for a nonblocking item and record an owner/next action. Do not ask a person to know technical field IDs or prompt syntax that tools can discover.

Example: “This is a new feature in the existing CRM, or a new application? For this first version, should assignment be manual, automatic, or both?” Do not present invented options as the organization's actual policy. Recommend a sensible option when useful, label it a proposal and explain the tradeoff briefly.

## Summarize and confirm before deciding
Before turning new answers or proposed defaults into project decisions, show a compact summary: selected scope and app/work set when applicable, goal, inputs/revisions, proposed choices, assumptions, unresolved gaps and intended output paths. Ask the responsible human to confirm or correct the decisions. Reuse explicit confirmation already given for the same concrete decisions; do not ask again merely because a tool call or skill step changed. Acknowledging receipt of a question is not decision approval.

If a necessary decision remains unresolved, leave it open and describe the affected work. Clearly separate draft assumptions from confirmed choices. Do not silently invent business rules, policy, thresholds, Jira fields, credentials, endpoints, test outcomes or approvals.

## Role-specific intake prompts
| Skill / usual reviewer | Focus after existing inputs are read | Examples of useful missing-input questions |
|---|---|---|
| Context Builder / Dev Lead | Scope, greenfield/brownfield, foundation, preliminary design, enterprise references | Which application and boundaries? What must remain compatible? Which stack choices are fixed versus proposed? Who owns the Security/PII source? |
| Context Updater / Dev Lead; enterprise owner for shared rules | Requested change, baseline, source freshness and impact scope | Is this an app-only change or shared enterprise update? Which applications are known to be affected? Who reviews the new baseline? |
| BRD Builder / BA and business owner | Business goal, users, process, rules and measurable acceptance | Who performs this action? What outcome counts as success? Is a code-derived behavior required or merely how the old system works? |
| Technical Specification / Dev Lead with BA/design reviewer | Reviewable BRD, journeys, architecture decisions and prototype scope | Which user journey must be clickable first? Which APIs/data already exist? Which feedback is a proposal versus an approved requirement? |
| Implementation Planner / Dev Lead or delivery owner | Scope, dependencies, delivery slices and Jira destination | Which work should be in the first slice? Are there external prerequisites? Which Jira project should receive the proposed batch? |
| Implementation Builder / developer or Dev Lead | Selected stories, repository, AC and blocking design gaps | Which related stories are included? Which dependency is available now? Is this unresolved design choice approved or should that part remain blocked? |
| Test Case Generator / QA with BA for expected outcomes | Reviewed requirements, risk priorities, test roles and unknown expected results | Which journeys are business-critical? Which roles should have/deny access? What boundary or error outcome is still undecided? |
| Test Automation / QA or execution owner | QA-reviewed cases, authorized test target/actions, accounts, data and limits | Which nonproduction environment is authorized? Are external notifications disabled? Which cases need manual review? Is a scan explicitly authorized or excluded? |

Examples are aids, not a mandatory questionnaire. Adapt the batch to actual gaps, avoid asking all rows, and keep independent well-specified work moving within authorization.

## Pre-delivery quality and review checklist
- Required inputs have provenance and matching revisions; missing/inaccessible inputs are visible, not fabricated.
- Application, work set and output destinations are correct; no implicit overwrite or unapproved promotion of drafts.
- Output is traceable to user decisions, requirements, context and applicable evidence; assumptions/conflicts remain labeled.
- Skill-specific validation actually ran or is labeled blocked/not run; do not equate a structural check with runtime behavior or compliance.
- Explain the result, its limits, pending decisions and next reviewer in ordinary language.

Retain all specific approval gates: enterprise-owner review for shared baseline changes; designated BA/business review for requirements; explicit human approval for every prototype feedback change before replacing BRD/Word/prototype/spec; approval of the concrete Jira issue batch before creation; explicit safe environment/actions for test execution and separate concrete scan scope for ZAP. Intake confirmation alone does not approve later mutations whose material details were not presented.

Offer the next skill as an optional next step after the selected task is complete; do not start it automatically. When the user has already explicitly authorized a named sequence, stay within that sequence and retain its review gates rather than treating it as permission to invent missing decisions.
