# Database Design Principles
## Purpose of the Database Layer

The database layer is the authoritative persistence mechanism for business data.

Its responsibilities are to:

Persist authoritative business state.
Preserve domain ownership boundaries.
Maintain aggregate consistency.
Support approved resource lifecycles.
Store governance records.
Support future architectural evolution without redesign.

The database does not implement business workflows, authorization, governance decisions, or API behavior.

## Persistence Philosophy

The persistence model follows the approved Domain-Oriented Modular Monolith architecture.

Persistence exists to support business domains rather than define them.

The database structure shall reflect:

Approved domain boundaries.
Approved aggregate boundaries.
Approved ownership model.
Approved resource lifecycles.

Implementation convenience must never redefine business ownership.

## Collection Ownership Principles

Every collection shall have exactly one owning domain.

Only the owning domain may:

Define persistence rules.
Modify authoritative records.
Control lifecycle transitions.

Reading another domain's data does not transfer ownership.

Cross-domain shared collections are prohibited.

## Domain Ownership Alignment

Database ownership shall remain aligned with the approved backend domains:

Identity
Social Graph
Content
Community
Media
Governance

Feed remains a derived domain and owns no authoritative persisted business data.

Governance owns governance records but never assumes ownership of governed resources.

## Aggregate Persistence Boundaries

Each aggregate shall persist independently.

Aggregate persistence boundaries shall mirror approved aggregate boundaries.

Persistence must preserve:

Aggregate ownership.
Aggregate invariants.
Aggregate lifecycle independence.

No aggregate shall span multiple domain owners.

## Data Consistency Principles

The database is the authoritative source of persisted business state.

Consistency requirements follow aggregate ownership.

Each domain is responsible for maintaining the consistency of the resources it owns.

Cross-domain consistency shall be achieved through approved application-layer coordination rather than shared persistence ownership.

## Reference vs Embedding Philosophy

Document relationships shall be selected according to ownership and lifecycle alignment.

General principles:

Embed data when it shares the same owner and lifecycle.
Reference data when ownership or lifecycle differs.
References shall preserve domain boundaries.
Relationship modeling must never violate ownership principles.

Implementation-specific decisions are deferred to later design tasks.

## Identifier Strategy

Every persisted resource shall have one stable identifier.

Identifiers shall:

Be globally unique.
Remain immutable throughout the resource lifecycle.
Be independent of business attributes.
Be suitable for cross-domain references.

Identifier generation strategy will be defined during schema design.

## Timestamp Strategy

Authoritative business resources shall support consistent lifecycle timestamps.

Timestamp usage shall:

Represent lifecycle progression.
Support auditability.
Support operational traceability.
Remain consistent across all domains.

Timestamp implementation details are deferred.

## Soft Deletion Philosophy

Logical deletion is preferred over physical deletion for business resources where lifecycle continuity or governance requires historical retention.

Soft deletion shall:

Preserve resource identity.
Preserve ownership.
Preserve auditability.
Preserve governance compatibility.

Physical deletion shall be reserved for implementation-defined scenarios consistent with approved retention policies.

## Derived Data Philosophy

Derived information is not authoritative business state.

Derived data:

Exists only to support application behavior.
Must never become the source of truth.
Shall remain reproducible from authoritative data whenever practical.

Feed data remains a derived read model and shall not become an ownership boundary.

## Auditability Principles

Persistence shall support reconstruction of important business and governance events.

Auditability shall preserve:

Resource ownership.
Lifecycle progression.
Governance accountability.
Administrative traceability.

Governance records remain authoritative audit resources owned by the Governance domain.

## Future Evolution Principles

Database evolution shall follow the Evolutionary Architecture Principle.

Future changes shall:

Preserve domain ownership.
Preserve aggregate boundaries.
Preserve identifier stability.
Preserve API compatibility whenever practical.
Minimize migration complexity.

Schema evolution must extend the existing model rather than replace established architectural boundaries.

## Database Design Constraints

The following constraints are authoritative:

Domain ownership determines collection ownership.
One authoritative owner per persisted resource.
Aggregate boundaries shall not cross domains.
Governance authority shall not alter ownership.
Feed shall not persist authoritative business state.
Persistence shall support approved API contracts rather than redefine them.
Database design shall remain implementation-independent wherever possible.
Simplicity shall take precedence over speculative optimization.

## Principles Validation

The database design principles confirm that:

Persistence preserves approved domain boundaries.
Collection ownership aligns with backend module ownership.
Aggregate persistence aligns with approved aggregate boundaries.
Governance ownership remains independent from business ownership.
Feed remains a derived, non-authoritative domain.
The database remains compatible with future architectural evolution without requiring redesign.

--- 

# Collection Inventory
## Collection Inventory Objectives
Purpose

The Collection Inventory defines the authoritative set of MongoDB collections required to support the approved MVP.

It establishes:

The complete persistence inventory.
The authoritative owner of every persisted collection.
Alignment between collections, aggregates, and backend domains.
Stable ownership boundaries before document design begins.

Collection inventory defines what exists, not how it is stored.

Every persisted collection shall have exactly one authoritative owning domain.

## Collection Classification Principles

Collections are classified according to the role they play within the approved architecture.

Business Collections

