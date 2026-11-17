# EA-05R-03 — Record Requirements Catalogue Review

**Editorial Programme:** EA-05R — Requirements Catalogue Review

**Subsystem:** Record

**Review Target:** EA-05-03 Parts 1–45

**Status:** Review Complete — Remediation Required

---

# 1. Purpose

This review evaluates the complete EA-05-03 Record Requirements Catalogue for source coverage, REM traceability, identifier continuity, normative-strength preservation, requirement structure, terminology, duplication, invariant linkage, treatment of non-normative material and readiness for canonical assembly.

The review introduces no protocol behaviour.

---

# 2. Authoritative review corpus

The review used:

- `design-notes/03-record-model.md`;
- `rem/REM-03 Part 1` through `rem/REM-03 Part 10`;
- `rem/REM-03R-01 — Record Requirement Extraction Review.md`;
- `rem/REM-03R-02 — Record Requirement Remediation Verification.md`;
- `editorial/EA-03 Protocol Invariants.md`;
- `editorial/EA-04 Canonical Terminology Map.md`; and
- `editorial/EA-05-03 Part 1` through `editorial/EA-05-03 Part 45`.

The authoritative design source remains `design-notes/03-record-model.md`.

---

# 3. Review controls and results

| Control | Result | Evidence |
|---|---|---|
| Source-section coverage | Pass | Sections 1–48 are represented across Parts 1–45 |
| REM coverage | Pass | REM-03-001 through REM-03-483 are each accounted for exactly once in coverage tables |
| REL-REC continuity | Pass | REL-REC-001 through REL-REC-313 are continuous and unique |
| Required requirement fields | Pass | Every generated requirement contains title, level, normative keyword, statement, rationale, source and related-invariant treatment |
| Normative keyword presence | Pass | Every catalogue requirement declares one recognised normative keyword and uses it in its statement |
| Non-normative treatment | Pass | Verified examples, open questions and specification-status entries are excluded where required by REM-03R-02 |
| Duplicate statements | Pass | No identical normative statement appears under more than one REL-REC identifier |
| Later-section leakage | Pass | No requirement was found sourced to a section later than its catalogue part scope |
| Canonical terminology | Pass with note | No deprecated capitalised protocol term from EA-04 was adopted as a replacement definition |
| Provisional-status preservation | Pass | All 17 Section 47 requirements remain marked PROVISIONAL v0.1 |
| Open-question preservation | Pass | REM-03-456 through REM-03-465 remain non-normative and generate no REL-REC identifiers |
| Related-invariant linkage | Remediation required | All 174 requirements in Parts 23–45 currently state “None identified”, including requirements with direct EA-03 relationships |
| Statement keyword formatting | Remediation required | 166 statements in Parts 23–44 do not bold the operative normative keyword consistently with Parts 1–22 |

---

# 4. Findings

## EA-05R-03-F01 — Incomplete related-invariant cross-check

**Severity:** Medium

**Affected scope:** EA-05-03 Parts 23–45; REL-REC-140 through REL-REC-313

Every generated requirement in Parts 23–45 currently records `None identified.` under Related Invariants. The uniform result is not credible as a completed EA-03 cross-check. Direct relationships exist at minimum for stable identifiers, repository acceptance, authority, portability, preservation of unknown valid information, historical integrity, rights and ownership distinctions, migration, compliance claims and the source-defined Record invariants in Section 44.

### Required remediation

- Review REL-REC-140 through REL-REC-313 against EA-03.
- Add only genuinely applicable CI or AI references.
- Retain `None identified.` where no direct invariant relationship exists.
- Do not create new invariant identifiers or broaden requirement statements.

---

## EA-05R-03-F02 — Inconsistent normative-keyword emphasis

**Severity:** Low

**Affected scope:** 166 statements across EA-05-03 Parts 23–44

The requirements declare the correct normative keyword, but most statements generated in Parts 23–44 leave that keyword unbolded. Earlier catalogue parts consistently bold the operative keyword within the statement.

### Required remediation

- Bold the operative `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT` or `MAY` in each affected statement.
- Do not change wording, strength or qualifications.

---

# 5. Non-defect review notes

## 5.1 Section 46

REM-03-456 through REM-03-465 are intentionally unresolved and non-normative. Their exclusion from catalogue requirements is correct. They require a later founder decision process but do not constitute an EA-05-03 extraction defect.

## 5.2 Section 47

REL-REC-295 through REL-REC-311 correctly retain **PROVISIONAL v0.1** status. The catalogue may complete editorial review with those markers intact, but canonical adoption requires the provisional decisions to be confirmed, amended or explicitly carried forward as provisional.

## 5.3 Compound source effects

The catalogue decomposes source entries where distinct positive and prohibitory effects require separate normative keywords. Consolidated list requirements retain compatible source effects and individual REM traceability.

---

# 6. Review verdict

EA-05-03 is complete in source coverage, REM accounting and identifier continuity, but it is not yet ready for canonical assembly.

The catalogue must first resolve EA-05R-03-F01 and EA-05R-03-F02 and then undergo a focused remediation verification.

Following successful verification:

1. EA-05R-03 may be marked complete;
2. Section 46 founder decisions and Section 47 provisional decisions may be processed;
3. the approved parts may be assembled into the canonical Record Requirements Catalogue; and
4. `editorial/MASTER_INDEX.md` may be updated.

---

# 7. Remediation verification checklist

- [ ] Every requirement in Parts 23–45 has been cross-checked against EA-03.
- [ ] Applicable CI and AI references have been added without inventing relationships.
- [ ] Legitimate `None identified.` entries remain explicit.
- [ ] All 166 affected statements use established bold normative-keyword formatting.
- [ ] No requirement statement or normative strength changed during formatting remediation.
- [ ] REL-REC-001 through REL-REC-313 remain continuous and unique.
- [ ] REM-03-001 through REM-03-483 remain completely and uniquely accounted for.
- [ ] Section 46 entries remain non-normative.
- [ ] Section 47 requirements remain PROVISIONAL v0.1.

---

# Document status

**Review Complete — Remediation Required**
