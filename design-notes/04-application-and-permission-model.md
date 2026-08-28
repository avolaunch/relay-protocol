# Relay Protocol v0.1  
## Core Object 4: Application and Permission Model

### 1. Definition

A **Relay Application** is software that requests limited authority to read from, write to or otherwise interact with a Relay Identity or Relay Repository.

A Relay Application may provide:

- a social interface;
- a publishing tool;
- a portfolio builder;
- an AI assistant;
- a messaging service;
- a professional network;
- an analytics service;
- an import or migration tool;
- a moderation service;
- a mobile or desktop client.

An application is not the owner of the identity, repository or records it accesses.

Its authority exists only through an explicit, valid and revocable **Permission Grant**.

---

## 2. Purpose

The Application and Permission Model exists to separate:

- the user’s underlying digital continuity;
- the service experience offered by an application;
- the authority granted to that application.

The model must allow a person to:

- connect an application without surrendering control of their identity;
- see exactly what the application wants to do;
- approve only the required capabilities;
- limit access by resource, action, duration and purpose;
- revoke access;
- inspect the application’s activity;
- replace the application without losing repository state.

The central principle is:

> Applications may act for a person, but they must not become the person.

---

## 3. Core components

The model contains the following components:

1. **Application Identity**
2. **Application Manifest**
3. **Permission Request**
4. **Permission Grant**
5. **Scope**
6. **Capability**
7. **Authorisation Session**
8. **Access Token or Capability Token**
9. **Delegated Key**
10. **Audit Event**
11. **Revocation Record**
12. **Consent Receipt**

---

## 4. Application Identity

Every Relay Application must have a stable machine-readable identity.

Example:

```text
rid:app:8df41k2m...
```

The Application Identity must be distinct from:

- the company name;
- the application’s visible product name;
- a domain;
- a callback URL;
- an installation;
- a specific device;
- a version number.

An application may change branding or infrastructure without becoming a new application identity, provided continuity is authorised and verifiable.

---

## 5. Application controller

Every Application Identity must identify the person, organisation or authority responsible for it.

The application controller may be:

- a company;
- an individual developer;
- a non-profit organisation;
- an open-source project;
- a government body;
- another Relay Identity.

The controller is responsible for:

- the accuracy of the Application Manifest;
- handling granted access;
- securing credentials;
- respecting declared purposes;
- complying with retention commitments;
- processing revocation;
- reporting material security incidents.

The protocol should distinguish between:

- application identity;
- application controller;
- hosting provider;
- software publisher;
- individual installation.

---

## 6. Application Manifest

An **Application Manifest** is a signed, versioned description of the application.

It should contain:

- Application Identity;
- visible application name;
- controller identity;
- application type;
- verified domains;
- redirect or callback locations;
- supported protocol versions;
- requested scope catalogue;
- privacy policy reference;
- data retention declaration;
- AI training declaration;
- contact details;
- security incident endpoint;
- current public keys;
- manifest version;
- signature.

Example:

```json
{
  "id": "rid:app:8df41k2m",
  "name": "Example Writing Client",
  "controller": "rid:relay:example-company",
  "version": 4,
  "domains": [
    "write.example.com"
  ],
  "callbacks": [
    "https://write.example.com/relay/callback"
  ],
  "keys": [
    {
      "id": "app-key-2",
      "type": "Ed25519",
      "publicKey": "..."
    }
  ],
  "dataPractices": {
    "retention": "7-days-after-revocation",
    "modelTraining": "prohibited",
    "thirdPartySharing": "none"
  },
  "signature": "..."
}
```

The exact structure remains provisional.

---

## 7. Manifest requirements

### 7.1 Versioned

Material changes must create a new manifest version.

Examples include:

- controller change;
- new domain;
- new callback location;
- changed retention policy;
- changed AI usage;
- key rotation;
- expanded permission catalogue.

### 7.2 Signed

The manifest must be signed by a valid authority for the Application Identity.

### 7.3 Discoverable

A Relay Provider must be able to resolve the current valid manifest before displaying a permission request.

### 7.4 Human-readable

The manifest must contain enough information for a consent interface to explain the request in ordinary language.

### 7.5 Machine-readable

