# REM-03 Part 3 — Record Requirement Extraction Matrix (Sections 11–15)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 11–15 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

11. Issued assertions
12. Record provenance
13. Human, assisted and automated creation
14. Visibility model
15. Audience

Requirement identifiers continue sequentially from Part 2, beginning with `REM-03-099`.

---

# 11. Issued assertions

## REM-03-099 — Support for externally issued assertions

**Source**  
Section 11: “Some records are assertions made by another identity.”

**Requirement**  
The Relay Record Model MUST support records containing assertions made by an identity other than the record subject.

**Classification**  
Assertions; external authority; identity modelling.

**Notes**  
Examples include qualifications, employment confirmations, professional licences and moderation labels.

---

## REM-03-100 — Issuer identification

**Source**  
Section 11: “Such a record must distinguish: issuer...”

**Requirement**  
An issued assertion record MUST identify the issuer of the assertion.

**Classification**  
Assertion provenance; issuer identity; accountability.

**Notes**  
The issuer is the identity making and signing the claim, not necessarily the holder repository or subject.

---

## REM-03-101 — Assertion subject identification

**Source**  
Section 11: “Such a record must distinguish: ... subject...”

**Requirement**  
An issued assertion record MUST identify the subject to whom or to which the assertion applies.

**Classification**  
Subject identification; assertion semantics.

**Notes**  
The subject may be a Relay Identity or another protocol-addressable object where the schema permits.

---

## REM-03-102 — Holder repository identification

**Source**  
Section 11: “Such a record must distinguish: ... holder repository...”

**Requirement**  
An issued assertion record MUST identify the repository holding the assertion record.

**Classification**  
Repository context; assertion storage; portability.

**Notes**  
The holder repository may belong to the assertion subject, but holding the record does not make the holder its issuer.

---

## REM-03-103 — Issuance-time identification

**Source**  
Section 11: “Such a record must distinguish: ... issuance time...”

**Requirement**  
An issued assertion record MUST identify the time at which the assertion was issued.

**Classification**  
Temporal metadata; assertion lifecycle.

**Notes**  
Issuance time is distinct from the time at which the record was imported into or accepted by the holder repository.

---

## REM-03-104 — Expiration representation

**Source**  
Section 11: “Such a record must distinguish: ... expiration...”

**Requirement**  
An issued assertion record MUST represent whether the assertion expires and, where applicable, its expiration time or condition.

**Classification**  
Assertion lifecycle; validity period.

**Notes**  
A non-expiring assertion may represent expiration explicitly as absent or null according to the applicable schema.

---

## REM-03-105 — Revocation-status representation

**Source**  
Section 11: “Such a record must distinguish: ... revocation status...”

**Requirement**  
An issued assertion record MUST represent its revocation status.

**Classification**  
Assertion lifecycle; trust; verification.

**Notes**  
The source requires the status to be distinguishable but does not prescribe the revocation-resolution mechanism in this section.

---

## REM-03-106 — Issuer-signature representation

**Source**  
Section 11: “Such a record must distinguish: ... issuer signature.”

**Requirement**  
An issued assertion record MUST contain or reference an issuer signature capable of binding the issuer to the signed assertion.

**Classification**  
Cryptographic integrity; issuer authentication; verification.

**Notes**  
The signature must protect the issuer’s claim against undetected alteration.

---

## REM-03-107 — Holder storage permission

**Source**  
Section 11: “The holder may store the credential in their repository...”

**Requirement**  
A holder MAY store an issued assertion or credential in the holder’s Relay Repository.

**Classification**  
Credential storage; repository control; portability.

**Notes**  
Storage by the holder does not transfer issuer authority or permit modification of the signed claim.

---

## REM-03-108 — Signed-claim immutability

**Source**  
Section 11: “...but cannot alter the issuer’s signed claim without invalidating it.”

**Requirement**  
A holder or other non-issuer MUST NOT alter the issuer’s signed claim while continuing to represent the issuer signature as valid.

**Classification**  
Integrity; assertion immutability; signature validity.

**Notes**  
Any alteration to signed claim content must invalidate the original signature unless the issuer signs the altered content as a new assertion.

---

# 12. Record provenance

## REM-03-109 — Structured provenance support

**Source**  
Section 12: “Every record should support structured provenance.”

**Requirement**  
Every Relay Record SHOULD support structured provenance information.

