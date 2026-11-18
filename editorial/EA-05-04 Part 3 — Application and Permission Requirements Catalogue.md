# EA-05-04 — Application and Permission Requirements Catalogue

## Part 3 — Scope, Resource Boundaries and Read/Write Authority

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how Relay application authority is bounded by composable scopes, resource levels and independently grantable actions. It also separates materially different read states and write operations so that access to one category does not silently confer another.

This catalogue part is generated from the completed and verified REM-04 extraction series. The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 11–15 and REM-04 entries `REM-04-149` through `REM-04-212`.

It governs:

- composable permission scopes;
- optional scope constraints;
- resource-scope levels;
- repository-wide authority;
- the recommended v0.1 action vocabulary;
- separation of high-authority actions;
- current, historical, metadata, blob, provenance, restricted and private reads; and
- distinct creation, update, deletion, visibility, rights, draft and publication authority.

Section 16 and later are intentionally deferred.

---

# 3. Requirements

---

## REL-APP-059

### Title

Defined Scope Boundary

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Each permission scope **MUST** define the boundary within which an application is authorised to act.

### Rationale

A precise boundary separates authorised operations from activity that must be rejected.

### Source

- REM-04-149
- `design-notes/04-application-and-permission-model.md`, Section 11

### Related Invariants

- CI-06

---

## REL-APP-060

### Title

Composable Narrow Scopes

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay scopes **SHOULD** be composable from narrower access dimensions rather than represented only through broad, undifferentiated labels.

### Rationale

Composable scopes allow authority to be expressed by resource, action, purpose and other constraints without hiding the actual permission behind a general account-access label.

### Source

- REM-04-150
- REM-04-151
- `design-notes/04-application-and-permission-model.md`, Section 11

### Related Invariants

- CI-06

---

## REL-APP-061

### Title

Available Scope Constraints

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A permission scope **MAY** be limited by repository, collection, specific record, record field, action, audience, time, purpose, application installation, device, frequency, geographic jurisdiction or legal context.

### Rationale

These independently applicable dimensions allow authority to be tailored to the application function and relevant security, privacy and policy constraints.

### Source

- REM-04-152
- REM-04-153
- REM-04-154
- REM-04-155
- REM-04-156
- REM-04-157
- REM-04-158
- REM-04-159
- REM-04-160
- REM-04-161
- REM-04-162
- REM-04-163
- `design-notes/04-application-and-permission-model.md`, Section 11

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-062

### Title

Scope-Narrowness Evaluation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Implementations **MUST** be able to represent and evaluate relative scope narrowness, including the difference between public and all-record access and between individual-record and collection-wide authority.

### Rationale

Consent, policy evaluation and enforcement require implementations to determine whether a requested or exercised scope exceeds the approved boundary.

### Source

- REM-04-164
- `design-notes/04-application-and-permission-model.md`, Section 11

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-063

### Title

Resource-Scope Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Each resource scope **MUST** identify the resources that the application is authorised to access.

### Rationale

Resource identification defines what is accessible independently of the action scope that defines what may be done.

### Source

- REM-04-165
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06

---

## REL-APP-064

### Title

Repository-Wide Resource Scope

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Permission Model **MAY** represent a resource scope covering an entire Relay Repository.

### Rationale

Repository-wide authority remains possible for exceptional functions, but it is not the default or preferred scope.

### Source

- REM-04-166
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06

---

## REL-APP-065

### Title

Rare Repository-Wide Grants

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Repository-wide resource scopes **SHOULD** be granted only rarely.

### Rationale

A narrower collection, record, field, blob or derived-service scope should be used whenever it can support the declared purpose.

### Source

- REM-04-167
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06

---

## REL-APP-066

### Title

Sensitive Treatment of Repository-Wide Authority

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A repository-wide resource scope **SHOULD** be presented, reviewed and handled as highly sensitive authority.

### Rationale

