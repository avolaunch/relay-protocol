# REM-04 Part 8 — Application and Permission Requirement Extraction Matrix (Sections 36–40)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 36–40 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

36. User-present and user-absent actions
37. High-authority operations
38. Permission management authority
39. Revocation
40. Revocation Record

Requirement identifiers continue sequentially from Part 7, beginning with `REM-04-440`.

---

# 36. User-present and user-absent actions

## REM-04-440 — Interaction-mode distinction

**Source**  
Section 36: “Relay should distinguish” user-present and user-absent actions.

**Requirement**  
Relay SHOULD distinguish between user-present actions and user-absent actions when representing or evaluating application authority.

**Classification**  
Interaction context; permission semantics; recommendation.

**Notes**  
The distinction allows the same nominal action to carry different authority depending on whether the user is actively participating.

---

## REM-04-441 — User-present action semantics

**Source**  
Section 36, User-present action: “The user is actively interacting with the application.”

**Requirement**  
A user-present action classification MUST mean that the user is actively interacting with the application when the action occurs.

**Classification**  
Interaction context; semantic definition.

**Notes**  
Pressing a publish control is the source example. Merely having an active account or background session does not establish user presence.

---

## REM-04-442 — User-absent action semantics

**Source**  
Section 36, User-absent action: “The application acts later or continuously.”

**Requirement**  
A user-absent action classification MUST mean that the application acts later, automatically or continuously without the user actively interacting at the time of execution.

**Classification**  
Background authority; interaction context; semantic definition.

**Notes**  
Scheduled republication is the source example.

---

## REM-04-443 — Independent interaction-mode authorisation

**Source**  
Section 36: “A grant may permit one and not the other.”

**Requirement**  
A Permission Grant MAY authorise a given action in one interaction mode while withholding authority for that action in the other mode.

**Classification**  
Granular authorisation; interaction-mode scope.

**Notes**  
Authority to create content while the user is present does not automatically authorise background creation.

---

## REM-04-444 — User-present-only condition

**Source**  
Section 36 example: `"interactionMode": "user-present-only"`.

**Requirement**  
The permission model SHOULD support an explicit condition restricting an action to user-present execution only.

**Classification**  
Conditional permission; interaction-mode scope; recommendation.

**Notes**  
The example syntax is illustrative and not treated as a final wire format.

---

## REM-04-445 — No implicit background authority

**Source**  
Section 36, distinction between user-present and user-absent actions and the statement that a grant may permit one but not the other.

**Requirement**  
Authority for a user-present action MUST NOT be interpreted as implicit authority to perform the same action while the user is absent.

**Classification**  
Least privilege; background access; permission interpretation.

**Notes**  
Background authority must arise from the grant’s explicit terms.

---

# 37. High-authority operations

## REM-04-446 — Stronger protection for high-authority operations

**Source**  
Section 37: “Certain operations require stronger protection.”

**Requirement**  
Operations classified as high-authority MUST receive stronger protection than ordinary content operations.

**Classification**  
High-authority security; risk controls.

**Notes**  
The source identifies operations capable of affecting identity continuity, repository control, recovery or large-scale private-data exposure.

---

## REM-04-447 — Provider migration classification

**Source**  
Section 37, high-authority operations: “provider migration”.

**Requirement**  
Provider migration MUST be treated as a high-authority operation.

**Classification**  
Migration authority; high-risk operation.

**Notes**  
Migration can alter the infrastructure serving the person’s canonical repository.

---

## REM-04-448 — Private repository export classification

**Source**  
Section 37, high-authority operations: “repository export containing private records”.

**Requirement**  
Export of repository data containing private records MUST be treated as a high-authority operation.

**Classification**  
Data export; confidentiality; high-risk operation.

**Notes**  
The classification applies because the operation can create a large external copy of sensitive repository content.

---

## REM-04-449 — Key rotation classification

**Source**  
Section 37, high-authority operations: “key rotation”.

**Requirement**  
Rotation of identity, repository or equivalent controlling keys MUST be treated as a high-authority operation.

**Classification**  
Cryptographic authority; key management; high-risk operation.

**Notes**  
Routine application-session key renewal is not necessarily equivalent to rotation of controlling authority.

---

## REM-04-450 — Recovery-change classification

**Source**  
Section 37, high-authority operations: “recovery changes”.

**Requirement**  
Changes to recovery authority or recovery configuration MUST be treated as high-authority operations.

**Classification**  
Recovery security; identity control; high-risk operation.

