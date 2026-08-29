# REM-03 Part 5 — Record Requirement Extraction Matrix (Sections 21–25)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 21–25 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

21. Record deletion
22. Tombstone
23. Restoration
24. Expiration
25. References between records

Requirement identifiers continue sequentially from Part 4, beginning with `REM-03-245`.

---

# 21. Record deletion

## REM-03-245 — Deletion as an authorised repository operation

**Source**  
Section 21: “Deleting a record is an authorised repository operation.”

**Requirement**  
Deleting a Relay Record MUST be performed as an authorised operation of the authoritative Relay Repository.

**Classification**  
Deletion; repository authority; lifecycle.

**Notes**  
An application hiding or removing a local representation does not by itself constitute canonical record deletion.

---

## REM-03-246 — Deleted Record URI identification

**Source**  
Section 21, deletion metadata: “the Record URI”.

**Requirement**  
A deletion operation MUST identify the Record URI of the logical record being deleted.

**Classification**  
Deletion metadata; record identification.

**Notes**  
The stable Record URI ensures that the deletion applies to an unambiguous logical record.

---

## REM-03-247 — Deleted version identification

**Source**  
Section 21, deletion metadata: “the version deleted”.

**Requirement**  
A deletion operation MUST identify the Record Version to which the deletion applies.

**Classification**  
Deletion metadata; versioning; concurrency.

**Notes**  
Identifying the version prevents ambiguity where the record has changed since a deletion request was prepared.

---

## REM-03-248 — Deletion time

**Source**  
Section 21, deletion metadata: “deletion time”.

**Requirement**  
A deletion operation MUST record the time at which the deletion became accepted repository state.

**Classification**  
Deletion metadata; temporal history; auditability.

**Notes**  
The deletion time should represent repository acceptance rather than merely local request creation.

---

## REM-03-249 — Deletion authority identification

**Source**  
Section 21, deletion metadata: “authorising authority”.

**Requirement**  
A deletion operation MUST identify the authority that authorised the deletion.

**Classification**  
Authority; accountability; deletion metadata.

**Notes**  
The authorising authority may be the controller or another authority permitted by the protocol and applicable repository rules.

---

## REM-03-250 — Deletion mode identification

**Source**  
Section 21, deletion metadata: “deletion mode”.

**Requirement**  
A deletion operation MUST identify the deletion mode being applied.

**Classification**  
Deletion state; lifecycle semantics.

**Notes**  
Deletion modes have materially different consequences and must not be represented as an undifferentiated deleted state.

---

## REM-03-251 — Tombstone-requirement identification

**Source**  
Section 21, deletion metadata: “tombstone requirements”.

**Requirement**  
A deletion operation MUST identify the tombstone requirements that apply to the deleted record.

**Classification**  
Deletion; tombstone; repository integrity.

**Notes**  
The applicable schema or deletion mode may determine what minimum persistent metadata must remain.

---

## REM-03-252 — Soft-deletion semantics

**Source**  
Section 21, Soft deletion: “The active record is hidden, but the provider retains its prior content.”

**Requirement**  
A soft-deletion state MUST mean that the active record is hidden while the provider retains its prior content.

**Classification**  
Deletion mode; retention; visibility.

**Notes**  
Soft deletion must not be represented as content erasure.

---

## REM-03-253 — Content-erasure semantics

**Source**  
Section 21, Content erasure: “The prior content is removed, while minimum verification metadata remains.”

**Requirement**  
A content-erasure state MUST remove the prior record content while retaining the minimum metadata required for verification and repository integrity.

**Classification**  
Deletion mode; erasure; verification.

**Notes**  
The source does not define the complete minimum metadata set in this section.

---

## REM-03-254 — Expiring-deletion semantics

**Source**  
Section 21, Expiring deletion: “The record becomes unavailable after a stated date.”

**Requirement**  
An expiring-deletion state MUST specify a date after which the record becomes unavailable.

