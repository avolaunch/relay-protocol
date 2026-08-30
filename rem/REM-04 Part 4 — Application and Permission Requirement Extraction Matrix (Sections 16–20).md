# REM-04 Part 4 — Application and Permission Requirement Extraction Matrix (Sections 16–20)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 16–20 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

16. Purpose limitation
17. Purpose vocabulary
18. Retention
19. Onward sharing
20. AI processing

Requirement identifiers continue sequentially from Part 3, beginning with `REM-04-213`.

---

# 16. Purpose limitation

## REM-04-213 — Purpose declaration for non-trivial requests

**Source**  
Section 16: “Every non-trivial permission request should declare a purpose.”

**Requirement**  
Every non-trivial Permission Request SHOULD declare the purpose for which access is requested.

**Classification**  
Purpose limitation; consent transparency; recommendation.

**Notes**  
The source uses “should”, so this is a recommended requirement rather than an unconditional validity rule. Trivial requests are not defined in this section and remain an implementation-policy question.

---

## REM-04-214 — Purpose represented separately from action

**Source**  
Section 16: “Purpose is separate from action.”

**Requirement**  
The permission model MUST represent purpose independently from the action being requested.

**Classification**  
Permission semantics; purpose limitation; data modelling.

**Notes**  
An action such as `read` describes what an application may do, while purpose describes why it may do it.

---

## REM-04-215 — Same action with different purposes

**Source**  
Section 16: “Two applications may request the same action for different purposes.”

**Requirement**  
The permission model MUST support different declared purposes for otherwise equivalent requested actions.

**Classification**  
Purpose limitation; consent granularity; interoperability.

**Notes**  
The model must not treat equal action scopes as equivalent where the declared purposes differ materially.

---

## REM-04-216 — Material distinction between user-serving inference and commercial training

**Source**  
Section 16 contrasts “Read private notes to answer the user’s questions” with “Read private notes to improve a commercial AI model.”

**Requirement**  
The permission model MUST be capable of distinguishing access used to answer the user’s questions from access used to improve a commercial AI model.

**Classification**  
Purpose limitation; AI governance; consent granularity.

**Notes**  
The two uses may involve the same underlying read action but create materially different consequences and therefore require distinct permission semantics.

---

## REM-04-217 — Representation of materially different purposes

**Source**  
Section 16: “The permission model must be capable of representing that distinction.”

**Requirement**  
The permission model MUST represent materially different purposes explicitly enough for a user, provider or automated policy engine to distinguish them.

**Classification**  
Purpose representation; consent; automated policy.

**Notes**  
Purpose must not be reduced to unstructured wording that cannot be reliably compared or evaluated.

---

# 17. Purpose vocabulary

## REM-04-218 — Basic machine-readable purpose vocabulary

**Source**  
Section 17: “Relay should define a basic machine-readable purpose vocabulary while allowing extension.”

**Requirement**  
Relay SHOULD define a basic machine-readable vocabulary for declaring permission purposes.

**Classification**  
Vocabulary; interoperability; recommendation.

**Notes**  
A shared vocabulary enables consistent consent interfaces and automated policy checks across applications and providers.

---

## REM-04-219 — Extensible purpose vocabulary

**Source**  
Section 17: “Relay should define a basic machine-readable purpose vocabulary while allowing extension.”

**Requirement**  
The purpose vocabulary SHOULD allow extension beyond the core Relay-defined terms.

**Classification**  
Extensibility; vocabulary governance; recommendation.

**Notes**  
Extensions should preserve machine readability and should not silently redefine existing core terms.

---

## REM-04-220 — Identity-display purpose

**Source**  
Section 17, possible core purposes: `identity-display`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing identity display.

**Classification**  
Purpose vocabulary; identity presentation; recommendation.

**Notes**  
This purpose covers use of identity data to present an identity to a user or audience.

---

## REM-04-221 — Content-display purpose

**Source**  
Section 17, possible core purposes: `content-display`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing content display.