**Notes**  
Recovery changes can determine who may regain control after loss or compromise.

---

## REM-04-451 — Identity-transfer classification

**Source**  
Section 37, high-authority operations: “identity transfer”.

**Requirement**  
Any supported transfer of Relay Identity control MUST be treated as a high-authority operation.

**Classification**  
Identity control; transfer authority; high-risk operation.

**Notes**  
The source classifies the operation but does not settle whether or how identity transfer is ultimately supported.

---

## REM-04-452 — Repository-erasure classification

**Source**  
Section 37, high-authority operations: “repository erasure”.

**Requirement**  
Repository-wide erasure MUST be treated as a high-authority operation.

**Classification**  
Destructive operation; repository lifecycle; high-risk operation.

**Notes**  
This is distinct from deletion of an individual record.

---

## REM-04-453 — Permission-management delegation classification

**Source**  
Section 37, high-authority operations: “granting another application permission-management authority”.

**Requirement**  
Granting an application authority to manage permissions MUST itself be treated as a high-authority operation.

**Classification**  
Delegated administration; permission security; high-risk operation.

**Notes**  
Such authority may enable the grantee to affect access by other applications and therefore requires controls beyond ordinary content access.

---

## REM-04-454 — Ordinary-token prohibition

**Source**  
Section 37: “A normal content application token must not perform these operations.”

**Requirement**  
A normal content-application token MUST NOT authorise any high-authority operation identified by the protocol.

**Classification**  
Token separation; privilege boundary; high-authority security.

**Notes**  
High-authority capabilities must be represented and protected separately from ordinary content scopes.

---

## REM-04-455 — Fresh authentication

**Source**  
Section 37: high-authority actions should require “fresh authentication”.

**Requirement**  
A high-authority action SHOULD require fresh authentication close to the time of the operation.

**Classification**  
Authentication assurance; high-authority security; recommendation.

**Notes**  
A long-running background session alone should not normally satisfy this requirement.

---

## REM-04-456 — Stronger authentication

**Source**  
Section 37: high-authority actions should require “stronger authentication”.

**Requirement**  
A high-authority action SHOULD require stronger authentication than routine low-risk content access.

**Classification**  
Authentication assurance; step-up security; recommendation.

**Notes**  
The source does not prescribe one authentication method; the required strength may depend on implementation and risk.

---

## REM-04-457 — Explicit confirmation

**Source**  
Section 37: high-authority actions should require “explicit confirmation”.

**Requirement**  
A high-authority action SHOULD require explicit user confirmation for the specific operation.

**Classification**  
User confirmation; high-risk consent; recommendation.

**Notes**  
General acceptance of an application’s ordinary permissions is not equivalent to confirmation of a particular high-authority action.

---

## REM-04-458 — Operation-specific capability

**Source**  
Section 37: high-authority actions should require an “operation-specific capability”.

**Requirement**  
A high-authority action SHOULD be authorised through a capability restricted to that specific operation.

**Classification**  
Capability security; least privilege; recommendation.

**Notes**  
The capability should not expose unrelated high-authority powers.

---

## REM-04-459 — Delay or secondary approval

**Source**  
Section 37: high-authority actions should require “delay or secondary approval where appropriate”.

**Requirement**  
A high-authority action SHOULD support a delay, secondary approval or equivalent additional safeguard where the operation’s risk warrants it.

**Classification**  
Risk mitigation; multi-party approval; recommendation.

**Notes**  
The qualifier “where appropriate” requires risk-based application rather than universal delay for every operation.

---

# 38. Permission management authority

## REM-04-460 — No ordinary self-escalation authority

**Source**  
Section 38: “An application should not normally be allowed to grant itself... additional permissions.”

**Requirement**  
An application SHOULD NOT normally be permitted to grant itself additional permissions.

**Classification**  
Privilege escalation prevention; permission management; recommendation.

**Notes**  
Any exceptional delegated arrangement must remain within an explicit high-authority grant.

---

## REM-04-461 — No ordinary third-party permission authority

**Source**  
Section 38: “An application should not normally be allowed to grant... other applications additional permissions.”

**Requirement**  
An application SHOULD NOT normally be permitted to grant additional permissions to other applications.

**Classification**  
Delegated administration; privilege control; recommendation.

**Notes**  
The source allows specialised delegation but rejects it as the normal consumer model.

---

## REM-04-462 — Permission management as high authority

**Source**  
Section 38: “Permission management is a high-authority capability.”

