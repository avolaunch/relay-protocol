# REM-05R-01 — Relationship Requirement Extraction Review

## Document status

**Canonical requirement-extraction review**

This document reviews the completed REM-05 extraction series against the authoritative source model, `design-notes/05-relationship-model.md`.

The review covers:

- `REM-05 Part 1 — Relationship Requirement Extraction Matrix (Sections 1–5).md`
- `REM-05 Part 2 — Relationship Requirement Extraction Matrix (Sections 6–10).md`
- `REM-05 Part 3 — Relationship Requirement Extraction Matrix (Sections 11–15).md`
- `REM-05 Part 4 — Relationship Requirement Extraction Matrix (Sections 16–20).md`
- `REM-05 Part 5 — Relationship Requirement Extraction Matrix (Sections 21–25).md`
- `REM-05 Part 6 — Relationship Requirement Extraction Matrix (Sections 26–30).md`
- `REM-05 Part 7 — Relationship Requirement Extraction Matrix (Sections 31–35).md`
- `REM-05 Part 8 — Relationship Requirement Extraction Matrix (Sections 36–40).md`
- `REM-05 Part 9 — Relationship Requirement Extraction Matrix (Sections 41–45).md`
- `REM-05 Part 10 — Relationship Requirement Extraction Matrix (Sections 46–50).md`
- `REM-05 Part 11 — Relationship Requirement Extraction Matrix (Sections 51–55).md`
- `REM-05 Part 12 — Relationship Requirement Extraction Matrix (Sections 56–60).md`

The source model is authoritative. The extraction matrices are reviewed artefacts and do not override source wording where the two differ.

---

# 1. Review objectives

The review verifies:

1. complete section coverage;
2. requirement numbering continuity;
3. traceability to source statements;
4. preservation of normative strength;
5. absence of unsupported requirements;
6. absence of material omissions;
7. correct section attribution;
8. appropriate decomposition of compound source statements;
9. consistent terminology across all twelve parts;
10. preservation of qualifications, exceptions and provisional status;
11. separation of genuine extraction defects from acceptable editorial explanation or decomposition.

The review does **not** redesign the Relationship Model and does not resolve open design questions on behalf of the source.

---

# 2. Coverage and numbering audit

| Part | Source sections | Requirement range | Review status |
|---|---:|---:|---|
| Part 1 | 1–5 | REM-05-001–053 | Covered |
| Part 2 | 6–10 | REM-05-054–096 | Covered |
| Part 3 | 11–15 | REM-05-097–151 | Covered |
| Part 4 | 16–20 | REM-05-152–209 | Covered |
| Part 5 | 21–25 | REM-05-210–278 | Covered |
| Part 6 | 26–30 | REM-05-279–342 | Covered; finding recorded below |
| Part 7 | 31–35 | REM-05-343–399 | Covered |
| Part 8 | 36–40 | REM-05-400–457 | Covered |
| Part 9 | 41–45 | REM-05-458–505 | Covered |
| Part 10 | 46–50 | REM-05-506–542 | Covered; findings recorded below |
| Part 11 | 51–55 | REM-05-543–600 | Covered |
| Part 12 | 56–60 | REM-05-601–673 | Covered; findings recorded below |

### Numbering result

The REM-05 sequence is continuous from `REM-05-001` through `REM-05-673`.

No numbering gaps or collisions were identified at part boundaries.

### Section coverage result

All sixty numbered source sections are represented exactly once as primary extraction scope across Parts 1–12.

No source section is absent from the extraction series.

---

# 3. Overall assessment

REM-05 is **substantially complete and highly traceable**, but it is **not yet fit for Requirements Catalogue generation without a targeted remediation pass**.

The principal issue is not missing source coverage. The principal issue is **normative promotion**: a small number of examples, descriptive possibilities, open questions and provisional assumptions were converted into stronger normative requirements than the source itself establishes.

Most of the 673 extracted requirements are acceptable decompositions of the source. Repetition of a principle in a later invariant, compliance scenario or provisional-decision section is not automatically a duplicate defect because the source itself deliberately restates those principles in different editorial roles.

