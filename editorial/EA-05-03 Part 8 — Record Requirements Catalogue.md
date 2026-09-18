# EA-05-03 — Record Requirements Catalogue

## Part 8 — Issued Assertions, Holder Storage and Signed-Claim Integrity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines support for assertions issued by an identity other than the record subject, the information an issued assertion must distinguish, the holder's permission to store an assertion and the integrity rule governing alteration of an issuer's signed claim.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 11 and REM-03 requirements `REM-03-099` through `REM-03-108`.

It defines normative requirements governing:

- support for assertions made by an identity other than the record subject;
- identification of the issuer, subject and holder repository;
- representation of issuance time, expiration and revocation status;
- inclusion or reference of an issuer signature;
- holder storage of an issued assertion or credential; and
- validity of the issuer signature when the signed claim is altered.

Source Section 12 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-100` through `REM-03-106` are consolidated because the source imposes one mandatory distinction rule and then enumerates the seven items governed by it. Every item remains explicit and individually traceable.

The prose and JSON examples in Section 11 are illustrative. They do not establish an exhaustive set of assertion issuers or types, mandatory physical field names, final schema content, cryptographic mechanisms or wire syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-059

### Title

Externally Issued Assertion Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support records containing assertions made by an identity other than the record subject.

### Rationale

Externally issued assertions allow records to represent claims whose authority comes from an issuer distinct from the identity or object to which the claim applies.

### Source

- REM-03-099
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-08
- CI-12

---

## REL-REC-060

### Title

Required Issued-Assertion Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An issued assertion record **MUST** distinguish:

- the issuer of the assertion;
- the subject to whom or to which the assertion applies;
- the repository holding the assertion record;
- the time at which the assertion was issued;
- whether the assertion expires and, where applicable, its expiration time or condition;
- the assertion's revocation status; and
- an issuer signature, contained or referenced, that is capable of binding the issuer to the signed assertion.

### Rationale

These distinctions allow implementations to determine who made the claim, what it concerns, where it is held, its lifecycle status and whether its signed content remains attributable to the issuer.

### Source

- REM-03-100
- REM-03-101
- REM-03-102
- REM-03-103
- REM-03-104
- REM-03-105
- REM-03-106
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-07
- CI-08
- CI-10

---

## REL-REC-061

### Title

Holder Storage of Issued Assertions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A holder **MAY** store an issued assertion or credential in the holder's Relay Repository.

### Rationale

Holder storage supports portability and repository-based custody without transferring issuer authority or granting permission to alter the issuer's signed claim.

### Source

- REM-03-107
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-03
- CI-07

---

## REL-REC-062

### Title

Signed-Claim Integrity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A holder or other non-issuer **MUST NOT** alter the issuer's signed claim while continuing to represent the issuer signature as valid.

### Rationale

An issuer signature can attest only to the claim content the issuer signed. Altering that content invalidates the original signature unless the issuer signs the altered content as a new assertion.

### Source

- REM-03-108
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-08
- CI-10

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-099` | Direct | `REL-REC-059` |
| `REM-03-100` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-101` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-102` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-103` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-104` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-105` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-106` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-107` | Direct | `REL-REC-061` |
| `REM-03-108` | Direct | `REL-REC-062` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-100` through `REM-03-106` retains all seven mandatory distinctions in the Statement, Source list and coverage table for `REL-REC-060`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 11 of `design-notes/03-record-model.md`.
- Source Sections 12–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-099` through `REM-03-108`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-058`.
- First identifier in this part: `REL-REC-059`.
- Final identifier in this part: `REL-REC-062`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–8.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-100` through `REM-03-106` retain individual traceability through the Source list and coverage table for `REL-REC-060`.

## Issued-assertion verification

- The Record Model supports assertions made by an identity other than the record subject.
- Issuer, subject and holder repository remain distinct concepts.
- Issuance time is not conflated with repository acceptance or import time.
- Expiration and revocation status remain represented as separate lifecycle concerns.
- No revocation-resolution mechanism is invented.
- The issuer signature may be contained or referenced and must bind the issuer to the signed assertion.
- No signature algorithm, encoding or key-resolution mechanism is selected.

## Holder-storage verification

- Holder storage retains the source-level `MAY` strength.
- Storage does not transfer issuer authority.
- Storage does not permit alteration of the issuer's signed claim while preserving the signature's represented validity.

## Signed-claim verification

- The prohibition applies when a holder or other non-issuer alters the signed claim while continuing to represent the issuer signature as valid.
- The rule does not prohibit storage of the assertion or management of information outside the signed claim.
- Altered claim content requires invalidation of the original signature unless the issuer signs the altered content as a new assertion.

## Illustrative-example verification

- Section 11 prose and JSON examples generate no separate normative catalogue requirements.
- Universities, employers, professional bodies and communities are not treated as an exhaustive issuer or assertion-type set.
- `schema`, `issuer`, `subject`, `issuedAt`, `expiresAt`, `credential` and `issuerSignature` are not made mandatory physical field names.
- The example schema identifier, identities, qualification, timestamp, null value and signature placeholder are not treated as final schema content or wire syntax.
- Omission of holder-repository and revocation-status representations from the example JSON does not weaken the source's mandatory distinction list.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No physical field, cryptographic mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 8 defines externally issued assertions, their required distinguishing information, holder storage permission and signed-claim integrity. It generates `REL-REC-059` through `REL-REC-062` from `REM-03-099` through `REM-03-108`.

The next catalogue part should begin with source Section 12 and `REM-03-109`.
