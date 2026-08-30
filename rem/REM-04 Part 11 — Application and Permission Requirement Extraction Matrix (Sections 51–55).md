# REM-04 Part 11 — Application and Permission Requirement Extraction Matrix (Sections 51–55)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 51–55 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

51. Malicious or deceptive applications
52. Application portability
53. Application replacement
54. Permission portability during provider migration
55. Provider access

Requirement identifiers continue sequentially from Part 10, beginning with `REM-04-596`.

---

# 51. Malicious or deceptive applications

## REM-04-596 — No claim of eliminating malicious software

**Source**  
Section 51: “The protocol cannot eliminate malicious software.”

**Requirement**  
Relay implementations and documentation MUST NOT represent the protocol as capable of eliminating malicious or deceptive software.

**Classification**  
Security boundary; risk disclosure; protocol limitation.

**Notes**  
The protocol reduces exposure and limits authority, but cannot guarantee that every application is benign.

---

## REM-04-597 — Narrow grants as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “narrow grants”.

**Requirement**  
The Application and Permission Model MUST use narrowly bounded grants as a control for limiting damage caused by malicious, deceptive or compromised applications.

**Classification**  
Least privilege; security architecture; permission scope.

**Notes**  
A grant should expose only the minimum resources, actions, duration and purpose needed for the approved function.

---

## REM-04-598 — Signed manifests as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “signed manifests”.

**Requirement**  
Applications participating in the permission model MUST use signed Application Manifests so that manifest claims can be attributed to an authorised application authority.

**Classification**  
Application authenticity; manifest integrity; accountability.

**Notes**  
A signature establishes attribution and integrity of the manifest; it does not establish that the application is trustworthy.

---

## REM-04-599 — Verified callback locations as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “verified callback locations”.

**Requirement**  
Authorisation flows MUST restrict callbacks or redirects to verified locations associated with the Application Identity.

**Classification**  
Authorisation security; redirect validation; application verification.

**Notes**  
This reduces callback substitution, credential interception and redirection to infrastructure not controlled by the declared application.

---

## REM-04-600 — Explicit purpose declarations as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “explicit purpose declarations”.

**Requirement**  
Permission requests MUST make their intended purposes explicit where purpose declaration is required by the model.

**Classification**  
Purpose limitation; consent transparency; accountability.

**Notes**  
Purpose declarations enable informed approval, policy checks, audits and later comparison between approved and observed behaviour.

---

## REM-04-601 — Short-lived tokens as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “short-lived tokens”.

**Requirement**  
Implementations SHOULD use short-lived access tokens to reduce the period during which stolen, leaked or abused credentials remain useful.

**Classification**  
Credential security; token lifecycle; recommendation.

**Notes**  
Long-running authority may rely on separately revocable refresh mechanisms or renewed capabilities rather than permanently valid access tokens.

---

## REM-04-602 — Auditability as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “auditability”.

**Requirement**  
Application access and material permission activity SHOULD be auditable in accordance with the protocol’s audit-event model.

**Classification**  
Auditability; incident response; accountability.

**Notes**  
Auditability does not itself prevent misuse, but supports detection, investigation, user review and enforcement.

---

## REM-04-603 — Fast revocation as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “fast revocation”.

**Requirement**  
The permission system MUST support revocation becoming effective for future access as quickly as practical.

**Classification**  
Revocation; incident containment; security responsiveness.

**Notes**  
The requirement concerns termination of continuing authority and does not imply erasure of prior lawful disclosures or canonical records already created.

---

## REM-04-604 — Separation of high-authority operations as a damage-limitation control

**Source**  
Section 51: the protocol can reduce damage by requiring “separation of high-authority operations”.

**Requirement**  
High-authority operations MUST remain separated from ordinary application permissions and ordinary content-access tokens.

**Classification**  
Privilege separation; high-authority controls; security architecture.

**Notes**  
Examples include migration, recovery changes, key management, repository erasure and permission-management authority.

---

## REM-04-605 — Application reputation and verification layers

**Source**  
Section 51: the protocol can reduce damage through “application reputation and verification layers”.

**Requirement**  
Relay providers and ecosystem services MAY use application reputation and verification layers as additional decision inputs before granting or continuing access.

**Classification**  
Trust policy; application verification; ecosystem security.

**Notes**  
Reputation or verification must not be represented as a universal guarantee of trustworthiness.

---

## REM-04-606 — Pre-approval trust policies

**Source**  
Section 51: “Providers and users may apply trust policies before approving applications.”

**Requirement**  
Providers and users MAY apply trust policies before approving a Permission Request.

