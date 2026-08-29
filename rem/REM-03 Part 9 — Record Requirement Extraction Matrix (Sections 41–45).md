# REM-03 Part 9 — Record Requirement Extraction Matrix (Sections 41–45)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 41–45 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

41. Record portability
42. Record interoperability
43. Required v0.1 record operations
44. Record invariants
45. Compliance scenario

Requirement identifiers continue sequentially from Part 8, beginning with `REM-03-394`.

---

# 41. Record portability

## REM-03-394 — Preservation of Record URI during portability

**Source**  
Section 41, portability capability: another compliant provider can “preserve its Record URI”.

**Requirement**  
A compliant receiving provider MUST preserve the Record URI of a portable record.

**Classification**  
Portability; identifier stability; migration.

**Notes**  
Migration must not assign a new logical identity merely because the serving provider changes.

---

## REM-03-395 — Preservation of collection and schema

**Source**  
Section 41, portability capability: another compliant provider can “preserve its collection and schema”.

**Requirement**  
A compliant receiving provider MUST preserve the record’s collection association and schema identifier during migration.

**Classification**  
Portability; schema continuity; collection continuity.

**Notes**  
Preserving content without its collection and schema context would remove operational meaning required for validation and interoperability.

---

## REM-03-396 — Envelope validation after migration

**Source**  
Section 41, portability capability: another compliant provider can “validate its envelope”.

**Requirement**  
A portable record MUST remain capable of passing applicable Record Envelope validation at the receiving compliant provider.

**Classification**  
Portability; envelope validation; protocol conformance.

**Notes**  
Migration must preserve the protocol-level metadata and context necessary for validation.

---

## REM-03-397 — Preservation of record content

**Source**  
Section 41, portability capability: another compliant provider can “preserve its content”.

**Requirement**  
A compliant receiving provider MUST preserve the record’s schema-defined content during migration.

**Classification**  
Portability; content integrity; migration.

**Notes**  
Any deliberate transformation belongs to a separately authorised translation or migration process and must not be confused with faithful preservation.

---

## REM-03-398 — Preservation of blob references

**Source**  
Section 41, portability capability: another compliant provider can “preserve blob references”.

**Requirement**  
A compliant receiving provider MUST preserve the record’s blob references during migration.

**Classification**  
Portability; blob integrity; media continuity.

**Notes**  
The storage location may change, but the stable blob identity and relationship to the record must remain intact.

---

## REM-03-399 — Preservation of version history

**Source**  
Section 41, portability capability: another compliant provider can “preserve its version history”.

**Requirement**  
A compliant receiving provider MUST preserve the record’s version history during migration.

**Classification**  
Portability; historical integrity; versioning.

**Notes**  
Portability is not satisfied by retaining only the latest visible payload where the protocol history is required to verify record state.

---

## REM-03-400 — Preservation of unknown extensions

**Source**  
Section 41, portability capability: another compliant provider can “preserve unknown extensions”.

**Requirement**  
A compliant receiving provider MUST preserve valid extensions that it does not understand.

**Classification**  
Forward compatibility; portability; extension preservation.

**Notes**  
Lack of local interpretation is not permission to strip unknown but valid extension data.

---

## REM-03-401 — Continued visibility-rule enforcement

**Source**  
Section 41, portability capability: another compliant provider can “continue serving it according to its visibility rules”.

**Requirement**  
A compliant receiving provider MUST continue serving a migrated record in accordance with its applicable visibility rules.

**Classification**  
Portability; access control; visibility continuity.

**Notes**  
Migration must not silently make restricted or private content public, or make public content unavailable without a separately valid reason.

---

## REM-03-402 — Operational meaning required for portability

**Source**  
Section 41: “A migration that converts every record into flat files without operational meaning does not satisfy Relay portability.”

**Requirement**  
A migration MUST NOT be considered Relay-portable if it merely converts records into flat files while losing the protocol metadata, relationships, validation context or operational meaning required by the Record Model.

**Classification**  
Portability threshold; semantic preservation; migration validity.

**Notes**  
Exportability alone is not sufficient. The receiving environment must be able to continue treating the information as operational Relay records.

---

# 42. Record interoperability

## REM-03-403 — Universal type support not required

**Source**  
Section 42: “Relay interoperability does not require every application to support every record type.”

