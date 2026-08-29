# REM-03 Part 1 — Record Requirement Extraction Matrix (Sections 1–5)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 1–5 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

1. Definition
2. Purpose
3. Record envelope and record content
4. Required envelope fields
5. Record URI

Requirement identifiers use the form `REM-03-XXX` and continue sequentially throughout this part.

---

# 1. Definition

## REM-03-001 — Structured record representation

**Source**  
Section 1, paragraph 1: “A Relay Record is a structured, independently addressable unit of information accepted into a Relay Repository.”

**Requirement**  
A Relay Record MUST be represented as a structured unit of information rather than as an unstructured or application-private object.

**Classification**  
Core object definition; structural requirement.

**Notes**  
The source does not prescribe a final serialisation format in this section. “Structured” therefore establishes a protocol-level expectation that the record can be parsed, validated and interpreted according to defined fields or schema rules.

---

## REM-03-002 — Independent addressability

**Source**  
Section 1, paragraph 1: “A Relay Record is a structured, independently addressable unit of information accepted into a Relay Repository.”

**Requirement**  
Each Relay Record MUST be independently addressable.

**Classification**  
Identification; addressing; interoperability.

**Notes**  
Independent addressability means that a record must be capable of being identified and referenced without relying solely on its position inside another object, an application-specific database row or an application-owned URL.

---

## REM-03-003 — Repository acceptance

**Source**  
Section 1, paragraph 1: “A Relay Record is a structured, independently addressable unit of information accepted into a Relay Repository.”

**Requirement**  
An information object MUST NOT be treated as a canonical Relay Record until it has been accepted into a Relay Repository.

**Classification**  
Repository authority; canonical state; lifecycle.

**Notes**  
This requirement distinguishes locally generated or application-held objects from repository-accepted protocol records.

---

## REM-03-004 — Permitted record subject matter

**Source**  
Section 1, paragraph 2: “A record represents a specific object, statement, action or relationship associated with a Relay Identity.”

**Requirement**  
A Relay Record MUST represent a specific object, statement, action or relationship associated with a Relay Identity.

**Classification**  
Semantic scope; identity association.

**Notes**  
The listed categories are broad semantic classes, not a closed enumeration of schema types.

---

## REM-03-005 — Support for diverse record types

**Source**  
Section 1, examples: profile, post, article, project, photograph, comment, reaction, relationship declaration, application preference, credential, permission grant, moderation label and deletion marker.

**Requirement**  
The Relay Record Model MUST be capable of representing multiple categories of digital object, including content, activity, relationship, preference, credential, authority, moderation and deletion-related records.

**Classification**  
Extensibility; data-model breadth; interoperability.

**Notes**  
The examples are illustrative. Implementations must not interpret the list as limiting the protocol to those record types.

---

## REM-03-006 — Application-independent definition

**Source**  
Section 1: “A record is not defined by the application that created it.”

**Requirement**  
A Relay Record MUST be defined independently of the application that created, submitted or first displayed it.

**Classification**  
Application independence; portability; interoperability.

**Notes**  
Record meaning and validity must derive from protocol metadata, schema and repository state rather than from proprietary application behaviour.

---

## REM-03-007 — Application interaction without application ownership

**Source**  
Section 1: “An application may create, edit or display a record, but the record belongs to the repository in which it was authorised.”

**Requirement**  
An application MAY create, edit or display a Relay Record only through valid protocol and repository-authorised operations, but such interaction MUST NOT establish application ownership of the record.

**Classification**  
Application interaction; authority separation; ownership.

**Notes**  
The source permits application participation while expressly separating that participation from record control.

---

## REM-03-008 — Repository-based record control

**Source**  
Section 1: “An application may create, edit or display a record, but the record belongs to the repository in which it was authorised.”

**Requirement**  
Control of a Relay Record MUST be anchored in the Relay Repository in which the record was authorised.

**Classification**  
Repository authority; control; ownership.

