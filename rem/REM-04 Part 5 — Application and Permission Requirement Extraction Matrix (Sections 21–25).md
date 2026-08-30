# REM-04 Part 5 — Application and Permission Requirement Extraction Matrix (Sections 21–25)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 21–25 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

21. AI permission declaration
22. Duration
23. One-time capabilities
24. Conditional permission
25. Permission inheritance

Requirement identifiers continue sequentially from Part 4, beginning with `REM-04-274`.

---

# 21. AI permission declaration

## REM-04-274 — AI-use declaration in AI-related requests

**Source**  
Section 21: “An AI-related request should declare...”

**Requirement**  
An AI-related Permission Request SHOULD include a structured declaration of the AI activities for which access is requested.

**Classification**  
AI transparency; permission request; recommendation.

**Notes**  
The source uses “should”, so this is a recommended requirement rather than an unconditional validity rule.

---

## REM-04-275 — AI inference declaration

**Source**  
Section 21 example field: `"inference": true`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether requested data will be used for AI inference.

**Classification**  
AI transparency; purpose limitation.

**Notes**  
Inference concerns use of records to produce an output, typically for the requesting user or application workflow.

---

## REM-04-276 — AI personalisation declaration

**Source**  
Section 21 example field: `"personalisation": true`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether requested data will be used for personalisation.

**Classification**  
AI transparency; personalisation; purpose limitation.

**Notes**  
Personalisation must remain distinguishable from general model training.

---

## REM-04-277 — Embedding declaration

**Source**  
Section 21 example field: `"embedding": true`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether requested data will be transformed into embeddings, vectors or another searchable representation.

**Classification**  
AI transparency; derived data; indexing.

**Notes**  
The declaration should not be omitted merely because the resulting representation is not human-readable.

---

## REM-04-278 — Fine-tuning declaration

**Source**  
Section 21 example field: `"fineTuning": false`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether requested data will be used to fine-tune or otherwise adapt a model.

**Classification**  
AI transparency; model adaptation; purpose limitation.

**Notes**  
Fine-tuning must be represented separately from inference, personalisation and general training.

---

## REM-04-279 — General model-training declaration

**Source**  
Section 21 example field: `"generalTraining": false`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether requested data will be used for general model training.

**Classification**  
AI transparency; model training; high-impact purpose.

**Notes**  
A declaration permitting inference must not be interpreted as permission for general training.

---

## REM-04-280 — Human-review declaration

**Source**  
Section 21 example field: `"humanReview": false`.

**Requirement**  
An AI-related Permission Request SHOULD declare whether human reviewers may inspect inputs, outputs or related processing artefacts.

**Classification**  
Human review; privacy transparency; permission request.

**Notes**  
Human review is a separate disclosure from automated AI processing.

---

## REM-04-281 — External model-provider declaration

**Source**  
Section 21 example field: `"externalModelProvider": "rid:app:model-provider"`.

**Requirement**  
An AI-related Permission Request SHOULD identify any external model provider involved in processing.

**Classification**  
Third-party processing; AI transparency; application identity.

**Notes**  
Where the external provider has a Relay Application Identity, that stable identity should be used rather than only a brand name.

---

## REM-04-282 — Consent disclosure of data used

**Source**  
Section 21: “The consent interface should explain: what data is used...”

**Requirement**  
The consent interface SHOULD explain which data will be used in the requested AI processing.

**Classification**  
Consent interface; data transparency; recommendation.

**Notes**  
The disclosure should be concrete enough for the person to distinguish public, restricted, private, current, historical or derived data where relevant.

---

## REM-04-283 — Consent disclosure of AI activity

**Source**  
Section 21: “The consent interface should explain... which AI activity occurs...”

**Requirement**  
The consent interface SHOULD explain the specific AI activity or activities that will occur.

**Classification**  
Consent interface; AI transparency.

**Notes**  
The interface should not collapse inference, personalisation, embedding, fine-tuning, training and evaluation into one generic AI label.

---

## REM-04-284 — Consent disclosure of processing location

**Source**  
Section 21: “The consent interface should explain... where processing occurs...”

**Requirement**  
The consent interface SHOULD explain where AI processing will occur.

**Classification**  
Consent interface; processing location; jurisdictional transparency.

**Notes**  
The source does not define a mandatory location vocabulary in this section.

---

## REM-04-285 — Consent disclosure of third-party model providers

**Source**  
Section 21: “The consent interface should explain... whether a third-party model provider is involved...”

**Requirement**  
The consent interface SHOULD explain whether a third-party model provider is involved.

**Classification**  
Consent interface; onward processing; third-party disclosure.

**Notes**  
This disclosure is required independently of whether the requesting application remains the primary user-facing service.

---

## REM-04-286 — Consent disclosure of AI-related retention