**Requirement**  
A compliant Relay application MUST NOT be required to fully interpret or render every valid Relay record type.

**Classification**  
Interoperability; application capability; extensibility.

**Notes**  
Interoperability is achieved through safe handling and preservation, not mandatory universal feature support.

---

## REM-03-404 — Declared full-support capability

**Source**  
Section 42 example: “Fully supports com.relay.post.v1”.

**Requirement**  
An application MAY declare full support for a record schema that it can validate, interpret and operate on according to that schema.

**Classification**  
Capability declaration; schema support; interoperability.

**Notes**  
The example is illustrative and does not establish a final capability-advertisement syntax.

---

## REM-03-405 — Declared read-only capability

**Source**  
Section 42 example: “Read-only support for com.relay.article.v1”.

**Requirement**  
An application MAY declare read-only support for a schema where it can safely interpret records but does not support authorised modification operations.

**Classification**  
Capability declaration; read-only interoperability.

**Notes**  
Read-only support must not be represented as full operational support.

---

## REM-03-406 — Preserve-without-display capability

**Source**  
Section 42 example: “Preserves but does not display com.example.design.canvas.v1”.

**Requirement**  
An application MAY preserve a valid record type without rendering or interpreting its schema-specific content.

**Classification**  
Forward compatibility; preservation; limited support.

**Notes**  
This permits safe passage of unknown record types through applications and migrations.

---

## REM-03-407 — Minimum handling of unsupported records

**Source**  
Section 42: “The minimum requirement is that unsupported records are not damaged, misrepresented or discarded.”

**Requirement**  
A compliant application MUST NOT damage, misrepresent or discard a valid record solely because the application does not support its record type.

**Classification**  
Minimum interoperability; preservation; data integrity.

**Notes**  
The application may decline to display or operate on the record, but must preserve it accurately where it assumes custody or participates in migration.

---

# 43. Required v0.1 record operations

## REM-03-408 — Create-record operation

**Source**  
Section 43 required operation: “Create record”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support creation of a record through an authorised repository operation.

**Classification**  
Required operation; creation; repository lifecycle.

**Notes**  
Creation remains subject to schema, authority, validation and accepted-commit requirements.

---

## REM-03-409 — Read-current-record operation

**Source**  
Section 43 required operation: “Read current record”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support reading the current accepted version of a logical record.

**Classification**  
Required operation; retrieval; current state.

**Notes**  
Access remains subject to the record’s visibility and audience rules.

---

## REM-03-410 — Read-specific-version operation

**Source**  
Section 43 required operation: “Read specific record version”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support reading a specific historical Record Version where that version remains retrievable and access is authorised.

**Classification**  
Required operation; historical retrieval; versioning.

**Notes**  
This operation is distinct from resolving the current version through the base Record URI.

---

## REM-03-411 — List-records-by-collection operation

**Source**  
Section 43 required operation: “List records by collection”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support listing records by collection.

**Classification**  
Required operation; collection retrieval; discovery.

**Notes**  
The results must respect visibility, audience and other access controls.

---

## REM-03-412 — Validate-record-envelope operation

**Source**  
Section 43 required operation: “Validate record envelope”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support validation of a Record Envelope against protocol-level structural requirements.

**Classification**  
Required operation; envelope validation.

**Notes**  
Envelope validation is separate from schema-content and semantic validation.

---

## REM-03-413 — Validate-record-schema operation

**Source**  
Section 43 required operation: “Validate record schema”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support validation of record content against its declared schema where that schema is supported.

**Classification**  
Required operation; schema validation.

**Notes**  
Unknown valid schemas must still be preserved even where local schema validation is unavailable.

---

## REM-03-414 — Update-record operation

**Source**  
Section 43 required operation: “Update record”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support authorised updates to records whose schemas permit updating.

**Classification**  
Required operation; update; versioning.

**Notes**  
An accepted update creates a new Record Version and must satisfy concurrency and authority rules.

---

## REM-03-415 — Delete-record operation

**Source**  
Section 43 required operation: “Delete record”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support authorised record deletion.

**Classification**  
Required operation; deletion; lifecycle.

**Notes**  
Deletion must preserve the distinctions among deletion modes and apply applicable tombstone requirements.

---

## REM-03-416 — Restore-record operation

**Source**  
Section 43 required operation: “Restore record where permitted”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support restoration of a deleted record where the schema and retained state permit restoration and the controller authorises it.

