# Relay Protocol v0.1  
## Core Object 8: Discovery and Resolution Model

### 1. Definition

**Relay Discovery and Resolution** is the process through which an application translates a human-readable handle or permanent Relay Identifier into the current, verifiable operational information required to interact with a Relay Identity.

That information may include:

- the current Identity Document;
- the current Relay Provider;
- repository location;
- authorisation endpoint;
- event endpoint;
- supported protocol versions;
- public keys;
- verified handles;
- migration status;
- service capabilities.

Resolution must continue working when the identity:

- changes provider;
- changes handle;
- rotates keys;
- moves services;
- temporarily loses a provider;
- recovers from a compromised service;
- uses different providers for different functions.

The resolution system must not make one application or hosting provider the permanent gatekeeper of the identity.

---

## 2. Purpose

The Discovery and Resolution Model exists to answer two fundamental questions:

> Which persistent Relay Identity does this visible name refer to?

and:

> Where are that identity’s current authorised services located?

Without a reliable resolution mechanism:

- applications would store permanent provider URLs;
- changing provider would break incoming references;
- handles could be confused with identities;
- released usernames could inherit historical relationships;
- malicious providers could redirect identities;
- provider disappearance could make identities unreachable;
- migration would remain dependent on the former provider.

Resolution is therefore the bridge between persistent identity and replaceable infrastructure.

---

## 3. Core distinction

Relay must distinguish between:

1. **Identity**
2. **Handle**
3. **Identity Document**
4. **Service Location**

These are related, but they are not interchangeable.

### Identity

The permanent protocol-level entity.

Example:

```text
rid:relay:7fs82k9m4v
```

### Handle

A human-readable name associated with the identity.

Example:

```text
miles.example.com
```

### Identity Document

The signed operational description of the identity.

### Service Location

A current endpoint where a Relay service can be reached.

Example:

```text
https://provider-b.example/repository/7fs82k9m4v
```

A handle may change.

A service location may change.

An Identity Document may be updated.

The Relay Identifier remains stable.

---

## 4. Resolution inputs

A Relay resolver may receive one of several input types.

### Relay Identifier

```text
rid:relay:7fs82k9m4v
```

This should resolve directly to the current valid Identity Document.

### Human-readable handle

```text
miles.example.com
```

This must first resolve to a Relay Identifier, then to the current Identity Document.

### Record URI

```text
relay://rid:relay:7fs82k9m4v/com.relay.post/post_123
```

The resolver extracts the Relay Identifier, resolves its current repository service, then requests the record.

### Historical service URL

```text
https://provider-a.example/repository/7fs82k9m4v
```

The former provider may return a signed migration response pointing toward the current Identity Document or service location.

### Application-specific alias

An application may store a local alias, but it must ultimately resolve to a Relay Identifier rather than become a separate identity authority.

---

## 5. Resolution outputs

A successful identity resolution should return or reference:

- Relay Identifier;
- current Identity Document;
- Identity Document version;
- document integrity hash;
- current valid keys;
- current service locations;
- verified handles;
- protocol versions;
- resolution time;
- migration or recovery status;
- verification evidence.

Example:

```json
{
  "id": "rid:relay:7fs82k9m4v",
  "identityDocument": {
    "version": 8,
    "hash": "sha256:identity-document-8...",
    "updatedAt": "2026-08-24T16:00:00Z"
  },
  "handles": [
    {
      "value": "miles.example.com",
      "status": "verified"
    }
  ],
  "services": {
    "repository": "https://provider-b.example/repository/7fs82k9m4v",
    "authorization": "https://provider-b.example/authorize",
    "events": "https://provider-b.example/events"
  },
  "status": "active"
}
```

The exact transport format remains provisional.

---

## 6. Resolution trust requirements

A resolver must not trust a service location merely because a server returned it.

The resolver should verify:

- that the Identity Document names the requested Relay Identifier;
- that the document is correctly signed;
- that the signing authority was valid;
- that the document supersedes the previous valid document;
- that the requested handle is genuinely linked to the identity;
- that service locations belong to the current document;
- that the document is not known to be revoked or superseded.

---

## 7. Discovery versus resolution

Relay should distinguish:

### Discovery

Finding possible information about an identity.

Examples:

- searching for a person by visible name;
- finding a Relay handle;
- locating a public profile;
- identifying possible matching identities.

### Resolution

Cryptographically establishing the current operational Identity Document for a specific Relay Identifier or verified handle.

Discovery may return several possible results.

Resolution should produce one verified identity result or a clear failure.

Search ranking must not become identity authority.

---

## 8. Human-readable handles

