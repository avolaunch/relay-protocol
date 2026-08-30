# REM-03 Part 10 — Record Requirement Extraction Matrix (Sections 46–48)

## Document status

**Canonical editorial extraction**

This document extracts design obligations, provisional requirements and the governing record principle from Sections 46–48 of `design-notes/03-record-model.md`.

The source model is the sole source for the entries below. Section 46 contains unresolved design questions rather than settled protocol rules; these entries are therefore classified explicitly as **open design obligations** and must not be interpreted as final v0.1 decisions. Section 47 contains provisional assumptions, which remain subject to later resolution and specification refinement.

No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

46. Open design questions
47. Provisional decisions for v0.1
48. Core record principle

Requirement identifiers continue sequentially from Part 9, beginning with `REM-03-456`.

---

# 46. Open design questions

## REM-03-456 — Resolve envelope-field placement

**Source**  
Section 46.1: “Which fields belong directly inside every record, and which should be inherited from the containing commit or collection?”

**Requirement**  
The final Relay Record specification MUST determine which required fields are carried directly within each record and which may be inherited from an authoritative containing commit, collection or equivalent repository context.

**Classification**  
Open design obligation; envelope structure; inheritance.

**Notes**  
This is not a settled v0.1 rule. The resolution must preserve unambiguous access to all required record information regardless of whether it is embedded or inherited.

---

## REM-03-457 — Resolve individual record-signature requirements

**Source**  
Section 46.2: “Should records be individually signed in addition to being covered by a signed commit?”

**Requirement**  
The final Relay Record specification MUST determine whether individual records require signatures in addition to the authority and integrity protection supplied by signed repository commits.

**Classification**  
Open design obligation; signatures; integrity; authority proof.

**Notes**  
Section 47 provisionally treats signed commits as the minimum authority proof and individual signatures as optional for externally issued assertions.

---

## REM-03-458 — Resolve restricted-record enforcement mechanism

**Source**  
Section 46.3: “Should restricted records use repository access controls only, or require content-level encryption?”

**Requirement**  
The final Relay Record specification MUST determine whether restricted-record confidentiality relies on repository access controls, content-level encryption or a defined combination of both.

**Classification**  
Open design obligation; visibility enforcement; confidentiality.

**Notes**  
The decision must distinguish access-authorisation rules from cryptographic confidentiality guarantees.

---

## REM-03-459 — Resolve usage-rights vocabulary

**Source**  
Section 46.4: “Should Relay define a basic rights vocabulary, rely on existing licensing standards, or allow external vocabularies?”

**Requirement**  
The final Relay Record specification MUST determine whether usage rights are expressed through a Relay-defined vocabulary, recognised external licensing standards, externally defined vocabularies or a compatible combination of these approaches.

**Classification**  
Open design obligation; rights metadata; interoperability.

**Notes**  
The resolution must preserve the distinction between visibility and usage rights established earlier in the source model.

---

## REM-03-460 — Resolve minimum AI-provenance information

**Source**  
Section 46.5: “What minimum structured information should be required when a participating application declares AI involvement?”

**Requirement**  
The final Relay Record specification MUST define the minimum structured provenance information required when an application declares AI involvement in the creation or transformation of a record.

**Classification**  
Open design obligation; AI provenance; authorship disclosure.

**Notes**  
The source does not claim universal detection or proof of AI involvement. The unresolved issue concerns the minimum structure of a declared involvement record.

---

## REM-03-461 — Resolve historical-version retention rules

**Source**  
Section 46.6: “Which historical versions must remain retrievable, and which may be reduced to hashes or tombstones?”

**Requirement**  
The final Relay Record specification MUST define which historical Record Versions remain retrievable as content and which may be retained only through integrity hashes, tombstones or other minimum verification metadata.

**Classification**  
Open design obligation; history retention; deletion; integrity.

**Notes**  
The resolution must balance repository integrity, portability, storage constraints, privacy and legally required erasure.

---

## REM-03-462 — Resolve Relay core schema governance

**Source**  
Section 46.7: “Who may publish schemas under the Relay core namespace?”

**Requirement**  
The final Relay governance model MUST define who is authorised to publish, revise or retire schemas under the Relay core namespace.

**Classification**  
Open design obligation; schema governance; namespace authority.

**Notes**  
This question applies specifically to the Relay core namespace and does not negate permissionless third-party schema publication under independent namespaces.

---

## REM-03-463 — Resolve dynamic-audience evaluation and caching

**Source**  
Section 46.8: “How should relationship-based audiences be evaluated and cached?”

**Requirement**  
The final Relay Record specification MUST define how relationship-based dynamic audiences are evaluated and how any cached audience decisions are refreshed, invalidated or marked stale.

**Classification**  
Open design obligation; dynamic audiences; cache consistency; access control.

**Notes**  
The resolution must address whether access is evaluated at publication time, access time or according to another explicit rule.

---

## REM-03-464 — Resolve cross-repository transaction support

**Source**  
Section 46.9: “Can one operation safely require changes to records in two independent repositories?”

**Requirement**  
The final Relay architecture MUST determine whether a single logical operation may safely and atomically require record changes across two independent Relay Repositories.

