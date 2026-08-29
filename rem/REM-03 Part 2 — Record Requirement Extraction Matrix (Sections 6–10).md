# REM-03 Part 2 — Record Requirement Extraction Matrix (Sections 6–10)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 6–10 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

6. Record version
7. Record type and schema
8. Core record categories
9. Singleton and repeatable records
10. Authorship, authority and submission

Requirement identifiers continue sequentially from Part 1, beginning with `REM-03-046`.

---

# 6. Record version

## REM-03-046 — New version for each accepted change

**Source**  
Section 6: “Each accepted change to a record creates a new Record Version.”

**Requirement**  
Each change accepted by the authoritative Relay Repository MUST create a new Record Version.

**Classification**  
Versioning; repository state; lifecycle.

**Notes**  
A local or unaccepted edit does not create a canonical Record Version. Version creation is tied to repository acceptance.

---

## REM-03-047 — Commit-based version identification

**Source**  
Section 6: “A version may be identified by the commit in which it was accepted...”

**Requirement**  
A Record Version MAY be identified by the repository commit in which that version was accepted.

**Classification**  
Version identification; commit history; integrity.

**Notes**  
The source permits, but does not require, commit identity to serve as the sole version identifier.

---

## REM-03-048 — Monotonic version-number identification

**Source**  
Section 6: “A version may be identified by... a monotonically increasing version number...”

**Requirement**  
A Record Version MAY be identified by a monotonically increasing version number.

**Classification**  
Version identification; ordering.

**Notes**  
Where used, the version number must increase monotonically for successive accepted versions of the same logical record.

---

## REM-03-049 — Content-hash version identification

**Source**  
Section 6: “A version may be identified by... a content hash...”

**Requirement**  
A Record Version MAY be identified by a cryptographic or otherwise protocol-approved content hash.

**Classification**  
Version identification; content integrity.

**Notes**  
The source does not select a final hash algorithm in this section.

---

## REM-03-050 — Combined version-identification mechanisms

**Source**  
Section 6: “A version may be identified by... a combination of these.”

**Requirement**  
A Record Version MAY use a combination of commit identity, monotonic version number and content hash for identification.

**Classification**  
Version identification; integrity; interoperability.

**Notes**  
A combined mechanism can provide human-readable ordering, repository traceability and content-level verification simultaneously.

---

## REM-03-051 — Logical identity represented by the Record URI

**Source**  
Section 6.1: “The Record URI identifies the continuing logical record.”

**Requirement**  
The Record URI MUST identify the continuing logical record across its accepted versions.

**Classification**  
Logical identity; persistent addressing; versioning.

**Notes**  
This restates and applies the stable-identifier rule from Section 5 within the version model.

---

## REM-03-052 — Version reference represented separately

**Source**  
Section 6.1: “A version reference identifies a particular historical state.”

**Requirement**  
A version reference MUST identify one particular historical state of a logical record.

**Classification**  
Historical addressing; version identity.

**Notes**  
The version reference is distinct from the base Record URI, which identifies the logical record as a whole.

---

## REM-03-053 — Separation of logical-record and historical-version references

**Source**  
Section 6.1, distinction between the logical record and a specific version.

**Requirement**  
Implementations MUST preserve a clear semantic distinction between a reference to the continuing logical record and a reference to one specific historical version.

**Classification**  
Addressing semantics; versioning; interoperability.

**Notes**  
An implementation must not silently treat the base Record URI as though it were permanently bound to a single historical state.

---

## REM-03-054 — Provisional version-reference syntax

**Source**  
Section 6.1: “The exact version-reference syntax remains open.”

**Requirement**  
Relay v0.1 implementations MUST NOT treat the example `?version=3` syntax as a final or exclusive version-reference format.

**Classification**  
Specification status; implementation caution.

**Notes**  
The example expresses the conceptual distinction between logical and version identity, not a final wire-format decision.

---

## REM-03-055 — Repository declaration of the current version

**Source**  
Section 6.2: “The repository must clearly indicate which version is current.”

**Requirement**  
The authoritative Relay Repository MUST clearly indicate which accepted Record Version is current for each logical record.

**Classification**  
Repository state; current-version resolution; consistency.

**Notes**  
The mechanism may be represented through repository state, commit history, metadata or another protocol-defined method, but the current version must be unambiguous.

---

## REM-03-056 — Stale cached-version disclosure