Collections that persist authoritative business resources owned by business domains.

Examples:

User Accounts
User Profiles
Posts
Comments
Herds
Relationship Collections

Collections that persist relationships between business entities while remaining authoritative resources owned by a single domain.

Examples:

Follows
Herd Memberships
Votes
Shepherd Assignments
Governance Collections

Collections that persist governance-owned resources.

Examples:

Reports
Moderation Actions

Governance collections contain governance state only.

They never become authoritative storage for governed business resources.

Supporting Collections

No supporting collections are required by the approved MVP architecture.

Additional supporting collections may be introduced only when justified by future approved architectural requirements.

## Domain Collection Inventory
### Identity Domain

Purpose

Persist platform identity and profile information.

Owned Collections

User Accounts
User Profiles

Ownership Rationale

Identity is the authoritative owner of user identity, authentication lifecycle, and public profile lifecycle.

### Social Graph Domain

Purpose

Persist user-to-user relationships.

Owned Collections

Follows

Ownership Rationale

The Social Graph exclusively owns follow relationship lifecycle and relationship management.

### Content Domain

Purpose

Persist discussion content and engagement.

Owned Collections

Posts
Comments
Votes

Ownership Rationale

The Content domain exclusively owns content creation, discussion lifecycle, and voting.

### Community Domain

Purpose

Persist community structure and participation.

Owned Collections

Herds
Herd Memberships
Shepherd Assignments

Ownership Rationale

Community exclusively owns herd lifecycle, membership lifecycle, and delegated community authority.

### Media Domain

Purpose

Persist reusable media assets.

Owned Collections

Images

Ownership Rationale

Media owns media asset lifecycle independently of the resources that reference those assets.

### Governance Domain

Purpose

Persist governance workflows and moderation history.

Owned Collections

Reports
Moderation Actions

Ownership Rationale

Governance owns governance records, enforcement history, and moderation workflows without assuming ownership of governed business resources.

### Feed Domain

Purpose

Provide derived content consumption.

Owned Collections

None.

Ownership Rationale

Feed is a derived domain that composes data from authoritative domains.

It owns no persisted authoritative collections.

## Collection Ownership Matrix
| Domain       | Collection           | Aggregate        | Ownership    |
| ------------ | -------------------- | ---------------- | ------------ |
| Identity     | User Accounts        | User Identity    | Identity     |
| Identity     | User Profiles        | User Identity    | Identity     |
| Social Graph | Follows              | Follow           | Social Graph |
| Content      | Posts                | Personal Content | Content      |
| Content      | Comments             | Discussion       | Content      |
| Content      | Votes                | Voting           | Content      |
| Community    | Herds                | Community        | Community    |
| Community    | Herd Memberships     | Membership       | Community    |
| Community    | Shepherd Assignments | Community        | Community    |
| Media        | Images               | Media            | Media        |
| Governance   | Reports              | Reporting        | Governance   |
| Governance   | Moderation Actions   | Moderation       | Governance   |

## Aggregate to Collection Mapping
| Aggregate        | Authoritative Collection     |
| ---------------- | ---------------------------- |
| User Identity    | User Accounts, User Profiles |
| Follow           | Follows                      |
| Personal Content | Posts                        |
| Discussion       | Comments                     |
| Voting           | Votes                        |
| Community        | Herds                        |
| Membership       | Herd Memberships             |
| Media            | Images                       |
| Reporting        | Reports                      |
| Moderation       | Moderation Actions           |

Note

The User Identity aggregate spans two closely related authoritative resources—account identity and public profile—both owned exclusively by the Identity domain. Ownership remains singular because both collections belong to the same aggregate owner.

## Collection Responsibility Rules

The following rules are authoritative.

CI-01

Every collection has exactly one owning domain.

CI-02

Collection ownership follows aggregate ownership.

CI-03

Collections never have shared ownership.

CI-04

Only the owning domain may define persistence rules or lifecycle transitions for its collections.

CI-05

Cross-domain reads do not transfer collection ownership.

CI-06

Governance owns governance collections only.

Governance actions never transfer ownership of business collections.

CI-07

Feed owns no authoritative collections.

Feed consumes authoritative collections to produce derived views.

CI-08

Collection ownership remains independent of API access patterns, query patterns, or implementation details.

## Future Collection Evolution

Future collections may be introduced only when justified by approved platform requirements.

New collections shall:

Belong to exactly one approved domain.
Preserve aggregate ownership boundaries.
Preserve existing ownership rules.
Avoid introducing shared ownership.
Extend the existing persistence model rather than replace it.

Collection evolution shall follow the Evolutionary Architecture Principle.

## Collection Inventory Validation

The collection inventory confirms that:

Every approved aggregate has an authoritative persistence home.
Every collection has exactly one owning domain.
No collection has shared ownership.
Feed remains a derived domain with no authoritative persistence.
Governance ownership remains independent from business ownership.
Collection ownership aligns with approved backend domains.
Collection inventory preserves aggregate boundaries.
Collection inventory is sufficient to begin document structure design.

---

# Document Structure

## Document Modeling Principles

### Purpose of Document Structure

The document structure defines the authoritative logical organization of persisted business resources.

Its objectives are to:

