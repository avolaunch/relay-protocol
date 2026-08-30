# REM-04 Part 12 — Application and Permission Requirement Extraction Matrix (Sections 56–60)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 56–60 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

56. First-party applications
57. Service-to-service applications
58. Indexer permissions
59. Consent delegation
60. Organisational application grants

Requirement identifiers continue sequentially from Part 11, beginning with `REM-04-648`.

---

# 56. First-party applications

## REM-04-648 — First-party client identification

**Source**  
Section 56: “An application built by the current Relay Provider must still identify itself as an application.”

**Requirement**  
An application built or supplied by the current Relay Provider MUST identify itself as a Relay Application.

**Classification**  
Application identity; first-party transparency; provider separation.

**Notes**  
Provider ownership or authorship of the client does not remove the client from the Application and Permission Model.

---

## REM-04-649 — Provider infrastructure distinction

**Source**  
Section 56: “The user should be able to distinguish: provider infrastructure...”

**Requirement**  
The user SHOULD be able to distinguish provider infrastructure from application-level actors and interfaces.

**Classification**  
User transparency; provider role separation; recommendation.

**Notes**  
Provider infrastructure includes the systems necessary to host and operate the repository, as distinct from optional software experiences.

---

## REM-04-650 — Provider administrative-access distinction

**Source**  
Section 56: “The user should be able to distinguish... provider administrative access...”

**Requirement**  
The user SHOULD be able to distinguish provider administrative access from application permissions and ordinary application activity.

**Classification**  
Administrative authority; transparency; role separation; recommendation.

**Notes**  
Administrative access must not be presented as though it were merely another optional client permission.

---

## REM-04-651 — Optional first-party-client distinction

**Source**  
Section 56: “The user should be able to distinguish... optional first-party client...”

**Requirement**  
The user SHOULD be able to identify an optional first-party client as a distinct application actor.

**Classification**  
Application identity; user choice; recommendation.

**Notes**  
A provider-supplied interface may be convenient or bundled, but it remains distinguishable from the underlying provider role.

---

## REM-04-652 — Third-party-application distinction

**Source**  
Section 56: “The user should be able to distinguish... third-party applications.”

**Requirement**  
The user SHOULD be able to distinguish third-party applications from provider infrastructure, provider administration and first-party clients.

**Classification**  
Application identity; ecosystem transparency; recommendation.

**Notes**  
This distinction supports informed consent and accurate attribution of application activity.

---

## REM-04-653 — No first-party evasion of the Permission Model

**Source**  
Section 56: “A provider must not evade the Permission Model merely because it also built the interface.”

**Requirement**  
A Relay Provider MUST NOT evade or bypass the Permission Model merely because the provider also developed, distributes or operates the user interface.

**Classification**  
Permission enforcement; first-party neutrality; provider accountability.

**Notes**  
The same authority boundaries that apply to third-party applications must remain meaningful for optional first-party applications.

---

# 57. Service-to-service applications

## REM-04-654 — Support for applications without direct user interfaces

**Source**  
Section 57: “Some applications may operate without a direct end-user interface.”

**Requirement**  
The Application and Permission Model MUST support application actors that operate without a direct end-user interface.

**Classification**  
Service architecture; application actor model; interoperability.

**Notes**  
The absence of a visible client interface does not remove the service from protocol governance.

---

## REM-04-655 — Search indexer as an application actor

**Source**  
Section 57, examples: “search indexer”.

**Requirement**  
A search indexer interacting with Relay data MUST be treated as an application actor where the Application and Permission Model applies.

**Classification**  
Service-to-service application; indexing; accountability.

**Notes**  
Section 58 provides additional indexing-specific requirements.

---

## REM-04-656 — Moderation labeller as an application actor

**Source**  
Section 57, examples: “moderation labeller”.

**Requirement**  
A moderation-labelling service interacting with Relay data MUST be treated as an application actor.

