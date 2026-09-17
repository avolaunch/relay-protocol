# REM-03R-02 — Record Requirement Remediation Verification

## Document status

**Canonical post-remediation verification review**

**Authoritative source:** `design-notes/03-record-model.md`

**Original review:** `rem/REM-03R-01 — Record Requirement Extraction Review.md`

**Remediation commit reviewed:** `4c49dfd29e19311eb88fbffbe79fcb1b98e4a10f`

**Extraction reviewed:** REM-03 Parts 1–10

**Source coverage:** Sections 1–48

**Requirement range verified:** `REM-03-001` through `REM-03-483`

---

# 1. Purpose and review scope

This review verifies the REM-03 remediation performed in response to findings `REM-03R-F01` through `REM-03R-F08` before canonical Requirements Catalogue generation.

The Record Model is the sole authoritative source. The review independently checks the remediated extraction against that source rather than treating the remediation commit or its stated intent as evidence of correctness.

The review covers:

- the complete extraction across REM-03 Parts 1–10;
- every remediation finding recorded in REM-03R-01;
- every identifier converted to explicit non-normative status;
- the source-level strength of the Section 45 compliance scenario;
- the unresolved status of the Section 46 open design questions;
- the overriding **PROVISIONAL v0.1** status of the Section 47 decisions;
- the Section 48 Core Record Principle and model-boundary hand-off;
- identifier continuity, uniqueness and part boundaries across the complete `REM-03-001`–`REM-03-483` sequence; and
- the remediation diff for unrelated source drift.

This document performs verification only. It does not generate EA-05-03 catalogue requirements and does not modify the extraction.

---

# 2. Files reviewed

## Authoritative source and prior review

- `design-notes/03-record-model.md`
- `rem/REM-03R-01 — Record Requirement Extraction Review.md`

## Remediated extraction

- `rem/REM-03 Part 1 — Record Requirement Extraction Matrix (Sections 1–5).md`
- `rem/REM-03 Part 2 — Record Requirement Extraction Matrix (Sections 6–10).md`
- `rem/REM-03 Part 3 — Record Requirement Extraction Matrix (Sections 11–15).md`
- `rem/REM-03 Part 4 — Record Requirement Extraction Matrix (Sections 16–20).md`
- `rem/REM-03 Part 5 — Record Requirement Extraction Matrix (Sections 21–25).md`
- `rem/REM-03 Part 6 — Record Requirement Extraction Matrix (Sections 26–30).md`
- `rem/REM-03 Part 7 — Record Requirement Extraction Matrix (Sections 31–35).md`
- `rem/REM-03 Part 8 — Record Requirement Extraction Matrix (Sections 36–40).md`
- `rem/REM-03 Part 9 — Record Requirement Extraction Matrix (Sections 41–45).md`
- `rem/REM-03 Part 10 — Record Requirement Extraction Matrix (Sections 46–48).md`

---

# 3. Verification method

The verification used five complementary checks.

1. **Source comparison.** Each finding and affected entry was checked directly against the cited passage in `design-notes/03-record-model.md`, including its wording, normative strength, qualifications and editorial status.
2. **Complete extraction review.** All ten extraction parts were reviewed in source-section order to confirm that the remediation remained consistent with surrounding substantive requirements and did not disturb unaffected coverage.
3. **Remediation-diff isolation.** Commit `4c49dfd29e19311eb88fbffbe79fcb1b98e4a10f` was compared with its parent. Exactly 83 REM entries changed: the 60 entries requiring non-normative treatment, `REM-03-007`, the five Section 45 scenario entries and the 17 Section 47 classification clarifications. No unexpected REM entry changed.
4. **Structural validation.** Every REM heading was enumerated, sorted and counted. Each entry was also checked for the required Source, Requirement, Classification and Notes fields.
5. **Boundary validation.** Section 46, Section 47 and Section 48 were separately checked to ensure that unresolved questions, provisional decisions, the governing principle and the next-model hand-off remain distinct.

