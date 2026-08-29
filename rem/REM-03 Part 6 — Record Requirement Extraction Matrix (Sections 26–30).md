# REM-03 Part 6 — Record Requirement Extraction Matrix (Sections 26–30)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 26–30 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

26. Embedded content
27. Blob references
28. Lists and ordering
29. Local application state
30. Draft records

Requirement identifiers continue sequentially from Part 5, beginning with `REM-03-282`.

---

# 26. Embedded content

## REM-03-282 — Limited embedded representation

**Source**  
Section 26: “A record may contain a limited embedded representation of another object.”

**Requirement**  
A Relay Record MAY contain a limited embedded representation of another object.

**Classification**  
Embedding; content modelling; interoperability.

**Notes**  
The source permits limited representations such as quoted text, thumbnails, preview titles or an author handle observed at publication time. An embed is not a complete replacement for the referenced source object.

---

## REM-03-283 — Embedded quoted text

**Source**  
Section 26, examples: “quoted text”.

**Requirement**  
An embedded representation MAY include quoted text from another object.

**Classification**  
Embedding; quotation; content representation.

**Notes**  
Where exact historical fidelity matters, the embed should be associated with the observed source version and observation time.

---

## REM-03-284 — Embedded thumbnail

**Source**  
Section 26, examples: “thumbnail”.

**Requirement**  
An embedded representation MAY include a thumbnail associated with another object.

**Classification**  
Embedding; media preview.

**Notes**  
The thumbnail may be a historical preview and must not be assumed to reflect the current source object indefinitely.

---

## REM-03-285 — Embedded preview title

**Source**  
Section 26, examples: “preview title”.

**Requirement**  
An embedded representation MAY include a preview title associated with another object.

**Classification**  
Embedding; preview metadata.

**Notes**  
The preview title may preserve the value observed when the embed was created even if the source title later changes.

---

## REM-03-286 — Embedded historical author handle

**Source**  
Section 26, examples: “author handle at time of publication”.

**Requirement**  
An embedded representation MAY preserve the author handle observed at the time of publication or embedding.

**Classification**  
Embedding; historical metadata; identity presentation.

**Notes**  
A historical handle is not necessarily the identity’s current handle and must not replace the stable Relay Identity identifier where identity verification is required.

---

## REM-03-287 — Provenance for embedded content

**Source**  
Section 26: “Embedded content should include provenance.”

**Requirement**  
Embedded content SHOULD include provenance sufficient to identify its source and observation context.

**Classification**  
Provenance; embedding; recommendation.

**Notes**  
Useful provenance may include the source Record URI, observed version and observation time, as illustrated by the source example.

---

## REM-03-288 — Embedded source reference

**Source**  
Section 26 example: `"source": "relay://..."`.

**Requirement**  
Where an embed derives from a Relay Record, its provenance SHOULD identify the source Record URI.

**Classification**  
Provenance; referential integrity; recommendation.

**Notes**  
The example is informative, but identifying the source is necessary to make the provenance useful and auditable.

---

## REM-03-289 — Embedded observed-version reference

**Source**  
Section 26 example: `"observedVersion": 2`.

**Requirement**  
Where an embed represents a specific observed historical state, its provenance SHOULD identify the observed Record Version.

**Classification**  
Version provenance; embedding; recommendation.

**Notes**  
Version identification prevents later source updates from being mistaken for the state originally embedded.

---

## REM-03-290 — Embedded observation time

**Source**  
Section 26 example: `"observedAt": "2026-08-24T10:00:00Z"`.

**Requirement**  
Embedded-content provenance SHOULD identify when the source state was observed.

**Classification**  
Temporal provenance; embedding; recommendation.

**Notes**  
Observation time is especially useful where the embedded representation may diverge from the source’s later state.

---

## REM-03-291 — Embed as historical observation

**Source**  
Section 26: “An embed is a historical observation, not necessarily the current state of the source record.”

**Requirement**  
An application MUST treat an embed as a historical observation and MUST NOT assume that it necessarily represents the current state of the source record.

**Classification**  
Historical state; application behaviour; consistency.

**Notes**  
Applications may separately resolve the source Record URI to obtain current state, but must not silently overwrite the historical meaning of the embed.

---

# 27. Blob references

## REM-03-292 — Blob-reference support

