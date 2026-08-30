# REM-05 Part 1 — Relationship Requirement Extraction Matrix (Sections 1–5)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 1–5 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

1. Definition
2. Purpose
3. Relationship as a record
4. Relationship components
5. Source

Requirement identifiers begin with `REM-05-001`.

---

# 1. Definition

## REM-05-001 — Structured relationship representation

**Source**  
Section 1: “A Relay Relationship is a structured, portable record describing a connection between Relay Identities, Relay Records or recognised external entities.”

**Requirement**  
A Relay Relationship MUST be represented as a structured record.

**Classification**  
Core object definition; structural requirement; interoperability.

**Notes**  
The source does not prescribe a final serialisation format in this section. “Structured” requires the relationship to be represented through defined fields or schema-governed data rather than only through unstructured application state.

---

## REM-05-002 — Relationship portability

**Source**  
Section 1: “A Relay Relationship is a structured, portable record...”

**Requirement**  
A Relay Relationship MUST be portable across compatible Relay implementations.

**Classification**  
Portability; interoperability; application independence.

**Notes**  
Portability requires preservation of sufficient identity, type, authority and relationship-state information for another compatible implementation to continue interpreting the connection.

---

## REM-05-003 — Identity-to-identity relationships

**Source**  
Section 1: a Relay Relationship describes a connection between “Relay Identities, Relay Records or recognised external entities.”

**Requirement**  
The Relationship Model MUST support relationships in which a Relay Identity is connected to another Relay Identity.

**Classification**  
Relationship domain; identity modelling; interoperability.

**Notes**  
Examples include follows, subscribes to, collaborates with, works for, endorses, trusts, blocks and is represented by.

---

## REM-05-004 — Identity-to-record and record-related relationships

**Source**  
Section 1: a Relay Relationship describes a connection between “Relay Identities, Relay Records or recognised external entities.”

**Requirement**  
The Relationship Model MUST support relationships involving Relay Records as a source or target where permitted by the applicable schema.

**Classification**  
Relationship domain; record references; extensibility.

**Notes**  
Examples include authored, owns, manages or is connected to a record. The precise permitted source and target combinations are schema-defined.

---

## REM-05-005 — Relationships involving recognised external entities

**Source**  
Section 1: a Relay Relationship describes a connection between “Relay Identities, Relay Records or recognised external entities.”

**Requirement**  
The Relationship Model MUST be capable of representing a connection involving a recognised external entity where no suitable Relay-native entity exists.

**Classification**  
External interoperability; relationship domain; extensibility.

**Notes**  
Recognition and identifier rules for external entities must prevent an arbitrary display string from being mistaken for a stable protocol identity.

---

## REM-05-006 — Support for diverse relationship semantics

**Source**  
Section 1 examples: follows; subscribes to; collaborates with; works for; is a member of; endorses; trusts; blocks; is represented by; authored; owns; manages; is connected to.

**Requirement**  
The Relationship Model MUST support multiple categories of connection, including social, subscription, collaboration, employment, membership, endorsement, trust, blocking, representation, authorship, ownership, management and general association relationships.

**Classification**  
Semantic breadth; extensibility; interoperability.

**Notes**  
The examples are illustrative rather than exhaustive. New relationship types may be introduced through schemas without redefining the core model.

---

## REM-05-007 — Relationship survival beyond the originating application

**Source**  
Section 1: “A Relay Relationship must not depend solely on the continued existence of the application through which it was created.”

**Requirement**  
The continued validity, resolution and interpretation of a Relay Relationship MUST NOT depend solely on the continued existence, availability or operation of the application through which the relationship was created.

**Classification**  
Application independence; continuity; resilience.

**Notes**  
An application may participate in relationship creation, but canonical relationship state must remain available through the repository and protocol model after that application is replaced, withdrawn or unavailable.

---

## REM-05-008 — Applications may assist relationship establishment

**Source**  
Section 1: “An application may help establish, display, filter or interpret a relationship...”

**Requirement**  
An authorised application MAY assist a user or Relay Identity in establishing a Relay Relationship.

**Classification**  
Application interaction; delegated operation; relationship lifecycle.