**Classification**  
Purpose vocabulary; content presentation; recommendation.

**Notes**  
This should remain distinguishable from publishing, indexing, analytics or model training.

---

## REM-04-222 — Content-publishing purpose

**Source**  
Section 17, possible core purposes: `content-publishing`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing content publishing.

**Classification**  
Purpose vocabulary; publishing; recommendation.

**Notes**  
Publishing should not be inferred merely from read or draft-creation access.

---

## REM-04-223 — Communication purpose

**Source**  
Section 17, possible core purposes: `communication`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing communication.

**Classification**  
Purpose vocabulary; messaging; recommendation.

**Notes**  
The scope and communication channels remain subject to the separate resource and action grant.

---

## REM-04-224 — Search purpose

**Source**  
Section 17, possible core purposes: `search`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing search.

**Classification**  
Purpose vocabulary; discovery; recommendation.

**Notes**  
Search should remain distinguishable from persistent indexing where relevant.

---

## REM-04-225 — Indexing purpose

**Source**  
Section 17, possible core purposes: `indexing`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing indexing.

**Classification**  
Purpose vocabulary; indexing; recommendation.

**Notes**  
Indexing may involve durable derived representations and therefore may require different retention or processing disclosures from transient search.

---

## REM-04-226 — Recommendation purpose

**Source**  
Section 17, possible core purposes: `recommendation`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing recommendation.

**Classification**  
Purpose vocabulary; recommendation systems; recommendation.

**Notes**  
Recommendation remains distinct from analytics, personalisation and general model training.

---

## REM-04-227 — Analytics purpose

**Source**  
Section 17, possible core purposes: `analytics`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing analytics.

**Classification**  
Purpose vocabulary; analytics; recommendation.

**Notes**  
The declaration does not itself authorise any particular data scope or retention period.

---

## REM-04-228 — Personalisation purpose

**Source**  
Section 17, possible core purposes: `personalisation`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing personalisation.

**Classification**  
Purpose vocabulary; personalisation; recommendation.

**Notes**  
Personalisation may overlap operationally with AI processing but remains a distinct declared purpose.

---

## REM-04-229 — Moderation purpose

**Source**  
Section 17, possible core purposes: `moderation`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing moderation.

**Classification**  
Purpose vocabulary; moderation; recommendation.

**Notes**  
Moderation purpose does not imply a universal moderation policy or unrestricted access to all records.

---

## REM-04-230 — Backup purpose

**Source**  
Section 17, possible core purposes: `backup`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing backup.

**Classification**  
Purpose vocabulary; continuity; recommendation.

**Notes**  
Backup-related access should still declare scope, retention and restoration implications.

---

## REM-04-231 — Migration purpose

**Source**  
Section 17, possible core purposes: `migration`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing migration.

**Classification**  
Purpose vocabulary; portability; recommendation.

**Notes**  
Migration purpose does not automatically grant high-authority migration actions, which require explicit action scope.

---

## REM-04-232 — AI-inference purpose

**Source**  
Section 17, possible core purposes: `AI-inference`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing AI inference.

**Classification**  
Purpose vocabulary; AI processing; recommendation.

**Notes**  
Inference should remain distinguishable from fine-tuning and general training.

---

## REM-04-233 — AI-training purpose

**Source**  
Section 17, possible core purposes: `AI-training`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing AI training.

**Classification**  
Purpose vocabulary; AI governance; recommendation.

**Notes**  
Training is materially different from transient inference and should not be inferred from a general AI declaration.

---

## REM-04-234 — Research purpose

**Source**  
Section 17, possible core purposes: `research`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing research.

**Classification**  
Purpose vocabulary; research; recommendation.

**Notes**  
The term may require additional explanatory text to identify the specific research context and data use.

---

## REM-04-235 — Commercial-licensing purpose

**Source**  
Section 17, possible core purposes: `commercial-licensing`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing commercial licensing.

**Classification**  
Purpose vocabulary; commercial use; recommendation.

