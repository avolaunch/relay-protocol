# REM-03 Part 4 — Record Requirement Extraction Matrix (Sections 16–20)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 16–20 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

16. Usage rights
17. Record creation
18. Record validation
19. Record update
20. Immutable records

Requirement identifiers continue sequentially from Part 3, beginning with `REM-03-166`.

---

# 16. Usage rights

## REM-03-166 — Separation of visibility and usage rights

**Source**  
Section 16: “Visibility and usage rights are separate.”

**Requirement**  
The Relay Record Model MUST represent record visibility separately from record usage rights.

**Classification**  
Rights modelling; access control; separation of concerns.

**Notes**  
Permission to view a record does not by itself establish permission to reproduce, modify, exploit, syndicate or train models on that record.

---

## REM-03-167 — Public visibility does not imply reproduction rights

**Source**  
Section 16: “A public record may be viewable without granting unlimited rights to reproduce it.”

**Requirement**  
Public visibility MUST NOT be interpreted as an unlimited grant to reproduce the record.

**Classification**  
Usage rights; public records; licensing.

**Notes**  
Applications and observers must distinguish public readability from reproduction permission.

---

## REM-03-168 — Public visibility does not imply commercial-use rights

**Source**  
Section 16: “A public record may be viewable without granting unlimited rights to commercially exploit it.”

**Requirement**  
Public visibility MUST NOT be interpreted as an unlimited grant to commercially exploit the record.

**Classification**  
Usage rights; commercial use; licensing.

**Notes**  
Commercial-use permissions may be separately granted, restricted or prohibited.

---

## REM-03-169 — Public visibility does not imply model-training rights

**Source**  
Section 16: “A public record may be viewable without granting unlimited rights to train models on it.”

**Requirement**  
Public visibility MUST NOT be interpreted as an unlimited grant to use the record for model training.

**Classification**  
Usage rights; model training; licensing.

**Notes**  
The protocol may express a model-training restriction even where the record is publicly readable.

---

## REM-03-170 — Public visibility does not imply modification rights

**Source**  
Section 16: “A public record may be viewable without granting unlimited rights to modify it.”

**Requirement**  
Public visibility MUST NOT be interpreted as an unlimited grant to modify the record or create derivatives.

**Classification**  
Usage rights; modification; derivative works.

**Notes**  
Modification and derivative rights must be evaluated separately from view access.

---

## REM-03-171 — Public visibility does not imply syndication rights

**Source**  
Section 16: “A public record may be viewable without granting unlimited rights to syndicate it.”

**Requirement**  
Public visibility MUST NOT be interpreted as an unlimited grant to syndicate or redistribute the record.

**Classification**  
Usage rights; redistribution; syndication.

**Notes**  
A rights declaration may require attribution, permission or another condition for redistribution.

---

## REM-03-172 — Structured rights declaration support

**Source**  
Section 16: “A record may include a structured rights declaration.”

**Requirement**  
A Relay Record MAY include a structured rights declaration.

**Classification**  
Rights metadata; extensibility; licensing.

**Notes**  
The source example includes view, redistribution, commercial use, model training and derivative-work terms, but the exact final schema remains outside this section.

---

## REM-03-173 — Expression of view terms

**Source**  
Section 16, example rights declaration: `"view": "public"`.

**Requirement**  
A structured rights declaration MAY express terms governing viewing or access.

**Classification**  
Rights metadata; access terms.

**Notes**  
This rights expression remains distinct from the record’s protocol visibility classification.

---

## REM-03-174 — Expression of redistribution terms

**Source**  
Section 16, example rights declaration: `"redistribution": "attribution-required"`.

**Requirement**  
A structured rights declaration MAY express terms governing redistribution or syndication.

**Classification**  
Rights metadata; redistribution; licensing.

**Notes**  
Terms may include conditions such as attribution, permission or prohibition.

---

## REM-03-175 — Expression of commercial-use terms

**Source**  
Section 16, example rights declaration: `"commercialUse": "prohibited"`.

**Requirement**  
A structured rights declaration MAY express terms governing commercial use.

**Classification**  
Rights metadata; commercial licensing.

**Notes**  
The protocol can represent the declared term but does not itself guarantee external enforcement.

