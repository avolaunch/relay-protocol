# REM-04 Part 13 — Application and Permission Requirement Extraction Matrix (Sections 61–65)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 61–65 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

61. Denial
62. Automatic policy enforcement
63. Inactive grants
64. Emergency revocation
65. Required v0.1 application operations

Requirement identifiers continue sequentially from Part 12, beginning with `REM-04-694`.

---

# 61. Denial

## REM-04-694 — Permission-request denial

**Source**  
Section 61: “A user may deny a request.”

**Requirement**  
A user MAY deny a Permission Request.

**Classification**  
Consent; user control; authorisation outcome.

**Notes**  
Denial is a valid terminal or interim outcome and must not be treated as an implementation error.

---

## REM-04-695 — Complete denial

**Source**  
Section 61, denial types: “complete”.

**Requirement**  
The authorisation model MUST support complete denial of a Permission Request.

**Classification**  
Consent; denial granularity.

**Notes**  
A complete denial rejects all requested authority.

---

## REM-04-696 — Partial denial

**Source**  
Section 61, denial types: “partial”.

**Requirement**  
The authorisation model MUST support partial denial of a Permission Request.

**Classification**  
Consent; granular approval; denial granularity.

**Notes**  
Partial denial may coexist with partial approval of other requested capabilities.

---

## REM-04-697 — Temporary denial

**Source**  
Section 61, denial types: “temporary”.

**Requirement**  
The authorisation model MUST support temporary denial of a Permission Request.

**Classification**  
Consent; temporal policy; denial granularity.

**Notes**  
A temporary denial does not necessarily prohibit a later renewed request.

---

## REM-04-698 — Policy-based denial

**Source**  
Section 61, denial types: “policy-based”.

**Requirement**  
The authorisation model MUST support denial based on standing user or organisational policy.

**Classification**  
Policy enforcement; consent; automated authorisation.

**Notes**  
The applicable policy may be evaluated automatically, but the resulting denial remains attributable to the governing authority or policy context.

---

## REM-04-699 — Minimise disclosure of private denial policy

**Source**  
Section 61: “The system should avoid revealing unnecessary private policy details to the application.”

**Requirement**  
The authorisation system SHOULD avoid disclosing unnecessary private policy details when returning a denial to an application.

**Classification**  
Privacy; information minimisation; denial handling.

**Notes**  
The application may need to know that permission was denied without learning the user’s broader trust rules, block lists or internal policy rationale.

---

## REM-04-700 — Generic denial response support

**Source**  
Section 61 example: return `permission_denied` rather than a detailed explanation of the user’s company-specific blocking policy.

**Requirement**  
The authorisation system SHOULD support a generic denial response where a more detailed reason would reveal unnecessary private policy information.

**Classification**  
Privacy; protocol response; denial handling.

**Notes**  
This does not prohibit more detailed explanations to the user or authorised administrators.

---

# 62. Automatic policy enforcement

## REM-04-701 — Standing authorisation policies

**Source**  
Section 62: “A user may define standing rules...”

**Requirement**  
A user MAY define standing rules that govern how Permission Requests are evaluated.

**Classification**  
Policy enforcement; user control; automation.

**Notes**  
Standing rules may prohibit, permit, require confirmation for or time-limit particular classes of authority.

---

## REM-04-702 — Policy prohibition of general model training

**Source**  
Section 62 example: “Never allow general model training.”

**Requirement**  
A standing policy MAY prohibit Permission Requests that include general model training.

**Classification**  
AI governance; policy enforcement; privacy.

**Notes**  
This is an illustrative policy capability rather than a universal default.

---

## REM-04-703 — Policy-based automatic approval of public-profile reading

**Source**  
Section 62 example: “Allow public-profile readers automatically.”

**Requirement**  
A standing policy MAY pre-authorise automatic approval of low-risk public-profile reading requests.

**Classification**  
Policy enforcement; automatic approval; low-risk access.

**Notes**  
Automatic approval remains subject to the source requirement that it be limited to low-risk, pre-authorised conditions.

---