**Classification**  
Required operation; restoration; conditional lifecycle.

**Notes**  
Restoration is conditional and creates a new current version without erasing the historical deletion event.

---

## REM-03-417 — Read-tombstone operation

**Source**  
Section 43 required operation: “Read tombstone”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support reading an accessible tombstone for a deleted or retired logical record.

**Classification**  
Required operation; tombstone retrieval; historical integrity.

**Notes**  
The tombstone must expose only the minimum information allowed by protocol and policy.

---

## REM-03-418 — Verify-record-integrity operation

**Source**  
Section 43 required operation: “Verify record integrity”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support verification of record integrity against the applicable integrity reference and accepted repository history.

**Classification**  
Required operation; integrity verification.

**Notes**  
The exact proof mechanism may depend on commits, hashes, signatures or other protocol-defined structures.

---

## REM-03-419 — Resolve-record-references operation

**Source**  
Section 43 required operation: “Resolve record references”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support resolution of references to other Relay Records or specific Record Versions where accessible.

**Classification**  
Required operation; reference resolution; interoperability.

**Notes**  
Unavailable targets must be handled accurately rather than causing the referring record to be misrepresented.

---

## REM-03-420 — Upload-and-attach-blob operation

**Source**  
Section 43 required operation: “Upload and attach blob”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support uploading a blob and attaching its stable reference to a record where permitted by the schema.

**Classification**  
Required operation; blob management; media attachment.

**Notes**  
Temporary storage URLs must not become the blob’s permanent identity.

---

## REM-03-421 — Change-visibility operation

**Source**  
Section 43 required operation: “Change visibility”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support authorised changes to a record’s visibility classification where permitted.

**Classification**  
Required operation; visibility; access control.

**Notes**  
A visibility change may create a new version even where the primary content does not change.

---

## REM-03-422 — Change-audience operation

**Source**  
Section 43 required operation: “Change audience”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support authorised changes to a restricted record’s audience rules where permitted.

**Classification**  
Required operation; audience management; access control.

**Notes**  
Audience removal revokes future authorised access but cannot guarantee deletion of copies already received.

---

## REM-03-423 — Inspect-provenance operation

**Source**  
Section 43 required operation: “Inspect provenance”.

**Requirement**  
A compliant Relay v0.1 implementation MUST support inspection of the structured provenance associated with a record.

**Classification**  
Required operation; provenance; transparency.

**Notes**  
Inspection must preserve the distinction between declared provenance and verified provenance.

---

## REM-03-424 — Preserve-unknown-record-types operation

**Source**  
Section 43 required operation: “Preserve unknown record types”.

**Requirement**  
A compliant Relay v0.1 implementation MUST preserve valid record types that it does not understand.

**Classification**  
Required operation; forward compatibility; preservation.

**Notes**  
Unknown records may be preserved without being rendered or fully validated against their schema locally.

---

## REM-03-425 — Detect-update-conflict operation

**Source**  
Section 43 required operation: “Detect update conflict”.

**Requirement**  
A compliant Relay v0.1 implementation MUST detect when competing updates attempt to replace the same current version.

**Classification**  
Required operation; conflict detection; concurrency.

**Notes**  
Detected conflicts must not be silently collapsed into one linear continuation.

---

# 44. Record invariants

## REM-03-426 — Record URI non-reassignment invariant

**Source**  
Section 44, Invariant 1: “A Record URI identifies one logical record and must not be reassigned.”

**Requirement**  
A Record URI MUST identify exactly one logical record and MUST NOT be reassigned to another logical record.

**Classification**  
Invariant; identifier integrity; non-reuse.

**Notes**  
The rule continues to apply after deletion and is supported by tombstone retention.

---

## REM-03-427 — URI stability under editing invariant

**Source**  
Section 44, Invariant 2: “Editing a record does not change its Record URI.”

**Requirement**  
Editing a record MUST NOT change the Record URI of the logical record.

**Classification**  
Invariant; identifier stability; versioning.

**Notes**  
The edit creates a new version rather than a new logical identity.

---

## REM-03-428 — Accepted-commit membership invariant

**Source**  
Section 44, Invariant 3: “Every current record version belongs to an accepted repository commit.”

**Requirement**  
Every current Record Version MUST belong to an accepted repository commit.

