# EA-05-05 — Relationship Requirements Catalogue

## Part 18 — Relationship Imports and Legacy External Targets

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing import of relationship data from external platforms and temporary use of legacy external identifiers as relationship targets.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-309`, following Part 17's coverage of reverse relationships, indexes and event delivery. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 44–45 and REM-05 requirements `REM-05-489` through `REM-05-505`.

It defines normative requirements governing:

- optional import of external relationship data;
- mandatory provenance for imported relationships;
- import method, source-service and timestamp provenance;
- verification boundaries for imported usernames and external identifiers;
- verified matching and user-confirmed matching workflows;
- unresolved external references and later verified upgrades;
- temporary external relationship targets;
- explicit typing, service namespace and identifier preservation for external targets;
- portability limitations of external targets; and
- preservation of import provenance when an external target is upgraded to a verified Relay Identity.

Section 46 relationship duplication and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-309

### Title

External Relationship Import Capability

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay implementation **MAY** allow a user to import relationship data from an external platform.

### Rationale

Import provides a migration path from legacy services into user-controlled Relay relationship state without making the external platform authoritative for Relay records.

### Source

- REM-05-489
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-310

### Title

Imported Relationship Provenance

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every imported relationship **MUST** include machine-readable provenance identifying that it originated through an import process, the external source service where known, and the time at which the import occurred.

### Rationale

Imported relationship data must remain distinguishable from relationships established natively through Relay authorisation. Method, source and import time provide the minimum source-defined provenance needed to interpret and audit that distinction.

### Source

- REM-05-490
- REM-05-491
- REM-05-492
- REM-05-493
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-311

### Title

No Automatic Relay Identity Verification From Imported Identifier

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

An importer **SHOULD NOT** treat an imported username, handle or external identifier as a verified match to a Relay Identity without an appropriate verification basis.

### Rationale

An external identifier establishes a reference within another service's namespace; it does not by itself establish control of, or equivalence to, a Relay Identity.

### Source

- REM-05-494
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-312

### Title

Verified External Account Matching

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An importer **MAY** link an external relationship target to a Relay Identity when the external account has been validly verified as belonging to that Relay Identity.

### Rationale

Verified matching permits an imported reference to become resolvable through Relay while retaining a defensible basis for the identity association.

### Source

- REM-05-495
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02

---

## REL-REL-313

### Title

User Confirmation of Proposed Import Matches

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An importer **MAY** ask the importing user to confirm proposed matches between external identifiers and Relay Identities.

### Rationale

User confirmation can assist migration and matching workflows, but it remains attributable to the importing user and does not automatically become independent verification by the proposed Target identity.

### Source

- REM-05-496
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-314

### Title

Unresolved External Import References

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An importer **MAY** retain an unresolved external relationship reference when no verified Relay Identity match is available, provided the reference remains explicitly represented as external or unresolved.

### Rationale

Import continuity should not depend on immediate identity resolution. Explicit unresolved status prevents the retained reference from being misrepresented as a verified Relay target.

### Source

- REM-05-497
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-315

### Title

Later Upgrade of Imported External References

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An importer **MAY** later link or upgrade an unresolved external relationship reference when a verified Relay Identity match becomes available.

### Rationale

A migration bridge can become more portable as identity resolution improves. The upgrade changes target resolution, not the historical fact that the relationship originated through import.

### Source

- REM-05-498
- `design-notes/05-relationship-model.md`, Section 44

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-316

### Title

Temporary External Relationship Targets

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship record **MAY** temporarily identify its Target using an external identifier when no verified Relay Target is available.

### Rationale

Temporary external targets provide a compatibility bridge for imported or legacy relationship data while making clear that the reference has not yet achieved stable Relay identity resolution.

### Source

- REM-05-499
- `design-notes/05-relationship-model.md`, Section 45

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-317

### Title

External Target Reference Structure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A legacy external relationship Target **MUST** be explicitly typed as external, identify the external service or namespace in which the reference is meaningful, and preserve the external identifier used by that service.

### Rationale

Type, namespace and identifier together form the minimum source-defined structure needed to prevent an external reference from being confused with a Relay Identifier or resolved in the wrong external namespace.

### Source

- REM-05-500
- REM-05-501
- REM-05-502
- `design-notes/05-relationship-model.md`, Section 45

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-318

### Title

External Target Portability Limitation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Implementations **MUST** treat external relationship Targets as less portable and less reliably resolvable than stable Relay Targets.

### Rationale

External identifiers remain dependent on another service's namespace, availability and account lifecycle. They therefore cannot provide the same portability or independent resolution guarantees as stable Relay identifiers.

### Source

- REM-05-503
- `design-notes/05-relationship-model.md`, Section 45

### Related Invariants

- CI-03

---

## REL-REL-319

### Title

Verified Relay Identity Upgrade for External Targets

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

If an external account later verifies a Relay Identity, the relationship record **MAY** be updated or linked to reference that verified Relay Identity.

### Rationale

Verified identity linkage permits a transitional external reference to become a stable Relay-resolvable Target without requiring the imported relationship to remain permanently tied to the legacy service.

### Source

- REM-05-504
- `design-notes/05-relationship-model.md`, Section 45

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-320

### Title

Import Provenance Preservation Through Identity Upgrade

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Updating or linking an external relationship Target to a verified Relay Identity **MUST NOT** remove or obscure the relationship's original import provenance.

### Rationale

Improved target resolution does not rewrite the origin of the relationship data. Consumers must remain able to distinguish a relationship that originated through external import from one established natively through Relay.

### Source

- REM-05-505
- `design-notes/05-relationship-model.md`, Section 45

### Related Invariants

- CI-02
- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that form one source-defined provenance structure or one external-reference structure:

- `REM-05-490` through `REM-05-493` are consolidated into `REL-REL-310`. The general provenance requirement, import method, source service where known and import timestamp are the source-defined provenance structure for imported relationships and retain `MUST` strength.
- `REM-05-500` through `REM-05-502` are consolidated into `REL-REL-317`. Explicit external type, external service/namespace and external identifier are the three source-defined fields of one legacy external Target structure and retain `MUST` strength.

No other REM-05 entries in the covered range are consolidated. Import capability, verification boundary, verified matching, user confirmation, unresolved-reference retention, later upgrade, temporary external targeting, portability limitation, verified identity upgrade and provenance preservation remain independently meaningful and testable requirements.

All REM-05 requirements from `REM-05-489` through `REM-05-505` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 18 begins at `REM-05-489`, immediately after Part 17's final covered requirement `REM-05-488`.
- Coverage ends at `REM-05-505`, the end of source Section 45 and REM-05 Part 9.
- Section 46 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 44–45.

## Numbering verification

- First catalogue requirement: `REL-REL-309`.
- Final catalogue requirement: `REL-REL-320`.
- Catalogue numbering continues directly from Part 17's `REL-REL-308`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- External relationship import remains optional.
- Imported relationship provenance remains mandatory.
- Source service remains mandatory where known, preserving the extraction's condition.
- Imported usernames and external identifiers are not automatically elevated to verified Relay identities.
- Verified external-account matching, user confirmation, unresolved-reference retention and later upgrade remain optional workflows.
- Temporary external relationship Targets remain optional transitional references.
- External Target type, namespace and identifier remain mandatory structural fields.
- External Targets remain explicitly less portable than stable Relay Targets.
- Verified Relay Identity upgrade remains optional.
- Identity upgrade remains prohibited from removing or obscuring original import provenance.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part provides a controlled bridge from legacy platform relationships into Relay without pretending that imported identifiers already possess Relay-native verification or portability. Import provenance remains visible throughout the lifecycle; unresolved external references remain explicitly external; and later verified identity resolution improves portability without rewriting the historical origin of the relationship. The resulting model supports migration while preserving provenance and identity-verification boundaries.

The next catalogue part should begin with `REM-05-506` / source Section 46 and continue catalogue numbering from `REL-REL-321`.