**Requirement**  
Permission-management authority MUST be classified and protected as a high-authority capability.

**Classification**  
Permission administration; high-authority security.

**Notes**  
This includes authority capable of issuing, changing or revoking grants for applications.

---

## REM-04-463 — Managed-application boundary

**Source**  
Section 38: delegated grants must define “which applications may be managed”.

**Requirement**  
A delegated permission-management grant MUST define which applications the delegate is authorised to manage.

**Classification**  
Delegated administration; application scope.

**Notes**  
The delegate must not assume authority over applications outside the defined set.

---

## REM-04-464 — Grantable-scope boundary

**Source**  
Section 38: delegated grants must define “which scopes may be granted”.

**Requirement**  
A delegated permission-management grant MUST define the maximum scopes the delegate may grant or manage.

**Classification**  
Delegated administration; scope ceiling; least privilege.

**Notes**  
A delegate cannot lawfully issue authority broader than this ceiling.

---

## REM-04-465 — Delegation-duration boundary

**Source**  
Section 38: delegated grants must define “maximum duration”.

**Requirement**  
A delegated permission-management grant MUST define the maximum duration of grants the delegate may issue or maintain.

**Classification**  
Delegated administration; temporal limitation.

**Notes**  
The duration ceiling applies independently of the delegate’s own grant duration.

---

## REM-04-466 — User-confirmation rule

**Source**  
Section 38: delegated grants must define “whether user confirmation is required”.

**Requirement**  
A delegated permission-management grant MUST define whether individual managed permission actions require user confirmation.

**Classification**  
Delegated administration; confirmation policy.

**Notes**  
The rule must be explicit rather than inferred from the type of managing application.

---

## REM-04-467 — Revocation-authority rule

**Source**  
Section 38: delegated grants must define “whether grants may be revoked”.

**Requirement**  
A delegated permission-management grant MUST define whether the delegate may revoke grants.

**Classification**  
Delegated administration; revocation authority.

**Notes**  
Authority to issue or inspect permissions does not automatically imply authority to revoke them.

---

## REM-04-468 — Enterprise and guardian use

**Source**  
Section 38: “This may be useful for enterprise or guardian-managed identities...”

**Requirement**  
The protocol MAY support delegated permission management for enterprise-managed or guardian-managed identities.

**Classification**  
Managed identity; delegated administration; optional capability.

**Notes**  
This permission remains high-authority even where such organisational or guardian arrangements are expected.

---

## REM-04-469 — Non-default consumer behaviour

**Source**  
Section 38: delegated permission management “should not be standard consumer behaviour”.

**Requirement**  
Delegated permission-management authority SHOULD NOT be enabled as standard consumer behaviour.

**Classification**  
Consumer safety; secure defaults; recommendation.

**Notes**  
Implementations should require deliberate activation and clear explanation when offering this capability.

---

# 39. Revocation

## REM-04-470 — User revocation capability

**Source**  
Section 39: “The user must be able to revoke a Permission Grant.”

**Requirement**  
The user MUST be able to revoke an issued Permission Grant.

**Classification**  
User control; grant lifecycle; revocation.

**Notes**  
Revocability is a core property of application authority in the Relay model.

---

## REM-04-471 — Entire-application revocation

**Source**  
Section 39, revocation may apply to “an entire application”.

**Requirement**  
The revocation model MUST support revocation of all authority granted to an application.

**Classification**  
Application-wide revocation; user control.

**Notes**  
This does not automatically delete canonical records previously created under valid authority.

---

## REM-04-472 — Installation revocation

**Source**  
Section 39, revocation may apply to “one installation”.

**Requirement**  
Where installations are distinguished, the revocation model SHOULD support revocation of one installation without necessarily revoking the entire Application Identity.

**Classification**  
Installation security; granular revocation; recommendation.

**Notes**  
This supports removal of authority from a lost or retired device.

---

## REM-04-473 — Scope revocation

**Source**  
Section 39, revocation may apply to “one scope”.

**Requirement**  
The revocation model MUST support withdrawal of one authorised scope without requiring revocation of all unrelated scopes.

**Classification**  
Scope reduction; granular revocation.

**Notes**  
The resulting authority must exclude the revoked scope.

---

## REM-04-474 — Collection revocation

**Source**  
Section 39, revocation may apply to “one collection”.

**Requirement**  
The revocation model MUST support withdrawal of authority for a specified collection.

**Classification**  
Resource-level revocation; collection scope.

