# EA-05-03 — Record Requirements Catalogue

## Part 11 — Record Visibility Classifications and Access Semantics

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the access-classification requirement for Relay Records, the recommended Relay v0.1 visibility classifications and the access and discovery semantics of public, unlisted, restricted and private records.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 14 and REM-03 requirements `REM-03-140` through `REM-03-151`.

It defines normative requirements governing:

- declaration or inheritance of record access classification;
- Relay v0.1 support for public, unlisted, restricted and private classifications;
- public-record readability;
- unlisted-record readability, discovery intent and ecosystem handling;
- restricted-record access authority; and
- controller and explicitly authorised service access to private records.

Source Section 15 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-141` through `REM-03-144` are consolidated because the source applies one recommendation to four access classifications. Every classification remains explicit and individually traceable. The remaining requirements are kept separate because they define independently testable access or discovery effects and, in several cases, carry different normative keywords.

The JSON in Section 14 is illustrative. It does not establish mandatory physical field names, final audience syntax or the audience rules defined in Section 15 and therefore generates no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-074

### Title

Record Access Classification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** declare or inherit an access classification.

### Rationale

An explicit or inherited classification provides the visibility context required to determine how a record may be accessed without requiring a particular physical field layout.

### Source

- REM-03-140
- `design-notes/03-record-model.md`, Section 14

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-075

### Title

Relay v0.1 Visibility Classifications

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** support the following access classifications:

- `public`;
- `unlisted`;
- `restricted`; and
- `private`.

### Rationale

The four recommended classifications provide distinct visibility modes for open access, URI-based access with reduced discovery, authority-limited access and controller-centred private access.

### Source

- REM-03-141
- REM-03-142
- REM-03-143
- REM-03-144
- `design-notes/03-record-model.md`, Section 14

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-076

### Title

Public Record Readability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A public record **MUST** be readable by any observer capable of resolving and accessing the repository through the protocol.

### Rationale

Public classification establishes open protocol readability for observers that can reach the repository. Readability does not itself grant separate reproduction, modification or usage rights.

### Source

- REM-03-145
- `design-notes/03-record-model.md`, Section 14.1

### Related Invariants

- CI-05
- AI-07

---

## REL-REC-077

### Title

Unlisted Record URI-Based Readability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An unlisted record **MUST** be readable by an observer possessing its stable Record URI, subject to the repository being resolvable and available.

### Rationale

Unlisted access relies on possession of the stable Record URI rather than identity-based authorisation, while remaining dependent on the repository being reachable.

### Source

- REM-03-146
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- CI-05
- AI-07

---

## REL-REC-078

### Title

Unlisted Non-Indexing Intent

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An unlisted classification **MUST** signal that the record is not intended for public indexing or general discovery.

### Rationale

The signal distinguishes reduced discoverability from restricted access: an unlisted record remains readable to a holder of its URI but is not intended for general indexing or discovery.

### Source

- REM-03-147
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- AI-07

---

## REL-REC-079

### Title

Honouring Unlisted Status

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Applications and indexers **SHOULD** honour an unlisted record's non-indexing and non-discovery intent.

### Rationale

Ecosystem observance gives practical effect to unlisted status while remaining a recommendation rather than a technical guarantee against indexing or disclosure by third parties.

### Source

- REM-03-148
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- CI-04
- AI-07

---

## REL-REC-080

### Title

Restricted Record Access Authority

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A restricted record **MUST** be readable only by identities, applications or groups holding valid access authority for that record.

### Rationale

Restricted classification conditions readability on valid access authority rather than on possession of the Record URI alone.

### Source

- REM-03-149
- `design-notes/03-record-model.md`, Section 14.3

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-081

### Title

Private Record Controller Access

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A private record **MUST** be readable by the controller.

### Rationale

Private classification retains the controller as the primary party authorised to read the record.

### Source

- REM-03-150
- `design-notes/03-record-model.md`, Section 14.4

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-082

### Title

Private Service Explicit Authorisation

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A private service **MUST NOT** read a private record unless it has been explicitly authorised to do so.

### Rationale

Private-record access by a service requires explicit authority; general application access or repository connectivity does not establish that authority.

### Source

- REM-03-151
- `design-notes/03-record-model.md`, Section 14.4

### Related Invariants

- CI-02
- CI-06
- AI-07

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-140` | Direct | `REL-REC-074` |
| `REM-03-141` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-142` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-143` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-144` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-145` | Direct | `REL-REC-076` |
| `REM-03-146` | Direct | `REL-REC-077` |
| `REM-03-147` | Direct | `REL-REC-078` |
| `REM-03-148` | Direct | `REL-REC-079` |
| `REM-03-149` | Direct | `REL-REC-080` |
| `REM-03-150` | Direct | `REL-REC-081` |
| `REM-03-151` | Direct | `REL-REC-082` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-141` through `REM-03-144` preserves all four recommended classifications in the Statement, Source list and coverage table for `REL-REC-075`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 14 of `design-notes/03-record-model.md`.
- Source Sections 15–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-140` through `REM-03-151`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-073`.
- First identifier in this part: `REL-REC-074`.
- Final identifier in this part: `REL-REC-082`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers are continuous and unique across Parts 1–11.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-141` through `REM-03-144` retain individual traceability through the Source list and coverage table for `REL-REC-075`.

## Classification verification

- Every Relay Record must declare or inherit an access classification.
- Declaration and inheritance remain distinct permitted means of supplying the classification.
- Public, unlisted, restricted and private support retains the source-level `SHOULD` strength.
- The four classifications retain distinct access semantics.
- No physical access-classification field layout is required.

## Public and unlisted verification

- Public records are readable by observers capable of resolving and accessing the repository through the protocol.
- Public readability does not create separate reproduction, modification or usage rights.
- An unlisted record is readable by a holder of its stable Record URI where the repository is resolvable and available.
- Unlisted access does not add an identity-authorisation requirement.
- Unlisted classification signals non-indexing and non-discovery intent.
- Applications and indexers retain the source-level `SHOULD` obligation to honour that intent.
- Unlisted status is not represented as secrecy, restricted access or a technical guarantee against third-party indexing or disclosure.

## Restricted and private verification

- Restricted readability requires valid access authority held by an identity, application or group.
- Possession of a restricted record's URI alone is not treated as sufficient authority.
- A private record remains readable by the controller.
- A private service requires explicit authorisation to read a private record.
- Controller access and private-service authorisation remain separate requirements with their respective `MUST` and `MUST NOT` keywords.

## Illustrative-example verification

- The Section 14 JSON generates no separate normative catalogue requirements.
- `visibility`, `classification` and `audience` are not made mandatory physical field names.
- The example identity, group, audience array and JSON structure are not treated as final access-control syntax.
- Section 15 audience or dynamic-audience rules are not imported from the example.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No access mechanism, field name, audience rule, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 11 defines access classification, recommended visibility modes and the access and discovery semantics of public, unlisted, restricted and private records. It generates `REL-REC-074` through `REL-REC-082` from `REM-03-140` through `REM-03-151`.

The next catalogue part should begin with source Section 15 and `REM-03-152`.