**Classification**  
Provenance; transparency; recommendation.

**Notes**  
The source uses “should”, so structured provenance is a strong recommendation rather than an unconditional validity requirement for every schema.

---

## REM-03-110 — Direct-creation provenance

**Source**  
Section 12: provenance may identify “whether it was created directly”.

**Requirement**  
Record provenance MAY indicate that the record was created directly rather than imported or derived.

**Classification**  
Creation provenance; origin declaration.

**Notes**  
A direct-creation declaration describes origin method and does not by itself verify authorship.

---

## REM-03-111 — Import provenance

**Source**  
Section 12: provenance may identify “whether it was imported”.

**Requirement**  
Record provenance MAY indicate that the record was imported.

**Classification**  
Import provenance; migration; origin declaration.

**Notes**  
Imported status should be distinguishable from direct creation in the holder repository.

---

## REM-03-112 — Originating-service provenance

**Source**  
Section 12: provenance may identify “the originating service”.

**Requirement**  
Record provenance MAY identify the service from which the record or its source material originated.

**Classification**  
Source provenance; service origin.

**Notes**  
A named service is a declared source and is not automatically proof that the service supplied or authenticated the material.

---

## REM-03-113 — Source-record provenance

**Source**  
Section 12: provenance may identify “a source record”.

**Requirement**  
Record provenance MAY reference a source record from which the Relay Record was imported, copied, derived or transformed.

**Classification**  
Derivation provenance; record references; traceability.

**Notes**  
Where possible, the source record should be identified using a stable reference.

---

## REM-03-114 — Source-file provenance

**Source**  
Section 12: provenance may identify “a source file”.

**Requirement**  
Record provenance MAY identify a source file used to create, import or transform the record.

**Classification**  
File provenance; derivation traceability.

**Notes**  
The applicable schema may determine whether the file is embedded, externally referenced or represented by an integrity hash.

---

## REM-03-115 — AI-system involvement provenance

**Source**  
Section 12: provenance may identify “an AI system involved”.

**Requirement**  
Record provenance MAY identify an AI system involved in creating, editing, transforming or processing the record.

**Classification**  
AI provenance; creation transparency.

**Notes**  
Identification of an AI system does not, by itself, establish the extent or nature of its contribution.

---

## REM-03-116 — Transformation-process provenance

**Source**  
Section 12: provenance may identify “a transformation process”.

**Requirement**  
Record provenance MAY identify a process through which source material was transformed into the current record.

**Classification**  
Transformation provenance; processing history.

**Notes**  
Examples may include conversion, summarisation, redaction, editing or schema migration.

---

## REM-03-117 — Migration-event provenance

**Source**  
Section 12: provenance may identify “a migration event”.

**Requirement**  
Record provenance MAY identify a migration event affecting the record.

**Classification**  
Migration provenance; repository history; portability.

**Notes**  
Migration provenance can distinguish original creation from later movement between services, repositories or providers.

---

## REM-03-118 — Declared source is not automatic proof

**Source**  
Section 12.1: “A declared source does not automatically prove that the source is authentic.”

**Requirement**  
An implementation MUST NOT treat a declared provenance source as automatically authenticated or verified solely because it appears in the record.

**Classification**  
Trust boundaries; provenance verification; security.

**Notes**  
Source declaration and source verification are separate protocol concepts.

---

## REM-03-119 — Self-declared provenance level

**Source**  
Section 12.1: provenance may be “self-declared”.

**Requirement**  
The provenance model MAY represent provenance information as self-declared.

**Classification**  
Provenance assurance level; self-attestation.

**Notes**  
Self-declared provenance reflects a statement by the controller or record creator without independent attestation.

---

## REM-03-120 — Application-attested provenance level

**Source**  
Section 12.1: provenance may be “application-attested”.

**Requirement**  
The provenance model MAY represent provenance information as attested by an application.

**Classification**  
Provenance assurance level; application attestation.

**Notes**  
Trust in an application-attested claim depends on the application’s identity, authority and attestation mechanism.

---

## REM-03-121 — Cryptographically verified provenance level

**Source**  
Section 12.1: provenance may be “cryptographically verified”.

**Requirement**  
The provenance model MAY represent provenance information as cryptographically verified.

**Classification**  
Provenance assurance level; cryptographic verification.

**Notes**  
Cryptographic verification should identify what was verified and by which key or authority.

