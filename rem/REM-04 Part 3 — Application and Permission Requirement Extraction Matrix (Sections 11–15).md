# REM-04 Part 3 — Application and Permission Requirement Extraction Matrix (Sections 11–15)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 11–15 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

11. Scope
12. Resource scope
13. Action scope
14. Read access
15. Write access

Requirement identifiers continue sequentially from Part 2, beginning with `REM-04-149`.

---

# 11. Scope

## REM-04-149 — Scope defines the access boundary

**Source**  
Section 11: “A Scope defines the boundary of access.”

**Requirement**  
Each permission scope MUST define the boundary within which an application is authorised to act.

**Classification**  
Authorisation; access boundary; least privilege.

**Notes**  
A scope must be sufficiently precise to distinguish authorised activity from unauthorised activity.

---

## REM-04-150 — Composable scopes

**Source**  
Section 11: “Relay scopes should be composable rather than expressed as broad labels such as: Full account access.”

**Requirement**  
Relay scopes SHOULD be composable from narrower access dimensions rather than represented only through broad, undifferentiated labels.

**Classification**  
Scope design; least privilege; recommendation.

**Notes**  
Composition allows a grant to combine specific resources, actions, purposes and other constraints without granting general account authority.

---

## REM-04-151 — Avoidance of broad full-account labels

**Source**  
Section 11, example of a discouraged broad label: “Full account access”.

**Requirement**  
Permission interfaces and grants SHOULD avoid using a broad label such as `Full account access` where the requested authority can be expressed through narrower scopes.

**Classification**  
Consent clarity; least privilege; recommendation.

**Notes**  
The source does not absolutely prohibit repository-wide grants, but discourages vague labels that hide the actual authority requested.

---

## REM-04-152 — Repository constraint

**Source**  
Section 11: “A scope may be limited by: repository...”

**Requirement**  
A permission scope MAY be limited to a specified Relay Repository.

**Classification**  
Resource scope; repository boundary.

**Notes**  
Repository limitation prevents a grant from automatically applying to other repositories controlled by the same identity.

---

## REM-04-153 — Collection constraint

**Source**  
Section 11: “A scope may be limited by... collection...”

**Requirement**  
A permission scope MAY be limited to one or more specified collections.

**Classification**  
Resource scope; collection boundary.

**Notes**  
Collection-level scoping is narrower than repository-wide access and broader than record-level access.

---

## REM-04-154 — Specific-record constraint

**Source**  
Section 11: “A scope may be limited by... specific record...”

**Requirement**  
A permission scope MAY be limited to one or more specific Relay Records.

**Classification**  
Resource scope; record-level authorisation.

**Notes**  
The stable Record URI provides the natural identifier for a record-level scope.

---

## REM-04-155 — Record-field constraint

**Source**  
Section 11: “A scope may be limited by... record field...”

**Requirement**  
A permission scope MAY be limited to specified fields within an otherwise accessible record.

**Classification**  
Field-level access; data minimisation.

**Notes**  
Field-level scoping allows an application to receive only the information required for its declared function.

---

## REM-04-156 — Action constraint

**Source**  
Section 11: “A scope may be limited by... action...”

**Requirement**  
A permission scope MAY be limited to specified actions.

**Classification**  
Action authorisation; least privilege.

**Notes**  
Read, create, update and delete authority must not be assumed to accompany one another.

---

## REM-04-157 — Audience constraint

**Source**  
Section 11: “A scope may be limited by... audience...”

**Requirement**  
A permission scope MAY be constrained by the audience or visibility context of the affected records.

**Classification**  
Audience; visibility; contextual access.

**Notes**  
For example, an application may be permitted to read public records without receiving access to restricted or private records.

---

## REM-04-158 — Time constraint

**Source**  
Section 11: “A scope may be limited by... time...”

**Requirement**  
A permission scope MAY be limited by a defined time period, start time, expiration time or other temporal condition.

**Classification**  
Temporal authorisation; grant duration.

**Notes**  
A time constraint may apply to the grant as a whole or to a specific capability within it.

---

## REM-04-159 — Purpose constraint

**Source**  
Section 11: “A scope may be limited by... purpose...”

