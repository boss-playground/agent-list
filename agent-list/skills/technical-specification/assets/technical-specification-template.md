# [Application / Feature] — Technical Specification

Latest Update: [ISO 8601 with timezone]
Owner: [technical owner]
Status: draft
Reviewers: [BA / Dev Lead / relevant policy owner]
BRD: [path and revision]
Application context: [path and revision]
Enterprise baseline: [path and reviewed revision / not reviewed]

## 1. Scope and evidence
[Included journeys, exclusions, source evidence and known limitations]

| Source ID | Source / path / symbol | Revision / section | Verification status |
|---|---|---|---|
| [S-001] | [source] | [revision] | [checked / unavailable / unconfirmed] |

Evidence categories throughout: existing evidence, proposed design, unconfirmed, conflict.

## 2. Architecture and responsibilities
[Frontend, services, data, integrations, boundaries; separate current from target design]

## 3. Screens and journeys
| Screen ID | Name / purpose | Actor | Entry / exit | States | BR / AC IDs | Evidence category / source |
|---|---|---|---|---|---|---|
| [SC-001] | [screen] | [role] | [paths] | [loading, empty, etc.] | [existing IDs] | [category / source] |

## 4. Screen detail: [SC-001]
[Fields, types, display sources, visibility, state transitions, accessibility and responsive behavior]

### Interaction: [IN-001]
- Trigger / screen: [event / SC ID]
- Actor / preconditions: [role and prerequisites]
- Requirement / acceptance IDs: [BR / AC]
- Business logic: [ordered rules and decisions]
- Frontend responsibility: [presentation and preliminary validation]
- Server responsibility: [authoritative validation, authorization and data operation]
- Data reads/writes: [entities/fields]
- API ID: [API-001 / none / proposed]
- Validation and error handling: [rule, feedback, failure path]
- Security / PII: [enterprise requirement IDs, applicability, unresolved questions]
- Success / Cancel / retry behavior: [states; idempotency if relevant]
- Evidence category / source: [existing evidence / proposed / unconfirmed / conflict]
- Prototype behavior: [simulation and limits]

## 5. API contracts
| API ID | Operation / route | Auth / authorization | Request | Response / errors | Evidence category / source |
|---|---|---|---|---|---|
| [API-001] | [existing or explicitly proposed] | [contract / unresolved] | [schema] | [schema and status] | [category / source] |

[Include detailed schemas where the table is insufficient. Never present guessed endpoints as existing.]

## 6. Data design
| Entity / field | Type / constraints | Read/write owner | Classification | Relationship | Evidence category / source |
|---|---|---|---|---|---|
| [entity.field] | [type] | [component] | [source-backed / unknown] | [relation] | [category / source] |

## 7. Validation, security and privacy mapping
| Rule ID | Description | Enterprise source / requirement | Enforcement location | Screens / interactions | Status / gaps |
|---|---|---|---|---|---|
| [rule] | [requirement, not invented policy] | [ID] | [server/client] | [SC / IN] | [status] |

## 8. Prototype map and instructions
Entry point: `prototype/index.html` relative to this specification; project-root path follows the selected work-set contract.
Run/open instructions: [actual steps]
Simulation notice: synthetic data only; no production integrations

| Prototype route/state | Screen / interaction | Supported behavior | Deliberately simulated / excluded |
|---|---|---|---|
| [route] | [SC / IN] | [clickable flow] | [limits] |

## 9. Traceability coverage
| Requirement / AC | Screens | Interactions | APIs / data | Validation / test evidence | Gaps |
|---|---|---|---|---|---|
| [BR / AC] | [SC] | [IN] | [IDs] | [check] | [uncovered behavior] |

## 10. Decisions, assumptions and conflicts
| ID | Category | Item | Affected IDs | Owner / next action |
|---|---|---|---|---|
| [Q-001] | [assumption / question / conflict] | [item] | [IDs] | [owner] |

## 11. Validation and review
Browser interaction tests: [not run / exact flows and results]
Static checks: [actual checks]
Accessibility/responsive review: [coverage and limits]
Network / persistence check: [actual result]
Production implementation: not performed
Security/compliance verification: not implied
Approval: pending

## 12. Prototype feedback and synchronized revision history
Human approval gate: every feedback change proposal must be explicitly approved before updating any existing BRD, Word, prototype or specification artifact.
Approved proposal / batch ID: [none / ID]
Approved by / when: [pending / human and timestamp]
Artifact-set revision: [review identifier]
Matching BRD Markdown / Word revision: [identifier / export pending]
Matching prototype / specification revision: [identifier]

| Feedback ID / date | User request | Affected BR/AC/SC/IN IDs | Impact / decision | Review owner / status | Changed artifacts / revision | Validation |
|---|---|---|---|---|---|---|
| [FB-001] | [verbatim or faithful summary] | [IDs] | [proposed / applied / rejected / ambiguous] | [owner] | [paths / revision] | [checks / blockers] |

Stale or pending artifacts: [none only if verified; otherwise exact files and reason]
Unresolved feedback: [ambiguities, requirement conflicts, policy conflicts and next decision]
