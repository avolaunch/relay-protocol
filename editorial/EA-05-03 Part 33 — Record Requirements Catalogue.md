# EA-05-03 — Record Requirements Catalogue

## Part 33 — Reactions

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 36, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 36 and REM-03 entries `REM-03-361` through `REM-03-367`.

Source Section 37 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-363`, `REM-03-364` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-208

### Title

Reaction represented as a record

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A reaction **SHOULD** normally be represented as an independently addressable Relay Record.

### Rationale

The source establishes record representation as the normal model while leaving room for exceptional schema-specific approaches.

### Source

- REM-03-361
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

None identified.

---

## REL-REC-209

### Title

Reaction ownership by reacting identity

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A reaction record **SHOULD** normally be controlled by the Relay Repository and authority of the identity that performed the reaction.

### Rationale

The identity controlling the target content does not thereby own reactions made by other identities.

### Source

- REM-03-362
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-02

---

## REL-REC-210

### Title

Reaction aggregation permitted

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** aggregate individual reaction records into counts or equivalent derived summaries.

### Rationale

Aggregation does not replace the underlying canonical reaction records.

### Source

- REM-03-365
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

None identified.

---

## REL-REC-211

### Title

Reaction count is derived

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An aggregate reaction count **MUST** be treated as a derived value rather than as the underlying canonical reaction objects.

### Rationale

A count may change as reaction records are created, deleted, restricted or become unavailable.

### Source

- REM-03-366
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-07

---

## REL-REC-212

### Title

Individual reactions remain canonical

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Individual accepted reaction records **MUST** remain the underlying canonical objects from which aggregate reaction values are derived.

### Rationale

Applications must not substitute an untraceable count for the canonical reaction records where record-level verification or ownership matters.

### Source

- REM-03-367
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-361` | Direct | `REL-REC-208` |
| `REM-03-362` | Direct | `REL-REC-209` |
| `REM-03-363` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-364` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-365` | Direct | `REL-REC-210` |
| `REM-03-366` | Direct | `REL-REC-211` |
| `REM-03-367` | Direct | `REL-REC-212` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 36 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-361` through `REM-03-367`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-207`.
- First identifier in this part: `REL-REC-208`.
- Final identifier in this part: `REL-REC-212`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–33.

## Traceability verification

- Every settled normative rule in scope maps directly or through justified decomposition to a catalogue requirement.
- Every generated requirement cites its in-scope REM identifier and authoritative design-note section.
- Every excluded entry remains individually accounted for in the coverage table.

## Source-status and implementation-neutrality verification

- Normative strength and material qualifications are preserved.
- Illustrative examples and open design questions do not become protocol requirements.
- No example vocabulary, physical field, syntax, mechanism or implementation detail is made mandatory unless the source establishes that obligation.
- Extraction Notes are used as rationale only and do not broaden the authoritative source rule.

## Normative-language verification

- Each generated catalogue requirement carries one explicit normative keyword.
- No later-section requirement is imported.

---

# 6. Part conclusion

Part 33 catalogues the settled normative content of Record Model Section 36 and excludes 2 explicitly non-normative entries.

The next catalogue part should address Section 37.