A Relay handle exists to make identities usable by people.

Possible handle forms include:

```text
miles.example.com
@miles@example.com
miles.relay.example
```

The final syntax remains open.

A handle must not be treated as the permanent identity anchor.

The handle resolves to the Relay Identifier.

The Relay Identifier does not derive its authority from continued possession of the handle alone.

---

## 9. Domain-based handles

A domain-based handle may be verified through DNS or a well-known resource.

Example:

```text
miles.example.com
```

Possible verification methods include:

- DNS TXT record;
- HTTPS-hosted identity file;
- domain-signed challenge;
- delegated subdomain record;
- DNSSEC-supported assertion.

A domain-based handle provides useful independence from a Relay Provider because the person may control the domain separately.

---

## 10. DNS verification

A possible DNS record might contain:

```text
_relay.miles.example.com TXT "rid=rid:relay:7fs82k9m4v"
```

A resolver may verify:

- that the record is published under the expected domain;
- that the declared Relay Identifier matches the Identity Document;
- that the Identity Document also lists the domain as a verified handle.

Verification should be bidirectional.

The domain points to the identity.

The identity also claims the domain.

---

## 11. HTTPS verification

A domain may publish a document at a standard location such as:

```text
https://miles.example.com/.well-known/relay-identity
```

The document may contain:

```json
{
  "relayIdentifier": "rid:relay:7fs82k9m4v",
  "identityDocument": "https://resolver.example/identity/rid:relay:7fs82k9m4v",
  "proof": "..."
}
```

The exact location and structure remain provisional.

HTTPS verification should require valid transport security and should ideally be supported by additional signed identity evidence.

---

## 12. Provider-issued handles

A Relay Provider may issue a handle such as:

```text
miles.provider-a.example
```

This provides convenient onboarding.

However, it is less independent than a user-controlled domain.

If the user leaves Provider A:

- the provider-based handle may be retired;
- it may redirect temporarily;
- the user may adopt another handle;
- the Relay Identifier remains unchanged.

Applications must not treat the loss of a provider-issued handle as the loss of the identity.

---

## 13. Multiple handles

A Relay Identity may have multiple handles.

Examples:

```text
miles.example.com
miles.provider-b.example
@miles
```

Each handle may have its own:

- verification method;
- status;
- issue time;
- expiration;
- intended context;
- priority.

One handle may be designated as preferred for display.

Applications should still store the Relay Identifier as the durable reference.

---

## 14. Handle status

A handle may have a status such as:

```text
asserted
pending-verification
verified
expired
revoked
released
disputed
historical
```

A displayed verification badge should identify what was verified.

For example:

```text
Verified control of miles.example.com
```

is more precise than:

```text
Verified person
```

Domain control does not automatically verify legal identity.

---

## 15. Handle binding

A **Handle Binding** links a handle to a Relay Identifier.

A valid binding should contain or prove:

- handle;
- Relay Identifier;
- issue time;
- verification method;
- current status;
- optional expiration;
- proof from the handle authority;
- acknowledgement in the Identity Document.

Example:

```json
{
  "handle": "miles.example.com",
  "relayIdentifier": "rid:relay:7fs82k9m4v",
  "verifiedAt": "2026-08-24T10:00:00Z",
  "method": "dns",
  "status": "verified"
}
```

---

## 16. Bidirectional verification

Relay should prefer bidirectional verification.

### Direction 1

The handle authority states:

```text
This handle refers to Relay Identity X.
```

### Direction 2

Relay Identity X states:

```text
This handle belongs to me.
```

Both directions reduce the risk of:

- mistaken records;
- malicious claims;
- stale handle bindings;
- identity impersonation.

---

## 17. Handle reassignment

A handle may later be assigned to another identity.

Example:

```text
@miles
```

was previously linked to Identity A and is later linked to Identity B.

Applications must not transfer:

- old relationships;
- old records;
- old credentials;
- historical reputation;
- messages;
- permissions;

from Identity A to Identity B.

Historical objects remain linked to Relay Identifier A.

The visible handle may change in current displays.

---

## 18. Handle history

An identity may retain a history of former handles.

Example:

```json
{
  "handle": "miles.provider-a.example",
  "status": "historical",
  "validFrom": "2025-01-01T00:00:00Z",
  "validUntil": "2026-08-24T16:00:00Z"
}
```

Historical handle information can help explain old screenshots, mentions and cached displays.

A historical handle must not continue to function as current identity authority unless explicitly redirected.

---

## 19. Handle collision

A collision occurs when multiple identities claim the same handle.

Resolution must not choose an identity based only on:

- search rank;
- provider preference;
- earliest cached result;
- visible profile similarity.

The resolver should require valid current handle-binding evidence.

If conflicting valid-looking claims exist, the handle should be marked disputed until resolved.

---

## 20. Handle dispute

A handle dispute may involve:

- expired domain ownership;
- provider naming conflict;
- compromised DNS;
- stale cached binding;
- fraudulent claim;
- legal trademark dispute.

The protocol can determine cryptographic control.

It cannot necessarily settle all legal rights to a name.

Applications should distinguish:

- technically verified control;
- provider naming policy;
- legal ownership claims.

---

## 21. Permanent Relay Identifier resolution

Resolving a Relay Identifier is more important than resolving a handle.

The resolver must obtain the current valid Identity Document for:

```text
rid:relay:7fs82k9m4v
```

This mechanism must remain operational when the current provider changes.

The resolution method is therefore one of the most important architectural decisions in Relay v0.1.

---

## 22. Resolution architecture options

Several architectures are possible.

### 22.1 Provider-based resolution

The Relay Identifier points directly to a provider.

This is simple but undermines provider independence.

### 22.2 Domain-based resolution

The identity is anchored to a user-controlled domain.

This offers independence but requires domain ownership and creates recovery risks if the domain expires.

### 22.3 Distributed resolver network

Independent resolvers replicate signed Identity Documents.

This reduces dependence on one provider but introduces network governance and consistency challenges.

### 22.4 Transparency log

Identity Document updates are published to one or more append-only logs.

This supports auditability but may require an additional lookup layer.

### 22.5 Existing decentralised identifier infrastructure

Relay could use or profile an existing decentralised identifier method.

This reduces invention but may inherit complexity and governance assumptions.

### 22.6 Hybrid resolution

Relay could combine:

- signed Identity Documents;
- user-controlled domains where available;
- replicated resolution nodes;
- optional transparency logs;
- recovery publication authority.

A hybrid model is the likely direction for v0.1.

---

## 23. Provider independence requirement

The current Relay Provider must not hold the only method of publishing a new Identity Document.

Otherwise, the provider could prevent migration by refusing to update resolution.

The controller needs at least one authority path independent of the active provider.

Possible independent paths include:

- user-held root key;
- recovery key;
- controller-owned domain;
- independent resolution service;
- replicated signed update log;
- trusted recovery quorum.

---

## 24. Identity Document update chain

Each Identity Document version should reference the previous version.

Example:

```text
Document 7 → Document 8 → Document 9
```

A new document should include:

- Relay Identifier;
- document version;
- previous document hash;
- updated keys;
- updated services;
- update time;
- authorising signature.

This creates a verifiable continuity chain.

---

## 25. Resolution of the current document

A resolver may encounter several Identity Document versions.

It must determine which valid document is current.

This may involve:

- highest authorised version;
- valid previous-document chain;
- latest transparency-log entry;
- controller-issued checkpoint;
- recovery override;
- migration-cutover record.

A higher version number alone is not sufficient if the update was not validly authorised.

---

## 26. Document sequence numbers

Identity Documents may use a monotonically increasing version number.

Example:

```text
version: 12
```

This helps detect stale documents.

However, version numbers must be protected by the signed document chain.

An attacker must not be able to publish:

```text
version: 9999
```

and override legitimate authority merely by using a larger number.

---

## 27. Document expiry

An Identity Document may include an expiration or revalidation time.

This can reduce the risk of stale documents remaining trusted indefinitely.

Example:

```json
{
  "validUntil": "2027-08-24T00:00:00Z"
}
```

However, expiry creates availability risks if the controller cannot publish an update.

Relay v0.1 may prefer non-expiring documents with revocation and update status, while allowing optional refresh guidance.

---

## 28. Resolution cache

Applications and resolvers may cache Identity Documents.

A cache should retain:

- Relay Identifier;
- document version;
- document hash;
- retrieval time;
- expiry or refresh time;
- verification status;
- source resolver.

Caching improves performance but creates stale-resolution risk.

---

## 29. Cache refresh

An application should refresh resolution when:

- the cache becomes stale;
- a request fails;
- migration is reported;
- a signature key changes;
- a high-authority action is about to occur;
- a security event is received;
- the Identity Document advertises a new version.

High-risk operations should not rely indefinitely on cached resolution.

---

## 30. Stale resolution

A stale resolver may return Provider A after the identity has moved to Provider B.

Provider A may assist by returning a signed migration notice.

The application should then:

1. verify the notice;
2. refresh the Identity Document;
3. verify the new provider;
4. update its cache;
5. resume through Provider B.

A redirect must not be followed blindly.

