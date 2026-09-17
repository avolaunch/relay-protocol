# EA-05-05 — Relationship Requirements Catalogue

## Part 27 — Core Relationship Principle and Catalogue Closure

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft — Catalogue Complete

---

# 1. Purpose

This final part completes the canonical Relationship Requirements Catalogue derived from REM-05.

It converts the Relationship Model's concluding core principle into the final canonical Relationship requirement, explicitly accounts for the model's non-normative hand-off to the Migration and Portability Model, and records end-to-end closure of the 27-part EA-05-05 catalogue.

The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Section 60 and the final REM-05 entries:

- `REM-05-672` — normative Core Relationship Principle;
- `REM-05-673` — non-normative Migration and Portability Model hand-off.

It continues normative catalogue numbering from `REL-REL-432` and closes REM-05 coverage at `REM-05-673`.

---

# 3. Requirements

---

## REL-REL-432

### Title

Relationships Exist Between Persistent Identities Rather Than Applications

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Relationship Model **MUST** treat a relationship as existing between persistent identities rather than as an object owned by or inherently contained within the application that introduced, created, displayed or facilitated that relationship.

### Rationale

This is the Relationship Model's concluding core principle and summarises the portability objective expressed throughout the model. Applications may facilitate creation, presentation and authorised use of relationship records, but application participation does not make the application the canonical owner of the relationship. Anchoring relationship state to persistent identities is what permits that state to survive application replacement and remain part of the user's portable Relay graph.

### Source

- REM-05-672
- `design-notes/05-relationship-model.md`, Section 60

### Related Invariants

- CI-01
- CI-02
- CI-03
- CI-04
- CI-05

---

# 4. Non-Normative Model-Boundary Accounting

## REM-05-673 — Migration and Portability Model hand-off

`REM-05-673` is explicitly a **non-normative model-boundary note**.

Section 60 identifies the Relay Migration and Portability Model as the next core object and describes its subject matter as movement of identities, repositories, records, blobs, grants and relationships between providers without breaking continuity.

### Catalogue treatment

- `REM-05-673` generates **no `REL-REL` identifier**.
- It creates **no normative Relationship Model requirement**.
- It does **not** import Migration and Portability requirements into EA-05-05.
- Requirements governing provider migration beyond those already normatively defined by the Relationship Model must be derived from the Migration and Portability Model's own authoritative design source.

This treatment preserves the source-model boundary while retaining complete REM-05 traceability.

---

# 5. Final Consolidation and Traceability Record

No consolidation is performed in Part 27.

- `REM-05-672` maps one-to-one to `REL-REL-432`.
- `REM-05-673` is explicitly accounted for as non-normative and produces no catalogue identifier.

The complete REM-05 extraction range `REM-05-001` through `REM-05-673` is now accounted for across EA-05-05 Parts 1–27.

## Special-status REM accounting

The final catalogue preserves the verified remediation boundaries:

| REM range | Status | Catalogue treatment |
|---|---|---|
| `REM-05-291`–`REM-05-295` | Non-normative model examples | Explicitly accounted for in Part 11; no `REL-REL` identifiers |
| `REM-05-636`–`REM-05-645` | Non-normative Open Design Issues | Explicitly accounted for in Part 26; unresolved; no `REL-REL` identifiers |
| `REM-05-646`–`REM-05-671` | **PROVISIONAL v0.1** | Represented in Part 26 as `REL-REL-416`–`REL-REL-431`, with provisional status visibly preserved |
| `REM-05-673` | Non-normative model-boundary note | Explicitly accounted for in Part 27; no `REL-REL` identifier |

No entry in a non-normative range has been converted into an ordinary normative catalogue requirement.

---

# 6. End-to-End Catalogue Closure QA

## 6.1 REM coverage closure

The catalogue begins at `REM-05-001` in Part 1 and ends at `REM-05-673` in Part 27.

The part boundaries form a continuous source sequence:

- Parts 1–4: `REM-05-001`–`REM-05-131`;
- Parts 5–8: `REM-05-132`–`REM-05-218`;
- Parts 9–12: `REM-05-219`–`REM-05-342`;
- Parts 13–16: `REM-05-343`–`REM-05-457`;
- Parts 17–20: `REM-05-458`–`REM-05-542`;
- Parts 21–23: `REM-05-543`–`REM-05-600`;
- Parts 24–25: `REM-05-601`–`REM-05-635`;
- Part 26: `REM-05-636`–`REM-05-671`;
- Part 27: `REM-05-672`–`REM-05-673`.

