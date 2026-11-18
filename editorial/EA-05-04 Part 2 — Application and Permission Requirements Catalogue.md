# EA-05-04 — Application and Permission Requirements Catalogue

## Part 2 — Application Manifests, Verification, Permission Requests and Grants

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines Application Manifest integrity and contents, material-change versioning, bounded application verification, complete Permission Request declarations and the foundational semantics of Permission Grants.

This catalogue part is generated from the completed and verified REM-04 extraction series. The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 6–10 and REM-04 entries `REM-04-070` through `REM-04-148`.

The following verified non-normative examples generate no catalogue requirements:

- `REM-04-091` through `REM-04-097`, example material-manifest changes;
- `REM-04-104` through `REM-04-110`, example verification statuses; and
- `REM-04-139` through `REM-04-146`, illustrative Permission Grant fields.

The Section 6 example manifest structure remains non-final and non-exhaustive. No illustrative field name or JSON structure is made mandatory.

Section 11 and later are intentionally deferred.

---

# 3. Requirements

---

## REL-APP-033

### Title

Signed Application Manifest

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Application Manifest **MUST** be signed by an authority valid for the corresponding Application Identity.

### Rationale

A valid signature binds the manifest's declarations to the stable application actor and permits integrity and authority verification.

### Source

- REM-04-070
- REM-04-098
- `design-notes/04-application-and-permission-model.md`, Sections 6 and 7

### Related Invariants

- CI-02
- CI-08

---

## REL-APP-034

### Title

Versioned Application Manifest

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Application Manifest **MUST** be versioned.

### Rationale

Versioning makes application declarations and later material changes traceable over time.

### Source

- REM-04-071
- `design-notes/04-application-and-permission-model.md`, Section 6

### Related Invariants

- CI-10

---

## REL-APP-035

### Title

Application Description

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An Application Manifest **MUST** describe the application associated with its Application Identity.

### Rationale

The manifest must identify the application behaviour and declarations to which consent and policy evaluation apply.

### Source

- REM-04-072
- `design-notes/04-application-and-permission-model.md`, Section 6

### Related Invariants

- CI-08

---

## REL-APP-036

### Title

Recommended Manifest Information

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An Application Manifest **SHOULD** contain the applicable stable Application Identity, user-visible name, controller identity, application type, verified domains, authorised redirect or callback locations, supported protocol versions, requestable scope catalogue, privacy-policy reference, retention practices, AI or model-training declaration, contact details, security-incident contact mechanism, current verification keys, manifest version identifier and verifiable signature or signature reference.

### Rationale

This source-defined information set supports identification, consent presentation, automated policy evaluation, contact, incident response and cryptographic verification without selecting the illustrative JSON structure as final syntax.

### Source

- REM-04-073
- REM-04-074
- REM-04-075
- REM-04-076
- REM-04-077
- REM-04-078
- REM-04-079
- REM-04-080
- REM-04-081
- REM-04-082
- REM-04-083
- REM-04-084
- REM-04-085
- REM-04-086
- REM-04-087
- REM-04-088
- `design-notes/04-application-and-permission-model.md`, Section 6

### Related Invariants

- CI-08
- CI-10
- CI-11

---

## REL-APP-037

### Title

No Finalisation of Illustrative Manifest Structure

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement

Relay v0.1 implementations **MUST NOT** treat the Section 6 example Application Manifest structure as a final or exhaustive wire-format specification.

### Rationale

The example illustrates manifest semantics but does not select final physical field names, syntax or a closed metadata set.

### Source

- REM-04-089
- `design-notes/04-application-and-permission-model.md`, Section 6

### Related Invariants

- CI-12

---

## REL-APP-038

### Title

New Version for Material Manifest Change

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every material change to an Application Manifest **MUST** create a new manifest version.

### Rationale

Material changes must remain distinguishable from the declarations under which existing consent or trust decisions were made.

### Source

- REM-04-090
- `design-notes/04-application-and-permission-model.md`, Section 7

### Related Invariants

- CI-10

---

## REL-APP-039

### Title

Current Manifest Resolution Before Consent

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Relay Provider **MUST** be able to resolve an application's current valid Application Manifest before displaying a Permission Request to a user.

### Rationale

Consent must be based on the current authoritative application declarations rather than an unavailable, stale or invalid manifest.

### Source

- REM-04-099
- `design-notes/04-application-and-permission-model.md`, Section 7

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-040

### Title

Human-Readable Consent Support

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An Application Manifest **MUST** contain sufficient information for a consent interface to explain the application and its request in ordinary language.