**Source**  
Section 6.2: “An application must not treat an older cached version as current without identifying that it may be stale.”

**Requirement**  
An application MUST NOT present or process an older cached Record Version as current unless it clearly identifies that the cached version may be stale.

**Classification**  
Client behaviour; cache consistency; user disclosure.

**Notes**  
This does not prohibit offline or cached use. It requires the application to avoid falsely representing uncertain cached state as authoritative current state.

---

# 7. Record type and schema

## REM-03-057 — Schema identifier defines record type

**Source**  
Section 7: “The schema identifier defines the record’s type and structure.”

**Requirement**  
The declared schema identifier MUST define the record’s type.

**Classification**  
Schema identification; record typing.

**Notes**  
Applications should determine protocol record type from the schema identifier rather than from the creating application or presentation context.

---

## REM-03-058 — Schema identifier defines record structure

**Source**  
Section 7: “The schema identifier defines the record’s type and structure.”

**Requirement**  
The declared schema identifier MUST identify the structural rules that apply to the record content.

**Classification**  
Schema identification; structural validation.

**Notes**  
The schema identifier must resolve, directly or indirectly, to sufficient structural rules for validation.

---

## REM-03-059 — Schema definition of required fields

**Source**  
Section 7, schema obligations: “required fields”.

**Requirement**  
A record schema MUST define which fields are required.

**Classification**  
Schema definition; validation.

**Notes**  
Required fields may include schema-specific content fields in addition to protocol-level envelope requirements.

---

## REM-03-060 — Schema definition of optional fields

**Source**  
Section 7, schema obligations: “optional fields”.

**Requirement**  
A record schema MUST define which fields are optional.

**Classification**  
Schema definition; extensibility; validation.

**Notes**  
Fields must not be left ambiguous as to whether their absence invalidates the record.

---

## REM-03-061 — Schema definition of field types

**Source**  
Section 7, schema obligations: “field types”.

**Requirement**  
A record schema MUST define the data type of each schema-governed field.

**Classification**  
Schema definition; type safety; validation.

**Notes**  
Field types may include primitive, structured, reference or protocol-defined types.

---

## REM-03-062 — Schema definition of validation constraints

**Source**  
Section 7, schema obligations: “validation constraints”.

**Requirement**  
A record schema MUST define the validation constraints applicable to its fields and content structure.

**Classification**  
Schema validation; data integrity.

**Notes**  
Constraints may include permitted values, lengths, formats, cardinality or cross-field conditions.

---

## REM-03-063 — Schema definition of field meaning

**Source**  
Section 7, schema obligations: “meaning of each field”.

**Requirement**  
A record schema MUST define the semantic meaning of each schema-governed field.

**Classification**  
Semantic interoperability; schema documentation.

**Notes**  
Structural type alone is insufficient for interoperability where applications cannot determine what a field represents.

---

## REM-03-064 — Schema definition of supported operations

**Source**  
Section 7, schema obligations: “supported operations”.

**Requirement**  
A record schema MUST define which operations are supported for records conforming to that schema.

**Classification**  
Schema behaviour; lifecycle; operation validation.

**Notes**  
Supported operations may include creation, update, supersession, expiration or other schema-defined actions.

---

## REM-03-065 — Schema definition of compatibility rules

**Source**  
Section 7, schema obligations: “compatibility rules”.

**Requirement**  
A record schema MUST define its compatibility rules.

**Classification**  
Schema evolution; interoperability; version compatibility.

**Notes**  
Compatibility rules should enable implementations to determine whether records or schema versions can be interpreted, migrated or processed together.

---

## REM-03-066 — Schema definition of singleton or repeatable status

**Source**  
Section 7, schema obligations: “whether the record is singleton or repeatable”.

**Requirement**  
A record schema MUST define whether its records are singleton or repeatable within the applicable repository context.

**Classification**  
Cardinality; schema behaviour; repository-state validation.

**Notes**  
Section 9 defines the meaning of singleton and repeatable records.

---

## REM-03-067 — Schema definition of update or supersession behaviour

**Source**  
Section 7, schema obligations: “whether updates or only superseding records are allowed.”

**Requirement**  
A record schema MUST define whether an existing logical record may be updated or whether changes must be represented through a new superseding record.

**Classification**  
Lifecycle; versioning; schema behaviour.

**Notes**  
This distinction affects logical identity, history and repository-state validation.

---

## REM-03-068 — Schema namespace does not establish application ownership