---

## REM-03-176 — Expression of model-training terms

**Source**  
Section 16, example rights declaration: `"modelTraining": "prohibited"`.

**Requirement**  
A structured rights declaration MAY express terms governing use of the record for model training.

**Classification**  
Rights metadata; artificial intelligence; licensing.

**Notes**  
The declaration expresses the controller’s or rights holder’s term; compliance may depend on external enforcement mechanisms.

---

## REM-03-177 — Expression of derivative-work terms

**Source**  
Section 16, example rights declaration: `"derivatives": "permission-required"`.

**Requirement**  
A structured rights declaration MAY express terms governing modification or derivative works.

**Classification**  
Rights metadata; modification; derivative works.

**Notes**  
The final vocabulary and enforceability model are not fixed by the example.

---

## REM-03-178 — Protocol expression of rights terms

**Source**  
Section 16: “The protocol can express these terms.”

**Requirement**  
The Relay Protocol MUST be capable of representing structured usage-rights terms associated with a record.

**Classification**  
Protocol capability; rights expression; interoperability.

**Notes**  
This is an expression capability, not a guarantee that every observer will comply.

---

## REM-03-179 — No guarantee of external compliance

**Source**  
Section 16: “It cannot guarantee that every external observer will obey them.”

**Requirement**  
The Relay Protocol MUST NOT represent structured usage-rights terms as a guarantee that every external observer will obey them.

**Classification**  
Protocol limitation; rights enforcement; trust boundary.

**Notes**  
Once information is disclosed externally, protocol metadata alone cannot ensure behavioural compliance.

---

## REM-03-180 — Contractual enforcement dependency

**Source**  
Section 16: “Enforcement may depend on contracts.”

**Requirement**  
Enforcement of declared usage rights MAY depend on contractual mechanisms outside the Relay Protocol.

**Classification**  
External enforcement; contracts; governance.

**Notes**  
The protocol may carry the declaration without being the sole enforcement mechanism.

---

## REM-03-181 — Application-policy enforcement dependency

**Source**  
Section 16: “Enforcement may depend on application policies.”

**Requirement**  
Enforcement of declared usage rights MAY depend on application policies.

**Classification**  
External enforcement; application governance.

**Notes**  
Applications may choose to enforce or refuse operations based on the rights declaration.

---

## REM-03-182 — Technical-control enforcement dependency

**Source**  
Section 16: “Enforcement may depend on technical controls.”

**Requirement**  
Enforcement of declared usage rights MAY depend on technical controls.

**Classification**  
External enforcement; technical controls; access management.

**Notes**  
Examples could include access gates, encryption or controlled delivery, though the source does not mandate a specific mechanism here.

---

## REM-03-183 — Licensing-system enforcement dependency

**Source**  
Section 16: “Enforcement may depend on licensing systems.”

**Requirement**  
Enforcement of declared usage rights MAY depend on licensing systems.

**Classification**  
External enforcement; licensing infrastructure.

**Notes**  
A licensing system may interpret, issue or enforce terms carried by the record.

---

## REM-03-184 — Legal enforcement dependency

**Source**  
Section 16: “Enforcement may depend on applicable law.”

**Requirement**  
Enforcement of declared usage rights MAY depend on applicable law.

**Classification**  
External enforcement; legal framework.

**Notes**  
The protocol must not be treated as replacing legal rights, remedies or jurisdiction-specific obligations.

---

# 17. Record creation

## REM-03-185 — Valid schema required for creation

**Source**  
Section 17, creation requirement 1: “a valid schema”.

**Requirement**  
Creating a canonical Relay Record MUST require a valid schema.

**Classification**  
Record creation; schema validation.

**Notes**  
The schema must be sufficient to identify the record type, structure and applicable rules.

---

## REM-03-186 — Unique Record Key required for creation

**Source**  
Section 17, creation requirement 2: “a unique Record Key”.

**Requirement**  
Creating a canonical Relay Record MUST require a Record Key that is unique within the applicable repository and collection scope.

**Classification**  
Record creation; uniqueness; addressing.

**Notes**  
The source requires uniqueness but does not restate the complete uniqueness scope in this section; the repository and collection context is consistent with the record model.

---