**Notes**  
Establishment remains subject to repository authority, applicable permissions and the schema governing the relationship type.

---

## REM-05-009 — Applications may display relationships

**Source**  
Section 1: “An application may help establish, display, filter or interpret a relationship...”

**Requirement**  
An application MAY display a Relay Relationship that it is authorised to access.

**Classification**  
Application presentation; access control; interoperability.

**Notes**  
Display does not establish ownership, authorship or canonical authority over the relationship.

---

## REM-05-010 — Applications may filter relationships

**Source**  
Section 1: “An application may help establish, display, filter or interpret a relationship...”

**Requirement**  
An application MAY filter Relay Relationships for presentation or application-specific use without altering their canonical protocol meaning.

**Classification**  
Application presentation; derived views; application autonomy.

**Notes**  
Filtering is an application-layer operation. Omitting a relationship from a view does not revoke or delete the underlying relationship record.

---

## REM-05-011 — Applications may interpret relationships

**Source**  
Section 1: “An application may help establish, display, filter or interpret a relationship...”

**Requirement**  
An application MAY provide an application-specific interpretation or presentation of a Relay Relationship, provided it does not falsely represent the relationship’s schema-defined meaning or authority.

**Classification**  
Application interpretation; semantic integrity; presentation independence.

**Notes**  
Different applications may present compatible relationship data differently, but the underlying schema and canonical record remain authoritative.

---

## REM-05-012 — Application participation does not establish ownership

**Source**  
Section 1: “...but it does not automatically own that relationship.”

**Requirement**  
An application MUST NOT be treated as the owner or controlling authority of a Relay Relationship solely because it established, submitted, displayed, filtered or interpreted that relationship.

**Classification**  
Ownership separation; application independence; authority.

**Notes**  
The application may be recorded as submitter or provenance metadata while the relationship remains under repository and authorising-identity control.

---

# 2. Purpose

## REM-05-013 — Preservation of relationship continuity

**Source**  
Section 2: “The Relationship Model exists to preserve relationship continuity.”

**Requirement**  
The Relay Relationship Model MUST preserve the continuity of a relationship across changes in applications, providers and compatible service environments.

**Classification**  
Core purpose; continuity; portability.

**Notes**  
Relationship continuity means that the connection remains independently resolvable and interpretable rather than being reduced to platform-specific account state.

---

## REM-05-014 — Establishment through one application

**Source**  
Section 2: the model must allow a person to “establish a connection through one application”.

**Requirement**  
The Relationship Model MUST allow a person to establish a relationship through an authorised application.

**Classification**  
Application interaction; relationship creation; user capability.

**Notes**  
The application is an interface or delegated submitter; the resulting relationship must not become application-owned state.

---

## REM-05-015 — Cross-application relationship viewing

**Source**  
Section 2: the model must allow a person to “view or act on that connection through another compatible application”.

**Requirement**  
The Relationship Model MUST allow a relationship established through one application to be viewed through another compatible and authorised application.

**Classification**  
Interoperability; application replaceability; portability.

**Notes**  
The second application may present the relationship differently but must be able to resolve and interpret the canonical connection.

---

## REM-05-016 — Cross-application relationship action

**Source**  
Section 2: the model must allow a person to “view or act on that connection through another compatible application”.

**Requirement**  
The Relationship Model MUST allow another compatible application to perform authorised operations on or in relation to an existing relationship.

**Classification**  
Interoperability; delegated operation; application replaceability.

**Notes**  
Permitted actions depend on the applicable schema, relationship state and Permission Grant. Cross-application operability does not imply unrestricted modification.

---

## REM-05-017 — Relationship retention after provider change

**Source**  
Section 2: the model must allow a person to “retain the connection after changing providers”.

**Requirement**  
A change of Relay Provider MUST NOT, by itself, terminate or invalidate a portable Relay Relationship.

**Classification**  
Provider independence; migration; continuity.

**Notes**  
Provider migration may require updated resolution or routing information, but the logical relationship and its stable references must remain intact.

---

## REM-05-018 — Public and private relationship distinction

**Source**  
Section 2: the model must allow a person to “distinguish public relationships from private ones”.