**Classification**  
Trust policy; consent control; application admission.

**Notes**  
Policies may consider verification status, controller identity, declared practices, reputation, security posture or other permitted criteria.

---

## REM-04-607 — Trust policy must not silently expand authority

**Source**  
Section 51, read together with the permission model’s requirement for explicit grants and trust-policy use before approval.

**Requirement**  
A favourable trust-policy result MUST NOT itself create or expand application authority beyond the explicit Permission Grant.

**Classification**  
Authority boundary; trust-policy limitation; consent integrity.

**Notes**  
Trust determines whether approval is acceptable; the grant determines what the application may actually do.

---

# 52. Application portability

## REM-04-608 — Infrastructure portability of an Application Identity

**Source**  
Section 52: “An application itself may change hosting providers or infrastructure while retaining the same Application Identity.”

**Requirement**  
An application MAY change hosting provider or infrastructure while retaining the same Application Identity.

**Classification**  
Application portability; identity continuity; infrastructure independence.

**Notes**  
Continuity is permitted only where the requirements in this section remain satisfied.

---

## REM-04-609 — Authorised manifest update for application portability

**Source**  
Section 52: application portability requires “an authorised manifest update”.

**Requirement**  
An infrastructure or hosting change that affects manifest information MUST be represented through an authorised Application Manifest update.

**Classification**  
Manifest lifecycle; application portability; authority verification.

**Notes**  
The update must be attributable to valid authority for the continuing Application Identity.

---

## REM-04-610 — Controller-authority continuity

**Source**  
Section 52: application portability requires “continuity of controller authority”.

**Requirement**  
Retention of the same Application Identity across an infrastructure move MUST require verifiable continuity of controller authority.

**Classification**  
Controller continuity; application identity; anti-takeover control.

**Notes**  
A server move must not permit an unrelated party to assume the Application Identity without an authorised controller transition.

---

## REM-04-611 — Updated service locations

**Source**  
Section 52: application portability requires “updated service locations”.

**Requirement**  
The current Application Manifest MUST be updated to identify service locations that changed as part of the application’s infrastructure move.

**Classification**  
Manifest accuracy; service discovery; application portability.

**Notes**  
Service locations may include domains, endpoints or other protocol-resolvable locations.

---

## REM-04-612 — Updated keys or callbacks

**Source**  
Section 52: application portability requires “updated keys or callbacks”.

**Requirement**  
Where an infrastructure move changes application keys or callback locations, the Application Manifest MUST be updated to identify the new authorised values.

**Classification**  
Key management; callback security; manifest lifecycle.

**Notes**  
Previously valid keys or callbacks should be retired or restricted according to the application’s transition and security policy.

---

## REM-04-613 — No silent permission expansion during application portability

**Source**  
Section 52: application portability requires “no silent expansion of permissions”.

**Requirement**  
An application infrastructure move MUST NOT silently expand the scopes, purposes, duration or other authority of existing Permission Grants.

**Classification**  
Consent integrity; permission continuity; application portability.

**Notes**  
Materially broader behaviour requires re-authorisation under the applicable rules.

---

## REM-04-614 — Server movement alone does not require a new Application Identity

**Source**  
Section 52: “Users should not be forced to approve an entirely new application merely because its servers moved.”

**Requirement**  
Users SHOULD NOT be required to approve an entirely new Application Identity solely because the application moved servers or hosting infrastructure.

**Classification**  
User experience; application continuity; recommendation.

**Notes**  
This recommendation applies only where identity continuity, controller authority and manifest integrity remain verifiable.

---

## REM-04-615 — Application portability does not bypass material-change review

**Source**  
Section 52, combined requirements for continuity and no silent permission expansion.

**Requirement**  
Application portability MUST NOT be used to bypass re-authorisation or review required by material changes to the controller, data practices, purposes or requested authority.

**Classification**  
Re-authorisation; manifest drift; portability limitation.

**Notes**  
Infrastructure continuity and behavioural continuity are separate questions.

---

# 53. Application replacement

## REM-04-616 — Support for application replacement

**Source**  
Section 53: “The model must allow a person to stop using Application A and begin using Application B.”

**Requirement**  
The Application and Permission Model MUST allow a person to stop using one application and begin using another.

**Classification**  
Application replaceability; user choice; interoperability.

**Notes**  
Replacement must not require surrendering the person’s underlying identity or repository state.

---

## REM-04-617 — Replacement application may receive profile-read authority

**Source**  
Section 53: Application B may receive permission to “read the same profile”.

