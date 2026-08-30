# REM-04 Part 1 — Application and Permission Requirement Extraction Matrix (Sections 1–5)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 1–5 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

1. Definition
2. Purpose
3. Core components
4. Application Identity
5. Application controller

Requirement identifiers begin at `REM-04-001`.

---

# 1. Definition

## REM-04-001 — Relay Application as software

**Source**  
Section 1: “A Relay Application is software that requests limited authority to read from, write to or otherwise interact with a Relay Identity or Relay Repository.”

**Requirement**  
A Relay Application MUST be represented as software that interacts with a Relay Identity or Relay Repository only through requested authority.

**Classification**  
Core object definition; application model.

**Notes**  
The application is distinct from the identity, repository, records, controller and installation through which it operates.

---

## REM-04-002 — Limited application authority

**Source**  
Section 1: “A Relay Application is software that requests limited authority...”

**Requirement**  
A Relay Application MUST request limited authority rather than receive unrestricted control over a Relay Identity or Relay Repository.

**Classification**  
Least privilege; delegated authority; security.

**Notes**  
The detailed dimensions of limitation are defined later in the model and include resource, action, duration and purpose.

---

## REM-04-003 — Read authority

**Source**  
Section 1: a Relay Application may request authority “to read from” a Relay Identity or Relay Repository.

**Requirement**  
A Relay Application MAY request authority to read authorised information from a Relay Identity or Relay Repository.

**Classification**  
Permission capability; read access.

**Notes**  
Read authority must remain within the scope of a valid Permission Grant.

---

## REM-04-004 — Write authority

**Source**  
Section 1: a Relay Application may request authority “to... write to” a Relay Identity or Relay Repository.

**Requirement**  
A Relay Application MAY request authority to write authorised information or operations to a Relay Identity or Relay Repository.

**Classification**  
Permission capability; write access.

**Notes**  
Write authority does not make the application the owner or controller of the affected identity, repository or records.

---

## REM-04-005 — Other authorised interactions

**Source**  
Section 1: a Relay Application may request authority to “otherwise interact with” a Relay Identity or Relay Repository.

**Requirement**  
A Relay Application MAY request other explicitly defined interaction capabilities beyond reading and writing.

**Classification**  
Permission capability; extensibility.

**Notes**  
Other interactions must still be limited, declared and authorised through a valid grant.

---

## REM-04-006 — Support for varied application functions

**Source**  
Section 1, examples: social interface, publishing tool, portfolio builder, AI assistant, messaging service, professional network, analytics service, import or migration tool, moderation service, and mobile or desktop client.

**Requirement**  
The Application and Permission Model MUST support varied application functions without restricting Relay Applications to a single product category or interface type.

**Classification**  
Application diversity; extensibility; interoperability.

**Notes**  
The examples are illustrative rather than an exhaustive taxonomy.

---

## REM-04-007 — No application ownership of identity

**Source**  
Section 1: “An application is not the owner of the identity... it accesses.”

**Requirement**  
A Relay Application MUST NOT be treated as the owner of any Relay Identity it accesses.

**Classification**  
Ownership boundary; identity control.

**Notes**  
Application access is delegated and revocable. It does not transfer identity ownership.

---

## REM-04-008 — No application ownership of repository

**Source**  
Section 1: “An application is not the owner of the... repository... it accesses.”

**Requirement**  
A Relay Application MUST NOT be treated as the owner of any Relay Repository it accesses.

**Classification**  
Ownership boundary; repository control.

**Notes**  
The application may perform authorised operations without becoming the repository’s controlling authority.

---

## REM-04-009 — No application ownership of records

**Source**  
Section 1: “An application is not the owner of the... records it accesses.”

**Requirement**  
A Relay Application MUST NOT acquire ownership of Relay Records merely by creating, reading, editing, displaying or otherwise accessing them.

**Classification**  
Ownership boundary; record control; application independence.

