# REM-03R-01 — Record Requirement Extraction Review

## Document status

**Canonical editorial extraction review**

**Source model:** `design-notes/03-record-model.md`  
**Extraction reviewed:** REM-03 Parts 1–10  
**Source coverage:** Sections 1–48  
**Requirement range reviewed:** `REM-03-001` through `REM-03-483`

---

# 1. Purpose

This review verifies the complete REM-03 Record Requirement Extraction Matrix against the Record Model before canonical Requirements Catalogue generation.

The design note is the sole authoritative source. The review tests source coverage, numbering, traceability, normative strength, qualifications and exceptions, omission, unsupported promotion, section attribution, decomposition, terminology, and the treatment of examples, explanatory material, scenarios, open questions, provisional decisions, invariants and model-boundary statements.

This document does not modify the extraction. Findings below identify remediation required before EA-05-03 catalogue generation.

---

# 2. Extraction sequence and numbering review

| Part | Source Sections | REM range | Review result |
|---|---:|---:|---|
| Part 1 | 1–5 | `REM-03-001`–`REM-03-045` | Continuous |
| Part 2 | 6–10 | `REM-03-046`–`REM-03-098` | Continuous |
| Part 3 | 11–15 | `REM-03-099`–`REM-03-165` | Continuous |
| Part 4 | 16–20 | `REM-03-166`–`REM-03-244` | Continuous |
| Part 5 | 21–25 | `REM-03-245`–`REM-03-281` | Continuous |
| Part 6 | 26–30 | `REM-03-282`–`REM-03-322` | Continuous |
| Part 7 | 31–35 | `REM-03-323`–`REM-03-360` | Continuous |
| Part 8 | 36–40 | `REM-03-361`–`REM-03-393` | Continuous |
| Part 9 | 41–45 | `REM-03-394`–`REM-03-455` | Continuous |
| Part 10 | 46–48 | `REM-03-456`–`REM-03-483` | Continuous |

**Numbering verdict:** PASS. The ten-part extraction forms one continuous, unique sequence from `REM-03-001` through `REM-03-483` with no identifier gap at a part boundary.

**Source-section coverage verdict:** PASS. Sections 1–48 are represented in order and no source section is absent from the extraction series.

---

# 3. Review findings

## REM-03R-F01 — Illustrative record-type examples promoted into a mandatory model capability

**Affected REM-03 requirement(s)**  
`REM-03-005`

**Severity**  
Medium

**Defect classification**  
Example over-extraction; unsupported normative promotion.

**Source-model basis**  
Section 1 defines a Relay Record and then supplies an illustrative list introduced as “Examples include”. The list is not a closed mandatory capability set.

**Review finding**  
`REM-03-005` converts the illustrative list into a `MUST` capability covering content, activity, relationship, preference, credential, authority, moderation and deletion-related records. Although the Notes correctly say the examples are illustrative, the Requirement promotes those examples into an ordinary normative obligation.

**Required correction**  
Retain the identifier for traceability but convert the entry to an explicitly non-normative model-example record, or remove the ordinary normative requirement while accounting for the examples in extraction notes. The general semantic scope remains covered by `REM-03-004` and later category/schema requirements.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F02 — Application interaction rule adds an unsupported universal authorisation condition

**Affected REM-03 requirement(s)**  
`REM-03-007`

**Severity**  
High

**Defect classification**  
Invented qualification; semantic strengthening.

**Source-model basis**  
Section 1 states that an application “may create, edit or display a record, but the record belongs to the repository in which it was authorised.”

**Review finding**  
The extraction adds that an application may create, edit or display a record “only through valid protocol and repository-authorised operations.” That condition is not stated in this source sentence and is materially over-broad for display: public records can be displayed without the display itself being a repository-authorised mutation. Creation and editing authority are established elsewhere in the model and should not be imported into this sentence in a way that changes the meaning of display.

**Required correction**  
Preserve the source permission and ownership separation without the added universal condition. The entry may state that applications MAY create, edit or display records and that such interaction MUST NOT establish application ownership. Leave operation-specific authority requirements to the source sections that define creation, update and access.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F03 — Provisional/open syntax statements converted into ordinary normative prohibitions

**Affected REM-03 requirement(s)**  
`REM-03-025`, `REM-03-054`

