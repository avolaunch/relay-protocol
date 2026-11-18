# EA-05-04 — Application and Permission Requirements Catalogue

## Part 4 — Purpose, Retention, Onward Sharing and AI Processing

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines purpose limitation, external-retention disclosure and accountability, onward-sharing transparency, and granular representation of AI processing activities.

This catalogue part is generated from the completed and verified REM-04 extraction series. The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 16–20 and REM-04 entries `REM-04-213` through `REM-04-273`.

Verified non-normative vocabulary examples generate no catalogue requirements:

- `REM-04-220` through `REM-04-237`, possible purpose values;
- `REM-04-241` through `REM-04-246`, possible retention declarations; and
- `REM-04-255` through `REM-04-259`, possible onward-sharing values.

No example vocabulary, retention syntax or sharing value is selected as final protocol content.

Section 21 and later are intentionally deferred.

---

# 3. Requirements

---

## REL-APP-078

### Title

Purpose Declaration for Non-Trivial Requests

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Every non-trivial Permission Request **SHOULD** declare the purpose for which access is requested.

### Rationale

Purpose disclosure supports meaningful consent while preserving the source qualification for non-trivial requests.

### Source

- REM-04-213
- `design-notes/04-application-and-permission-model.md`, Section 16

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-079

### Title

Purpose Separate from Action

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** represent purpose independently from the requested action and support different declared purposes for otherwise equivalent actions.

### Rationale

What an application may do and why it may do it are distinct permission dimensions.

### Source

- REM-04-214
- REM-04-215
- `design-notes/04-application-and-permission-model.md`, Section 16

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-080

### Title

User-Serving Inference and Commercial Training Distinction

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** distinguish access used to answer the user's questions from access used to improve a commercial AI model.

### Rationale

The same read operation can create materially different consequences depending on its purpose.

### Source

- REM-04-216
- `design-notes/04-application-and-permission-model.md`, Section 16

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-081

### Title

Explicit Representation of Materially Different Purposes

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** represent materially different purposes explicitly enough for users, providers and automated policy engines to distinguish them.

### Rationale

Purpose must be comparable and evaluable rather than ambiguous unstructured wording.

### Source

- REM-04-217
- `design-notes/04-application-and-permission-model.md`, Section 16

### Related Invariants

- CI-06
- CI-08
- CI-11

---

## REL-APP-082

### Title

Basic Machine-Readable Purpose Vocabulary

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay **SHOULD** define a basic machine-readable vocabulary for declaring permission purposes.

### Rationale

A shared vocabulary enables consistent consent and automated policy evaluation.

### Source

- REM-04-218
- `design-notes/04-application-and-permission-model.md`, Section 17

### Related Invariants

- CI-08
- CI-12

---

## REL-APP-083

### Title

Extensible Purpose Vocabulary

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The Relay purpose vocabulary **SHOULD** allow extension beyond its core terms.

### Rationale

Extensions permit new purposes without redefining established semantics.

### Source

- REM-04-219
- `design-notes/04-application-and-permission-model.md`, Section 17

### Related Invariants

- CI-12

---

## REL-APP-084

### Title

Supplementary Purpose Explanation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** provide human-readable explanatory text in addition to a machine-readable purpose declaration.

### Rationale

Additional text can explain context while structured purpose remains available for policy evaluation.

### Source

- REM-04-238
- `design-notes/04-application-and-permission-model.md`, Section 17

### Related Invariants

- CI-06

---

## REL-APP-085

### Title

No Vague Custom Wording as Sole Purpose Declaration

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** rely solely on vague custom wording to declare the purpose of requested access.

### Rationale

Vague free text prevents reliable comparison and informed understanding.

### Source

- REM-04-239
- `design-notes/04-application-and-permission-model.md`, Section 17

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-086

### Title

External-Retention Declaration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Permission Request **MUST** declare whether the application retains accessed data outside the Relay Repository.

### Rationale

External copies, caches and derived data can persist outside repository control.

### Source

- REM-04-240
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-087

### Title

Machine-Readable Retention Period

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Where a retention period is declared, that period **SHOULD** be expressed in a machine-readable form.

### Rationale

Machine-readable duration supports consent, expiry checks and auditing without selecting the illustrative syntax.

### Source

- REM-04-247
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-08

---

## REL-APP-088

### Title

No Guarantee of Complete External Deletion

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The protocol **MUST NOT** represent itself as technically guaranteeing deletion of all external copies retained by an application or third party.

### Rationale

Relay cannot prove universal deletion from systems outside protocol control.

### Source

- REM-04-248
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-08
- CI-10

---

## REL-APP-089

### Title

Explicit Retention Commitment

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** be capable of expressing an application's retention commitment explicitly.

### Rationale

An attributable commitment allows retention behaviour to be understood and reviewed.

### Source

- REM-04-249
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-090

### Title

Recording Approved Retention Terms

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** be capable of recording the retention terms approved by the user.

### Rationale

Recorded approval distinguishes requested retention from the terms granted.

### Source

- REM-04-250
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-091

### Title

Retention Audit Support

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The Permission Model **SHOULD** support auditing of declared and approved retention commitments.

### Rationale

Audit support creates accountability without claiming complete technical enforcement.

### Source