**Notes**  
Record authority remains governed by the repository, authorising identity and applicable record model.

---

## REM-04-010 — Explicit Permission Grant required

**Source**  
Section 1: “Its authority exists only through an explicit... Permission Grant.”

**Requirement**  
A Relay Application MUST NOT exercise authority unless that authority is established through an explicit Permission Grant.

**Classification**  
Consent; authorisation; security.

**Notes**  
Authority must not be inferred solely from installation, account creation, prior interaction or application branding.

---

## REM-04-011 — Valid Permission Grant required

**Source**  
Section 1: “Its authority exists only through an... valid... Permission Grant.”

**Requirement**  
A Relay Application MUST NOT exercise authority under an invalid, expired, malformed, superseded or otherwise non-effective Permission Grant.

**Classification**  
Authorisation validity; security; lifecycle.

**Notes**  
The validity conditions are elaborated later in the source model.

---

## REM-04-012 — Revocable Permission Grant required

**Source**  
Section 1: “Its authority exists only through an... revocable Permission Grant.”

**Requirement**  
Application authority MUST be granted through a Permission Grant that can be revoked.

**Classification**  
Revocation; user control; authorisation lifecycle.

**Notes**  
A grant that cannot be withdrawn would conflict with the source model’s core authority boundary.

---

# 2. Purpose

## REM-04-013 — Separation of digital continuity and application experience

**Source**  
Section 2: the model exists to separate “the user’s underlying digital continuity” from “the service experience offered by an application”.

**Requirement**  
The Application and Permission Model MUST keep the user’s underlying digital continuity separate from the service experience provided by any particular application.

**Classification**  
Application independence; continuity; portability.

**Notes**  
Changing applications must not inherently require abandoning the person’s underlying identity or repository state.

---

## REM-04-014 — Separation of digital continuity and application authority

**Source**  
Section 2: the model exists to separate “the user’s underlying digital continuity” from “the authority granted to that application”.

**Requirement**  
The user’s digital continuity MUST remain distinct from the authority granted to any application.

**Classification**  
Authority separation; continuity; user control.

**Notes**  
An application’s authority is temporary and bounded; the user’s digital continuity is not defined by that grant.

---

## REM-04-015 — Separation of application experience and authority

**Source**  
Section 2: the model exists to separate “the service experience offered by an application” from “the authority granted to that application”.

**Requirement**  
An application’s user experience MUST remain conceptually and technically distinct from the authority granted to it.

**Classification**  
Separation of concerns; permission transparency.

**Notes**  
A feature-rich or trusted-looking interface does not itself justify broader authority.

---

## REM-04-016 — Connection without identity surrender

**Source**  
Section 2: the model must allow a person to “connect an application without surrendering control of their identity”.

**Requirement**  
The model MUST allow a person to connect a Relay Application without surrendering control of their Relay Identity.

**Classification**  
User control; identity sovereignty; delegated access.

**Notes**  
Connection establishes limited application authority, not transfer of identity control.

---

## REM-04-017 — Permission-request transparency

**Source**  
Section 2: the model must allow a person to “see exactly what the application wants to do”.

**Requirement**  
The model MUST provide sufficient information for a person to understand exactly what an application is requesting authority to do.

**Classification**  
Consent transparency; human-readable authorisation.

**Notes**  
The request must be understandable at the capability and scope level rather than expressed only as opaque technical tokens.

---

## REM-04-018 — Selective capability approval

**Source**  
Section 2: the model must allow a person to “approve only the required capabilities”.

**Requirement**  
The model MUST allow a person to approve only the capabilities required for the intended application function.

**Classification**  
Least privilege; granular consent.

**Notes**  
The model must not force approval of unrelated capabilities as an inseparable bundle where narrower approval is sufficient.

---

## REM-04-019 — Resource limitation

**Source**  
Section 2: the model must allow a person to “limit access by resource...”