**Requirement**  
A replacement application MAY receive permission to read the same profile records previously used by another application.

**Classification**  
Application replacement; read authority; repository continuity.

**Notes**  
The replacement application requires its own valid Permission Grant and does not inherit the previous application’s authority automatically.

---

## REM-04-618 — Replacement application may display the same posts

**Source**  
Section 53: Application B may receive permission to “display the same posts”.

**Requirement**  
A replacement application MAY receive permission to read and display the same repository posts used by the previous application.

**Classification**  
Content portability; application replacement; presentation independence.

**Notes**  
The canonical posts remain repository records rather than application-owned content.

---

## REM-04-619 — Replacement application may update the same records

**Source**  
Section 53: Application B may receive permission to “update the same records”.

**Requirement**  
A replacement application MAY receive permission to update existing logical records, subject to the same protocol, scope and authority rules that apply to any application.

**Classification**  
Write interoperability; application replacement; record continuity.

**Notes**  
The records retain their stable identifiers and version history when edited through the replacement application.

---

## REM-04-620 — Replacement application may interact with the same relationships

**Source**  
Section 53: Application B may receive permission to “interact with the same relationships”.

**Requirement**  
A replacement application MAY receive permission to interact with the same repository relationships where the user grants the required authority.

**Classification**  
Relationship portability; application replacement; interoperability.

**Notes**  
The relationships are repository state and must not be treated as belonging exclusively to the application that first presented them.

---

## REM-04-621 — No recreation of underlying repository state

**Source**  
Section 53: “The user must not need to recreate the underlying repository state.”

**Requirement**  
Replacing an application MUST NOT require the user to recreate underlying repository state that already exists in a portable protocol form.

**Classification**  
Repository continuity; application replaceability; portability.

**Notes**  
Existing identities, records, relationships, versions and other supported state should remain available to the replacement application through authorised access.

---

## REM-04-622 — Unsupported application-specific records may remain unsupported

**Source**  
Section 53: “Application-specific records may remain unsupported...”

**Requirement**  
A replacement application MAY decline to interpret or render application-specific record types that it does not support.

**Classification**  
Partial interoperability; application capability; schema support.

**Notes**  
Lack of rendering support does not permit damage, misrepresentation or deletion of valid records.

---

## REM-04-623 — Preservation of unsupported application-specific records

**Source**  
Section 53: application-specific records “must be preserved”.

**Requirement**  
Valid application-specific records MUST be preserved even when the replacement application does not support their schema or presentation.

**Classification**  
Unknown-schema preservation; application replacement; data integrity.

**Notes**  
Preservation supports later use by another compatible application and prevents lock-in through deliberate data loss.

---

## REM-04-624 — No automatic transfer of grants between applications

**Source**  
Section 53 states that Application B “may receive permission”, within a model based on application-specific grants.

**Requirement**  
A replacement application MUST receive its own explicit Permission Grant and MUST NOT automatically inherit the previous application’s grant.

**Classification**  
Consent integrity; application identity; authority separation.

**Notes**  
Repository state is portable between applications; application authority is not silently transferable.

---

# 54. Permission portability during provider migration

## REM-04-625 — Conditional grant continuity during repository migration

**Source**  
Section 54: “When a repository moves providers, existing grants may continue only if...”

**Requirement**  
An existing Permission Grant MAY continue after repository-provider migration only when all applicable continuation conditions are satisfied.

**Classification**  
Provider migration; grant continuity; conditional authority.

**Notes**  
Grant continuation is not automatic merely because repository records and identity remain portable.

---

## REM-04-626 — Provider-independent grant requirement

**Source**  
Section 54: an existing grant may continue only if “the grant is provider-independent”.

**Requirement**  
A grant MUST be provider-independent to remain valid across repository-provider migration.

**Classification**  
Grant portability; provider independence; migration.

**Notes**  
A grant explicitly bound to the former provider cannot simply be treated as valid at the new provider.

---

## REM-04-627 — New-provider capability support requirement

**Source**  
Section 54: an existing grant may continue only if “the new provider supports the relevant capability”.

**Requirement**  
A grant MAY continue after migration only where the new provider supports the capabilities required by that grant.

**Classification**  
Capability compatibility; provider migration; grant validation.

**Notes**  
Unsupported capabilities must not be simulated, silently broadened or misrepresented as available.

---

## REM-04-628 — Secure discovery of the new provider

**Source**  
Section 54: an existing grant may continue only if “the application can securely discover the new provider”.

**Requirement**  
The application MUST be able to securely discover and verify the new authoritative provider before exercising a continuing grant after migration.

