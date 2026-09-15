# REM-05 Part 11 — Relationship Requirement Extraction Matrix (Sections 51–55)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 51–55 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

51. Relationship-based permissions
52. Provider migration
53. Application replacement
54. Relationship schema governance
55. Required v0.1 relationship operations

Requirement identifiers continue sequentially from Part 10, beginning with `REM-05-543`.

---

# 51. Relationship-based permissions

## REM-05-543 — Relationships must not automatically grant broad application authority

**Source**  
Section 51: “A relationship must not automatically grant broad application authority.”

**Requirement**  
A Relay implementation MUST NOT treat the existence of a relationship as automatically granting broad application or repository authority to either participant.

**Classification**  
Permissions; least authority; relationship semantics.

**Notes**  
Social, organisational or descriptive relationships are not implicit technical permission grants.

---

## REM-05-544 — Colleague status does not imply repository editing authority

**Source**  
Section 51 example: “Alice is Bob’s colleague” does not mean “Alice may edit Bob’s repository.”

**Requirement**  
An implementation MUST NOT infer repository editing authority from a colleague relationship alone.

**Classification**  
Permissions; repository authority; social relationship.

**Notes**  
The example illustrates the broader rule that relationship meaning and technical capability are separate.

---

## REM-05-545 — Relationship-derived authority must be explicitly declared

**Source**  
Section 51: “Any authority must be explicitly declared within an authority-bearing relationship or Permission Grant.”

**Requirement**  
Any technical authority associated with a relationship MUST be explicitly declared in an authority-bearing relationship or an applicable Permission Grant.

**Classification**  
Authority; permission grants; explicit authorisation.

---

## REM-05-546 — Social meaning and technical authority must remain separate

**Source**  
Section 51: “Social meaning and technical authority must remain separate.”

**Requirement**  
Relay implementations MUST maintain a semantic distinction between the social or organisational meaning of a relationship and any technical authority granted to a participant.

**Classification**  
Separation of concerns; relationship semantics; permissions.

**Notes**  
Applications may use relationships as contextual inputs, but technical capabilities require explicit authority.

---

# 52. Provider migration

## REM-05-547 — Source Relay Identifiers must survive provider migration

**Source**  
Section 52: “When a source or target moves Relay Provider: the Relay Identifier remains unchanged.”

**Requirement**  
When the source identity of a relationship moves to a different Relay Provider, its Relay Identifier MUST remain unchanged.

**Classification**  
Provider migration; identity continuity; portability.

---

## REM-05-548 — Target Relay Identifiers must survive provider migration

**Source**  
Section 52: “When a source or target moves Relay Provider: the Relay Identifier remains unchanged.”

**Requirement**  
When the target identity of a relationship moves to a different Relay Provider, its Relay Identifier MUST remain unchanged.

**Classification**  
Provider migration; identity continuity; portability.

---

## REM-05-549 — Relationship Record URIs must survive provider migration

**Source**  
Section 52: “the relationship Record URI remains unchanged.”

**Requirement**  
A relationship Record URI MUST remain unchanged when its source or target moves Relay Provider.

**Classification**  
Record identity; provider migration; relationship continuity.

**Notes**  
Provider location is not part of the persistent identity of the relationship record.

---

## REM-05-550 — Identity Documents must identify the new provider after migration

**Source**  
Section 52: “the Identity Document points to the new provider.”

**Requirement**  
After a Relay Identity changes provider, its Identity Document MUST resolve the identity to the new provider location according to the Identity Model.

**Classification**  
Identity resolution; provider migration; discovery.

---

## REM-05-551 — Applications must resolve migrated repository locations

**Source**  
Section 52: “applications resolve the new repository location.”

**Requirement**  
Compatible applications MUST resolve the current repository location after a provider migration rather than continuing to depend on the former provider location.

**Classification**  
Application interoperability; repository discovery; migration.

---

## REM-05-552 — Provider migration must not require recreating follows

**Source**  
Section 52: “no follow, membership or collaboration needs to be recreated.”

**Requirement**  
A provider migration MUST NOT require an existing follow relationship to be recreated solely because the source or target changed provider.

**Classification**  
Relationship continuity; follow; provider portability.

---

## REM-05-553 — Provider migration must not require recreating memberships

**Source**  
Section 52: “no follow, membership or collaboration needs to be recreated.”

**Requirement**  
A provider migration MUST NOT require an existing membership relationship to be recreated solely because the source or target changed provider.

**Classification**  
Relationship continuity; membership; provider portability.

---

## REM-05-554 — Provider migration must not require recreating collaborations

**Source**  
Section 52: “no follow, membership or collaboration needs to be recreated.”

