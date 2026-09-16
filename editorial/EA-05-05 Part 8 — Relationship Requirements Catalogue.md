# EA-05-05 — Relationship Requirements Catalogue

## Part 8 — Relationship Context and Validity Period

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing contextual relationship scope and relationship validity periods.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-156`, following Part 7's coverage of private relationships and visibility. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 20–21 and REM-05 requirements `REM-05-200` through `REM-05-218`.

It defines normative requirements governing:

- contextual relationship scope;
- representative project, organisation, content, temporal and community contexts;
- stable Record URI references for Relay Record contexts;
- context-specific roles;
- multiple contextual relationships between the same identities;
- prevention of global inference from context-specific relationships;
- relationship start, end, expiration, renewal and effective-time semantics;
- machine-readable validity bounds;
- historical verifiability after expiration;
- termination of current authority and access effects after expiration.

Section 22 relationship evidence and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-156

### Title

Contextual Relationship Scope

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A relationship **MAY** be scoped to a defined context.

### Rationale

Context permits a relationship to express meaning within a bounded project, organisation, topic, time period, community or other domain rather than being interpreted as universally applicable.

### Source

- REM-05-200
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-12

---

## REL-REL-157

### Title

Representative Relationship Contexts

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A contextual relationship **MAY** identify a project record, organisation, content category or topic, temporal scope, or specific community or group as its context.

### Rationale

Section 20 presents these as examples of the same contextual-scoping capability. They illustrate the model's ability to bind relationship meaning to different domains without establishing a closed context vocabulary.

### Source

- REM-05-201
- REM-05-202
- REM-05-203
- REM-05-204
- REM-05-205
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-12

---

## REL-REL-158

### Title

Stable Record Reference for Relationship Context

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Where a relationship context is a Relay Record, the relationship **MAY** identify that context using the record's stable Record URI.

### Rationale

A stable Record URI permits the contextual relationship to remain meaningful and portable independently of temporary application or provider URLs.

### Source

- REM-05-206
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-03
- CI-08

---

## REL-REL-159

### Title

Context-Specific Relationship Role

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A contextual relationship **MAY** identify the role held by the Source or Target within that context.

### Rationale

Context and role together can express a narrower relationship meaning, such as a particular role on a specific project, without asserting that role outside the identified context.

### Source

- REM-05-207
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-12

---

## REL-REL-160

### Title

Multiple Contextual Relationships Between Identical Participants

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** permit the same two identities to hold multiple distinct relationships in different contexts.

### Rationale

Source and Target identity alone do not uniquely determine relationship meaning. The same participants may collaborate, subscribe, hold roles or otherwise relate differently across distinct contexts.

### Source

- REM-05-208
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-12

---

## REL-REL-161

### Title

No Global Inference From Context-Specific Relationship

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** infer a global relationship from a relationship that is explicitly limited to a particular context.

### Rationale

Context is a semantic boundary. Treating a context-specific declaration as globally applicable would broaden its meaning beyond the Source's actual declaration.

### Source

- REM-05-209
- `design-notes/05-relationship-model.md`, Section 20

### Related Invariants

- CI-12

---

## REL-REL-162

### Title

Relationship Validity Start

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema or record **MAY** define the time from which the relationship begins.

### Rationale

A relationship's effective start may differ from record creation time, including where a declaration records an earlier relationship or becomes operative at a future time.

### Source

- REM-05-210
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- AI-09

---

## REL-REL-163

### Title

Relationship Validity End

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema or record **MAY** define the time at which the relationship ends.

### Rationale

An explicit end time permits current and historical relationship state to be distinguished without requiring deletion of the underlying record.

### Source

- REM-05-211
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- AI-09

---

## REL-REL-164

### Title

Relationship Expiration

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship **MAY** include an expiration condition or expiration time.

### Rationale

Expiration permits a relationship's current effects to cease automatically according to schema-defined temporal semantics while preserving historical state where appropriate.

### Source

- REM-05-212
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- AI-09

---

## REL-REL-165

### Title

Relationship Renewal

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** define whether and how an expiring or expired relationship can be renewed.

### Rationale

Different relationship types may require different renewal semantics, including fresh approval, evidence or issuance. Renewal therefore remains schema-governed rather than universal.

### Source

- REM-05-213
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- AI-09

---

## REL-REL-166

### Title

Relationship Effective Time

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship **MAY** declare the date or time at which its declared effects become effective.

### Rationale

Effective time can be semantically distinct from record creation, start of evidence or other lifecycle timestamps, particularly for formally dated relationships.

### Source

- REM-05-214
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- AI-09

---

## REL-REL-167

### Title

Machine-Readable Relationship Validity Bounds

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Where a relationship declares validity bounds, those bounds **SHOULD** be represented in a machine-readable form.

### Rationale

Machine-readable temporal bounds permit interoperable evaluation of relationship currency and expiration without depending on application-specific interpretation of human-readable dates.

### Source

- REM-05-215
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- CI-12
- AI-09

---

## REL-REL-168

### Title

Historical Verifiability After Relationship Expiration

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An expired relationship **MAY** remain historically verifiable after it ceases to be current.

### Rationale

Expiration governs current effect, not necessarily historical truth or provenance. Retaining verifiability permits past relationships to be demonstrated without treating them as presently active.

### Source

- REM-05-216
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- CI-10
- AI-09

---

## REL-REL-169

### Title

Expired Relationship Does Not Preserve Current Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An expired relationship **MUST NOT** continue to produce current authority solely on the basis of its former active state.

### Rationale

Historical verifiability must not silently reactivate authority that the validity period has ended. New authority requires a valid renewed, replacement or otherwise current basis.

### Source

- REM-05-217
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-170

### Title

Expired Relationship Does Not Preserve Current Access

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An expired relationship **MUST NOT** continue to grant current access solely because it remains historically verifiable.

### Rationale

Historical evidence and current access authority are separate concerns. Preserving proof that a relationship once existed must not extend access beyond its valid period.

### Source

- REM-05-218
- `design-notes/05-relationship-model.md`, Section 21

### Related Invariants

- CI-06
- AI-09

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express a single source-defined capability or illustrative category set:

- `REM-05-201` through `REM-05-205` are consolidated into `REL-REL-157`. Project, organisation, content/topic, temporal and community/group contexts are the source's illustrative examples of one contextual-scoping capability. The consolidation preserves every extracted context class without turning the examples into a closed or mandatory context vocabulary.

No other REM-05 entries in the covered range are consolidated. General contextual support, stable context-record references, context-specific roles, participant cardinality and inference limits are independently meaningful behaviours. Start time, end time, expiration, renewal and effective time remain separate temporal capabilities because supporting one does not imply supporting another. Historical verifiability, current authority and current access remain separate because expiration may preserve historical evidence while terminating distinct operational effects.

All REM-05 requirements from `REM-05-200` through `REM-05-218` are represented exactly once in the catalogue mapping, either independently or through the explicit consolidation above.

---

# 5. Editorial QA Record

## Scope verification

- Part 8 begins at `REM-05-200`, immediately after Part 7's final covered requirement `REM-05-199`.
- Coverage ends at `REM-05-218`, the end of source Section 21.
- Section 22 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 20–21.

## Numbering verification

- First catalogue requirement: `REL-REL-156`.
- Final catalogue requirement: `REL-REL-170`.
- Catalogue numbering continues directly from Part 7's `REL-REL-155`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- The consolidated requirement retains all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Source context examples remain `MAY` capabilities rather than mandatory schemas or a closed context vocabulary.
- Multiple relationships between identical participants remains a distinct `MUST` cardinality requirement.
- The prohibition on global inference remains `SHOULD NOT` and has not been promoted to `MUST NOT`.
- Optional validity dimensions remain separate `MAY` capabilities.
- Machine-readable validity bounds remain `SHOULD` rather than `MUST`.
- Historical verifiability remains compatible with mandatory termination of expired authority and access effects.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes context as an explicit semantic boundary rather than an application-local label, allowing the same identities to hold distinct relationships in different domains without those declarations being silently broadened into global relationships. It then separates temporal validity from historical verifiability: an expired relationship may remain provable, but that historical record cannot by itself preserve current authority or access.

The next catalogue part should begin with `REM-05-219` / source Section 22 and continue catalogue numbering from `REL-REL-171`.