# REM-04 Part 15 — Application and Permission Requirement Extraction Matrix (Sections 68–70)

## Document status

**Canonical editorial extraction**

This document extracts and classifies material from Sections 68–70 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole authoritative source. Open questions remain non-normative, provisional v0.1 decisions remain explicitly provisional, and the editorial hand-off to the next model is retained only as a non-normative boundary note.

---

## Extraction scope

This part covers:

68. Open design questions
69. Provisional decisions for v0.1
70. Core application principle

Requirement identifiers continue sequentially from Part 14, beginning with `REM-04-793`.

---

# 68. Open design questions

## REM-04-793 — Authorisation standard open design issue

**Source**  
Section 68.1: “Should Relay directly adopt an existing OAuth-based profile, define a compatible extension or create a capability-first authorisation layer?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-794 — Grant storage open design issue

**Source**  
Section 68.2: “Should Permission Grants live inside the main repository, a separate private authority repository or the Relay Provider’s authorisation service?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-795 — Purpose enforcement open design issue

**Source**  
Section 68.3: “Which purpose restrictions can be technically enforced, and which remain auditable commitments?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-796 — Field-level access open design issue

**Source**  
Section 68.4: “How much complexity should v0.1 accept for permissions limited to specific record fields?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-797 — Delegated keys open design issue

**Source**  
Section 68.5: “Should delegated application keys be required, optional or postponed in the first reference implementation?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-798 — Cross-provider grants open design issue

**Source**  
Section 68.6: “How should a new provider validate grants originally issued through another provider?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-799 — Application trust registry open design issue

**Source**  
Section 68.7: “Should Relay define a shared application registry, rely on distributed manifests or support both?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-800 — Material manifest change open design issue

**Source**  
Section 68.8: “Which application changes must invalidate or pause existing grants?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-801 — AI vocabulary open design issue

**Source**  
Section 68.9: “What standard vocabulary is sufficient to distinguish inference, embeddings, fine-tuning, evaluation and general training?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-802 — Legal terms open design issue

**Source**  
Section 68.10: “How should machine-readable permission terms relate to privacy policies, contracts and regional law?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-803 — Public data access open design issue

**Source**  
Section 68.11: “Which usage declarations, if any, can be attached to public records without requiring a direct grant?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

## REM-04-804 — Installation identity open design issue

**Source**  
Section 68.12: “Should each installation have its own key pair and revocation state in v0.1?”

**Requirement**  
**Non-normative open design issue.** The source leaves this question unresolved. No candidate answer is selected by REM-04.

**Classification**  
Open design issue; non-normative; excluded from catalogue generation until resolved.

**Notes**  
This entry preserves the unresolved question for founder and design review. It MUST NOT be treated as a settled protocol requirement.

---

# 69. Provisional decisions for v0.1

## REM-04-805 — Stable Application Identity

**Source**  
Section 69 provisional decision: “every application has a stable Application Identity”.

**Requirement**  
**PROVISIONAL v0.1.** Every application MUST have a stable Application Identity.

**Classification**  
Application identity; continuity; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-806 — Signed Application Manifest

**Source**  
Section 69 provisional decision: “every application publishes a signed, versioned manifest”.

**Requirement**  
**PROVISIONAL v0.1.** Every application MUST publish a signed Application Manifest.

**Classification**  
Manifest integrity; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-807 — Versioned Application Manifest

**Source**  
Section 69 provisional decision: “every application publishes a signed, versioned manifest”.

**Requirement**  
**PROVISIONAL v0.1.** Every Application Manifest MUST be versioned.

**Classification**  
Manifest versioning; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-808 — Explicit grants

**Source**  
Section 69 provisional decision: “grants are explicit and revocable”.

**Requirement**  
**PROVISIONAL v0.1.** Permission Grants MUST be explicit.

**Classification**  
Grant semantics; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-809 — Revocable grants

**Source**  
Section 69 provisional decision: “grants are explicit and revocable”.

**Requirement**  
**PROVISIONAL v0.1.** Permission Grants MUST be revocable.

**Classification**  
Revocation; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-810 — Resource-and-action scopes

**Source**  
Section 69 provisional decision: “scopes are defined by resource and action”.

**Requirement**  
**PROVISIONAL v0.1.** Permission scopes MUST be defined by resource and action.

