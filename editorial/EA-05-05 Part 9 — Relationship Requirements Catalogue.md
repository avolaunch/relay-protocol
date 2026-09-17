# EA-05-05 — Relationship Requirements Catalogue

## Part 9 — Relationship Evidence and Verification

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing relationship evidence, evidentiary status and the distinction between claimed and independently verified relationships.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-171`, following Part 8's coverage of relationship context and validity periods. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 22–23 and REM-05 requirements `REM-05-219` through `REM-05-250`.

It defines normative requirements governing:

- self-declared relationships;
- evidence-required relationship types;
- representative relationship categories for which schemas may require evidence;
- supported evidence forms;
- relationship evidentiary-status declaration and vocabulary;
- distinction between claimed and independently verified relationships;
- coexistence of claim and verification records;
- preservation of different evidentiary weight;
- prevention of false verification labels;
- verification provenance, method, date, scope, expiration and revocation status.

Section 24 authority-bearing relationships and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-171

### Title

Self-Declared Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationships declared solely by the Source identity where the applicable schema permits self-declaration.

### Rationale

Not every relationship requires third-party evidence. Relay must preserve the ability of an identity to make a valid relationship claim without falsely elevating that claim into independent verification.

### Source

- REM-05-219
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-172

### Title

Evidence-Required Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationship types whose validity or status depends on evidence.

### Rationale

Some relationship meanings cannot be established solely through self-assertion. The schema must therefore be able to make evidence material to validity or evidentiary status.

### Source

- REM-05-220
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-173

### Title

Schema-Required Evidence for Representative Relationship Types

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** require evidence for employment, professional-membership, legal-representation, guardianship, company-directorship, ownership or academic-affiliation relationships.

### Rationale

Section 22 presents these categories as examples of relationships that may require evidence. They illustrate schema-level evidentiary requirements without establishing a closed vocabulary or requiring evidence for every instance of every listed relationship type.

### Source

- REM-05-221
- REM-05-222
- REM-05-223
- REM-05-224
- REM-05-225
- REM-05-226
- REM-05-227
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-174

### Title

Supported Relationship Evidence Forms

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A relationship **MAY** reference or rely on a Verifiable Credential, independently authorised reciprocal relationship record, relevant organisation-issued assertion, recognised registry reference, legal document or schema-permitted application-specific attestation as evidence.

### Rationale

Section 22 lists these as possible evidence forms rather than mandating one universal verification mechanism. Their evidentiary meaning remains dependent on issuer, provenance, validity, scope and the applicable relationship schema.

### Source

- REM-05-228
- REM-05-229
- REM-05-230
- REM-05-231
- REM-05-232
- REM-05-233
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-175

### Title

Relationship Evidentiary-Status Declaration

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship record **SHOULD** declare the evidentiary status of the relationship.

### Rationale

Explicit evidentiary status permits applications to distinguish assertion, reciprocal confirmation, issuer attestation, credential backing, external verification and dispute rather than presenting all relationship records as equally substantiated.

### Source

- REM-05-234
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-10

---

## REL-REL-176

### Title

Relationship Evidentiary-Status Vocabulary

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The relationship evidence-status model **SHOULD** support `self-declared`, `reciprocally confirmed`, `issuer-attested`, `credential-backed`, `externally verified` and `disputed` classifications.

### Rationale

These source-defined classifications express materially different evidentiary conditions. Preserving them enables applications to communicate the basis and state of a relationship claim without collapsing distinct evidence states into a single verified/unverified flag.

### Source

- REM-05-235
- REM-05-236
- REM-05-237
- REM-05-238
- REM-05-239
- REM-05-240
- `design-notes/05-relationship-model.md`, Section 22

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-177

### Title

Claimed and Verified Relationship Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relay implementations **MUST** distinguish a relationship claimed by a party from a relationship supported by independent verification or issuer evidence.

### Rationale

A self-assertion and an independently substantiated relationship may express similar surface semantics while carrying materially different evidentiary meaning. Relay must preserve that distinction in the relationship model.

### Source

- REM-05-241
- `design-notes/05-relationship-model.md`, Section 23

### Related Invariants

- CI-10

---

## REL-REL-178

### Title

Coexistence of Relationship Claim and Verification Records

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A self-declared relationship record and a separately verified or credential-backed relationship record **MAY** coexist.

### Rationale

Independent evidence need not overwrite the original claim. Preserving both records permits their separate provenance, ownership and lifecycle to remain visible.

### Source

- REM-05-242
- `design-notes/05-relationship-model.md`, Section 23

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-179

### Title

Preservation of Different Evidentiary Weight

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Applications **MUST** treat self-declared and independently verified relationship records as carrying different evidentiary weight.

### Rationale

Relay does not prescribe one universal ranking among all evidence sources, but an application cannot erase the meaningful distinction between an unsupported claim and independent verification.

### Source

- REM-05-243
- `design-notes/05-relationship-model.md`, Section 23

### Related Invariants

- CI-10

---

## REL-REL-180

### Title

No False Verification Label for Self-Declared Relationships

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** describe a self-declared relationship as verified.

### Rationale

A self-declared relationship may be a legitimate record, but presenting it as verified would misrepresent its evidentiary basis.

### Source

- REM-05-244
- `design-notes/05-relationship-model.md`, Section 23

### Related Invariants

- CI-10

---

## REL-REL-181

### Title

Relationship Verification Metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relationship verification metadata **SHOULD** identify the verifier, verification method, verification date, verification scope, applicable expiration and revocation status.

### Rationale

These source-defined dimensions establish who performed verification, how and when it occurred, what was actually verified, and whether the evidentiary basis remains current. Together they provide the provenance and lifecycle context needed to interpret a verification claim.

### Source

- REM-05-245
- REM-05-246
- REM-05-247
- REM-05-248
- REM-05-249
- REM-05-250
- `design-notes/05-relationship-model.md`, Section 23

### Related Invariants

- CI-10
- AI-09

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined category set, evidence-form set, vocabulary or metadata structure:

- `REM-05-221` through `REM-05-227` are consolidated into `REL-REL-173`. Employment, professional membership, legal representation, guardianship, company directorship, ownership and academic affiliation are Section 22 examples of relationship types for which a schema may require evidence. They remain optional examples rather than seven mandatory evidence rules.
- `REM-05-228` through `REM-05-233` are consolidated into `REL-REL-174`. Verifiable Credentials, reciprocal signed relationships, organisation-issued assertions, registry references, legal documents and application-specific attestations are the source-listed forms of one optional relationship-evidence capability.
- `REM-05-235` through `REM-05-240` are consolidated into `REL-REL-176`. The six values form the source-defined evidentiary-status vocabulary and share the same `SHOULD` strength.
- `REM-05-245` through `REM-05-250` are consolidated into `REL-REL-181`. Verifier, method, date, scope, expiration and revocation status are six fields of the same verification-metadata recommendation and retain the source's `SHOULD` strength.

No other REM-05 entries in the covered range are consolidated. Support for self-declared and evidence-required relationship types remains separate because neither capability implies the other. Evidence-status declaration remains distinct from the vocabulary it can use. Claimed-versus-verified distinction, record coexistence, different evidentiary weight and false verification labelling each impose independently meaningful requirements.

All REM-05 requirements from `REM-05-219` through `REM-05-250` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 9 begins at `REM-05-219`, immediately after Part 8's final covered requirement `REM-05-218`.
- Coverage ends at `REM-05-250`, the end of source Section 23.
- Section 24 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 22–23.

## Numbering verification

- First catalogue requirement: `REL-REL-171`.
- Final catalogue requirement: `REL-REL-181`.
- Catalogue numbering continues directly from Part 8's `REL-REL-170`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Evidence-requiring relationship examples remain `MAY` schema capabilities rather than mandatory universal evidence rules.
- Evidence forms remain `MAY` options rather than a prescribed universal verification architecture.
- Evidentiary-status declaration and vocabulary retain `SHOULD` strength.
- Claimed-versus-verified distinction and different evidentiary weight retain their independent `MUST` obligations.
- Coexistence of claim and verification records remains `MAY`.
- The source's prohibition on describing a self-declared relationship as verified remains `SHOULD NOT` and has not been promoted to `MUST NOT`.
- Verification metadata retains `SHOULD` strength across all six source-defined dimensions.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves a central evidence boundary in the Relationship Model: Relay may record a person's own claim without treating that claim as independently verified. Evidence forms and evidence-status classifications remain extensible and schema-sensitive, while applications must preserve the material evidentiary difference between self-declaration and independent verification. Verification itself is accompanied by provenance and lifecycle metadata so that a verified label does not become an unqualified or permanent assertion.

The next catalogue part should begin with `REM-05-251` / source Section 24 and continue catalogue numbering from `REL-REL-182`.