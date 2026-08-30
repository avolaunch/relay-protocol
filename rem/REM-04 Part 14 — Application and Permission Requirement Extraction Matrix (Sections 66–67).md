# REM-04 Part 14 — Application and Permission Requirement Extraction Matrix (Sections 66–67)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 66–67 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

66. Permission invariants
67. Compliance scenario

Requirement identifiers continue sequentially from Part 13, beginning with `REM-04-748`.

---

# 66. Permission invariants

## REM-04-748 — Continuous preservation of permission invariants

**Source**  
Section 66: “The following rules must always remain true.”

**Requirement**  
Every compliant Relay Application and Permission implementation MUST preserve all permission invariants defined in Section 66 at all times.

**Classification**  
Core invariant; compliance; authorisation integrity.

**Notes**  
The invariants apply across grant issuance, token use, application operation, provider migration, suspension, revocation and replacement. They are not optional implementation guidance.

---

## REM-04-749 — Authority requires a valid basis

**Source**  
Section 66, Invariant 1: “An application has no authority without a valid grant or public-access rule.”

**Requirement**  
An application MUST NOT exercise authority over a Relay Identity, Relay Repository or protected resource unless that authority is supported by a currently valid Permission Grant or an applicable public-access rule.

**Classification**  
Authority basis; access control; core invariant.

**Notes**  
Application registration, installation, authentication or possession of application credentials does not independently establish authority over user-controlled resources.

---

## REM-04-750 — Grants cannot exceed user approval

**Source**  
Section 66, Invariant 2: “A grant cannot authorise more than the user approved.”

**Requirement**  
A Permission Grant MUST NOT authorise any resource, action, purpose, duration, interaction mode, retention practice, onward-sharing practice, AI use or condition beyond what the approving authority explicitly approved.

**Classification**  
Consent fidelity; grant limitation; core invariant.

**Notes**  
Where approval is partial, the grant must contain only the approved subset of the request.

---

## REM-04-751 — Applications cannot expand their own grants

**Source**  
Section 66, Invariant 3: “An application cannot expand its own grant.”

**Requirement**  
An application MUST NOT expand, replace or reinterpret its own Permission Grant so as to obtain additional authority without a valid approval process.

**Classification**  
Privilege escalation prevention; grant governance; core invariant.

**Notes**  
This prohibition applies whether expansion is attempted through token claims, delegated keys, manifest changes, scope interpretation or application-controlled metadata.

---

## REM-04-752 — Revocation does not delete canonical records

**Source**  
Section 66, Invariant 4: “Revoking an application does not delete canonical records it previously created.”

**Requirement**  
Revocation of an application or its Permission Grant MUST NOT, solely because of that revocation, delete canonical records previously created or submitted through the application.

**Classification**  
Record continuity; revocation semantics; application replaceability.

**Notes**  
The user may separately delete records through an authorised operation. Revocation terminates authority; it does not reverse valid repository history.

---

## REM-04-753 — Read permission does not imply retention

**Source**  
Section 66, Invariant 5: “Permission to read does not imply permission to retain, redistribute or train models.”

**Requirement**  
Permission to read a resource MUST NOT be interpreted as permission to retain a copy outside the authorised context.

**Classification**  
Purpose limitation; retention; core invariant.

**Notes**  
External retention requires its own approved declaration or authority.

---

## REM-04-754 — Read permission does not imply redistribution

**Source**  
Section 66, Invariant 5: “Permission to read does not imply permission to retain, redistribute or train models.”

**Requirement**  
Permission to read a resource MUST NOT be interpreted as permission to redistribute, disclose or provide that resource to another party.

**Classification**  
Onward sharing; purpose limitation; core invariant.

**Notes**  
Redistribution remains separately governed even where the application may lawfully display or process the resource for the approved user-facing purpose.

---

## REM-04-755 — Read permission does not imply model training

**Source**  
Section 66, Invariant 5: “Permission to read does not imply permission to retain, redistribute or train models.”

**Requirement**  
Permission to read a resource MUST NOT be interpreted as permission to use that resource for fine-tuning, general model training or another training activity.

**Classification**  
AI governance; purpose limitation; core invariant.

**Notes**  
AI inference, personalisation, embedding, evaluation and training remain distinct permission purposes under the source model.

---

## REM-04-756 — Create permission does not imply delete permission

**Source**  
Section 66, Invariant 6: “Permission to create a record does not imply permission to delete or change its visibility.”

**Requirement**  
Permission to create a record MUST NOT be interpreted as permission to delete that record or any other record.

