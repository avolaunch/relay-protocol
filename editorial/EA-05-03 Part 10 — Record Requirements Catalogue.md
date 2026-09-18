# EA-05-03 — Record Requirements Catalogue

## Part 10 — Creation Modes, Authorship Declarations and Evidentiary Limits

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines representation of creation modes, limits on inferring those modes from record style or content, recommended sources of creation-mode declarations, optional tool information, preservation of declarations and the evidentiary limit on claims of human authorship.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 13 and REM-03 requirements `REM-03-124` through `REM-03-139`.

It defines normative requirements governing:

- optional representation of different creation modes;
- prohibition of creation-mode assignment solely from style or content;
- recommended declaration or attestation sources;
- optional structured information about creation tools and their roles;
- preservation of authorised creation-mode declarations and associated metadata; and
- the limit on claims that Relay proves human authorship.

Source Section 14 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-124` through `REM-03-131` are consolidated because the source introduces one permission for multiple creation forms and then provides seven possible declarations. `REM-03-133` through `REM-03-136` are consolidated because the source applies one recommendation to four declaration or attestation sources. Every mode and source remains explicit and individually traceable.

The declaration list and JSON in Section 13 are illustrative and non-exclusive. They do not establish a closed creation-mode vocabulary, mandatory physical field names, mandatory tool roles, final schema content or wire syntax and therefore generate no additional catalogue requirements.

---

# 3. Requirements

---

## REL-REC-068

### Title

Creation-Mode Representation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Relay Record Model **MAY** represent multiple forms of human, assisted, automated, imported or unknown creation, including the following non-exclusive declarations:

- `human-created`;
- `human-assisted`;
- `AI-assisted`;
- `AI-generated`;
- `automated`;
- `imported`; and
- `unknown`, where the creation mode cannot be determined or responsibly asserted.

### Rationale

Creation-mode declarations allow records to communicate different forms of authorship and automation while retaining uncertainty where the mode cannot be responsibly established. The listed declarations are permitted options rather than a mandatory or closed vocabulary.

### Source

- REM-03-124
- REM-03-125
- REM-03-126
- REM-03-127
- REM-03-128
- REM-03-129
- REM-03-130
- REM-03-131
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-069

### Title

No Style-Only Creation-Mode Inference

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** assign a human, assisted, AI-generated, automated, imported or equivalent creation label solely by analysing the style or content of the record.

### Rationale

Style or content alone does not establish a record's creation mode. Preventing such analysis from being represented as a declared mode preserves the distinction between an authorised declaration or attestation and an unsupported inference.

### Source

- REM-03-132
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

## REL-REC-070

### Title

Creation-Mode Declaration Sources

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A creation-mode declaration **SHOULD** be capable of being:

- made by the record controller;
- made or attested by the submitting application;
- made or attested by a trusted creation system; or
- issued or attested by an external verification service.

### Rationale

Supporting multiple declaration sources allows creation mode to be represented in different operational contexts while leaving the applicable identity, trust, attestation and verification mechanisms to their governing specifications.

### Source

- REM-03-133
- REM-03-134
- REM-03-135
- REM-03-136
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-071

### Title

Structured Creation-Tool Information

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** include structured details about tools involved in its creation and the role performed by each tool.

### Rationale

Optional tool details can provide richer creation provenance without requiring them for every record or creation-mode declaration.

### Source

- REM-03-137
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

## REL-REC-072

### Title

Preservation of Creation Declarations

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** preserve authorised creation-mode declarations and associated creation metadata across record handling and migration.

### Rationale

Preservation prevents creation declarations and their supporting context from being lost as records are handled or moved, while making no claim that preservation proves the declarations true.

### Source

- REM-03-138
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-03
- CI-08
- CI-10

---

## REL-REC-073

### Title

No Universal Human-Authorship Claim

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay v0.1 **MUST NOT** claim that creation-mode declarations or provenance metadata provide universal proof of human authorship.

### Rationale

Relay can preserve declarations and attestations, but their existence does not solve the broader evidentiary problem of proving human authorship in every context.

### Source

- REM-03-139
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-124` | Consolidated creation-mode representation | `REL-REC-068` |
| `REM-03-125` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-126` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-127` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-128` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-129` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-130` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-131` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-132` | Direct | `REL-REC-069` |
| `REM-03-133` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-134` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-135` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-136` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-137` | Direct | `REL-REC-071` |
| `REM-03-138` | Direct | `REL-REC-072` |
| `REM-03-139` | Direct | `REL-REC-073` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated mode or declaration source in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 13 of `design-notes/03-record-model.md`.
- Source Sections 14–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-124` through `REM-03-139`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-067`.
- First identifier in this part: `REL-REC-068`.
- Final identifier in this part: `REL-REC-073`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–10.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-124` through `REM-03-131` retain individual traceability through the Source list and coverage table for `REL-REC-068`.
- `REM-03-133` through `REM-03-136` retain individual traceability through the Source list and coverage table for `REL-REC-070`.

## Creation-mode verification

- All seven listed creation-mode declarations remain explicit and optional.
- The declaration list remains non-exclusive and is not treated as a closed or final protocol vocabulary.
- No declaration is required for every record.
- `unknown` remains available where the creation mode cannot be determined or responsibly asserted.

## Inference-boundary verification

- A creation label must not be assigned solely from record style or content.
- The word “solely” remains explicit and is not broadened into a prohibition against every possible evidence-based assessment.
- An unsupported inference is not presented as an authorised creation-mode declaration or attestation.

## Declaration-source verification

- The controller, submitting application, trusted creation system and external verification service remain explicit supported sources.
- The declaration-source capability retains the source-level `SHOULD` strength.
- No identity, trust, attestation or verification mechanism is invented.

## Creation-information and preservation verification

- Structured tool and role information remains optional.
- Richer tool information is not required for every creation declaration.
- Preservation of authorised creation-mode declarations and associated creation metadata retains the source-level `SHOULD` strength.
- Declaration preservation remains distinct from proof that the declaration is true.

## Evidentiary-limit verification

- Relay v0.1 does not claim that creation-mode declarations or provenance metadata solve universal proof of human authorship.

## Illustrative-example verification

- The Section 13 declaration list and JSON generate no additional normative catalogue requirements.
- `creation`, `mode`, `tools`, `name` and `role` are not made mandatory physical field names.
- The example assistant name, `editing` role and `human-assisted` value are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No closed vocabulary, field name, verification mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 10 defines creation-mode representation, inference limits, declaration sources, creation-tool information, declaration preservation and the universal-human-authorship evidentiary boundary. It generates `REL-REC-068` through `REL-REC-073` from `REM-03-124` through `REM-03-139`.

The next catalogue part should begin with source Section 14 and `REM-03-140`.
