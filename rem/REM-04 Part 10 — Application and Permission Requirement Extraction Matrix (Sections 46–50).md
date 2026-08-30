# REM-04 Part 10 — Application and Permission Requirement Extraction Matrix (Sections 46–50)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 46–50 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

46. Audit events
47. User access history
48. Application activity attribution
49. Application suspension
50. Application key compromise

Requirement identifiers continue sequentially from Part 9, beginning with `REM-04-539`.

---

# 46. Audit events

## REM-04-539 — Authorisation audit-event production

**Source**  
Section 46: “The authorisation system should produce audit events...”

**Requirement**  
The authorisation system SHOULD produce structured audit events for material permission, token, application and security actions.

**Classification**  
Auditability; accountability; recommendation.

**Notes**  
The source uses “should”, making this a recommended v0.1 behaviour rather than an unconditional validity rule.

---

## REM-04-540 — Permission-request audit event

**Source**  
Section 46, audit-event list: “permission requested”.

**Requirement**  
The authorisation system SHOULD record an audit event when an application submits a permission request.

**Classification**  
Auditability; permission lifecycle; recommendation.

**Notes**  
The event should identify the requesting application and the request context without exposing unnecessary sensitive content.

---

## REM-04-541 — Permission-grant audit event

**Source**  
Section 46, audit-event list: “permission granted”.

**Requirement**  
The authorisation system SHOULD record an audit event when a Permission Grant is issued.

**Classification**  
Auditability; consent; grant lifecycle; recommendation.

**Notes**  
The event should reference the resulting grant and the approved authority.

---

## REM-04-542 — Permission-denial audit event

**Source**  
Section 46, audit-event list: “permission denied”.

**Requirement**  
The authorisation system SHOULD record an audit event when a permission request is denied.

**Classification**  
Auditability; consent; recommendation.

**Notes**  
The event need not reveal private denial reasons where disclosure would create risk.

---

## REM-04-543 — Token-issuance audit event

**Source**  
Section 46, audit-event list: “token issued”.

**Requirement**  
The authorisation system SHOULD record an audit event when an access token, capability token or equivalent authority token is issued.

**Classification**  
Auditability; token lifecycle; recommendation.

**Notes**  
The audit record should identify the authority represented by the token without exposing the token secret itself.

---

## REM-04-544 — High-risk-action audit event

**Source**  
Section 46, audit-event list: “high-risk action performed”.

**Requirement**  
The authorisation system SHOULD record an audit event when a high-risk or high-authority action is performed.

**Classification**  
Security monitoring; high-authority operations; recommendation.

**Notes**  
Examples may include migration, private export, key rotation, recovery changes or repository erasure.

---

## REM-04-545 — Grant-narrowing audit event

**Source**  
Section 46, audit-event list: “grant narrowed”.

**Requirement**  
The authorisation system SHOULD record an audit event when the scope or capability of a Permission Grant is reduced.

**Classification**  
Auditability; scope management; recommendation.

**Notes**  
The audit trail should allow later comparison between the previous and revised authority.

---

## REM-04-546 — Grant-renewal audit event

**Source**  
Section 46, audit-event list: “grant renewed”.

**Requirement**  
The authorisation system SHOULD record an audit event when a Permission Grant is renewed.

**Classification**  
Auditability; grant lifecycle; recommendation.

**Notes**  
Renewal should remain distinguishable from creation of a materially broader grant.

---

## REM-04-547 — Grant-revocation audit event

**Source**  
Section 46, audit-event list: “grant revoked”.

**Requirement**  
The authorisation system SHOULD record an audit event when a Permission Grant is revoked.

**Classification**  
Auditability; revocation; recommendation.

**Notes**  
The audit event should reference the revoked grant and effective revocation time.

---

## REM-04-548 — Manifest-change audit event

**Source**  
Section 46, audit-event list: “application manifest changed”.

**Requirement**  
The authorisation system SHOULD record an audit event when an Application Manifest changes.

**Classification**  
Auditability; manifest lifecycle; recommendation.

**Notes**  
The event should identify the relevant manifest version and whether the change was treated as material.

---

## REM-04-549 — Security-incident-report audit event

**Source**  
Section 46, audit-event list: “application security incident reported”.

**Requirement**  
The authorisation system SHOULD record an audit event when an application security incident is reported.

**Classification**  
Security monitoring; incident response; recommendation.

**Notes**  
Sensitive incident details may require restricted visibility.

---