**Classification**  
Open design obligation; distributed transactions; repository independence.

**Notes**  
The source leaves open whether such operations are supported, prohibited or represented through coordinated but independently committed actions.

---

## REM-03-465 — Resolve cross-identity record transfer semantics

**Source**  
Section 46.10: “Can a logical record ever move from one Relay Identity’s repository to another while preserving its identity, or should transfer always create a new record with provenance?”

**Requirement**  
The final Relay Record specification MUST determine whether a logical record may transfer between Relay Identities while preserving its Record URI or whether every cross-identity transfer creates a new logical record with explicit provenance linking it to the source.

**Classification**  
Open design obligation; record transfer; identity authority; provenance.

**Notes**  
The resolution must preserve clear authority history and must not allow transfer to disguise a change of controller or authorship.

---

# 47. Provisional decisions for v0.1

## REM-03-466 — JSON-compatible structured records

**Source**  
Section 47: “Relay v0.1 will provisionally assume: JSON-compatible structured records.”

**Requirement**  
Relay v0.1 SHOULD provisionally represent records using a JSON-compatible structured data model.

**Classification**  
Provisional v0.1 decision; serialisation model; structure.

**Notes**  
This establishes data-model compatibility, not necessarily one final canonical byte-level serialisation.

---

## REM-03-467 — Stable Record URIs

**Source**  
Section 47: “stable Record URIs”.

**Requirement**  
Relay v0.1 MUST provisionally use stable Record URIs for the persistent identity of logical records.

**Classification**  
Provisional v0.1 decision; identifier stability; portability.

**Notes**  
This assumption is consistent with the record invariants and the core record principle.

---

## REM-03-468 — Versioned schemas

**Source**  
Section 47: “versioned schemas”.

**Requirement**  
Relay v0.1 MUST provisionally support explicit schema versioning.

**Classification**  
Provisional v0.1 decision; schema evolution; compatibility.

**Notes**  
Schema identifiers should make the applicable schema version determinable.

---

## REM-03-469 — One current version per logical record

**Source**  
Section 47: “one current version per logical record”.

**Requirement**  
Relay v0.1 MUST provisionally maintain exactly one authoritative current version for each active logical record.

**Classification**  
Provisional v0.1 decision; version state; consistency.

**Notes**  
Conflicting proposed versions may be preserved as candidates, but they must not both be silently treated as one linear current continuation.

---

## REM-03-470 — Optimistic concurrency checks

**Source**  
Section 47: “optimistic concurrency checks”.

**Requirement**  
Relay v0.1 MUST provisionally use optimistic concurrency checks for record updates.

**Classification**  
Provisional v0.1 decision; concurrency; conflict prevention.

**Notes**  
An update should identify the version it expects to replace so stale updates can be rejected or explicitly reconciled.

---

## REM-03-471 — Signed commits as minimum authority proof

**Source**  
Section 47: “signed repository commits as the minimum authority proof”.

**Requirement**  
Relay v0.1 MUST provisionally treat a valid signed repository commit as the minimum authority proof for an accepted record operation.

**Classification**  
Provisional v0.1 decision; authority proof; commit integrity.

**Notes**  
This does not preclude stronger or additional signatures where required by a schema or assertion type.

---

## REM-03-472 — Optional signatures for externally issued assertions

**Source**  
Section 47: “optional individual record signatures for externally issued assertions”.

**Requirement**  
Relay v0.1 MAY provisionally support individual record signatures for externally issued assertions in addition to signed repository commits.

**Classification**  
Provisional v0.1 decision; issued assertions; signatures.

**Notes**  
The signature preserves the issuer’s claim independently of the holder repository’s authority to store the assertion.

---

## REM-03-473 — Four visibility classifications

**Source**  
Section 47: “public, unlisted, restricted and private visibility classifications”.

**Requirement**  
Relay v0.1 SHOULD provisionally support public, unlisted, restricted and private record visibility classifications.

**Classification**  
Provisional v0.1 decision; visibility; access control.

**Notes**  
These classifications do not by themselves determine usage rights or legal ownership.

---

## REM-03-474 — Logical deletion with tombstones

**Source**  
Section 47: “logical deletion with tombstones”.

**Requirement**  
Relay v0.1 MUST provisionally support logical deletion represented through tombstones or equivalent minimum persistent deletion records.

**Classification**  
Provisional v0.1 decision; deletion; repository history.

**Notes**  
The retained tombstone should preserve only the information necessary for integrity, deletion history and identifier non-reuse.

---

## REM-03-475 — No reuse of deleted Record Keys

**Source**  
Section 47: “no reuse of deleted Record Keys”.

**Requirement**  
Relay v0.1 MUST provisionally prohibit reuse of a deleted Record Key for a different logical record.

**Classification**  
Provisional v0.1 decision; identifier integrity; deletion.

**Notes**  
The associated tombstone preserves evidence that the identifier has already been used.

---

## REM-03-476 — Content-addressed blob references

**Source**  
Section 47: “content-addressed blob references”.

**Requirement**  
Relay v0.1 MUST provisionally identify referenced blobs through content-addressed identifiers rather than treating temporary storage URLs as permanent blob identity.

