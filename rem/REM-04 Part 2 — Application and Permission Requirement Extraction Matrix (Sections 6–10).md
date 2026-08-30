# REM-04 Part 2 — Application and Permission Requirement Extraction Matrix (Sections 6–10)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 6–10 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

6. Application Manifest
7. Manifest requirements
8. Application verification status
9. Permission Request
10. Permission Grant

Requirement identifiers continue sequentially from Part 1, beginning with `REM-04-070`.

---

# 6. Application Manifest

## REM-04-070 — Signed manifest

**Source**  
Section 6: “An Application Manifest is a signed, versioned description of the application.”

**Requirement**  
Every Application Manifest MUST be signed by an authority valid for the corresponding Application Identity.

**Classification**  
Application identity; authenticity; manifest integrity.

**Notes**  
The signature establishes that the manifest was issued or approved by an authority entitled to act for the Application Identity. It does not, by itself, prove that every claim in the manifest is true.

---

## REM-04-071 — Versioned manifest

**Source**  
Section 6: “An Application Manifest is a signed, versioned description of the application.”

**Requirement**  
Every Application Manifest MUST be versioned.

**Classification**  
Manifest lifecycle; change control; auditability.

**Notes**  
Versioning enables providers and users to identify which application declarations applied when a permission was requested or granted.

---

## REM-04-072 — Manifest describes the application

**Source**  
Section 6: “An Application Manifest is a signed, versioned description of the application.”

**Requirement**  
The Application Manifest MUST describe the application associated with its Application Identity.

**Classification**  
Application metadata; transparency; consent support.

**Notes**  
The description must be sufficient to support the human-readable and machine-readable requirements defined in Section 7.

---

## REM-04-073 — Manifest Application Identity

**Source**  
Section 6, recommended manifest content: “Application Identity”.

**Requirement**  
An Application Manifest SHOULD contain the stable Application Identity to which the manifest applies.

**Classification**  
Manifest content; application identification.

**Notes**  
The source uses “should contain”. The field anchors the manifest to the machine-readable application identity rather than only to a product name or domain.

---

## REM-04-074 — Visible application name

**Source**  
Section 6, recommended manifest content: “visible application name”.

**Requirement**  
An Application Manifest SHOULD contain the application name intended for display to users.

**Classification**  
Manifest content; user transparency.

**Notes**  
The visible product name remains distinct from the stable Application Identity.

---

## REM-04-075 — Controller identity

**Source**  
Section 6, recommended manifest content: “controller identity”.

**Requirement**  
An Application Manifest SHOULD identify the application controller.

**Classification**  
Manifest content; accountability; controller identification.

**Notes**  
The application controller is the person, organisation or authority responsible for the Application Identity and its conduct.

---

## REM-04-076 — Application type

**Source**  
Section 6, recommended manifest content: “application type”.

**Requirement**  
An Application Manifest SHOULD declare the application type.

**Classification**  
Manifest content; application classification.

**Notes**  
Application type may assist consent presentation and automated policy evaluation, but it must not substitute for specific requested capabilities.

---

## REM-04-077 — Verified domains

**Source**  
Section 6, recommended manifest content: “verified domains”.

**Requirement**  
An Application Manifest SHOULD list domains whose relationship to the application has been verified.

**Classification**  
Manifest content; domain verification; security.

**Notes**  
A listed domain should not be described as verified unless the applicable verification process has actually been completed.

---

## REM-04-078 — Redirect or callback locations

**Source**  
Section 6, recommended manifest content: “redirect or callback locations”.

**Requirement**  
An Application Manifest SHOULD declare the redirect or callback locations authorised for the application.

**Classification**  
Manifest content; authorisation flow security.

**Notes**  
Declared callback locations allow providers to reject redirection to undeclared or untrusted destinations.

---

## REM-04-079 — Supported protocol versions

**Source**  
Section 6, recommended manifest content: “supported protocol versions”.

**Requirement**  
An Application Manifest SHOULD identify the Relay protocol versions supported by the application.

**Classification**  
Manifest content; compatibility; interoperability.

**Notes**  
This enables providers to determine whether a compatible authorisation exchange can be performed.

---

## REM-04-080 — Requested scope catalogue

**Source**  
Section 6, recommended manifest content: “requested scope catalogue”.

**Requirement**  
An Application Manifest SHOULD declare the catalogue of permission scopes the application may request.

