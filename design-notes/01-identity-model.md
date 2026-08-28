# Relay Protocol v0.1  
## Core Object 1: Relay Identity

### 1. Definition

A **Relay Identity** is the persistent protocol-level entity through which a person or organisation exercises authority over records, relationships and application permissions.

A Relay Identity must not depend permanently on:

- a single application;
- a single hosting provider;
- a single username;
- a single domain;
- a single device;
- a single authentication method.

The identity must remain recognisable as the same identity when any of those elements change.

A Relay Identity is therefore not a profile, account or address.

It is the persistent authority behind them.

---

## 2. Identity components

A Relay Identity consists of five distinct components:

1. **Relay Identifier**
2. **Identity Document**
3. **Controller**
4. **Keys**
5. **Service Locations**

These components must remain conceptually separate.

---

## 3. Relay Identifier

The **Relay Identifier** is the permanent machine-readable identifier for the identity.

Example:

```text
rid:relay:7fs82k9m4v...
```

The exact identifier format remains provisional, but it must satisfy the following requirements.

### 3.1 Permanence

The identifier must remain unchanged when the person:

- changes username;
- changes domain;
- changes Relay Provider;
- replaces a device;
- rotates cryptographic keys;
- changes applications.

### 3.2 Uniqueness

Two independently created Relay Identities must not produce the same identifier.

### 3.3 Non-semantic structure

The identifier should not contain information such as:

- the person's name;
- nationality;
- provider;
- email address;
- account type;
- creation location.

An identifier should identify an entity without describing it.

### 3.4 Provider independence

The identifier must not contain the Relay Provider's domain as an essential part of the identity.

The following would therefore be unsuitable as the permanent identifier:

```text
miles@provider.example
```

or:

```text
https://provider.example/users/miles
```

Those addresses may locate or describe the identity, but they should not define it.

---

## 4. Human-readable handle

A Relay Identity may have one or more human-readable handles.

Examples:

```text
@miles
@miles.jacoby
miles.example.com
```

A handle exists to make an identity understandable and discoverable by people.

It is not the identity itself.

### 4.1 Handles may change

A person may:

- rename a handle;
- add another handle;
- remove a handle;
- move a domain-based handle;
- use different handles in different contexts.

Changing a handle must not create a new Relay Identity.

### 4.2 Handles must resolve to an identity

A valid handle must provide a way for compatible applications to determine:

- the associated Relay Identifier;
- the current Identity Document;
- the current Relay Provider or service location.

### 4.3 Handles may be verified

A person may prove control over a handle through methods such as:

- DNS records;
- domain-hosted verification files;
- signed challenges;
- email-domain verification;
- provider-issued verification.

The protocol should distinguish between:

- an asserted handle;
- a verified handle;
- a formerly verified handle.

### 4.4 Handle reassignment

If a handle is released and later assigned to another identity, applications must not treat the new holder as the previous identity.

Historical records must remain linked to the permanent Relay Identifier, not merely the visible handle.

---

## 5. Identity Document

Each Relay Identity has an **Identity Document**.

The Identity Document is a signed machine-readable record describing the current operational state of the identity.

It may contain:

- the Relay Identifier;
- current public keys;
- recovery keys or recovery authorities;
- current Relay Provider;
- service endpoints;
- verified handles;
- supported protocol versions;
- previous document reference;
- document version;
- timestamp;
- signature.

Example:

```json
{
  "id": "rid:relay:7fs82k9m4v",
  "version": 8,
  "updatedAt": "2026-08-24T10:00:00Z",
  "handles": [
    {
      "value": "miles.example.com",
      "status": "verified"
    }
  ],
  "keys": {
    "signing": [
      {
        "id": "key-signing-3",
        "type": "Ed25519",
        "publicKey": "..."
      }
    ],
    "recovery": [
      {
        "id": "key-recovery-1",
        "type": "Ed25519",
        "publicKey": "..."
      }
    ]
  },
  "services": {
    "repository": "https://relay-provider.example/repository/7fs82k9m4v",
    "authorization": "https://relay-provider.example/oauth",
    "events": "https://relay-provider.example/events"
  },
  "previousDocumentHash": "sha256:...",
  "signature": "..."
}
```