## REM-04-550 — Rejected-unauthorised-attempt audit event

**Source**  
Section 46, audit-event list: “unauthorised attempt rejected”.

**Requirement**  
The authorisation system SHOULD record an audit event when an unauthorised attempt is rejected.

**Classification**  
Security monitoring; enforcement; recommendation.

**Notes**  
Implementations should avoid placing secrets or exploitable request details into user-visible audit records.

---

## REM-04-551 — Audit-event time attribution

**Source**  
Section 46, audit-event fields: “time”.

**Requirement**  
Each audit event SHOULD identify the time at which the audited action or result occurred.

**Classification**  
Audit metadata; temporal traceability; recommendation.

**Notes**  
The timestamp format is not finalised in this section.

---

## REM-04-552 — Audit-event application attribution

**Source**  
Section 46, audit-event fields: “application”.

**Requirement**  
Each audit event SHOULD identify the Application Identity associated with the action where applicable.

**Classification**  
Audit metadata; application attribution; recommendation.

**Notes**  
Application attribution does not establish authorship or ownership of affected records.

---

## REM-04-553 — Audit-event grant reference

**Source**  
Section 46, audit-event fields: “grant”.

**Requirement**  
Each audit event SHOULD identify or reference the Permission Grant under which the action occurred, where applicable.

**Classification**  
Audit metadata; authority traceability; recommendation.

**Notes**  
Events concerning denied requests or pre-grant activity may instead reference the permission request.

---

## REM-04-554 — Audit-event resource identification

**Source**  
Section 46, audit-event fields: “resource”.

**Requirement**  
Each audit event SHOULD identify the resource or resource scope affected by the action, where applicable.

**Classification**  
Audit metadata; resource traceability; recommendation.

**Notes**  
Sensitive resource identifiers may be generalised or access-controlled where necessary.

---

## REM-04-555 — Audit-event action identification

**Source**  
Section 46, audit-event fields: “action”.

**Requirement**  
Each audit event SHOULD identify the action attempted or performed.

**Classification**  
Audit metadata; operation traceability; recommendation.

**Notes**  
The action should use a stable machine-readable value where practical.

---

## REM-04-556 — Audit-event result identification

**Source**  
Section 46, audit-event fields: “result”.

**Requirement**  
Each audit event SHOULD identify the result of the audited action.

**Classification**  
Audit metadata; outcome traceability; recommendation.

**Notes**  
Results may include success, denial, failure, revocation or another defined outcome.

---

## REM-04-557 — Installation attribution where relevant

**Source**  
Section 46, audit-event fields: “installation where relevant”.

**Requirement**  
An audit event SHOULD identify the specific application installation where that distinction is relevant and available.

**Classification**  
Audit metadata; installation attribution; recommendation.

**Notes**  
Installation attribution supports granular investigation and revocation without redefining the stable Application Identity.

---

## REM-04-558 — Private handling of sensitive audit information

**Source**  
Section 46: “Sensitive audit information may remain private.”

**Requirement**  
Sensitive audit information MAY be restricted from public disclosure and retained in a private audit context.

**Classification**  
Privacy; audit data; access control.

**Notes**  
Privacy restrictions must not destroy the underlying auditability required for authorised inspection or security investigation.

---

# 47. User access history

## REM-04-559 — User inspection of connected applications

**Source**  
Section 47: “A person should be able to inspect: connected applications...”

**Requirement**  
A person SHOULD be able to inspect the applications currently or previously connected to their Relay Identity or Repository.

**Classification**  
Transparency; user control; recommendation.

**Notes**  
The history may distinguish active, suspended and revoked applications.

---

## REM-04-560 — User inspection of current grants

**Source**  
Section 47, inspection list: “current grants”.

**Requirement**  
A person SHOULD be able to inspect their current Permission Grants.

**Classification**  
Transparency; permission management; recommendation.

**Notes**  
The view should expose meaningful scope, purpose, duration and restrictions rather than only grant identifiers.

---

## REM-04-561 — User inspection of recently used permissions

**Source**  
Section 47, inspection list: “recently used permissions”.

**Requirement**  
A person SHOULD be able to inspect which permissions were used recently.

**Classification**  
Transparency; access history; recommendation.

**Notes**  
This enables a person to distinguish dormant grants from actively exercised authority.

---

## REM-04-562 — User inspection of last access time

**Source**  
Section 47, inspection list: “last access time”.