**Notes**  
“Belongs to the repository” is treated here as a control and authority rule, not as a statement about legal ownership under external law.

---

# 2. Purpose

## REM-03-009 — Cross-application usability

**Source**  
Section 2, paragraph 1: “The Relay Record Model exists to make digital objects usable across applications without making every application interpret all information identically.”

**Requirement**  
The Relay Record Model MUST enable digital objects to be used across multiple applications.

**Classification**  
Interoperability; portability; application independence.

**Notes**  
Cross-application usability is a primary purpose of the record model and should guide schema, addressing and validation decisions.

---

## REM-03-010 — Interpretation flexibility

**Source**  
Section 2, paragraph 1: “...without making every application interpret all information identically.”

**Requirement**  
The Relay Record Model MUST NOT require every application to interpret, present or use all record information identically.

**Classification**  
Application autonomy; extensibility; presentation independence.

**Notes**  
This preserves interoperability at the protocol level without imposing a single application experience or semantic presentation layer.

---

## REM-03-011 — Record location support

**Source**  
Section 2, consistency objective: applications must be able to “locate a record”.

**Requirement**  
The Relay Record Model MUST provide sufficient consistent information for an application to locate a record.

**Classification**  
Discovery; addressing; interoperability.

**Notes**  
The source does not define the complete resolution mechanism in Sections 1–5, but it establishes location as a required capability of the model.

---

## REM-03-012 — Record-type determination

**Source**  
Section 2, consistency objective: applications must be able to “determine its type”.

**Requirement**  
The Relay Record Model MUST provide sufficient consistent information for an application to determine a record’s type.

**Classification**  
Schema identification; interoperability.

**Notes**  
Section 4 later identifies the schema identifier as required envelope information.

---

## REM-03-013 — Structural validation support

**Source**  
Section 2, consistency objective: applications must be able to “validate its structure”.

**Requirement**  
The Relay Record Model MUST provide sufficient consistent information for an application to validate a record’s structure.

**Classification**  
Validation; schema conformance.

**Notes**  
This requirement does not imply that every application must implement every schema, only that the model exposes enough information for validation where support exists.

---

## REM-03-014 — Repository-history verification support

**Source**  
Section 2, consistency objective: applications must be able to “verify its repository history”.

**Requirement**  
The Relay Record Model MUST provide sufficient consistent information for an application to verify a record’s repository history.

**Classification**  
Integrity; provenance; repository history.

**Notes**  
The detailed commit and verification mechanisms are outside Sections 1–5, but the capability is required here as a design objective.

---

## REM-03-015 — Authorising-identity determination

**Source**  
Section 2, consistency objective: applications must be able to “understand who authorised it”.

**Requirement**  
The Relay Record Model MUST expose sufficient information for an application to determine which Relay Identity authorised the record.

**Classification**  
Authority; identity; accountability.

**Notes**  
This is separate from determining which application transmitted or displayed the record.

---

## REM-03-016 — Visibility determination

**Source**  
Section 2, consistency objective: applications must be able to “determine its visibility”.

**Requirement**  
The Relay Record Model MUST expose sufficient information for an application to determine a record’s visibility classification.

**Classification**  
Access control; visibility; metadata.

**Notes**  
Section 4 identifies visibility classification as required envelope information.

---

## REM-03-017 — Current-version identification

**Source**  
Section 2, consistency objective: applications must be able to “identify its current version”.

**Requirement**  
The Relay Record Model MUST provide sufficient information for an application to identify the current version of a logical record.

**Classification**  
Versioning; state management; consistency.

**Notes**  
The detailed version model appears in later sections of the source, but current-version identification is already an explicit purpose requirement.

---

## REM-03-018 — Migration preservation

**Source**  
Section 2, consistency objective: applications must be able to “preserve it during migration”.

**Requirement**  
The Relay Record Model MUST support preservation of a record during repository or provider migration.