**Classification**  
Manifest content; permission transparency; least privilege.

**Notes**  
Listing a scope in the catalogue does not grant that scope. Each actual request still requires explicit approval and a valid Permission Grant.

---

## REM-04-081 — Privacy policy reference

**Source**  
Section 6, recommended manifest content: “privacy policy reference”.

**Requirement**  
An Application Manifest SHOULD include a reference to the application’s applicable privacy policy.

**Classification**  
Manifest content; privacy transparency.

**Notes**  
A policy reference supplements, but does not replace, the structured permission and data-practice declarations required for informed consent.

---

## REM-04-082 — Data retention declaration

**Source**  
Section 6, recommended manifest content: “data retention declaration”.

**Requirement**  
An Application Manifest SHOULD declare the application’s data-retention practices.

**Classification**  
Manifest content; retention; privacy.

**Notes**  
The declaration should be structured sufficiently for both human explanation and automated policy checks.

---

## REM-04-083 — AI training declaration

**Source**  
Section 6, recommended manifest content: “AI training declaration”.

**Requirement**  
An Application Manifest SHOULD declare whether and under what conditions accessed data may be used for AI or model training.

**Classification**  
Manifest content; AI use; purpose limitation.

**Notes**  
The declaration must remain distinct from a particular user’s Permission Grant, which may prohibit training even where the application generally supports it.

---

## REM-04-084 — Contact details

**Source**  
Section 6, recommended manifest content: “contact details”.

**Requirement**  
An Application Manifest SHOULD provide current contact details for the application or its controller.

**Classification**  
Manifest content; accountability; support.

**Notes**  
Contact details support user enquiries, incident coordination and provider communication.

---

## REM-04-085 — Security incident endpoint

**Source**  
Section 6, recommended manifest content: “security incident endpoint”.

**Requirement**  
An Application Manifest SHOULD identify an endpoint or contact mechanism for material security incidents.

**Classification**  
Manifest content; incident response; security.

**Notes**  
The endpoint should enable providers or affected parties to report security concerns through a defined channel.

---

## REM-04-086 — Current public keys

**Source**  
Section 6, recommended manifest content: “current public keys”.

**Requirement**  
An Application Manifest SHOULD publish the application’s current public keys required for signature or authentication verification.

**Classification**  
Manifest content; cryptographic identity; key management.

**Notes**  
Key status and rotation must be reflected through manifest versioning where material.

---

## REM-04-087 — Manifest version field

**Source**  
Section 6, recommended manifest content: “manifest version”.

**Requirement**  
An Application Manifest SHOULD include an explicit manifest version identifier.

**Classification**  
Manifest content; version control; auditability.

**Notes**  
The identifier must allow distinct material versions to be unambiguously referenced.

---

## REM-04-088 — Manifest signature field

**Source**  
Section 6, recommended manifest content: “signature”.

**Requirement**  
An Application Manifest SHOULD include the signature or signature reference needed to verify its issuing authority and integrity.

**Classification**  
Manifest content; cryptographic integrity.

**Notes**  
The exact signature representation remains subject to the final serialisation design.

---

## REM-04-089 — Provisional manifest structure

**Source**  
Section 6: “The exact structure remains provisional.”

**Requirement**  
Relay v0.1 implementations MUST NOT treat the example Application Manifest structure as a final or exhaustive wire-format specification.

**Classification**  
Specification status; implementation caution.

**Notes**  
The example communicates intended information and nesting, not a final normative serialisation.

---

# 7. Manifest requirements

## REM-04-090 — New version for material changes

**Source**  
Section 7.1: “Material changes must create a new manifest version.”

**Requirement**  
Every material change to an Application Manifest MUST create a new manifest version.

**Classification**  
Manifest lifecycle; change control; auditability.

**Notes**  
A material change is one that could affect application identity continuity, security, consent, data handling or the scope of authority users may be asked to grant.

---

## REM-04-091 — Controller change is material

**Source**  
Section 7.1, examples of material changes: “controller change”.

**Requirement**  
A change of application controller MUST create a new manifest version.

**Classification**  
Controller change; accountability; manifest versioning.

**Notes**  
A controller change may also require additional continuity verification beyond ordinary versioning.

---

## REM-04-092 — New domain is material

**Source**  
Section 7.1, examples of material changes: “new domain”.

**Requirement**  
Adding a new application domain MUST create a new manifest version.

**Classification**  
Domain security; manifest versioning.