**Requirement**  
The model MUST allow application access to be limited by resource.

**Classification**  
Scope restriction; resource-level access control.

**Notes**  
Resources may include repositories, collections, records, fields, blobs or other protocol-defined objects.

---

## REM-04-020 — Action limitation

**Source**  
Section 2: the model must allow a person to “limit access by... action...”

**Requirement**  
The model MUST allow application access to be limited by permitted action.

**Classification**  
Capability restriction; least privilege.

**Notes**  
Read, create, update, delete, share and administrative actions may require separate authority.

---

## REM-04-021 — Duration limitation

**Source**  
Section 2: the model must allow a person to “limit access by... duration...”

**Requirement**  
The model MUST allow application authority to be limited by duration.

**Classification**  
Temporal scope; authorisation lifecycle.

**Notes**  
Duration limits may include expiration times, session limits or other protocol-defined temporal conditions.

---

## REM-04-022 — Purpose limitation

**Source**  
Section 2: the model must allow a person to “limit access by... purpose”.

**Requirement**  
The model MUST allow application authority to be limited by declared purpose.

**Classification**  
Purpose limitation; consent; data governance.

**Notes**  
Purpose declarations must be meaningful enough to support user understanding, audit and policy evaluation.

---

## REM-04-023 — Revocation capability

**Source**  
Section 2: the model must allow a person to “revoke access”.

**Requirement**  
The model MUST allow a person to revoke an application’s granted access.

**Classification**  
Revocation; user control; security.

**Notes**  
Revocation must affect future authorised access and operations according to the protocol’s revocation rules.

---

## REM-04-024 — Application activity inspection

**Source**  
Section 2: the model must allow a person to “inspect the application’s activity”.

**Requirement**  
The model MUST allow a person to inspect material activity performed by an application under delegated authority.

**Classification**  
Auditability; transparency; accountability.

**Notes**  
The source establishes activity inspection as a required user capability. The detailed audit-event structure appears later in the model.

---

## REM-04-025 — Application replacement without repository-state loss

**Source**  
Section 2: the model must allow a person to “replace the application without losing repository state”.

**Requirement**  
The model MUST allow a person to replace an application without losing canonical Relay Repository state.

**Classification**  
Portability; application independence; continuity.

**Notes**  
Application-specific local state may be excluded where it was never canonical repository state.

---

## REM-04-026 — Applications may act for a person

**Source**  
Section 2, central principle: “Applications may act for a person...”

**Requirement**  
A Relay Application MAY perform actions on behalf of a person where those actions are authorised by a valid Permission Grant.

**Classification**  
Delegated authority; application operation.

**Notes**  
Acting for a person is conditional and scoped, not inherent in the application’s identity.

---

## REM-04-027 — Applications must not become the person

**Source**  
Section 2, central principle: “Applications may act for a person, but they must not become the person.”

**Requirement**  
A Relay Application MUST NOT be represented or treated as the person or Relay Identity on whose behalf it acts.

**Classification**  
Identity separation; delegated authority; accountability.

**Notes**  
Operations should preserve the distinction between the authorising identity and the submitting application.

---

# 3. Core components

## REM-04-028 — Application Identity component

**Source**  
Section 3, component 1: “Application Identity”.

**Requirement**  
The Application and Permission Model MUST include an Application Identity component.

**Classification**  
Architecture; application identification.

**Notes**  
The Application Identity provides the stable machine-readable identity described in Section 4.

---

## REM-04-029 — Application Manifest component

**Source**  
Section 3, component 2: “Application Manifest”.

**Requirement**  
The Application and Permission Model MUST include an Application Manifest component.

**Classification**  
Architecture; application metadata; trust.

**Notes**  
The manifest’s detailed contents and requirements appear in later sections.

---

## REM-04-030 — Permission Request component

**Source**  
Section 3, component 3: “Permission Request”.

