# REM-05R-02 — Relationship Requirement Extraction Remediation Verification

## Document status

**Canonical post-remediation verification review**

This document verifies the targeted remediation performed after `REM-05R-01 — Relationship Requirement Extraction Review.md`.

Authoritative source:

- `design-notes/05-relationship-model.md`

Remediated files reviewed:

- `rem/REM-05 Part 6 — Relationship Requirement Extraction Matrix (Sections 26–30).md`
- `rem/REM-05 Part 10 — Relationship Requirement Extraction Matrix (Sections 46–50).md`
- `rem/REM-05 Part 12 — Relationship Requirement Extraction Matrix (Sections 56–60).md`

The purpose of this review is verification, not redesign. It does not reopen accepted extraction choices from REM-05R-01 and does not resolve open design questions on behalf of the source model.

---

# 1. Verification objectives

This review verifies that:

1. every finding `REM-05R-F01` through `REM-05R-F09` has been correctly remediated;
2. remediation has not introduced a new extraction defect in the affected areas;
3. unaffected requirements in the remediated files retain their prior substance;
4. requirement identifiers remain continuous and unique from `REM-05-001` through `REM-05-673`;
5. non-normative entries are clearly excluded from ordinary normative catalogue treatment;
6. Section 58 remains unresolved;
7. Section 59 remains explicitly provisional;
8. all remediated entries remain traceable to `design-notes/05-relationship-model.md`.

---

# 2. Verification summary

| Finding | Affected entries | Verification result |
|---|---|---|
| REM-05R-F01 | REM-05-291–295 | Resolved |
| REM-05R-F02 | REM-05-506 | Resolved |
| REM-05R-F03 | REM-05-508 | Resolved |
| REM-05R-F04 | REM-05-509 | Resolved |
| REM-05R-F05 | REM-05-515–516 | Resolved |
| REM-05R-F06 | REM-05-636–645 | Resolved |
| REM-05R-F07 | REM-05-646–671 | Resolved |
| REM-05R-F08 | REM-05-627–633 principally; Section 57 generally | Resolved |
| REM-05R-F09 | REM-05-673 | Resolved |

**Result:** all nine findings identified by REM-05R-01 are resolved.

No new blocking extraction defect was identified during this verification pass.

---

# 3. Finding-by-finding verification

## REM-05R-F01 — Formal-group examples

**Original defect**  
Section 27 examples were promoted into five `SHOULD` support requirements.

**Remediation verified**  
`REM-05-291` through `REM-05-295` are now explicitly labelled **Non-normative model example** entries. Their classifications are non-normative and their Notes state that they preserve source traceability without imposing support obligations.

**Source trace**  
Section 27 continues to identify organisation, association, project team, community and cooperative only as examples.

**Verification result**  
**Resolved.** The examples remain visible without acquiring normative force.

---

## REM-05R-F02 — Descriptive duplicate possibility

**Original defect**  
The descriptive statement that multiple applications may attempt to create equivalent records was promoted to a mandatory repository obligation.

**Remediation verified**  
`REM-05-506` now preserves the source as a `MAY` possibility and explicitly classifies it as descriptive duplicate-handling context. Its Notes state that it does not independently impose a mandatory repository obligation.

The operative repository guidance remains separately captured by `REM-05-507`.

**Verification result**  
**Resolved.** No independent `MUST anticipate` obligation remains.

---

## REM-05R-F03 — Duplicate-prevention decomposition

**Original defect**  
A qualification inside a `SHOULD` source sentence was strengthened into a separate `MUST`.

**Remediation verified**  
`REM-05-508` now uses `SHOULD` and explicitly records that this preserves the normative strength of the parent duplicate-prevention sentence.

**Verification result**  
**Resolved.** Decomposition no longer increases normative strength.

---

## REM-05R-F04 — Client-specific duplicate follows

**Original defect**  
Source wording `should not need` was promoted to `MUST NOT be required`.

**Remediation verified**  
`REM-05-509` now states that a user `SHOULD NOT` be required to create a separate active relationship record solely because another compatible application is used.

**Verification result**  
**Resolved.** Source strength is preserved.

