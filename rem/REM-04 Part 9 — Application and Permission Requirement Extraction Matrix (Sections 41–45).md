# REM-04 Part 9 — Application and Permission Requirement Extraction Matrix (Sections 41–45)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 41–45 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

41. Revocation effects
42. Records created by revoked applications
43. Scope reduction
44. Re-authorisation
45. Manifest drift

Requirement identifiers continue sequentially from Part 8, beginning with `REM-04-495`.

---

# 41. Revocation effects

## REM-04-495 — No new access tokens after revocation

**Source**  
Section 41: “After revocation: new access tokens must not be issued.”

**Requirement**  
After a Permission Grant is revoked, the authorisation system MUST NOT issue any new access token under that revoked grant.

**Classification**  
Revocation enforcement; token lifecycle; access control.

**Notes**  
This applies regardless of whether previously issued tokens have already expired or remain technically unexpired.

---

## REM-04-496 — Refresh authority failure after revocation

**Source**  
Section 41: “After revocation: refresh authority must fail.”

**Requirement**  
After a Permission Grant is revoked, every refresh token, renewable session or equivalent refresh authority derived from that grant MUST fail.

**Classification**  
Revocation enforcement; refresh authority; session lifecycle.

**Notes**  
The implementation must not allow a revoked grant to regain effective access by exchanging old refresh authority for new access tokens.

---

## REM-04-497 — Delegated-key invalidation after revocation

**Source**  
Section 41: “After revocation: delegated keys must become invalid.”

**Requirement**  
After a Permission Grant is revoked, every delegated application key associated with that grant MUST become invalid for future operations.

**Classification**  
Delegated authority; key lifecycle; revocation enforcement.

**Notes**  
A repository must evaluate the continuing validity of the underlying grant even where a delegated signature is cryptographically valid.

---

## REM-04-498 — Background-subscription termination

**Source**  
Section 41: “After revocation: background subscriptions must stop.”

**Requirement**  
After revocation, every background subscription authorised by the revoked grant MUST stop.

**Classification**  
Background access; revocation enforcement; event subscriptions.

**Notes**  
This includes subscriptions used for synchronisation, indexing, monitoring or other continuous processing.

---

## REM-04-499 — Rejection of new repository submissions

**Source**  
Section 41: “After revocation: new repository submissions must be rejected.”

**Requirement**  
A Relay Repository MUST reject every new submission that relies on authority from a revoked Permission Grant.

**Classification**  
Repository validation; revocation enforcement; write authority.

**Notes**  
A valid application signature or delegated-key signature is insufficient where the underlying grant has been revoked.

---

## REM-04-500 — Cessation of event delivery

**Source**  
Section 41: “After revocation: event delivery must cease.”

**Requirement**  
After revocation, event delivery performed under the revoked Permission Grant MUST cease.

**Classification**  
Event delivery; background access; revocation enforcement.

**Notes**  
This applies to future repository events and does not require erasure of events already lawfully delivered.

---

## REM-04-501 — Retained-data handling after revocation

**Source**  
Section 41: “After revocation: cached or retained data must be handled according to the approved retention declaration.”

**Requirement**  
After revocation, an application MUST handle cached or retained data in accordance with the retention declaration approved in the applicable Permission Grant.

**Classification**  
Retention; post-revocation obligations; compliance.

**Notes**  
Revocation terminates future authority but does not replace or nullify the previously approved retention terms.

---

## REM-04-502 — Canonical records are not automatically erased

**Source**  
Section 41: “Revocation does not automatically erase: canonical records already created.”

**Requirement**  
Revocation of an application or Permission Grant MUST NOT automatically erase canonical records already created under valid authority.

**Classification**  
Record continuity; revocation boundaries; application replaceability.

**Notes**  
Deletion of those records is a separate repository operation requiring its own authority and policy basis.

---

## REM-04-503 — Lawfully disclosed copies are not automatically erased

