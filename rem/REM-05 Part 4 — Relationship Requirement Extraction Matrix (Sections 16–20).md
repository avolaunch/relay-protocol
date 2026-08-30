# REM-05 Part 4 — Relationship Requirement Extraction Matrix (Sections 16–20)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 16–20 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

16. Subscriptions
17. Followers and audiences
18. Private relationships
19. Visibility
20. Relationship context

Requirement identifiers continue sequentially from Part 3, beginning with `REM-05-152`.

---

# 16. Subscriptions

## REM-05-152 — Subscription as a directed relationship

**Source**  
Section 16: “A subscription is a directed relationship requesting delivery of a defined category of activity.”

**Requirement**  
A subscription MUST be represented as a directed relationship from a source to a target.

**Classification**  
Relationship semantics; direction; subscription model.

**Notes**  
The target is not required to create a reciprocal subscription record.

---

## REM-05-153 — Subscription requests defined activity delivery

**Source**  
Section 16: “A subscription is a directed relationship requesting delivery of a defined category of activity.”

**Requirement**  
A subscription MUST identify or permit identification of the category of activity whose delivery is requested.

**Classification**  
Delivery request; semantic scope; subscription model.

**Notes**  
A subscription is more specific than an undifferentiated request to receive all target activity where filters are supplied.

---

## REM-05-154 — Subscription may be more specific than a follow

**Source**  
Section 16: “A subscription may be more specific than a follow.”

**Requirement**  
A subscription MAY apply narrower activity, content or delivery criteria than a follow relationship.

**Classification**  
Relationship distinction; filtering; extensibility.

**Notes**  
Applications must not assume that follow and subscription records are semantically interchangeable.

---

## REM-05-155 — Collection filtering

**Source**  
Section 16: “A subscription may specify: collections...”

**Requirement**  
A subscription MAY restrict requested delivery to one or more specified record collections.

**Classification**  
Subscription filter; collection scope.

**Notes**  
The source example requests article and project collections.

---

## REM-05-156 — Topic filtering

**Source**  
Section 16: “A subscription may specify: ... topics...”

**Requirement**  
A subscription MAY restrict requested delivery to specified topics.

**Classification**  
Subscription filter; topic scope.

**Notes**  
Topic interpretation should be schema-defined or otherwise machine-readable where interoperability is required.

---

## REM-05-157 — Event-type filtering

**Source**  
Section 16: “A subscription may specify: ... event types...”

**Requirement**  
A subscription MAY restrict requested delivery to specified event types.

**Classification**  
Subscription filter; event scope.

**Notes**  
Event-type filtering may distinguish creation, update, publication or other supported activity classes.

---

## REM-05-158 — Delivery-method preference

**Source**  
Section 16: “A subscription may specify: ... delivery method...”

**Requirement**  
A subscription MAY declare a requested delivery method.

**Classification**  
Delivery preference; subscription behaviour.

**Notes**  
The source example uses feed delivery. A requested method is not necessarily guaranteed by the target.

---

## REM-05-159 — Frequency preference

**Source**  
Section 16: “A subscription may specify: ... frequency...”

**Requirement**  
A subscription MAY declare a requested delivery frequency.

**Classification**  
Delivery preference; scheduling.

**Notes**  
Frequency may represent immediate, periodic, digest or another schema-defined mode.

---

## REM-05-160 — Language preference

**Source**  
Section 16: “A subscription may specify: ... language...”

**Requirement**  
A subscription MAY declare one or more language preferences.

**Classification**  
Delivery preference; localisation.

**Notes**  
Language preference should not be interpreted as a guarantee that matching content exists.

---

## REM-05-161 — Priority preference

**Source**  
Section 16: “A subscription may specify: ... priority.”

**Requirement**  
A subscription MAY declare a requested priority.

**Classification**  
Delivery preference; prioritisation.

**Notes**  
The receiving or delivery service may apply its own supported priority model.

---

## REM-05-162 — Requested delivery is not guaranteed

**Source**  
Section 16: “The target is not required to provide every requested delivery method.”

**Requirement**  
A subscription request MUST NOT be interpreted as obligating the target to provide every requested delivery method.

**Classification**  
Target autonomy; delivery semantics; non-guarantee.

**Notes**  
Applications should distinguish the subscriber’s preference from the target’s supported delivery capabilities.

---

# 17. Followers and audiences