---

## 31. Signed migration notice

A former provider may return:

```json
{
  "status": "moved",
  "identity": "rid:relay:7fs82k9m4v",
  "newIdentityDocument": "sha256:identity-document-9...",
  "effectiveAt": "2026-08-24T16:00:00Z",
  "signature": "..."
}
```

The application must still verify the new Identity Document through an accepted authority path.

The former provider’s notice is useful evidence, not ultimate authority.

---

## 32. Resolver service

A **Resolver Service** accepts a Relay Identifier or handle and returns verifiable resolution information.

A resolver may be operated by:

- a Relay Provider;
- an independent company;
- a public-interest organisation;
- an application;
- the user;
- a distributed network.

Applications should be able to choose among compatible resolvers.

---

## 33. Resolver output verification

Applications should not need to trust the resolver blindly.

The resolver should return:

- signed Identity Document;
- verification chain;
- handle proof where applicable;
- update or checkpoint evidence;
- resolver observation metadata.

The application or SDK should verify the cryptographic evidence itself.

---

## 34. Resolver disagreement

Two resolvers may return different Identity Documents.

Possible reasons include:

- stale cache;
- network delay;
- malicious resolver;
- unresolved fork;
- recovery event;
- hidden provider equivocation.

The client should compare:

- document versions;
- document ancestry;
- signatures;
- checkpoints;
- transparency evidence;
- observation times.

A disagreement must not be silently resolved through arbitrary preference.

---

## 35. Resolution conflict state

If conflicting current documents cannot be reconciled, the identity may be marked:

```text
resolution-conflict
```

Applications may then:

- allow cautious read-only access;
- suspend high-authority operations;
- display a warning;
- request controller intervention;
- consult additional resolvers or witnesses.

---

## 36. Identity Document fork

An Identity Document fork occurs when two valid-looking documents reference the same prior document.

Example:

```text
              Document 9A
             /
Document 8
             \
              Document 9B
```

Possible causes include:

- simultaneous provider migration;
- compromised root key;
- recovery event;
- resolver equivocation;
- device conflict.

Identity Document forks are higher risk than ordinary repository forks because they may redirect the entire identity.

---

## 37. Identity fork resolution

Resolving an identity fork may require:

- root identity authority;
- recovery authority;
- controller quorum;
- trusted prior checkpoint;
- time-delayed recovery;
- external witness evidence.

The resolution should produce a new document that identifies:

- fork point;
- accepted branch;
- rejected branch;
- replacement keys;
- reason;
- effective time.

---

## 38. Recovery resolution

If the active provider disappears, the controller must be able to publish a replacement Identity Document.

A recovery update may:

- point to a new provider;
- revoke unavailable provider keys;
- replace repository keys;
- identify the last recoverable Repository Head;
- mark data loss where applicable;
- supersede the previous service locations.

The recovery authority must be defined before provider failure occurs.

---

## 39. Root authority

Relay may define a **Root Authority** for high-authority identity changes.

The root authority may be:

- a user-held key;
- a multi-device threshold;
- a recovery key;
- a trusted-contact quorum;
- an organisational approval policy.

The active provider should not be the sole root authority by default.

---

## 40. Root-key rotation

The identity must be able to rotate root authority without changing the Relay Identifier.

A root-key rotation should require:

- current root authority;
- or valid recovery authority;
- a signed Identity Document update;
- explicit revocation or retirement of the old key;
- optional transition period;
- witness or checkpoint publication where supported.

---

## 41. Compromised root authority

If root authority is compromised, recovery may require:

- previously configured recovery quorum;
- delay period;
- notification to active devices;
- challenge window;
- trusted checkpoint;
- provider-independent recovery publication.

The system should not allow an attacker with one compromised session to replace the identity’s full resolution state instantly.

---

## 42. Service descriptor

An Identity Document may contain one or more **Service Descriptors**.

Example:

```json
{
  "id": "repository-primary",
  "type": "RelayRepositoryService",
  "endpoint": "https://provider-b.example/repository/7fs82k9m4v",
  "protocolVersions": [
    "relay-0.1"
  ],
  "priority": 1
}
```

A descriptor may include:

- service type;
- endpoint;
- supported protocol versions;
- capabilities;
- priority;
- region;
- encryption requirements;
- status;
- expiration.

---

## 43. Service types

Relay v0.1 may recognise:

```text
identity
repository
authorization
events
blobs
migration
recovery
credentials
public-profile
```

Future versions may add more service types.

Applications should ignore unknown service descriptors while preserving them.

---

## 44. Multiple endpoints

A service may expose several endpoints.

Examples:

- primary and backup;
- geographic replicas;
- read and write endpoints;
- public and private endpoints;
- protocol-version-specific endpoints.

The descriptor must indicate:

- which endpoint is authoritative;
- which endpoints are read-only;
- failover rules;
- priority;
- health status where available.

---

## 45. Repository authority endpoint

The Identity Document must clearly identify which service may accept canonical repository writes.

A read-only mirror must not be mistaken for the canonical write provider.

Example:

```json
{
  "type": "RelayRepositoryService",
  "endpoint": "https://provider-b.example/repository/7fs82k9m4v",
  "authority": "canonical-write"
}
```

---

## 46. Service capability discovery

Applications may need to know whether a provider supports:

- private records;
- blobs above a certain size;
- event subscriptions;
- migration APIs;
- specific protocol versions;
- delegated application keys;
- particular schema operations.

The service endpoint may publish a signed capability document.

Capabilities must not override the Identity Document’s authority assignments.

---

## 47. Protocol version negotiation

An application and provider may support different Relay versions.

Resolution should expose supported versions.

Example:

```json
{
  "protocolVersions": [
    "relay-0.1",
    "relay-0.2"
  ]
}
```

The client selects a mutually supported version.

A provider must not silently reinterpret data using incompatible semantics.

---

## 48. Downgrade protection

An attacker may attempt to force use of an older, weaker protocol version.

The Identity Document or service descriptor should identify:

- minimum accepted version;
- deprecated versions;
- transition period;
- required security profile.

Clients should reject unsafe downgrades.

---

## 49. Service unavailability

Resolution may succeed even when a service is unavailable.

The result should distinguish:

```text
identity resolved
repository unavailable
authorization unavailable
provider migrating
service suspended
```

An unavailable service does not mean the identity does not exist.

Applications should display the correct condition.

---

## 50. Resolution failure classes

A resolver should distinguish:

### Unknown identity

No valid Identity Document can be found.

### Invalid identifier

The input does not follow a supported identifier format.

### Handle not found

No valid current handle binding exists.

### Handle disputed

Conflicting valid-looking bindings exist.

### Invalid document signature

The document cannot be authenticated.

### Stale document

A newer valid document is known.

### Resolution conflict

Competing valid-looking current documents exist.

### Service unavailable

The identity resolves, but a service cannot currently be reached.

### Identity deactivated

The identity is intentionally inactive.

### Identity terminated

The identity has been permanently retired.

### Resolution restricted

Legal, policy or privacy restrictions prevent a complete result.

---

## 51. Negative caching

Resolvers may cache failures such as:

```text
handle not found
```

Negative caching must use short lifetimes.

Otherwise, a newly created or recovered identity may remain falsely undiscoverable.

High-authority clients should retry through another resolver when appropriate.

---

## 52. Privacy-preserving resolution

Public resolution may reveal:

- current provider;
- service regions;
- identity activity;
- migration history;
- handle associations.

Some identities may require privacy.

Possible approaches include:

- public minimal Identity Document;
- restricted service details;
- privacy-preserving indirection;
- separate public and private service descriptors;
- encrypted endpoint disclosure to authorised applications;
- pseudonymous Relay Identities.

Relay v0.1 should expose only information required for public interoperability.

---

## 53. Pseudonymous identities

A Relay Identity does not need to reveal a legal name.

A pseudonymous identity may still have:

- stable Relay Identifier;
- verified pseudonymous handle;
- repository;
- relationships;
- reputation;
- application grants.

Resolution proves continuity of the pseudonymous identity, not the real-world identity behind it.

---

## 54. Legal identity verification

An identity may optionally hold credentials asserting legal identity.

These credentials are separate from resolution.

The resolver should not expose sensitive legal identity information merely because an application can resolve the Relay Identifier.

Applications requiring identity verification should request appropriate credential access.

---

## 55. Search and discovery services

A **Discovery Service** may allow users to search by:

- name;
- handle;
- organisation;
- topic;
- credential;
- public profile content.

Search results should include the Relay Identifier.

The search service may rank results, but ranking does not establish identity authority.

A user should be able to verify the selected result through resolution.

---

## 56. Discovery result

A discovery result may contain:

```json
{
  "relayIdentifier": "rid:relay:7fs82k9m4v",
  "displayName": "Miles",
  "preferredHandle": "miles.example.com",
  "profileRecord": "relay://rid:relay:7fs82k9m4v/com.relay.profile/main",
  "resolutionStatus": "verified"
}
```

Profile information may be stale or indexed.

The Relay Identifier is the durable reference used for resolution.

---

## 57. Impersonation resistance