**Source**  
Section 41: “Revocation does not automatically erase: copies lawfully disclosed.”

**Requirement**  
Revocation MUST NOT be represented as automatically erasing copies that were lawfully disclosed before revocation.

**Classification**  
Disclosure; revocation limitations; user transparency.

**Notes**  
Separate contractual, legal or retention obligations may still require deletion or restriction of such copies.

---

## REM-04-504 — Audit history survives revocation

**Source**  
Section 41: “Revocation does not automatically erase: audit history.”

**Requirement**  
Revocation MUST NOT automatically erase audit history relating to the application, grant or actions performed under that grant.

**Classification**  
Auditability; historical accountability; revocation boundaries.

**Notes**  
Audit retention remains subject to applicable privacy, minimisation and legal requirements.

---

## REM-04-505 — Legally required retention survives revocation

**Source**  
Section 41: “Revocation does not automatically erase: data another party is legally required to retain.”

**Requirement**  
Revocation MUST NOT be represented as overriding a lawful obligation imposed on another party to retain data.

**Classification**  
Legal retention; revocation limitations; compliance.

**Notes**  
The source does not define which laws apply. Implementations must avoid promising deletion where legal retention duties may continue.

---

## REM-04-506 — Revocation affects future authority

**Source**  
Section 41, combined revocation effects and non-erasure statements.

**Requirement**  
Revocation MUST terminate future authority under the affected grant without being treated as retroactive invalidation of actions that were validly authorised before revocation.

**Classification**  
Authority lifecycle; revocation semantics; historical integrity.

**Notes**  
This requirement captures the source’s distinction between stopping future access and preserving valid historical state.

---

# 42. Records created by revoked applications

## REM-04-507 — Revocation does not delete application-created records

**Source**  
Section 42: “Revoking an application must not delete records merely because the application originally created them.”

**Requirement**  
Revoking an application MUST NOT delete a record solely because that application originally created or submitted it.

**Classification**  
Record ownership; application replaceability; revocation boundaries.

**Notes**  
The canonical record remains governed by repository authority and the authorising Relay Identity rather than by the originating application.

---

## REM-04-508 — Posts remain in the user’s repository

**Source**  
Section 42 example: “a post remains in the user’s repository.”

**Requirement**  
A canonical post created through a subsequently revoked application MUST remain in the user’s repository unless separately deleted through an authorised record operation.

**Classification**  
Record continuity; content persistence; application replaceability.

**Notes**  
The example illustrates the general rule that application revocation and record deletion are separate operations.

---

## REM-04-509 — Projects remain portable

**Source**  
Section 42 example: “a project remains portable.”

**Requirement**  
A project record created through a subsequently revoked application MUST remain portable according to the Relay Record Model.

**Classification**  
Portability; application replaceability; record continuity.

**Notes**  
Revocation must not trap the project inside the application that created it.

---

## REM-04-510 — Comments remain under user authority

**Source**  
Section 42 example: “a comment remains under the user’s authority.”

**Requirement**  
A comment created through a subsequently revoked application MUST remain under the authority of the authorising Relay Identity.

**Classification**  
Record authority; authorship; application independence.

**Notes**  
The originating application does not gain continuing ownership or control over the comment.

---

## REM-04-511 — Imported archives remain available

**Source**  
Section 42 example: “an imported archive remains available.”

**Requirement**  
An archive validly imported through an application MUST remain available after that application is revoked, subject to repository policy and any separate deletion decision.

**Classification**  
Import continuity; repository state; application replaceability.

**Notes**  
The application’s loss of authority does not reverse a completed, valid import.

---

## REM-04-512 — Separate user-directed deletion

**Source**  
Section 42: “The user may separately choose to delete those records.”

**Requirement**  
The user MAY separately authorise deletion of records previously created through a revoked application.

**Classification**  
User control; record deletion; authority separation.

**Notes**  
The deletion decision must be independent of the application-revocation decision.

---

## REM-04-513 — Record continuity is required for application replaceability

