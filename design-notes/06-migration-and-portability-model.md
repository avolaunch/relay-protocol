# Relay Protocol v0.1  
## Core Object 6: Migration and Portability Model

### 1. Definition

**Relay Migration** is the controlled transfer of operational responsibility for a Relay Identity, Relay Repository or related service from one compatible provider to another without breaking continuity.

A successful migration must preserve:

- the Relay Identifier;
- repository identity;
- Record URIs;
- valid repository history;
- active relationships;
- supported application access;
- public discoverability;
- control by the same authorised identity.

Migration is not merely downloading data.

It is the process through which a new provider becomes capable of serving and operating the same persistent digital identity.

---

## 2. Purpose

The Migration and Portability Model exists to make provider independence real.

Without migration, a provider may claim that the user owns their data while still remaining operationally indispensable.

Relay portability must allow a person to:

- leave a provider without creating a new identity;
- retain the same canonical records;
- preserve references from other identities;
- continue using compatible applications;
- prove that transferred records were not altered;
- recover from provider failure;
- move again in the future.

The primary test is:

> Can the user replace the current provider while remaining recognisably and technically the same Relay Identity?

---

## 3. Portability layers

Relay distinguishes between five forms of portability.

### 3.1 Data portability

The user can obtain a usable copy of their records and blobs.

### 3.2 Identity portability

The same Relay Identifier remains valid after the provider changes.

### 3.3 Operational portability

The new provider can accept authorised commits and serve the repository.

### 3.4 Relationship portability

Existing relationships continue to point to the same identities and records.

### 3.5 Application portability

Compatible applications can discover and interact with the new provider without requiring the user to rebuild their digital presence.

A system does not satisfy Relay portability merely by supporting data portability.

---

## 4. Migration actors

A migration may involve:

1. **Controller**
2. **Source Provider**
3. **Destination Provider**
4. **Identity Resolution Service**
5. **Authorised Applications**
6. **Repository Verifier**
7. **Blob Storage Provider**
8. **Recovery Authority**

Some of these roles may be performed by the same organisation, but they remain conceptually distinct.

---

## 5. Controller

The **Controller** is the authority that approves migration.

Migration is a high-authority operation.

Approval must not be inferred merely because an application has ordinary repository access.

The controller must explicitly authorise:

- the destination provider;
- the repositories or services being moved;
- the migration scope;
- the activation of the destination;
- the retirement of the source provider.

---

## 6. Source Provider

The **Source Provider** is the provider currently responsible for the Relay service being migrated.

Its responsibilities may include:

- producing a complete export;
- serving repository history;
- transferring blobs;
- providing final synchronisation;
- temporarily redirecting requests;
- stopping new canonical writes after cutover;
- retaining or deleting residual data according to policy.

The source provider must not be able to prevent lawful migration solely to retain the user.

---

## 7. Destination Provider

The **Destination Provider** is the provider preparing to assume operational responsibility.

Its responsibilities include:

- validating the Relay Identity;
- verifying migration authority;
- importing repository data;
- verifying commits and signatures;
- importing or locating blobs;
- preserving Record URIs;
- supporting required schemas;
- accepting final synchronisation;
- publishing readiness;
- beginning service only after valid activation.

---

## 8. Migration object

A migration should be represented by a signed **Migration Record** or equivalent authority object.

Example:

```json
{
  "id": "migration_01JXA4",
  "relayIdentity": "rid:relay:7fs82k9m4v",
  "repository": "repo:relay:7fs82k9m4v",
  "sourceProvider": "rid:provider:alpha",
  "destinationProvider": "rid:provider:beta",
  "scope": [
    "identity-services",
    "repository",
    "blobs",
    "application-grants"
  ],
  "requestedAt": "2026-08-24T10:00:00Z",
  "expiresAt": "2026-08-31T10:00:00Z",
  "authorisedBy": "rid:relay:7fs82k9m4v",
  "signature": "..."
}
```

The migration object should be specific enough to prevent a destination provider from claiming authority over services that were not approved for transfer.

---

## 9. Migration scope

A migration may cover all or part of the Relay environment.

Possible scopes include:

```text
Identity Document hosting
Public repository
Restricted repository
Private vault
Blob storage
Authorisation service
Event delivery
Application grant state
Search index participation
Recovery service
```

Relay v0.1 may initially support a full migration of identity resolution and one primary repository.

Partial service migration should remain possible in the architecture.

---

## 10. Migration states

A migration may move through the following states:

```text
requested
authorised
preparing
exporting
transferring
verifying
synchronising
ready
activating
completed
failed
cancelled
rolled-back
disputed
```