No evidence was found that the extraction has lost a whole source section or a major relationship concept.

---

# 4. Findings

## REM-05R-F01 — Formal-group examples were promoted into normative support requirements

**Affected requirements**  
`REM-05-291` through `REM-05-295`

**Severity**  
Moderate

**Defect classification**  
Normative-strength inflation; example over-extraction.

**Source-model basis**  
Section 27 states:

> “Examples: organisation; association; project team; community; cooperative.”

The source identifies these as examples of formal groups. It does not state that every conforming formal-group implementation `SHOULD` support each example as an independently normative capability.

**Review finding**  
The extraction converts each example into a `SHOULD` requirement. That adds normative force not present in the source.

The underlying semantic observation is valid: these are intended examples of the formal-group concept. The defect is the conversion of illustrative scope into five normative support obligations.

**Required correction**  
Either:

- remove `REM-05-291` through `REM-05-295` as independent normative requirements and preserve the examples in Notes; or
- retain them as explicitly non-normative model examples rather than `SHOULD` requirements.

**Disposition**  
**Remediation required before catalogue generation.**

---

## REM-05R-F02 — Descriptive duplicate possibility was promoted to a mandatory repository obligation

**Affected requirement**  
`REM-05-506`

**Severity**  
Moderate

**Defect classification**  
Normative-strength inflation.

**Source-model basis**  
Section 46 states:

> “Multiple applications may attempt to create equivalent relationship records.”

This describes a condition the model must be capable of encountering. The following source sentence then provides the actual normative guidance:

> “The repository should prevent accidental duplication where the schema defines one active relationship per source, target and context.”

**Review finding**  
`REM-05-506` converts the descriptive first sentence into:

> “A Relay repository MUST anticipate...”

The concept is useful context, but the source does not independently impose a `MUST anticipate` obligation. The operative requirement is already captured by `REM-05-507`.

**Required correction**  
Treat the multiple-application condition as explanatory context for duplicate handling rather than an independent `MUST` requirement.

**Disposition**  
**Remediation required before catalogue generation.**

---

## REM-05R-F03 — A SHOULD-level duplicate-prevention rule was decomposed into a stronger MUST

**Affected requirement**  
`REM-05-508`

**Severity**  
Moderate

**Defect classification**  
Incorrect normative strength.

**Source-model basis**  
Section 46 states:

> “The repository should prevent accidental duplication where the schema defines one active relationship per source, target and context.”

**Review finding**  
`REM-05-507` correctly preserves this as `SHOULD`. `REM-05-508` then extracts the source/target/context qualification as a separate `MUST` governing duplicate detection.

Decomposition is reasonable, but decomposition must not strengthen a `SHOULD` source sentence into a `MUST` unless another source statement independently establishes that stronger obligation.

**Required correction**  
Retain the source/target/context qualification, but preserve the parent sentence’s `SHOULD` strength or fold the qualification back into `REM-05-507`.

**Disposition**  
**Remediation required before catalogue generation.**

---

## REM-05R-F04 — Client-specific follow duplication was strengthened from SHOULD to MUST NOT

**Affected requirement**  
`REM-05-509`

**Severity**  
Moderate

**Defect classification**  
Incorrect normative strength.

**Source-model basis**  
Section 46 states:

> “Alice should not need five separate active follow records for Bob merely because five clients were used.”

**Review finding**  
The extraction converts `should not need` into `MUST NOT be required`.

The extracted meaning is faithful, but the normative level is stronger than the source.

**Required correction**  
Use `SHOULD NOT` or preserve the sentence as explanatory support for the schema-dependent duplicate-prevention requirement.

**Disposition**  
**Remediation required before catalogue generation.**

---

## REM-05R-F05 — Permitted coexistence was promoted into unconditional mandatory coexistence rules

**Affected requirements**  
`REM-05-515`, `REM-05-516`

**Severity**  
Moderate

**Defect classification**  
Normative-strength inflation; qualification distortion.

**Source-model basis**  
Section 47 states:

> “Different relationship types or contexts may coexist.”