### Rationale

A person cannot make an informed authorisation decision from opaque identifiers or machine-only declarations.

### Source

- REM-04-100
- `design-notes/04-application-and-permission-model.md`, Section 7

### Related Invariants

- CI-06

---

## REL-APP-041

### Title

Machine-Readable Policy Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An Application Manifest **MUST** expose relevant declarations in a machine-readable form that supports automated policy evaluation.

### Rationale

Machine-readable declarations permit consistent enforcement of user and provider policies without replacing human-readable consent.

### Source

- REM-04-101
- `design-notes/04-application-and-permission-model.md`, Section 7

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-042

### Title

Automated User-Policy Evaluation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Relay Provider **SHOULD** be capable of evaluating a user's configured policy preferences against machine-readable application declarations.

### Rationale

Automated evaluation can enforce standing preferences consistently while leaving approval requirements and risk controls intact.

### Source

- REM-04-102
- `design-notes/04-application-and-permission-model.md`, Section 7

### Related Invariants

- CI-06

---

## REL-APP-043

### Title

Application Verification Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The Application and Permission Model **MAY** represent an application verification status.

### Rationale

Verification status can communicate specific established facts or completed reviews without becoming a universal trust guarantee.

### Source

- REM-04-103
- `design-notes/04-application-and-permission-model.md`, Section 8

### Related Invariants

- CI-08

---

## REL-APP-044

### Title

No Universal Trust Guarantee from Verification

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application verification status **MUST NOT** be represented as a universal guarantee that the application is trustworthy, secure or compliant in all respects.

### Rationale

Verification establishes only the facts or review outcomes within its defined scope.

### Source

- REM-04-111
- `design-notes/04-application-and-permission-model.md`, Section 8

### Related Invariants

- CI-08
- CI-11

---

## REL-APP-045

### Title

Verification-Fact Representation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application verification status **MAY** indicate established control of a specified domain, established controller identity, completion of a specified security review or acceptance into a defined provider catalogue.

### Rationale

These are bounded facts that a verification status may communicate without selecting a closed status vocabulary.

### Source

- REM-04-112
- REM-04-113
- REM-04-114
- REM-04-115
- `design-notes/04-application-and-permission-model.md`, Section 8

### Related Invariants

- CI-08

---

## REL-APP-046

### Title

Verification Explanation in Consent

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A consent screen **SHOULD** explain the specific fact, review or certification represented by an application's verification status.

### Rationale

Users need the scope of verification to avoid interpreting a badge or status as a broader guarantee.

### Source

- REM-04-116
- `design-notes/04-application-and-permission-model.md`, Section 8

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-047

### Title

Permission Request Representation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Request **MUST** represent an application's proposed access to a specified Relay Identity or Relay Repository.

### Rationale

The request is the explicit proposal from which consent and any resulting grant are derived.

### Source

- REM-04-117
- `design-notes/04-application-and-permission-model.md`, Section 9

### Related Invariants

- CI-06

---

## REL-APP-048

### Title

Permission Request Contents

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Request **MUST** identify the requesting Application Identity, the Relay Identity from whom authority is requested, requested resources, requested actions, proposed duration, declared purposes, proposed retention, onward-sharing status, AI processing, requested model training, interactive or continuous access mode, and any high-authority operations.

### Rationale

These independently reviewable declarations define what the user is being asked to authorise and prevent approval from being inferred for undisclosed resources, uses or risk levels.

### Source

- REM-04-118
- REM-04-119
- REM-04-120
- REM-04-121
- REM-04-122
- REM-04-123
- REM-04-124
- REM-04-125
- REM-04-126
- REM-04-127
- REM-04-128
- REM-04-129
- `design-notes/04-application-and-permission-model.md`, Section 9

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-049

### Title

Permission Grant Issuance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be an authorisation issued by the relevant Relay Identity in response to a Permission Request.

### Rationale

The grant records approved authority and must originate from the identity whose resources or repository are affected.

### Source

- REM-04-130
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-050

### Title

Cryptographically Authorised Permission Grant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be signed or otherwise cryptographically authorised by valid authority for the issuing Relay Identity.

### Rationale

Cryptographic authorisation permits independent verification that the grant was issued by valid identity authority.

### Source

- REM-04-131
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-02
- CI-08

---

## REL-APP-051

### Title

Explicit Permission Grant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** express the granted authority explicitly.

### Rationale

Explicit authority prevents applications and providers from deriving permission from ambiguous context or application possession.

### Source

