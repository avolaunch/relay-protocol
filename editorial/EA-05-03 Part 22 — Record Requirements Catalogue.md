# EA-05-03 — Record Requirements Catalogue

## Part 22 — Inter-Record References, Version Pinning and Unavailable Targets

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines stable inter-record references, semantic relationship identification, logical and version-pinned targets and accurate handling when referenced targets become unavailable.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 25 and REM-03 requirements `REM-03-275` through `REM-03-281`.

It defines normative requirements governing reference addressing, reference semantics, target version selection, exact-version integrity and unavailable-target behaviour.

Source Section 26 and later sections are intentionally deferred to subsequent catalogue parts. No embedding or provenance requirement from Section 26 is imported.

The seven in-scope REM entries remain separate because each establishes an independently testable permission, recommendation, validity rule or application obligation. The example relationship names and JSON generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-133

### Title

Stable Record URI References

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** refer to another Relay Record using the target's stable Record URI.

### Rationale

Stable Record URI references allow relationships to survive changes of application, provider or storage location.

### Source

- REM-03-275
- `design-notes/03-record-model.md`, Section 25

### Related Invariants

- CI-02
- CI-08

---

## REL-REC-134

### Title

Semantic Relationship Identification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An inter-record reference **SHOULD** identify the semantic relationship between the referring record and its target.

### Rationale

Identifying reference semantics allows applications to interpret the relationship without selecting the illustrative relationship names as a mandatory vocabulary.

### Source

- REM-03-276
- `design-notes/03-record-model.md`, Section 25

### Related Invariants

- CI-08

---

## REL-REC-135

### Title

Logical-Record Reference

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reference **MAY** point to the continuing logical record without identifying a specific historical Record Version.

### Rationale

Logical-record references follow the continuing record identity and may resolve to its current version at access time.

### Source

- REM-03-277
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-136

### Title

Version-Pinned Reference

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reference **MAY** identify a specific historical Record Version.

### Rationale

Version pinning preserves the exact historical state selected by the referring record.

### Source

- REM-03-278
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-137

### Title

Exact-Version References for Verifiable Observations

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A quotation or signed assertion **SHOULD** use a version-pinned reference where verification depends on the exact record state observed at the time.

### Rationale

Pinning the observed version prevents later changes to the current logical record from altering the state on which verification depends.

### Source

- REM-03-279
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-138

### Title

Referring-Record Validity After Target Unavailability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A referring record **MUST NOT** become invalid solely because its referenced target later becomes deleted, restricted, unavailable, migrated or blocked by an application.

### Rationale

Target availability can change without changing the validity of the referring record itself.

### Source

- REM-03-280
- `design-notes/03-record-model.md`, Section 25.2

### Related Invariants

- CI-08

---

## REL-REC-139

### Title

Accurate Handling of Unavailable Reference Targets

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An application **MUST** accurately represent and handle a referenced target that is deleted, restricted, unavailable, migrated or blocked.

### Rationale

Accurate handling preserves the distinction between an unavailable target and an invalid referring record without prescribing a particular user interface or recovery mechanism.

### Source

- REM-03-281
- `design-notes/03-record-model.md`, Section 25.2

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-275` | Direct | `REL-REC-133` |
| `REM-03-276` | Direct | `REL-REC-134` |
| `REM-03-277` | Direct | `REL-REC-135` |
| `REM-03-278` | Direct | `REL-REC-136` |
| `REM-03-279` | Direct | `REL-REC-137` |
| `REM-03-280` | Direct | `REL-REC-138` |
| `REM-03-281` | Direct | `REL-REC-139` |

Every REM entry in scope maps directly to one catalogue requirement. No REM entry is consolidated or excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 25 of `design-notes/03-record-model.md`.
- Source Sections 26–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-275` through `REM-03-281`.
- No embedding or provenance requirement from Section 26 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-132`.
- First identifier in this part: `REL-REC-133`.
- Final identifier in this part: `REL-REC-139`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–22.

## Traceability verification

- Every in-scope normative REM entry is represented directly or through justified consolidation.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- Logical-record and version-pinned references remain separately traceable.
- Referring-record validity and application handling remain separate obligations.

## Reference-target verification

- Stable Record URI addressing retains `MAY` strength.
- Semantic relationship identification retains `SHOULD` strength.
- Logical-record and specific-version references remain distinct permissions.
- Exact-version referencing remains a `SHOULD` recommendation limited to cases where verification depends on the observed state.

## Unavailable-target verification

- Later target deletion, restriction, unavailability, migration or application blocking does not by itself invalidate the referring record.
- Applications remain responsible for accurate representation and handling of unavailable targets.
- No target content, substitute record, user-interface behaviour or recovery mechanism is invented.

## Illustrative-example verification

- The example relationship names and JSON generate no normative catalogue requirements.
- No example field name, relationship term, URI or structure becomes mandatory.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 22 defines resilient inter-record references, preserves logical and historical target choices and requires accurate handling of unavailable targets.

The next catalogue part should address Section 26.