**Classification**  
Scope model; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-811 — Separate purpose declaration

**Source**  
Section 69 provisional decision: “purpose, retention, onward sharing and AI use are separate declarations”.

**Requirement**  
**PROVISIONAL v0.1.** Purpose MUST be represented as a declaration distinct from retention, onward sharing and AI use.

**Classification**  
Purpose limitation; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-812 — Separate retention declaration

**Source**  
Section 69 provisional decision: “purpose, retention, onward sharing and AI use are separate declarations”.

**Requirement**  
**PROVISIONAL v0.1.** Retention MUST be represented as a declaration distinct from purpose, onward sharing and AI use.

**Classification**  
Retention; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-813 — Separate onward-sharing declaration

**Source**  
Section 69 provisional decision: “purpose, retention, onward sharing and AI use are separate declarations”.

**Requirement**  
**PROVISIONAL v0.1.** Onward sharing MUST be represented as a declaration distinct from purpose, retention and AI use.

**Classification**  
Onward sharing; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-814 — Separate AI-use declaration

**Source**  
Section 69 provisional decision: “purpose, retention, onward sharing and AI use are separate declarations”.

**Requirement**  
**PROVISIONAL v0.1.** AI use MUST be represented as a declaration distinct from purpose, retention and onward sharing.

**Classification**  
AI use; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-815 — Partial approval

**Source**  
Section 69 provisional decision: “partial approval is supported”.

**Requirement**  
**PROVISIONAL v0.1.** The Permission Model MUST support partial approval of a Permission Request.

**Classification**  
Consent granularity; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-816 — Short-lived ordinary access

**Source**  
Section 69 provisional decision: “ordinary access uses short-lived tokens”.

**Requirement**  
**PROVISIONAL v0.1.** Ordinary application access MUST use short-lived tokens.

**Classification**  
Token lifetime; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-817 — Renewable long-running authority

**Source**  
Section 69 provisional decision: “long-running access uses renewable authority”.

**Requirement**  
**PROVISIONAL v0.1.** Long-running application access MUST use renewable authority.

**Classification**  
Long-running access; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-818 — Separate high-authority approval

**Source**  
Section 69 provisional decision: “high-authority operations require separate approval”.

**Requirement**  
**PROVISIONAL v0.1.** High-authority operations MUST require approval separate from ordinary application access.

**Classification**  
High-authority operations; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-819 — Record continuity after revocation

**Source**  
Section 69 provisional decision: “application-created records remain in the user’s repository after revocation”.

**Requirement**  
**PROVISIONAL v0.1.** Application-created canonical records MUST remain in the user’s Relay Repository after application revocation unless separately deleted through valid authority.

**Classification**  
Record continuity; revocation; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-820 — Re-authorisation for expanded behaviour

**Source**  
Section 69 provisional decision: “materially expanded behaviour requires re-authorisation”.

**Requirement**  
**PROVISIONAL v0.1.** Materially expanded application behaviour MUST require re-authorisation.

**Classification**  
Material change; re-authorisation; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-821 — Private provider audit records

**Source**  
Section 69 provisional decision: “providers maintain private audit records”.

**Requirement**  
**PROVISIONAL v0.1.** Relay Providers MUST maintain private authorisation audit records.

**Classification**  
Auditability; privacy; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-822 — Connected-application inspection

**Source**  
Section 69 provisional decision: “users can inspect connected applications and revoke access”.

**Requirement**  
**PROVISIONAL v0.1.** Users MUST be able to inspect connected applications.

**Classification**  
User control; inspection; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-823 — Application access revocation

**Source**  
Section 69 provisional decision: “users can inspect connected applications and revoke access”.

**Requirement**  
**PROVISIONAL v0.1.** Users MUST be able to revoke application access.

**Classification**  
User control; revocation; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-824 — Safe grant continuity during migration

**Source**  
Section 69 provisional decision: “provider migration preserves grants where safely possible but replaces provider-specific tokens”.

**Requirement**  
**PROVISIONAL v0.1.** Provider migration SHOULD preserve Permission Grants where continuation is safe.

**Classification**  
Provider migration; grant continuity; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-825 — Provider-specific token replacement