**Notes**  
The new domain should be verified before being represented as verified or used for security-sensitive authorisation flows.

---

## REM-04-093 — New callback location is material

**Source**  
Section 7.1, examples of material changes: “new callback location”.

**Requirement**  
Adding or materially changing a redirect or callback location MUST create a new manifest version.

**Classification**  
Authorisation flow security; manifest versioning.

**Notes**  
Callback changes can alter where authorisation responses or credentials are delivered and therefore require traceable versioning.

---

## REM-04-094 — Retention-policy change is material

**Source**  
Section 7.1, examples of material changes: “changed retention policy”.

**Requirement**  
A material change to the application’s data-retention policy MUST create a new manifest version.

**Classification**  
Retention; privacy; manifest versioning.

**Notes**  
Existing grants must not automatically be interpreted as approval of newly expanded retention practices.

---

## REM-04-095 — AI-usage change is material

**Source**  
Section 7.1, examples of material changes: “changed AI usage”.

**Requirement**  
A material change to declared AI processing or model-training practices MUST create a new manifest version.

**Classification**  
AI use; purpose limitation; manifest versioning.

**Notes**  
Expanded AI use may require a new or amended Permission Request rather than relying on an earlier grant.

---

## REM-04-096 — Key rotation is material

**Source**  
Section 7.1, examples of material changes: “key rotation”.

**Requirement**  
Application key rotation MUST be reflected in a new manifest version.

**Classification**  
Key management; cryptographic continuity; manifest versioning.

**Notes**  
The new version must preserve verifiable continuity between the Application Identity and its replacement keys.

---

## REM-04-097 — Expanded permission catalogue is material

**Source**  
Section 7.1, examples of material changes: “expanded permission catalogue”.

**Requirement**  
Expanding the catalogue of permissions an application may request MUST create a new manifest version.

**Classification**  
Permission transparency; manifest versioning; least privilege.

**Notes**  
Catalogue expansion does not alter existing grants or authorise the newly listed permissions.

---

## REM-04-098 — Manifest authority signature

**Source**  
Section 7.2: “The manifest must be signed by a valid authority for the Application Identity.”

**Requirement**  
A manifest signature MUST be issued by an authority valid for the Application Identity.

**Classification**  
Manifest authenticity; application authority.

**Notes**  
A syntactically valid signature from an unrelated key does not satisfy this requirement.

---

## REM-04-099 — Resolve current valid manifest before consent display

**Source**  
Section 7.3: “A Relay Provider must be able to resolve the current valid manifest before displaying a permission request.”

**Requirement**  
A Relay Provider MUST be able to resolve the application’s current valid manifest before displaying a Permission Request to a user.

**Classification**  
Provider behaviour; manifest resolution; consent integrity.

**Notes**  
The consent interface must not rely only on application-supplied display text that has not been checked against the current valid manifest.

---

## REM-04-100 — Human-readable consent information

**Source**  
Section 7.4: “The manifest must contain enough information for a consent interface to explain the request in ordinary language.”

**Requirement**  
The Application Manifest MUST contain sufficient information for a consent interface to explain the application and its request in ordinary language.

**Classification**  
Informed consent; human-readable transparency.

**Notes**  
Technical scope identifiers may be shown as supplementary detail but must not be the only explanation presented to an ordinary user.

---

## REM-04-101 — Machine-readable policy support

**Source**  
Section 7.5: “The manifest must also support automated policy checks.”

**Requirement**  
The Application Manifest MUST expose its relevant declarations in a machine-readable form that supports automated policy evaluation.

**Classification**  
Policy automation; machine readability; consent controls.

**Notes**  
Structured declarations may include retention, AI training, onward sharing, controller identity and requested scope catalogue.

---

## REM-04-102 — Provider evaluation of user policy preferences

**Source**  
Section 7.5: “The Relay Provider should be able to evaluate that preference automatically.”

**Requirement**  
A Relay Provider SHOULD be capable of automatically evaluating a user’s configured policy preferences against machine-readable application declarations.

**Classification**  
Provider behaviour; automated policy enforcement; recommendation.

**Notes**  
The source example concerns refusing applications that train models on private records, but the requirement is applicable to other machine-readable policy preferences.

---

# 8. Application verification status

## REM-04-103 — Application verification status support

**Source**  
Section 8: “An application may have a verification status such as...”

**Requirement**  
The application model MAY represent an application verification status.

