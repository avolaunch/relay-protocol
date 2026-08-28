# Relay Protocol v0.1  
## Core Object 7: Commit and Verification Model

### 1. Definition

A **Relay Commit** is a signed, ordered and verifiable statement that one or more changes have been accepted into a Relay Repository.

A commit may contain operations such as:

- creating a record;
- updating a record;
- deleting a record;
- restoring a record;
- attaching or detaching a blob;
- changing record visibility;
- changing repository metadata;
- resolving a conflict.

The Commit and Verification Model allows an independent party to determine:

- whether a repository change was authorised;
- whether records have been altered;
- which repository state is current;
- whether migration preserved repository history;
- whether two copies of a repository are consistent;
- whether conflicting histories exist.

Relay uses cryptographic verification without requiring:

- a blockchain;
- cryptocurrency;
- proof of work;
- proof of stake;
- global transaction consensus;
- one central verification authority.

---

## 2. Purpose

The Commit and Verification Model exists to establish **repository integrity and continuity**.

Without it, a provider could:

- alter records during storage;
- omit records during migration;
- rewrite historical timestamps;
- fabricate application actions;
- serve different repository histories to different observers;
- claim that an incomplete export is complete.

The model does not attempt to prove that the factual content of every record is true.

It proves that:

> A particular repository authority accepted a particular change, in a particular order, producing a particular repository state.

---

## 3. What verification proves

Relay verification may establish that:

- a commit belongs to the stated repository;
- a commit was signed by valid authority;
- a commit follows a particular previous commit;
- the listed operations match their hashes;
- a record version was included in a valid commit;
- a blob matches its declared content identifier;
- a repository export matches a declared Repository Head;
- a migrated repository matches its source state;
- an Identity Document was valid when a commit was created.

Verification does not automatically establish that:

- a statement inside a record is factually correct;
- the human controller personally created the content;
- the controller understood an application’s behaviour;
- a provider complied with every privacy promise;
- a public timestamp proves the event occurred at an exact real-world moment;
- a record was created without AI assistance;
- a credential issuer is trustworthy.

These require additional evidence or trust systems.

---

## 4. Core components

The Commit and Verification Model contains:

1. **Operation**
2. **Commit**
3. **Commit Identifier**
4. **Previous Commit Reference**
5. **Repository Head**
6. **Content Hash**
7. **Commit Signature**
8. **Authorising Key**
9. **Authenticated Repository Structure**
10. **Verification Proof**
11. **Checkpoint**
12. **Witness**
13. **Fork**
14. **Resolution Commit**

---

## 5. Operation

An **Operation** describes one requested repository change.

Relay v0.1 should support at least:

```text
create
update
delete
restore
attach-blob
detach-blob
change-visibility
change-audience
change-rights
supersede
resolve-conflict
```

An operation must identify:

- operation type;
- target record or collection;
- expected current state where applicable;
- resulting content or content hash;
- submitting application or authority;
- relevant Permission Grant;
- operation-specific conditions.

Example:

```json
{
  "operation": "update",
  "record": "relay://rid:relay:alice/com.relay.post/post_123",
  "expectedVersion": 3,
  "newContentHash": "sha256:98c2...",
  "submittedBy": "rid:app:writing-client",
  "permissionGrant": "grant_01JX8K"
}
```

---

## 6. Operation validation

Before an operation is accepted into a commit, the repository must validate:

### 6.1 Structural validity

The operation follows the required protocol format.

### 6.2 Schema validity

The resulting record satisfies its declared schema.

### 6.3 Authority validity

The submitter has permission to perform the operation.

### 6.4 State validity

The operation is compatible with the current repository state.

For example:

- the expected version is current;
- the Record Key is not already used;
- the target record exists;
- a deleted Record Key is not being reused;
- singleton constraints are respected.

### 6.5 Policy validity

The operation does not violate applicable repository or provider policy.

Policy rejection must remain distinguishable from protocol-invalid authority.

---

## 7. Commit

A **Commit** is an atomic group of validated operations accepted into the repository history.

Example:

```json
{
  "repository": "repo:relay:alice",
  "commitVersion": "relay-commit-0.1",
  "previousCommit": "sha256:31fd...",
  "createdAt": "2026-08-24T10:00:00Z",
  "operations": [
    {
      "operation": "create",
      "record": "relay://rid:relay:alice/com.relay.post/post_123",
      "contentHash": "sha256:98c2..."
    }
  ],
  "resultingStateRoot": "sha256:a461...",
  "authorisation": {
    "identity": "rid:relay:alice",
    "key": "key-signing-3",
    "submittedBy": "rid:app:writing-client",
    "permissionGrant": "grant_01JX8K"
  },
  "signature": "..."
}
```