Each state should be attributable and time-stamped.

Applications and providers should not treat the destination as authoritative before activation.

---

## 11. Migration initiation

A migration begins when the controller selects or authorises a destination provider.

The initiation process should include:

- destination identity verification;
- destination capability check;
- migration scope review;
- storage and feature compatibility check;
- estimated transfer size;
- unsupported schema warning;
- private-data handling review;
- residual-data policy;
- application continuity options.

The destination must not receive broad access before the controller approves the migration request.

---

## 12. Destination capability declaration

Before migration, the destination provider should declare its capabilities.

Example:

```json
{
  "supportedProtocolVersions": [
    "relay-0.1"
  ],
  "supportedServices": [
    "identity",
    "repository",
    "blobs",
    "authorisation"
  ],
  "maximumBlobSize": 1073741824,
  "privateRecordSupport": "restricted-only",
  "unknownSchemaPreservation": true,
  "migrationRollbackSupport": true
}
```

The controller must be warned where the destination cannot fully preserve operational behaviour.

A destination may preserve unsupported records without being able to display or interpret them.

---

## 13. Compatibility check

Before transfer begins, the destination should evaluate:

- protocol version compatibility;
- repository size;
- commit-history support;
- blob media types;
- encryption requirements;
- schema preservation;
- private-record support;
- application grant compatibility;
- event-subscription support;
- recovery configuration.

A migration must not silently discard unsupported information.

The user should receive a clear result such as:

```text
Fully supported
Preserved but not displayed
Requires conversion
Cannot be migrated
Requires separate service
```

---

## 14. Migration authorisation

Migration requires stronger authorisation than ordinary content actions.

The protocol should require some combination of:

- fresh passkey authentication;
- identity signing key;
- recovery-authority confirmation;
- secondary device approval;
- time-delayed confirmation;
- provider-independent recovery code.

The exact requirement may depend on risk and repository sensitivity.

A normal application access token must not be sufficient.

---

## 15. Protection against forced migration

A provider, application or attacker must not be able to migrate an identity merely because it controls:

- an active session;
- an email account;
- a handle;
- a domain;
- a content-creation grant;
- the current hosting account.

Migration authority must derive from the Relay Identity’s defined control model.

---

## 16. Export package

The source provider must produce a provider-independent export package.

A complete export should contain:

```text
relay-export/
├── manifest.json
├── identity/
│   ├── current-document.json
│   └── document-history/
├── repository/
│   ├── metadata.json
│   ├── head.json
│   ├── commits/
│   ├── records/
│   └── tombstones/
├── blobs/
│   ├── manifest.json
│   └── objects/
├── schemas/
├── permissions/
├── relationships/
├── verification/
└── migration/
```

Some sections may contain references rather than embedded data where the migration model permits remote transfer.

---

## 17. Export manifest

The export manifest should declare:

- export format version;
- Relay Identifier;
- Repository Identifier;
- source provider;
- export creation time;
- included services;
- excluded services;
- current Repository Head;
- number of records;
- number and total size of blobs;
- encryption state;
- included grant state;
- integrity root;
- completeness declaration.

Example:

```json
{
  "format": "relay-export-0.1",
  "identity": "rid:relay:7fs82k9m4v",
  "repository": "repo:relay:7fs82k9m4v",
  "sourceProvider": "rid:provider:alpha",
  "createdAt": "2026-08-24T11:00:00Z",
  "repositoryHead": "sha256:4be1...",
  "records": 1842,
  "blobs": 613,
  "blobBytes": 42949672960,
  "completeness": "complete",
  "integrityRoot": "sha256:91ad..."
}
```

---

## 18. Export completeness

An export must identify whether it is:

```text
complete
partial
public-only
collection-limited
date-limited
metadata-only
recovery export
```

A partial export must not be used to claim that full migration has occurred.

The destination should reject a migration marked complete when required repository components are missing.

---

## 19. Export while repository remains active

A repository may continue receiving writes while the initial export is produced.

In that case, the export represents a specific Repository Head.

Example:

```text
Initial export head:
sha256:4be1...
```

Any commits created after that head must be transferred during final synchronisation.

The source must retain an ordered migration delta.

---

## 20. Migration snapshot

The initial export creates a **Migration Snapshot**.

The snapshot contains the complete repository state as of a defined commit.

The snapshot must be:

- internally consistent;
- verifiable;
- linked to a Repository Head;
- reproducible from the included commit history where required.

The destination imports the snapshot before final synchronisation.

---

## 21. Incremental transfer