**Source**  
Section 42: “This is essential to application replaceability.”

**Requirement**  
The permission and record models MUST preserve canonical records independently of the continued availability or authorisation of the application that created them.

**Classification**  
Application replaceability; continuity; architectural principle.

**Notes**  
Without this rule, revoking or replacing an application would risk destroying the user’s repository state.

---

# 43. Scope reduction

## REM-04-514 — Partial grant narrowing

**Source**  
Section 43: “A user may narrow a grant without fully revoking it.”

**Requirement**  
A user MUST be able to narrow a Permission Grant without being required to revoke the grant in full.

**Classification**  
Grant lifecycle; granular control; least privilege.

**Notes**  
The revised grant may preserve still-approved capabilities while removing others.

---

## REM-04-515 — Scope reduction may remove actions

**Source**  
Section 43 example: reducing “Read, create, update and delete posts” to “Read and create posts.”

**Requirement**  
A scope-reduction operation MAY remove one or more previously granted actions while retaining other approved actions.

**Classification**  
Action scope; grant modification; granular control.

**Notes**  
The example is illustrative and does not limit scope reduction to action-level changes.

---

## REM-04-516 — Revised grant supersedes previous grant

**Source**  
Section 43: “A revised grant should: supersede the previous grant.”

**Requirement**  
A revised, narrowed Permission Grant SHOULD supersede the previous grant it replaces.

**Classification**  
Grant versioning; supersession; recommendation.

**Notes**  
Supersession should leave no ambiguity as to which grant defines current authority.

---

## REM-04-517 — Removed authority becomes invalid

**Source**  
Section 43: “A revised grant should: invalidate authority no longer included.”

**Requirement**  
A scope reduction SHOULD invalidate every capability, token, delegated key or other authority no longer included in the revised grant.

**Classification**  
Grant enforcement; scope reduction; revocation semantics.

**Notes**  
Implementations must not allow removed authority to remain effective through stale tokens or cached grant state.

---

## REM-04-518 — Scope-reduction audit trail

**Source**  
Section 43: “A revised grant should: preserve an audit trail.”

**Requirement**  
A scope-reduction operation SHOULD preserve an audit trail of the previous grant, the revised grant and the authority removed.

**Classification**  
Auditability; grant lifecycle; accountability.

**Notes**  
The audit trail supports later reconstruction of what authority existed at a particular time.

---

## REM-04-519 — Avoid unnecessary reconnection

**Source**  
Section 43: “A revised grant should: avoid forcing unnecessary reconnection.”

**Requirement**  
A scope-reduction mechanism SHOULD avoid forcing the application to reconnect or repeat the full authorisation flow where the remaining authority can safely continue.

**Classification**  
User experience; grant continuity; recommendation.

**Notes**  
This does not permit stale or excessive authority to survive for convenience.

---

## REM-04-520 — Reduced grant defines current maximum authority

**Source**  
Section 43, combined scope-reduction requirements.

**Requirement**  
After a grant is narrowed, the revised grant MUST define the application’s maximum current authority.

**Classification**  
Current authority; grant lifecycle; enforcement.

**Notes**  
Earlier broader grants must not remain independently exercisable after effective supersession.

---

# 44. Re-authorisation

## REM-04-521 — Re-authorisation after grant expiration

**Source**  
Section 44: “An application must request re-authorisation when: the existing grant expires.”

**Requirement**  
An application MUST request re-authorisation after its existing Permission Grant expires before continuing any operation that requires that authority.

**Classification**  
Grant expiration; re-authorisation; access control.

**Notes**  
Expired authority must not be silently renewed or treated as still valid.

---

## REM-04-522 — Re-authorisation for broader scopes

**Source**  
Section 44: “An application must request re-authorisation when: it requests broader scopes.”

**Requirement**  
An application MUST request re-authorisation before exercising any scope broader than the currently approved grant.

**Classification**  
Scope expansion; consent; least privilege.