The exact serialisation remains provisional.

---

## 8. Commit atomicity

All operations in a commit must either:

- be accepted together;
- or fail together.

A repository must not apply only part of a commit while representing the commit as valid.

For example, if a commit contains:

```text
Create article
Attach cover image
Update project index
```

and the image attachment fails validation, the repository must not silently create the article and omit the remaining operations.

---

## 9. Commit ordering

Each non-initial commit must identify the previous canonical commit.

Example:

```text
Commit A → Commit B → Commit C
```

Commit C is valid as the next canonical commit only if:

- it references Commit B;
- Commit B is the current Repository Head;
- its authority is valid;
- its operations pass validation.

This creates an ordered repository history.

---

## 10. Initial commit

The first repository commit is the **Genesis Commit**.

It has no previous repository commit.

It should identify:

- Repository Identifier;
- associated Relay Identifier;
- initial repository format;
- initial schema rules;
- creation time;
- initial Identity Document reference;
- initial authority;
- initial Repository Head.

Example:

```json
{
  "repository": "repo:relay:alice",
  "previousCommit": null,
  "type": "genesis",
  "identityDocument": "sha256:identity-doc-1...",
  "resultingStateRoot": "sha256:initial-state...",
  "signature": "..."
}
```

The Genesis Commit anchors later repository verification.

---

## 11. Commit Identifier

A **Commit Identifier** should be derived from the deterministic cryptographic hash of the commit’s canonical representation.

Example:

```text
sha256:4be1...
```

If any signed commit field changes, the Commit Identifier must change.

This includes changes to:

- operation list;
- previous commit reference;
- repository identifier;
- resulting state root;
- authorisation data;
- timestamp;
- protocol version.

The signature itself may be excluded from the hashed signing payload or handled according to the chosen canonical format.

---

## 12. Canonical serialisation

Cryptographic hashes require a deterministic representation.

The same logical commit must produce the same bytes before hashing and signing.

Relay must therefore define canonical serialisation rules covering:

- field ordering;
- string encoding;
- number representation;
- date formatting;
- Unicode normalisation;
- omitted values;
- null values;
- arrays;
- binary references.

JSON may be used as a developer-facing representation, but ordinary JSON serialisation is not sufficiently deterministic on its own.

Relay v0.1 must select or define a canonical encoding.

---

## 13. Content Hash

A **Content Hash** is a cryptographic digest of a record version, blob or other immutable representation.

Example:

```text
sha256:98c2...
```

A content hash allows a verifier to detect alteration.

The hash proves that:

- the retrieved bytes match the referenced bytes;
- two identical hashes refer to identical hashed content, subject to the security of the hash function.

It does not prove who created the content.

---

## 14. Hash algorithm identifiers

Hashes must include an algorithm identifier.

Examples:

```text
sha256:...
sha512:...
blake3:...
```

The protocol must permit algorithm upgrades.

It must not assume that one algorithm remains secure forever.

A record or commit should be verifiable using the algorithm that was valid when it was created, subject to later security policy.

---

## 15. Hash agility

Relay should support cryptographic agility.

A future protocol version may:

- approve new hash algorithms;
- deprecate weak algorithms;
- require re-checkpointing;
- permit dual hashes during migration;
- distinguish historically valid from currently recommended algorithms.

Changing the hash algorithm must not change the logical Record URI or Relay Identifier.

It may produce a new cryptographic representation or checkpoint.

---

## 16. Repository State Root

The **Repository State Root** is a cryptographic summary of the repository state after a commit.

It should allow verification that:

- a particular record belongs to the state;
- a particular record is absent where supported;
- the exported repository matches the declared state;
- two providers hold the same state;
- migration transferred the complete state.

The state root may be produced by an authenticated data structure such as:

- Merkle tree;
- Merkle search tree;
- Merkle DAG;
- another deterministic authenticated index.

---

## 17. Why a commit chain alone may be insufficient

A simple hash-linked commit chain proves ordering, but verifying one record may require replaying all commits.

An authenticated repository structure can provide efficient proofs such as:

```text
Record post_123 exists in Repository Head H.
```

without downloading the full repository.

Relay v0.1 should support efficient record-inclusion verification.

The first reference implementation may use a simpler structure if it remains compatible with later optimisation.

---

## 18. Inclusion Proof

An **Inclusion Proof** demonstrates that a record or record version is represented in a particular Repository State Root.

The proof should identify:

- Repository Identifier;
- Repository Head;
- Record URI;
- record version or content hash;
- proof path;
- verification algorithm.

A verifier can use the proof to confirm the record’s inclusion without trusting the serving provider.