**Severity**  
Medium

**Defect classification**  
Specification-status over-extraction; open-design treatment.

**Source-model basis**  
Section 3 says the exact serialisation “remains provisional”. Section 6.1 says the exact version-reference syntax “remains open”.

**Review finding**  
Both source statements describe specification status. The extraction converts them into `MUST NOT` implementation requirements. The intended caution is editorially valid, but an unresolved/provisional format statement is not itself an ordinary protocol prohibition and should not later receive an ordinary catalogue identifier as if the source had normatively selected a wire-format constraint.

**Required correction**  
Retain both REM identifiers for traceability but classify them explicitly as non-normative specification-status/open-design notes. Their substance should remain visible: the Section 3 JSON and Section 6.1 `?version=3` forms are examples, not final syntax.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F04 — Example fields and illustrative cases repeatedly promoted into standalone normative requirements

**Affected REM-03 requirement(s)**  
`REM-03-173`–`REM-03-177`; `REM-03-283`–`REM-03-286`; `REM-03-288`–`REM-03-290`; `REM-03-307`–`REM-03-310`; `REM-03-353`; `REM-03-363`–`REM-03-364`; `REM-03-370`; `REM-03-374`–`REM-03-377`

**Severity**  
Medium

**Defect classification**  
Example over-extraction; illustrative syntax/content promoted to normative `MAY`/`SHOULD` requirements.

**Source-model basis**  
The affected source passages are explicitly examples or example JSON: rights fields in Section 16; embed forms and example provenance fields in Section 26; local-state examples in Section 29; the example `replyTo` representation in Section 35; example reaction fields in Section 36; repost example commentary in Section 37; and example moderation-label fields in Section 38.

**Review finding**  
The extraction generally avoids making the example field names mandatory, but it still creates ordinary normative entries from illustrative material. That changes examples into protocol permissions or recommendations and risks later catalogue treatment making the examples appear selected by the protocol. The underlying normative concepts are already captured by surrounding source-derived requirements, including structured rights support, embed provenance, local/canonical-state criteria, reference semantics, reaction/repost modelling and independently issued moderation labels.

**Required correction**  
Retain the affected identifiers for stable traceability but mark the entries explicitly non-normative model examples, or fold the examples into Notes on the surrounding normative requirements without assigning them ordinary catalogue treatment. Do not infer a final field vocabulary or required schema shape from example JSON.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F05 — Validation examples promoted into normative validation recommendations

**Affected REM-03 requirement(s)**  
`REM-03-195`–`REM-03-199`; `REM-03-201`–`REM-03-204`; `REM-03-206`–`REM-03-209`; `REM-03-211`–`REM-03-214`; `REM-03-216`–`REM-03-218`

**Severity**  
High

**Defect classification**  
Example over-extraction; normative promotion of illustrative validation checks.

**Source-model basis**  
Sections 18.1–18.5 define five validation levels and then label the detailed checks under each level as “Examples”.

**Review finding**  
The extraction correctly captures the validation levels themselves in `REM-03-193`, `REM-03-194`, `REM-03-200`, `REM-03-205`, `REM-03-210`, `REM-03-215` and `REM-03-219`. It then promotes the illustrative checks beneath those headings into standalone `SHOULD` or `MAY` requirements. This is not source-strength preservation: the source presents them as examples of what each validation layer can encompass, not as separately recommended conformance checks.

**Required correction**  
Retain the affected identifiers for traceability but convert them to explicitly non-normative validation examples. Preserve the normative validation-layer requirements and the semantic/protocol-validity boundary. Later specifications or schemas may independently make particular checks mandatory where the source actually establishes that obligation.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F06 — Compliance-scenario entries locally strengthened above the scenario’s `SHOULD` framing

**Affected REM-03 requirement(s)**  
`REM-03-445`, `REM-03-448`, `REM-03-450`, `REM-03-452`, `REM-03-453`

**Severity**  
High

**Defect classification**  
Normative-strength promotion; scenario handling.

**Source-model basis**  
Section 45 opens with: “A basic record implementation should pass the following test.” The subsequent scenario demonstrates expected behaviour for creation, cross-application update, conflict, reply ownership, visibility change, deletion and migration.