**Classification**  
Provider discovery; migration security; authority routing.

**Notes**  
The discovery mechanism must resist redirection to an unauthorised or impersonating service.

---

## REM-04-629 — Grant must remain unrevoked

**Source**  
Section 54: an existing grant may continue only if “the user has not revoked the grant”.

**Requirement**  
A revoked grant MUST NOT regain validity merely because the repository migrates to a new provider.

**Classification**  
Revocation persistence; provider migration; authority continuity.

**Notes**  
Migration must preserve relevant revocation state.

---

## REM-04-630 — Migration-policy approval of grant continuation

**Source**  
Section 54: an existing grant may continue only if “migration policy allows continuation”.

**Requirement**  
A grant MAY continue after provider migration only where the applicable migration policy permits continuation.

**Classification**  
Migration policy; grant continuity; provider transition.

**Notes**  
Migration policy may require suspension, token reissuance, user review or re-authorisation for selected grants.

---

## REM-04-631 — No copying of provider-specific tokens

**Source**  
Section 54: “Provider-specific tokens should not simply be copied.”

**Requirement**  
Provider-specific tokens SHOULD NOT be copied directly from the former provider to the new provider as the mechanism for continuing access.

**Classification**  
Token security; provider migration; recommendation.

**Notes**  
Such tokens may be audience-bound, issuer-bound, cryptographically provider-specific or otherwise unsuitable for reuse.

---

## REM-04-632 — New token issuance based on a continuing grant

**Source**  
Section 54: “The new provider may issue new tokens based on the continuing grant.”

**Requirement**  
The new provider MAY issue new access tokens based on a continuing valid Permission Grant.

**Classification**  
Token issuance; provider migration; grant continuity.

**Notes**  
The new provider must validate the grant, revocation state, capability support and migration policy before issuing authority.

---

## REM-04-633 — Re-authorisation of high-risk grants after migration

**Source**  
Section 54: “High-risk grants may require re-authorisation after migration.”

**Requirement**  
Migration policy MAY require high-risk grants to be re-authorised after repository-provider migration.

**Classification**  
High-risk authority; re-authorisation; migration security.

**Notes**  
This may include grants involving private exports, key management, recovery, permission management or other high-authority capabilities.

---

## REM-04-634 — Migration must preserve grant constraints

**Source**  
Section 54, combined continuation conditions and new-token issuance based on the continuing grant.

**Requirement**  
Any grant continued after migration MUST retain its approved scope, purpose, duration, restrictions and revocation status unless the user explicitly authorises a change.

**Classification**  
Consent integrity; grant portability; migration.

**Notes**  
Migration cannot be used as a mechanism for silently widening application authority.

---

# 55. Provider access

## REM-04-635 — Provider access must be defined

**Source**  
Section 55: “A Relay Provider’s own access must also be defined.”

**Requirement**  
The Relay Provider’s own access to a hosted repository MUST be explicitly defined.

**Classification**  
Provider authority; hosting governance; access control.

**Notes**  
Provider operational authority is not unlimited merely because the provider hosts the repository.

---

## REM-04-636 — Provider authority to store records

**Source**  
Section 55: hosting may require operational authority to “store records”.

**Requirement**  
A hosting agreement and protocol role MAY authorise a Relay Provider to store repository records.

**Classification**  
Provider operations; storage authority; hosting.

**Notes**  
Storage authority must remain limited to the provider’s defined operational role.

---

## REM-04-637 — Provider authority to serve records

**Source**  
Section 55: hosting may require operational authority to “serve records”.

**Requirement**  
A hosting agreement and protocol role MAY authorise a Relay Provider to serve repository records to authorised requesters.

**Classification**  
Provider operations; record delivery; access enforcement.

**Notes**  
The provider must apply the record’s visibility, audience and other access rules when serving content.

---

## REM-04-638 — Provider authority to validate commits

**Source**  
Section 55: hosting may require operational authority to “validate commits”.

**Requirement**  
A Relay Provider MAY validate repository commits as part of its protocol and hosting role.

**Classification**  
Repository validation; provider operations; integrity.

**Notes**  
Validation authority does not permit the provider to create unauthorised commits on behalf of the user.

---

## REM-04-639 — Provider authority to deliver events

**Source**  
Section 55: hosting may require operational authority to “deliver events”.

**Requirement**  
A Relay Provider MAY deliver repository events where authorised by protocol rules, subscriptions and applicable access controls.

**Classification**  
Event delivery; provider operations; subscriptions.

**Notes**  
Event delivery must stop or change where the relevant subscription or authority is revoked.