This structure is illustrative rather than final.

---

## 6. Identity Document requirements

### 6.1 Versioned

Every material change must create a new version.

Examples include:

- changing provider;
- rotating a key;
- adding a handle;
- removing a compromised key;
- changing recovery authority.

### 6.2 Signed

Each new Identity Document must be authorised by a currently valid authority.

Depending on the change, that may be:

- an active identity key;
- a recovery key;
- a recovery quorum;
- another authorised recovery method.

### 6.3 Verifiable

A compatible application must be able to verify:

- that the document belongs to the stated Relay Identifier;
- that the document has not been altered;
- that its signer was authorised;
- that it supersedes the previous valid document.

### 6.4 Discoverable

Applications must have a defined method for locating the current valid Identity Document.

The discovery system must not rely permanently on the current Relay Provider.

### 6.5 Historically traceable

The protocol should retain enough information to verify the sequence of Identity Document changes.

This does not require every document to remain publicly available forever, but it must be possible to establish that a current document follows an authorised chain of updates.

---

## 7. Controller

The **Controller** is the person, organisation or authorised authority capable of making changes to the Relay Identity.

In the simplest case:

```text
One human controls one Relay Identity.
```

However, the protocol should also allow:

- an organisation controlled by multiple authorised representatives;
- a minor's identity managed by a guardian;
- an estate-managed identity;
- a brand identity;
- a team identity;
- an automated agent operating under delegated authority.

### 7.1 Controller is a role

The Controller is not necessarily a single database user.

Control may be exercised through:

- one cryptographic key;
- several authorised keys;
- a threshold of several keys;
- a recovery process;
- a delegated authority.

### 7.2 Multiple controllers

An identity may define several controllers.

For example:

```text
Any 2 of 3 directors may approve a provider migration.
```

Or:

```text
A parent may manage the identity until a transfer-of-control condition is met.
```

The exact multi-controller model may be limited in v0.1, but the data model must not assume that all identities are permanently controlled by one login account.

---

## 8. Authentication versus identity authority

The protocol must distinguish between:

- **authentication**, which proves that someone may use a session;
- **identity authority**, which permits changes to the identity itself.

A user signing into an application does not necessarily gain authority to:

- migrate the identity;
- rotate root keys;
- change recovery settings;
- transfer control;
- delete the repository.

For example, a normal application session may allow:

```text
Create a post
Edit a profile field
Follow another identity
```

But not:

```text
Change Relay Provider
Replace recovery keys
Transfer identity control
```

High-authority operations should require stronger verification.

---

## 9. Keys

A Relay Identity may use several key types.

### 9.1 Signing keys

Signing keys authorise ordinary records and repository commits.

They may be rotated without changing the Relay Identifier.

### 9.2 Authentication keys

Authentication keys allow a person or device to establish a session.

These may be associated with:

- passkeys;
- registered devices;
- hardware security keys;
- secure mobile credentials.

Authentication keys do not necessarily have authority to alter the Identity Document.

### 9.3 Recovery keys

Recovery keys are used when ordinary access is lost or compromised.

Recovery authority should be separated from everyday signing authority.

### 9.4 Delegated application keys

An application may receive a limited delegated capability.

Such a key may permit the application to perform only specific actions.

For example:

```text
Create records of type relay.post
Read public profile records
Upload blobs
Valid until 30 September 2026
```

It must not become a general identity key.

### 9.5 Key rotation

The protocol must support:

- adding a new key;
- retiring an old key;
- revoking a compromised key;
- recording when a key became valid;
- recording when a key ceased to be valid.

Historical signatures must be validated against the key state that existed when the signature was created.

---

## 10. Service Locations

A Relay Identity may point to one or more service locations.

These may include:

- repository endpoint;
- authorisation endpoint;
- event endpoint;
- media endpoint;
- migration endpoint;
- public profile endpoint;
- credential endpoint.

Service locations are replaceable.

Changing a service location must not alter the Relay Identifier.

### 10.1 Provider migration

When a person changes Relay Provider:

- the Identity Document is updated;
- new service locations are published;
- the old provider may redirect requests temporarily;
- applications discover the new location;
- the identity remains unchanged.