## REM-05-163 — Followers not represented only as a provider counter

**Source**  
Section 17: “A person’s followers should not be represented only as a provider-maintained counter.”

**Requirement**  
A compliant relationship implementation SHOULD NOT represent a person’s followers solely as a provider-maintained numeric counter.

**Classification**  
Graph integrity; portability; recommendation.

**Notes**  
A provider counter alone does not preserve the underlying portable relationship graph.

---

## REM-05-164 — Follower count is derived

**Source**  
Section 17: “The count is a derived value.”

**Requirement**  
A follower count MUST be treated as a derived value rather than as the canonical relationship data itself.

**Classification**  
Derived data; graph semantics; indexing.

**Notes**  
Canonical follower relationships remain the underlying relationship records.

---

## REM-05-165 — Distributed follower graph

**Source**  
Section 17: “The underlying graph consists of relationship records distributed across follower repositories.”

**Requirement**  
The follower graph MUST be understood as relationship records distributed across the repositories of the follower identities.

**Classification**  
Distributed graph; repository authority; portability.

**Notes**  
The followed identity’s repository need not contain canonical copies of all incoming follow declarations.

---

## REM-05-166 — Follower index support

**Source**  
Section 17: “A service may build an index showing: ‘Bob has 20,000 known active followers.’”

**Requirement**  
A service MAY build an index or derived count of known active follower relationships.

**Classification**  
Indexing; derived service; discovery.

**Notes**  
The index does not replace the authoritative distributed relationship records.

---

## REM-05-167 — Indexed-repository dependency

**Source**  
Section 17: “That count depends on: indexed repositories...”

**Requirement**  
A derived follower count MUST account for or disclose that its coverage depends on which repositories have been indexed.

**Classification**  
Index coverage; completeness; derived data.

**Notes**  
Unindexed repositories can cause undercounting.

---

## REM-05-168 — Visibility dependency

**Source**  
Section 17: “That count depends on: ... relationship visibility...”

**Requirement**  
A derived follower count MUST account for the visibility of the underlying relationship records.

**Classification**  
Visibility; count completeness; privacy.

**Notes**  
Private or restricted follow relationships may be unavailable to a public index.

---

## REM-05-169 — Block-rule dependency

**Source**  
Section 17: “That count depends on: ... block rules...”

**Requirement**  
A derived follower count MUST account for applicable block rules where those rules affect inclusion or disclosure.

**Classification**  
Blocking; derived graph; audience calculation.

**Notes**  
Different authorised viewers may receive different effective counts.

---

## REM-05-170 — Unavailable-identity dependency

**Source**  
Section 17: “That count depends on: ... unavailable identities...”

**Requirement**  
A derived follower count MUST account for identities that cannot currently be resolved or reached.

**Classification**  
Resolution; count reliability; availability.

**Notes**  
Unavailable does not necessarily mean deleted or invalid.

---

## REM-05-171 — Revoked-record dependency

**Source**  
Section 17: “That count depends on: ... revoked records...”

**Requirement**  
A derived active-follower count MUST exclude or appropriately classify revoked follow records.

**Classification**  
Revocation; count accuracy; relationship status.

**Notes**  
Historical counts may apply different inclusion rules if clearly labelled.

---

## REM-05-172 — Index-freshness dependency

**Source**  
Section 17: “That count depends on: ... index freshness.”

**Requirement**  
A derived follower count MUST account for the freshness of the index from which it was calculated.

**Classification**  
Index freshness; synchronisation; derived data.

**Notes**  
A stale index may include ended relationships or omit newly created ones.

---

## REM-05-173 — No false precision or completeness

**Source**  
Section 17: “Applications must not present derived counts as more precise or complete than their data permits.”

**Requirement**  
An application MUST NOT present a derived follower or audience count as more precise or complete than the underlying indexed data permits.

**Classification**  
Presentation integrity; derived data; user disclosure.

**Notes**  
Qualifiers such as “known”, “indexed” or “estimated” may be necessary.

---

# 18. Private relationships

## REM-05-174 — Relationships need not be public

**Source**  
Section 18: “Not every relationship should be public.”

**Requirement**  
The Relationship Model SHOULD support relationships that are not publicly visible.

**Classification**  
Privacy; visibility; recommendation.

**Notes**  
Relationship portability must not require public disclosure of sensitive graph information.

---

## REM-05-175 — Private friendship support