**Requirement**  
A person SHOULD be able to inspect the most recent known access time for an application, grant or relevant installation.

**Classification**  
Transparency; temporal access history; recommendation.

**Notes**  
The interface should identify the context to which the timestamp applies.

---

## REM-04-563 — User inspection of records created or changed

**Source**  
Section 47, inspection list: “records created or changed”.

**Requirement**  
A person SHOULD be able to inspect which records an application created or changed.

**Classification**  
Transparency; record provenance; recommendation.

**Notes**  
This must not imply that the application owns or authored the record.

---

## REM-04-564 — User inspection of exports

**Source**  
Section 47, inspection list: “exports performed”.

**Requirement**  
A person SHOULD be able to inspect repository or data exports performed through an application or grant.

**Classification**  
Transparency; data movement; recommendation.

**Notes**  
Private-record exports may warrant heightened visibility and security review.

---

## REM-04-565 — User inspection of active installations

**Source**  
Section 47, inspection list: “active installations”.

**Requirement**  
A person SHOULD be able to inspect active application installations associated with their grants.

**Classification**  
Transparency; installation management; recommendation.

**Notes**  
This supports installation-specific revocation where implemented.

---

## REM-04-566 — User inspection of background subscriptions

**Source**  
Section 47, inspection list: “background subscriptions”.

**Requirement**  
A person SHOULD be able to inspect active background subscriptions or continuous-access processes.

**Classification**  
Transparency; background authority; recommendation.

**Notes**  
The interface should make clear that these processes may act while the person is absent.

---

## REM-04-567 — User inspection of revoked applications

**Source**  
Section 47, inspection list: “revoked applications”.

**Requirement**  
A person SHOULD be able to inspect applications whose authority has been revoked.

**Classification**  
Transparency; revocation history; recommendation.

**Notes**  
Revoked applications should remain visible in history even though their future authority has ended.

---

## REM-04-568 — Meaningful human-readable activity history

**Source**  
Section 47: “The system should show meaningful information... rather than only displaying token identifiers.”

**Requirement**  
The access-history interface SHOULD present activity in meaningful human-readable terms rather than exposing only token, grant or internal identifier values.

**Classification**  
User experience; transparency; recommendation.

**Notes**  
Human-readable presentation should remain backed by machine-readable identifiers for verification and support.

---

# 48. Application activity attribution

## REM-04-569 — Retention of application attribution

**Source**  
Section 48: “Repository changes made through an application should retain attribution.”

**Requirement**  
Repository changes made through an application SHOULD retain attribution identifying how the operation entered the repository.

**Classification**  
Provenance; auditability; recommendation.

**Notes**  
This attribution is operational provenance, not a transfer of authorship, ownership or repository authority.

---

## REM-04-570 — Authorising-identity attribution

**Source**  
Section 48 example: `"authorisedBy": "rid:relay:alice"`.

**Requirement**  
Application-mediated repository changes SHOULD identify the Relay Identity that authorised the operation.

**Classification**  
Authority attribution; provenance; recommendation.

**Notes**  
The authorising identity remains distinct from the submitting application.

---

## REM-04-571 — Submitting-application attribution

**Source**  
Section 48 example: `"submittedBy": "rid:app:writing-client"`.

**Requirement**  
Application-mediated repository changes SHOULD identify the Application Identity that submitted the operation.

**Classification**  
Application attribution; provenance; recommendation.

**Notes**  
Submission attribution does not make the application the author or owner.

---

## REM-04-572 — Grant attribution

**Source**  
Section 48 example: `"grant": "grant_01JX8K"`.

**Requirement**  
Application-mediated repository changes SHOULD identify or reference the Permission Grant under which the operation was authorised.

**Classification**  
Authority traceability; provenance; recommendation.

**Notes**  
The repository must still validate that the grant was valid and sufficient at the time of acceptance.

---

## REM-04-573 — Installation attribution

**Source**  
Section 48 example: `"installation": "install_72A"`.

**Requirement**  
Application-mediated repository changes SHOULD identify the specific installation where that distinction is available and relevant.

**Classification**  
Installation attribution; provenance; recommendation.

**Notes**  
Installation attribution supports investigation and granular revocation.

---

## REM-04-574 — Attribution does not establish application authorship

**Source**  
Section 48: “This does not make the application the author or owner.”

**Requirement**  
Application activity attribution MUST NOT be interpreted as establishing the application as the author of the affected record.

**Classification**  
Authorship separation; application independence.