### 10.2 Multiple service providers

A Relay Identity may eventually use different providers for different functions.

For example:

```text
Identity resolution: Provider A
Public repository: Provider B
Private vault: Provider C
Media storage: Provider D
```

Relay v0.1 may begin with one primary provider, but the architecture should not permanently bind all services together.

---

## 11. Identity creation

Creating a Relay Identity should produce:

1. a Relay Identifier;
2. an initial Identity Document;
3. at least one valid identity authority;
4. a recovery configuration;
5. a repository location;
6. a signed initial identity event.

The creation process must not require a public blockchain.

### 11.1 Initial trust

The initial Identity Document establishes the first recognised authority for the identity.

That document becomes the root from which future authorised changes are verified.

### 11.2 Hosted creation

A Relay Provider may assist with identity creation.

However, the provider must not secretly retain exclusive authority that prevents the person from migrating.

### 11.3 Self-hosted creation

A technically capable person or organisation may create and host a Relay Identity independently.

A self-hosted identity and a commercially hosted identity must use the same protocol-level rules.

---

## 12. Identity recovery

Recovery is a core protocol requirement, not an optional hosting feature.

A practical recovery system may use one or more of:

- recovery code;
- secondary passkey;
- trusted devices;
- trusted contacts;
- provider-assisted identity verification;
- delayed recovery;
- multi-party approval;
- offline recovery key.

### 12.1 Recovery must not silently create a new identity

A successful recovery operation restores control over the existing Relay Identifier.

It must not create a replacement identity and merely copy visible data.

### 12.2 Recovery events must be recorded

A successful recovery should create a signed or otherwise verifiable identity event indicating:

- that recovery occurred;
- which authority approved it;
- which keys were replaced or revoked;
- when the change became effective.

### 12.3 Recovery risk

The recovery system may become the weakest point in identity security.

Relay implementations must therefore distinguish clearly between:

- ordinary authentication recovery;
- identity-authority recovery;
- provider-account recovery.

These are not necessarily the same process.

---

## 13. Identity transfer

The protocol may permit a Relay Identity to be transferred to another controller.

Possible cases include:

- organisational leadership change;
- estate succession;
- transfer of a brand;
- a minor reaching adulthood;
- legal restructuring.

Transfer must be explicit and verifiable.

It must not occur merely because:

- a provider account was sold;
- a domain expired;
- an email address changed;
- a username was reassigned.

The transfer rules require further design and may be restricted in v0.1.

---

## 14. Identity deletion

Deleting a Relay Identity is not equivalent to deleting a provider account.

A deletion process must define what happens to:

- the Identity Document;
- the repository;
- public records;
- private records;
- relationships;
- application permissions;
- credentials;
- historical signatures;
- identifiers referenced by other people.

A Relay Identifier should not later be reassigned to another entity.

The protocol may support an identity state such as:

```text
deactivated
```

or:

```text
terminated
```

rather than pretending that all historical references can disappear.

The exact deletion model will be defined after the repository and relationship models are complete.

---

## 15. Identity states

A Relay Identity may have one of the following states:

### Active

The identity is operational and its current service locations are available.

### Migrating

The identity is moving between providers.

Both old and new service information may temporarily be available.

### Recovery pending

A recovery process has begun but is not yet complete.

High-authority actions may be temporarily restricted.

### Suspended

The current provider has restricted service.

Suspension by a provider must not automatically terminate the underlying identity.

### Deactivated

The controller has intentionally disabled normal operation.

### Terminated

The identity has been permanently retired according to the protocol's termination rules.

These states describe the identity or service condition and must not be conflated with an application's moderation decision.

---

## 16. Provider suspension versus identity suspension

A Relay Provider may suspend hosting for legal, security or contractual reasons.

However, the provider is suspending its service, not claiming ownership over the identity.

Where legally permissible, the provider should allow:

- repository export;
- migration to another provider;
- access to recovery information;
- retrieval of lawful records.

An application may separately choose not to display or interact with an identity.

The protocol must distinguish between:

- provider suspension;
- application blocking;
- community moderation;
- protocol-level identity termination.

---

## 17. Required v0.1 identity operations