**Classification**  
Action separation; least privilege; core invariant.

**Notes**  
Deletion requires an independently granted action scope.

---

## REM-04-757 — Create permission does not imply visibility-change permission

**Source**  
Section 66, Invariant 6: “Permission to create a record does not imply permission to delete or change its visibility.”

**Requirement**  
Permission to create a record MUST NOT be interpreted as permission to change the visibility or audience of that record.

**Classification**  
Visibility control; action separation; core invariant.

**Notes**  
A grant may permit creation while requiring user confirmation or a separate capability before publication or visibility expansion.

---

## REM-04-758 — Ordinary content access does not imply identity authority

**Source**  
Section 66, Invariant 7: “Ordinary content access does not imply identity, key, recovery or migration authority.”

**Requirement**  
Ordinary content access MUST NOT be interpreted as authority to alter, transfer or otherwise exercise control over the Relay Identity itself.

**Classification**  
High-authority separation; identity control; core invariant.

**Notes**  
Identity-level authority must be explicitly and separately granted through stronger controls.

---

## REM-04-759 — Ordinary content access does not imply key authority

**Source**  
Section 66, Invariant 7: “Ordinary content access does not imply identity, key, recovery or migration authority.”

**Requirement**  
Ordinary content access MUST NOT be interpreted as authority to create, rotate, revoke or manage identity or repository keys.

**Classification**  
Key management; high-authority separation; core invariant.

**Notes**  
Application delegated keys remain bounded by their underlying grants and do not confer key-management authority.

---

## REM-04-760 — Ordinary content access does not imply recovery authority

**Source**  
Section 66, Invariant 7: “Ordinary content access does not imply identity, key, recovery or migration authority.”

**Requirement**  
Ordinary content access MUST NOT be interpreted as authority to configure, replace or exercise identity or repository recovery mechanisms.

**Classification**  
Recovery security; high-authority separation; core invariant.

**Notes**  
Recovery operations require separately defined high-authority protection.

---

## REM-04-761 — Ordinary content access does not imply migration authority

**Source**  
Section 66, Invariant 7: “Ordinary content access does not imply identity, key, recovery or migration authority.”

**Requirement**  
Ordinary content access MUST NOT be interpreted as authority to initiate, approve or complete provider or repository migration.

**Classification**  
Migration security; high-authority separation; core invariant.

**Notes**  
Migration authority must be separately granted and may require fresh authentication, explicit confirmation or an operation-specific capability.

---

## REM-04-762 — Visible application name is not protocol identity

**Source**  
Section 66, Invariant 8: “An application’s visible name is not its permanent protocol identity.”

**Requirement**  
An application’s visible product name, brand or display label MUST NOT be used as its permanent protocol identity.

**Classification**  
Application identity; naming separation; core invariant.

**Notes**  
The stable Application Identity remains distinct from mutable branding and human-readable presentation.

---

## REM-04-763 — Material purpose change requires renewed approval

**Source**  
Section 66, Invariant 9: “A materially changed application purpose requires renewed approval.”

**Requirement**  
An application MUST obtain renewed approval before using previously granted access for a materially changed purpose.

**Classification**  
Re-authorisation; purpose limitation; core invariant.

**Notes**  
A manifest update alone does not expand the purpose authorised by an existing grant.

---

## REM-04-764 — Provider-built clients remain applications

**Source**  
Section 66, Invariant 10: “A provider-built client remains subject to the application model.”

**Requirement**  
A client application built, distributed or operated by the current Relay Provider MUST remain subject to the Application and Permission Model.

**Classification**  
First-party application governance; provider separation; core invariant.

**Notes**  
Provider ownership of the interface does not permit the provider to bypass application identity, manifest, consent, scope or revocation requirements.

---

## REM-04-765 — Active grants must be inspectable

**Source**  
Section 66, Invariant 11: “The user must be able to inspect and revoke active grants.”

**Requirement**  
The user or other authorised controller MUST be able to inspect all active Permission Grants affecting the Relay Identity or Repository.

**Classification**  
Transparency; user control; core invariant.

**Notes**  
Inspection should expose meaningful application, scope, purpose, duration and activity information rather than only opaque token identifiers.

---

## REM-04-766 — Active grants must be revocable

**Source**  
Section 66, Invariant 11: “The user must be able to inspect and revoke active grants.”

**Requirement**  
The user or other authorised controller MUST be able to revoke active Permission Grants.

**Classification**  
Revocation; user control; core invariant.

**Notes**  
Revocation may be granular where the implementation supports application-, installation-, scope-, record-, key-, refresh-authority- or session-level revocation.