**Requirement**  
A permission scope MAY limit authorised processing to one or more declared purposes.

**Classification**  
Purpose limitation; consent.

**Notes**  
Authority to perform an action does not necessarily authorise every possible use of the resulting data.

---

## REM-04-160 — Installation constraint

**Source**  
Section 11: “A scope may be limited by... application installation...”

**Requirement**  
A permission scope MAY be limited to a particular application installation.

**Classification**  
Installation-bound authority; device security.

**Notes**  
This permits separate authorisation decisions for different installations of the same Application Identity.

---

## REM-04-161 — Device constraint

**Source**  
Section 11: “A scope may be limited by... device...”

**Requirement**  
A permission scope MAY be limited to a specified device or device-bound credential.

**Classification**  
Device-bound authorisation; security.

**Notes**  
Device limitation does not redefine the stable Application Identity.

---

## REM-04-162 — Frequency constraint

**Source**  
Section 11: “A scope may be limited by... frequency...”

**Requirement**  
A permission scope MAY limit how frequently the application may perform an authorised action or access an authorised resource.

**Classification**  
Rate limitation; abuse prevention; contextual access.

**Notes**  
Frequency constraints may support privacy, cost, security or operational policies.

---

## REM-04-163 — Geographic or legal-context constraint

**Source**  
Section 11: “A scope may be limited by... geographic or legal context.”

**Requirement**  
A permission scope MAY be constrained by a specified geographic jurisdiction or legal context.

**Classification**  
Jurisdiction; policy enforcement; contextual authorisation.

**Notes**  
The protocol must represent the constraint without itself claiming to determine all applicable legal obligations.

---

## REM-04-164 — Comparative scope narrowness

**Source**  
Section 11 examples distinguish `Read public profile records` from `Read all repository records`, and `Update record post_123` from `Update all posts`.

**Requirement**  
Implementations MUST be able to represent and evaluate relative scope narrowness, including distinctions between public and all-record access and between individual-record and collection-wide authority.

**Classification**  
Scope comparison; least privilege; policy evaluation.

**Notes**  
This supports consent interfaces, automated policy checks and enforcement of grants that approve only the narrower request.

---

# 12. Resource scope

## REM-04-165 — Resource scope identifies accessible resources

**Source**  
Section 12: “A resource scope identifies what the application may access.”

**Requirement**  
Each resource scope MUST identify the resources that the application is authorised to access.

**Classification**  
Resource authorisation; access boundary.

**Notes**  
The resource scope is distinct from the action scope, which identifies what the application may do with those resources.

---

## REM-04-166 — Repository-wide resource scope

**Source**  
Section 12, Repository-wide: “Entire repository”.

**Requirement**  
The permission model MAY represent a repository-wide resource scope covering the entire repository.

**Classification**  
Repository-wide access; high sensitivity.

**Notes**  
The source permits the level but treats it as exceptional and sensitive.

---

## REM-04-167 — Repository-wide access should be rare

**Source**  
Section 12: “This should be rare and treated as highly sensitive.”

**Requirement**  
Repository-wide resource scopes SHOULD be granted only rarely.

**Classification**  
Least privilege; high-risk permission; recommendation.

**Notes**  
A narrower collection-, record-, field- or blob-level scope should be preferred where it can support the application’s purpose.

---

## REM-04-168 — Repository-wide access sensitivity

**Source**  
Section 12: “This should be rare and treated as highly sensitive.”

**Requirement**  
A repository-wide resource scope SHOULD be presented, reviewed and handled as highly sensitive authority.

**Classification**  
Consent UX; security; recommendation.

**Notes**  
The consent interface should not present repository-wide access as an ordinary content permission.

---

## REM-04-169 — Collection-level resource scope

**Source**  
Section 12, Collection-level example: `com.relay.post`.

**Requirement**  
The permission model MUST support resource scopes limited to a specified collection.

**Classification**  
Collection access; resource scope.

**Notes**  
A collection-level grant must not automatically extend to other collections in the repository.

---

## REM-04-170 — Record-level resource scope

**Source**  
Section 12, Record-level example: a specific Relay Record URI.

**Requirement**  
The permission model MUST support resource scopes limited to a specific Relay Record.