**Notes**  
Commercial licensing purpose remains separate from legal usage rights and must not override record-level rights declarations.

---

## REM-04-236 — Security purpose

**Source**  
Section 17, possible core purposes: `security`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing security.

**Classification**  
Purpose vocabulary; security operations; recommendation.

**Notes**  
Security purpose must not be used as an unlimited catch-all for unrelated data access.

---

## REM-04-237 — Fraud-prevention purpose

**Source**  
Section 17, possible core purposes: `fraud-prevention`.

**Requirement**  
The core purpose vocabulary SHOULD support a machine-readable purpose representing fraud prevention.

**Classification**  
Purpose vocabulary; risk control; recommendation.

**Notes**  
Fraud-prevention access remains subject to separate resource, action, duration and retention limits.

---

## REM-04-238 — Additional explanatory text

**Source**  
Section 17: “An application may provide additional explanatory text...”

**Requirement**  
An application MAY provide human-readable explanatory text in addition to a machine-readable purpose declaration.

**Classification**  
Consent explanation; application metadata; permission.

**Notes**  
Explanatory text can provide context but must not replace the structured purpose value.

---

## REM-04-239 — Prohibition on vague custom wording as the sole purpose declaration

**Source**  
Section 17: an application “should not rely only on vague custom wording.”

**Requirement**  
An application SHOULD NOT rely solely on vague custom wording to declare the purpose of requested access.

**Classification**  
Consent clarity; machine readability; recommendation.

**Notes**  
The intent is to preserve comparability, automation and meaningful user understanding.

---

# 18. Retention

## REM-04-240 — External-retention declaration

**Source**  
Section 18: “A permission request must declare whether the application retains data outside the repository.”

**Requirement**  
Every Permission Request MUST declare whether the application retains accessed data outside the Relay Repository.

**Classification**  
Retention; consent disclosure; data handling.

**Notes**  
The declaration concerns copies, caches or derived data held outside the authoritative repository.

---

## REM-04-241 — No-retention declaration

**Source**  
Section 18, possible declarations: `no-retention`.

**Requirement**  
The retention model MUST be capable of representing that an application does not retain data outside the repository.

**Classification**  
Retention vocabulary; data minimisation.

**Notes**  
Operational logs or unavoidable transport buffers may require separate treatment in later specification work.

---

## REM-04-242 — Session-only retention declaration

**Source**  
Section 18, possible declarations: `session-only`.

**Requirement**  
The retention model MUST be capable of representing retention limited to the active session.

**Classification**  
Retention vocabulary; session handling.

**Notes**  
The end condition for the session should be unambiguous to implementations.

---

## REM-04-243 — Temporary-cache retention declaration

**Source**  
Section 18, possible declarations: `temporary-cache`.

**Requirement**  
The retention model MUST be capable of representing temporary caching outside the repository.

**Classification**  
Retention vocabulary; caching.

**Notes**  
A temporary-cache declaration should normally be accompanied by a machine-readable duration.

---

## REM-04-244 — Retained-until-revocation declaration

**Source**  
Section 18, possible declarations: `retained-until-revocation`.

**Requirement**  
The retention model MUST be capable of representing retention that continues until the Permission Grant is revoked.

**Classification**  
Retention vocabulary; revocation lifecycle.

**Notes**  
Revocation ends authorised future retention but cannot by itself technically prove deletion of every external copy.

---

## REM-04-245 — Retained-for-defined-period declaration

**Source**  
Section 18, possible declarations: `retained-for-defined-period`.

**Requirement**  
The retention model MUST be capable of representing retention for a defined period.

**Classification**  
Retention vocabulary; time limitation.

**Notes**  
The period should be represented in a machine-readable format.

---

## REM-04-246 — Retained-indefinitely declaration

**Source**  
Section 18, possible declarations: `retained-indefinitely`.

**Requirement**  
The retention model MUST be capable of representing indefinite retention.

**Classification**  
Retention vocabulary; high-impact disclosure.