**Source**  
Section 69 provisional decision: “provider migration preserves grants where safely possible but replaces provider-specific tokens”.

**Requirement**  
**PROVISIONAL v0.1.** Provider migration MUST replace provider-specific tokens rather than copying or continuing them unchanged.

**Classification**  
Provider migration; token replacement; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-826 — OAuth-compatible authorisation preference

**Source**  
Section 69 provisional decision: “OAuth-compatible authorisation practices will be preferred over a wholly proprietary login mechanism”.

**Requirement**  
**PROVISIONAL v0.1.** Relay v0.1 SHOULD prefer OAuth-compatible authorisation practices over a wholly proprietary login mechanism.

**Classification**  
Authorisation interoperability; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

## REM-04-827 — Partly contractual purpose restrictions

**Source**  
Section 69 provisional decision: “purpose restrictions may initially be partly contractual and auditable rather than fully technically enforceable”.

**Requirement**  
**PROVISIONAL v0.1.** Relay v0.1 MAY initially represent some purpose restrictions as contractual and auditable commitments rather than fully technically enforceable controls.

**Classification**  
Purpose enforcement; auditability; provisional v0.1 decision.

**Notes**  
This entry records the current v0.1 working baseline. Its provisional status MUST remain explicit in downstream catalogue and review artefacts until the source confirms or replaces the decision.

---

# 70. Core application principle

## REM-04-828 — Temporary application authority

**Source**  
Section 70: “A Relay Application receives temporary, limited authority to interact with a person’s digital continuity...”

**Requirement**  
A Relay Application MUST receive only temporary authority to interact with a person’s digital continuity.

**Classification**  
Core principle; authority duration; application limitation.

**Notes**  
Application authority is delegated for a bounded period or renewable lifecycle. It is not permanent merely because an Application Identity or installation persists.

---

## REM-04-829 — Limited application authority

**Source**  
Section 70: “A Relay Application receives temporary, limited authority to interact with a person’s digital continuity...”

**Requirement**  
A Relay Application MUST receive only authority limited by its valid approval basis, resources, actions, purposes, duration and applicable conditions.

**Classification**  
Core principle; least authority; grant limitation.

**Notes**  
The application model delegates bounded authority rather than general control over the Relay Identity, Repository or digital continuity.

---

## REM-04-830 — No application ownership of digital continuity

**Source**  
Section 70: a Relay Application “never receives ownership of that continuity.”

**Requirement**  
A Relay Application MUST NOT receive or be represented as receiving ownership of the person’s digital continuity.

**Classification**  
Core principle; ownership separation; user authority.

**Notes**  
Application authority remains delegated and limited. It does not transfer ownership of the Relay Identity, Repository, records, relationships or other continuity objects.

---

## REM-04-831 — Relationship Model boundary

**Source**  
Section 70: “The next core object is the Relay Relationship Model...”

**Requirement**  
**Non-normative model-boundary note.** The source identifies the Relationship Model as the next design model and summarises its subject matter.

**Classification**  
Editorial transition; non-normative; excluded from the Application and Permission Requirements Catalogue.

**Notes**  
Requirements for follows, subscriptions, collaborations, memberships and other relationships are extracted from the authoritative Relationship Model rather than inferred from this hand-off sentence.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 68–70 of `design-notes/04-application-and-permission-model.md`.
- All twelve Section 68 questions were retained as non-normative open design issues.
- All sixteen Section 69 bullets were represented. Compound bullets were decomposed where they contain independently testable obligations.
- The Section 70 core principle was decomposed into temporary authority, limited authority and non-ownership.
- The Relationship Model hand-off was retained only as a non-normative boundary note.

## Numbering verification

- First entry: `REM-04-793`.
- Final entry: `REM-04-831`.
- Numbering continues directly from `REM-04-792` without gaps or duplicates.

## Status verification

- Section 68 generated no settled protocol requirements.
- Section 69 entries are explicitly labelled `PROVISIONAL v0.1`.
- Section 70’s model-boundary sentence generated no normative Application and Permission requirement.

## REM-04 sequence closure

- Parts 1–15 collectively cover Sections 1–70 of the Application and Permission Model.
- The REM-04 sequence begins at `REM-04-001` and concludes at `REM-04-831`.
- Open, provisional, normative and model-boundary material remain visibly distinct.