**Requirement**  
A provider migration MUST NOT require an existing collaboration relationship to be recreated solely because the source or target changed provider.

**Classification**  
Relationship continuity; collaboration; provider portability.

---

## REM-05-555 — Relationship continuity across provider migration is a core portability test

**Source**  
Section 52: “This is the key portability test for the Relationship Model.”

**Requirement**  
A conforming Relationship Model implementation MUST preserve operational relationship continuity across Relay Provider migration.

**Classification**  
Portability; conformance; provider migration.

**Notes**  
The test is whether stable identity and record references allow compatible applications to continue using the relationship without reconstruction.

---

# 53. Application replacement

## REM-05-556 — Replacement applications read authorised relationship records

**Source**  
Section 53: “When a user changes applications: the new application reads authorised relationship records.”

**Requirement**  
When a user changes compatible applications, the replacement application MUST be able to read relationship records for which it has the necessary authorisation and schema support.

**Classification**  
Application replacement; portability; authorised access.

---

## REM-05-557 — Supported relationships continue operating after application replacement

**Source**  
Section 53: “supported relationships continue operating.”

**Requirement**  
Relationship types supported by a replacement application SHOULD continue operating without requiring the user to recreate the underlying relationships.

**Classification**  
Application portability; relationship continuity; interoperability.

---

## REM-05-558 — Unsupported relationship types must remain preserved

**Source**  
Section 53: “unsupported relationship types remain preserved.”

**Requirement**  
A relationship type unsupported by a replacement application MUST remain preserved in its authoritative repository rather than being removed because the new application does not understand or display it.

**Classification**  
Forward compatibility; data preservation; application replacement.

---

## REM-05-559 — Application-specific relationship views may differ

**Source**  
Section 53: “application-specific views may differ.”

**Requirement**  
Compatible applications MAY present, organise or interpret authorised relationship records through different application-specific views, provided they do not silently alter the canonical relationship semantics.

**Classification**  
Application autonomy; presentation; relationship semantics.

---

## REM-05-560 — Application replacement must not transfer relationship ownership

**Source**  
Section 53: “no relationship is transferred into application ownership.”

**Requirement**  
Changing applications MUST NOT transfer ownership or canonical authority over a relationship to either the former or replacement application.

**Classification**  
Ownership; application independence; portability.

---

## REM-05-561 — New clients may omit unsupported relationship types from display

**Source**  
Section 53: “A new client may choose not to display every relationship type.”

**Requirement**  
A replacement client MAY choose not to display relationship types that it does not support.

**Classification**  
Client behaviour; presentation; schema support.

**Notes**  
Non-display is distinct from deletion, invalidation or mutation of the underlying relationship record.

---

## REM-05-562 — New clients must not delete unsupported relationships

**Source**  
Section 53: “It must not delete or silently alter unsupported relationships.”

**Requirement**  
A replacement client MUST NOT delete a relationship merely because the client does not support its relationship type.

**Classification**  
Data preservation; application replacement; unknown schemas.

---

## REM-05-563 — New clients must not silently alter unsupported relationships

**Source**  
Section 53: “It must not delete or silently alter unsupported relationships.”

**Requirement**  
A replacement client MUST NOT silently alter a relationship record merely because the client does not support or understand its relationship type.

**Classification**  
Data integrity; application replacement; unknown schemas.

---

# 54. Relationship schema governance

## REM-05-564 — Relay should define a limited core relationship schema set

**Source**  
Section 54: “Relay should define a limited set of core relationship schemas.”

**Requirement**  
Relay SHOULD define and govern a limited set of core relationship schemas for commonly interoperable relationship types.

**Classification**  
Schema governance; core protocol; interoperability.

---

## REM-05-565 — Follow may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.follow.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.follow.v1` as a core relationship schema.

**Classification**  
Schema governance; follow; core schema.

---

## REM-05-566 — Subscribe may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.subscribe.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.subscribe.v1` as a core relationship schema.

**Classification**  
Schema governance; subscription; core schema.

---

## REM-05-567 — Block may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.block.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.block.v1` as a core relationship schema.

**Classification**  
Schema governance; block; core schema.

---

## REM-05-568 — Mute may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.mute.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.mute.v1` as a core relationship schema.

**Classification**  
Schema governance; mute; core schema.

---

## REM-05-569 — Member may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.member.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.member.v1` as a core relationship schema.

**Classification**  
Schema governance; membership; core schema.

---

## REM-05-570 — Collaborator may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.collaborator.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.collaborator.v1` as a core relationship schema.

**Classification**  
Schema governance; collaboration; core schema.

---

## REM-05-571 — Trust may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.trust.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.trust.v1` as a core relationship schema.