## REM-03-187 — Schema-valid content required for creation

**Source**  
Section 17, creation requirement 3: “content that passes schema validation”.

**Requirement**  
Creating a canonical Relay Record MUST require content that passes validation against the declared schema.

**Classification**  
Record creation; content validation; schema conformance.

**Notes**  
Application usability or semantic preference does not substitute for schema validity.

---

## REM-03-188 — Valid visibility classification required for creation

**Source**  
Section 17, creation requirement 4: “a valid visibility classification”.

**Requirement**  
Creating a canonical Relay Record MUST require a valid visibility classification.

**Classification**  
Record creation; access control; visibility.

**Notes**  
The visibility must conform to the protocol and any schema-specific restrictions.

---

## REM-03-189 — Valid repository authority required for creation

**Source**  
Section 17, creation requirement 5: “valid repository authority”.

**Requirement**  
Creating a canonical Relay Record MUST require valid repository authority for the creation operation.

**Classification**  
Record creation; authority validation; repository control.

**Notes**  
An application’s ability to construct a record locally does not establish authority to make it canonical.

---

## REM-03-190 — Accepted commit required for creation

**Source**  
Section 17, creation requirement 6: “inclusion in an accepted commit”.

**Requirement**  
Creating a canonical Relay Record MUST require inclusion of the creation operation in an accepted repository commit.

**Classification**  
Record creation; commit history; canonical state.

**Notes**  
Repository acceptance is the transition from proposed or local state to canonical repository state.

---

## REM-03-191 — Local application generation is not canonical creation

**Source**  
Section 17: “A record is not canonical merely because an application generated it locally.”

**Requirement**  
A locally generated application object MUST NOT be treated as a canonical Relay Record solely because an application created it.

**Classification**  
Canonical state; application independence; repository authority.

**Notes**  
The object may be a draft or proposed operation until accepted by the repository.

---

## REM-03-192 — Repository acceptance establishes canonical state

**Source**  
Section 17: “It becomes canonical only when accepted by the repository.”

**Requirement**  
A record MUST become canonical only when accepted by the authoritative Relay Repository.

**Classification**  
Canonical state; repository acceptance; lifecycle.

**Notes**  
This rule applies regardless of which application or agent submitted the creation operation.

---

# 18. Record validation

## REM-03-193 — Multi-level validation model

**Source**  
Section 18: “Validation occurs at several levels.”

**Requirement**  
Relay record validation MUST distinguish multiple validation levels rather than treating all validity questions as one undifferentiated check.

**Classification**  
Validation architecture; separation of concerns.

**Notes**  
The source identifies envelope, schema, authority, repository-state and semantic validation.

---

## REM-03-194 — Envelope validation

**Source**  
Section 18.1: “Envelope validation — Checks protocol-level structure.”

**Requirement**  
Envelope validation MUST check the record’s protocol-level structure.

**Classification**  
Envelope validation; protocol conformance.

**Notes**  
Envelope validation is distinct from validating schema-defined content or application-specific meaning.

---

## REM-03-195 — URI validation

**Source**  
Section 18.1, example: “valid URI”.

**Requirement**  
Envelope validation SHOULD verify that protocol URIs used by the record are valid.

**Classification**  
Envelope validation; addressing.

**Notes**  
The source lists this as an example of envelope validation rather than a complete validation algorithm.

---

## REM-03-196 — Identifier validation

**Source**  
Section 18.1, example: “valid identifier”.

**Requirement**  
Envelope validation SHOULD verify that required protocol identifiers are valid.

**Classification**  
Envelope validation; identifier integrity.

**Notes**  
This may include repository, identity, collection or record identifiers as applicable.

---

## REM-03-197 — Required-metadata validation

**Source**  
Section 18.1, example: “required metadata”.

**Requirement**  
Envelope validation SHOULD verify that all required protocol metadata is present or validly inherited.

**Classification**  
Envelope validation; metadata completeness.

**Notes**  
The common required envelope information is defined earlier in the source model.

---

## REM-03-198 — Encoding validation

**Source**  
Section 18.1, example: “supported encoding”.

**Requirement**  
Envelope validation SHOULD verify that the record uses a supported encoding.

**Classification**  
Envelope validation; serialisation; interoperability.

