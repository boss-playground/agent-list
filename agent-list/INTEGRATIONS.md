# Integrations — Setup and Verification Guide

Latest Update: 2026-11-08T16:19:25Z
Owner: Platform administrator / enterprise policy owner / Jira project owner (to be assigned)
Status: proposed setup guidance; no connection verified

เอกสารนี้อธิบายสิ่งที่ต้องเชื่อมต่อและวิธีตรวจสิทธิ์ ไม่ได้เชื่อม Jira หรือ SharePoint ให้แล้ว และไม่ได้ขอให้ใส่รหัสผ่าน/token ในแชตหรือไฟล์ context

## 1. Connection choices
Use the organization's approved, official Jira and SharePoint connector, MCP integration or API client when it supports the required operation. Availability differs by product, workspace, edition and admin policy. A connected app in one client does not prove it is available in another, and storing a URL in Markdown does not grant access.

Before installation/configuration, the platform owner should identify the exact client and integration, verify its publisher and current official documentation, review requested permissions and approve the minimum necessary access. This package deliberately contains no guessed MCP server URLs, OAuth scope strings, API endpoints, configuration JSON or client-specific installation commands. Obtain those only from the verified official documentation for the selected integration and deployed version. A third-party MCP server requires separate organizational review; do not assume it is official because its name contains Jira or SharePoint.

Supported fallbacks are authorized document exports, repository files or human-supplied structured inputs. Fallbacks permit drafting with explicit freshness/coverage limits, not claiming a live integration or an external action.

### Confirmed deployment and preferred Jira connection
The user confirmed **Jira Cloud**. Prefer **Atlassian's official remote MCP server** for the Jira integration, subject to the organization's admin policy and the selected client's support. Follow the current [official Atlassian MCP setup guide](https://support.atlassian.com/atlassian-ai-gateway/docs/get-started-with-the-atlassian-remote-mcp-server/) for client-specific setup and authentication; this guide was read on 2026-11-08. It documents Codex and Claude setup and an OAuth sign-in flow that respects existing Atlassian permissions.

Use the official client setup/authentication process rather than copying credentials into this package. Confirm the current endpoint and commands from that source when configuring the actual client; no client configuration was applied here. Connected products and permissions can be broader than this workflow requires, so retain least-privilege review and expose/use only needed capabilities where supported. The mandatory human approval of each concrete Jira creation batch, destination verification, retry/duplicate controls and manual fallback still apply.

**SharePoint deployment remains unknown.** Confirm whether the organization uses SharePoint Online or another deployment and identify its approved connector/access method before giving platform-specific setup instructions. Jira Cloud confirmation does not establish SharePoint availability or consent.

## 2. Capability matrix by skill
| Skill | Jira capability | SharePoint / enterprise policy capability | Safe fallback / limitation |
|---|---|---|---|
| Context Builder | Not required | Read selected Security/PII documents and metadata if creating/verifying enterprise context | Approved exports or existing baseline; record source/version and that live source was not checked |
| Context Updater | Not required | Read current selected policy documents/metadata for comparison with reviewed baseline | Compare provided versions; without current source access, report current-source check blocked |
| BRD Builder | Optional read of relevant stories/tasks if included as input | Read reviewed enterprise context; source read if freshness/applicability needs verification | BA notes, code and approved context/exports; preserve source gaps |
| Technical Specification | Optional read of linked requirements/tasks | Read enterprise context and relevant accessible policy evidence | Supplied BRD/context; label unverified requirements, stop compliance-dependent decisions |
| Implementation Planner | Read project configuration/required fields and relevant backlog; create approved stories/tasks and approved dependency links only | Read enterprise context and relevant policy evidence | Draft plan and Jira batch only; human creates tickets or supplies verified results; never claim creation from a draft |
| Implementation Builder | Read selected stories/tasks/dependencies; no Jira write needed | Read enterprise context and applicable policy evidence | Authorized story/task export plus context; no automatic transition/comment |
| Test Case Generator | Optional read of story/AC metadata | Read context and source-backed Security/PII rules | Reviewed requirement/context exports; generate cases only, flag unknown expectations |
| Test Automation | Optional read of reviewed case/story linkage; no Jira write needed | Read applicable test constraints and policy evidence | QA-reviewed cases/context and separately authorized test target; no automatic Jira test-result publication |

Read access to enterprise context does not require every skill to fetch every policy document on every run. Resolve the reviewed baseline and fetch only the source material needed for the requested scope or freshness check. Record what was actually read and checked. Never confuse a locally cached file with a successful check of SharePoint's current version.