**Source**  
Section 7.1: a record using `com.example.music.track.v1` “does not belong to Example Music.”

**Requirement**  
Use of an application-associated or organisation-associated schema namespace MUST NOT be interpreted as ownership of conforming records by that application or organisation.

**Classification**  
Ownership separation; schema namespace; application independence.

**Notes**  
A schema authority may define a type without controlling every record that uses it.

---

## REM-03-069 — Namespace identifies schema authority

**Source**  
Section 7.1: “The namespace identifies the schema authority.”

**Requirement**  
A schema namespace MUST identify the authority responsible for defining and maintaining that schema.

**Classification**  
Schema governance; namespace authority; accountability.

**Notes**  
Schema authority concerns the definition of the schema, not ownership or repository control of individual records.

---

## REM-03-070 — Repository and identity retain record control

**Source**  
Section 7.1: “The record remains controlled by its repository and authorising identity.”

**Requirement**  
A record using a third-party schema MUST remain controlled by its authoritative repository and authorising Relay Identity.

**Classification**  
Repository authority; identity control; application independence.

**Notes**  
Schema authorship does not displace repository authority or identity authorisation.

---

## REM-03-071 — Schema control of comment-reference behaviour

**Source**  
Section 7.2: schemas may define “whether comments may reference the record”.

**Requirement**  
A schema MAY define whether records representing comments are permitted to reference records of that schema.

**Classification**  
Schema-specific behaviour; references; interaction model.

**Notes**  
The source permits schema-level control but does not require every schema to support comments.

---

## REM-03-072 — Schema control of revision support

**Source**  
Section 7.2: schemas may define “whether the record supports revisions”.

**Requirement**  
A schema MAY define whether conforming records support revisions.

**Classification**  
Schema-specific behaviour; versioning.

**Notes**  
A schema that does not support revisions may require superseding records instead of updates.

---

## REM-03-073 — Schema control of expiration

**Source**  
Section 7.2: schemas may define “whether the record can expire”.

**Requirement**  
A schema MAY define whether conforming records can expire.

**Classification**  
Schema-specific behaviour; lifecycle.

**Notes**  
Where expiration is supported, the schema should define the relevant fields and state consequences.

---

## REM-03-074 — Schema control of public visibility eligibility

**Source**  
Section 7.2: schemas may define “whether the record may be public”.

**Requirement**  
A schema MAY restrict whether conforming records are eligible for public visibility.

**Classification**  
Schema-specific behaviour; visibility; access control.

**Notes**  
A repository or application must not assign public visibility where the applicable schema prohibits it.

---

## REM-03-075 — Schema declaration of Record URI fields

**Source**  
Section 7.2: schemas may define “whether a field contains another Record URI”.

**Requirement**  
A schema MAY define that a field contains a reference to another Record URI.

**Classification**  
Referential structure; schema-specific behaviour; interoperability.

**Notes**  
Declaring reference fields enables applications and validators to distinguish protocol references from ordinary strings.

---

## REM-03-076 — Schema control of blob requirements

**Source**  
Section 7.2: schemas may define “whether a blob is required”.

**Requirement**  
A schema MAY require an associated blob for a conforming record.

**Classification**  
Media and binary content; schema-specific behaviour; validation.

**Notes**  
Where a blob is required, the schema should define how the blob is referenced and validated.

---

## REM-03-077 — Schema control of instance cardinality

**Source**  
Section 7.2: schemas may define “whether multiple instances are allowed”.

**Requirement**  
A schema MAY define whether multiple conforming record instances are permitted in the applicable repository context.

**Classification**  
Cardinality; schema-specific behaviour; repository-state validation.

**Notes**  
This overlaps with the required singleton-or-repeatable declaration and describes one behavioural consequence of that declaration.

---

## REM-03-078 — Separation of protocol validation and application presentation

**Source**  
Section 7.2: “Protocol-level validation must remain separate from application-specific presentation.”

**Requirement**  
Protocol-level record validation MUST remain separate from application-specific presentation logic.

**Classification**  
Separation of concerns; validation; application independence.

**Notes**  
A record may be protocol-valid even where a particular application cannot or chooses not to render it. Conversely, attractive or usable presentation does not establish protocol validity.

---

# 8. Core record categories

## REM-03-079 — Broad category distinction

**Source**  
Section 8: “Relay v0.1 should distinguish several broad categories.”

