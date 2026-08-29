# REM-03 Part 7 — Record Requirement Extraction Matrix (Sections 31–35)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 31–35 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

31. Application-specific records
32. Schema extension
33. Record translation
34. Canonical records and projections
35. Comments and replies

Requirement identifiers continue sequentially from Part 6, beginning with `REM-03-323`.

---

# 31. Application-specific records

## REM-03-323 — Custom record-type definition

**Source**  
Section 31: “An application may define a custom record type.”

**Requirement**  
An application MAY define a custom Relay record type.

**Classification**  
Schema extensibility; application-defined records; permissionless innovation.

**Notes**  
A custom type remains subject to the wider Relay requirements for schema definition, repository acceptance and record portability.

---

## REM-03-324 — Portable custom records

**Source**  
Section 31: “A custom record should remain portable even if only one application currently understands it.”

**Requirement**  
A custom record SHOULD remain portable even where only one application currently implements or understands its schema.

**Classification**  
Portability; application independence; recommendation.

**Notes**  
Limited ecosystem support does not justify binding the record permanently to the originating application.

---

## REM-03-325 — Preservation without rendering

**Source**  
Section 31: “A new application may... preserve it without rendering it.”

**Requirement**  
An application MAY preserve an unsupported custom record without rendering its schema-defined content.

**Classification**  
Forward compatibility; preservation; application behaviour.

**Notes**  
Preservation allows records to survive transitions through applications that do not yet understand their schema.

---

## REM-03-326 — Limited metadata rendering

**Source**  
Section 31: “A new application may... render limited metadata.”

**Requirement**  
An application MAY render only the protocol-level or otherwise understood metadata of a custom record whose full schema it does not implement.

**Classification**  
Graceful degradation; metadata presentation; interoperability.

**Notes**  
Limited rendering must not imply that the application has fully interpreted or validated unsupported schema content.

---

## REM-03-327 — Interpretation after schema implementation

**Source**  
Section 31: “A new application may... interpret it after implementing the schema.”

**Requirement**  
An application MAY interpret a custom record after implementing the applicable schema.

**Classification**  
Schema implementation; interoperability; application capability.

**Notes**  
Interpretation should follow the schema’s declared structure, semantics and compatibility rules.

---

## REM-03-328 — Permissioned transformation of custom records

**Source**  
Section 31: “A new application may... transform it into another schema with permission.”

**Requirement**  
An application MAY transform a custom record into another schema only where the required permission has been obtained.

**Classification**  
Schema transformation; controller authority; application behaviour.

**Notes**  
Section 33 provides additional provenance and source-preservation requirements for translated records.

---

## REM-03-329 — Prohibition on anti-competitive obscurity

**Source**  
Section 31: “The originating application must not encrypt or obscure the record solely to prevent competing clients from using it...”

**Requirement**  
The originating application MUST NOT encrypt, encode or otherwise obscure a record solely to prevent competing clients from using, preserving or interpreting it.

**Classification**  
Application independence; anti-lock-in; interoperability.

**Notes**  
This prohibition targets deliberate competitive exclusion rather than legitimate confidentiality or security controls.

---

## REM-03-330 — Security-based encryption exception

**Source**  
Section 31: “...unless the content genuinely requires encryption for user security.”

**Requirement**  
An originating application MAY encrypt or obscure record content where that protection is genuinely required for user security.

**Classification**  
Security; confidentiality; exception handling.

**Notes**  
The security purpose must be genuine and must not be used as a pretext for application lock-in.

---

# 32. Schema extension

## REM-03-331 — Controlled schema extension

**Source**  
Section 32: “Relay should allow controlled schema extension.”

**Requirement**  
Relay SHOULD support controlled extension of existing schemas.

**Classification**  
Schema extensibility; interoperability; recommendation.

**Notes**  
“Controlled” indicates that extensions must remain identifiable and must not undermine required core semantics.

---

## REM-03-332 — Optional extension fields

**Source**  
Section 32, possible approach: “optional extension fields”.