---

## REM-03-122 — Externally issued provenance level

**Source**  
Section 12.1: provenance may be “externally issued”.

**Requirement**  
The provenance model MAY represent provenance information as externally issued by another identity or authority.

**Classification**  
Provenance assurance level; external assertion.

**Notes**  
Externally issued provenance should retain the issuer information and integrity evidence needed to evaluate the claim.

---

## REM-03-123 — Provenance-assurance-level indication

**Source**  
Section 12.1: “The record should indicate which level applies.”

**Requirement**  
A record containing provenance information SHOULD indicate the applicable provenance assurance level.

**Classification**  
Provenance transparency; trust signalling; recommendation.

**Notes**  
At minimum, consumers should be able to distinguish self-declaration from application attestation, cryptographic verification and external issuance.

---

# 13. Human, assisted and automated creation

## REM-03-124 — Multiple creation modes

**Source**  
Section 13: “Relay records may be created through different forms of authorship.”

**Requirement**  
The Relay Record Model MAY represent multiple forms of human, assisted, automated, imported or unknown creation.

**Classification**  
Creation provenance; authorship modes; extensibility.

**Notes**  
The source presents a non-exclusive set of possible declarations.

---

## REM-03-125 — Human-created declaration

**Source**  
Section 13, possible declaration: `human-created`.

**Requirement**  
A record MAY declare a `human-created` creation mode.

**Classification**  
Creation mode; human authorship declaration.

**Notes**  
The declaration alone does not constitute universal proof that no automated tool contributed.

---

## REM-03-126 — Human-assisted declaration

**Source**  
Section 13, possible declaration: `human-assisted`.

**Requirement**  
A record MAY declare a `human-assisted` creation mode.

**Classification**  
Creation mode; assisted authorship.

**Notes**  
This mode may be used where a human remains the principal creator while receiving tool assistance.

---

## REM-03-127 — AI-assisted declaration

**Source**  
Section 13, possible declaration: `AI-assisted`.

**Requirement**  
A record MAY declare an `AI-assisted` creation mode.

**Classification**  
Creation mode; AI assistance.

**Notes**  
The record may additionally identify the AI system and its role.

---

## REM-03-128 — AI-generated declaration

**Source**  
Section 13, possible declaration: `AI-generated`.

**Requirement**  
A record MAY declare an `AI-generated` creation mode.

**Classification**  
Creation mode; automated generation.

**Notes**  
The applicable schema or provenance model may provide more detail about prompts, tools or human review.

---

## REM-03-129 — Automated declaration

**Source**  
Section 13, possible declaration: `automated`.

**Requirement**  
A record MAY declare an `automated` creation mode.

**Classification**  
Creation mode; automation.

**Notes**  
Automation is broader than AI generation and may include deterministic systems, sensors or scheduled processes.

---

## REM-03-130 — Imported declaration

**Source**  
Section 13, possible declaration: `imported`.

**Requirement**  
A record MAY declare an `imported` creation mode.

**Classification**  
Creation mode; import provenance.

**Notes**  
An imported declaration should be supplemented with source and import details where available.

---

## REM-03-131 — Unknown declaration

**Source**  
Section 13, possible declaration: `unknown`.

**Requirement**  
A record MAY declare its creation mode as `unknown` when the mode cannot be determined or responsibly asserted.

**Classification**  
Creation mode; uncertainty representation.

**Notes**  
An explicit unknown value is preferable to unsupported inference.

---

## REM-03-132 — No style-only inference

**Source**  
Section 13: “These labels must not be inferred solely from style or content.”

**Requirement**  
An implementation MUST NOT assign a human, assisted, AI-generated, automated, imported or equivalent creation label solely by analysing the style or content of the record.

**Classification**  
Inference limitation; authorship integrity; safety.

**Notes**  
Content analysis may inform a separate probabilistic assessment, but it must not be presented as the record’s declared creation mode without an authorised declaration or attestation.

---

## REM-03-133 — Controller declaration

**Source**  
Section 13: creation labels “should be declared by: the controller...”

**Requirement**  
A creation-mode declaration SHOULD be capable of being made by the record controller.

**Classification**  
Creation declaration; controller authority; recommendation.

**Notes**  
The declaration’s assurance level should indicate that it is controller-declared where applicable.

---

## REM-03-134 — Submitter declaration