Relay discovery interfaces should reduce impersonation through:

- visible Relay Identifier details;
- verified handle evidence;
- credential indicators;
- relationship context;
- profile provenance;
- warning for newly reassigned handles;
- warning for unresolved identity claims.

A familiar display name alone is not sufficient evidence.

---

## 58. Name similarity

Many people may share the same display name.

Relay does not require display-name uniqueness.

Applications should help users distinguish identities through:

- handles;
- avatars;
- verified domains;
- credentials;
- mutual relationships;
- Relay Identifier fingerprint;
- profile context.

---

## 59. Identifier fingerprint

Applications may show a short fingerprint derived from the Relay Identifier.

Example:

```text
Miles · Relay 7FS8-2K9M
```

This can help users distinguish identities where handles or names are similar.

The fingerprint is a display aid, not a separate identifier.

---

## 60. QR and direct-link resolution

A Relay Identity may be shared through:

- QR code;
- NFC;
- deep link;
- contact card;
- signed invitation.

These should contain the Relay Identifier and may also include:

- current handle;
- resolver hint;
- verification proof;
- intended action.

A resolver hint may improve performance but must not replace independent verification.

---

## 61. Resolver hints

A Relay URI may contain a non-authoritative resolver hint.

Example:

```text
relay:rid:relay:7fs82k9m4v?resolver=https://resolver.example
```

The client may try that resolver first.

It must still verify the returned Identity Document.

---

## 62. Offline identity presentation

A user may present a signed identity package offline.

This could include:

- Relay Identifier;
- current Identity Document;
- handle proof;
- expiration or freshness information;
- QR encoding;
- signature.

The receiving device may verify the package without immediate network access.

It should refresh online later before high-risk actions.

---

## 63. Resolution freshness

A resolution result should include freshness information.

Example:

```json
{
  "resolvedAt": "2026-08-24T16:05:00Z",
  "documentUpdatedAt": "2026-08-24T16:00:00Z",
  "refreshAfter": "2026-08-24T17:05:00Z"
}
```

Applications may use different refresh intervals based on risk.

---

## 64. High-risk resolution

Before performing actions such as:

- provider migration;
- repository export;
- private-data access;
- key management;
- payment;
- authority delegation;

the application should perform fresh resolution through trusted sources.

A cached profile result is not sufficient.

---

## 65. Resolution event notifications

Applications may subscribe to identity events such as:

```text
identity-document-updated
provider-changed
key-rotated
handle-added
handle-revoked
identity-recovered
identity-deactivated
```

Event notifications improve responsiveness.

They do not replace fresh resolution and verification.

---

## 66. Resolver security

A resolver should protect against:

- forged documents;
- cache poisoning;
- replay of old documents;
- downgrade attacks;
- malicious redirects;
- denial of service;
- inconsistent responses;
- privacy leakage;
- identifier enumeration abuse.

Resolvers should publish:

- supported methods;
- caching policy;
- audit policy;
- signing keys;
- incident contact;
- availability status.

---

## 67. Resolver authentication

A resolver may sign its response.

This proves which resolver provided the result.

However, the application should primarily verify the enclosed identity evidence.

Resolver signature is useful for:

- audit;
- dispute;
- detecting inconsistent resolver behaviour;
- service accountability.

---

## 68. Resolver transparency

An independent resolver may publish transparency information such as:

- observed Identity Document versions;
- update times;
- conflict reports;
- resolver software version;
- signed checkpoints.

This can help detect hidden inconsistencies.

Private identity details should not be exposed unnecessarily.

---

## 69. Resolution rate limits

Public resolution services may impose rate limits to prevent abuse.

Rate limiting must not make basic identity portability dependent on expensive proprietary access.

The ecosystem should permit:

- local resolvers;
- multiple public resolvers;
- provider-operated resolvers;
- cached verified documents;
- direct identity discovery.

---

## 70. Bulk resolution

Indexers and large applications may need bulk resolution.

Bulk resolution may support:

- multiple Relay Identifiers;
- document version checks;
- changed-since queries;
- batched key updates;
- migration detection.

Bulk interfaces must preserve the same verification guarantees as individual resolution.

---

## 71. Resolution and blocking

An application may resolve an identity even when the user has blocked it.

Resolution is distinct from interaction permission.

A block may prevent:

- display;
- event delivery;
- messages;
- relationship requests;
- repository access.

It does not erase the target Relay Identifier from existence.

---

## 72. Resolution and moderation

An application may refuse to display or interact with a resolved identity under its moderation policy.

It should distinguish:

```text
Identity is valid but blocked by this application.
```

from:

```text
Identity could not be cryptographically resolved.
```

Moderation status is not resolution status.

---

## 73. Resolution and provider suspension

A provider may suspend a repository while the Relay Identity remains valid.

Resolution may return:

```json
{
  "identityStatus": "active",
  "repositoryStatus": "provider-suspended"
}
```

Where permitted, the controller may migrate to another provider.

---

## 74. Identity deactivation

A deactivated identity may publish a final Identity Document state.

It may indicate:

- no active repository service;
- read-only archival service;
- no new application authorisations;
- optional reactivation authority.

External references to the Relay Identifier remain valid historical references.

---

## 75. Identity termination

A terminated identity should resolve to a signed terminal status.

Example:

```json
{
  "id": "rid:relay:7fs82k9m4v",
  "status": "terminated",
  "terminatedAt": "2028-01-01T00:00:00Z",
  "finalIdentityDocument": "sha256:...",
  "reasonVisibility": "private"
}
```

The Relay Identifier must never be reassigned.

---

## 76. Service migration status

During migration, the Identity Document or resolution result may expose:

```text
migrating
destination-ready
cutover-pending
moved
```

Applications should avoid initiating high-risk long-running operations during uncertain cutover states.

Read operations may continue according to migration policy.

---

## 77. Resolution during migration

During migration:

- the source remains authoritative until activation;
- the destination may be available in test mode;
- the Identity Document may include migration metadata;
- applications continue using the source for canonical writes;
- after activation, the new document points to the destination.

The resolver must not prematurely direct writes to the destination.

---

## 78. Service failover

A Relay Identity may define a read-only or emergency failover service.

The Identity Document must specify:

- service role;
- activation condition;
- whether the failover may accept writes;
- how activation is authorised;
- freshness of replicated state.

A backup endpoint must not become canonical automatically without valid authority.

---

## 79. Resolution without global consensus

Relay does not require every resolver worldwide to agree instantly.

It requires:

- signed Identity Documents;
- verifiable update chains;
- detectable conflicts;
- authority-based resolution;
- eventual propagation of valid updates.

Temporary stale results are possible.

Undetectable arbitrary reassignment should not be.

---

## 80. Resolver bootstrap

A new application needs a way to locate initial resolution services.

Possible bootstrap methods include:

- bundled trusted resolver list;
- DNS discovery;
- user-selected resolver;
- provider resolver;
- protocol registry;
- direct document location hint.

The application should allow resolver replacement where practical.

No single resolver should be permanently mandatory.

---

## 81. Core resolution registry

Relay may define a lightweight registry of resolver services.

The registry may list:

- resolver endpoint;
- operator;
- supported protocol versions;
- public keys;
- jurisdiction;
- status;
- policy.

The registry should not assign identities or decide which Identity Document is valid.

It is a directory of resolver services, not a central identity owner.

---

## 82. Self-resolution

A technically capable identity may publish and resolve its own Identity Document.

Self-hosting must use the same protocol rules as managed hosting.

A self-hosted identity should remain resolvable through compatible resolvers without needing approval from a commercial provider.

---

## 83. Resolution interoperability

A compliant resolver should be able to resolve identities hosted by any compatible Relay Provider.

A provider must not return usable results only to its own applications.

The output should use open, documented formats.

---

## 84. Resolution API operations

A compliant implementation should support operations equivalent to:

```text
Resolve Relay Identifier
Resolve handle
Verify handle binding
Read current Identity Document
Read Identity Document version
Verify Identity Document chain
Read service descriptors
Read protocol capabilities
Report migration status
Report identity status
Refresh cached resolution
Detect stale document
Detect Identity Document fork
Report resolution conflict
Resolve Record URI to current repository
Retrieve signed migration notice
```

The exact endpoint design will be defined later.

---

## 85. Resolution invariants

The following rules must always remain true.

### Invariant 1

A handle resolves to a Relay Identifier; it does not replace the Relay Identifier.

### Invariant 2

Changing a handle does not change the Relay Identifier.

### Invariant 3

Changing a provider does not change the Relay Identifier.

### Invariant 4

A service URL is not the permanent identity.

### Invariant 5

A released handle does not transfer historical identity continuity to its next holder.

### Invariant 6

The current provider must not be the only authority capable of publishing a replacement Identity Document.

### Invariant 7

A resolver response must be independently verifiable.

### Invariant 8

Search ranking does not determine identity authority.

### Invariant 9

A read-only mirror must not be presented as the canonical write provider.

### Invariant 10

A migration redirect must not be followed without verifying identity authority.

### Invariant 11

Conflicting current Identity Documents must produce a detectable resolution conflict.