**Notes**  
Authority over other collections may remain valid where the grant permits.

---

## REM-04-475 — Record revocation

**Source**  
Section 39, revocation may apply to “one record”.

**Requirement**  
The revocation model MUST support withdrawal of application authority over a specified record.

**Classification**  
Record-level revocation; granular access control.

**Notes**  
The source concerns authority over the record, not deletion of the record itself.

---

## REM-04-476 — Delegated-key revocation

**Source**  
Section 39, revocation may apply to “one delegated key”.

**Requirement**  
The revocation model MUST support invalidation of an individual delegated application key.

**Classification**  
Key revocation; delegated authority.

**Notes**  
Other installations or keys may remain authorised where separately valid.

---

## REM-04-477 — Refresh-authority revocation

**Source**  
Section 39, revocation may apply to “one refresh authority”.

**Requirement**  
The revocation model MUST support revocation of an application’s refresh authority.

**Classification**  
Token lifecycle; renewable authority; revocation.

**Notes**  
Revoking refresh authority prevents future token renewal even though already expired access tokens require no further invalidation.

---

## REM-04-478 — Active-session revocation

**Source**  
Section 39, revocation may apply to “one active session”.

**Requirement**  
The revocation model MUST support termination of a specified active authorisation or access session.

**Classification**  
Session security; granular revocation.

**Notes**  
Session termination need not revoke every other valid installation or grant.

---

## REM-04-479 — Prompt future-effect requirement

**Source**  
Section 39: “A revocation must become effective for future access as quickly as practical.”

**Requirement**  
A revocation MUST become effective against future access as quickly as practical.

**Classification**  
Revocation propagation; access enforcement; timeliness.

**Notes**  
Implementations should minimise propagation and cache delays while recognising that immediate global effect may not always be technically achievable.

---

# 40. Revocation Record

## REM-04-480 — Revocation Record semantics

**Source**  
Section 40: “A Revocation Record identifies authority that is no longer valid.”

**Requirement**  
A Revocation Record MUST identify authority that is no longer valid.

**Classification**  
Authority state; revocation evidence; record semantics.

**Notes**  
The record may identify a grant or another revocable authority object supported by the implementation.

---

## REM-04-481 — Revoked-authority reference

**Source**  
Section 40 example field: `"grant": "grant_01JX8K"`.

**Requirement**  
A Revocation Record MUST identify the grant or other authority object being revoked.

**Classification**  
Traceability; revocation target.

**Notes**  
The identifier must be sufficient to prevent ambiguity about which authority became invalid.

---

## REM-04-482 — Revocation time

**Source**  
Section 40 example field: `"revokedAt"`.

**Requirement**  
A Revocation Record MUST identify the time at which revocation became effective or was recorded.

**Classification**  
Temporal metadata; authority lifecycle.

**Notes**  
The final protocol must clarify any distinction between requested, recorded and effective times where they differ.

---

## REM-04-483 — Revoking authority

**Source**  
Section 40 example field: `"revokedBy"`.

**Requirement**  
A Revocation Record MUST identify the identity or valid authority that authorised the revocation.

**Classification**  
Authority attribution; auditability.

**Notes**  
Revocation must not be accepted solely because an unauthorised party submitted a correctly structured record.

---

## REM-04-484 — Revocation reason support

**Source**  
Section 40 example field `reason` and the list of possible reasons.

**Requirement**  
A Revocation Record SHOULD support a structured reason for the revocation.

**Classification**  
Revocation metadata; auditability; recommendation.

**Notes**  
The reason may be generalised or withheld where disclosure creates risk.

---

## REM-04-485 — Revocation-record integrity

**Source**  
Section 40 example field: `"signature": "..."`.

**Requirement**  
A Revocation Record MUST be protected by a valid signature or equivalent protocol integrity and authority mechanism.

**Classification**  
Integrity; authority proof; revocation security.

**Notes**  
The example uses a signature, but the exact serialisation and cryptographic mechanism remain implementation details unless fixed elsewhere.

---

## REM-04-486 — User-revoked reason

**Source**  
Section 40 possible reason: `user-revoked`.

**Requirement**  
The revocation-reason vocabulary SHOULD support user-initiated revocation.

**Classification**  
Reason vocabulary; user control; recommendation.

**Notes**  
The exact token shown in the source is illustrative unless adopted by the final schema.

---

## REM-04-487 — Expired reason

**Source**  
Section 40 possible reason: `expired`.