**Source**  
Section 13: creation labels “should be declared by: ... the submitting application...”

**Requirement**  
A creation-mode declaration SHOULD be capable of being made or attested by the submitting application.

**Classification**  
Creation declaration; application attestation; recommendation.

**Notes**  
The application should identify its role and the basis for the declaration.

---

## REM-03-135 — Trusted creation-system declaration

**Source**  
Section 13: creation labels “should be declared by: ... a trusted creation system...”

**Requirement**  
A creation-mode declaration SHOULD be capable of being made or attested by a trusted creation system.

**Classification**  
Creation declaration; trusted-system attestation; recommendation.

**Notes**  
Trust in the declaration depends on the creation system’s identity and integrity mechanisms.

---

## REM-03-136 — External verification-service declaration

**Source**  
Section 13: creation labels “should be declared by: ... an external verification service.”

**Requirement**  
A creation-mode declaration SHOULD be capable of being issued or attested by an external verification service.

**Classification**  
Creation declaration; external verification; recommendation.

**Notes**  
The record should distinguish an external attestation from a controller or application declaration.

---

## REM-03-137 — Rich creation-tool information

**Source**  
Section 13: “A Relay record may contain richer information...” including tool name and role.

**Requirement**  
A Relay Record MAY include structured details about tools involved in creation and the role performed by each tool.

**Classification**  
Creation provenance; tool disclosure; extensibility.

**Notes**  
Examples of roles may include drafting, editing, translation, generation, enhancement or verification.

---

## REM-03-138 — Preservation of creation declarations

**Source**  
Section 13: “Relay v0.1 should preserve these declarations...”

**Requirement**  
Relay v0.1 SHOULD preserve authorised creation-mode declarations and associated creation metadata across record handling and migration.

**Classification**  
Provenance preservation; portability; recommendation.

**Notes**  
Preservation should include the declarant or attester and the applicable assurance level where available.

---

## REM-03-139 — No universal human-authorship claim

**Source**  
Section 13: Relay v0.1 “must not claim to solve universal proof of human authorship.”

**Requirement**  
Relay v0.1 MUST NOT claim that creation-mode declarations or provenance metadata provide universal proof of human authorship.

**Classification**  
Specification limitation; trust boundary; claims discipline.

**Notes**  
Relay can preserve declarations and attestations while remaining explicit about their evidentiary limits.

---

# 14. Visibility model

## REM-03-140 — Access-classification requirement

**Source**  
Section 14: “Every record must declare or inherit an access classification.”

**Requirement**  
Every Relay Record MUST declare or inherit an access classification.

**Classification**  
Visibility; access control; record envelope.

**Notes**  
Inherited classification must remain unambiguous and determinable by an authorised consumer.

---

## REM-03-141 — Public classification support

**Source**  
Section 14: “Relay v0.1 should support: public...”

**Requirement**  
Relay v0.1 SHOULD support a `public` access classification.

**Classification**  
Visibility classification; recommendation.

**Notes**  
Public visibility does not imply unrestricted usage rights.

---

## REM-03-142 — Unlisted classification support

**Source**  
Section 14: “Relay v0.1 should support: ... unlisted...”

**Requirement**  
Relay v0.1 SHOULD support an `unlisted` access classification.

**Classification**  
Visibility classification; recommendation.

**Notes**  
Unlisted records are addressable to holders of the URI but are not intended for public indexing or discovery.

---

## REM-03-143 — Restricted classification support

**Source**  
Section 14: “Relay v0.1 should support: ... restricted...”

**Requirement**  
Relay v0.1 SHOULD support a `restricted` access classification.

**Classification**  
Visibility classification; recommendation.

**Notes**  
Restricted access depends on valid authority held by identified identities, applications or groups.

---

## REM-03-144 — Private classification support

**Source**  
Section 14: “Relay v0.1 should support: ... private.”

**Requirement**  
Relay v0.1 SHOULD support a `private` access classification.

**Classification**  
Visibility classification; recommendation.

**Notes**  
Private records remain readable only by the controller and explicitly authorised private services.

---

## REM-03-145 — Public-record readability

**Source**  
Section 14.1: “Readable by any observer capable of resolving the repository.”

**Requirement**  
A public record MUST be readable by any observer capable of resolving and accessing the repository through the protocol.

**Classification**  
Public access; visibility semantics.

**Notes**  
This concerns protocol access and does not grant separate rights to reproduce, exploit or modify the content.