**Requirement**  
The Relationship Model MUST distinguish public relationships from private relationships.

**Classification**  
Visibility; privacy; access control.

**Notes**  
The distinction must be represented through protocol-understandable visibility or audience information rather than being left solely to application presentation.

---

## REM-05-019 — Revocation of a party’s own relationship side

**Source**  
Section 2: the model must allow a person to “revoke or change their side of a relationship”.

**Requirement**  
A Relay Identity MUST be able to revoke its own relationship declaration or its own side of a relationship, subject to the governing schema and repository rules.

**Classification**  
User control; revocation; relationship lifecycle.

**Notes**  
Revoking one party’s declaration does not necessarily delete or invalidate a separate declaration independently made by another party.

---

## REM-05-020 — Modification of a party’s own relationship side

**Source**  
Section 2: the model must allow a person to “revoke or change their side of a relationship”.

**Requirement**  
A Relay Identity MUST be able to change its own relationship declaration or relationship-side state where the applicable schema permits modification.

**Classification**  
User control; relationship lifecycle; schema behaviour.

**Notes**  
Some relationship types may require supersession, a new version or a separate state-transition record rather than direct mutation.

---

## REM-05-021 — Verification of authorising identity

**Source**  
Section 2: the model must allow a person to “verify which identity authorised each relationship claim”.

**Requirement**  
The Relationship Model MUST provide sufficient information to verify which Relay Identity authorised each relationship claim.

**Classification**  
Authority; provenance; verification.

**Notes**  
The authorising identity is distinct from an application or agent that submitted the relationship operation.

---

## REM-05-022 — Prevention of relationship-based platform lock-in

**Source**  
Section 2: the model must allow a person to “prevent applications from converting every relationship into permanent platform lock-in”.

**Requirement**  
The Relationship Model MUST prevent an application from making continued access to or interpretation of a relationship dependent on permanent use of that application or platform.

**Classification**  
Anti-lock-in; portability; application independence.

**Notes**  
Application-specific extensions may exist, but they must not erase or replace the portable protocol-level relationship state.

---

## REM-05-023 — Exported usernames are insufficient for portability

**Source**  
Section 2: “A list of exported usernames is not sufficient.”

**Requirement**  
An implementation MUST NOT claim operational relationship portability solely because it can export a list of usernames or display handles.

**Classification**  
Portability; identity resolution; compliance boundary.

**Notes**  
Usernames and handles may be mutable, provider-specific or ambiguous. Operational portability requires stable identity resolution and sufficient relationship semantics.

---

## REM-05-024 — Resolution required for operational portability

**Source**  
Section 2: “A relationship is operationally portable only when another compatible service can resolve the identities involved and continue interpreting the connection.”

**Requirement**  
A relationship MUST NOT be considered operationally portable unless another compatible service can resolve the identities involved.

**Classification**  
Identity resolution; portability; interoperability.

**Notes**  
Resolution must use stable identifiers or equivalent protocol mechanisms rather than relying solely on provider-local URLs or visible handles.

---

## REM-05-025 — Continued interpretation required for operational portability

**Source**  
Section 2: “A relationship is operationally portable only when another compatible service can resolve the identities involved and continue interpreting the connection.”

**Requirement**  
A relationship MUST NOT be considered operationally portable unless another compatible service can continue interpreting the relationship’s type and meaning.

**Classification**  
Semantic interoperability; portability; schema resolution.

**Notes**  
Stable identifiers without interpretable relationship semantics are insufficient for operational portability.

---

# 3. Relationship as a record

## REM-05-026 — Relationship represented as a Relay Record

**Source**  
Section 3: “A Relay Relationship is represented as a Relay Record.”

**Requirement**  
Every canonical Relay Relationship MUST be represented as a Relay Record.

**Classification**  
Core representation; record model integration; canonical state.

**Notes**  
Relationship records inherit the applicable identification, versioning, authority, visibility, integrity and repository-history rules of the Relay Record Model.

---

## REM-05-027 — Normal storage in the declarant’s repository

**Source**  
Section 3: “It is normally stored in the repository of the identity making the relationship declaration.”