The manifest must also support automated policy checks.

For example, a user may choose:

```text
Never allow applications that train models on my private records.
```

The Relay Provider should be able to evaluate that preference automatically.

---

## 8. Application verification status

An application may have a verification status such as:

```text
unverified
domain-verified
controller-verified
security-reviewed
ecosystem-certified
suspended
revoked
```

Verification must not be represented as a universal guarantee of trustworthiness.

It may indicate specific facts such as:

- control of a domain;
- identity of the controller;
- completion of a security review;
- acceptance into a provider catalogue.

The consent screen should explain what was actually verified.

---

## 9. Permission Request

A **Permission Request** is an application’s proposal for access to a Relay Identity or Repository.

A request must specify:

- the application;
- the identity being asked;
- requested resources;
- requested actions;
- duration;
- purpose;
- retention;
- onward sharing;
- whether AI processing is involved;
- whether model training is requested;
- whether access is interactive or continuous;
- whether high-authority operations are requested.

Example:

```json
{
  "application": "rid:app:8df41k2m",
  "resources": [
    {
      "collection": "com.relay.profile",
      "actions": ["read"]
    },
    {
      "collection": "com.relay.post",
      "actions": ["read", "create", "update"]
    }
  ],
  "duration": {
    "type": "until-revoked"
  },
  "purpose": [
    "display-profile",
    "publish-user-authored-content"
  ],
  "retention": {
    "cacheDuration": "7d",
    "retainAfterRevocation": false
  },
  "aiUse": {
    "inference": false,
    "training": false
  }
}
```

---

## 10. Permission Grant

A **Permission Grant** is a signed authorisation issued by the Relay Identity in response to a Permission Request.

A grant must be:

- explicit;
- limited;
- attributable;
- inspectable;
- revocable;
- time-bound where appropriate;
- no broader than the approved request.

Example:

```json
{
  "id": "grant_01JX8K",
  "issuer": "rid:relay:7fs82k9m4v",
  "application": "rid:app:8df41k2m",
  "issuedAt": "2026-08-24T10:00:00Z",
  "expiresAt": null,
  "resources": [
    {
      "collection": "com.relay.profile",
      "actions": ["read"]
    },
    {
      "collection": "com.relay.post",
      "actions": ["read", "create", "update"]
    }
  ],
  "purpose": [
    "display-profile",
    "publish-user-authored-content"
  ],
  "restrictions": {
    "modelTraining": false,
    "onwardSharing": false
  },
  "signature": "..."
}
```

The grant itself may be stored as an authority record in the repository or in a dedicated authorisation service.

---

## 11. Scope

A **Scope** defines the boundary of access.

Relay scopes should be composable rather than expressed as broad labels such as:

```text
Full account access
```

A scope may be limited by:

- repository;
- collection;
- specific record;
- record field;
- action;
- audience;
- time;
- purpose;
- application installation;
- device;
- frequency;
- geographic or legal context.

Example:

```text
Read public profile records
```

is narrower than:

```text
Read all repository records
```

And:

```text
Update record post_123
```

is narrower than:

```text
Update all posts
```

---

## 12. Resource scope

A resource scope identifies what the application may access.

Possible resource levels include:

### Repository-wide

```text
Entire repository
```

This should be rare and treated as highly sensitive.

### Collection-level

```text
com.relay.post
```

### Record-level

```text
relay://rid:relay:alice/com.relay.post/post_123
```

### Field-level

```text
Profile display name and avatar only
```

### Blob-level

```text
Read and upload portfolio images
```

### Derived service-level

```text
Receive public repository events
```

The protocol should prefer the narrowest practical scope.

---

## 13. Action scope

A grant must identify allowed actions.

Relay v0.1 should distinguish at least:

```text
discover
read
list
create
update
delete
restore
upload-blob
attach-blob
change-visibility
change-audience
subscribe-events
export
import
migrate
manage-permissions
manage-keys
manage-recovery
```

High-authority actions such as:

```text
migrate
manage-keys
manage-recovery
manage-permissions
```

must not be bundled with ordinary content access.

---

## 14. Read access

Read access may apply to:

- current record content;
- historical versions;
- metadata only;
- blobs;
- provenance;
- restricted content;
- private content.