**Classification**  
Schema governance; trust; core schema.

---

## REM-05-572 — Endorse may be defined as a core relationship schema

**Source**  
Section 54 possible core schema: `com.relay.relationship.endorse.v1`.

**Requirement**  
Relay MAY define `com.relay.relationship.endorse.v1` as a core relationship schema.

**Classification**  
Schema governance; endorsement; core schema.

---

## REM-05-573 — Third parties may define additional relationship schemas

**Source**  
Section 54: “Third parties may define additional schemas.”

**Requirement**  
Third parties MAY define relationship schemas beyond the Relay core schema set.

**Classification**  
Extensibility; third-party schemas; schema governance.

---

## REM-05-574 — Custom schemas must define semantics

**Source**  
Section 54: “A custom schema must clearly define: semantics.”

**Requirement**  
A custom relationship schema MUST clearly define the semantics of the relationship it represents.

**Classification**  
Custom schema; semantics; interoperability.

---

## REM-05-575 — Custom schemas must define direction

**Source**  
Section 54: “A custom schema must clearly define: direction.”

**Requirement**  
A custom relationship schema MUST clearly define its direction semantics.

**Classification**  
Custom schema; direction; relationship semantics.

---

## REM-05-576 — Custom schemas must define consent requirements

**Source**  
Section 54: “A custom schema must clearly define: consent requirements.”

**Requirement**  
A custom relationship schema MUST clearly define any consent, acceptance or approval requirements governing creation and activation of the relationship.

**Classification**  
Custom schema; consent; lifecycle.

---

## REM-05-577 — Custom schemas must define authority implications

**Source**  
Section 54: “A custom schema must clearly define: authority implications.”

**Requirement**  
A custom relationship schema MUST clearly define whether the relationship conveys any technical authority and, where applicable, the implications of that authority.

**Classification**  
Custom schema; authority; permissions.

---

## REM-05-578 — Custom schemas must define lifecycle

**Source**  
Section 54: “A custom schema must clearly define: lifecycle.”

**Requirement**  
A custom relationship schema MUST clearly define the lifecycle applicable to the relationship.

**Classification**  
Custom schema; lifecycle; state model.

---

## REM-05-579 — Custom schemas must define privacy expectations

**Source**  
Section 54: “A custom schema must clearly define: privacy expectations.”

**Requirement**  
A custom relationship schema MUST clearly define the privacy expectations applicable to the relationship and its associated data.

**Classification**  
Custom schema; privacy; visibility.

---

# 55. Required v0.1 relationship operations

## REM-05-580 — v0.1 must support creation of unilateral relationships

**Source**  
Section 55 required operation: “Create unilateral relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support creation of a unilateral relationship.

**Classification**  
Required operation; unilateral relationship; v0.1 conformance.

---

## REM-05-581 — v0.1 must support reading relationships

**Source**  
Section 55 required operation: “Read relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support reading an authorised relationship record.

**Classification**  
Required operation; read; v0.1 conformance.

---

## REM-05-582 — v0.1 must support listing relationships by type

**Source**  
Section 55 required operation: “List relationships by type.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support listing authorised relationship records by relationship type.

**Classification**  
Required operation; listing; relationship type.

---

## REM-05-583 — v0.1 must support updating relationship metadata

**Source**  
Section 55 required operation: “Update relationship metadata.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support updating relationship metadata where the acting identity has authority to modify that metadata.

**Classification**  
Required operation; metadata; update.

---

## REM-05-584 — v0.1 must support ending relationships

**Source**  
Section 55 required operation: “End relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support ending a relationship declaration in accordance with the relationship schema and the acting identity’s authority.

**Classification**  
Required operation; termination; lifecycle.

---

## REM-05-585 — v0.1 must support relationship deletion or tombstoning

**Source**  
Section 55 required operation: “Delete or tombstone relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support deleting or tombstoning a relationship record in accordance with applicable record, history and relationship rules.

**Classification**  
Required operation; deletion; tombstone.

**Notes**  
This operation does not grant one participant authority to delete or falsify another identity’s independently controlled relationship record.

---

## REM-05-586 — v0.1 must support relationship requests

**Source**  
Section 55 required operation: “Create relationship request.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support creating a relationship request for consent- or approval-based relationships.

**Classification**  
Required operation; request; consent.

---

## REM-05-587 — v0.1 must support accepting relationship requests

**Source**  
Section 55 required operation: “Accept relationship request.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support acceptance of a relationship request by an identity authorised to accept it.

**Classification**  
Required operation; acceptance; consent.

---

## REM-05-588 — v0.1 must support declining relationship requests