**Requirement**  
The revocation or invalidation vocabulary SHOULD support authority that is no longer valid because it expired.

**Classification**  
Reason vocabulary; temporal expiry; recommendation.

**Notes**  
An implementation may distinguish natural expiration from an active revocation event while preserving a common invalid-authority model.

---

## REM-04-488 — Application-compromised reason

**Source**  
Section 40 possible reason: `application-compromised`.

**Requirement**  
The revocation-reason vocabulary SHOULD support application compromise as a reason for invalidating authority.

**Classification**  
Security incident; reason vocabulary; recommendation.

**Notes**  
This reason can support rapid invalidation of grants, keys, sessions or refresh authority associated with the compromised application.

---

## REM-04-489 — Application-suspended reason

**Source**  
Section 40 possible reason: `application-suspended`.

**Requirement**  
The revocation-reason vocabulary SHOULD support application suspension as a reason for invalidating or pausing authority.

**Classification**  
Application status; reason vocabulary; recommendation.

**Notes**  
The final protocol should distinguish temporary suspension from permanent revocation where their effects differ.

---

## REM-04-490 — Scope-replaced reason

**Source**  
Section 40 possible reason: `scope-replaced`.

**Requirement**  
The revocation-reason vocabulary SHOULD support replacement of prior scope authority by a revised grant.

**Classification**  
Grant supersession; reason vocabulary; recommendation.

**Notes**  
This supports auditable scope reduction or restructuring without representing the application as wholly revoked.

---

## REM-04-491 — Provider-security-action reason

**Source**  
Section 40 possible reason: `provider-security-action`.

**Requirement**  
The revocation-reason vocabulary SHOULD support a provider security action as a reason for invalidating authority.

**Classification**  
Provider security; reason vocabulary; recommendation.

**Notes**  
The provider must itself possess valid protocol or policy authority to take the action.

---

## REM-04-492 — Identity-recovery reason

**Source**  
Section 40 possible reason: `identity-recovery`.

**Requirement**  
The revocation-reason vocabulary SHOULD support identity recovery as a reason for invalidating prior application authority.

**Classification**  
Recovery security; reason vocabulary; recommendation.

**Notes**  
Recovery may require invalidating grants, keys or sessions that existed before control was restored.

---

## REM-04-493 — Controller-change reason

**Source**  
Section 40 possible reason: `controller-change`.

**Requirement**  
The revocation-reason vocabulary SHOULD support a material application-controller change as a reason for invalidating prior authority.

**Classification**  
Application governance; reason vocabulary; recommendation.

**Notes**  
A controller change may also trigger manifest versioning and re-authorisation requirements in later sections.

---

## REM-04-494 — Privacy-preserving reason disclosure

**Source**  
Section 40: “The reason may be private or generalised where disclosure would create risk.”

**Requirement**  
A Revocation Record MAY keep the detailed reason private or expose only a generalised reason where fuller disclosure would create security, privacy or safety risk.

**Classification**  
Privacy; security disclosure; revocation metadata.

**Notes**  
Generalisation must not obscure the fact that the referenced authority is no longer valid.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 36–40 of `design-notes/04-application-and-permission-model.md`.
- Section 41 and later revocation effects were not extracted into this part.
- Examples were used to clarify interaction modes, revocation structure and reason vocabulary without treating provisional JSON as final schema syntax.

## Numbering verification

- First requirement: `REM-04-440`.
- Final requirement: `REM-04-494`.
- Requirement numbering continues directly from Part 7.
- Identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each high-authority operation was extracted independently because each creates a separately testable classification rule.
- Each revocation target was extracted independently because granular revocation is an explicit feature of the source model.
- Revocation-reason examples were retained as recommended vocabulary support rather than falsely promoted into a final closed enumeration.

## Normative-language verification

- Source “must” statements are represented as `MUST` or `MUST NOT`.
- Source “should” statements remain `SHOULD` or `SHOULD NOT` recommendations.
- Source “may” statements remain `MAY` permissions.
- Definitions were converted into testable requirements without strengthening optional source language.

## Editorial verification

- User-present authority is not treated as implicit background authority.
- Ordinary content tokens cannot exercise high-authority operations.
- Permission-management delegation cannot exceed explicit application, scope, duration, confirmation and revocation boundaries.
- Revocation is granular and future-facing; it is not represented as automatic deletion of previously created records or copies.
- Revocation reason privacy does not weaken the requirement that invalid authority remain clearly identifiable.
