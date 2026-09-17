# EA-05-05 — Relationship Requirements Catalogue

## Part 24 — Relationship Invariants

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the canonical catalogue requirements derived from the Relationship Model's explicit invariant set.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-387`, following Part 23's coverage of required v0.1 relationship operations. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

Section 56 states that these rules “must always remain true.” They therefore represent mandatory protocol constraints rather than optional implementation guidance.

---

# 2. Scope

This part covers source Section 56 and REM-05 requirements `REM-05-601` through `REM-05-616`.

It defines invariant requirements governing:

- canonical authority over relationship declarations;
- application-independent source and target identity continuity;
- provider-independent relationship continuity;
- unilateral and reciprocal consent semantics;
- independent control of relationship records;
- separation of relationship labels from technical authority;
- privacy preservation during graph indexing;
- non-canonical status of derived follower counts;
- application non-ownership of introduced relationships;
- protection of historical relationships from handle reassignment;
- distinction between self-declaration and external verification;
- historical integrity after relationship termination; and
- separation of blocks and mutes from protocol-level deletion or identity suspension.

Section 57 compliance-scenario requirements and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-387

### Title

Authorising Identity Authority Over Relationship Declarations

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship declaration **MUST** remain under the canonical authority of the identity that authorised that declaration.

### Rationale

A relationship declaration is an act of the authorising identity. Participation by another identity, application, provider or index does not transfer canonical authority over that declaration.

### Source

- REM-05-601
- `design-notes/05-relationship-model.md`, Section 56, Invariant 1

### Related Invariants

- CI-02
- CI-04

---

## REL-REL-388

### Title

Relationship Identifier Continuity Across Application Change

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing applications **MUST NOT** change either the source Relay Identifier or the target Relay Identifier referenced by an existing relationship.

### Rationale

Applications are replaceable clients of portable relationship state. Application replacement must not change the identities participating in an existing relationship.

### Source

- REM-05-602
- REM-05-603
- `design-notes/05-relationship-model.md`, Section 56, Invariant 2

### Related Invariants

- CI-04
- CI-05

---

## REL-REL-389

### Title

Relationship Continuity Across Provider Change

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing Relay Provider **MUST NOT** require an existing relationship to be recreated solely because of the provider change.

### Rationale

Provider replaceability requires relationship state to remain attached to persistent Relay identity and canonical records rather than to a particular hosting provider.

### Source

- REM-05-604
- `design-notes/05-relationship-model.md`, Section 56, Invariant 3

### Related Invariants

- CI-03
- CI-05

---

## REL-REL-390

### Title

No Mutual-Consent Representation for Unilateral Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A unilateral relationship **MUST NOT** be represented, displayed or interpreted as evidence of mutual consent.

### Rationale

A unilateral declaration proves only the authorising identity's action. Presenting it as mutual would attribute consent to an identity that has not independently authorised that state.

### Source

- REM-05-605
- `design-notes/05-relationship-model.md`, Section 56, Invariant 4

### Related Invariants

- CI-02
- CI-06
- AI-08

---

## REL-REL-391

### Title

Independent Authority for Reciprocal Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A reciprocal relationship **MUST** require independently authorised participation from each identity whose declaration is necessary to establish reciprocity.

### Rationale

Reciprocity cannot be created by one participant acting for another. Each required declaration must originate from the authority of the identity to which it belongs.

### Source

- REM-05-606
- `design-notes/05-relationship-model.md`, Section 56, Invariant 5

### Related Invariants

- CI-02
- CI-06
- AI-08

---

## REL-REL-392

### Title

No Cross-Identity Relationship Record Rewriting

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

One identity **MUST NOT** be permitted to rewrite a relationship record canonically controlled by another identity.

### Rationale

Independent record authority is necessary to preserve consent, provenance and historical integrity across unilateral and reciprocal relationship models.

### Source

- REM-05-607
- `design-notes/05-relationship-model.md`, Section 56, Invariant 6

### Related Invariants

- CI-02
- CI-07
- CI-10

---

## REL-REL-393

### Title

No Undeclared Technical Authority From Relationship Labels

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A relationship label **MUST NOT** be interpreted as granting technical authority unless that authority is explicitly defined by the applicable authority-bearing relationship or Permission Grant.

### Rationale

Social, organisational or descriptive relationship meaning is distinct from technical authority. Authority must remain explicit and bounded rather than inferred from labels such as member, collaborator, follower or friend.

### Source

- REM-05-608
- `design-notes/05-relationship-model.md`, Section 56, Invariant 7

### Related Invariants

- CI-06
- CI-11

---

## REL-REL-394

### Title

Private Relationship Preservation During Graph Indexing

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Indexing or graph processing by an application **MUST NOT** cause a private relationship to become publicly discoverable solely because the relationship was indexed.

### Rationale

Derived indexes must preserve the visibility constraints of their source relationship data. Indexing does not create new publication authority.

### Source

- REM-05-609
- `design-notes/05-relationship-model.md`, Section 56, Invariant 8

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-395

### Title

Derived Follower Count Is Not Canonical Relationship State

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A derived follower count **MUST NOT** be treated as the canonical relationship graph or as a substitute for the underlying canonical relationship records.

### Rationale

Follower counts are derived views that may be incomplete, stale or index-specific. Canonical relationship authority remains in the underlying authorised relationship records.

### Source

- REM-05-610
- `design-notes/05-relationship-model.md`, Section 56, Invariant 9