## REM-04-704 — Policy-required confirmation for deletion

**Source**  
Section 62 example: “Require confirmation for deletion.”

**Requirement**  
A standing policy MAY require explicit confirmation before granting or exercising deletion authority.

**Classification**  
High-risk action; policy enforcement; user confirmation.

**Notes**  
The confirmation requirement may apply at grant time, operation time or both.

---

## REM-04-705 — Policy-based expiration of inactive grants

**Source**  
Section 62 example: “Expire inactive grants after 90 days.”

**Requirement**  
A standing policy MAY cause inactive grants to expire after a defined period.

**Classification**  
Grant lifecycle; policy enforcement; inactivity management.

**Notes**  
The exact period is policy-defined; 90 days is illustrative.

---

## REM-04-706 — Policy restriction on unverified applications

**Source**  
Section 62 example: “Block unverified applications from private records.”

**Requirement**  
A standing policy MAY prevent unverified applications from receiving access to private records.

**Classification**  
Trust policy; verification; private-data protection.

**Notes**  
Verification status must still be interpreted according to what was actually verified, not as a universal guarantee of trustworthiness.

---

## REM-04-707 — Authorisation-service policy evaluation

**Source**  
Section 62: “The authorisation service may evaluate requests against these policies.”

**Requirement**  
An authorisation service MAY evaluate Permission Requests against applicable standing policies.

**Classification**  
Automated authorisation; policy enforcement.

**Notes**  
The evaluation result must not grant authority beyond the policy and the underlying request.

---

## REM-04-708 — Automatic approval limited to low-risk conditions

**Source**  
Section 62: “Automatic approval should be limited to low-risk, pre-authorised conditions.”

**Requirement**  
Automatic approval SHOULD be limited to low-risk conditions that were explicitly pre-authorised by the user or governing authority.

**Classification**  
Risk control; automated authorisation; consent.

**Notes**  
High-authority, materially changed or otherwise sensitive requests should not be silently approved through broad automation.

---

# 63. Inactive grants

## REM-04-709 — Inactive-grant review flag

**Source**  
Section 63: “A grant that has not been used for a long period may be flagged for review...”

**Requirement**  
An inactive Permission Grant MAY be flagged for user or administrator review.

**Classification**  
Grant lifecycle; inactivity management; review.

**Notes**  
The source does not define a universal inactivity threshold.

---

## REM-04-710 — Automatic expiration under user policy

**Source**  
Section 63: an inactive grant may be “automatically expired according to user policy”.

**Requirement**  
An inactive Permission Grant MAY expire automatically where an applicable user policy requires expiration.

**Classification**  
Grant lifecycle; policy enforcement; expiration.

**Notes**  
Automatic expiration must be attributable to an existing policy rather than an undisclosed application decision.

---

## REM-04-711 — Restriction pending re-authentication

**Source**  
Section 63: an inactive grant may be “restricted until re-authentication”.

**Requirement**  
An inactive Permission Grant MAY be restricted until the user completes re-authentication.

**Classification**  
Authentication; inactivity management; risk control.

**Notes**  
Restriction may be narrower than full revocation or expiration.

---

## REM-04-712 — Inactive grant may remain unchanged

**Source**  
Section 63: an inactive grant may be “left unchanged”.

**Requirement**  
An inactive Permission Grant MAY remain unchanged where policy and risk controls permit.

**Classification**  
Grant lifecycle; policy discretion.

**Notes**  
The source allows multiple valid inactivity responses rather than mandating one universal outcome.

---

## REM-04-713 — User visibility of stale permissions

**Source**  
Section 63: “The user should be able to see stale permissions.”

**Requirement**  
The system SHOULD allow the user to identify stale or long-unused permissions.

**Classification**  
Transparency; user access history; grant management.

**Notes**  
Meaningful presentation should be preferred over opaque token-only information.

---

## REM-04-714 — Discourage permanent forgotten access

**Source**  
Section 63: “Relay should discourage permanent forgotten access.”

**Requirement**  
Relay implementations SHOULD discourage indefinite access that remains active but forgotten by the user.