**Source**  
Section 18, examples: “friendship”.

**Requirement**  
The model MAY represent friendship as a private relationship.

**Classification**  
Private relationship; social graph.

**Notes**  
The example is illustrative rather than an exhaustive schema mandate.

---

## REM-05-176 — Private family-connection support

**Source**  
Section 18, examples: “family connection”.

**Requirement**  
The model MAY represent family connections as private relationships.

**Classification**  
Private relationship; sensitive data.

**Notes**  
Family relationships may create heightened privacy and safety risks.

---

## REM-05-177 — Private collaboration support

**Source**  
Section 18, examples: “private collaboration”.

**Requirement**  
The model MAY represent collaborations whose existence or details are private.

**Classification**  
Private relationship; collaboration.

**Notes**  
A private collaboration remains distinct from a public collaborator declaration.

---

## REM-05-178 — Private trusted-contact support

**Source**  
Section 18, examples: “trusted contact”.

**Requirement**  
The model MAY represent trusted-contact relationships privately.

**Classification**  
Private relationship; trust; security.

**Notes**  
Trusted-contact relationships may have security or recovery implications and should not be exposed by default.

---

## REM-05-179 — Private professional-relationship support

**Source**  
Section 18, examples: “client relationship; medical or legal relationship”.

**Requirement**  
The model MAY represent client, medical and legal relationships privately.

**Classification**  
Private relationship; professional confidentiality; sensitive data.

**Notes**  
The existence of such a relationship may itself be sensitive.

---

## REM-05-180 — Private sensitive-group membership support

**Source**  
Section 18, examples: “membership in a sensitive group.”

**Requirement**  
The model MAY represent membership in a sensitive group as a private relationship.

**Classification**  
Private relationship; group membership; sensitive data.

**Notes**  
Sensitive-group membership must not be inferred as publicly visible merely because the group itself is public.

---

## REM-05-181 — Protection of private target identity

**Source**  
Section 18: “A private relationship record should not expose its target or meaning to unauthorised observers.”

**Requirement**  
A private relationship record SHOULD NOT expose its target identity to an unauthorised observer.

**Classification**  
Confidentiality; target protection; recommendation.

**Notes**  
Metadata leakage may reveal the relationship even where content is encrypted.

---

## REM-05-182 — Protection of private relationship meaning

**Source**  
Section 18: “A private relationship record should not expose its target or meaning to unauthorised observers.”

**Requirement**  
A private relationship record SHOULD NOT expose the semantic meaning or type of the relationship to an unauthorised observer.

**Classification**  
Confidentiality; semantic privacy; recommendation.

**Notes**  
Protecting only the target while disclosing the relationship type may still reveal sensitive information.

---

## REM-05-183 — Restricted record access option

**Source**  
Section 18, possible implementations: “restricted record access”.

**Requirement**  
An implementation MAY protect private relationships through restricted record access.

**Classification**  
Privacy mechanism; access control.

**Notes**  
Relay v0.1 may use this as an initial implementation approach.

---

## REM-05-184 — Encrypted relationship-record option

**Source**  
Section 18, possible implementations: “encrypted relationship records”.

**Requirement**  
An implementation MAY protect private relationships through encrypted relationship records.

**Classification**  
Privacy mechanism; encryption.

**Notes**  
The source does not define the encryption architecture in this section.

---

## REM-05-185 — Opaque audience-identifier option

**Source**  
Section 18, possible implementations: “opaque audience identifiers”.

**Requirement**  
An implementation MAY use opaque audience identifiers to reduce disclosure of private relationship audiences.

**Classification**  
Privacy mechanism; audience protection.

**Notes**  
Opaque identifiers should not be reversibly exposed to unauthorised observers through supporting metadata.

---

## REM-05-186 — Separate private repository option

**Source**  
Section 18, possible implementations: “separately stored private relationship repositories.”

**Requirement**  
An implementation MAY store private relationships in a separate private relationship repository.

**Classification**  
Privacy architecture; repository separation.

**Notes**  
Separation must preserve authorised portability and repository authority.

---

## REM-05-187 — Provisional v0.1 privacy scope

**Source**  
Section 18: “Relay v0.1 may initially support restricted relationship records while deferring advanced private graph protection to a later version.”

**Requirement**  
Relay v0.1 MAY initially implement private relationships using restricted relationship records and defer advanced private-graph protections.