**Requirement**  
A schema extension mechanism MAY support optional extension fields.

**Classification**  
Schema extensibility; optional metadata.

**Notes**  
Applications that do not understand an optional extension should still be able to preserve the underlying record.

---

## REM-03-333 — Referenced extension records

**Source**  
Section 32, possible approach: “referenced extension records”.

**Requirement**  
A schema extension mechanism MAY represent additional information through separately referenced extension records.

**Classification**  
Schema extensibility; composability; record references.

**Notes**  
Separate records can reduce mutation of the base record and allow independent authority or lifecycle rules.

---

## REM-03-334 — Schema inheritance

**Source**  
Section 32, possible approach: “schema inheritance”.

**Requirement**  
A schema extension mechanism MAY support schema inheritance.

**Classification**  
Schema extensibility; reuse; compatibility.

**Notes**  
Inheritance must not change the established meaning of inherited required core fields.

---

## REM-03-335 — Namespaced metadata

**Source**  
Section 32, possible approach: “namespaced metadata”.

**Requirement**  
A schema extension mechanism MAY support namespaced metadata.

**Classification**  
Namespace management; extensibility; collision avoidance.

**Notes**  
Namespacing allows independently defined extensions to coexist without redefining or colliding with core fields.

---

## REM-03-336 — Core-field semantic immutability

**Source**  
Section 32: “Extensions must not redefine the meaning of required core fields.”

**Requirement**  
A schema extension MUST NOT redefine, contradict or replace the established meaning of any required core field.

**Classification**  
Core interoperability; schema integrity; extension constraints.

**Notes**  
Extensions may add information but cannot silently change the semantics on which other implementations rely.

---

## REM-03-337 — Ignoring unsupported extensions

**Source**  
Section 32: “Another application may ignore the extension while preserving it.”

**Requirement**  
An application MAY ignore an extension it does not understand.

**Classification**  
Forward compatibility; application behaviour.

**Notes**  
Ignoring means declining to interpret or use the extension, not deleting it.

---

## REM-03-338 — Preservation of unsupported extensions

**Source**  
Section 32: “Another application may ignore the extension while preserving it.”

**Requirement**  
An application that ignores an unsupported extension SHOULD preserve that extension when reading, storing or rewriting the record.

**Classification**  
Data preservation; forward compatibility; recommendation.

**Notes**  
Preservation prevents applications with partial schema support from causing silent information loss.

---

# 33. Record translation

## REM-03-339 — Schema translation capability

**Source**  
Section 33: “Applications may translate one record schema into another.”

**Requirement**  
An application MAY translate a record from one schema into another schema.

**Classification**  
Schema translation; interoperability; migration.

**Notes**  
Translation may be lossy or reversible, but those characteristics must be disclosed through provenance.

---

## REM-03-340 — Source Record URI provenance

**Source**  
Section 33: “A translated record must preserve provenance, including: source Record URI...”

**Requirement**  
A translated record MUST preserve the source Record URI in its provenance.

**Classification**  
Translation provenance; source traceability.

**Notes**  
The source URI links the translated result to the logical record from which it was derived.

---

## REM-03-341 — Source schema provenance

**Source**  
Section 33: “A translated record must preserve provenance, including... source schema...”

**Requirement**  
A translated record MUST preserve the identifier of the source schema in its provenance.

**Classification**  
Translation provenance; schema traceability.

**Notes**  
The source schema is necessary to understand the original semantics and assess the transformation.

---

## REM-03-342 — Transformation-application provenance

**Source**  
Section 33: “A translated record must preserve provenance, including... transformation application...”

**Requirement**  
A translated record MUST identify the application or agent that performed the transformation.

**Classification**  
Translation provenance; application accountability.

**Notes**  
This identifies the party responsible for applying the translation logic.

---

## REM-03-343 — Transformation-time provenance

**Source**  
Section 33: “A translated record must preserve provenance, including... transformation time...”

**Requirement**  
A translated record MUST record when the transformation occurred.