Establish a consistent document model across all collections.
Preserve approved domain ownership boundaries.
Preserve aggregate consistency.
Standardize lifecycle representation.
Standardize governance compatibility.
Provide an implementation-independent blueprint for future schema design.

Document structure defines what information belongs to a document, not how it is physically implemented.

---

### Document Modeling Philosophy

Every persisted document represents exactly one authoritative business resource.

A document is the persistence representation of a resource owned by a single domain.

Document design shall prioritize:

Business clarity
Ownership preservation
Aggregate integrity
Lifecycle transparency
Evolutionary compatibility

Implementation convenience shall never redefine business ownership or aggregate boundaries.

---

### Document Ownership Principles

Every document shall have exactly one authoritative owner.

Ownership rules established by the Data Model and Collection Inventory remain unchanged.

Only the owning domain may define:

Business information
Lifecycle transitions
Mutable business state
Business invariants

Other domains may consume information but never redefine the document structure of foreign resources.

---

### Aggregate Alignment

Document boundaries shall remain aligned with approved aggregate boundaries.

A document shall belong to one aggregate only.

Document structure shall preserve:

Aggregate ownership
Aggregate lifecycle
Aggregate consistency
Aggregate invariants

Documents shall never become shared persistence models between aggregates.

---

### Business Data vs Derived Data

Documents shall persist authoritative business information only.

Business information includes:

Resource identity
Business state
Ownership information
Lifecycle state
Governance compatibility
Business attributes

Derived information:

Does not define business truth.
Shall not become authoritative.
Shall remain reproducible from authoritative business data whenever practical.

Documents should avoid persisting presentation-oriented projections.

---

### Mutable vs Immutable Information

Document structure shall distinguish between immutable and mutable information.

Immutable information represents business identity and historical facts.

Examples include:

Resource identity
Original creator
Creation context

Mutable information represents legitimate business evolution.

Examples include:

Profile details
Content revisions
Community configuration
Visibility state

Business rules determine mutability.

Persistence structure shall make this distinction explicit.

---

### System-Managed vs User-Managed Information

Every document shall distinguish between information managed by users and information managed by the platform.

User-managed information represents intentional user actions.

Examples:

Profile content
Post content
Community descriptions

System-managed information represents platform responsibility.

Examples:

Lifecycle state
Timestamps
Governance state
Operational metadata

System-managed information shall not be directly controlled by users.

---

### Lifecycle Philosophy

Every business resource shall expose its lifecycle explicitly.

Lifecycle information shall describe the current authoritative state of the resource.

Lifecycle representation shall:

Reflect approved lifecycle definitions.
Support business workflows.
Support governance workflows.
Support future evolution.

Lifecycle information shall never be inferred from unrelated fields.

---

### Metadata Philosophy

Metadata supports resource management without redefining business meaning.

Metadata exists to provide:

Operational context
Lifecycle traceability
Governance compatibility
Evolution support

Metadata shall remain secondary to business information.

Metadata shall never become the primary representation of business state.

---

### Consistency Principles

Document structure shall support consistency within aggregate boundaries.

Consistency responsibilities include:

Single authoritative owner
Single lifecycle owner
Stable business identity
Explicit lifecycle representation
Explicit ownership representation
Consistent metadata organization

Cross-domain consistency remains the responsibility of the application architecture rather than document structure.

---

### Future Evolution

Document structures shall evolve through extension rather than replacement.

Future document evolution shall:

Preserve document identity.
Preserve ownership.
Preserve lifecycle semantics.
Preserve API compatibility where practical.
Avoid structural redesign of existing business resources.

New capabilities should introduce additive changes whenever possible.

---

### Validation

The document structure architecture is consistent with:

- PROJECT_CONTEXT.md
- ADR-001
- Backend Architecture
- Data Model
- API Contracts
- Database Design Principles
- Collection Inventory

No architectural conflicts were identified.

## Identity Domain Document Structures

### User Accounts

Purpose

The User Account document represents the authoritative platform identity used for authentication and account lifecycle management.

It establishes the existence of a platform member and owns the authentication lifecycle.

It does not represent the user's public profile.

Ownership

Owning Domain

Identity

The Identity domain exclusively owns:

Account creation
Authentication lifecycle
Credential lifecycle
Account status
Account recovery lifecycle

No other domain may modify authoritative account information.

Lifecycle

The User Account lifecycle follows the approved account lifecycle architecture.

The document shall support lifecycle transitions including:

Registration
Verification
Active participation
Temporary restriction
Account deactivation
Account deletion (subject to approved retention policies)

Lifecycle information shall remain explicit.

Required Logical Sections
Identity

Represents the stable identity of the account.

Includes logical information such as:

Stable account identifier
Login identity
Account identity
Business Information

Represents account-specific business information.

Includes:

Authentication-related information
Verification state
Account configuration required for platform participation

Business information shall not include public profile data.

Lifecycle Information

Represents the authoritative lifecycle state of the account.

Includes:

Current account state
Lifecycle timestamps
Verification progression
Account transition history required for business workflows
Governance Information

Represents governance compatibility.

May include:

Restriction state
Enforcement compatibility
Administrative status required for governance workflows

Governance records remain owned by the Governance domain.

The account document stores only the current business state resulting from governance decisions.