---

## REM-05R-F05 — Relationship coexistence

**Original defect**  
The source permission that different relationship types or contexts `may coexist` was converted into mandatory coexistence rules.

**Remediation verified**  
`REM-05-515` and `REM-05-516` now use `MAY` and preserve schema qualification. Their Notes explicitly distinguish permitted coexistence from an unconditional mandatory coexistence rule.

**Verification result**  
**Resolved.** The extraction now preserves both permissive strength and schema-defined uniqueness.

---

## REM-05R-F06 — Open design questions

**Original defect**  
The ten unresolved Section 58 questions were converted into settled `MUST define` requirements.

**Remediation verified**  
`REM-05-636` through `REM-05-645` are now explicitly labelled **Non-normative Open Design Issue** entries.

The section introduction states that these are not settled protocol requirements and must not be carried into a Requirements Catalogue as normative requirements unless resolved by an authoritative design decision.

The individual entries preserve the questions rather than selecting answers. Candidate mechanisms remain candidates; no indexing architecture, reciprocal activation mechanism, encryption model, request transport, authority boundary, recovery behaviour, historical-mutuality rule, identity-matching threshold or schema-conflict rule has been silently chosen.

**Verification result**  
**Resolved.** Section 58 remains genuinely unresolved and is correctly excluded from ordinary normative catalogue treatment.

---

## REM-05R-F07 — Provisional v0.1 assumptions

**Original defect**  
Section 59 classifications said provisional while requirement wording often read as unconditional final normative requirements.

**Remediation verified**  
`REM-05-646` through `REM-05-671` now carry **PROVISIONAL v0.1** directly in the requirement text and `Provisional v0.1 decision` in the classification.

The section introduction states that the entries describe the current working baseline and must not be treated as final, immutable protocol commitments without later confirmation.

Where the source itself contains permissive wording, such as deferral of advanced end-to-end encrypted graph privacy, that permission remains visible.

**Verification result**  
**Resolved.** Provisional status is no longer merely metadata; it is explicit in the extracted decision text and must be preserved downstream.

---

## REM-05R-F08 — Compliance-scenario normative strength

**Original defect**  
Several Section 57 scenario steps used `MUST` even though the scenario is introduced as a test a basic implementation `should` pass.

**Remediation verified**  
Section 57 now explicitly establishes that scenario-specific entries retain `SHOULD` strength. `REM-05-617` through `REM-05-635`, including the principally affected `REM-05-627` through `REM-05-633`, use `SHOULD` or `SHOULD NOT` for scenario expectations.

Where the same principle is mandatory elsewhere, Notes cross-reference the independently mandatory invariant rather than deriving `MUST` strength from the compliance narrative. This is particularly clear for application ownership and rewriting another participant’s record.

**Verification result**  
**Resolved.** The compliance scenario now preserves its own normative level without weakening independently mandatory source requirements elsewhere.

---

## REM-05R-F09 — Migration and Portability Model hand-off

**Original defect**  
The Section 60 editorial transition to the next model was promoted into a normative Relationship Model requirement.

**Remediation verified**  
`REM-05-673` is now explicitly a **Non-normative model-boundary note**. Its Notes state that it is not a normative Relationship Model requirement, must not enter the Relationship Requirements Catalogue as such, and that Migration and Portability requirements must be extracted from that model’s own authoritative source.

**Verification result**  
**Resolved.** The model boundary is preserved without losing traceability.

---

# 4. Unaffected-requirement preservation

The remediation was targeted rather than a broad rewrite.

Within Part 6, the substantive normative change is confined to the status and wording of `REM-05-291` through `REM-05-295`; surrounding personal-group, membership, request and acceptance requirements retain their established substance and identifiers.

Within Part 10, the changes are confined to the findings affecting `REM-05-506`, `REM-05-508`, `REM-05-509`, `REM-05-515` and `REM-05-516`, together with editorial QA wording reflecting those corrections. The remaining Section 46–50 extraction retains its established substance and identifiers.