**Review finding**  
Most Section 45 extraction entries correctly retain `SHOULD`, but five scenario-local outcomes are expressed as `MUST` or `MUST NOT`. Equivalent mandatory principles exist elsewhere in the Record Model, but that does not permit the extraction to silently promote the strength of the scenario itself. The scenario must remain a scenario-level conformance expectation rather than becoming a second source of stronger normativity.

**Required correction**  
Normalise the Section 45 scenario treatment consistently: positive scenario behaviours SHOULD occur and scenario prohibitions SHOULD NOT occur. Specifically, weaken `REM-03-445` to `SHOULD NOT`; `REM-03-448`, `REM-03-450`, `REM-03-452` and `REM-03-453` to `SHOULD`. Preserve mandatory equivalents separately where they are independently sourced from Sections 1–44.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F07 — Open design questions converted into mandatory resolution requirements

**Affected REM-03 requirement(s)**  
`REM-03-456`–`REM-03-465`

**Severity**  
High

**Defect classification**  
Open-design over-extraction; unsupported normativity.

**Source-model basis**  
Section 46 is explicitly titled “Open design questions” and asks ten unresolved questions concerning envelope placement, signatures, visibility enforcement, rights vocabulary, AI provenance, history retention, schema governance, dynamic audiences, cross-repository transactions and record transfer.

**Review finding**  
Part 10 correctly labels the entries “Open design obligation” and states that they are not settled v0.1 rules, but each Requirement nevertheless says the final specification or architecture `MUST` determine an answer. That converts unresolved editorial questions into ordinary normative obligations. The questions are important programme work, but they are not protocol requirements until governance/specification work resolves them.

**Required correction**  
Retain `REM-03-456`–`REM-03-465` as explicitly **Non-normative Open Design Issue** entries. Remove ordinary `MUST` treatment. Preserve the questions and their traceability without selecting an answer, strengthening an alternative or assigning future catalogue requirements until the design issue is resolved through the appropriate governance process.

**Disposition**  
Remediation required before catalogue generation.

---

## REM-03R-F08 — Capability-declaration examples in interoperability section over-decomposed as selected capability levels

**Affected REM-03 requirement(s)**  
`REM-03-404`–`REM-03-406`

**Severity**  
Low

**Defect classification**  
Example over-extraction; unnecessary normative decomposition.

**Source-model basis**  
Section 42 says a compliant application may state examples such as full support, read-only support, or preservation without display. Its actual minimum requirement is that unsupported records are not damaged, misrepresented or discarded.

**Review finding**  
The examples illustrate possible application capability declarations; they do not establish three canonical capability levels or a required negotiation taxonomy. `REM-03-407` correctly captures the substantive minimum interoperability rule.

**Required correction**  
Retain `REM-03-404`–`REM-03-406` only as non-normative capability examples, or consolidate their illustrative meaning into Notes associated with `REM-03-403`/`REM-03-407`. Do not create ordinary catalogue requirements that imply Relay v0.1 has selected a formal three-level capability vocabulary.

**Disposition**  
Remediation required before catalogue generation.

---

# 4. Special-status review

## 4.1 Provisional v0.1 decisions — `REM-03-466`–`REM-03-482`

Section 47 expressly says Relay v0.1 “will provisionally assume” the listed decisions. Part 10 visibly carries that status into every affected entry through both the Requirement and Classification.

**Review treatment:** acceptable special-status extraction. These entries must remain visibly **PROVISIONAL v0.1** through remediation and any later catalogue treatment. They must not be flattened into final protocol commitments merely because an individual entry uses `MUST`, `SHOULD` or `MAY` to express the behaviour provisionally assumed. Catalogue generation should preserve both the behavioural keyword and the overriding provisional status.

No finding requires removal of `REM-03-466`–`REM-03-482`; the defect is avoided so long as their provisional status remains explicit.

## 4.2 Core record principle — `REM-03-483`

Section 48 explicitly reduces the Record Model to one governing rule. `REM-03-483` is a reasonable normative rendering of that governing principle and is traceable to the source. No remediation is required.

## 4.3 Model-boundary hand-off

The final sentence of Section 48 introduces the next core object, the Relay Application and Permission Model. It is a model-boundary/editorial hand-off and was not extracted as an additional REM-03 requirement. This treatment is correct.

---

# 5. Coverage, omission and traceability assessment