System Metadata

Represents operational metadata required by the platform.

Examples include:

Audit timestamps
Versioning metadata
Internal operational metadata

Metadata shall never redefine business state.

Required Business Information

The User Account document shall authoritatively represent:

Platform identity
Authentication state
Verification state
Account lifecycle
Account participation eligibility
Required System Metadata

The document shall contain metadata supporting:

Lifecycle management
Operational traceability
Schema evolution
Audit support
Governance-Related Information

The document shall expose only governance-compatible business state.

Examples include:

Whether participation is currently permitted
Whether restrictions are active

The document shall not contain moderation history.

Fields Intentionally Excluded

The User Account document shall not contain:

Public profile information
Social relationships
Posts
Comments
Votes
Herd memberships
Reputation calculations
Feed information
Reports
Moderation history

These belong to their respective owning domains.

Validation

The User Account document satisfies:

Identity ownership
Aggregate ownership
Authentication ownership
Governance compatibility
Separation of identity from profile

Architecture establishes User Accounts as the authoritative persistence model for authentication and account lifecycle while remaining independent from public profile information.

---

### User Profiles

Purpose

The User Profile document represents the user's public identity and presentation within the platform.

It is independent from authentication.

Ownership

Owning Domain

Identity

The Identity domain exclusively owns:

Public profile lifecycle
Profile presentation
Profile visibility configuration

Lifecycle

The profile lifecycle follows the account lifecycle while maintaining independent business state.

Profile information evolves through user updates without affecting account identity.

Required Logical Sections
Identity

Represents the stable profile identity.

Includes:

Stable profile identifier
Public identity

Business Information

Represents public-facing information.

Examples include:

Display information
Biography
Profile presentation
User-configurable profile attributes

Lifecycle Information

Represents:

Profile creation
Profile updates
Visibility lifecycle
Current profile state

Governance Information

Represents governance outcomes affecting profile visibility.

Only current governance-compatible business state is stored.

Historical moderation remains owned by Governance.

System Metadata

Represents:

Audit timestamps
Operational metadata
Version metadata

Required Business Information

The profile document shall represent:

Public identity
Public presentation
Public configuration
Profile visibility state

Required System Metadata

The document shall support:

Operational traceability
Lifecycle management
Future evolution

Governance-Related Information

The profile may expose:

Current visibility restrictions
Current participation restrictions affecting presentation

The profile shall not contain moderation history.

Fields Intentionally Excluded

The profile shall not contain:

Authentication information
Credentials
Session information
Follow relationships
Posts
Comments
Votes
Herd memberships
Governance history

Validation

The User Profile document preserves:

Separation of authentication and presentation
Identity ownership
Lifecycle independence
Governance compatibility

Architecture establishes User Profiles as the authoritative persistence model for public identity and presentation while remaining independent from authentication.

---

## Social Graph Domain Document Structures

### Follows

Purpose

The Follow document represents an authoritative user-to-user relationship.

It defines the existence and lifecycle of a follow relationship.

It does not represent profile information or activity.

Ownership

Owning Domain

Social Graph

The Social Graph domain exclusively owns:

Relationship creation
Relationship removal
Relationship lifecycle

No other domain owns follow relationships.

Lifecycle

The Follow document supports:

Relationship creation
Active relationship
Relationship termination

The lifecycle remains independent from user profile updates.

Required Logical Sections
Identity

Represents the stable relationship identity.

Includes:

Stable relationship identifier

Business Information

Represents the follow relationship.

Includes:

Relationship participants
Relationship status
Relationship configuration where applicable

Lifecycle Information

Represents:

Creation
Current lifecycle state
Relationship termination where applicable

Governance Information

Represents whether governance currently affects the relationship.

Only current governance-compatible business state shall be stored.

System Metadata

Represents:

Audit timestamps
Operational metadata
Version metadata

Required Business Information

The document shall authoritatively represent:

Follow relationship
Relationship lifecycle
Current relationship state

Required System Metadata

The document shall support:

Lifecycle management
Operational traceability
Future schema evolution

Governance-Related Information

The Follow document may contain current governance-compatible state affecting relationship validity.

Governance records remain external.

Fields Intentionally Excluded

The Follow document shall not contain:

User profile information
Authentication information
Feed information
Posts
Comments
Votes
Herd memberships
Reputation
Moderation history

Validation

The Follow document preserves:

Social Graph ownership
Independent relationship lifecycle
Aggregate boundaries
Governance compatibility

Architecture establishes Follows as the authoritative persistence model for user relationship lifecycle.

## Content Domain Document Structures

### Posts

Purpose

The Post document represents the authoritative persistence model for user-created content.

It owns the complete business lifecycle of a post from creation through its eventual removal or archival.

Posts represent authored content regardless of whether they are published personally or within a Herd.

Ownership

Owning Domain

Content

The Content domain exclusively owns:

Post creation
Post editing
Publication state
Content lifecycle
Content visibility resulting from business rules

No other domain owns post content.

Lifecycle

The Post document shall support lifecycle transitions including:

Draft (if introduced in future evolution)
Published
Edited
Soft deleted
Archived (future evolution)

Lifecycle transitions remain owned by the Content domain.