**Requirement**  
The Application and Permission Model MUST include a Permission Request component.

**Classification**  
Architecture; consent initiation.

**Notes**  
A request expresses the authority sought before a grant is issued.

---

## REM-04-031 — Permission Grant component

**Source**  
Section 3, component 4: “Permission Grant”.

**Requirement**  
The Application and Permission Model MUST include a Permission Grant component.

**Classification**  
Architecture; delegated authority.

**Notes**  
The Permission Grant is the source of explicit, valid and revocable application authority.

---

## REM-04-032 — Scope component

**Source**  
Section 3, component 5: “Scope”.

**Requirement**  
The Application and Permission Model MUST include a Scope component.

**Classification**  
Architecture; access limitation.

**Notes**  
Scope defines the boundaries within which a granted capability may be exercised.

---

## REM-04-033 — Capability component

**Source**  
Section 3, component 6: “Capability”.

**Requirement**  
The Application and Permission Model MUST include a Capability component.

**Classification**  
Architecture; permitted actions.

**Notes**  
Capabilities represent the operations an application is allowed to perform.

---

## REM-04-034 — Authorisation Session component

**Source**  
Section 3, component 7: “Authorisation Session”.

**Requirement**  
The Application and Permission Model MUST include an Authorisation Session component.

**Classification**  
Architecture; consent flow; session security.

**Notes**  
The authorisation session supports the process through which permission is requested and granted.

---

## REM-04-035 — Access or Capability Token component

**Source**  
Section 3, component 8: “Access Token or Capability Token”.

**Requirement**  
The Application and Permission Model MUST include an Access Token, Capability Token or protocol-equivalent component for exercising granted authority.

**Classification**  
Architecture; credential; runtime authorisation.

**Notes**  
The source allows either access-token or capability-token terminology and does not yet settle one final mechanism.

---

## REM-04-036 — Delegated Key component

**Source**  
Section 3, component 9: “Delegated Key”.

**Requirement**  
The Application and Permission Model MUST include a Delegated Key component where cryptographic delegation is supported.

**Classification**  
Architecture; cryptographic authority; delegation.

**Notes**  
Later sections determine when delegated keys are optional or required.

---

## REM-04-037 — Audit Event component

**Source**  
Section 3, component 10: “Audit Event”.

**Requirement**  
The Application and Permission Model MUST include an Audit Event component.

**Classification**  
Architecture; auditability; accountability.

**Notes**  
Audit events support the user’s ability to inspect application activity.

---

## REM-04-038 — Revocation Record component

**Source**  
Section 3, component 11: “Revocation Record”.

**Requirement**  
The Application and Permission Model MUST include a Revocation Record component.

**Classification**  
Architecture; revocation; history.

**Notes**  
The record preserves the fact and authority of a revocation event.

---

## REM-04-039 — Consent Receipt component

**Source**  
Section 3, component 12: “Consent Receipt”.

**Requirement**  
The Application and Permission Model MUST include a Consent Receipt component.

**Classification**  
Architecture; consent evidence; transparency.

**Notes**  
A Consent Receipt provides a persistent representation of what was approved.

---

# 4. Application Identity

## REM-04-040 — Stable Application Identity

**Source**  
Section 4: “Every Relay Application must have a stable machine-readable identity.”

**Requirement**  
Every Relay Application MUST have a stable Application Identity.

**Classification**  
Application identification; persistence.

**Notes**  
Stability allows grants, manifests, audit events and revocations to refer consistently to the same application.

---

## REM-04-041 — Machine-readable Application Identity

**Source**  
Section 4: “Every Relay Application must have a stable machine-readable identity.”

**Requirement**  
Every Application Identity MUST be machine-readable.

**Classification**  
Application identification; interoperability.

**Notes**  
The example `rid:app:...` syntax is illustrative unless finalised elsewhere.

---

## REM-04-042 — Distinct from company name

