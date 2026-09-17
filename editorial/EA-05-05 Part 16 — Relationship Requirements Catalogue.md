# EA-05-05 — Relationship Requirements Catalogue

## Part 16 — Relationship Privacy and Discovery

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing privacy risks in portable relationship graphs and the mechanisms through which applications may discover relationship records without changing canonical ownership.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-281`, following Part 15's coverage of trust relationships, endorsements and reputation as a derived layer. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 39–40 and REM-05 requirements `REM-05-439` through `REM-05-457`.

It defines normative requirements governing:

- treatment of portable relationship graphs as privacy-sensitive datasets;
- sensitive association and attribute inference risks;
- non-public relationship defaults;
- encryption support for private relationships;
- visibility enforcement by relationship indexes;
- application data minimisation;
- preservation of access classifications during export;
- protection against private-group membership inference;
- the limits of decentralisation as a privacy property;
- relationship discovery through repositories, indexes, reciprocal records, events and public graph services;
- repository obligations concerning reverse lookup;
- reverse discovery through separate indexers; and
- preservation of canonical ownership regardless of discovery path.

Section 41 reverse relationships and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-281

### Title

Portable Relationship Graph Privacy Sensitivity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relay implementations **MUST** treat portable relationship graphs as potentially sensitive datasets requiring explicit privacy protections, including protection against disclosure or inference of sensitive personal associations and attributes.

### Rationale

Portability increases user control but also enables aggregation and correlation across contexts. Relationship data may reveal sensitive information even where the endpoint records themselves do not directly disclose it.

### Source

- REM-05-439
- REM-05-440
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-282

### Title

No Universal Public Relationship Default

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay implementations **MUST NOT** apply public visibility as the universal default for all relationship records.

### Rationale

Relationship sensitivity varies by type, context and participant intent. A universal public default would expose associations that the source model expressly treats as potentially sensitive.

### Source

- REM-05-441
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10

---

## REL-REL-283

### Title

Private Relationship Encryption Support

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Private relationship records **SHOULD** support encryption appropriate to their confidentiality requirements while preserving authorised resolution and lifecycle management.

### Rationale

Private graph data can reveal sensitive associations and therefore benefits from confidentiality protection beyond access metadata alone.

### Source

- REM-05-442
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10

---

## REL-REL-284

### Title

Relationship Index Visibility Enforcement

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Relationship indexes **SHOULD** preserve and enforce the visibility and access classifications of the relationship records they observe.

### Rationale

Indexing provides a discovery or derived-view function; it does not create authority to broaden the audience of indexed relationship data.

### Source

- REM-05-443
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-285

### Title

Relationship Access Data Minimisation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Applications **SHOULD** request the narrowest relationship access required for their declared functionality.

### Rationale

A portable graph can expose broad social and contextual information. Least-access requests reduce unnecessary disclosure and limit aggregation risk.

### Source

- REM-05-444
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-286

### Title

Relationship Export Access-Classification Preservation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An export containing relationship records **MUST** preserve each record's visibility and access-classification metadata.

### Rationale

Portability must not silently convert restricted or private graph data into public data. Access semantics remain relevant when records move between compatible systems.

### Source

- REM-05-445
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-287

### Title

Private Group Membership Inference Protection

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Implementations **SHOULD** prevent private group membership from being inferred through exposed counts, metadata, identifiers, event patterns or related graph information.

### Rationale

Private membership can be disclosed indirectly even when member identities are never explicitly listed. Counts and metadata therefore require the same inference-risk analysis as direct relationship records.

### Source

- REM-05-446
- REM-05-447
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-288

### Title

No Privacy Assumption From Decentralisation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay privacy design **MUST NOT** assume that decentralisation or portability alone protects relationship data from surveillance, aggregation or inference.

### Rationale

A decentralised graph can become more invasive than a centralised one when privacy protections are weak. Privacy therefore requires explicit controls across records, indexes, applications, exports and event mechanisms.

### Source

- REM-05-448
- `design-notes/05-relationship-model.md`, Section 39

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-289

### Title

Relationship Discovery Paths

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** discover relationship information, subject to applicable visibility, permission and authorisation rules, through source repositories, authorised relationship indexes, reciprocal records, authorised event subscriptions and public graph services.

### Rationale

Section 40 defines multiple legitimate discovery paths for a distributed relationship graph. These mechanisms provide different access or synchronisation routes without changing the authority of the underlying declarations.

### Source

- REM-05-449
- REM-05-450
- REM-05-451
- REM-05-452
- REM-05-453
- `design-notes/05-relationship-model.md`, Section 40

### Related Invariants

- CI-02
- CI-10
- CI-12

---

## REL-REL-290

### Title

No Repository Requirement for Global Reverse Lookup

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Repository **MUST NOT** be considered non-compliant merely because it does not provide a global reverse-relationship lookup service or enumerate every external identity whose separately controlled repository contains a relationship directed at one of its identities.

### Rationale

Canonical relationship declarations are distributed across source repositories. Requiring a target repository to maintain ecosystem-wide reverse indexes would collapse the distinction between canonical storage and derived graph services.

### Source

- REM-05-454
- REM-05-455
- `design-notes/05-relationship-model.md`, Section 40

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-291

### Title

Separate Reverse-Discovery Indexers

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A separate indexer **MAY** provide global or reverse relationship-discovery services that individual repositories are not required to provide.

### Rationale

Reverse discovery is a derived ecosystem capability rather than an obligation of every canonical repository. Separating the roles allows specialised indexes without transferring ownership of relationship records.

### Source

- REM-05-456
- `design-notes/05-relationship-model.md`, Section 40

### Related Invariants

- CI-02
- CI-03
- CI-10

---

## REL-REL-292

### Title

Discovery Does Not Alter Canonical Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The mechanism through which an application discovers a relationship **MUST NOT** alter which repository or identity is the canonical source of the underlying relationship declaration.

### Rationale

Repositories, indexes, reciprocal references, event subscriptions and graph services are access or derived-view mechanisms. Discovery through them cannot transfer authorship or canonical authority away from the Source identity's declaration.

### Source

- REM-05-457
- `design-notes/05-relationship-model.md`, Section 40

### Related Invariants

- CI-02
- CI-03

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined privacy risk or one coherent option set:

- `REM-05-439` and `REM-05-440` are consolidated into `REL-REL-281`. The general requirement to treat portable graphs as privacy-sensitive and the requirement to account for sensitive-association inference express the same source-defined privacy-risk premise and share `MUST` strength.
- `REM-05-446` and `REM-05-447` are consolidated into `REL-REL-287`. Counts and metadata are the two source-defined indirect channels through which private group membership should not leak and share `SHOULD` strength.
- `REM-05-449` through `REM-05-453` are consolidated into `REL-REL-289`. Source repositories, authorised relationship indexes, reciprocal records, event subscriptions and public graph services are the five source-defined optional relationship-discovery paths and share `MAY` strength.
- `REM-05-454` and `REM-05-455` are consolidated into `REL-REL-290`. The general absence of a global reverse-lookup obligation and the follower-enumeration example express the same repository-scope boundary and share the verified extraction's `MUST NOT` treatment.

No other REM-05 entries in the covered range are consolidated. Public-default prohibition, encryption support, index visibility enforcement, access minimisation, export classification preservation, decentralisation/privacy separation, separate-indexer capability and canonical-ownership preservation remain independently meaningful and testable requirements.

All REM-05 requirements from `REM-05-439` through `REM-05-457` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 16 begins at `REM-05-439`, immediately after Part 15's final covered requirement `REM-05-438`.
- Coverage ends at `REM-05-457`, the end of source Section 40 and REM-05 Part 8.
- Section 41 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 39–40.

## Numbering verification

- First catalogue requirement: `REL-REL-281`.
- Final catalogue requirement: `REL-REL-292`.
- Catalogue numbering continues directly from Part 15's `REL-REL-280`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Portable graph privacy sensitivity remains mandatory.
- Universal public visibility remains prohibited.
- Encryption, index visibility enforcement and application data minimisation retain `SHOULD` strength.
- Export access-classification preservation remains mandatory.
- Private-group inference protection retains `SHOULD` strength.
- Decentralisation is not treated as an inherent privacy guarantee.
- All five source discovery paths remain optional.
- Repositories are not required to provide ecosystem-wide reverse lookup or follower enumeration.
- Separate indexers remain optional providers of reverse discovery.
- Discovery mechanisms cannot change canonical ownership.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves the central tension of a portable relationship graph: portability increases user control while also increasing the possibility of aggregation, correlation and inference. Privacy therefore remains an explicit protocol concern rather than an assumed consequence of decentralisation. At the same time, relationship discovery is deliberately plural: repositories, indexes, reciprocal references, events and graph services can expose authorised views, but none of those discovery mechanisms acquires canonical ownership merely by making a relationship easier to find.

The next catalogue part should begin with `REM-05-458` / source Section 41 and continue catalogue numbering from `REL-REL-293`.