**Classification**  
Deletion mode; scheduled state transition; availability.

**Notes**  
The record may remain available before the stated date unless another access rule applies.

---

## REM-03-255 — Legal-restriction semantics

**Source**  
Section 21, Legal restriction: “The content is withheld because of a legal or regulatory requirement.”

**Requirement**  
A legal-restriction state MUST indicate that content is being withheld because of a legal or regulatory requirement.

**Classification**  
Deletion-related state; legal compliance; availability.

**Notes**  
Legal restriction is not necessarily equivalent to erasure or canonical deletion.

---

## REM-03-256 — Provider-removal semantics

**Source**  
Section 21, Provider removal: “The current provider refuses to serve the record, without necessarily changing the canonical repository history.”

**Requirement**  
A provider-removal state MUST indicate that the current provider refuses to serve the record and MUST NOT imply that canonical repository history has necessarily changed.

**Classification**  
Provider behaviour; availability; repository history.

**Notes**  
Provider refusal and protocol-level deletion are distinct states.

---

## REM-03-257 — Distinct presentation of deletion states

**Source**  
Section 21: “These states must not be presented as equivalent.”

**Requirement**  
Implementations MUST NOT present soft deletion, content erasure, expiring deletion, legal restriction and provider removal as equivalent states.

**Classification**  
State semantics; application presentation; deletion accuracy.

**Notes**  
Applications should communicate the actual state without claiming erasure, legal restriction or canonical deletion where that has not occurred.

---

# 22. Tombstone

## REM-03-258 — Tombstone definition

**Source**  
Section 22: “A Tombstone is the minimum persistent record indicating that a logical record previously existed but is no longer active or available.”

**Requirement**  
A Tombstone MUST be a persistent record indicating that a logical record previously existed and is no longer active or available.

**Classification**  
Tombstone; deletion history; repository integrity.

**Notes**  
The tombstone preserves historical existence without retaining the full active record.

---

## REM-03-259 — Minimum tombstone content

**Source**  
Section 22: “A tombstone should not contain more deleted content than is necessary to preserve repository integrity and prevent identifier reuse.”

**Requirement**  
A Tombstone SHOULD contain no more deleted content than is necessary to preserve repository integrity and prevent identifier reuse.

**Classification**  
Data minimisation; tombstone; privacy; recommendation.

**Notes**  
The source permits minimum verification metadata while discouraging unnecessary retention of deleted content.

---

## REM-03-260 — Deleted Record Key non-reuse

**Source**  
Section 22.1: “A deleted Record Key must not be reused for a different logical record.”

**Requirement**  
A Record Key previously used by a deleted record MUST NOT be reused for a different logical record.

**Classification**  
Identifier integrity; key uniqueness; deletion history.

**Notes**  
This prevents a new object from inheriting the apparent identity or references of the deleted record.

---

## REM-03-261 — Tombstone evidence of prior identifier use

**Source**  
Section 22.1: “The tombstone preserves the fact that the identifier has already been used.”

**Requirement**  
The Tombstone MUST preserve sufficient evidence that the deleted record’s identifier has already been used.

**Classification**  
Identifier history; repository integrity; tombstone.

**Notes**  
The evidence need not include the deleted content itself.

---

# 23. Restoration

## REM-03-262 — Schema permission for restoration

**Source**  
Section 23: “A deleted record may be restored if the schema permits restoration...”

**Requirement**  
A deleted record MAY be restored only if its applicable schema permits restoration.

**Classification**  
Restoration; schema behaviour; lifecycle.

**Notes**  
Schemas may prohibit restoration for records whose semantics require permanent retirement.

---

## REM-03-263 — Availability of deleted content for restoration

**Source**  
Section 23: restoration is permitted if “the deleted content remains available”.

**Requirement**  
Restoration of a deleted record requires the deleted content or sufficient recoverable record state to remain available.

**Classification**  
Restoration; data availability; lifecycle.

**Notes**  
A content-erased record may therefore be unrestorable unless recoverable content exists through a permitted mechanism.