**Classification**  
Portability; migration; persistence.

**Notes**  
Preservation includes maintaining the logical identity and required protocol information of the record across migration.

---

## REM-03-019 — Inter-record references

**Source**  
Section 2, consistency objective: applications must be able to “refer to it from other records”.

**Requirement**  
The Relay Record Model MUST allow one record to be referenced from another record.

**Classification**  
Referential integrity; relationships; interoperability.

**Notes**  
Independent addressability and stable Record URIs provide the basis for this capability.

---

## REM-03-020 — Permissionless schema extensibility

**Source**  
Section 2: “The model must allow third parties to introduce new record types without requiring permission from a central platform.”

**Requirement**  
The Relay Record Model MUST allow third parties to introduce new record types without obtaining permission from a central platform.

**Classification**  
Extensibility; decentralisation; governance.

**Notes**  
This does not remove the need for schemas, namespaces, validation rules or repository acceptance. It prevents a central platform from being the mandatory gatekeeper for defining new record types.

---

# 3. Record envelope and record content

## REM-03-021 — Two-layer conceptual model

**Source**  
Section 3: “Every Relay Record consists of two conceptual layers: 1. the Record Envelope; 2. the Record Content.”

**Requirement**  
Every Relay Record MUST consist conceptually of a Record Envelope and Record Content.

**Classification**  
Core structure; data model.

**Notes**  
The requirement is conceptual and does not require a particular physical storage layout. An implementation may serialise the layers together provided their roles remain distinguishable.

---

## REM-03-022 — Envelope responsibility

**Source**  
Section 3: “The envelope contains protocol-level metadata required for identification, verification, access and interoperability.”

**Requirement**  
The Record Envelope MUST contain the protocol-level metadata required to identify, verify, access and interoperate with the record.

**Classification**  
Protocol metadata; envelope structure.

**Notes**  
Schema-specific content must not be relied upon as the sole source of protocol-level identity, access or verification information where the envelope is defined to carry it.

---

## REM-03-023 — Content responsibility

**Source**  
Section 3: “The content contains the information defined by the record’s schema.”

**Requirement**  
Record Content MUST contain the information defined by the record’s declared schema.

**Classification**  
Schema conformance; content structure.

**Notes**  
The content layer is schema-governed, while the envelope carries cross-schema protocol metadata.

---

## REM-03-024 — Separation of protocol metadata and schema content

**Source**  
Section 3, combined description of Record Envelope and Record Content.

**Requirement**  
Implementations MUST preserve a clear semantic separation between protocol-level envelope metadata and schema-defined record content.

**Classification**  
Separation of concerns; interoperability; validation.

**Notes**  
This requirement is derived directly from the source’s explicit two-layer model. It does not require two separate files or database objects.

---

## REM-03-025 — Provisional serialisation

**Source**  
Section 3: “The exact serialisation remains provisional.”

**Requirement**  
Relay v0.1 implementations MUST NOT treat the example serialisation in Section 3 as a final, fixed or exhaustive wire-format specification.

**Classification**  
Specification status; implementation caution.

**Notes**  
The example demonstrates conceptual fields and nesting. It is informative rather than a final normative serialisation contract.

---

# 4. Required envelope fields

## REM-03-026 — Required active-record envelope information

**Source**  
Section 4: “Every active Relay Record must include or inherit the following information...”

**Requirement**  
Every active Relay Record MUST include or inherit all protocol-required envelope information defined by the Relay Record Model.

**Classification**  
Envelope completeness; active-record validity.

**Notes**  
“Inherit” allows required information to be supplied through a valid enclosing repository, collection or protocol context rather than duplicated in every serialised record, provided it remains unambiguous and verifiable.

---

## REM-03-027 — Record URI information

**Source**  
Section 4, required information: “Record URI”.

**Requirement**  
Every active Relay Record MUST include or inherit a Record URI.

**Classification**  
Identification; addressing.