**Classification**  
Service-to-service application; moderation; accountability.

**Notes**  
The service’s labels or outputs do not give it unrestricted access to the records it processes.

---

## REM-04-657 — Backup service as an application actor

**Source**  
Section 57, examples: “backup service”.

**Requirement**  
A backup service interacting with a Relay Identity or Repository MUST be treated as an application actor.

**Classification**  
Service-to-service application; backup; delegated access.

**Notes**  
Backup purpose does not itself establish unlimited repository access or indefinite retention authority.

---

## REM-04-658 — Media transcoder as an application actor

**Source**  
Section 57, examples: “media transcoder”.

**Requirement**  
A media-transcoding service interacting with Relay records or blobs MUST be treated as an application actor.

**Classification**  
Service-to-service application; media processing; accountability.

**Notes**  
Its grant should be limited to the required media objects and processing operations.

---

## REM-04-659 — Analytics processor as an application actor

**Source**  
Section 57, examples: “analytics processor”.

**Requirement**  
An analytics-processing service interacting with Relay data MUST be treated as an application actor.

**Classification**  
Service-to-service application; analytics; accountability.

**Notes**  
Analytics purpose must not be used as a broad substitute for declared resources, actions, retention or onward sharing.

---

## REM-04-660 — Application Identity for service-to-service actors

**Source**  
Section 57: “These services must still have: an Application Identity...”

**Requirement**  
Every service-to-service application actor MUST have an Application Identity.

**Classification**  
Application identity; machine actor accountability.

**Notes**  
The identity must remain stable and distinct from individual deployments where applicable.

---

## REM-04-661 — Manifest for service-to-service actors

**Source**  
Section 57: “These services must still have... a manifest...”

**Requirement**  
Every service-to-service application actor MUST have an Application Manifest.

**Classification**  
Application manifest; transparency; service accountability.

**Notes**  
A backend-only implementation does not justify omission of manifest information.

---

## REM-04-662 — Defined scopes for service-to-service actors

**Source**  
Section 57: “These services must still have... defined scopes...”

**Requirement**  
Every service-to-service application actor MUST operate under defined scopes.

**Classification**  
Scope limitation; least privilege; service security.

**Notes**  
The scopes should be no broader than the processing function requires.

---

## REM-04-663 — Declared purpose for service-to-service actors

**Source**  
Section 57: “These services must still have... declared purpose...”

**Requirement**  
Every service-to-service application actor MUST declare its processing purpose.

**Classification**  
Purpose limitation; service transparency.

**Notes**  
The lack of a direct user-facing interface makes machine-readable and authorisation-interface disclosure especially important.

---

## REM-04-664 — Limited authority for service-to-service actors

**Source**  
Section 57: “These services must still have... limited authority...”

**Requirement**  
Every service-to-service application actor MUST have authority limited to its approved resources, actions, purpose, duration and conditions.

**Classification**  
Least privilege; delegated authority; service security.

**Notes**  
A service integration must not receive unrestricted authority merely because it operates in backend infrastructure.

---

## REM-04-665 — Revocation behaviour for service-to-service actors

**Source**  
Section 57: “These services must still have... revocation behaviour.”

**Requirement**  
Every service-to-service application actor MUST define and support revocation behaviour.

**Classification**  
Revocation; service lifecycle; authority control.

**Notes**  
Revocation behaviour should address active tokens, subscriptions, delegated keys and retained data as applicable.

---

## REM-04-666 — Hidden backend integrations remain application actors

**Source**  
Section 57: “A hidden backend integration is still an application actor.”

**Requirement**  
A backend integration MUST NOT be excluded from the Application and Permission Model merely because it is hidden from the end user or invoked indirectly by another application.

**Classification**  
Application actor classification; transparency; anti-evasion.

**Notes**  
The requirement prevents user-facing applications from bypassing permission controls through undisclosed backend services.

---

# 58. Indexer permissions

## REM-04-667 — Conditional public indexing without a private grant

