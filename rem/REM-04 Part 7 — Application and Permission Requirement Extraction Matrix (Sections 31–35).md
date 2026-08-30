# REM-04 Part 7 — Application and Permission Requirement Extraction Matrix (Sections 31–35)

## Document status

**Canonical editorial extraction**

This document extracts application and permission requirements from Sections 31–35 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

31. Short-lived and long-lived access
32. Capability token
33. Delegated application key
34. Application installations
35. Background access

Requirement identifiers continue sequentially from Part 6, beginning with `REM-04-391`.

---

# 31. Short-lived and long-lived access

## REM-04-391 — Preference for short-lived access tokens

**Source**  
Section 31: “Relay should prefer short-lived access tokens.”

**Requirement**  
Relay implementations SHOULD prefer short-lived access tokens over unnecessarily long-lived access tokens.

**Classification**  
Token security; least privilege; recommendation.

**Notes**  
Short-lived tokens reduce the period during which a stolen or leaked token can be used.

---

## REM-04-392 — Long-running access through refresh tokens

**Source**  
Section 31: “Long-running access may use: refresh tokens...”

**Requirement**  
An implementation MAY support long-running access through refresh tokens.

**Classification**  
Session continuity; token lifecycle.

**Notes**  
Use of a refresh token does not remove the requirement that the underlying authority remain valid and revocable.

---

## REM-04-393 — Long-running access through renewable capability sessions

**Source**  
Section 31: “Long-running access may use... renewable capability sessions...”

**Requirement**  
An implementation MAY support long-running access through renewable capability sessions.

**Classification**  
Capability lifecycle; session continuity.

**Notes**  
Renewal should remain constrained by the original grant and current repository policy.

---

## REM-04-394 — Long-running access through delegated keys

**Source**  
Section 31: “Long-running access may use... delegated keys...”

**Requirement**  
An implementation MAY support long-running access through delegated application keys.

**Classification**  
Delegated authority; cryptographic access.

**Notes**  
Section 33 defines limits that must apply to delegated keys.

---

## REM-04-395 — Long-running access through re-authorisation

**Source**  
Section 31: “Long-running access may use... re-authorisation.”

**Requirement**  
An implementation MAY require periodic or event-triggered re-authorisation for continued long-running access.

**Classification**  
Consent renewal; authority lifecycle.

**Notes**  
Re-authorisation can be used when policy, risk, scope or application circumstances have materially changed.

---

## REM-04-396 — Independent revocability of refresh authority

**Source**  
Section 31: “Refresh authority must be revocable independently of already expired access tokens.”

**Requirement**  
Refresh authority MUST be revocable independently of access tokens that have already expired.

**Classification**  
Revocation; token lifecycle; security.

**Notes**  
Revoking refresh authority prevents issuance of future access tokens even though previously issued access tokens may already be unusable due to expiration.

---

## REM-04-397 — Fresh authentication for high-authority actions

**Source**  
Section 31: “High-authority actions should require fresh authentication rather than relying only on a long-lived background session.”

**Requirement**  
High-authority actions SHOULD require fresh authentication and SHOULD NOT rely solely on a long-lived background session.

**Classification**  
Step-up authentication; high-risk operations; recommendation.

**Notes**  
High-authority actions include operations such as migration, key management, recovery management and permission administration.

---

# 32. Capability token

## REM-04-398 — Capability-based access support

**Source**  
Section 32: “Relay may support capability-based access in addition to conventional scopes.”

**Requirement**  
Relay implementations MAY support capability-based access in addition to conventional scope-based access.

**Classification**  
Authorisation model; capability security; extensibility.

**Notes**  
Capability-based access complements rather than necessarily replaces conventional scopes.

---

## REM-04-399 — Capability token authority target

**Source**  
Section 32: “A capability token grants authority over a specific object or operation.”

**Requirement**  
A capability token MUST grant authority over a specifically identified object, operation or both.

**Classification**  
Capability scope; least privilege.

**Notes**  
A capability token should not imply broad account-level authority unless such breadth is explicitly encoded and authorised.