**Classification**  
Least privilege; grant lifecycle; security recommendation.

**Notes**  
Review prompts, inactivity indicators, expiration policies and re-authentication are possible mechanisms.

---

# 64. Emergency revocation

## REM-04-715 — Emergency revocation capability

**Source**  
Section 64: “A user should be able to perform an emergency action such as: Revoke all applications.”

**Requirement**  
A user SHOULD be able to invoke an emergency revocation action affecting all applications.

**Classification**  
Emergency security; revocation; user control.

**Notes**  
The precise mechanism may vary, but it should provide rapid containment during compromise or loss scenarios.

---

## REM-04-716 — Emergency revocation after device theft

**Source**  
Section 64: emergency revocation may be necessary after “device theft”.

**Requirement**  
The emergency revocation mechanism SHOULD support containment following device theft.

**Classification**  
Emergency security; device compromise.

**Notes**  
Device-specific revocation may also be available, but the emergency action may be broader where the user cannot determine the exact affected authority.

---

## REM-04-717 — Emergency revocation during identity recovery

**Source**  
Section 64: emergency revocation may be necessary after “identity recovery”.

**Requirement**  
The emergency revocation mechanism SHOULD support use during or following identity recovery.

**Classification**  
Recovery; emergency security; revocation.

**Notes**  
Emergency revocation must remain distinct from terminating the Relay Identity itself.

---

## REM-04-718 — Emergency revocation after suspected compromise

**Source**  
Section 64: emergency revocation may be necessary after “suspected compromise”.

**Requirement**  
The emergency revocation mechanism SHOULD support rapid containment when compromise is suspected.

**Classification**  
Incident response; emergency security.

**Notes**  
The source does not require proof of compromise before emergency action is available.

---

## REM-04-719 — Emergency revocation after malicious application activity

**Source**  
Section 64: emergency revocation may be necessary after “malicious application activity”.

**Requirement**  
The emergency revocation mechanism SHOULD support containment of malicious application activity.

**Classification**  
Incident response; application security; revocation.

**Notes**  
Application suspension and ecosystem action may complement, but do not replace, user-controlled emergency revocation.

---

## REM-04-720 — Emergency revocation must not delete records

**Source**  
Section 64: “Emergency revocation should not delete repository records.”

**Requirement**  
Emergency revocation SHOULD NOT delete repository records.

**Classification**  
Revocation effects; record preservation; application replaceability.

**Notes**  
Authority termination is separate from deletion of user-controlled repository state.

---

## REM-04-721 — Emergency revocation must not terminate identity

**Source**  
Section 64: “Emergency revocation should not terminate the identity.”

**Requirement**  
Emergency revocation SHOULD NOT terminate the Relay Identity.

**Classification**  
Identity continuity; revocation effects.

**Notes**  
The emergency action targets delegated application authority rather than the user’s underlying identity continuity.

---

## REM-04-722 — Emergency revocation must not erase audit history

**Source**  
Section 64: “Emergency revocation should not erase audit history.”

**Requirement**  
Emergency revocation SHOULD NOT erase audit history.

**Classification**  
Auditability; incident response; evidence preservation.

**Notes**  
Audit history may be especially important for investigating the event that triggered emergency revocation.

---

# 65. Required v0.1 application operations

## REM-04-723 — Register Application Identity operation

**Source**  
Section 65 required operations: “Register Application Identity”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support registering an Application Identity.

**Classification**  
Required operation; application lifecycle.

**Notes**  
Registration must preserve the stable machine-readable identity requirements defined earlier in the source model.

---

## REM-04-724 — Resolve Application Manifest operation

**Source**  
Section 65 required operations: “Resolve Application Manifest”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support resolving an Application Manifest.

**Classification**  
Required operation; manifest discovery.

**Notes**  
Resolution should identify the current valid manifest relevant to the Application Identity.

---

## REM-04-725 — Verify Application Manifest operation

**Source**  
Section 65 required operations: “Verify Application Manifest”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support verification of an Application Manifest.