### Related Invariants

- CI-07
- AI-01

---

## REL-REL-396

### Title

No Application Ownership From Relationship Introduction

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** acquire ownership or canonical authority over a relationship merely because the relationship was initiated, discovered or introduced through that application.

### Rationale

Applications facilitate relationship interactions but do not thereby become owners of the resulting user-authorised relationship state.

### Source

- REM-05-611
- `design-notes/05-relationship-model.md`, Section 56, Invariant 10

### Related Invariants

- CI-02
- CI-04

---

## REL-REL-397

### Title

Historical Relationship Protection From Handle Reassignment

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Reassignment or reuse of a released handle **MUST NOT** redirect historical relationship references from the original identity to a new identity.

### Rationale

Historical relationships must remain bound to persistent identity rather than mutable human-readable handles. Otherwise handle reuse could silently rewrite the identity to which historical relationship state refers.

### Source

- REM-05-612
- `design-notes/05-relationship-model.md`, Section 56, Invariant 11

### Related Invariants

- CI-01
- CI-05
- CI-10

---

## REL-REL-398

### Title

No External-Verification Claim for Unverified Self-Declared Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A self-declared relationship **MUST NOT** be represented as externally verified unless independent verification satisfying the applicable verification model has actually occurred.

### Rationale

Self-declaration and external verification carry different evidentiary meaning. The protocol must preserve that distinction so consumers can evaluate relationship claims accurately.

### Source

- REM-05-613
- `design-notes/05-relationship-model.md`, Section 56, Invariant 12

### Related Invariants

- CI-08
- CI-10

---

## REL-REL-399

### Title

Historical Integrity After Relationship Termination

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Ending a relationship **MUST NOT** permit its historical existence to be falsely represented as never having occurred where the protocol retains historical evidence of that relationship.

### Rationale

Termination changes current relationship state; it does not authorise falsification of historical state. This distinction preserves provenance and auditability without requiring every terminated relationship to remain publicly visible.

### Source

- REM-05-614
- `design-notes/05-relationship-model.md`, Section 56, Invariant 13

### Related Invariants

- CI-10
- AI-09

---

## REL-REL-400

### Title

Blocks and Mutes Do Not Delete or Suspend Identities

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Neither a block nor a mute **MUST** be interpreted as protocol-level deletion or suspension of the affected identity.

### Rationale

Blocks and mutes control interaction, visibility or client behaviour between particular participants. They do not change the protocol-level existence or standing of the affected Relay Identity.

### Source

- REM-05-615
- REM-05-616
- `design-notes/05-relationship-model.md`, Section 56, Invariant 14

### Related Invariants

- CI-01
- CI-06

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that are direct decompositions of a single source invariant and retain identical normative force:

- `REM-05-602` and `REM-05-603` are consolidated into `REL-REL-388`. Both derive from Section 56, Invariant 2 and jointly preserve the source and target Relay Identifier across application replacement.
- `REM-05-615` and `REM-05-616` are consolidated into `REL-REL-400`. Both derive from Section 56, Invariant 14 and jointly establish that blocks and mutes are not protocol-level identity deletion or suspension.

No other REM-05 entries in the covered range are consolidated. Each remaining invariant expresses an independently meaningful constitutional constraint and remains separately testable.

All REM-05 requirements from `REM-05-601` through `REM-05-616` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 24 begins at `REM-05-601`, immediately after Part 23's final covered requirement `REM-05-600`.
- Coverage ends at `REM-05-616`, the end of source Section 56.
- Section 57 and later requirements are excluded from this part.
- The authoritative source was checked directly for all fourteen Section 56 invariants.

## Numbering verification

- First catalogue requirement: `REL-REL-387`.
- Final catalogue requirement: `REL-REL-400`.
- Catalogue numbering continues directly from Part 23's `REL-REL-386`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- All Section 56 requirements retain mandatory invariant strength.
- Application and provider replacement remain unable to rewrite relationship identity or require relationship recreation.
- Unilateral relationship state remains distinct from mutual consent.
- Reciprocal relationship state continues to require independently authorised participation.
- Cross-identity rewriting remains prohibited.
- Relationship labels remain unable to imply undeclared technical authority.
- Private relationship visibility remains protected from index-derived publication.
- Derived follower counts remain non-canonical.
- Application introduction does not create relationship ownership.
- Handle reuse cannot redirect historical relationship references.
- Self-declaration remains distinct from external verification.
- Relationship termination cannot authorise historical falsification.
- Blocks and mutes remain interaction controls rather than protocol-level deletion or identity suspension.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers.

The remaining catalogue rules are now immediately relevant to upcoming parts:

- Section 57 / `REM-05-617` onward is a compliance scenario whose entries retain overall `SHOULD` / `SHOULD NOT` scenario strength rather than being silently promoted to invariant-level `MUST` requirements.
- `REM-05-636` through `REM-05-645` must remain unresolved and explicitly non-normative.
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status.
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

Section 56 is a natural standalone catalogue boundary because it restates the Relationship Model's core guarantees as explicit invariants. These requirements act as constitutional checks on the more detailed behaviours defined earlier in the catalogue: application and provider replaceability, independent authority, privacy, canonical ownership, persistent identity and historical integrity must continue to hold regardless of implementation detail.

The next catalogue part should begin with `REM-05-617` / source Section 57 and continue catalogue numbering from `REL-REL-401`.