**Source**  
Section 58: “Public indexers may read public records without a private grant where protocol policy allows.”

**Requirement**  
A public indexer MAY read public records without a private Permission Grant only where applicable protocol policy permits such access.

**Classification**  
Public access; indexing; protocol policy.

**Notes**  
Public visibility alone does not create an unconditional indexing entitlement; protocol policy remains controlling.

---

## REM-04-668 — Explicit authority for restricted indexing

**Source**  
Section 58: “However, restricted or private indexing requires explicit authority.”

**Requirement**  
Indexing restricted records MUST require explicit authority.

**Classification**  
Restricted access; indexing permission; privacy.

**Notes**  
The authority must identify the applicable resources, indexing purpose and related processing conditions.

---

## REM-04-669 — Explicit authority for private indexing

**Source**  
Section 58: “However, restricted or private indexing requires explicit authority.”

**Requirement**  
Indexing private records MUST require explicit authority.

**Classification**  
Private access; indexing permission; privacy.

**Notes**  
Access to private content for another purpose must not be silently repurposed for indexing.

---

## REM-04-670 — Indexing-purpose declaration

**Source**  
Section 58: “Indexers should declare: indexing purpose...”

**Requirement**  
An indexer SHOULD declare its indexing purpose.

**Classification**  
Purpose limitation; indexing transparency; recommendation.

**Notes**  
Examples may include discovery, search, internal retrieval or another specifically described purpose.

---

## REM-04-671 — Refresh-behaviour declaration

**Source**  
Section 58: “Indexers should declare... refresh behaviour...”

**Requirement**  
An indexer SHOULD declare how and when indexed information is refreshed.

**Classification**  
Index lifecycle; freshness; recommendation.

**Notes**  
The declaration should allow users and providers to understand expected propagation of updates.

---

## REM-04-672 — Deletion-handling declaration

**Source**  
Section 58: “Indexers should declare... deletion handling...”

**Requirement**  
An indexer SHOULD declare how deletion, tombstone or retirement events are handled in the index.

**Classification**  
Deletion propagation; indexing lifecycle; recommendation.

**Notes**  
The declaration should address removal, de-indexing or retained historical metadata where applicable.

---

## REM-04-673 — Indexer-retention declaration

**Source**  
Section 58: “Indexers should declare... retention...”

**Requirement**  
An indexer SHOULD declare how long indexed data and derived representations are retained.

**Classification**  
Retention; indexing transparency; recommendation.

**Notes**  
Retention should cover both source copies and derived index structures where relevant.

---

## REM-04-674 — Embedding-creation declaration

**Source**  
Section 58: “Indexers should declare... whether embeddings are created...”

**Requirement**  
An indexer SHOULD declare whether it creates embeddings or comparable derived representations from Relay records.

**Classification**  
AI processing; derived data; indexing transparency; recommendation.

**Notes**  
Embedding creation is distinct from ordinary textual indexing and should not be implied by a generic search permission.

---

## REM-04-675 — Model-training declaration by indexers

**Source**  
Section 58: “Indexers should declare... whether model training occurs...”

**Requirement**  
An indexer SHOULD declare whether indexed records or derived representations are used for model training.

**Classification**  
AI training; purpose limitation; indexing transparency; recommendation.

**Notes**  
Indexing authority must not be treated automatically as authority for general or application-specific model training.

---

## REM-04-676 — Index-removal process declaration

**Source**  
Section 58: “Indexers should declare... how users request removal from the index.”

**Requirement**  
An indexer SHOULD declare the process by which users may request removal from the index.

**Classification**  
User control; removal process; indexing transparency; recommendation.

**Notes**  
The process may be subject to protocol policy, legal obligations and public-record rules, but it should be discoverable.

---

## REM-04-677 — Indexer is not the canonical source

**Source**  
Section 58: “Indexing does not make the indexer the canonical source.”