---

# 4. Finding-by-finding disposition

| Finding | Affected identifiers | Verification result | Disposition |
|---|---|---|---|
| `REM-03R-F01` | `REM-03-005` | The illustrative Section 1 record-type list is now an explicit non-normative model example. It is not presented as a mandatory or closed capability set. | **Resolved** |
| `REM-03R-F02` | `REM-03-007` | The unsupported condition restricting creation, editing and display to repository-authorised operations has been removed. The source permission to create, edit or display remains, together with the prohibition on application ownership. Display is not characterised as a repository-authorised mutation. | **Resolved** |
| `REM-03R-F03` | `REM-03-025`, `REM-03-054` | The provisional serialisation and open version-reference syntax are explicit non-normative specification-status/open-design notes. Neither carries ordinary `MUST NOT` treatment, while both retain the warning that the examples are not final syntax. | **Resolved** |
| `REM-03R-F04` | 24 illustrative entries | Every cited entry is explicitly classified as a non-normative model example. The entries account for the examples without selecting final schema field names, mandatory vocabularies or required schema shapes. | **Resolved** |
| `REM-03R-F05` | 20 validation-example entries | Every detailed check beneath the five validation levels is explicitly classified as a non-normative validation example. The substantive validation-layer requirements remain normative and unchanged. | **Resolved** |
| `REM-03R-F06` | `REM-03-445`, `REM-03-448`, `REM-03-450`, `REM-03-452`, `REM-03-453` | The scenario entries now consistently retain Section 45’s governing `SHOULD` framing: the prohibition is `SHOULD NOT` and the four positive outcomes are `SHOULD`. | **Resolved** |
| `REM-03R-F07` | `REM-03-456`–`REM-03-465` | All ten Section 46 questions remain present and are explicitly classified as Non-normative Open Design Issues. Ordinary `MUST determine`/`MUST define` treatment has been removed, and no alternative is selected or strengthened. | **Resolved** |
| `REM-03R-F08` | `REM-03-404`–`REM-03-406` | The three capability statements are explicit non-normative examples rather than selected formal capability levels. The substantive interoperability rules in `REM-03-403` and `REM-03-407` remain unchanged. | **Resolved** |

**Finding disposition result:** all eight findings are fully resolved.

---

# 5. Explicit non-normative-status verification

The following 60 retained identifiers now receive explicit non-normative treatment in both their Requirement and Classification fields.

| Review basis | Identifiers | Status verified |
|---|---|---|
| Illustrative record-type breadth | `REM-03-005` | Non-normative model example |
| Provisional/open syntax status | `REM-03-025`, `REM-03-054` | Non-normative specification-status/open-design notes |
| Section 16 example rights fields | `REM-03-173`–`REM-03-177` | Non-normative model examples |
| Section 18.1 envelope-validation examples | `REM-03-195`–`REM-03-199` | Non-normative validation examples |
| Section 18.2 schema-validation examples | `REM-03-201`–`REM-03-204` | Non-normative validation examples |
| Section 18.3 authority-validation examples | `REM-03-206`–`REM-03-209` | Non-normative validation examples |
| Section 18.4 repository-state examples | `REM-03-211`–`REM-03-214` | Non-normative validation examples |
| Section 18.5 semantic-validation examples | `REM-03-216`–`REM-03-218` | Non-normative validation examples |
| Section 26 embed-form examples | `REM-03-283`–`REM-03-286` | Non-normative model examples |
| Section 26 example provenance fields | `REM-03-288`–`REM-03-290` | Non-normative model examples |
| Section 29 local-state examples | `REM-03-307`–`REM-03-310` | Non-normative model examples |
| Section 35 example reply representation | `REM-03-353` | Non-normative model example |
| Section 36 example reaction fields | `REM-03-363`–`REM-03-364` | Non-normative model examples |
| Section 37 example repost commentary | `REM-03-370` | Non-normative model example |
| Section 38 example moderation-label fields | `REM-03-374`–`REM-03-377` | Non-normative model examples |
| Section 42 capability-declaration examples | `REM-03-404`–`REM-03-406` | Non-normative capability examples |
| Section 46 open questions | `REM-03-456`–`REM-03-465` | Non-normative Open Design Issues |

