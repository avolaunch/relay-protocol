# EA-05-03 — Record Requirements Catalogue

## Part 9 — Structured Provenance and Provenance Assurance

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines support for structured record provenance, the origin and processing information provenance may identify, the boundary between source declaration and verification, the assurance forms provenance may represent and the recommended indication of the applicable assurance level.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 12 and REM-03 requirements `REM-03-109` through `REM-03-123`.

It defines normative requirements governing:

- support for structured provenance information;
- optional identification of record origin, source, processing and migration information;
- separation of declared provenance from authentication or verification;
- optional provenance assurance representations; and
- indication of the applicable provenance assurance level.

Source Section 13 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-110` through `REM-03-117` are consolidated because the source introduces one permission for provenance to identify information and then enumerates eight optional matters. `REM-03-119` through `REM-03-122` are consolidated because the source introduces one permission for provenance to use four assurance representations. Every optional matter and assurance form remains explicit and individually traceable.

The JSON in Section 12 is illustrative. It does not establish mandatory physical field names, provenance-method vocabulary, schema content or final wire syntax and therefore generates no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-063

### Title

Structured Provenance Support

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Every Relay Record **SHOULD** support structured provenance information.

### Rationale

Structured provenance allows a record to carry interoperable information about its origin and processing history. The source recommends support for that information without requiring every record to contain provenance.

### Source

- REM-03-109
- `design-notes/03-record-model.md`, Section 12

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-064

### Title

Optional Provenance Information

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Record provenance **MAY** identify:

- whether the record was created directly;
- whether the record was imported;
- the service from which the record or its source material originated;
- a source record from which the record was imported, copied, derived or transformed;
- a source file used to create, import or transform the record;
- an AI system involved in creating, editing, transforming or processing the record;
- a process through which source material was transformed into the current record; and
- a migration event affecting the record.

### Rationale

These optional provenance elements allow implementations to describe different origins and processing histories without requiring every provenance representation to contain every element or prescribing how sources are stored or referenced.

### Source

- REM-03-110
- REM-03-111
- REM-03-112
- REM-03-113
- REM-03-114
- REM-03-115
- REM-03-116
- REM-03-117
- `design-notes/03-record-model.md`, Section 12

### Related Invariants

- CI-03
- CI-05
- CI-08
- CI-10

---

## REL-REC-065

### Title

Provenance Declaration Is Not Automatic Verification

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** treat a declared provenance source as automatically authenticated or verified solely because it appears in the record.

### Rationale

A source declaration states provenance but does not itself supply proof of source authenticity. Keeping declaration and verification separate prevents unverified metadata from being treated as established evidence.

### Source

- REM-03-118
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-066

### Title

Provenance Assurance Representations

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The provenance model **MAY** represent provenance information as:

- self-declared;
- application-attested;
- cryptographically verified; or
- externally issued by another identity or authority.

### Rationale

The four representations allow provenance to communicate different assurance bases without imposing a universal ranking, trust value or implementation mechanism.

### Source

- REM-03-119
- REM-03-120
- REM-03-121
- REM-03-122
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-067

### Title

Applicable Provenance Assurance Indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A record containing provenance information **SHOULD** indicate the applicable provenance assurance level.

### Rationale

Indicating the applicable assurance level helps consumers distinguish the basis on which provenance is presented while retaining the source's recommended rather than mandatory strength.

### Source

- REM-03-123
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-109` | Direct | `REL-REC-063` |
| `REM-03-110` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-111` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-112` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-113` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-114` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-115` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-116` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-117` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-118` | Direct | `REL-REC-065` |
| `REM-03-119` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-120` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-121` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-122` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-123` | Direct | `REL-REC-067` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated permission in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 12 of `design-notes/03-record-model.md`.
- Source Sections 13–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-109` through `REM-03-123`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-062`.
- First identifier in this part: `REL-REC-063`.
- Final identifier in this part: `REL-REC-067`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers are continuous and unique across Parts 1–9.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-110` through `REM-03-117` retain individual traceability through the Source list and coverage table for `REL-REC-064`.
- `REM-03-119` through `REM-03-122` retain individual traceability through the Source list and coverage table for `REL-REC-066`.

## Structured-provenance verification

- Structured provenance support retains the source-level `SHOULD` strength.
- Support for structured provenance is not converted into a requirement that every record contain provenance information.
- All eight provenance matters remain explicit and optional.
- No provenance representation is required to contain all eight matters.
- No source-reference format, embedding model, integrity-hash mechanism or storage arrangement is prescribed.
- AI-system identification does not assert the extent, nature or significance of the system's involvement.

## Declaration and verification boundary

- A declared source is not treated as automatically authenticated or verified.
- Provenance declaration and provenance verification remain separate concepts.

## Assurance-representation verification

- Self-declared, application-attested, cryptographically verified and externally issued provenance remain explicit optional representations.
- No universal ranking, trust value or equivalence is imposed among the four representations.
- No application-attestation mechanism, cryptographic algorithm, key model or external-issuance mechanism is selected.
- Indication of the applicable assurance level retains the source-level `SHOULD` strength.

## Illustrative-example verification

- The Section 12 JSON generates no separate normative catalogue requirements.
- `provenance`, `method`, `sourceService`, `sourceIdentifier`, `importedAt` and `importedBy` are not made mandatory physical field names.
- `imported`, the example service, source identifier, timestamp and application identity are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No assurance ranking, field name, cryptographic mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 9 defines structured provenance support, optional provenance information, the source-declaration verification boundary, provenance assurance representations and applicable-level indication. It generates `REL-REC-063` through `REL-REC-067` from `REM-03-109` through `REM-03-123`.

The next catalogue part should begin with source Section 13 and `REM-03-124`.