**Notes**  
The Record URI is further defined in Section 5 as the stable identifier of the logical record.

---

## REM-03-028 — Repository Identifier information

**Source**  
Section 4, required information: “Repository Identifier”.

**Requirement**  
Every active Relay Record MUST include or inherit the identifier of the Relay Repository in which it is authorised.

**Classification**  
Repository identity; authority; routing.

**Notes**  
The repository identifier must be sufficient to associate the record with its authoritative repository context.

---

## REM-03-029 — Collection information

**Source**  
Section 4, required information: “collection”.

**Requirement**  
Every active Relay Record MUST include or inherit its collection identifier.

**Classification**  
Organisation; schema grouping; addressing.

**Notes**  
The collection contributes to record organisation and, in the example URI, forms part of the logical address.

---

## REM-03-030 — Record Key information

**Source**  
Section 4, required information: “Record Key”.

**Requirement**  
Every active Relay Record MUST include or inherit a Record Key.

**Classification**  
Identification; uniqueness; addressing.

**Notes**  
The source does not define the complete uniqueness scope in Sections 1–5, but the example places the Record Key within a repository and collection context.

---

## REM-03-031 — Schema identifier information

**Source**  
Section 4, required information: “schema identifier”.

**Requirement**  
Every active Relay Record MUST include or inherit a schema identifier.

**Classification**  
Schema identification; validation; interoperability.

**Notes**  
The schema identifier enables applications to determine the record type and validate its content structure.

---

## REM-03-032 — Creation time information

**Source**  
Section 4, required information: “creation time”.

**Requirement**  
Every active Relay Record MUST include or inherit its creation time.

**Classification**  
Temporal metadata; lifecycle.

**Notes**  
The source does not specify timestamp syntax in Sections 1–5, although the example uses an ISO 8601 UTC timestamp.

---

## REM-03-033 — Current update time information

**Source**  
Section 4, required information: “current update time”.

**Requirement**  
Every active Relay Record MUST include or inherit the time of its current accepted update.

**Classification**  
Temporal metadata; version state.

**Notes**  
This value must represent the current accepted record state rather than an unaccepted local edit.

---

## REM-03-034 — Authorising Relay Identity information

**Source**  
Section 4, required information: “authorising Relay Identity”.

**Requirement**  
Every active Relay Record MUST include or inherit the identity of the Relay Identity that authorised it.

**Classification**  
Authority; identity; accountability.

**Notes**  
The authorising identity is not necessarily the same as the submitting application, subject or issuer.

---

## REM-03-035 — Visibility classification information

**Source**  
Section 4, required information: “visibility classification”.

**Requirement**  
Every active Relay Record MUST include or inherit a visibility classification.

**Classification**  
Access control; visibility metadata.

**Notes**  
The detailed visibility classes are defined later in the source model.

---

## REM-03-036 — Content information

**Source**  
Section 4, required information: “content”.

**Requirement**  
Every active Relay Record MUST include or inherit schema-defined content.

**Classification**  
Record payload; schema conformance.

**Notes**  
For deletion markers or other specialised schemas, the required content may be minimal, but it must still conform to the applicable schema.

---

## REM-03-037 — Integrity reference information

**Source**  
Section 4, required information: “integrity reference”.

**Requirement**  
Every active Relay Record MUST include or inherit an integrity reference sufficient to support verification of the accepted record state.

**Classification**  
Integrity; verification; repository history.

**Notes**  
Sections 1–5 do not mandate the exact form of the integrity reference. It may be defined through a commit, hash or other protocol mechanism elsewhere in the specification.

---

## REM-03-038 — Additional schema- or operation-specific fields

**Source**  
Section 4: “Additional fields may be required depending on the schema or operation.”

**Requirement**  
A schema or operation MAY require additional fields beyond the common envelope information, and implementations MUST enforce those additional requirements when applicable.

**Classification**  
Extensibility; schema validation; operation validation.