Governance actions may affect visibility without transferring ownership.

Required Logical Sections
Identity

Represents the stable identity of the post.

Includes:

Stable post identifier
Authoritative content identity

Business Information

Represents the authored resource.

Includes:

Authored content
Publication context
Content configuration
Author-owned editable information

Lifecycle Information

Represents:

Creation
Publication
Content revision
Current lifecycle state
Deletion state where applicable

Governance Information

Represents the current governance-compatible business state.

Examples include:

Current visibility
Current restriction status

Historical moderation records remain owned by the Governance domain.

System Metadata

Represents:

Operational metadata
Audit timestamps
Version metadata

Required Business Information

The Post document shall authoritatively represent:

The content itself
Authorship
Publication context
Current business visibility
Current lifecycle state

Required System Metadata

The document shall support:

Operational traceability
Lifecycle management
Future schema evolution

Governance-Related Information

The document stores only the effective outcome of governance decisions.

It shall not store:

Reports
Appeals
Moderation history
Enforcement timeline

Fields Intentionally Excluded

The Post document shall not contain:

Comments
Votes
Follow relationships
Herd membership information
User profile information
Governance history
Feed projections

Validation

The Post document preserves:

Content ownership
Aggregate boundaries
Governance compatibility
Independent lifecycle

### Comments

Purpose

The Comment document represents the authoritative persistence model for discussion beneath a post or another comment.

Each comment is an independent business resource.

Ownership

Owning Domain

Content

The Content domain exclusively owns:

Comment lifecycle
Comment editing
Discussion participation

Lifecycle

The Comment document shall support:

Creation
Editing
Soft deletion
Future archival

Discussion continuity remains independent from governance records.

Required Logical Sections
Identity

Stable comment identity.

Business Information

Includes:

Comment content
Discussion context
Author-owned information

Lifecycle Information

Represents:

Creation
Updates
Current lifecycle state

Governance Information

Represents:

Current moderation outcome
Current visibility

Historical governance remains external.

System Metadata

Represents:

Audit timestamps
Version metadata
Operational metadata

Required Business Information

The document shall represent:

Comment content
Discussion participation
Current visibility
Lifecycle state

Required System Metadata

Supports:

Traceability
Lifecycle management
Evolution

Governance-Related Information

Stores only effective governance state.

No moderation history shall be embedded.

Fields Intentionally Excluded

The Comment document shall not contain:

Replies as embedded business resources
Votes
Reports
Moderation history
Feed data

Validation

The Comment document preserves:

Independent lifecycle
Aggregate ownership
Governance compatibility

### Votes

Purpose

The Vote document represents the authoritative record of an individual voting action.

Each vote represents one user's participation in content evaluation.

Ownership

Owning Domain

Content

The Content domain exclusively owns:

Vote creation
Vote updates
Vote removal

Lifecycle

The Vote lifecycle supports:

Creation
Vote modification
Vote removal

Votes remain independent business resources.

Required Logical Sections
Identity

Stable vote identity.

Business Information

Represents:

Vote intent
Vote target
Current vote state

Lifecycle Information

Represents:

Creation
Updates
Current lifecycle state

Governance Information

Represents only governance outcomes affecting vote validity.

System Metadata

Supports:

Auditability
Operational traceability
Evolution

Required Business Information

The Vote document shall represent:

User intent
Current vote
Participation state
Required System Metadata

Supports lifecycle and operational management.

Governance-Related Information

Only current governance-compatible business state shall exist.

Historical moderation remains external.

Fields Intentionally Excluded

The Vote document shall not contain:

Vote aggregates
Reputation calculations
Feed ranking
Content snapshots
Moderation history

Validation

The Vote document preserves:

Independent ownership
Independent lifecycle
Aggregate consistency

## Community Domain Document Structures

### Herds

Purpose

The Herd document represents the authoritative persistence model for a community.

It owns community identity, configuration, participation policy, and operational settings.

Ownership

Owning Domain

Community

The Community domain exclusively owns:

Community lifecycle
Community configuration
Membership policy
Visibility configuration

Lifecycle

The Herd document shall support:

Creation
Configuration updates
Restriction
Soft deletion
Future archival

Ownership remains unchanged throughout the lifecycle.

Required Logical Sections
Identity

Represents:

Stable Herd identity
Public community identity

Business Information

Represents:

Community description
Membership model
Visibility configuration
Community configuration
Operational rules

Lifecycle Information

Represents:

Creation
Configuration updates
Current lifecycle state

Governance Information

Represents current governance-compatible community state.

Historical governance remains external.

System Metadata

Represents:

Operational metadata
Audit timestamps
Version metadata

Required Business Information

The Herd document shall authoritatively represent:

Community identity
Membership policy
Community configuration
Current operational state

Required System Metadata

Supports:

Operational traceability
Lifecycle management
Future evolution

Governance-Related Information

Stores only effective governance outcomes affecting the community.

Fields Intentionally Excluded

The Herd document shall not contain:

Membership records
Shepherd assignments
Posts
Moderation history
Reports

Validation

The Herd document preserves:

Community ownership
Independent lifecycle
Governance compatibility

### Herd Memberships

Purpose

The Herd Membership document represents the authoritative participation relationship between a user and a Herd.

