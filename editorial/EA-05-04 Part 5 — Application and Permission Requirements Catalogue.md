# EA-05-04 — Application and Permission Requirements Catalogue

## Part 5 — AI Declarations, Grant Duration, One-Time Authority and Inheritance

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines structured AI-use disclosure, Permission Grant duration models, one-time capability lifecycle, conditional grants and explicit permission-inheritance boundaries.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 21–25 and REM-04 entries `REM-04-274` through `REM-04-322`.

Verified non-normative examples generate no catalogue requirements:

- `REM-04-275`–`REM-04-281`, illustrative AI-declaration fields;
- `REM-04-299`–`REM-04-304`, example one-time capability uses;
- `REM-04-311`–`REM-04-317`, example grant conditions and JSON fields; and
- `REM-04-319`–`REM-04-321`, permission-inheritance examples.

No example field name, structure, threshold, condition type or one-time operation is selected as mandatory.

Section 26 and later are deferred.

---

# 3. Requirements

---

## REL-APP-100

### Title

Structured AI-Use Declaration

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An AI-related Permission Request **SHOULD** include a structured declaration of the AI activities for which access is requested.

### Rationale

Structured disclosure permits distinct AI activities to be reviewed without making the illustrative Section 21 fields mandatory.

### Source

- REM-04-274
- `design-notes/04-application-and-permission-model.md`, Section 21

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-101

### Title

AI Consent Explanation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The consent interface for AI-related access **SHOULD** explain which data will be used, which AI activities will occur, where processing occurs, whether a third-party model provider is involved, whether data is retained, and whether humans may review inputs or outputs.

### Rationale

These disclosures expose the data, processing, location, external actors, persistence and human-access consequences needed for informed consent.

### Source

- REM-04-282
- REM-04-283
- REM-04-284
- REM-04-285
- REM-04-286
- REM-04-287
- `design-notes/04-application-and-permission-model.md`, Section 21

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-102

### Title

Explicit Grant Validity Conditions

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Grant model **MUST** support grants with explicitly defined validity conditions.

### Rationale

An implementation must be able to determine when authority begins, continues and ceases rather than treating every grant as indefinite.

### Source

- REM-04-288
- `design-notes/04-application-and-permission-model.md`, Section 22

### Related Invariants

- CI-06

---

## REL-APP-103

### Title

Supported Grant Duration Models

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Permission Grant **MAY** be limited to one operation, one session, a specified expiration time, a defined duration, the period until revocation, the validity of a defined relationship, or the validity of a specified credential.

### Rationale

The source permits multiple duration and dependency models without requiring one universal model.

### Source

- REM-04-289
- REM-04-290
- REM-04-291
- REM-04-292
- REM-04-293
- REM-04-294
- REM-04-295
- `design-notes/04-application-and-permission-model.md`, Section 22

### Related Invariants

- CI-06

---

## REL-APP-104

### Title

Reviewability of Indefinite Grants

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An indefinite Permission Grant **SHOULD** remain reviewable by the person or authorised controller.

### Rationale

Indefinite duration must not remove visibility into continuing authority.

### Source

- REM-04-296
- `design-notes/04-application-and-permission-model.md`, Section 22

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-105

### Title

Revocability of Indefinite Grants

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An indefinite Permission Grant **SHOULD** remain revocable.

### Rationale

Until-revoked or indefinite authority does not become irrevocable authority.

### Source

- REM-04-297
- `design-notes/04-application-and-permission-model.md`, Section 22

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-106

### Title

One-Time Capability Preference

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An operation requiring only isolated authority **SHOULD** use a one-time capability rather than a long-lived Permission Grant.

### Rationale

One-time authority reduces the period and breadth of exposure for an isolated operation.

### Source

- REM-04-298
- `design-notes/04-application-and-permission-model.md`, Section 23

### Related Invariants

- CI-06

---

## REL-APP-107

### Title

One-Time Capability Invalidation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A one-time capability **MUST** become invalid after successful use, expiration, revocation, reaching its defined failure threshold, or a relevant repository-state change that makes the authorised operation stale or unsafe.

### Rationale

Invalidation prevents replay, use after withdrawal or expiry, brute-force reuse and execution against obsolete repository state.

### Source

- REM-04-305
- REM-04-306
- REM-04-307
- REM-04-308
- REM-04-309
- `design-notes/04-application-and-permission-model.md`, Section 23

### Related Invariants

- CI-06
- CI-07

---

## REL-APP-108

### Title

Conditional Permission Grants

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Permission Grant **MAY** include explicit conditions that further restrict when or how an approved capability may be exercised.

### Rationale

Conditions narrow already approved authority and must not silently broaden the underlying grant.

### Source

- REM-04-310
- `design-notes/04-application-and-permission-model.md`, Section 24

### Related Invariants

- CI-06

---

## REL-APP-109

### Title

No Implicit Permission Inheritance

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Permission **SHOULD NOT** be inherited implicitly solely because records, identities, repositories or collections are related.

### Rationale

A relationship or nesting structure is not itself an authorisation grant.

### Source

- REM-04-318
- `design-notes/04-application-and-permission-model.md`, Section 25

### Related Invariants

- CI-06

---

## REL-APP-110

### Title

Explicit Permission-Inheritance Rules

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Any permission-inheritance rule **MUST** be explicitly defined in the applicable schema or Permission Grant.

### Rationale

Explicit rules prevent applications and providers from inferring authority from user-interface grouping, nesting or relationship links.

### Source

- REM-04-322
- `design-notes/04-application-and-permission-model.md`, Section 25

### Related Invariants

- CI-06
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-274` | Direct | `REL-APP-100` |
| `REM-04-275`–`REM-04-281` | Non-normative example fields | Excluded |
| `REM-04-282`–`REM-04-287` | Consolidated consent disclosure set | `REL-APP-101` |
| `REM-04-288` | Direct | `REL-APP-102` |
| `REM-04-289`–`REM-04-295` | Consolidated permitted duration models | `REL-APP-103` |
| `REM-04-296`–`REM-04-298` | Direct | `REL-APP-104`–`REL-APP-106` |
| `REM-04-299`–`REM-04-304` | Non-normative operation examples | Excluded |
| `REM-04-305`–`REM-04-309` | Consolidated invalidation events | `REL-APP-107` |
| `REM-04-310` | Direct | `REL-APP-108` |
| `REM-04-311`–`REM-04-317` | Non-normative condition examples | Excluded |
| `REM-04-318` | Direct | `REL-APP-109` |
| `REM-04-319`–`REM-04-321` | Non-normative inheritance examples | Excluded |
| `REM-04-322` | Direct | `REL-APP-110` |

Every normative entry is represented and each non-normative example range is explicitly accounted for.

---

# 5. Editorial QA record

- Source scope is limited to Sections 21–25 and `REM-04-274` through `REM-04-322`.
- Previous endpoint: `REL-APP-099`.
- First identifier: `REL-APP-100`.
- Final identifier: `REL-APP-110`.
- Total requirements: 11.
- Numbering is continuous and unique.
- AI-request declaration and consent explanation retain `SHOULD` strength.
- Duration alternatives retain `MAY` strength.
- Indefinite grants remain reviewable and revocable recommendations.
- One-time invalidation events retain `MUST` strength.
- Conditions narrow authority and permission inheritance remains explicit.
- No illustrative field or example operation became mandatory.
- No Section 26 or later material is imported.

---

# 6. Part conclusion

Part 5 establishes structured AI disclosure, grant-validity options, one-time authority lifecycle and explicit permission-inheritance rules.

Part 6 should begin with source Section 26 and `REM-04-323`.