**Notes**  
Indefinite retention is a disclosure state, not an endorsement or guarantee that such retention is lawful or acceptable.

---

## REM-04-247 — Machine-readable retention period

**Source**  
Section 18: “Where a period is declared, it should be machine-readable.”

**Requirement**  
Where a retention period is declared, that period SHOULD be expressed in a machine-readable form.

**Classification**  
Retention; machine readability; recommendation.

**Notes**  
The source example uses an ISO 8601 duration but does not make that exact syntax final in this section.

---

## REM-04-248 — No technical guarantee of complete external deletion

**Source**  
Section 18: “The protocol cannot technically guarantee deletion of all external copies.”

**Requirement**  
The protocol MUST NOT represent itself as technically guaranteeing deletion of all external copies retained by an application or third party.

**Classification**  
Protocol limitation; retention; truthful representation.

**Notes**  
The protocol can express commitments and support accountability without claiming impossible universal enforcement.

---

## REM-04-249 — Explicit retention commitment

**Source**  
Section 18: the protocol can “make the commitment explicit”.

**Requirement**  
The permission model MUST be capable of expressing an application’s retention commitment explicitly.

**Classification**  
Retention disclosure; consent evidence.

**Notes**  
The commitment should be attributable to the requesting application and linked to the approved grant.

---

## REM-04-250 — Recording approved retention terms

**Source**  
Section 18: the protocol can “record what the user approved”.

**Requirement**  
The permission model MUST be capable of recording the retention terms approved by the user.

**Classification**  
Consent receipt; auditability; retention.

**Notes**  
The recorded approval should distinguish the requested terms from the actual granted terms where they differ.

---

## REM-04-251 — Retention audit support

**Source**  
Section 18: the protocol can “enable audits”.

**Requirement**  
The permission model SHOULD support auditing of declared and approved retention commitments.

**Classification**  
Auditability; compliance; recommendation.

**Notes**  
Audit support does not itself prove that every application behaved compliantly.

---

## REM-04-252 — Identification of retention non-compliance

**Source**  
Section 18: the protocol can “identify non-compliant applications”.

**Requirement**  
The protocol SHOULD support identifying applications that do not comply with their declared or granted retention commitments.

**Classification**  
Compliance monitoring; accountability; recommendation.

**Notes**  
Detection mechanisms and evidence standards remain outside Sections 16–20.

---

## REM-04-253 — Contractual enforcement support

**Source**  
Section 18: the protocol can “support contractual enforcement”.

**Requirement**  
The protocol MAY provide records and declarations that support contractual enforcement of retention commitments.

**Classification**  
Legal support; accountability; permission.

**Notes**  
The protocol does not itself adjudicate or enforce external contracts.

---

# 19. Onward sharing

## REM-04-254 — Onward-sharing declaration

**Source**  
Section 19: “Applications must declare whether data may be disclosed to third parties.”

**Requirement**  
Every application requesting access MUST declare whether accessed data may be disclosed to third parties.

**Classification**  
Onward sharing; consent disclosure; data governance.

**Notes**  
The declaration must cover disclosure of copies as well as any direct repository access granted to third parties.

---

## REM-04-255 — No-sharing declaration

**Source**  
Section 19, possible values: `none`.

**Requirement**  
The onward-sharing model MUST be capable of representing that no third-party disclosure is permitted or intended.

**Classification**  
Onward-sharing vocabulary; data minimisation.

**Notes**  
The meaning should be aligned with any separately declared processors or infrastructure providers.

---

## REM-04-256 — Processors-only declaration

**Source**  
Section 19, possible values: `processors-only`.

**Requirement**  
The onward-sharing model MUST be capable of representing disclosure limited to processors acting on behalf of the application.

**Classification**  
Onward-sharing vocabulary; processor access.

**Notes**  
Processor access should not be represented as unrestricted independent use.

---

## REM-04-257 — Named-parties declaration

**Source**  
Section 19, possible values: `named-parties`.

**Requirement**  
The onward-sharing model MUST be capable of representing disclosure limited to specifically named third parties.