**Classification**  
Provisional v0.1 decision; blob identity; integrity; portability.

**Notes**  
Temporary retrieval locations may change without changing the blob’s logical content identity.

---

## REM-03-477 — Structured provenance

**Source**  
Section 47: “structured provenance”.

**Requirement**  
Relay v0.1 SHOULD provisionally support structured record provenance.

**Classification**  
Provisional v0.1 decision; provenance; traceability.

**Notes**  
Provenance declarations must continue to distinguish declared origin from independently verified authenticity.

---

## REM-03-478 — Preservation of unknown fields and schemas

**Source**  
Section 47: “preservation of unknown fields and schemas”.

**Requirement**  
Relay v0.1 MUST provisionally preserve valid but unknown fields, extensions and record schemas during storage, migration and round-trip processing.

**Classification**  
Provisional v0.1 decision; forward compatibility; portability.

**Notes**  
An implementation may decline to render or interpret an unknown type but must not damage or discard it solely because it is unknown.

---

## REM-03-479 — Acting-identity storage for replies, reactions and reposts

**Source**  
Section 47: “replies, reactions and reposts stored in the acting identity’s repository”.

**Requirement**  
Relay v0.1 SHOULD provisionally store replies, reactions and reposts in the repository of the identity that authorised the respective action record.

**Classification**  
Provisional v0.1 decision; ownership boundary; repository authority.

**Notes**  
The repository of the referenced content may index or display these records but does not become their canonical owner.

---

## REM-03-480 — Projections remain non-canonical unless explicitly saved

**Source**  
Section 47: “application projections remaining non-canonical unless explicitly saved”.

**Requirement**  
Relay v0.1 MUST provisionally treat application projections as non-canonical unless the controller explicitly saves and authorises them as repository records.

**Classification**  
Provisional v0.1 decision; projections; canonical state.

**Notes**  
Derived views, cards, rankings and recommendations must not automatically pollute the person’s canonical repository history.

---

## REM-03-481 — Moderation labels as separate records

**Source**  
Section 47: “moderation labels represented as separate records”.

**Requirement**  
Relay v0.1 SHOULD provisionally represent moderation labels as records separate from the target record.

**Classification**  
Provisional v0.1 decision; moderation; assertions; record separation.

**Notes**  
A moderation label does not rewrite the target record and may be trusted or ignored according to application policy.

---

## REM-03-482 — Schema rules layered over a common envelope

**Source**  
Section 47: “schema-specific rules layered on top of a common protocol envelope.”

**Requirement**  
Relay v0.1 MUST provisionally apply schema-specific content and behaviour rules on top of a common protocol-level Record Envelope.

**Classification**  
Provisional v0.1 decision; envelope architecture; schema layering.

**Notes**  
This preserves common identification, authority, visibility and integrity semantics while allowing schema-specific extensibility.

---

# 48. Core record principle

## REM-03-483 — Stable portable object under repository authority

**Source**  
Section 48: “A Relay Record is a stable, portable object under repository authority, not a disposable row inside the application that happened to create it.”

**Requirement**  
Every Relay Record MUST be treated as a stable and portable logical object governed by repository authority, and MUST NOT be treated as a disposable application-owned database row whose identity or continued existence depends on the application that created it.

**Classification**  
Core governing principle; portability; repository authority; application independence.

**Notes**  
This principle summarises the Record Model and governs interpretation of the more detailed requirements throughout REM-03.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 46–48 of `design-notes/03-record-model.md`.
- Section 46 entries remain explicitly classified as unresolved design obligations.
- Section 47 entries remain explicitly classified as provisional v0.1 decisions.
- Section 48 is represented as the governing core record principle.

## Numbering verification

- First requirement: `REM-03-456`.
- Final requirement: `REM-03-483`.
- Numbering continues directly from Part 9.
- Requirement identifiers are continuous and unique within this part.
- Across Parts 1–10, the intended REM-03 range is `REM-03-001` through `REM-03-483`.

## Traceability verification

- Every entry contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each Section 46 question maps to one explicit unresolved design obligation.
- Each Section 47 bullet maps to one explicit provisional decision.
- The Section 48 principle maps to one governing normative requirement.
- No answer to an open design question was invented or implied.

## Normative-language verification

- Open questions use `MUST determine` or `MUST define` to express the obligation to resolve the issue, not a predetermined answer.
- Provisional assumptions retain explicit provisional wording in both classification and requirement text.
- `MUST`, `SHOULD` and `MAY` are used according to the strength and character of the source statement.
- The core principle uses mandatory language because it is presented as the single rule to which the Record Model reduces.

## Closing REM-03 verification

- The ten REM-03 parts collectively cover source Sections 1–48 without an intended gap or overlap in section scope.
- Logical record identity remains separate from application ownership, schema authority, storage location and historical version identity.
- Repository acceptance remains the basis of canonical record state.
- Portability preserves operational meaning, not merely exported bytes.
- Unknown valid records and extensions remain preservable even where unsupported by a receiving application.
- The next source model identified by Section 48 is `design-notes/04-application-and-permission-model.md`.
