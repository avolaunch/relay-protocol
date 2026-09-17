# EA-05-03 — Record Requirements Catalogue

## Part 4 — Record Types, Schema Authority and Schema-Defined Behaviour

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how a schema identifier establishes a Relay Record's type and structure, what every record schema must define, how schema authority remains separate from record ownership and control, and which record behaviours a schema may define.

It also preserves the boundary between protocol-level validation and application-specific presentation.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 7 and REM-03 requirements `REM-03-057` through `REM-03-078`.

It defines normative requirements governing:

- schema identification of record type and structure;
- the information and behaviour every record schema must define;
- separation of schema namespaces from application or organisation ownership;
- identification of schema authority;
- continued repository and authorising-identity control when a third-party schema is used;
- optional schema-defined record behaviours; and
- separation of protocol-level validation from application-specific presentation.

Source Section 8 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-057` and `REM-03-058` are consolidated because they express the two effects of the same schema-identifier rule. `REM-03-059` through `REM-03-067` are consolidated because the source introduces one mandatory schema-definition obligation and enumerates the matters governed by that obligation. `REM-03-071` through `REM-03-077` are consolidated as the expressly optional behaviours listed under one schema-level permission. Each consolidated item remains explicit and individually traceable.

---

# 3. Requirements

---

## REL-REC-041

### Title

Schema Identification of Record Type and Structure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The schema identifier **MUST** define the Relay Record's type and structure.

### Rationale

Using the schema identifier for both type and structure gives implementations a common basis for determining what a record represents and which structural rules apply to it.

### Source

- REM-03-057
- REM-03-058
- `design-notes/03-record-model.md`, Section 7

### Related Invariants

- CI-08
- CI-09

---

## REL-REC-042

### Title

Mandatory Record Schema Definition

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A record schema **MUST** define:

- its required fields;
- its optional fields;
- its field types;
- its validation constraints;
- the meaning of each field;
- its supported operations;
- its compatibility rules;
- whether the record is singleton or repeatable; and
- whether updates are allowed or only superseding records are allowed.

### Rationale

A schema must state the structural, semantic, operational, compatibility and lifecycle rules needed for interoperable validation and handling of conforming records.

### Source

- REM-03-059
- REM-03-060
- REM-03-061
- REM-03-062
- REM-03-063
- REM-03-064
- REM-03-065
- REM-03-066
- REM-03-067
- `design-notes/03-record-model.md`, Section 7

### Related Invariants

- CI-08
- CI-12
- AI-09

---

## REL-REC-043

### Title

Schema Namespace Does Not Establish Record Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Use of an application-associated or organisation-associated schema namespace **MUST NOT** establish ownership of a conforming record by that application or organisation.

### Rationale

A namespace identifies who defines a schema, not who owns each record that uses it. Keeping those concepts separate preserves record independence from applications and organisations.

### Source

- REM-03-068
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-02
- CI-04

---

## REL-REC-044

### Title

Schema Namespace Authority Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema namespace **MUST** identify the schema authority.

### Rationale

Identifying the schema authority makes responsibility for the schema distinguishable from ownership or control of records that conform to it.

### Source

- REM-03-069
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-12

---

## REL-REC-045

### Title

Record Control When Using a Third-Party Schema

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Record that uses a third-party schema **MUST** remain controlled by its Relay Repository and authorising Relay Identity.

### Rationale

Schema authorship does not displace repository authority or the authorising identity's control of an individual record.

### Source

- REM-03-070
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-02
- CI-07
- AI-01

---

## REL-REC-046

### Title

Optional Schema-Defined Record Behaviour

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record schema **MAY** define:

- whether comments may reference the record;
- whether the record supports revisions;
- whether the record can expire;
- whether the record may be public;
- whether a field contains another Record URI;
- whether a blob is required; and
- whether multiple instances are allowed.

### Rationale

Schemas may govern behaviours specific to their record types without making any listed behaviour mandatory for every schema or record.

### Source

- REM-03-071
- REM-03-072
- REM-03-073
- REM-03-074
- REM-03-075
- REM-03-076
- REM-03-077
- `design-notes/03-record-model.md`, Section 7.2

### Related Invariants

- CI-12
- AI-09

---

## REL-REC-047

### Title

Protocol Validation and Application Presentation Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Protocol-level validation **MUST** remain separate from application-specific presentation.

### Rationale

Protocol validity must be determined by protocol and schema rules rather than by how a particular application chooses or is able to present a record.

### Source

- REM-03-078
- `design-notes/03-record-model.md`, Section 7.2

### Related Invariants

- CI-04
- CI-09

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-057` | Consolidated schema-identifier obligation | `REL-REC-041` |
| `REM-03-058` | Consolidated schema-identifier obligation | `REL-REC-041` |
| `REM-03-059` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-060` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-061` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-062` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-063` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-064` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-065` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-066` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-067` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-068` | Direct | `REL-REC-043` |
| `REM-03-069` | Direct | `REL-REC-044` |
| `REM-03-070` | Direct | `REL-REC-045` |
| `REM-03-071` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-072` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-073` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-074` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-075` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-076` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-077` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-078` | Direct | `REL-REC-047` |

No REM entry in scope is excluded from normative catalogue generation. The three consolidations follow the source's own aggregate rules and lists while retaining every item in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 7 of `design-notes/03-record-model.md`.
- Source Sections 8–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-057` through `REM-03-078`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-040`.
- First identifier in this part: `REL-REC-041`.
- Final identifier in this part: `REL-REC-047`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–4.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-057` and `REM-03-058` retain individual traceability through the Source list and coverage table for `REL-REC-041`.
- `REM-03-059` through `REM-03-067` retain individual traceability through the Source list and coverage table for `REL-REC-042`.
- `REM-03-071` through `REM-03-077` retain individual traceability through the Source list and coverage table for `REL-REC-046`.

## Schema-definition verification

- The schema identifier defines both record type and record structure.
- Every mandatory schema-definition concern listed in Section 7 remains explicit.
- No example namespace, final field name, schema syntax or implementation detail has been made normative.

## Authority and control verification

- A schema namespace does not establish record ownership by its associated application or organisation.
- The namespace identifies the schema authority.
- A record using a third-party schema remains controlled by its repository and authorising identity.
- Schema authority is not treated as authority over each conforming record.

## Optional-behaviour verification

- All seven schema-defined behaviours retain the source-level `MAY` framing.
- No listed behaviour is required to be defined or enabled by every schema.
- The source example namespace is not treated as a selected or mandatory namespace vocabulary.

## Validation-boundary verification

- Protocol-level validation remains separate from application-specific presentation.
- Presentation capability or choice does not determine protocol validity.
- No requirement or qualification has been imported from later Record Model sections.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- Consolidation does not remove any independently traceable obligation or optional behaviour.

---

# 6. Part conclusion

Part 4 defines schema identification, mandatory schema content, schema authority, record-control separation, optional schema-defined behaviour and the protocol-validation boundary. It generates `REL-REC-041` through `REL-REC-047` from `REM-03-057` through `REM-03-078`.

The next catalogue part should begin with source Section 8 and `REM-03-079`.