---

## 19. Absence Proof

An **Absence Proof** demonstrates that no active record exists at a specified repository position in a particular state.

This may be useful for:

- proving a Record Key is unused;
- verifying deletion;
- checking singleton records;
- validating migration completeness.

Absence proofs are more complex than inclusion proofs and depend on the authenticated data structure.

Relay v0.1 may make them optional.

---

## 20. Commit Signature

A commit must contain a valid cryptographic signature.

The signature binds:

- repository;
- previous commit;
- operations;
- resulting state root;
- authorisation information;
- timestamp or sequence information;
- protocol version.

A valid signature proves that the holder of the relevant private key authorised the signed commit representation.

---

## 21. Signing authority

A commit may be signed by:

- an active identity signing key;
- a repository signing key authorised by the Relay Identity;
- a delegated application key within its grant;
- a multi-party authority satisfying a defined threshold;
- a recovery authority during an authorised recovery operation.

The commit must identify which authority path was used.

---

## 22. Identity keys and repository keys

Relay should distinguish between:

### Identity key

Used for high-authority changes such as:

- Identity Document updates;
- provider migration;
- repository-key delegation;
- recovery configuration.

### Repository key

Used for ordinary repository commits.

The repository key may be rotated without changing the Relay Identity.

Compromise of a repository key should not automatically allow an attacker to:

- migrate the identity;
- replace recovery authority;
- transfer identity control.

---

## 23. Provider signing

A Relay Provider may countersign or attest that it accepted and served a commit.

However, provider signature must not replace identity authority.

A provider attestation may prove:

- when the provider accepted the commit;
- which repository state it served;
- that the provider performed validation;
- which service version processed it.

The user’s repository history must remain verifiable after leaving that provider.

---

## 24. Application submission signature

An application may sign the operation it submits.

This can prove:

- which application prepared the operation;
- which installation submitted it;
- that the operation was not altered in transit.

The repository may then include the operation in an identity-authorised commit.

This creates two distinct proofs:

1. application submission;
2. repository acceptance.

The application submission signature does not by itself make the operation canonical.

---

## 25. Commit authorisation patterns

Relay may support several patterns.

### 25.1 Direct identity signing

The identity signs each commit.

Suitable for:

- self-hosting;
- high-security repositories;
- local-first applications.

### 25.2 Delegated repository signing

The identity authorises a repository key operated by the provider or user device.

Suitable for:

- managed hosting;
- ordinary user experience;
- background repository operations.

### 25.3 Application-scoped signing

An application signs operations using a delegated key, and the repository validates the grant before accepting them.

### 25.4 Threshold signing

Several authorised parties approve a high-authority commit.

Suitable for:

- organisations;
- guardianship;
- sensitive migrations.

The commit must make the authority path inspectable.

---

## 26. Commit timestamp

A commit should include a timestamp.

However, an ordinary self-declared timestamp proves only that the signer included that value.

It does not independently prove exact real-world creation time.

Relay should distinguish between:

- claimed commit time;
- provider-observed time;
- witness-observed time;
- externally anchored time.

---

## 27. Commit sequence

A repository may use a monotonically increasing sequence number in addition to hashes.

Example:

```text
Commit sequence: 1842
```

The sequence assists:

- synchronisation;
- debugging;
- detecting missing commits;
- pagination;
- event delivery.

The cryptographic previous-commit reference remains the authoritative ordering mechanism.

A sequence number alone is not sufficient proof.

---

## 28. Clock uncertainty

Providers and devices may have inaccurate clocks.

Relay should avoid treating small timestamp differences as proof of invalidity.

The protocol may record:

- signer-claimed time;
- provider-received time;
- witness-observed time;
- clock source where available.

Ordering within a repository is established primarily by commit ancestry, not timestamp.

---

## 29. Identity Document reference

Every commit must be verifiable against the identity authority valid at the time of signing.

A commit should therefore reference:

- the relevant Identity Document version;
- or enough key-validity information to resolve it.

Example:

```json
{
  "identityDocument": "sha256:identity-document-8..."
}
```

This allows later verification after keys have rotated.

---

## 30. Historical key validation

A key revoked today may have been valid when an earlier commit was created.

Verification must determine:

- when the key became valid;
- when it was revoked;
- whether the commit falls within that authority period;
- whether revocation was retroactive because of compromise.

The protocol must not simply check whether the key is active now.

---

## 31. Key revocation effects

A revocation may be:

### Prospective

The key becomes invalid for future commits.

Earlier valid commits remain valid.

### Retroactive compromise declaration

The controller declares that commits after a specified point may be unauthorised.

This creates a potential repository fork or recovery event requiring explicit resolution.