---

## REM-04-400 — Capability token object specificity

**Source**  
Section 32 example: “May update post_123 until 14:00”.

**Requirement**  
A capability token MAY restrict authority to a specific record or other protocol object.

**Classification**  
Object-level scope; capability restriction.

**Notes**  
The example is illustrative rather than a fixed token syntax.

---

## REM-04-401 — Capability token operation specificity

**Source**  
Section 32 example: “May update post_123 until 14:00”.

**Requirement**  
A capability token MAY restrict authority to a specific operation.

**Classification**  
Action scope; capability restriction.

**Notes**  
Authority to perform one operation must not silently imply authority to perform related operations.

---

## REM-04-402 — Capability token temporal restriction

**Source**  
Section 32 example: “May update post_123 until 14:00”.

**Requirement**  
A capability token MAY include a defined expiration time or other temporal boundary.

**Classification**  
Duration; capability lifecycle.

**Notes**  
Time-limited authority is more precise than indefinite authority where the intended task is temporary.

---

## REM-04-403 — Preference for precise capability authority

**Source**  
Section 32: the specific capability example “is more precise than: May update all posts indefinitely.”

**Requirement**  
Where practical, implementations SHOULD prefer capability authority that is limited by object, operation and duration over broad indefinite authority.

**Classification**  
Least privilege; authorisation precision; recommendation.

**Notes**  
This requirement reflects the source’s comparison between a narrowly bounded capability and broad indefinite permission.

---

## REM-04-404 — Capability tokens for collaborative editing

**Source**  
Section 32: “Capability tokens may be useful for: collaborative editing...”

**Requirement**  
Capability tokens MAY be used to authorise bounded collaborative-editing operations.

**Classification**  
Use case; collaboration; capability access.

**Notes**  
The capability should identify the relevant object, permitted action and applicable duration or conditions.

---

## REM-04-405 — Capability tokens for temporary sharing

**Source**  
Section 32: “Capability tokens may be useful for... temporary sharing...”

**Requirement**  
Capability tokens MAY be used to authorise temporary sharing of a record or resource.

**Classification**  
Use case; temporary access; sharing.

**Notes**  
Temporary sharing should not be treated as permanent audience membership unless separately authorised.

---

## REM-04-406 — Capability tokens for one-time publication

**Source**  
Section 32: “Capability tokens may be useful for... one-time publication...”

**Requirement**  
Capability tokens MAY be used to authorise one-time publication operations.

**Classification**  
Use case; one-time authority; publication.

**Notes**  
The capability should become unusable after successful exercise or another defined invalidation event.

---

## REM-04-407 — Capability tokens for restricted-record access

**Source**  
Section 32: “Capability tokens may be useful for... restricted record access...”

**Requirement**  
Capability tokens MAY be used to authorise access to specifically identified restricted records.

**Classification**  
Use case; restricted access; access control.

**Notes**  
Possession and validation of the capability must not imply access to unrelated restricted records.

---

## REM-04-408 — Capability tokens for delegated workflow steps

**Source**  
Section 32: “Capability tokens may be useful for... delegated workflow steps.”

**Requirement**  
Capability tokens MAY be used to authorise a bounded delegated step within a larger workflow.

**Classification**  
Use case; workflow delegation; capability access.

**Notes**  
The delegated step should not grant authority over the entire workflow unless explicitly authorised.

---

# 33. Delegated application key

## REM-04-409 — Delegated key association with a grant

**Source**  
Section 33: “An application may receive a delegated key associated with a Permission Grant.”

**Requirement**  
An application MAY receive a delegated key only where that key is associated with an identifiable Permission Grant.

**Classification**  
Delegated authority; key management; traceability.

**Notes**  
The key’s authority derives from the grant and must not exist as independent, unlimited authority.

---

## REM-04-410 — Delegated signing of repository submissions

**Source**  
Section 33: “The key may sign repository submissions within the grant’s limits.”

**Requirement**  
A delegated application key MAY sign repository submissions only within the limits of its associated Permission Grant.