**Review finding**  
The source permits coexistence. It does not, by that sentence alone, impose an unconditional `MUST NOT` / `MUST permit` obligation for every schema configuration.

`REM-05-515` partly protects against this by adding “unless the governing schema explicitly requires that restriction,” but it still converts a source `may` into a mandatory repository rule. `REM-05-516` similarly converts possible coexistence of contexts into a `MUST permit` requirement.

The intended design direction is clear, but the extraction should not increase normative force beyond the source.

**Required correction**  
Represent coexistence as a permitted schema outcome (`MAY`) and retain the source distinction between uniqueness constraints and legitimate differences in type or context.

**Disposition**  
**Remediation required before catalogue generation.**

---

## REM-05R-F06 — Open design questions were converted into settled MUST requirements

**Affected requirements**  
`REM-05-636` through `REM-05-645`

**Severity**  
High

**Defect classification**  
Open-question over-extraction; normative-status error.

**Source-model basis**  
Section 58 is explicitly titled **Open design questions** and presents ten unresolved questions concerning:

- distributed graph indexing;
- reciprocal activation;
- private graph encryption;
- dynamic audiences;
- relationship requests;
- authority relationships;
- identity recovery;
- historical mutuality;
- external identity matching;
- schema conflicts.

The source deliberately does not answer those questions.

**Review finding**  
The extraction correctly avoids selecting one of the candidate answers, but it converts every open question into a `MUST define` or `MUST specify` protocol requirement.

That is still a normative promotion. An open design question is an editorial/design obligation to resolve, not yet a protocol conformance requirement imposed by the Relationship Model.

These items are valuable and should not be lost, but they must remain visibly non-normative until resolved by an authoritative design decision.

**Required correction**  
Reclassify `REM-05-636` through `REM-05-645` as non-normative **Open Design Issue** entries, or remove them from the normative extraction sequence and preserve them in a dedicated unresolved-design section.

They MUST NOT enter the Requirements Catalogue as settled protocol requirements in their present form.

**Disposition**  
**Blocking remediation required before catalogue generation.**

---

## REM-05R-F07 — Provisional v0.1 assumptions were expressed with final normative force

**Affected requirements**  
`REM-05-646` through `REM-05-671`

**Severity**  
High

**Defect classification**  
Provisional-status distortion; normative-strength ambiguity.

**Source-model basis**  
Section 59 states:

> “Relay v0.1 will provisionally assume:”

and then lists the working assumptions.

**Review finding**  
The extraction consistently labels these entries as **Provisional v0.1 decision**, which is valuable and prevents complete loss of the source qualification. However, many requirements then use unconditional RFC-style `MUST` language.

The result contains an internal tension: the classification says provisional while the requirement wording reads final and mandatory.

The source supports treating these assumptions as the current v0.1 working baseline, but it does not support erasing their provisional status.

**Required correction**  
Before catalogue generation, adopt one consistent treatment for Section 59:

- preserve these as explicitly **PROVISIONAL** v0.1 requirements with the provisional status carried into the requirement text and catalogue metadata; or
- keep them in a separate provisional-decision register until the relevant design decisions are confirmed.

Do not silently catalogue them as ordinary final `MUST` requirements.

**Disposition**  
**Blocking editorial remediation required before catalogue generation.**

---

## REM-05R-F08 — Compliance-scenario narrative contains local normative strengthening

**Affected requirements**  
Principally `REM-05-627` through `REM-05-633`

**Severity**  
Low to Moderate

**Defect classification**  
Normative-strength inconsistency; compliance-scenario decomposition.

**Source-model basis**  
Section 57 introduces the scenario with:

> “A basic relationship implementation should pass the following test.”

The scenario then narrates expected outcomes, including independent ownership, termination behaviour and private-block behaviour.

**Review finding**  
Most scenario entries are appropriately expressed as `SHOULD`. Several individual scenario steps are expressed as `MUST` because the same principles are mandatory elsewhere in the model.

Those stronger principles are substantively supported by Sections 31, 34, 51 and 56, so this is **not an unsupported model invention**. The defect is narrower: requirements attributed specifically to the Section 57 compliance scenario should not appear to derive `MUST` strength from narrative text introduced by an overall `SHOULD` compliance test.