Large repositories should support incremental migration.

The destination may receive:

1. repository metadata;
2. commit history;
3. current records;
4. smaller blobs;
5. large blobs;
6. later commits;
7. final cutover delta.

Incremental transfer must preserve integrity and ordering.

The destination must not serve incomplete data as though migration were finished.

---

## 22. Blob migration

Blobs may be migrated through:

- direct provider-to-provider transfer;
- controller download and upload;
- temporary signed transfer URLs;
- shared content-addressed storage;
- deferred background transfer;
- verified remote references.

Every transferred blob must be checked against its content hash.

A matching filename or file size is not sufficient.

---

## 23. Deferred blob transfer

For very large repositories, a destination may activate before every non-essential blob is locally copied, provided:

- repository records remain valid;
- unavailable blobs are clearly identified;
- the source continues serving them temporarily;
- each blob has a verified transfer plan;
- the user is informed;
- the migration cannot silently remain incomplete indefinitely.

The protocol should define which assets are required before activation.

---

## 24. Blob reference continuity

A blob’s permanent identity must not depend on its current storage URL.

If a blob is identified as:

```text
blob:sha256:84b3...
```

the destination may serve it from a new URL without changing records that reference it.

Temporary source URLs should not become permanent canonical identifiers.

---

## 25. Repository verification

The destination must verify:

- Relay Identifier consistency;
- Repository Identifier consistency;
- Identity Document chain;
- commit signatures;
- commit ordering;
- Repository Head;
- record hashes;
- record schemas;
- tombstones;
- blob hashes;
- export integrity root;
- migration authority.

A destination must not activate a repository it cannot verify.

---

## 26. Verification report

The destination should produce a signed verification report.

Example:

```json
{
  "migration": "migration_01JXA4",
  "repository": "repo:relay:7fs82k9m4v",
  "verifiedHead": "sha256:4be1...",
  "recordsVerified": 1842,
  "blobsVerified": 613,
  "unknownSchemasPreserved": 7,
  "errors": [],
  "status": "verified",
  "verifiedAt": "2026-08-24T15:00:00Z",
  "destinationSignature": "..."
}
```

The controller should be able to inspect a human-readable summary before activation.

---

## 27. Verification failure

A migration must pause or fail when verification detects:

- missing commits;
- invalid signatures;
- mismatched repository identifiers;
- altered records;
- missing tombstones;
- blob hash mismatches;
- incomplete export represented as complete;
- unsupported encryption;
- conflicting repository histories.

The destination must not silently repair or omit invalid data without explicit approval and a recorded remediation process.

---

## 28. Final synchronisation

Before cutover, the destination must receive all valid commits created after the Migration Snapshot.

The source should then enter a controlled state such as:

```text
migration-freeze
```

or:

```text
read-only
```

The final delta is transferred and verified.

The source and destination must agree on the same final Repository Head before activation.

---

## 29. Write freeze

A short write freeze may be required during final cutover.

During the freeze:

- applications may read;
- new writes may be queued or temporarily rejected;
- users must be informed;
- the duration should be minimised.

Queued writes must not be accepted by both providers independently.

---

## 30. Zero-downtime migration

More advanced implementations may support zero-downtime migration.

Possible methods include:

- dual-delivery of commits;
- source-forwarded writes;
- destination shadow replication;
- short-lived write-routing authority;
- consensus over a temporary migration coordinator.

Relay v0.1 should not require zero downtime.

A brief controlled write freeze is acceptable for the first reference implementation.

---

## 31. Activation

Activation is the high-authority step that makes the destination provider operationally authoritative.

Activation should require:

- verified import;
- final Repository Head agreement;
- destination readiness;
- controller approval;
- updated Identity Document;
- updated service locations;
- destination acknowledgement.

The activation event should be signed and historically traceable.

---

## 32. Identity Document update

The Identity Document must be updated to point to the destination provider.

Example:

```json
{
  "services": {
    "repository": "https://provider-b.example/repository/7fs82k9m4v",
    "authorization": "https://provider-b.example/authorize",
    "events": "https://provider-b.example/events"
  },
  "previousDocumentHash": "sha256:old-document...",
  "migration": "migration_01JXA4",
  "signature": "..."
}
```

The Relay Identifier remains unchanged.

---

## 33. Resolution update

After activation, identity resolution must return the new service locations.

Applications should discover the new provider through identity resolution rather than permanently storing the former repository URL.

Temporary caches may continue to hold old service locations, so transitional redirection may be required.

---

## 34. Source-provider redirect

After migration, the source provider may expose a signed migration response such as:

```json
{
  "status": "moved",
  "identity": "rid:relay:7fs82k9m4v",
  "destination": "https://provider-b.example/repository/7fs82k9m4v",
  "effectiveAt": "2026-08-24T16:00:00Z",
  "identityDocument": "sha256:new-document...",
  "signature": "..."
}
```

A redirect is a transition aid.

It must not become the permanent foundation of identity continuity.

---

## 35. Application discovery after migration

Applications should resolve the Relay Identity before beginning or renewing access.

After migration, an application should:

1. detect the provider change;
2. verify the new Identity Document;
3. locate the new authorisation service;
4. validate whether its Permission Grant remains active;
5. obtain a destination-issued token;
6. resume access.

The user should not need to manually reconnect every compatible application where safe continuity is possible.

---

## 36. Permission Grant continuity

Permission Grants should be conceptually provider-independent where possible.

A grant should be issued by the Relay Identity, not owned solely by the source provider.

However, provider-specific access tokens must not simply be copied to the destination.

The destination should verify the continuing grant and issue new credentials.

---

## 37. Grants requiring re-authorisation

Some grants may require renewed approval after migration.

Examples include:

- access to private encrypted records;
- provider-specific services;
- high-authority permissions;
- applications unsupported by the destination;
- grants tied to a source-provider key;
- grants affected by changed security policy.

The migration interface must identify these before cutover where possible.

---

## 38. Application token invalidation

Once activation is complete:

- source-provider access tokens should stop authorising new actions;
- source refresh tokens should be invalidated;
- delegated keys should be revalidated or replaced;
- new tokens should be issued only by the destination.

A temporary transition period may be permitted for read-only access, but not for competing canonical writes.

---

## 39. Event subscription continuity

Applications subscribed to repository events must be informed of the provider change.

Possible mechanisms include:

- signed migration event;
- final source-provider event;
- identity-resolution refresh;
- destination subscription renewal;
- event cursor handover.

The destination should avoid replaying all historical events as though they were new.

---

## 40. Event cursor migration

Where supported, the migration may preserve an event cursor or final source event marker.

Example:

```json
{
  "sourceFinalCursor": "cursor_882199",
  "destinationStartingHead": "sha256:final-head..."
}
```

Applications can then resume from the correct repository state.

---

## 41. Relationship continuity

Relationships should survive migration automatically because they reference stable Relay Identifiers and Record URIs.

For example:

```text
Alice follows:
rid:relay:bob
```

Bob’s provider may change.

The target remains the same identity.

No new follow record is required.

---

## 42. Record-reference continuity

External records may refer to:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

That URI must continue resolving after Alice changes providers.

The referring record must not be updated merely because the physical hosting location changed.

---

## 43. Handle continuity

A handle may remain unchanged during migration.

If the handle is controlled independently through a domain or separate naming service, only its resolution target may need updating.

A provider-based handle such as:

```text
alice.provider-a.example
```

may not remain usable after migration unless the source supports continued redirection.

The Relay Identifier remains the authoritative continuity anchor.

---

## 44. Provider-specific handles

Users should be warned that provider-specific handles are less portable than independently controlled handles.

The destination may assign a new display handle while preserving:

- Relay Identifier;
- verified external handles;
- historical handle metadata;
- repository continuity.

Applications must not mistake a changed visible handle for a changed identity.

---

## 45. Migration without source cooperation

A critical portability system must consider source-provider failure or refusal.

Possible cases include:

- provider closure;
- provider insolvency;
- service outage;
- malicious lockout;
- lost infrastructure;
- provider refusal to export;
- legal restriction.

Relay should support migration using the most recent independently held export or replica where possible.

---

## 46. User-held recovery export

Users should be able to maintain a periodically updated recovery export.

A recovery export may be stored:

- on the user’s device;
- in cloud storage chosen by the user;
- with a backup provider;
- through encrypted distributed storage;
- with trusted custodians.

The export must be encrypted where it contains restricted or private information.

---

## 47. Backup provider

A user may authorise an independent backup provider to maintain a continuously updated replica.

The backup provider may receive:

- repository commits;
- encrypted blobs;
- identity document history;
- migration metadata.

It should not automatically have authority to serve as the active provider.

Activation still requires controller or recovery authority.

---

## 48. Emergency migration

An emergency migration occurs when the source provider cannot participate normally.

The controller or recovery authority may:

1. present a recent verified repository copy;
2. prove authority over the Relay Identity;
3. select a destination provider;
4. restore the repository;
5. publish a new Identity Document;
6. mark the previous provider location as unavailable or obsolete.