**Classification**  
Record-level access; least privilege.

**Notes**  
A record-level scope may be used for operations such as updating or displaying one identified object.

---

## REM-04-171 — Field-level resource scope

**Source**  
Section 12, Field-level example: “Profile display name and avatar only”.

**Requirement**  
The permission model MUST support resource scopes limited to specified record fields.

**Classification**  
Field-level access; data minimisation.

**Notes**  
An application receiving selected profile fields must not infer permission to read the remainder of the profile record.

---

## REM-04-172 — Blob-level resource scope

**Source**  
Section 12, Blob-level example: “Read and upload portfolio images”.

**Requirement**  
The permission model MUST support resource scopes limited to specified blobs or blob-related categories.

**Classification**  
Blob access; media permission.

**Notes**  
Blob authority should distinguish reading, uploading and attachment where those actions differ.

---

## REM-04-173 — Derived service-level resource scope

**Source**  
Section 12, Derived service-level example: “Receive public repository events”.

**Requirement**  
The permission model MUST support scopes for derived services or event streams that do not directly expose unrestricted repository content.

**Classification**  
Service-level access; events; derived data.

**Notes**  
A subscription to public repository events must not be treated as authority to read unrelated private repository state.

---

## REM-04-174 — Preference for the narrowest practical resource scope

**Source**  
Section 12: “The protocol should prefer the narrowest practical scope.”

**Requirement**  
The protocol and consent interfaces SHOULD prefer the narrowest practical resource scope capable of supporting the declared application purpose.

**Classification**  
Least privilege; data minimisation; recommendation.

**Notes**  
Practicality permits a broader scope where narrower representation would make the intended function infeasible, but convenience alone should not justify unnecessary access.

---

# 13. Action scope

## REM-04-175 — Grant must identify allowed actions

**Source**  
Section 13: “A grant must identify allowed actions.”

**Requirement**  
Every Permission Grant MUST explicitly identify the actions the application is authorised to perform.

**Classification**  
Action authorisation; grant completeness.

**Notes**  
Absence of an action from the grant must not be interpreted as implicit authority to perform it.

---

## REM-04-176 — Discover action

**Source**  
Section 13, required v0.1 action distinction: `discover`.

**Requirement**  
Relay v0.1 SHOULD distinguish `discover` as an independently grantable action.

**Classification**  
Action vocabulary; discovery; recommendation.

**Notes**  
Discovery may reveal the existence or metadata of resources without granting full read access.

---

## REM-04-177 — Read action

**Source**  
Section 13: `read`.

**Requirement**  
Relay v0.1 SHOULD distinguish `read` as an independently grantable action.

**Classification**  
Action vocabulary; read access; recommendation.

**Notes**  
The exact content states available under read authority are further constrained by Section 14.

---

## REM-04-178 — List action

**Source**  
Section 13: `list`.

**Requirement**  
Relay v0.1 SHOULD distinguish `list` as an independently grantable action.

**Classification**  
Action vocabulary; collection enumeration; recommendation.

**Notes**  
Authority to read one known record must not automatically imply authority to enumerate all records in a collection.

---

## REM-04-179 — Create action

**Source**  
Section 13: `create`.

**Requirement**  
Relay v0.1 SHOULD distinguish `create` as an independently grantable action.

**Classification**  
Action vocabulary; record creation; recommendation.

**Notes**  
Creation authority may still be limited by schema, collection, publication state and purpose.

---

## REM-04-180 — Update action

**Source**  
Section 13: `update`.

**Requirement**  
Relay v0.1 SHOULD distinguish `update` as an independently grantable action.

**Classification**  
Action vocabulary; record update; recommendation.

**Notes**  
Update authority must not be inferred from create authority.

---

## REM-04-181 — Delete action

**Source**  
Section 13: `delete`.

**Requirement**  
Relay v0.1 SHOULD distinguish `delete` as an independently grantable action.

**Classification**  
Action vocabulary; destructive operation; recommendation.

**Notes**  
Deletion is materially more destructive than ordinary content creation or editing and should be separately visible in consent.

---

## REM-04-182 — Restore action

**Source**  
Section 13: `restore`.

**Requirement**  
Relay v0.1 SHOULD distinguish `restore` as an independently grantable action.