Retroactive invalidation must not silently rewrite history.

---

## 32. Commit acceptance

A provider accepts a commit only after validating:

- repository identity;
- expected previous commit;
- operation structure;
- schema rules;
- authorisation;
- key validity;
- Permission Grant validity;
- state constraints;
- resulting state root;
- signature.

Acceptance moves the Repository Head to the new Commit Identifier.

---

## 33. Commit rejection

A rejected commit must not alter canonical repository state.

Possible rejection reasons include:

```text
invalid-signature
unknown-repository
stale-head
invalid-schema
permission-denied
grant-revoked
record-conflict
record-not-found
record-key-used
invalid-state-root
unsupported-protocol-version
provider-policy-rejection
```

The response should distinguish protocol failure from provider policy where safe.

---

## 34. Stale-head rejection

A commit prepared against an earlier Repository Head must not be accepted automatically.

Example:

```text
Application expected head B.
Repository is already at head C.
```

The application must:

- refresh repository state;
- reconstruct the operation;
- merge changes where appropriate;
- or request conflict resolution.

This prevents silent overwriting.

---

## 35. Batch commits

A commit may contain several operations.

Batching can improve:

- atomic workflows;
- performance;
- consistency;
- reduced signing overhead.

However, very large commits may make:

- failure handling harder;
- audit review less clear;
- synchronisation less efficient.

Relay should not require one operation per commit or permit unbounded commit size.

Providers may define reasonable limits.

---

## 36. System-generated commits

A provider may need to generate commits for actions such as:

- retention expiry;
- restoration;
- migration normalisation;
- conflict resolution requested by the controller;
- automated deletion under approved policy.

A system-generated commit still requires valid delegated authority.

The provider must identify itself as submitter and state the authority used.

---

## 37. Deterministic state calculation

Given:

- the same Genesis Commit;
- the same ordered valid commits;
- the same schemas and deterministic rules;

two compliant implementations should derive the same canonical repository state.

Where schema behaviour is non-deterministic or application-specific, it must not affect protocol-level repository state calculation.

---

## 38. Verification modes

Relay should support several verification modes.

### 38.1 Full verification

The verifier checks:

- complete commit history;
- every signature;
- every operation;
- every resulting state root;
- all records and blobs.

### 38.2 Snapshot verification

The verifier validates:

- a trusted checkpoint;
- all commits after that checkpoint;
- current state.

### 38.3 Record verification

The verifier checks one record against a Repository Head using an inclusion proof.

### 38.4 Export verification

The verifier confirms that an export matches its manifest and Repository Head.

### 38.5 Migration verification

The destination confirms that the imported state matches the source state.

Different use cases may require different levels.

---

## 39. Full verification

Full verification provides the strongest independent assurance but may be expensive for large repositories.

It may require:

- Identity Document history;
- commit history;
- schemas;
- record versions;
- blob hashes;
- revocation records.

The reference implementation should provide a command or service capable of full verification.

---

## 40. Checkpoint

A **Checkpoint** is a signed assertion about repository state at a particular Commit Identifier.

Example:

```json
{
  "repository": "repo:relay:alice",
  "commit": "sha256:head-100...",
  "stateRoot": "sha256:root-100...",
  "createdAt": "2026-08-24T10:00:00Z",
  "signedBy": "rid:relay:alice",
  "signature": "..."
}
```

A verifier may trust a checkpoint and validate only later commits.

---

## 41. Checkpoint purposes

Checkpoints may support:

- faster verification;
- backup validation;
- migration;
- recovery;
- cryptographic algorithm upgrade;
- pruning old operational history;
- independent witnessing.

A checkpoint must not conceal known repository forks or invalid history.

---

## 42. Checkpoint trust

A checkpoint may be signed by:

- the Relay Identity;
- the active provider;
- an independent backup provider;
- a witness service;
- several parties.

A verifier decides which signatures it requires.

The protocol should not force all users to trust one global checkpoint service.

---

## 43. Witness

A **Witness** is an independent service that observes and signs a repository state or commit.

A witness may help detect:

- provider equivocation;
- hidden forks;
- retroactive history rewriting;
- inconsistent states served to different observers.

A witness does not own or control the repository.

---

## 44. Witness statement

A witness statement may contain:

```json
{
  "repository": "repo:relay:alice",
  "observedCommit": "sha256:head-100...",
  "observedAt": "2026-08-24T10:05:00Z",
  "witness": "rid:service:witness-one",
  "signature": "..."
}
```

This proves that the witness observed the stated commit by the stated time according to its own clock.

---

## 45. Witness privacy

Private repository activity should not automatically be disclosed to public witnesses.

Possible privacy-preserving approaches include witnessing only:

- Repository Head;
- state root;
- commit identifier;
- encrypted commitment.

A witness does not need record contents to attest that a repository state existed.

---

## 46. Multiple witnesses

A user may choose several independent witnesses.

This reduces dependence on:

- one provider;
- one registry;
- one jurisdiction;
- one technical implementation.

Relay v0.1 should permit witnessing but not require it for ordinary repository validity.

---

## 47. Provider equivocation

**Equivocation** occurs when a provider serves different canonical repository histories to different observers.

Example:

```text
Observer A sees head X.
Observer B sees incompatible head Y.
```

If X and Y cannot exist in one linear history, the provider may be serving a hidden fork.

Witnesses and cross-checks can expose this.

---

## 48. Fork

A **Fork** occurs when two commits claim the same previous commit.

Example:

```text
        Commit B
       /
Commit A
       \
        Commit C
```

Both B and C reference A.

A fork may result from:

- concurrent writes;
- provider error;
- offline device activity;
- migration failure;
- compromised key;
- malicious equivocation;
- recovery from stale backup.

A fork must be detected and surfaced.

---

## 49. Valid-looking fork

Both branches may contain cryptographically valid signatures.

Cryptographic validity alone does not determine which branch is canonical.

The resolution may depend on:

- which authority was active;
- migration state;
- key revocation;
- provider activation time;
- controller decision;
- recovery policy.

---

## 50. Fork detection

A verifier detects a fork when it finds:

- two distinct commits;
- for the same repository;
- referencing the same previous commit;
- where neither descends from the other.

Providers should expose fork status rather than silently selecting one branch.

---

## 51. Fork states

A repository may enter a state such as:

```text
fork-detected
resolution-pending
resolved
compromised
```

During unresolved high-risk forks, providers may:

- permit read-only access;
- reject ordinary writes;
- require controller review;
- isolate suspicious branches.

---

## 52. Resolution Commit

A **Resolution Commit** explicitly identifies the canonical outcome of a fork.

It may:

- select one branch;
- merge compatible records;
- invalidate unauthorised commits;
- restore from a trusted checkpoint;
- rotate compromised keys.

Example:

```json
{
  "type": "fork-resolution",
  "repository": "repo:relay:alice",
  "forkPoint": "sha256:commit-A...",
  "selectedBranch": "sha256:commit-B...",
  "rejectedBranch": "sha256:commit-C...",
  "resultingStateRoot": "sha256:resolved-root...",
  "reason": "destination accepted writes before migration activation",
  "authorisedBy": "rid:relay:alice",
  "signature": "..."
}
```

---

## 53. Branch preservation

Rejected branches may remain available as historical evidence.

They must not continue to be served as canonical repository state.

A resolution should preserve enough information to establish:

- that a fork existed;
- which commits were affected;
- why one branch was rejected or reconciled.

---

## 54. Merge resolution

Where both branches contain legitimate changes, a resolution may create a new state incorporating both.

For example:

```text
Branch B updated profile.
Branch C created unrelated post.
```

A controller-approved resolution may preserve both changes.

Conflicting edits to the same record require explicit merge or selection.

---

## 55. Repository pruning

Providers may wish to prune old operational data.

Pruning must not destroy the ability to verify current state beyond the declared verification model.

Possible approaches include:

- retaining all commit metadata but removing deleted content;
- retaining checkpoints and later commits;
- archiving older history;
- preserving hashes and signatures;
- storing old history with an independent archival provider.

Relay v0.1 should not require indefinite hot storage of every prior record body.

---

## 56. Pruning declaration

A repository should disclose its verification-retention mode.

Examples:

```text
full-history
checkpointed-history
metadata-only-history
limited-history
```

A provider must not claim full historical verification if required data has been discarded.

---

## 57. Deleted-content verification

After content erasure, the repository may retain:

- Record URI;
- deleted version number;
- prior content hash;
- deletion commit;
- tombstone;
- authorising authority.

This proves that a version with a particular hash existed without retaining the content itself.

A verifier cannot reconstruct deleted content from the hash.

---

## 58. Privacy of commit metadata

Even when record contents are encrypted, commit metadata may reveal:

- activity timing;
- number of records;
- application usage;
- relationship activity;
- repository growth.

Sensitive repositories may need:

- encrypted operation details;
- padded commits;
- batched timing;
- private witness arrangements;
- separated public and private commit streams.

Relay v0.1 may initially accept some metadata leakage while clearly documenting it.

---

## 59. Public and private commit streams

A future implementation may separate:

- public repository commits;
- private repository commits;
- identity-authority commits.

This reduces unnecessary disclosure and allows different security models.