**Source**  
Section 27: “A record may refer to one or more blobs.”

**Requirement**  
A Relay Record MAY refer to one or more blobs.

**Classification**  
Blob handling; media; content storage.

**Notes**  
Blobs may hold binary or large content while the record retains protocol metadata and references.

---

## REM-03-293 — Blob identifier

**Source**  
Section 27: “Blob references should include: blob identifier...”

**Requirement**  
A blob reference SHOULD include a blob identifier.

**Classification**  
Blob identity; recommendation.

**Notes**  
The blob identifier should provide stable identity independent of a temporary delivery URL.

---

## REM-03-294 — Blob media type

**Source**  
Section 27: “Blob references should include... media type...”

**Requirement**  
A blob reference SHOULD include the blob’s media type.

**Classification**  
Media metadata; interoperability; recommendation.

**Notes**  
Media type enables applications to determine whether and how they can process or present the referenced content.

---

## REM-03-295 — Blob intended role

**Source**  
Section 27: “Blob references should include... intended role...”

**Requirement**  
A blob reference SHOULD identify the intended role or purpose of the blob within the record.

**Classification**  
Media semantics; schema interpretation; recommendation.

**Notes**  
Examples may include primary image, attachment, thumbnail or another schema-defined purpose.

---

## REM-03-296 — Blob accessibility metadata

**Source**  
Section 27: “Blob references should include... accessibility metadata where applicable...”

**Requirement**  
A blob reference SHOULD include accessibility metadata where applicable.

**Classification**  
Accessibility; media metadata; recommendation.

**Notes**  
The example uses alternative text for an image. Other media may require captions, transcripts or schema-specific accessibility information.

---

## REM-03-297 — Optional blob dimensions or duration

**Source**  
Section 27: “Blob references should include... optional dimensions or duration...”

**Requirement**  
A blob reference MAY include dimensions or duration where relevant to the referenced media.

**Classification**  
Media metadata; optional enrichment.

**Notes**  
Dimensions are relevant to visual media, while duration is relevant to audio, video or time-based media.

---

## REM-03-298 — Blob integrity hash

**Source**  
Section 27: “Blob references should include... integrity hash.”

**Requirement**  
A blob reference SHOULD include an integrity hash.

**Classification**  
Integrity; blob verification; recommendation.

**Notes**  
The hash enables applications or repositories to verify that retrieved blob content matches the referenced object.

---

## REM-03-299 — Temporary URL not permanent blob identity

**Source**  
Section 27: “The record must not treat a temporary storage URL as the blob’s permanent identity.”

**Requirement**  
A Relay Record MUST NOT treat a temporary storage or delivery URL as the permanent identity of a blob.

**Classification**  
Blob identity; storage independence; portability.

**Notes**  
Temporary URLs may expire, rotate or change providers. Stable blob identity must remain independent of the current retrieval location.

---

# 28. Lists and ordering

## REM-03-300 — Ordered-item support

**Source**  
Section 28: “Some records contain ordered items.”

**Requirement**  
The Relay Record Model MUST support schemas for records containing ordered items.

**Classification**  
Ordering; schema behaviour; content modelling.

**Notes**  
Examples include portfolio ordering, image galleries, playlists and article sections.

---

## REM-03-301 — Schema-defined ordering model

**Source**  
Section 28: “The schema must define whether ordering is...”

**Requirement**  
A schema governing ordered items MUST define how ordering is represented or derived.

**Classification**  
Schema definition; ordering semantics; validation.

**Notes**  
The source identifies three permitted models: ordering as record content, ordering derived by an application, or ordering maintained through separate relationship records.

---

## REM-03-302 — Ordering as record content

**Source**  
Section 28: ordering may be “part of the record content”.

**Requirement**  
A schema MAY define ordering as part of the record content.

**Classification**  
Ordering; schema-specific behaviour.

**Notes**  
Under this model, changes to order may constitute changes to the record content and may create a new version.

---

## REM-03-303 — Application-derived ordering

**Source**  
Section 28: ordering may be “derived by an application”.

**Requirement**  
A schema MAY define that ordering is derived by an application rather than stored canonically in the record.

**Classification**  
Application behaviour; ordering; schema-specific behaviour.