**Notes**  
Existing approval applies only to the previously authorised scope.

---

## REM-04-523 — Re-authorisation after controller change

**Source**  
Section 44: “An application must request re-authorisation when: its controller changes.”

**Requirement**  
An application MUST request re-authorisation when the responsible application controller changes.

**Classification**  
Controller identity; material change; re-authorisation.

**Notes**  
A controller change may alter who is accountable for handling access and data.

---

## REM-04-524 — Re-authorisation after material retention change

**Source**  
Section 44: “An application must request re-authorisation when: its retention policy materially changes.”

**Requirement**  
An application MUST request re-authorisation before relying on a materially changed data-retention policy.

**Classification**  
Retention; material change; re-authorisation.

**Notes**  
A materially broader or longer retention practice cannot inherit approval from an earlier, narrower declaration.

---

## REM-04-525 — Re-authorisation after AI-usage change

**Source**  
Section 44: “An application must request re-authorisation when: its AI usage changes.”

**Requirement**  
An application MUST request re-authorisation when its AI use changes from the activity previously approved.

**Classification**  
AI processing; consent; material change.

**Notes**  
Examples may include adding training, embedding, human review or an external model provider.

---

## REM-04-526 — Re-authorisation before adding onward sharing

**Source**  
Section 44: “An application must request re-authorisation when: it adds onward sharing.”

**Requirement**  
An application MUST request re-authorisation before adding onward sharing not covered by the current grant.

**Classification**  
Third-party disclosure; consent; scope expansion.

**Notes**  
Approval for direct application access does not imply approval for partner or processor distribution.

---

## REM-04-527 — Re-authorisation for materially different manifest

**Source**  
Section 44: “An application must request re-authorisation when: its manifest is materially different.”

**Requirement**  
An application MUST request re-authorisation when its current Application Manifest is materially different from the manifest version under which consent was granted.

**Classification**  
Manifest versioning; material change; re-authorisation.

**Notes**  
Section 45 requires the protocol to define which manifest changes are material.

---

## REM-04-528 — Re-authorisation after authority-invalidating security event

**Source**  
Section 44: “An application must request re-authorisation when: a security event invalidates existing authority.”

**Requirement**  
An application MUST request re-authorisation when a security event invalidates its existing authority.

**Classification**  
Security incident; authority lifecycle; re-authorisation.

**Notes**  
The affected prior grant or credentials must not be silently reused after the security event.

---

## REM-04-529 — No silent reliance on old approval

**Source**  
Section 44: “An application may not silently rely on an old approval for materially new behaviour.”

**Requirement**  
An application MUST NOT silently rely on an earlier approval to justify materially new behaviour.

**Classification**  
Consent integrity; material change; application conduct.

**Notes**  
The user must be given a new opportunity to review and approve the changed behaviour.

---

## REM-04-530 — Re-authorisation precedes materially new behaviour

**Source**  
Section 44, combined triggers and prohibition on old approval.

**Requirement**  
Where re-authorisation is required, the application MUST obtain the new grant before performing the materially changed behaviour.

**Classification**  
Authorisation sequence; consent; enforcement.

**Notes**  
Disclosure after the fact does not satisfy the requirement.

---

# 45. Manifest drift

## REM-04-531 — Compare approved and current manifest versions

**Source**  
Section 45: “A Relay Provider should compare the approved Application Manifest version with the current manifest.”

**Requirement**  
A Relay Provider SHOULD compare the Application Manifest version approved by the user with the application’s current valid manifest.

**Classification**  
Manifest drift; provider validation; recommendation.

**Notes**  
The comparison enables detection of material changes that may require restricted access or re-authorisation.

---

## REM-04-532 — Pause access after material manifest change

**Source**  
Section 45: “If the current version introduces material changes, the provider may: pause access.”

**Requirement**  
Where material manifest drift is detected, a Relay Provider MAY pause the application’s access.

**Classification**  
Provider response; manifest drift; risk control.