**Requirement**  
An indexer MUST NOT be treated as the canonical source of a Relay Record merely because it stores, transforms, ranks or exposes an indexed representation of that record.

**Classification**  
Canonical authority; indexing; repository primacy.

**Notes**  
Canonical record state remains anchored in the authoritative repository and its accepted history.

---

# 59. Consent delegation

## REM-04-678 — Support for delegated consent authority

**Source**  
Section 59: “In some cases, another authority may approve permissions on behalf of the identity.”

**Requirement**  
The Permission Model MAY support another authority approving permissions on behalf of a Relay Identity.

**Classification**  
Delegated consent; authority model; extensibility.

**Notes**  
Delegation must be independently established and must not be inferred from ordinary account access.

---

## REM-04-679 — Parent or guardian delegation

**Source**  
Section 59, examples: “parent or guardian”.

**Requirement**  
The model MAY represent a parent or guardian as a delegated consent authority where valid authority exists.

**Classification**  
Delegated consent; guardianship; authority representation.

**Notes**  
The protocol representation does not itself determine whether guardianship is legally valid in a particular jurisdiction.

---

## REM-04-680 — Organisational-administrator delegation

**Source**  
Section 59, examples: “organisational administrator”.

**Requirement**  
The model MAY represent an organisational administrator as a delegated consent authority for an organisational or managed identity.

**Classification**  
Delegated consent; organisational governance.

**Notes**  
The delegation should be limited to the administrator’s actual organisational authority.

---

## REM-04-681 — Legal-representative delegation

**Source**  
Section 59, examples: “legal representative”.

**Requirement**  
The model MAY represent a legal representative as a delegated consent authority where valid representative authority exists.

**Classification**  
Delegated consent; legal authority; representation.

**Notes**  
The underlying authority may require external legal verification.

---

## REM-04-682 — Enterprise-policy delegation

**Source**  
Section 59, examples: “enterprise security policy”.

**Requirement**  
The model MAY permit an applicable enterprise security policy to approve, deny or constrain permissions on behalf of a managed identity.

**Classification**  
Enterprise governance; policy enforcement; delegated consent.

**Notes**  
Policy-based authority should remain attributable and distinguishable from direct approval by an individual user.

---

## REM-04-683 — Delegated-agent consent

**Source**  
Section 59, examples: “delegated agent”.

**Requirement**  
The model MAY represent a delegated agent as an authority capable of approving permissions within the agent’s authorised limits.

**Classification**  
Delegated consent; agent authority; scope limitation.

**Notes**  
The agent must not be able to approve beyond the delegation it received.

---

## REM-04-684 — Record of the approving authority

**Source**  
Section 59: “The system must record: who approved...”

**Requirement**  
The system MUST record the identity or authority that approved a delegated Permission Grant.

**Classification**  
Auditability; delegated consent; attribution.

**Notes**  
The record must distinguish the approving authority from the identity on whose behalf approval occurred.

---

## REM-04-685 — Record of delegation basis

**Source**  
Section 59: “The system must record... under what authority...”

**Requirement**  
The system MUST record the authority basis under which delegated approval was made.

**Classification**  
Authority provenance; delegated consent; auditability.

**Notes**  
The basis may reference guardianship, organisational role, legal representation, policy or another delegation record.

---

## REM-04-686 — Record of controller override rights

**Source**  
Section 59: “The system must record... whether the controller may override the decision...”

**Requirement**  
The system MUST record whether the identity controller may override the delegated consent decision.

**Classification**  
Override authority; delegated consent; governance.

**Notes**  
The source does not require that override always be permitted; it requires the rule to be explicit.

---

## REM-04-687 — Record of delegation expiration

**Source**  
Section 59: “The system must record... when the delegation expires.”

**Requirement**  
The system MUST record when the delegated consent authority expires.

**Classification**  
Temporal authority; delegation lifecycle; auditability.

**Notes**  
An expired delegation must not continue to authorise new consent decisions.