**Notes**  
Applications must not imply that an application-derived order is repository-wide canonical order unless the schema establishes that meaning.

---

## REM-03-304 — Relationship-record ordering

**Source**  
Section 28: ordering may be “maintained through separate relationship records”.

**Requirement**  
A schema MAY define that ordering is maintained through separate relationship records.

**Classification**  
Relationship modelling; ordering; schema-specific behaviour.

**Notes**  
This allows order to be changed independently of the primary items being ordered.

---

## REM-03-305 — No assumed repository-wide order

**Source**  
Section 28: “Applications should not assume a repository-wide universal order where the schema does not define one.”

**Requirement**  
Applications SHOULD NOT assume a repository-wide universal order where the applicable schema does not define one.

**Classification**  
Application behaviour; ordering; recommendation.

**Notes**  
Display order may be local, contextual or application-derived unless the schema establishes canonical ordering semantics.

---

# 29. Local application state

## REM-03-306 — Canonical repository exclusion for some preferences

**Source**  
Section 29: “Not every application preference belongs in the canonical Relay Repository.”

**Requirement**  
Applications MUST NOT assume that every application preference or implementation detail belongs in the canonical Relay Repository.

**Classification**  
Repository scope; application state; data minimisation.

**Notes**  
Examples that may remain local include window size, dismissed-tooltip state, temporary draft position and client-specific cache configuration.

---

## REM-03-307 — Local window-size state

**Source**  
Section 29, examples: “window size”.

**Requirement**  
Application window-size state MAY remain local to the application.

**Classification**  
Local state; user interface preference.

**Notes**  
This example is illustrative of state that often has little portability or continuity value.

---

## REM-03-308 — Local dismissed-tooltip state

**Source**  
Section 29, examples: “dismissed tooltip state”.

**Requirement**  
Dismissed-tooltip state MAY remain local to the application.

**Classification**  
Local state; user interface preference.

**Notes**  
Such state generally concerns one application’s interface rather than the person’s portable digital record.

---

## REM-03-309 — Local temporary draft position

**Source**  
Section 29, examples: “temporary draft position”.

**Requirement**  
Temporary draft-position state MAY remain local to the application.

**Classification**  
Local state; editing state.

**Notes**  
This does not prevent a repository or schema from supporting portable drafts; it distinguishes transient editing position from canonical record content.

---

## REM-03-310 — Local cache configuration

**Source**  
Section 29, examples: “client-specific cache configuration”.

**Requirement**  
Client-specific cache configuration MAY remain local to the application.

**Classification**  
Local state; implementation detail.

**Notes**  
Cache configuration is typically an application implementation concern rather than portable user-controlled state.

---

## REM-03-311 — Portability-value test for canonical inclusion

**Source**  
Section 29: “A record belongs in the canonical repository when portability or continuity provides meaningful user value.”

**Requirement**  
Information or state SHOULD be stored in the canonical Relay Repository when preserving it across applications provides meaningful portability or continuity value to the user.

**Classification**  
Repository scope; portability; recommendation.

**Notes**  
The criterion focuses on user value rather than technical possibility.

---

## REM-03-312 — Discouragement of irrelevant implementation details

**Source**  
Section 29: “The protocol should discourage applications from filling the repository with irrelevant implementation details.”

**Requirement**  
The protocol SHOULD discourage applications from storing irrelevant implementation details in the canonical Relay Repository.

**Classification**  
Data minimisation; repository hygiene; recommendation.

**Notes**  
Excess local-state records can reduce clarity, portability and long-term repository usefulness.

---

## REM-03-313 — Reasonable survival expectation test

**Source**  
Section 29: “Would the person reasonably expect this information or state to survive when changing applications?”

**Requirement**  
Applications SHOULD evaluate canonical inclusion by asking whether the person would reasonably expect the information or state to survive a change of application.

**Classification**  
Repository scope; user expectation; recommendation.

**Notes**  
The test is editorial guidance for deciding whether state has meaningful portability or continuity value.

---

## REM-03-314 — Local retention where survival is not expected

**Source**  
Section 29: “If not, it may remain local.”

**Requirement**  
Information or state MAY remain local where a person would not reasonably expect it to survive a change of application.

**Classification**  
Local state; repository scope.

**Notes**  
This is permission, not a prohibition on portability. A schema or user choice may still justify canonical storage in a particular case.

