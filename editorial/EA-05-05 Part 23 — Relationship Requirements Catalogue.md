# EA-05-05 — Relationship Requirements Catalogue

## Part 23 — Required v0.1 Relationship Operations

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the operation-level conformance requirements for a Relay v0.1 relationship implementation and the explicit scope allowance for advanced encrypted relationship-graph operations in the first reference implementation.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-366`, following Part 22's coverage of relationship schema governance. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Section 55 and REM-05 requirements `REM-05-580` through `REM-05-600`.

It defines v0.1 support requirements for unilateral relationship creation; authorised reading and listing; metadata updates; relationship ending, deletion and tombstoning; relationship requests and responses; reciprocal-record linking; authority verification; visibility, context and expiration changes; revocation; block and mute creation; external relationship import; preservation of unknown schemas; and target identity resolution.

It also preserves the source allowance for the first reference implementation to defer advanced encrypted relationship-graph operations without weakening privacy or access-control obligations applicable to supported relationship data.

Section 56 relationship invariants and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-366
### Title
Unilateral Relationship Creation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support creation of a unilateral relationship.
### Rationale
Unilateral relationships are a foundational relationship form and are explicitly included in the required v0.1 operation set.
### Source
- REM-05-580
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02

---

## REL-REL-367
### Title
Authorised Relationship Reading
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support reading an authorised relationship record.
### Rationale
Portable relationship state must be retrievable by authorised consumers if it is to survive application replacement and support interoperable use.
### Source
- REM-05-581
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-03
- CI-10

---

## REL-REL-368
### Title
Relationship Listing by Type
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support listing authorised relationship records by relationship type.
### Rationale
Type-based listing enables clients to reconstruct usable relationship views without requiring application ownership of the underlying graph.
### Source
- REM-05-582
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-03
- CI-10

---

## REL-REL-369
### Title
Relationship Metadata Update
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support updating relationship metadata where the acting identity has authority to modify that metadata.
### Rationale
Relationship records require controlled evolution while preserving the authority boundary of the identity that owns or controls the affected data.
### Source
- REM-05-583
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-370
### Title
Relationship Ending
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support ending a relationship declaration in accordance with the relationship schema and the acting identity's authority.
### Rationale
Relationship lifecycle semantics require an interoperable mechanism for an authorised identity to end its relationship declaration without rewriting another participant's independently controlled state.
### Source
- REM-05-584
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-371
### Title
Relationship Deletion or Tombstoning
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support deleting or tombstoning a relationship record in accordance with applicable record, history and relationship rules.
### Rationale
Deletion and tombstoning are required lifecycle operations, but their availability does not grant one participant authority to delete or falsify another identity's independently controlled relationship record or historical state.
### Source
- REM-05-585
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-372
### Title
Relationship Request Creation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support creating a relationship request for consent- or approval-based relationships.
### Rationale
Relationships requiring Target consent or approval need a portable request operation rather than unilateral activation.
### Source
- REM-05-586
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-373
### Title
Relationship Request Acceptance
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support acceptance of a relationship request by an identity authorised to accept it.
### Rationale
Consent-based relationship activation requires an explicit authorised acceptance path.
### Source
- REM-05-587
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-374
### Title
Relationship Request Decline
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support declining a relationship request by an identity authorised to respond to it.
### Rationale
A consent workflow must support refusal as well as acceptance and must not treat non-acceptance as implied consent.
### Source
- REM-05-588
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-375
### Title
Reciprocal Relationship Record Linking
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support linking independently authorised reciprocal relationship records where the governing relationship schema uses reciprocal records.
### Rationale
Reciprocity must be representable without collapsing independently authorised declarations into a single jointly owned record.
### Source
- REM-05-589
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02

---

## REL-REL-376
### Title
Relationship Authority Verification
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support verification of authority asserted by an authority-bearing relationship.
### Rationale
Where a relationship explicitly conveys technical authority, relying systems need a defined operation for determining whether that authority is valid and current.
### Source
- REM-05-590
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10
- CI-12

---

## REL-REL-377
### Title
Relationship Visibility Change
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support changing relationship visibility where the acting identity is authorised to control that visibility.
### Rationale
Privacy state must be controllable through interoperable relationship operations while respecting ownership and authority boundaries.
### Source
- REM-05-591
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10

---

## REL-REL-378
### Title
Relationship Context Addition
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support adding context to a relationship where permitted by the relationship schema and the acting identity's authority.
### Rationale
Context is part of relationship meaning for scoped relationships and must be modifiable only within the governing schema and authority rules.
### Source
- REM-05-592
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-379
### Title
Relationship Expiration Setting
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support setting an expiration for relationship records whose schema permits or requires expiration.
### Rationale
Time-bounded relationships require an interoperable way to represent the end of their validity period.
### Source
- REM-05-593
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02

---

## REL-REL-380
### Title
Authority-Bearing Relationship Revocation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support revocation of an authority-bearing relationship by an appropriately authorised revoking authority.
### Rationale
Explicit technical authority must be revocable through a defined operation so that ended authority does not remain operational merely because an earlier relationship record exists.
### Source
- REM-05-594
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10
- CI-12

---

## REL-REL-381
### Title
Block Creation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support creation of a block relationship.
### Rationale
Blocking is an explicit required interaction-control operation in the v0.1 relationship model.
### Source
- REM-05-595
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10

---

## REL-REL-382
### Title
Mute Creation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support creation of a mute relationship or preference consistent with the Relationship Model.
### Rationale
Muting is an explicit required user-controlled filtering operation and remains semantically distinct from blocking, deletion or identity suspension.
### Source
- REM-05-596
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10

---

## REL-REL-383
### Title
External Relationship Import
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support importing an external relationship while preserving the provenance and verification distinctions required by the Relationship Model.
### Rationale
Import is part of the required v0.1 operation set, but migration convenience must not erase external provenance or misrepresent imported identifiers as verified Relay identities.
### Source
- REM-05-597
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-10

---

## REL-REL-384
### Title
Unknown Relationship Schema Preservation
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** preserve relationship records using schemas it does not understand rather than deleting or silently rewriting them solely because the schema is unknown.
### Rationale
Forward compatibility requires clients and providers to preserve valid relationship data they cannot interpret so that application replacement does not destroy extensible protocol state.
### Source
- REM-05-598
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-02
- CI-03

---

## REL-REL-385
### Title
Relationship Target Identity Resolution
**Level:** Conformance
**Normative Keyword:** **MUST**
### Statement
A compliant Relay v0.1 relationship implementation **MUST** support resolution of a relationship target identity sufficiently to locate and interpret the current target where the target is represented by a resolvable Relay Identity.
### Rationale
Stable relationship references depend on resolution of Relay identities independently of application or provider changes.
### Source
- REM-05-599
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-03

---

## REL-REL-386
### Title
Advanced Encrypted Graph Operation Deferral
**Level:** Implementation
**Normative Keyword:** **MAY**
### Statement
The first Relay reference implementation **MAY** defer advanced encrypted relationship-graph operations beyond its initial implementation scope.
### Rationale
The source explicitly permits advanced encrypted graph functionality to remain outside the first reference implementation. This is an implementation-scope allowance only and does not remove privacy, visibility, authorisation or access-control requirements applying to relationship data that v0.1 does support.
### Source
- REM-05-600
- `design-notes/05-relationship-model.md`, Section 55
### Related Invariants
- CI-10

---

# 4. Consolidation and Traceability Record

No REM-05 requirements are consolidated in this part.

Section 55 explicitly enumerates the operations that a compliant v0.1 implementation must support. The verified REM extraction deliberately represents every listed required operation as a separate `MUST` requirement. Preserving that separation keeps each conformance capability independently identifiable and testable and avoids allowing support for one operation to imply support for another.

`REM-05-600` is separately represented as `REL-REL-386` because it is not a required v0.1 operation. It preserves the source's `MAY` allowance for advanced encrypted graph operations to remain outside the first reference implementation.

All REM-05 requirements from `REM-05-580` through `REM-05-600` are represented exactly once. No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 23 begins at `REM-05-580`, immediately after Part 22's final covered requirement `REM-05-579`.
- Coverage ends at `REM-05-600`, the end of source Section 55 and REM-05 Part 11.
- Section 56 and later requirements are excluded from this part.
- The authoritative source was checked directly for Section 55.

## Numbering verification

- First catalogue requirement: `REL-REL-366`.
- Final catalogue requirement: `REL-REL-386`.
- Catalogue numbering continues directly from Part 22's `REL-REL-365`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps one-to-one to a catalogue requirement.
- Every operation explicitly listed by Section 55 as required for a compliant v0.1 implementation retains `MUST` strength.
- Authority conditions added by the verified extraction are preserved for metadata updates, relationship ending, request responses, visibility changes, context changes and revocation.
- Deletion/tombstoning does not imply authority to delete or falsify another identity's independently controlled relationship state.
- Reciprocal-record linking preserves independent participant authorisation.
- External import preserves provenance and verification distinctions.
- Unknown relationship schemas must be preserved rather than deleted or silently rewritten solely because they are unknown.
- Target identity resolution is limited to targets represented by resolvable Relay Identities.
- Advanced encrypted graph-operation deferral retains `MAY` strength and does not weaken applicable privacy or access-control requirements.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part converts the source's v0.1 operation list into an explicit conformance surface without collapsing independently testable capabilities. A compliant implementation must support the complete listed operation set, while each operation remains constrained by the ownership, authorisation, privacy, provenance and lifecycle rules established elsewhere in the Relationship Model. The only scope deferral in this section concerns advanced encrypted graph operations in the first reference implementation; it is not a general exemption from relationship privacy or access-control requirements.

The next catalogue part should begin with `REM-05-601` / source Section 56 and continue catalogue numbering from `REL-REL-387`.