**Classification**  
Required operation; manifest integrity; application verification.

**Notes**  
Verification must be represented as specific verified facts rather than a universal guarantee of trustworthiness.

---

## REM-04-726 — Submit Permission Request operation

**Source**  
Section 65 required operations: “Submit Permission Request”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support submission of a Permission Request.

**Classification**  
Required operation; authorisation initiation.

**Notes**  
The request must contain the information required by Section 9.

---

## REM-04-727 — Display Permission Request operation

**Source**  
Section 65 required operations: “Display Permission Request”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support displaying a Permission Request to the user through an appropriate consent interface.

**Classification**  
Required operation; consent interface; transparency.

**Notes**  
The display must communicate the concrete consequences required by the consent-interface rules.

---

## REM-04-728 — Approve full request operation

**Source**  
Section 65 required operations: “Approve full request”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support approval of a complete Permission Request.

**Classification**  
Required operation; consent outcome.

**Notes**  
The resulting grant may be no broader than the approved request.

---

## REM-04-729 — Approve partial request operation

**Source**  
Section 65 required operations: “Approve partial request”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support partial approval of a Permission Request.

**Classification**  
Required operation; granular consent.

**Notes**  
Denied and approved scopes must remain distinguishable.

---

## REM-04-730 — Deny request operation

**Source**  
Section 65 required operations: “Deny request”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support denial of a Permission Request.

**Classification**  
Required operation; consent outcome.

**Notes**  
Denial handling should respect privacy-minimisation requirements from Section 61.

---

## REM-04-731 — Issue Permission Grant operation

**Source**  
Section 65 required operations: “Issue Permission Grant”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support issuing a Permission Grant after valid approval.

**Classification**  
Required operation; delegated authority.

**Notes**  
The grant must be explicit, limited, attributable, inspectable and revocable.

---

## REM-04-732 — Read Permission Grant operation

**Source**  
Section 65 required operations: “Read Permission Grant”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support reading or inspecting an existing Permission Grant.

**Classification**  
Required operation; transparency; grant management.

**Notes**  
Inspection should expose the grant’s current scope, purpose, duration and restrictions to authorised parties.

---

## REM-04-733 — Issue short-lived access token operation

**Source**  
Section 65 required operations: “Issue short-lived access token”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support issuing a short-lived access token bound to an approved grant.

**Classification**  
Required operation; token issuance; delegated access.

**Notes**  
The token must remain limited, time-bound, audience-bound and unsuitable as proof of identity ownership.

---

## REM-04-734 — Renew authorised access operation

**Source**  
Section 65 required operations: “Renew authorised access”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support renewal of access where continuing authority remains valid.

**Classification**  
Required operation; access renewal; grant lifecycle.

**Notes**  
Renewal must fail where refresh authority, the underlying grant or relevant policy is no longer valid.

---

## REM-04-735 — Validate access token operation

**Source**  
Section 65 required operations: “Validate access token”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support validation of an access token before authority is exercised.

**Classification**  
Required operation; token validation; access control.

**Notes**  
Validation should include integrity, expiry, audience and grant-boundary checks.

---

## REM-04-736 — Create delegated application key operation

**Source**  
Section 65 required operations: “Create delegated application key”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support creation of a delegated application key associated with a Permission Grant.

**Classification**  
Required operation; delegated key management.

**Notes**  
The delegated key must remain unable to expand its authority or perform operations outside the grant.

---

## REM-04-737 — List connected applications operation

**Source**  
Section 65 required operations: “List connected applications”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support listing applications currently or historically connected to the Relay Identity.

**Classification**  
Required operation; transparency; application management.

**Notes**  
The user-access-history rules determine the meaningful information that should accompany the list.

---

## REM-04-738 — Inspect application activity operation

**Source**  
Section 65 required operations: “Inspect application activity”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support inspection of application activity.

**Classification**  
Required operation; auditability; user transparency.

**Notes**  
Activity should be presented meaningfully rather than only through opaque token identifiers.

---

## REM-04-739 — Narrow Permission Grant operation