**Classification**  
Invariant; canonical state; repository history.

**Notes**  
A locally generated or pending version cannot be represented as canonical current state.

---

## REM-03-429 — Submitter-authority distinction invariant

**Source**  
Section 44, Invariant 4: “The submitting application is not necessarily the authorising identity.”

**Requirement**  
The Record Model MUST NOT assume that the submitting application or agent is the authorising identity.

**Classification**  
Invariant; authority separation; submission provenance.

**Notes**  
The two roles may coincide but must remain independently representable.

---

## REM-03-430 — Schema-use ownership invariant

**Source**  
Section 44, Invariant 5: “Using a schema does not give the schema publisher ownership of the record.”

**Requirement**  
Use of a schema MUST NOT confer ownership or repository control of the record on the schema publisher.

**Classification**  
Invariant; schema authority; ownership separation.

**Notes**  
Schema authority governs the schema definition, not individual conforming records.

---

## REM-03-431 — Visibility-rights distinction invariant

**Source**  
Section 44, Invariant 6: “Visibility does not determine legal ownership or usage rights.”

**Requirement**  
A record’s visibility classification MUST NOT be treated as determining its legal ownership or usage rights.

**Classification**  
Invariant; visibility; rights separation.

**Notes**  
A public record may remain subject to licensing, attribution, commercial-use or model-training restrictions.

---

## REM-03-432 — Deletion-history integrity invariant

**Source**  
Section 44, Invariant 7: “A record may be deleted without pretending that it never existed in repository history.”

**Requirement**  
Record deletion MUST preserve sufficient repository history to avoid falsely representing that the logical record never existed.

**Classification**  
Invariant; deletion; historical integrity.

**Notes**  
The retained history may be reduced to minimum verification metadata or a tombstone according to policy.

---

## REM-03-433 — Unknown-field migration invariant

**Source**  
Section 44, Invariant 8: “Unknown but valid fields and extensions must survive migration.”

**Requirement**  
Unknown but valid fields and extensions MUST survive migration without being stripped or altered solely because the receiving implementation does not understand them.

**Classification**  
Invariant; forward compatibility; migration preservation.

**Notes**  
This rule applies to valid unknown data, not malformed or prohibited fields.

---

## REM-03-434 — Projection canonicality invariant

**Source**  
Section 44, Invariant 9: “An application projection is not canonical unless deliberately accepted into the repository.”

**Requirement**  
An application projection MUST NOT be treated as a canonical Relay Record unless the controller deliberately causes it to be accepted into the repository.

**Classification**  
Invariant; projection; canonical state.

**Notes**  
Derived views, scores and presentation objects remain application state until deliberately saved.

---

## REM-03-435 — Cached-copy identity and provenance invariant

**Source**  
Section 44, Invariant 10: “A cached copy must retain the canonical Record URI and source provenance.”

**Requirement**  
A cached copy of a Relay Record MUST retain the canonical Record URI and source provenance.

**Classification**  
Invariant; caching; provenance; identity preservation.

**Notes**  
A cache must not relabel itself as the canonical source or detach the copy from its source identity.

---

## REM-03-436 — Index non-ownership invariant

**Source**  
Section 44, Invariant 11: “A public record may be indexed, but the index does not become its canonical owner.”

**Requirement**  
Indexing a public record MUST NOT make the index the canonical owner or authoritative repository of that record.

**Classification**  
Invariant; indexing; ownership separation.

**Notes**  
An index is a discovery or projection layer and remains subordinate to the canonical repository source.

---

## REM-03-437 — Acting-identity ownership invariant

**Source**  
Section 44, Invariant 12: “A reply, reaction or repost belongs to the identity that authorised that record, not to the owner of the referenced content.”

**Requirement**  
A reply, reaction or repost MUST remain controlled by the identity that authorised that record and MUST NOT become owned by the controller of the referenced content merely because it points to that content.

**Classification**  
Invariant; record ownership; cross-repository interaction.

**Notes**  
The referenced-content controller may index, display or moderate the interaction within an application, but does not thereby become its canonical controller.

---

# 45. Compliance scenario

## REM-03-438 — Basic compliance-scenario expectation

**Source**  
Section 45: “A basic record implementation should pass the following test.”

**Requirement**  
A basic Relay Record implementation SHOULD pass the complete compliance scenario defined in Section 45.