**Classification**  
Application trust metadata; verification.

**Notes**  
Verification status is optional metadata and must not be confused with a universal trust guarantee.

---

## REM-04-104 — Unverified status

**Source**  
Section 8, example status: “unverified”.

**Requirement**  
The verification-status model MAY represent an application as unverified.

**Classification**  
Verification status; trust transparency.

**Notes**  
Unverified does not necessarily mean malicious; it indicates that specified verification steps have not been established.

---

## REM-04-105 — Domain-verified status

**Source**  
Section 8, example status: “domain-verified”.

**Requirement**  
The verification-status model MAY represent that control of one or more application domains has been verified.

**Classification**  
Verification status; domain control.

**Notes**  
Domain verification proves only the fact represented by the applicable verification process.

---

## REM-04-106 — Controller-verified status

**Source**  
Section 8, example status: “controller-verified”.

**Requirement**  
The verification-status model MAY represent that the identity of the application controller has been verified.

**Classification**  
Verification status; controller identity.

**Notes**  
Controller verification does not guarantee secure or compliant future behaviour.

---

## REM-04-107 — Security-reviewed status

**Source**  
Section 8, example status: “security-reviewed”.

**Requirement**  
The verification-status model MAY represent that the application has completed a defined security review.

**Classification**  
Verification status; security assurance.

**Notes**  
The review scope, reviewer and date should be discoverable where necessary to explain the meaning of the status.

---

## REM-04-108 — Ecosystem-certified status

**Source**  
Section 8, example status: “ecosystem-certified”.

**Requirement**  
The verification-status model MAY represent that the application has received a defined ecosystem certification.

**Classification**  
Verification status; certification.

**Notes**  
Certification must be attributable to the relevant certifying authority and criteria.

---

## REM-04-109 — Suspended status

**Source**  
Section 8, example status: “suspended”.

**Requirement**  
The verification-status model MAY represent that an application is suspended.

**Classification**  
Application status; enforcement; risk management.

**Notes**  
A provider should not present a suspended application as ordinarily verified or available without clearly indicating the suspension.

---

## REM-04-110 — Revoked status

**Source**  
Section 8, example status: “revoked”.

**Requirement**  
The verification-status model MAY represent that an application’s verification or recognised authority has been revoked.

**Classification**  
Application status; revocation; trust metadata.

**Notes**  
The precise operational consequences depend on the authority and status being revoked.

---

## REM-04-111 — No universal trust guarantee

**Source**  
Section 8: “Verification must not be represented as a universal guarantee of trustworthiness.”

**Requirement**  
An application verification status MUST NOT be represented as a universal guarantee that the application is trustworthy, secure or compliant in all respects.

**Classification**  
Verification semantics; user transparency; anti-misrepresentation.

**Notes**  
Verification must remain limited to the specific facts or assessment actually established.

---

## REM-04-112 — Verification may indicate domain control

**Source**  
Section 8: verification may indicate “control of a domain”.

**Requirement**  
A verification status MAY indicate that control of a specified domain has been established.

**Classification**  
Verification fact; domain control.

**Notes**  
The consent interface must not inflate this fact into broader claims about the controller or security of the application.

---

## REM-04-113 — Verification may indicate controller identity

**Source**  
Section 8: verification may indicate “identity of the controller”.

**Requirement**  
A verification status MAY indicate that the identity of the application controller has been established.

**Classification**  
Verification fact; controller identity.

**Notes**  
Identity verification does not itself establish that all declared practices are followed.

---

## REM-04-114 — Verification may indicate security review completion

**Source**  
Section 8: verification may indicate “completion of a security review”.

**Requirement**  
A verification status MAY indicate that the application completed a specified security review.

**Classification**  
Verification fact; security review.

**Notes**  
The status should not imply that no future vulnerabilities or incidents are possible.

---

## REM-04-115 — Verification may indicate catalogue acceptance

**Source**  
Section 8: verification may indicate “acceptance into a provider catalogue”.

**Requirement**  
A verification status MAY indicate that a provider accepted the application into a defined catalogue.

**Classification**  
Verification fact; provider catalogue.

**Notes**  
Catalogue acceptance reflects the provider’s criteria and must not be presented as universal ecosystem approval.

---

## REM-04-116 — Explain what was verified

**Source**  
Section 8: “The consent screen should explain what was actually verified.”

**Requirement**  
A consent screen SHOULD explain the specific facts, review or certification represented by an application’s verification status.

