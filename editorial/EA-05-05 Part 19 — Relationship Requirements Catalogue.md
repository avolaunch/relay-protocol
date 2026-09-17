# EA-05-05 — Relationship Requirements Catalogue

## Part 19 — Relationship Duplication, Uniqueness and Application Metadata

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing duplicate relationship creation across applications, schema-defined relationship uniqueness, coexistence of distinct relationship types and contexts, and separation of application-specific metadata from canonical relationship state.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-321`, following Part 18's coverage of relationship imports and legacy external targets. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 46–48 and REM-05 requirements `REM-05-506` through `REM-05-523`.

It defines catalogue treatment governing:

- the descriptive possibility that equivalent relationships may be created through multiple applications;
- repository prevention of accidental duplicate active relationships;
- source, target and context dimensions in duplicate detection;
- application independence of portable relationship state;
- schema-defined uniqueness constraints;
- representative follow and membership uniqueness rules;
- repository enforcement of declared uniqueness constraints;
- coexistence of different relationship types and contexts;
- local application relationship metadata;
- portable user-owned relationship metadata; and
- protection of canonical relationship records from application-interface rewrites.

Section 49 algorithmic use of relationships and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-321

### Title

Equivalent Relationship Creation Across Applications

**Level:** Descriptive

**Normative Keyword:** **MAY**

### Statement

Multiple applications **MAY** attempt to create semantically equivalent relationship records for the same Source, Target and context.

### Rationale

This records the interoperability condition that motivates duplicate-handling requirements. It does not independently impose a mandatory repository obligation or require duplicate creation to be accepted.

### Source

- REM-05-506
- `design-notes/05-relationship-model.md`, Section 46

### Related Invariants

- CI-03

---

## REL-REL-322

### Title

Accidental Active Relationship Duplicate Prevention

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Relay repository **SHOULD** prevent accidental duplicate active relationship records when the governing schema defines a single active relationship for a given Source, Target and context.

### Rationale

Portable relationships should not multiply merely because different compatible applications interact with the same user-controlled relationship state. Enforcement remains conditional on the schema defining the applicable uniqueness semantics.

### Source

- REM-05-507
- `design-notes/05-relationship-model.md`, Section 46

### Related Invariants

- CI-03

---

## REL-REL-323

### Title

Duplicate Detection Across Source, Target and Context

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where a relationship schema defines uniqueness by Source, Target and context, duplicate detection **SHOULD** evaluate all of those dimensions rather than treating Target identity alone as sufficient.

### Rationale

The same identities may legitimately participate in different relationship types or contextual relationships. Duplicate detection must therefore respect the dimensions actually declared by the governing schema.

### Source

- REM-05-508
- `design-notes/05-relationship-model.md`, Section 46

### Related Invariants

- CI-03

---

## REL-REL-324

### Title

No Client-Specific Duplicate Active Relationship Requirement

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A user **SHOULD NOT** be required to create a separate active relationship record solely because the same relationship is accessed or managed through a different compatible application.

### Rationale

The relationship is portable user-controlled state rather than state belonging to the client through which it is created or used.

### Source

- REM-05-509
- `design-notes/05-relationship-model.md`, Section 46

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-325

### Title

Separation of Application-Specific Relationship Metadata

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An implementation **MAY** store application-specific metadata separately from the canonical relationship record.

### Rationale

Local presentation and behavioural preferences can remain application-specific without duplicating or altering portable relationship semantics.

### Source

- REM-05-510
- `design-notes/05-relationship-model.md`, Section 46

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-326

### Title

Schema-Defined Relationship Uniqueness

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** define explicit uniqueness constraints governing how many active records of that relationship type may coexist for specified identity and context dimensions.

### Rationale

Different relationship types require different multiplicity rules. Expressing uniqueness at schema level allows repositories to enforce those semantics consistently without imposing one universal relationship cardinality rule.

### Source

- REM-05-511
- `design-notes/05-relationship-model.md`, Section 47

### Related Invariants

- CI-03

---

## REL-REL-327

### Title

Representative Relationship Uniqueness Rules

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** define type-appropriate uniqueness rules, including a single active follow from a given Source to a given Target or membership uniqueness across organisation, member and role.

### Rationale

The source provides follow and membership as representative examples of schema-defined uniqueness. They illustrate that the dimensions forming a uniqueness key can vary with relationship semantics and do not establish a closed vocabulary of permitted uniqueness rules.

### Source

- REM-05-512
- REM-05-513
- `design-notes/05-relationship-model.md`, Section 47

### Related Invariants

- CI-03

---

## REL-REL-328

### Title

Repository Enforcement of Schema Uniqueness

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Relay repository **SHOULD** enforce the uniqueness constraints declared by the governing relationship schema when accepting creation or activation of relationship records.

### Rationale

Schema-level uniqueness has operational value only when repositories apply it to relationship lifecycle operations that could otherwise create conflicting active records.

### Source

- REM-05-514
- `design-notes/05-relationship-model.md`, Section 47

### Related Invariants

- CI-03

---

## REL-REL-329

### Title

Coexistence of Different Relationship Types

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Different relationship types **MAY** coexist between the same identities where the governing schemas permit them.

### Rationale

Two identities can have more than one legitimate semantic relationship. Uniqueness within one relationship type must not silently collapse distinct relationship meanings into a single record.

### Source

- REM-05-515
- `design-notes/05-relationship-model.md`, Section 47

### Related Invariants

- CI-03

---

## REL-REL-330

### Title

Coexistence of Different Relationship Contexts

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Relationships in different contexts **MAY** coexist where the governing schema treats those contexts as independently valid.

### Rationale

A relationship scoped to one project, organisation, community or other context is not necessarily equivalent to a relationship involving the same identities in another context.

### Source

- REM-05-516
- `design-notes/05-relationship-model.md`, Section 47

### Related Invariants

- CI-03

---

## REL-REL-331

### Title

Local Application Relationship Metadata

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** maintain local relationship metadata including custom labels, feed priority, display grouping, notification settings and private notes, subject to applicable privacy and access controls.

### Rationale

The source identifies these values as examples of application-local state rather than canonical relationship semantics. Consolidating them preserves that shared role without requiring every application to implement every metadata category.

### Source

- REM-05-517
- REM-05-518
- REM-05-519
- REM-05-520
- REM-05-521
- `design-notes/05-relationship-model.md`, Section 48

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-332

### Title

Portable User-Owned Relationship Metadata

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Relationship metadata intended to remain portable across compatible applications **MAY** be represented in a separate record controlled by the user.

### Rationale

Separating portable preference or metadata state from the core relationship permits user-controlled metadata to travel across applications without changing the relationship's canonical protocol meaning.

### Source

- REM-05-522
- `design-notes/05-relationship-model.md`, Section 48

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-333

### Title

No Application-Interface Rewrite of Core Relationship

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** rewrite the canonical relationship record merely to satisfy application-specific interface, presentation or local-state requirements.

### Rationale

Application-specific behaviour belongs at the application or metadata layer unless it changes the protocol-level meaning of the relationship. This protects portable canonical state from client-specific coupling.

### Source

- REM-05-523
- `design-notes/05-relationship-model.md`, Section 48

### Related Invariants

- CI-02
- CI-03

---

# 4. Consolidation and Traceability Record

This part performs two bounded consolidations:

- `REM-05-512` and `REM-05-513` are consolidated into `REL-REL-327`. The follow and membership rules are the two source-defined examples of schema-specific uniqueness and both retain `MAY` strength. The catalogue statement preserves them as representative examples rather than a closed uniqueness vocabulary.
- `REM-05-517` through `REM-05-521` are consolidated into `REL-REL-331`. Custom labels, feed priority, display grouping, notification settings and private notes are the five source-defined examples of application-local relationship metadata and all retain `MAY` strength.

No other REM-05 entries in the covered range are consolidated. In particular:

- `REM-05-506` remains separately represented as a descriptive `MAY` condition and is not transformed into a repository obligation;
- `REM-05-507` and `REM-05-508` remain separate `SHOULD` requirements because duplicate prevention and the dimensions evaluated by duplicate detection are independently testable;
- `REM-05-509` retains `SHOULD NOT` strength;
- `REM-05-510` remains separate from `REM-05-522` because application-specific metadata separation and portable user-owned metadata are different storage concerns;
- `REM-05-511` remains separate from its examples and enforcement requirement; and
- `REM-05-515` and `REM-05-516` remain separate `MAY` requirements because coexistence by relationship type and coexistence by context are distinct semantic dimensions.

All REM-05 requirements from `REM-05-506` through `REM-05-523` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

No explicitly non-normative REM entries from the remediation-exclusion ranges occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 19 begins at `REM-05-506`, immediately after Part 18's final covered requirement `REM-05-505`.
- Coverage ends at `REM-05-523`, the end of source Section 48.
- Section 49 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 46–48.
- The remediated REM-05 Part 10 extraction was used for catalogue treatment.

## Numbering verification

- First catalogue requirement: `REL-REL-321`.
- Final catalogue requirement: `REL-REL-333`.
- Catalogue numbering continues directly from Part 18's `REL-REL-320`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- `REM-05-506` remains a descriptive `MAY` condition.
- `REM-05-508` retains `SHOULD` strength.
- `REM-05-509` retains `SHOULD NOT` strength.
- `REM-05-515` and `REM-05-516` each retain `MAY` strength and remain distinct.
- Duplicate prevention remains conditional on governing schema uniqueness semantics.
- Application changes do not become a reason to require duplicate portable relationships.
- Schema-defined uniqueness remains optional, while repository enforcement of declared constraints retains `SHOULD` strength.
- Application-local metadata remains optional and separate from protocol-level relationship semantics.
- Portable relationship metadata remains optionally representable as separate user-controlled state.
- Application-interface needs remain insufficient reason to rewrite canonical relationship state.

## Status-boundary verification

The special remediation-exclusion statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves the distinction between portable relationship semantics and application-specific use of those relationships. Schema-defined uniqueness can prevent accidental duplicate portable state without collapsing legitimately distinct relationship types or contexts. Application-specific metadata can remain local, while metadata intended to travel can be user-controlled in separate portable records. The core relationship therefore remains stable across compatible clients rather than being rewritten around individual interface requirements.

The next catalogue part should begin with `REM-05-524` / source Section 49 and continue catalogue numbering from `REL-REL-334`.