**Classification**  
Compliance scenario; implementation recommendation.

**Notes**  
The source uses “should”, so the scenario is an expected baseline test rather than language redefining every conformance tier.

---

## REM-03-439 — Initial public-record creation

**Source**  
Section 45, Initial record: “Application A creates a public post...” and “The repository accepts it as version 1.”

**Requirement**  
The implementation SHOULD allow an authorised application to create a public record that becomes version 1 when accepted by the repository.

**Classification**  
Compliance scenario; creation; initial version.

**Notes**  
The example Record URI is illustrative rather than mandatory syntax beyond the source model’s provisional URI design.

---

## REM-03-440 — Cross-application record reading and updating

**Source**  
Section 45, Update through another application: “Application B reads the record and updates the text.”

**Requirement**  
The implementation SHOULD allow another authorised application to read and update the same logical record.

**Classification**  
Compliance scenario; cross-application interoperability; update.

**Notes**  
The second application does not acquire ownership by performing the update.

---

## REM-03-441 — Acceptance of the second version

**Source**  
Section 45, Update through another application: “The repository accepts version 2.”

**Requirement**  
A valid cross-application update SHOULD be accepted as a new Record Version rather than replacing version 1 without history.

**Classification**  
Compliance scenario; versioning; repository acceptance.

**Notes**  
The new version remains part of the same logical record.

---

## REM-03-442 — URI continuity across applications and versions

**Source**  
Section 45, Update through another application: “The Record URI remains unchanged.”

**Requirement**  
The Record URI SHOULD remain unchanged when another application creates a new accepted version of the record.

**Classification**  
Compliance scenario; identifier stability; application independence.

**Notes**  
This scenario tests the general URI-stability invariant.

---

## REM-03-443 — Stale-update detection

**Source**  
Section 45, Concurrent update: “Application A attempts to update version 1 after version 2 already exists.”

**Requirement**  
The implementation SHOULD detect an update based on a stale expected version when a newer current version already exists.

**Classification**  
Compliance scenario; concurrency; conflict detection.

**Notes**  
The example tests optimistic concurrency behaviour.

---

## REM-03-444 — Stale-update rejection or conflict marking

**Source**  
Section 45, Concurrent update: “The repository rejects the stale update or marks it as a conflict.”

**Requirement**  
The repository SHOULD reject a stale update or explicitly mark and preserve it as a conflict requiring resolution.

**Classification**  
Compliance scenario; conflict handling; repository state.

**Notes**  
The source allows either rejection or explicit conflict treatment.

---

## REM-03-445 — No silent overwrite of current version

**Source**  
Section 45, Concurrent update: “It does not silently overwrite version 2.”

**Requirement**  
The repository MUST NOT silently overwrite the current version with an update based on stale state.

**Classification**  
Compliance scenario; data integrity; concurrency.

**Notes**  
This is the mandatory failure condition within the scenario.

---

## REM-03-446 — Reply stored in replying identity’s repository

**Source**  
Section 45, Reply from another identity: “Bob creates a reply in Bob’s repository referencing Alice’s post.”

**Requirement**  
The implementation SHOULD support creation of a reply in the replying identity’s repository while referencing the original record in another repository.

**Classification**  
Compliance scenario; cross-repository reference; reply ownership.

**Notes**  
The reply is a separate canonical record rather than content inserted into the original author’s record.

---

## REM-03-447 — Cross-application display of reply

**Source**  
Section 45, Reply from another identity: “Alice’s application displays the reply.”

**Requirement**  
An application displaying the original record SHOULD be able to resolve and display an accessible reply stored in another identity’s repository.

**Classification**  
Compliance scenario; reference resolution; display interoperability.

**Notes**  
Display does not transfer canonical control of the reply.

---

## REM-03-448 — Reply-controller continuity

**Source**  
Section 45, Reply from another identity: “Bob remains the controller of the reply record.”

**Requirement**  
The replying identity MUST remain the controller of the reply record even when another identity’s application displays it.

**Classification**  
Compliance scenario; ownership; repository authority.

**Notes**  
This tests the acting-identity ownership invariant.

---

## REM-03-449 — Visibility change creates a version

**Source**  
Section 45, Visibility change: “Alice changes the post from public to restricted. A new version records the change.”

**Requirement**  
An authorised change from public to restricted visibility SHOULD create a new accepted Record Version recording that change.