**Notes**  
Authorship and authorisation must be determined from the applicable record and authority metadata.

---

## REM-04-575 — Attribution does not establish application ownership

**Source**  
Section 48: “This does not make the application the author or owner.”

**Requirement**  
Application activity attribution MUST NOT be interpreted as giving the application ownership or control of the affected record.

**Classification**  
Ownership separation; application independence.

**Notes**  
The record remains under repository authority and the applicable authorising identity.

---

## REM-04-576 — Attribution records repository-entry path

**Source**  
Section 48: “It records how the operation entered the repository.”

**Requirement**  
Application activity attribution MUST represent the submission path by which the operation entered the repository.

**Classification**  
Operational provenance; repository history.

**Notes**  
This requirement describes the meaning of the attribution, not a claim about the application’s semantic contribution to the content.

---

# 49. Application suspension

## REM-04-577 — Application suspension capability

**Source**  
Section 49: “A Relay Provider or ecosystem authority may mark an application as suspended...”

**Requirement**  
A Relay Provider or recognised ecosystem authority MAY mark an application as suspended.

**Classification**  
Security response; ecosystem governance.

**Notes**  
The source does not define a universal suspension authority or appeals process in this section.

---

## REM-04-578 — Suspension for compromised keys

**Source**  
Section 49, suspension reasons: “compromised keys”.

**Requirement**  
An application MAY be suspended where its application keys are compromised.

**Classification**  
Security response; key compromise.

**Notes**  
Suspension can reduce ongoing risk while key revocation and manifest updates are processed.

---

## REM-04-579 — Suspension for malware

**Source**  
Section 49, suspension reasons: “malware”.

**Requirement**  
An application MAY be suspended where it contains, distributes or operates as malware.

**Classification**  
Security response; malicious software.

**Notes**  
The applicable authority must rely on evidence and policy outside the scope of this section.

---

## REM-04-580 — Suspension for fraud

**Source**  
Section 49, suspension reasons: “fraud”.

**Requirement**  
An application MAY be suspended because of fraudulent conduct.

**Classification**  
Security response; fraud prevention.

**Notes**  
Suspension does not determine final legal liability.

---

## REM-04-581 — Suspension for manifest deception

**Source**  
Section 49, suspension reasons: “manifest deception”.

**Requirement**  
An application MAY be suspended where its Application Manifest is materially deceptive or misrepresents its identity, practices or requested authority.

**Classification**  
Manifest integrity; security response.

**Notes**  
This is distinct from an ordinary non-material manifest error.

---

## REM-04-582 — Suspension for repeated permission abuse

**Source**  
Section 49, suspension reasons: “repeated permission abuse”.

**Requirement**  
An application MAY be suspended where it repeatedly abuses granted permissions or attempts operations outside granted authority.

**Classification**  
Permission enforcement; security response.

**Notes**  
Audit events can support evidence of repeated abuse.

---

## REM-04-583 — Suspension at controller request

**Source**  
Section 49, suspension reasons: “controller request”.

**Requirement**  
An application MAY be suspended at the request of its authorised application controller.

**Classification**  
Application lifecycle; controller authority.

**Notes**  
The request must be authenticated as originating from valid controller authority.

---

## REM-04-584 — Suspension for legal restriction

**Source**  
Section 49, suspension reasons: “legal restriction”.

**Requirement**  
An application MAY be suspended where required or justified by an applicable legal restriction.

**Classification**  
Legal compliance; application suspension.

**Notes**  
The protocol does not determine the validity or jurisdictional scope of the legal restriction.

---

## REM-04-585 — Suspension may prevent new grants

**Source**  
Section 49, suspension effects: “new grants”.

**Requirement**  
Application suspension MAY prevent issuance of new Permission Grants to the suspended application.

**Classification**  
Suspension effect; permission lifecycle.

**Notes**  
Existing grants may require separate restriction, pause or revocation treatment.

---

## REM-04-586 — Suspension may prevent token renewal

**Source**  
Section 49, suspension effects: “token renewal”.

**Requirement**  
Application suspension MAY prevent renewal of access tokens, refresh authority or equivalent ongoing access.

**Classification**  
Suspension effect; token lifecycle.

**Notes**  
Providers may also invalidate active authority according to security policy.

---

## REM-04-587 — Suspension may prevent repository submissions

**Source**  
Section 49, suspension effects: “repository submissions”.

**Requirement**  
Application suspension MAY cause repositories to reject new submissions from the suspended application.