**Classification**  
Action vocabulary; restoration; recommendation.

**Notes**  
Restore authority applies only where the schema and repository state permit restoration.

---

## REM-04-183 — Upload-blob action

**Source**  
Section 13: `upload-blob`.

**Requirement**  
Relay v0.1 SHOULD distinguish `upload-blob` as an independently grantable action.

**Classification**  
Action vocabulary; blob storage; recommendation.

**Notes**  
Uploading a blob does not necessarily grant authority to attach it to a canonical record.

---

## REM-04-184 — Attach-blob action

**Source**  
Section 13: `attach-blob`.

**Requirement**  
Relay v0.1 SHOULD distinguish `attach-blob` as an independently grantable action.

**Classification**  
Action vocabulary; record association; recommendation.

**Notes**  
Attachment may change record content or metadata and therefore may require update authority in addition to blob access.

---

## REM-04-185 — Change-visibility action

**Source**  
Section 13: `change-visibility`.

**Requirement**  
Relay v0.1 SHOULD distinguish `change-visibility` as an independently grantable action.

**Classification**  
Action vocabulary; visibility control; recommendation.

**Notes**  
Content-editing authority must not automatically include authority to make a record public, restricted or private.

---

## REM-04-186 — Change-audience action

**Source**  
Section 13: `change-audience`.

**Requirement**  
Relay v0.1 SHOULD distinguish `change-audience` as an independently grantable action.

**Classification**  
Action vocabulary; audience control; recommendation.

**Notes**  
Audience changes can expose or revoke access for other identities and therefore require explicit authority.

---

## REM-04-187 — Subscribe-events action

**Source**  
Section 13: `subscribe-events`.

**Requirement**  
Relay v0.1 SHOULD distinguish `subscribe-events` as an independently grantable action.

**Classification**  
Action vocabulary; event subscriptions; recommendation.

**Notes**  
Event subscriptions may provide continuous access and should be distinguished from one-time interactive reads.

---

## REM-04-188 — Export action

**Source**  
Section 13: `export`.

**Requirement**  
Relay v0.1 SHOULD distinguish `export` as an independently grantable action.

**Classification**  
Action vocabulary; data portability; recommendation.

**Notes**  
Export authority may involve bulk access and external retention beyond ordinary record viewing.

---

## REM-04-189 — Import action

**Source**  
Section 13: `import`.

**Requirement**  
Relay v0.1 SHOULD distinguish `import` as an independently grantable action.

**Classification**  
Action vocabulary; data import; recommendation.

**Notes**  
Import authority may create multiple records and must remain subject to schema and repository validation.

---

## REM-04-190 — Migrate action

**Source**  
Section 13: `migrate`.

**Requirement**  
Relay v0.1 SHOULD distinguish `migrate` as an independently grantable high-authority action.

**Classification**  
Action vocabulary; migration; high authority; recommendation.

**Notes**  
Migration may affect the repository provider, operational continuity and broad repository state.

---

## REM-04-191 — Manage-permissions action

**Source**  
Section 13: `manage-permissions`.

**Requirement**  
Relay v0.1 SHOULD distinguish `manage-permissions` as an independently grantable high-authority action.

**Classification**  
Action vocabulary; permission administration; high authority.

**Notes**  
An application with this authority may alter access granted to itself or others, depending on the exact scope.

---

## REM-04-192 — Manage-keys action

**Source**  
Section 13: `manage-keys`.

**Requirement**  
Relay v0.1 SHOULD distinguish `manage-keys` as an independently grantable high-authority action.

**Classification**  
Action vocabulary; cryptographic authority; high authority.

**Notes**  
Key management can affect identity and repository authority and therefore requires heightened consent and enforcement.

---

## REM-04-193 — Manage-recovery action

**Source**  
Section 13: `manage-recovery`.

**Requirement**  
Relay v0.1 SHOULD distinguish `manage-recovery` as an independently grantable high-authority action.

**Classification**  
Action vocabulary; recovery authority; high authority.

**Notes**  
Recovery authority may affect the user’s ability to regain or retain control of their identity.

---

## REM-04-194 — Separation of high-authority actions