## 3. Jira: least privilege and setup
1. Identify the actual Jira tenant/site and target project by authorized lookup or user-provided reference. Verify the project key/ID; do not infer it from a display name.
2. Prefer read access for most skills. Implementation Planner needs only the relevant project reads, issue creation and dependency-link permissions needed for the approved batch. Project administration, workflow/board changes, broad issue deletion, account management and unrelated projects are not needed.
3. Inspect real issue types/hierarchy, required fields/custom-field options and permitted parent/link relationships. Proposed Kanban defaults (To Do, In Progress, Review, Done) are planning preferences, not authorization to change the board or workflow. Do not transition issues automatically.
4. Authenticate through the approved connector's sign-in flow or organization-managed credential mechanism. Use a scoped identity where supported. Do not save tokens/passwords in `SKILL.md`, context, scripts, Git, logs or reports. Handle credentials only via authorized secret storage/runtime injection; never ask a user to paste them into the chat.
5. Verify read access with a known permitted project/issue and confirm correct tenant/project and identity scope. Do not create a test issue merely to verify access unless that concrete creation is approved. Missing write permission is a blocker, not permission to request broad admin access.
6. Before any write, present the exact ticket batch and obtain explicit human approval. Approval of connection/setup alone does not approve ticket creation. If required fields change the material batch, update the proposal and obtain approval before writing.
7. After creation, retain each returned key/URL and verify the record and links when possible. Record partial success and uncertain responses. Use stable batch/item markers and read-before-retry reconciliation; never rerun a whole batch blindly.

### Jira verification record
- Client/integration and publisher: Atlassian official remote MCP preferred for confirmed Jira Cloud; actual client/setup not selected or verified
- Official documentation checked: [Atlassian MCP setup guide](https://support.atlassian.com/atlassian-ai-gateway/docs/get-started-with-the-atlassian-remote-mcp-server/), read 2026-11-08; recheck at configuration time
- Tenant/project and permitted scope: [not verified]
- Authentication method / credential store: [method only; no secret values]
- Read verification: [not performed / timestamp and reference]
- Write capability: [not verified / authorized batch outcome]
- Actual issue types/required fields: [not verified]
- Batch approval/ledger: [none / reference]

## 4. SharePoint: read-only enterprise standards
1. Obtain the authorized site/library/document links for Security and PII, their owners and the intended version/effective date. Resolve the canonical document, not an unrelated search snippet or an unverified copy.
2. Restrict the integration to the required sites/libraries/documents where supported and to read-only access. Do not request tenant-wide administration, unrestricted write or external sharing merely to read policy. If a chosen connector cannot narrow scope sufficiently, escalate the choice to the administrator or use approved exports.
3. Use the organization's sign-in and access-control flow. Do not bypass inaccessible files, permission restrictions, conditional access or MFA. Do not copy cookies/tokens to workaround access. Authentication, connector consent and access expansion remain explicit authorized setup steps.
4. Read the actual relevant document content and provenance: canonical URL/path, title, owner, section, version/revision, effective date if present, and successful read timestamp. Preserve classification and internal-use restrictions. Do not transmit internal policy content to a new external service simply to parse it without authorization.
5. Keep a separate `last successful check` and `latest attempt/result`. A login failure, stale cache, partial extraction or unsupported attachment does not mean the standard is unchanged. If source content cannot be read, request an authorized accessible export or report the check blocked.
6. When a standard changes, propose the context difference and affected applications for owner review. Reading SharePoint does not authorize editing SharePoint, publishing a new policy or automatically replacing an approved enterprise baseline.

### SharePoint verification record
- Client/integration and publisher: [not selected]
- Official documentation checked: [URL, version/date; not checked]
- Authorized site/library/documents: [not provided]
- Read-only permission scope: [not verified]
- Policy owner / canonical source / version: [unknown]
- Last successful source read: [not checked]
- Latest attempt / coverage / result: [not checked]
- Export fallback and freshness limitation: [none / details]

## 5. Manual/export fallback
An authorized person can provide policy files or selected text with canonical URL, title, version/effective date and owner, and a Jira issue export containing key, summary, description, AC, linked tasks, dependencies and relevant field values. Include only information needed for the task, excluding secrets and real personal records. Obtain permission before moving sensitive information to a new destination.

Record who supplied each input and when, but do not treat that timestamp as proof of the live source's freshness. Label source checks as `provided export reviewed; live source not checked` where applicable. Code-derived behavior remains implementation evidence, not a replacement for missing business/policy approval.

For Jira, generate the proposed batch locally when write access is absent. If a human creates the issues, record the supplied keys as human-reported until verified; do not state the skill created them. If the source cannot be accessed later, preserve the last confirmed result and describe the limitation.

## 6. Readiness check before a run
- Correct client, authenticated identity, destination and minimum permission scope verified?
- Selected source documents/projects accessible and relevant revisions recorded?
- Requested operation supported, or fallback clearly labeled?
- Human approval recorded for the concrete Jira write batch?
- No secrets or real PII embedded in files/evidence?
- Verification limits and partial outcomes visible in the result?

Integration readiness is separate from skill correctness and separate from authorization for each consequential operation. No connection or permission is established by this guide.

## 7. Optional Graphify candidate
See [GRAPHIFY.md](GRAPHIFY.md) for the verified candidate product, eight-skill read/refresh lifecycle and source security. This is a separate optional integration: Jira/SharePoint access does not approve uploading their content to a graph service or semantic model. Candidate configuration, source manifests, code/document freshness and graph access must be explicitly reviewed. No Graphify install, hook, provider or MCP connection has been established.
