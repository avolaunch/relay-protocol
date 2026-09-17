# EA-05-05 — Relationship Requirements Catalogue

## Part 21 — Relationship Authority, Provider Migration and Application Replacement

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing separation of relationship meaning from technical authority, continuity across Relay Provider migration, and preservation of relationship state across application replacement.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-346`, following Part 20's coverage of algorithmic use and relationship-based access. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 51–53 and REM-05 requirements `REM-05-543` through `REM-05-563`.

It defines normative requirements governing:

- separation of social or organisational relationship meaning from technical authority;
- explicit declaration of relationship-derived authority;
- continuity of Relay Identifiers and relationship Record URIs across provider migration;
- post-migration identity and repository resolution;
- preservation of follows, memberships and collaborations across provider migration;
- provider migration as a relationship-portability conformance test;
- authorised relationship access by replacement applications;
- continuity and preservation of supported and unsupported relationship types;
- application-specific relationship views;
- application-independent relationship ownership; and
- non-deletion and non-mutation of unsupported relationship records.

Section 54 relationship schema governance and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-346

### Title

No Implicit Technical Authority From Relationship Existence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay implementation **MUST NOT** treat the existence or social or organisational meaning of a relationship as automatically granting broad application, repository or other technical authority to either participant.

### Rationale

Relationships describe or establish interpersonal, organisational or contextual state. Technical capabilities require their own explicit authority basis and cannot safely be inferred from social meaning alone.

### Source

- REM-05-543
- REM-05-544
- `design-notes/05-relationship-model.md`, Section 51

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-347

### Title

Explicit Declaration of Relationship-Derived Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Any technical authority associated with a relationship **MUST** be explicitly declared in an authority-bearing relationship or an applicable Permission Grant.

### Rationale

Explicit authority makes technical capability attributable and inspectable rather than an implicit consequence of relationship labels.

### Source

- REM-05-545
- `design-notes/05-relationship-model.md`, Section 51

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-348

### Title

Separation of Social Meaning and Technical Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relay implementations **MUST** maintain a semantic distinction between the social or organisational meaning of a relationship and any technical authority granted to a participant.

### Rationale

Applications may use relationship state as contextual information, but authority remains a distinct protocol concept requiring explicit authorisation.

### Source

- REM-05-546
- `design-notes/05-relationship-model.md`, Section 51

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-349

### Title

Relay Identifier Continuity Across Provider Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

When either the Source or Target identity of a relationship moves to a different Relay Provider, that identity's Relay Identifier **MUST** remain unchanged.

### Rationale

Provider location is not part of persistent Relay identity. Relationship portability depends on stable participant identifiers across infrastructure changes.

### Source

- REM-05-547
- REM-05-548
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-350

### Title

Relationship Record URI Continuity Across Provider Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship Record URI **MUST** remain unchanged when its Source or Target moves Relay Provider.

### Rationale

A provider move changes hosting or resolution location, not the persistent identity of the relationship record.

### Source

- REM-05-549
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-03

---

## REL-REL-351

### Title

Post-Migration Identity Resolution

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

After a Relay Identity changes provider, its Identity Document **MUST** resolve the identity to the new provider location according to the Identity Model.

### Rationale

Stable identity requires a mutable resolution layer capable of directing compatible applications to the identity's current provider.

### Source

- REM-05-550
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-352

### Title

Application Resolution After Provider Migration

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Compatible applications **MUST** resolve the current repository location after a provider migration rather than continuing to depend on the former provider location.

### Rationale

Stable identifiers provide portability only if applications resolve them dynamically enough to follow legitimate provider changes.

### Source

- REM-05-551
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-353

### Title

No Relationship Recreation Solely for Provider Migration

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A provider migration **MUST NOT** require an existing follow, membership or collaboration relationship to be recreated solely because the Source or Target changed provider.

### Rationale

These source-defined examples test whether relationship identity is genuinely portable rather than coupled to a hosting provider.

### Source

- REM-05-552
- REM-05-553
- REM-05-554
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-354

### Title

Operational Relationship Continuity Across Provider Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A conforming Relationship Model implementation **MUST** preserve operational relationship continuity across Relay Provider migration.

### Rationale

The source identifies this as the key portability test for the Relationship Model: stable identity and record references must permit compatible applications to continue using relationships without reconstruction.

### Source

- REM-05-555
- `design-notes/05-relationship-model.md`, Section 52

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-355

### Title

Authorised Relationship Reading by Replacement Applications

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

When a user changes compatible applications, the replacement application **MUST** be able to read relationship records for which it has the necessary authorisation and schema support.

### Rationale

Application portability requires relationship data to remain available independently of the application that previously presented or used it.

### Source

- REM-05-556
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-356

### Title

Supported Relationship Continuity After Application Replacement

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Relationship types supported by a replacement application **SHOULD** continue operating without requiring the user to recreate the underlying relationships.

### Rationale

A compatible application should consume existing portable relationship state rather than treating application replacement as relationship re-creation.

### Source

- REM-05-557
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03

---

## REL-REL-357

### Title

Preservation of Unsupported Relationship Types

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship type unsupported by a replacement application **MUST** remain preserved in its authoritative repository rather than being removed because the replacement application does not understand or display it.

### Rationale

Application capability must not determine the continued existence of canonical portable relationship state.

### Source

- REM-05-558
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03

---

## REL-REL-358

### Title

Application-Specific Relationship Views

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Compatible applications **MAY** present, organise or interpret authorised relationship records through different application-specific views, provided they do not silently alter canonical relationship semantics.

### Rationale

Application replacement preserves portable data and semantics without requiring identical interfaces or presentation models.

### Source

- REM-05-559
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03
- CI-12

---

## REL-REL-359

### Title

Application Replacement Does Not Transfer Relationship Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing applications **MUST NOT** transfer ownership or canonical authority over a relationship to either the former or replacement application.

### Rationale

Applications are clients of user-controlled relationship state, not canonical owners of that state.

### Source

- REM-05-560
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-360

### Title

Optional Non-Display of Unsupported Relationship Types

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A replacement client **MAY** choose not to display relationship types that it does not support.

### Rationale

Clients are not required to implement presentation for every extensible relationship schema. Non-display remains distinct from deletion, invalidation or mutation.

### Source

- REM-05-561
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03

---

## REL-REL-361

### Title

No Deletion or Silent Alteration of Unsupported Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A replacement client **MUST NOT** delete or silently alter a relationship record merely because the client does not support or understand its relationship type.

### Rationale

Unknown-schema preservation is necessary for forward compatibility and user ownership. A client's lack of support cannot become authority to destroy or rewrite canonical relationship state.

### Source

- REM-05-562
- REM-05-563
- `design-notes/05-relationship-model.md`, Section 53

### Related Invariants

- CI-03

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express the same source-defined rule across parallel participants, relationship examples or paired prohibited actions:

- `REM-05-543` and `REM-05-544` are consolidated into `REL-REL-346`. The colleague/repository-editing case is the source's concrete example of the broader prohibition on automatically deriving technical authority from relationship existence and shares `MUST NOT` strength.
- `REM-05-547` and `REM-05-548` are consolidated into `REL-REL-349`. They apply the same provider-migration identifier-continuity rule independently to Source and Target and share `MUST` strength.
- `REM-05-552` through `REM-05-554` are consolidated into `REL-REL-353`. Follow, membership and collaboration are the three source-defined relationship examples that must not require recreation solely because of provider migration and share `MUST NOT` strength.
- `REM-05-562` and `REM-05-563` are consolidated into `REL-REL-361`. Deletion and silent alteration are the paired source-defined prohibited treatments of unsupported relationship records and share `MUST NOT` strength.

No other REM-05 entries in the covered range are consolidated. Explicit authority declaration and semantic separation remain distinct; provider identifier continuity, record identity, resolution and operational continuity remain independently testable; and replacement-application reading, supported continuity, unsupported preservation, view autonomy, ownership independence and optional non-display remain separate requirements.

All REM-05 requirements from `REM-05-543` through `REM-05-563` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 21 begins at `REM-05-543`, immediately after Part 20's final covered requirement `REM-05-542`.
- Coverage ends at `REM-05-563`, the end of source Section 53.
- Section 54 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 51–53.

## Numbering verification

- First catalogue requirement: `REL-REL-346`.
- Final catalogue requirement: `REL-REL-361`.
- Catalogue numbering continues directly from Part 20's `REL-REL-345`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Relationship existence and social meaning remain prohibited from automatically granting broad technical authority.
- Relationship-derived technical authority remains explicitly declared through an authority-bearing relationship or Permission Grant.
- Source and Target Relay Identifiers and relationship Record URIs remain stable across provider migration.
- Identity Documents and applications remain responsible for resolving the new provider/repository location.
- Provider migration does not require recreation of follows, memberships or collaborations.
- Operational relationship continuity remains a conformance requirement for provider migration.
- Replacement applications retain authorised access to supported relationship records.
- Supported relationship continuity retains `SHOULD` strength.
- Unsupported relationship types remain preserved.
- Application-specific views and optional non-display remain permitted.
- Application replacement cannot transfer relationship ownership.
- Unsupported relationships cannot be deleted or silently altered merely because a replacement client does not support them.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part reinforces two core portability boundaries. First, social or organisational relationships do not themselves confer technical authority: authority must remain explicit and separately inspectable. Second, neither provider migration nor application replacement may break or appropriate canonical relationship state. Stable identifiers, dynamic resolution, unknown-schema preservation and application-independent ownership together allow relationships to survive changes in infrastructure and client software without reconstruction or silent mutation.

The next catalogue part should begin with `REM-05-564` / source Section 54 and continue catalogue numbering from `REL-REL-362`.