**Requirement**  
A relationship declaration SHOULD normally be stored in the repository controlled by the Relay Identity making that declaration.

**Classification**  
Repository placement; authority; recommended behaviour.

**Notes**  
The source uses “normally”, allowing schema-defined or delegated exceptions without changing which identity authorised the declaration.

---

## REM-05-028 — Declarant repository as canonical source

**Source**  
Section 3: “Alice’s repository is the canonical source of Alice’s declaration that she follows Bob.”

**Requirement**  
The repository of the identity making a relationship declaration MUST serve as the canonical source of that identity’s declaration, unless the protocol defines an authorised equivalent repository arrangement.

**Classification**  
Canonical authority; repository control; provenance.

**Notes**  
The canonical source establishes the authoritative record of the declarant’s claim; it does not make the declarant authoritative over the target identity’s independent claims.

---

## REM-05-029 — Independent existence of unilateral declarations

**Source**  
Section 3: “Bob’s repository does not need to contain the same record for Alice’s declaration to exist.”

**Requirement**  
A unilateral relationship declaration MUST be capable of existing without a matching record in the target identity’s repository.

**Classification**  
Directed relationships; repository independence; relationship semantics.

**Notes**  
This applies to directed relationship types such as follow or block. Reciprocal relationship schemas may impose additional confirmation requirements.

---

## REM-05-030 — No mandatory target-side duplication

**Source**  
Section 3: “Bob’s repository does not need to contain the same record for Alice’s declaration to exist.”

**Requirement**  
The protocol MUST NOT require the target repository to duplicate a declarant’s relationship record solely for that declaration to be valid.

**Classification**  
Data duplication avoidance; repository independence; interoperability.

**Notes**  
A target repository may separately record receipt, acknowledgement, reciprocal confirmation or a derived index, but such data is not automatically the canonical source of the original declaration.

---

# 4. Relationship components

## REM-05-031 — Support for source component

**Source**  
Section 4, component list: “Source”.

**Requirement**  
The Relationship Model MUST support representation of the relationship Source.

**Classification**  
Relationship structure; source identification.

**Notes**  
Section 5 defines the Source as the identity or record making the declaration.

---

## REM-05-032 — Support for target component

**Source**  
Section 4, component list: “Target”.

**Requirement**  
The Relationship Model MUST support representation of the relationship Target.

**Classification**  
Relationship structure; target identification.

**Notes**  
Target semantics and permitted target categories are defined in later sections of the source model.

---

## REM-05-033 — Support for relationship-type component

**Source**  
Section 4, component list: “Relationship Type”.

**Requirement**  
The Relationship Model MUST support representation of the Relationship Type.

**Classification**  
Relationship structure; semantic typing; schema identification.

**Notes**  
The Relationship Type defines the meaning of the connection and is governed by a schema.

---

## REM-05-034 — Support for direction component

**Source**  
Section 4, component list: “Direction”.

**Requirement**  
The Relationship Model MUST support representation of relationship Direction where relevant to the applicable schema.

**Classification**  
Relationship structure; directionality.

**Notes**  
Direction may distinguish directed, reciprocal or mutually interpreted relationships.

---

## REM-05-035 — Support for status component

**Source**  
Section 4, component list: “Status”.

**Requirement**  
The Relationship Model MUST support representation of relationship Status where required by the applicable schema.

**Classification**  
Relationship structure; lifecycle state.

**Notes**  
Possible statuses may include pending, active, declined, revoked, expired or suspended, as defined later or by schema.

---

## REM-05-036 — Support for visibility component

**Source**  
Section 4, component list: “Visibility”.

**Requirement**  
The Relationship Model MUST support representation of relationship Visibility.

**Classification**  
Relationship structure; access control; privacy.

**Notes**  
Visibility determines the broad classification of access and must remain distinct from a more specific Audience restriction where both are used.

---

## REM-05-037 — Support for audience component

**Source**  
Section 4, component list: “Audience”.

**Requirement**  
The Relationship Model MUST support representation of an Audience for relationship access where required.

**Classification**  
Relationship structure; audience control; privacy.