**Classification**  
Consent interface; verification transparency; recommendation.

**Notes**  
Displaying only a generic badge without explaining its meaning is insufficient to meet the recommendation.

---

# 9. Permission Request

## REM-04-117 — Permission Request definition

**Source**  
Section 9: “A Permission Request is an application’s proposal for access to a Relay Identity or Repository.”

**Requirement**  
A Permission Request MUST represent an application’s proposed access to a specified Relay Identity or Relay Repository.

**Classification**  
Authorisation lifecycle; permission request.

**Notes**  
A request is a proposal only. It creates no authority until an explicit valid Permission Grant is issued.

---

## REM-04-118 — Requested application identification

**Source**  
Section 9, required request information: “the application”.

**Requirement**  
A Permission Request MUST identify the requesting Application Identity.

**Classification**  
Permission request; application identification; accountability.

**Notes**  
A visible application name alone is insufficient where it cannot be reliably bound to the stable Application Identity.

---

## REM-04-119 — Identity being asked

**Source**  
Section 9, required request information: “the identity being asked”.

**Requirement**  
A Permission Request MUST identify the Relay Identity from whom authority is requested.

**Classification**  
Permission request; grantor identification.

**Notes**  
This prevents a request intended for one identity from being ambiguously applied to another.

---

## REM-04-120 — Requested resources

**Source**  
Section 9, required request information: “requested resources”.

**Requirement**  
A Permission Request MUST identify the resources the application proposes to access.

**Classification**  
Resource scope; least privilege; permission request.

**Notes**  
Resources may be expressed by repository, collection, record or another protocol-defined boundary.

---

## REM-04-121 — Requested actions

**Source**  
Section 9, required request information: “requested actions”.

**Requirement**  
A Permission Request MUST identify each action the application proposes to perform on the requested resources.

**Classification**  
Action scope; least privilege; permission request.

**Notes**  
Read, create, update and delete are distinct actions and must not be silently bundled where separate approval is meaningful.

---

## REM-04-122 — Requested duration

**Source**  
Section 9, required request information: “duration”.

**Requirement**  
A Permission Request MUST declare the proposed duration of access.

**Classification**  
Temporal scope; permission request.

**Notes**  
Duration may be fixed, session-based, until revoked or another defined period, but must be communicated clearly.

---

## REM-04-123 — Requested purpose

**Source**  
Section 9, required request information: “purpose”.

**Requirement**  
A Permission Request MUST declare the purpose or purposes for which the requested authority will be used.

**Classification**  
Purpose limitation; informed consent.

**Notes**  
The purpose declaration is part of the approved boundary and must not be treated as decorative explanatory text.

---

## REM-04-124 — Requested retention

**Source**  
Section 9, required request information: “retention”.

**Requirement**  
A Permission Request MUST declare the proposed retention of data obtained or created under the requested authority.

**Classification**  
Retention; privacy; permission request.

**Notes**  
The declaration should include relevant caching and post-revocation retention behaviour.

---

## REM-04-125 — Onward-sharing declaration

**Source**  
Section 9, required request information: “onward sharing”.

**Requirement**  
A Permission Request MUST declare whether accessed data or authority may be shared onward with another party or service.

**Classification**  
Data sharing; privacy; permission request.

**Notes**  
Onward sharing must not be inferred merely from a linked privacy policy.

---

## REM-04-126 — AI-processing declaration

**Source**  
Section 9, required request information: “whether AI processing is involved”.

**Requirement**  
A Permission Request MUST declare whether the requested access involves AI processing.

**Classification**  
AI use; transparency; permission request.

**Notes**  
AI processing for inference or assistance is distinct from model training and must not be conflated with it.

---

## REM-04-127 — Model-training declaration

**Source**  
Section 9, required request information: “whether model training is requested”.

**Requirement**  
A Permission Request MUST explicitly declare whether use of accessed data for model training is requested.

**Classification**  
AI training; explicit consent; purpose limitation.

**Notes**  
Silence or a general AI-processing declaration must not be interpreted as approval for model training.

---

## REM-04-128 — Interactive or continuous access declaration

**Source**  
Section 9, required request information: “whether access is interactive or continuous”.

**Requirement**  
A Permission Request MUST state whether the proposed access occurs only during interactive use or may continue without the user actively operating the application.

**Classification**  
Access mode; background access; informed consent.