---

## REM-04-640 — Provider authority to create backups

**Source**  
Section 55: hosting may require operational authority to “create backups”.

**Requirement**  
A Relay Provider MAY create backups as part of its documented repository-hosting role.

**Classification**  
Backup; provider operations; resilience.

**Notes**  
Backup handling must remain subject to the hosting agreement, security commitments, retention rules and applicable law.

---

## REM-04-641 — Provider authority to scan for malware

**Source**  
Section 55: hosting may require operational authority to “scan for malware”.

**Requirement**  
A Relay Provider MAY scan hosted content for malware where this activity is documented and limited to the provider’s operational and security role.

**Classification**  
Security operations; malware scanning; provider authority.

**Notes**  
Malware scanning does not create unrestricted permission to analyse content for unrelated purposes.

---

## REM-04-642 — Provider authority to enforce legal restrictions

**Source**  
Section 55: hosting may require operational authority to “enforce legal restrictions”.

**Requirement**  
A Relay Provider MAY restrict or withhold hosted content where required to enforce applicable legal or regulatory restrictions.

**Classification**  
Legal compliance; provider operations; content restriction.

**Notes**  
Provider removal or withholding must not be misrepresented as necessarily changing canonical repository history where the underlying model distinguishes those states.

---

## REM-04-643 — Hosting access is not an unrestricted application grant

**Source**  
Section 55: “The provider must not treat hosting access as an unrestricted application grant.”

**Requirement**  
A Relay Provider MUST NOT treat its repository-hosting access as an unrestricted application Permission Grant.

**Classification**  
Authority separation; provider limitation; least privilege.

**Notes**  
Operational hosting access and optional application access are distinct authority categories.

---

## REM-04-644 — Separate documentation of provider operational authority

**Source**  
Section 55: provider operational authority “should be documented separately”.

**Requirement**  
Provider operational authority SHOULD be documented separately from application Permission Grants.

**Classification**  
Provider governance; transparency; recommendation.

**Notes**  
Separate documentation allows users and auditors to distinguish infrastructure access from application behaviour.

---

## REM-04-645 — Provider authority limited to hosting agreement

**Source**  
Section 55: provider operational authority should be “limited to the hosting agreement and protocol role”.

**Requirement**  
A Relay Provider’s operational authority MUST remain limited to the authority justified by the hosting agreement.

**Classification**  
Contractual limitation; provider authority; least privilege.

**Notes**  
The hosting agreement must not be treated as blanket permission for unrelated application, commercial or analytical use.

---

## REM-04-646 — Provider authority limited to protocol role

**Source**  
Section 55: provider operational authority should be “limited to the hosting agreement and protocol role”.

**Requirement**  
A Relay Provider’s operational authority MUST remain limited to its defined protocol role.

**Classification**  
Protocol-role limitation; provider authority; separation of concerns.

**Notes**  
Actions outside that role require a separate lawful and protocol-valid basis of authority.

---

## REM-04-647 — Separate authority for optional provider applications

**Source**  
Section 55 distinguishes provider operational authority from an unrestricted application grant.

**Requirement**  
Where a provider also operates an optional user-facing application, that application MUST rely on its own Application Identity and applicable Permission Grant rather than on the provider’s hosting authority.

**Classification**  
First-party application separation; provider governance; permission model.

**Notes**  
This requirement follows directly from the source’s separation between hosting access and application authority and is elaborated further in the next source section.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 51–55 of `design-notes/04-application-and-permission-model.md`.
- Section 56 and later content was excluded as an independent extraction source.
- Section 56 is mentioned only in a note where it confirms the authority separation already imposed by Section 55.

## Numbering verification

- First requirement: `REM-04-596`.
- Final requirement: `REM-04-647`.
- Requirement numbering continues directly from Part 10.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, bullet or necessary decomposition of a compound statement.
- Security controls listed in Section 51 were separated because each represents an independently testable mechanism.
- Provider operational functions in Section 55 were separated because each requires a distinct authority and governance assessment.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or options.
- Descriptive continuation conditions in Section 54 were expressed as mandatory conditions only where the source states that grants may continue “only if” those conditions are satisfied.

## Editorial verification

- Application reputation and verification do not replace explicit permission grants.
- Application portability does not permit silent expansion of authority.
- Repository state is portable between applications, while application-specific grants are not automatically transferable.
- Provider migration preserves revocation and grant restrictions and does not permit provider-specific token copying as the default continuity mechanism.
- Provider operational authority remains separate from application authority and is limited to the hosting agreement and protocol role.