**Notes**  
The common envelope is a baseline, not an exhaustive definition of every valid record or operation.

---

# 5. Record URI

## REM-03-039 — Stable logical-record identifier

**Source**  
Section 5: “The Record URI is the stable identifier of the logical record.”

**Requirement**  
The Record URI MUST serve as the stable identifier of the logical record.

**Classification**  
Identification; persistence; logical identity.

**Notes**  
The URI identifies the continuing logical object rather than a particular version or storage representation.

---

## REM-03-040 — Stability across record edits

**Source**  
Section 5: “The Record URI must remain stable when the record is edited.”

**Requirement**  
A record edit MUST NOT change the Record URI of the logical record.

**Classification**  
Versioning; identifier stability.

**Notes**  
Edits may create new record versions, but the logical-record URI remains unchanged.

---

## REM-03-041 — Stability across repository-provider changes

**Source**  
Section 5: “The Record URI must remain stable when the repository changes providers.”

**Requirement**  
A change of repository provider MUST NOT change the Record URI of the logical record.

**Classification**  
Portability; provider independence; identifier stability.

**Notes**  
This requirement prevents a storage or hosting provider from becoming embedded as the permanent identity of a record.

---

## REM-03-042 — Stability across identity-handle changes

**Source**  
Section 5: “The Record URI must remain stable when the identity changes handles.”

**Requirement**  
A change to the associated identity’s human-readable handle MUST NOT change the Record URI of the logical record.

**Classification**  
Identity persistence; handle independence; identifier stability.

**Notes**  
The record identifier must rely on stable protocol identity rather than mutable user-facing naming.

---

## REM-03-043 — Stability across application display contexts

**Source**  
Section 5: “The Record URI must remain stable when another application displays it.”

**Requirement**  
The Record URI MUST remain unchanged when the record is resolved, rendered or displayed by a different application.

**Classification**  
Application independence; interoperability; identifier stability.

**Notes**  
Applications may create their own local routes or presentation URLs, but those must not replace or redefine the canonical Record URI.

---

## REM-03-044 — Stability across media-storage changes

**Source**  
Section 5: “The Record URI must remain stable when the media storage location changes.”

**Requirement**  
A change to the storage location of media associated with a record MUST NOT change the Record URI of the logical record.

**Classification**  
Storage independence; portability; identifier stability.

**Notes**  
Media locators may change independently of the record’s stable logical identity.

---

## REM-03-045 — Logical identity distinct from version identity

**Source**  
Section 5: “The Record URI identifies the logical object, not one particular version of its content.”

**Requirement**  
The base Record URI MUST identify the logical record and MUST NOT identify only one particular content version.

**Classification**  
Logical identity; versioning; addressing.

**Notes**  
A separate version reference mechanism is required when a specific historical state must be identified.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 1–5 of `design-notes/03-record-model.md`.
- No requirements from Sections 6 onward were introduced as independent requirements.
- Later-section concepts are mentioned only in notes where necessary to avoid overstating what Sections 1–5 define.

## Numbering verification

- First requirement: `REM-03-001`.
- Final requirement: `REM-03-045`.
- Requirement numbering is continuous with no duplicate or omitted identifiers.
- Section sequence follows the source model: 1, 2, 3, 4, 5.

## Traceability verification

- Every requirement contains a **Source**, **Requirement**, **Classification** and **Notes** field.
- Every requirement is traceable to an explicit sentence, phrase, list item or necessary decomposition of a compound source statement.
- Compound source statements were separated where they create independently testable obligations.
- Illustrative examples were not converted into closed taxonomies or mandatory final syntax.

## Editorial verification

- Normative language uses `MUST`, `MUST NOT` and `MAY` consistently.
- Requirements preserve the source model’s distinction between repository authority, application participation and logical record identity.
- Provisional syntax is identified as provisional and has not been promoted into a final wire-format requirement.
- Explanatory notes do not add new protocol obligations beyond the source.
