# REM-04R-01 — Application and Permission Requirement Extraction Review

## Document status

**Canonical requirement-extraction review**

This document reviews the REM-04 extraction series against the authoritative source model, `design-notes/04-application-and-permission-model.md`.

The review covers:

- `REM-04 Part 1 — Application and Permission Requirement Extraction Matrix (Sections 1–5).md`
- `REM-04 Part 2 — Application and Permission Requirement Extraction Matrix (Sections 6–10).md`
- `REM-04 Part 3 — Application and Permission Requirement Extraction Matrix (Sections 11–15).md`
- `REM-04 Part 4 — Application and Permission Requirement Extraction Matrix (Sections 16–20).md`
- `REM-04 Part 5 — Application and Permission Requirement Extraction Matrix (Sections 21–25).md`
- `REM-04 Part 6 — Application and Permission Requirement Extraction Matrix (Sections 26–30).md`
- `REM-04 Part 7 — Application and Permission Requirement Extraction Matrix (Sections 31–35).md`
- `REM-04 Part 8 — Application and Permission Requirement Extraction Matrix (Sections 36–40).md`
- `REM-04 Part 9 — Application and Permission Requirement Extraction Matrix (Sections 41–45).md`
- `REM-04 Part 10 — Application and Permission Requirement Extraction Matrix (Sections 46–50).md`
- `REM-04 Part 11 — Application and Permission Requirement Extraction Matrix (Sections 51–55).md`
- `REM-04 Part 12 — Application and Permission Requirement Extraction Matrix (Sections 56–60).md`
- `REM-04 Part 13 — Application and Permission Requirement Extraction Matrix (Sections 61–65).md`
- `REM-04 Part 14 — Application and Permission Requirement Extraction Matrix (Sections 66–67).md`

The source model is authoritative. The extraction matrices do not override source wording where the two differ.

---

# 1. Review objectives

The review verifies complete section coverage, continuous numbering, source traceability, preservation of normative strength and qualifications, absence of unsupported requirements, appropriate decomposition, consistent terminology, and separation of normative requirements from examples, open questions, provisional decisions and model-boundary text.

The review does not redesign the Application and Permission Model or resolve open design questions on behalf of the source.

---

# 2. Coverage and numbering audit

| Part | Source sections | Requirement range | Review status |
|---|---:|---:|---|
| Part 1 | 1–5 | REM-04-001–069 | Covered; finding recorded below |
| Part 2 | 6–10 | REM-04-070–148 | Covered; findings recorded below |
| Part 3 | 11–15 | REM-04-149–212 | Covered |
| Part 4 | 16–20 | REM-04-213–273 | Covered; finding recorded below |
| Part 5 | 21–25 | REM-04-274–322 | Covered; findings recorded below |
| Part 6 | 26–30 | REM-04-323–390 | Covered; finding recorded below |
| Part 7 | 31–35 | REM-04-391–439 | Covered; findings recorded below |
| Part 8 | 36–40 | REM-04-440–494 | Covered; findings recorded below |
| Part 9 | 41–45 | REM-04-495–538 | Covered; finding recorded below |
| Part 10 | 46–50 | REM-04-539–595 | Covered; finding recorded below |
| Part 11 | 51–55 | REM-04-596–647 | Covered; finding recorded below |
| Part 12 | 56–60 | REM-04-648–693 | Covered; findings recorded below |
| Part 13 | 61–65 | REM-04-694–747 | Covered; finding recorded below |
| Part 14 | 66–67 | REM-04-748–792 | Covered; finding recorded below |
| Missing part | 68–70 | None | Not extracted; blocking finding recorded below |

### Numbering result

The existing REM-04 sequence is continuous from `REM-04-001` through `REM-04-792`. No numbering gaps or collisions were identified.

### Section coverage result

Sections 1 through 67 are represented exactly once as primary extraction scope. Sections 68 through 70 are absent. The extraction series is therefore incomplete against the authoritative source.

---

# 3. Overall assessment

REM-04 is detailed and generally traceable, but it is **not ready for Requirements Catalogue generation**.

The blocking defect is incomplete coverage: the source contains seventy sections, while the extraction ends at Section 67. The omitted tail contains twelve open design questions, sixteen provisional v0.1 decisions, the core application principle and the editorial hand-off to the Relationship Model.