### Invariant 12

A temporarily unavailable repository does not imply that the identity does not exist.

### Invariant 13

A valid Relay Identity may be pseudonymous.

### Invariant 14

Moderation or blocking decisions must not be represented as cryptographic resolution failure.

### Invariant 15

A terminated Relay Identifier must never be reassigned.

---

## 86. Compliance scenario

A basic Discovery and Resolution implementation should pass the following test.

### Initial identity

Alice has:

```text
Relay Identifier:
rid:relay:alice

Handle:
alice.example.com

Provider:
Provider A
```

Her domain and Identity Document both confirm the handle binding.

### Handle resolution

Application X receives:

```text
alice.example.com
```

It resolves the handle to:

```text
rid:relay:alice
```

It then retrieves and verifies Alice’s current Identity Document.

### Record resolution

Application X receives:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

It resolves Alice’s current repository service and retrieves the record.

### Provider migration

Alice migrates from Provider A to Provider B.

A new Identity Document:

- retains `rid:relay:alice`;
- references the previous document;
- points repository and authorisation services to Provider B;
- is signed by valid identity authority.

### Stale application cache

Application X still has Provider A cached.

Provider A returns a signed migration notice.

Application X refreshes Alice’s Identity Document, verifies Provider B and updates its cache.

### Handle change

Alice changes her preferred handle from:

```text
alice.example.com
```

to:

```text
alice.new-example.com
```

Her Relay Identifier remains unchanged.

Existing relationships and Record URIs continue to refer to `rid:relay:alice`.

### Handle reassignment

The old handle is later assigned to another identity.

Historical records and relationships remain linked to Alice’s Relay Identifier.

They do not transfer to the new holder.

### Provider failure

Provider B becomes unavailable.

Alice uses her independent recovery authority to publish a new Identity Document pointing to Provider C.

Resolvers verify the recovery chain and return Provider C as current.

If these events occur without creating a new identity or depending permanently on a former provider, the implementation satisfies the basic Relay Discovery and Resolution objective.

---

## 87. Open design questions

### 87.1 Relay Identifier method

Should Relay define a new identifier method or adopt an existing decentralised identifier format?

### 87.2 Authoritative document publication

Where is the current Identity Document published so that the active provider cannot block migration?

### 87.3 Resolver network

Should Relay use:

- independent replicated resolvers;
- a transparency log;
- domain-based resolution;
- an existing identifier network;
- or a hybrid?

### 87.4 Root authority custody

How should ordinary users retain provider-independent identity authority without being forced to manage raw cryptographic keys?

### 87.5 Handle format

Should Relay standardise:

- domain handles;
- `@user@domain` handles;
- both;
- or another form?

### 87.6 Handle expiration

How quickly should a released handle become available for reassignment?

### 87.7 Reassignment warnings

How long should applications warn that a handle has changed owners?

### 87.8 Resolver disagreement

What exact algorithm should clients use when resolvers return competing document chains?

### 87.9 Identity Document privacy

Which service details must be public, and which may be disclosed only to authorised applications?

### 87.10 Recovery publication

How does a controller publish a recovery Identity Document if:

- the provider is gone;
- the domain has expired;
- and normal devices are lost?

### 87.11 Transparency logs

Should high-authority Identity Document updates be published to independent transparency logs?

### 87.12 Offline resolution

What minimum evidence should an offline identity package contain, and how long may it be trusted?

---

## 88. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- every identity has one permanent, non-semantic Relay Identifier;
- handles are optional, human-readable and replaceable;
- domain-based handles are supported;
- provider-issued handles are allowed but treated as less portable;
- handle verification is bidirectional;
- the Identity Document is signed and versioned;
- each Identity Document references its predecessor;
- service locations are discovered through the current Identity Document;
- applications store Relay Identifiers rather than permanent provider URLs;
- resolvers return independently verifiable documents;
- several compatible resolver services may exist;
- the active provider is not the sole identity-update authority;
- migration notices are signed but not independently authoritative;
- conflicting Identity Documents create a visible resolution-conflict state;
- Record URIs are resolved by first resolving the identity’s current repository service;
- search and discovery remain separate from cryptographic resolution;
- the first implementation may use a hybrid of domain verification, signed document chains and replicated resolver nodes.

---

## 89. Core discovery principle

The Discovery and Resolution Model can be reduced to one rule:

> Relay resolves a permanent identity to its current services; it never mistakes the current name, server or application for the identity itself.

The next core object is the **Relay Schema and Interoperability Model**: how record types are defined, versioned, extended and preserved so that applications can understand shared records without one company controlling every possible form of digital expression.