**Classification**  
Translation provenance; temporal metadata.

**Notes**  
Transformation time is distinct from the source record’s creation or update time.

---

## REM-03-344 — Reversibility disclosure

**Source**  
Section 33: “A translated record must preserve provenance, including... whether the translation is reversible...”

**Requirement**  
A translated record MUST state whether the translation is reversible.

**Classification**  
Translation quality; provenance; information preservation.

**Notes**  
A translation is reversible only where the source representation can be reconstructed without unrecorded loss.

---

## REM-03-345 — Omitted-information disclosure

**Source**  
Section 33: “A translated record must preserve provenance, including... any information omitted.”

**Requirement**  
A translated record MUST disclose any source information omitted during translation.

**Classification**  
Translation transparency; provenance; data loss disclosure.

**Notes**  
This prevents a lossy translation from being mistaken for a complete representation of the source.

---

## REM-03-346 — No silent replacement of source records

**Source**  
Section 33: “Translation must not silently replace the source record unless the controller explicitly authorises that change.”

**Requirement**  
A translation operation MUST NOT silently replace the source record.

**Classification**  
Source preservation; controller authority; translation safety.

**Notes**  
By default, the translated record is a derived object rather than an implicit overwrite of the source.

---

## REM-03-347 — Explicit authority for source replacement

**Source**  
Section 33: “...unless the controller explicitly authorises that change.”

**Requirement**  
A translated record MAY replace its source record only where the controller explicitly authorises the replacement.

**Classification**  
Controller authority; lifecycle; translation.

**Notes**  
The authorisation should be explicit and recorded through the repository operation accepting the change.

---

# 34. Canonical records and projections

## REM-03-348 — Projection definition

**Source**  
Section 34: “A Projection is an application-specific representation derived from one or more records.”

**Requirement**  
A Projection MUST be treated as an application-specific representation derived from one or more source records.

**Classification**  
Derived data; application presentation; conceptual definition.

**Notes**  
Examples include feed cards, profile pages, search results, résumés and recommendation scores.

---

## REM-03-349 — Projection not automatically canonical

**Source**  
Section 34: “A projection is not automatically a Relay Record.”

**Requirement**  
An application-generated Projection MUST NOT be treated as a canonical Relay Record merely because it was derived or displayed.

**Classification**  
Canonical-state boundary; derived data; repository hygiene.

**Notes**  
Derived application views remain outside canonical repository history unless deliberately saved.

---

## REM-03-350 — Deliberate saving requirement

**Source**  
Section 34: “It becomes a repository record only if the controller deliberately saves it.”

**Requirement**  
A Projection MUST become a repository record only when the controller deliberately saves it through an authorised repository operation.

**Classification**  
Controller intent; repository acceptance; canonical state.

**Notes**  
Automatic generation, caching or display does not satisfy the deliberate-saving requirement.

---

## REM-03-351 — Prevention of projection pollution

**Source**  
Section 34: “This distinction prevents application-generated views from polluting the person’s canonical history.”

**Requirement**  
Applications SHOULD preserve the distinction between Projections and repository records so that transient or application-generated views do not pollute the controller’s canonical history.

**Classification**  
Repository hygiene; data minimisation; recommendation.

**Notes**  
The requirement supports meaningful canonical history rather than indiscriminate persistence of every derived presentation.

---

# 35. Comments and replies

## REM-03-352 — Reply stored in replying identity’s repository

**Source**  
Section 35: “A reply should normally be a record in the replying identity’s repository.”

**Requirement**  
A reply SHOULD normally be represented as a record in the repository of the identity that created the reply.

**Classification**  
Reply ownership; repository authority; recommendation.

**Notes**  
The source allows exceptional arrangements but establishes the replying identity’s repository as the normal canonical location.

---

## REM-03-353 — Reply reference to target record

**Source**  
Section 35 example: Bob’s reply contains `replyTo` referencing Alice’s post.

**Requirement**  
A reply record SHOULD identify the record to which it replies using the target’s stable Record URI or an equivalent schema-defined reference.