**Notes**  
Continuous access generally presents a broader risk and must not be hidden behind a one-time interactive consent screen.

---

## REM-04-129 — High-authority operation declaration

**Source**  
Section 9, required request information: “whether high-authority operations are requested”.

**Requirement**  
A Permission Request MUST identify whether it includes high-authority operations.

**Classification**  
Elevated authority; risk disclosure; permission request.

**Notes**  
High-authority operations may require stronger authentication, more prominent consent or additional restrictions elsewhere in the model.

---

# 10. Permission Grant

## REM-04-130 — Permission Grant definition

**Source**  
Section 10: “A Permission Grant is a signed authorisation issued by the Relay Identity in response to a Permission Request.”

**Requirement**  
A Permission Grant MUST be an authorisation issued by the relevant Relay Identity in response to a Permission Request.

**Classification**  
Authorisation lifecycle; permission grant.

**Notes**  
The grant represents actual delegated authority, unlike the request, which represents only proposed authority.

---

## REM-04-131 — Signed grant

**Source**  
Section 10: “A Permission Grant is a signed authorisation...”

**Requirement**  
A Permission Grant MUST be signed or otherwise cryptographically authorised by valid authority for the issuing Relay Identity.

**Classification**  
Grant authenticity; delegated authority; cryptographic proof.

**Notes**  
The exact signature representation may be supplied through repository or authorisation-service mechanisms, but the authority must be verifiable.

---

## REM-04-132 — Explicit grant

**Source**  
Section 10, grant requirement: “explicit”.

**Requirement**  
A Permission Grant MUST express the granted authority explicitly.

**Classification**  
Explicit consent; authorisation clarity.

**Notes**  
Authority must not be inferred solely from application installation, account creation, silence or unrelated acceptance.

---

## REM-04-133 — Limited grant

**Source**  
Section 10, grant requirement: “limited”.

**Requirement**  
A Permission Grant MUST be limited to defined resources, actions and applicable conditions.

**Classification**  
Least privilege; scope limitation.

**Notes**  
A grant that provides undefined or unlimited authority does not satisfy this requirement merely because the user clicked an approval control.

---

## REM-04-134 — Attributable grant

**Source**  
Section 10, grant requirement: “attributable”.

**Requirement**  
A Permission Grant MUST be attributable to its issuing Relay Identity and receiving Application Identity.

**Classification**  
Accountability; grant provenance.

**Notes**  
Attribution enables later inspection of who granted authority to which application.

---

## REM-04-135 — Inspectable grant

**Source**  
Section 10, grant requirement: “inspectable”.

**Requirement**  
A Permission Grant MUST be available for inspection by the issuing identity through an authorised interface or service.

**Classification**  
User transparency; grant management; auditability.

**Notes**  
Inspection should expose the active scope, purpose, duration, restrictions and application identity.

---

## REM-04-136 — Revocable grant

**Source**  
Section 10, grant requirement: “revocable”.

**Requirement**  
A Permission Grant MUST be revocable by valid authority for the issuing Relay Identity.

**Classification**  
Revocation; user control; delegated authority.

**Notes**  
Revocation terminates future authorised use but may not by itself erase copies already lawfully received; retention obligations remain separately relevant.

---

## REM-04-137 — Time-bound where appropriate

**Source**  
Section 10, grant requirement: “time-bound where appropriate”.

**Requirement**  
A Permission Grant MUST include an appropriate temporal boundary where the nature or risk of the authority calls for time limitation.

**Classification**  
Temporal scope; risk control.

**Notes**  
The source does not require every grant to have a fixed expiry, but time-unlimited authority must not be used where a narrower duration is appropriate.

---

## REM-04-138 — Grant no broader than request

**Source**  
Section 10, grant requirement: “no broader than the approved request”.

**Requirement**  
A Permission Grant MUST NOT authorise resources, actions, purposes, duration or other authority broader than the Permission Request approved by the user.

**Classification**  
Consent integrity; scope containment; least privilege.

**Notes**  
A provider may issue a narrower grant than requested. It may not silently expand the approved request.

---

## REM-04-139 — Grant identifier

**Source**  
Section 10 example: grant field `id`.

**Requirement**  
A Permission Grant SHOULD have a stable identifier that allows it to be referenced, inspected and revoked.

**Classification**  
Grant identification; lifecycle management.

**Notes**  
The source example is illustrative, but a stable grant reference is necessary to operationalise inspectability and revocation.

---