---

## REM-04-767 — Provider migration cannot silently broaden access

**Source**  
Section 66, Invariant 12: “Provider migration must not silently broaden application access.”

**Requirement**  
Repository or provider migration MUST NOT silently broaden the resources, actions, purposes, duration or other authority available to an application.

**Classification**  
Migration safety; grant continuity; core invariant.

**Notes**  
Any broader authority after migration requires a valid approval or re-authorisation process.

---

## REM-04-768 — Application suspension cannot erase user records

**Source**  
Section 66, Invariant 13: “Application suspension must not erase user-owned repository records.”

**Requirement**  
Suspension of an application MUST NOT erase user-controlled or user-owned repository records.

**Classification**  
Application suspension; record continuity; core invariant.

**Notes**  
Suspension may prevent new grants, token renewal, submissions or event delivery, but it does not transfer or extinguish repository state.

---

## REM-04-769 — Tokens evidence authority, not identity ownership

**Source**  
Section 66, Invariant 14: “A token is evidence of delegated authority, not ownership of the Relay Identity.”

**Requirement**  
An access token, capability token, refresh token or equivalent authorisation credential MUST be treated only as evidence of delegated authority and MUST NOT be treated as proof that its holder owns or controls the Relay Identity beyond the token’s grant.

**Classification**  
Token semantics; identity ownership; core invariant.

**Notes**  
Token compromise must therefore be contained to the delegated authority wherever the architecture and grant boundaries permit.

---

# 67. Compliance scenario

## REM-04-770 — Basic implementation compliance test

**Source**  
Section 67: “A basic application implementation should pass the following test.”

**Requirement**  
A basic Relay Application and Permission implementation SHOULD pass the complete compliance scenario defined in Section 67 while preserving user authority and application replaceability.

**Classification**  
End-to-end compliance; implementation test; recommendation.

**Notes**  
The scenario is cumulative. Passing only individual steps is insufficient if the complete lifecycle produces privilege expansion, loss of repository state or application lock-in.

---

## REM-04-771 — Initial request must represent each requested capability

**Source**  
Section 67, Initial request: Application A requests read-public-profile, read-posts, create-posts, update-posts, delete-posts, read-private-drafts and recommendation-model training capabilities.

**Requirement**  
The Permission Request MUST represent each requested resource, action and AI purpose distinctly enough for the user to approve or deny them independently where practical.

**Classification**  
Permission request; granularity; compliance scenario.

**Notes**  
The scenario deliberately combines ordinary read and write actions with deletion, private-record access and model training to test granular consent.

---

## REM-04-772 — Partial approval must be supported

**Source**  
Section 67, Partial approval: the user approves profile reading, post reading, post creation and post updating while denying deletion, private-draft reading and recommendation-model training.

**Requirement**  
The implementation MUST support approval of a proper subset of a Permission Request without requiring approval of the full request.

**Classification**  
Granular consent; partial approval; compliance scenario.

**Notes**  
The application may operate with reduced capability, explain unavailable features or decline to continue where a denied permission is genuinely essential.

---

## REM-04-773 — Denied deletion authority must be excluded

**Source**  
Section 67, Partial approval: the user denies “Delete posts.”

**Requirement**  
Where the user denies post-deletion authority, the issued Permission Grant MUST exclude the delete action.

**Classification**  
Grant construction; denied scope; compliance scenario.

**Notes**  
The later unauthorised-deletion test depends on this exclusion being machine-enforceable.

---

## REM-04-774 — Denied private-draft access must be excluded

**Source**  
Section 67, Partial approval: the user denies “Read private drafts.”

**Requirement**  
Where the user denies access to private drafts, the issued Permission Grant MUST exclude authority to read those drafts.

**Classification**  
Private-data access; denied scope; compliance scenario.

**Notes**  
Approval to read posts generally must not be broadened to include private drafts.

---

## REM-04-775 — Denied model-training purpose must be excluded

**Source**  
Section 67, Partial approval: the user denies “Train a recommendation model.”

**Requirement**  
Where the user denies recommendation-model training, the issued Permission Grant MUST exclude that AI training purpose.

**Classification**  
AI governance; denied purpose; compliance scenario.

**Notes**  
Read access to profile or post data does not override this denial.

---

## REM-04-776 — Grant must contain only approved capabilities

**Source**  
Section 67, Partial approval: “The issued grant contains only the approved capabilities.”

**Requirement**  
The Permission Grant issued after partial approval MUST contain only the capabilities expressly approved by the user.