---

## REM-03-146 — Unlisted URI-based readability

**Source**  
Section 14.2: “Readable by anyone possessing the stable Record URI...”

**Requirement**  
An unlisted record MUST be readable by an observer possessing its stable Record URI, subject to the repository being resolvable and available.

**Classification**  
Unlisted access; URI possession; visibility semantics.

**Notes**  
The source does not require identity-based authorisation for unlisted access.

---

## REM-03-147 — Unlisted non-indexing intent

**Source**  
Section 14.2: unlisted records are “not intended for public indexing or general discovery.”

**Requirement**  
An unlisted classification MUST signal that the record is not intended for public indexing or general discovery.

**Classification**  
Discovery control; indexing intent; visibility semantics.

**Notes**  
Unlisted status reduces discoverability but does not make the record secret from anyone who obtains the URI.

---

## REM-03-148 — Honour unlisted status

**Source**  
Section 14.2: “Applications and indexers should honour the unlisted status.”

**Requirement**  
Applications and indexers SHOULD honour an unlisted record’s non-indexing and non-discovery intent.

**Classification**  
Application behaviour; indexing policy; recommendation.

**Notes**  
The source describes an ecosystem obligation rather than a technical guarantee against third-party indexing.

---

## REM-03-149 — Restricted valid-authority requirement

**Source**  
Section 14.3: “Readable only by identities, applications or groups holding valid access authority.”

**Requirement**  
A restricted record MUST be readable only by identities, applications or groups holding valid access authority for that record.

**Classification**  
Restricted access; authorisation; access control.

**Notes**  
Possession of the Record URI alone is insufficient for restricted access.

---

## REM-03-150 — Private controller access

**Source**  
Section 14.4: “Readable only by the controller and explicitly authorised private services.”

**Requirement**  
A private record MUST be readable by the controller.

**Classification**  
Private access; controller authority.

**Notes**  
The controller remains the primary authorised party for private record access.

---

## REM-03-151 — Private-service explicit authorisation

**Source**  
Section 14.4: “Readable only by the controller and explicitly authorised private services.”

**Requirement**  
A private service MUST NOT read a private record unless it has been explicitly authorised to do so.

**Classification**  
Private access; service authorisation; least privilege.

**Notes**  
General application access or repository connectivity does not imply authority to read private records.

---

# 15. Audience

## REM-03-152 — Restricted audience declaration

**Source**  
Section 15: “A restricted record may identify its intended audience...”

**Requirement**  
A restricted record MAY identify its intended audience through structured audience rules.

**Classification**  
Audience modelling; restricted access; extensibility.

**Notes**  
The audience representation may use direct identities, applications, groups, grants or other defined rules.

---

## REM-03-153 — Identity-based audience

**Source**  
Section 15: intended audience may use “specific Relay Identities”.

**Requirement**  
A restricted-record audience MAY identify specific Relay Identities.

**Classification**  
Audience rule; identity-based access.

**Notes**  
Each identity must hold valid access authority under the applicable rule.

---

## REM-03-154 — Application-based audience

**Source**  
Section 15: intended audience may use “approved applications”.

**Requirement**  
A restricted-record audience MAY identify approved applications.

**Classification**  
Audience rule; application access.

**Notes**  
Application approval should not be interpreted as authority for users or services outside the granted scope.

---

## REM-03-155 — Relationship-based audience

**Source**  
Section 15: intended audience may use “relationship-based groups”.

**Requirement**  
A restricted-record audience MAY be defined using a relationship-based group.

**Classification**  
Audience rule; relationship-based access; dynamic authorisation.

**Notes**  
The record or schema must define how changing relationship membership affects access.

---

## REM-03-156 — Named access-group audience

**Source**  
Section 15: intended audience may use “named access groups”.

**Requirement**  
A restricted-record audience MAY identify one or more named access groups.

**Classification**  
Audience rule; group-based access.

**Notes**  
Group membership and authority must be resolvable under the relevant protocol or repository rules.

---

## REM-03-157 — Permission-grant audience

**Source**  
Section 15: intended audience may use “valid permission grants”.

**Requirement**  
A restricted-record audience MAY be defined by possession of a valid permission grant.

**Classification**  
Audience rule; permission-based access; delegated authority.

**Notes**  
Expired, revoked or out-of-scope grants must not confer access.