The grant must distinguish these.

For example:

```text
Read current public posts
```

must not automatically permit:

```text
Read deleted versions of private posts
```

---

## 15. Write access

Write access must distinguish between:

- creating new records;
- updating existing records;
- deleting records;
- changing visibility;
- changing rights;
- submitting drafts;
- publishing canonical records.

An application allowed to create a draft should not automatically be allowed to publish it.

An application allowed to update the text of a record should not automatically be allowed to make it public.

---

## 16. Purpose limitation

Every non-trivial permission request should declare a purpose.

Examples:

```text
Display a public profile
Publish user-authored posts
Generate a private summary
Import an archive
Provide search
Recommend content
Measure readership
Train a general-purpose model
```

Purpose is separate from action.

Two applications may request the same action for different purposes.

For example:

```text
Read private notes to answer the user’s questions
```

is materially different from:

```text
Read private notes to improve a commercial AI model
```

The permission model must be capable of representing that distinction.

---

## 17. Purpose vocabulary

Relay should define a basic machine-readable purpose vocabulary while allowing extension.

Possible core purposes include:

```text
identity-display
content-display
content-publishing
communication
search
indexing
recommendation
analytics
personalisation
moderation
backup
migration
AI-inference
AI-training
research
commercial-licensing
security
fraud-prevention
```

An application may provide additional explanatory text, but should not rely only on vague custom wording.

---

## 18. Retention

A permission request must declare whether the application retains data outside the repository.

Possible declarations include:

```text
no-retention
session-only
temporary-cache
retained-until-revocation
retained-for-defined-period
retained-indefinitely
```

Where a period is declared, it should be machine-readable.

Example:

```json
{
  "retention": {
    "type": "temporary-cache",
    "duration": "P7D"
  }
}
```

The protocol cannot technically guarantee deletion of all external copies.

However, it can:

- make the commitment explicit;
- record what the user approved;
- enable audits;
- identify non-compliant applications;
- support contractual enforcement.

---

## 19. Onward sharing

Applications must declare whether data may be disclosed to third parties.

Possible values include:

```text
none
processors-only
named-parties
category-based
unrestricted
```

Where possible, the request should identify:

- the third party;
- the category of data shared;
- the purpose;
- the retention period;
- whether the third party receives direct repository access or a copy.

A grant prohibiting onward sharing must not be treated as permission to distribute data through an application partner network.

---

## 20. AI processing

The permission model must treat AI use as several distinct activities.

These include:

### AI inference

Using records temporarily to produce an output for the user.

### Personalisation

Using records to tailor an application’s behaviour.

### Embedding or indexing

Transforming records into vectors or other searchable representations.

### Fine-tuning

Using records to adapt a model for a specific user or application.

### General model training

Using records to improve a model for broader use.

### Evaluation

Using records to test or benchmark a system.

These should not be collapsed into a single checkbox labelled:

```text
Allow AI
```

---

## 21. AI permission declaration

An AI-related request should declare:

```json
{
  "aiUse": {
    "inference": true,
    "personalisation": true,
    "embedding": true,
    "fineTuning": false,
    "generalTraining": false,
    "humanReview": false,
    "externalModelProvider": "rid:app:model-provider"
  }
}
```

The consent interface should explain:

- what data is used;
- which AI activity occurs;
- where processing occurs;
- whether a third-party model provider is involved;
- whether data is retained;
- whether humans may review inputs or outputs.

---

## 22. Duration

A Permission Grant may be valid:

```text
for one operation
for one session
until a specific time
for a defined duration
until revoked
while a relationship remains valid
while a credential remains valid
```

Examples:

```json
{
  "duration": {
    "type": "one-operation"
  }
}
```

or:

```json
{
  "duration": {
    "type": "expires-at",
    "value": "2026-09-24T00:00:00Z"
  }
}
```

Indefinite grants should still be reviewable and revocable.

---

## 23. One-time capabilities

Some operations should use a one-time capability rather than a long-lived grant.

Examples:

- import one archive;
- publish one post;
- download one export;
- approve one migration;
- share one restricted record;
- upload one blob.

A one-time capability becomes invalid after:

- successful use;
- expiration;
- revocation;
- failure threshold;
- change in relevant repository state.

---

## 24. Conditional permission

A grant may include conditions.

Examples:

```text
May publish only after user confirmation
May read only public posts
May update only records it originally created
May upload files smaller than 50 MB
May access private notes only from the user’s registered device
May export only after high-authority authentication
```

Example:

```json
{
  "conditions": {
    "userConfirmationRequired": true,
    "maximumBlobSize": 52428800,
    "createdByApplicationOnly": true
  }
}
```

---

## 25. Permission inheritance

Permission should not be inherited implicitly merely because records are related.

For example:

- permission to read a post does not automatically permit reading the author’s private profile;
- permission to read a project does not automatically permit reading every collaborator’s repository;
- permission to access a folder-like collection does not necessarily permit deleted versions.

Any inheritance rules must be explicit in the schema or grant.

---

## 26. Consent interface

A Relay Provider or trusted authorisation service should present the permission request to the user.

The interface must show:

- application name;
- responsible controller;
- verification status;
- requested data;
- requested actions;
- duration;
- purpose;
- retention;
- AI use;
- onward sharing;
- high-risk capabilities;
- whether the request differs from a previous version.

The interface should not rely on legalistic phrases such as:

```text
Access your data
```

It should show concrete consequences.

Example:

> This application can read your public profile, create and edit posts at your instruction, and cache those posts for seven days. It cannot read private records, delete posts, train AI models or share copies with third parties.

---

## 27. Granular approval

The user should be able to approve less than the full request where practical.

For example, the application requests:

```text
Read profile
Read posts
Create posts
Delete posts
Read private drafts
```

The user may approve:

```text
Read profile
Read posts
Create posts
```

and deny:

```text
Delete posts
Read private drafts
```

The application may then:

- operate with reduced capability;
- explain that some features are unavailable;
- decline to continue if a genuinely essential permission was refused.

It must not falsely describe optional access as essential.

---

## 28. Consent receipt

After approval, the user should receive a **Consent Receipt**.

The receipt records:

- application;
- manifest version;
- approved scopes;
- denied scopes;
- purpose;
- retention declaration;
- AI declaration;
- issue time;
- expiration;
- user-facing explanation shown at approval;
- grant identifier.

The receipt allows the person to later answer:

> What exactly did I agree to?

The consent receipt may be stored privately in the repository or authorisation service.

---

## 29. Authorisation session

An **Authorisation Session** is the temporary interaction through which a person reviews and approves a Permission Request.

The session should be protected against:

- callback substitution;
- replay;
- request tampering;
- cross-site request forgery;
- session fixation;
- malicious redirect locations.

The implementation should follow modern secure authorisation practices, including:

- exact callback matching;
- short-lived authorisation codes;
- proof key mechanisms;
- state validation;
- nonce validation;
- secure transport.

The Relay protocol need not reinvent all low-level authorisation mechanisms.

---

## 30. Access token

An **Access Token** allows an application to exercise an approved grant.

A token must be:

- limited to the grant;
- time-bound;
- audience-bound;
- protected against tampering;
- revocable or short-lived;
- unsuitable as proof of ownership of the identity.

The token should identify or reference:

- Application Identity;
- Relay Identity;
- Permission Grant;
- approved capabilities;
- expiration;
- intended Relay Provider or service.

---

## 31. Short-lived and long-lived access

Relay should prefer short-lived access tokens.

Long-running access may use:

- refresh tokens;
- renewable capability sessions;
- delegated keys;
- re-authorisation.

Refresh authority must be revocable independently of already expired access tokens.

High-authority actions should require fresh authentication rather than relying only on a long-lived background session.

---

## 32. Capability token

Relay may support capability-based access in addition to conventional scopes.

A capability token grants authority over a specific object or operation.

Example:

```text
May update post_123 until 14:00
```

This is more precise than:

```text
May update all posts indefinitely
```

Capability tokens may be useful for:

- collaborative editing;
- temporary sharing;
- one-time publication;
- restricted record access;
- delegated workflow steps.

---

## 33. Delegated application key

An application may receive a delegated key associated with a Permission Grant.