**Notes**  
The final serialisation and encoding set remain subject to the broader protocol specification.

---

## REM-03-199 — Timestamp validation

**Source**  
Section 18.1, example: “valid timestamp”.

**Requirement**  
Envelope validation SHOULD verify that required timestamps are valid.

**Classification**  
Envelope validation; temporal metadata.

**Notes**  
Validity may include format, parseability and compliance with protocol timestamp rules.

---

## REM-03-200 — Schema validation

**Source**  
Section 18.2: “Schema validation — Checks the content against the declared schema.”

**Requirement**  
Schema validation MUST check record content against the record’s declared schema.

**Classification**  
Schema validation; content conformance.

**Notes**  
The declared schema, not the creating application’s private assumptions, governs schema validation.

---

## REM-03-201 — Required-field schema validation

**Source**  
Section 18.2, example: “required fields”.

**Requirement**  
Schema validation SHOULD verify the presence of all required schema fields.

**Classification**  
Schema validation; field completeness.

**Notes**  
Missing required fields should cause schema validation failure.

---

## REM-03-202 — Value-type schema validation

**Source**  
Section 18.2, example: “value types”.

**Requirement**  
Schema validation SHOULD verify that field values conform to their declared types.

**Classification**  
Schema validation; type safety.

**Notes**  
Type checking may apply to primitive, structured and reference values.

---

## REM-03-203 — Length-constraint schema validation

**Source**  
Section 18.2, example: “permitted lengths”.

**Requirement**  
Schema validation SHOULD verify compliance with permitted field or content lengths.

**Classification**  
Schema validation; constraint enforcement.

**Notes**  
Length rules must derive from the applicable schema.

---

## REM-03-204 — Reference-constraint schema validation

**Source**  
Section 18.2, example: “allowed references”.

**Requirement**  
Schema validation SHOULD verify that record references are permitted by the declared schema.

**Classification**  
Schema validation; referential constraints.

**Notes**  
This may include allowed reference types, targets or cardinality.

---

## REM-03-205 — Authority validation

**Source**  
Section 18.3: “Authority validation — Checks that the operation was authorised.”

**Requirement**  
Authority validation MUST determine whether the record operation was validly authorised.

**Classification**  
Authority validation; security; repository control.

**Notes**  
A structurally valid record must still fail if the operation lacks valid authority.

---

## REM-03-206 — Controller-signature validation

**Source**  
Section 18.3, example: “valid controller signature”.

**Requirement**  
Authority validation SHOULD verify any controller signature required for the operation.

**Classification**  
Authority validation; signature verification.

**Notes**  
The applicable operation or authorisation model determines whether a controller signature is required.

---

## REM-03-207 — Delegated-grant validation

**Source**  
Section 18.3, example: “valid delegated application grant”.

**Requirement**  
Authority validation SHOULD verify any delegated application grant relied upon by the submitter.

**Classification**  
Authority validation; delegation; application permissions.

**Notes**  
The grant must be valid for the submitting application and requested operation.

---

## REM-03-208 — Key-revocation validation

**Source**  
Section 18.3, example: “non-revoked key”.

**Requirement**  
Authority validation SHOULD verify that a signing or authorising key used for the operation has not been revoked.

**Classification**  
Authority validation; key management; security.

**Notes**  
A cryptographically correct signature from a revoked key must not be treated as currently authorised.

---

## REM-03-209 — Authorisation-scope validation

**Source**  
Section 18.3, example: “operation within scope”.

**Requirement**  
Authority validation SHOULD verify that the requested operation falls within the scope of the applicable authority or grant.

**Classification**  
Authority validation; scope enforcement; least privilege.

**Notes**  
A valid grant for one operation or collection must not automatically authorise unrelated operations.

---

## REM-03-210 — Repository-state validation

**Source**  
Section 18.4: “Repository-state validation — Checks the operation against current state.”

**Requirement**  
Repository-state validation MUST check the proposed operation against the repository’s current authoritative state.

**Classification**  
Repository-state validation; consistency; concurrency.

**Notes**  
This validation prevents operations that are structurally valid but inconsistent with current repository state.

---

## REM-03-211 — Record Key uniqueness validation