**Notes**  
Audience rules may limit access to specified identities, groups or qualifying parties.

---

## REM-05-038 — Support for context component

**Source**  
Section 4, component list: “Context”.

**Requirement**  
The Relationship Model MUST support representation of relationship Context where needed to interpret the connection accurately.

**Classification**  
Relationship structure; contextual semantics.

**Notes**  
Context may distinguish, for example, a collaboration within one project from a general collaboration claim.

---

## REM-05-039 — Support for provenance component

**Source**  
Section 4, component list: “Provenance”.

**Requirement**  
The Relationship Model MUST support representation of relationship Provenance.

**Classification**  
Relationship structure; provenance; accountability.

**Notes**  
Provenance may identify the authorising identity, submitting application, grant, evidence or repository history associated with the declaration.

---

## REM-05-040 — Support for validity-period component

**Source**  
Section 4, component list: “Validity Period”.

**Requirement**  
The Relationship Model MUST support representation of a Validity Period where a relationship is time-bound.

**Classification**  
Relationship structure; temporal validity; lifecycle.

**Notes**  
Not every relationship is time-limited, but schemas must be able to express start, expiry or other temporal bounds where relevant.

---

## REM-05-041 — Support for reciprocal-reference component

**Source**  
Section 4, component list: “Reciprocal Reference”.

**Requirement**  
The Relationship Model MUST support representation of a Reciprocal Reference where a relationship depends on or is associated with another party’s declaration.

**Classification**  
Relationship structure; reciprocity; cross-record reference.

**Notes**  
A reciprocal reference must not collapse two independently authorised records into one indistinguishable record.

---

## REM-05-042 — Support for authority component

**Source**  
Section 4, component list: “Authority”.

**Requirement**  
The Relationship Model MUST support representation of the Authority under which a relationship declaration or relationship-conveyed power exists.

**Classification**  
Relationship structure; authority; delegation.

**Notes**  
Authority is particularly important for representation, guardianship, management or other relationships that may convey permission or legal effect.

---

## REM-05-043 — Support for conditions component

**Source**  
Section 4, component list: “Conditions”.

**Requirement**  
The Relationship Model MUST support representation of Conditions that limit or qualify a relationship where required by the applicable schema.

**Classification**  
Relationship structure; conditional semantics; policy.

**Notes**  
Conditions may restrict duration, context, permitted actions, evidence requirements or other schema-defined aspects of the relationship.

---

## REM-05-044 — Components are schema-dependent

**Source**  
Section 4: “Not every relationship requires every component.”

**Requirement**  
An implementation MUST NOT require every listed relationship component for every relationship type unless the applicable schema requires it.

**Classification**  
Schema flexibility; validation; extensibility.

**Notes**  
The component list defines the model’s representational capabilities, while each schema determines which components are required, optional or prohibited.

---

# 5. Source

## REM-05-045 — Source identifies the declarant

**Source**  
Section 5: “The Source is the identity or record making the relationship declaration.”

**Requirement**  
The Source component MUST identify the identity or record making the relationship declaration.

**Classification**  
Source semantics; declarant identification; accountability.

**Notes**  
The Source is the declarant within the relationship statement and is distinct from the Target and from any application submitting the operation.

---

## REM-05-046 — Source may be an identity

**Source**  
Section 5: “The Source is the identity or record making the relationship declaration.”

**Requirement**  
The Relationship Model MUST support a Relay Identity as the Source of a relationship declaration.

**Classification**  
Source semantics; identity modelling.

**Notes**  
This is the normal case for person-, organisation- or agent-controlled relationship declarations.

---

## REM-05-047 — Source may be a record

**Source**  
Section 5: “The Source is the identity or record making the relationship declaration.”

**Requirement**  
The Relationship Model MUST support a Relay Record as the Source of a relationship declaration where the governing schema permits record-originated semantics.

**Classification**  
Source semantics; record relationships; extensibility.

**Notes**  
The authorising identity and repository authority behind the source record must remain independently verifiable.

---

## REM-05-048 — Source corresponds to the declarant in statement semantics

**Source**  
Section 5 example: “Alice follows Bob. Alice is the source.”