**Requirement**  
Relay v0.1 SHOULD distinguish broad record categories sufficient to describe the principal semantic role of a record.

**Classification**  
Record taxonomy; semantic interoperability; recommendation.

**Notes**  
The source uses “should”, so this is a recommended protocol distinction rather than an unconditional validity requirement.

---

## REM-03-080 — Entity-record category

**Source**  
Section 8.1: “Entity records — Describe a persistent entity or object.”

**Requirement**  
The record-category model SHOULD support an Entity Record category for records that describe a persistent entity or object.

**Classification**  
Record taxonomy; entity modelling; recommendation.

**Notes**  
Examples include profiles, projects, publications, organisations and media items.

---

## REM-03-081 — Activity-record category

**Source**  
Section 8.2: “Activity records — Describe an action or event.”

**Requirement**  
The record-category model SHOULD support an Activity Record category for records that describe an action or event.

**Classification**  
Record taxonomy; event modelling; recommendation.

**Notes**  
Examples include publish, react, follow, endorse, revoke and announce activities.

---

## REM-03-082 — Relationship-record category

**Source**  
Section 8.3: “Relationship records — Describe a directed or mutual relationship between identities or records.”

**Requirement**  
The record-category model SHOULD support a Relationship Record category for directed or mutual relationships between identities or records.

**Classification**  
Record taxonomy; relationship modelling; recommendation.

**Notes**  
Examples include follows, collaborates with, authored, member of and replies to.

---

## REM-03-083 — Authority-record category

**Source**  
Section 8.4: “Authority records — Describe permission or control.”

**Requirement**  
The record-category model SHOULD support an Authority Record category for records that describe permission or control.

**Classification**  
Record taxonomy; authority modelling; recommendation.

**Notes**  
Examples include permission grants, delegated keys, recovery authorities and application authorisations.

---

## REM-03-084 — Assertion-record category

**Source**  
Section 8.5: “Assertion records — Describe a claim.”

**Requirement**  
The record-category model SHOULD support an Assertion Record category for records that describe a claim.

**Classification**  
Record taxonomy; assertion modelling; recommendation.

**Notes**  
Examples include qualifications, employment claims, authorship, verification and moderation labels.

---

## REM-03-085 — Tombstone-record category

**Source**  
Section 8.6: “Tombstone records — Record the deletion or retirement of another record without retaining its full active content.”

**Requirement**  
The record-category model SHOULD support a Tombstone Record category that records the deletion or retirement of another record without retaining that record’s full active content.

**Classification**  
Record taxonomy; deletion state; recommendation.

**Notes**  
A tombstone preserves the fact and target of deletion or retirement while allowing active content to be removed.

---

## REM-03-086 — Shared fields across categories

**Source**  
Section 8.6: “These categories may share common fields while using different schemas.”

**Requirement**  
Different record categories MAY share common fields.

**Classification**  
Schema reuse; extensibility; data modelling.

**Notes**  
Shared fields can support consistent envelope or cross-category semantics without requiring one universal content schema.

---

## REM-03-087 — Different schemas across categories

**Source**  
Section 8.6: “These categories may share common fields while using different schemas.”

**Requirement**  
Records in different categories MAY use different schemas even where they share common fields.

**Classification**  
Schema diversity; extensibility; record taxonomy.

**Notes**  
Category is a broad semantic classification and must not be treated as a substitute for the specific schema identifier.

---

# 9. Singleton and repeatable records

## REM-03-088 — Schema-defined collection cardinality

**Source**  
Section 9: “A schema may define a collection as either singleton or repeatable.”

**Requirement**  
A schema MAY define the applicable collection as singleton or repeatable.

**Classification**  
Cardinality; schema behaviour; collection modelling.

**Notes**  
Section 7 requires the schema to state which model applies; Section 9 defines their meaning.

---

## REM-03-089 — Singleton active-record constraint

**Source**  
Section 9, Singleton: “Only one active logical record of that schema or role exists per repository.”

**Requirement**  
For a singleton schema or role, no more than one active logical record of that schema or role MAY exist in a repository.

**Classification**  
Cardinality; repository-state validation; singleton constraint.

**Notes**  
Historical versions of the singleton logical record may exist. The constraint concerns competing active logical records.

---

## REM-03-090 — Repeatable multiple-record allowance

**Source**  
Section 9, Repeatable: “Multiple records may exist.”