**Source**  
Section 18.4, example: “Record Key does not already exist”.

**Requirement**  
Repository-state validation SHOULD verify that a newly created Record Key has not already been used in the applicable scope.

**Classification**  
Repository-state validation; uniqueness.

**Notes**  
Later deletion rules may preserve used identifiers through tombstones, but those rules are outside this part.

---

## REM-03-212 — Current-version validation

**Source**  
Section 18.4, example: “version being updated is current”.

**Requirement**  
Repository-state validation SHOULD verify that the version targeted by an update is the current version expected by the operation.

**Classification**  
Repository-state validation; concurrency; versioning.

**Notes**  
This supports optimistic concurrency and prevents silent overwriting.

---

## REM-03-213 — Referenced-commit validation

**Source**  
Section 18.4, example: “referenced commit is valid”.

**Requirement**  
Repository-state validation SHOULD verify that any referenced repository commit is valid.

**Classification**  
Repository-state validation; commit integrity.

**Notes**  
Validity may include existence, repository membership and consistency with the operation’s expected state.

---

## REM-03-214 — Singleton-constraint validation

**Source**  
Section 18.4, example: “singleton constraints are respected”.

**Requirement**  
Repository-state validation SHOULD verify compliance with applicable singleton constraints.

**Classification**  
Repository-state validation; cardinality; schema behaviour.

**Notes**  
An operation must not create a second competing current singleton record where the schema permits only one.

---

## REM-03-215 — Optional semantic validation

**Source**  
Section 18.5: “An application may perform additional meaning-based checks.”

**Requirement**  
An application MAY perform additional semantic or meaning-based validation checks.

**Classification**  
Application validation; semantic checks; extensibility.

**Notes**  
These checks are optional and application-specific unless separately required by another policy or schema.

---

## REM-03-216 — Reachability semantic check

**Source**  
Section 18.5, example: “whether a URL is reachable”.

**Requirement**  
An application MAY check whether a referenced URL is reachable.

**Classification**  
Semantic validation; application behaviour.

**Notes**  
URL reachability is not equivalent to protocol validity and may change over time.

---

## REM-03-217 — Media-suitability semantic check

**Source**  
Section 18.5, example: “whether a media file is suitable”.

**Requirement**  
An application MAY check whether an associated media file is suitable for its intended context.

**Classification**  
Semantic validation; media policy; application behaviour.

**Notes**  
Suitability criteria may differ between applications without changing protocol validity.

---

## REM-03-218 — Community-policy semantic check

**Source**  
Section 18.5, example: “whether text violates community policy”.

**Requirement**  
An application MAY check whether record content violates its community policy.

**Classification**  
Semantic validation; moderation; application policy.

**Notes**  
A community-policy decision is not itself a protocol-structure or authority-validity decision.

---

## REM-03-219 — Semantic validation separate from protocol validity

**Source**  
Section 18.5: “Semantic validation is generally application-specific and must not be confused with protocol validity.”

**Requirement**  
Application-specific semantic validation MUST remain distinct from protocol validity.

**Classification**  
Validation boundary; application independence; interoperability.

**Notes**  
A protocol-valid record may be rejected or hidden by a particular application policy without becoming protocol-invalid.

---

# 19. Record update

## REM-03-220 — Update applies to an existing logical record

**Source**  
Section 19: “An update changes the content or metadata of an existing logical record.”

**Requirement**  
A record update MUST operate on an existing logical record and MUST change that record’s content, metadata or both.

**Classification**  
Record update; lifecycle; logical identity.

**Notes**  
An update preserves the logical Record URI while creating a new accepted version.

---

## REM-03-221 — Update Record URI identification

**Source**  
Section 19, update requirement: “the Record URI”.

**Requirement**  
An update operation MUST identify the Record URI of the logical record being updated.

**Classification**  
Record update; addressing; target identification.

**Notes**  
The Record URI identifies the continuing logical record, not merely a local application object.

---

## REM-03-222 — Replaced-version identification

**Source**  
Section 19, update requirement: “the version being replaced”.

**Requirement**  
An update operation MUST identify the Record Version being replaced.

**Classification**  
Record update; concurrency; versioning.

**Notes**  
This enables the repository to detect stale or conflicting updates.

---