Relay v0.1 may use one logical repository history while keeping private operation contents encrypted.

The architecture should not permanently require all activity to be publicly observable.

---

## 60. Verification API

A compliant provider should expose operations equivalent to:

```text
Read Repository Head
Read commit
List commits after a known head
Verify commit
Read record proof
Read checkpoint
Read witness statements
Report fork status
```

The exact transport and endpoint design will be defined later.

---

## 61. Offline verification

A repository export must be verifiable without contacting the former provider, provided the verifier has:

- export package;
- required Identity Documents;
- schemas;
- public keys;
- revocation information;
- trusted checkpoints where used.

Offline verification is essential for provider independence.

---

## 62. Independent verifier

Relay should support an independent verification tool that is not operated by the repository provider.

The tool should be able to report:

```text
Repository identity: valid
Commit chain: valid
Current head: valid
Record count: 1,842
Blob count: 613
Invalid signatures: 0
Missing commits: 0
Unknown schemas: 7
Forks detected: 0
```

This tool is an important part of proving portability.

---

## 63. Verification error classes

Verification failures should be grouped clearly.

Possible classes include:

### Integrity failure

Content does not match its hash.

### Authority failure

Signature or Permission Grant is invalid.

### Continuity failure

Commit ancestry is missing or inconsistent.

### State failure

The resulting state does not match the declared root.

### Identity failure

The signing key was not valid for the identity.

### Completeness failure

Required records, commits or blobs are missing.

### Schema failure

Record content does not match the declared schema.

### Fork failure

Competing histories exist.

These should not be collapsed into a generic “invalid repository” response.

---

## 64. Verification warnings

Some findings may be warnings rather than failures.

Examples:

```text
Unknown schema preserved
Historical timestamp not independently witnessed
Old but historically valid hash algorithm
Blob intentionally omitted from metadata-only export
Application provenance self-declared
```

A verifier should distinguish:

- cryptographic failure;
- incomplete evidence;
- unsupported interpretation;
- policy warning.

---

## 65. Schema verification

A verifier must validate records against the schema version applicable when the record was accepted.

Later schema changes must not retroactively make historical records invalid unless the schema explicitly defines such behaviour.

Schemas themselves should be:

- versioned;
- integrity-addressed;
- retrievable;
- attributable to a publisher.

---

## 66. Schema disappearance

If a schema publisher disappears, historical records must remain preservable and verifiable.

An export should include:

- the schema;
- or a verifiable copy;
- or a stable integrity-addressed reference.

An application should not be able to invalidate user records by deleting its online schema definition.

---

## 67. Blob verification

A blob is verified by recalculating its content hash.

The verifier should confirm:

- algorithm;
- byte length;
- media type where declared;
- content hash;
- record references.

Media type does not itself prove content safety.

Malware and content-policy checks are separate.

---

## 68. Encrypted blob verification

For encrypted blobs, the protocol must define whether the permanent hash applies to:

- plaintext;
- ciphertext;
- or both.

Hashing plaintext improves identity across re-encryption but may leak equality.

Hashing ciphertext preserves storage confidentiality but changes when re-encrypted.

Relay may need separate identifiers such as:

```text
plaintextContentHash
ciphertextStorageHash
```

This remains an open design issue.

---

## 69. Verification during migration

The destination provider must verify:

1. export manifest;
2. Identity Document chain;
3. Genesis Commit;
4. commit ancestry;
5. signatures;
6. resulting state;
7. records;
8. tombstones;
9. blobs;
10. final Repository Head.

Activation must not occur if critical verification fails.

---

## 70. Source and destination comparison

Before migration activation, both providers should report the same:

```text
Repository Identifier
Final Repository Head
Repository State Root
Record count
Blob manifest root
```

Count equality alone is not sufficient.

The cryptographic roots provide the stronger comparison.

---

## 71. Verification receipt

A verification process may produce a signed receipt.

Example:

```json
{
  "repository": "repo:relay:alice",
  "verifiedHead": "sha256:head-102...",
  "verifiedStateRoot": "sha256:root-102...",
  "verificationMode": "full",
  "verifiedAt": "2026-08-24T15:00:00Z",
  "verifier": "rid:service:independent-verifier",
  "result": "valid",
  "signature": "..."
}
```

A receipt records what was checked, not an eternal guarantee of repository truth.

---

## 72. External anchoring

A repository may optionally anchor a checkpoint in an external system.

Possible systems include:

- public transparency log;
- trusted timestamp service;
- institutional archive;
- distributed ledger;
- public blockchain.

External anchoring is optional.

Relay must not require one specific anchoring infrastructure.

---

## 73. Transparency log

