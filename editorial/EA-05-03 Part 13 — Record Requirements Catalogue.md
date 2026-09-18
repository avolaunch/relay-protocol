# EA-05-03 — Record Requirements Catalogue

## Part 13 — Usage-Rights Expression and Enforcement Boundaries

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the separation between record visibility and usage rights, the limits of rights implied by public visibility, structured usage-rights expression and the boundary between protocol expression and external enforcement.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 16 and REM-03 requirements `REM-03-166` through `REM-03-184`.

It defines normative requirements governing:

- separation of record visibility from usage rights;
- limitations on rights implied by public visibility;
- optional structured rights declarations;
- protocol capability to represent structured usage-rights terms;
- the absence of guaranteed external compliance; and
- permitted external enforcement dependencies.

Source Section 17 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-167` through `REM-03-171` are consolidated because the source applies one public-visibility qualification to five usage categories. `REM-03-180` through `REM-03-184` are consolidated because the source permits reliance on five external enforcement mechanisms. Every limitation and enforcement dependency remains explicit and individually traceable.

`REM-03-173` through `REM-03-177` are explicit Non-normative model examples. They illustrate possible rights terms but do not establish final rights fields, term names, vocabulary values or enforceability rules and therefore generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-089

### Title

Visibility and Usage-Rights Separation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** represent record visibility separately from record usage rights.

### Rationale

Permission to view a record does not itself establish permission to reproduce, modify, commercially exploit, syndicate or use that record for model training.

### Source

- REM-03-166
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-090

### Title

Public Visibility Does Not Grant Unlimited Usage Rights

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Public visibility **MUST NOT** be interpreted as an unlimited grant to:

- reproduce the record;
- commercially exploit the record;
- use the record for model training;
- modify the record or create derivatives; or
- syndicate or redistribute the record.

### Rationale

Public readability determines access, not the separate terms governing downstream use of the record.

### Source

- REM-03-167
- REM-03-168
- REM-03-169
- REM-03-170
- REM-03-171
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- AI-07

---

## REL-REC-091

### Title

Structured Rights Declaration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** include a structured rights declaration.

### Rationale

A structured declaration allows usage terms to accompany a record without requiring every record to contain one or fixing a final rights vocabulary in this section.

### Source

- REM-03-172
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-092

### Title

Protocol Usage-Rights Expression Capability

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Protocol **MUST** be capable of representing structured usage-rights terms associated with a record.

### Rationale

Protocol-level expression enables interoperable communication of usage terms while remaining distinct from enforcement or guaranteed compliance.

### Source

- REM-03-178
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-093

### Title

No Guarantee of External Rights Compliance

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay Protocol **MUST NOT** represent structured usage-rights terms as a guarantee that every external observer will obey them.

### Rationale

The protocol can express usage terms, but metadata alone cannot ensure the behaviour of every observer after information has been disclosed.

### Source

- REM-03-179
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08

---

## REL-REC-094

### Title

External Usage-Rights Enforcement Dependencies

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Enforcement of declared usage rights **MAY** depend on:

- contractual mechanisms outside the Relay Protocol;
- application policies;
- technical controls;
- licensing systems; or
- applicable law.

### Rationale

Usage-rights enforcement may rely on mechanisms beyond protocol expression without requiring every declaration to use every mechanism or selecting how any mechanism operates.

### Source

- REM-03-180
- REM-03-181
- REM-03-182
- REM-03-183
- REM-03-184
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-166` | Direct | `REL-REC-089` |
| `REM-03-167` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-168` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-169` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-170` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-171` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-172` | Direct | `REL-REC-091` |
| `REM-03-173` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative view term |
| `REM-03-174` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative redistribution term |
| `REM-03-175` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative commercial-use term |
| `REM-03-176` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative model-training term |
| `REM-03-177` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative derivative-work term |
| `REM-03-178` | Direct | `REL-REC-092` |
| `REM-03-179` | Direct | `REL-REC-093` |
| `REM-03-180` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-181` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-182` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-183` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-184` | Consolidated external enforcement dependency | `REL-REC-094` |

Every normative REM entry in scope maps to one catalogue requirement. `REM-03-173` through `REM-03-177` remain explicitly accounted for but generate no normative requirements because their source material is illustrative example JSON.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 16 of `design-notes/03-record-model.md`.
- Source Sections 17–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-166` through `REM-03-184`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-088`.
- First identifier in this part: `REL-REC-089`.
- Final identifier in this part: `REL-REC-094`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–13.

## Traceability verification

- Every normative REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-167` through `REM-03-171` retain individual traceability through the Source list and coverage table for `REL-REC-090`.
- `REM-03-180` through `REM-03-184` retain individual traceability through the Source list and coverage table for `REL-REC-094`.
- `REM-03-173` through `REM-03-177` remain explicitly accounted for as non-normative exclusions.

## Visibility and usage-rights verification

- Record visibility remains separate from record usage rights.
- Public visibility does not imply unlimited reproduction, commercial-exploitation, model-training, modification, derivative-work, syndication or redistribution rights.
- All five public-visibility limitations remain explicit and independently traceable.

## Rights-expression verification

- Record inclusion of a structured rights declaration retains the source-level `MAY` strength.
- Protocol capability to represent structured usage-rights terms retains the source-level `MUST` strength.
- The record-level permission and protocol-level capability remain separate requirements.
- Rights expression is not treated as enforcement or guaranteed compliance.

## External-enforcement verification

- The protocol does not represent rights terms as a guarantee of external-observer compliance.
- Contracts, application policies, technical controls, licensing systems and applicable law remain explicit optional enforcement dependencies.
- No declaration is required to use every enforcement dependency.
- No contractual term, application policy, technical control, licensing system, legal remedy or jurisdictional rule is selected or invented.

## Non-normative and illustrative-example verification

- `REM-03-173` through `REM-03-177` generate no normative catalogue requirements.
- The Section 16 JSON generates no normative catalogue requirements.
- `rights`, `view`, `redistribution`, `commercialUse`, `modelTraining` and `derivatives` are not made mandatory physical field names.
- `public`, `attribution-required`, `prohibited` and `permission-required` are not treated as final or mandatory vocabulary values.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No rights vocabulary, enforcement mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 13 defines visibility and usage-rights separation, public-visibility limitations, structured rights expression and external-enforcement boundaries. It generates `REL-REC-089` through `REL-REC-094` from normative material in `REM-03-166` through `REM-03-184`, while explicitly excluding five non-normative example entries.

The next catalogue part should begin with source Section 17 and `REM-03-185`.