**Source**  
Section 13: “High-authority actions such as migrate, manage-keys, manage-recovery, manage-permissions must not be bundled with ordinary content access.”

**Requirement**  
High-authority actions, including migration, key management, recovery management and permission management, MUST NOT be bundled into ordinary content-access permissions.

**Classification**  
Privilege separation; high-risk authorisation; consent.

**Notes**  
These actions require separate, explicit approval and must remain independently revocable where the protocol supports granular revocation.

---

# 14. Read access

## REM-04-195 — Read access to current content

**Source**  
Section 14: “Read access may apply to: current record content...”

**Requirement**  
A Permission Grant MAY authorise reading the current content of records within its resource scope.

**Classification**  
Read access; current state.

**Notes**  
Current-content authority does not by itself include historical-version access.

---

## REM-04-196 — Read access to historical versions

**Source**  
Section 14: “Read access may apply to... historical versions...”

**Requirement**  
A Permission Grant MAY separately authorise reading historical record versions.

**Classification**  
Read access; history; sensitive data.

**Notes**  
Historical versions may contain superseded, deleted or previously private information and therefore require explicit distinction.

---

## REM-04-197 — Metadata-only read access

**Source**  
Section 14: “Read access may apply to... metadata only...”

**Requirement**  
A Permission Grant MAY limit read access to record metadata without granting access to record content.

**Classification**  
Read access; metadata; data minimisation.

**Notes**  
Metadata-only access may support discovery, indexing or synchronisation use cases.

---

## REM-04-198 — Blob read access

**Source**  
Section 14: “Read access may apply to... blobs...”

**Requirement**  
A Permission Grant MAY separately authorise reading blobs associated with accessible records.

**Classification**  
Read access; blobs; media.

**Notes**  
Authority to read record metadata or content must not automatically imply authority to retrieve every associated blob.

---

## REM-04-199 — Provenance read access

**Source**  
Section 14: “Read access may apply to... provenance...”

**Requirement**  
A Permission Grant MAY separately authorise access to structured record provenance.

**Classification**  
Read access; provenance; transparency.

**Notes**  
Provenance may reveal source services, transformation systems, migration details or application activity not contained in the primary record content.

---

## REM-04-200 — Restricted-content read access

**Source**  
Section 14: “Read access may apply to... restricted content...”

**Requirement**  
A Permission Grant MAY authorise reading restricted content only where the grant and underlying audience or access rules permit it.

**Classification**  
Read access; restricted data; audience enforcement.

**Notes**  
General read authority over public records must not be interpreted as access to restricted records.

---

## REM-04-201 — Private-content read access

**Source**  
Section 14: “Read access may apply to... private content.”

**Requirement**  
A Permission Grant MAY authorise reading private content only through an explicit scope that identifies or includes private access.

**Classification**  
Read access; private data; high sensitivity.

**Notes**  
Private-content authority should receive heightened consent treatment because it exceeds ordinary public or restricted access.

---

## REM-04-202 — Grant must distinguish read-access categories

**Source**  
Section 14: “The grant must distinguish these.”

**Requirement**  
A Permission Grant MUST distinguish among current content, historical versions, metadata, blobs, provenance, restricted content and private content where any of those categories are requested.

**Classification**  
Grant precision; read scope; least privilege.

**Notes**  
A single undifferentiated `read` label is insufficient where materially different data states or sensitivity levels are involved.

---

## REM-04-203 — Public-current read does not imply private-history read

**Source**  
Section 14: “Read current public posts must not automatically permit: Read deleted versions of private posts.”

**Requirement**  
Authority to read current public records MUST NOT automatically grant authority to read deleted, historical or private versions of records.

**Classification**  
Privilege separation; read access; privacy.

**Notes**  
This is a concrete application of the requirement to distinguish data state, visibility and historical access.

---

# 15. Write access

## REM-04-204 — Distinction between record creation and other write actions

**Source**  
Section 15: “Write access must distinguish between: creating new records...”

**Requirement**  
Write authority MUST distinguish permission to create new records from other forms of write access.

**Classification**  
Write access; record creation; least privilege.

**Notes**  
Create authority does not automatically include update, deletion, publication or visibility authority.

---