Repository-wide access exposes a much broader state boundary than ordinary content permissions and requires correspondingly clear consent and controls.

### Source

- REM-04-168
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-067

### Title

Supported Narrow Resource Scopes

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** support resource scopes limited to a specified collection, Relay Record, set of record fields, blob or blob category, or derived service or event stream.

### Rationale

These scope levels permit access to be matched to the actual application function without granting unrelated repository content.

### Source

- REM-04-169
- REM-04-170
- REM-04-171
- REM-04-172
- REM-04-173
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06
- CI-09

---

## REL-APP-068

### Title

Narrowest Practical Resource Scope

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The protocol and consent interfaces **SHOULD** prefer the narrowest practical resource scope capable of supporting the declared application purpose.

### Rationale

The qualification permits a broader scope where a narrower representation would make the intended function infeasible, while rejecting unnecessary access based only on convenience.

### Source

- REM-04-174
- `design-notes/04-application-and-permission-model.md`, Section 12

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-069

### Title

Explicit Allowed Actions

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Permission Grant **MUST** explicitly identify the actions the application is authorised to perform.

### Rationale

An action absent from the grant cannot safely be inferred from access to the resource or from another approved action.

### Source

- REM-04-175
- `design-notes/04-application-and-permission-model.md`, Section 13

### Related Invariants

- CI-06

---

## REL-APP-070

### Title

Recommended v0.1 Action Distinctions

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** distinguish the following independently grantable actions: discover, read, list, create, update, delete, restore, upload-blob, attach-blob, change-visibility, change-audience, subscribe-events, export, import, migrate, manage-permissions, manage-keys and manage-recovery.

### Rationale

The source-defined action vocabulary separates materially different capabilities, including destructive, continuous and high-authority operations, without implying that one action authorises another.

### Source

- REM-04-176
- REM-04-177
- REM-04-178
- REM-04-179
- REM-04-180
- REM-04-181
- REM-04-182
- REM-04-183
- REM-04-184
- REM-04-185
- REM-04-186
- REM-04-187
- REM-04-188
- REM-04-189
- REM-04-190
- REM-04-191
- REM-04-192
- REM-04-193
- `design-notes/04-application-and-permission-model.md`, Section 13

### Related Invariants

- CI-06
- CI-12

---

## REL-APP-071

### Title

Separation of High-Authority Actions

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

High-authority actions, including migration, key management, recovery management and permission management, **MUST NOT** be bundled into ordinary content-access permissions.

### Rationale

These actions can alter constitutional authority or broad repository control and therefore require separate explicit approval.

### Source

- REM-04-194
- `design-notes/04-application-and-permission-model.md`, Section 13

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-072

### Title

Selectable Read-Access Categories

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Permission Grant **MAY** separately authorise current record content, historical versions, metadata only, associated blobs, structured provenance, restricted content or private content within its resource scope.

### Rationale

Separating these categories permits data-state and sensitivity boundaries to be granted without turning ordinary current-content access into access to history, media or private information.

### Source

- REM-04-195
- REM-04-196
- REM-04-197
- REM-04-198
- REM-04-199
- REM-04-200
- REM-04-201
- `design-notes/04-application-and-permission-model.md`, Section 14

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-073

### Title

Distinguishable Read-Access Categories

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** distinguish current content, historical versions, metadata, blobs, provenance, restricted content and private content where any of those categories are requested.

### Rationale

An undifferentiated read label is insufficient where the requested data states or sensitivity levels differ materially.

### Source

- REM-04-202
- `design-notes/04-application-and-permission-model.md`, Section 14

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-074

### Title

No Private or Historical Access from Public-Current Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Authority to read current public records **MUST NOT** automatically grant authority to read deleted, historical or private versions of records.

### Rationale

Current state, history and visibility are separate access dimensions and require separate authority.

### Source

- REM-04-203
- `design-notes/04-application-and-permission-model.md`, Section 14

### Related Invariants

- CI-06
- AI-07

---