---

## REM-04-688 — No inference of delegation from account access

**Source**  
Section 59: “Consent delegation must not be inferred merely from access to an account.”

**Requirement**  
Consent delegation MUST NOT be inferred solely because a person, application or agent can access an account, session, device or repository interface.

**Classification**  
Authority validation; anti-impersonation; delegated consent.

**Notes**  
Operational access and authority to approve new Permission Grants are separate capabilities.

---

# 60. Organisational application grants

## REM-04-689 — Support for multi-party organisational approval

**Source**  
Section 60: “An organisational Relay Identity may require multi-party approval.”

**Requirement**  
The Permission Model MAY support an organisational Relay Identity requiring approval from multiple authorised parties.

**Classification**  
Organisational governance; multi-party authorisation.

**Notes**  
The applicable approval threshold should be defined by organisational policy or authority records.

---

## REM-04-690 — Threshold approval for sensitive organisational actions

**Source**  
Section 60, example: “Two authorised directors must approve repository export.”

**Requirement**  
An organisational grant MAY require a defined threshold of authorised approvers before a sensitive operation or capability is approved.

**Classification**  
Threshold authorisation; organisational security; high-authority operations.

**Notes**  
The two-director example is illustrative rather than a universal threshold.

---

## REM-04-691 — Pending state before threshold satisfaction

**Source**  
Section 60: “A grant may remain pending until the required approval threshold is met.”

**Requirement**  
An organisational Permission Grant MAY remain pending and MUST NOT become exercisable until its required approval threshold has been met.

**Classification**  
Grant lifecycle; threshold authorisation; pending state.

**Notes**  
A pending grant is not equivalent to an active grant and must not support token issuance or authorised operations.

---

## REM-04-692 — Basic multi-controller support permitted in Relay v0.1

**Source**  
Section 60: “Relay v0.1 may implement only basic multi-controller support...”

**Requirement**  
Relay v0.1 MAY implement only basic multi-controller and multi-approver functionality.

**Classification**  
Version scope; implementation allowance; organisational governance.

**Notes**  
The allowance limits initial implementation complexity but does not permit the conceptual model to assume single-person approval in all cases.

---

## REM-04-693 — No universal single-click consent assumption

**Source**  
Section 60: “...but the model should not assume that every permission comes from one individual click.”

**Requirement**  
The Permission Model SHOULD NOT assume that every Permission Grant is produced by one individual approval action or a single user-interface click.

**Classification**  
Organisational governance; consent modelling; recommendation.

**Notes**  
Implementations should preserve room for thresholds, sequential approval, policy approval and other multi-controller processes.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 56–60 of `design-notes/04-application-and-permission-model.md`.
- Section 61 and later content was excluded.
- Examples were treated as illustrative unless the source expressly imposed a normative rule.

## Numbering verification

- First requirement: `REM-04-648`.
- Final requirement: `REM-04-693`.
- Requirement numbering continues directly from Part 11.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit sentence, list item or necessary decomposition of a compound source statement.
- Lists of mandatory service-to-service attributes and delegated-consent audit fields were extracted individually because each is separately testable.
- Recommended indexer declarations retain `SHOULD` language and were not strengthened into universal mandates.

## Normative-language verification

- Source “must” and “must not” statements are represented using `MUST` and `MUST NOT`.
- Source “should” and “should not” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or implementation options.
- Illustrative actor types and organisational thresholds were not converted into exclusive or universal categories.

## Editorial verification

- First-party clients remain distinguishable from provider infrastructure and administrative authority.
- Hidden backend integrations remain application actors subject to identity, manifest, scope, purpose, limitation and revocation requirements.
- Public indexing remains conditional on protocol policy, while restricted and private indexing require explicit authority.
- Indexers do not become canonical record sources.
- Delegated consent remains explicit, attributable, time-bounded and distinct from mere account access.
- Organisational grants may require threshold approval and remain non-exercisable while pending.