The review found no missing source section and no numbering gap across the ten extraction parts. The principal defects are not missing coverage but **over-extraction and strength/status handling**: illustrative examples were repeatedly converted into ordinary normative entries; the compliance scenario was locally strengthened; and open design questions were expressed as mandatory resolution obligations.

Outside the findings above, the extraction generally preserves the Record Model’s important distinctions:

- logical Record URI versus historical Record Version;
- schema authority versus record/repository control;
- subject versus authorising identity versus submitter;
- provenance declaration versus verification;
- visibility versus usage rights;
- protocol validation versus application semantic validation;
- canonical records versus application projections and local drafts;
- source records versus translations, embeds, cached copies and indexes;
- record identity versus commit identity;
- application support limitations versus preservation of unknown valid records.

Repeated source principles appearing again as invariants or compliance examples are not treated as extraction duplicates merely because the subject matter overlaps. Where the source deliberately restates a rule in an invariant role, that editorial role is preserved.

No material source omission was identified that independently blocks remediation. The review does not certify the current extraction because the identified promotions would materially affect canonical catalogue content if left unchanged.

---

# 6. Finding summary

| Finding | Severity | Primary issue | Status |
|---|---|---|---|
| REM-03R-F01 | Medium | Record-type examples promoted | Open — remediation required |
| REM-03R-F02 | High | Invented universal authorisation condition | Open — remediation required |
| REM-03R-F03 | Medium | Provisional/open syntax promoted | Open — remediation required |
| REM-03R-F04 | Medium | Example fields/cases promoted | Open — remediation required |
| REM-03R-F05 | High | Validation examples promoted | Open — remediation required |
| REM-03R-F06 | High | Compliance scenario strengthened | Open — remediation required |
| REM-03R-F07 | High | Open questions made normative | Open — remediation required |
| REM-03R-F08 | Low | Capability examples over-decomposed | Open — remediation required |

**Finding count:** 8  
**Severity distribution:** 4 High; 3 Medium; 1 Low.

---

# 7. Editorial QA record

## Scope QA

- Authoritative source reviewed: `design-notes/03-record-model.md`, Sections 1–48.
- Extraction reviewed: REM-03 Parts 1–10.
- Requirement range reviewed: `REM-03-001`–`REM-03-483`.
- No REM-04 or later source model was used to create new Record requirements.

## Numbering QA

- First identifier: `REM-03-001`.
- Final identifier: `REM-03-483`.
- Part boundaries are continuous: 045→046, 098→099, 165→166, 244→245, 281→282, 322→323, 360→361, 393→394 and 455→456.
- No numbering remediation is required; affected identifiers should be retained where possible so traceability remains stable.

## Normative-strength QA

- Mandatory source rules are generally preserved as `MUST`/`MUST NOT`.
- Recommendations and permissions are generally preserved as `SHOULD`/`SHOULD NOT` and `MAY`.
- Findings F01, F03, F04, F05, F07 and F08 identify material that should not receive ordinary normative treatment.
- Finding F02 identifies an added condition not supplied by the cited source.
- Finding F06 identifies scenario-local strengthening that must be normalised to the scenario’s `SHOULD` framing.

## Status-boundary QA

- Section 46 must remain unresolved and non-normative.
- Section 47 must remain explicitly **PROVISIONAL v0.1**.
- Section 48 core principle is retained as the governing Record principle.
- Section 48’s hand-off to the Application and Permission Model remains non-normative editorial boundary text.

## Catalogue-readiness QA

The current extraction must not be used directly for EA-05-03 catalogue generation. Doing so would risk assigning canonical Record requirement identifiers to examples and unresolved design issues and would preserve several unsupported strength promotions.

---

# 8. Final verdict

## **REMEDIATION REQUIRED — REM-03 is not ready for Requirements Catalogue generation.**

REM-03 is structurally complete and continuously numbered across `REM-03-001`–`REM-03-483`, but the eight findings above require targeted remediation before catalogue generation.

The remediation should preserve existing REM identifiers wherever possible, explicitly reclassify non-normative examples and open issues rather than deleting traceability, preserve `REM-03-466`–`REM-03-482` as **PROVISIONAL v0.1**, and normalise Section 45 scenario strength without importing stronger equivalent rules from other source sections.
