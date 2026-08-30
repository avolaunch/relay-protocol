# EA-05-02 — Repository Requirements Catalogue
## Part 2 — Records, Record URIs, Collections & Record Keys

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Repository Records, Record URIs, Collections and Record Keys.

It establishes how Repository content is identified, organised and addressed independently of providers and applications while preserving stable protocol identity.

---

# 2. Scope

This part defines normative requirements governing:

- Repository Records
- Record metadata
- Record URIs
- Collections
- Collection ownership
- Core and external collections
- Record Keys

---

# 3. Requirements

## REL-REP-024

### Title
Repository Record

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** represent the smallest independently addressable structured protocol object within a Relay Repository.

### Rationale
Defines the fundamental protocol unit of repository content.

### Source
REM-02 — RREM-0031

### Related Invariants
- CI-08

---

## REL-REP-025

### Title
Repository Record Metadata

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** contain sufficient metadata to identify its type, logical identity, authorising identity, creation time, version and governing schema.

### Rationale
Supports interoperability and independent verification.

### Source
REM-02 — RREM-0032 to RREM-0037

### Related Invariants
- CI-08

---

## REL-REP-026

### Title
Repository Record Content

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** contain its structured content together with the protocol-defined integrity information and, where required, a valid signature.

### Rationale
Ensures complete, verifiable repository records.

### Source
REM-02 — RREM-0038 to RREM-0040

### Related Invariants
- CI-08

---

## REL-REP-027

### Title
Record URI

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** possess a stable protocol-level Record URI.

### Rationale
Provides permanent logical addressing.

### Source
REM-02 — RREM-0041

### Related Invariants
- CI-05

---

## REL-REP-028

### Title
Record URI Stability

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
A Record URI **MUST NOT** change because of provider migration, application changes, Handle changes or Record revisions.

### Rationale
Logical identity is independent of operational change.

### Source
REM-02 — RREM-0042 to RREM-0045

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-029

### Title
Logical Record Identity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
A Record URI **MUST** identify the logical Record rather than an individual historical version.

### Rationale
Separates identity from version history.

### Source
REM-02 — RREM-0046, RREM-0047

### Related Invariants
- CI-08

---

## REL-REP-030

### Title
Collections

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Repository Records **MUST** be organised into Collections according to protocol-defined schema families.

### Rationale
Provides consistent repository organisation.

### Source
REM-02 — RREM-0048 to RREM-0050

### Related Invariants
- CI-08

---

## REL-REP-031

### Title
Collection Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Schema publishers **MUST NOT** acquire ownership of Repository Records solely because those Records use schemas published by them.

### Rationale
Schema publication and record ownership are independent.

### Source
REM-02 — RREM-0051, RREM-0052

### Related Invariants
- CI-01

---

## REL-REP-032

### Title
Collection Extensibility

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
Relay **MAY** define core Collections, and third parties **MAY** define additional protocol-compatible Collections.

### Rationale
Supports ecosystem extensibility.

### Source
REM-02 — RREM-0053 to RREM-0056

### Related Invariants
- CI-03

---

## REL-REP-033

### Title
Record Key

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** possess a unique, stable Record Key within its Collection.

### Rationale
Provides stable logical identity within collections.

### Source
REM-02 — RREM-0057, RREM-0058

### Related Invariants
- CI-05

---

## REL-REP-034

### Title
Non-semantic Record Keys

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
Record Keys **SHOULD** be non-semantic and **MUST** remain independent of titles, filenames and presentation labels.

### Rationale
Avoids semantic coupling and preserves identifier stability.

### Source
REM-02 — RREM-0059, RREM-0060

### Related Invariants
- CI-05

---

# Editorial Review Notes

This part establishes the Repository addressing model. Repository Records, Record URIs, Collections and Record Keys together provide stable, provider-independent identification and organisation of repository content. These requirements separate logical identity from presentation, schema ownership and implementation details, ensuring that repository content remains portable and interoperable across compliant implementations.