The key may sign repository submissions within the grant’s limits.

A delegated key must not be able to:

- alter the Relay Identity;
- expand its own permissions;
- change recovery authority;
- migrate the repository;
- create valid operations outside the grant.

The repository must verify both:

- the delegated signature;
- the continuing validity of the underlying grant.

---

## 34. Application installations

One application may exist across multiple installations.

Examples:

- web session;
- mobile phone;
- desktop application;
- browser extension;
- server-side background worker.

The permission model should distinguish:

- the Application Identity;
- a specific installation;
- a specific device;
- a specific session.

The user may revoke:

```text
the entire application
```

or only:

```text
the installation on an old device
```

where the implementation supports this distinction.

---

## 35. Background access

An application requesting continuous or background access must declare it.

Examples include:

- syncing records;
- generating a daily digest;
- monitoring repository events;
- maintaining a search index;
- processing incoming replies.

The user-facing consent must explain that the application may act while the user is not actively using it.

Background access should use narrower, renewable authority wherever practical.

---

## 36. User-present and user-absent actions

Relay should distinguish:

### User-present action

The user is actively interacting with the application.

Example:

```text
User presses Publish.
```

### User-absent action

The application acts later or continuously.

Example:

```text
Application automatically republishes scheduled content.
```

A grant may permit one and not the other.

Example:

```json
{
  "actions": ["create"],
  "interactionMode": "user-present-only"
}
```

---

## 37. High-authority operations

Certain operations require stronger protection.

These include:

- provider migration;
- repository export containing private records;
- key rotation;
- recovery changes;
- identity transfer;
- repository erasure;
- granting another application permission-management authority.

A normal content application token must not perform these operations.

High-authority actions should require:

- fresh authentication;
- stronger authentication;
- explicit confirmation;
- operation-specific capability;
- delay or secondary approval where appropriate.

---

## 38. Permission management authority

An application should not normally be allowed to grant itself or other applications additional permissions.

Permission management is a high-authority capability.

Where delegated, the grant must define:

- which applications may be managed;
- which scopes may be granted;
- maximum duration;
- whether user confirmation is required;
- whether grants may be revoked.

This may be useful for enterprise or guardian-managed identities, but should not be standard consumer behaviour.

---

## 39. Revocation

The user must be able to revoke a Permission Grant.

Revocation may apply to:

- an entire application;
- one installation;
- one scope;
- one collection;
- one record;
- one delegated key;
- one refresh authority;
- one active session.

A revocation must become effective for future access as quickly as practical.

---

## 40. Revocation Record

A **Revocation Record** identifies authority that is no longer valid.

Example:

```json
{
  "grant": "grant_01JX8K",
  "revokedAt": "2026-08-25T12:00:00Z",
  "revokedBy": "rid:relay:7fs82k9m4v",
  "reason": "user-revoked",
  "signature": "..."
}
```

Possible reasons include:

```text
user-revoked
expired
application-compromised
application-suspended
scope-replaced
provider-security-action
identity-recovery
controller-change
```

The reason may be private or generalised where disclosure would create risk.

---

## 41. Revocation effects

After revocation:

- new access tokens must not be issued;
- refresh authority must fail;
- delegated keys must become invalid;
- background subscriptions must stop;
- new repository submissions must be rejected;
- event delivery must cease;
- cached or retained data must be handled according to the approved retention declaration.

Revocation does not automatically erase:

- canonical records already created;
- copies lawfully disclosed;
- audit history;
- data another party is legally required to retain.

---

## 42. Records created by revoked applications

Revoking an application must not delete records merely because the application originally created them.

For example:

- a post remains in the user’s repository;
- a project remains portable;
- a comment remains under the user’s authority;
- an imported archive remains available.

The user may separately choose to delete those records.

This is essential to application replaceability.

---

## 43. Scope reduction

A user may narrow a grant without fully revoking it.

Example:

```text
Before:
Read, create, update and delete posts

After:
Read and create posts
```

A revised grant should:

- supersede the previous grant;
- invalidate authority no longer included;
- preserve an audit trail;
- avoid forcing unnecessary reconnection.

---

## 44. Re-authorisation

An application must request re-authorisation when:

- the existing grant expires;
- it requests broader scopes;
- its controller changes;
- its retention policy materially changes;
- its AI usage changes;
- it adds onward sharing;
- its manifest is materially different;
- a security event invalidates existing authority.

An application may not silently rely on an old approval for materially new behaviour.

---

## 45. Manifest drift

A Relay Provider should compare the approved Application Manifest version with the current manifest.

If the current version introduces material changes, the provider may:

- pause access;
- restrict access to previously approved behaviour;
- require user review;
- revoke the grant in severe cases.

Minor non-material changes need not trigger full re-authorisation.

The protocol should define which manifest changes are material.

---

## 46. Audit events

The authorisation system should produce audit events for:

- permission requested;
- permission granted;
- permission denied;
- token issued;
- high-risk action performed;
- grant narrowed;
- grant renewed;
- grant revoked;
- application manifest changed;
- application security incident reported;
- unauthorised attempt rejected.

Audit events should identify:

- time;
- application;
- grant;
- resource;
- action;
- result;
- installation where relevant.

Sensitive audit information may remain private.

---

## 47. User access history

A person should be able to inspect:

- connected applications;
- current grants;
- recently used permissions;
- last access time;
- records created or changed;
- exports performed;
- active installations;
- background subscriptions;
- revoked applications.

The system should show meaningful information such as:

```text
Example Writing Client updated post_123 yesterday at 14:32.
```

rather than only displaying token identifiers.

---

## 48. Application activity attribution

Repository changes made through an application should retain attribution.

Example:

```json
{
  "authorisedBy": "rid:relay:alice",
  "submittedBy": "rid:app:writing-client",
  "grant": "grant_01JX8K",
  "installation": "install_72A"
}
```

This does not make the application the author or owner.

It records how the operation entered the repository.

---

## 49. Application suspension

A Relay Provider or ecosystem authority may mark an application as suspended because of:

- compromised keys;
- malware;
- fraud;
- manifest deception;
- repeated permission abuse;
- controller request;
- legal restriction.

Suspension may prevent:

- new grants;
- token renewal;
- repository submissions;
- event delivery.

The application’s suspension must not delete the user’s records.

---

## 50. Application key compromise

If an application key is compromised:

- the application controller should publish a manifest update;
- affected keys should be revoked;
- providers should reject new requests signed by compromised keys;
- affected grants may require re-authorisation;
- suspicious activity should be visible to users.

A key compromise affecting the application must not automatically compromise the user’s root identity authority.

---

## 51. Malicious or deceptive applications

The protocol cannot eliminate malicious software.

It can reduce damage by requiring:

- narrow grants;
- signed manifests;
- verified callback locations;
- explicit purpose declarations;
- short-lived tokens;
- auditability;
- fast revocation;
- separation of high-authority operations;
- application reputation and verification layers.

Providers and users may apply trust policies before approving applications.

---

## 52. Application portability

An application itself may change hosting providers or infrastructure while retaining the same Application Identity.

This requires:

- an authorised manifest update;
- continuity of controller authority;
- updated service locations;
- updated keys or callbacks;
- no silent expansion of permissions.

Users should not be forced to approve an entirely new application merely because its servers moved.

---

## 53. Application replacement

The model must allow a person to stop using Application A and begin using Application B.

Application B may receive permission to:

- read the same profile;
- display the same posts;
- update the same records;
- interact with the same relationships.

The user must not need to recreate the underlying repository state.

Application-specific records may remain unsupported, but they must be preserved.

---

## 54. Permission portability during provider migration

When a repository moves providers, existing grants may continue only if:

- the grant is provider-independent;
- the new provider supports the relevant capability;
- the application can securely discover the new provider;
- the user has not revoked the grant;
- migration policy allows continuation.

Provider-specific tokens should not simply be copied.

The new provider may issue new tokens based on the continuing grant.

High-risk grants may require re-authorisation after migration.

---

## 55. Provider access

A Relay Provider’s own access must also be defined.

Hosting a repository may require operational authority to:

- store records;
- serve records;
- validate commits;
- deliver events;
- create backups;
- scan for malware;
- enforce legal restrictions.

The provider must not treat hosting access as an unrestricted application grant.