**Classification**  
Consent fidelity; grant limitation; compliance scenario.

**Notes**  
This is the scenario-level application of Invariant 2.

---

## REM-04-777 — Authorising identity attribution for created records

**Source**  
Section 67, Record creation: “The repository records... the user as authorising identity.”

**Requirement**  
When Application A creates a post under the grant, the repository MUST record the user as the authorising Relay Identity.

**Classification**  
Repository provenance; authorisation attribution; compliance scenario.

**Notes**  
The application’s role as submitter does not make it the authorising identity.

---

## REM-04-778 — Application submitter attribution for created records

**Source**  
Section 67, Record creation: “The repository records... Application A as submitter.”

**Requirement**  
When Application A creates a post under the grant, the repository MUST record Application A as the submitting application.

**Classification**  
Submission provenance; application attribution; compliance scenario.

**Notes**  
This records how the operation entered the repository without transferring authorship or ownership to the application.

---

## REM-04-779 — Grant attribution for created records

**Source**  
Section 67, Record creation: “The repository records... the Permission Grant used.”

**Requirement**  
When Application A creates a post under the grant, the repository MUST record or retain a verifiable reference to the Permission Grant used for the operation.

**Classification**  
Grant traceability; auditability; compliance scenario.

**Notes**  
The grant reference supports later inspection of whether the operation fell within approved authority.

---

## REM-04-780 — Unauthorised deletion must be rejected

**Source**  
Section 67, Unauthorised deletion attempt: “The repository rejects the operation because deletion was not granted.”

**Requirement**  
The repository MUST reject Application A’s attempt to delete the post when the applicable Permission Grant does not include deletion authority.

**Classification**  
Runtime authorisation; enforcement; compliance scenario.

**Notes**  
Successful creation or update of the record does not imply deletion authority.

---

## REM-04-781 — Manifest purpose change cannot expand an existing grant

**Source**  
Section 67, Manifest change: “Application A later changes its policy to permit general model training. The existing grant does not automatically expand.”

**Requirement**  
A manifest or policy change permitting general model training MUST NOT automatically expand an existing Permission Grant.

**Classification**  
Manifest drift; grant stability; compliance scenario.

**Notes**  
The grant remains bounded by the purpose approved when it was issued.

---

## REM-04-782 — Changed purpose requires user review and approval

**Source**  
Section 67, Manifest change: “The user must review and approve the changed purpose.”

**Requirement**  
Before Application A may use previously accessible data for the changed model-training purpose, the user MUST review and approve that changed purpose through re-authorisation.

**Classification**  
Purpose limitation; re-authorisation; compliance scenario.

**Notes**  
The implementation must not rely on the earlier approval for materially new AI behaviour.

---

## REM-04-783 — Revocation prevents new token issuance

**Source**  
Section 67, Revocation: after revocation, “Application A can no longer... obtain new tokens.”

**Requirement**  
After the user revokes Application A, the authorisation system MUST NOT issue new access tokens or equivalent active authority to Application A under the revoked grant.

**Classification**  
Revocation effects; token issuance; compliance scenario.

**Notes**  
Refresh or renewal authority associated with the revoked grant must also cease to provide usable access.

---

## REM-04-784 — Revocation prevents new submissions

**Source**  
Section 67, Revocation: after revocation, “Application A can no longer... submit updates.”

**Requirement**  
After the user revokes Application A, the repository MUST reject new update submissions made under the revoked authority.

**Classification**  
Revocation enforcement; repository submissions; compliance scenario.

**Notes**  
The rule applies to future operations and does not invalidate canonical operations accepted before revocation.

---

## REM-04-785 — Revocation stops private event delivery

**Source**  
Section 67, Revocation: after revocation, “Application A can no longer... receive private events.”

**Requirement**  
After the user revokes Application A, private repository event delivery to Application A under the revoked authority MUST cease.

**Classification**  
Revocation enforcement; event subscriptions; compliance scenario.

**Notes**  
Public events may remain available only under an independent applicable public-access rule.

---

## REM-04-786 — Revocation preserves the created post

**Source**  
Section 67, Revocation: “The post remains in the repository.”

**Requirement**  
Revocation of Application A MUST NOT remove the post that was validly created under the grant.

**Classification**  
Record continuity; revocation semantics; compliance scenario.

**Notes**  
The post remains under repository and user authority and may later be accessed by another authorised application.

---

## REM-04-787 — Replacement application may receive post access

**Source**  
Section 67, Replacement: “Application B receives permission to read and update posts.”