**Source**  
Section 4: “The Application Identity must be distinct from... the company name.”

**Requirement**  
An Application Identity MUST remain distinct from the name of any company associated with the application.

**Classification**  
Identity separation; controller distinction.

**Notes**  
A company may operate several applications, and an application controller may not be a company.

---

## REM-04-043 — Distinct from visible product name

**Source**  
Section 4: “The Application Identity must be distinct from... the application’s visible product name.”

**Requirement**  
An Application Identity MUST remain distinct from the application’s visible product or brand name.

**Classification**  
Identity separation; branding independence.

**Notes**  
Branding may change without necessarily changing the underlying Application Identity.

---

## REM-04-044 — Distinct from domain

**Source**  
Section 4: “The Application Identity must be distinct from... a domain.”

**Requirement**  
An Application Identity MUST remain distinct from any domain used by the application.

**Classification**  
Identity separation; infrastructure independence.

**Notes**  
Domains may be verified attributes of an application without serving as its permanent identity.

---

## REM-04-045 — Distinct from callback URL

**Source**  
Section 4: “The Application Identity must be distinct from... a callback URL.”

**Requirement**  
An Application Identity MUST remain distinct from any redirect or callback URL used during authorisation.

**Classification**  
Identity separation; authorisation infrastructure.

**Notes**  
Callback locations may change or multiply while application identity remains continuous.

---

## REM-04-046 — Distinct from installation

**Source**  
Section 4: “The Application Identity must be distinct from... an installation.”

**Requirement**  
An Application Identity MUST remain distinct from any individual installation of the application.

**Classification**  
Identity separation; installation management.

**Notes**  
Multiple installations may operate under one Application Identity while retaining installation-specific state or credentials.

---

## REM-04-047 — Distinct from device

**Source**  
Section 4: “The Application Identity must be distinct from... a specific device.”

**Requirement**  
An Application Identity MUST remain distinct from any specific device on which the application runs.

**Classification**  
Identity separation; device independence.

**Notes**  
Device identity may be relevant to sessions or security controls but does not define the application itself.

---

## REM-04-048 — Distinct from version number

**Source**  
Section 4: “The Application Identity must be distinct from... a version number.”

**Requirement**  
An Application Identity MUST remain distinct from any application version number.

**Classification**  
Identity separation; software lifecycle.

**Notes**  
Application upgrades should not automatically produce a new Application Identity.

---

## REM-04-049 — Branding change with identity continuity

**Source**  
Section 4: “An application may change branding... without becoming a new application identity, provided continuity is authorised and verifiable.”

**Requirement**  
An application MAY change branding without creating a new Application Identity, provided identity continuity is authorised and verifiable.

**Classification**  
Identity continuity; branding change; verification.

**Notes**  
A branding change must not be used to conceal an unauthorised transfer or replacement of the application’s controlling identity.

---

## REM-04-050 — Infrastructure change with identity continuity

**Source**  
Section 4: “An application may change... infrastructure without becoming a new application identity, provided continuity is authorised and verifiable.”

**Requirement**  
An application MAY change infrastructure without creating a new Application Identity, provided identity continuity is authorised and verifiable.

**Classification**  
Identity continuity; infrastructure change; verification.

**Notes**  
Infrastructure includes domains, hosting, callback locations and other operational components.

---

## REM-04-051 — Authorised continuity requirement

**Source**  
Section 4: continuity is permitted “provided continuity is authorised...”

**Requirement**  
Application Identity continuity across branding or infrastructure changes MUST be authorised by a valid authority for that Application Identity.

**Classification**  
Identity continuity; authority; governance.

**Notes**  
Unilateral claims of continuity are insufficient where the controlling authority cannot be established.

---

## REM-04-052 — Verifiable continuity requirement

**Source**  
Section 4: continuity is permitted “provided continuity is... verifiable.”

**Requirement**  
Application Identity continuity across branding or infrastructure changes MUST be verifiable.