**Required correction**  
Either:

- keep Section 57 scenario requirements at `SHOULD` and cross-reference the independently mandatory invariant requirements; or
- retain `MUST` only where the Source field also cites the separate mandatory source statement that supplies that strength.

**Disposition**  
**Editorial remediation required. Not a substantive model defect.**

---

## REM-05R-F09 — Section 60 hand-off to the next model was promoted into a Relationship Model requirement

**Affected requirement**  
`REM-05-673`

**Severity**  
Moderate

**Defect classification**  
Scope over-extraction; model-boundary error.

**Source-model basis**  
Section 60 closes by stating:

> “The next core object is the Relay Migration and Portability Model: how identities, repositories, records, blobs, grants and relationships move between providers without breaking continuity.”

**Review finding**  
This is an editorial transition describing the subject of the next design model. `REM-05-673` converts it into a mandatory Relationship Model requirement that the Migration and Portability Model `MUST preserve` continuity.

The principle is consistent with the source corpus, but the sentence is not itself a normative Relationship Model requirement. Requirements for the next model should be extracted from that model when its own REM is generated.

**Required correction**  
Remove `REM-05-673` from the normative REM-05 extraction or retain the statement only as a non-normative model-boundary note.

**Disposition**  
**Remediation required before catalogue generation.**

---

# 5. Items reviewed and accepted

The following potentially sensitive extraction patterns were reviewed and are **not defects**.

## 5.1 Decomposition of compound lists

Where the source states that a schema, record, verification result, authority relationship or operation must/should/may contain several independently meaningful fields or behaviours, splitting those list items into individually traceable requirements is acceptable.

This is editorial decomposition, not duplication, provided the parent normative strength is preserved.

## 5.2 Repetition across invariants and compliance scenarios

Sections 56 and 57 deliberately restate earlier model principles.

For example, independent relationship ownership, application/provider portability, non-falsification of another identity’s record and private-block behaviour appear earlier and then reappear as invariants or compliance checks.

That repetition is source-authored and therefore does not constitute an accidental extraction duplicate by itself.

The catalogue stage may consolidate equivalent requirements while retaining multiple source traces.

## 5.3 Possible core schemas in Section 54

`REM-05-565` through `REM-05-572` retain `MAY` strength for schemas that the source explicitly introduces as “Possible core schemas.”

These entries do not incorrectly claim that the listed schemas are already mandatory core schemas.

## 5.4 Derived follower counts and reputation

The extraction consistently preserves the distinction between canonical relationship records and derived values such as follower counts, reverse-index views and reputation results.

No defect was identified in that separation.

## 5.5 Claims, verification and disputes

The extraction preserves the source distinction between self-declared claims, independently verified relationships, verification metadata and separately represented disputes/counterclaims.

No material collapse of those evidentiary states was identified.

## 5.6 Blocks and mutes

The extraction preserves the distinction between blocks, mutes, protocol-level deletion and provider/identity suspension.

No material defect was identified in that distinction.

## 5.7 Authority-bearing relationships

The extraction consistently preserves the principle that a relationship label does not silently confer broad technical authority and that authority-bearing relationships require explicit capabilities and scope.

No material omission was identified in this area.

---

# 6. Omission audit

No material source requirement was identified as wholly absent from REM-05 Parts 1–12.

The source concepts represented include:

- relationship definition and purpose;
- relationship records and components;
- source and target semantics;
- relationship types and direction;
- unilateral and reciprocal relationships;
- lifecycle and status;
- independent ownership;
- application and provider continuity;
- follows and subscriptions;
- followers, audiences and derived counts;
- private relationships and selective visibility;
- context and validity periods;
- evidence and verification;
- authority-bearing relationships;
- groups and membership;
- requests and acceptance;
- termination, revocation and disputes;
- blocks and mutes;
- trust, endorsement and reputation;
- privacy risks and discovery;
- reverse relationships and indexes;
- event delivery;
- imports and external identifiers;
- duplication and uniqueness;
- application-specific metadata;
- algorithmic interpretation;
- relationship-based access and permissions;
- provider migration and application replacement;
- schema governance;
- required v0.1 operations;
- invariants;
- compliance scenario;
- open design questions;
- provisional v0.1 decisions;
- the core relationship principle.