Emergency migration may lose commits that were never replicated or exported.

The system must state the last verified Repository Head restored.

---

## 49. Data-loss disclosure

Where emergency migration restores an older repository state, the destination must disclose:

- last verified commit;
- last verified timestamp;
- known missing period;
- unavailable blobs;
- unresolved event gaps.

The destination must not imply complete continuity where data may have been lost.

---

## 50. Provider disappearance

Identity resolution must not depend permanently on a provider that may disappear.

The protocol therefore needs an authority path through which a valid controller can publish a replacement Identity Document.

Possible mechanisms include:

- controller-owned domain;
- decentralised identifier resolution;
- independent identity registry;
- replicated signed document log;
- recovery-authority publication.

The precise mechanism remains an open design decision.

---

## 51. Split-brain migration

A split-brain condition occurs when both source and destination believe they are authoritative and accept writes.

This may produce conflicting repository histories.

The protocol must:

- detect differing heads;
- stop automatic write acceptance where possible;
- identify the last common commit;
- require explicit controller resolution;
- preserve evidence of both branches.

Silent last-write-wins resolution is not acceptable.

---

## 52. Migration fork

A migration fork may look like:

```text
Commit A
├── Source Commit B
└── Destination Commit C
```

Both B and C reference A.

Neither may automatically be discarded merely because one provider claims authority.

Resolution must determine:

- which provider had valid write authority;
- whether one branch was created after activation;
- whether a compromise occurred;
- whether records can be reconciled.

---

## 53. Canonical branch resolution

The controller may issue a signed resolution identifying:

- the selected canonical branch;
- invalidated commits;
- reconciled records;
- effective Repository Head;
- reason;
- recovery or security actions taken.

Where both branches contain valid user actions, a new reconciled commit may be created.

---

## 54. Rollback

A migration may be rolled back before final completion.

Rollback may occur because of:

- failed verification;
- destination outage;
- unsupported data;
- controller cancellation;
- security concern;
- incomplete blob transfer.

Before activation, rollback should normally return full authority to the source.

After activation, returning to the source is technically another migration unless a defined cutover rollback window remains active.

---

## 55. Cutover rollback window

A destination may support a limited rollback window.

During this period:

- the source retains a read-only replica;
- the destination is authoritative;
- new commits are tracked;
- rollback requires transferring destination commits back to the source;
- the Identity Document must be updated again.

The rollback mechanism must not allow both providers to accept authoritative writes concurrently.

---

## 56. Migration cancellation

The controller may cancel migration before activation.

Cancellation should:

- revoke destination transfer authority;
- delete or quarantine imported private data according to policy;
- preserve migration audit records;
- return the source repository to normal operation;
- invalidate temporary migration tokens.

The destination must not retain operational access after cancellation.

---

## 57. Destination failure after activation

If the destination fails shortly after activation, recovery may use:

- rollback to source;
- emergency migration to another provider;
- backup-provider activation;
- user-held export restoration.

The source must not automatically reclaim authority without controller or recovery approval.

---

## 58. Residual source data

After migration, the source provider may retain data because of:

- rollback policy;
- user-selected backup;
- legal retention;
- billing dispute;
- security investigation;
- technical deletion delay.

The user must be informed of:

- what remains;
- why it remains;
- how long it remains;
- whether it remains accessible;
- whether it is encrypted;
- when deletion is expected.

---

## 59. Source-data deletion

Where permitted and requested, the source should delete residual operational copies after:

- migration completion;
- rollback window expiry;
- verification by the controller;
- fulfilment of legal obligations.

Deletion of source copies must not delete the destination repository.

The source may retain minimal migration and audit metadata where necessary.

---

## 60. Migration receipt

The controller should receive a **Migration Receipt**.

The receipt should include:

- migration identifier;
- source and destination providers;
- scope;
- initial snapshot head;
- final migrated head;
- activation time;
- verification result;
- unsupported items;
- grants continued;
- grants requiring re-authorisation;
- residual source-data policy;
- destination signature;
- controller approval.

The receipt provides evidence of what was moved and when authority changed.

---

## 61. Migration audit trail

The protocol should preserve events for:

```text
migration requested
migration authorised
export produced
destination verified
write freeze started
final head agreed
identity document updated
destination activated
source deactivated
migration completed
residual deletion confirmed
```

Sensitive operational details may remain private.

The existence and outcome of migration should remain verifiable.

---

## 62. Migration and private encryption

Private encrypted records create additional requirements.

The migration must ensure that:

- the destination can serve authorised ciphertext;
- user-controlled keys remain available;
- source-provider-only keys are not required;
- key wrapping is updated where necessary;
- destination staff do not gain unintended plaintext access;
- revoked source-provider keys cannot decrypt future content.

A repository is not meaningfully portable if only the former provider can decrypt it.

---

## 63. Re-encryption

Some migration models may require re-encryption.

Examples include:

- replacing a source-provider storage key;
- changing destination key-management systems;
- removing a compromised provider;
- updating recipient key sets.

Re-encryption must not change the logical Record URI.

It may change:

- ciphertext;
- storage representation;
- encryption metadata;
- blob storage hash where the hash applies to ciphertext.

The protocol must define whether content identifiers refer to plaintext or encrypted representation.

---

## 64. Migration and schema preservation

The destination must preserve unknown but valid schemas.

It may classify them as:

```text
supported
read-only
preserved
unsupported
invalid
```

Unsupported records must not be discarded merely because the destination lacks an interface for them.

The user should be able to migrate again later with those records intact.

---

## 65. Schema conversion

A destination may offer schema conversion.

Conversion must be:

- optional;
- attributable;
- reversible where possible;
- provenance-preserving;
- separately approved when information may be lost.

The original record should normally remain preserved unless the controller explicitly approves replacement.

---

## 66. Migration and moderation

A destination provider may enforce different hosting policies.

Before migration, it may reject or restrict records that violate its policies.

The provider must disclose:

- which records are affected;
- whether they will be preserved but not served;
- whether they must be removed;
- whether migration can proceed partially;
- whether another provider may be more suitable.

Relay portability does not require every provider to host every lawful or unlawful record.

It requires that provider policy does not silently become identity ownership.

---

## 67. Legal restrictions

A migration may be limited by:

- court orders;
- sanctions;
- regulated records;
- data-localisation law;
- contractual obligations;
- evidence preservation;
- child-safety requirements.

The provider should distinguish between:

- inability to transfer certain records;
- inability to transfer the entire repository;
- temporary legal hold;
- permanent prohibition.

The protocol cannot override applicable law.

---

## 68. Cross-border migration

A destination in another jurisdiction may create different:

- privacy protections;
- government-access risks;
- data-transfer obligations;
- retention requirements;
- consumer remedies.

The migration interface should disclose jurisdictional changes where known.

This is especially important for private repositories and organisational identities.

---

## 69. Service unbundling

A future Relay Identity may use different providers for:

```text
Identity resolution
Public repository
Private vault
Blob storage
Authorisation
Recovery
```

Migration should therefore be service-specific.

A user may move blob storage without moving identity resolution.

A user may move the public repository while retaining a separate recovery provider.

Relay v0.1 may implement bundled migration while preserving this separation in the data model.

---

## 70. Partial migration

A partial migration moves selected services or collections.

Examples:

```text
Move public posts but retain private vault
Move blob storage only
Move one application-specific collection
Move identity resolution but not repository hosting
```

Partial migration must not create ambiguous authority.

Each service must have one clearly discoverable current authority unless the protocol explicitly supports replication.

---

## 71. Collection migration

A collection may be moved to another provider only if the identity and repository model supports distributed repositories.

Because Relay v0.1 assumes one canonical primary repository, collection-level operational migration may be deferred.

Collection-level export and backup may still be supported.

---

## 72. Replication versus migration

**Replication** creates an additional copy.

**Migration** changes operational authority.

A replica may be:

- backup;
- cache;
- read-only mirror;
- disaster-recovery copy;
- search index.

A replica does not become canonical merely because it has a complete copy.

The protocol must clearly identify:

- canonical provider;
- replica provider;
- replica freshness;
- whether the replica may be activated.

---

## 73. Mirror service

A user may authorise a public read-only mirror.

The mirror may improve:

- availability;
- geographic performance;
- resilience;
- censorship resistance.

The mirror must preserve:

- canonical Record URIs;
- source Repository Identifier;
- observed Repository Head;
- freshness information.

It must not accept canonical writes.

---

## 74. Migration performance

The protocol should support:

- resumable transfers;
- chunked blobs;
- deduplication;
- parallel verification;
- compression;
- incremental commits;
- transfer checkpoints.

A failed network connection should not require restarting a multi-terabyte migration.

---

## 75. Transfer checkpoint

A destination may record verified checkpoints such as:

```json
{
  "migration": "migration_01JXA4",
  "lastVerifiedCommit": "sha256:3bb7...",
  "verifiedBlobs": 482,
  "remainingBlobs": 131,
  "updatedAt": "2026-08-24T13:30:00Z"
}
```