---

# 30. Draft records

## REM-03-315 — Local draft creation before acceptance

**Source**  
Section 30: “Applications may create local drafts before repository acceptance.”

**Requirement**  
Applications MAY create local draft records before repository acceptance.

**Classification**  
Draft lifecycle; local state; application behaviour.

**Notes**  
Local drafting allows incomplete work to exist before it becomes a canonical repository record.

---

## REM-03-316 — Draft non-canonicity before commit

**Source**  
Section 30: “A draft is not canonical until committed.”

**Requirement**  
A draft MUST NOT be treated as canonical until it has been included in an accepted repository commit.

**Classification**  
Canonical state; draft lifecycle; repository authority.

**Notes**  
Local persistence or application synchronisation alone does not establish canonical repository acceptance.

---

## REM-03-317 — Optional private repository drafts

**Source**  
Section 30: “A repository may optionally support private draft records.”

**Requirement**  
A Relay Repository MAY support private draft records.

**Classification**  
Repository capability; drafts; privacy.

**Notes**  
This capability is optional. A private repository-supported draft remains distinct from a fully canonical published or active record where the schema or workflow makes that distinction.

---

## REM-03-318 — Draft incompleteness indication

**Source**  
Section 30: “A draft should clearly indicate... that it is incomplete.”

**Requirement**  
A draft SHOULD clearly indicate that it is incomplete.

**Classification**  
Draft metadata; user disclosure; recommendation.

**Notes**  
Applications should not present draft content as final or complete where that status is material to the user.

---

## REM-03-319 — Draft synchronisation indication

**Source**  
Section 30: “A draft should clearly indicate... whether it is synchronised.”

**Requirement**  
A draft SHOULD clearly indicate whether it has been synchronised.

**Classification**  
Draft metadata; synchronisation; recommendation.

**Notes**  
Synchronisation status is distinct from canonical repository acceptance.

---

## REM-03-320 — Draft creating-application indication

**Source**  
Section 30: “A draft should clearly indicate... which application created it.”

**Requirement**  
A draft SHOULD identify the application that created it.

**Classification**  
Draft provenance; application accountability; recommendation.

**Notes**  
This helps users and other applications understand draft origin and compatibility expectations.

---

## REM-03-321 — Cross-application draft-editability indication

**Source**  
Section 30: “A draft should clearly indicate... whether another application may edit it.”

**Requirement**  
A draft SHOULD clearly indicate whether another application is permitted to edit it.

**Classification**  
Draft permissions; interoperability; recommendation.

**Notes**  
Editability may depend on schema support, repository authority, application grants and draft format compatibility.

---

## REM-03-322 — No false canonical-storage representation

**Source**  
Section 30: “Applications must not present unsynchronised local drafts as safely stored canonical records.”

**Requirement**  
Applications MUST NOT present unsynchronised local drafts as safely stored canonical Relay Records.

**Classification**  
User disclosure; draft safety; canonical state.

**Notes**  
Applications must accurately distinguish local-only state from repository-accepted canonical state so that users are not misled about durability, portability or recoverability.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 26–30 of `design-notes/03-record-model.md`.
- Section 31 and later content was excluded.
- Source examples were used only to clarify the model and were not promoted into mandatory final syntax.

## Numbering verification

- First requirement: `REM-03-282`.
- Final requirement: `REM-03-322`.
- Requirement numbering continues directly from Part 5.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, example category or necessary decomposition of a compound statement.
- Recommended blob metadata and draft metadata remain `SHOULD` requirements.
- Optional embedding, ordering, local-state and draft capabilities remain `MAY` requirements.

## Normative-language verification

- Source “must” and categorical prohibitions are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` or `SHOULD NOT` recommendations.
- Source “may” and “optionally” statements are preserved as `MAY` permissions.
- Descriptive statements were converted into testable requirements without strengthening optional source language.

## Editorial verification

- Embedded representations remain historical observations rather than assumed live source state.
- Stable blob identity remains independent of temporary storage URLs.
- Ordering semantics remain schema-defined rather than repository-wide by assumption.
- Canonical repository scope is guided by meaningful user portability and continuity value.
- Local drafts, synchronised drafts and canonical committed records remain clearly distinguished.
