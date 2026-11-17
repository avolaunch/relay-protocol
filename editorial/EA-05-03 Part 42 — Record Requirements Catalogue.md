# EA-05-03 — Record Requirements Catalogue

## Part 42 — Compliance scenario

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 45, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 45 and REM-03 entries `REM-03-438` through `REM-03-455`.

Source Section 46 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-277

### Title

Basic compliance-scenario expectation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A basic Relay Record implementation **SHOULD** pass the complete compliance scenario defined in Section 45.

### Rationale

The source uses “should”, so the scenario is an expected baseline test rather than language redefining every conformance tier.

### Source

- REM-03-438
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- AI-10

---

## REL-REC-278

### Title

Initial public-record creation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** allow an authorised application to create a public record that becomes version 1 when accepted by the repository.

### Rationale

The example Record URI is illustrative rather than mandatory syntax beyond the source model’s provisional URI design.

### Source

- REM-03-439
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-279

### Title

Cross-application record reading and updating

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** allow another authorised application to read and update the same logical record.

### Rationale

The second application does not acquire ownership by performing the update.

### Source

- REM-03-440
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-280

### Title

Acceptance of the second version

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A valid cross-application update **SHOULD** be accepted as a new Record Version rather than replacing version 1 without history.

### Rationale

The new version remains part of the same logical record.

### Source

- REM-03-441
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-10

---

## REL-REC-281

### Title

URI continuity across applications and versions

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The Record URI **SHOULD** remain unchanged when another application creates a new accepted version of the record.

### Rationale

This scenario tests the general URI-stability invariant.

### Source

- REM-03-442
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05

---

## REL-REC-282

### Title

Stale-update detection

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** detect an update based on a stale expected version when a newer current version already exists.

### Rationale

The example tests optimistic concurrency behaviour.

### Source

- REM-03-443
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-07

---

## REL-REC-283

### Title

Stale-update rejection or conflict marking

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The repository **SHOULD** reject a stale update or explicitly mark and preserve it as a conflict requiring resolution.

### Rationale

The source allows either rejection or explicit conflict treatment.

### Source

- REM-03-444
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-284

### Title

No silent overwrite of current version

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

The repository **SHOULD NOT** silently overwrite the current version with an update based on stale state.

### Rationale

This retains the Section 45 scenario’s governing SHOULD framing. Independently sourced mandatory concurrency requirements remain elsewhere in the extraction.

### Source

- REM-03-445
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-07

---

## REL-REC-285

### Title

Reply stored in replying identity’s repository

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** support creation of a reply in the replying identity’s repository while referencing the original record in another repository.

### Rationale

The reply is a separate canonical record rather than content inserted into the original author’s record.

### Source

- REM-03-446
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-286

### Title

Cross-application display of reply

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An application displaying the original record **SHOULD** be able to resolve and display an accessible reply stored in another identity’s repository.

### Rationale

Display does not transfer canonical control of the reply.

### Source

- REM-03-447
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-287

### Title

Reply-controller continuity

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** remain the controller of the reply record even when another identity’s application displays it.

### Rationale

This tests the acting-identity ownership invariant.

### Source

- REM-03-448
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02

---

## REL-REC-288

### Title

Visibility change creates a version

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An authorised change from public to restricted visibility **SHOULD** create a new accepted Record Version recording that change.

### Rationale

The primary content may remain unchanged while the metadata change creates a new version.

### Source

- REM-03-449
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06
- AI-07

---

## REL-REC-289

### Title

Refusal of future unauthorised access

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

After a valid visibility restriction, the repository **SHOULD** refuse future access attempts that do not satisfy the applicable authority or audience rule.

### Rationale

The requirement concerns future authorised service and cannot revoke copies already obtained.

### Source

- REM-03-450
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-290

### Title

Policy-governed removal of active content

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

When the controller deletes the record, the implementation **SHOULD** remove or withhold its active content in accordance with the applicable deletion policy.

### Rationale

The exact retained verification metadata depends on the deletion mode and tombstone requirements.

### Source

- REM-03-451
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02

---

## REL-REC-291

### Title

Tombstone prevention of Record URI reuse

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Deletion **SHOULD** leave sufficient tombstone state to prevent reuse or reassignment of the deleted Record URI.

### Rationale

This applies even when the active content has been erased.

### Source

- REM-03-452
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-292

### Title

Tombstone preservation of minimum verification history

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The tombstone **SHOULD** preserve the minimum verification history required to demonstrate the prior existence and authorised deletion of the logical record.

### Rationale

The tombstone should not retain more deleted content than necessary.

### Source

- REM-03-453
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06
- CI-10
- CI-08

---

## REL-REC-293

### Title

Migration continuity for URI, versions and tombstone

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Repository migration **SHOULD** preserve the record’s Record URI, accepted versions and tombstone intact at the receiving provider.

### Rationale

This scenario tests portability after both versioning and deletion history have occurred.

### Source

- REM-03-454
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05
- CI-03
- AI-04
- CI-10

---

## REL-REC-294

### Title

Basic Relay Record objective

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An implementation **SHOULD** be considered to satisfy the basic Relay Record objective when it completes the Section 45 operations without conflating application ownership, logical record identity, historical versions or visibility state.

### Rationale

The scenario evaluates both functional operations and preservation of the Record Model’s core conceptual boundaries.

### Source

- REM-03-455
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-10
- AI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-438` | Direct | `REL-REC-277` |
| `REM-03-439` | Direct | `REL-REC-278` |
| `REM-03-440` | Direct | `REL-REC-279` |
| `REM-03-441` | Direct | `REL-REC-280` |
| `REM-03-442` | Direct | `REL-REC-281` |
| `REM-03-443` | Direct | `REL-REC-282` |
| `REM-03-444` | Direct | `REL-REC-283` |
| `REM-03-445` | Direct | `REL-REC-284` |
| `REM-03-446` | Direct | `REL-REC-285` |
| `REM-03-447` | Direct | `REL-REC-286` |
| `REM-03-448` | Direct | `REL-REC-287` |
| `REM-03-449` | Direct | `REL-REC-288` |
| `REM-03-450` | Direct | `REL-REC-289` |
| `REM-03-451` | Direct | `REL-REC-290` |
| `REM-03-452` | Direct | `REL-REC-291` |
| `REM-03-453` | Direct | `REL-REC-292` |
| `REM-03-454` | Direct | `REL-REC-293` |
| `REM-03-455` | Direct | `REL-REC-294` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 45 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-438` through `REM-03-455`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-276`.
- First identifier in this part: `REL-REC-277`.
- Final identifier in this part: `REL-REC-294`.
- Total catalogue requirements in this part: 18.
- Catalogue identifiers remain continuous and unique across Parts 1–42.

## Traceability verification

- Every settled normative rule in scope maps directly or through justified decomposition to a catalogue requirement.
- Every generated requirement cites its in-scope REM identifier and authoritative design-note section.
- Every excluded entry remains individually accounted for in the coverage table.

## Source-status and implementation-neutrality verification

- Normative strength and material qualifications are preserved.
- Illustrative examples and open design questions do not become protocol requirements.
- No example vocabulary, physical field, syntax, mechanism or implementation detail is made mandatory unless the source establishes that obligation.
- Extraction Notes are used as rationale only and do not broaden the authoritative source rule.

## Normative-language verification

- Each generated catalogue requirement carries one explicit normative keyword.
- No later-section requirement is imported.

---

# 6. Part conclusion

Part 42 catalogues the settled normative content of Record Model Section 45.

The next catalogue part should address Section 46.