**Classification**  
Suspension effect; repository enforcement.

**Notes**  
The rejection must not alter the status of already accepted canonical records merely because of application suspension.

---

## REM-04-588 — Suspension may prevent event delivery

**Source**  
Section 49, suspension effects: “event delivery”.

**Requirement**  
Application suspension MAY stop event delivery or background subscriptions to the suspended application.

**Classification**  
Suspension effect; background access.

**Notes**  
Stopping delivery does not erase events or records already accepted into repository history.

---

## REM-04-589 — Suspension must not delete user records

**Source**  
Section 49: “The application’s suspension must not delete the user’s records.”

**Requirement**  
Suspending an application MUST NOT delete records under the user’s repository authority merely because the application created, submitted or previously accessed them.

**Classification**  
Application replaceability; record persistence; ownership separation.

**Notes**  
The user may separately authorise deletion under the Record Model.

---

# 50. Application key compromise

## REM-04-590 — Manifest update after key compromise

**Source**  
Section 50: “the application controller should publish a manifest update”.

**Requirement**  
Following compromise of an application key, the application controller SHOULD publish an updated Application Manifest reflecting the changed key state.

**Classification**  
Incident response; manifest lifecycle; recommendation.

**Notes**  
The updated manifest should provide verifiable replacement or revocation information.

---

## REM-04-591 — Revocation of affected application keys

**Source**  
Section 50: “affected keys should be revoked”.

**Requirement**  
Application keys affected by compromise SHOULD be revoked.

**Classification**  
Key management; incident response; recommendation.

**Notes**  
Revocation should occur as quickly as practical to limit unauthorised use.

---

## REM-04-592 — Rejection of requests signed by compromised keys

**Source**  
Section 50: “providers should reject new requests signed by compromised keys”.

**Requirement**  
Relay Providers SHOULD reject new permission requests, token requests or repository operations signed by known compromised application keys.

**Classification**  
Signature validation; incident response; recommendation.

**Notes**  
Historical operations validly accepted before compromise discovery are not automatically invalidated by this requirement.

---

## REM-04-593 — Re-authorisation after application key compromise

**Source**  
Section 50: “affected grants may require re-authorisation”.

**Requirement**  
Permission Grants affected by an application key compromise MAY require user re-authorisation.

**Classification**  
Grant lifecycle; incident response.

**Notes**  
The need for re-authorisation depends on the compromised key’s role and the ability to establish secure application continuity.

---

## REM-04-594 — User visibility of suspicious activity

**Source**  
Section 50: “suspicious activity should be visible to users”.

**Requirement**  
Suspicious activity associated with an application key compromise SHOULD be made visible to affected users in a meaningful and safe form.

**Classification**  
Security transparency; incident response; recommendation.

**Notes**  
Disclosure may generalise sensitive technical details where full publication would create further risk.

---

## REM-04-595 — Application key compromise does not automatically compromise root identity authority

**Source**  
Section 50: “A key compromise affecting the application must not automatically compromise the user’s root identity authority.”

**Requirement**  
Compromise of an application key MUST NOT, by itself, be treated as compromise of the user’s root Relay Identity authority.

**Classification**  
Authority separation; key hierarchy; security isolation.

**Notes**  
This depends on application keys and grants remaining cryptographically and operationally subordinate to the user’s root identity authority.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 46–50 of `design-notes/04-application-and-permission-model.md`.
- Section 45 content was used only to establish the starting boundary; Section 51 and later content was excluded.
- Examples were used to clarify required attribution and audit semantics without being promoted into final mandatory serialisation syntax.

## Numbering verification

- First requirement: `REM-04-539`.
- Final requirement: `REM-04-595`.
- Numbering continues directly from Part 9.
- Requirement identifiers are continuous, unique and ordered according to source-section sequence.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each listed audit event, inspection capability, attribution field, suspension reason, suspension effect and key-compromise response was evaluated as an independently testable statement.
- Optional and recommended source language was preserved as `MAY` and `SHOULD` rather than strengthened to unconditional `MUST` requirements.

## Editorial verification

- Auditability is preserved without treating application submission as authorship or ownership.
- User access history is expressed as meaningful inspectability rather than exposure of internal identifiers alone.
- Application suspension is separated from record deletion and from final legal determinations.
- Key compromise responses are separated into manifest, key, provider, grant and user-notification obligations.
- Compromise of subordinate application authority is not conflated with compromise of the user’s root identity authority.