Within Part 12, remediation changes the editorial status or normative treatment required by REM-05R-01 for the Section 57 compliance scenario, Section 58 open questions, Section 59 provisional decisions and `REM-05-673`. Section 56 invariants remain mandatory, and `REM-05-672` remains the extracted core relationship principle.

No evidence was identified that the remediation altered an unrelated protocol concept or answered a question the source leaves open.

---

# 5. Numbering and continuity verification

The remediation retained identifiers rather than deleting and renumbering non-normative traceability entries.

The part boundaries therefore remain:

| Part | Requirement range |
|---|---:|
| Part 1 | REM-05-001–053 |
| Part 2 | REM-05-054–096 |
| Part 3 | REM-05-097–151 |
| Part 4 | REM-05-152–209 |
| Part 5 | REM-05-210–278 |
| Part 6 | REM-05-279–342 |
| Part 7 | REM-05-343–399 |
| Part 8 | REM-05-400–457 |
| Part 9 | REM-05-458–505 |
| Part 10 | REM-05-506–542 |
| Part 11 | REM-05-543–600 |
| Part 12 | REM-05-601–673 |

The full identifier sequence remains continuous from `REM-05-001` through `REM-05-673`.

No identifier was removed, duplicated or reassigned by the remediation. The retained identifiers for non-normative examples, open issues and the model-boundary note are traceability identifiers; their presence in the sequence does not make them normative requirements.

---

# 6. Catalogue-treatment verification

The remediated extraction now contains three statuses that must be distinguished during catalogue generation:

### Normative extracted requirements

Ordinary normative requirements continue to carry their source-derived `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT` or `MAY` semantics.

### Explicitly non-normative entries

The following must be excluded from ordinary normative catalogue requirements:

- `REM-05-291` through `REM-05-295` — non-normative formal-group examples;
- `REM-05-636` through `REM-05-645` — non-normative Open Design Issues;
- `REM-05-673` — non-normative model-boundary note.

They may be retained in catalogue-adjacent traceability or editorial registers, but must not be silently converted back into conformance obligations.

### Provisional v0.1 decisions

`REM-05-646` through `REM-05-671` are part of the current v0.1 working baseline but remain explicitly provisional. If carried into catalogue work, their provisional status must be preserved visibly in catalogue metadata and wording rather than flattened into ordinary final requirements.

---

# 7. Traceability verification

The remediated entries remain traceable to the authoritative source:

- Part 6 corrections map directly to Section 27’s formal-group examples and surrounding formal-group semantics.
- Part 10 corrections map directly to Sections 46 and 47, including the distinction between descriptive possibility, `SHOULD` duplicate prevention, `SHOULD NOT` client duplication and `MAY` coexistence.
- Part 12 corrections map directly to Section 57’s overall `SHOULD` compliance test, Section 58’s explicit open-question status, Section 59’s “will provisionally assume” qualification and Section 60’s transition to the next core model.

No remediation entry relies on a different design note to manufacture stronger authority than the Relationship Model supplies.

---

# 8. Editorial QA

Final QA confirms:

- all nine REM-05R-01 findings have a verified disposition;
- no unresolved finding remains hidden behind classification wording;
- no new blocking extraction defect was identified in the remediated areas;
- unaffected requirement identifiers and substantive concepts remain stable;
- the sequence remains continuous and unique through `REM-05-673`;
- non-normative examples and open issues are explicitly distinguishable from conformance requirements;
- Section 58 remains unresolved;
- Section 59 remains explicitly provisional;
- Section 60's model hand-off remains non-normative;
- the authoritative source remains `design-notes/05-relationship-model.md`;
- this verification does not begin Requirements Catalogue generation.

---

# 9. Final verdict

**VERIFIED — REM-05 is ready to proceed to Requirements Catalogue generation.**

All findings `REM-05R-F01` through `REM-05R-F09` are resolved by the targeted remediation. The resulting extraction remains continuous from `REM-05-001` through `REM-05-673`, preserves source traceability and normative strength in the reviewed areas, keeps Section 58 unresolved, keeps Section 59 provisional, and clearly excludes non-normative traceability entries from ordinary normative catalogue treatment.

Catalogue generation may therefore proceed, provided it preserves the status distinctions recorded in this verification review.