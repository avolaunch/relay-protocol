# EA-05-05 — Relationship Requirements Catalogue

## Part 15 — Trust, Endorsements and Derived Reputation

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing scoped trust relationships, endorsements and reputation as a derived rather than canonical relationship layer.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-265`, following Part 14's coverage of blocks and mutes. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 36–38 and REM-05 requirements `REM-05-400` through `REM-05-438`.

It defines normative requirements governing:

- attributable and purpose-scoped trust declarations;
- trust targets and category limitations;
- prohibition on inferring universal trust from narrow trust;
- endorsement semantics and supported subjects;
- endorsement attribution, context, time, visibility and evidence metadata;
- endorser control and anti-fabrication requirements;
- the absence of a protocol-defined universal reputation score in Relay v0.1;
- permissible inputs to contextual reputation derivation;
- methodological plurality among reputation services;
- reputation-result provenance, context, freshness and limitations;
- separation of derived reputation results from canonical relationship records.

Section 39 relationship privacy risks and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-265

### Title

Scoped Attributable Trust Relationship

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay trust relationship **MUST** represent an attributable choice by the Source identity to rely on a Target for a defined purpose, and every such trust relationship **MUST** define the scope within which that reliance applies.

### Rationale

Trust in Relay is a source-controlled declaration of reliance, not an objective or universal property of the Target. Purpose and scope are therefore integral to the relationship's meaning rather than optional descriptive metadata.

### Source

- REM-05-400
- REM-05-404
- `design-notes/05-relationship-model.md`, Section 36

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-266

### Title

Trust Target Types

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A trust relationship **MUST** be capable of targeting a Relay Identity, a service or an organisation for a defined reliance, recommendation, moderation, verification or other scoped purpose.

### Rationale

Section 36 demonstrates trust across identity, service and organisational targets. These target forms share the same scoped-trust semantics and must remain addressable without converting trust in one function into general trust in the Target.

### Source

- REM-05-401
- REM-05-402
- REM-05-403
- `design-notes/05-relationship-model.md`, Section 36

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-267

### Title

Trust Purpose Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A trust relationship's context **MUST** be capable of identifying the purpose for which trust is granted.

### Rationale

Purpose supplies the primary semantic boundary for a trust declaration and prevents reliance for one function from being silently interpreted as reliance for another.

### Source

- REM-05-405
- `design-notes/05-relationship-model.md`, Section 36

### Related Invariants

- CI-12

---

## REL-REL-268

### Title

Trust Category Limitation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A trust relationship **MUST** support further limitation by categories relevant to its declared purpose.

### Rationale

Category scoping allows a Source to rely on the same Target for some judgements or functions but not others, preserving granular control within the broader purpose.

### Source

- REM-05-406
- `design-notes/05-relationship-model.md`, Section 36

### Related Invariants

- CI-12

---

## REL-REL-269

### Title

No Universal Trust Inference From Scoped Trust

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application or derived service **MUST NOT** infer or present a general universal trust score from a trust relationship limited to a particular purpose, category or context.

### Rationale

A narrow declaration of reliance cannot legitimately be transformed into a broad reputation or trust judgement that the Source did not make.

### Source

- REM-05-407
- `design-notes/05-relationship-model.md`, Section 36

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-270

### Title

Directed Attributable Endorsement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay endorsement **MUST** be represented as a directed assertion by an endorsing identity expressing support for a defined Target or subject.

### Rationale

An endorsement is attributable to the endorser and communicates that identity's support. It does not become an assertion authored or controlled by the endorsed Target.

### Source

- REM-05-408
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-271

### Title

Endorsement Target and Subject Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An endorsement **MUST** be capable of expressing support for a person represented by a Relay Identity, a specific Relay Record, a defined skill or a defined claim.

### Rationale

Section 37 defines person, record, skill and claim as supported endorsement subjects. Treating them as one target-and-subject capability preserves their shared mandatory support requirement while allowing schemas to distinguish their representation.

### Source

- REM-05-409
- REM-05-410
- REM-05-411
- REM-05-412
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-272

### Title

Endorsement Structural Metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An endorsement **SHOULD** identify the endorser, Target, subject, relevant context, issue date or time, visibility or access classification, and whether supporting evidence is included or referenced.

### Rationale

These source-defined dimensions establish attribution, semantic scope, temporal context, disclosure treatment and evidentiary status. Together they make an endorsement independently interpretable without broadening its meaning beyond what the endorser asserted.

### Source

- REM-05-413
- REM-05-414
- REM-05-415
- REM-05-416
- REM-05-417
- REM-05-418
- REM-05-419
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-273

### Title

Specific Endorsement Subject Context

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An endorsement's context **MUST** be capable of identifying a specific subject such as a skill or professional domain.

### Rationale

Specific subject context prevents a narrow endorsement from being interpreted as broad or unconditional support for the Target.

### Source

- REM-05-420
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-12

---

## REL-REL-274

### Title

Endorser Control of Endorsement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The endorsing identity **MUST** retain control over its endorsement declaration.

### Rationale

The endorsement expresses the endorser's assertion and therefore remains under the endorser's independent authority throughout its lifecycle.

### Source

- REM-05-421
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-275

### Title

Target Cannot Rewrite or Fabricate Endorsement

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Target of an endorsement **MUST NOT** be permitted to rewrite the endorser's endorsement record or create an endorsement falsely attributed to another identity.

### Rationale

Both rewriting and fabrication would transfer authorship or control away from the actual endorser and destroy the endorsement's attributable integrity.

### Source

- REM-05-422
- REM-05-423
- `design-notes/05-relationship-model.md`, Section 37

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-276

### Title

No Universal Reputation Score in Relay v0.1

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

Relay v0.1 **SHOULD NOT** define or mandate a universal reputation score applicable across identities, applications or contexts.

### Rationale

Reputation is contextual and method-dependent. Establishing one protocol-level universal score would collapse differing purposes, inputs and application judgements into an apparently canonical assessment.

### Source

- REM-05-424
- `design-notes/05-relationship-model.md`, Section 38

### Related Invariants

- CI-12

---

## REL-REL-277

### Title

Contextual Reputation Inputs

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A reputation application or service **MAY** derive a contextual reputation result from relationship records, credentials, endorsements, attributable activity, moderation labels, application-specific behaviour and attributable community participation.

### Rationale

Section 38 identifies these as permissible reputation inputs rather than a mandatory or exhaustive formula. Each service may select inputs appropriate to its declared context while preserving the provenance and limitations of the resulting derivation.

### Source

- REM-05-425
- REM-05-426
- REM-05-427
- REM-05-428
- REM-05-429
- REM-05-430
- REM-05-431
- `design-notes/05-relationship-model.md`, Section 38

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-278

### Title

Reputation Methodological Plurality

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The protocol **MUST** permit different applications or services to calculate reputation using different methodologies and inputs.

### Rationale

A derived reputation result belongs to the service that computes it, not to the protocol as a canonical assessment. Methodological plurality preserves application autonomy and contextual interpretation.

### Source

- REM-05-432
- `design-notes/05-relationship-model.md`, Section 38

### Related Invariants

- CI-12

---

## REL-REL-279

### Title

Derived Reputation Result Provenance and Limitations

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every derived reputation result **MUST** identify the application or service that produced it, the source inputs or input categories used, the relevant interpretive context, the calculation or last-update time, and material limitations affecting its coverage, accuracy or interpretation.

### Rationale

These source-defined dimensions make a derived result attributable and interpretable. They allow consumers to distinguish who calculated the result, what informed it, where it applies, how current it is and what uncertainty or incompleteness constrains its use.

### Source

- REM-05-433
- REM-05-434
- REM-05-435
- REM-05-436
- REM-05-437
- `design-notes/05-relationship-model.md`, Section 38

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-280

### Title

Separation of Reputation Result From Source Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A derived reputation result **MUST** remain a separate object or view from the underlying relationship records used to calculate it.

### Rationale

Derived reputation must not overwrite, replace or become the canonical owner of source relationships. The underlying records retain their own provenance, authority and lifecycle independently of any score or derived assessment.

### Source

- REM-05-438
- `design-notes/05-relationship-model.md`, Section 38

### Related Invariants

- CI-02
- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that form a single source-defined semantic unit, supported target set, metadata structure or option set:

- `REM-05-400` and `REM-05-404` are consolidated into `REL-REL-265`. Attributable reliance for a defined purpose and mandatory scoping are inseparable defining semantics of a Relay trust relationship and share `MUST` strength.
- `REM-05-401` through `REM-05-403` are consolidated into `REL-REL-266`. Identity, service and organisation are the three source-demonstrated mandatory trust target capabilities and share `MUST` strength.
- `REM-05-409` through `REM-05-412` are consolidated into `REL-REL-271`. Person, record, skill and claim are the source-defined endorsement target or subject forms and share mandatory support strength.
- `REM-05-413` through `REM-05-419` are consolidated into `REL-REL-272`. Endorser, Target, subject, context, date, visibility and evidence inclusion are the seven source-defined endorsement metadata recommendations and share `SHOULD` strength.
- `REM-05-422` and `REM-05-423` are consolidated into `REL-REL-275`. Rewriting and fabrication are the paired source prohibitions protecting endorsement attribution and share `MUST NOT` strength.
- `REM-05-425` through `REM-05-431` are consolidated into `REL-REL-277`. Relationships, credentials, endorsements, activity, moderation labels, application-specific behaviour and community participation are the seven source-defined optional reputation inputs and share `MAY` strength.
- `REM-05-433` through `REM-05-437` are consolidated into `REL-REL-279`. Producing service, source inputs, context, calculation time and limitations are the five mandatory provenance and interpretation dimensions for a derived reputation result and share `MUST` strength.

No other REM-05 entries in the covered range are consolidated. Trust purpose identification, category limitation and universal-trust inference remain independently meaningful requirements. Endorsement definition, specific subject context and endorser control remain separate. The Relay v0.1 universal-reputation boundary, methodological plurality and separation of derived results from source relationships likewise remain independently testable.

All REM-05 requirements from `REM-05-400` through `REM-05-438` are represented exactly once in the catalogue mapping, either independently or through the seven explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 15 begins at `REM-05-400`, immediately after Part 14's final covered requirement `REM-05-399`.
- Coverage ends at `REM-05-438`, the end of source Section 38.
- Section 39 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 36–38.

## Numbering verification

- First catalogue requirement: `REL-REL-265`.
- Final catalogue requirement: `REL-REL-280`.
- Catalogue numbering continues directly from Part 14's `REL-REL-264`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Trust remains an attributable, mandatory and explicitly scoped declaration.
- Identity, service and organisation trust-target support remains mandatory.
- Purpose and category limitation remain mandatory capabilities.
- Universal trust inference from narrow trust remains prohibited.
- Endorsements remain directed attributable assertions with mandatory support for the source-defined target and subject forms.
- Endorsement metadata retains `SHOULD` strength.
- Endorser control remains mandatory and Target rewriting or fabrication remains prohibited.
- The Relay v0.1 universal reputation score boundary retains `SHOULD NOT` strength.
- Reputation inputs remain optional rather than becoming a mandatory formula.
- Methodological plurality remains mandatory protocol behaviour.
- Reputation-result provenance and limitation fields remain mandatory.
- Derived reputation remains separate from canonical source relationships.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part keeps trust, endorsement and reputation at deliberately different semantic layers. Trust is an attributable and tightly scoped choice by one identity to rely on a Target. An endorsement is an independently controlled directed assertion of support. Reputation is a service-produced derivation that may consume those and other inputs but does not become canonical protocol truth or take ownership of the underlying records. The catalogue therefore preserves context, attribution and methodological plurality while preventing narrow trust or source records from being silently transformed into universal assessments.

The next catalogue part should begin with `REM-05-439` / source Section 39 and continue catalogue numbering from `REL-REL-281`.