**Requirement**  
For a repeatable schema or collection, multiple logical records MAY exist in the repository.

**Classification**  
Cardinality; collection behaviour.

**Notes**  
The schema and repository may still impose other uniqueness or validation constraints.

---

## REM-03-091 — Preferred singleton-update behaviour

**Source**  
Section 9: “A singleton update should normally create a new version of the same logical record rather than a second competing current record.”

**Requirement**  
An update to a singleton record SHOULD normally create a new version of the existing logical record rather than create a second competing current logical record.

**Classification**  
Versioning; singleton lifecycle; recommendation.

**Notes**  
The source deliberately uses “should normally”, allowing exceptional schema-defined cases while establishing the preferred behaviour.

---

# 10. Authorship, authority and submission

## REM-03-092 — Distinction among subject, authorising identity and submitter

**Source**  
Section 10: “Relay must distinguish between three concepts: subject; authorising identity; submitting application or agent.”

**Requirement**  
The Relay Record Model MUST distinguish the record subject, the authorising identity and the submitting application or agent as separate concepts.

**Classification**  
Authority separation; authorship; accountability.

**Notes**  
The three roles may be fulfilled by related parties but must remain conceptually and representationally distinct.

---

## REM-03-093 — Roles may coincide

**Source**  
Section 10: “These are often the same today, but they do not have to be.”

**Requirement**  
The model MAY permit the subject, authorising identity and submitter to refer to the same entity where factually appropriate.

**Classification**  
Role modelling; flexibility.

**Notes**  
Coincidence of roles must not remove their semantic distinction.

---

## REM-03-094 — Roles may differ

**Source**  
Section 10: “These are often the same today, but they do not have to be.”

**Requirement**  
The model MUST support records in which the subject, authorising identity and submitter are different entities.

**Classification**  
Role modelling; delegation; interoperability.

**Notes**  
This is necessary for credentials, delegated applications, agents and records concerning third parties or external objects.

---

## REM-03-095 — Subject semantics

**Source**  
Section 10.1: “The identity or object the record concerns.”

**Requirement**  
The subject field or equivalent representation MUST identify the identity or object that the record concerns.

**Classification**  
Subject identification; semantic modelling.

**Notes**  
The subject is not necessarily the identity that authorised the record or the agent that submitted it.

---

## REM-03-096 — Authorising-identity semantics

**Source**  
Section 10.2: “The identity under whose repository authority the record is accepted.”

**Requirement**  
The authorising-identity field or equivalent representation MUST identify the identity under whose repository authority the record was accepted.

**Classification**  
Authority; repository acceptance; accountability.

**Notes**  
This role establishes whose repository authority made the record canonical within that repository.

---

## REM-03-097 — Submitter semantics

**Source**  
Section 10.3: “The application or agent that transmitted the operation.”

**Requirement**  
The submitter field or equivalent representation MUST identify the application or agent that transmitted the record operation.

**Classification**  
Submission provenance; application accountability; delegation.

**Notes**  
Transmission does not itself establish authorisation or ownership.

---

## REM-03-098 — Representation without role conflation

**Source**  
Section 10.3: “A record should be able to represent all three without conflating them.”

**Requirement**  
A Relay Record SHOULD be capable of representing the subject, authorising identity and submitter independently without conflating one role with another.

**Classification**  
Data modelling; authority separation; recommendation.

**Notes**  
The source uses “should”, but the recommendation is foundational to accurate provenance and authority representation.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 6–10 of `design-notes/03-record-model.md`.
- Section 11 and later content was excluded.
- Examples were used only to clarify source meaning and were not promoted into mandatory final syntax.

## Numbering verification

- First requirement: `REM-03-046`.
- Final requirement: `REM-03-098`.
- Requirement numbering continues directly from Part 1.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, bullet, heading definition or necessary decomposition of a compound statement.
- Schema-definition bullets were extracted individually because each imposes a separately testable obligation.
- Optional schema behaviours were retained as `MAY` requirements rather than converted into universal mandates.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or options.
- Descriptive definitions were converted into normative language only where necessary to make the protocol model testable, without strengthening optional source language.

## Editorial verification

- Logical-record identity remains distinct from historical-version identity.
- Schema authority remains distinct from record ownership and repository control.
- Protocol validation remains distinct from application presentation.
- Subject, authorising identity and submitter remain independently representable roles.
- Provisional example syntax has not been treated as final specification syntax.