**Source**  
Section 55 required operation: “Decline relationship request.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support declining a relationship request by an identity authorised to respond to it.

**Classification**  
Required operation; decline; consent.

---

## REM-05-589 — v0.1 must support linking reciprocal relationship records

**Source**  
Section 55 required operation: “Link reciprocal relationship records.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support linking independently authorised reciprocal relationship records where the governing relationship schema uses reciprocal records.

**Classification**  
Required operation; reciprocity; record linking.

---

## REM-05-590 — v0.1 must support verification of relationship authority

**Source**  
Section 55 required operation: “Verify relationship authority.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support verification of authority asserted by an authority-bearing relationship.

**Classification**  
Required operation; authority verification; permissions.

---

## REM-05-591 — v0.1 must support changing relationship visibility

**Source**  
Section 55 required operation: “Change relationship visibility.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support changing relationship visibility where the acting identity is authorised to control that visibility.

**Classification**  
Required operation; visibility; privacy.

---

## REM-05-592 — v0.1 must support relationship context

**Source**  
Section 55 required operation: “Add relationship context.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support adding context to a relationship where permitted by the relationship schema and the acting identity’s authority.

**Classification**  
Required operation; context; relationship semantics.

---

## REM-05-593 — v0.1 must support relationship expiration

**Source**  
Section 55 required operation: “Set expiration.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support setting an expiration for relationship records whose schema permits or requires expiration.

**Classification**  
Required operation; expiration; lifecycle.

---

## REM-05-594 — v0.1 must support revocation of authority-bearing relationships

**Source**  
Section 55 required operation: “Revoke authority-bearing relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support revocation of an authority-bearing relationship by an appropriately authorised revoking authority.

**Classification**  
Required operation; revocation; authority.

---

## REM-05-595 — v0.1 must support block creation

**Source**  
Section 55 required operation: “Create block.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support creation of a block relationship.

**Classification**  
Required operation; block; interaction control.

---

## REM-05-596 — v0.1 must support mute creation

**Source**  
Section 55 required operation: “Create mute.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support creation of a mute relationship or preference consistent with the Relationship Model.

**Classification**  
Required operation; mute; user preference.

---

## REM-05-597 — v0.1 must support external relationship import

**Source**  
Section 55 required operation: “Import external relationship.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support importing an external relationship while preserving the provenance and verification distinctions required by the Relationship Model.

**Classification**  
Required operation; import; provenance.

---

## REM-05-598 — v0.1 must preserve unknown relationship schemas

**Source**  
Section 55 required operation: “Preserve unknown relationship schemas.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST preserve relationship records using schemas it does not understand rather than deleting or silently rewriting them solely because the schema is unknown.

**Classification**  
Required operation; forward compatibility; unknown schemas.

---

## REM-05-599 — v0.1 must resolve target identity

**Source**  
Section 55 required operation: “Resolve target identity.”

**Requirement**  
A compliant Relay v0.1 relationship implementation MUST support resolution of a relationship target identity sufficiently to locate and interpret the current target where the target is represented by a resolvable Relay Identity.

**Classification**  
Required operation; identity resolution; relationship target.

---

## REM-05-600 — Advanced encrypted graph operations may remain outside the first reference implementation

**Source**  
Section 55: “Advanced encrypted graph operations may remain outside the first reference implementation.”

**Requirement**  
The first Relay reference implementation MAY defer advanced encrypted relationship-graph operations beyond its initial implementation scope.

**Classification**  
Implementation scope; encryption; v0.1 reference implementation.

**Notes**  
This allowance does not remove the privacy and access-control requirements that apply to relationship data supported by v0.1.

---

## Editorial QA

The extraction for Sections 51–55 has been reviewed for numbering, traceability, normative strength and separation of relationship semantics from authority.

- Requirement numbering is continuous from `REM-05-543` through `REM-05-600` with no gaps or duplicates.
- Every requirement traces to an explicit statement, list item or example in Sections 51–55 of the source model.
- Social and organisational relationship meaning is kept distinct from technical authority; no relationship label is promoted into an implicit Permission Grant.
- Provider migration preserves stable Relay Identifiers and relationship Record URIs and does not require relationship reconstruction.
- Application replacement preserves unsupported relationship records and does not transfer relationship ownership to applications.
- The possible core-schema list remains optional (`MAY`); it is not promoted into a mandatory final core schema registry.
- Third-party schema extensibility is preserved while requiring custom schemas to define semantics, direction, consent, authority implications, lifecycle and privacy expectations.
- Every operation explicitly listed as required for a compliant v0.1 implementation is represented as a separate `MUST` requirement.
- The source allowance to defer advanced encrypted graph operations is preserved without weakening existing privacy or access requirements.