The review therefore finds **no blocking omission defect**.

---

# 7. Duplication audit

No numbering collision exists.

No pair of requirements was found whose duplication alone requires deletion before remediation.

There is deliberate semantic repetition because later source sections restate earlier rules as:

- invariants;
- compliance tests;
- provisional v0.1 decisions;
- summary principles.

This should be handled during catalogue consolidation through multi-source traceability rather than by assuming every repeated extraction is erroneous.

The exception is where a descriptive sentence and its immediately following normative sentence were both extracted but the descriptive sentence was independently promoted into a mandatory obligation, as identified in `REM-05R-F02`.

---

# 8. Terminology audit

The extraction is generally consistent in its use of:

- Relay Identity / Relay Identifier;
- Relay Record / Record URI;
- source and target;
- unilateral and reciprocal relationship;
- relationship declaration;
- canonical relationship record;
- relationship schema;
- Permission Grant;
- authority-bearing relationship;
- provider migration;
- application replacement;
- visibility and privacy classifications;
- derived index or reputation result.

No terminology inconsistency was identified that independently blocks catalogue generation.

The main terminology risk is not naming but **status semantics**: open, provisional and normative material must remain distinguishable after remediation.

---

# 9. Severity summary

| Severity | Findings | Count |
|---|---|---:|
| High | F06, F07 | 2 |
| Moderate | F01, F02, F03, F04, F05, F09 | 6 |
| Low–Moderate | F08 | 1 |
| Blocking omissions | None | 0 |
| Numbering defects | None | 0 |

Total recorded findings: **9**.

---

# 10. Required remediation set

Before REM-05 proceeds to Requirements Catalogue generation, a targeted remediation pass should:

1. remove normative force from Section 27 illustrative formal-group examples;
2. correct the normative strength of `REM-05-506`, `REM-05-508`, `REM-05-509`, `REM-05-515` and `REM-05-516`;
3. reclassify Section 58 open design questions as non-normative unresolved design issues;
4. preserve Section 59’s provisional status explicitly and consistently rather than allowing provisional assumptions to appear as ordinary final requirements;
5. normalise Section 57 compliance-scenario strength or add the independent mandatory source citations that justify any retained `MUST` wording;
6. remove `REM-05-673` from the normative Relationship Model extraction or convert it to a non-normative model-boundary note;
7. re-run numbering and traceability QA after any removal, renumbering or status change.

No broad rewrite of REM-05 is required.

---

# 11. Final review verdict

## Verdict: **Remediation required before catalogue generation**

REM-05 is structurally complete, continuously numbered and substantively faithful across the great majority of its extraction.

The review found **no missing source section and no blocking conceptual omission**.

However, the extraction currently contains a limited but material set of normative-status defects, especially:

- examples promoted into recommendations;
- descriptive possibilities promoted into mandatory rules;
- open design questions promoted into `MUST` requirements;
- provisional v0.1 assumptions expressed with wording that can be mistaken for final normative commitments;
- an editorial transition to the next model promoted into a Relationship Model requirement.

Because the Requirements Catalogue is intended to consolidate normative requirements, allowing these defects to flow downstream would make later catalogue review substantially harder.

REM-05 should therefore undergo **one targeted remediation pass**, followed by a short verification review, before catalogue generation begins.

---

# 12. Final editorial QA

The review document itself has been checked for:

- coverage of all twelve REM-05 parts;
- continuous recorded range `REM-05-001` through `REM-05-673`;
- evidence-based findings tied to source wording;
- distinction between extraction defects and acceptable decomposition;
- distinction between editorial defects and substantive model questions;
- explicit remediation for every defect;
- preservation of unresolved questions as unresolved;
- preservation of provisional decisions as provisional;
- absence of invented source requirements;
- a clear catalogue-readiness verdict.

No additional defect has been added solely to increase finding count.