Ownership

Owning Domain

Community

The Community domain exclusively owns:

Membership lifecycle
Membership approval
Membership removal

Lifecycle

Supports:

Join request
Approval
Active membership
Removal
Departure

Membership remains independent from the Herd lifecycle.

Required Logical Sections
Identity

Stable membership identity.

Business Information

Represents:

Membership relationship
Membership role
Participation status

Lifecycle Information

Represents:

Join progression
Approval progression
Current lifecycle state

Governance Information

Represents only current restrictions affecting membership.

System Metadata

Represents:

Operational metadata
Audit timestamps
Version metadata

Required Business Information

The document shall represent:

Membership status
Participation eligibility
Current membership role

Required System Metadata

Supports operational traceability and lifecycle management.

Governance-Related Information

Only effective governance state shall be stored.

Fields Intentionally Excluded

The Membership document shall not contain:

Herd configuration
User profile
Shepherd history
Moderation history

Validation

The Membership document preserves:

Relationship ownership
Independent lifecycle
Aggregate consistency

### Shepherd Assignments

Purpose

The Shepherd Assignment document represents moderation authority delegated within a Herd.

It models authority assignment rather than community membership.

Ownership

Owning Domain

Community

The Community domain exclusively owns:

Assignment lifecycle
Authority delegation
Authority removal

Lifecycle

Supports:

Assignment
Role modification
Revocation
Expiration (future evolution)
Required Logical Sections
Identity

Stable assignment identity.

Business Information

Represents:

Assigned authority
Delegated permissions
Operational scope

Lifecycle Information

Represents:

Assignment
Updates
Current authority state

Governance Information

Represents only the current authority status required for governance execution.

Governance actions remain owned by the Governance domain.

System Metadata

Represents:

Operational metadata
Audit timestamps
Version metadata

Required Business Information

The document shall represent:

Authority assignment
Assignment scope
Current operational state

Required System Metadata

Supports:

Auditability
Lifecycle management
Future evolution

Governance-Related Information

Stores only current authority necessary for moderation execution.

Historical moderation actions remain external.

Fields Intentionally Excluded

The document shall not contain:

Moderation history
Reports
Enforcement records
Membership history
Herd configuration

Validation
The Shepherd Assignment document preserves:

Community ownership
Delegated authority boundaries
Governance compatibility
Independent lifecycle

## Media Domain Document Structures

### Images

Purpose

The Image document represents the authoritative persistence model for uploaded image assets.

It owns the complete lifecycle of an image independent of the business resource to which it is attached.

The Image document represents the asset itself rather than its usage within the platform.

Ownership

Owning Domain

Media

The Media domain exclusively owns:

Image lifecycle
Image storage lifecycle
Image processing lifecycle
Image availability
Image visibility resulting from business rules

No other domain owns image resources.

Lifecycle

The Image document shall support lifecycle transitions including:

Upload initiated
Upload completed
Available
Replaced (future evolution)
Soft deleted
Archived (future evolution)

Attachment to business resources shall not transfer ownership.

Required Logical Sections
Identity

Represents the stable identity of the image resource.

Includes:

Stable image identifier
Asset identity
Business Information

Represents the image resource.

Includes:

Asset information
Media characteristics
Attachment context
Media configuration

Business information shall describe the image itself rather than the business resource using it.

Lifecycle Information

Represents:

Upload lifecycle
Availability lifecycle
Current operational state
Deletion state where applicable
Governance Information

Represents only the current governance-compatible state affecting image availability.

Examples include:

Current visibility
Current restriction state

Historical moderation remains owned by the Governance domain.

System Metadata

Represents:

Operational metadata
Audit timestamps
Version metadata
Processing metadata
Required Business Information

The Image document shall authoritatively represent:

Asset identity
Asset ownership
Asset usage context
Current availability
Current visibility
Required System Metadata

The document shall support:

Processing traceability
Lifecycle management
Operational monitoring
Future schema evolution
Governance-Related Information

The Image document stores only effective governance outcomes.

It shall not contain:

Reports
Investigation history
Moderation decisions
Appeals
Enforcement history
Fields Intentionally Excluded

The Image document shall not contain:

Embedded post information
Embedded profile information
Embedded Herd information
Business resource history
Feed information
Governance history
Validation

The Image document preserves:

Media ownership
Independent asset lifecycle
Aggregate boundaries
Governance compatibility

Architecture establishes Images as independently owned media resources whose lifecycle remains separate from the business resources that consume them.

---

## Governance Domain Document Structures

### Governance Document Philosophy

Governance resources differ fundamentally from business resources.

Governance documents are authoritative historical records.

They preserve accountability rather than current business behavior.

Their primary architectural responsibilities are:

Auditability
Accountability
Enforcement
Historical preservation
Administrative traceability

Unlike business resources, governance records are intentionally append-oriented and historically significant.

---

### Reports

Purpose

The Report document represents the initiation of a governance workflow.

It records that a platform member has reported a business resource for review.

A Report does not represent a moderation decision.

Ownership

Owning Domain

Governance

The Governance domain exclusively owns:

Report lifecycle
Investigation lifecycle
Review workflow
Report disposition
Lifecycle

The Report document shall support:

Report submission
Review assignment
Investigation
Resolution
Closure

Reports shall never be rewritten to hide historical workflow progression.

Required Logical Sections
Identity

Represents:

Stable report identity
Governance case identity
Business Information

Represents:

Report reason
Report context
Report scope
Investigation inputs

This information represents governance business data rather than platform business resources.

Lifecycle Information

Represents:

Submission
Investigation progression
Review progression
Resolution
Closure

Lifecycle history is part of the authoritative governance record.

Governance Information

Represents:

Investigation ownership
Review status
Decision status
Escalation state
Resolution information

Unlike business resources, governance information forms the core business purpose of the document.

System Metadata

Represents:

Audit metadata
Operational metadata
Administrative traceability
Version metadata
Required Business Information

The Report document shall authoritatively represent:

Governance case
Investigation context
Resolution outcome
Required System Metadata

Supports:

Full auditability
Administrative traceability
Historical reconstruction
Future workflow evolution
Governance-Related Information

Governance information is the primary business information.

The document intentionally preserves:

Investigation progression
Review progression
Resolution history
Escalation history

Historical preservation is mandatory.

Fields Intentionally Excluded

The Report document shall not contain:

Embedded copies of business resources
Authentication information
Feed information
Current business resource ownership

Business resources remain owned by their originating domains.

Validation

The Report document preserves:

Governance ownership
Independent governance lifecycle
Historical integrity
Auditability

---

### Moderation Actions

Purpose

The Moderation Action document represents an authoritative governance decision affecting one or more business resources.

It records the decision itself rather than the business resource being governed.

Ownership

Owning Domain

Governance

The Governance domain exclusively owns:

Enforcement decisions
Administrative actions
Appeals (future evolution)
Enforcement history
Lifecycle

The Moderation Action document shall support:

Decision creation
Enforcement
Modification where permitted
Expiration where applicable
Historical preservation

Once recorded, moderation history shall remain permanently reconstructable.

Required Logical Sections
Identity

Represents:

Stable action identity
Enforcement identity
Business Information

Represents:

Enforcement action
Enforcement scope
Administrative rationale
Target context
Lifecycle Information

Represents:

Decision creation
Enforcement progression
Expiration
Completion

Historical progression shall remain preserved.

Governance Information

Represents:

Authority responsible
Decision rationale
Enforcement status
Appeal status (future evolution)
Administrative accountability

Governance information is the primary business purpose of the document.

System Metadata

Represents:

Audit metadata
Administrative traceability
Operational metadata
Version metadata
Required Business Information

The Moderation Action document shall authoritatively represent:

Enforcement decision
Enforcement scope
Administrative authority
Decision rationale
Current enforcement state
Required System Metadata

Supports:

Auditability
Accountability
Historical reconstruction
Future workflow evolution
Governance-Related Information

The document intentionally preserves:

Enforcement history
Decision rationale
Administrative authority
Historical progression

Unlike business resources, governance history is never discarded.

Fields Intentionally Excluded

The Moderation Action document shall not contain:

Embedded business resources
Authentication data
Feed information
Business ownership information

Business resources remain owned by their respective domains.

Validation

The Moderation Action document preserves:

Governance ownership
Historical integrity
Auditability
Administrative accountability
Authority preservation

---

# Reference Strategy

## Purpose of the Reference Strategy

The Reference Strategy defines the architectural rules governing how persisted business resources relate to one another.

Its objectives are to:

Preserve ownership boundaries.
Preserve aggregate independence.
Preserve domain isolation.
Enable navigation between related resources.
Support future architectural evolution.
Maintain consistency across the persistence model.

References describe relationships.

They do not establish authority.

## Reference Design Philosophy

The persistence model adopts an Ownership-Oriented Reference Strategy.

Reference relationships shall:

- Preserve domain ownership.
- Preserve aggregate boundaries.
- Preserve lifecycle independence.
- Preserve stable resource identity.
- Minimize coupling.

Implementation details remain outside the scope of this architecture.

## Reference Ownership Principles

Reference relationships shall follow the following principles.

RS-01

Every referenced resource retains its original owner.

RS-02

References never transfer ownership.

RS-03

Owning domains remain solely responsible for:

lifecycle,
validation,
consistency,
governance integration.
RS-04

Consumers may reference resources.

Consumers never become authoritative owners.

RS-05

Reference direction never determines business authority.

Authority always follows ownership.

## Aggregate Boundary Preservation

References shall preserve approved aggregate boundaries.

An aggregate may reference resources owned by another aggregate.

It shall never absorb them into its own authoritative state.

Aggregate boundaries remain responsible for protecting:

invariants,
lifecycle,
ownership,
consistency.

References connect aggregates.

They do not merge aggregates.

## Reference Direction Rules

Reference direction represents dependency rather than ownership.

The following principles are authoritative.

RR-01

References flow toward authoritative resources.

RR-02

Referenced resources remain independently valid.

RR-03

Reference direction shall follow approved domain dependency rules.

RR-04

Reverse relationships shall never be required for ownership enforcement.

RR-05

Reference direction shall minimize coupling between domains.

## Intra-Aggregate vs Cross-Aggregate References

Intra-Aggregate References

Resources sharing:

owner,
lifecycle,
aggregate,