- REM-04-251
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-10
- CI-11

---

## REL-APP-092

### Title

Retention Non-Compliance Identification

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The protocol **SHOULD** support identifying applications that do not comply with declared or granted retention commitments.

### Rationale

Detectable non-compliance enables user, provider and governance responses.

### Source

- REM-04-252
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-10
- CI-11

---

## REL-APP-093

### Title

Contractual Retention-Enforcement Support

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The protocol **MAY** provide records and declarations that support contractual enforcement of retention commitments.

### Rationale

Protocol evidence can support external accountability without adjudicating contracts.

### Source

- REM-04-253
- `design-notes/04-application-and-permission-model.md`, Section 18

### Related Invariants

- CI-10
- CI-11

---

## REL-APP-094

### Title

Onward-Sharing Declaration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every application requesting access **MUST** declare whether accessed data may be disclosed to third parties.

### Rationale

Approval for an application must not silently become approval for undisclosed partners.

### Source

- REM-04-254
- `design-notes/04-application-and-permission-model.md`, Section 19

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-095

### Title

Onward-Sharing Details

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where possible, a Permission Request involving onward sharing **SHOULD** identify the receiving third party, shared data category, third-party purpose, third-party retention period, and whether the recipient receives direct repository access or a copy.

### Rationale

These details support meaningful consent while preserving the source qualification.

### Source

- REM-04-260
- REM-04-261
- REM-04-262
- REM-04-263
- REM-04-264
- `design-notes/04-application-and-permission-model.md`, Section 19

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-096

### Title

No Partner-Network Distribution Under No-Sharing Grant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Permission Grant that prohibits onward sharing **MUST NOT** be interpreted as permitting distribution through an application partner network.

### Rationale

Application partnerships cannot override the approved sharing restriction.

### Source

- REM-04-265
- `design-notes/04-application-and-permission-model.md`, Section 19

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-097

### Title

Distinct AI-Use Activities

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** represent different forms of AI use as distinct activities rather than one undifferentiated permission.

### Rationale

Distinct representation permits different approval, retention and sharing treatment.

### Source

- REM-04-266
- `design-notes/04-application-and-permission-model.md`, Section 20

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-098

### Title

Representable AI-Use Categories

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The AI-use model **MUST** separately represent inference, personalisation, embedding or indexing, fine-tuning, general model training and evaluation.

### Rationale

These activities differ in purpose, persistence, audience and model effect.

### Source

- REM-04-267
- REM-04-268
- REM-04-269
- REM-04-270
- REM-04-271
- REM-04-272
- `design-notes/04-application-and-permission-model.md`, Section 20

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-099

### Title

No Generic Allow-AI Choice

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Consent interfaces and permission representations **SHOULD NOT** collapse inference, personalisation, embedding, fine-tuning, general training and evaluation into one generic `Allow AI` choice.

### Rationale

A single control obscures materially different processing.

### Source

- REM-04-273
- `design-notes/04-application-and-permission-model.md`, Section 20

### Related Invariants

- CI-06
- CI-11

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-213` | Direct | `REL-APP-078` |
| `REM-04-214`–`REM-04-215` | Consolidated purpose/action separation | `REL-APP-079` |
| `REM-04-216`–`REM-04-219` | Direct | `REL-APP-080`–`REL-APP-083` |
| `REM-04-220`–`REM-04-237` | Non-normative vocabulary examples | Excluded |
| `REM-04-238`–`REM-04-240` | Direct | `REL-APP-084`–`REL-APP-086` |
| `REM-04-241`–`REM-04-246` | Non-normative declaration examples | Excluded |
| `REM-04-247`–`REM-04-254` | Direct | `REL-APP-087`–`REL-APP-094` |
| `REM-04-255`–`REM-04-259` | Non-normative sharing examples | Excluded |
| `REM-04-260`–`REM-04-264` | Consolidated qualified disclosures | `REL-APP-095` |
| `REM-04-265`–`REM-04-266` | Direct | `REL-APP-096`–`REL-APP-097` |
| `REM-04-267`–`REM-04-272` | Consolidated AI-use category set | `REL-APP-098` |
| `REM-04-273` | Direct | `REL-APP-099` |

Every normative REM entry is represented directly or through consolidation that preserves its source-defined clause. Every verified example-only entry is explicitly excluded.

---

# 5. Editorial QA record

- Source scope is limited to Sections 16–20 and `REM-04-213` through `REM-04-273`.
- Previous endpoint: `REL-APP-077`.
- First identifier: `REL-APP-078`.
- Final identifier: `REL-APP-099`.
- Total requirements in this part: 22.
- Numbering remains continuous and unique.
- Purpose remains distinct from action.
- Non-trivial purpose declaration retains `SHOULD` strength.
- Retention commitments remain distinct from any claim that external deletion is technically guaranteed.
- The source qualification remains explicit for onward-sharing details.
- AI inference, personalisation, embeddings, fine-tuning, general training and evaluation remain distinct.
- No possible vocabulary value or illustrative syntax became mandatory.
- No content from Section 21 or later is imported.

---

# 6. Part conclusion

Part 4 establishes purpose limitation, external-retention accountability, onward-sharing transparency and granular AI-use permission semantics.

Part 5 should begin with source Section 21 and `REM-04-274`.