**Source**  
Section 21: “The consent interface should explain... whether data is retained...”

**Requirement**  
The consent interface SHOULD explain whether data used in AI processing will be retained.

**Classification**  
Consent interface; retention; AI processing.

**Notes**  
Where retention occurs, the relevant retention declaration from Section 18 should also apply.

---

## REM-04-287 — Consent disclosure of human review

**Source**  
Section 21: “The consent interface should explain... whether humans may review inputs or outputs.”

**Requirement**  
The consent interface SHOULD explain whether humans may review AI-processing inputs or outputs.

**Classification**  
Consent interface; human review; privacy transparency.

**Notes**  
This should be disclosed even where human review is limited to support, safety, evaluation or incident investigation.

---

# 22. Duration

## REM-04-288 — Permission Grant duration support

**Source**  
Section 22: “A Permission Grant may be valid...”

**Requirement**  
The Permission Grant model MUST support grants with explicitly defined validity conditions.

**Classification**  
Grant lifecycle; duration; authorisation.

**Notes**  
The source lists several permitted duration models rather than requiring one universal model.

---

## REM-04-289 — One-operation duration

**Source**  
Section 22: “for one operation”.

**Requirement**  
A Permission Grant MAY be limited to one operation.

**Classification**  
Duration; least privilege; one-time authority.

**Notes**  
Section 23 further defines one-time capabilities as a preferred mechanism for some such operations.

---

## REM-04-290 — One-session duration

**Source**  
Section 22: “for one session”.

**Requirement**  
A Permission Grant MAY be limited to one session.

**Classification**  
Duration; session-bound authority.

**Notes**  
The session boundary must be determinable by the implementation.

---

## REM-04-291 — Fixed expiration time

**Source**  
Section 22: “until a specific time”.

**Requirement**  
A Permission Grant MAY remain valid until a specified expiration time.

**Classification**  
Duration; time-bound access.

**Notes**  
The example uses an absolute timestamp, but the final timestamp syntax is governed by the protocol’s general encoding rules.

---

## REM-04-292 — Defined-duration validity

**Source**  
Section 22: “for a defined duration”.

**Requirement**  
A Permission Grant MAY remain valid for a defined duration.

**Classification**  
Duration; time-bound access.

**Notes**  
A defined duration should be machine-readable where practical.

---

## REM-04-293 — Until-revoked validity

**Source**  
Section 22: “until revoked”.

**Requirement**  
A Permission Grant MAY remain valid until revoked.

**Classification**  
Duration; revocation; long-lived authority.

**Notes**  
Until-revoked does not mean irrevocable or exempt from review.

---

## REM-04-294 — Relationship-bound validity

**Source**  
Section 22: “while a relationship remains valid”.

**Requirement**  
A Permission Grant MAY remain valid only while a defined relationship remains valid.

**Classification**  
Conditional duration; relationship-based authority.

**Notes**  
The relationship and the method for evaluating its current validity must be identifiable.

---

## REM-04-295 — Credential-bound validity

**Source**  
Section 22: “while a credential remains valid”.

**Requirement**  
A Permission Grant MAY remain valid only while a specified credential remains valid.

**Classification**  
Conditional duration; credential-based authority.

**Notes**  
Expiration or revocation of the credential should terminate the dependent grant.

---

## REM-04-296 — Reviewability of indefinite grants

**Source**  
Section 22: “Indefinite grants should still be reviewable and revocable.”

**Requirement**  
An indefinite Permission Grant SHOULD remain reviewable by the person or authorised controller.

**Classification**  
Grant governance; reviewability; recommendation.

**Notes**  
Indefinite duration must not remove user visibility into the grant.

---

## REM-04-297 — Revocability of indefinite grants

**Source**  
Section 22: “Indefinite grants should still be reviewable and revocable.”

**Requirement**  
An indefinite Permission Grant SHOULD remain revocable.

**Classification**  
Revocation; grant lifecycle; recommendation.

**Notes**  
This reinforces the broader rule that application authority is revocable.

---

# 23. One-time capabilities

## REM-04-298 — Prefer one-time capabilities for suitable operations

**Source**  
Section 23: “Some operations should use a one-time capability rather than a long-lived grant.”

**Requirement**  
Operations that require only isolated authority SHOULD use a one-time capability rather than a long-lived Permission Grant.

**Classification**  
Least privilege; capability security; recommendation.

**Notes**  
The source identifies imports, single publications, exports, migrations, restricted-record sharing and blob uploads as examples.

---

## REM-04-299 — One-time archive-import capability

**Source**  
Section 23 example: “import one archive”.

**Requirement**  
An application MAY request a one-time capability limited to importing one archive.

**Classification**  
Import; one-time capability.