**Classification**  
Identity continuity; verification; trust.

**Notes**  
Verification may rely on signed manifests, application keys, controller authority or another protocol-defined continuity mechanism.

---

# 5. Application controller

## REM-04-053 — Controller identification

**Source**  
Section 5: “Every Application Identity must identify the person, organisation or authority responsible for it.”

**Requirement**  
Every Application Identity MUST identify its responsible application controller.

**Classification**  
Controller accountability; application governance.

**Notes**  
The controller is distinct from the Application Identity itself.

---

## REM-04-054 — Person as controller

**Source**  
Section 5: the responsible controller may be a “person”; examples include “an individual developer”.

**Requirement**  
The model MUST support an individual person as the controller of an Application Identity.

**Classification**  
Controller model; extensibility.

**Notes**  
A corporate entity must not be required where an individual legitimately controls the application.

---

## REM-04-055 — Organisation as controller

**Source**  
Section 5: the controller may be an organisation, including a company, non-profit organisation or government body.

**Requirement**  
The model MUST support an organisation as the controller of an Application Identity.

**Classification**  
Controller model; organisational accountability.

**Notes**  
The organisation type does not alter the requirement for identifiable responsibility.

---

## REM-04-056 — Open-source project as controller

**Source**  
Section 5: the controller may be “an open-source project”.

**Requirement**  
The model MUST support an open-source project as the identified controller or responsible authority for an Application Identity.

**Classification**  
Controller model; open-source governance.

**Notes**  
The project must still expose sufficient responsible authority for manifest signing, incident handling and other controller duties.

---

## REM-04-057 — Relay Identity as controller

**Source**  
Section 5: the controller may be “another Relay Identity”.

**Requirement**  
The model MUST support another Relay Identity as the controller of an Application Identity.

**Classification**  
Controller model; identity linkage.

**Notes**  
The controller relationship must remain explicit rather than inferred from application usage.

---

## REM-04-058 — Manifest accuracy responsibility

**Source**  
Section 5: “The controller is responsible for... the accuracy of the Application Manifest.”

**Requirement**  
The application controller MUST be responsible for the accuracy of the Application Manifest.

**Classification**  
Controller responsibility; manifest integrity.

**Notes**  
Materially inaccurate manifest information undermines informed consent and policy evaluation.

---

## REM-04-059 — Granted-access handling responsibility

**Source**  
Section 5: “The controller is responsible for... handling granted access.”

**Requirement**  
The application controller MUST be responsible for how granted access is handled and exercised.

**Classification**  
Controller responsibility; delegated access; accountability.

**Notes**  
Responsibility persists even where technical processing is performed by infrastructure or subcontractors.

---

## REM-04-060 — Credential security responsibility

**Source**  
Section 5: “The controller is responsible for... securing credentials.”

**Requirement**  
The application controller MUST be responsible for securing application credentials, keys and other authorisation material.

**Classification**  
Controller responsibility; credential security.

**Notes**  
Compromise handling and rotation procedures are elaborated later in the model.

---

## REM-04-061 — Declared-purpose compliance responsibility

**Source**  
Section 5: “The controller is responsible for... respecting declared purposes.”

**Requirement**  
The application controller MUST ensure that granted authority and accessed data are used consistently with declared purposes.

**Classification**  
Purpose limitation; controller responsibility; consent compliance.

**Notes**  
A valid technical grant does not authorise undisclosed or incompatible use outside the declared purpose.

---

## REM-04-062 — Retention-commitment compliance responsibility

**Source**  
Section 5: “The controller is responsible for... complying with retention commitments.”

**Requirement**  
The application controller MUST comply with its declared data-retention commitments.

**Classification**  
Data governance; controller responsibility; retention.

**Notes**  
Retention commitments may be communicated through the Application Manifest and consent process.

---

## REM-04-063 — Revocation-processing responsibility