may reference one another freely when required by the aggregate model.

These references remain internal to aggregate consistency.

Cross-Aggregate References

Cross-aggregate references shall remain lightweight relationships.

They shall preserve:

aggregate independence,
lifecycle independence,
ownership separation.

Cross-aggregate references shall never:

synchronize lifecycle,
duplicate authoritative state,
redefine ownership.

## Intra-Domain vs Cross-Domain References

Intra-Domain References

References inside the same domain remain governed by the owning domain.

The domain controls:

reference validity,
lifecycle compatibility,
consistency.

Cross-Domain References

Cross-domain references exist only where business relationships require them.

Cross-domain references:

preserve module boundaries,
preserve ownership,
preserve authority separation.

Cross-domain references shall never allow one domain to modify another domain's authoritative state.

## Business References vs Governance References

Business References

Business references describe normal platform relationships.

Examples include relationships between:

users,
posts,
comments,
communities,
memberships,
media.

Business references exist solely to support platform functionality.

Governance References

Governance references identify governance actors and governance targets.

Governance references do not establish business ownership.

Governance records remain independently owned by the Governance domain while referencing externally owned business resources.

Governance authority remains independent from business ownership.

## Bidirectional vs Unidirectional Reference Philosophy

The persistence architecture adopts a Unidirectional-by-Default philosophy.

Bidirectional references increase:

coupling,
synchronization requirements,
consistency complexity.

Unidirectional references preserve:

ownership,
simplicity,
modularity,
evolutionary flexibility.

Bidirectional references may only be introduced when a future approved architectural requirement demonstrates a clear business need.

Implementation convenience alone is insufficient justification.

## Reference Stability Principles

Every persisted reference shall target a stable resource identity.

Reference targets shall remain:

immutable,
globally identifiable,
independent of mutable business attributes.

Business information may evolve.

Reference identity remains stable.

Stable references reduce migration complexity and preserve long-term compatibility.

## Reference Lifecycle Considerations

References shall not own lifecycle.

Each referenced resource remains responsible for its own lifecycle progression.

Lifecycle changes affecting referenced resources shall not automatically redefine referencing resource ownership.

References must remain compatible with:

soft deletion,
governance restrictions,
restoration,
future retention policies.

Reference architecture shall preserve lifecycle independence across all domains.

## Reference Consistency Rules

Reference consistency shall be maintained by the owning application workflows rather than by shared ownership.

Consistency principles:

RC-01

Only authoritative resources may be referenced.

RC-02

References shall remain logically valid throughout the resource lifecycle.

RC-03

Reference validation belongs to the owning application workflows.

RC-04

Reference consistency shall never require shared ownership.

RC-05

Reference consistency shall preserve aggregate independence.

## Circular Reference Prevention

Circular references increase:

coupling,
dependency complexity,
lifecycle synchronization,
future migration difficulty.

The persistence model therefore adopts the following rules.

CR-01

Circular ownership relationships are prohibited.

CR-02

Circular aggregate dependencies are prohibited.

CR-03

Reference graphs shall remain compatible with the approved acyclic module dependency model.

CR-04

Cross-domain references shall never introduce dependency cycles.

CR-05

Future schema evolution shall preserve acyclic architectural boundaries.

## Cross-Domain Dependency Alignment

Reference relationships shall align with the approved backend dependency model.

References may exist only where domain dependencies are already architecturally permitted.

Reference relationships shall never introduce new architectural dependencies.

The persistence model therefore remains subordinate to:

approved backend module boundaries,
approved capability contracts,
approved ownership model,
approved governance boundaries.

Persistence reflects architecture.

It never defines architecture.

## Domain Reference Strategy

Identity

Identity resources become the primary reference targets for participation and accountability.

Identity remains the authoritative owner of identity information.

Community

Community references identify participation context while preserving Community ownership of Herds and memberships.

Content

Content references connect authors, discussions, communities, and media while preserving Content ownership.

Media

Business resources reference media assets.

Media ownership remains independent of attachment.

Governance

Governance references identify governance actors and governed resources.

Governance remains the owner of governance records only.

## Feed Compatibility

Feed remains a derived read-only domain.

Feed consumes authoritative references from business domains.

Feed owns no authoritative references or persisted business relationships.

## Reference Stability Principles

References target stable resource identities.

Reference identity remains independent of mutable business attributes.

## Reference Lifecycle Principles

References preserve lifecycle independence.

Lifecycle changes never transfer ownership.

## Reference Consistency Rules

Reference consistency remains the responsibility of approved application workflows.

Shared ownership is prohibited.

## Circular Reference Prevention

Reference architecture shall remain acyclic.

Circular ownership and circular domain dependency models are prohibited.

## Future Evolution Strategy

Reference evolution shall:

- Preserve ownership boundaries.
- Preserve aggregate independence.
- Preserve identifier stability.
- Preserve API compatibility whenever practical.
- Extend rather than replace the approved persistence model.

## Reference Strategy Validation

The reference architecture confirms:

- Ownership boundaries remain preserved.
- Aggregate boundaries remain preserved.
- Domain dependencies remain unchanged.
- Governance authority remains independent.
- Feed remains derived.
- Future schema evolution remains compatible with the approved architecture.