**Classification**  
Compliance scenario; visibility; metadata versioning.

**Notes**  
The primary content may remain unchanged while the metadata change creates a new version.

---

## REM-03-450 — Refusal of future unauthorised access

**Source**  
Section 45, Visibility change: “Future unauthorised access is refused.”

**Requirement**  
After a valid visibility restriction, the repository MUST refuse future access attempts that do not satisfy the applicable authority or audience rule.

**Classification**  
Compliance scenario; access control; visibility enforcement.

**Notes**  
The requirement concerns future authorised service and cannot revoke copies already obtained.

---

## REM-03-451 — Policy-governed removal of active content

**Source**  
Section 45, Deletion: “Its active content is removed according to policy.”

**Requirement**  
When the controller deletes the record, the implementation SHOULD remove or withhold its active content in accordance with the applicable deletion policy.

**Classification**  
Compliance scenario; deletion; policy enforcement.

**Notes**  
The exact retained verification metadata depends on the deletion mode and tombstone requirements.

---

## REM-03-452 — Tombstone prevention of Record URI reuse

**Source**  
Section 45, Deletion: “A tombstone prevents reuse of the Record URI...”

**Requirement**  
Deletion MUST leave sufficient tombstone state to prevent reuse or reassignment of the deleted Record URI.

**Classification**  
Compliance scenario; tombstone; identifier integrity.

**Notes**  
This applies even when the active content has been erased.

---

## REM-03-453 — Tombstone preservation of minimum verification history

**Source**  
Section 45, Deletion: a tombstone “preserves minimum verification history.”

**Requirement**  
The tombstone MUST preserve the minimum verification history required to demonstrate the prior existence and authorised deletion of the logical record.

**Classification**  
Compliance scenario; tombstone; historical integrity.

**Notes**  
The tombstone should not retain more deleted content than necessary.

---

## REM-03-454 — Migration continuity for URI, versions and tombstone

**Source**  
Section 45, Migration: “The post’s versions, tombstone and Record URI remain intact.”

**Requirement**  
Repository migration SHOULD preserve the record’s Record URI, accepted versions and tombstone intact at the receiving provider.

**Classification**  
Compliance scenario; migration; portability.

**Notes**  
This scenario tests portability after both versioning and deletion history have occurred.

---

## REM-03-455 — Basic Relay Record objective

**Source**  
Section 45: “If these operations occur without confusing application ownership, record identity, historical versions or visibility state, the implementation satisfies the basic Relay Record objective.”

**Requirement**  
An implementation SHOULD be considered to satisfy the basic Relay Record objective when it completes the Section 45 operations without conflating application ownership, logical record identity, historical versions or visibility state.

**Classification**  
Compliance scenario; baseline objective; conceptual integrity.

**Notes**  
The scenario evaluates both functional operations and preservation of the Record Model’s core conceptual boundaries.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 41–45 of `design-notes/03-record-model.md`.
- Sections 46–48 were excluded from this part.
- Section 45 was treated as a compliance scenario and not as permission to invent additional protocol behaviour.

## Numbering verification

- First requirement: `REM-03-394`.
- Final requirement: `REM-03-455`.
- Numbering continues directly from Part 8.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each portability capability in Section 41 was extracted separately because each is independently testable.
- Each required operation in Section 43 was extracted as an individual compliance obligation.
- Each invariant in Section 44 was extracted separately and preserved as an unconditional rule.
- Section 45 steps were decomposed only where the source establishes distinct observable outcomes.

## Normative-language verification

- Section 43’s “must support” list is represented using `MUST`.
- Section 44 invariants are represented using `MUST` or `MUST NOT`.
- Section 45’s overall “should pass” framing is retained as `SHOULD`, except where the scenario itself expressly states a mandatory prohibition or invariant outcome.
- Example capability declarations in Section 42 remain illustrative and have not been promoted into a final negotiation syntax.

## Editorial verification

- Portability requires preservation of operational meaning, not merely flat-file export.
- Interoperability does not require universal schema support, but unsupported records must remain undamaged, accurately represented and preserved.
- Record identity, application capability, repository authority and schema authority remain distinct.
- Cached copies and indexes remain non-canonical representations tied to the canonical Record URI and provenance.
- The compliance scenario preserves conflict detection, reply ownership, visibility enforcement, deletion history and migration continuity.