**Notes**  
The capability must not imply continuing import or repository access.

---

## REM-04-300 — One-time publication capability

**Source**  
Section 23 example: “publish one post”.

**Requirement**  
An application MAY request a one-time capability limited to publishing one post or equivalent record.

**Classification**  
Publication; one-time capability.

**Notes**  
The capability should identify the permitted operation and relevant target or schema context.

---

## REM-04-301 — One-time export-download capability

**Source**  
Section 23 example: “download one export”.

**Requirement**  
An application MAY request a one-time capability limited to downloading one export.

**Classification**  
Export; one-time capability.

**Notes**  
Repeated exports require separate or broader explicit authority.

---

## REM-04-302 — One-time migration approval

**Source**  
Section 23 example: “approve one migration”.

**Requirement**  
A migration approval MAY be represented as a one-time capability limited to one migration operation.

**Classification**  
Migration; high-authority action; one-time capability.

**Notes**  
The capability should not establish open-ended migration authority.

---

## REM-04-303 — One-time restricted-record sharing

**Source**  
Section 23 example: “share one restricted record”.

**Requirement**  
An application MAY request a one-time capability limited to sharing one restricted record.

**Classification**  
Restricted access; sharing; one-time capability.

**Notes**  
The target record and intended recipient or audience should be unambiguous.

---

## REM-04-304 — One-time blob upload

**Source**  
Section 23 example: “upload one blob”.

**Requirement**  
An application MAY request a one-time capability limited to uploading one blob.

**Classification**  
Blob operation; one-time capability.

**Notes**  
The capability may also be constrained by media type, size, purpose or destination.

---

## REM-04-305 — Invalidation after successful use

**Source**  
Section 23: “A one-time capability becomes invalid after: successful use...”

**Requirement**  
A one-time capability MUST become invalid after successful use.

**Classification**  
Capability lifecycle; replay prevention.

**Notes**  
The capability must not be reusable for a second operation after successful completion.

---

## REM-04-306 — Invalidation after expiration

**Source**  
Section 23: “A one-time capability becomes invalid after... expiration...”

**Requirement**  
A one-time capability MUST become invalid upon expiration.

**Classification**  
Capability lifecycle; time-bound access.

**Notes**  
An expired capability must not be revived without a newly authorised capability.

---

## REM-04-307 — Invalidation after revocation

**Source**  
Section 23: “A one-time capability becomes invalid after... revocation...”

**Requirement**  
A one-time capability MUST become invalid upon revocation.

**Classification**  
Revocation; capability lifecycle.

**Notes**  
Revocation must take precedence over unused capability status.

---

## REM-04-308 — Invalidation after failure threshold

**Source**  
Section 23: “A one-time capability becomes invalid after... failure threshold...”

**Requirement**  
A one-time capability MUST become invalid when its defined failure threshold is reached.

**Classification**  
Abuse prevention; capability security; lifecycle.

**Notes**  
The source does not define one universal failure threshold.

---

## REM-04-309 — Invalidation after relevant state change

**Source**  
Section 23: “A one-time capability becomes invalid after... change in relevant repository state.”

**Requirement**  
A one-time capability MUST become invalid when a relevant repository-state change makes the authorised operation stale or unsafe.

**Classification**  
Repository-state validation; capability lifecycle; concurrency.

**Notes**  
Examples may include a changed current version, deleted target, altered audience or completed migration.

---

# 24. Conditional permission

## REM-04-310 — Conditional grants

**Source**  
Section 24: “A grant may include conditions.”

**Requirement**  
A Permission Grant MAY include explicit conditions that further restrict when or how an approved capability may be exercised.

**Classification**  
Conditional authorisation; least privilege.

**Notes**  
Conditions narrow authority and must not silently broaden the underlying grant.

---

## REM-04-311 — User-confirmation condition

**Source**  
Section 24 example: “May publish only after user confirmation”.

**Requirement**  
A Permission Grant MAY require user confirmation before a publishing operation is executed.

**Classification**  
Conditional authorisation; publication; user confirmation.

**Notes**  
The application must not treat the initial grant as the final confirmation where the condition requires a later confirmation step.

---

## REM-04-312 — Public-record-only condition

**Source**  
Section 24 example: “May read only public posts”.

**Requirement**  
A Permission Grant MAY restrict read access to public records only.

**Classification**  
Visibility constraint; conditional access.

**Notes**  
The condition must exclude unlisted, restricted and private records unless separately authorised.

---

## REM-04-313 — Created-by-application condition

**Source**  
Section 24 example: “May update only records it originally created”.

**Requirement**  
A Permission Grant MAY restrict update authority to records originally created by the authorised application.

**Classification**  
Provenance-based constraint; update authority.

**Notes**  
The repository must be able to determine the relevant creation provenance reliably.

