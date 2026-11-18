# REM-04R-02 — Application and Permission Requirement Extraction Remediation Verification

## Document status

**Canonical post-remediation verification review**

This document verifies the remediation performed after `REM-04R-01 — Application and Permission Requirement Extraction Review.md`.

Authoritative source:

- `design-notes/04-application-and-permission-model.md`

Remediated scope:

- REM-04 Parts 1–14, where affected by REM-04R-01 findings
- `REM-04 Part 15 — Application and Permission Requirement Extraction Matrix (Sections 68–70).md`

The purpose of this review is verification, not redesign. It does not resolve the Section 68 questions or remove the provisional status of Section 69.

---

# 1. Verification objectives

This review verifies that:

1. every finding `REM-04R-F01` through `REM-04R-F13` is resolved;
2. all seventy source sections are covered;
3. identifiers are continuous and unique from `REM-04-001` through `REM-04-831`;
4. example-only material is explicitly non-normative;
5. example JSON selects no mandatory field name or physical structure;
6. Section 67 retains `SHOULD`-level scenario strength;
7. all twelve Section 68 questions remain unresolved;
8. all sixteen Section 69 bullets are represented with explicit provisional status;
9. Section 70’s core principle is extracted without promoting its model-boundary sentence;
10. every remediated entry remains traceable to the authoritative design note.

---

# 2. Verification summary

| Finding | Affected scope | Verification result |
|---|---|---|
| REM-04R-F01 | Sections 68–70 | Resolved |
| REM-04R-F02 | REM-04-006 | Resolved |
| REM-04R-F03 | REM-04-091–097, 104–110 | Resolved |
| REM-04R-F04 | REM-04-139–146, 275–281, 481–485, 570–573 | Resolved |
| REM-04R-F05 | REM-04-220–237, 241–246, 255–259 | Resolved |
| REM-04R-F06 | REM-04-299–304, 311–317, 319–321 | Resolved |
| REM-04R-F07 | REM-04-338–339 | Resolved |
| REM-04R-F08 | REM-04-400–408 | Resolved |
| REM-04R-F09 | REM-04-420–424, 432–436, 444 | Resolved |
| REM-04R-F10 | REM-04-486–493 | Resolved |
| REM-04R-F11 | REM-04-508–511, 515 | Resolved |
| REM-04R-F12 | REM-04-655–659, 679–683, 702–706 | Resolved |
| REM-04R-F13 | REM-04-771–792 | Resolved |

**Result:** all thirteen findings are resolved. No new blocking extraction defect was identified.

---

# 3. Finding-by-finding verification

## REM-04R-F01 — Missing Sections 68–70

Part 15 now covers Sections 68–70 and continues directly from `REM-04-792`.

- `REM-04-793` through `REM-04-804` preserve all twelve Section 68 questions as non-normative open design issues.
- `REM-04-805` through `REM-04-827` represent all sixteen Section 69 provisional bullets. Compound bullets are decomposed only where they contain independently testable obligations.
- `REM-04-828` through `REM-04-830` extract temporary authority, limited authority and non-ownership from the Section 70 core principle.
- `REM-04-831` preserves the Relationship Model hand-off as a non-normative model-boundary note.

**Verification result:** **Resolved.**

## REM-04R-F02 through F12 — Illustrative-material promotion

All 134 entries identified across F02 through F12 are now explicitly labelled **Non-normative model example**.

Their classifications state that they are illustrative, non-normative and excluded from catalogue generation. Their Notes state that any future normative use requires independent support from the authoritative source.

The remediation therefore preserves traceability without selecting:

- application product categories;
- a closed material-manifest-change list;
- verification-status values;
- Permission Grant, AI-use, Revocation Record or attribution fields;
- purpose, retention, onward-sharing or revocation-reason vocabularies;
- one-time capability types;
- grant conditions;
- inheritance examples;
- consent-example wording;
- capability-token use cases;
- installation categories;
- background-task categories;
- an `interactionMode` field;
- record-type-specific revocation outcomes;
- service-actor categories;
- delegated-consent categories;
- standing-policy examples.

General requirements independently established by the source remain normative. The remediation does not weaken the source-level requirements for grants, declarations, consent, revocation, attribution, service actors, delegated consent or standing policies.

**Verification result:** **Resolved.**

## REM-04R-F13 — Compliance-scenario strength

`REM-04-770` continues to state that a basic implementation `SHOULD` pass the complete scenario.

`REM-04-771` through `REM-04-792` now use `SHOULD` or `SHOULD NOT`. No scenario entry derives `MUST` strength solely from Section 67.

Mandatory equivalents elsewhere in the source remain mandatory in their independently sourced entries, particularly the Section 66 invariants. The remediation changes only the strength of the Section 67 scenario decomposition.

**Verification result:** **Resolved.**

---

# 4. Coverage and numbering verification