- REM-04-132
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-06

---

## REL-APP-052

### Title

Limited Permission Grant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be limited to defined resources, actions and applicable conditions.

### Rationale

The grant must bound what an application may access and do rather than confer general repository control.

### Source

- REM-04-133
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-06

---

## REL-APP-053

### Title

Attributable Permission Grant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be attributable to its issuing Relay Identity and receiving Application Identity.

### Rationale

Attribution identifies both the authority that granted access and the application actor permitted to exercise it.

### Source

- REM-04-134
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-08
- CI-10

---

## REL-APP-054

### Title

Inspectable Permission Grant

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be available for inspection by the issuing identity through an authorised interface or service.

### Rationale

Inspection supports informed control, review and revocation of active application authority.

### Source

- REM-04-135
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-055

### Title

Revocable Permission Grant

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be revocable by valid authority for the issuing Relay Identity.

### Rationale

The issuing identity must retain the ability to terminate delegated authority.

### Source

- REM-04-136
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-056

### Title

Risk-Appropriate Temporal Boundary

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** include an appropriate temporal boundary where the nature or risk of the authority calls for time limitation.

### Rationale

Time bounds reduce the persistence of authority where indefinite access would create disproportionate risk.

### Source

- REM-04-137
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-06

---

## REL-APP-057

### Title

Grant No Broader Than Approved Request

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Permission Grant **MUST NOT** authorise resources, actions, purposes, duration or other authority broader than the Permission Request approved by the user.

### Rationale

The grant must faithfully encode the approved request and cannot expand authority during issuance.

### Source

- REM-04-138
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-06

---

## REL-APP-058

### Title

Permission Grant Storage Location

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Permission Grant **MAY** be stored as an authority record in the Relay Repository or in a dedicated authorisation service.

### Rationale

The source permits more than one storage boundary and does not yet require a single physical grant location.

### Source

- REM-04-147
- REM-04-148
- `design-notes/04-application-and-permission-model.md`, Section 10

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-070`, `REM-04-098` | Consolidated equivalent signature rules | `REL-APP-033` |
| `REM-04-071`–`REM-04-072` | Direct | `REL-APP-034`–`REL-APP-035` |
| `REM-04-073`–`REM-04-088` | Consolidated source-defined information set | `REL-APP-036` |
| `REM-04-089`–`REM-04-090` | Direct | `REL-APP-037`–`REL-APP-038` |
| `REM-04-091`–`REM-04-097` | Non-normative examples | Excluded |
| `REM-04-099`–`REM-04-102` | Direct | `REL-APP-039`–`REL-APP-042` |
| `REM-04-103` | Direct | `REL-APP-043` |
| `REM-04-104`–`REM-04-110` | Non-normative examples | Excluded |
| `REM-04-111` | Direct | `REL-APP-044` |
| `REM-04-112`–`REM-04-115` | Consolidated bounded verification facts | `REL-APP-045` |
| `REM-04-116`–`REM-04-117` | Direct | `REL-APP-046`–`REL-APP-047` |
| `REM-04-118`–`REM-04-129` | Consolidated Permission Request contents | `REL-APP-048` |
| `REM-04-130`–`REM-04-138` | Direct | `REL-APP-049`–`REL-APP-057` |
| `REM-04-139`–`REM-04-146` | Non-normative example fields | Excluded |
| `REM-04-147`–`REM-04-148` | Consolidated permitted storage locations | `REL-APP-058` |

Every in-scope REM entry is represented, consolidated with its material clauses intact, or excluded because of verified non-normative status.

---

# 5. Editorial QA record

- Source scope is limited to Sections 6–10 and `REM-04-070` through `REM-04-148`.
- Previous catalogue endpoint: `REL-APP-032`.
- First identifier in this part: `REL-APP-033`.
- Final identifier in this part: `REL-APP-058`.
- Total requirements in this part: 26.
- Catalogue numbering is continuous and unique.
- Example material changes, verification statuses and grant fields generate no normative catalogue requirements.
- The manifest example remains non-final and non-exhaustive.
- Verification remains bounded to specific facts and is not a universal trust guarantee.
- Permission Request declarations and Permission Grant constraints remain independently testable within their consolidated lists.
- No requirement from Section 11 or later is imported.

---

# 6. Part conclusion

Part 2 establishes signed, versioned and policy-readable Application Manifests, bounded verification semantics, complete Permission Requests and explicit, limited, inspectable and revocable Permission Grants.

Part 3 should begin with source Section 11 and `REM-04-149`.
