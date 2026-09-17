# EA-05-05 — Relationship Requirements Catalogue

## Part 22 — Relationship Schema Governance

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing the Relay core relationship schema set, third-party relationship-schema extensibility, and the minimum semantic declarations required of custom relationship schemas.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-362`, following Part 21's coverage of relationship-based permissions, provider migration and application replacement. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Section 54 and REM-05 requirements `REM-05-564` through `REM-05-579`.

It defines normative requirements governing:

- governance of a limited Relay core relationship schema set;
- candidate core schemas for follow, subscribe, block, mute, member, collaborator, trust and endorse relationships;
- third-party definition of additional relationship schemas; and
- mandatory semantic, directional, consent, authority, lifecycle and privacy declarations for custom relationship schemas.

Section 55 required v0.1 relationship operations and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-362

### Title

Limited Core Relationship Schema Set

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay **SHOULD** define and govern a limited set of core relationship schemas for commonly interoperable relationship types.

### Rationale

A bounded core vocabulary supports cross-application interoperability without requiring every possible relationship type to become part of the Relay core. The model therefore favours a limited governed foundation combined with extensibility.

### Source

- REM-05-564
- `design-notes/05-relationship-model.md`, Section 54

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-363

### Title

Candidate Core Relationship Schemas

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Relay **MAY** define the following schemas as members of its core relationship schema set:

- `com.relay.relationship.follow.v1`;
- `com.relay.relationship.subscribe.v1`;
- `com.relay.relationship.block.v1`;
- `com.relay.relationship.mute.v1`;
- `com.relay.relationship.member.v1`;
- `com.relay.relationship.collaborator.v1`;
- `com.relay.relationship.trust.v1`; and
- `com.relay.relationship.endorse.v1`.

### Rationale

The source identifies these eight schemas as possible members of the core set rather than as mandatory v0.1 schema commitments. Consolidating them preserves their common optional status while retaining each candidate schema explicitly.

### Source

- REM-05-565
- REM-05-566
- REM-05-567
- REM-05-568
- REM-05-569
- REM-05-570
- REM-05-571
- REM-05-572
- `design-notes/05-relationship-model.md`, Section 54

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-364

### Title

Third-Party Relationship Schema Extensibility

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

Third parties **MAY** define relationship schemas beyond the Relay core relationship schema set.

### Rationale

The Relationship Model is intentionally extensible. A limited core must not become a closed vocabulary that prevents communities, applications or domains from defining additional portable relationship semantics.

### Source

- REM-05-573
- `design-notes/05-relationship-model.md`, Section 54

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-365

### Title

Custom Relationship Schema Semantic Contract

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A custom relationship schema **MUST** clearly define:

- the semantics of the relationship it represents;
- its direction semantics;
- any consent, acceptance or approval requirements governing creation and activation;
- whether the relationship conveys technical authority and, where applicable, the implications of that authority;
- the lifecycle applicable to the relationship; and
- the privacy expectations applicable to the relationship and its associated data.

### Rationale

Custom schemas remain interoperable only when their essential behavioural meaning is explicit. These six source-defined dimensions establish the minimum semantic contract needed for compatible implementations to distinguish relationship meaning, consent, authority, lifecycle and privacy rather than inferring them from schema names or application convention.

### Source

- REM-05-574
- REM-05-575
- REM-05-576
- REM-05-577
- REM-05-578
- REM-05-579
- `design-notes/05-relationship-model.md`, Section 54

### Related Invariants

- CI-02
- CI-10
- CI-12

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that form one source-defined option set or one source-defined schema contract:

- `REM-05-565` through `REM-05-572` are consolidated into `REL-REL-363`. The eight named schemas are presented together by the source as possible core schemas and all retain `MAY` strength. Consolidation does not make any individual candidate mandatory or imply that adoption of one requires adoption of the others.
- `REM-05-574` through `REM-05-579` are consolidated into `REL-REL-365`. Semantics, direction, consent requirements, authority implications, lifecycle and privacy expectations are the six mandatory elements of one custom relationship-schema semantic contract and all retain `MUST` strength.

No other REM-05 entries in the covered range are consolidated. The recommendation to maintain a limited core schema set and the permission for third parties to define additional schemas remain independently meaningful governance requirements.

All REM-05 requirements from `REM-05-564` through `REM-05-579` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 22 begins at `REM-05-564`, immediately after Part 21's final covered requirement `REM-05-563`.
- Coverage ends at `REM-05-579`, the end of source Section 54.
- Section 55 and later requirements are excluded from this part.
- The authoritative source was checked directly for Section 54.

## Numbering verification

- First catalogue requirement: `REL-REL-362`.
- Final catalogue requirement: `REL-REL-365`.
- Catalogue numbering continues directly from Part 21's `REL-REL-361`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- The limited core schema set retains `SHOULD` strength.
- Each of the eight named candidate core schemas retains `MAY` strength and is not promoted into a mandatory core commitment.
- Third-party schema definition remains permitted.
- All six source-defined custom-schema declarations retain `MUST` strength.
- Schema extensibility does not weaken the requirement for explicit semantics, direction, consent, authority, lifecycle and privacy expectations.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves the Relationship Model's intended balance between interoperability and extensibility. Relay may govern a deliberately limited core vocabulary, but the listed core schemas remain candidates rather than mandatory commitments, and third parties remain free to define additional relationship types. That extensibility is constrained by a clear semantic contract: custom schemas must state what the relationship means, how it is directed and consented to, whether it carries authority, how it changes over time, and what privacy expectations apply.

The next catalogue part should begin with `REM-05-580` / source Section 55 and continue catalogue numbering from `REL-REL-366`.