**Requirement**  
The model MUST allow Application B to receive a valid Permission Grant to read and update the user’s existing posts independently of Application A.

**Classification**  
Application replacement; new grant; compliance scenario.

**Notes**  
Application B’s authority derives from its own grant, not from transfer of Application A’s token or installation state.

---

## REM-04-788 — Replacement application may edit records created through another application

**Source**  
Section 67, Replacement: “Application B opens and edits the post originally created through Application A.”

**Requirement**  
Application B MUST be able to open and edit the post originally created through Application A when Application B holds the required valid authority and the record schema permits the operation.

**Classification**  
Application interoperability; record continuity; compliance scenario.

**Notes**  
The originating application does not retain exclusive control over the record.

---

## REM-04-789 — Replacement must not require export or copying

**Source**  
Section 67, Replacement: “No export, copying or account recreation is required.”

**Requirement**  
Replacing Application A with Application B MUST NOT require the user to export and re-import, duplicate or otherwise copy the underlying repository records merely to continue using them.

**Classification**  
Application replaceability; repository continuity; anti-lock-in.

**Notes**  
Applications operate against the continuing repository state rather than owning separate canonical copies.

---

## REM-04-790 — Replacement must not require account recreation

**Source**  
Section 67, Replacement: “No export, copying or account recreation is required.”

**Requirement**  
Replacing Application A with Application B MUST NOT require recreation of the Relay Identity, repository account or underlying repository state.

**Classification**  
Identity continuity; application replaceability; anti-lock-in.

**Notes**  
Application replacement changes the service interface and delegated authority, not the user’s underlying digital continuity.

---

## REM-04-791 — Compliance requires preserved user authority

**Source**  
Section 67, conclusion: “If all these actions occur while preserving user authority and application replaceability, the implementation satisfies the basic Relay Application and Permission objective.”

**Requirement**  
The compliance scenario MUST be completed without transferring, weakening or bypassing the user’s underlying authority over the Relay Identity, Repository and records.

**Classification**  
User authority; end-to-end compliance; acceptance criterion.

**Notes**  
A technically functioning scenario does not satisfy the objective if the application becomes the effective owner or unavoidable controller of the user’s repository state.

---

## REM-04-792 — Compliance requires application replaceability

**Source**  
Section 67, conclusion: “If all these actions occur while preserving user authority and application replaceability, the implementation satisfies the basic Relay Application and Permission objective.”

**Requirement**  
The compliance scenario MUST preserve the user’s ability to replace one application with another without losing or recreating the underlying repository state.

**Classification**  
Application replaceability; end-to-end compliance; acceptance criterion.

**Notes**  
Replaceability is demonstrated when Application B can operate on the existing post using its own approved authority after Application A is revoked.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 66–67 of `design-notes/04-application-and-permission-model.md`.
- Sections 68 and later were excluded.
- The compliance scenario was treated as an end-to-end implementation test and was not expanded with behaviours absent from the source.

## Numbering verification

- First requirement: `REM-04-748`.
- Final requirement: `REM-04-792`.
- Requirement numbering continues directly from Part 13.
- Requirement identifiers are continuous, unique and ordered according to the source.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each of the 14 permission invariants was extracted as an independently traceable requirement or, where a single invariant contains multiple independently testable prohibitions, as separate requirements.
- Every compliance-scenario requirement is traceable to a stated request, approval, denial, repository action, manifest change, revocation effect, replacement action or conclusion.

## Normative-language verification

- Section 66’s “must always remain true” statement is preserved through `MUST` and `MUST NOT` invariant requirements.
- Section 67’s statement that a basic implementation “should pass” the test is preserved as a `SHOULD` at the scenario level.
- Individual behaviours stated as required outcomes within the scenario use normative language sufficient to make the test executable and auditable.

## Editorial verification

- Delegated authority remains distinct from identity ownership.
- Application attribution remains distinct from authorship and repository control.
- Read, retain, redistribute and model-training permissions remain separate.
- Create, delete and visibility-change permissions remain separate.
- Ordinary content authority remains separate from identity, key, recovery and migration authority.
- Revocation terminates future authority without deleting canonical records.
- Manifest changes do not silently expand existing grants.
- Application replacement preserves the continuing Relay Identity, Repository and records.

## REM-04 sequence closure

- Parts 1–14 collectively cover Sections 1–67 of the Application and Permission Model.
- The REM-04 requirement sequence begins at `REM-04-001` and concludes at `REM-04-792`.
- No source sections within the defined REM-04 extraction scope were skipped or duplicated.