| Part | Source sections | Identifier range |
|---|---:|---:|
| Part 1 | 1–5 | REM-04-001–070 |
| Part 2 | 6–10 | REM-04-071–146 |
| Part 3 | 11–15 | REM-04-147–211 |
| Part 4 | 16–20 | REM-04-212–269 |
| Part 5 | 21–25 | REM-04-270–322 |
| Part 6 | 26–30 | REM-04-323–390 |
| Part 7 | 31–35 | REM-04-391–439 |
| Part 8 | 36–40 | REM-04-440–494 |
| Part 9 | 41–45 | REM-04-495–538 |
| Part 10 | 46–50 | REM-04-539–595 |
| Part 11 | 51–55 | REM-04-596–647 |
| Part 12 | 56–60 | REM-04-648–693 |
| Part 13 | 61–65 | REM-04-694–747 |
| Part 14 | 66–67 | REM-04-748–792 |
| Part 15 | 68–70 | REM-04-793–831 |

The full sequence contains 831 identifiers. It is continuous and unique, with no gap, collision or reassignment.

Retaining identifiers for examples, open issues and the model-boundary note preserves traceability. It does not make those entries normative.

---

# 5. Section 68 verification

All twelve open questions are present:

1. authorisation standard;
2. grant storage;
3. purpose enforcement;
4. field-level access;
5. delegated keys;
6. cross-provider grants;
7. application trust registry;
8. material manifest change;
9. AI vocabulary;
10. legal terms;
11. public data access;
12. installation identity.

No entry selects a candidate answer. These entries must not enter the Requirements Catalogue as settled protocol requirements unless an authoritative design decision resolves them.

---

# 6. Section 69 verification

All sixteen source bullets are represented. Decomposition produces 23 provisional entries because four bullets contain independently testable paired or grouped obligations:

- signed and versioned manifests;
- explicit and revocable grants;
- four separate declaration categories;
- inspection and revocation;
- grant preservation and provider-specific token replacement during migration.

Every resulting entry begins with **PROVISIONAL v0.1**. The extraction preserves:

- `MUST` or `SHOULD` where the working baseline establishes a present v0.1 expectation;
- the safety qualification “where continuation is safe” for migration grant continuity;
- `MAY` for initially contractual and auditable purpose restrictions;
- preference, rather than an unconditional mandate, for OAuth-compatible practices.

No provisional entry may be flattened into an ordinary final catalogue requirement without visibly retaining its provisional status.

---

# 7. Section 70 verification

The core rule is decomposed into three independently testable requirements:

- temporary application authority;
- limited application authority;
- no application ownership of a person’s digital continuity.

The extraction does not imply that temporary authority must use a particular token lifetime, refresh mechanism or implementation structure.

The final sentence identifying the Relationship Model is retained as `REM-04-831`, an explicitly non-normative boundary note. It creates no Application and Permission requirement and imports no Relationship Model obligation.

---

# 8. Catalogue-treatment verification

The remediated REM-04 contains four distinct statuses.

### Normative extracted requirements

Ordinary entries retain source-derived `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT` or `MAY` semantics.

### Non-normative model examples

The 134 entries remediated under F02 through F12 are excluded from ordinary catalogue requirements.

### Non-normative open design issues

`REM-04-793` through `REM-04-804` remain unresolved and are excluded from ordinary catalogue requirements.

### Provisional v0.1 requirements

`REM-04-805` through `REM-04-827` may enter catalogue work only with explicit provisional status.

`REM-04-831` is a non-normative model-boundary note and is excluded from the catalogue.

---

# 9. Traceability and regression verification

Every remediated entry retains its original Source field or, in Part 15, cites the exact Section 68 question, Section 69 provisional bullet or Section 70 principle.

The remediation is targeted. Unaffected entries retain their identifiers and substantive wording. No source question was answered by inference, no example field became mandatory, and no requirement was imported from the Relationship Model.

The complete extraction remains anchored solely to `design-notes/04-application-and-permission-model.md`.

---

# 10. Final editorial QA

Final QA confirms:

- all thirteen REM-04R-01 findings are resolved;
- Sections 1–70 are fully covered;
- the sequence is continuous and unique through `REM-04-831`;
- 134 example-only entries are explicitly non-normative;
- all twelve open questions remain unresolved;
- all sixteen provisional bullets are represented by 23 explicitly provisional entries;
- Section 67 uses `SHOULD` and `SHOULD NOT` throughout its scenario decomposition;
- Section 70 preserves temporary authority, limited authority and non-ownership;
- the Relationship Model hand-off is non-normative;
- no new blocking extraction defect was identified;
- catalogue generation has not begun in this verification document.

---

# 11. Final verdict

**VERIFIED — REM-04 is ready to proceed to Requirements Catalogue generation.**

All findings `REM-04R-F01` through `REM-04R-F13` are resolved. REM-04 now covers the complete authoritative Application and Permission Model, remains continuous from `REM-04-001` through `REM-04-831`, preserves examples and open issues as non-normative, preserves Section 69 as provisional, and maintains source-level normative strength.