## REM-04-205 — Distinction for updating existing records

**Source**  
Section 15: “Write access must distinguish between... updating existing records...”

**Requirement**  
Write authority MUST separately identify permission to update existing records.

**Classification**  
Write access; record update.

**Notes**  
Update authority may be further limited to specific fields, records or metadata categories.

---

## REM-04-206 — Distinction for deleting records

**Source**  
Section 15: “Write access must distinguish between... deleting records...”

**Requirement**  
Write authority MUST separately identify permission to delete records.

**Classification**  
Write access; destructive operation.

**Notes**  
Deletion authority must not be inferred from create or update authority.

---

## REM-04-207 — Distinction for changing visibility

**Source**  
Section 15: “Write access must distinguish between... changing visibility...”

**Requirement**  
Write authority MUST separately identify permission to change record visibility.

**Classification**  
Write access; visibility control.

**Notes**  
Changing content and changing who may access that content are separate operations.

---

## REM-04-208 — Distinction for changing rights

**Source**  
Section 15: “Write access must distinguish between... changing rights...”

**Requirement**  
Write authority MUST separately identify permission to change structured usage-rights declarations.

**Classification**  
Write access; rights management.

**Notes**  
Permission to edit record text must not be interpreted as permission to alter licensing, model-training or redistribution terms.

---

## REM-04-209 — Distinction for submitting drafts

**Source**  
Section 15: “Write access must distinguish between... submitting drafts...”

**Requirement**  
Write authority MUST separately identify permission to create or submit draft records.

**Classification**  
Write access; draft lifecycle.

**Notes**  
A draft may remain local or repository-supported without becoming a published canonical record.

---

## REM-04-210 — Distinction for publishing canonical records

**Source**  
Section 15: “Write access must distinguish between... publishing canonical records.”

**Requirement**  
Write authority MUST separately identify permission to publish or commit a record as canonical repository state.

**Classification**  
Write access; publication; canonical state.

**Notes**  
Publication causes repository acceptance and may have visibility, provenance and audit consequences beyond draft creation.

---

## REM-04-211 — Draft creation does not imply publication authority

**Source**  
Section 15: “An application allowed to create a draft should not automatically be allowed to publish it.”

**Requirement**  
Permission to create or edit a draft SHOULD NOT automatically grant permission to publish that draft as a canonical record.

**Classification**  
Privilege separation; draft workflow; recommendation.

**Notes**  
A separate user action or grant may be required before publication.

---

## REM-04-212 — Text update does not imply public-visibility authority

**Source**  
Section 15: “An application allowed to update the text of a record should not automatically be allowed to make it public.”

**Requirement**  
Permission to update a record’s text SHOULD NOT automatically grant permission to change the record’s visibility to public.

**Classification**  
Privilege separation; visibility; recommendation.

**Notes**  
The application may retain text-editing authority while visibility remains controlled by the user or another narrowly authorised workflow.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 11–15 of `design-notes/04-application-and-permission-model.md`.
- Sections 16 onward were excluded.
- Examples were used only to clarify scope relationships and were not treated as final syntax requirements.

## Numbering verification

- First requirement: `REM-04-149`.
- Final requirement: `REM-04-212`.
- Numbering continues directly from Part 2.
- Requirement identifiers are continuous and unique.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each resource and action category was extracted independently where it creates a separately testable permission boundary.
- The Section 13 action list was preserved as a recommended v0.1 distinction because the source uses `should distinguish`.
- Mandatory separation of high-authority operations was retained as `MUST NOT`.

## Normative-language verification

- Source `must` statements are represented as `MUST` or `MUST NOT`.
- Source `should` statements are preserved as `SHOULD` or `SHOULD NOT` recommendations.
- Source `may` statements remain optional capabilities expressed as `MAY`.
- Definitions were made testable without strengthening optional source language.

## Editorial verification

- Resource scope remains distinct from action scope.
- Repository-wide authority is permitted but explicitly treated as rare and highly sensitive.
- Read access distinguishes current content, history, metadata, blobs, provenance and visibility classes.
- Draft authority remains separate from publication authority.
- Content editing remains separate from visibility and rights management.
- High-authority actions remain separate from ordinary content permissions.