**Classification**  
Onward-sharing vocabulary; named recipients.

**Notes**  
Named parties should be identifiable in a stable and inspectable manner where possible.

---

## REM-04-258 — Category-based declaration

**Source**  
Section 19, possible values: `category-based`.

**Requirement**  
The onward-sharing model MUST be capable of representing disclosure to third parties described by category.

**Classification**  
Onward-sharing vocabulary; recipient categories.

**Notes**  
Category-based wording should be specific enough to support meaningful consent and policy evaluation.

---

## REM-04-259 — Unrestricted-sharing declaration

**Source**  
Section 19, possible values: `unrestricted`.

**Requirement**  
The onward-sharing model MUST be capable of representing unrestricted third-party disclosure.

**Classification**  
Onward-sharing vocabulary; high-impact disclosure.

**Notes**  
This is a disclosure state and does not itself establish lawfulness or compatibility with record-level rights.

---

## REM-04-260 — Third-party identity disclosure

**Source**  
Section 19: where possible, the request should identify “the third party”.

**Requirement**  
Where possible, a Permission Request involving onward sharing SHOULD identify the third party that will receive data or access.

**Classification**  
Onward sharing; recipient transparency; recommendation.

**Notes**  
Where an exact party is not known, a category declaration may be used, subject to adequate specificity.

---

## REM-04-261 — Shared data-category disclosure

**Source**  
Section 19: where possible, the request should identify “the category of data shared”.

**Requirement**  
Where possible, a Permission Request involving onward sharing SHOULD identify the category of data to be shared.

**Classification**  
Onward sharing; data transparency; recommendation.

**Notes**  
The category should correspond to the granted resource scope rather than using an unnecessarily broad description.

---

## REM-04-262 — Sharing-purpose disclosure

**Source**  
Section 19: where possible, the request should identify “the purpose”.

**Requirement**  
Where possible, a Permission Request involving onward sharing SHOULD identify the purpose of the third-party disclosure.

**Classification**  
Onward sharing; purpose limitation; recommendation.

**Notes**  
The third-party purpose may differ from the requesting application’s primary purpose and should be represented separately where necessary.

---

## REM-04-263 — Third-party retention disclosure

**Source**  
Section 19: where possible, the request should identify “the retention period”.

**Requirement**  
Where possible, a Permission Request involving onward sharing SHOULD identify the retention period applicable to the third party.

**Classification**  
Onward sharing; retention; recommendation.

**Notes**  
The requesting application’s retention commitment does not automatically describe the third party’s retention behaviour.

---

## REM-04-264 — Direct-access versus copy disclosure

**Source**  
Section 19: where possible, the request should identify “whether the third party receives direct repository access or a copy.”

**Requirement**  
Where possible, a Permission Request involving onward sharing SHOULD distinguish between direct repository access and disclosure of a copied dataset or record.

**Classification**  
Onward sharing; access topology; recommendation.

**Notes**  
These modes create different revocation, audit and persistence consequences.

---

## REM-04-265 — Prohibition on partner-network distribution under a no-sharing grant

**Source**  
Section 19: “A grant prohibiting onward sharing must not be treated as permission to distribute data through an application partner network.”

**Requirement**  
A Permission Grant that prohibits onward sharing MUST NOT be interpreted as permitting distribution through an application partner network.

**Classification**  
Onward-sharing restriction; consent enforcement.

**Notes**  
Commercial or technical relationships between the application and its partners do not override the grant restriction.

---

# 20. AI processing

## REM-04-266 — Distinct AI-use activities

**Source**  
Section 20: “The permission model must treat AI use as several distinct activities.”

**Requirement**  
The permission model MUST represent different forms of AI use as distinct activities rather than as one undifferentiated permission.

**Classification**  
AI governance; consent granularity; permission semantics.

**Notes**  
Distinct representation allows different approval, retention and onward-sharing rules to apply to each activity.

---

## REM-04-267 — AI-inference activity