**Classification**  
Record references; reply semantics; interoperability.

**Notes**  
The `replyTo` field name is illustrative; the applicable schema defines the final field structure.

---

## REM-03-354 — Indexing and display by target-side services

**Source**  
Section 35: “Alice’s provider or application may index and display Bob’s reply...”

**Requirement**  
The provider or application serving the target record MAY index and display a reply stored in another identity’s repository.

**Classification**  
Cross-repository discovery; application presentation; indexing.

**Notes**  
Indexing or display does not transfer canonical authority over the reply.

---

## REM-03-355 — Reply repository remains canonical source

**Source**  
Section 35: “...but Bob’s repository remains the canonical source of the reply.”

**Requirement**  
The replying identity’s repository MUST remain the canonical source of the reply unless an explicitly authorised protocol operation changes that authority.

**Classification**  
Canonical source; repository authority; reply ownership.

**Notes**  
Copies, indexes and cached renderings are secondary representations.

---

## REM-03-356 — Cross-client reply editing

**Source**  
Section 35: “Bob can edit or delete the reply through another client.”

**Requirement**  
The replying identity SHOULD be able to edit the reply through an authorised client other than the application that originally created it.

**Classification**  
Application independence; portability; user control.

**Notes**  
Editing remains subject to the reply schema, repository permissions and versioning rules.

---

## REM-03-357 — Cross-client reply deletion

**Source**  
Section 35: “Bob can edit or delete the reply through another client.”

**Requirement**  
The replying identity SHOULD be able to delete the reply through an authorised client other than the application that originally created it.

**Classification**  
Application independence; deletion; user control.

**Notes**  
Deletion remains subject to the repository’s deletion and tombstone requirements.

---

## REM-03-358 — Target author does not own reply

**Source**  
Section 35: “Alice does not own Bob’s comment.”

**Requirement**  
The identity controlling the target record MUST NOT be treated as the owner or controller of another identity’s reply merely because the reply references that target.

**Classification**  
Ownership separation; repository authority; relationship records.

**Notes**  
The target-side application may moderate display without acquiring canonical control of the reply record.

---

## REM-03-359 — Application-specific moderation policies

**Source**  
Section 35: “different applications may apply different moderation policies”.

**Requirement**  
Different applications MAY apply different moderation or display policies to the same reply.

**Classification**  
Application autonomy; moderation; presentation policy.

**Notes**  
Application-level moderation affects presentation or availability within that application and does not automatically alter the canonical reply.

---

## REM-03-360 — Reply survival beyond originating application

**Source**  
Section 35: “the reply survives the disappearance of the application used to create it.”

**Requirement**  
A canonical reply SHOULD remain available through its repository independently of the continued existence of the application that created it.

**Classification**  
Application independence; persistence; portability.

**Notes**  
This outcome depends on repository continuity and reinforces why the application is not the canonical owner of the reply.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 31–35 of `design-notes/03-record-model.md`.
- Section 36 and later content was excluded.
- Examples were used to clarify meaning and were not promoted into final mandatory field names or serialisation syntax.

## Numbering verification

- First requirement: `REM-03-323`.
- Final requirement: `REM-03-360`.
- Requirement numbering continues directly from Part 6.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit sentence, list item, definition or necessary decomposition of a compound source statement.
- Distinct translation-provenance fields were extracted separately because each is independently testable.
- Application permissions and recommendations were preserved as `MAY` and `SHOULD` rather than strengthened into unconditional mandates.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- Descriptive statements were converted into normative form only where needed to express a testable model rule without changing their meaning.

## Editorial verification

- Custom-schema portability remains separate from universal schema support.
- Legitimate security encryption remains permitted while anti-competitive obscurity is prohibited.
- Extensions cannot redefine required core-field semantics.
- Translation preserves source provenance and cannot silently replace the source.
- Projections remain non-canonical unless deliberately saved by the controller.
- Reply indexing and moderation remain separate from canonical repository authority over the reply.