A compliant Relay v0.1 implementation must support:

```text
Create identity
Resolve identity
Read current Identity Document
Verify Identity Document
Update service location
Add key
Revoke key
Rotate key
Add handle
Remove handle
Verify handle
Initiate recovery
Complete recovery
Export identity metadata
Migrate provider
```

Identity transfer and permanent termination may remain provisional until their security models are more fully defined.

---

## 18. Identity invariants

The following rules must always remain true.

### Invariant 1

Changing a handle does not change the Relay Identifier.

### Invariant 2

Changing a provider does not change the Relay Identifier.

### Invariant 3

Rotating a key does not change the Relay Identifier.

### Invariant 4

An application cannot become the Controller merely because it created records for the person.

### Invariant 5

A provider cannot become the permanent owner of an identity merely because it hosts the repository.

### Invariant 6

A historical record remains attributable to the same Relay Identifier after provider migration.

### Invariant 7

A released handle must not transfer historical identity continuity to its next holder.

### Invariant 8

Recovery restores authority over the same identity rather than creating a substitute identity.

### Invariant 9

A provider suspension must not be represented as protocol-level deletion.

### Invariant 10

High-authority identity operations must be distinguishable from ordinary application actions.

---

## 19. Compliance scenario

A basic identity implementation should pass the following test.

### Initial state

A person creates a Relay Identity with:

```text
Relay Identifier:
rid:relay:7fs82k9m4v

Handle:
miles.provider-a.example

Provider:
Provider A
```

### Change 1: Handle update

The person changes the handle to:

```text
miles.example.com
```

The Relay Identifier remains:

```text
rid:relay:7fs82k9m4v
```

### Change 2: Key rotation

The person replaces the ordinary signing key.

Previously signed records remain verifiable.

The Relay Identifier remains unchanged.

### Change 3: Provider migration

The person moves the repository from Provider A to Provider B.

The Identity Document now points to Provider B.

Applications resolve the identity and locate the new provider.

The Relay Identifier remains unchanged.

### Change 4: Application replacement

The person stops using Application X and begins using Application Y.

Application Y reads the person's authorised records and relationships from Provider B.

The person does not recreate the identity or rebuild the underlying social graph.

If all four changes occur without breaking continuity, the implementation satisfies the basic Relay identity objective.

---

## 20. Open design questions

The following questions remain unresolved.

### 20.1 Identifier format

Should Relay define its own identifier method, or use an existing decentralised identifier structure?

### 20.2 Identity Document discovery

Where is the current authoritative Identity Document resolved when the user changes providers?

Possible approaches include:

- domain-based discovery;
- distributed resolution registry;
- signed redirect chain;
- independent resolution nodes;
- existing decentralised identifier infrastructure.

### 20.3 Recovery authority

Should managed Relay Providers be permitted to recover identities independently, or should recovery always require an additional user-controlled authority?

### 20.4 Provider disappearance

How does the identity remain resolvable if the current provider disappears without publishing a migration event?

### 20.5 Handle conflicts

How are handle claims and conflicts resolved across providers?

### 20.6 Organisational control

What minimum multi-controller model should v0.1 support?

### 20.7 Identity transfer

Should transfer be supported in v0.1, or delayed until stronger legal and technical models exist?

---

## 21. Provisional decisions for v0.1

To keep implementation achievable, Relay v0.1 will provisionally assume:

- each identity has one primary Relay Provider;
- each identity has one permanent non-semantic Relay Identifier;
- each identity has a versioned signed Identity Document;
- handles are optional and replaceable;
- passkeys are the preferred user authentication method;
- signing and recovery authority are distinct;
- provider migration preserves the Relay Identifier;
- identity records are verifiable without blockchain consensus;
- multi-controller identities are allowed by the model but may receive limited implementation support;
- private-vault identity authority will be designed separately.

---

## 22. Core identity principle

The identity model can be reduced to one rule:

> A Relay Identity belongs to its controller, not to the application that displays it, the provider that hosts it, the handle that names it or the device that accesses it.

The next core object is the **Relay Repository**: the canonical collection of records associated with a Relay Identity and the mechanism through which those records remain verifiable, portable and usable across applications.