**Classification**  
Cryptographic authority; repository submission; scope enforcement.

**Notes**  
A valid signature does not establish valid authority where the submitted operation exceeds the grant.

---

## REM-04-411 — Prohibition on identity alteration

**Source**  
Section 33: “A delegated key must not be able to: alter the Relay Identity...”

**Requirement**  
A delegated application key MUST NOT be capable of altering the Relay Identity.

**Classification**  
Identity protection; delegated-key restriction.

**Notes**  
Identity-level control remains outside ordinary application delegation unless a separate high-authority mechanism explicitly provides it.

---

## REM-04-412 — Prohibition on self-expansion of permissions

**Source**  
Section 33: “A delegated key must not be able to... expand its own permissions...”

**Requirement**  
A delegated application key MUST NOT be capable of expanding its own permissions.

**Classification**  
Privilege escalation prevention; delegated-key restriction.

**Notes**  
Changes to permission scope require valid external authorisation from the appropriate authority.

---

## REM-04-413 — Prohibition on recovery-authority changes

**Source**  
Section 33: “A delegated key must not be able to... change recovery authority...”

**Requirement**  
A delegated application key MUST NOT be capable of changing recovery authority.

**Classification**  
Recovery security; delegated-key restriction.

**Notes**  
Recovery control is a high-authority function and must remain outside ordinary delegated application access.

---

## REM-04-414 — Prohibition on repository migration

**Source**  
Section 33: “A delegated key must not be able to... migrate the repository...”

**Requirement**  
A delegated application key MUST NOT be capable of migrating the repository.

**Classification**  
Migration security; delegated-key restriction.

**Notes**  
Repository migration requires distinct high-authority approval.

---

## REM-04-415 — Prohibition on out-of-grant operations

**Source**  
Section 33: “A delegated key must not be able to... create valid operations outside the grant.”

**Requirement**  
A delegated application key MUST NOT create a valid repository operation outside the limits of its associated Permission Grant.

**Classification**  
Scope enforcement; delegated authority; repository validation.

**Notes**  
Repositories must reject operations that are correctly signed but not authorised by the current grant.

---

## REM-04-416 — Verification of delegated signature

**Source**  
Section 33: “The repository must verify both: the delegated signature...”

**Requirement**  
The repository MUST verify the delegated key’s signature before accepting a delegated submission.

**Classification**  
Signature validation; repository security.

**Notes**  
Signature verification confirms use of the delegated key but does not alone confirm continuing authorisation.

---

## REM-04-417 — Verification of continuing grant validity

**Source**  
Section 33: “The repository must verify both... the continuing validity of the underlying grant.”

**Requirement**  
The repository MUST verify the continuing validity of the underlying Permission Grant before accepting a delegated submission.

**Classification**  
Grant validation; revocation enforcement; repository security.

**Notes**  
The repository must account for expiration, revocation, scope changes and any other condition affecting current grant validity.

---

## REM-04-418 — Dual validation requirement

**Source**  
Section 33: “The repository must verify both: the delegated signature; the continuing validity of the underlying grant.”

**Requirement**  
A delegated repository operation MUST NOT be accepted unless both the delegated signature and the underlying grant are valid.

**Classification**  
Combined authority validation; repository acceptance.

**Notes**  
Neither a valid signature with an invalid grant nor a valid grant with an invalid signature is sufficient.

---

# 34. Application installations

## REM-04-419 — Multiple installations per application

**Source**  
Section 34: “One application may exist across multiple installations.”

**Requirement**  
The permission model MUST support one Application Identity being used across multiple installations.

**Classification**  
Installation model; application identity; multi-device support.

**Notes**  
Multiple installations must not automatically be treated as multiple independent Application Identities.

---

## REM-04-420 — Web-session installation support

**Source**  
Section 34 examples: “web session”.

**Requirement**  
The installation model MAY represent a web session as a distinct application installation or session context.

**Classification**  
Installation type; web access.

**Notes**  
The example is illustrative and does not prescribe a fixed installation identifier format.

