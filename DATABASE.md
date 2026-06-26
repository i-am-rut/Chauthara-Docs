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