**Source**  
Section 5: “The controller is responsible for... processing revocation.”

**Requirement**  
The application controller MUST process revocation in accordance with the protocol and applicable Permission Grant conditions.

**Classification**  
Revocation; controller responsibility; lifecycle.

**Notes**  
Processing includes ceasing future unauthorised access and fulfilling any associated token, credential or retention obligations.

---

## REM-04-064 — Security-incident reporting responsibility

**Source**  
Section 5: “The controller is responsible for... reporting material security incidents.”

**Requirement**  
The application controller MUST report material security incidents affecting the application’s Relay authority, credentials, grants or accessed information.

**Classification**  
Incident response; controller responsibility; transparency.

**Notes**  
The detailed reporting channel and timing are addressed by later manifest and compliance requirements.

---

## REM-04-065 — Distinguish Application Identity and controller

**Source**  
Section 5: “The protocol should distinguish between: application identity; application controller...”

**Requirement**  
The protocol SHOULD distinguish the Application Identity from the application controller.

**Classification**  
Role separation; application governance; recommendation.

**Notes**  
The application is the identified software actor; the controller is the responsible person, organisation or authority.

---

## REM-04-066 — Distinguish controller and hosting provider

**Source**  
Section 5: “The protocol should distinguish between... application controller; hosting provider...”

**Requirement**  
The protocol SHOULD distinguish the application controller from the hosting provider.

**Classification**  
Role separation; infrastructure governance; recommendation.

**Notes**  
A hosting provider may supply infrastructure without controlling the application’s declared purposes or permissions.

---

## REM-04-067 — Distinguish controller and software publisher

**Source**  
Section 5: “The protocol should distinguish between... application controller... software publisher...”

**Requirement**  
The protocol SHOULD distinguish the application controller from the software publisher.

**Classification**  
Role separation; software distribution; recommendation.

**Notes**  
The publisher or distributor of software may differ from the authority responsible for the Application Identity.

---

## REM-04-068 — Distinguish Application Identity and installation

**Source**  
Section 5: “The protocol should distinguish between... application identity... individual installation.”

**Requirement**  
The protocol SHOULD distinguish the Application Identity from each individual installation.

**Classification**  
Role separation; installation identity; recommendation.

**Notes**  
This supports installation-specific credentials, sessions or revocation without redefining the application’s stable identity.

---

## REM-04-069 — Distinguish controller and installation

**Source**  
Section 5, distinction among application identity, application controller, hosting provider, software publisher and individual installation.

**Requirement**  
The protocol SHOULD preserve the distinction between the responsible application controller and an individual application installation.

**Classification**  
Role separation; controller accountability; recommendation.

**Notes**  
An installation is an operational instance, not the person or authority accountable for application conduct.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 1–5 of `design-notes/04-application-and-permission-model.md`.
- Section 6 and later manifest-detail requirements were excluded.
- Examples were used to clarify scope but were not treated as closed taxonomies or final identifier syntax.

## Numbering verification

- First requirement: `REM-04-001`.
- Final requirement: `REM-04-069`.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Compound source statements were decomposed where they establish separately testable authority, ownership, scope or responsibility rules.
- Each listed core component was extracted independently because each represents a distinct architectural obligation.
- Each controller responsibility was extracted independently because each creates a separately auditable accountability obligation.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or supported options.
- Descriptive definitions were converted into normative requirements only where necessary to make the model testable, without strengthening optional language.

## Editorial verification

- Application authority remains explicit, valid, limited and revocable.
- Application access does not imply ownership of identities, repositories or records.
- Application Identity remains distinct from branding, company name, domain, callback URL, installation, device and version number.
- Application Identity remains distinct from the responsible controller.
- Controller responsibilities remain attributable even where infrastructure, publishing or installations are operated by separate parties.
- Application replacement and infrastructure change do not inherently break user continuity where identity continuity is authorised and verifiable.