The 60 identifiers remain available for stable traceability, but their illustrative or unresolved content is no longer presented as an ordinary protocol requirement.

## Preserved substantive validation requirements

The remediation did not weaken or replace the actual validation-layer requirements:

- `REM-03-193` and `REM-03-194` preserve the multi-level model and envelope-validation layer;
- `REM-03-200` preserves schema validation;
- `REM-03-205` preserves authority validation;
- `REM-03-210` preserves repository-state validation;
- `REM-03-215` preserves the permission for application semantic validation; and
- `REM-03-219` preserves the boundary between semantic validation and protocol validity.

---

# 6. Section 45 scenario-strength verification

Section 45 states that a basic implementation **should** pass the scenario. The affected entries now preserve that scenario-level strength.

| Identifier | Required remediated keyword | Verified result |
|---|---|---|
| `REM-03-445` | `SHOULD NOT` | Pass |
| `REM-03-448` | `SHOULD` | Pass |
| `REM-03-450` | `SHOULD` | Pass |
| `REM-03-452` | `SHOULD` | Pass |
| `REM-03-453` | `SHOULD` | Pass |

The entries remain scenario-level expectations. Independently sourced mandatory requirements elsewhere in REM-03 remain separate and were not imported into the scenario.

---

# 7. Section 46 open-design verification

Each Section 46 source question maps to one retained Non-normative Open Design Issue.

| Identifier | Open subject | Verification |
|---|---|---|
| `REM-03-456` | Envelope-field placement | Question retained; embedded versus inherited placement remains unresolved |
| `REM-03-457` | Individual record signatures | Question retained; no signature requirement selected |
| `REM-03-458` | Restricted-record enforcement | Access controls, encryption and combined approaches remain unresolved |
| `REM-03-459` | Usage-rights vocabulary | Relay-defined, existing and external vocabulary approaches remain unresolved |
| `REM-03-460` | Minimum AI-provenance information | Minimum declaration structure remains unresolved |
| `REM-03-461` | Historical-version retention | Retrievable content versus hashes/tombstones remains unresolved |
| `REM-03-462` | Relay core schema governance | Publishing authority remains unresolved |
| `REM-03-463` | Dynamic-audience evaluation and caching | Evaluation and caching rules remain unresolved |
| `REM-03-464` | Cross-repository transactions | Support and safe transaction semantics remain unresolved |
| `REM-03-465` | Cross-identity record transfer | Identity-preserving transfer versus new record with provenance remains unresolved |

No entry imposes an ordinary requirement to resolve the question, supplies an answer, selects an alternative or strengthens one alternative over another.

---

# 8. Section 47 PROVISIONAL v0.1 boundary verification

All 17 Section 47 entries are explicitly classified as **PROVISIONAL v0.1** decisions. Each Requirement also retains provisional wording, and the remediation did not change any individual behavioural keyword.

| Identifier | Behavioural keyword | Provisional subject |
|---|---|---|
| `REM-03-466` | `SHOULD` | JSON-compatible structured records |
| `REM-03-467` | `MUST` | Stable Record URIs |
| `REM-03-468` | `MUST` | Versioned schemas |
| `REM-03-469` | `MUST` | One current version per logical record |
| `REM-03-470` | `MUST` | Optimistic concurrency checks |
| `REM-03-471` | `MUST` | Signed commits as minimum authority proof |
| `REM-03-472` | `MAY` | Optional signatures for externally issued assertions |
| `REM-03-473` | `SHOULD` | Four visibility classifications |
| `REM-03-474` | `MUST` | Logical deletion with tombstones |
| `REM-03-475` | `MUST` | No reuse of deleted Record Keys |
| `REM-03-476` | `MUST` | Content-addressed blob references |
| `REM-03-477` | `SHOULD` | Structured provenance |
| `REM-03-478` | `MUST` | Preservation of unknown fields and schemas |
| `REM-03-479` | `SHOULD` | Acting-identity storage for replies, reactions and reposts |
| `REM-03-480` | `MUST` | Projections remain non-canonical unless explicitly saved |
| `REM-03-481` | `SHOULD` | Moderation labels as separate records |
| `REM-03-482` | `MUST` | Schema rules layered over a common envelope |