## REM-03-223 — New-content identification

**Source**  
Section 19, update requirement: “the new content”.

**Requirement**  
An update operation that changes content MUST identify the proposed new content.

**Classification**  
Record update; content change; schema validation.

**Notes**  
Metadata-only updates are separately permitted in Section 19.2.

---

## REM-03-224 — Update-authority identification

**Source**  
Section 19, update requirement: “the authorising authority”.

**Requirement**  
An update operation MUST identify the authority authorising the update.

**Classification**  
Record update; authority; accountability.

**Notes**  
The repository must be able to validate that authority before accepting the update.

---

## REM-03-225 — Accepting-commit identification

**Source**  
Section 19, update requirement: “the commit accepting the update”.

**Requirement**  
An accepted record update MUST be identifiable by the repository commit that accepted it.

**Classification**  
Record update; commit history; integrity.

**Notes**  
The accepting commit anchors the new version in canonical repository history.

---

## REM-03-226 — Expected-current-version declaration

**Source**  
Section 19.1: “An update should state which current version it expects.”

**Requirement**  
An update operation SHOULD state which current Record Version it expects to replace.

**Classification**  
Optimistic concurrency; update safety; recommendation.

**Notes**  
The source uses “should”, establishing preferred concurrency-safe behaviour rather than an absolute requirement in all cases.

---

## REM-03-227 — Conflict rejection or explicit resolution

**Source**  
Section 19.1: “If the current version is already 4, the repository should reject the update or require explicit conflict resolution.”

**Requirement**  
Where the repository’s current version differs from the version expected by the update, the repository SHOULD reject the update or require explicit conflict resolution.

**Classification**  
Optimistic concurrency; conflict handling; recommendation.

**Notes**  
The repository should not silently apply a stale update over a newer accepted version.

---

## REM-03-228 — Prevention of silent overwriting

**Source**  
Section 19.1: “This prevents silent overwriting.”

**Requirement**  
The update process SHOULD prevent one update from silently overwriting a newer accepted record version.

**Classification**  
Concurrency safety; data integrity; recommendation.

**Notes**  
Expected-version checking and explicit conflict resolution are the mechanisms identified by the source.

---

## REM-03-229 — Visibility changes may create a new version

**Source**  
Section 19.2: changes to “visibility” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to record visibility MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning; access control.

**Notes**  
The source permits version creation for metadata-only changes.

---

## REM-03-230 — Audience changes may create a new version

**Source**  
Section 19.2: changes to “audience” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to the record audience MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning; audience control.

**Notes**  
Versioning audience changes preserves an auditable access-history transition.

---

## REM-03-231 — Rights changes may create a new version

**Source**  
Section 19.2: changes to “rights” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to record rights MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning; rights management.

**Notes**  
The source does not require every metadata change to create a version, but expressly permits it.

---

## REM-03-232 — Title changes may create a new version

**Source**  
Section 19.2: changes to “title” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to the record title MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning.

**Notes**  
Whether title is envelope metadata or schema content may depend on the applicable schema.

---

## REM-03-233 — Label changes may create a new version

**Source**  
Section 19.2: changes to “labels” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to record labels MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning; classification.

**Notes**  
Labels may affect discovery, moderation or application presentation while leaving primary content unchanged.

---

## REM-03-234 — Blob-reference changes may create a new version

**Source**  
Section 19.2: changes to “blob references” may create a new version even where primary content remains unchanged.

**Requirement**  
A change to blob references MAY create a new Record Version even when the primary content is unchanged.

**Classification**  
Metadata update; versioning; media references.

**Notes**  
This allows storage or associated binary references to change while preserving the logical record identity.

---

# 20. Immutable records

## REM-03-235 — Schema-defined immutability

**Source**  
Section 20: “Some schemas may define records as immutable after creation.”

**Requirement**  
A schema MAY define conforming records as immutable after creation.

**Classification**  
Schema behaviour; immutability; lifecycle.

**Notes**  
Immutability is schema-defined rather than universally imposed on every Relay Record.

---

## REM-03-236 — Immutable signed credentials

**Source**  
Section 20, example: “signed credentials”.

**Requirement**  
A schema MAY define signed credentials as immutable records.