---

## REM-03-264 — Controller authorisation of restoration

**Source**  
Section 23: restoration is permitted if “the controller authorises restoration”.

**Requirement**  
Restoration MUST be authorised by the controller.

**Classification**  
Authority; restoration; accountability.

**Notes**  
Any delegated restoration mechanism must operate under valid controller authority.

---

## REM-03-265 — Commit recording of restoration

**Source**  
Section 23: restoration is permitted if “a new commit records the operation”.

**Requirement**  
A restoration operation MUST be recorded in a new accepted repository commit.

**Classification**  
Repository history; restoration; commits.

**Notes**  
Local reappearance of content without repository acceptance does not restore the canonical record.

---

## REM-03-266 — Restoration creates a new current version

**Source**  
Section 23: “Restoration creates a new current version.”

**Requirement**  
Successful restoration MUST create a new current Record Version.

**Classification**  
Versioning; restoration; repository state.

**Notes**  
The restored record must not silently revert the current pointer to an old version as though deletion never occurred.

---

## REM-03-267 — Preservation of deletion history after restoration

**Source**  
Section 23: “It does not erase the deletion event from repository history.”

**Requirement**  
Restoration MUST NOT erase or conceal the prior deletion event from repository history.

**Classification**  
Historical integrity; auditability; restoration.

**Notes**  
The repository history must show both deletion and restoration as distinct accepted operations.

---

# 24. Expiration

## REM-03-268 — Schema-defined expiration

**Source**  
Section 24: “A schema or record may define an expiration time.”

**Requirement**  
A schema MAY define expiration behaviour and an expiration time for conforming records.

**Classification**  
Expiration; schema behaviour; lifecycle.

**Notes**  
The schema should define the meaning and consequences of expiration.

---

## REM-03-269 — Record-defined expiration

**Source**  
Section 24: “A schema or record may define an expiration time.”

**Requirement**  
A record MAY define an expiration time where the applicable schema permits or supports it.

**Classification**  
Expiration; record metadata; lifecycle.

**Notes**  
The record-level value must conform to schema rules.

---

## REM-03-270 — Expiration as end of public display

**Source**  
Section 24: expiration may mean “no longer publicly displayed”.

**Requirement**  
A schema MAY define expiration to mean that the record is no longer publicly displayed.

**Classification**  
Expiration semantics; visibility.

**Notes**  
This interpretation does not necessarily invalidate or delete the record.

---

## REM-03-271 — Expiration as assertion invalidity

**Source**  
Section 24: expiration may mean “no longer valid as an assertion”.

**Requirement**  
A schema MAY define expiration to mean that the record is no longer valid as an assertion.

**Classification**  
Expiration semantics; assertion validity.

**Notes**  
The historical assertion may remain available even after it ceases to be currently valid.

---

## REM-03-272 — Expiration as loss of access

**Source**  
Section 24: expiration may mean “no longer accessible”.

**Requirement**  
A schema MAY define expiration to mean that the record is no longer accessible.

**Classification**  
Expiration semantics; access control.

**Notes**  
The schema should clarify whether all access ends or only specified access classes are affected.

---

## REM-03-273 — Expiration as deletion eligibility

**Source**  
Section 24: expiration may mean “eligible for deletion”.

**Requirement**  
A schema MAY define expiration to make the record eligible for deletion.

**Classification**  
Expiration semantics; deletion lifecycle.

**Notes**  
Eligibility for deletion does not itself establish that deletion has occurred.

---

## REM-03-274 — Required schema interpretation of expiration

**Source**  
Section 24: “The schema must specify which interpretation applies.”

**Requirement**  
A schema supporting expiration MUST specify the exact semantic consequence or consequences of expiration.

**Classification**  
Schema definition; expiration semantics; interoperability.

**Notes**  
Applications must not infer one expiration meaning from another without schema authority.

---

# 25. References between records

## REM-03-275 — Stable Record URI references