**Classification**  
Version scope; implementation phasing; privacy.

**Notes**  
Deferral does not permit restricted records to be exposed contrary to their access rules.

---

# 19. Visibility

## REM-05-188 — Public relationship visibility

**Source**  
Section 19, visibility values: “public”.

**Requirement**  
The Relationship Model MAY support public relationship visibility.

**Classification**  
Visibility classification; public access.

**Notes**  
Public visibility remains subject to schema and applicable policy.

---

## REM-05-189 — Unlisted relationship visibility

**Source**  
Section 19, visibility values: “unlisted”.

**Requirement**  
The Relationship Model MAY support unlisted relationship visibility.

**Classification**  
Visibility classification; discovery limitation.

**Notes**  
Unlisted should be distinguished from private; an authorised direct resolver may still access the relationship.

---

## REM-05-190 — Restricted relationship visibility

**Source**  
Section 19, visibility values: “restricted”.

**Requirement**  
The Relationship Model MAY support restricted relationship visibility.

**Classification**  
Visibility classification; audience control.

**Notes**  
Restricted visibility requires an authorised audience or access rule.

---

## REM-05-191 — Private relationship visibility

**Source**  
Section 19, visibility values: “private”.

**Requirement**  
The Relationship Model MAY support private relationship visibility.

**Classification**  
Visibility classification; confidentiality.

**Notes**  
Private visibility may require stronger protection than ordinary restricted disclosure.

---

## REM-05-192 — Separate visibility of relationship existence

**Source**  
Section 19: “Visibility may apply separately to: existence of the relationship...”

**Requirement**  
The model MAY control disclosure of the existence of a relationship independently from disclosure of its other fields.

**Classification**  
Selective disclosure; existence privacy.

**Notes**  
An observer may be authorised to know that a relationship exists without seeing its type or context.

---

## REM-05-193 — Separate visibility of relationship type

**Source**  
Section 19: “Visibility may apply separately to: ... relationship type...”

**Requirement**  
The model MAY control disclosure of the relationship type independently from the existence and other details of the relationship.

**Classification**  
Selective disclosure; semantic privacy.

**Notes**  
The type may be more sensitive than the fact that some relationship exists.

---

## REM-05-194 — Separate visibility of target identity

**Source**  
Section 19: “Visibility may apply separately to: ... target identity...”

**Requirement**  
The model MAY control disclosure of the target identity independently from other relationship information.

**Classification**  
Selective disclosure; target privacy.

**Notes**  
A record may reveal a role or membership while withholding the specific target in some use cases.

---

## REM-05-195 — Separate visibility of context

**Source**  
Section 19: “Visibility may apply separately to: ... context...”

**Requirement**  
The model MAY control disclosure of relationship context independently from the relationship’s existence or general type.

**Classification**  
Selective disclosure; contextual privacy.

**Notes**  
Internal role, project or organisational context may require narrower access.

---

## REM-05-196 — Separate visibility of dates

**Source**  
Section 19: “Visibility may apply separately to: ... dates...”

**Requirement**  
The model MAY control disclosure of relationship dates independently from other relationship fields.

**Classification**  
Selective disclosure; temporal privacy.

**Notes**  
Dates may reveal employment history, membership periods or personal circumstances.

---

## REM-05-197 — Separate visibility of evidence

**Source**  
Section 19: “Visibility may apply separately to: ... associated evidence.”

**Requirement**  
The model MAY control disclosure of associated evidence independently from the relationship declaration itself.

**Classification**  
Selective disclosure; evidence confidentiality.

**Notes**  
A relationship may be publicly asserted while supporting credentials remain restricted.

---

## REM-05-198 — Public membership with private internal details

**Source**  
Section 19 example: publicly disclose “Member of Organisation Z” without exposing “Internal role or membership number”.

**Requirement**  
The model SHOULD permit a relationship to disclose a public high-level statement while withholding more sensitive internal details.

**Classification**  
Selective disclosure; data minimisation; recommendation.

**Notes**  
This requirement illustrates field-level visibility rather than requiring this exact organisation schema.

---

## REM-05-199 — Schema support for selective disclosure

**Source**  
Section 19: “The schema should support selective disclosure where needed.”

**Requirement**  
A relationship schema SHOULD support selective disclosure where its fields have materially different visibility requirements.

**Classification**  
Schema design; selective disclosure; recommendation.