A second recurring defect is normative promotion. Illustrative lists, example JSON fields, example values and example scenarios were repeatedly converted into ordinary `MUST`, `SHOULD` or `MAY` requirements. These entries preserve useful source context, but they must be explicitly non-normative unless another source statement independently establishes the obligation.

The Section 67 compliance scenario also contains local strength inflation. Its individual steps were generally written as `MUST` or `MUST NOT`, although the source introduces the complete scenario as a `SHOULD`-level test.

---

# 4. Findings

## REM-04R-F01 — Sections 68–70 are absent from the extraction series

**Affected scope**  
Source Sections 68, 69 and 70

**Severity**  
High

**Defect classification**  
Blocking coverage omission.

**Review finding**  
The authoritative design note continues after Section 67. Section 68 records twelve unresolved design questions. Section 69 records sixteen provisional v0.1 assumptions. Section 70 states the core application principle and then identifies the Relationship Model as the next model.

None of this material appears in REM-04 Parts 1–14.

**Required correction**  
Create a sequential REM-04 part covering Sections 68–70. Preserve Section 68 as non-normative open design issues, preserve Section 69 as explicitly provisional v0.1 requirements, extract the independently testable clauses of the Section 70 core principle, and retain the hand-off to the Relationship Model only as a non-normative model-boundary note.

**Disposition**  
**Blocking remediation required before catalogue generation.**

---

## REM-04R-F02 — Application-function examples were promoted into a mandatory breadth requirement

**Affected requirement**  
`REM-04-006`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction.

**Review finding**  
Section 1 provides examples of possible Relay Applications. The extraction converts that example list into a `MUST support varied application functions` requirement. The model’s general application definition remains normative elsewhere, but the listed product categories and interface types are illustrative.

**Required correction**  
Retain the entry as an explicitly non-normative breadth example rather than an independent protocol obligation.

---

## REM-04R-F03 — Material-change and verification examples were promoted into selected rules or statuses

**Affected requirements**  
`REM-04-091` through `REM-04-097`; `REM-04-104` through `REM-04-110`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction; premature vocabulary selection.

**Review finding**  
Section 7.1 labels the changes as examples of material changes. Section 8 introduces the status list with “such as”. The extraction converts the first list into mandatory manifest-version triggers and the second into individually normative status values.

The general requirements for versioned material changes and provider verification-status support are independently represented by `REM-04-090` and `REM-04-103`. The examples should not select a final list.

**Required correction**  
Reclassify the affected entries as non-normative model examples. Do not infer a closed material-change list or verification vocabulary.

---

## REM-04R-F04 — Example JSON fields were promoted into physical or semantic requirements

**Affected requirements**  
`REM-04-139` through `REM-04-146`; `REM-04-275` through `REM-04-281`; `REM-04-481` through `REM-04-485`; `REM-04-570` through `REM-04-573`

**Severity**  
High

**Defect classification**  
Illustrative-structure promotion.

**Review finding**  
The cited source basis for these entries is example JSON in Sections 10, 21, 40 and 48. The examples illustrate Permission Grants, AI-use declarations, Revocation Records and application activity attribution. They do not select mandatory field names, a final physical structure, a signature representation or a complete metadata set.

Several underlying concepts are independently normative elsewhere. That does not make the example fields an additional source of final schema obligations.

**Required correction**  
Reclassify the affected entries as non-normative model examples. Preserve independently sourced semantic requirements separately and do not carry example field names into the catalogue as required schema.

---

## REM-04R-F05 — Possible purpose, retention and onward-sharing values were promoted beyond the source

**Affected requirements**  
`REM-04-220` through `REM-04-237`; `REM-04-241` through `REM-04-246`; `REM-04-255` through `REM-04-259`

**Severity**  
Moderate

**Defect classification**  
Premature vocabulary selection; normative-strength inflation.

**Review finding**  
Sections 17, 18 and 19 introduce these lists as “Possible core purposes”, “Possible declarations” and “Possible values”. The extraction turns them into `SHOULD` or `MUST` support requirements for each listed term.

The source does require a machine-readable purpose vocabulary, a retention declaration and an onward-sharing declaration. It does not yet establish every listed value as a mandatory or recommended final vocabulary item.

**Required correction**  
Retain the individual values as non-normative vocabulary examples. Preserve `REM-04-218`, `REM-04-219`, `REM-04-240`, `REM-04-247` through `REM-04-254`, and `REM-04-260` through `REM-04-265` at their source-supported strength.

---