Its operational authority should be documented separately and limited to the hosting agreement and protocol role.

---

## 56. First-party applications

An application built by the current Relay Provider must still identify itself as an application.

The user should be able to distinguish:

- provider infrastructure;
- provider administrative access;
- optional first-party client;
- third-party applications.

A provider must not evade the Permission Model merely because it also built the interface.

---

## 57. Service-to-service applications

Some applications may operate without a direct end-user interface.

Examples:

- search indexer;
- moderation labeller;
- backup service;
- media transcoder;
- analytics processor.

These services must still have:

- an Application Identity;
- a manifest;
- defined scopes;
- declared purpose;
- limited authority;
- revocation behaviour.

A hidden backend integration is still an application actor.

---

## 58. Indexer permissions

Public indexers may read public records without a private grant where protocol policy allows.

However, restricted or private indexing requires explicit authority.

Indexers should declare:

- indexing purpose;
- refresh behaviour;
- deletion handling;
- retention;
- whether embeddings are created;
- whether model training occurs;
- how users request removal from the index.

Indexing does not make the indexer the canonical source.

---

## 59. Consent delegation

In some cases, another authority may approve permissions on behalf of the identity.

Examples:

- parent or guardian;
- organisational administrator;
- legal representative;
- enterprise security policy;
- delegated agent.

The system must record:

- who approved;
- under what authority;
- whether the controller may override the decision;
- when the delegation expires.

Consent delegation must not be inferred merely from access to an account.

---

## 60. Organisational application grants

An organisational Relay Identity may require multi-party approval.

Example:

```text
Two authorised directors must approve repository export.
```

A grant may remain pending until the required approval threshold is met.

Relay v0.1 may implement only basic multi-controller support, but the model should not assume that every permission comes from one individual click.

---

## 61. Denial

A user may deny a request.

The denial may be:

- complete;
- partial;
- temporary;
- policy-based.

The system should avoid revealing unnecessary private policy details to the application.

For example, the application may receive:

```text
permission_denied
```

rather than:

```text
denied because user blocks all applications from this company
```

---

## 62. Automatic policy enforcement

A user may define standing rules such as:

```text
Never allow general model training.
Allow public-profile readers automatically.
Require confirmation for deletion.
Expire inactive grants after 90 days.
Block unverified applications from private records.
```

The authorisation service may evaluate requests against these policies.

Automatic approval should be limited to low-risk, pre-authorised conditions.

---

## 63. Inactive grants

A grant that has not been used for a long period may be:

- flagged for review;
- automatically expired according to user policy;
- restricted until re-authentication;
- left unchanged.

The user should be able to see stale permissions.

Relay should discourage permanent forgotten access.

---

## 64. Emergency revocation

A user should be able to perform an emergency action such as:

```text
Revoke all applications
```

This may be necessary after:

- device theft;
- identity recovery;
- suspected compromise;
- malicious application activity.

Emergency revocation should not:

- delete repository records;
- terminate the identity;
- erase audit history.

---

## 65. Required v0.1 application operations

A compliant implementation must support:

```text
Register Application Identity
Resolve Application Manifest
Verify Application Manifest
Submit Permission Request
Display Permission Request
Approve full request
Approve partial request
Deny request
Issue Permission Grant
Read Permission Grant
Issue short-lived access token
Renew authorised access
Validate access token
Create delegated application key
List connected applications
Inspect application activity
Narrow Permission Grant
Revoke Permission Grant
Revoke installation
Revoke delegated key
Expire Permission Grant
Require re-authorisation
Record Consent Receipt
Record Audit Event
```

High-authority capability grants may be limited in the first reference implementation.

---

## 66. Permission invariants

The following rules must always remain true.

### Invariant 1

An application has no authority without a valid grant or public-access rule.

### Invariant 2

A grant cannot authorise more than the user approved.

### Invariant 3

An application cannot expand its own grant.

### Invariant 4

Revoking an application does not delete canonical records it previously created.

### Invariant 5

Permission to read does not imply permission to retain, redistribute or train models.

### Invariant 6

Permission to create a record does not imply permission to delete or change its visibility.

### Invariant 7

Ordinary content access does not imply identity, key, recovery or migration authority.

