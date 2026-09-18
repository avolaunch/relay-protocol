# EA-05-03 — Record Requirements Catalogue

## Part 15 — Layered Record Validation and Protocol-Validity Boundaries

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the layered Relay record-validation model, the distinct purpose of each substantive validation layer and the boundary between application-specific semantic checks and protocol validity.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 18 and REM-03 requirements `REM-03-193` through `REM-03-219`.

It defines normative requirements governing:

- separation of record validation into multiple levels;
- envelope, schema, authority and repository-state validation;
- optional application semantic validation; and
- separation of application-specific semantic validation from protocol validity.

Source Section 19 and later sections are intentionally deferred to subsequent catalogue parts. Section 17 canonical-creation conditions are not duplicated.

`REM-03-195` through `REM-03-199`, `REM-03-201` through `REM-03-204`, `REM-03-206` through `REM-03-209`, `REM-03-211` through `REM-03-214`, and `REM-03-216` through `REM-03-218` are explicit Non-normative validation examples. They illustrate possible checks within the five validation layers but do not establish mandatory algorithms, exhaustive checklists or final protocol rules and therefore generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-097

### Title

Multi-Level Record Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Relay record validation **MUST** distinguish multiple validation levels rather than treating all validity questions as one undifferentiated check.

### Rationale

Separating envelope, schema, authority, repository-state and semantic validation preserves the different questions each layer answers and prevents success at one layer from being interpreted as success at every other layer.

### Source

- REM-03-193
- `design-notes/03-record-model.md`, Section 18

### Related Invariants

- CI-08

---

## REL-REC-098

### Title

Envelope Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Envelope validation **MUST** check the record's protocol-level structure.

### Rationale

Envelope validation establishes structural protocol conformance while remaining distinct from schema-defined content, operation authority, repository state and application-specific meaning.

### Source

- REM-03-194
- `design-notes/03-record-model.md`, Section 18.1

### Related Invariants

- CI-08

---

## REL-REC-099

### Title

Schema Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Schema validation **MUST** check record content against the record's declared schema.

### Rationale

The declared schema supplies the applicable content constraints without allowing private application assumptions to substitute for schema conformance.

### Source

- REM-03-200
- `design-notes/03-record-model.md`, Section 18.2

### Related Invariants

- CI-08

---

## REL-REC-100

### Title

Authority Validation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Authority validation **MUST** determine whether the record operation was authorised.

### Rationale

Structural or schema validity does not establish that an operation was performed under valid authority.

### Source

- REM-03-205
- `design-notes/03-record-model.md`, Section 18.3

### Related Invariants

- CI-06
- CI-08

---

## REL-REC-101

### Title

Repository-State Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Repository-state validation **MUST** check the proposed operation against the repository's current state.

### Rationale

An operation can be structurally and schema-valid yet remain inconsistent with the repository state against which it is proposed.

### Source

- REM-03-210
- `design-notes/03-record-model.md`, Section 18.4

### Related Invariants

- AI-01
- CI-08

---

## REL-REC-102

### Title

Optional Application Semantic Validation

**Level:** Application

**Normative Keyword:** **MAY**

### Statement

An application **MAY** perform additional semantic or meaning-based validation checks.

### Rationale

Applications may evaluate meaning or suitability for their own contexts without making those checks universal protocol-validity conditions.

### Source

- REM-03-215
- `design-notes/03-record-model.md`, Section 18.5

### Related Invariants

- AI-07

---

## REL-REC-103

### Title

Semantic Validation Separate from Protocol Validity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Application-specific semantic validation **MUST** remain distinct from protocol validity.

### Rationale

An application may reject or hide a protocol-valid record under its own meaning-based or policy checks without making that record protocol-invalid.

### Source

- REM-03-219
- `design-notes/03-record-model.md`, Section 18.5

### Related Invariants

- AI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-193` | Direct | `REL-REC-097` |
| `REM-03-194` | Direct | `REL-REC-098` |
| `REM-03-195` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative URI check |
| `REM-03-196` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative identifier check |
| `REM-03-197` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative required-metadata check |
| `REM-03-198` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative encoding check |
| `REM-03-199` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative timestamp check |
| `REM-03-200` | Direct | `REL-REC-099` |
| `REM-03-201` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative required-field check |
| `REM-03-202` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative value-type check |
| `REM-03-203` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative length-constraint check |
| `REM-03-204` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative reference-constraint check |
| `REM-03-205` | Direct | `REL-REC-100` |
| `REM-03-206` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative controller-signature check |
| `REM-03-207` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative delegated-grant check |
| `REM-03-208` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative key-revocation check |
| `REM-03-209` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative authorisation-scope check |
| `REM-03-210` | Direct | `REL-REC-101` |
| `REM-03-211` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative Record Key uniqueness check |
| `REM-03-212` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative current-version check |
| `REM-03-213` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative referenced-commit check |
| `REM-03-214` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative singleton-constraint check |
| `REM-03-215` | Direct | `REL-REC-102` |
| `REM-03-216` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative URL-reachability check |
| `REM-03-217` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative media-suitability check |
| `REM-03-218` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative community-policy check |
| `REM-03-219` | Direct | `REL-REC-103` |

Every normative REM entry in scope maps directly to one catalogue requirement. All twenty non-normative validation examples remain explicitly accounted for but generate no normative catalogue requirements.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 18 of `design-notes/03-record-model.md`.
- Source Sections 19–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-193` through `REM-03-219`.
- Section 17 canonical-creation conditions are not duplicated.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-096`.
- First identifier in this part: `REL-REC-097`.
- Final identifier in this part: `REL-REC-103`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–15.

## Traceability verification

- Every normative REM entry in scope maps directly to one catalogue requirement.
- Every catalogue requirement cites one in-scope REM identifier and the authoritative design-note subsection.
- Every non-normative example REM entry is individually identified in the coverage table.
- No normative REM entries are consolidated or accounted for through an existing catalogue requirement in this part.

## Validation-layer verification

- Envelope, schema, authority, repository-state and semantic validation remain distinct and traceable.
- Success at one validation layer is not represented as automatically establishing success at another layer.
- Envelope validation remains limited to protocol-level structure.
- Schema validation remains tied to content and the declared schema.
- Authority validation remains tied to whether the operation was authorised.
- Repository-state validation remains tied to checking the operation against current repository state.
- Application semantic validation retains the source-level `MAY` strength.

## Protocol-validity boundary verification

- Application-specific semantic validation remains distinct from protocol validity.
- Application rejection or hiding under a meaning-based or policy check is not represented as making an otherwise protocol-valid record protocol-invalid.
- No application-specific semantic criterion is promoted into a universal protocol-validity condition.

## Non-normative validation-example verification

- `REM-03-195` through `REM-03-199`, `REM-03-201` through `REM-03-204`, `REM-03-206` through `REM-03-209`, `REM-03-211` through `REM-03-214`, and `REM-03-216` through `REM-03-218` generate no normative catalogue requirements.
- The example lists are not treated as exhaustive validation algorithms, mandatory checklists or final protocol rules.
- No example-derived URI, identifier, metadata, encoding, timestamp, field, type, length, reference, signature, grant, key, scope, state, version, commit, singleton, reachability, suitability or policy mechanism is invented or selected.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- No validation rule, algorithm, field name, schema detail, authority mechanism, repository-state procedure, application policy, implementation detail or requirement has been imported from another Record Model section.

---

# 6. Part conclusion

Part 15 establishes a layered record-validation model and preserves the boundary between optional application-specific semantic checks and protocol validity.

The next catalogue part should address Section 19 and record-update semantics.