## REL-APP-075

### Title

Distinct Write Authorities

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Write authority **MUST** distinguish permission to create new records, update existing records, delete records, change visibility, change structured usage rights, create or submit drafts, and publish records as canonical repository state.

### Rationale

Each write operation has a different effect on repository state, visibility, rights or lifecycle and must remain independently grantable.

### Source

- REM-04-204
- REM-04-205
- REM-04-206
- REM-04-207
- REM-04-208
- REM-04-209
- REM-04-210
- `design-notes/04-application-and-permission-model.md`, Section 15

### Related Invariants

- CI-06
- CI-07
- AI-07

---

## REL-APP-076

### Title

Draft Authority Does Not Imply Publication

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Permission to create or edit a draft **SHOULD NOT** automatically grant permission to publish that draft as a canonical Relay Record.

### Rationale

Draft preparation and canonical publication are distinct lifecycle steps and may require separate user action or approval.

### Source

- REM-04-211
- `design-notes/04-application-and-permission-model.md`, Section 15

### Related Invariants

- CI-06
- CI-07

---

## REL-APP-077

### Title

Text-Update Authority Does Not Imply Public Visibility

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Permission to update a record's text **SHOULD NOT** automatically grant permission to make the record public.

### Rationale

Content modification and audience exposure are separate authorities, allowing a user to delegate editing while retaining visibility control.

### Source

- REM-04-212
- `design-notes/04-application-and-permission-model.md`, Section 15

### Related Invariants

- CI-06
- AI-07

---

# 4. REM coverage and consolidation

| REM range | Catalogue treatment | Catalogue identifier |
|---|---|---|
| `REM-04-149` | Direct | `REL-APP-059` |
| `REM-04-150`–`REM-04-151` | Consolidated composability guidance | `REL-APP-060` |
| `REM-04-152`–`REM-04-163` | Consolidated optional constraint set | `REL-APP-061` |
| `REM-04-164`–`REM-04-168` | Direct | `REL-APP-062`–`REL-APP-066` |
| `REM-04-169`–`REM-04-173` | Consolidated required scope levels | `REL-APP-067` |
| `REM-04-174`–`REM-04-175` | Direct | `REL-APP-068`–`REL-APP-069` |
| `REM-04-176`–`REM-04-193` | Consolidated source-defined action vocabulary | `REL-APP-070` |
| `REM-04-194` | Direct | `REL-APP-071` |
| `REM-04-195`–`REM-04-201` | Consolidated selectable read categories | `REL-APP-072` |
| `REM-04-202`–`REM-04-203` | Direct | `REL-APP-073`–`REL-APP-074` |
| `REM-04-204`–`REM-04-210` | Consolidated distinct write authorities | `REL-APP-075` |
| `REM-04-211`–`REM-04-212` | Direct | `REL-APP-076`–`REL-APP-077` |

All independently testable clauses remain explicit within the consolidated constraint, vocabulary, read-category and write-authority requirements.

---

# 5. Editorial QA record

- Source scope is limited to Sections 11–15 and `REM-04-149` through `REM-04-212`.
- Previous catalogue endpoint: `REL-APP-058`.
- First identifier: `REL-APP-059`.
- Final identifier: `REL-APP-077`.
- Total requirements in this part: 19.
- Numbering is continuous and unique.
- Source `MUST`, `SHOULD`, `SHOULD NOT` and `MAY` strengths are preserved.
- Repository-wide access remains permitted but rare and highly sensitive.
- The v0.1 action vocabulary remains a `SHOULD`, while high-authority bundling retains `MUST NOT`.
- Public-current read authority does not imply historical or private access.
- Draft, publication, content update, visibility and rights authority remain distinct.
- No requirement from Section 16 or later is imported.

---

# 6. Part conclusion

Part 3 establishes composable scope boundaries and independently grantable resource, action, read and write authority.

Part 4 should begin with source Section 16 and `REM-04-213`.