---

## REM-04-314 — Maximum-blob-size condition

**Source**  
Section 24 example: “May upload files smaller than 50 MB”.

**Requirement**  
A Permission Grant MAY impose a maximum blob size on upload operations.

**Classification**  
Blob constraint; resource control; conditional permission.

**Notes**  
The limit should be represented in a machine-readable unit.

---

## REM-04-315 — Registered-device condition

**Source**  
Section 24 example: “May access private notes only from the user’s registered device”.

**Requirement**  
A Permission Grant MAY restrict access to specified or registered devices.

**Classification**  
Device-bound access; private data; conditional permission.

**Notes**  
Device identity and registration status must be verifiable at access time.

---

## REM-04-316 — High-authority authentication condition

**Source**  
Section 24 example: “May export only after high-authority authentication”.

**Requirement**  
A Permission Grant MAY require high-authority authentication before an export or other sensitive operation is executed.

**Classification**  
Step-up authentication; export; high-risk operation.

**Notes**  
Possession of an ordinary background session must not satisfy the condition unless the required authentication level is met.

---

## REM-04-317 — Machine-readable conditions

**Source**  
Section 24 JSON example containing `userConfirmationRequired`, `maximumBlobSize` and `createdByApplicationOnly`.

**Requirement**  
Grant conditions SHOULD be represented in a machine-readable form that can be evaluated by the Relay Provider or authorisation service.

**Classification**  
Policy automation; conditional authorisation; recommendation.

**Notes**  
The example field names are illustrative rather than a final fixed schema.

---

# 25. Permission inheritance

## REM-04-318 — No implicit permission inheritance

**Source**  
Section 25: “Permission should not be inherited implicitly merely because records are related.”

**Requirement**  
Permission SHOULD NOT be inherited implicitly solely because records, identities, repositories or collections are related.

**Classification**  
Permission boundaries; least privilege; recommendation.

**Notes**  
A relationship between objects is not itself an authorisation grant.

---

## REM-04-319 — Post access does not imply private-profile access

**Source**  
Section 25 example: “permission to read a post does not automatically permit reading the author’s private profile”.

**Requirement**  
Permission to read a record MUST NOT automatically grant access to private profile information belonging to the record’s author.

**Classification**  
Privacy boundary; non-inheritance; identity data.

**Notes**  
Private profile access requires separate explicit authority.

---

## REM-04-320 — Project access does not imply collaborator-repository access

**Source**  
Section 25 example: “permission to read a project does not automatically permit reading every collaborator’s repository”.

**Requirement**  
Permission to read a project record MUST NOT automatically grant access to the repositories of its collaborators.

**Classification**  
Cross-repository boundary; non-inheritance; privacy.

**Notes**  
Each collaborator’s repository remains governed by its own authority and grants.

---

## REM-04-321 — Collection access does not imply deleted-version access

**Source**  
Section 25 example: “permission to access a folder-like collection does not necessarily permit deleted versions.”

**Requirement**  
Permission to access a collection MUST NOT be assumed to include access to deleted or historical versions unless the grant explicitly includes them.

**Classification**  
Historical-data access; deletion state; non-inheritance.

**Notes**  
Current content, historical versions and deleted versions are distinct resource scopes.

---

## REM-04-322 — Explicit inheritance rules

**Source**  
Section 25: “Any inheritance rules must be explicit in the schema or grant.”

**Requirement**  
Any permission-inheritance rule MUST be explicitly defined in the applicable schema or Permission Grant.

**Classification**  
Permission semantics; schema rules; grant interpretation.

**Notes**  
Applications and providers must not infer inheritance from user-interface grouping, object nesting or relationship links alone.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 21–25 of `design-notes/04-application-and-permission-model.md`.
- Section 26 and later content was excluded.
- JSON examples were treated as illustrative structures rather than final fixed wire formats.

## Numbering verification

- First requirement: `REM-04-274`.
- Final requirement: `REM-04-322`.
- Requirement numbering continues directly from Part 4.
- Requirement identifiers are continuous, unique and ordered according to source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, example or necessary decomposition of a compound obligation.
- AI declaration fields were extracted separately because each represents a distinct consent and purpose dimension.
- One-time capability invalidation events were extracted separately because each creates an independently testable lifecycle condition.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` or `SHOULD NOT` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- Illustrative examples were not converted into universal mandatory operations beyond the source’s stated rules.

## Editorial verification

- AI inference, personalisation, embedding, fine-tuning, general training and human review remain separately representable.
- Indefinite grants remain reviewable and revocable.
- One-time capabilities terminate after use, expiration, revocation, failure threshold or relevant state change.
- Conditions narrow grants and do not broaden underlying authority.
- Permission inheritance is explicit rather than inferred from record relationships or collection structure.