---

## REM-04-421 — Mobile installation support

**Source**  
Section 34 examples: “mobile phone”.

**Requirement**  
The installation model MAY represent a mobile-device installation separately from other installations of the same application.

**Classification**  
Installation type; device-specific access.

**Notes**  
Separate representation enables installation-specific inspection and revocation.

---

## REM-04-422 — Desktop installation support

**Source**  
Section 34 examples: “desktop application”.

**Requirement**  
The installation model MAY represent a desktop application installation separately from other installations.

**Classification**  
Installation type; desktop access.

**Notes**  
The installation remains associated with the same stable Application Identity unless a distinct application identity is warranted.

---

## REM-04-423 — Browser-extension installation support

**Source**  
Section 34 examples: “browser extension”.

**Requirement**  
The installation model MAY represent a browser-extension installation separately from other application installations.

**Classification**  
Installation type; browser integration.

**Notes**  
Browser-extension installations may have distinct device, browser and session risk characteristics.

---

## REM-04-424 — Background-worker installation support

**Source**  
Section 34 examples: “server-side background worker”.

**Requirement**  
The installation model MAY represent a server-side background worker as a distinct installation or execution context.

**Classification**  
Installation type; background service.

**Notes**  
A server-side worker may operate without an active user session and therefore requires explicit background-access treatment.

---

## REM-04-425 — Distinction between application identity and installation

**Source**  
Section 34: “The permission model should distinguish: the Application Identity; a specific installation...”

**Requirement**  
The permission model SHOULD distinguish the stable Application Identity from a specific application installation.

**Classification**  
Identity separation; installation model; recommendation.

**Notes**  
Revoking an installation need not revoke the entire Application Identity where installation-level control is supported.

---

## REM-04-426 — Distinction between installation and device

**Source**  
Section 34: “The permission model should distinguish... a specific installation; a specific device...”

**Requirement**  
The permission model SHOULD distinguish a specific installation from the device on which it operates.

**Classification**  
Device identity; installation separation; recommendation.

**Notes**  
A device may host multiple installations, and one installation may have multiple sessions.

---

## REM-04-427 — Distinction between device and session

**Source**  
Section 34: “The permission model should distinguish... a specific device; a specific session.”

**Requirement**  
The permission model SHOULD distinguish a specific device from a specific authorisation or application session.

**Classification**  
Session management; device separation; recommendation.

**Notes**  
Ending one session should not necessarily revoke all authority associated with the device or installation.

---

## REM-04-428 — Whole-application revocation

**Source**  
Section 34: “The user may revoke: the entire application...”

**Requirement**  
The permission model MAY support revocation of all authority granted to an application across its installations.

**Classification**  
Revocation; application-level control.

**Notes**  
Whole-application revocation should invalidate or prevent renewal of all associated installation authority where applicable.

---

## REM-04-429 — Installation-specific revocation

**Source**  
Section 34: “The user may revoke... only: the installation on an old device...”

**Requirement**  
Where implementation support exists, the permission model MAY allow revocation of one specific installation without revoking the entire application.

**Classification**  
Granular revocation; installation control.

**Notes**  
This enables removal of authority from a lost, retired or untrusted device while preserving other valid installations.

---

# 35. Background access

## REM-04-430 — Declaration of continuous access

**Source**  
Section 35: “An application requesting continuous or background access must declare it.”

**Requirement**  
An application requesting continuous access MUST explicitly declare that continuous access is requested.

**Classification**  
Permission disclosure; continuous access; transparency.

**Notes**  
Continuous access must not be inferred from an ordinary interactive-access request.

---

## REM-04-431 — Declaration of background access

**Source**  
Section 35: “An application requesting continuous or background access must declare it.”

**Requirement**  
An application requesting background access MUST explicitly declare that background access is requested.

**Classification**  
Permission disclosure; background processing; transparency.

**Notes**  
Background access means the application may act while the user is not actively interacting with it.

---

## REM-04-432 — Background access for record synchronisation