---

## REM-03-158 — Other defined access rules

**Source**  
Section 15: intended audience may use “another defined access rule”.

**Requirement**  
A restricted-record audience MAY use another explicitly defined access rule supported by the applicable schema or protocol.

**Classification**  
Audience extensibility; access-rule modelling.

**Notes**  
The rule must be sufficiently defined for consistent access evaluation.

---

## REM-03-159 — Dynamic-audience evaluation rule

**Source**  
Section 15.1: “An audience based on a changing relationship must define whether access is evaluated...”

**Requirement**  
An audience based on a changing relationship MUST define the point or rule by which audience membership and access are evaluated.

**Classification**  
Dynamic access; relationship state; authorisation semantics.

**Notes**  
Without this rule, implementations could disagree about whether later relationship changes affect earlier records.

---

## REM-03-160 — Publication-time evaluation option

**Source**  
Section 15.1: access may be evaluated “at publication time”.

**Requirement**  
A dynamic audience MAY define access using audience membership as it existed at publication time.

**Classification**  
Dynamic audience; snapshot access semantics.

**Notes**  
Under this model, later relationship changes do not automatically alter the original audience unless another rule applies.

---

## REM-03-161 — Access-time evaluation option

**Source**  
Section 15.1: access may be evaluated “at access time”.

**Requirement**  
A dynamic audience MAY define access using audience membership as it exists at the time of each access attempt.

**Classification**  
Dynamic audience; live access semantics.

**Notes**  
Under this model, a later follower or group member may gain access to an earlier record unless the schema or record states otherwise.

---

## REM-03-162 — Alternative dynamic-audience rule

**Source**  
Section 15.1: access may be evaluated “through another rule”.

**Requirement**  
A dynamic audience MAY use another explicitly defined temporal or membership-evaluation rule.

**Classification**  
Dynamic audience; access-rule extensibility.

**Notes**  
The rule must remain deterministic enough for consistent enforcement.

---

## REM-03-163 — Schema or record override of follower access

**Source**  
Section 15.1: a later follower could gain access to earlier records “unless the schema or record states otherwise.”

**Requirement**  
A schema or individual record MAY define whether later audience membership grants access to records created before that membership began.

**Classification**  
Dynamic audience; retroactive access; schema behaviour.

**Notes**  
This rule should be explicit wherever access-time evaluation could otherwise create ambiguity.

---

## REM-03-164 — Future-access revocation on audience removal

**Source**  
Section 15.2: “Removing an identity from an audience revokes future authorised access.”

**Requirement**  
Removing an identity from a record’s audience MUST revoke that identity’s future authorised access under the removed audience rule.

**Classification**  
Access revocation; audience management; authorisation.

**Notes**  
This applies to future protocol-authorised access and does not retroactively erase information already received.

---

## REM-03-165 — No guarantee of deletion of received copies

**Source**  
Section 15.2: “It cannot guarantee deletion of copies already received.”

**Requirement**  
The Relay protocol MUST NOT represent audience removal or access revocation as guaranteeing deletion of copies already received by a former audience member.

**Classification**  
Revocation limitation; data-copy persistence; claims discipline.

**Notes**  
Deletion of external copies may depend on recipient behaviour, contracts, application controls or applicable law.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 11–15 of `design-notes/03-record-model.md`.
- Section 16 and later content was excluded.
- Examples were used only to clarify source meaning and were not promoted into closed taxonomies or final serialisation requirements.

## Numbering verification

- First requirement: `REM-03-099`.
- Final requirement: `REM-03-165`.
- Requirement numbering continues directly from Part 2.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, definition or necessary decomposition of a compound source statement.
- Issued-assertion fields were extracted individually because each creates a separately testable obligation.
- Optional provenance fields, creation labels and audience mechanisms were preserved as `MAY` capabilities.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or options.
- Descriptive visibility definitions were converted into testable semantics without changing their intended access boundaries.

## Editorial verification

- Issuer, subject and holder repository remain distinct roles.
- Provenance declarations are not treated as automatic verification.
- Creation-mode labels are not inferred solely from style or content.
- Relay’s preservation of authorship declarations is not overstated as universal proof of human authorship.
- Public visibility is not conflated with usage rights.
- Unlisted status is described as a discovery and indexing intent, not secrecy.
- Audience removal revokes future authorised access but does not promise deletion of previously received copies.