A **Transparency Log** may record repository checkpoints or Identity Document updates in an append-only public structure.

This can help detect:

- hidden rewrites;
- inconsistent identity documents;
- provider equivocation;
- backdated changes.

A transparency log need not contain record contents.

---

## 74. Global consensus is unnecessary

Relay repositories are individually controlled histories.

The world does not need to agree on every post, update or private record.

Consensus is needed only over questions such as:

- which identity authority is valid;
- which Repository Head the controller recognises;
- whether a migration cutover occurred.

These can be resolved through signed identity authority rather than global network consensus.

---

## 75. Provider trust reduction

The Commit and Verification Model reduces, but does not eliminate, provider trust.

A provider may still:

- refuse service;
- delay writes;
- censor records under its policy;
- lose unreplicated data;
- retain unauthorised copies;
- misrepresent legal compliance.

Cryptographic verification primarily protects against undetected alteration and false continuity claims.

Availability and privacy require additional safeguards.

---

## 76. Local-first commits

A future Relay client may create commits locally before synchronising with a provider.

Benefits include:

- offline use;
- direct user signing;
- reduced provider authority;
- local backup.

Challenges include:

- conflict handling;
- key storage;
- multi-device synchronisation;
- stale Repository Heads.

Relay v0.1 should not require local-first operation, but its commit format should not prevent it.

---

## 77. Multi-device commits

Several devices may submit repository operations.

Each device may have:

- its own authentication credential;
- a delegated device key;
- limited scopes;
- revocation state.

The repository still maintains one canonical commit sequence.

Concurrent submissions must be resolved against the current Repository Head.

---

## 78. Multi-party commits

An organisation may require multiple approvals for certain commits.

Example:

```text
Two directors must approve repository migration.
```

A commit may contain:

- multiple signatures;
- threshold-signature proof;
- reference to a completed approval record.

The protocol must identify which authority rule was satisfied.

---

## 79. High-authority commit types

Some commits should be specially classified.

Examples:

```text
repository-genesis
fork-resolution
recovery
migration-cutover
repository-key-delegation
repository-key-revocation
repository-termination
```

These commits may require stronger authority than ordinary content commits.

---

## 80. Recovery commit

A **Recovery Commit** may establish a new canonical state after compromise or provider failure.

It should identify:

- trusted prior checkpoint;
- recovered Repository Head;
- missing or invalidated commits;
- new keys;
- recovery authority;
- reason;
- resulting state.

Recovery must preserve transparency about any lost or rejected history.

---

## 81. Repository termination commit

A repository termination should be represented by a high-authority final commit or identity event.

It may indicate:

- repository archived;
- repository erased;
- identity terminated;
- final Repository Head;
- residual verification data;
- no further commits permitted.

A terminated Repository Identifier must not later be assigned to a different identity.

---

## 82. Verification and moderation

A cryptographically valid record may still violate:

- law;
- provider policy;
- community standards;
- application rules.

Verification and moderation are separate.

An application may correctly state:

```text
This record is authentic to the repository but hidden under our policy.
```

It should not represent moderation removal as cryptographic invalidity.

---

## 83. Verification and factual truth

A signed record saying:

```text
Alice won an award.
```

proves only that the relevant authority signed or accepted that statement.

Factual trust may require:

- external credential;
- issuer reputation;
- supporting evidence;
- independent verification;
- dispute records.

Relay must avoid presenting cryptographic provenance as universal truth.

---

## 84. Required v0.1 commit operations

A compliant implementation must support:

```text
Create Genesis Commit
Validate operation
Create commit
Sign commit
Verify commit signature
Calculate Commit Identifier
Read previous commit
Read Repository Head
Advance Repository Head
Reject stale-head commit
Calculate Repository State Root
Generate record inclusion proof
Verify record inclusion proof
Create checkpoint
Verify checkpoint
List commits after known head
Detect missing commit
Detect fork
Report fork status
Create Resolution Commit
Verify repository export
Verify migrated repository
Verify blob hash
Verify historical key authority
Produce verification report
```

Witnessing and absence proofs may be optional in the first reference implementation.

---

## 85. Commit invariants

The following rules must always remain true.

### Invariant 1

Every non-genesis canonical commit references the previous canonical commit.

### Invariant 2

A commit’s identifier changes if its signed contents change.

### Invariant 3

A valid signature does not by itself prove factual truth.

### Invariant 4

A commit cannot be canonical unless its authority was valid when accepted.

### Invariant 5

A rejected commit does not alter repository state.

### Invariant 6

All operations in an accepted commit are applied atomically.

### Invariant 7

The Repository Head identifies one current canonical commit.

### Invariant 8

Two conflicting successors to one commit create a detectable fork.

