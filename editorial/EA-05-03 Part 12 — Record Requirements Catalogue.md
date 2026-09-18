# EA-05-03 — Record Requirements Catalogue

## Part 12 — Restricted Audiences, Dynamic Evaluation and Access Revocation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how restricted records may identify intended audiences, how changing relationship-based audiences determine access, how later audience membership may affect earlier records and what audience removal can and cannot revoke.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 15 and REM-03 requirements `REM-03-152` through `REM-03-165`.

It defines normative requirements governing:

- optional structured audience rules for restricted records;
- permitted identity-, application-, relationship-, group-, grant- and other rule-based audiences;
- required evaluation semantics for audiences based on changing relationships;
- permitted publication-time, access-time and alternative evaluation rules;
- schema- or record-defined treatment of later audience membership;
- revocation of future authorised access after audience removal; and
- the inability of revocation to guarantee deletion of copies already received.

Source Section 16 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-152` through `REM-03-158` are consolidated because the source introduces one permission to identify an intended audience and then enumerates six permitted audience bases. `REM-03-160` through `REM-03-162` are consolidated because the source permits three alternative dynamic-audience evaluation approaches. Every audience basis and evaluation approach remains explicit and individually traceable.

The audience examples in Section 15 are illustrative. They do not establish mandatory rules, default audience semantics, physical field names, schema vocabulary or final access-control syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-083

### Title

Restricted Record Audience Declaration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A restricted record **MAY** identify its intended audience through structured audience rules using:

- specific Relay Identities;
- approved applications;
- relationship-based groups;
- named access groups;
- valid permission grants; or
- another explicitly defined access rule supported by the applicable schema or protocol.

### Rationale

Multiple optional audience bases allow restricted access to be expressed for different identity, application, relationship, group and permission contexts without requiring every record to use every basis or prescribing their resolution mechanisms.

### Source

- REM-03-152
- REM-03-153
- REM-03-154
- REM-03-155
- REM-03-156
- REM-03-157
- REM-03-158
- `design-notes/03-record-model.md`, Section 15

### Related Invariants

- CI-02
- CI-06
- CI-12
- AI-07

---

## REL-REC-084

### Title

Dynamic Audience Evaluation Rule

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An audience based on a changing relationship **MUST** define the point or rule by which audience membership and access are evaluated.

### Rationale

An explicit evaluation point or rule prevents ambiguity over whether later relationship changes affect access to records created earlier.

### Source

- REM-03-159
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-085

### Title

Dynamic Audience Evaluation Options

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A dynamic audience **MAY** define access using:

- audience membership as it existed at publication time;
- audience membership as it exists at the time of each access attempt; or
- another explicitly defined temporal or membership-evaluation rule.

### Rationale

These alternatives support snapshot, live and other defined audience semantics without selecting a universal evaluation default.

### Source

- REM-03-160
- REM-03-161
- REM-03-162
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-086

### Title

Later Audience Membership and Earlier Records

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema or individual record **MAY** define whether later audience membership grants access to records created before that membership began.

### Rationale

Schema- or record-level definition prevents a changing relationship from automatically implying either retroactive access or permanent exclusion from earlier records.

### Source

- REM-03-163
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-087

### Title

Future Access Revocation on Audience Removal

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Removing an identity from a record's audience **MUST** revoke that identity's future authorised access under the removed audience rule.

### Rationale

Audience removal must end future access that depended on the removed rule, while remaining distinct from deletion of information the identity previously received.

### Source

- REM-03-164
- `design-notes/03-record-model.md`, Section 15.2

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-088

### Title

No Received-Copy Deletion Guarantee

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay protocol **MUST NOT** represent audience removal or access revocation as guaranteeing deletion of copies already received by a former audience member.

### Rationale

Revocation can terminate future protocol-authorised access but cannot ensure that a recipient deletes information already obtained.

### Source

- REM-03-165
- `design-notes/03-record-model.md`, Section 15.2

### Related Invariants

- AI-07

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-152` | Consolidated restricted-audience permission | `REL-REC-083` |
| `REM-03-153` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-154` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-155` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-156` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-157` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-158` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-159` | Direct | `REL-REC-084` |
| `REM-03-160` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-161` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-162` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-163` | Direct | `REL-REC-086` |
| `REM-03-164` | Direct | `REL-REC-087` |
| `REM-03-165` | Direct | `REL-REC-088` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated audience basis or evaluation option in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 15 of `design-notes/03-record-model.md`.
- Source Sections 16–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-152` through `REM-03-165`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-082`.
- First identifier in this part: `REL-REC-083`.
- Final identifier in this part: `REL-REC-088`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–12.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-152` through `REM-03-158` retain individual traceability through the Source list and coverage table for `REL-REC-083`.
- `REM-03-160` through `REM-03-162` retain individual traceability through the Source list and coverage table for `REL-REC-085`.

## Restricted-audience verification

- All six restricted-audience bases remain explicit and optional.
- No restricted record is required to use every audience basis.
- No identity, application-approval, group-membership, permission-grant or access-rule resolution mechanism is invented.

## Dynamic-audience verification

- An audience based on a changing relationship must define its access-evaluation point or rule.
- Publication-time, access-time and alternative evaluation remain permitted options.
- No universal evaluation default is selected.
- A schema or individual record may define whether later audience membership grants access to earlier records.
- Later followers or group members are not assumed always to receive access to earlier records.

## Audience-removal verification

- Removing an identity from an audience revokes future authorised access under the removed audience rule.
- Future access revocation remains distinct from deletion of information already received.
- Audience removal and access revocation are not represented as guaranteeing deletion of received copies.
- No mechanism for deleting external copies is invented.

## Illustrative-example verification

- Section 15 audience examples generate no separate normative catalogue requirements.
- “Only Bob”, “Only current collaborators”, “Only Application X”, membership-credential holders and “Visible to current followers” are not made mandatory rules, schema vocabulary or default access semantics.
- No physical audience-field name or final access-control syntax is inferred from an example.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No usage-rights requirement, access mechanism, audience default, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 12 defines restricted-audience declarations, dynamic-audience evaluation, later-membership treatment and the effects and limits of audience removal. It generates `REL-REC-083` through `REL-REC-088` from `REM-03-152` through `REM-03-165`.

The next catalogue part should begin with source Section 16 and `REM-03-166`.