No REM range is left between catalogue parts. Non-normative entries remain part of coverage accounting even though they do not consume `REL-REL` identifiers.

## 6.2 Catalogue numbering closure

The first canonical Relationship requirement is `REL-REL-001` in Part 1.

The final canonical Relationship requirement is `REL-REL-432` in Part 27.

Across the 27 parts, catalogue numbering proceeds continuously from `REL-REL-001` through `REL-REL-432`. The deliberate absence of catalogue identifiers for non-normative REM entries does not create gaps in `REL-REL` numbering because those entries consume no catalogue identifier.

**Final canonical Relationship requirement count: 432.**

## 6.3 Non-normative closure

All explicitly non-normative REM entries identified by the verified remediation review are accounted for without ordinary normative catalogue creation:

- five model examples: `REM-05-291`–`REM-05-295`;
- ten Open Design Issues: `REM-05-636`–`REM-05-645`;
- one model-boundary hand-off: `REM-05-673`.

**Total explicitly non-normative REM entries excluded from normative catalogue creation: 16.**

The Section 58 Open Design Issues remain unresolved. Catalogue generation has not selected among candidate architectures or silently transformed an open question into a protocol decision.

## 6.4 PROVISIONAL v0.1 closure

All 26 provisional extraction entries `REM-05-646` through `REM-05-671` are represented in Part 26.

They consolidate into 16 catalogue requirements, `REL-REL-416` through `REL-REL-431`.

Every such catalogue requirement remains visibly marked **PROVISIONAL v0.1**. Its normative keyword expresses the strength of the current working baseline only and does not convert the provisional decision into a final immutable protocol commitment.

## 6.5 Remediation-strength preservation

The catalogue preserves the verified REM-05 remediation decisions, including:

- `REM-05-291`–`REM-05-295` as non-normative examples;
- `REM-05-506` as descriptive `MAY` treatment;
- `REM-05-508` at `SHOULD` strength;
- `REM-05-509` at `SHOULD NOT` strength;
- `REM-05-515` and `REM-05-516` at `MAY` strength;
- Section 57 compliance-scenario requirements at scenario-level `SHOULD` / `SHOULD NOT` strength rather than invariant-level promotion;
- `REM-05-636`–`REM-05-645` as unresolved non-normative Open Design Issues;
- `REM-05-646`–`REM-05-671` as explicitly **PROVISIONAL v0.1**;
- `REM-05-673` as a non-normative model-boundary note.

No closure treatment silently strengthens these remediated statuses.

## 6.6 Consolidation integrity

Consolidations throughout EA-05-05 are bounded to source entries that form one source-defined semantic unit, option set, metadata structure, example vocabulary or directly equivalent requirement.

Each catalogue part retains all contributing REM identifiers in its Source and consolidation records. Requirements concerning the same broad topic were not consolidated merely for topical similarity where they remained independently meaningful or testable.

## 6.7 Cross-part continuity

The 27-part catalogue preserves sequential continuity in both dimensions:

- source traceability: `REM-05-001` → `REM-05-673`;
- canonical numbering: `REL-REL-001` → `REL-REL-432`.

Part 27 therefore closes the REM-05 Relationship Requirements Catalogue without requiring modification of the verified extraction, extraction-review, remediation-verification or earlier catalogue-part documents.

### Closure result

**PASS — EA-05-05 Relationship Requirements Catalogue generation is complete for REM-05.**

The catalogue contains 432 canonical Relationship requirements, explicitly accounts for every REM-05 entry through `REM-05-673`, preserves all identified non-normative and provisional boundaries, and is ready for the appropriate post-catalogue editorial step.

---

# Editorial Review Notes

The final source principle states the architectural objective that the preceding catalogue makes concrete: a Relay relationship belongs to the persistent identity layer, not to the application that happens to introduce or display it.

EA-05-05 should now be treated as catalogue-complete for REM-05. The next editorial task should not create another Relationship catalogue part. It should perform post-catalogue housekeeping and programme-state reconciliation, including updating the authoritative editorial index to reflect completion of REM-05 extraction, review, remediation verification and all 27 EA-05-05 catalogue parts before the programme proceeds to the next unfinished catalogue or cross-catalogue phase.