## REM-04R-F06 — Concrete capability, condition and inheritance examples were promoted into protocol requirements

**Affected requirements**  
`REM-04-299` through `REM-04-304`; `REM-04-311` through `REM-04-317`; `REM-04-319` through `REM-04-321`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction; strength inflation.

**Review finding**  
Sections 23 through 25 use examples to illustrate one-time capabilities, grant conditions and non-inheritance. The extraction makes each example independently normative, including `MUST NOT` rules derived from examples beneath a general `SHOULD NOT` non-inheritance rule.

**Required correction**  
Reclassify the example-specific entries as non-normative. Preserve the general one-time-capability preference, grant-condition support and `REM-04-318` non-inheritance recommendation.

---

## REM-04R-F07 — Consent-interface example content was promoted into separate recommendations

**Affected requirements**  
`REM-04-338`, `REM-04-339`

**Severity**  
Low to Moderate

**Defect classification**  
Example decomposition.

**Review finding**  
Section 26 requires the interface to show specified information and recommends concrete consequences rather than vague legalistic descriptions. The example sentence is illustrative. Its positive and negative clauses should not become additional catalogue candidates.

**Required correction**  
Retain these entries as non-normative examples supporting `REM-04-337`.

---

## REM-04R-F08 — Capability-token use cases and concrete bounds were promoted into selected requirements

**Affected requirements**  
`REM-04-400` through `REM-04-408`

**Severity**  
Moderate

**Defect classification**  
Example and descriptive-use-case over-extraction.

**Review finding**  
Section 32 defines capability authority over a specific object or operation. It then supplies a time-bounded example, a contrasting broad example and a list of areas where capability tokens “may be useful”. The extraction turns those illustrations and use cases into separate `MAY` and `SHOULD` requirements.

**Required correction**  
Keep the source-supported general capability-token definition. Reclassify the concrete object, operation, time and use-case entries as non-normative examples unless their obligation is independently sourced elsewhere.

---

## REM-04R-F09 — Installation, background-access and interaction-mode examples were promoted

**Affected requirements**  
`REM-04-420` through `REM-04-424`; `REM-04-432` through `REM-04-436`; `REM-04-444`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction.

**Review finding**  
Sections 34 through 36 use examples to illustrate installation types, background tasks and a user-present-only condition. The general distinctions and declaration requirements are independently present in `REM-04-419`, `REM-04-425` through `REM-04-431`, `REM-04-437` through `REM-04-443` and `REM-04-445`.

**Required correction**  
Reclassify the affected example-specific entries as non-normative and do not select physical installation categories or an `interactionMode` field.

---

## REM-04R-F10 — Revocation-reason examples were promoted into a recommended vocabulary

**Affected requirements**  
`REM-04-486` through `REM-04-493`

**Severity**  
Moderate

**Defect classification**  
Premature vocabulary selection.

**Review finding**  
Section 40 introduces the reason list as possible reasons. The extraction converts each possible value into a `SHOULD support` requirement.

**Required correction**  
Retain the values as non-normative vocabulary examples. Preserve the general Revocation Record definition and disclosure-risk qualification without selecting a final reason vocabulary.

---

## REM-04R-F11 — Record-survival examples were promoted into separate mandatory obligations

**Affected requirements**  
`REM-04-508` through `REM-04-511`; `REM-04-515`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction.

**Review finding**  
Sections 42 and 43 use posts, projects, comments, archives and a before/after action set to illustrate the general rules. The general non-deletion, replaceability and grant-narrowing semantics are independently represented.

**Required correction**  
Reclassify the concrete examples as non-normative. Do not turn example record types or an example scope reduction into additional mandatory semantics.

---

## REM-04R-F12 — Example service actors, delegated authorities and standing policies were promoted

**Affected requirements**  
`REM-04-655` through `REM-04-659`; `REM-04-679` through `REM-04-683`; `REM-04-702` through `REM-04-706`

**Severity**  
Moderate

**Defect classification**  
Example over-extraction.

**Review finding**  
Sections 57, 59 and 62 explicitly label these lists as examples or use “such as”. The extraction turns each example into a separate application-actor, delegated-authority or standing-policy requirement.

**Required correction**  
Reclassify the individual examples as non-normative. Preserve the general service-to-service, delegated-consent and standing-policy requirements and their safeguards.

---

## REM-04R-F13 — Compliance-scenario steps were strengthened beyond the source-level test