**Notes**  
Selective disclosure should be explicit rather than inferred from application presentation alone.

---

# 20. Relationship context

## REM-05-200 — Contextual relationship support

**Source**  
Section 20: “A relationship may exist within a defined context.”

**Requirement**  
A relationship MAY be scoped to a defined context.

**Classification**  
Context modelling; relationship scope.

**Notes**  
Context can prevent a narrow relationship from being interpreted as universal.

---

## REM-05-201 — Project context support

**Source**  
Section 20, example: “collaborator on Project X”.

**Requirement**  
A relationship MAY identify a project record as its context.

**Classification**  
Project relationship; context modelling.

**Notes**  
The source example also includes a context-specific role.

---

## REM-05-202 — Organisation context support

**Source**  
Section 20, example: “member of Organisation Z”.

**Requirement**  
A relationship MAY identify an organisation as its context.

**Classification**  
Organisational relationship; context modelling.

**Notes**  
Organisation membership does not necessarily imply membership in unrelated organisations or groups.

---

## REM-05-203 — Content-category context support

**Source**  
Section 20, example: “subscriber to Photography posts”.

**Requirement**  
A relationship MAY be scoped to a content category or topic.

**Classification**  
Subscription context; content scope.

**Notes**  
This enables multiple subscriptions to the same target with different filters.

---

## REM-05-204 — Temporal employment context support

**Source**  
Section 20, example: “employee during 2024–2026”.

**Requirement**  
A relationship MAY include a temporal context limiting when it applies.

**Classification**  
Temporal context; employment relationship.

**Notes**  
Detailed validity-period requirements are addressed in Section 21.

---

## REM-05-205 — Community context support

**Source**  
Section 20, example: “moderator of Community Q”.

**Requirement**  
A role-bearing relationship MAY be scoped to a specific community or group context.

**Classification**  
Community role; authority context.

**Notes**  
A moderator relationship in one community must not imply moderation authority elsewhere.

---

## REM-05-206 — Context record reference

**Source**  
Section 20 example: `"record": "relay://.../project_42"`.

**Requirement**  
Where the context is a Relay Record, the relationship MAY identify that context using the record’s stable Record URI.

**Classification**  
Record reference; context identification; portability.

**Notes**  
Temporary application or provider URLs should not replace the stable Record URI.

---

## REM-05-207 — Context-specific role

**Source**  
Section 20 example: `"role": "designer"`.

**Requirement**  
A contextual relationship MAY identify the role held by the source or target within that context.

**Classification**  
Role modelling; contextual semantics.

**Notes**  
The applicable schema should define whose role is represented and the role vocabulary.

---

## REM-05-208 — Multiple contextual relationships between the same identities

**Source**  
Section 20: “The same two identities may have multiple relationships in different contexts.”

**Requirement**  
The model MUST permit the same two identities to hold multiple distinct relationships in different contexts.

**Classification**  
Cardinality; contextual graph; relationship identity.

**Notes**  
Applications must not merge contextual relationships merely because their source and target match.

---

## REM-05-209 — No global inference from context-specific relationship

**Source**  
Section 20: “A global relationship should not be inferred from a context-specific one.”

**Requirement**  
An application SHOULD NOT infer a global relationship from a relationship that is explicitly limited to a particular context.

**Classification**  
Inference limitation; context integrity; recommendation.

**Notes**  
For example, collaboration on one project does not establish a general collaborator relationship across all work.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 16–20 of `design-notes/05-relationship-model.md`.
- Sections 21 onward were excluded as independent requirements.
- Examples were used to clarify permitted structures and were not converted into closed vocabularies.

## Numbering verification

- First requirement: `REM-05-152`.
- Final requirement: `REM-05-209`.
- Numbering continues directly from Part 3.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, example or necessary decomposition of a compound statement.
- Subscription options, follower-count dependencies, visibility dimensions and context examples were separated where they impose independently testable semantics.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements remain `SHOULD` recommendations.
- Source “may” statements remain `MAY` permissions.
- Descriptive definitions were normalised only where necessary to make protocol behaviour testable.

## Editorial verification

- A subscription remains a request and does not create a target delivery obligation.
- Follower counts remain derived, qualified index outputs rather than canonical graph records.
- Private relationships protect both target identity and semantic meaning where required.
- Visibility dimensions remain independently controllable.
- Context-specific relationships are not promoted into global relationships.