The behavioural keywords operate inside the overriding **PROVISIONAL v0.1** boundary. None of these entries has been flattened into a final protocol commitment.

---

# 9. Section 48 principle and hand-off verification

`REM-03-483` remains the single governing Core Record Principle. It preserves both elements of the source rule:

- a Relay Record is a stable, portable logical object governed by repository authority; and
- it is not a disposable application-owned database row dependent on the creating application.

The final source sentence introducing the Relay Application and Permission Model remains an editorial model-boundary hand-off. It has not generated `REM-03-484` or any other additional REM-03 requirement.

---

# 10. Numbering, uniqueness and traceability results

| Part | Source sections | Verified range | Count | Result |
|---|---:|---:|---:|---|
| Part 1 | 1–5 | `REM-03-001`–`REM-03-045` | 45 | Continuous |
| Part 2 | 6–10 | `REM-03-046`–`REM-03-098` | 53 | Continuous |
| Part 3 | 11–15 | `REM-03-099`–`REM-03-165` | 67 | Continuous |
| Part 4 | 16–20 | `REM-03-166`–`REM-03-244` | 79 | Continuous |
| Part 5 | 21–25 | `REM-03-245`–`REM-03-281` | 37 | Continuous |
| Part 6 | 26–30 | `REM-03-282`–`REM-03-322` | 41 | Continuous |
| Part 7 | 31–35 | `REM-03-323`–`REM-03-360` | 38 | Continuous |
| Part 8 | 36–40 | `REM-03-361`–`REM-03-393` | 33 | Continuous |
| Part 9 | 41–45 | `REM-03-394`–`REM-03-455` | 62 | Continuous |
| Part 10 | 46–48 | `REM-03-456`–`REM-03-483` | 28 | Continuous |

**Complete sequence result:**

- total identifiers: 483;
- unique identifiers: 483;
- missing identifiers: none;
- duplicate identifiers: none;
- first identifier: `REM-03-001`;
- final identifier: `REM-03-483`;
- part-boundary gaps: none;
- renumbered unaffected requirements: none; and
- entries missing Source, Requirement, Classification or Notes fields: none.

Stable traceability has therefore been preserved across the remediation.

---

# 11. Residual and newly discovered findings

No residual defect from `REM-03R-F01` through `REM-03R-F08` remains.

No new material source, normative-strength, status-boundary, numbering, uniqueness or traceability defect was identified.

The remediation diff contains no unrelated REM-entry change. Parts 3 and 5 remained unchanged, and changes in the other parts are confined to the expected finding dispositions and the Section 47 status clarification.

---

# 12. Final verdict

## **VERIFIED — REM-03 is ready for EA-05-03 Requirements Catalogue generation.**

All eight REM-03R-01 findings are resolved. The extraction remains complete and continuously numbered from `REM-03-001` through `REM-03-483`; all converted examples and open issues are explicitly non-normative; the Section 45 scenario retains its source-level `SHOULD` framing; the Section 46 questions remain unresolved; the Section 47 decisions remain unmistakably **PROVISIONAL v0.1**; and `REM-03-483` remains the governing Core Record Principle.

EA-05-03 catalogue generation may proceed as the next editorial task, provided that catalogue treatment continues to exclude the explicitly non-normative entries from ordinary requirement generation and preserves the overriding **PROVISIONAL v0.1** status of `REM-03-466`–`REM-03-482`.