**Affected requirements**  
`REM-04-771` through `REM-04-792`

**Severity**  
Moderate

**Defect classification**  
Normative-strength inflation in scenario decomposition.

**Review finding**  
Section 67 introduces the complete compliance scenario with “A basic application implementation should pass the following test.” `REM-04-770` correctly preserves `SHOULD`, but the decomposed scenario steps are written as `MUST` or `MUST NOT`.

Many of the same principles are mandatory elsewhere, especially in Sections 41, 42, 44, 53 and 66. That independent support does not change the strength of entries traced only to the Section 67 scenario.

**Required correction**  
Normalise the scenario entries to `SHOULD` or `SHOULD NOT`, or add the independent mandatory source citation wherever `MUST` is retained. The scenario itself must remain a recommendation-level end-to-end test.

---

# 5. Items reviewed and accepted

The following patterns are not defects:

1. Compound normative lists are decomposed into individually traceable requirements where the parent strength is preserved.
2. Repetition across operational rules, invariants and provisional decisions is source-authored and may later be consolidated through multi-source catalogue traceability.
3. Application Manifest contents in Section 6 are introduced by “It should contain”; their `SHOULD` extraction is not based solely on the following JSON example.
4. Resource and action distinctions in Sections 12 and 13 are part of the model vocabulary and are not merely example JSON fields.
5. The extraction generally preserves the distinction between identity ownership, delegated authority, tokens, grants, installations and applications.
6. Provider-built clients remain subject to the application model, and application-created records remain independent of application availability or revocation.
7. Section 66 invariants are correctly treated as mandatory because the source states that they must always remain true.

---

# 6. Omission audit

No material omission was identified within Sections 1 through 67. The blocking omission is the complete absence of Sections 68 through 70.

The covered concepts include application identity, controllers, manifests, verification, requests, grants, scopes, purpose, retention, onward sharing, AI use, consent, tokens, delegated keys, installations, background access, revocation, auditability, application replacement, provider migration, service actors, indexing, delegated consent, organisational approval, policy enforcement, operations, invariants and the compliance scenario.

---

# 7. Duplication and terminology audit

No numbering collision was identified. Repeated principles generally reflect deliberate source restatement and should be consolidated later through traceability rather than deleted automatically.

Terminology is generally consistent in its use of Application Identity, Application Manifest, Permission Request, Permission Grant, Consent Receipt, Access Token, capability token, delegated key, Relay Identity and Relay Repository.

The principal terminology risk is status semantics: illustrative, open, provisional and normative material must remain visibly distinct.

---

# 8. Severity summary

| Severity | Findings | Count |
|---|---|---:|
| High | F01, F04 | 2 |
| Moderate | F02, F03, F05, F06, F08, F09, F10, F11, F12, F13 | 10 |
| Low–Moderate | F07 | 1 |
| Numbering defects | None | 0 |

Total recorded findings: **13**.

---

# 9. Required remediation set

Before catalogue generation:

1. add a sequential REM-04 part for Sections 68–70;
2. preserve the Section 68 questions as non-normative open design issues;
3. preserve every Section 69 assumption as explicitly provisional v0.1 material;
4. decompose the Section 70 core principle without importing the following Relationship Model scope as a normative requirement;
5. reclassify the example-only entries identified in F02 through F12 as non-normative model examples;
6. normalise Section 67 scenario strength as required by F13;
7. verify complete traceability, numbering continuity and uniqueness after remediation.

No broad rewrite of the source model is required.

---

# 10. Final review verdict

## Verdict: **Remediation required before catalogue generation**

REM-04 is continuous and substantively detailed through `REM-04-792`, but it stops three source sections early and contains repeated normative promotion of illustrative content.

The extraction must be remediated before EA-05-04 begins. The open design questions must remain unresolved, provisional decisions must remain provisional, examples must not select final schemas or vocabularies, and the Section 67 test must retain source-level strength.

---

# 11. Final editorial QA

This review has been checked for:

- coverage of all existing fourteen REM-04 parts;
- confirmation of the existing continuous range `REM-04-001` through `REM-04-792`;
- explicit identification of missing Sections 68–70;
- evidence-based findings tied to source wording;
- separation of extraction defects from accepted decomposition;
- preservation of unresolved questions as unresolved;
- preservation of provisional decisions as provisional;
- no invented design resolution;
- a clear catalogue-readiness verdict.