### Invariant 9

A provider may attest to a commit but may not replace identity authority.

### Invariant 10

Historical commits remain verifiable after provider migration.

### Invariant 11

Key rotation does not invalidate commits validly signed before rotation.

### Invariant 12

Deleted content may be erased while retaining minimum integrity evidence.

### Invariant 13

A repository export must match its declared Repository Head and state root.

### Invariant 14

Verification must be possible independently of the current provider.

### Invariant 15

Unknown schemas may limit interpretation but must not prevent integrity preservation.

---

## 86. Compliance scenario

A basic Commit and Verification implementation should pass the following test.

### Genesis

Alice creates:

```text
Relay Identity:
rid:relay:alice

Repository:
repo:relay:alice
```

The repository creates and signs Genesis Commit 1.

### Record creation

Application A submits a valid request to create:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

The repository validates:

- schema;
- Permission Grant;
- Record Key;
- content hash;
- current Repository Head.

Commit 2 is accepted.

### Independent verification

An independent verifier retrieves:

- Genesis Commit 1;
- Commit 2;
- Identity Document history;
- the record;
- the inclusion proof.

It confirms that the record is included in Commit 2’s resulting repository state.

### Record update

Application B updates the post against Commit 2.

Commit 3 is accepted.

The Record URI remains unchanged.

### Stale update

Application A submits another update expecting Commit 2 as the current head.

The repository is already at Commit 3.

The stale submission is rejected.

### Key rotation

Alice rotates the repository signing key.

Commit 4 records the authorised delegation change.

Earlier commits remain valid under the former key’s historical validity period.

### Migration

The repository is exported at Commit 4.

Provider B independently verifies:

- commit chain;
- signatures;
- records;
- state root;
- blobs;
- final Repository Head.

Provider B reports the same canonical state.

### Fork detection

Due to an incorrect migration process:

- Provider A accepts Commit 5A;
- Provider B accepts Commit 5B;
- both reference Commit 4.

The system detects a fork.

Alice issues a Resolution Commit selecting or reconciling the valid changes.

If these events occur without undetected alteration, silent overwriting or dependence on one provider’s claims, the implementation satisfies the basic Relay Commit and Verification objective.

---

## 87. Open design questions

### 87.1 Canonical encoding

Should commits use canonical JSON, CBOR, DAG-CBOR or another deterministic encoding?

### 87.2 Authenticated data structure

Which structure best supports:

- record proofs;
- efficient updates;
- partial synchronisation;
- implementation simplicity?

### 87.3 Signing model

Should the repository commit key usually be:

- user-held;
- provider-operated under delegation;
- device-held;
- or configurable?

### 87.4 Individual record signatures

When should a record be individually signed in addition to commit-level signing?

### 87.5 Checkpoint requirements

How frequently should providers create checkpoints, and who should sign them?

### 87.6 Historical pruning

What minimum information must remain for a provider to claim Relay v0.1 compliance?

### 87.7 Witnessing

Should independent witnessing be recommended, required for high-value identities or entirely optional?

### 87.8 Timestamping

Should Relay specify an optional trusted timestamp profile?

### 87.9 Hash algorithms

Which algorithms should v0.1 require and which should remain optional?

### 87.10 Encrypted content hashes

Should permanent blob identity be based on plaintext, ciphertext or a layered model?

### 87.11 Fork resolution

Which authority rules govern resolution after key compromise, provider equivocation or split-brain migration?

### 87.12 Local-first support

How much complexity should v0.1 accept to support offline and multi-device commit creation?

---

## 88. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- commits form a signed hash-linked history;
- every commit references one previous canonical commit;
- one canonical Repository Head exists at a time;
- operations are applied atomically;
- record content and blobs use cryptographic hashes;
- commits contain or reference a resulting Repository State Root;
- repository authority is distinct from application submission authority;
- ordinary repository signing may use a delegated repository key;
- high-authority commits require stronger identity authority;
- historical key validity is retained for verification;
- stale-head submissions are rejected;
- forks are detected and require explicit resolution;
- exports are independently verifiable;
- full history may later be checkpointed or archived;
- deleted content may be removed while hashes and tombstones remain;
- external witnesses and transparency logs are optional;
- no public blockchain or global consensus is required;
- verification tooling must work independently of the active provider.

---

## 89. Core verification principle

The Commit and Verification Model can be reduced to one rule:

> Relay does not ask users to trust that a provider preserved their history correctly; it gives another provider or independent tool a way to verify it.

The next core object is the **Relay Discovery and Resolution Model**: how applications translate a human-readable handle or permanent Relay Identifier into the current Identity Document, provider location and repository services without making one company the permanent gatekeeper.