**Source**  
Section 20, AI inference: “Using records temporarily to produce an output for the user.”

**Requirement**  
The AI-use model MUST be capable of representing temporary use of records to produce an output for the user as AI inference.

**Classification**  
AI processing; inference; consent scope.

**Notes**  
Inference does not by itself imply permission for retention, fine-tuning or general training.

---

## REM-04-268 — Personalisation activity

**Source**  
Section 20, Personalisation: “Using records to tailor an application’s behaviour.”

**Requirement**  
The AI-use model MUST be capable of representing use of records to tailor an application’s behaviour as personalisation.

**Classification**  
AI processing; personalisation; consent scope.

**Notes**  
Personalisation may or may not involve model adaptation, which should be disclosed separately where applicable.

---

## REM-04-269 — Embedding or indexing activity

**Source**  
Section 20, Embedding or indexing: “Transforming records into vectors or other searchable representations.”

**Requirement**  
The AI-use model MUST be capable of representing transformation of records into vectors or other searchable representations as embedding or indexing.

**Classification**  
AI processing; derived representations; indexing.

**Notes**  
Derived representations may persist even where the original record is no longer directly retained, so retention and deletion commitments should address them explicitly.

---

## REM-04-270 — Fine-tuning activity

**Source**  
Section 20, Fine-tuning: “Using records to adapt a model for a specific user or application.”

**Requirement**  
The AI-use model MUST be capable of representing use of records to adapt a model for a specific user or application as fine-tuning.

**Classification**  
AI processing; model adaptation; consent scope.

**Notes**  
Fine-tuning should remain distinguishable from transient inference and broader general training.

---

## REM-04-271 — General-model-training activity

**Source**  
Section 20, General model training: “Using records to improve a model for broader use.”

**Requirement**  
The AI-use model MUST be capable of representing use of records to improve a model for broader use as general model training.

**Classification**  
AI processing; model training; high-impact consent.

**Notes**  
Broader-use training is materially different from user-specific processing and requires its own explicit declaration.

---

## REM-04-272 — Evaluation activity

**Source**  
Section 20, Evaluation: “Using records to test or benchmark a system.”

**Requirement**  
The AI-use model MUST be capable of representing use of records to test or benchmark a system as evaluation.

**Classification**  
AI processing; evaluation; consent scope.

**Notes**  
Evaluation may involve human review, external providers or retained datasets, which require separate disclosures where applicable.

---

## REM-04-273 — Prohibition on a single generic AI checkbox

**Source**  
Section 20: “These should not be collapsed into a single checkbox labelled: Allow AI.”

**Requirement**  
Consent interfaces and permission representations SHOULD NOT collapse inference, personalisation, embedding, fine-tuning, general training and evaluation into a single generic “Allow AI” choice.

**Classification**  
Consent design; AI transparency; recommendation.

**Notes**  
A single generic control would obscure materially different processing activities and undermine meaningful consent.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 16–20 of `design-notes/04-application-and-permission-model.md`.
- Section 21 and later material was excluded.
- Examples were used to clarify meaning but were not promoted into final syntax requirements.

## Numbering verification

- First requirement: `REM-04-213`.
- Final requirement: `REM-04-273`.
- Requirement numbering continues directly from Part 3.
- Identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit sentence, list item, defined activity or necessary decomposition of a compound source statement.
- The purpose-vocabulary entries were extracted separately because each represents an independently testable vocabulary capability.
- Retention and onward-sharing declarations were separated from the protocol’s limitations and accountability mechanisms.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` or `SHOULD NOT` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- The protocol’s stated inability to guarantee deletion was retained as a truthful limitation rather than transformed into a technical enforcement promise.

## Editorial verification

- Purpose remains distinct from action.
- Machine-readable purpose values remain distinct from supplementary explanatory text.
- Retention commitments remain distinct from technical guarantees of deletion.
- Onward sharing remains distinct from direct repository access and from disclosure of copies.
- AI inference, personalisation, embedding, fine-tuning, general training and evaluation remain independently representable activities.