Checkpoints must not be mistaken for completed migration.

---

## 76. User experience requirements

Migration must be understandable to ordinary users.

The user should be shown:

- what is moving;
- what is not moving;
- whether service will be interrupted;
- whether applications will remain connected;
- whether private data is supported;
- whether any records are incompatible;
- what the source provider will retain;
- when the destination becomes active.

The user should not need to understand commit hashes to migrate safely.

---

## 77. Provider comparison

A migration interface may compare destination providers by:

- supported Relay version;
- storage;
- price;
- jurisdiction;
- recovery options;
- private-vault support;
- portability guarantees;
- backup support;
- content policies;
- application compatibility.

This comparison layer is not part of the core protocol, but it may improve practical provider competition.

---

## 78. Migration test mode

A destination may offer a non-authoritative test import.

This allows the user to inspect:

- record rendering;
- unsupported schemas;
- media availability;
- application compatibility;
- storage usage.

A test import must not:

- publish records;
- accept canonical writes;
- change identity resolution;
- appear as the active provider.

---

## 79. Provider exit plan

Every compliant provider should publish an exit plan explaining:

- standard export availability;
- migration API availability;
- backup options;
- notice period before closure;
- handling of unpaid accounts;
- residual-data deletion;
- emergency access procedure.

Provider insolvency must not be the first time users discover whether their repository is portable.

---

## 80. Provider shutdown

A provider planning shutdown should:

1. notify users;
2. stop accepting long-term commitments;
3. provide migration tools;
4. permit bulk transfer;
5. publish signed shutdown status;
6. maintain resolution or redirection for a transition period;
7. support recovery exports;
8. delete residual data according to policy.

The protocol should permit ecosystem services to assist affected users.

---

## 81. Forced provider removal

A provider may be removed from an ecosystem directory because of:

- fraud;
- security failure;
- false portability claims;
- repeated data loss;
- protocol non-compliance.

Removal from a directory does not terminate identities hosted there.

Users must still be able to migrate where technically and legally possible.

---

## 82. Portability certification

A provider may be tested for compliance through scenarios such as:

- complete export;
- independent verification;
- migration to another implementation;
- preservation of unknown schemas;
- Record URI continuity;
- application reconnection;
- source-token invalidation;
- emergency restore.

Certification should verify behaviour, not merely policy documents.

---

## 83. Required v0.1 migration operations

A compliant implementation must support:

```text
Request migration
Describe migration scope
Verify destination provider
Authorise migration
Create complete export
Create Migration Snapshot
Transfer repository
Transfer blobs
Resume interrupted transfer
Verify repository history
Verify blob integrity
Produce verification report
Transfer incremental commits
Enter write freeze
Perform final synchronisation
Confirm final Repository Head
Update Identity Document
Activate destination provider
Deactivate source-provider writes
Redirect source requests
Reissue application credentials
Complete migration
Cancel migration before activation
Produce Migration Receipt
Export recovery copy
Restore from recovery copy
Detect migration fork
Initiate explicit fork resolution
```

Advanced partial-service migration may remain outside the first reference implementation.

---

## 84. Migration invariants

The following rules must always remain true.

### Invariant 1

Migration does not change the Relay Identifier.

### Invariant 2

Migration does not change the Repository Identifier.

### Invariant 3

Migration does not change existing Record URIs.

### Invariant 4

The destination cannot become authoritative without valid controller approval.

### Invariant 5

The destination must verify repository integrity before activation.

### Invariant 6

A data download alone is not proof of completed migration.

### Invariant 7

Only one provider may accept canonical writes after cutover unless an explicit multi-provider protocol is used.

### Invariant 8

Provider-specific access tokens must not be treated as portable identity authority.

### Invariant 9

Unknown valid schemas must survive migration.

### Invariant 10

A migration must disclose missing, unsupported or unverified data.

### Invariant 11

Source-provider suspension does not automatically terminate the Relay Identity.

### Invariant 12

A source provider must not retain permanent control through provider-only encryption keys.

### Invariant 13

A rollback must not create two competing canonical repositories.

### Invariant 14

Relationships continue to reference stable identities rather than provider locations.

### Invariant 15

A migration failure must leave a clearly identified authoritative repository state.

---

## 85. Compliance scenario

A basic migration implementation should pass the following test.

### Initial state

Alice has:

```text
Relay Identity:
rid:relay:alice

Repository:
repo:relay:alice

Current Provider:
Provider A

Current Repository Head:
sha256:head-100
```

Alice has:

- profile records;
- public posts;
- restricted drafts;
- media blobs;
- follow relationships;
- active application grants.

### Migration request

Alice selects Provider B.

Provider B declares support for:

- Relay v0.1;
- public and restricted records;
- all existing schemas;
- content-addressed blobs;
- permission-grant continuity.

Alice authorises the migration using fresh high-authority authentication.

### Initial transfer

Provider A produces a complete export at:

```text
sha256:head-100
```

Provider B imports and verifies it.

### Continued activity

While transfer occurs, Alice creates two more posts.

Provider A reaches:

```text
sha256:head-102
```

### Final synchronisation

Provider A enters a short write freeze.

Commits 101 and 102 are transferred.

Both providers confirm:

```text
Final Repository Head:
sha256:head-102
```

### Activation

Alice approves activation.

Her Identity Document is updated to point to Provider B.

Provider B begins accepting writes.

Provider A stops accepting canonical writes and publishes a signed migration redirect.

### Application continuity

Application X resolves Alice’s identity, discovers Provider B, verifies its existing grant and receives a new Provider B token.

Alice’s profile, posts and relationships remain available.

### Record continuity

An external reply still points to:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

The Record URI resolves through Provider B without modification.

### Source cleanup

After the rollback period, Provider A deletes residual repository content according to policy and issues confirmation.

If these steps occur without changing Alice’s identity, record identifiers, relationships or canonical history, the implementation satisfies the basic Relay Migration objective.

---

## 86. Emergency migration compliance scenario

### Failure state

Provider A becomes unavailable without completing migration.

Alice possesses a recovery export whose last verified Repository Head is:

```text
sha256:head-98
```

The last known active provider head was believed to be:

```text
sha256:head-100
```

### Recovery

Alice proves control of the Relay Identity through recovery authority.

Provider B verifies the recovery export and restores:

```text
sha256:head-98
```

Alice publishes a new Identity Document pointing to Provider B.

### Disclosure

Provider B reports:

```text
Restored through head-98.
Commits 99 and 100 could not be recovered.
```

Alice retains the same Relay Identifier.

Applications reconnect to Provider B.

This satisfies emergency identity continuity, while accurately acknowledging incomplete record continuity.

---

## 87. Open design questions

### 87.1 Identity resolution

What mechanism allows a controller to publish a new Identity Document when the current provider has disappeared?

### 87.2 Migration authority

What exact combination of keys, devices or recovery authorities should be required for migration?

### 87.3 Grant portability

Should Permission Grants be signed portable records, or should each destination require re-authorisation?

### 87.4 Application transition

How long should source-provider redirects and read-only token support remain active?

### 87.5 Private encryption

How should encryption keys be transferred or rewrapped without exposing private content?

### 87.6 Blob activation threshold

Must every blob be transferred before cutover, or may non-essential blobs remain temporarily remote?

### 87.7 Zero-downtime writes

Should the protocol eventually define temporary dual-provider coordination?

### 87.8 Recovery replicas

Should compliant providers be required to support an independent backup or user-held recovery export?

### 87.9 Fork resolution

What evidence determines which branch had valid authority during split-brain migration?

### 87.10 Legal portability limits

How should providers represent records that cannot legally move to a selected jurisdiction?

### 87.11 Partial-service migration

When should Relay support independent providers for identity, repository, vault and blobs?

### 87.12 Migration pricing

Should providers be permitted to charge reasonable transfer costs, and how should anti-lock-in rules be expressed?

---

## 88. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- one primary active Relay Provider at a time;
- migration is approved through a high-authority controller action;
- the source produces a complete provider-independent export;
- the destination verifies the repository before activation;
- the initial transfer is followed by incremental synchronisation;
- a short write freeze is acceptable;
- the Identity Document update performs the authoritative cutover;
- stable Relay Identifiers, Repository Identifiers and Record URIs are preserved;
- provider-specific tokens are replaced after migration;
- compatible Permission Grants may continue;
- unknown schemas must be preserved;
- blobs are verified by content hash;
- the source may provide temporary signed redirects;
- the source ceases canonical writes after activation;
- the user receives a Migration Receipt;
- emergency restoration from a verified export is supported;
- loss of unreplicated recent commits must be disclosed;
- advanced zero-downtime and partial-service migration may be deferred.

---

## 89. Core migration principle

The Migration and Portability Model can be reduced to one rule:

> A Relay Provider may operate a person’s digital continuity, but it must remain technically replaceable without requiring the person to become someone new.

The next core object is the **Relay Commit and Verification Model**: how repository changes are signed, ordered and independently verified without requiring a blockchain or global consensus.