**Source**  
Section 25: “A record may refer to another Relay Record using its stable Record URI.”

**Requirement**  
A Relay Record MAY refer to another Relay Record using the target’s stable Record URI.

**Classification**  
Inter-record references; addressing; interoperability.

**Notes**  
The stable URI allows the reference to survive application, provider and storage changes.

---

## REM-03-276 — Semantic relationship identification

**Source**  
Section 25: “A reference should identify its semantic relationship.”

**Requirement**  
An inter-record reference SHOULD identify the semantic relationship between the referring record and the target record.

**Classification**  
Reference semantics; interoperability; recommendation.

**Notes**  
Examples include `replyTo`, `quotes`, `derivedFrom`, `supersedes`, `memberOf`, `attachedTo`, `endorses` and `labels`.

---

## REM-03-277 — Logical-record reference

**Source**  
Section 25.1: “A reference may point to the current logical record...”

**Requirement**  
A reference MAY point to the continuing logical record without pinning a specific historical version.

**Classification**  
Reference target; logical identity; versioning.

**Notes**  
Resolution of such a reference may produce the current version at access time.

---

## REM-03-278 — Version-pinned reference

**Source**  
Section 25.1: “A reference may point to... a specific historical version.”

**Requirement**  
A reference MAY identify a specific historical Record Version.

**Classification**  
Reference target; historical identity; versioning.

**Notes**  
Version pinning is appropriate where the exact observed state matters.

---

## REM-03-279 — Exact-version references for quotations and signed assertions

**Source**  
Section 25.1: “A quotation or signed assertion may need to reference the exact version observed at the time.”

**Requirement**  
A quotation or signed assertion SHOULD use a version-pinned reference where verification depends on the exact state observed at the time.

**Classification**  
Integrity; quotation provenance; signed assertions; recommendation.

**Notes**  
Referencing only the current logical record could later resolve to altered content.

---

## REM-03-280 — Reference survival after target unavailability

**Source**  
Section 25.2: “The referring record remains valid...” after the target becomes deleted, restricted, unavailable, migrated or application-blocked.

**Requirement**  
A referring record MUST NOT become invalid solely because its referenced target later becomes deleted, restricted, unavailable, migrated or blocked by an application.

**Classification**  
Referential resilience; record validity; lifecycle.

**Notes**  
The reference may become unresolved or inaccessible without invalidating the referring record itself.

---

## REM-03-281 — Accurate handling of unavailable targets

**Source**  
Section 25.2: “...the application must handle the unavailable target accurately.”

**Requirement**  
An application MUST accurately represent and handle a referenced target that is unavailable, restricted, deleted, migrated or blocked.

**Classification**  
Application behaviour; broken references; presentation accuracy.

**Notes**  
The application must not fabricate target content, silently substitute another record or falsely claim that the referring record is invalid.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 21–25 of `design-notes/03-record-model.md`.
- Section 26 and later content was excluded.
- Examples were used only to clarify source meaning and were not promoted into mandatory final syntax.

## Numbering verification

- First requirement: `REM-03-245`.
- Final requirement: `REM-03-281`.
- Requirement numbering continues directly from Part 4.
- Requirement identifiers are continuous, unique and ordered according to source section sequence.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, definition or necessary decomposition of a compound rule.
- Deletion metadata and deletion modes were extracted separately because each creates an independently testable obligation or semantic state.
- Expiration interpretations were retained as schema options rather than universal consequences.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or schema options.
- Descriptive definitions were converted into testable requirements without strengthening optional source language.

## Editorial verification

- Provider removal remains distinct from canonical deletion.
- Content erasure remains distinct from soft deletion and legal restriction.
- Tombstones minimise deleted-content retention while preserving repository and identifier integrity.
- Restoration creates a new version and does not erase deletion history.
- Expiration consequences remain schema-defined and are not conflated.
- Broken or unavailable references do not invalidate the referring record, while applications remain responsible for accurate handling.