**Source**  
Section 65 required operations: “Narrow Permission Grant”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support narrowing an existing Permission Grant without requiring full revocation.

**Classification**  
Required operation; scope reduction; least privilege.

**Notes**  
Authority removed by the narrowed grant must become invalid while the audit trail is preserved.

---

## REM-04-740 — Revoke Permission Grant operation

**Source**  
Section 65 required operations: “Revoke Permission Grant”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support revocation of a Permission Grant.

**Classification**  
Required operation; revocation; user control.

**Notes**  
Revocation affects future authority and does not automatically erase canonical records or lawful retained copies.

---

## REM-04-741 — Revoke installation operation

**Source**  
Section 65 required operations: “Revoke installation”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support revocation of a specific application installation.

**Classification**  
Required operation; installation management; granular revocation.

**Notes**  
Installation revocation should not necessarily revoke the entire Application Identity where the model supports installation-level distinction.

---

## REM-04-742 — Revoke delegated key operation

**Source**  
Section 65 required operations: “Revoke delegated key”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support revocation of a delegated application key.

**Classification**  
Required operation; key revocation; delegated authority.

**Notes**  
Repositories must reject subsequent operations relying on the revoked key.

---

## REM-04-743 — Expire Permission Grant operation

**Source**  
Section 65 required operations: “Expire Permission Grant”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support expiration of a Permission Grant.

**Classification**  
Required operation; grant lifecycle; temporal authority.

**Notes**  
Expiration may occur at a defined time, after a defined duration or according to applicable policy.

---

## REM-04-744 — Require re-authorisation operation

**Source**  
Section 65 required operations: “Require re-authorisation”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support requiring re-authorisation when continuing use of existing authority is no longer valid or sufficient.

**Classification**  
Required operation; re-authorisation; material change control.

**Notes**  
Triggers include grant expiry, broader scopes, material manifest changes and relevant security events.

---

## REM-04-745 — Record Consent Receipt operation

**Source**  
Section 65 required operations: “Record Consent Receipt”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support recording a Consent Receipt.

**Classification**  
Required operation; consent evidence; transparency.

**Notes**  
The receipt should preserve what the user approved, denied and was shown at the time of approval.

---

## REM-04-746 — Record Audit Event operation

**Source**  
Section 65 required operations: “Record Audit Event”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support recording Audit Events for relevant authorisation activity.

**Classification**  
Required operation; auditability; accountability.

**Notes**  
Sensitive audit information may remain private while still being preserved for authorised inspection.

---

## REM-04-747 — Limited high-authority capability support in first reference implementation

**Source**  
Section 65: “High-authority capability grants may be limited in the first reference implementation.”

**Requirement**  
The first Relay v0.1 reference implementation MAY limit support for high-authority capability grants.

**Classification**  
Implementation scope; phased delivery; high-authority operations.

**Notes**  
This allowance does not permit ordinary application tokens to perform high-authority operations or weaken the protection requirements applying to any high-authority capability that is implemented.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 61–65 of `design-notes/04-application-and-permission-model.md`.
- Section 66 and later content was excluded.
- Examples were used to clarify intended capability and were not treated as exhaustive taxonomies unless the source explicitly required the listed v0.1 operations.

## Numbering verification

- First requirement: `REM-04-694`.
- Final requirement: `REM-04-747`.
- Requirement numbering continues directly from Part 12.
- Requirement identifiers are continuous, unique and ordered according to source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, bullet, example or required-operation entry.
- Section 65 operations were extracted individually because each is an independently testable compliance capability.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- Illustrative policy examples remain optional capabilities and were not converted into universal default policies.

## Editorial verification

- Denial responses preserve user-policy privacy.
- Automatic approval remains limited to low-risk, explicitly pre-authorised conditions.
- Inactive-grant handling remains policy-dependent rather than universally mandatory.
- Emergency revocation remains separate from repository deletion, identity termination and audit erasure.
- Required v0.1 operations remain bounded by the permission, token, revocation and high-authority rules defined earlier in the source model.