## REM-04-140 — Grant issuer identification

**Source**  
Section 10 example: grant field `issuer`.

**Requirement**  
A Permission Grant MUST identify the Relay Identity that issued the authorisation.

**Classification**  
Grant attribution; issuer identification.

**Notes**  
The issuer must correspond to the authority whose repository or identity resources are being delegated.

---

## REM-04-141 — Granted application identification

**Source**  
Section 10 example: grant field `application`.

**Requirement**  
A Permission Grant MUST identify the Application Identity receiving the authority.

**Classification**  
Grant attribution; application identification.

**Notes**  
Authority granted to one application must not automatically be transferable to another Application Identity.

---

## REM-04-142 — Grant issuance time

**Source**  
Section 10 example: grant field `issuedAt`.

**Requirement**  
A Permission Grant SHOULD record the time at which it was issued.

**Classification**  
Temporal metadata; auditability.

**Notes**  
Issuance time supports validity checks, audit history and later interpretation of applicable manifest versions.

---

## REM-04-143 — Grant expiration time

**Source**  
Section 10 example: grant field `expiresAt` and requirement to be time-bound where appropriate.

**Requirement**  
A Permission Grant SHOULD record an expiration time or an explicit indication that no fixed expiration applies.

**Classification**  
Temporal scope; grant validity.

**Notes**  
A null or absent fixed expiry does not remove revocability.

---

## REM-04-144 — Granted resources and actions

**Source**  
Section 10 example: `resources` with collection and action entries.

**Requirement**  
A Permission Grant MUST identify the resources and actions actually authorised.

**Classification**  
Resource scope; action scope; least privilege.

**Notes**  
The grant must be independently inspectable without requiring the application to reinterpret the original request.

---

## REM-04-145 — Granted purposes

**Source**  
Section 10 example: grant field `purpose`.

**Requirement**  
A Permission Grant MUST identify the purposes for which the granted authority may be exercised.

**Classification**  
Purpose limitation; consent integrity.

**Notes**  
Use outside the approved purpose falls outside the grant even where the technical resource and action scope would otherwise permit it.

---

## REM-04-146 — Grant restrictions

**Source**  
Section 10 example: `restrictions` including model training and onward sharing.

**Requirement**  
A Permission Grant MUST preserve any approved restrictions that limit use of the granted authority or resulting data.

**Classification**  
Grant restrictions; privacy; purpose limitation.

**Notes**  
Restrictions may include prohibitions on model training, onward sharing, retention or other defined practices.

---

## REM-04-147 — Grant storage as authority record

**Source**  
Section 10: “The grant itself may be stored as an authority record in the repository...”

**Requirement**  
A Permission Grant MAY be stored as an authority record in the Relay Repository.

**Classification**  
Grant storage; authority records; repository model.

**Notes**  
Repository storage is permitted but not mandated as the only architecture.

---

## REM-04-148 — Grant storage in authorisation service

**Source**  
Section 10: “...or in a dedicated authorisation service.”

**Requirement**  
A Permission Grant MAY be stored in a dedicated authorisation service.

**Classification**  
Grant storage; authorisation architecture.

**Notes**  
Where a dedicated service is used, the grant must remain verifiable, attributable, inspectable and revocable according to the same protocol requirements.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 6–10 of `design-notes/04-application-and-permission-model.md`.
- Sections 11 onward were excluded.
- Example serialisations were used to clarify operational fields but were not treated as final wire-format specifications.

## Numbering verification

- First requirement: `REM-04-070`.
- Final requirement: `REM-04-148`.
- Requirement numbering continues directly from Part 1.
- Requirement identifiers are continuous, unique and ordered according to source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Manifest content items, request declarations and grant properties were extracted individually because each represents a separately testable obligation or recommendation.
- Source “must”, “should” and “may” language was retained as `MUST`, `SHOULD` and `MAY` wherever directly applicable.

## Editorial verification

- Manifest declarations were not treated as proof of trustworthiness.
- Verification status was limited to the specific facts actually verified.
- A Permission Request was kept distinct from actual delegated authority.
- A Permission Grant was required to remain explicit, limited, attributable, inspectable and revocable.
- Grant scope was prevented from exceeding the user-approved request.
- Manifest permission catalogues were not interpreted as grants.
- AI processing and model training were kept as separate declarations.
- The example manifest and grant structures remain explicitly provisional or illustrative rather than final serialisation mandates.