### Invariant 8

An application’s visible name is not its permanent protocol identity.

### Invariant 9

A materially changed application purpose requires renewed approval.

### Invariant 10

A provider-built client remains subject to the application model.

### Invariant 11

The user must be able to inspect and revoke active grants.

### Invariant 12

Provider migration must not silently broaden application access.

### Invariant 13

Application suspension must not erase user-owned repository records.

### Invariant 14

A token is evidence of delegated authority, not ownership of the Relay Identity.

---

## 67. Compliance scenario

A basic application implementation should pass the following test.

### Initial request

Application A requests:

```text
Read public profile
Read posts
Create posts
Update posts
Delete posts
Read private drafts
Train a recommendation model
```

### Partial approval

The user approves:

```text
Read public profile
Read posts
Create posts
Update posts
```

The user denies:

```text
Delete posts
Read private drafts
Train a recommendation model
```

The issued grant contains only the approved capabilities.

### Record creation

Application A creates a post under the grant.

The repository records:

- the user as authorising identity;
- Application A as submitter;
- the Permission Grant used.

### Unauthorised deletion attempt

Application A attempts to delete the post.

The repository rejects the operation because deletion was not granted.

### Manifest change

Application A later changes its policy to permit general model training.

The existing grant does not automatically expand.

The user must review and approve the changed purpose.

### Revocation

The user revokes Application A.

Application A can no longer:

- obtain new tokens;
- submit updates;
- receive private events.

The post remains in the repository.

### Replacement

Application B receives permission to read and update posts.

Application B opens and edits the post originally created through Application A.

No export, copying or account recreation is required.

If all these actions occur while preserving user authority and application replaceability, the implementation satisfies the basic Relay Application and Permission objective.

---

## 68. Open design questions

### 68.1 Authorisation standard

Should Relay directly adopt an existing OAuth-based profile, define a compatible extension or create a capability-first authorisation layer?

### 68.2 Grant storage

Should Permission Grants live inside the main repository, a separate private authority repository or the Relay Provider’s authorisation service?

### 68.3 Purpose enforcement

Which purpose restrictions can be technically enforced, and which remain auditable commitments?

### 68.4 Field-level access

How much complexity should v0.1 accept for permissions limited to specific record fields?

### 68.5 Delegated keys

Should delegated application keys be required, optional or postponed in the first reference implementation?

### 68.6 Cross-provider grants

How should a new provider validate grants originally issued through another provider?

### 68.7 Application trust registry

Should Relay define a shared application registry, rely on distributed manifests or support both?

### 68.8 Material manifest change

Which application changes must invalidate or pause existing grants?

### 68.9 AI vocabulary

What standard vocabulary is sufficient to distinguish inference, embeddings, fine-tuning, evaluation and general training?

### 68.10 Legal terms

How should machine-readable permission terms relate to privacy policies, contracts and regional law?

### 68.11 Public data access

Which usage declarations, if any, can be attached to public records without requiring a direct grant?

### 68.12 Installation identity

Should each installation have its own key pair and revocation state in v0.1?

---

## 69. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- every application has a stable Application Identity;
- every application publishes a signed, versioned manifest;
- grants are explicit and revocable;
- scopes are defined by resource and action;
- purpose, retention, onward sharing and AI use are separate declarations;
- partial approval is supported;
- ordinary access uses short-lived tokens;
- long-running access uses renewable authority;
- high-authority operations require separate approval;
- application-created records remain in the user’s repository after revocation;
- materially expanded behaviour requires re-authorisation;
- providers maintain private audit records;
- users can inspect connected applications and revoke access;
- provider migration preserves grants where safely possible but replaces provider-specific tokens;
- OAuth-compatible authorisation practices will be preferred over a wholly proprietary login mechanism;
- purpose restrictions may initially be partly contractual and auditable rather than fully technically enforceable.

---

## 70. Core application principle

The Application and Permission Model can be reduced to one rule:

> A Relay Application receives temporary, limited authority to interact with a person’s digital continuity; it never receives ownership of that continuity.

The next core object is the **Relay Relationship Model**: how follows, subscriptions, collaborations, memberships and other connections exist independently of the applications through which they were created.