**Classification**  
Immutability; credentials; example capability.

**Notes**  
The example is illustrative and does not require every credential schema to use identical lifecycle rules.

---

## REM-03-237 — Immutable historical attestations

**Source**  
Section 20, example: “historical attestations”.

**Requirement**  
A schema MAY define historical attestations as immutable records.

**Classification**  
Immutability; attestations; example capability.

**Notes**  
Immutability preserves the original historical assertion while allowing later revocation or supersession where supported.

---

## REM-03-238 — Immutable issued receipts

**Source**  
Section 20, example: “issued receipts”.

**Requirement**  
A schema MAY define issued receipts as immutable records.

**Classification**  
Immutability; receipts; example capability.

**Notes**  
Corrections may require a superseding or annotating record rather than rewriting the original receipt.

---

## REM-03-239 — Immutable completed audit events

**Source**  
Section 20, example: “completed audit events”.

**Requirement**  
A schema MAY define completed audit events as immutable records.

**Classification**  
Immutability; audit history; example capability.

**Notes**  
The purpose is to preserve the original event history rather than allow retrospective silent alteration.

---

## REM-03-240 — Revocation of immutable records

**Source**  
Section 20: “An immutable record may be revoked.”

**Requirement**  
An immutable record MAY be revoked without rewriting its original content.

**Classification**  
Immutability; revocation; lifecycle.

**Notes**  
Revocation changes the record’s current status while preserving the historical assertion.

---

## REM-03-241 — Supersession of immutable records

**Source**  
Section 20: “An immutable record may be superseded.”

**Requirement**  
An immutable record MAY be superseded by a later record without rewriting the original record.

**Classification**  
Immutability; supersession; lifecycle.

**Notes**  
The superseding record should preserve traceability to the original assertion.

---

## REM-03-242 — Annotation of immutable records

**Source**  
Section 20: “An immutable record may be annotated.”

**Requirement**  
An immutable record MAY be annotated without altering the original immutable content.

**Classification**  
Immutability; annotation; historical context.

**Notes**  
Annotations may add context, correction or status information while preserving the original record.

---

## REM-03-243 — Legally necessary deletion of immutable records

**Source**  
Section 20: “An immutable record may be... deleted where legally necessary.”

**Requirement**  
An immutable record MAY be deleted where deletion is legally necessary.

**Classification**  
Immutability; deletion; legal compliance.

**Notes**  
Immutability must not be interpreted as overriding mandatory legal deletion obligations.

---

## REM-03-244 — No silent rewriting of immutable records

**Source**  
Section 20: “It cannot be silently rewritten as though the original assertion had always been different.”

**Requirement**  
An immutable record MUST NOT be silently rewritten in a manner that presents the original assertion as though it had always contained different content.

**Classification**  
Immutability; historical integrity; auditability.

**Notes**  
Corrections or changes must be represented through explicit revocation, supersession, annotation or legally necessary deletion rather than concealed historical alteration.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 16–20 of `design-notes/03-record-model.md`.
- Section 21 and later deletion-model requirements were excluded.
- References to later tombstone or deletion behaviour appear only where needed to clarify scope and were not extracted as requirements in this part.

## Numbering verification

- First requirement: `REM-03-166`.
- Final requirement: `REM-03-244`.
- Requirement numbering continues directly from Part 3.
- Requirement identifiers are continuous, unique and ordered according to source sequence.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, example capability or necessary decomposition of a compound statement.
- Creation prerequisites, validation levels, update fields and metadata-update categories were extracted separately because each is independently testable.
- Illustrative examples were identified as examples and were not converted into universal mandatory schema types.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or options.
- Example validation checks use `SHOULD` or `MAY` rather than being overstated as exhaustive absolute requirements.

## Editorial verification

- Visibility remains separate from usage rights.
- Rights expression remains separate from guaranteed external enforcement.
- Local application generation remains separate from canonical repository acceptance.
- Envelope, schema, authority, repository-state and semantic validation remain distinct.
- Application-specific semantic rejection is not represented as protocol invalidity.
- Optimistic concurrency prevents silent overwriting without changing the stable logical Record URI.
- Immutable records may be revoked, superseded, annotated or legally deleted, but may not be silently rewritten.