**Notes**  
Pausing access is one permitted response and is not mandated in every case.

---

## REM-04-533 — Restrict access to previously approved behaviour

**Source**  
Section 45: “If the current version introduces material changes, the provider may: restrict access to previously approved behaviour.”

**Requirement**  
Where material manifest drift is detected, a Relay Provider MAY restrict the application to behaviour covered by the previously approved manifest and grant.

**Classification**  
Least privilege; manifest drift; provider enforcement.

**Notes**  
The application must not gain the benefit of materially expanded behaviour merely because its manifest changed.

---

## REM-04-534 — Require user review after material change

**Source**  
Section 45: “If the current version introduces material changes, the provider may: require user review.”

**Requirement**  
Where material manifest drift is detected, a Relay Provider MAY require the user to review the changed manifest and permission implications.

**Classification**  
User consent; manifest drift; re-authorisation.

**Notes**  
User review may result in approval, narrowing, denial or revocation.

---

## REM-04-535 — Revoke grant in severe manifest-drift cases

**Source**  
Section 45: “If the current version introduces material changes, the provider may: revoke the grant in severe cases.”

**Requirement**  
Where material manifest drift creates a severe risk, a Relay Provider MAY revoke the affected Permission Grant.

**Classification**  
Provider security action; revocation; manifest drift.

**Notes**  
The source leaves severity criteria open for later definition or policy.

---

## REM-04-536 — Non-material changes need not trigger full re-authorisation

**Source**  
Section 45: “Minor non-material changes need not trigger full re-authorisation.”

**Requirement**  
A minor, non-material Application Manifest change NEED NOT trigger a full re-authorisation flow.

**Classification**  
Manifest versioning; proportionality; re-authorisation.

**Notes**  
The implementation must still preserve manifest version history and distinguish non-material changes from material ones.

---

## REM-04-537 — Define material manifest changes

**Source**  
Section 45: “The protocol should define which manifest changes are material.”

**Requirement**  
The Relay protocol SHOULD define which categories of Application Manifest change are material for re-authorisation and provider-enforcement purposes.

**Classification**  
Protocol governance; manifest versioning; recommendation.

**Notes**  
Likely examples elsewhere in the source include controller, retention, AI-use, callback, domain and permission-catalogue changes, but this section does not establish a final exhaustive taxonomy.

---

## REM-04-538 — Materiality determines response severity

**Source**  
Section 45, distinction between material and minor non-material changes.

**Requirement**  
Provider responses to manifest drift SHOULD be proportionate to the materiality and risk of the detected change.

**Classification**  
Risk-based enforcement; proportionality; manifest drift.

**Notes**  
The source permits a range from no full re-authorisation for minor changes through to revocation in severe cases.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 41–45 of `design-notes/04-application-and-permission-model.md`.
- Section 40 was used only as the immediately preceding context for numbering and was not re-extracted.
- Section 46 and later content was excluded.

## Numbering verification

- First requirement: `REM-04-495`.
- Final requirement: `REM-04-538`.
- Requirement numbering continues directly from Part 8.
- Requirement identifiers are continuous, unique and ordered by source section.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit sentence, bullet, example or necessary decomposition of a compound source statement.
- Each revocation effect was extracted independently because each is separately enforceable and testable.
- Each re-authorisation trigger was extracted independently because each represents a distinct material-change condition.

## Normative-language verification

- Source “must” and “must not” statements are represented using `MUST` and `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- Statements that something “need not” occur were retained as non-requirement permissions rather than converted into prohibitions.

## Editorial verification

- Revocation terminates future authority but is not represented as retroactive erasure.
- Canonical records remain independent of the application that created them.
- Scope reduction is distinct from full revocation and from re-authorisation.
- Re-authorisation is required before materially changed behaviour occurs.
- Manifest drift is treated as a comparison and risk-control process rather than automatic revocation in every case.
- Explanatory notes do not introduce new protocol obligations beyond the source.