**Source**  
Section 35 examples: “syncing records”.

**Requirement**  
A grant MAY authorise background access for record synchronisation where that purpose is explicitly declared and approved.

**Classification**  
Background-use case; synchronisation.

**Notes**  
The grant should remain limited to the records, actions and frequency necessary for synchronisation.

---

## REM-04-433 — Background access for digest generation

**Source**  
Section 35 examples: “generating a daily digest”.

**Requirement**  
A grant MAY authorise background access for scheduled digest generation where that purpose is explicitly declared and approved.

**Classification**  
Background-use case; scheduled processing.

**Notes**  
The permission should state the relevant data scope and processing cadence where practical.

---

## REM-04-434 — Background access for repository-event monitoring

**Source**  
Section 35 examples: “monitoring repository events”.

**Requirement**  
A grant MAY authorise background access for monitoring repository events where the event scope and purpose are approved.

**Classification**  
Background-use case; event subscription.

**Notes**  
Event monitoring should not imply unrestricted read or write access to repository content.

---

## REM-04-435 — Background access for search-index maintenance

**Source**  
Section 35 examples: “maintaining a search index”.

**Requirement**  
A grant MAY authorise background access for maintaining a search index where indexing, retention and scope are explicitly approved.

**Classification**  
Background-use case; indexing; derived data.

**Notes**  
Indexing may create derived representations and should remain consistent with the approved purpose and retention declarations.

---

## REM-04-436 — Background access for incoming-reply processing

**Source**  
Section 35 examples: “processing incoming replies”.

**Requirement**  
A grant MAY authorise background access for processing incoming replies where the relevant event and record scopes are approved.

**Classification**  
Background-use case; messaging and interaction processing.

**Notes**  
Processing replies does not automatically authorise unrelated repository operations.

---

## REM-04-437 — User-facing explanation of inactive-use operation

**Source**  
Section 35: “The user-facing consent must explain that the application may act while the user is not actively using it.”

**Requirement**  
The user-facing consent interface MUST explain that an application with background authority may act while the user is not actively using the application.

**Classification**  
Consent disclosure; background authority; transparency.

**Notes**  
The explanation should describe concrete background behaviour rather than rely only on the phrase “background access.”

---

## REM-04-438 — Narrow background authority

**Source**  
Section 35: “Background access should use narrower, renewable authority wherever practical.”

**Requirement**  
Background access SHOULD use narrowly scoped authority wherever practical.

**Classification**  
Least privilege; background access; recommendation.

**Notes**  
Scope may be narrowed by resource, action, frequency, duration, purpose or installation.

---

## REM-04-439 — Renewable background authority

**Source**  
Section 35: “Background access should use narrower, renewable authority wherever practical.”

**Requirement**  
Background access SHOULD use renewable rather than unnecessarily permanent authority wherever practical.

**Classification**  
Authority lifecycle; background access; recommendation.

**Notes**  
Renewal allows current grant validity, policy and application status to be reassessed before continued access.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 31–35 of `design-notes/04-application-and-permission-model.md`.
- Section 36 and later content was excluded.
- Examples were used to clarify scope and use cases without being promoted into fixed final token syntax.

## Numbering verification

- First requirement: `REM-04-391`.
- Final requirement: `REM-04-439`.
- Requirement numbering continues directly from Part 6.
- Identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each requirement is traceable to an explicit source statement, list item, example or necessary decomposition of a compound obligation.
- Compound security rules were separated where they impose independently testable controls.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or supported options.
- Illustrative use cases remain optional and have not been converted into universal mandatory features.

## Editorial verification

- Access-token lifetime, refresh authority, delegated keys and re-authorisation remain distinct mechanisms.
- Capability tokens remain object- or operation-specific rather than broad substitute account permissions.
- Delegated-key signature validity is kept separate from continuing grant validity.
- Application Identity, installation, device and session remain distinct concepts.
- Application-wide revocation and installation-specific revocation remain separate operations.
- Background authority requires explicit declaration, concrete user-facing disclosure and narrow renewable scope where practical.