**Requirement**  
The Source MUST correspond to the grammatical and semantic declarant of the relationship statement defined by the schema.

**Classification**  
Semantic integrity; source identification; validation.

**Notes**  
For a relationship represented as “Alice follows Bob”, Alice is the Source and Bob is the Target. Reversing those fields would express a different claim.

---

## REM-05-049 — Normal correspondence with repository controller

**Source**  
Section 5: “The source must normally correspond to the Relay Identity controlling the repository in which the relationship record exists.”

**Requirement**  
The Source SHOULD normally correspond to the Relay Identity controlling the repository in which the relationship record is stored.

**Classification**  
Repository authority; source validation; recommended behaviour.

**Notes**  
The source wording combines “must” with “normally”, establishing a strong default while allowing authorised exceptions such as record sources, delegated structures or schema-defined repository arrangements.

---

## REM-05-050 — Exceptions require valid authority and semantics

**Source**  
Section 5: “The source must normally correspond to the Relay Identity controlling the repository...” and an application may submit under delegated authority.

**Requirement**  
Where the Source does not directly correspond to the repository-controlling Relay Identity, the implementation MUST be able to validate the authority and schema basis for that exception.

**Classification**  
Authority validation; repository integrity; exception handling.

**Notes**  
A mismatch must not be accepted merely because an application supplied the record. The relationship must remain attributable to a valid authorising identity or record context.

---

## REM-05-051 — Delegated application submission

**Source**  
Section 5: “An application may submit the declaration under delegated authority...”

**Requirement**  
An application MAY submit a relationship declaration on behalf of the Source only under valid delegated authority.

**Classification**  
Delegation; application submission; access control.

**Notes**  
The repository must validate the application’s grant, delegated key or equivalent authority before accepting the declaration.

---

## REM-05-052 — Submitter is distinct from relationship source

**Source**  
Section 5: “...but the application is not the relationship source unless the application itself is intentionally acting as a Relay Identity.”

**Requirement**  
An application that submits a relationship declaration under delegated authority MUST NOT be recorded or interpreted as the relationship Source solely because it transmitted the operation.

**Classification**  
Role separation; provenance; semantic integrity.

**Notes**  
The application may be recorded as submitter while the authorising Relay Identity or record remains the Source.

---

## REM-05-053 — Application may intentionally act as a Relay Identity

**Source**  
Section 5: the application is not the relationship source “unless the application itself is intentionally acting as a Relay Identity.”

**Requirement**  
An application MAY be the Source of a relationship only where it is intentionally represented and authorised as a Relay Identity rather than merely operating as software for another identity.

**Classification**  
Application identity; source semantics; authority.

**Notes**  
This exception requires an explicit identity role. Possession of an Application Identity or Permission Grant alone does not make the application a Relay Identity or relationship Source.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 1–5 of `design-notes/05-relationship-model.md`.
- Section 6 and later relationship semantics were excluded as independent requirements.
- Later concepts are mentioned only where necessary to clarify a requirement already present in Sections 1–5.

## Numbering verification

- First requirement: `REM-05-001`.
- Final requirement: `REM-05-053`.
- Requirement identifiers are continuous, unique and ordered according to the source sections.
- No requirement identifiers were inherited from earlier chat-generated drafts.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, example, component entry or necessary decomposition of a compound statement.
- The Section 4 component list was extracted individually because each component represents a separately testable model capability.
- Examples were used to clarify semantics and were not treated as a closed taxonomy.

## Normative-language verification

- Explicit source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “may” statements are preserved as `MAY` permissions.
- Source qualifications such as “normally” are preserved through `SHOULD` defaults and explanatory notes rather than strengthened into universal rules.
- Descriptive definitions were converted into testable normative requirements without adding obligations beyond the source model.

## Editorial verification

- Relationship control remains independent of the application that established or displayed the relationship.
- The declarant repository remains the canonical source of the declarant’s relationship claim.
- A unilateral declaration does not require target-side duplication.
- Operational portability requires both stable identity resolution and continued semantic interpretation.
- The relationship Source remains distinct from the submitting application unless the application intentionally acts as a Relay Identity.
