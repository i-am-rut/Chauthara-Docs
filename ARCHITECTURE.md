## Architecture vs Implementation

Architecture approval and implementation sequencing are independent concerns.

Certain architectural areas may be approved before implementation.

Implementation may occur through phased delivery:

- Phase 1 — Core Platform
- Phase 2 — Governance & Operations

Deferred implementation does not invalidate approved architecture.

Approved architecture remains authoritative regardless of implementation phase.

# Architecture Drivers

## Functional Drivers
### FD-01 — Identity Lifecycle Management
#### Description
Support the complete account lifecycle:

Registration
Authentication
Session management
Email verification
Password recovery
Profile management

#### Why It Matters
Identity is the foundation of all platform participation.

#### Related Features
User Accounts
User Profiles

#### Related Domains
Identity

#### Architectural Impact
Architecture must provide:

Centralized authentication
Identity-aware authorization
Account lifecycle workflows
Separation between account credentials and public profile representation

### FD-02 — Social Relationship Management
#### Description
Support user-to-user follow relationships.

#### Why It Matters
The Following Feed depends entirely on the social graph.

#### Related Features
Follow System

#### Related Domains
Social Graph

#### Architectural Impact
Architecture must support:

Efficient relationship creation/removal
Relationship queries
Feed relationship traversal

### FD-03 — User Content Creation And Discussion
#### Description
Support creation and management of:

Posts
Comments
Replies
Voting

#### Why It Matters
Discussion is the primary platform activity.

#### Related Features
Personal Posting
Comments & Replies
HypeUp/HypeDown

#### Related Domains
Content

#### Architectural Impact
Architecture must support:

Hierarchical discussions
Content ownership
Content lifecycle management
Content engagement tracking

### FD-04 — Community Management
#### Description
Support creation and operation of Herd communities.

#### Why It Matters
Communities are a primary organizational structure of the platform.

#### Related Features
Herd Creation
Herd Membership
Shepherd Assignment

#### Related Domains
Community

#### Architectural Impact
Architecture must support:

Community identity management
Membership management
Governance role assignment
Community-scoped operations

### FD-05 — Feed Composition And Consumption
#### Description
Support retrieval of:

Following Feed
Herd Feed

#### Why It Matters
Feeds are the primary content consumption mechanism.

#### Related Features
Following Feed
Herd Feed

#### Related Domains
Feed

#### Architectural Impact
Architecture must support:

Content aggregation
Efficient feed queries
Deterministic chronological ordering
Future feed evolution without redesign

### FD-06 — Media Management
#### Description
Support image upload, retrieval, attachment, and removal.

#### Why It Matters
Images are used by:

Profiles
Herds
Posts

#### Related Features
Image Uploads

#### Related Domains
Media

#### Architectural Impact
Architecture must support:

Media lifecycle management
Media ownership tracking
External media storage integration

### FD-07 — Governance And Moderation Workflows
#### Description
Support:

Reporting
Moderation actions
Escalation
Enforcement
Governance oversight

#### Why It Matters
Governance is a first-class MVP capability, not a future enhancement.

#### Related Features
Reporting System
Shepherd Moderation
Platform Moderation

#### Related Domains
Governance

#### Architectural Impact
Architecture must support:

Governance workflows
Role-based authority
Escalation paths
Enforcement actions
Governance visibility boundaries
Audit history

### FD-08 — Ownership And Lifecycle Enforcement
#### Description
Support ownership, stewardship, lifecycle, and moderation boundaries defined in the MVP model.

#### Why It Matters
Ownership and governance are core business rules.

#### Related Features
Applies platform-wide.

#### Related Domains
Identity
Social Graph
Content
Community
Media
Governance

#### Architectural Impact
Architecture must consistently enforce:

Ownership boundaries
Lifecycle transitions
Governance overrides
Resource authority rules

## Quality Drivers
### QD-01 — Maintainability
#### Description
Architecture should be understandable, modular, and easy to evolve.

#### Why It Matters
Project is initially developed and maintained by a solo developer.

#### Priority
Critical

#### Architectural Impact
Favor:

Clear domain boundaries
Simple abstractions
Consistent patterns
Low coupling

### QD-02 — Simplicity
#### Description
Prefer the simplest architecture that satisfies MVP requirements.

#### Why It Matters
Explicitly aligned with Evolutionary Architecture principles.

#### Priority
Critical

#### Architectural Impact
Avoid:

Premature microservices
Event-driven complexity
Infrastructure-heavy solutions

### QD-03 — Security
#### Description
Protect user identities, authentication flows, media access, and governance operations.

#### Why It Matters
Identity and moderation systems are platform-critical.

#### Priority
Critical

#### Architectural Impact
Require:

Authentication
Authorization
Secure session handling
Governance access controls

### QD-04 — Reliability
#### Description
Core platform workflows should function predictably.

#### Why It Matters
Users must trust content, communities, and governance outcomes.

#### Priority
High

#### Architectural Impact
Require:

Consistent data handling
Failure recovery
Defensive validation

### QD-05 — Performance
#### Description
Support responsive content retrieval and interaction.

#### Why It Matters
Feeds, discussions, and community browsing are frequent operations.

#### Priority
High

#### Architectural Impact
Prioritize:

Efficient query patterns
Feed retrieval efficiency
Appropriate indexing strategy

### QD-06 — Auditability
#### Description
Governance actions must be traceable.

#### Why It Matters
Governance hierarchy depends on accountability.

#### Priority
High

#### Architectural Impact
Require:

Moderation history
Enforcement records
Governance action tracking

### QD-07 — Extensibility
#### Description
Allow future capabilities without major redesign.

#### Why It Matters
Future releases are expected to expand platform functionality.

#### Priority
High

#### Architectural Impact
Favor:

Stable domain boundaries
Modular services
Evolvable APIs

### QD-08 — Developer Experience
#### Description
Architecture should support efficient development and debugging.

#### Why It Matters
The project is intentionally designed as a learning platform.

#### Priority
Medium

#### Architectural Impact
Favor:

Predictable structure
Consistent conventions
Simple deployment workflows

### QD-09 — Operability
#### Description
Application should be easy to deploy, monitor, and maintain.

#### Why It Matters
Operational complexity should remain proportional to MVP scale.

#### Priority
Medium

#### Architectural Impact
Favor:

Simple deployment topology
Centralized logging
Straightforward environment management

### QD-10 — Scalability
#### Description
Architecture should support moderate growth without immediate redesign.

#### Why It Matters
Growth is possible but not assumed.

#### Priority
Medium

#### Architectural Impact
Favor:

Horizontal growth paths
Stateless application design where practical
Scalable storage patterns

## Constraints
### C-01 — MVP Scope Constraint
#### Description
Architecture must support approved MVP functionality only.

#### Source
PROJECT_CONTEXT.md
FEATURES.md

#### Architectural Impact
No architecture for future hypothetical features.
No infrastructure introduced solely for future scale.
Architecture must remain proportional to MVP scope.

### C-02 — Approved Domain Boundary Constraint
#### Description
Architecture must preserve approved business domains.

#### Source
DATA_MODEL.md
API_CONTRACTS.md

#### Architectural Impact
Architecture should align with:

Identity
Social Graph
Content
Community
Feed
Media
Governance

Domain boundaries should not be merged arbitrarily.

### C-03 — Governance Hierarchy Constraint
#### Description
Architecture must preserve approved governance authority.

#### Source
DATA_MODEL.md
API_CONTRACTS.md

#### Architectural Impact
Architecture must enforce:

Law
↓
Platform Administrator
↓
Herd Owner
↓
Shepherd
↓
Member

Governance rules cannot be bypassed by implementation choices.

### C-04 — Ownership Boundary Constraint
#### Description
Architecture must preserve approved ownership responsibilities.

#### Source
DATA_MODEL.md

#### Architectural Impact
Ownership, stewardship, and moderation authority must remain distinct concerns.

### C-05 — API Contract Constraint
#### Description
Approved API contracts are authoritative.

#### Source
API_CONTRACTS.md

#### Architectural Impact
Architecture supports APIs.

APIs should not be redesigned to fit implementation preferences.

### C-06 — Technology Constraint
#### Description
Implementation target is MERN-based.

#### Source
PROJECT_CONTEXT.md

#### Architectural Impact
Architecture should remain compatible with:

Next.js
TypeScript
Node.js
Express
MongoDB

Technology choices should not require platform replacement.

### C-07 — Solo Developer Constraint
#### Description
Architecture must remain operable by a single developer.

#### Source
PROJECT_CONTEXT.md

#### Architectural Impact
Avoid:

Excessive service decomposition
Operationally expensive infrastructure
Complex deployment topologies

### C-08 — Operational Simplicity Constraint
#### Description
Operational burden must remain proportional to MVP scale.

#### Source
Quality Drivers

#### Architectural Impact
Prefer:

Fewer moving parts
Simpler deployments
Reduced operational overhead

### C-09 — Deployment Reality Constraint
#### Description
Architecture must support cost-conscious deployment.

#### Source
PROJECT_CONTEXT.md

#### Architectural Impact
Architecture should not require:

Large managed-service ecosystems
Complex orchestration platforms
Enterprise infrastructure

### C-10 — Learning Value Constraint
#### Description
Project serves both product goals and learning goals.

#### Source
PROJECT_CONTEXT.md

#### Architectural Impact
Architectural decisions should expose important real-world concepts without introducing unnecessary complexity.

## Architectural Principles
### AP-01 — Simplicity First
#### Principle Statement
Choose the simplest architecture that satisfies approved requirements.

#### Rationale
Simplicity is the primary architectural optimization goal.

#### Architectural Impact
Prefer:
Monolithic deployment
Simple service boundaries
Direct communication patterns

Avoid speculative complexity.

### AP-02 — Evolutionary Architecture
#### Principle Statement
Design for current requirements while preserving future growth paths.

#### Rationale
Architecture should evolve when requirements evolve.

#### Architectural Impact
Avoid premature optimization.

Document future scaling paths instead of implementing them immediately.

### AP-03 — Domain-Driven Boundaries
#### Principle Statement
Architecture should align with approved business domains.

#### Rationale
Business boundaries are more stable than technical boundaries.

#### Architectural Impact
Backend organization, APIs, and data ownership should reflect approved domains.

### AP-04 — API-First Thinking
#### Principle Statement
API contracts are authoritative external system contracts.

#### Rationale
Approved API surface already represents validated business behavior.

#### Architectural Impact
Implementation should serve APIs rather than redesign them.

### AP-05 — Ownership Boundary Preservation
#### Principle Statement
Ownership boundaries must remain explicit throughout the architecture.

#### Rationale
Ownership is a core platform concept.

#### Architectural Impact
Resource ownership rules must remain enforceable at every architectural layer.

### AP-06 — Governance-Aware Design
#### Principle Statement
Governance is a first-class platform capability.

#### Rationale
Moderation is part of core platform behavior.

#### Architectural Impact
Governance workflows must be represented explicitly rather than treated as exceptional cases.

### AP-07 — Security By Default
#### Principle Statement
Secure behavior should be the default behavior.

#### Rationale
Identity and governance systems require strong protection.

#### Architectural Impact
Favor:

Authentication-first workflows
Explicit authorization checks
Least-privilege access

### AP-08 — Explicit Authority Boundaries
#### Principle Statement
Authority must be explicit and verifiable.

#### Rationale
Governance depends on clearly defined authority.

#### Architectural Impact
Avoid implicit permission models.

Authority decisions should be traceable.

### AP-09 — Independent Evolvability
#### Principle Statement
Domains should evolve with minimal impact on unrelated domains.

#### Rationale
Supports maintainability and future growth.

#### Architectural Impact
Favor low coupling between domains.

### AP-10 — Operational Simplicity
#### Principle Statement
Operational complexity should scale only when justified by real requirements.

#### Rationale
Operations should not become the primary maintenance burden.

#### Architectural Impact
Prefer operationally simple solutions by default.

## Architectural Implications
The drivers establish the following architecture expectations:

- Architecture should be organized around approved business domains.
- Governance must be treated as a first-class architectural concern.
- Ownership, lifecycle, and moderation boundaries must be enforceable by design.
- Simplicity is preferred over speculative scalability.
- Security must be embedded into identity, authorization, and governance workflows.
- Feed retrieval and discussion operations require focused performance consideration.
- Future evolution should occur through extension of existing domain boundaries rather than architectural replacement.
- All future ADRs should be evaluated against these functional and quality drivers.

Architecture readiness remains high because MVP specifications, ownership boundaries, lifecycle definitions, governance rules, and API boundaries are already stable.

The constraints and principles establish the following expectations:

Architecture should remain a modular monolith unless requirements prove otherwise.
Business domains should become primary architectural boundaries.
Governance concerns must be represented explicitly throughout the system.
API contracts remain authoritative architectural inputs.
Security and authorization must be integrated into all architectural layers.
Simplicity takes precedence over speculative scalability.
Future scaling paths should be documented rather than prematurely implemented.
All future ADRs should explicitly reference these drivers when evaluating alternatives.

--- 

# Backend Architecture Definition
## Backend Architectural Style

### Architectural Style
The backend architecture follows a Domain-Oriented Modular Monolith.

The system is implemented as a single deployable application while organizing business logic around approved business domains.

Approved backend domains:

- Identity
- Social Graph
- Content
- Community
- Feed
- Media
- Governance

Operationally the platform remains a monolith.

Architecturally the platform is modular.

---

### Architectural Style Rationale
The Domain-Oriented Modular Monolith was selected because it:

- Aligns with Simplicity First.
- Aligns with Evolutionary Architecture.
- Preserves approved domain boundaries.
- Preserves governance boundaries.
- Preserves ownership boundaries.
- Minimizes operational complexity.
- Supports solo developer operation.
- Provides a clear future evolution path.

The architecture intentionally avoids microservices and service-oriented architectures during MVP development.

---

### Architectural Characteristics
Characteristics:

- Single deployable backend application.
- Single primary database.
- Domain-oriented internal organization.
- Explicit module boundaries.
- API-first design.
- Governance-aware architecture.
- Ownership-aware architecture.
- Low operational overhead.
- Evolution-friendly structure.

---

### Architectural Boundaries
Backend modules align with approved MVP domains:

- Identity
- Social Graph
- Content
- Community
- Feed
- Media
- Governance

Domain boundaries remain authoritative.

Cross-domain access must occur through explicit module contracts rather than direct internal dependency chains.

---

### Architectural Responsibilities
Each module owns:

- Business rules
- Lifecycle enforcement
- Ownership enforcement
- Authorization rules
- Governance constraints
- Domain-specific workflows

The backend architecture remains responsible for enforcing approved governance hierarchy and ownership boundaries.

---

### Evolution Strategy
MVP:
- Single deployable modular monolith.

Near-Term:
- Strengthen module isolation.
- Increase internal contract discipline.

Future:
- Extract individual modules into independent services only when justified by measurable operational requirements.

Architectural evolution follows the Evolutionary Architecture principle.

---

## Backend Domain Architecture

### Domain Design Principles

The backend shall follow a Domain-Oriented Modular Monolith architecture.

Domain boundaries shall align with approved business domains rather than technical layers.

Every domain shall:

- Own its business resources.
- Own its aggregate lifecycles.
- Own its business rules.
- Expose capabilities through defined interfaces.
- Prevent direct modification of resources owned by other domains.

Domains may reference information from other domains but may not assume ownership authority.

Feed remains a derived domain.

Governance remains an independent authority domain.

---

### Approved Backend Domains

#### Identity

Purpose:

Manage platform identity and participation eligibility.

Owns:

- User Account
- User Profile

---

#### Social Graph

Purpose:

Manage user-to-user relationships.

Owns:

- Follow Relationship

---

#### Content

Purpose:

Manage discussion and contribution content.

Owns:

- Post
- Comment
- Vote

---

#### Community

Purpose:

Manage communities and participation structures.

Owns:

- Herd
- Herd Membership
- Shepherd Assignment

---

#### Media

Purpose:

Manage reusable media assets.

Owns:

- Image

---

#### Governance

Purpose:

Manage reporting, moderation, enforcement, escalation, and oversight workflows.

Owns:

- Report
- Moderation Action

---

#### Feed

Purpose:

Provide derived content consumption views.

Owns:

No authoritative business resources.

---

### Domain Responsibilities

#### Identity

Business Responsibilities
Account lifecycle management
Authentication workflows
Identity verification
Profile management
Identity retrieval

Owned Resources
User Profile

Owned Aggregates
User Identity Aggregate

Ownership Responsibilities
Enforce:
User ownership of accounts
User ownership of profiles

Governance Responsibilities
Expose governance targets:
Profile restriction
Account enforcement
Does not execute governance.

Lifecycle Responsibilities
Owns:
User Account lifecycle
User Profile lifecycle

#### Social Graph

Business Responsibilities
Follow creation
Follow removal
Relationship discovery

Owned Resources
Follow Relationship

Owned Aggregates
Follow Aggregate

Ownership Responsibilities
Enforce:
Following user ownership
Governance Responsibilities
Expose follow relationships as governance targets.

Lifecycle Responsibilities
Owns:
Follow lifecycle

#### Content

Business Responsibilities
Publish content
Manage discussions
Manage voting
Maintain authorship

Owned Resources
Post
Comment
Vote

Owned Aggregates
Personal Content Aggregate
Discussion Aggregate
Voting Aggregate

Ownership Responsibilities
Enforce:
Content ownership
Comment ownership
Vote ownership

Governance Responsibilities
Expose moderation targets:
Posts
Comments
Votes

Lifecycle Responsibilities
Owns:
Post lifecycle
Comment lifecycle
Vote lifecycle

#### Community

Business Responsibilities
Herd management
Membership management
Shepherd assignment

Owned Resources
Herd
Membership
Shepherd Assignment

Owned Aggregates
Community Aggregate
Membership Aggregate

Ownership Responsibilities
Enforce:
Herd ownership
Membership ownership
Shepherd assignment authority

Governance Responsibilities
Provide governance structure:
Herd Owner authority
Shepherd authority
Does not execute governance workflows.

Lifecycle Responsibilities
Owns:
Herd lifecycle
Membership lifecycle
Shepherd lifecycle

#### Media

Business Responsibilities
Image upload
Image attachment
Image removal

Owned Resources
Image

Owned Aggregates
Media Aggregate

Ownership Responsibilities
Enforce image ownership.

Governance Responsibilities
Expose images as moderation targets.

Lifecycle Responsibilities
Owns image lifecycle.

#### Governance

Business Responsibilities
Reporting
Moderation
Enforcement
Escalation
Oversight

Owned Resources
Report
Moderation Action

Owned Aggregates
Reporting Aggregate
Moderation Aggregate
Ownership Responsibilities
Enforce platform ownership of governance artifacts.

Governance Responsibilities
Primary governance owner.

Lifecycle Responsibilities
Owns:
Report lifecycle
Moderation Action lifecycle

#### Feed

Business Responsibilities
Following Feed generation
Herd Feed generation
Feed retrieval

Owned Resources
Feed

Owned Aggregates
None

Ownership Responsibilities
None

Governance Responsibilities
Consume governance outcomes.
Does not perform governance.

Lifecycle Responsibilities
None
Feed owns no business lifecycle.

---

### Domain Relationships

#### Identity
Downstream Consumers
| Consumer     | Dependency Type         | Rationale                                     |
| ------------ | ----------------------- | --------------------------------------------- |
| Social Graph | Reference Dependency    | Follow relationships reference users          |
| Content      | Reference Dependency    | Content authors are users                     |
| Community    | Reference Dependency    | Herd participation references users           |
| Media        | Reference Dependency    | Media ownership references users              |
| Governance   | Reference Dependency    | Governance actors and targets reference users |
| Feed         | Derived Data Dependency | Feed visibility depends on user identity      |

Upstream Dependencies
None.
Identity is a foundational domain.

#### Social Graph
Upstream Dependencies
| Provider | Dependency Type      |
| -------- | -------------------- |
| Identity | Reference Dependency |

Downstream Consumers
| Consumer   | Dependency Type         | Rationale                                    |
| ---------- | ----------------------- | -------------------------------------------- |
| Feed       | Derived Data Dependency | Following Feed depends on follows            |
| Governance | Governance Dependency   | Follow relationships may require enforcement |


#### Content
Upstream Dependencies
| Provider  | Dependency Type      |
| --------- | -------------------- |
| Identity  | Reference Dependency |
| Community | Reference Dependency |

Downstream Consumers
| Consumer   | Dependency Type         |
| ---------- | ----------------------- |
| Feed       | Derived Data Dependency |
| Governance | Governance Dependency   |

Rationale
Feed derives content visibility.
Governance moderates content.
Neither owns content.


#### Community
Upstream Dependencies
| Provider | Dependency Type      |
| -------- | -------------------- |
| Identity | Reference Dependency |

Downstream Consumers
| Consumer   | Dependency Type         |
| ---------- | ----------------------- |
| Content    | Workflow Dependency     |
| Feed       | Derived Data Dependency |
| Governance | Governance Dependency   |

Rationale
Content creation inside Herds depends on Community membership.
Feed visibility depends on Herd participation.
Governance actions may target Herds and memberships.

#### Media
Upstream Dependencies
| Provider | Dependency Type      |
| -------- | -------------------- |
| Identity | Reference Dependency |

Downstream Consumers
| Consumer   | Dependency Type       |
| ---------- | --------------------- |
| Identity   | Workflow Dependency   |
| Content    | Workflow Dependency   |
| Community  | Workflow Dependency   |
| Governance | Governance Dependency |

Rationale
Profiles, Posts, and Herds may attach media.
Governance may restrict media.
Media remains independently owned.

#### Governance
Upstream Dependencies
| Provider     | Dependency Type       |
| ------------ | --------------------- |
| Identity     | Reference Dependency  |
| Content      | Governance Dependency |
| Community    | Governance Dependency |
| Media        | Governance Dependency |
| Social Graph | Governance Dependency |

Downstream Consumers
None.
Governance is a terminal authority domain.

Rationale
Governance consumes information from other domains.
Other domains should not depend on Governance for normal business operation.
This is a major architectural rule.

#### Feed
Upstream Dependencies
| Provider     | Dependency Type         |
| ------------ | ----------------------- |
| Identity     | Derived Data Dependency |
| Social Graph | Derived Data Dependency |
| Content      | Derived Data Dependency |
| Community    | Derived Data Dependency |
| Governance   | Derived Data Dependency |

Downstream Consumers
None.
Feed is a presentation-oriented derived domain.

---

### Domain Authority Boundaries

#### Identity

Owns
User Account
User Profile
Identity lifecycle

References
Images

Does Not Own
Follows
Posts
Herds
Reports

Must Not Modify
Follow relationships
Posts
Memberships
Moderation actions

#### Social Graph

Owns
Follow relationships

References
User identities

Does Not Own
Profiles
Posts
Herds

Must Not Modify
User profiles
Content
Community state

#### Content

Owns
Posts
Comments
Votes

References
Users
Herds
Media

Does Not Own
Herd lifecycle
Membership lifecycle
Governance lifecycle

Must Not Modify
Herd membership
Shepherd assignments
Reports
Moderation actions

#### Community

Owns
Herds
Memberships
Shepherd Assignments

References
Users
Media

Does Not Own
Posts
Votes
Reports

Must Not Modify
Content lifecycle
Governance lifecycle

#### Media

Owns
Images

References
Users
Posts
Herds
Profiles

Does Not Own
Profiles
Posts
Herds

Must Not Modify
Profile state
Post state
Herd state

#### Governance

Owns
Reports
Moderation Actions
Enforcement workflows
Escalation workflows

References
Users
Posts
Comments
Herds
Images
Memberships

Does Not Own
Governed resources

Must Not Modify Directly
Business ownership
Content ownership
Community ownership

Important Clarification
Governance may:
Restrict
Remove
Restore
Escalate

But governance never becomes the owner.
Ownership remains with originating domains.
This preserves Ownership Boundary constraints.

#### Feed

Owns
Nothing authoritative.

References
Identity
Social Graph
Content
Community
Governance

Does Not Own
Any business resource.

Must Not Modify
Anything.
Feed is read-only.
Always.

---

### Authority Boundary Rules

These rules become authoritative.

Rule DB-01
A domain may modify only resources it owns.

Rule DB-02
A domain may reference another domain's resources.
Reference does not imply authority.

Rule DB-03
Cross-domain lifecycle transitions are prohibited.
Only the owning domain may execute lifecycle transitions.

Rule DB-04
Feed never becomes a source-of-truth domain.

Rule DB-05
Governance never becomes a business ownership domain.

Rule DB-06
Identity remains the root identity authority.

Rule DB-07
Community remains the sole authority for:
Herd lifecycle
Membership lifecycle
Shepherd lifecycle

Rule DB-08
Content remains the sole authority for:
Posts
Comments
Votes

---

### Governance Placement

Governance is an independent domain.

Governance owns:

- Reporting
- Enforcement
- Escalation
- Oversight

Governance targets include:

- Profiles
- Posts
- Comments
- Herds
- Memberships
- Images

Governance actions never transfer ownership.

Governance authority follows:

Law
↓
Platform Administrator
↓
Herd Owner
↓
Shepherd
↓
Member

Governance Ownership Model
Governance Owns
Governance Workflows

Including:

Report submission
Report review
Report dismissal
Escalation
Enforcement
Appeal review
Governance oversight
Governance Resources

Owns:

Report
Moderation Action

These are already platform-owned entities.

Governance Lifecycles

Owns:

Report lifecycle
Moderation Action lifecycle

No other domain may change governance state.

Governance Authority

Owns:

Enforcement decisions
Escalation decisions
Override decisions
Restoration decisions
Governance Does NOT Own

Governance never owns:

User Profiles
Posts
Comments
Votes
Herds
Memberships
Images

These remain owned by their original domains.

Governance Targets
Identity Domain

Governance Targets:

User Profile

Examples:

Profile restriction
Profile restoration
Content Domain

Governance Targets:

Post
Comment
Vote

Examples:

Content removal
Content restoration
Community Domain

Governance Targets:

Herd
Membership
Shepherd Assignment

Examples:

Herd restriction
Membership removal
Shepherd removal
Media Domain

Governance Targets:

Images

Examples:

Media restriction
Media removal
Social Graph Domain

Governance Targets:

Follow Relationships

Possible but uncommon.

MVP governance generally focuses on:

Profiles
Content
Communities
Media
Governance Integration Points

Governance must be able to:

Query

Information about:

Profiles
Posts
Comments
Herds
Memberships
Images
Act Upon

Governance outcomes affecting:

Visibility
Participation
Membership
Enforcement state
Audit

Historical moderation activity.

Governance Workflow Boundaries
Reporting Workflow

Owned By:

Governance

Consumes:

Identity
Content
Community
Media
Enforcement Workflow

Owned By:

Governance

Targets:

Identity
Content
Community
Media
Escalation Workflow

Owned By:

Governance

Hierarchy:

Shepherd
→ Herd Owner
→ Platform Administrator

This is entirely governance-owned.

Oversight Workflow

Owned By:

Governance

Targets:

Moderators
Shepherds
Herd Owners
Governance Escalation Boundaries
Shepherd

Can govern:

Herd-local content
Herd-local membership

Cannot govern:

Platform-wide identity
Platform-wide restrictions
Herd Owner

Can govern:

Entire herd
Shepherd actions

Cannot govern:

Platform-wide governance
Platform Administrator

Can govern:

Entire platform

Can override:

Herd Owner decisions
Shepherd decisions
Law

External authority.

Outside application architecture.

Must supersede platform decisions.

Governance Placement Decision

Governance is:

Independent Domain
Independent Lifecycle Owner
Independent Workflow Owner
Independent Authority Owner
Not Embedded Inside Any Other Domain

This is now authoritative.

---

### Feed Domain Position

Feed is a derived domain.

Feed:

- Owns no authoritative resources.
- Owns no aggregates.
- Owns no lifecycle.
- Owns no governance workflows.

Feed may:

- Compose content views.
- Apply visibility rules.
- Retrieve feed items.

Feed may not modify any domain state.

Feed Ownership Analysis
Does Feed Own Business Data?

No.

Feed contains projections of:

Posts
Authors
Herds
Membership visibility
Governance visibility

All owned elsewhere.

Does Feed Own Aggregates?

No.

Feed Aggregate does not exist.

Approved aggregate model contains no Feed aggregate.

Does Feed Own Lifecycle?

No.

Feed has no lifecycle.

Posts do.

Memberships do.

Feed does not.

Does Feed Own Governance?

No.

Feed consumes governance outcomes.

Feed never creates governance decisions.

Feed Responsibilities

Feed owns exactly four concerns.

Responsibility 1

Feed Composition

Example:

Following Feed composition.

Responsibility 2

Feed Visibility

Determine which items appear.

Responsibility 3

Feed Ordering

Newest-first ordering.

Approved by Feed API specification.

Responsibility 4

Feed Retrieval

Expose feed views.

Feed Limitations

Feed may NOT:

Create Content
Modify Content
Delete Content
Modify Memberships
Modify Profiles
Modify Governance State
Own Lifecycle State
Own Business Rules

Feed only applies business rules created elsewhere.

Feed Dependencies

Feed depends on:

Domain	Reason
Identity	Author visibility
Social Graph	Following Feed
Content	Feed items
Community	Herd Feed
Governance	Visibility filtering

Feed consumes all domains.

No domain consumes Feed.

Feed Authority Boundary
Feed Owns
Feed composition rules
Feed retrieval rules
Feed References
Profiles
Follows
Posts
Herds
Memberships
Governance outcomes
Feed Does Not Own

Any business resource.

Feed Must Not Modify

Anything.

Feed remains read-only.

Always.

Feed Position Decision

Feed is officially classified as:

Derived Domain

Characteristics:

Read Only
No Ownership
No Lifecycle
No Governance Authority
No Aggregate Ownership

Its sole purpose is consumption.

---

### Domain Dependency Rules

1. A domain may modify only resources it owns.
2. Cross-domain ownership is prohibited.
3. Cross-domain lifecycle transitions are prohibited.
4. Feed shall remain read-only.
5. Governance shall remain independent.
6. Identity remains the root identity authority.
7. Community remains the sole authority for Herd and Membership lifecycles.
8. Content remains the sole authority for Post, Comment, and Vote lifecycles.

---

## Backend Module Boundaries
### Backend Module Boundary Principles
#### MBP-01 — Domain Alignment
Every module maps to exactly one approved domain.
No module may span multiple domains.

#### MBP-02 — Exclusive Ownership
A module owns:
resources
aggregates
lifecycle rules
business rules
workflows
Only the owning module may modify them.

#### MBP-03 — Read Is Not Ownership
Modules may read information from other modules.
Reading never transfers ownership.

#### MBP-04 — Governance Does Not Own Governed Resources
Governance acts upon resources.
Governance never owns them.

#### MBP-05 — Feed Owns No Authoritative State
Feed consumes information.
Feed does not own information.

#### MBP-06 — Dependency Direction Matters
Modules depend on capabilities.
Not internal implementation.

#### MBP-07 — No Shared Business Logic
Business rules belong to exactly one module.

#### MBP-08 — Independent Evolvability
Modules should evolve independently whenever possible.

#### MBP-09 — Future Extraction Readiness
Every module should remain a potential future extraction candidate.
No extraction is planned.
Readiness is required.

#### MBP-10 — Authority Is Explicit
Authority boundaries remain visible in architecture.
No implicit governance privileges.

### Backend Module Inventory
Approved Module Inventory
| Module       | Classification             |
| ------------ | -------------------------- |
| Identity     | Core Business Module       |
| Social Graph | Core Business Module       |
| Content      | Core Business Module       |
| Community    | Core Business Module       |
| Feed         | Derived Module             |
| Media        | Supporting Business Module |
| Governance   | Authority Module           |


### Module Ownership Matrix
#### Identity Module
##### Purpose
Manage platform identity and participation eligibility.

##### Owned Resources
User Profile

##### Owned Aggregates
User Identity Aggregate

##### Owned Lifecycles
User Account
User Profile

##### Owned Business Rules
Registration eligibility
Authentication eligibility
Identity management

##### Owned Workflows
Register
Login
Logout
Verify Email
Password Recovery
Profile Maintenance

##### Authorization Responsibilities
Identity establishment
Actor resolution

##### Governance Responsibilities
Expose governance targets.
Never execute governance.

#### Social Graph Module
##### Purpose
Manage user relationships.

##### Owned Resources
Follow Relationship

##### Owned Aggregates
Follow Aggregate

##### Owned Lifecycles
Follow Relationship lifecycle

##### Owned Business Rules
Follow creation
Follow removal

##### Owned Workflows
Follow
Unfollow

##### Authorization Responsibilities
Validate relationship participation.

##### Governance Responsibilities
Expose moderation targets.

#### Content Module
##### Purpose
Manage platform discussion.

##### Owned Resources
Post
Comment
Vote

##### Owned Aggregates
Personal Content Aggregate
Discussion Aggregate
Voting Aggregate

##### Owned Lifecycles
Post lifecycle
Comment lifecycle
Vote lifecycle

##### Owned Business Rules
Content creation
Discussion participation
Voting

##### Owned Workflows
Post creation
Comment creation
Reply creation
Voting

##### Authorization Responsibilities
Content ownership enforcement.

##### Governance Responsibilities
Expose governance targets.

#### Community Module
##### Purpose
Manage communities.

##### Owned Resources
Herd
Membership
Shepherd Assignment

##### Owned Aggregates
Community Aggregate
Membership Aggregate

##### Owned Lifecycles
Herd lifecycle
Membership lifecycle
Shepherd lifecycle

##### Owned Business Rules
Community creation
Membership participation
Governance delegation

##### Owned Workflows
Create Herd
Join Herd
Leave Herd
Assign Shepherd
Revoke Shepherd

##### Authorization Responsibilities
Community authority validation.

##### Governance Responsibilities
Expose governance targets.

#### Media Module
##### Purpose
Manage media assets.

##### Owned Resources
Image
Owned Aggregates
Media Aggregate

##### Owned Lifecycles
Image lifecycle

##### Owned Business Rules
Upload
Attachment eligibility
Ownership

##### Owned Workflows
Upload Image
Remove Image

##### Authorization Responsibilities
Media ownership validation.

##### Governance Responsibilities
Expose moderation targets.

#### Governance Module
##### Purpose
Manage reporting, moderation, enforcement, escalation and oversight.

##### Owned Resources
Report
Moderation Action

##### Owned Aggregates
Reporting Aggregate
Moderation Aggregate

##### Owned Lifecycles
Report lifecycle
Moderation Action lifecycle

##### Owned Business Rules
Governance authority
Escalation
Enforcement
Review
Owned Workflows
Report review
Moderation execution
Escalation
Enforcement
Oversight

##### Authorization Responsibilities
Governance authority validation.

##### Governance Responsibilities
Own governance.

#### Feed Module
##### Purpose
Provide derived consumption views.

##### Owned Resources
None

##### Owned Aggregates
None

##### Owned Lifecycles
None

##### Owned Business Rules
Feed composition rules only.

##### Owned Workflows
Following Feed retrieval
Herd Feed retrieval

##### Authorization Responsibilities
Feed visibility validation.

##### Governance Responsibilities
Honor governance outcomes.

#### Implementation Implications
##### Backend
The backend architecture now has a stable module inventory and ownership model.

##### Database
No database changes required.

##### APIs
No API changes required.

##### Governance
Governance remains the only authority module.

##### Feed
Feed remains read-only and derived.

### Module Dependency Model
#### Dependency Principles
##### MDP-01 — Ownership Before Dependency
Ownership determines authority.
Dependency never grants authority.

##### MDP-02 — Capability Dependency Only
Modules consume capabilities.
Never internal rules.
Never internal workflows.
Never internal lifecycle control.

##### MDP-03 — No Shared Ownership
No resource may be jointly owned.
Ownership remains singular.

##### MDP-04 — Read Does Not Grant Write
Reading another module's information does not grant modification authority.

##### MDP-05 — Dependency Direction Must Be Explicit
Every dependency must have a business rationale.

##### MDP-06 — No Dependency Cycles
Cycles are forbidden.

##### MDP-07 — Feed Is Consumer Only
Feed may consume.
Feed may not be consumed.

##### MDP-08 — Governance Is Authority Only
Governance governs.
Governance does not become owner.

##### MDP-09 — Future Extraction Safe
Dependencies should be designed as though modules may become services later.

#### Module Dependency Analysis
##### Identity Module
Depends On

None

Exposes
Identity Resolution
Profile Retrieval
Participation Eligibility
Consumed By
Social Graph
Content
Community
Feed
Governance

##### Social Graph Module
Depends On

Identity

Consumes
User identity
Profile existence
Exposes
Follow relationships
Follower information
Consumed By

Feed

##### Content Module
Depends On

Identity
Community
Media

Consumes

Identity:

Author validation

Community:

Herd validation
Membership validation

Media:

Image attachment eligibility
Exposes
Posts
Comments
Votes
Content retrieval
Consumed By

Feed
Governance

##### Community Module
Depends On

Identity

Consumes
Member identity
Herd ownership identity
Shepherd identity
Exposes
Herd information
Membership information
Shepherd assignments
Consumed By

Content
Feed
Governance

##### Media Module
Depends On

Identity

Consumes
Ownership validation
Exposes
Image retrieval
Image ownership information
Consumed By

Content
Community
Feed
Governance

##### Governance Module
Depends On

Identity
Content
Community
Media

Consumes

Identity:

Profile targets

Content:

Post targets
Comment targets

Community:

Herd targets
Membership targets

Media:

Image targets
Exposes
Reports
Moderation outcomes
Enforcement decisions
Consumed By

Feed

##### Feed Module
Depends On

Identity
Social Graph
Content
Community
Media
Governance

Consumes

Identity:

Author information

Social Graph:

Follow relationships

Content:

Posts
Comments
Vote totals

Community:

Herd information

Media:

Image references

Governance:

Visibility outcomes
Exposes
Following Feed
Herd Feed
Consumed By

None

#### Module Dependency Matrix
| Module       | Depends On                                                    |
| ------------ | ------------------------------------------------------------- |
| Identity     | None                                                          |
| Social Graph | Identity                                                      |
| Community    | Identity                                                      |
| Media        | Identity                                                      |
| Content      | Identity, Community, Media                                    |
| Governance   | Identity, Content, Community, Media                           |
| Feed         | Identity, Social Graph, Content, Community, Media, Governance |

#### Dependency Graph
                    Identity
                    /  |   \
                   /   |    \
                  /    |     \
                 /     |      \
        Social Graph  Community  Media
                \        |        /
                 \       |       /
                  \      |      /
                     Content
                        |
                        |
                   Governance
                        |
                        |
                       Feed

#### Allowed Dependencies
| Consumer     | Provider     |
| ------------ | ------------ |
| Social Graph | Identity     |
| Community    | Identity     |
| Media        | Identity     |
| Content      | Identity     |
| Content      | Community    |
| Content      | Media        |
| Governance   | Identity     |
| Governance   | Content      |
| Governance   | Community    |
| Governance   | Media        |
| Feed         | Identity     |
| Feed         | Social Graph |
| Feed         | Content      |
| Feed         | Community    |
| Feed         | Media        |
| Feed         | Governance   |

#### Forbidden Dependencies
Identity → Anything

Forbidden.

Identity is foundational.

Social Graph → Content

Forbidden.

Following relationships do not own content.

Social Graph → Community

Forbidden.

Relationship graph independent of communities.

Community → Content

Forbidden.

Communities host content.

They do not own content.

Community → Governance

Forbidden.

Governance remains independent.

Content → Governance

Forbidden.

Content cannot make governance decisions.

Media → Content

Forbidden.

Media remains reusable.

Governance → Feed

Forbidden.

Governance governs resources.

Not consumption surfaces.

Feed → Feed

Forbidden.

Feed owns no authoritative data.

### Cross-Module Communication Model
#### MVP Communication Model
Internal Capability Contracts + Direct Invocation
Rule:
A module may invoke another module only through exposed capabilities.
Not through owned resources.
Not through owned lifecycles.
Not through internal workflows.

#### Future Evolution Path
MVP
Direct capability invocation
Future
Capability contracts become service contracts
Future Service Extraction
Replace direct invocation with API communication
No module redesign required.

This directly supports ADR-001 future evolution goals.

#### Implementation Implications
Backend
Module contracts become the primary dependency mechanism.

Governance
Governance remains downstream consumer of governed modules.
Never upstream owner.

Feed
Feed becomes the largest consumer.
Owns no authoritative state.

Future Architecture
Dependency graph remains extraction-ready.

### Governance Boundary Model
#### Governance Ownership Model
Governance owns:
Resource
Report
Moderation Action
Only these resources.
No others.

#### Governance Authority Model
Governance may:
Review reports
Execute moderation
Restrict visibility
Remove memberships
Restrict communities
Restrict profiles
Escalate actions
Reverse actions
Restore resources

#### Governance Access Model
Governance may read:
Module
Identity
Community
Content
Media
Governance requires visibility into moderation targets.

#### Governance Modification Model
Governance may influence:

| Resource Type | Authority |
| ------------- | --------- |
| Profile       | Restrict  |
| Herd          | Restrict  |
| Membership    | Remove    |
| Post          | Restrict  |
| Comment       | Restrict  |
| Image         | Restrict  |

Notice:
Governance influences.
Governance does not own.

#### Governance Workflow Ownership
Governance owns:
Reporting
Review
Escalation
Enforcement
Oversight
Restoration
No other module may own these workflows.

#### Governance Boundary Matrix
| Capability          | Governance May Read | Governance May Modify | Governance Owns |
| ------------------- | ------------------- | --------------------- | --------------- |
| User Profile        | Yes                 | Restrict              | No              |
| Follow Relationship | Read Only           | No                    | No              |
| Herd                | Yes                 | Restrict              | No              |
| Membership          | Yes                 | Remove                | No              |
| Shepherd Assignment | Yes                 | Revoke                | No              |
| Post                | Yes                 | Restrict              | No              |
| Comment             | Yes                 | Restrict              | No              |
| Vote                | Yes                 | No                    | No              |
| Image               | Yes                 | Restrict              | No              |
| Report              | Yes                 | Yes                   | Yes             |
| Moderation Action   | Yes                 | Yes                   | Yes             |

#### Governance Authority Rules
These become authoritative.

GAB-01
Governance may govern.
Governance may not own.

GAB-02
Governance decisions must be auditable.

GAB-03
Governance authority must follow hierarchy.

GAB-04
Governance cannot bypass ownership rules.

GAB-05
Governance actions must target resources through explicit workflows.

GAB-06
Governance owns moderation state.
Not business state.

### Feed Boundary Model
#### Feed Ownership Model
Feed owns:
Nothing.

#### Feed Owned Resources
None.

#### Feed Owned Aggregates
None.

#### Feed Owned Lifecycles
None.

#### Feed Owned Business Entities
None.

#### Feed Capability Model
Feed may:
Read
Aggregate
Filter
Order
Compose
Nothing else.

#### Feed Read Dependencies
Feed may read:
Module
Identity
Social Graph
Content
Community
Media
Governance

#### Feed Composition Responsibilities
Feed composes:

Following Feed
Using:
Social Graph
Content
Governance

Herd Feed
Using:
Community
Content
Governance

#### Feed Modification Authority
Feed may modify:
Nothing.

#### Feed Lifecycle Authority
Feed owns:
No lifecycle.

#### Feed Governance Authority
Feed may not:
Moderate
Enforce
Escalate
Restore
Feed only consumes governance outcomes.

#### Feed Boundary Matrix
| Capability          | Feed May Read | Feed May Modify | Feed Owns |
| ------------------- | ------------- | --------------- | --------- |
| Identity            | Yes           | No              | No        |
| Social Graph        | Yes           | No              | No        |
| Content             | Yes           | No              | No        |
| Community           | Yes           | No              | No        |
| Media               | Yes           | No              | No        |
| Governance Outcomes | Yes           | No              | No        |


#### Feed Authority Rules
These become authoritative.

FAB-01
Feed owns no business resources.

FAB-02
Feed owns no aggregates.

FAB-03
Feed owns no lifecycle.

FAB-04
Feed may compose.
Feed may not create.

FAB-05
Feed may filter.
Feed may not govern.

FAB-06
Feed may consume governance outcomes.
Feed may not generate governance outcomes.

FAB-07
Feed remains read-only.

#### Implementation Implications
Backend
Authority checks become separate from ownership checks.

Governance
Governance workflows remain centralized.

Feed
Feed remains stateless and derived.

Future Extraction
Governance can become a separate service without redefining ownership.
Feed can become a separate read service without redefining ownership.

## Backend Application Layer Architecture
### Application Service Architecture
Authoritative execution model:
Controller
    ↓
Application Service
    ↓
Domain Logic
    ↓
Repository
    ↓
Infrastructure

Application Services become the primary location for:
Use-case orchestration
Transaction ownership
Cross-module coordination
Authorization invocation
Governance invocation
Ownership enforcement coordination
Lifecycle enforcement coordination

### Layer Inventory
#### Layer 1 — API Layer

Purpose
Translate HTTP requests into application use cases.
This layer represents Express controllers and route handlers.

Responsibilities
Controllers MAY:
Request Extraction
Read:
Path parameters
Query parameters
Request body
Authenticated identity

Request Mapping
Transform HTTP input into application input models.
Example:
POST /posts
↓
CreatePostRequest

Response Mapping
Transform application results into API responses.
Example:
CreatePostResult
↓
201 Created

Error Translation Delegation
Pass errors to centralized error middleware.

Controllers Must NOT
Must Not Contain Business Rules
Forbidden:
if user is herd owner
inside controller.

Must Not Execute Authorization Logic
Forbidden:
if role === shepherd
inside controller.

Must Not Execute Governance Logic
Forbidden:
if community restricted
inside controller.

Must Not Execute Ownership Validation
Forbidden:
if post.authorId !== user.id
inside controller.

Must Not Execute Persistence
Forbidden:
PostModel.create()
inside controller.

Must Not Coordinate Transactions
Controllers never own transactions.

API Layer Summary
Controllers are transport adapters.
Nothing more.

#### Layer 2 — Application Layer
Purpose
Execute use cases.
This is the most important layer in the architecture.
Application Services become the workflow engine of the platform.

Responsibilities
Application Services own:
Use Case Orchestration
Examples:
Register User
Create Post
Join Herd
Assign Shepherd
Create Report
Remove Membership
Cross-Module Coordination
Examples:
Content Service may call:
Community Contract
Identity Contract
Governance Contract

Authorization Invocation
Application Services invoke authorization evaluation.
They do not implement authorization rules themselves.

Governance Invocation
Application Services invoke governance validation.

Ownership Validation Coordination
Application Services invoke ownership validation.

Lifecycle Enforcement Coordination
Application Services ensure valid state transitions.

Transaction Ownership
Application Services own transaction boundaries.
No other layer owns transactions.

Audit Generation Coordination
Governance workflows require:
Moderation records
Enforcement records
Activity records
Application Services coordinate creation.

Application Services Must NOT
Must Not Perform HTTP Logic
No:
req.body
res.status

Must Not Contain Database Queries
Forbidden:
mongoose.find()

Must Not Contain Cloudinary Logic
Forbidden:
cloudinary.uploader.upload()

Must Not Contain Persistence Details
Persistence belongs below.

Application Layer Summary
Application Services own workflow execution.
This becomes the primary execution layer of the platform.

#### Layer 3 — Domain Layer
Purpose
Own business rules.
This layer represents the business model of the platform.

Responsibilities
Domain Layer owns:
Ownership Rules
Examples:
Post author can edit post
Only herd owner can assign shepherd

Lifecycle Rules
Examples:
Deleted post cannot receive votes
Closed report cannot be escalated

Community Rules
Examples:
Membership required to post
Cannot join invite-only herd without invitation

Voting Rules
Examples:
One vote per user

Governance Rules
Examples:
Shepherd cannot override platform administrator

Aggregate Consistency Rules
Rules protecting aggregate integrity.

Domain Layer Must NOT
Must Not Access HTTP
Must Not Access Database
Must Not Access Cloudinary
Must Not Access Express
Must Not Access MongoDB Models

Domain Layer Summary
Domain Layer answers:
What is allowed?
Application Layer answers:
What should happen?

#### Layer 4 — Repository Layer
Purpose
Persistence abstraction.
Repositories manage storage operations.

Responsibilities
Repositories own:
Aggregate Retrieval
Example:
Get Post
Get Herd
Get Report

Aggregate Persistence
Example:
Save Post
Save Report

Query Operations
Example:
Find Comments By Post

Repositories Must NOT
Must Not Execute Authorization
Must Not Execute Governance Logic
Must Not Execute Ownership Rules
Must Not Execute Business Workflows
Must Not Coordinate Modules

Repository Summary
Repositories answer:
How is data stored and retrieved?
Nothing else.

#### Layer 5 — Infrastructure Layer
Purpose
Integrate external systems.

Responsibilities
Infrastructure owns:
MongoDB
Cloudinary
Email Provider
Logging
Cache
Environment Configuration
Third-Party APIs

Infrastructure Must NOT
Must Not Execute Business Rules
Must Not Execute Authorization Rules
Must Not Execute Governance Rules
Must Not Own Workflows

Infrastructure Summary
Infrastructure answers:
How does the system interact with the outside world?

#### Allowed dependency direction:
API
 ↓
Application
 ↓
Domain
 ↓
Repository
 ↓
Infrastructure

### Request Execution Model
#### Execution Architecture Principles
EA-01 — Application Services Own Workflow Execution
Controllers receive requests.
Application Services execute workflows.
This remains the most important execution rule.
Controller
    ↓
Application Service
Controllers never execute business workflows.

EA-02 — Authorization Is Explicit
Authorization must never be implicit.
Every protected use case must invoke authorization evaluation explicitly.
This aligns with:
Security By Default
Explicit Authority Boundaries

EA-03 — Governance Is Explicit
Governance must never be hidden.
Governance validation should be visible inside execution flows.
This aligns with Governance-Aware Design.

EA-04 — Ownership Enforcement Is Explicit
Ownership validation must occur before state mutation.
Ownership checks should never be delegated to repositories.

EA-05 — Domain Rules Execute Before Persistence
Business validity must be confirmed before storage operations.

EA-06 — Persistence Happens Last
Database mutation should be the final step before response creation.

EA-07 — API Layer Remains Stateless
Controllers do not retain execution state.
Execution state exists only inside application workflows.

#### Standard Request Execution Flow
This becomes the default request lifecycle for most write operations.
Authoritative Flow
Request
    ↓
Authentication
    ↓
Controller
    ↓
Request Validation
    ↓
Application Service
    ↓
Authorization
    ↓
Ownership Validation
    ↓
Governance Validation
    ↓
Domain Rules
    ↓
Transaction Start
    ↓
Persistence
    ↓
Transaction Commit
    ↓
Result Mapping
    ↓
Response

#### Execution Stage Responsibilities
Stage 1 — Authentication
Purpose:
Identify actor.
Output:
AuthenticatedUser
Examples:
userId
roles
permissions
Authentication must complete before controller execution.

Stage 2 — Controller
Purpose:
Translate HTTP request into application request.
Example:
POST /posts
↓
CreatePostCommand
No business logic.

Stage 3 — Request Validation
Purpose:
Validate API contract compliance.
Examples:
Required fields
Data types
Length constraints
Query constraints
Business validation does not occur here.

Stage 4 — Application Service Entry
Application Service becomes workflow owner.
Example:
CreatePostApplicationService
All subsequent business execution occurs here.

Stage 5 — Authorization
Purpose:
Determine whether actor may perform operation.
Examples:
Can create herd?
Can assign shepherd?
Can moderate report?
Authorization executes before business mutation.

Stage 6 — Ownership Validation
Purpose:
Verify ownership rights.
Examples:
User owns post
User owns profile
User owns image
Ownership remains separate from authorization.

Stage 7 — Governance Validation
Purpose:
Verify governance restrictions.
Examples:
User restricted?
Post restricted?
Herd restricted?
Governance enforcement becomes a mandatory checkpoint.

Stage 8 — Domain Rule Execution
Purpose:
Apply business rules.
Examples:
One vote per user
Membership required
Closed report cannot escalate
Domain Layer owns these rules.

Stage 9 — Transaction Start
Transaction begins only after workflow validity is confirmed.
Purpose:
Protect consistency.

Stage 10 — Persistence
Repositories execute storage operations.
Examples:
Save Post
Save Membership
Save Report

Stage 11 — Commit
Transaction completes.
Changes become durable.

Stage 12 — Result Mapping
Application result becomes API result.

Stage 13 — Response
Controller returns API contract response.

#### Read Request Execution Flow
Read workflows are different.
No mutation.
No transaction ownership.

Authoritative Read Flow
Request
    ↓
Authentication (if required)
    ↓
Controller
    ↓
Request Validation
    ↓
Application Service
    ↓
Authorization
    ↓
Visibility Validation
    ↓
Query Execution
    ↓
Result Composition
    ↓
Response

Why Ownership Validation Usually Does Not Exist
Reads generally require:
Can user see this?
rather than:
Does user own this?
Ownership checks only execute when ownership controls visibility.

#### Governance Workflow Execution Flow
Governance workflows require additional execution stages.
Example
Remove Herd Member

Authoritative Governance Flow
Request
    ↓
Authentication
    ↓
Controller
    ↓
Request Validation
    ↓
Governance Application Service
    ↓
Authority Validation
    ↓
Governance Hierarchy Validation
    ↓
Scope Validation
    ↓
Target Validation
    ↓
Moderation Rule Evaluation
    ↓
Transaction Start
    ↓
Create Moderation Action
    ↓
Execute Enforcement
    ↓
Create Audit Record
    ↓
Commit
    ↓
Response

Why Separate Governance Flow Exists
Governance operations contain:
Authority
Hierarchy
Escalation
Enforcement
Normal workflows do not.

#### Ownership Enforcement Flow
Ownership enforcement becomes standardized.

Authoritative Pattern
Application Service
    ↓
Load Aggregate
    ↓
Ownership Evaluation
    ↓
Continue Workflow

Example
Edit Post
Load Post
    ↓
Verify Author
    ↓
Continue Edit

Important Rule
Ownership enforcement occurs before mutation.
Never after persistence.

#### Authorization Invocation Flow
Authorization becomes a mandatory application-layer concern.

Authoritative Pattern
Application Service
    ↓
Authorization Service
    ↓
Decision
    ↓
Continue / Reject

Examples
Assign Shepherd
Delete Herd
Review Report
Escalate Moderation Action

Important Rule
Authorization rules remain centralized.
Controllers never evaluate permissions.
Repositories never evaluate permissions.

#### Governance Enforcement Invocation Flow
Governance enforcement remains separate from authorization.

Example
Create Post

Authorization
Can user create post?

Governance
Is user restricted?
Is herd restricted?

Authoritative Pattern
Application Service
    ↓
Authorization
    ↓
Governance Validation
    ↓
Continue Workflow

Why Separate?
Authorization answers:
May this actor perform this action?
Governance answers:
Has authority restricted this actor or resource?
These are fundamentally different concerns.

#### Feed Execution Architecture
Feed is a special case.
Feed owns no authoritative state.
Feed remains derived.

Following Feed Flow
Request
    ↓
Feed Controller
    ↓
Feed Application Service
    ↓
Identity Queries
    ↓
Social Graph Queries
    ↓
Content Queries
    ↓
Governance Visibility Filtering
    ↓
Feed Composition
    ↓
Response

Herd Feed Flow
Request
    ↓
Feed Controller
    ↓
Feed Application Service
    ↓
Community Validation
    ↓
Content Queries
    ↓
Governance Visibility Filtering
    ↓
Feed Composition
    ↓
Response

Important Feed Rule
Feed never modifies state.
Feed never owns transactions.
Feed only composes.

#### Cross-Module Workflow Example
Example:
Create Herd Post

Execution Flow
Request
    ↓
Content Controller
    ↓
CreatePostApplicationService
    ↓
Authorization
    ↓
Community Contract
       Verify Membership
    ↓
Governance Contract
       Verify Restrictions
    ↓
Content Domain Rules
    ↓
Save Post
    ↓
Response

Why This Matters
It demonstrates:
Module ownership preserved
Governance invoked explicitly
Application Service owns workflow
Content never modifies Community data

### Module Interaction Model
#### Module Interaction Principles
MI-01 — Modules Communicate Through Capabilities
Modules communicate through capabilities.
Not through internal implementation details.

Example:
Content should ask:
Community:
CanUserPostInHerd?
Not:
Read Membership Collection Directly

MI-02 — Ownership Remains Local
Only the owning module may modify its resources.

Example:
Community owns:
Herd
Membership
Shepherd Assignment
Content may never modify them.

MI-03 — Application Layer Is The Communication Boundary
Cross-module communication occurs exclusively through Application Services.
This becomes a critical architecture rule.

MI-04 — Repositories Never Cross Modules
Repositories belong to a module.
Repositories are never shared.

MI-05 — Domain Rules Remain Local
Business rules execute inside the owning module.
Never inside consuming modules.

MI-06 — Governance Remains Independent
Governance acts upon modules.
Modules do not depend on Governance for normal operation.
This preserves the approved Governance Domain position.

#### Authoritative Module Communication Model
Approved Pattern
Application Service
        ↓
Module Contract
        ↓
Target Module Application Service

Example
Create Herd Post

Content Application Service
        ↓
Community Contract
        ↓
Community Application Service
        ↓
Membership Evaluation
        ↓
Result

Why This Model
The caller receives:
Business Capability
instead of:
Database Access
This preserves ownership boundaries.

#### Module Contract Architecture
Every module exposes a public contract.

Example:
Identity Module
Public Contract:
GetUserById()
UserExists()
ProfileExists()

Community Module
Public Contract:
CanUserJoinHerd()
CanUserPostInHerd()
IsShepherd()
IsHerdOwner()

Governance Module
Public Contract:
IsUserRestricted()
IsPostRestricted()
IsCommunityRestricted()

Important Rule
Contracts expose:
Capabilities
Not entities.
Preferred:
CanUserPostInHerd()
Avoid:
GetMembershipDocument()
The capability abstraction protects module boundaries.

#### Authoritative Invocation Pattern
Standard Pattern
Controller
        ↓
Application Service
        ↓
Module Contract
        ↓
Target Application Service
        ↓
Repository

Example
Follow User

SocialGraphApplicationService
        ↓
IdentityContract
        ↓
IdentityApplicationService
        ↓
User Exists?
        ↓
Return Result
        ↓
Continue Follow Workflow

Why This Matters
The Social Graph module never touches:
Identity Repository
Identity Model
Identity Collections
Boundary preserved.

#### Allowed Communication Patterns
Pattern A
Application Service
→ Module Contract
→ Application Service
Allowed

Pattern B
Feed
→ Multiple Module Contracts
Allowed
Feed is a derived aggregation module.

Pattern C
Governance
→ Module Contracts
Allowed
Governance evaluates targets owned by other modules.

Pattern D
Read-Only Capability Queries
Allowed
Example:
UserExists()

Pattern E
Business Capability Requests
Allowed
Example:
CanUserPostInHerd()

#### Forbidden Communication Patterns
These become hard architectural rules.
Forbidden Pattern 1
Repository → Repository
Content Repository
        ↓
Community Repository
Forbidden.
Reason:
Destroys module boundaries.

Forbidden Pattern 2
Repository → Module
Repository
        ↓
Application Service
Forbidden.
Repositories are persistence components.
Not workflow coordinators.

Forbidden Pattern 3
Controller → Repository
Controller
        ↓
Repository
Forbidden.
Bypasses application layer.

Forbidden Pattern 4
Controller → Foreign Module
Content Controller
        ↓
Community Module
Forbidden.
Controllers never coordinate workflows.

Forbidden Pattern 5
Domain → Domain Mutation
Content Domain
        ↓
Modify Community Aggregate
Forbidden.
Only owning module may mutate aggregate state.

Forbidden Pattern 6
Cross-Module Aggregate Modification
Example:
Content
        ↓
Update Membership
Forbidden.
Community owns Membership.
Only Community may modify it.

Forbidden Pattern 7
Direct Database Access Across Modules
Example:
Content Module
        ↓
Membership Collection
Forbidden.

Forbidden Pattern 8
Circular Invocation Chains

Example:
Content
 ↓
Community
 ↓
Governance
 ↓
Content
Forbidden.
Violates acyclic dependency architecture.

#### Dependency Enforcement Model
Rule DE-01
Dependencies follow approved module graph.

Rule DE-02
No dependency cycles.
Ever.

Rule DE-03
Dependencies originate at Application Services.
Not repositories.
Not controllers.
Not domain objects.

Rule DE-04
Contracts are the only cross-module entry point.

#### Governance Communication Model
Governance requires special treatment.

Governance Consumes Capabilities
Example:
Governance
    ↓
Content Contract
Query:
Does Post Exist?

Governance Executes Governance
Example:
Restrict Post
Governance creates:
Moderation Action

Content Executes Mutation
Example:
Apply Restriction State

Important Governance Rule
Governance owns:
Decision
Target module owns:
State Mutation
This preserves ownership boundaries.
Example
Governance
    ↓
Restrict Post
Produces:
Restriction Decision
Then:
Content Contract
    ↓
Apply Restriction
Content performs the actual aggregate update.

#### Feed Communication Model
Feed is unique.
Feed owns no authoritative state.
Feed May Read
Identity
Social Graph
Content
Community
Governance

Feed May NOT Modify
Anything.
Ever.

Feed Pattern
Feed Application Service
        ↓
Identity Contract
        ↓
Social Graph Contract
        ↓
Content Contract
        ↓
Governance Contract
        ↓
Compose Feed

#### Future Extraction Readiness
This architecture intentionally mirrors service boundaries.
Current:
Application Service
        ↓
Module Contract
        ↓
Application Service

Future:
Service A
        ↓
API
        ↓
Service B

Minimal redesign required.
This aligns with Evolutionary Architecture.

#### Authoritative Communication Architecture
The official communication model becomes:
Module A
Application Service
        ↓
Module Contract
        ↓
Module B
Application Service
All cross-module interactions must use this pattern.
No exceptions.

### Transaction Architecture
#### Transaction Ownership Model
Decision
Application Services own transactions.
This becomes the authoritative rule.

Why Not Controllers?
Controllers are transport adapters.
They do not own workflows.
They do not understand business consistency requirements.

Why Not Repositories?
Repositories own persistence.
They do not understand:
Authorization
Governance
Ownership
Domain rules

Authoritative Ownership Model
Application Service
        ↓
Begin Transaction
        ↓
Execute Workflow
        ↓
Commit / Rollback

#### Transaction Lifecycle
Authoritative Sequence
Validation
        ↓
Authorization
        ↓
Ownership
        ↓
Governance
        ↓
Domain Rules
        ↓
Transaction Start
        ↓
Persistence
        ↓
Commit

Important Rule
Transactions begin as late as possible.
This minimizes:
Lock duration
Transaction scope
Failure surface

Example
Create Post

Correct:
Validate Input
        ↓
Validate Membership
        ↓
Validate Restrictions
        ↓
Start Transaction
        ↓
Save Post
        ↓
Commit

Incorrect:
Start Transaction
        ↓
Perform Validation
        ↓
Perform Authorization
        ↓
Perform Governance
This wastes transaction lifetime.

#### Cross Module Transaction Strategy
Single Workflow Owner Transaction
Application Service coordinates workflow.
Other modules provide validation capabilities.
Only owning module mutates its resources.

Example
Create Herd Post

Content Service
        ↓
Community Validation
        ↓
Governance Validation
        ↓
Content Transaction
        ↓
Save Post

Only Content mutates.
Only Content owns transaction.
Every mutation workflow has one transaction owner.
The owner is:
Owning Module Application Service

#### Eventual Consistency Requirement
For MVP:
Eventual consistency is not required.

Reason:
Most workflows modify only one aggregate owner.

Examples:
Create Post
Vote
Join Herd
Follow User
Create Report
Ownership boundaries naturally reduce cross-module mutation.

Future Evolution Path
If future requirements introduce:
One workflow
        ↓
Multiple aggregate owners

Then:
Domain Events
Outbox Pattern
Eventual Consistency
may be introduced.
Not now.

### Validation Architecture
#### Validation Categories
Validation is not one thing.
The architecture contains five validation classes:
| Validation Type          | Purpose                 |
| ------------------------ | ----------------------- |
| Input Validation         | API correctness         |
| Authorization Validation | Permission checks       |
| Ownership Validation     | Resource ownership      |
| Governance Validation    | Restriction enforcement |
| Domain Validation        | Business rules          |

#### Input Validation Placement
Responsibility
API Layer
Examples
Required fields
Field length
Email format
Pagination constraints

Purpose
Ensure request matches API contract.

Must NOT Include
User owns post
User can assign shepherd
Membership required
These are business validations.

Decision
Input validation occurs:
Controller
        ↓
Validation Middleware
before Application Service execution.

#### Authorization Validation Placement
Responsibility
Application Layer

Purpose
Determine:
May actor perform action?
Examples
Can create herd?
Can assign shepherd?
Can moderate report?

Execution Pattern
Application Service
        ↓
Authorization Service

Decision
Authorization belongs to Application Layer.
Not Controllers.
Not Repositories.

#### Ownership Validation Placement
Responsibility
Domain Layer
Executed by Application Layer.

Purpose
Determine:
Does actor own resource?
Examples
Owns Post?
Owns Profile?
Owns Herd?

Pattern
Application Service
        ↓
Load Aggregate
        ↓
Ownership Rule

Decision
Ownership rules belong to Domain.
Invocation belongs to Application Layer.

#### Governance Validation Placement
Responsibility
Governance Module
Invoked by Application Layer.

Purpose
Determine:
Has authority restricted action?
Examples
User restricted?
Post restricted?
Herd restricted?

Pattern
Application Service
        ↓
Governance Contract
        ↓
Governance Evaluation

Decision
Governance rules remain centralized in Governance.

#### Domain Validation Placement
Responsibility
Domain Layer

Examples
One vote per user
Cannot join twice
Cannot escalate closed report

Purpose
Protect business invariants.

Decision
Domain validation belongs exclusively to Domain Layer.

### Error Architecture
#### Error Classification
Category 1
Input Validation Errors

Examples:
Missing field
Invalid format
Invalid pagination

Category 2
Authorization Errors

Examples:
Permission denied
Role insufficient

Category 3
Ownership Errors

Examples:
Not post owner
Not herd owner

Category 4
Governance Errors

Examples:
Restricted user
Restricted herd
Restricted content

Category 5
Domain Rule Violations

Examples:
Already voted
Already member
Closed report

Category 6
Infrastructure Errors

Examples:
Mongo unavailable
Cloudinary unavailable
Email provider failure

#### Error Origination Model
| Error Type     | Origin                |
| -------------- | --------------------- |
| Input          | Validation Middleware |
| Authorization  | Authorization Service |
| Ownership      | Domain Rules          |
| Governance     | Governance Module     |
| Domain         | Domain Layer          |
| Infrastructure | Infrastructure Layer  |

#### Error Propagation Flow
Authoritative Pattern
Error
        ↓
Throw Domain/Application Error
        ↓
Application Service
        ↓
Bubble Up
        ↓
Global Error Middleware
        ↓
API Error Contract
        ↓
Response

Important Rule
Controllers do not translate errors.
Global Error Middleware translates errors.

Example
NotPostOwnerError

Flow:
Domain Layer
        ↓
Application Service
        ↓
Error Middleware
        ↓
403 Response

#### API Error Contract Compatibility
The architecture remains compatible with the approved API Error Contract.
Validation errors.
Authorization errors.
Governance errors.
Domain errors.
Infrastructure errors.
All eventually become standardized API responses.

---

## Backend Authorization Architecture

### Authorization Principles
The following become authoritative.

AUTH-01 — Authentication Is Not Authorization
Authentication answers:
Who are you?
Authorization answers:
What may you do?
Authenticated users are not automatically authorized.

AUTH-02 — Explicit Authorization
Every state-changing workflow must perform explicit authorization.
No implicit permissions.

AUTH-03 — Ownership First
Resource owners receive primary authority over their resources.
Unless governance authority applies.

AUTH-04 — Governance Overrides Ownership
Approved governance actors may override ownership authority.
Consistent with approved Governance Override Matrix.

AUTH-05 — Least Privilege
Actors receive minimum authority required.
No broad permissions.
No wildcard ownership.

AUTH-06 — Deny By Default
If authority cannot be proven:
Access denied.
Never infer authority.

AUTH-07 — Traceable Authority Decisions
Authorization decisions must be explainable.

Inputs:
Actor
Resource
Scope
Authority source
must be identifiable.

AUTH-08 — Domain Ownership Preservation
Authorization never transfers ownership.
Authority ≠ ownership.
Consistent with Domain Architecture.

AUTH-09 — Governance Scope Isolation
Governance authority exists only within approved scope.
Example:
Shepherd authority applies only to assigned Herds.

AUTH-10 — Hierarchy Enforcement
Higher governance authority may override lower authority.
Lower authority may never override higher authority.
Consistent with approved governance hierarchy.

### Authorization Execution Model
#### Selected Architecture
Hybrid Authorization Model

Authentication Middleware
Middleware Responsibilities
Authentication only.

Examples:
JWT validation
Session validation
Identity extraction

Output:
AuthenticatedPrincipal

Application Service Responsibilities
Authorization.

Examples:
Ownership checks
Governance checks
Role checks
Scope checks
Hierarchy checks
This becomes the authoritative authorization execution boundary.

#### Authorization Execution Boundary
Primary Execution Boundary
Application Services

Reason:
Application Services own workflow execution.
Authorization is workflow-specific.

Secondary Enforcement Boundary
Domain invariants.
Domains reject invalid state.
Domains do not perform permission evaluation.

Validation Order
Request
    ↓
Authentication Middleware
    ↓
Controller
    ↓
Application Service
    ↓
Authorization Evaluation
    ↓
Ownership Evaluation
    ↓
Governance Evaluation
    ↓
Domain Execution
    ↓
Persistence
This becomes the authoritative execution sequence.

#### Authorization Service Architecture
Selected Model
Hybrid Authorization Service
Not controller logic.
Not module-specific duplication.
Not global permission matrix.

Architecture
Application Service
        ↓
Authorization Service
        ↓
Ownership Policies
Governance Policies
Scope Policies

AuthorizationService Responsibilities
Evaluate Ownership
Examples:
CanEditPost
CanDeleteComment
CanDeleteImage

Evaluate Governance
Examples:
CanModeratePost
CanRemoveMember
CanAssignShepherd

Evaluate Scope
Examples:
Shepherd belongs to Herd
Content belongs to Herd

Evaluate Hierarchy
Examples:
Herd Owner overrides Shepherd
Platform Admin overrides Herd Owner

Inputs
Actor
Action
Target Resource
Context

Outputs
Authorized
Denied
Reason
Authority Source

Authority Source examples:
Ownership
Shepherd Authority
Herd Owner Authority
Platform Authority
Dependencies

AuthorizationService may consume capability contracts from:
Identity Module
Content Module
Community Module
Governance Module

while preserving module boundaries required by ADR-001.


### Ownership Authorization
#### Ownership authority model
Authoritative Ownership Rule
Every mutable resource must have exactly one authoritative ownership model.
Authorization always evaluates ownership before business execution.
Ownership authority becomes the primary authorization mechanism.
Governance authority becomes the exception mechanism.

Ownership Sources
Ownership may originate from:
Direct Ownership
Examples:
Profile Owner
Post Author
Comment Author
Image Owner

Relationship Ownership
Examples:
Follow Relationship Owner
Membership Owner
Vote Owner

Community Ownership
Examples:
Herd Owner
Shepherd Assignment Owner

System Ownership
Examples:
Report
Moderation Action
These are not user-owned resources.
Ownership authorization is not applicable.
Governance authorization applies instead.

#### Resource Ownership Authority Matrix
Identity Domain
User Profile
Owner:
Profile Owner
Allowed:
View Profile
Update Profile
Manage Profile Media
Denied:
Modify Another User Profile
Governance Override:
Platform Administrator
Social Graph Domain

Follow Relationship
Owner:
Following User
Allowed:
Create Follow
Delete Follow
Denied:
Modify Another User Follow Relationship
Governance Override:
Platform Administrator

Content Domain
Post
Owner:
Post Author
Allowed:
Edit Post
Delete Post
Manage Post Images
Denied:
Edit Another User Post
Delete Another User Post
Governance Override:
Shepherd (Scoped)
Herd Owner (Scoped)
Platform Administrator

Comment
Owner:
Comment Author
Allowed:
Edit Comment
Delete Comment
Denied:
Edit Another User Comment
Delete Another User Comment
Governance Override:
Shepherd (Scoped)
Herd Owner (Scoped)
Platform Administrator

Vote
Owner:
Voting User
Allowed:
Change Vote
Withdraw Vote
Denied:
Modify Another User Vote
Governance Override:
Platform Administrator

Community Domain
Herd
Owner:
Herd Owner
Allowed:
Update Herd
Update Rules
Manage Identity
Manage Shepherds
Denied:
Modify Another Herd
Governance Override:
Platform Administrator

Membership
Owner:
Membership User
Allowed:
Leave Herd
Denied:
Remove Other Memberships
Governance Override:
Shepherd
Herd Owner
Platform Administrator

Shepherd Assignment
Owner:
Herd Owner
Allowed:
Assign Shepherd
Revoke Shepherd
Denied:
Modify Other Herd Governance
Governance Override:
Platform Administrator

Media Domain
Image
Owner:
Uploading User
Allowed:
Delete Image
Denied:
Delete Another User Image
Governance Override:
Shepherd (Scoped)
Herd Owner (Scoped)
Platform Administrator

#### Ownership Validation Flow
Standard Flow
Request
    ↓
Authentication
    ↓
Load Resource
    ↓
Ownership Validation
    ↓
Governance Override Check
    ↓
Domain Execution
    ↓
Persistence

This becomes the default ownership workflow.
Why Resource Load Happens First
Ownership evaluation requires:
ownerId
authorId
membershipOwnerId
herdOwnerId
imageOwnerId
These values belong to the resource.
Therefore resource retrieval must occur before ownership validation.

#### Ownership Authorization Service Model
Ownership checks are centralized through AuthorizationService.
Application Services do not directly compare IDs.
Example
Avoid:
if (post.authorId !== actor.id)
inside multiple services.
Instead:
authorizationService.assertCanEditPost(
    actor,
    post
)

#### Ownership Capability Inventory
Identity
CanModifyProfile()

Social Graph
CanManageFollowRelationship()

Content
CanEditPost()
CanDeletePost()
CanEditComment()
CanDeleteComment()
CanManageVote()

Community
CanManageHerd()
CanAssignShepherd()
CanRevokeShepherd()
CanLeaveMembership()

Media
CanDeleteImage()
These become authoritative ownership authorization capabilities.

#### Relationship Resource Ownership Model
Relationship resources require special handling.

Follow Relationship
Authority Source:
Relationship Creator
Validation:
actorId == followerId

Vote
Authority Source:
Voting User
Validation:
actorId == voterId

Membership
Authority Source:
Membership User
Validation:
actorId == memberId
Relationship resources follow the same ownership architecture as primary resources.
No special authorization framework required.

#### Authoritative Decision Tree
Request
    ↓
Ownership Check
    ↓
Owner?
    ├── Yes → Allow
    │
    └── No
          ↓
     Governance Check
          ↓
     Authorized?
          ├── Yes → Allow
          └── No → Deny

#### Ownership Preservation Rules
These become authoritative architecture rules.

OWN-01
Ownership never changes because of moderation.

OWN-02
Moderation authority does not imply ownership authority.

OWN-03
Governance actions operate on resources.
They never acquire resources.

OWN-04
Only owning domains may modify ownership fields.
Consistent with Domain Authority Boundaries.

OWN-05
Ownership checks execute before business logic.

OWN-06
Ownership decisions must be explicit and traceable.

#### Ownership Audit Requirements
Ownership denials should generate structured security events.
Example:

Actor:
User-123

Action:
EditPost

Target:
Post-456

Decision:
Denied

Reason:
OwnershipViolation

For MVP:
Required
Authorization denial logs
Governance override logs
Moderation ownership overrides

Not Required Yet
Dedicated authorization audit database
Real-time security monitoring
SIEM integration
Consistent with MVP scope and solo developer constraints.


### Governance Authorization
#### Governance Authorization Principles
GOV-AUTH-01 — Governance Is Authority, Not Ownership
Governance actors gain authority.
They never gain ownership.
Example:
Shepherd removes Post
Result:
Post Owner remains unchanged
Ownership survives moderation.

GOV-AUTH-02 — Scope Before Authority
Authority cannot be evaluated until scope is validated.
Example:
Shepherd of Herd A
cannot moderate:
Content in Herd B
even if content is otherwise moderateable.

GOV-AUTH-03 — Hierarchy Before Action
Authority level must be validated before governance execution.
Lower authority may never overrule higher authority.

GOV-AUTH-04 — Explicit Override
Governance overrides must be intentional.
No implicit moderation authority.
Every override must identify:
Authority Source
Scope
Reason

GOV-AUTH-05 — Traceable Governance
Every governance decision must be explainable and auditable.

GOV-AUTH-06 — Deny By Default
Unknown governance authority equals denied authority.

#### Governance Authority Model
Member
Authority:
Report Content
Report Profiles
Report Herds
Cannot:
Moderate
Restrict
Remove
Restore
Override

Shepherd
Authority Scope:
Assigned Herd Only
May:
Review Reports
Remove Herd Content
Remove Herd Memberships
Dismiss Reports
Escalate Reports
Cannot:
Restrict Profiles
Assign Shepherds
Override Herd Owner
Execute Platform Actions

Herd Owner
Authority Scope:
Owned Herd Only
May:
Everything Shepherd Can Do
Assign Shepherds
Remove Shepherds
Override Shepherd Decisions
Manage Herd Governance
Cannot:
Platform Restrictions
Platform Identity Enforcement
Platform-Wide Governance

Platform Administrator
Authority Scope:
Entire Platform
May:
Review Escalations
Restrict Profiles
Restrict Herds
Reverse Governance Actions
Restore Content
Expand Enforcement
Override Herd Owners
Override Shepherds
This becomes the highest internal authority.

#### Authoritative Governance Evaluation Sequence
Request
    ↓
Authentication
    ↓
Role Evaluation
    ↓
Scope Evaluation
    ↓
Authority Evaluation
    ↓
Hierarchy Evaluation
    ↓
Governance Execution
This becomes the mandatory governance workflow.

#### Governance Authorization Service Architecture
Governance authorization remains centralized.
Selected Model
AuthorizationService
    ↓
Governance Policy Layer

Responsibilities
Evaluate Governance Roles
Examples:
IsShepherd()
IsHerdOwner()
IsPlatformAdmin()

Evaluate Governance Scope
Examples:
CanModerateWithinHerd()
CanManageMembership()

Evaluate Governance Hierarchy
Examples:
CanOverrideDecision()
CanReverseAction()

Evaluate Governance Overrides
Examples:
CanRemovePost()
CanRestrictProfile()
CanRestoreContent()

#### Governance Scope Architecture
Scope is the most important governance control.
Without scope enforcement:
One Shepherd
=
Platform Administrator
which would be catastrophic.

Shepherd Scope
Scope Boundary:
Assigned Herd
Governable Resources:
Herd Posts
Herd Comments
Herd Memberships
Not Governable:
Profiles
Other Herds
Platform Governance

Herd Owner Scope
Scope Boundary:
Owned Herd
Governable Resources:
Entire Herd
Memberships
Shepherd Assignments
Herd Content
Not Governable:
Platform Identity
Other Herds
Platform Restrictions

Platform Administrator Scope
Scope Boundary:
Global
Governable Resources:
All Resources
All Governance Actors
All Governance Decisions

#### Governance Override Architecture
This is where governance intersects ownership.

Principle
Ownership evaluated first.
Governance evaluated second.

Override Decision Model
Ownership Check
      ↓
Authorized?
      ↓
 YES → Execute

 NO
      ↓
 Governance Authority Check
      ↓
 Authorized?
      ↓
 YES → Execute Override

 NO → Deny
This becomes authoritative.

#### Governance Escalation Architecture
Escalation is not authorization failure.
Escalation is authority transfer.

Escalation Path
Shepherd
    ↓
Herd Owner
    ↓
Platform Administrator
Already defined in governance model.

Escalation Rules
Shepherd
May escalate to:
Herd Owner
Platform Administrator

Herd Owner
May escalate to:
Platform Administrator

Platform Administrator
Terminal authority.
No internal escalation exists.

#### Governance Capability Inventory
These become authoritative governance authorization capabilities.

Community Governance
CanReviewReport()
CanDismissReport()
CanEscalateReport()
CanRemoveMembership()
CanModerateContent()

Herd Governance
CanAssignShepherd()
CanRemoveShepherd()
CanOverrideShepherdDecision()

Platform Governance
CanRestrictProfile()
CanRestrictHerd()
CanRestoreContent()
CanReverseGovernanceAction()
CanExpandEnforcement()
CanReviewEscalation()

Hierarchy Capabilities
CanOverrideDecision()
CanEscalateDecision()

#### Governance Audit Architecture
Governance decisions are business-critical.
All governance actions must generate audit records.
Required MVP Audit Fields:

ActorId
ActorRole

Action

TargetType
TargetId

Scope

Decision

AuthoritySource

Reason

Timestamp

Governance Audit Categories
Governance Action
Example:
Membership Removal

Governance Override
Example:
Shepherd removed Post

Governance Escalation
Example:
Escalated to Platform Admin

Governance Reversal
Example:
Platform Admin restored Post

#### Governance Architecture Rules
These become authoritative.
GOV-ARCH-01
Governance authority never transfers ownership.

GOV-ARCH-02
Scope evaluation precedes authority evaluation.

GOV-ARCH-03
Hierarchy evaluation precedes governance execution.

GOV-ARCH-04
Governance overrides must be explicit.

GOV-ARCH-05
All governance actions are auditable.

GOV-ARCH-06
Higher authority may override lower authority.

GOV-ARCH-07
Lower authority may never override higher authority.

GOV-ARCH-08
Governance authorization executes inside Application Services.

GOV-ARCH-09
Governance authority is evaluated through AuthorizationService.

GOV-ARCH-10
Governance decisions remain traceable and explainable.

### Cross-Module Authorization
#### Cross-Module Authorization Principles
CMA-01 — Authorization Never Bypasses Module Ownership
Authorization may query a module.
Authorization may not directly access another module's persistence layer.
Forbidden:
Content Service
    ↓
Community Database Collection
Allowed:
Content Service
    ↓
Community Contract

CMA-02 — Ownership Remains Local
Only owning modules know authoritative ownership.
Example:
Community owns Herd Owner
Content cannot decide Herd ownership.
Community must answer.

CMA-03 — Authorization Consumes Capabilities
Authorization consumes capabilities.
Not databases.
Not repositories.
Not domain entities directly.

CMA-04 — Authorization Queries Are Read-Only
Cross-module authorization never modifies state.
Authorization is information gathering.
Not workflow execution.

CMA-05 — Authorization Must Remain Explicit
Dependencies required for authorization must be visible.
No hidden repository calls.
No indirect database access.

#### Cross-Module Authorization Mode
Module Contract-Based Authorization
Authorization
     ↓
Module Contracts

Selected.
Preserves ownership.
Preserves modularity.
Consistent with Module Boundary Architecture.

Authoritative Model
Authorization acquires information exclusively through module capability contracts.

#### Authorization Dependency Architecture
Authorization becomes a consumer of module contracts.
Architecture
Application Service
        ↓
AuthorizationService
        ↓
Module Contracts
        ↓
Owning Modules

Example
Edit Post
PostApplicationService
        ↓
AuthorizationService
        ↓
ContentCapabilities
        ↓
GetPostAuthor()
Authorization never touches repositories directly.

#### Authorization Capability Contract Model
Modules expose authorization-safe capabilities.
Not business services.
Not repositories.
Not domain internals.

Identity Module
Exposes:
GetUserIdentity()
IsActiveUser()
IsRestrictedUser()
Purpose:
Identity eligibility validation.

Social Graph Module
Exposes:
IsFollowing()
GetFollowOwner()
Purpose:
Relationship ownership validation.

Content Module
Exposes:
GetPostAuthor()
GetCommentAuthor()
GetVoteOwner()
IsPostInHerd()
Purpose:
Content ownership validation.

Community Module
Exposes:
GetHerdOwner()
IsShepherd()
IsMember()
GetMembershipOwner()
GetAssignedHerd()
Purpose:
Community authority validation.

Media Module
Exposes:
GetImageOwner()
IsImageAttached()
Purpose:
Media ownership validation.

Governance Module
Exposes:
GetGovernanceRole()
CanOverrideAuthority()
GetModerationScope()
Purpose:
Governance authority validation.

#### Authorization Contract Rules
These become architectural rules.
AUTH-CONTRACT-01
Contracts expose facts.
Not workflows.
Good:
GetPostAuthor()
Bad:
DeletePost()

AUTH-CONTRACT-02
Contracts expose authority information.
Not internal implementation.
Good:
GetHerdOwner()
Bad:
GetHerdAggregate()

AUTH-CONTRACT-03
Contracts remain read-only.
No state mutation.

AUTH-CONTRACT-04
Contracts return minimal information.
Only information needed for authorization.

#### Authorization Query Categories
Authorization queries fall into four categories.
Category 1
Ownership Queries
Examples:
GetPostAuthor()
GetCommentAuthor()
GetImageOwner()

Category 2
Relationship Queries
Examples:
GetMembershipOwner()
GetFollowOwner()

Category 3
Scope Queries
Examples:
IsMember()
IsShepherd()
GetAssignedHerd()

Category 4
Governance Queries
Examples:
CanOverrideAuthority()
GetGovernanceRole()

#### Authorization Decision Execution Model
Authorization becomes an orchestration workflow.
Example
Can User Remove Membership?
Required Data:
Actor
Membership
Herd
Role

Execution:
AuthorizationService
        ↓
Community Contract
        ↓
GetMembershipOwner()

Community Contract
        ↓
GetHerdOwner()

Governance Contract
        ↓
GetGovernanceRole()
Decision produced.
No direct repository access.
No cross-domain mutation.

#### Allowed Authorization Dependency Graph
Consistent with approved domain dependency model.
Identity
Authorization may query:
Identity
Only.

Social Graph
Authorization may query:
Identity
Social Graph

Content
Authorization may query:
Identity
Content
Community
Governance

Community
Authorization may query:
Identity
Community
Governance

Media
Authorization may query:
Identity
Media
Governance

Governance
Authorization may query:
Identity
Community
Content
Media
Social Graph
Governance
Consistent with Governance's approved dependency position.

Feed
Authorization may query:
Identity
Social Graph
Content
Community
Governance
Because Feed is derived.

#### Forbidden Authorization Patterns
These are important.
Forbidden Pattern 1
Cross-Repository Access
Content Repository
    ↓
Community Repository
Prohibited.

Forbidden Pattern 2
Cross-Domain Entity Mutation
Governance
    ↓
Modify Post Aggregate
Prohibited.
Governance requests actions.
Owning domain executes changes.
Consistent with Domain Authority Boundaries.

Forbidden Pattern 3
Shared Authorization Tables
Authorization Database
Rejected.
Creates duplicate ownership model.

Forbidden Pattern 4
Controller Authorization Orchestration
Controller
    ↓
Multiple Module Calls
Rejected.
Authorization belongs in Application Services.

Forbidden Pattern 5
Repository-Level Authorization
Rejected by approved authorization architecture.

#### Governance + Cross-Module Authorization
Governance is unique.
Governance frequently requires information from multiple domains.
Example:
Can Shepherd Remove Post?
Requires:
Content → Post
Community → Herd
Community → Shepherd Assignment
Governance → Authority Rules

Execution:
AuthorizationService
      ↓
Content Contract
      ↓
Community Contract
      ↓
Governance Contract
      ↓
Decision

This remains acceptable because:
Read-only
Contract-based
Ownership preserved

#### Future Evolution Strategy
Current Architecture:
AuthorizationService
        ↓
In-Process Module Contracts
Suitable for Modular Monolith.

Future Service Extraction:
AuthorizationService
        ↓
Capability APIs
No redesign required.
Only transport changes.
This aligns with Evolutionary Architecture and ADR-001 future extraction guidance.

#### Cross-Module Authorization Rules
These become authoritative.
CMA-RULE-01
Authorization may query any required module through approved capability contracts.

CMA-RULE-02
Authorization may never access another module's repository.

CMA-RULE-03
Authorization contracts are read-only.

CMA-RULE-04
Authorization contracts expose facts, not workflows.

CMA-RULE-05
Authorization never bypasses ownership boundaries.

CMA-RULE-06
Governance authority never implies resource ownership.

CMA-RULE-07
Authorization orchestration belongs to AuthorizationService.

CMA-RULE-08
Cross-module authorization dependencies must remain explicit.

CMA-RULE-09
Authorization decisions remain traceable to source modules.

CMA-RULE-10
Future service extraction must preserve capability-contract semantics.


- Capability contract model
- Authorization dependency rules
- Allowed patterns
- Forbidden patterns

### Authorization Errors
#### Authorization Failure Classification Model
Authorization failures are not all identical.
Different failure categories communicate different architectural problems.
AUTH-FAIL-01
Not Authenticated
Meaning:
Actor identity unavailable
Examples:
Missing JWT
Invalid JWT
Expired Session
Result:
401 Unauthorized
Application execution stops immediately.

AUTH-FAIL-02
Insufficient Authority
Meaning:
Actor exists
BUT
Does not possess required authority
Examples:
Member attempts shepherd action
Shepherd attempts admin action
Result:
403 Forbidden

AUTH-FAIL-03
Ownership Violation
Meaning:
Actor is authenticated
BUT
Resource ownership check fails
Examples:
Edit another user's post
Delete another user's image
Modify another user's profile
Result:
403 Forbidden

AUTH-FAIL-04
Governance Scope Violation
Meaning:
Governance actor exists
BUT
Requested resource is outside approved scope
Examples:
Shepherd of Herd A
attempts moderation inside Herd B
Result:
403 Forbidden

AUTH-FAIL-05
Governance Hierarchy Violation
Meaning:
Requested action violates authority hierarchy
Examples:
Shepherd reversing Herd Owner decision
Herd Owner reversing Platform Admin decision
Result:
403 Forbidden

AUTH-FAIL-06
Restricted Resource Access
Meaning:
Resource exists
BUT
Actor is not permitted to interact with it
Examples:
Restricted profile
Restricted herd
Governed content
Result:
403 Forbidden

AUTH-FAIL-07
Governance State Violation
Meaning:
Governance workflow state prevents action
Examples:
Dismiss already resolved report
Review closed escalation
Result:
409 Conflict
This is not a permission problem.
This is a workflow-state problem.

#### Authorization Exception Model
Authorization failures should become explicit application exceptions.

Base Exception
AuthorizationException

Derived Exceptions
AuthenticationRequiredException
InsufficientAuthorityException
OwnershipViolationException
GovernanceScopeViolationException
GovernanceHierarchyViolationException
RestrictedResourceAccessException

Why
Provides:
Consistent handling
Consistent logging
Consistent API responses
Easier testing

#### Authorization Error Propagation Architecture
Selected model:

Authorization Layer
        ↓
Application Service
        ↓
Global Error Handler
        ↓
API Error Contract
This aligns with the Application Service Architecture already approved.

Standard Flow
Request
    ↓
Authentication
    ↓
Authorization
    ↓
Failure
    ↓
Authorization Exception
    ↓
Application Layer
    ↓
Global Error Handler
    ↓
Error Contract Response

Why This Model
Prevents:
Controller-specific error handling
Prevents:
Duplicate authorization response logic
Creates:
Single security error path

#### Authorization → API Contract Mapping
Authorization architecture must remain consistent with API Error Contracts.

Authentication Failure
AuthenticationRequiredException
Response:
{
  "code": "AUTHENTICATION_REQUIRED",
  "message": "Authentication required."
}
HTTP:
401 Unauthorized

Ownership Violation
OwnershipViolationException
Response:
{
  "code": "OWNERSHIP_VIOLATION",
  "message": "You are not authorized to perform this action."
}
HTTP:
403 Forbidden

Governance Scope Violation
{
  "code": "GOVERNANCE_SCOPE_VIOLATION",
  "message": "You are not authorized to perform this action."
}
HTTP:
403 Forbidden

Governance Hierarchy Violation
{
  "code": "GOVERNANCE_HIERARCHY_VIOLATION",
  "message": "You are not authorized to perform this action."
}
HTTP:
403 Forbidden

Insufficient Authority
{
  "code": "INSUFFICIENT_AUTHORITY",
  "message": "You are not authorized to perform this action."
}
HTTP:
403 Forbidden

##### Important Security Decision
Public responses remain intentionally generic.
Do NOT reveal:
ownership IDs
governance roles
scope details
hierarchy information
Reason:
Security By Default principle.

#### Resource Existence vs Authorization
This is an important architectural decision.

Problem
User requests:
PATCH /posts/123
Two possibilities:
Post does not exist
or
Post exists but actor lacks authority

Selected MVP Strategy
Resource lookup executes first.
Then:
404 Not Found
if resource absent.
Otherwise:
403 Forbidden
if authorization fails.

Rationale
Advantages:
Simpler implementation
Easier debugging
Better developer experience
Suitable for MVP
Potential information disclosure risk is acceptable for MVP scope.

### Authorization Audit Model
#### Authorization Audit Architecture
Not every authorization event deserves permanent audit records.
Different events have different value.
Category A
Governance Actions
Always audited.
Examples:
Content Removal
Membership Removal
Profile Restriction
Content Restoration
Required.

Category B
Governance Overrides
Always audited.
Examples:
Shepherd Override
Herd Owner Override
Platform Admin Override
Required.

Category C
Governance Escalations
Always audited.
Examples:
Report Escalated
Decision Escalated
Required.

Category D
Authorization Denials
Logged.
Not stored as governance records.
Examples:
Ownership violation
Authority violation
Scope violation

#### Security Event Architecture
Authorization failures may generate security events.

Logged Security Events
Repeated Ownership Violations
Example:
User repeatedly attempts to edit
resources owned by others

Repeated Governance Violations
Example:
Repeated moderation attempts
outside scope

Repeated Privilege Escalation Attempts
Example:
Member repeatedly calls admin APIs

For MVP:
Simple structured logs are sufficient.
No SIEM.
No intrusion detection system.
Consistent with operational simplicity constraints.

#### Authorization Logging Model
Every authorization decision should be loggable.
Recommended structure:
Timestamp
ActorId
Action
TargetType
TargetId
Decision
AuthoritySource
FailureReason

Example
Actor:
user-123

Action:
DeletePost

Target:
post-456

Decision:
Denied

Reason:
OwnershipViolation

#### Authorization Error Rules
These become authoritative.
AUTH-ERR-01
Authentication failures return 401.

AUTH-ERR-02
Authorization failures return 403.

AUTH-ERR-03
Workflow-state violations return 409.

AUTH-ERR-04
Authorization failures must propagate through the Global Error Handler.

AUTH-ERR-05
Authorization responses must not reveal internal authority details.

AUTH-ERR-06
Governance actions must always be auditable.

AUTH-ERR-07
Governance overrides must always be auditable.

AUTH-ERR-08
Authorization denials must be logged.

AUTH-ERR-09
Authorization exceptions must be explicit application exceptions.

AUTH-ERR-10
Authorization error behavior must remain consistent with the platform-wide Error Contract.

---

## Backend Governance Architecture

### Governance Principles
#### Architectural Rule GA-01
Governance owns authority, not resources.

Governance owns:

Governance Resources
Report
Moderation Action

Governance Lifecycles
Report lifecycle
Moderation Action lifecycle

Governance Workflows
Report intake
Review
Dismissal
Escalation
Enforcement
Restoration
Oversight

Governance Decisions
Moderation outcomes
Enforcement outcomes
Escalation outcomes
Override outcomes

Governance Audit Records

Governance event history

Governance decision history

Governance does not own:

Identity Domain Resources
User Profile

Content Domain Resources
Post
Comment
Vote

Community Domain Resources
Herd
Membership
Shepherd Assignment

Media Domain Resources
Image

Governance acts upon them.

Governance never owns them.

Ownership remains with originating domains.

---

#### Architectural Rule GA-02

Every governance action must belong to exactly one governance workflow.

No orphan moderation actions are permitted.

Workflow Classification Model
| Workflow              | Classification       |
| --------------------- | -------------------- |
| Report Intake         | Intake Workflow      |
| Community Review      | Review Workflow      |
| Community Enforcement | Enforcement Workflow |
| Escalation            | Authority Workflow   |
| Platform Review       | Review Workflow      |
| Platform Enforcement  | Enforcement Workflow |
| Oversight             | Audit Workflow       |

Workflow 1 — Report Intake
Purpose

Receive governance concerns.

Trigger

Member submits report.

Output

Report created.

Owner

Governance Module.

Workflow 2 — Community Review
Purpose

Evaluate herd-scoped governance issues.

Actors
Shepherd
Herd Owner
Output

Moderation outcome.

Owner

Governance Module.

Workflow 3 — Community Enforcement
Purpose

Apply community-scoped governance actions.

Examples:

Remove post
Remove comment
Remove membership
Owner

Governance Module.

Workflow 4 — Escalation
Purpose

Transfer authority review upward.

Hierarchy:

Shepherd
↓
Herd Owner
↓
Platform Administrator

Owner

Governance Module.

Workflow 5 — Platform Review
Purpose

Review escalated or platform-level issues.

Actor

Platform Administrator.

Owner

Governance Module.

Workflow 6 — Platform Enforcement
Purpose

Apply platform-wide restrictions.

Examples:

Restrict profile
Restrict herd
Expand enforcement
Owner

Governance Module.

Workflow 7 — Oversight
Purpose

Review governance behavior itself.

Targets:

Shepherds
Herd Owners
Governance history
Owner

Governance Module.

---

#### Architectural Rule GA-03

Governance authority must always be validated before governance workflow execution.

Authorization determines whether a governance actor may act.

Governance determines what governance workflow executes.

This preserves separation from Authorization Architecture.

Shepherd
Responsibilities
Review herd reports
Moderate herd content
Moderate herd membership
Escalate issues

Authority Scope
Assigned Herd only.

Limitations
Cannot:
Restrict profiles
Restrict herds
Override herd owner decisions
Escalation Authority

Can escalate upward.

Override Authority
None.

Herd Owner
Responsibilities
Resolve community disputes
Review escalations
Govern own herd

Authority Scope
Owned Herd only.

Limitations
Cannot:
Apply platform restrictions
Override platform decisions
Escalation Authority

Can escalate upward.

Override Authority
Can override Shepherd decisions.

Platform Administrator
Responsibilities
Platform governance
Platform enforcement
Governance oversight

Authority Scope
Entire platform.

Limitations
None within platform governance scope.

Escalation Authority

Final internal authority.

Override Authority
Can override:
Shepherd
Herd Owner

Governance Hierarchy Model
Platform Administrator
          ↑
      Herd Owner
          ↑
       Shepherd
          ↑
        Member

---

#### GA-04 — Governance Must Be Auditable

All governance decisions must be:

- Traceable
- Reviewable
- Reconstructable

Governance history remains authoritative.

---

### Governance Workflow Architecture

#### Workflow Inventory

Governance owns:

1. Report Intake
2. Community Review
3. Community Enforcement
4. Escalation
5. Platform Review
6. Platform Enforcement
7. Oversight

---

#### Report Lifecycle

Submitted
↓
Under Review
↓
Dismissed | Moderated | Escalated
↓
Platform Review
↓
Final Outcome

Report Lifecycle Architecture
Report States
Submitted
    ↓
Under Review
    ↓
 ┌───────────────┬───────────────┐
 │               │               │
Dismissed    Moderated      Escalated
                             ↓
                      Platform Review
                             ↓
                       Final Outcome
Submitted

Created by:

Member
Shepherd
Herd Owner
Platform Administrator

Contains:

Target
Reason
Reporter
Context

Ownership:

Governance Domain

Under Review

Report assigned to:

Shepherd
Herd Owner
Platform Administrator

Depending on governance scope.

No enforcement exists yet.

Dismissed

Review completed.

No moderation required.

Terminal state.

Moderated

Community governance outcome applied.

Moderation Action created.

Terminal unless escalated later.

Escalated

Community governance unable or unwilling to resolve.

Transferred upward.

Governance ownership unchanged.

Platform Review

Platform Administrator becomes reviewing authority.

Community authority ends.

Final Outcome

Platform decision recorded.

May include:

Uphold
Reverse
Restore
Expand

Terminal review state.

Architectural Rule GW-01
A Report may only move forward through governance lifecycle states.
Backward transitions are prohibited.

---

#### Community Governance Flow

Report
↓
Shepherd Review
↓
Dismiss | Moderate | Escalate
↓
Herd Owner Review
↓
Resolve | Reverse | Escalate

Shepherd Moderation Workflow
Report Submitted
      ↓
Shepherd Review
      ↓
 ┌─────────────┬─────────────┐
 │             │             │
Dismiss    Moderate     Escalate

Shepherd Review Responsibilities
Can:

Review herd reports
Review herd content
Review herd membership issues

Cannot:

Restrict profiles
Restrict herds
Execute platform enforcement

Shepherd Outcomes
Dismiss

Report closed.

Moderate

Moderation Action created.

Community enforcement applied.

Escalate

Transferred to Herd Owner.

Herd Owner Review Workflow
Escalated Matter
        ↓
 Herd Owner Review
        ↓
 ┌───────────────┬───────────────┐
 │               │               │
Uphold      Reverse      Escalate

Herd Owner Responsibilities
Can:

Review Shepherd decisions
Reverse Shepherd outcomes
Uphold Shepherd outcomes

Cannot:

Restrict profiles
Restrict platform-wide resources

Herd Owner Outcomes
Uphold

Original moderation remains.

Reverse

Moderation reversed.

Escalate

Transferred to Platform Governance.

Architectural Rule GW-02
Community governance may govern only herd-scoped resources.

---

#### Platform Governance Flow

Escalated Matter
↓
Platform Review
↓
Uphold | Reverse | Expand
↓
Final Outcome

Platform Review Responsibilities

Review:

Escalations
Platform reports
Governance disputes
Governance actor behavior

Platform Outcomes
Uphold

Existing moderation remains.

No additional enforcement.

Reverse

Previous moderation invalidated.

Enforcement removed.

Restore

Previously restricted resource restored.

May accompany reversal.

Expand

Additional enforcement applied.

Examples:

Remove Post
      ↓
Restrict Profile

or

Remove Content
      ↓
Restrict Herd

Architectural Rule GW-03
Only Platform Administrators may execute enforcement expansion.

Recommended Decision Flow
Report Submitted
        ↓
Governance Intake
        ↓
Scope Determination
        ↓
Authority Assignment
        ↓
Community Review
        ↓
 ┌─────────────┬─────────────┬──────────────┐
 │             │             │
Dismiss    Moderate     Escalate
                          ↓
                    Herd Owner
                          ↓
                ┌─────────┴─────────┐
                │                   │
            Resolve           Escalate
                                    ↓
                          Platform Review
                                    ↓
                   ┌────────┬────────┬────────┐
                   │        │        │
                Uphold  Reverse  Expand
                                    ↓
                            Final Outcome


#### Governance Scope Determination
Before review begins:
Governance identifies:
Target Type
Profile
Post
Comment
Herd
Membership
Image

Target Context
Herd-scoped
Platform-scoped

Required Authority
Shepherd
Herd Owner
Platform Administrator

Architectural Rule GW-04
Authority assignment must occur before review begins.
Reviewers are never self-selected.

#### Workflow Ownership Architecture
Content Module

Provides:

Post information
Comment information

Does not:

Execute moderation workflow

Community Module

Provides:

Herd information
Membership information

Does not:

Execute moderation workflow

Identity Module

Provides:

Actor identity
Profile information

Does not:

Execute moderation workflow

Media Module

Provides:

Image information

Does not:

Execute moderation workflow

Architectural Rule GW-05
Governance workflows may consume domain information.
Governance workflows may not be executed by non-governance modules.

---

### Governance Enforcement Architecture

#### Enforcement Principles
Governance enforces authority.
Governance does not assume ownership.
Ownership remains unchanged.

Enforcement Definition
Enforcement Means

A governance decision that changes:

Visibility
Participation
Access
Eligibility

Without transferring ownership.

Enforcement Does NOT Mean
Ownership transfer
Aggregate transfer
Lifecycle ownership transfer
Resource reassignment

Architectural Rule GE-01
Governance enforces.
Ownership persists.
Always.


---

#### Enforcement Model
Enforcement Execution Model
Governance Decision
↓
Moderation Action
↓
Enforcement Outcome
↓
Owning Domain Applies State Change

Why

This preserves:

Domain ownership
Governance authority
Module boundaries

Example — Post Removal
Governance Decision
        ↓
Remove Post
        ↓
Content Module
        ↓
Post Visibility Restricted

Ownership remains:

Post Owner = Original Author

Example — Membership Removal
Governance Decision
        ↓
Remove Membership
        ↓
Community Module
        ↓
Membership Disabled

Ownership remains:

Membership Owner = Member

Architectural Rule GE-02
Governance decisions create enforcement outcomes.
Owning domains execute resulting state changes.

Enforcement Execution Responsibilities
Governance Module

Responsible for:

Decision creation
Enforcement determination
Enforcement recording
Enforcement auditing
Owning Domain

Responsible for:

Resource state updates
Visibility changes
Participation changes
Lifecycle compliance

Architectural Rule GE-03
Governance decides.
Owning domains apply.

Enforcement Reversal Architecture
Enforcement Reversal Flow
Moderation Action
        ↓
Enforcement Applied
        ↓
Platform Review
        ↓
Reversal Decision
        ↓
Enforcement Removed
Example
Post Removed
      ↓
Platform Review
      ↓
Decision Reversed
      ↓
Post Restored

Ownership unchanged.

Architectural Rule GE-04
Every enforcement action must be reversible unless prohibited by law or external policy.

Enforcement Expansion Definition

Escalating governance consequences.

Example:

Remove Post
      ↓
Restrict Profile

Another example:

Remove Membership
       ↓
Restrict Herd
Recommended Model
Existing Enforcement
          ↓
Platform Review
          ↓
Expanded Enforcement
          ↓
Additional Moderation Action

Important:

Expansion creates new governance actions.

Expansion does not overwrite history.

Architectural Rule GE-05
Enforcement expansion creates additional governance decisions.
History must remain immutable.

---

#### Enforcement Capabilities

Governance may:

- Restrict
- Remove
- Restore
- Escalate
- Expand Enforcement

Governance may not:

- Transfer Ownership
- Become Resource Owner

Resource Enforcement Matrix
Profile
Owning Domain
Identity
Enforcement Examples
Restrict Profile
Restore Profile
Authority
| Authority              | Allowed |
| ---------------------- | ------- |
| Shepherd               | No      |
| Herd Owner             | No      |
| Platform Administrator | Yes     |
Override
Platform Administrator only.

Post
Owning Domain
Content
Enforcement Examples
Remove Post
Restore Post
Authority
| Authority              | Allowed    |
| ---------------------- | ---------- |
| Shepherd               | Herd Scope |
| Herd Owner             | Herd Scope |
| Platform Administrator | Global     |

Comment
Owning Domain
Content
Enforcement Examples
Remove Comment
Restore Comment
Authority
| Authority              | Allowed    |
| ---------------------- | ---------- |
| Shepherd               | Herd Scope |
| Herd Owner             | Herd Scope |
| Platform Administrator | Global     |

Image
Owning Domain
Media
Enforcement Examples
Restrict Image
Restore Image
Authority
| Authority              | Allowed    |
| ---------------------- | ---------- |
| Shepherd               | Herd Scope |
| Herd Owner             | Herd Scope |
| Platform Administrator | Global     |

Herd
Owning Domain
Community
Enforcement Examples
Restrict Herd
Restore Herd
Authority
| Authority              | Allowed       |
| ---------------------- | ------------- |
| Shepherd               | No            |
| Herd Owner             | Own Herd Only |
| Platform Administrator | Global        |

Membership
Owning Domain
Community
Enforcement Examples
Remove Membership
Restore Membership
Authority
| Authority              | Allowed       |
| ---------------------- | ------------- |
| Shepherd               | Assigned Herd |
| Herd Owner             | Own Herd      |
| Platform Administrator | Global        |

Shepherd Assignment
Owning Domain
Community
Enforcement Examples
Remove Shepherd
Reinstate Shepherd
Authority
| Authority              | Allowed  |
| ---------------------- | -------- |
| Shepherd               | No       |
| Herd Owner             | Own Herd |
| Platform Administrator | Global   |

Architectural Rule GE-06
Enforcement authority must never exceed governance authority hierarchy.


---

#### Ownership Preservation

Governance actions never transfer ownership.

Ownership remains authoritative regardless of enforcement state.

Ownership Boundary Proof
Governance may:
Restrict
Restore
Remove
Escalate
Expand

Governance may not:
Reassign ownership
Become owner
Change aggregate ownership
Change domain ownership

Therefore:
FD-08 satisfied
Ownership remains authoritative.

Governance Authority Boundary Proof
Governance owns:
Reports
Moderation Actions
Enforcement Workflows

Governance does not own:

Profiles
Posts
Comments
Herds
Memberships
Images

Consistent with approved Governance Domain architecture.

---

### Governance Audit Architecture

#### Audit Principles

All governance outcomes must be auditable.

Audit history is immutable.

Overrides never erase history.

Governance Audit Principles
GAP-01 — Governance Decisions Must Be Traceable

Every governance outcome must be attributable to:

An actor
A workflow
A decision

GAP-02 — Governance History Is Immutable

Historical governance records are never rewritten.

New events extend history.

They do not replace history.

GAP-03 — Authority Must Be Visible

Audit records must reveal:

Who acted
What authority they possessed
Why action was permitted

GAP-04 — Escalations Must Be Visible

Escalation history must remain visible.

The system must show:

Shepherd
    ↓
Herd Owner
    ↓
Platform Administrator

when applicable.

GAP-05 — Overrides Must Never Erase Prior Decisions

Override history remains visible.

Example:

Decision A
      ↓
Override
      ↓
Decision B

Both remain auditable.

GAP-06 — Enforcement Must Be Auditable

Every enforcement action must be traceable to:

Report
Review
Decision

Architectural Rule GAU-01
Every governance outcome must be explainable through audit history.

---

#### Mandatory Governance Events

- Report Created
- Report Assigned
- Report Dismissed
- Report Escalated
- Moderation Action Applied
- Enforcement Applied
- Enforcement Reversed
- Platform Override Executed
- Enforcement Expanded
- Governance Actor Reviewed

Mandatory Governance Events
Report Created

Trigger:

User submits report

Purpose:

Establish governance entry point.

Report Assigned

Trigger:

Review authority determined

Purpose:

Track review ownership.

Report Dismissed

Trigger:

No action required

Purpose:

Record moderation outcome.

Report Escalated

Trigger:

Authority transferred upward

Purpose:

Record escalation path.

Moderation Action Applied

Trigger:

Moderation decision executed

Purpose:

Record governance outcome.

Enforcement Applied

Trigger:

Restriction becomes active

Purpose:

Record enforcement history.

Enforcement Reversed

Trigger:

Restoration

Purpose:

Record rollback history.

Platform Override Executed

Trigger:

Higher authority overrides lower authority

Purpose:

Record authority exercise.

Enforcement Expanded

Trigger:

Additional enforcement added

Purpose:

Record escalation severity.

Governance Actor Reviewed

Trigger:

Shepherd review
Herd Owner review

Purpose:

Support oversight workflows.

Architectural Rule GAU-02
Every governance state transition must produce an auditable governance event.

Optional Governance Events
These support future governance evolution.

Not mandatory for MVP.

Examples:

Internal review notes
Governance workload metrics
Queue assignment changes

Architectural Rule GAU-03
Optional audit records must never replace mandatory governance records.

Governance-Owned Audit History
Audit Ownership Model
Governance Owns
Governance event history
Governance review history
Enforcement history
Escalation history
Override history

Other Domains Own
Business resources.
Not governance history.

Architectural Rule GAU-04

Governance is the authoritative owner of governance history.

Audit Retention Ownership
Governance Domain Responsible For

Retention of:

Reports
Moderation Actions
Governance Events

Other Domains Responsible For

Retention of:

Profiles
Posts
Herds
Memberships
Images
Architectural Rule GAU-05
Governance history remains independent from governed resource ownership.

Audit Access Boundaries
Shepherd

May view:

Relevant herd governance history

Cannot view:

Platform-wide governance history

Herd Owner

May view:

Herd governance history
Shepherd governance actions

Cannot view:

Platform-wide governance history

Platform Administrator

May view:

Entire governance history

Architectural Rule GAU-06
Audit visibility follows governance authority hierarchy.

---

#### Traceability Chain

Report
↓
Reviewer
↓
Decision
↓
Moderation Action
↓
Enforcement
↓
Current Outcome

Architectural Rule GAU-07
Every enforcement outcome must be traceable back to an originating report.

Governance History Review Architecture
Perspective 1 — Resource History

Questions:

What happened to this post?

Review:

Resource
    ↓
Governance Events
    ↓
Current Status
Perspective 2 — Governance Actor History

Questions:

What actions has this Shepherd performed?

Review:

Actor
    ↓
Governance Actions
    ↓
Outcomes
Perspective 3 — Governance Workflow History

Questions:

How did this report progress?

Review:

Report
    ↓
Review Path
    ↓
Decision Path

Architectural Rule GAU-08
Governance history must be reviewable by resource, actor, and workflow.

Oversight Review Architecture
Recommended Oversight Flow
Governance Actor
         ↓
Governance Activity Review
         ↓
Oversight Evaluation
         ↓
Outcome
Oversight Targets

Shepherd

Review:

Dismissal patterns
Enforcement patterns
Escalation patterns

Herd Owner

Review:

Override patterns
Enforcement patterns
Escalation patterns

Platform Administrator

External review only.

Not governed by lower authorities.

Consistent with hierarchy.

Architectural Rule GAU-09
Governance actors are auditable participants in governance workflows.

---

### Governance Integration Architecture
Governance Integration Principles
GIP-01 — Governance Is An Authority Consumer

Governance consumes domain information.

Governance does not own domain information.

GIP-02 — Governance Owns Governance Workflows

Domains never execute:

Reporting
Moderation
Escalation
Oversight

These remain Governance responsibilities.

GIP-03 — Domains Own Resource State

Governance may request outcomes.

Domains apply changes to resources they own.

GIP-04 — Governance Is Workflow-Centric

Governance integrates through workflow execution.

Not through direct resource ownership.

GIP-05 — Authorization Remains Separate

Governance never performs authorization decisions.

Authorization Architecture remains authoritative.

Architectural Rule GI-01
Governance may govern resources.
Governance may not become resource owner.

#### Identity Integration

Identity owns profiles.

Governance governs profiles.

Identity remains authoritative.

Governance consumes Identity capabilities.

Integration Responsibilities
Identity Provides
User identity resolution
Profile information
Participation eligibility
Governance actor information
Governance Consumes
Profile targets
Actor identities
Profile enforcement outcomes
Integration Flow
Governance Workflow
        ↓
Identity Capability
        ↓
Profile Information
        ↓
Governance Decision
        ↓
Identity Applies Restriction

Architectural Rule GI-02
Identity owns profile state.
Governance owns profile governance.

---

#### Content Integration

Content owns posts, comments, and votes.

Governance governs content.

Content remains authoritative.

Governance remains moderation authority.

Integration Responsibilities
Content Provides
Post information
Comment information
Vote information
Ownership information
Governance Provides
Moderation decisions
Enforcement decisions
Restoration decisions
Integration Flow
Report
   ↓
Governance Review
   ↓
Moderation Outcome
   ↓
Content Module
   ↓
Content Visibility Updated
Ownership Validation

Post ownership remains:

Author

even after moderation.

Consistent with approved ownership architecture.

Architectural Rule GI-03
Governance may affect content visibility.
Governance may not own content.

---

#### Community Integration

Community owns:

- Herds
- Memberships
- Shepherd Assignments

Governance governs community resources.

Community remains authoritative.

Governance remains governing authority.

Integration Responsibilities
Community Provides
Herd information
Membership information
Shepherd assignments
Governance hierarchy context

Governance Provides
Moderation outcomes
Enforcement outcomes
Escalation outcomes

Integration Flow
Governance Decision
        ↓
Community Capability
        ↓
Membership Restricted

or

Governance Decision
        ↓
Community Capability
        ↓
Herd Restricted

Herd Governance Context

Community supplies:

Shepherd
      ↓
Herd Owner

relationship information.

Governance uses that information.

Governance does not own it.

Architectural Rule GI-04
Community owns governance structure.
Governance owns governance execution.

---

#### Media Integration

Media owns images.

Governance governs images.

Media remains authoritative.

Governance remains moderation authority.

Integration Responsibilities
Media Provides
Image information
Ownership information
Attachment information

Governance Provides
Restriction outcomes
Restoration outcomes

Integration Flow
Image Report
       ↓
Governance Review
       ↓
Moderation Outcome
       ↓
Media Module
       ↓
Image Restricted

Architectural Rule GI-05
Governance may restrict media.
Governance may not own media.

---

#### Feed Integration

Feed consumes governance outcomes.

Feed never executes governance decisions.

Feed consumes governance outcomes.

Integration Responsibilities
Governance Provides
Visibility eligibility
Restriction outcomes
Restoration outcomes

Feed Provides
Feed composition
Feed retrieval

Integration Flow
Post Restricted
        ↓
Governance Outcome
        ↓
Feed Composition
        ↓
Excluded From Feed

Important Clarification
Feed does not determine:

Should this post be restricted?

Governance determines that.

Feed only determines:

Should restricted content appear?

The answer is derived from Governance state.

Architectural Rule GI-06
Feed never performs governance decisions.
Feed consumes governance decisions.

---

#### Authorization Integration

Authorization determines:

- Whether action is permitted.

Governance determines:

- What governance action occurs.

Responsibilities remain separate.

Authorization remains authoritative.

Governance consumes authorization outcomes.

Responsibility Matrix
| Responsibility        | Authorization | Governance |
| --------------------- | ------------- | ---------- |
| Actor Validation      | Yes           | No         |
| Scope Validation      | Yes           | No         |
| Hierarchy Validation  | Yes           | No         |
| Workflow Execution    | No            | Yes        |
| Moderation Decisions  | No            | Yes        |
| Escalation Decisions  | No            | Yes        |
| Enforcement Decisions | No            | Yes        |
| Audit Recording       | No            | Yes        |

Governance Execution Flow
Governance Request
        ↓
Authorization Service
        ↓
Authority Verified
        ↓
Governance Workflow
        ↓
Decision
        ↓
Audit

Architectural Rule GI-07
Authorization determines whether an actor may act.
Governance determines what action occurs.

#### Governance Capability Contract Architecture
Recommended Decision

Governance consumes module capabilities.

Never module internals.

Example

Governance should consume:

ContentCapability

Not:

Content Repository

Governance should consume:

CommunityCapability

Not:

Community Aggregate Internals

Why
This preserves:

Modular Monolith boundaries
Future extraction readiness
Independent evolvability

Consistent with Module Boundary principles.

Architectural Rule GI-08
Governance integrates through capability contracts.
Never through internal module implementation.

---

### Governance Validation

Validated Against:

- ADR-001
- Domain Architecture
- Module Boundaries
- Application Layer Architecture
- Authorization Architecture
- Functional Drivers
- Quality Drivers
- Architectural Principles

Result:

Backend Governance Architecture Approved.

---

## Backend Data Access Architecture

### Purpose

The Backend Data Access Architecture defines how backend modules interact with persistence while preserving:

- Domain Ownership
- Module Ownership
- Authorization Boundaries
- Governance Boundaries
- Feed Read-Only Boundaries
- Future Evolution Readiness

The architecture follows:

- Domain-Oriented Modular Monolith
- Capability-Based Module Interaction
- Repository + Query Separation
- Persistence Encapsulation
- Evolutionary Architecture

Adopt Repository + Query Separation as the authoritative Backend Data Access Architecture.
Authoritative Architecture:
Controller
    ↓
Application Service
    ↓
Repository
    ↓
MongoDB

Query Services
    ↓
MongoDB

Why This Fits Chauthara

Because it aligns with every approved architecture decision:

Preserves Module Ownership

Repositories remain owned by modules.

Preserves Feed Design

Feed is read-only and query-oriented.

Feed naturally becomes a query consumer rather than a repository owner.

Preserves Governance Design

Governance workflows use repositories.

Governance review surfaces use query services.

Prevents Repository Bloat

Repositories remain focused on:

Aggregate persistence
Aggregate retrieval
Lifecycle persistence

Not feed composition.

Not reporting dashboards.

Not governance analytics.

Supports Future Extraction

Future service extraction becomes easier because:

Repository
=
Write Contract

Query Service
=
Read Contract

without introducing CQRS complexity today.

---

### Data Access Principles

#### DAP-01

Persistence ownership follows module ownership.

#### DAP-02

Only owning modules may modify authoritative resources.

#### DAP-03

Cross-module persistence access is prohibited.

#### DAP-04

Modules consume capabilities, not repositories.

#### DAP-05

Persistence implementation details remain encapsulated.

#### DAP-06

Feed remains a derived read-only domain.

#### DAP-07

Governance governs resources but does not own them.

Authoritative Repository Architecture
Rule DAA-01
Repositories are the only persistence abstraction allowed for authoritative resource modification.

Rule DAA-02
Repositories belong exclusively to the owning module.

Rule DAA-03
Repositories manage aggregate persistence.

Rule DAA-04
Complex retrieval logic belongs in Query Services.

Rule DAA-05
Application Services orchestrate repositories and query services.

Rule DAA-06
Repositories never orchestrate workflows.

Rule DAA-07
Feed retrieval must use Query Services.

Rule DAA-08
Governance review surfaces should use Query Services.

Rule DAA-09
Repositories remain internal implementation details of their owning module.

Rule DAA-10
Cross-module repository access is prohibited.

---

### Repository Architecture

Architecture Pattern:

Controller
→ Application Service
→ Repository
→ MongoDB

Repositories own:

- Persistence
- Lifecycle persistence
- Existence checks
- Ownership-scoped retrieval

Repositories do not own:

- Workflow orchestration
- Authorization
- Governance decisions
- Feed composition
- Cross-module integration

Aggregate-to-Repository Mapping
Hybrid Rule
One Authoritative Resource = One Repository
Because:
Resource ownership is already defined.
API contracts are resource-oriented.
MongoDB collections naturally align.
Simpler than strict aggregate repositories.
Easier for solo development.

#### Repository Principles

- Repository ownership follows module ownership.
- One authoritative resource maps to one repository.
- Repositories remain internal module assets.
- Repositories are not integration contracts.

ROP-01 — Repository Ownership Follows Module Ownership
Repository ownership must always align with module ownership.

Example:

Identity Module
    ↓
UserProfileRepository
Content Module
    ↓
PostRepository

Repository ownership can never cross module boundaries.

ROP-02 — Repository Authority Follows Resource Authority
The repository that persists a resource is the authoritative persistence owner.

Example:

PostRepository

owns Post persistence authority.

No other repository may write Post state.

ROP-03 — Repositories Are Internal Module Assets
Repositories are implementation details of modules.

Repositories are not cross-module contracts.

Modules expose capabilities.

Not repositories.

ROP-04 — One Resource Owner = One Repository Owner
Every authoritative resource must have exactly one repository owner.

Never:

PostRepository
AND
FeedRepository

owning Post persistence.

Ownership remains singular.

ROP-05 — Feed Owns No Repositories
Feed owns no authoritative resources.

Therefore Feed owns no repositories.

Feed only owns query services.

This follows approved Feed architecture.

ROP-06 — Governance Owns Governance Repositories Only
Governance owns:

ReportRepository
ModerationActionRepository

Governance never owns:

PostRepository
HerdRepository
UserProfileRepository

Governance governs.

Governance does not own.

This follows approved Governance architecture.

ROP-07 — Repository Writes Remain Local
Repositories may write only resources owned by their module.

Cross-module writes are forbidden.

ROP-08 — Repositories Do Not Orchestrate
Repositories:

Persist
Retrieve
Query owned aggregates

Repositories do not:

Coordinate workflows
Invoke authorization
Invoke governance
Start transactions

Application Services own those responsibilities.

---

### Repository Inventory

#### Identity
Identity Module

Owned Resource:

User Profile

Repository:

UserProfileRepository

Responsibilities:

Create profile
Retrieve profile
Update profile
Profile existence checks
Profile lookup

Owns:
users
collection.

#### Social Graph
Social Graph Module

Owned Resource:

Follow Relationship

Repository:

FollowRepository

Responsibilities:

Follow creation
Follow removal
Follow existence checks
Follow retrieval

Owns:
follows
collection.

#### Content
Content Module

Owned Resources:

Post
Comment
Vote

Repositories:

PostRepository
CommentRepository
VoteRepository

Responsibilities:

PostRepository
Post persistence
Post retrieval
Post updates
Post deletion lifecycle
CommentRepository
Comment persistence
Reply persistence
Comment retrieval
VoteRepository
Vote persistence
Vote updates
Vote removal

Owns:
posts
comments
votes
collections.

#### Community
Community Module

Owned Resources:

Herd
Membership
Shepherd Assignment

Repositories:

HerdRepository
MembershipRepository
ShepherdAssignmentRepository

Owns:
herds
memberships
shepherdAssignments
collections.

#### Media
Media Module

Owned Resource:

Image

Repository:

ImageRepository

Owns:
images
collection.

#### Governance
Governance Module

Owned Resources:

Report
Moderation Action

Repositories:

ReportRepository
ModerationActionRepository

Owns:
reports
moderationActions
collections.

#### Feed
Feed Module

Repositories:

NONE

Feed owns:
FollowingFeedQueryService
HerdFeedQueryService
only.
Feed owns no persistence state.

#### Repository Inventory Matrix
| Module       | Repository                   |
| ------------ | ---------------------------- |
| Identity     | UserProfileRepository        |
| Social Graph | FollowRepository             |
| Content      | PostRepository               |
| Content      | CommentRepository            |
| Content      | VoteRepository               |
| Community    | HerdRepository               |
| Community    | MembershipRepository         |
| Community    | ShepherdAssignmentRepository |
| Media        | ImageRepository              |
| Governance   | ReportRepository             |
| Governance   | ModerationActionRepository   |
| Feed         | None                         |

#### Repository Responsibility Boundaries
Each repository may:
Allowed
Persist owned resources
Retrieve owned resources
Execute ownership-scoped queries
Execute existence checks
Execute lifecycle persistence

Forbidden
Repositories must never:
Call repositories from other modules
Invoke Application Services
Perform authorization
Perform governance decisions
Execute workflows
Compose feeds
Send events
Manage transactions

#### Authoritative Repository Ownership Rules
DAA-11
Repository ownership follows module ownership.

DAA-12
Repositories are internal module implementation details.

DAA-13
Cross-module repository access is prohibited.

DAA-14
Cross-module repository writes are prohibited.

DAA-15
One authoritative resource maps to one authoritative repository.

DAA-16
Repositories persist owned resources only.

DAA-17
Repositories never perform workflow orchestration.

DAA-18
Repositories never perform authorization.

DAA-19
Repositories never perform governance decisions.

DAA-20
Feed owns no repositories.

DAA-21
Governance owns only governance repositories.

DAA-22
Repositories never become module integration points.
Application Services remain module integration points.

---

### Cross-Module Data Access Rules

#### Cross-Module Data Access Model

Authoritative flow:

Application Service
        ↓
Module Capability
        ↓
Owning Module
        ↓
Repository

Never:

Application Service
        ↓
Foreign Repository

#### Approved Integration Mechanism

Capability Contracts

Modules may consume:

- Existence checks
- Validation checks
- Approved retrieval operations
- Governance retrieval operations

Modules may not consume:

- Foreign repositories
- Foreign query services
- Foreign collections
- Foreign schemas
- Foreign persistence models

#### Cross-Module Access Pattern

Application Service
→ Capability Contract
→ Owning Module
→ Repository

#### Capability Categories
Not every capability is equal.
Category 1 — Existence Capabilities
Purpose:
Validate existence.

Examples:
identityCapability.userExists(userId)
communityCapability.herdExists(herdId)
contentCapability.postExists(postId)

Category 2 — Validation Capabilities
Purpose:
Validate business conditions.

Examples:
communityCapability.isMember(
  userId,
  herdId
)

communityCapability.canPostInHerd(
  userId,
  herdId
)

mediaCapability.canAttachImage(
  imageId,
  userId
)

Category 3 — Retrieval Capabilities
Purpose:
Expose approved read data.

Examples:
contentCapability.getPostSummary(postId)
communityCapability.getHerdSummary(herdId)
identityCapability.getProfileSummary(userId)

Important:
Summary.
Not internal entity exposure.

Category 4 — Governance Capabilities
Purpose:
Provide moderation visibility.

Examples:
contentCapability.getModerationTarget(postId)
communityCapability.getModerationTarget(herdId)
identityCapability.getModerationTarget(userId)

#### Authoritative Dependency Pattern
Content → Community
Allowed
Validate Membership
Validate Herd
Validate Posting Eligibility
Through:
Community Capability
Only.
Never:
MembershipRepository

Content → Media
Allowed
Image Ownership Validation
Image Existence Validation
Through:
Media Capability
Only.

Social Graph → Identity
Allowed
User Existence
Profile Visibility
Through:
Identity Capability
Only.

Governance → Identity
Allowed
Profile Information
Profile Governance Target
Through:
Identity Capability
Only.

Governance → Content
Allowed
Post Target
Comment Target
Through:
Content Capability
Only.

Governance → Community
Allowed
Herd Target
Membership Target
Through:
Community Capability
Only.

Feed → Everything
Feed is special.
Feed consumes:
Identity
Social Graph
Content
Community
Governance

through:
Query Services
not repositories.
Feed remains read-only.
This preserves approved Feed architecture.

#### Repository Visibility Rules
Allowed
Repository visible to:

Owning Module Only

Example:

PostRepository

Visible To:
Content Module
Only.

Forbidden
Governance → PostRepository

Feed → MembershipRepository

Community → UserProfileRepository

Content → HerdRepository

All forbidden.

#### Capability Ownership Rules
Capabilities belong to the owning module.
Example:
Community Module
Exposes:
Membership Validation
Membership Retrieval
Herd Retrieval
Posting Eligibility
Community remains owner.
Consumers remain consumers.

#### Future Extraction Alignment
Current:
Content
    ↓
CommunityCapability

Future:
Content
    ↓
Community Service API

No architectural redesign required.
Only implementation changes.
This is exactly what ADR-001 expects when future extraction becomes justified.

#### Authoritative Cross-Module Data Access Rules
DAA-23
Modules may not access repositories owned by other modules.

DAA-24
Repository access remains internal to the owning module.

DAA-25
Cross-module access must occur through capability contracts.

DAA-26
Capabilities are the only approved module integration mechanism.

DAA-27
Capabilities may expose:
Existence checks
Validation checks
Approved retrieval operations
Governance retrieval operations

DAA-28
Capabilities must not expose repository implementations.

DAA-29
Capabilities must not expose database structures.

DAA-30
Capabilities must not expose collection ownership.

DAA-31
Feed consumes query services, never repositories.

DAA-32
Governance consumes governance-target capabilities, never foreign repositories.

DAA-33
Cross-module writes are prohibited.

DAA-34
Only owning modules may execute lifecycle persistence.

DAA-35
Capability contracts must remain future-service-extraction compatible.

#### Cross-Module Access Matrix
| Consumer                | Access Method        |
| ----------------------- | -------------------- |
| Social Graph → Identity | Identity Capability  |
| Community → Identity    | Identity Capability  |
| Media → Identity        | Identity Capability  |
| Content → Identity      | Identity Capability  |
| Content → Community     | Community Capability |
| Content → Media         | Media Capability     |
| Governance → Identity   | Identity Capability  |
| Governance → Content    | Content Capability   |
| Governance → Community  | Community Capability |
| Governance → Media      | Media Capability     |
| Feed → Identity         | Query Services       |
| Feed → Social Graph     | Query Services       |
| Feed → Content          | Query Services       |
| Feed → Community        | Query Services       |
| Feed → Governance       | Query Services       |


---

### Query Architecture

Architecture Pattern:

Controller
→ Application Service
→ Query Service
→ MongoDB

#### Dedicated Query Services
Authoritative Architecture:

Controller
      ↓
Application Service
      ↓
Query Service
      ↓
MongoDB

For reads.

And:

Controller
      ↓
Application Service
      ↓
Repository
      ↓
MongoDB

For writes.

#### Query Categories

##### Resource Queries

- Profile retrieval
- Post retrieval
- Herd retrieval

Category 1 — Resource Queries

Purpose:

Retrieve owned resources.

Examples:

Get Profile
Get Post
Get Comment
Get Herd

Characteristics:

Simple retrieval
Ownership-oriented
Single resource focus

Example:

PostQueryService.getPost(postId)

##### Validation Queries

- Existence checks
- Membership checks

Category 2 — Validation Queries

Purpose:

Support capability contracts.

Examples:

User Exists
Membership Exists
Post Exists
Image Exists

Example:

communityCapability.isMember()

internally using:

MembershipQueryService

Characteristics:

Lightweight
Authorization support
Workflow support

##### Feed Queries

- Following Feed
- Herd Feed

Category 3 — Feed Queries

Purpose:

Compose derived feed views.

Examples:

Following Feed
Herd Feed

Characteristics:

Multi-module
Aggregation heavy
Read-only

These belong to Feed.

Not Content.

Not Community.

This preserves Feed ownership.

##### Governance Queries

- Report review queues
- Escalation queues
- Governance activity

Category 4 — Governance Queries

Purpose:

Support moderation workflows.

Examples:

Report Queue
Escalation Queue
Governance Activity
Moderation History

Characteristics:

Multi-resource
Governance-owned
Audit-focused

These belong to Governance.

Not Content.

Not Community.

Not Identity.

#### Administrative Queries
Category 5 — Administrative Queries

Future category.

Examples:

Operational Reports
Platform Statistics

Not required for MVP.

Document only.

#### Query Ownership Model

The most important decision.

Rule

Queries belong to the module that owns the read concern.

Not the module that owns the data.

Example:

Following Feed.

Consumes:

Posts
Profiles
Follows
Governance Visibility

Who owns query?

Answer:

Feed Module

because Feed owns feed composition.

Not Content.

Example:

Governance Queue.

Consumes:

Reports
Moderation Actions
Posts
Comments
Profiles

Who owns query?

Answer:

Governance Module

because Governance owns moderation review.

#### Query Ownership Matrix
| Query Type           | Owner        |
| -------------------- | ------------ |
| Profile Retrieval    | Identity     |
| Follow Retrieval     | Social Graph |
| Post Retrieval       | Content      |
| Comment Retrieval    | Content      |
| Vote Retrieval       | Content      |
| Herd Retrieval       | Community    |
| Membership Retrieval | Community    |
| Image Retrieval      | Media        |
| Following Feed       | Feed         |
| Herd Feed            | Feed         |
| Report Queue         | Governance   |
| Escalation Queue     | Governance   |
| Governance Activity  | Governance   |

#### Query Service Inventory
Identity
UserProfileQueryService

Responsibilities

Profile Retrieval
Profile Existence
Profile Summary
Social Graph
FollowQueryService

Responsibilities

Relationship Retrieval
Follower Lists
Following Lists
Content
PostQueryService
CommentQueryService
VoteQueryService

Responsibilities

Post Retrieval
Comment Retrieval
Vote Retrieval
Content Summaries
Community
HerdQueryService
MembershipQueryService
ShepherdAssignmentQueryService

Responsibilities

Herd Retrieval
Membership Retrieval
Participation Validation
Media
ImageQueryService

Responsibilities

Image Retrieval
Ownership Retrieval
Governance
ReportQueryService
GovernanceReviewQueryService
GovernanceActivityQueryService

Responsibilities

Review Queues
Escalation Queues
Audit Retrieval
Feed
FollowingFeedQueryService
HerdFeedQueryService

Responsibilities

Feed Composition
Feed Filtering
Feed Ordering
Feed Retrieval



#### Feed Query Architecture
Feed Query Architecture

This deserves special treatment.

Feed is a derived domain.

Feed owns:

Composition
Filtering
Ordering
Retrieval

Not content.

Not follows.

Not profiles.

Authoritative model:

FollowingFeedQueryService

      ↓

Identity Capability
Social Graph Capability
Content Capability
Governance Capability

Never:

FollowingFeedQueryService
       ↓
PostRepository

Directly.

Feed consumes capabilities and query contracts.

Not repositories.

#### Governance Query Architecture
Governance owns moderation review.

Therefore Governance owns moderation queries.

Example:

GovernanceReviewQueryService

Consumes:

Content Capability
Community Capability
Identity Capability

Produces:

Review Queue
Escalation Queue
Moderation Context

This preserves Governance ownership.

#### MongoDB Query Strategy
MongoDB Query Strategy

Repositories:

Prefer:

Simple CRUD
Simple Persistence Queries
Existence Checks

Query Services:

May use:

Aggregation Pipelines
Sorting
Filtering
Pagination
Projection
Read Optimization

This creates a clean separation:
| Layer               | Responsibility |
| ------------------- | -------------- |
| Repository          | Persistence    |
| Query Service       | Retrieval      |
| Application Service | Workflow       |
| Capability          | Integration    |

#### Query Visibility Rules
Query Services May
Read multiple collections
Aggregate data
Project data
Build DTOs
Support feed composition
Support governance review

Query Services May Not
Modify persistence state
Start workflows
Execute lifecycle transitions
Perform authorization decisions
Perform governance decisions

#### Authoritative Query Rules
DAA-36
Queries and persistence are separate architectural concerns.

DAA-37
Repositories own persistence.

DAA-38
Query Services own retrieval.

DAA-39
Complex read operations must use Query Services.

DAA-40
Feed retrieval must use Feed-owned Query Services.

DAA-41
Governance review retrieval must use Governance-owned Query Services.

DAA-42
Query ownership follows read responsibility ownership.

DAA-43
Repositories must not contain feed composition logic.

DAA-44
Repositories must not contain governance review logic.

DAA-45
Query Services may aggregate multiple collections.

DAA-46
Query Services remain read-only.

DAA-47
Query Services may not modify persistence state.

DAA-48
Query Services may not execute workflows.

DAA-49
Application Services orchestrate Query Services.

DAA-50
Feed remains the owner of feed composition queries.

#### Query Ownership Rule

Queries belong to the module that owns the read concern.

Not necessarily the module that owns the data.

#### Feed Query Ownership

Feed owns:

- FollowingFeedQueryService
- HerdFeedQueryService

#### Governance Query Ownership

Governance owns:

- GovernanceReviewQueryService
- GovernanceActivityQueryService

---

### Transaction Architecture

#### Transaction Ownership Model
Transaction Ownership Model
Controller
      ↓
Application Service
      ↓
Transaction
      ↓
Repositories

TAA-01
Only Application Services may start transactions.

TAA-02
Repositories may participate in transactions.
Repositories may not create transactions.

TAA-03
Query Services never participate in transactions.
Query Services are read-only.

#### Transaction Boundary Rule
Transactions exist only when:
Multiple persistence changes
must succeed or fail together.

Examples
Create Post
Writes:
posts
only.
Transaction:
Not required.

Create Comment
Writes:
comments
only.
Transaction:
Not required.

Vote
Writes:
votes
only.
Transaction:
Not required.

Join Herd
Writes:
memberships
only.
Transaction:
Not required.

Shepherd Assignment
Writes:
shepherdAssignments
and potentially updates herd governance metadata.
Transaction:
Required.

Governance Enforcement
Writes:
moderationActions
and
target enforcement state
Transaction:
Required.

TAA-04
Single-write workflows should not use MongoDB transactions.

TAA-05
Transactions are reserved for multi-write consistency requirements.

#### Transaction Ownership

Application Services own transactions.

Repositories participate in transactions but never create them.

#### Transaction Usage

Transactions are used only when:

- Multiple persistence changes must succeed together
- Governance enforcement requires consistency
- Multi-document consistency is required

#### Cross-Module Consistency Model
Validate → Persist

Pattern:

Capability Validation
        ↓
Local Persistence

Example:

Content Service

↓
Community Capability

Validate Membership

↓

PostRepository

Create Post

No distributed transaction.

No shared persistence ownership.

TAA-06
Cross-module workflows must prefer:
Validate
Then Persist
over distributed transactions.

TAA-07
Cross-module validation does not imply shared transaction ownership.

#### Governance Transaction Rule
Governance actions must remain auditable and consistent.
Therefore:

Moderation Action
+
Governed State Change

must commit together.

TAA-08
Governance enforcement workflows require transactions.
Example
Governance Service

Start Transaction
↓
Create Moderation Action
↓
Apply Restriction
↓
Commit

#### MongoDB Transaction Policy
Use transactions for:
Governance Enforcement
Multi-document consistency
Multi-collection writes
Critical authority transitions

Avoid transactions for:
Reads
Queries
Feed Retrieval
Validation
Single-document writes

TAA-09
MongoDB transactions are an exception mechanism.
Not the default persistence model.

#### Failure Recovery Model
When transaction exists:

Commit
OR
Rollback

No partial success.

When transaction does not exist:

Validation
↓
Persistence

Failure simply returns error.

No compensation required.

TAA-10
Failure recovery should remain transaction-based rather than compensation-based.

#### Future Extraction Validation

Current:

Application Service
        ↓
Local Transaction

Future:

Module Service
        ↓
Local Transaction

No redesign required.

What does NOT scale?

Cross-Module Transactions

Exactly why we avoid them.

#### Transaction Responsibility Matrix
| Component             | May Start Transaction |
| --------------------- | --------------------- |
| Controller            | No                    |
| Application Service   | Yes                   |
| Repository            | No                    |
| Query Service         | No                    |
| Capability Contract   | No                    |
| Governance Capability | No                    |
| Feed Query Service    | No                    |


#### Authoritative Transaction Rules
TAA-01
Application Services own transactions.

TAA-02
Repositories participate but never create transactions.

TAA-03
Query Services never participate in transactions.

TAA-04
Single-write workflows should not use transactions.

TAA-05
Transactions are reserved for multi-write consistency requirements.

TAA-06
Cross-module workflows must prefer Validate → Persist.

TAA-07
Cross-module validation does not imply shared transactions.

TAA-08
Governance enforcement workflows require transactions.

TAA-09
MongoDB transactions are exceptional, not default.

TAA-10
Failure recovery should prefer rollback over compensation.

TAA-11
Cross-module transactions are prohibited by default.

TAA-12
Distributed consistency mechanisms are out of MVP scope.

---

### Persistence Isolation Rules
Repository Isolation + Persistence Encapsulation

Authoritative Architecture:

Module
   ↓
Capability
   ↓
Repository
   ↓
Persistence

Only the owning module may see persistence internals.

#### Public Layer
Visible to other modules.

Examples:

Capability Contracts
DTOs
Validation Responses
Query Results

#### Internal Layer
Visible only inside module.

Examples:

Repositories
Query Services
Mongoose Models
Schemas
Indexes
Collection Names

#### Persistence Layer
(Database) Visible only through persistence layer.

Examples:

Mongo Collections
Aggregation Pipelines
Index Definitions
Database Queries

#### Authoritative Visibility Model
External Modules
      ↓
Capabilities

Internal Module
      ↓
Repositories
Query Services

Persistence
      ↓
MongoDB

#### Isolation Rules
##### Collection Isolation Rules
Question:
Should Content know:
memberships
collection exists?

Recommended Rule
No.
Content should know:
communityCapability.isMember()
exists.
Nothing else.

PIA-01
Collection names are private implementation details.

PIA-02
Collection ownership belongs exclusively to the owning module.

PIA-03
Foreign modules must not reference foreign collections.

Example
Allowed:
communityCapability.isMember(...)

Forbidden:
db.collection("memberships")
inside Content.

##### Schema Isolation Rules
Question:

Should Content know:

Membership Schema

fields?

Example:

{
  herdId,
  memberId,
  joinedAt,
  status
}
Recommended Rule

No.

Only Community owns membership structure.

Content should receive:

{
  isMember: true
}

or

{
  canPost: true
}

through capability contracts.

PIA-04
Schema definitions are private module assets.

PIA-05
Foreign modules must not depend on foreign schema structure.

PIA-06
Capability contracts are the approved abstraction boundary.

##### Mongoose Model Isolation Rules
Question:

Should:

MembershipModel

be importable by Content?

Recommended:

No.

Never.

Example

Forbidden:

import MembershipModel
from community

inside Content.

Allowed:
communityCapability.isMember(...)

PIA-07
Mongoose Models remain module-private.

PIA-08
Cross-module model imports are prohibited.

PIA-09
Repositories are the only consumers of Mongoose Models.

Result
Repository
    ↓
Model

instead of

Application Service
    ↓
Model

or

Foreign Module
    ↓
Model

##### Index Isolation Rules
Question:

Should Content know:

Community indexes?

Example:

{ herdId: 1, memberId: 1 }

Answer:

No.

Indexes are persistence optimization details.

Not business contracts.

PIA-10
Index definitions are private persistence concerns.

PIA-11
Index structures may change without affecting consumers.

PIA-12
Capabilities must not expose index assumptions.

##### Query Service Isolation Rules
Query Services are not integration points.

This is important.

Many architectures accidentally expose query services.

Wrong:

Content
      ↓
MembershipQueryService

Correct:

Content
      ↓
Community Capability
      ↓
MembershipQueryService

PIA-13
Query Services remain internal to their owning module.

PIA-14
Cross-module Query Service access is prohibited.

PIA-15
Query Services are implementation details.
Not contracts.

##### Repository Isolation Rules
No Cross-Module Repository Access

PIA-16
Repositories are visible only inside their owning module.

PIA-17
Cross-module repository imports are prohibited.

PIA-18
Repository APIs are not module contracts.

PIA-19
Repositories remain replaceable implementation details.


- Cross-module repository access prohibited.
- Cross-module query service access prohibited.
- Cross-module model imports prohibited.
- Cross-module collection access prohibited.

#### Persistence Encapsulation Model
Every module owns:

Capability Contracts
Repositories
Query Services
Models
Schemas
Indexes
Collections

External modules may see:

Capability Contracts
Only

Architecture:

Content

   ↓

Community Capability

   ↓

Community Internal Layer

   ↓
   ├─ Repository
   ├─ Query Service
   ├─ Model
   ├─ Schema
   └─ Collection

Everything below capability boundary remains hidden.

#### Persistence Isolation Matrix
| Artifact                   | Visible Outside Module |
| -------------------------- | ---------------------- |
| Capability Contract        | Yes                    |
| DTOs                       | Yes                    |
| Validation Results         | Yes                    |
| Repository                 | No                     |
| Query Service              | No                     |
| Mongoose Model             | No                     |
| Schema                     | No                     |
| Collection                 | No                     |
| Index                      | No                     |
| Aggregation Pipeline       | No                     |
| Transaction Implementation | No                     |

#### Future Service Extraction Validation
Current:

Content
    ↓
Community Capability

Future:

Content
    ↓
Community API

No redesign required.

Why?
Because Content never knew:

Collections
Models
Schemas
Indexes

in the first place.

This directly supports ADR-001 future evolution goals.

#### Authoritative Persistence Isolation Rules
PIA-01
Collection names are private implementation details.

PIA-02
Collection ownership belongs exclusively to owning modules.

PIA-03
Foreign collection access is prohibited.

PIA-04
Schemas are module-private assets.

PIA-05
Foreign schema dependencies are prohibited.

PIA-06
Capability contracts are the approved abstraction boundary.

PIA-07
Mongoose Models are module-private.

PIA-08
Cross-module model imports are prohibited.

PIA-09
Repositories are the only consumers of Mongoose Models.

PIA-10
Indexes are private persistence concerns.

PIA-11
Index structures may evolve independently.

PIA-12
Capabilities must not expose persistence optimizations.

PIA-13
Query Services are internal implementation details.

PIA-14
Cross-module Query Service access is prohibited.

PIA-15
Query Services are not contracts.

PIA-16
Repositories are visible only inside owning modules.

PIA-17
Cross-module repository imports are prohibited.

PIA-18
Repository APIs are not module contracts.

PIA-19
Repositories remain replaceable implementation details.

PIA-20
Capability contracts are the only approved persistence boundary crossing mechanism.


---

### MongoDB Alignment
MongoDB organization must preserve:

Domain Ownership
Module Ownership
Repository Ownership
Governance Boundaries
Feed Read-Only Nature
Future Service Extraction

without introducing:

Premature denormalization
Premature CQRS
Premature multi-database architecture

Resource-Based Collection Ownership

Collection ownership should follow authoritative resource ownership.

This aligns with:

Repository Architecture
Resource Ownership Model
API Resource Model
Module Ownership Model



#### Collection Ownership Model

Identity Module

Owns:

users

Collection.

Repository:

UserProfileRepository

Social Graph Module

Owns:

follows

Collection.

Repository:

FollowRepository

Content Module

Owns:

posts
comments
votes

Collections.

Repositories:

PostRepository
CommentRepository
VoteRepository

Community Module

Owns:

herds
memberships
shepherdAssignments

Collections.

Repositories:

HerdRepository
MembershipRepository
ShepherdAssignmentRepository

Media Module

Owns:

images

Collection.

Repository:

ImageRepository

Governance Module

Owns:

reports
moderationActions

Collections.

Repositories:

ReportRepository
ModerationActionRepository

Feed Module
Owns:
No Collections
Feed remains a derived domain.
Feed owns no persistence state.
This remains consistent with the approved Feed architecture.

##### Collection Ownership Matrix
| Module       | Collection          |
| ------------ | ------------------- |
| Identity     | users               |
| Social Graph | follows             |
| Content      | posts               |
| Content      | comments            |
| Content      | votes               |
| Community    | herds               |
| Community    | memberships         |
| Community    | shepherdAssignments |
| Media        | images              |
| Governance   | reports             |
| Governance   | moderationActions   |
| Feed         | None                |


#### Repository-to-Collection Alignment
Should repositories span multiple collections?

Example
PostRepository

manages:

posts

only.

or

PostRepository

manages:

posts
comments
votes

?

Recommended Rule

Repository authority should align with resource authority.

Result:

UserProfileRepository
      ↓
users

FollowRepository
      ↓
follows

PostRepository
      ↓
posts

CommentRepository
      ↓
comments

VoteRepository
      ↓
votes

etc.

MAA-01
One authoritative repository owns one authoritative collection.

MAA-02
Repository ownership follows collection ownership.

MAA-03
Cross-collection repository ownership is prohibited.

Why?

Because future extraction becomes trivial.

Example:

Today:

PostRepository
       ↓
posts

Future:

Content Service
       ↓
posts

No redesign.

#### Aggregate Alignment Evaluation

A subtle but important topic.

Question:

Should MongoDB collections align with:

Modules?
Aggregates?
Resources?
Evaluation
Module Alignment

Rejected.

Too coarse.

Aggregate Alignment

Partially useful.

But aggregate boundaries do not map cleanly to MongoDB collections.

Examples:

Post
Comment
Vote

remain independent resources.

Resource Alignment

Best fit.

Resources already drive:

Ownership
APIs
Authorization
Governance
Recommended Rule

Collections align primarily with resources.

Aggregates remain a business concept.

Collections remain a persistence concept.

MAA-04
Aggregate boundaries do not mandate collection boundaries.

MAA-05
Collections align with authoritative resources.

#### Persistence Model

- Resource-oriented collections
- One repository per authoritative resource
- Reference-based relationships
- Limited embedding for value objects only

#### MongoDB Modeling Strategy
Should we aggressively embed documents?
Reference-Based Modeling

Example:

{
  "_id": "comment",
  "postId": "..."
}
Advantages
Aligns with ownership.
Aligns with moderation.
Aligns with repositories.

Modeling Rule
Prefer:
Reference-Based Modeling
for authoritative resources.

MAA-06
Authoritative resources should remain independently persisted.

MAA-07
Relationships should primarily use references rather than deep embedding.

MAA-08
Embedding is allowed only for small lifecycle-dependent value objects.

Examples:
Image Metadata
Audit Metadata
Display Preferences
not independent resources.

#### Feed Persistence Rule

Feed owns no collections.

Feed is not a source of truth.

Feed remains special.

Feed owns:

FollowingFeedQueryService
HerdFeedQueryService

Only.

Feed owns:

No Collection

No Repository.

No Persistence State.

Feed composes from:

posts
profiles
follows
memberships
governance visibility

through Query Services and Capabilities.

MAA-09
Feed remains persistence-free.

MAA-10
Feed never becomes a source of truth.

#### Governance Ownership Rule

Governance authority does not imply collection ownership.

Governance owns:

reports
moderationActions

only.

Governance does not own:

posts
comments
herds
profiles

Even though Governance may govern them.

This distinction is critical.

MAA-11
Governance authority does not imply collection ownership.

MAA-12
Governed resources remain owned by originating modules.

Example

Post Restriction:

Content
      owns Post

Governance
      owns ModerationAction

Both remain independent.

#### Future Database Decomposition Validation
Current Architecture:
MongoDB
 ├─ users
 ├─ follows
 ├─ posts
 ├─ comments
 ├─ votes
 ├─ herds
 ├─ memberships
 ├─ shepherdAssignments
 ├─ images
 ├─ reports
 └─ moderationActions

Future:
Identity Database

Content Database

Community Database

Governance Database

possible.

Why?
Because ownership already exists.

Collections already map naturally.

No redesign required.

MAA-13
Collection ownership must remain future-database-decomposition compatible.

MAA-14
Current architecture remains single MongoDB deployment.

MAA-15
Future decomposition must not influence MVP complexity.

---

### Future Evolution Strategy
The Future Evolution Strategy must answer:

If Chauthara grows significantly:

Can modules become services?

Can databases be split?
Can read models evolve?
Can feeds scale independently?
Can governance scale independently?

Without requiring:

Major Redesign
Domain Reclassification
Ownership Rewrites
Persistence Rewrites

Evolution Philosophy
Build For Change

Current architecture remains simple.

Future evolution remains possible.

Advantages
Matches Architecture Drivers.
Matches ADR-001.
Matches Evolutionary Architecture principle.

FES-01
Current architecture must optimize for current requirements.

FES-02
Future evolution must remain possible without redesign.

FES-03
Future scalability concerns must not introduce present-day complexity.

#### Service Extraction Boundary
Service Extraction Evaluation
Identity

Extraction Difficulty:

Low

Reasons:

Clear ownership
Limited dependencies
Social Graph

Extraction Difficulty:

Low

Reasons:

Single resource ownership
Simple contracts
Content

Extraction Difficulty:

Moderate

Reasons:

High dependency volume
Feed participation

Still manageable.

Community

Extraction Difficulty:

Moderate

Reasons:

Membership validation
Governance integration
Governance

Extraction Difficulty:

Low

Reasons:

Strong ownership boundaries already established
Feed

Extraction Difficulty:

Very Low

Reasons:

No persistence ownership
Read-only domain

FES-04
Capability contracts are the future service extraction boundary.

FES-05
Repositories must never become extraction boundaries.

FES-06
Collection ownership must not be exposed externally.

#### Database Decomposition Boundary
Database Decomposition Readiness

Current Architecture:
MongoDB
users
follows
posts
comments
votes
herds
memberships
shepherdAssignments
images
reports
moderationActions

Future Possibility:

Identity Database

Content Database

Community Database

Governance Database

Question:

Can this happen?

Answer:

Yes.

Because ownership is already explicit.

Current:

Collection Ownership

Future:

Database Ownership

No conceptual change required.

Only infrastructure changes.

FES-07
Collection ownership is the foundation of future database ownership.

FES-08
Database decomposition must follow module ownership.

FES-09
Database decomposition must never split a module.

Example

Good:

Content Database

posts
comments
votes

Bad:

posts database

comments database

votes database

This would violate module ownership.

#### Repository Evolution Strategy

Current:

Repository
      ↓
MongoDB

Question:

Do repositories need to evolve?

Potentially.

Stage 1 (Current MVP)

Repositories:

CRUD
Persistence
Existence Checks

Stage 2 (Growing Platform)
Repositories:

Persistence
Optimized Queries
Caching Support

Stage 3 (Large Scale)
Repositories:

Persistence Only

Complex reads move entirely into query services.

Important:

No architectural change required.

Only responsibility refinement.

FES-10
Repository responsibilities may shrink over time.

FES-11
Repositories remain persistence-focused throughout all growth stages.

#### Query Evolution

Query services are the approved read-scaling mechanism.
Query Services are the most likely scaling pressure point.

Current:

Feed Query Services
Governance Query Services
Resource Query Services

Future:

Potential evolution:

Read Models

Search Infrastructure

Analytics Pipelines

Recommendation Systems

Question:

Does current architecture block this?

Answer:

No.

Because Query Services are already separate.

Current:

FollowingFeedQueryService

Future:

FeedReadModel

behind same service boundary.

Consumers remain unchanged.

FES-12
Query Services are the approved evolution point for read scaling.

FES-13
Read-model architecture may evolve behind Query Service boundaries.

FES-14
Repository architecture should not absorb read-scaling concerns.

#### Feed Evolution Strategy
Feed deserves special treatment.

Current MVP:

Chronological Feed

No recommendations.

Future Possibilities:

Ranking
Recommendations
Trending
Personalization

Question:

Where do these belong?

Not Content.

Not Community.

They belong exclusively to:

Feed Domain

This validates the earlier decision that Feed owns query composition.

FES-15
Future feed intelligence belongs exclusively to Feed.

FES-16
Content must never own feed algorithms.

FES-17
Feed evolution must not affect content ownership.

#### Governance Evolution Strategy
Current Governance:

Reports
Moderation Actions

Future Possibilities:

Automated Detection
Risk Scoring
Moderator Tooling
Governance Analytics

Question:

Where do these belong?

Answer:

Governance.

Not Content.

Not Community.

FES-18
Future governance intelligence belongs to Governance.

FES-19
Governance evolution must not require resource ownership changes.

#### Stable Architectural Boundaries

The following remain stable across future evolution:

- Domain Ownership
- Module Ownership
- Capability Contracts
- Governance Hierarchy
- Feed Derived-Domain Model

#### Scaling Trigger Rule

Scaling actions require demonstrated operational pressure.

Hypothetical future scale is not a trigger.

Repository Scaling Trigger

Consider evolution when:

Repository complexity
becomes difficult to maintain.

Not before.

Feed Scaling Trigger

Consider evolution when:

Feed query performance
becomes measurable bottleneck.

Not before.

Database Scaling Trigger

Consider decomposition when:

Operational constraints
justify separate ownership.

Not before.

Service Extraction Trigger

Consider extraction when:

Independent deployment
becomes valuable.

Not before.

FES-20
Scaling actions require demonstrated pressure.

FES-21
Hypothetical future scale is not a sufficient trigger.


#### Architectural Migration Boundaries
Stable Boundary 1

Domain Ownership

Must remain.

Stable Boundary 2

Module Ownership

Must remain.

Stable Boundary 3

Capability Contracts

Must remain.

Stable Boundary 4

Governance Authority Model

Must remain.

Stable Boundary 5

Feed Derived-Domain Model

Must remain.

FES-22
Future evolution must preserve ownership boundaries.

FES-23
Future evolution must preserve capability contracts.

FES-24
Future evolution must preserve governance hierarchy.

FES-25
Future evolution must preserve feed as a derived domain.


---

### Validation Summary

Validated Against:

- Architecture Drivers
- Domain Architecture
- Module Boundaries
- Application Layer Architecture
- Authorization Architecture
- Governance Architecture
- ADR-001

Status:
APPROVED

#### Architectural Risks Review

No blocking risks identified.

Minor future considerations:

Risk 1

Feed query complexity may eventually increase.

Mitigation:

Already isolated behind Feed Query Services.

Risk 2

Governance review queries may grow.

Mitigation:

Already isolated behind Governance Query Services.

Risk 3

Repository growth in Content module.

Mitigation:

Repository ownership already split by resource.

No redesign required.

---

## Backend Feed Architecture

### Feed Architectural Position

Feed is a Derived Domain.

Feed exists to provide content consumption views.

Feed:

- Owns no authoritative resources.
- Owns no aggregates.
- Owns no lifecycle.
- Owns no governance workflows.
- Owns no business state.

Feed remains permanently read-only.

Feed consumes information from:

- Identity
- Social Graph
- Content
- Community
- Media
- Governance

Feed may compose feed views.

Feed may not modify domain state.

---

### Feed Responsibility Model

#### Feed-Owned Concerns
FR-01 — Feed Composition

Feed owns composition of feed views.

Examples:

Following Feed
Herd Feed

Composition means:

Collecting eligible content
Combining content into a feed response
Producing a feed representation

Feed does not create content.

Feed only assembles content.

FR-02 — Feed Visibility Evaluation

Feed owns visibility evaluation during feed generation.

Examples:

Author visibility evaluation
Governance visibility evaluation
Membership visibility evaluation
Herd visibility evaluation

Feed determines:

Can this item appear?

Feed does not determine:

Should this item be moderated?

FR-03 — Feed Filtering

Feed owns filtering of ineligible content.

Examples:

Restricted content
Restricted authors
Restricted communities
Invisible membership contexts

Feed removes items that fail visibility requirements.

FR-04 — Feed Ordering

Feed owns feed ordering.

Approved MVP ordering:

Newest First
Deterministic Ordering

Already defined in Feed APIs and Architecture Drivers.

Feed does not rank.

Feed does not score.

Feed does not recommend.

FR-05 — Feed Retrieval

Feed owns feed retrieval workflows.

Examples:

Retrieve Following Feed
Retrieve Herd Feed

Feed exposes:

GET /feeds/following
GET /feeds/herds

as approved API capabilities.

#### Feed-Consumed Concerns
Identity

Consumes:

Author identity
Author visibility information
Profile visibility information

Purpose:

Determine whether author information may appear in a feed.

Social Graph

Consumes:

Follow relationships

Purpose:

Construct Following Feed candidate set.

Content

Consumes:

Posts
Post metadata
Post timestamps
Vote totals
Content visibility information

Purpose:

Provide feed items.

Community

Consumes:

Herd information
Membership information
Herd visibility information

Purpose:

Construct Herd Feed candidate set.

Media

Consumes:

Image references
Media visibility information

Purpose:

Enrich feed item representation.

Governance

Consumes:

Moderation outcomes
Enforcement outcomes
Visibility restrictions

Purpose:

Remove ineligible content.

Governance remains the authority.

Feed only consumes outcomes.

#### Feed-Forbidden Concerns
FF-01 — Content Creation

Feed may never:

Create posts
Create comments
Create votes

Content owns those workflows.

FF-02 — Content Modification

Feed may never:

Edit posts
Remove posts
Restore posts
Change vote totals

FF-03 — Community Modification

Feed may never:

Join Herds
Leave Herds
Remove members
Assign shepherds

Community owns these workflows.

FF-04 — Governance Operations

Feed may never:

Create reports
Execute moderation
Escalate moderation
Restrict resources
Restore resources

Governance owns these workflows.

FF-05 — Identity Modification

Feed may never:

Modify profiles
Modify accounts
Restrict users

FF-06 — Lifecycle Ownership

Feed may never:

Create lifecycle states
Transition lifecycle states
Persist lifecycle states

Feed owns no lifecycle.

FF-07 — Persistence Ownership

Feed may never:

Own collections
Own repositories
Own authoritative records

Feed is derived.

Feed is not a source of truth.

FF-08 — Recommendation Responsibilities

Explicitly forbidden for MVP:

Recommendation engines
Ranking systems
Personalization
Trending feeds
Engagement scoring

Consistent with architecture constraints and task requirements.

#### Feed Responsibility Rules (Authoritative)
FRR-01
Feed may compose.
Feed may not create.

FRR-02
Feed may retrieve.
Feed may not modify.

FRR-03
Feed may filter.
Feed may not govern.

FRR-04
Feed may consume governance outcomes.
Feed may not generate governance outcomes.

FRR-05
Feed may reference authoritative resources.
Feed may not own authoritative resources.

FRR-06
Feed may order content.
Feed may not rank content.

FRR-07
Feed may evaluate visibility.
Feed may not evaluate moderation authority.

FRR-08
Feed remains read-only under all circumstances.
No exceptions.

---

### Feed Composition Architecture

#### Approved Feed Types

MVP supports:

- Following Feed
- Herd Feed

No additional feed types are approved.

#### Feed Composition Principles
FCP-01 — Feed Is Composed, Never Stored

Feed views are generated from authoritative domain data.

Feed does not own feed records.

Feed does not persist feed items.

Feed does not maintain feed state.

FCP-02 — Feed Composition Is Deterministic

Given identical:

User
Visibility state
Governance state
Content state

Feed generation must produce identical results.

No randomness.

No ranking.

No recommendation logic.

FCP-03 — Feed Composition Consumes Authority Decisions

Feed does not make authority decisions.

Feed consumes:

Authorization outcomes
Membership outcomes
Governance outcomes

produced elsewhere.

FCP-04 — Visibility Before Composition

Visibility eligibility must be determined before feed assembly.

Invisible items never participate in composition.

FCP-05 — Ordering Happens After Eligibility

Feed ordering applies only to eligible items.

Workflow:

Candidate Items
→ Visibility Filtering
→ Eligibility Filtering
→ Ordering
→ Response

#### Following Feed Composition Inputs
Social Graph Inputs

Consumes:

Follow Relationships

Purpose:

Determine feed source authors.

Content Inputs

Consumes:

Personal Posts
Herd Posts
Post Metadata
Post Timestamps

Purpose:

Provide candidate feed items.

Identity Inputs

Consumes:

Author Information
Author Visibility State

Purpose:

Validate author visibility.

Community Inputs

Consumes:

Herd Visibility Information
Membership Visibility Information

Purpose:

Validate herd-context posts.

Governance Inputs

Consumes:

Post Restrictions
Author Restrictions
Herd Restrictions

Purpose:
Remove ineligible items.

#### Following Feed Composition Workflow
User
    ↓
Load Follow Relationships
    ↓
Identify Followed Authors
    ↓
Retrieve Candidate Posts
    ↓
Evaluate Visibility
    ↓
Apply Governance Outcomes
    ↓
Remove Ineligible Posts
    ↓
Order By CreatedAt DESC
    ↓
Generate Feed Response

#### Following Feed Eligibility Model
A post is eligible only when all conditions are satisfied.

FFE-01 — Author Eligibility
Author must be visible.

Examples:

Allowed:

Active profile

Rejected:

Restricted profile
Invisible profile

FFE-02 — Post Eligibility
Post must be visible.

Examples:

Allowed:

Active post

Rejected:

Removed post
Restricted post

FFE-03 — Herd Context Eligibility
For Herd Posts:

The herd must remain visible.

Examples:

Allowed:

Active herd

Rejected:

Restricted herd

FFE-04 — Governance Eligibility
Governance outcomes must allow visibility.

Examples:

Allowed:

No active restriction

Rejected:

Active moderation restriction

#### Herd Feed Composition Inputs
Community Inputs

Consumes:

Herd Information
Membership Information

Purpose:

Determine feed scope.

Content Inputs

Consumes:

Herd Posts
Post Metadata
Post Timestamps

Purpose:

Provide candidate feed items.

Identity Inputs

Consumes:

Author Information
Author Visibility State

Purpose:

Validate author visibility.

Governance Inputs

Consumes:

Herd Restrictions
Post Restrictions
Author Restrictions

Purpose:

Remove ineligible items.

#### Herd Feed Composition Workflow
User
    ↓
Validate Herd Visibility
    ↓
Validate Herd Access Eligibility
    ↓
Retrieve Herd Posts
    ↓
Evaluate Author Visibility
    ↓
Apply Governance Outcomes
    ↓
Remove Ineligible Posts
    ↓
Order By CreatedAt DESC
    ↓
Generate Feed Response

#### Herd Feed Eligibility Model
A post is eligible only when all conditions are satisfied.
HFE-01 — Herd Eligibility
Herd must be visible.

Examples:

Allowed:

Active herd

Rejected:

Restricted herd

HFE-02 — Access Eligibility
User must satisfy herd access requirements.

Examples:

Allowed:

Public herd access
Valid member access

Rejected:

No access rights

Feed does not determine membership.

Community owns membership authority.

Feed consumes membership outcomes.

HFE-03 — Post Eligibility
Post must remain visible.

Examples:

Allowed:

Active post

Rejected:

Removed post
Restricted post

HFE-04 — Author Eligibility
Author must remain visible.

Examples:

Allowed:

Active profile

Rejected:

Restricted profile

HFE-05 — Governance Eligibility
Governance outcomes must allow visibility.

Examples:

Allowed:

No active restriction

Rejected:

Active moderation restriction

#### Feed Visibility Rules

Following Feed:

Author Visible
AND
Post Visible
AND
Governance Allows Visibility
AND
(Herd Post ⇒ Herd Visible)
This becomes the authoritative Following Feed visibility rule.

Herd Feed:

User Has Herd Access
AND
Herd Visible
AND
Author Visible
AND
Post Visible
AND
Governance Allows Visibility
This becomes the authoritative Herd Feed visibility rule.

#### Feed Filtering Architecture
Filtering occurs after candidate retrieval and before ordering.
Filter Stage 1 — Author Filtering
Remove:

Restricted authors
Invisible authors

Filter Stage 2 — Herd Filtering
Remove:

Restricted herds
Invisible herds

Filter Stage 3 — Post Filtering
Remove:

Restricted posts
Removed posts
Invisible posts

Filter Stage 4 — Governance Filtering
Apply moderation outcomes.

Feed consumes:

Content restrictions
Profile restrictions
Herd restrictions

Feed never evaluates moderation authority.

Feed only applies outcomes.

#### Feed Ordering Rules
Ordering remains:

CreatedAt DESC

Newest content first.

Deterministic Tie-Breaking
When timestamps are identical:

CreatedAt DESC
↓
Resource Identifier ASC

Purpose:

Stable pagination
Deterministic retrieval
Consistent feed generation

No ranking signals.

No popularity signals.

No engagement signals.

#### Authoritative Feed Composition Rules
FCR-01
Feed composition occurs dynamically from authoritative module data.

FCR-02
Feed items are never stored as authoritative resources.

FCR-03
Visibility evaluation occurs before feed composition.

FCR-04
Governance outcomes must be applied before ordering.

FCR-05
Only eligible items may participate in feed ordering.

FCR-06
Following Feed source scope is determined exclusively by follow relationships.

FCR-07
Herd Feed source scope is determined exclusively by herd context.

FCR-08
Ordering remains chronological:
Newest First

FCR-09
Feed may consume governance outcomes.
Feed may not create governance outcomes.

FCR-10
Feed composition remains read-only.
No feed workflow may modify business state.

---

### Feed Query Architecture

#### Feed Query Services

Approved Feed Query Services:

- FollowingFeedQueryService
- HerdFeedQueryService

#### Feed Query Principles
FQP-01 — Feed Owns Feed Queries

Feed owns:

Following Feed queries
Herd Feed queries

Feed does not own:

Content queries
Profile queries
Membership queries

Those remain owned by their respective modules.

FQP-02 — Feed Consumes Capabilities

Feed consumes module capabilities.

Feed never consumes:

Repositories
Collections
Persistence models
Database queries

This preserves module isolation.

FQP-03 — Repository Isolation Is Absolute

Feed must never access:

Identity repositories
Social Graph repositories
Content repositories
Community repositories
Media repositories
Governance repositories

Repository ownership remains module-local.

FQP-04 — Query Services Are Feed-Owned

Feed owns query orchestration.

Feed does not own source data retrieval implementations.

FQP-05 — Capabilities Before Data

Feed depends on capabilities.

Not data structures.

Not persistence models.

Not collections.

This preserves future extraction readiness.

#### FollowingFeedQueryService
Responsibility
Generate Following Feed candidate views.

Responsibilities:
Load followed authors
Retrieve candidate posts
Retrieve author information
Retrieve governance visibility information
Assemble feed candidates
Return feed-ready projections

Does not:

Modify state
Persist data
Execute moderation
Execute authorization decisions
Inputs
Required Inputs
viewerId
page
limit

Derived from:

GET /feeds/following

Approved Feed API.

Outputs

Returns:

FollowingFeedResult
 ├─ Feed Items
 ├─ Pagination Metadata
 └─ Visibility-Eligible Content

Output remains derived.

No authoritative resources created.

##### Dependencies
Consumes capabilities from:

Social Graph

Purpose:

Determine followed authors.

Consumes:

GetFollowedProfiles()

Content

Purpose:

Retrieve posts authored by followed users.

Consumes:

GetPostsByAuthors()

Identity

Purpose:

Retrieve author visibility information.

Consumes:

GetProfileVisibility()

Community

Purpose:

Validate herd-context visibility.

Consumes:

GetHerdVisibility()

Governance

Purpose:

Retrieve moderation visibility outcomes.

Consumes:

GetVisibilityRestrictions()

Media

Purpose:

Resolve image references.

Consumes:

GetMediaReferences()

Feed may not directly access:

- Foreign repositories
- Foreign collections
- Foreign persistence models

#### Following Feed Query Workflow
FollowingFeedQueryService
        ↓
Social Graph Capability
        ↓
Followed Profiles
        ↓
Content Capability
        ↓
Candidate Posts
        ↓
Identity Capability
        ↓
Author Visibility
        ↓
Community Capability
        ↓
Herd Visibility
        ↓
Governance Capability
        ↓
Visibility Outcomes
        ↓
Media Capability
        ↓
Image References
        ↓
Feed Projection

#### HerdFeedQueryService
Responsibility

Generate Herd Feed candidate views.

Responsibilities:

Retrieve herd posts
Retrieve author information
Retrieve herd visibility information
Retrieve governance outcomes
Assemble feed candidates

Does not:

Persist state
Execute moderation
Change membership
Change content
Inputs
Required Inputs
viewerId
herdId
page
limit

Derived from:

GET /feeds/herds

Approved Feed API.

Outputs

Returns:

HerdFeedResult
 ├─ Feed Items
 ├─ Pagination Metadata
 └─ Visibility-Eligible Content

Derived only.

##### Dependencies

Consumes capabilities from:

Community

Purpose:

Validate herd access.

Consumes:

GetHerdAccessInformation()
GetMembershipInformation()

Content

Purpose:

Retrieve herd posts.

Consumes:

GetPostsByHerd()

Identity

Purpose:

Retrieve author visibility.

Consumes:

GetProfileVisibility()

Governance

Purpose:

Retrieve moderation visibility outcomes.

Consumes:

GetVisibilityRestrictions()

Media

Purpose:

Resolve image references.

Consumes:

GetMediaReferences()

Feed may not directly access:

- Foreign repositories
- Foreign collections
- Foreign persistence models

#### Herd Feed Query Workflow
HerdFeedQueryService
        ↓
Community Capability
        ↓
Access Validation Data
        ↓
Content Capability
        ↓
Candidate Herd Posts
        ↓
Identity Capability
        ↓
Author Visibility
        ↓
Governance Capability
        ↓
Visibility Outcomes
        ↓
Media Capability
        ↓
Image References
        ↓
Feed Projection

#### Feed Query Dependency Model
Feed may consume capabilities from approved modules only.

Identity Capabilities
Feed May Consume:

Profile Retrieval
Profile Visibility
Profile Summary Information

Feed Must Not Consume:

Identity Repository
User Collection
Authentication Infrastructure

Social Graph Capabilities
Feed May Consume:

Follow Relationship Retrieval
Followed Profile Discovery

Feed Must Not Consume:

Follow Repository
Follow Collection
Persistence Queries

Content Capabilities
Feed May Consume:

Post Retrieval
Post Visibility Information
Post Metadata

Feed Must Not Consume:

Post Repository
Comment Repository
Vote Repository
Mongo Collections

Community Capabilities
Feed May Consume:

Herd Visibility
Membership Visibility
Herd Access Information

Feed Must Not Consume:

Herd Repository
Membership Repository
Shepherd Repository

Media Capabilities
Feed May Consume:

Media References

Media Visibility
Feed Must Not Consume:

Media Repository
Storage Provider
Cloudinary Integration

Governance Capabilities
Feed May Consume:

Visibility Outcomes
Restriction Outcomes
Moderation Visibility Information

Feed Must Not Consume:

Report Repository
Moderation Repository
Governance Workflows

#### Feed Query Boundary Rules
FQB-01
Feed may consume capabilities.
Feed may not consume repositories.

FQB-02
Feed may consume projections.
Feed may not consume persistence models.

FQB-03
Feed may consume visibility outcomes.
Feed may not consume governance workflows.

FQB-04
Feed may retrieve authoritative information.
Feed may never become authoritative.

FQB-05
Feed may orchestrate retrieval.
Feed may not execute lifecycle transitions.

FQB-06
Cross-module access must occur through capability contracts only.
Direct repository access is prohibited.

FQB-07
Cross-module collection access is prohibited.

FQB-08
Cross-module persistence model access is prohibited.

FQB-09
Feed Query Services are the only approved Feed retrieval orchestration layer.

#### Approved Feed Query Structure
Feed Controller
        ↓
Feed Application Service
        ↓
Feed Query Service
        ↓
Capability Contracts
        ↓
Identity Module

Social Graph Module

Content Module

Community Module

Media Module

Governance Module

Not allowed:

Feed Service
      ↓
Content Repository

Not allowed:

Feed Service
      ↓
Mongo Collection

Not allowed:

Feed Service
      ↓
Foreign Persistence Model

---

### Feed Execution Architecture

#### Following Feed Execution Flow

Request
    ↓
Authentication
    ↓
Feed Controller
    ↓
Request Validation
    ↓
GetFollowingFeedApplicationService
    ↓
Authorization
    ↓
FollowingFeedQueryService
    ↓
Visibility Evaluation
    ↓
Governance Filtering
    ↓
Feed Composition
    ↓
Ordering
    ↓
Response

Stage 1 — Request

Example:

GET /feeds/following?page=1&limit=20

Request enters API layer.

Stage 2 — Authentication

Purpose:

Identify viewer.

Produces:

AuthenticatedUser
 ├─ userId
 ├─ roles
 └─ identity context

Feed execution requires viewer context.

Stage 3 — Feed Controller

Responsibilities:

Read query parameters
Read authenticated identity
Create application request object

Example:

GetFollowingFeedRequest
 ├─ viewerId
 ├─ page
 └─ limit

Controller performs no business logic.

Consistent with Application Layer Architecture.

Stage 4 — Request Validation

Validate:

page
limit
query contract compliance

Examples:

Allowed:

page=1
limit=20

Rejected:

page=-1
limit=5000

Business validation does not occur here.

Stage 5 — Feed Application Service

Execution ownership begins.

Example:

GetFollowingFeedApplicationService

Responsibilities:

Coordinate workflow
Invoke authorization
Invoke query service
Coordinate visibility evaluation
Coordinate composition

This becomes the workflow owner.

Stage 6 — Feed Authorization Check

Purpose:

Determine whether actor may retrieve feed.

Questions answered:

Is user authenticated?

Is user allowed to access feed APIs?

This is not ownership validation.

Feed retrieval is not ownership-driven.

Authorization remains explicit.

Stage 7 — FollowingFeedQueryService

Purpose:

Retrieve candidate feed projections.

Consumes:

Social Graph capabilities
Content capabilities
Identity capabilities
Community capabilities
Governance capabilities
Media capabilities

Returns:

Candidate Feed Items

No visibility guarantees yet.

Stage 8 — Visibility Evaluation

Purpose:

Determine feed eligibility.

Checks:

Author Visible?

Post Visible?

Herd Visible?

Rules originate from:

Identity
Content
Community

Feed applies them.

Feed does not own them.

Stage 9 — Governance Filtering

Purpose:

Apply moderation outcomes.

Examples:

Remove:

Restricted profiles
Restricted posts
Restricted herds

Feed consumes governance decisions.

Feed does not create governance decisions.

Consistent with Governance Architecture.

Stage 10 — Feed Composition

Purpose:

Build feed representation.

Output:

Feed Item Projection

Contains:

Post
Author summary
Herd summary (if applicable)
Media references
Vote totals

Still derived.

Stage 11 — Ordering

Apply approved feed ordering:

CreatedAt DESC

Tie breaker:

CreatedAt DESC
↓
ResourceId ASC

Deterministic ordering preserved.

Stage 12 — Response Mapping

Convert application result into API contract response.

Produces:

FollowingFeedResponse

Consistent with Feed API contracts.

#### Herd Feed Execution Flow

Request
    ↓
Authentication
    ↓
Feed Controller
    ↓
Request Validation
    ↓
GetHerdFeedApplicationService
    ↓
Authorization
    ↓
Herd Access Validation
    ↓
HerdFeedQueryService
    ↓
Visibility Evaluation
    ↓
Governance Filtering
    ↓
Feed Composition
    ↓
Ordering
    ↓
Response

Additional Herd Feed Stage

Unlike Following Feed, Herd Feed requires access validation.

Herd Access Validation

Purpose:

Determine whether actor may access the requested herd feed.

Consumes:

Community capabilities.

Questions answered:

Does Herd Exist?

Is Herd Visible?

Does User Have Access?

Examples:

Allowed:

Public herd
Valid member access

Rejected:

Access denied
Membership required

Important:

Feed consumes access outcomes.

Community owns access decisions.



#### Feed Execution Principles
FEP-01 — Feed Is A Read Workflow

Feed execution is fundamentally different from:

Create Post
Join Herd
Follow User
Report Content

Those are write workflows.

Feed execution is a read workflow.

Therefore:

No state mutation
No ownership mutation
No lifecycle transitions
No transaction ownership

FEP-02 — Feed Application Service Owns Execution

Consistent with Application Layer Architecture.

Controllers remain transport adapters.

Feed Application Services become execution owners.

Examples:

GetFollowingFeedApplicationService

GetHerdFeedApplicationService

Responsibilities:

Workflow orchestration
Visibility coordination
Feed composition coordination
Query service invocation
Response preparation

FEP-03 — Visibility Is Explicit

Feed visibility evaluation must never be implicit.

Visibility must be executed as a dedicated stage.

Examples:

Author visibility
Post visibility
Herd visibility
Governance visibility

FEP-04 — Governance Is Explicit

Feed must explicitly consume governance outcomes.

Feed may not bypass governance restrictions.

Feed may not infer governance decisions.

Feed may only use approved governance capabilities.

FEP-05 — Composition Happens After Eligibility

Feed composition may only occur after:

Authorization
Visibility evaluation
Governance evaluation

Only eligible items participate in composition.

#### Feed Authorization Checkpoints
Checkpoint 1 — Authentication

Required before feed execution begins.

Purpose:

Identify actor.

Checkpoint 2 — Feed Access Authorization

Purpose:

Determine feed retrieval eligibility.

Example:

Authenticated User
→ Allowed
Checkpoint 3 — Herd Access Authorization

Herd Feed only.

Purpose:

Determine herd visibility eligibility.

Delegated to Community capability.

#### Feed Visibility Checkpoints
Visibility evaluation occurs after query retrieval.
| Visibility Check       | Source Module |
| ---------------------- | ------------- |
| Author Visibility      | Identity      |
| Post Visibility        | Content       |
| Herd Visibility        | Community     |
| Media Visibility       | Media         |
| Restriction Visibility | Governance    |

#### Feed Governance Checkpoints
Governance evaluation occurs before composition.
| Governance Outcome | Effect                 |
| ------------------ | ---------------------- |
| Profile Restricted | Remove Content         |
| Post Restricted    | Remove Content         |
| Herd Restricted    | Remove Content         |
| Media Restricted   | Remove Media Reference |

#### Query Execution Sequence
Following Feed
Social Graph
    ↓
Content
    ↓
Identity
    ↓
Community
    ↓
Governance
    ↓
Media

Rationale:

Follow relationships determine candidate scope.

Everything else narrows visibility.

Herd Feed
Community
    ↓
Content
    ↓
Identity
    ↓
Governance
    ↓
Media

Rationale:

Herd context determines candidate scope.

Everything else narrows visibility.

#### Response Generation Architecture
Feed Result Model

Application Service returns:

FeedResult
 ├─ Items
 ├─ Pagination
 ├─ Metadata

Controller converts result into:

API Response

Controller remains transport-only.


#### Feed Execution Rules
FER-01
Feed execution is a read workflow.

FER-02
Feed Application Services own feed execution.

FER-03
Controllers remain transport adapters.

FER-04
Authorization executes before feed retrieval.

FER-05
Visibility evaluation executes before composition.

FER-06
Governance filtering executes before composition.

FER-07
Only eligible items may participate in feed ordering.

FER-08
Feed execution never owns transactions.

FER-09
Feed execution never performs persistence.

FER-10
Feed execution remains read-only.
No exceptions.

---

### Feed Validation Summary

Validated Against:

- Architecture Drivers
- Backend Architectural Style
- Backend Domain Architecture
- Backend Module Boundaries
- Backend Application Layer Architecture
- Backend Authorization Architecture
- Backend Governance Architecture
- Backend Data Access Architecture
- ADR-001

Validation Results:

- Ownership Boundaries: PASS
- Authority Boundaries: PASS
- Dependency Boundaries: PASS
- Read-Only Guarantees: PASS
- Governance Integration: PASS
- Architectural Principle Compliance: PASS

Backend Feed Architecture approved.

--- 

## Backend Media Architecture
Approved responsibilities:
Image Upload
Image Ownership
Image Lifecycle Management
Media Attachment Support
External Media Storage Integration

Media is currently consumed by:
Identity (Profile Images)
Community (Herd Images)
Content (Post Images)

Media exists because image lifecycle differs from content lifecycle, profile lifecycle, and community lifecycle.

### Media Responsibility Architecture
Architectural Purpose
Media is responsible for:
Image creation
Image ownership
Image lifecycle
Image attachment references
Image visibility state
Storage coordination
Media governance integration

Media is NOT responsible for:
Profiles
Herds
Posts
Feed composition
Governance workflows

### Media Ownership Architecture
#### Media Ownership Model
Authoritative Resource

The authoritative resource is:
Image
Media owns:
Image identity
Image metadata
Image owner
Image lifecycle state
Image governance state
Image attachment references
Approved API resource model already classifies Image as an independent primary resource.

#### Should Media Own Files Or References?
Decision

Media owns:

Image resource
Image metadata
Storage location reference

Media does NOT own:

Physical storage implementation
Rationale

The platform business resource is:

Image

not:

Cloudinary File
or
Storage Object

Storage systems are infrastructure concerns.

Media owns the business representation.

Infrastructure owns storage mechanics.

This remains consistent with Application Layer and Infrastructure separation.

#### Media Ownership Definition

An image is owned by:

The user that uploaded it.

Ownership includes:

Deletion authority
Attachment authority
Reuse authority

unless governance restrictions apply.

#### Authority Boundary Model
Media Owns

Media exclusively owns:

Image lifecycle
Image ownership
Image attachment records
Image visibility state
Image metadata

Only Media may modify those concerns.

Media References

Media may reference:

User Profile
Herd
Post

for attachment purposes.

Reference does not imply ownership.

Media Does NOT Own

Media does not own:

Identity Resources
User Profile

Owned by Identity.

Community Resources
Herd
Membership
Shepherd Assignment

Owned by Community.

Content Resources
Post
Comment
Vote

Owned by Content.

Governance Resources
Report
Moderation Action

Owned by Governance.

Does Attaching An Image Transfer Ownership?
Decision

No.

Attachment never transfers ownership.

Can Content Own Images?
Decision

No.

Content may reference images.

Content never owns images.

Can Community Own Images?
Decision

No.

Community may reference images.

Community never owns images.

Can Identity Own Images?
Decision

No.

Identity may reference images.

Identity never owns images.

#### Reusability Model
Core Architectural Rule

Media must remain reusable across domains.

Therefore:

Identity
Community
Content

must all consume the same Media capability model.

Approved Pattern

Identity
↓
Media Reference

Community
↓
Media Reference

Content
↓
Media Reference

Forbidden Pattern

ProfileImage
HerdImage
PostImage

as separate resource types.

Rationale

Separate image resources would:

Duplicate lifecycle logic
Duplicate ownership logic
Duplicate governance integration
Increase maintenance burden

Violates:

Simplicity First
Independent Evolvability
Domain-Oriented Modularity

#### Media Lifecycle Ownership
Lifecycle Owner

Media owns:

Entire Image Lifecycle

No other module may change image lifecycle state.

This follows the approved domain rule:

A domain may modify only resources it owns. architecture. (Governance placement section)

#### Media Governance Position
Architectural Position

Media is:

Supporting Business Domain

Consistent with approved module inventory. may govern. Governance may not own.**

Approved ownership boundaries
Governance separation
Feed read-only architecture
Future extensibility (additional media types later)
Simplicity First

without introducing new domains or ownership ambiguity.

### Media Contract Architecture
#### Image Lifecycle Model
Design Principle

The Image lifecycle should represent:

Business state
Visibility state
Attachment state

It should not model:

Storage implementation details
Upload processing details
CDN details
Infrastructure states

#### Candidate States Evaluation

Proposed states:

Uploaded
Attached
Detached
Restricted
Deleted

Evaluate each.

Uploaded
Meaning

Image exists.

Owned by a user.

Not attached to any resource.

Example

User uploads image.

Has not yet attached it anywhere.

Decision

Required

Attached
Meaning

Image is actively referenced by at least one resource.

Examples:

Profile image
Herd image
Post image
Decision

Required

Detached
Meaning

Image exists.

No active attachments remain.

Example

User replaces profile image.

Old image still exists.

No resources reference it.

Decision

Required

Restricted
Meaning

Governance has restricted image visibility.

Ownership remains unchanged.

Image remains stored.

Image remains recoverable.

Decision

Required

Consistent with Governance architecture.

Governance restricts visibility.

Governance does not destroy ownership.

Deleted
Meaning

Image lifecycle terminated.

Image no longer available for normal use.

Decision

Required

#### Approved Lifecycle States
The authoritative Image lifecycle becomes:
Uploaded
   ↓
Attached
   ↓
Detached
   ↓
Deleted

Restricted may occur from:
Uploaded
Attached
Detached

Restricted
   ↓
Restored

#### Forbidden States

The following states are rejected.

Draft

No business requirement.

Image upload is already explicit.

Pending Moderation

Governance architecture does not require pre-approval moderation.

Rejected.

Archived

No approved retention requirement.

Rejected.

Processing

Infrastructure concern.

Not business state.

Rejected.

Hidden

Already represented by Restricted.

Rejected.

#### Lifecycle Authority Model
Media Owns

Media exclusively owns:

Uploaded
Attached
Detached
Deleted

transitions.

Governance Owns

Governance owns:

Restriction decisions
Restoration decisions

through Moderation Actions.

Governance does not own Image lifecycle.

This remains consistent with approved Governance architecture. Resource Ownership Model and Modular Monolith boundaries.

#### Media Module Position
Module Classification

Media remains:

Supporting Business Module

Not:

Core Business Module

because platform participation can exist without media.

Users can:

Register
Follow
Post
Comment
Vote
Join Herds

without uploading images.

Architectural Role

Media provides:

Reusable Media Asset Management

for:

Identity
Community
Content

Media does not own:

Profiles
Herds
Posts

It owns only:

Image

resources.

#### Media Module Responsibilities
Approved Responsibilities
Responsibility 1

Image Upload

Responsibility 2

Image Retrieval

Responsibility 3

Image Ownership Enforcement

Responsibility 4

Attachment Management

Responsibility 5

Image Lifecycle Management

Responsibility 6

Media Visibility State

(Governance outcomes applied)

Responsibility 7

Media Metadata Management

#### Explicit Non-Responsibilities

Media must NOT own:

Profile Management

Identity owns this.

Herd Management

Community owns this.

Post Management

Content owns this.

Feed Composition

Feed owns this.

Moderation Decisions

Governance owns this.

Membership Validation

Community owns this.

Content Visibility Decisions

Governance owns this.

#### Media Resource Inventory
MVP Resource Inventory
Image

Authoritative Media resource.

Owns:

Identity
Ownership
Lifecycle
Attachment Relationships
Visibility State
Storage Metadata
No Additional Resources

Rejected for MVP:

Album

No requirement.

Folder

No requirement.

Gallery

No requirement.

Collection

No requirement.

Media Library

No business requirement.

#### Media Aggregate Architecture
Aggregate Evaluation

Question:

Should Media own multiple aggregates?

Candidate

Image Aggregate

Contains:

Image
Attachment References
Ownership
Lifecycle State
Visibility State
Decision

Approved.

Single aggregate.

Aggregate Boundary
Image Aggregate
 ├── Image
 ├── Ownership
 ├── Lifecycle
 ├── Visibility State
 └── Attachment References

Simple.

Consistent with MVP scope.

#### Media Capability Architecture

Following approved module interaction rules, modules expose capabilities rather than repositories or entities.

Capability Group 1
Upload Capabilities
CreateImage()

Purpose:

Create Media resource.

Capability Group 2
Ownership Capabilities
IsImageOwner()
GetImageOwner()

Purpose:

Ownership validation.

Capability Group 3
Attachment Capabilities
AttachImage()
DetachImage()

Purpose:

Relationship management.

Capability Group 4
Retrieval Capabilities
GetImage()
ImageExists()

Purpose:

Reference validation.

Capability Group 5
Visibility Capabilities
IsImageVisible()
IsImageRestricted()

Purpose:

Feed and consumer visibility.

Capability Group 6
Lifecycle Capabilities
DeleteImage()

Purpose:

Lifecycle transition.

#### Public Contract Architecture
Rule

Consumers may access Media only through Media Contract.

Never through:

Media Repository
Media Collection
Media Models
Approved Public Contract
MediaContract

CreateImage()

GetImage()

ImageExists()

IsImageOwner()

GetImageOwner()

AttachImage()

DetachImage()

DeleteImage()

IsImageVisible()

IsImageRestricted()

#### Media Dependency Graph
Identity
    ↑
    |
  Media

Consumers:

Identity
Community
Content
Governance
Feed

Meaning:

Media depends on Identity

Everyone else consumes Media

#### Media Workflow Boundaries
Identity Workflow Example
Change Profile Image

Identity owns:

Profile Update

Media owns:

Attachment Transition
Community Workflow Example
Change Herd Cover

Community owns:

Herd Update

Media owns:

Attachment Transition
Content Workflow Example
Create Post With Image

Content owns:

Post Creation

Media owns:

Image Attachment

#### Media Repository Ownership

Consistent with approved Data Access Architecture:

Media owns:

Image Repository
Image Queries
Image Persistence

No external module may:

Read Image Collection Directly
Write Image Collection Directly

Ownership remains local.

### Media Visibility Architecture
#### Visibility Architecture
Visibility Inputs

Visibility evaluation consumes:

Image State
Active
Deleted
Restricted
Governance State
Restricted
Restored
Ownership State
Owner
Viewer
Anonymous

where applicable.

#### Authoritative Visibility Flow
Image Request
    ↓
Load Image
    ↓
Evaluate Lifecycle
    ↓
Evaluate Governance State
    ↓
Determine Visibility
    ↓
Result
Visibility Outcomes
Visible

Allowed.

Hidden

Governance restriction.

Not Found

Deleted lifecycle.

#### Feed Visibility Integration

Feed consumes:

IsImageVisible()

from Media.

Feed Flow
Feed Service
    ↓
Media Contract
    ↓
Visibility Result

Feed never evaluates:

Restriction Rules
Deletion Rules

itself.

Media remains authority.


### Media Execution Architecture
#### Media Execution Principles
MEP-01 — Media Owns Media Workflows

Only Media may execute:

Upload Image
Delete Image
Attach Image
Detach Image
Restore Image

No external module may execute Media lifecycle transitions.

MEP-02 — Application Services Own Execution
Media workflows execute through:

Controller
    ↓
Media Application Service
    ↓
Domain Validation
    ↓
Repository

Never:

Controller
    ↓
Repository

This remains consistent with the approved Application Layer Architecture.

MEP-03 — Ownership Before Mutation
Ownership validation must occur before:

deletion
attachment changes
visibility changes initiated by owner actions

MEP-04 — Governance Before Visibility
Governance outcomes must always participate in visibility evaluation.

Visibility cannot ignore governance state.

MEP-05 — Media Remains Storage-Agnostic
Execution architecture must not depend on:

Cloudinary
S3
Local Storage

Media owns business workflows.

Infrastructure owns storage implementation.

#### Upload Execution Architecture
Use Case

User uploads image.

Examples:

Profile image
Profile cover
Herd image
Herd cover
Post image
Execution Flow
Request
    ↓
Authentication
    ↓
Media Controller
    ↓
Request Validation
    ↓
UploadImageApplicationService
    ↓
Ownership Context Validation
    ↓
Media Domain Rules
    ↓
Storage Upload
    ↓
Create Image Resource
    ↓
Persist Image
    ↓
Response
Ownership Context Validation

Validate:

Actor Exists
Actor Eligible

via Identity Contract.

Media does not validate passwords.

Media does not authenticate.

Identity remains root authority.

#### Delete Image Execution Architecture
Use Case

Owner deletes image.

Execution Flow
Request
    ↓
Authentication
    ↓
Media Controller
    ↓
DeleteImageApplicationService
    ↓
Authorization
    ↓
Ownership Validation
    ↓
Governance Validation
    ↓
Delete Image
    ↓
Persist
    ↓
Response
Required Validations
Ownership
IsImageOwner()

must pass.

Governance

Image cannot bypass:

Restriction State
Removal State

rules.

Governance remains authoritative.

#### Attachment Execution Architecture
Purpose

Associate Image with:

Profile
Herd
Post
Architectural Principle

Attachment ownership belongs to Media.

Business ownership belongs elsewhere.

Example

Profile Image Update

Identity
    ↓
Media Contract
    ↓
AttachImage()

Identity owns:

Profile Lifecycle

Media owns:

Attachment Relationship

#### Attachment Workflow Execution
Example

Create Post With Image

Content Controller
    ↓
CreatePostApplicationService
    ↓
Media Contract
        ↓
        AttachImage()
    ↓
Persist Post

Media validates:

Image Exists
Image Visible
Image Available

Content validates:

Post Rules
Membership Rules

Ownership remains preserved.

#### Retrieval Execution Architecture
Use Case

Display image.

Execution Flow
Request
    ↓
Media Controller
    ↓
GetImageApplicationService
    ↓
Visibility Evaluation
    ↓
Return Metadata

Important:

Media evaluates visibility.

Consumers do not reimplement visibility rules.

#### Cross-Module Execution Rules
Identity

Allowed:

Upload Profile Image
Attach Profile Image

via Media Contract.

Community

Allowed:

Upload Herd Image
Attach Herd Image

via Media Contract.

Content

Allowed:

Upload Post Image
Attach Post Image

via Media Contract.

Governance

Allowed:

Restrict Image
Restore Image

via Media Contract.

Feed

Allowed:

Check Visibility
Retrieve Metadata

via Media Contract.

#### Media Audit Architecture
Audit Requirement

Media itself does not own moderation audit history.

Governance owns moderation audit history.

Consistent with Governance Architecture.

Media Audit Events

Media should emit audit-worthy events:

Image Uploaded
Image Deleted
Image Restricted
Image Restored
Attachment Created
Attachment Removed

Governance may consume:

Restriction
Restoration

events.

#### Failure Handling Architecture
Storage Failure

Example:

Upload succeeds partially

Rule:

Image resource must not be persisted if storage upload fails.

Persistence Failure

Example:

Storage upload succeeds
Database save fails

Rule:

Compensating cleanup must execute.

Remove orphaned storage asset.

Governance Failure

Example:

Moderation action creation fails

Rule:

Governance transaction fails.

Restriction not committed.

#### Transaction Architecture
Media-Owned Transactions

Media workflows own:

Upload
Delete
Attach
Detach

transactions.

Governance Transactions

Governance owns:

Moderation Action Creation
Restriction Workflow
Restoration Workflow

transactions.

Rule

Single workflow owner.

Single transaction owner.

Consistent with Application Layer Architecture.

#### Media Execution Rules
MER-01
Media Application Services own Media workflow execution.

MER-02
Ownership validation executes before mutation.

MER-03
Governance validation executes before visibility decisions.

MER-04
Only Media may modify Image lifecycle state.

MER-05
Governance may govern Image state without owning Image resources.

MER-06
Cross-module interactions occur through Media Contracts only.

MER-07
Feed consumes Media visibility outcomes.

MER-08
Media remains storage-provider agnostic.

MER-09
Storage failures must not create orphaned Image resources.

MER-10
Media visibility evaluation remains centralized.

### Media Governance Architecture
#### Governance Integration Architecture

Governance owns:

Restriction
Restoration

workflows.

Media owns:

Image Lifecycle

workflows.

These remain separate.

#### Governance Restriction Flow
Example

Platform Administrator restricts image.

Execution:

Governance Controller
    ↓
Governance Application Service
    ↓
Authority Validation
    ↓
Target Validation
    ↓
Media Contract
        ↓
        Restrict Image
    ↓
Create Moderation Action
    ↓
Response

Important:

Governance does not directly modify repositories.

Only Media modifies Image state.

This preserves module ownership boundaries.

#### Governance Restoration Flow
Example

Administrator restores image.

Execution:

Governance Service
    ↓
Media Contract
        ↓
        Restore Image

Media remains owner.

Governance remains authority.

#### Governance Boundary Rules
GBR-M-01
Governance may restrict images.

GBR-M-02
Governance may restore images.

GBR-M-03
Governance may audit images.

GBR-M-04
Governance never owns images.

GBR-M-05
Governance never accesses Media repositories directly.

GBR-M-06
Governance actions must create moderation records.

### Media Evolution Strategy
#### Future Evolution Compatibility

Current architecture supports:

Video
Video Visibility
Video Governance
Video Attachments
Audio
Audio Visibility
Audio Governance
File Attachments
File Visibility
File Governance

No redesign required.

Execution model remains reusable.

#### Future Evolution Boundaries

Potential future additions:

Video
Media Resource
Audio
Media Resource
File Attachments
Media Resource
Processing Pipelines
Media Workflow

None require:

Module split
Domain split
Architecture redesign

The current boundary remains extensible and aligned with Evolutionary Architecture. -Oriented Modular Monolith.

Against Module Boundary Rules

Compliant.

Ownership, lifecycle, and repository boundaries remain preserved.

Against Governance Architecture

Compliant.

Governance governs images without acquiring ownership.

Against Feed Architecture

Compliant.

Feed consumes image information but remains read-only.

Against Data Access Architecture

Compliant.

Media repositories remain private to the module.

---

## Backend Error Handling Architecture

### Error Handling Principles
EHP-01 — Errors Are Domain-Aware

Errors are not technical implementation details.

Errors represent:

Business rule violations
Ownership violations
Governance violations
Resource state violations
Infrastructure failures

The architecture treats errors as first-class architectural objects.

EHP-02 — Errors Originate At The Lowest Responsible Layer

Errors should be created where knowledge exists.
| Situation                | Owner                  |
| ------------------------ | ---------------------- |
| Invalid membership state | Community Domain       |
| Post already deleted     | Content Domain         |
| Unauthorized moderation  | Governance Domain      |
| Database unavailable     | Infrastructure         |
| Missing resource         | Repository/Application |

EHP-03 — Errors Flow Upward Only

Errors propagate:

Infrastructure
    ↑
Repository
    ↑
Domain
    ↑
Application
    ↑
API

No layer may push errors downward.

EHP-04 — Error Translation Occurs At Boundaries

Errors may be translated only when crossing architectural boundaries.

Examples:

MongoError
    ↓
InfrastructureError

InfrastructureError
    ↓
InternalErrorResponse

EHP-05 — Internal Errors Are Never API Contracts

Internal implementation failures must never become client-visible responses.

Examples:

Forbidden:

MongoDB exceptions
Cloudinary exceptions
Stack traces
Collection names
Internal queries
File paths

EHP-06 — Ownership Boundaries Apply To Errors

The module that owns the violated rule owns the error.

Example:

Membership violation:

Owned by Community module.

Not Content.

Even if Content triggered the workflow.

### Error Taxonomy
Category 1 — Validation Errors

Purpose:

Input violates API contract.

Examples:

Missing required field
Invalid enum
Invalid query parameter
Invalid pagination
Created By

API Validation Layer

May Be Transformed By

Application Layer

Exposed To Client

Yes

Category 2 — Authentication Errors

Purpose:

Identity cannot be established.

Examples:

Missing token
Invalid token
Expired session
Created By

Authentication middleware

May Be Transformed By

Application Layer

Exposed

Yes

Category 3 — Authorization Errors

Purpose:

Actor lacks permission.

Examples:

Non-owner edits post
Non-shepherd moderates herd
Created By

Authorization services

Owned By

Authorization Architecture

Exposed

Yes

Category 4 — Ownership Errors

Purpose:

Ownership boundary violation.

Examples:

Edit foreign post
Delete foreign image
Modify foreign herd
Created By

Owning Domain

Examples:

Content
Media
Community
Exposed

Yes

Category 5 — Governance Errors

Purpose:

Governance authority violation.

Examples:

Shepherd outside scope
Invalid escalation
Restricted actor attempt
Created By

Governance Module

Exposed

Yes

Category 6 — Resource Errors

Purpose:

Requested resource unavailable.

Examples:

Post not found
Herd not found
Image not found
Created By

Repository/Application Layer

Exposed

Yes

Category 7 — Conflict Errors

Purpose:

Requested state transition invalid.

Examples:

Already following
Duplicate vote
Already member
Created By

Owning Domain

Exposed

Yes

Category 8 — Infrastructure Errors

Purpose:

Platform dependency unavailable.

Examples:

Mongo unavailable
Storage unavailable
Cache unavailable
Created By

Infrastructure Layer

Exposed

No

Translated before API response.

Category 9 — External Service Errors

Purpose:

Third-party integration failure.

Examples:

Cloudinary failure
Email provider failure
Created By

Infrastructure Layer

Exposed

No

Category 10 — Internal System Errors

Purpose:

Unexpected failure.

Examples:

Null state
Invariant violation
Unhandled exception
Created By

Any layer

Exposed

Never directly

#### Layer Responsibility Model
API Layer

Owns:

Request validation errors
Error response generation
Final translation boundary

Must NOT:

Create business errors
Create governance errors
Create ownership errors
Rule ER-API-01

Controllers may reject malformed requests.

Controllers may not reject valid business requests.

Application Layer

Owns:

Workflow-level error coordination
Error propagation
Boundary translation

May:

Translate lower-layer errors

Must NOT:

Create domain rules
Domain Layer

Owns:

Business rule errors
Ownership errors
Lifecycle errors
Conflict errors

This becomes the primary business error owner.

Repository Layer

Owns:

Resource retrieval failures
Persistence translation

May create:

ResourceNotFound
PersistenceFailure

Must NOT create:

Authorization errors
Governance errors
Business rule errors
Infrastructure Layer

Owns:

External system failures
Driver failures
Network failures

Must never expose raw implementation exceptions.

### Error Ownership Model
| Responsibility           | Owner                           |
| ------------------------ | ------------------------------- |
| Error Creation           | Layer where failure is detected |
| Error Classification     | Error Origin Layer              |
| Error Propagation        | All layers                      |
| Error Translation        | Boundary-crossing layer         |
| Error Logging            | Application + Infrastructure    |
| Error Audit              | Governance                      |
| HTTP Response Generation | API Layer                       |

### Error Boundary Rules
EBR-01 — Controllers Cannot Create Business Errors

Forbidden:

if (!membership)
   return CannotPostInHerd

Business errors belong to domain/application execution.

EBR-02 — Repositories Cannot Create Domain Errors

Forbidden:

Repository:
DuplicateVoteError

Repositories do not understand voting rules.

Only persistence.

EBR-03 — Repositories May Create Resource Errors

Allowed:

PostNotFound

because repository owns retrieval.

EBR-04 — Infrastructure Cannot Leak Implementation Exceptions

Forbidden:

MongoServerError
CloudinaryError
AxiosError

outside Infrastructure boundary.

Must translate.

EBR-05 — Domains Cannot Generate HTTP Errors

Forbidden:

404
403
409

Domains create business errors.

Not transport responses.

EBR-06 — Application Services Are The Primary Error Boundary

Application Services become the central location where:

Domain errors converge
Authorization errors converge
Governance errors converge
Infrastructure errors converge

before reaching API translation.

EBR-07 — Module Boundaries Preserve Error Ownership

Example:

Content Service
    ↓
Community Contract
    ↓
MembershipRequiredError

The error remains Community-owned.

Content must not reclassify it as a Content error.

### Error Propagation Principles
EPP-01 — Errors Propagate Toward Workflow Owners

Errors always move upward toward the current workflow owner.

For MVP:

Infrastructure
    ↑
Repository
    ↑
Domain
    ↑
Application Service
    ↑
Controller
    ↑
Error Middleware

The Application Service remains the primary error convergence point.

EPP-02 — Workflow Owners Decide Outcomes

The layer that owns the workflow determines:

Continue
Retry
Rollback
Abort

For most workflows:

Application Service

owns that decision.

EPP-03 — Error Translation Occurs Once

Errors should not be repeatedly translated.

Preferred:

Mongo Error
    ↓
Infrastructure Error
    ↑
Application Service
    ↑
API Translation

Avoid:

Mongo Error
 ↓
Infra Error
 ↓
Repository Error
 ↓
Application Error
 ↓
Controller Error
 ↓
HTTP Error

Excessive translation destroys error meaning.

EPP-04 — Failed Workflows Terminate Early

When a failure makes success impossible:

Execution stops immediately.

Example:

User Restricted

No reason to continue:

Authorization
Persistence
Feed updates

EPP-05 — Error Propagation Must Preserve Ownership

Errors retain ownership while propagating.

Example:

CommunityMembershipRequiredError

remains a Community error even when:

Community
  ↑
Content
  ↑
Controller

### Write Workflow Error Architecture
Write Workflow Error Architecture

Authoritative write flow:

Controller
    ↓
Application Service
    ↓
Authorization
    ↓
Ownership
    ↓
Governance
    ↓
Domain Rules
    ↓
Repository
    ↓
Infrastructure
Stage 1 — Controller Errors

Possible Errors:

ValidationError

Examples:

Missing title
Invalid page
Invalid body
Propagation

Stops immediately.

Transaction

Not started.

Response

Direct API error.

Stage 2 — Authorization Errors

Possible:

AuthorizationError

Examples:

Cannot assign shepherd
Cannot delete herd
Propagation

Authorization
↑
Application Service

Stops.

Transaction

Never starts.

Response

403

Stage 3 — Ownership Errors

Examples:

NotPostOwner
NotImageOwner
NotHerdOwner
Propagation

Ownership Validation
↑
Application Service

Stops.

Transaction

Never starts.

Response

403

Stage 4 — Governance Errors

Examples:

UserRestricted
CommunityRestricted
InvalidModerationScope
Propagation

Governance
↑
Application Service

Stops.

Transaction

Never starts.

Response

403

or

409

depending on approved API contract.

Stage 5 — Domain Errors

Examples:

MembershipRequired
DuplicateVote
AlreadyFollowing
Propagation

Domain
↑
Application Service

Stops workflow.

Transaction

May not yet exist.

If transaction exists:

Rollback.

Stage 6 — Repository Errors

Examples:

PostNotFound
MembershipNotFound
Propagation

Repository
↑
Application Service

Stops workflow.

Response

404

Stage 7 — Infrastructure Errors

Examples:

MongoUnavailable
StorageUnavailable
Propagation

Infrastructure
↑
Repository
↑
Application Service

Stops workflow.

Transaction

Rollback.

Response

500

Write Workflow Failure Sequence

Example:

Create Herd Post

Controller
 ↓
Application Service
 ↓
Authorization
 ✓
 ↓
Membership Validation
 ✗
 ↓
MembershipRequiredError
 ↑
Application Service
 ↑
Error Middleware
 ↓
403

Persistence never executes.

### Read Workflow Error Architecture
Read Workflow Error Architecture

Authoritative Read Flow

Controller
    ↓
Application Service
    ↓
Authorization
    ↓
Visibility Evaluation
    ↓
Query Service
    ↓
Repository

No transaction ownership.

No mutation.

Read Error Sources
Validation

Examples:

Invalid pagination
Invalid sorting

Stops immediately.

Authorization

Examples:

Private governance queue
Restricted moderation view

Stops immediately.

Visibility Errors

Examples:

Restricted profile
Restricted herd
Hidden content

Stops immediately.

Resource Errors

Examples:

PostNotFound
CommentNotFound

Stops immediately.

Infrastructure Errors

Examples:

Database unavailable
Read timeout

Stops immediately.

Return:

500

Read Workflow Failure Example

Get Herd

Controller
 ↓
Application Service
 ↓
Visibility Validation
 ✗
 ↓
RestrictedHerdError
 ↑
Application Service
 ↑
Controller
 ↓
403

No repository query beyond visibility evaluation.

### Governance Error Architecture
Governance Error Architecture

Governance workflows contain additional authority stages.

Authoritative Governance Flow:

Governance Application Service
    ↓
Authority Validation
    ↓
Hierarchy Validation
    ↓
Scope Validation
    ↓
Target Validation
    ↓
Moderation Rules
    ↓
Persistence
Authority Validation Failures

Examples:

NotShepherd
NotHerdOwner
NotPlatformAdmin

Propagation:

Authority Validation
    ↑
Governance Service

Stops immediately.

Hierarchy Validation Failures

Examples:

CannotModerateHigherAuthority
CannotOverrideAdmin

Stops immediately.

Scope Validation Failures

Examples:

OutsideHerdScope
WrongCommunity
InvalidTargetScope

Stops immediately.

Target Validation Failures

Examples:

ReportClosed
TargetRemoved
TargetNotFound

Stops immediately.

Enforcement Failures

Examples:

RestrictionAlreadyExists
MembershipAlreadyRemoved

Stops workflow.

Rollback transaction.

Governance Failure Example
Review Report
 ↓
Authority Validation
 ✓
 ↓
Scope Validation
 ✗
 ↓
OutsideHerdScopeError
 ↑
Governance Service
 ↑
Controller
 ↓
403

No moderation action created.

No audit mutation created.

### Feed Error Architecture
Feed Error Architecture

Feed is unique because it consumes multiple modules.

Feed owns:

No authoritative state
No transactions
No mutations

Feed performs:

Composition
Filtering
Aggregation
Visibility
Feed Error Sources
Identity Failures

Examples:

Profile unavailable
Identity lookup failure
Social Graph Failures

Examples:

Follow query failure
Content Failures

Examples:

Post retrieval failure
Community Failures

Examples:

Membership visibility failure
Governance Failures

Examples:

Visibility evaluation failure

#### Feed Failure Model
Rule FE-01 — Visibility Failure Is Fatal

If Feed cannot determine visibility:

Do Not Show Item

Visibility defaults to deny.

Security first.

Rule FE-02 — Missing Item Is Non-Fatal

Example:

Deleted Post

Remove item.

Continue composition.

Rule FE-03 — Composition Integrity Failure Is Fatal

Example:

Feed cannot determine actor identity.

Abort feed request.

Return error.

Rule FE-04 — Feed Never Returns Restricted Data

When uncertain:

Hide
Don't expose
Feed Failure Example
Feed Service
 ↓
Content Query
 ✓
 ↓
Governance Visibility
 ✗
 ↓
Visibility Unknown
 ↓
Exclude Item
 ↓
Continue Feed

No restricted content leaks.

### Error Propagation Architecture

Authoritative Flow:

Infrastructure
↑
Repository
↑
Domain
↑
Application Service
↑
Controller
↑
Error Middleware

Application Services are the primary error convergence boundary.

### Error Escalation Model
Escalation Level 1 — Expected Business Error

Examples:

Authorization
Ownership
Conflict
Resource

Behavior:

Stop Workflow
Return Contract Error

No alerts.

No operational escalation.

Escalation Level 2 — Governance Failure

Examples:

Authority Violation
Invalid Escalation
Scope Violation

Behavior:

Stop Workflow
Audit
Return Contract Error

Governance visibility required.

Escalation Level 3 — Infrastructure Failure

Examples:

Mongo Down
Storage Failure
Email Provider Failure

Behavior:

Rollback
Log
Operational Visibility
Return 500
Escalation Level 4 — Internal System Failure

Examples:

Unhandled Exception
Invariant Violation
Unexpected State

Behavior:

Rollback
Log
Correlate
Operational Alert Candidate
Return 500

#### Rollback Rules
RR-01

Validation failures:

No transaction
No rollback
RR-02

Authorization failures:

No transaction
No rollback
RR-03

Governance failures:

No transaction
No rollback
RR-04

Domain failures before persistence:

No rollback
RR-05

Failures after transaction start:

Rollback Required

Examples:

Repository failures
Infrastructure failures
Enforcement failures

### Error Translation Principles
ETP-01 — Internal Errors And API Errors Are Different Things

Internal errors exist to support:

Business execution
Debugging
Logging
Auditability
Operations

API errors exist to support:

Client behavior
API contracts
User feedback

They are not the same object.

Example

Internal:

MembershipRequiredError

External:

{
  "error": {
    "code": "MEMBERSHIP_REQUIRED",
    "message": "Membership is required."
  }
}

The internal implementation remains hidden.

ETP-02 — Translation Occurs At Architectural Boundaries

Translation occurs only when crossing:

Internal Architecture
        ↓
API Boundary

Errors remain internal until response generation.

ETP-03 — Translation Must Preserve Meaning

Translation may simplify.

Translation may sanitize.

Translation must not change business meaning.

Example:

Allowed:

ShepherdOutsideScopeError
        ↓
403 GOVERNANCE_SCOPE_VIOLATION

Forbidden:

ShepherdOutsideScopeError
        ↓
500 INTERNAL_ERROR

Meaning lost.

ETP-04 — Translation Must Never Leak Implementation

Clients should never learn:

Database structure
Collection names
Query logic
Cloudinary internals
Driver exceptions
Stack traces
ETP-05 — External Contracts Remain Stable

Internal implementation may evolve.

External contracts remain unchanged.

This supports future extraction readiness.

### Internal Error Model
Decision

Adopt a typed internal error hierarchy.

Authoritative model:

BaseError
│
├── ValidationError
├── AuthenticationError
├── AuthorizationError
├── OwnershipError
├── GovernanceError
├── ResourceError
├── ConflictError
├── InfrastructureError
├── ExternalServiceError
└── InternalSystemError

#### Base Error Architecture
BaseError

Every internal error inherits:

errorType
errorCode
message
module
workflow
severity
cause
metadata
Purpose

Provides:

Consistent propagation
Consistent logging
Consistent translation
Consistent observability

#### Domain Error Model
ValidationError

Examples:

InvalidPagination
InvalidSortField
InvalidRequestBody

Created By:

API Validation
AuthenticationError

Examples:

MissingAuthentication
ExpiredSession
InvalidToken

Created By:

Identity Module
Authentication Middleware
AuthorizationError

Examples:

InsufficientPermissions
RoleRequired
OperationForbidden

Created By:

Authorization Services
OwnershipError

Examples:

NotPostOwner
NotImageOwner
NotHerdOwner

Created By:

Owning Domain
GovernanceError

Examples:

ActorRestricted
ScopeViolation
HierarchyViolation
InvalidModerationAction

Created By:

Governance Module
ResourceError

Examples:

PostNotFound
HerdNotFound
ImageNotFound

Created By:

Repository/Application
ConflictError

Examples:

AlreadyFollowing
AlreadyMember
DuplicateVote

Created By:

Domain Layer
InfrastructureError

Examples:

DatabaseUnavailable
StorageUnavailable
CacheUnavailable

Created By:

Infrastructure
ExternalServiceError

Examples:

CloudinaryUnavailable
EmailProviderUnavailable

Created By:

Infrastructure
InternalSystemError

Examples:

UnexpectedState
InvariantViolation
UnhandledException

Created By:

Any layer.

### Error Translation Model
#### Layer Translation Responsibilities
API Layer

Owns:

Internal Error
        ↓
API Error Response

This is the final translation boundary.

API Layer Must Never

Create:

OwnershipError
GovernanceError
ConflictError

Those belong below.

Application Layer

Owns:

Boundary translation.

Examples:

MongoServerError
        ↓
InfrastructureError
CloudinaryError
        ↓
ExternalServiceError

Application Services normalize errors.

Domain Layer

May create:

Business Errors

Must not translate into HTTP concepts.

Forbidden:

403
404
409

inside Domain.

Repository Layer

May translate:

Mongo Not Found
        ↓
ResourceError

Must not expose driver exceptions.

Infrastructure Layer

Must translate:

MongoServerError
NetworkError
CloudinaryError

into platform-owned error types.

#### Translation Flow Architecture
Domain Error Example
Content Domain
        ↓
MembershipRequiredError
        ↑
Application Service
        ↑
Controller
        ↑
Error Middleware
        ↓
403

Error ownership preserved.

Repository Error Example
Mongo Query
        ↓
Document Missing
        ↓
PostNotFoundError
        ↑
Application Service
        ↑
API
        ↓
404
Infrastructure Error Example
Mongo Timeout
        ↓
DatabaseUnavailableError
        ↑
Application Service
        ↑
API
        ↓
500

Mongo never reaches clients.

### Error Translation Architecture

Internal errors are translated into API contract errors only at the API boundary.

Infrastructure details must never be exposed externally.

#### Module Boundary Translation Model
Decision

Modules expose contract errors.

Not raw errors.

Not implementation errors.

Authoritative Pattern
Content Module
        ↓
Community Contract
        ↓
MembershipRequiredError

Allowed.

Forbidden Pattern
Content Module
        ↓
Community Repository
        ↓
Mongo Exception

Forbidden.

Why

Capability contracts must remain stable.

Module consumers should never depend on:

Persistence
Drivers
Storage

This directly supports future extraction.

### HTTP Mapping Architecture
HTTP Mapping Architecture

This layer preserves the approved API Error Contract.

HTTP 400

Maps To:

ValidationError

Examples:

InvalidRequest
InvalidPagination
InvalidFilter
HTTP 401

Maps To:

AuthenticationError

Examples:

InvalidToken
MissingAuthentication
ExpiredSession
HTTP 403

Maps To:

AuthorizationError
OwnershipError
GovernanceError

Examples:

NotOwner
InsufficientPermission
RestrictedActor
HTTP 404

Maps To:

ResourceError

Examples:

PostNotFound
CommentNotFound
ProfileNotFound
HTTP 409

Maps To:

ConflictError

Examples:

DuplicateVote
AlreadyFollowing
AlreadyMember
HTTP 429

Maps To:

RateLimitExceeded

Infrastructure-adjacent but externally visible.

HTTP 500

Maps To:

InfrastructureError
ExternalServiceError
InternalSystemError

Examples:

DatabaseUnavailable
CloudinaryUnavailable
UnexpectedState

### Information Exposure Rules
IER-01 — No Infrastructure Details

Never expose:

MongoServerError
MongoTimeout
ConnectionPoolError
IER-02 — No Cloudinary Details

Never expose:

CloudinaryError
CloudinaryResponse
CloudinaryRequest
IER-03 — No Stack Traces

Never expose:

Stack traces
File paths
Line numbers
IER-04 — No Query Information

Never expose:

Aggregation pipeline
Collection names
Indexes
Queries
IER-05 — No Security Internals

Never expose:

Permission evaluation
Authorization logic
Governance logic

Only outcomes.

IER-06 — Governance Must Be Sanitized

Allowed:

Insufficient moderation authority.

Forbidden:

Actor failed shepherd hierarchy rule 4.
IER-07 — Unknown Failures Default To Generic Internal Error

Fallback:

{
  "error": {
    "code": "INTERNAL_ERROR",
    "message": "An unexpected error occurred."
  }
}

No additional information.

### Future Service Extraction Readiness

Current:

Module
    ↓
Module Contract
    ↓
Module

Future:

Service
    ↓
API Contract
    ↓
Service

Error model remains unchanged.

Because:

Errors are contract-based.
Errors are not persistence-based.
Errors are not framework-based.

This is fully compatible with ADR-001 future extraction goals.

### Error Visibility Principles
EVP-01 — Not All Errors Are Equal

The architecture distinguishes between:

Business Errors

Expected failures.

Examples:

AlreadyFollowing
MembershipRequired
NotPostOwner

These are part of normal system behavior.

Operational Errors

Unexpected failures.

Examples:

MongoUnavailable
CloudinaryUnavailable
UnhandledException

These indicate system problems.

Governance Errors

Authority-related failures.

Examples:

InvalidModerationScope
HierarchyViolation
UnauthorizedModerationAttempt

These may require auditing.

EVP-02 — Logging And Auditing Are Different Concerns

Logging answers:

What happened?

Auditing answers:

Who did what?
Why?
Against whom?

Logs are operational.

Audit records are governance artifacts.

Never combine them.

EVP-03 — Every Error Must Be Traceable

Every significant failure must be traceable through:

Request
    ↓
Controller
    ↓
Application Service
    ↓
Module
    ↓
Repository
    ↓
Infrastructure

No error should become anonymous.

EVP-04 — Security Overrides Visibility

Operational visibility must never expose:

Tokens
Passwords
Session secrets
Internal permissions
Infrastructure credentials

Security remains the highest priority.

### Error Logging Architecture
#### Logging Responsibility Model
| Error Type         | Log Required |
| ------------------ | ------------ |
| Validation         | No (default) |
| Authentication     | Yes          |
| Authorization      | Yes          |
| Ownership          | Optional     |
| Governance         | Yes          |
| Resource Not Found | Optional     |
| Conflict           | Optional     |
| Infrastructure     | Mandatory    |
| External Service   | Mandatory    |
| Internal System    | Mandatory    |

#### Logging Classification Model
Level 1 — Debug

Purpose:

Development diagnostics.

Examples:

Validation failures
Expected conflicts

Not required in production.

Level 2 — Info

Purpose:

Important workflow outcomes.

Examples:

Governance action denied
Authentication failure
Level 3 — Warning

Purpose:

Suspicious or unusual behavior.

Examples:

Repeated authorization failures
Repeated moderation failures
Level 4 — Error

Purpose:

Workflow failure.

Examples:

Database unavailable
Storage unavailable
Repository failure
Level 5 — Critical

Purpose:

System integrity risk.

Examples:

Unhandled exception
Invariant violation
Corrupted state detection

#### Structured Error Logging Architecture
Decision

Adopt structured logging.

Never rely on free-form strings.

Standard Error Log Structure

Every error log should contain:

timestamp
requestId
errorCode
errorType
severity
module
workflow
userId
resourceType
resourceId
message
Example
{
  "timestamp": "2026-06-24T12:00:00Z",
  "requestId": "req_123",
  "errorCode": "POST_NOT_FOUND",
  "errorType": "ResourceError",
  "severity": "warning",
  "module": "Content",
  "workflow": "EditPost",
  "userId": "user_456",
  "resourceType": "Post",
  "resourceId": "post_789"
}

#### Logging Ownership Model
API Layer

May log:

Request correlation
Response outcome

Must not own error logging.

Application Layer

Primary logging owner.

Responsible for:

Workflow failure logging
Cross-module failure logging
Governance workflow logging

Application Services become the primary logging boundary.

Domain Layer

May create error metadata.

Must not write logs directly.

This preserves separation of concerns.

Repository Layer

May log:

Persistence failures

Must not log business failures.

Infrastructure Layer

Owns:

Database failures
Network failures
Storage failures

Must emit structured operational logs.

### Governance Audit Error Model
Governance introduces special requirements.

Auditability is a first-class architecture driver.

Audit Principle

Not every governance error becomes an audit record.

Only authority-relevant failures.

Must Audit
Unauthorized Moderation Attempt

Example:

Member attempts moderation action

Reason:

Potential abuse attempt.

Governance Scope Violation

Example:

Shepherd moderates wrong herd

Reason:

Authority boundary violation.

Hierarchy Violation

Example:

Shepherd attempts override of Herd Owner

Reason:

Governance integrity concern.

Invalid Escalation Attempt

Example:

Escalate closed report

Reason:

Governance workflow violation.

Governance Override Failure

Example:

Invalid restoration
Invalid reversal

Reason:

Oversight visibility.

Not Required For Audit

Examples:

Report not found
Already restricted
Already restored

These are operational workflow outcomes.

Not authority violations.

Governance Audit Record Structure

Governance audit failures should contain:

auditId
timestamp
actorId
actorRole
workflow
action
targetType
targetId
failureCode
failureReason
requestId
Example
{
  "actorId": "user_123",
  "actorRole": "Shepherd",
  "action": "RestrictPost",
  "targetType": "Post",
  "targetId": "post_789",
  "failureCode": "SCOPE_VIOLATION",
  "requestId": "req_456"
}

### Governance Audit Architecture

Governance authority violations must generate audit records.

Audit records remain distinct from operational logs.

### Error Correlation Model
Problem

A single error may travel through:

Controller
 ↓
Application Service
 ↓
Repository
 ↓
Infrastructure

Without correlation:

4 separate logs
0 visibility
Decision

Adopt Request Correlation IDs.

Every request receives:

requestId

at the API boundary.

Correlation Flow
HTTP Request
    ↓
requestId generated
    ↓
Controller
    ↓
Application Service
    ↓
Repository
    ↓
Infrastructure

All logs include the same identifier.

Correlation Requirements
EC-01

Every error log contains:

requestId

Mandatory.

EC-02

Cross-module workflows preserve requestId.

Example:

Content
 ↓
Community
 ↓
Governance

Same requestId.

EC-03

Infrastructure logs preserve requestId.

Example:

Mongo timeout

must remain linked to originating request.

EC-04

Governance audit records include requestId.

Allows correlation between:

Audit Record
+
Operational Logs

#### Workflow Failure Traceability Model
Write Workflow
Request
 ↓
requestId
 ↓
Controller
 ↓
Application Service
 ↓
Authorization
 ↓
Governance
 ↓
Repository
 ↓
Infrastructure

Failure can be reconstructed.

Governance Workflow
Request
 ↓
Authority Validation
 ↓
Hierarchy Validation
 ↓
Scope Validation
 ↓
Enforcement

Every stage traceable.

Feed Workflow
Feed Request
 ↓
Identity Query
 ↓
Social Graph Query
 ↓
Content Query
 ↓
Governance Visibility
 ↓
Composition

Failures remain correlated.

### Operational Visibility Foundation
The MVP does not require:

Distributed tracing
OpenTelemetry
Metrics platform
Log aggregation infrastructure
Alerting infrastructure

These belong to future Observability Architecture.

MVP Requires
Structured Logs

Mandatory.

Request Correlation IDs

Mandatory.

Governance Audit Records

Mandatory.

Error Classification

Mandatory.

Consistent Error Metadata

Mandatory.

### Error Logging Rules
ELR-01
Business errors may be logged.
Operational errors must be logged.

ELR-02
Governance authority violations must be auditable.

ELR-03
Every operational error must contain requestId.

ELR-04
Audit records and logs remain separate systems.

ELR-05
Application Services remain the primary logging boundary.

ELR-06
Domain objects never write logs.

ELR-07
Infrastructure exceptions must be correlated.

ELR-08
No sensitive information may appear in logs.

### Error Evolution Principles
EES-01 — Error Contracts Must Outlive Implementations

Implementations change.

Error contracts should remain stable.

EES-02 — Errors Must Remain Domain-Oriented

EES-03 — Error Ownership Follows Domain Ownership

Future features may add:

New modules
New services
New infrastructure

Error ownership remains with the domain that owns the rule.

This preserves architectural consistency.

EES-04 — Translation Boundaries Must Remain Stable

Future systems may introduce:

Queues
Workers
Search
Cache
Third-party APIs

Translation architecture remains:

Internal Error
        ↓
Contract Error

unchanged.

### Error Evolution Architecture

- Error ownership remains module-scoped.
- Error contracts remain stable.
- Service extraction must not require error redesign.

#### Background Job Evolution
Potential Future Capabilities

Examples:

Email Delivery
Report Processing
Cleanup Tasks
Feed Rebuilding
Media Cleanup
New Error Sources

Examples:

JobExecutionFailure
JobTimeout
JobRetryExhausted
JobCancelled
Architectural Decision

Background jobs should use the same internal hierarchy.

Example:

InfrastructureError
        └── JobExecutionError

No parallel error system.

Error Ownership

Workflow owner remains:

Responsible Module

Example:

Media Cleanup Failure

belongs to:

Media Module

not a generic background-job module.

#### Notification System Evolution

Future:

Email Notifications
Push Notifications
In-App Notifications
New Error Sources

Examples:

DeliveryFailure
ProviderUnavailable
NotificationTimeout
Architectural Decision

Classify as:

ExternalServiceError

or

InfrastructureError

depending on source.

No new top-level category required.

#### Search Architecture Evolution

Future:

Search Index
Full Text Search
Search Projections
New Error Sources

Examples:

IndexUnavailable
SearchTimeout
ProjectionFailure
Architectural Decision

Classify as:

InfrastructureError

until Search becomes an independent module.

If Search becomes a module:

SearchError

may be introduced.

Not before.

Evolution Rule

Do not create categories for domains that do not yet exist.

#### Cache Evolution

Future:

Redis
Response Cache
Feed Cache
New Error Sources

Examples:

CacheUnavailable
CacheTimeout
CacheCorruption
Architectural Decision

Classify as:

InfrastructureError
Critical Rule

Cache failures must not become business failures.

Example:

Cache Failure
        ↓
Fallback To Source

when possible.

#### External Integration Evolution

Future:

OAuth
Email Provider
Analytics
Spam Detection
AI Services
New Error Sources

Examples:

ProviderUnavailable
ProviderRejectedRequest
RateLimitExceeded
InvalidProviderResponse
Architectural Decision

Remain under:

ExternalServiceError

No redesign required.

#### Media Pipeline Evolution

Current Media:

Upload
Attach
Delete

Future Media:

Compression
Resizing
Thumbnail Generation
Moderation Scanning
New Error Sources

Examples:

ImageProcessingFailure
CompressionFailure
ThumbnailFailure
ModerationScanFailure
Architectural Decision

Remain owned by:

Media Module

and classified as:

InfrastructureError

or

ExternalServiceError

depending on implementation.

#### Modular Monolith Evolution Validation

Current Architecture

Identity
Social Graph
Content
Community
Media
Governance
Feed

Each module owns:

Business rules
Errors
Error codes
Error semantics

This must remain authoritative.

#### Module Error Ownership Rule
EER-01

A module owns the errors produced by rules it owns.

Example:

Community
    ↓
MembershipRequiredError

Owned by Community forever.

EER-02

Consuming modules must never redefine foreign errors.

Example:

Forbidden:

Content
    ↓
Translate MembershipRequired
    ↓
ContentError

Ownership lost.

EER-03

Cross-module contracts expose contract errors.

Not implementation errors.

This remains compatible with service extraction.

### Service Extraction Readiness Assessment
The error architecture should require no redesign.

Current State
Content
    ↓
Community Contract
    ↓
MembershipRequiredError
Future State
Content Service
    ↓
HTTP/gRPC/API
    ↓
Community Service
    ↓
MembershipRequiredError

Error meaning remains unchanged.

Why This Works

Because errors are:

Contract-Based

rather than:

Implementation-Based

### Future Error Handling Guidance
#### Future Distributed System Compatibility
If modules become services:

Current:

DomainError

Future:

RemoteDomainError

Translation still produces:

MembershipRequired

externally.

Evolution Rule

Service boundaries may change.

Error semantics must not.

#### Future Observability Compatibility

A future Observability Architecture may introduce:

Metrics
Distributed Tracing
Alerting
Dashboards
OpenTelemetry

The current architecture already provides:

requestId
errorCode
module
workflow
severity

Therefore observability can be added incrementally.

No redesign required.

#### Future Error Category Governance
Decision

Top-level error categories should remain stable.

Current hierarchy:

ValidationError
AuthenticationError
AuthorizationError
OwnershipError
GovernanceError
ResourceError
ConflictError
InfrastructureError
ExternalServiceError
InternalSystemError
Rule FEG-01

New subtypes may be added freely.

Example:

InfrastructureError
    ├── DatabaseUnavailable
    ├── CacheUnavailable
    ├── SearchUnavailable

Allowed.

Rule FEG-02

New top-level categories require architectural justification.

This prevents taxonomy explosion.

#### Future Governance Compatibility

Governance is expected to grow significantly.

Potential additions:

Appeals
Moderator Reviews
Reputation Systems
Automated Moderation
Architectural Decision

All governance-related failures remain:

GovernanceError

subtypes.

Example:

AppealNotEligible
AutomatedReviewBlocked
ModeratorReviewConflict

No redesign required.

---

## Backend Validation Architecture
### Validation Principles
VAL-01 — Validation Is Explicit
Validation must never be implied.
Every validation category must be visible in execution flows.
Rationale:

Improves maintainability
Improves auditability
Improves developer understanding
Aligns with Explicit Authority Boundaries

VAL-02 — Validation Does Not Imply Authorization
Validation and authorization solve different problems.

VAL-03 — Validation Does Not Imply Ownership
Ownership validation is a specialized validation category.
Ownership and authorization remain independent concerns.

VAL-04 — Validation Is Layered
Validation occurs at multiple architectural layers.
No single layer owns all validation.
Each layer validates only what it owns.

VAL-05 — Validation Fails Early
The earliest responsible layer should reject invalid operations.
Benefits:

Reduced execution cost
Simpler debugging
Better security posture

VAL-06 — Business Validation Remains Domain-Owned
Business rules belong exclusively to the owning domain.
No shared business-rule engine.
No global validation framework.
Preserves module ownership boundaries.

VAL-07 — Ownership Boundaries Determine Validation Ownership
The owner of a resource owns its business validation.

VAL-08 — Governance Validation Is Independent
Governance validation is not authorization.
Governance validation is not ownership.
Governance validation is not domain validation.

VAL-09 — Validation Must Be Deterministic
Given identical inputs and identical system state:
Validation must produce identical outcomes.
No hidden side effects.
No validation-time mutations.
Validation remains read-only.

VAL-10 — Validation Never Mutates State
Validation evaluates state.
Validation never changes state.

### Validation Taxonomy
The preliminary five-category model defined during Application Layer Architecture is insufficient for full backend architecture.

Approved Validation Categories
| Validation Type             | Required | Independent Architecture |
| --------------------------- | -------- | ------------------------ |
| Input Validation            | Yes      | Yes                      |
| Authentication Validation   | Yes      | Yes                      |
| Authorization Validation    | Yes      | Yes                      |
| Ownership Validation        | Yes      | Yes                      |
| Governance Validation       | Yes      | Yes                      |
| Domain Validation           | Yes      | Yes                      |
| State Transition Validation | Yes      | Domain Subtype           |
| Cross-Module Validation     | Yes      | Yes                      |
| Persistence Validation      | Limited  | Repository Concern       |

Final Validation Taxonomy
Input Validation
Authentication Validation
Authorization Validation
Ownership Validation
Governance Validation
Domain Validation
 └─ State Transition Validation

Cross-Module Validation

Persistence Validation

### Validation Ownership Model
Validation ownership follows module ownership.

Authoritative Validation Responsibility Matrix
| Validation Type             | Primary Owner              | Execution Boundary                         |
| --------------------------- | -------------------------- | ------------------------------------------ |
| Input Validation            | API Layer                  | Controller / Validation Middleware         |
| Authentication Validation   | Identity                   | Authentication Middleware                  |
| Authorization Validation    | Authorization Architecture | Application Service                        |
| Ownership Validation        | Owning Domain              | Domain Rule invoked by Application Service |
| Governance Validation       | Governance Module          | Governance Contract                        |
| Domain Validation           | Owning Domain              | Domain Layer                               |
| State Transition Validation | Owning Domain              | Domain Layer                               |
| Cross-Module Validation     | Owning Module              | Module Contract                            |
| Persistence Validation      | Repository Layer           | Repository / Database                      |

### Validation Execution Architecture
VEP-01 — Validation Executes In Ownership Order
Validation should execute according to architectural ownership boundaries.

VEP-02 — Validation Executes Before Mutation
No mutation may occur before all required validation succeeds.

VEP-03 — Validation Ownership Follows Rule Ownership
The component owning a rule executes the rule.

VEP-04 — Validation Remains Read-Only
Validation may read state.
Validation may not mutate state.
Validation services are evaluators.
Not workflow executors.

VEP-05 — Expensive Validation Executes Last
Low-cost validation should reject requests before expensive validation runs.

#### Authoritative Validation Pipeline
The preliminary execution model established during Application Layer Architecture now becomes fully formalized.

Standard Write Validation Pipeline
This becomes the authoritative write execution model.
Request
    ↓
Authentication Validation
    ↓
Controller
    ↓
Input Validation
    ↓
Application Service
    ↓
Authorization Validation
    ↓
Ownership Validation
    ↓
Governance Validation
    ↓
Domain Validation
    ↓
State Transition Validation
    ↓
Transaction Start
    ↓
Persistence Validation
    ↓
Persistence
    ↓
Commit
    ↓
Response

Why This Order?
Authentication Before Everything
Need actor identity.
Without identity:
No authorization.
No ownership.
No governance evaluation.

#### Layer-Specific Validation Responsibilities
API Layer Validation
Allowed
API layer validates:
Request Shape
Nothing else.

Application Layer Validation
Application Services become validation coordinators.
Allowed
Application layer owns:
Validation Coordination not Validation Rules

Domain Layer Validation
The Domain Layer owns business validity.
Allowed
Domain validates:
Business Correctness

Repository Layer Validation
Important architectural decision.
Allowed
Repositories validate:
Persistence Integrity Only.

#### Read Validation Architecture
Reads differ fundamentally from writes.
No mutation.
No transactions.
No lifecycle transitions.

Authoritative Read Pipeline
Request
    ↓
Authentication (if required)
    ↓
Input Validation
    ↓
Application Service
    ↓
Authorization Validation
    ↓
Visibility Validation
    ↓
Cross-Module Validation
    ↓
Query Execution
    ↓
Result Composition
    ↓
Response

Why Ownership Usually Does Not Execute
Ownership-Based Reads
Ownership executes only when visibility depends on ownership.

#### Write Validation Architecture
Write operations require the complete validation stack.

Authoritative Write Pipeline
Authentication
↓
Input Validation
↓
Authorization Validation
↓
Ownership Validation
↓
Governance Validation
↓
Domain Validation
↓
State Transition Validation
↓
Persistence Validation
↓
Mutation

#### Governance Validation Architecture
Governance workflows require specialized validation.
Governance is an authority domain, not a resource domain.

Governance Validation Pipeline
Authentication
    ↓
Input Validation
    ↓
Authority Validation
    ↓
Hierarchy Validation
    ↓
Scope Validation
    ↓
Target Validation
    ↓
Governance Rule Validation
    ↓
State Transition Validation
    ↓
Enforcement Execution

Governance Validation Ownership Matrix
| Validation                       | Owner                      |
| -------------------------------- | -------------------------- |
| Authority Validation             | Authorization Architecture |
| Hierarchy Validation             | Governance                 |
| Scope Validation                 | Governance                 |
| Target Validation                | Owning Domain              |
| Enforcement Validation           | Governance                 |
| Governance State Validation      | Governance                 |
| Governance Transition Validation | Governance                 |

### Domain Validation Architecture
#### Domain Validation Principles
These principles become authoritative.

DVP-01 — Business Rules Are Domain-Owned
Every business rule belongs to exactly one domain.
No shared business rules.
No shared validation ownership.

DVP-02 — Domain Validation Protects Invariants
Domain validation exists to protect business invariants.

DVP-03 — Domain Validation Is Independent Of Transport
Domain validation must not know:
HTTP
Express
REST
JWT
MongoDB
Domain validation receives business state only.

DVP-04 — Domain Validation Is Independent Of Persistence
Domain validation must not depend on:
MongoDB
Collection Names
Indexes
Mongoose Models
Domain rules evaluate business state.
Not storage state.

DVP-05 — Domain Validation Never Mutates State
Validation evaluates.
Validation never modifies.

DVP-06 — Domain Validation Must Be Reusable
The same rule must execute consistently regardless of entry point.

DVP-07 — Validation Ownership Follows Aggregate Ownership
Aggregate owner owns aggregate validation.

Domain Rule Validation Architecture
This section defines how business rules are modeled.

#### Domain Rule Validation Architecture
This section defines how business rules are modeled.

Domain Rule Categories
Category 1 — Participation Rules
Owner:
Community

Category 2 — Uniqueness Rules
Owner:
Owning Domain

Category 3 — Lifecycle Rules
Owner:
Aggregate Owner

Category 4 — Capability Rules
Owner:
Community

Category 5 — Consistency Rules
Owner:
Aggregate Owner

Domain Rule Execution Model
Authoritative pattern:
Application Service
        ↓
Load Aggregate
        ↓
Domain Validation
        ↓
Continue Workflow

#### Domain Rule Violation Handling
Domain validation failures become typed domain errors.

Rule:
Domain validators never generate HTTP responses.
They generate domain failures.
Error translation remains centralized in Error Architecture.

### Ownership Validation Architecture
Ownership is important enough to receive dedicated architecture.
Ownership is not authorization.
Ownership is not governance.
Ownership is a domain concern.

#### Ownership Validation Principles
OVP-01 — Ownership Remains Domain-Owned
Resource owner validates ownership.

OVP-02 — Ownership Validation Uses Aggregate State
Ownership evaluation requires authoritative aggregate data.

OVP-03 — Ownership Is Explicit
Ownership must be evaluated explicitly.
Never inferred.
Never assumed.

OVP-04 — Ownership Does Not Grant Unlimited Authority
Ownership grants ownership authority.
Not governance authority.
Governance remains separate.

Ownership Evaluation Strategy
Authoritative flow:
Load Aggregate
        ↓
Evaluate Owner
        ↓
Match Actor
        ↓
Pass / Fail

Ownership Rule Model
Each domain owns ownership evaluators.

Ownership Violation Handling
Ownership failures become dedicated ownership errors.
Ownership violations are not generic authorization failures.
This preserves auditability and debugging quality.

### State Transition Validation Architecture
State transition validation protects lifecycle integrity.

STV-01 — Lifecycle Owner Owns Transition Rules
Only owner defines valid transitions.

STV-02 — Invalid Transitions Must Be Impossible
if lifecycle does not allow it.

STV-03 — Transitions Are Domain Rules
State transition validation is a specialized form of domain validation.
Not separate architecture.

State Transition Execution Pattern
Load Aggregate
        ↓
Current State
        ↓
Requested State
        ↓
Validate Transition
        ↓
Persist

State Transition Violation Handling
InvalidMembershipTransitionError
InvalidReportTransitionError
InvalidPostTransitionError
These remain domain-level failures.

### Aggregate Validation Architecture
Aggregate validation protects consistency inside aggregate boundaries.

#### Aggregate Validation Principles
AVP-01 — Aggregate Owner Protects Aggregate Integrity
Aggregate consistency belongs to aggregate owner.
Never external modules.

AVP-02 — Aggregate Validation Executes Before Mutation
Consistency must be verified before persistence.

AVP-03 — External Modules Cannot Validate Internal Consistency
Content cannot.
This preserves module boundaries.

#### Aggregate Validation Categories
Membership Consistency
Community owns.

Discussion Consistency
Content owns.

Governance Consistency
Governance owns.

Media Consistency
Media owns.

#### Aggregate Validation Execution
Load Aggregate
        ↓
Validate Aggregate Integrity
        ↓
Allow Mutation

### Cross-Module Validation Architecture
This is the most critical validation architecture for a Modular Monolith.

#### Cross-Module Validation Principles
CMV-01 — Validation Follows Capability Contracts
Cross-module validation occurs through capabilities.
Never through repositories.
Never through collections.
Consistent with approved Module Boundary Architecture.

CMV-02 — Consuming Module Never Reimplements Provider Rules

CMV-03 — Validation Authority Remains Local
Rule ownership never moves.
Provider validates.
Consumer consumes result.

CMV-04 — Cross-Module Validation Is Read-Only
Validation never grants mutation authority.

#### Capability Validation Model
Preferred capability style:
CanUserPostInHerd()
CanUserJoinHerd()
CanAssignShepherd()
IsUserRestricted()
CanAttachImage()

Avoid:
GetMembershipDocument()
GetRestrictionRecord()
GetImageDocument()
Capabilities preserve encapsulation.

#### Cross-Module Validation Flow
Create Herd Post
Content Application Service
        ↓
Community Contract
        ↓
CanUserPostInHerd()
        ↓
Governance Contract
        ↓
IsUserRestricted()
        ↓
Content Validation
        ↓
Persist Post

Upload Post Image
Content Application Service
        ↓
Media Contract
        ↓
CanAttachImage()
        ↓
Content Validation
        ↓
Persist Post

Restrict Post
Governance Application Service
        ↓
Content Contract
        ↓
Validate Target
        ↓
Governance Validation
        ↓
Enforcement

#### Cross-Module Boundary Preservation Rules
These become authoritative.
CMR-01
Validation never bypasses capability contracts.

CMR-02
Repositories never cross module boundaries.

CMR-03
Aggregate validation remains local.

CMR-04
Ownership validation remains local.

CMR-05
State transition validation remains local.

CMR-06
Cross-module validation returns decisions.
Not internal state.

CMR-07
Cross-module validation never transfers authority.

### Validation Error Architecture
#### Validation Failure Principles
VFP-01 — Every Validation Failure Is Intentional
Validation failures are expected business outcomes.
They are not system failures.

VFP-02 — Validation Failures Must Be Typed
Validation failures must have explicit types.

VFP-03 — Validation Failures Preserve Ownership
The owner of the validation rule owns the failure.

VFP-04 — Validation Failures Must Be Deterministic
Identical inputs and state must produce identical failures.

VFP-05 — Validation Failures Never Leak Infrastructure Details
Validation failures remain business-facing.
These are persistence concerns.
Not validation concerns.
Consistent with Error Boundary Architecture.

#### Validation Failure Classification Model
Each category now receives an official failure model.

Category 1 — Input Validation Failures

Owner:

API Layer
Characteristics:

Earliest failures
No business context required
No aggregate loading required

Category 2 — Authentication Validation Failures

Owner:

Identity
Characteristics:

Identity establishment failure
Workflow never begins

Category 3 — Authorization Validation Failures

Owner:

Authorization Architecture
Characteristics:

Actor known
Authority rejected

Category 4 — Ownership Validation Failures

Owner:

Owning Domain
Characteristics:

Actor known
Resource known
Ownership mismatch

Category 5 — Governance Validation Failures

Owner:

Governance
Characteristics:

Governance restriction detected
Governance hierarchy enforced

Category 6 — Domain Validation Failures

Owner:

Owning Domain
Characteristics:

Business rule violation
Aggregate invariant protection

Category 7 — State Transition Failures

Owner:

Lifecycle Owner
Characteristics:

Lifecycle violation
State machine protection

Category 8 — Persistence Validation Failures

Owner:

Repository Layer
Characteristics:

Persistence integrity protection
Final validation boundary

#### Validation-to-Error Integration Architecture
This section integrates Validation Architecture with Error Handling Architecture.

Adopt Hybrid Validation Result Strategy

Authoritative model:

Input Validation

Result-oriented.

Allows:

username invalid
email invalid
password invalid

to return together.

Business Validation

Exception-oriented.

Examples:

AlreadyMemberError
RestrictedUserError
OwnershipViolationError

These fail fast.

Validation Failure Flow

Authoritative pattern:

Validation
        ↓
Typed Validation Error
        ↓
Application Service
        ↓
Error Propagation
        ↓
Error Middleware
        ↓
API Error Contract
        ↓
Response

Consistent with approved Error Propagation Architecture.

### Validation Consistency Architecture
Consistency is the primary reason to define a dedicated Validation Architecture.
Without consistency:
Rules drift
Governance becomes unreliable
Ownership becomes inconsistent

VC-01 — One Rule, One Owner

A rule may exist in exactly one location.

Bad:

Controller
↓
Checks Membership

Community
↓
Checks Membership

Duplicate rule.

Forbidden.

VC-02 — One Rule, One Error

A rule should produce one canonical failure.

Example:

MembershipRequired

Always produces:

MembershipRequiredError

Never:

ForbiddenError
InvalidMembershipError
MembershipMissingError

Consistency improves debugging.

VC-03 — One Capability, One Validation Path

Example:

CanUserPostInHerd()

must execute the same validation regardless of caller.

Examples:

Post API
Future Admin Tool
Future Mobile API

All use the same capability.

VC-04 — Governance Validation Remains Centralized

Restrictions must never be duplicated.

Forbidden:

Content Checks Restrictions
Community Checks Restrictions
Media Checks Restrictions

Allowed:

Governance
↓
Restriction Evaluation

Single source of truth.

VC-05 — Ownership Validation Remains Local

Ownership validation remains with owning module.

Never centralized.

Reason:

Ownership is domain-specific.

VC-06 — Feed Validation Consumes Outcomes

Feed must not recreate validation.

Feed consumes:

Visibility Outcomes
Governance Outcomes

Feed does not reevaluate restrictions.

Consistent with Feed Architecture.


#### Validation Reuse Architecture

Reuse is necessary.

Duplication is dangerous.

However excessive centralization is equally dangerous.

#### Shared Validation Categories
Category A — Technical Validation Utilities

Allowed as shared utilities.

Examples:

Email Format
Username Format
Slug Format
URL Format
Pagination Format

These are not business rules.

Safe to centralize.

Category B — Contract Validators

Allowed.

Examples:

Request DTO Validation
Response Contract Validation
Query Validation

Owned by API layer.

Domain Validators

Must remain domain-owned.

Examples:

AlreadyMember
AlreadyVoted
CanAssignShepherd
MembershipRequired

Must never become shared utilities.

Capability Validators

Preferred reusable business validation pattern.

Examples:

CanUserJoinHerd()
CanUserPostInHerd()
CanAttachImage()
IsUserRestricted()

These become reusable capability contracts.

Consistent with Module Boundary Architecture.

Reuse Strategy Decision

Adopt:

Shared Technical Validators
+
Domain-Owned Business Validators
+
Capability-Based Reuse

Reject:

Global Business Validation Framework

Reason:

Violates ownership boundaries.

#### Validation Audit Strategy

Most validation failures do not require audit records.

Logging everything creates noise.

We need explicit rules.

Category A — No Audit Required

Examples:

Invalid Email
Missing Field
Invalid Pagination
Already Member
Already Voted

Reason:

Routine user mistakes.

Not governance relevant.

Category B — Structured Logging Required

Examples:

Repeated Ownership Violations
Unexpected Validation Patterns
Abnormal Validation Rates

Reason:

Operational visibility.

Supports Operability.

Category C — Governance Audit Required

Examples:

Governance Scope Violation
Governance Authority Violation
Governance Hierarchy Violation
Moderation Enforcement Rejection

Reason:

Governance actions must remain auditable.

Consistent with Governance Architecture and QD-06 Auditability.

#### Validation Audit Matrix
| Failure Type                   | Log      | Audit |
| ------------------------------ | -------- | ----- |
| Input Validation               | Optional | No    |
| Authentication                 | Yes      | No    |
| Authorization                  | Yes      | No    |
| Ownership                      | Yes      | No    |
| Domain Validation              | Optional | No    |
| Governance Validation          | Yes      | Yes   |
| Governance Hierarchy Violation | Yes      | Yes   |
| Governance Scope Violation     | Yes      | Yes   |
| Infrastructure Validation      | Yes      | No    |

#### Validation Consistency Rules
These become authoritative.

VCR-01
Validation ownership follows rule ownership.

VCR-02
Validation failures are typed.

VCR-03
One rule produces one canonical failure.

VCR-04
Governance validation remains centralized.

VCR-05
Ownership validation remains local.

VCR-06
Feed consumes validation outcomes.

VCR-07
Repositories never execute business validation.

VCR-08
Business validators remain domain-owned.

VCR-09
Capability contracts become the preferred reuse mechanism.

VCR-10
Validation must remain compatible with future service extraction.
Consistent with ADR-001 evolutionary goals.

### Validation Evolution Strategy
Validation architecture is a foundational architecture.
Unlike API contracts or feed algorithms, validation architecture touches nearly every workflow.
Therefore evolution must be controlled.

#### Validation Evolution Principles
VES-01 — Validation Ownership Must Remain Stable

The most important evolution rule.

Future features may introduce:

New domains
New workflows
New resources

But ownership principles must not change.

Rule:

Who Owns The Rule
↓
Owns The Validation
↓
Owns The Error

This remains permanent.

Reason:

Ownership stability is more valuable than validation reuse.

VES-02 — Validation Categories May Expand

Current taxonomy:

Input
Authentication
Authorization
Ownership
Governance
Domain
State Transition
Cross-Module
Persistence

Future categories may appear.

Examples:

Rate Limiting Validation
Anti-Spam Validation
Risk Validation
Fraud Validation

However:

New categories must not collapse existing ownership boundaries.

VES-03 — Validation Execution Order Remains Stable

Current authoritative order:

Authentication
↓
Input
↓
Authorization
↓
Ownership
↓
Governance
↓
Domain
↓
State Transition
↓
Persistence

Future categories may be inserted.

Example:

Authorization
↓
Risk Validation
↓
Ownership

But the existing order should remain stable whenever possible.

Reason:

Predictability improves maintainability.

VES-04 — Domain Validation Must Never Become Centralized

Future growth often introduces:

ValidationEngine
BusinessRuleEngine
RuleFramework

Decision:

Rejected.

Reason:

Violates:

Domain ownership
Module ownership
Independent evolvability

Consistent with Domain-Oriented Modular Monolith principles.

VES-05 — Capability Contracts Remain Validation Boundaries

Current architecture:

Module A
↓
Capability Contract
↓
Module B Validation

Future service extraction:

Service A
↓
API
↓
Service B Validation

Minimal redesign required.

This preserves ADR-001 future evolution goals.

Future Evolution Path
MVP

Current architecture:

Application Service
↓
Capability Contract
↓
Domain Validation
Future Growth

Possible additions:

Rate Limiting
Spam Detection
Trust Scoring
Abuse Detection

without redesigning:

Domain validation
Ownership validation
Governance validation
Service Extraction Future

If:

Community

becomes an independent service.

Validation architecture becomes:

Content
↓
Community API
↓
Community Validation

No rule ownership changes.

No validation redesign required.

This is an important architecture quality indicator.

---

## Backend Security Architecture
### Security Principles
SEC-01 — Secure by Default

Every architectural decision should default toward the safest behavior.

Examples:

Protected endpoints require authentication.
Deny unless explicitly permitted.
Sensitive fields excluded by default.
Private resources never exposed accidentally.

SEC-02 — Defense in Depth

Security should exist at multiple independent layers.

Example:

Request
      ↓
Transport Security
      ↓
Authentication
      ↓
Validation
      ↓
Authorization
      ↓
Governance
      ↓
Domain Rules
      ↓
Persistence

No single layer should be trusted to provide complete protection.

SEC-03 — Least Privilege

Every actor receives only the minimum authority required.

Applies to:

Users
Shepherds
Herd Owners
Platform Administrators
Internal modules

SEC-04 — Explicit Trust

Trust must never be inferred.

Every request must explicitly establish:

Identity
Authority
Ownership
Scope

before mutation occurs.

SEC-05 — Boundary Preservation

Security enforcement must respect approved ownership boundaries.

Security must never:

Transfer ownership
Collapse module boundaries
Introduce hidden authority

This aligns directly with ADR-001 and Module Boundary Architecture.

SEC-06 — Security Supports Architecture

Security enhances architecture.

It never redesigns:

domains
ownership
module responsibilities
governance hierarchy

Security integrates into architecture.

It does not replace architecture.

### Layered Security Architecture
Layered Backend Security Architecture.

Security responsibilities are distributed across existing architectural layers instead of introducing new architectural layers.

Security becomes an architectural concern rather than an isolated subsystem.

This aligns with:

Domain-Oriented Modular Monolith
Security by Default
Explicit Authority Boundaries
Ownership Preservation
Evolutionary Architecture
Solo developer maintainability

### Backend Trust Model
The backend adopts a Zero Implicit Trust model.

Every incoming request is considered untrusted until explicitly verified.

Authoritative trust progression:

Internet Client
        ↓
Untrusted Request
        ↓
Authentication
        ↓
Authenticated Identity
        ↓
Authorization
        ↓
Governance Validation
        ↓
Domain Validation
        ↓
Trusted Business Execution

Trust is earned progressively.

It is never assumed.

### Trust Boundaries
Boundary 1 — External Client → Backend

Everything arriving from clients is untrusted.

Includes:

Headers
Cookies
JWTs
JSON body
Query parameters
Uploaded files

Validation is mandatory.

Boundary 2 — API Layer → Application Layer

Controllers may trust only:

successfully validated request format
authenticated principal

Controllers must never trust:

ownership
permissions
governance eligibility
Boundary 3 — Application Layer → Domain Layer

Application Services must verify:

authorization
ownership
governance

before invoking domain behavior.

The Domain Layer assumes workflow prerequisites have already been enforced while still protecting business invariants.

Boundary 4 — Application → Repository

Repositories trust only valid application requests.

Repositories never perform:

authentication
authorization
governance

This preserves Repository responsibilities.

Boundary 5 — Backend → External Infrastructure

External systems remain partially trusted.

Examples:

Cloudinary
Email provider
MongoDB driver

Failures must be treated defensively.

No external response should be blindly trusted.

### Phase 1 Threat Model
The architecture targets realistic MVP threats rather than enterprise adversaries.

Identity Threats

Protect against:

credential stuffing
brute-force login attempts
stolen sessions
session fixation
token theft
account takeover
Authorization Threats

Protect against:

privilege escalation
insecure direct object references (IDOR)
ownership bypass
governance bypass
Input Threats

Protect against:

malformed requests
malicious payloads
oversized payloads
injection attacks through validated input
unsafe file uploads
Media Threats

Protect against:

malicious image uploads
unsupported file types
oversized uploads
unauthorized media access
Abuse Threats

Protect against:

automated account creation
spam
excessive API requests
feed scraping
abusive voting
resource exhaustion
Information Disclosure

Prevent exposure of:

passwords
password hashes
refresh tokens
internal IDs where unnecessary
moderation metadata
secrets
infrastructure details

#### Out of Scope (Phase 1)

The following are intentionally excluded to satisfy the MVP scope constraint:

Zero Trust enterprise networking
Hardware Security Modules (HSM)
Web Application Firewalls (WAF)
Intrusion Detection Systems
Behavioral anomaly detection
SIEM integration
Multi-region disaster recovery
End-to-end encryption
Multi-factor authentication (future enhancement)
Device fingerprinting
Adaptive authentication
OAuth/OpenID federation
Passwordless authentication

These remain future evolution paths consistent with Evolutionary Architecture.

### Security Responsibilities by Layer
| Layer                | Security Responsibility                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------- |
| API Layer            | Input validation, authentication entry, request normalization                                        |
| Application Layer    | Workflow security orchestration, authorization invocation, governance invocation, session validation |
| Domain Layer         | Business invariants, ownership invariants, lifecycle integrity                                       |
| Repository Layer     | No security decision ownership; persistence only                                                     |
| Infrastructure Layer | Secret access, encryption support, cookie signing, external integrations, TLS assumptions            |

This integrates cleanly with the previously approved Application Layer Architecture and Validation Architecture without changing their responsibilities.

### Domain Security Responsibilities
Security responsibilities follow existing domain ownership.
| Domain       | Security Responsibility                                         |
| ------------ | --------------------------------------------------------------- |
| Identity     | Identity establishment, credential ownership, session lifecycle |
| Social Graph | Protect follow relationship ownership                           |
| Content      | Protect content ownership and editing authority                 |
| Community    | Protect community membership and delegated authority            |
| Media        | Secure media lifecycle and ownership                            |
| Governance   | Enforce moderation authority and security overrides             |
| Feed         | Consume only already-authorized and visible content             |
Security ownership never crosses domain ownership boundaries.

### Security Ownership Model
Security responsibilities are intentionally decentralized.
| Responsibility          | Owner                       |
| ----------------------- | --------------------------- |
| Authentication          | Identity Module             |
| Authorization           | Authorization Service       |
| Governance Restrictions | Governance Module           |
| Ownership Rules         | Owning Domain               |
| Input Validation        | Validation Layer            |
| Business Validation     | Domain Layer                |
| Persistence Security    | Repository + Infrastructure |
| Secret Management       | Infrastructure              |
| Auditability            | Governance + Logging        |
This mirrors the existing ownership model rather than introducing a dedicated "Security Module."

### Security Assumptions
The architecture assumes:

HTTPS is enforced in production.
Express runs behind a trusted reverse proxy when deployed publicly.
Environment secrets are securely managed outside source control.
MongoDB authentication is enabled.
JWT signing keys remain confidential.
Users access the application through modern browsers supporting secure cookies.

### Authentication Principles
AUTHSEC-01 — Authentication Before Authorization

Every protected request must establish identity before any authorization evaluation.

Execution order:

Request
    ↓
Authentication
    ↓
Authenticated Principal
    ↓
Authorization
    ↓
Governance
    ↓
Business Execution
AUTHSEC-02 — Stateless Access Authentication

Application requests should authenticate using short-lived signed access tokens.

Backend business modules never store access-session state.

This preserves the stateless nature of the application layer.

AUTHSEC-03 — Stateful Refresh Control

Long-lived sessions require server-controlled refresh state.

Access remains stateless.

Refresh remains stateful.

This provides controlled session revocation without sacrificing API simplicity.

AUTHSEC-04 — Secure by Default

Authentication mechanisms should default to:

secure cookies
HttpOnly cookies
SameSite protection
short-lived access tokens
rotated refresh tokens

No insecure alternatives should exist.

AUTHSEC-05 — Explicit Session Ownership

Every authenticated session belongs to exactly one account.

Sessions are Identity-owned resources.

Other domains never own sessions.

Backend Identity Trust Flow
Authoritative authentication flow:

Browser
      ↓
Secure Cookie
      ↓
Authentication Middleware
      ↓
Identity Module
      ↓
Authenticated Principal
      ↓
Application Service
      ↓
Authorization
      ↓
Business Workflow

Identity establishment completes before any module interaction.

### Authentication Architecture
Hybrid JWT Authentication Architecture.

Characteristics:

Short-lived Access JWT
Long-lived Refresh Token
Refresh Token Rotation
Refresh Token persistence
Secure Cookies
Stateless API execution
Stateful session management

This balances:

Security
Simplicity
Maintainability
Evolutionary Architecture

without introducing enterprise complexity.

The Identity module becomes the exclusive owner of authentication.

Authentication responsibilities include:

Registration
Login
Session establishment
Session renewal
Logout
Email verification
Password reset
Session invalidation

No other module participates in authentication.

This preserves Identity as the root authority.

#### Authentication Execution Flow

Authoritative login workflow:

Login Request
      ↓
Input Validation
      ↓
Identity Application Service
      ↓
Credential Verification
      ↓
Account State Validation
      ↓
Generate Access Token
      ↓
Generate Refresh Token
      ↓
Persist Refresh Session
      ↓
Issue Secure Cookies
      ↓
Authenticated Response

Authentication completes before Authorization Architecture becomes active.

### JWT Strategy
Access Token

Purpose

Authenticate API requests.

Characteristics

Signed JWT
Short expiration
Stateless
Contains minimal claims
Never stored server-side

Recommended contents:

userId
sessionId
tokenVersion
issuedAt
expiration

Avoid embedding:

permissions
moderation state
profile data
follower counts
business state

These belong to authoritative domains and may change independently.

Access Token Lifetime

Recommended MVP duration:

10–15 minutes

Reasons:

Limits damage if stolen.
Low operational complexity.
Excellent browser UX with refresh tokens.

### Refresh Token Strategy
Refresh tokens represent authenticated sessions.

Unlike access tokens:

refresh tokens are persisted
refresh tokens are revocable
refresh tokens are rotated

Refresh workflow:

Expired Access Token
        ↓
Refresh Endpoint
        ↓
Validate Refresh Token
        ↓
Rotate Refresh Token
        ↓
Issue New Access Token
        ↓
Invalidate Previous Refresh Token

#### Refresh Token Storage

Refresh tokens should never be stored in plaintext.

Recommended:

Store:

token hash
session identifier
account identifier
expiration
device metadata (future optional)

This minimizes damage if the database is compromised.

### Cookie Strategy
Both tokens should be transmitted using cookies.

Recommended cookie attributes:
| Property                 | Access                                            | Refresh    |
| ------------------------ | ------------------------------------------------- | ---------- |
| HttpOnly                 | Yes                                               | Yes        |
| Secure                   | Production                                        | Production |
| SameSite                 | Strict (or Lax if cross-site requirements evolve) | Strict     |
| Accessible by JavaScript | No                                                | No         |

No tokens should be stored in:

localStorage
sessionStorage

This significantly reduces XSS exposure.

### Credential Security
Credentials exist only inside the Identity module.

Rules:

Passwords:

never logged
never cached
never returned
never persisted in plaintext

Credential verification occurs entirely inside Identity.

Other modules never access password information.

### Password Storage
Passwords must be:

one-way hashed
individually salted
computationally expensive to verify

Recommended algorithm:

Argon2id (preferred)
bcrypt (acceptable if Argon2 is unavailable)

The architecture specifies the required characteristics rather than binding to a single implementation.

### Password Reset Architecture
Password reset should be token-based.

Workflow:

Forgot Password
        ↓
Generate Reset Token
        ↓
Persist Hashed Token
        ↓
Email User
        ↓
Token Verification
        ↓
Reset Password
        ↓
Invalidate Existing Sessions
        ↓
Issue New Login

Important rule:

Changing password invalidates every active refresh session.

This limits damage from credential compromise.

### Email Verification Architecture
Email Verification Security

Verification architecture:

Registration
      ↓
Create Verification Token
      ↓
Persist Token Hash
      ↓
Send Email
      ↓
Verify Token
      ↓
Activate Account

Unverified accounts remain in:

Pending Verification

until verification succeeds.

This aligns with the approved account lifecycle defined in the feature specification.

### Session Lifecycle
Logout Architecture
Logout does not merely remove cookies.

Logout performs:

refresh session invalidation
cookie deletion
session termination

Authoritative flow:

Logout
      ↓
Authentication
      ↓
Invalidate Refresh Session
      ↓
Delete Cookies
      ↓
Success

Authoritative lifecycle:

Login
      ↓
Authenticated Session
      ↓
Access Token Renewal
      ↓
Refresh Rotation
      ↓
Logout
or
Expiration
or
Password Change
      ↓
Session Invalidated

Only Identity owns session lifecycle.

### Session Invalidation
Sessions become invalid when:

logout
password change
account suspension
account deletion
refresh expiration
administrator invalidation

Future additions may include:

device-specific logout
logout-all-devices

without redesign.

### Token Rotation
Refresh tokens must rotate on successful refresh.

Old refresh token:

→ invalid

New refresh token:

→ active

Benefits:

reduces replay window
enables theft detection
simplifies revocation

### Replay Protection
Replay attacks are mitigated through:

short-lived access tokens
refresh token rotation
server-side refresh validation
refresh invalidation after use
Secure + HttpOnly cookies

Future improvements:

device fingerprint validation
IP anomaly detection

remain outside MVP.

### CSRF Protection
Because authentication uses cookies, CSRF protection is required.

Recommended MVP approach:

SameSite cookies
CSRF token for state-changing requests
Origin / Referer validation where appropriate

This provides strong protection without unnecessary complexity.

### Authentication Middleware Placement
Authentication belongs immediately after transport concerns.

Authoritative request pipeline:

HTTP Request
      ↓
Security Headers
      ↓
Cookie Parsing
      ↓
Authentication Middleware
      ↓
Controller
      ↓
Validation
      ↓
Application Service
      ↓
Authorization
      ↓
Governance
      ↓
Business Logic

Authentication middleware responsibilities:

validate JWT
resolve principal
reject invalid tokens
attach authenticated identity

It must not:

authorize
check ownership
evaluate governance
perform business validation

### Authentication–Authorization Integration
Authentication output:

Authenticated Principal

Authorization input:

Actor
Action
Resource
Context

Relationship:

Authentication
        ↓
Produces Identity
        ↓
Authorization
        ↓
Produces Permission Decision

This preserves the separation established in the Authorization Architecture.

### Resource Protection Principles
The following principles become authoritative.

SEC-RP-01 — Protection Follows Ownership

Every resource inherits its primary security boundary from its owning module.

Examples:

Identity protects:

User Account
User Profile

Content protects:

Posts
Comments
Votes

Community protects:

Herds
Memberships

Media protects:

Images

Governance protects:

Reports
Moderation Actions

Security ownership never overrides architectural ownership.

SEC-RP-02 — Every Mutation Requires Security Evaluation

Every write operation follows the same protection pipeline.

Request
      ↓
Authentication
      ↓
Authorization
      ↓
Ownership Validation
      ↓
Governance Validation
      ↓
Domain Rules
      ↓
Persistence

Repositories never bypass this sequence.

SEC-RP-03 — Capability Contracts Are Security Boundaries

Module capability contracts are not merely communication mechanisms.

They are also security boundaries.

Every capability request must expose only the minimum information required.

Capabilities should return decisions rather than internal state whenever possible.

Preferred:

CanUserPostInHerd()

Avoid:

GetEntireMembershipDocument()

This preserves encapsulation and reduces accidental information exposure.

SEC-RP-04 — Sensitive Data Is Private by Default

Unless explicitly required by an approved API contract:

Sensitive information must never leave the owning module.

### Security Enforcement Boundaries
#### Workflow-Centric Resource Protection.

Security enforcement remains centered in:

Application Services
Authorization Service
Governance Service
Domain Rules

Repositories remain intentionally security-neutral.

This directly aligns with the approved Application Layer Architecture and Data Access Architecture.

--- 

Security exists at multiple architectural boundaries.

| Boundary       | Security Responsibility                  |
| -------------- | ---------------------------------------- |
| API            | Authentication entry                     |
| Application    | Authorization orchestration              |
| Module         | Capability protection                    |
| Domain         | Ownership and business invariants        |
| Repository     | Persistence only                         |
| Infrastructure | Secret protection and transport security |


No single boundary provides complete protection.

### Resource Access Security Pipeline
Every resource follows the same evaluation model.

Authenticated Principal
        ↓
Authorization
        ↓
Ownership Validation
        ↓
Governance Validation
        ↓
Visibility Evaluation
        ↓
Domain Rules
        ↓
Resource Access

This becomes the authoritative resource access pipeline.

### Ownership Protection Model
Ownership protection already exists architecturally.

Security architecture formalizes its enforcement.

Every mutable resource has:

one owner
one ownership rule
one modification authority
| Resource | Owner          |
| -------- | -------------- |
| Profile  | Profile Owner  |
| Post     | Post Author    |
| Comment  | Comment Author |
| Herd     | Herd Owner     |
| Image    | Image Owner    |
| Report   | Governance     |
No security mechanism may transfer ownership.

### Governance Protection Integration
Governance remains the only architectural authority capable of overriding ownership.

Security responsibilities:

validate governance authority
validate moderation scope
validate hierarchy
validate escalation

Governance never bypasses ownership.

Instead it executes approved governance workflows that instruct the owning module to perform the state transition.

This remains consistent with the Governance Architecture.

### Module-to-Module Security
Cross-module requests remain capability-based.

Security rules:

Modules may expose:

decisions
validation capabilities
resource existence
visibility status

Modules should avoid exposing:

internal persistence structures
database identifiers unnecessarily
implementation details

Authoritative interaction:

Content Module
      ↓
Community Contract
      ↓
Community Application Service
      ↓
Decision

Not:

Content
      ↓
Membership Collection

This preserves module isolation while reducing the attack surface.

### Capability Contract Security
Capability contracts become explicit security contracts.

Every capability should define:

required actor
required context
expected response
failure conditions

Capabilities should return:

Authorized
Denied
Exists
Not Found
Restricted

instead of raw persistence data whenever practical.

This minimizes unnecessary data disclosure.

### Database Security Principles
The database is considered an implementation detail.

Security architecture establishes the following rules.

DBSEC-01 — Database Never Authorizes

MongoDB never becomes the authorization engine.

Business authorization remains above persistence.

DBSEC-02 — Repositories Own Queries

Only repositories interact with MongoDB collections.

Controllers

❌ Never

Application Services

❌ Never

Domains

❌ Never

DBSEC-03 — Least Data Retrieval

Queries should retrieve only fields required by the workflow.

Avoid retrieving entire documents when only a subset is needed.

Benefits:

lower exposure
better performance
smaller attack surface
DBSEC-04 — No Cross-Module Collection Access

Repositories never query another module's collections directly.

Cross-module information is obtained through capability contracts.

This preserves the Data Access Architecture.

### Input Trust Boundaries
Every client input remains untrusted.

Includes:

request body
cookies
query parameters
uploaded files
path parameters
headers

Trust is established only after:

validation
authentication
authorization

No business layer should trust raw client input.

### Output Data Exposure Rules
Response contracts should follow:

Minimum Required Exposure

Sensitive fields should never appear unless explicitly required.

Examples:

Never expose:

password hash
refresh token
verification token
reset token
moderation notes
internal enforcement metadata
infrastructure identifiers
environment values
secret configuration

Derived values remain acceptable when already defined by approved API contracts.

### Sensitive Data Handling
Sensitive information includes:

Identity:

password hashes
email verification tokens
password reset tokens
refresh token hashes

Governance:

internal moderation reasoning
administrator-only notes

Infrastructure:

signing keys
environment variables
third-party credentials

Rules:

Sensitive data

never logged
never returned
never cached unnecessarily
never serialized into JWTs

### Secrets Management Principles
Secrets belong exclusively to infrastructure.

Examples:

JWT signing keys
database credentials
Cloudinary credentials
email provider credentials

Business modules must never hardcode secrets.

Application Services receive required capabilities through infrastructure configuration.

Future secret managers (e.g., Vault or cloud secret services) can replace environment variables without changing business modules.

### Media Access Security
Media protection follows Media Architecture.

Rules:

Image ownership:

Identity

Profile image

Content

Post image

Community

Herd image

Media validates:

upload ownership
attachment eligibility
visibility
deletion authority

Media never evaluates governance.

Governance provides restriction decisions.

Media applies them through approved workflows.

This preserves the Media Architecture.

### File Upload Security
Every upload follows the same security pipeline.

Upload Request
        ↓
Authentication
        ↓
Authorization
        ↓
Ownership Validation
        ↓
File Validation
        ↓
Media Validation
        ↓
Storage

File validation includes:

permitted MIME type
file size limits
supported formats
attachment eligibility

Future malware scanning may be added through background processing without redesign.

### API Protection Strategy
API security follows a layered model.

Every protected endpoint should receive:

HTTPS
Authentication
Validation
Authorization
Governance evaluation
Error standardization
Rate limiting

Public endpoints remain limited to:

registration
login
password reset initiation
email verification
selected public resource retrieval

Everything else is protected by default.

### Rate Limiting Strategy
Rate limiting should be capability-driven rather than globally uniform.

Recommended MVP categories:
| Endpoint Category  | Suggested Policy |
| ------------------ | ---------------- |
| Login              | Strict           |
| Registration       | Strict           |
| Password Reset     | Strict           |
| Email Verification | Moderate         |
| Feed Retrieval     | Moderate         |
| Search             | Moderate         |
| Content Creation   | Moderate         |
| Voting             | Moderate         |
| Public Read APIs   | Relaxed          |
This provides protection where abuse is most likely while avoiding unnecessary restrictions on normal usage.

Implementation details (algorithm, storage backend, distributed coordination) remain infrastructure concerns and should be defined later.

### Abuse Prevention Architecture
Abuse prevention should exist in multiple layers.

Identity

account verification
session controls

Application

rate limiting
workflow validation

Domain

duplicate vote prevention
duplicate membership prevention
ownership validation

Governance

reporting
moderation
enforcement

Infrastructure

request limits
upload constraints

No single mechanism should be expected to prevent all abuse.

### Resource Protection Principles

### Operational Security Principles
The following principles become authoritative.

OPS-SEC-01 — Operational Simplicity

Operational security should remain proportional to MVP scale.

Avoid:

SIEM platforms
Security orchestration platforms
Enterprise monitoring stacks
Distributed security infrastructure

Security operations should remain manageable by a solo developer.

OPS-SEC-02 — Observability Without Data Exposure

Logs should maximize operational usefulness while minimizing sensitive information.

Logs exist to explain system behavior.

Not to reproduce user data.

OPS-SEC-03 — Security Configuration Is Infrastructure

Security configuration belongs to Infrastructure.

Business modules must never:

read secrets directly
manage credentials
own security configuration

OPS-SEC-04 — Secure Evolution

Security enhancements should be additive.

New security capabilities should integrate with existing architecture instead of replacing it.

### Secure Logging Principles
#### Layered Operational Security Architecture.

Operational security becomes another architectural concern distributed across existing layers instead of introducing dedicated security infrastructure.

The architecture remains:

modular
observable
auditable
evolution-ready

while preserving simplicity.

---

Logs are operational assets.

Not business resources.

Logging should provide enough information to:

diagnose failures
investigate abuse
support governance
trace workflows

without exposing sensitive information.

#### Logging Classification
The following categories become authoritative.
| Category            | Purpose                               |
| ------------------- | ------------------------------------- |
| Application Logs    | Workflow execution                    |
| Error Logs          | Failures                              |
| Security Logs       | Authentication & authorization events |
| Governance Logs     | Moderation activities                 |
| Infrastructure Logs | External integrations                 |

Information That Must Never Be Logged

The following become prohibited:

Passwords

Password hashes

JWTs

Refresh tokens

Verification tokens

Password reset tokens

Session cookies

Secret keys

Environment variables

Cloud credentials

Database credentials

Personally sensitive request bodies unless explicitly required for debugging.

#### Structured Logging

Every log entry should contain standardized metadata.

Recommended fields:

timestamp
severity
requestId
actorId (if authenticated)
module
workflow
result
correlation identifier

This improves debugging without increasing architectural complexity.

### Audit Trail Requirements
Audit trails differ from logs.

Logs describe:

"What happened technically?"

Audit trails describe:

"What decision was made?"

#### Audit Ownership

Governance owns audit records for governance workflows.

Business modules own business history where required.

Infrastructure never owns business audit information.

#### Audit Events

The following should be auditable.

Authentication

login
logout
password reset
email verification

Governance

report review
enforcement
restoration
escalation

Identity

account restriction
profile restriction

Community

shepherd assignment
herd ownership changes

Security

refresh token invalidation
session termination

#### Audit Principles

Audit records should be:

immutable
chronological
attributable
queryable

Audit records should explain:

Actor

↓

Action

↓

Target

↓

Outcome

### Security Event Architecture
Security events represent meaningful security-relevant actions.

Examples

Authentication

Successful login

Failed login

Expired token

Refresh rotation

Authorization

Permission denied

Governance

Restriction applied

Restriction removed

Infrastructure

Secret configuration failure

External provider failure

Security events should be generated centrally through existing application workflows.

Dedicated event infrastructure is unnecessary for MVP.

### Incident Support Considerations
The architecture should support future incident investigation.

Every major workflow should be traceable through:

Request

↓

Request ID

↓

Application Service

↓

Module

↓

Result

↓

Audit Record

↓

Log Entry

This enables reconstruction of security incidents without requiring enterprise observability tooling.

### Security Configuration
Configuration remains an Infrastructure responsibility.

Configuration categories include:

Authentication

JWT signing keys
token lifetime
cookie configuration

Infrastructure

database URI
Cloudinary
email provider

Operational

log level
rate limits
upload limits

Application code should consume configuration.

It must never define configuration.

### Environment Separation
The architecture recognizes independent environments.

Development

Testing

Production

Each environment should maintain independent:

Secrets

Database

Storage

Email configuration

Security keys

Configuration must never be shared between production and non-production environments.

### Production Hardening Principles
The production deployment should enforce:

HTTPS

Secure cookies

Production secrets

Minimal environment exposure

Security headers

Restricted CORS

Disabled development diagnostics

Appropriate upload limits

Production hardening should remain infrastructure-driven rather than embedded in business modules.

### Dependency Security
Dependencies represent part of the platform's attack surface.

The architecture establishes the following principles.

DEP-SEC-01 — Trusted Dependencies

Use mature, actively maintained libraries.

Avoid abandoned packages.

DEP-SEC-02 — Minimal Dependencies

Prefer fewer dependencies.

Every dependency introduces:

security risk
maintenance burden
upgrade responsibility
DEP-SEC-03 — Regular Updates

Dependencies should be reviewed regularly.

Security updates receive priority over feature updates.

DEP-SEC-04 — Dependency Isolation

Third-party libraries remain infrastructure concerns.

Business rules should never depend on vendor-specific APIs unless encapsulated.

### Security Testing Strategy
Security verification becomes part of backend quality assurance.

#### Authentication Testing

Verify:

Registration

Login

Logout

Refresh

Password reset

Email verification

Session invalidation

#### Authorization Testing

Verify:

Ownership

Role hierarchy

Governance override

Scope restrictions

#### Input Validation Testing

Verify:

Invalid payloads

Oversized payloads

Malformed input

Boundary values

#### File Upload Testing

Verify:

Unsupported MIME types

Oversized files

Unauthorized uploads

Attachment restrictions

#### Governance Testing

Verify:

Hierarchy enforcement

Escalation

Restriction

Restoration

Audit creation

#### Abuse Prevention Testing

Verify:

Rate limiting

Duplicate actions

Replay prevention

Session invalidation

### Security Review Checklist
Every new backend feature should be reviewed against the following checklist.

#### Identity
Does the feature require authentication?
Does it create or modify sessions?

#### Authorization
Is authorization evaluated?
Is ownership evaluated?
Is governance evaluated?

#### Validation
Is all client input validated?
Are trust boundaries respected?

#### Data
Is sensitive data exposed?
Is least-data retrieval followed?
Are secrets isolated?

#### Operations
Is logging appropriate?
Is auditing required?
Are errors standardized?

#### Architecture
Does the feature preserve module boundaries?
Does it preserve ownership?
Does it preserve governance?
Does it preserve application-layer responsibilities?

This checklist becomes the standard architectural review process for future backend features.

### Security Evolution Strategy
Security should evolve alongside platform requirements.

Phase 1

Current architecture includes:

Authentication

Authorization

Governance integration

Rate limiting

Structured logging

Audit support

Secure configuration

Cookie security

Secrets management

Phase 2

Potential additions:

MFA

Device management

Advanced moderation protections

Media malware scanning

Expanded audit tooling

Background security jobs

Future

Possible future evolution:

OAuth

Passwordless authentication

Risk-based authentication

Secret managers

Hardware-backed keys

Security monitoring

Threat analytics

These enhancements extend the current architecture rather than replacing it.

### Backend Security Architecture Validation
he Backend Security Architecture is now validated against every approved backend architecture.

# Frontend Architecture Definition
## Frontend Architecture Style
### Frontend Architectural Goals
#### Observations
A purely UI-centric architecture is attractive for its simplicity but provides little guidance for long-term growth.
A rich client architecture duplicates responsibilities already owned by the backend, conflicting with the project's ownership and authority principles.
A traditional SPA architecture underutilizes the capabilities of Next.js App Router and React Server Components.
A domain-oriented frontend preserves conceptual alignment with the backend while still allowing the frontend to own presentation, navigation, interaction state, and user experience.

#### Domain-Oriented Frontend Architecture with a Backend-Authoritative Responsibility Model.
The frontend should be treated as an application layer dedicated to:

Presentation
User interaction
Navigation
Rendering
Client-side interaction state
API consumption
User experience orchestration

The backend remains authoritative for:

Business rules
Authorization
Authentication
Ownership
Governance
Lifecycle enforcement
Data integrity

#### Core Architectural Principles

The frontend should optimize for:

Presentation over business ownership – it renders and interacts with data but does not own business invariants.
Backend authority – server responses are the source of truth for security, permissions, and lifecycle.
Domain alignment – frontend concepts mirror approved backend domains to preserve a shared ubiquitous language.
Minimal client state – only interaction state, UI state, and transient state should be owned by the client.
Rendering as an architectural concern – rendering strategy should be chosen based on data characteristics, personalization, and performance, not by habit.
Evolutionary simplicity – introduce abstractions only when current requirements justify them, preserving a clear path for future expansion.

This recommendation aligns directly with the project's architectural principles of Simplicity First, Evolutionary Architecture, Domain-Driven Boundaries, API-First Thinking, Security by Default, and Operational Simplicity.

The frontend becomes responsible for:

Rendering UI
Managing navigation
Managing local interaction state
Consuming backend APIs
Coordinating user workflows
Presenting backend outcomes consistently

It intentionally avoids becoming a second business layer.

### Next.js App Router Philosophy
#### Observations
The Pages Router is stable but represents an older architectural model and does not align with the project's long-term direction.
A client-side SPA approach underutilizes Next.js and shifts unnecessary responsibility to the browser.
The App Router provides architectural capabilities—not merely routing features—that align with Chauthara's principles of simplicity, evolutionary architecture, and performance.

#### Next.js App Router as the authoritative frontend architectural foundation.

This decision is not based on popularity or framework trends.

It is based on architectural alignment with Chauthara's approved principles.

The App Router naturally supports:

Domain-oriented organization
Server-first rendering
Progressive enhancement
Layout persistence
Performance optimization
Evolutionary growth

without introducing additional architectural layers.

The App Router should therefore be viewed as the structural architecture of the frontend, not merely its navigation system.

#### Architectural Philosophy

The App Router should organize the frontend around application capabilities, not around technical implementation.

A route represents a user-accessible capability.

Examples include:

viewing a profile
reading a post
browsing a Herd
editing settings
creating content

Routes should never exist merely because an API exists.

Likewise, APIs should never exist merely because a route exists.

Both are independent expressions of the same business capability.

#### Layout Philosophy

Layouts are architectural composition boundaries, not reusable UI containers.

Their purpose is to define shared application structure for related capabilities.

Examples of architectural responsibilities include:

persistent navigation
authenticated application shell
shared page composition
shared context providers (when justified)
consistent visual structure

Layouts should not become:

business logic containers
data orchestration layers
global state managers
permission evaluators

Those concerns belong elsewhere in the architecture.

#### Nested Layout Philosophy

Nested layouts represent hierarchical capability composition.

Each additional layout should introduce a meaningful architectural boundary.

Examples include:

Platform Layout

↓

Authenticated Application Layout

↓

Settings Area

↓

Specific Settings Capability

Each level should exist because it represents a distinct structural concern—not merely to reduce duplicated JSX.

This reinforces maintainability by making shared responsibilities explicit.

#### Architectural Responsibilities of Layouts

Layouts may own:

persistent UI structure
navigation composition
consistent page framing
shared visual hierarchy
capability-specific shells
loading and error boundaries for their subtree

Layouts should avoid owning:

business workflows
API orchestration
domain state
authorization rules
lifecycle enforcement
resource ownership

These remain backend responsibilities or belong to lower-level frontend architectural layers.

#### Architectural Responsibilities of Pages

Pages represent entry points into business capabilities.

Their responsibility is to compose the experience for a specific route.

Pages should:

coordinate rendering
compose components
initiate data requirements
present capability-specific UI

Pages should avoid becoming:

service layers
reusable business abstractions
global state containers

A page is a composition boundary—not a business boundary.

#### Route Group Philosophy

Route groups exist to improve architectural organization, not user navigation.

They should separate:

public capabilities
authenticated capabilities
settings
administrative experiences
future governance interfaces

without affecting URL design.

This keeps URLs user-centric while allowing the internal architecture to evolve independently.

Route groups therefore support maintainability rather than functionality.

#### Routing and Domain Alignment

Although routes are user-facing rather than domain-facing, the routing architecture should remain conceptually aligned with approved business domains.

This does not mean every domain maps directly to a URL.

Instead, it means that related capabilities remain grouped around the same business concepts used throughout the platform.

For example:

Identity capabilities remain conceptually together.
Community capabilities remain conceptually together.
Feed capabilities remain conceptually together.

This shared ubiquitous language reduces cognitive overhead across frontend, backend, documentation, APIs, and future development.

#### Evolution Strategy

As the platform grows, the App Router should expand by introducing new capability areas rather than restructuring existing ones.

Future additions such as:

governance interfaces
moderation dashboards
notifications
analytics
messaging

should integrate as additional architectural capability areas, preserving the established routing philosophy.

The guiding principle is extension over reorganization, consistent with the project's Evolutionary Architecture principle.

---

The App Router becomes the structural framework for the frontend.

Future architectural work—including rendering, state management, navigation, and UI system design—should assume the App Router's layout hierarchy as the primary composition mechanism.

### Rendering Strategy
Analysis

Client-Side Rendering introduces unnecessary client responsibility.

Static Rendering alone cannot support a social platform whose primary data changes continuously.

Pure Server-Side Rendering treats every page as equally dynamic, increasing server work without corresponding benefit.

A Hybrid Rendering Architecture provides the greatest alignment with:

Simplicity First
Evolutionary Architecture
Performance
Maintainability

while fully utilizing the capabilities of the App Router.

#### Frontend Rendering Strategy
Rendering Architecture

The frontend shall adopt a Hybrid Rendering Architecture.

Rendering strategy shall be determined by the characteristics of the data being rendered rather than by framework defaults or developer preference.

Rendering becomes an architectural decision.

Not an implementation convenience.

#### Rendering Principles
The following become authoritative.

RND-01 — Server Rendering First

Server rendering becomes the default rendering strategy.

The frontend should prefer rendering on the server unless clear architectural reasons require client rendering.

Server rendering reduces:

Client JavaScript.
Hydration.
Duplicate requests.

while preserving backend authority.

RND-02 — Client Rendering By Exception

Client rendering should be introduced only when interaction requires browser execution.

Examples include:

User interaction.
Browser APIs.
Local interaction state.
Immediate UI feedback.

Client rendering shall not become the default simply because React components support it.

RND-03 — Static Rendering When Data Is Stable

Static rendering should be reserved for resources whose lifecycle does not require request-time personalization.

Static rendering should improve performance rather than define application architecture.

RND-04 — Rendering Does Not Determine Authority

Rendering location does not change authority.

Whether rendered:

on the server,
in the browser,
or statically,

the backend remains authoritative for:

Authentication.
Authorization.
Ownership.
Governance.
Business Rules.
Lifecycle Enforcement.

This preserves Security By Default.

RND-05 — Rendering Follows Data Characteristics

Rendering strategy should be selected according to:

Personalization.
Freshness requirements.
Visibility requirements.
Interaction requirements.

Rendering should never be selected solely because a feature belongs to a particular page.

#### Rendering Responsibility Model
Rendering responsibilities become explicitly separated.

Server Responsibilities

The server is responsible for:

Initial rendering.
Secure data retrieval.
Personalization.
Visibility-aware rendering.
Composition of server-rendered UI.
Client Responsibilities

The client is responsible for:

User interaction.
Local UI state.
Browser capabilities.
Immediate interface responsiveness.
Progressive enhancement.

The client is not responsible for:

Business validation.
Authorization.
Ownership evaluation.
Governance decisions.
Backend Responsibilities

The backend remains responsible for:

Data ownership.
Business rules.
Lifecycle management.
Authorization.
Governance.
Resource visibility.

Rendering consumes backend outcomes.

Rendering never produces them.

#### Rendering Decision Model
Rendering decisions shall follow the following evaluation order.

Is browser execution required?
        │
       Yes
        │
Client Rendering
        │
       No
        │
Is request-time personalization required?
        │
       Yes
        │
Server Rendering
        │
       No
        │
Is data sufficiently stable?
        │
       Yes
        │
Static Rendering
        │
       No
        │
Server Rendering

This becomes the authoritative rendering decision model.

#### Personalization Philosophy
Rendering strategy shall recognize two categories of application data.

##### Public Data

Public data may benefit from:

Static Rendering.
Cached Server Rendering.

depending on freshness requirements.

##### Personalized Data

Personalized data shall prefer Server Rendering.

Examples include:

Authenticated experiences.
User-specific visibility.
Personalized feeds.
User settings.

Personalization should not rely upon client-side reconstruction whenever server rendering can provide the initial experience.

##### Caching Philosophy

Caching supports rendering.

Caching does not determine rendering.

Rendering decisions should remain independent of caching implementation.

Caching strategy will be defined separately in the Performance Architecture.

This preserves separation of concerns.

#### Rendering Evolution Strategy
Future rendering capabilities may introduce:

Partial Prerendering.
Improved streaming.
Edge rendering where justified.
More granular cache control.

These enhancements should extend the Hybrid Rendering Architecture rather than replace it.

No future evolution should require changing the Rendering Principles established above.

---

Rendering becomes a first-class architectural concern.

Future architectural work shall assume:

Server Rendering as the preferred default.
Client Rendering by exception.
Static Rendering where appropriate.
Hybrid Rendering overall.

### Client Component vs Server Component Philosophy
Analysis
A Client Component First architecture duplicates responsibilities already addressed by the Rendering Strategy.
A Mixed approach creates inconsistent execution models and increases long-term maintenance costs.
A Server Component First architecture complements the approved Hybrid Rendering Architecture by making server execution the architectural default while allowing Client Components where browser execution is genuinely required.

#### Client Component vs Server Component Philosophy.
Component Architecture

The frontend shall adopt a Server Component First Architecture.

Server Components become the default component model.

Client Components become specialized execution units introduced only when browser execution is required.

#### Component Architecture Principles.
The following become authoritative.

CMP-01 — Server Components By Default

All components shall be assumed to be Server Components unless browser execution is required.

Client Components require explicit architectural justification.

This becomes the default component selection principle.

CMP-02 — Client Components By Capability

A Client Component shall exist only when one or more browser capabilities are required.

Examples include:

User interaction.
Browser APIs.
Local interaction state.
Client-side event handling.
Immediate visual feedback.

Client Components shall not exist solely because a component displays data.

CMP-03 — Server Components Own Data Composition

Server Components become the primary location for:

Data retrieval.
UI composition.
Rendering orchestration.
Passing prepared data to Client Components.

Server Components should prepare complete view models whenever practical.

CMP-04 — Client Components Own Interaction

Client Components own interface behavior.

Examples include:

Form interaction.
Menu behavior.
Dialog visibility.
Drag interactions.
Optimistic interface feedback.
Local component state.

They do not own business rules.

CMP-05 — Business Authority Remains External

Neither Server Components nor Client Components own:

Business validation.
Authorization.
Ownership.
Governance.
Lifecycle enforcement.

Both consume backend capability contracts.

This preserves the approved Backend Authority Model.

CMP-06 — Component Type Does Not Determine Business Responsibility

Server Components are not backend business logic.

Client Components are not frontend business logic.

Component type determines execution environment.

Business responsibility remains defined by the approved domain architecture.

#### Component Responsibility Model.
Server Components

Server Components own:

Initial UI composition.
Secure data retrieval.
Presentation assembly.
Rendering coordination.
Preparing data for interactive components.

Server Components should remain free of browser-specific behavior.

Client Components

Client Components own:

User interaction.
Browser execution.
Local component state.
Interface responsiveness.
Progressive enhancement.

Client Components should avoid performing initial application composition.

Shared Responsibilities

Both Server Components and Client Components participate in:

Consistent UI composition.
Presentation.
API contract consumption.
Domain-oriented frontend organization.

Neither component type owns application authority.

#### Data Ownership Model.
The following data ownership boundaries become authoritative.

Server Components

Server Components become the preferred owners of:

Initial application data.
Personalized data.
Request-time data.
Server-rendered content.

This aligns with the Rendering Responsibility Model.

Client Components

Client Components become the preferred owners of:

Temporary interaction state.
Local visual state.
Unsaved form state.
Immediate UI feedback.

Persistent application data should not migrate to the browser unnecessarily.

#### State Ownership Model.
The architecture distinguishes between application state and interaction state.

Application State

Application state remains derived from backend resources.

Examples include:

Profile information.
Herd information.
Feed data.
Posts.
Comments.
Memberships.

Application state should remain server-oriented.

Interaction State

Interaction state belongs to Client Components.

Examples include:

Modal visibility.
Dropdown state.
Form editing.
Selected tabs.
Input focus.
Animation state.

Interaction state should remain localized whenever practical.

This separation reduces unnecessary client-side state management.

#### Component Composition Model.
The following composition philosophy becomes authoritative.

Server Components compose the application.

Client Components enhance the application.

Composition should generally follow the pattern:

Server Component
        │
        ▼
Server Component
        │
        ▼
Client Component
        │
        ▼
Interactive UI

The preferred direction of composition is from server toward client.

This minimizes hydration while preserving interactive capabilities.

#### Component Communication Principles

The following become authoritative.

CMP-07 — Downward Composition

Server Components may compose Client Components.

This becomes the preferred composition model.

CMP-08 — Prepared Data Transfer

Client Components should receive prepared data rather than performing duplicate application queries whenever practical.

This reduces unnecessary client-side fetching.

CMP-09 — Localized Client Execution

Client execution should remain localized.

Interactive behavior should not unnecessarily propagate client execution throughout the component tree.

CMP-10 — Progressive Enhancement

Interactive capabilities should enhance the rendered application.

The application should not depend upon client execution for its primary rendering whenever server rendering satisfies the requirement.

#### Evolution Strategy

Future platform capabilities may increase the number of Client Components.

Examples include:

Rich editors.
Real-time collaboration.
Interactive moderation tools.
Advanced media editing.

These capabilities should extend the Server Component First Architecture.

The architecture should not evolve toward a Client Component First model.

---

Future frontend architecture shall assume:

Server Components as the default.
Client Components introduced only for browser execution.
Clear separation between application composition and interaction.

### Domain-Oriented Frontend Organization
Analysis

A Layer-Oriented organization is appropriate for smaller applications but becomes increasingly difficult to maintain as business capabilities expand.

A Feature-Oriented organization improves locality but may introduce unstable boundaries because features evolve with user experience rather than business capabilities.

A pure Domain-Oriented organization aligns closely with the approved backend architecture but benefits from limited technical organization within each domain.

A Hybrid Domain-Oriented organization combines stable business ownership with practical implementation flexibility while preserving the architectural principles established throughout the project.

#### Domain-Oriented Frontend Organization.
Frontend Organization Model

The frontend shall adopt a Domain-Oriented Organizational Model.

Business domains become the primary organizational boundary.

Technical organization exists only within the scope of a domain and shall never become the primary organizational principle.

This aligns the frontend with the approved Backend Domain-Oriented Modular Monolith while preserving frontend independence.

#### Organizational Principles.
The following become authoritative.

DOM-01 — Domains Represent Business Capabilities

A frontend domain represents a stable business capability rather than a technical implementation.

Domains shall reflect the same ubiquitous language established by the backend architecture.

DOM-02 — Domain Ownership Is Independent

Each frontend domain owns the UI capabilities that represent its business responsibility.

A domain should be understandable, maintainable, and evolvable without requiring knowledge of unrelated domains.

DOM-03 — Frontend Domains Mirror Business Boundaries

Frontend domains shall mirror the approved backend business domains.

This alignment is conceptual rather than structural.

The frontend is not required to replicate backend modules, directory structures, or implementation patterns.

Instead, both architectures share a common business language and ownership model.

DOM-04 — UI Ownership Follows Domain Ownership

UI capabilities belong to the domain responsible for the underlying business capability.

Ownership includes:

Screens.
Domain-specific components.
Interaction workflows.
Domain-specific presentation logic.
API consumption related to that capability.

Ownership does not include backend business rules.

DOM-05 — Shared Functionality Shall Remain Domain-Neutral

Only capabilities that are genuinely reusable across multiple domains should become shared frontend resources.

Examples include:

Design system components.
Generic UI primitives.
Utility functions.
Cross-cutting infrastructure.

Business-specific functionality shall not migrate into shared areas simply because it is used by multiple domains.

This preserves domain cohesion.

#### Domain Ownership Model.
The frontend shall recognize the same business domains established by the backend architecture.

Each domain owns its presentation and interaction responsibilities.

Illustrative examples include:
| Domain       | Primary Frontend Responsibility                                        |
| ------------ | ---------------------------------------------------------------------- |
| Identity     | Authentication flows, profile presentation, account settings           |
| Social Graph | Follow relationships and social interactions                           |
| Content      | Posts, comments, voting, content presentation                          |
| Community    | Herd discovery, membership, community interaction                      |
| Feed         | Feed presentation and navigation                                       |
| Media        | Media selection, upload workflows, media presentation                  |
| Governance   | User-facing reporting and governance interactions within Phase 1 scope |
These represent conceptual ownership boundaries rather than implementation requirements.

#### Cross-Domain Interaction Principles.
The following principles become authoritative.

DOM-06 — Domains Communicate Through Stable Interfaces

Domains shall interact through approved frontend interfaces and backend API contracts.

A domain should not depend upon another domain's internal implementation.

DOM-07 — Cross-Domain Dependencies Shall Be Directional

Cross-domain interaction should occur only where required by business workflows.

Dependencies should remain intentional, explicit, and limited.

Circular dependencies between domains should be avoided.

DOM-08 — Business Authority Remains Backend-Owned

Frontend domains own presentation and interaction.

Backend domains continue to own:

Business rules.
Authorization.
Governance.
Ownership.
Lifecycle enforcement.

Domain alignment shall not be interpreted as duplication of backend responsibilities.

#### Relationship with Backend Domains.
The frontend organization is aligned with the backend architecture but is not coupled to backend implementation.

Alignment means:

Shared terminology.
Shared business boundaries.
Shared capability ownership.
Stable API relationships.

Alignment does not mean:

Matching directory structures.
Mirroring backend module internals.
Creating one-to-one implementation dependencies.

The frontend and backend evolve independently while remaining synchronized through approved domain boundaries and API contracts.

#### Relationship with API Contracts.
API Contracts become the integration boundary between frontend domains and backend domains.

Each frontend domain consumes the APIs that correspond to its business capability.

Frontend domains shall not consume backend implementation details.

Changes within backend modules should not require frontend reorganization provided API contracts remain stable.

#### Evolution Strategy

Future platform capabilities shall extend the organizational model by:

expanding existing domains where appropriate, or
introducing new business domains when justified.

The organizational model shall not evolve by introducing additional technical layers as primary organizational boundaries.

This preserves long-term architectural consistency and minimizes large-scale refactoring.

---

Future module organization shall derive from the approved Domain-Oriented Organizational Model.
Technical organization decisions should reinforce domain ownership rather than replace it.

### Hybrid Domain-Based Organization
Analysis

A Layer-Based organization is well suited to small applications but gradually weakens domain cohesion by scattering related functionality across technical categories.

A Feature-Based organization improves locality but uses boundaries that are driven by product experience rather than business architecture. As features evolve, organizational boundaries may also change.

A Domain-Based organization aligns with the approved backend architecture and provides stable ownership, but benefits from lightweight technical organization within each domain.

A Hybrid Domain-Based organization preserves stable business boundaries while providing practical implementation organization. It complements the Domain-Oriented Frontend Organization established in the previous section without introducing competing organizational principles.

The frontend shall adopt a Hybrid Domain-Based Organization.

Business domains become the primary organizational boundary.

Technical organization exists only within the scope of an individual domain.

The application shall not be organized around global technical layers or transient product features.

#### Organizational Principles.
The following become authoritative.

ORG-01 — Domains Are the Primary Organizational Unit

Business domains become the highest-level organizational boundary.

Every implementation artifact shall belong to a domain unless it satisfies the requirements for a shared capability.

ORG-02 — Technical Layers Are Domain-Local

Technical implementation patterns may exist within a domain where they improve maintainability.

They shall not become application-wide organizational structures.

For example, organizing components or hooks within a domain is acceptable.

Organizing the entire application into global components, hooks, or services areas is not.

This preserves domain cohesion.

ORG-03 — Features Are Domain Capabilities

A feature is considered a capability of a domain rather than an independent organizational boundary.

Features belong to domains.

Domains do not belong to features.

This distinction ensures that product evolution does not destabilize the architectural organization.

ORG-04 — Shared Code Shall Be Intentionally Shared

Implementation shall become shared only when it is:

Domain-neutral.
Reusable across multiple domains.
Free of business-specific behavior.

Sharing implementation prematurely increases coupling and reduces domain autonomy.

ORG-05 — Business Logic Shall Not Become Shared Infrastructure

Presentation helpers and generic UI primitives may become shared.

Business-specific implementation shall remain within its owning domain even when reused by multiple capabilities.

Domain cohesion takes precedence over reducing duplication.

#### Organizational Responsibility Model.
The organizational strategy establishes three implementation categories.

##### Domain Implementation

Domain implementation contains:

Domain-specific UI.
Domain-specific interaction.
Domain-specific API integration.
Domain-specific presentation.
Domain-specific workflows.

Ownership remains entirely within the domain.

##### Shared Infrastructure

Shared infrastructure contains only implementation that is independent of any business domain.

Examples include:

Design system primitives.
Generic utilities.
Cross-cutting infrastructure.
Framework integration.
Application configuration.

Shared infrastructure shall not contain business capabilities.

##### Application Composition

Application composition integrates domain capabilities into a cohesive application.

Examples include:

Routing.
Layout composition.
Global providers.
Application shell.
Navigation composition.

Application composition coordinates domains without owning their business responsibilities.

#### Organizational Dependency Principles.
The following become authoritative.

ORG-06 — Dependencies Flow Toward Shared Infrastructure

Domains may depend upon shared infrastructure.

Shared infrastructure shall not depend upon domains.

This prevents circular architectural dependencies.

ORG-07 — Domain Independence

Domains should remain independently understandable and evolvable.

Changes within one domain should have minimal impact on unrelated domains.

ORG-08 — Cross-Domain Collaboration Through Stable Boundaries

When business workflows require collaboration between domains, interaction should occur through:

Approved frontend interfaces.
Stable API contracts.
Shared application composition.

Domains should not directly consume each other's internal implementation.

ORG-09 — Organization Reflects Business Architecture

The organizational model should communicate the business architecture of the platform.

A developer should understand the application's business capabilities before understanding its technical implementation.

This reinforces the shared ubiquitous language across frontend, backend, documentation, and API contracts.

#### Evolution Strategy

The organizational model shall evolve by:

introducing new domains,
extending existing domains,
refining domain-local implementation,

rather than reorganizing the application around new technical layers.

Future implementation patterns should reinforce domain ownership rather than replace it.

This preserves architectural continuity as the platform grows.

---

The forthcoming Frontend Module & Application Structure shall implement the Hybrid Domain-Based Organization defined in this section.
Directory structure, module boundaries, and implementation patterns shall derive from these organizational principles.

### Phase 1 Architectural Boundaries
Analysis

A Future-Oriented Architecture introduces abstractions that are not justified by the approved Phase 1 scope.

A Strict MVP Architecture minimizes complexity but may require unnecessary architectural restructuring as the platform evolves.

An Evolutionary Architecture provides the best balance by:

solving current requirements,
preserving architectural consistency,
documenting future evolution without implementing speculative infrastructure.

This approach remains fully aligned with the project's approved architectural principles.

##### Phase 1 Architectural Scope

The frontend architecture shall implement only the capabilities required to support the approved Core Platform MVP.

Architectural decisions shall optimize for current business capabilities while preserving natural extension points for future phases.

Deferred capabilities shall influence documentation through identified evolution paths only.

They shall not influence implementation architecture.

##### The following become authoritative.

BND-01 — Architecture Follows Approved Scope

Only approved Phase 1 capabilities shall influence architectural decisions.

Future roadmap items shall not introduce additional architectural abstractions until they become active project requirements.

BND-02 — Deferred Capabilities Shall Not Drive Design

The possibility of future functionality shall not justify introducing:

new abstraction layers,
additional state infrastructure,
routing complexity,
rendering strategies,
provider hierarchies,
communication mechanisms.

Architecture should remain proportional to current requirements.

BND-03 — Extension Over Anticipation

Future capabilities should extend the existing architecture.

They should not require the current architecture to anticipate them.

Extension points are preferred over speculative infrastructure.

BND-04 — Stable Architectural Foundations

Core architectural decisions established in previous sections remain authoritative regardless of future platform evolution.

Examples include:

Domain-Oriented Organization.
Hybrid Rendering Architecture.
Server Component First Architecture.
Hybrid Domain-Based Organization.

Future work should build upon these foundations rather than replace them.

#### Included Capabilities.
The following capabilities are considered within the architectural scope of Phase 1.

Identity
Authentication.
User profiles.
Account settings.
Session-aware navigation.

Social Graph
Following relationships.
Follower and following interactions.

Content
Personal posts.
Herd posts.
Comments.
Voting.
Content presentation.

Community
Herd discovery.
Herd membership.
Herd interaction.

Feed
Following feed.
Herd feed.
Feed presentation.

Media
Image upload workflows.
Image presentation.

Governance
Only user-facing governance workflows required by the approved MVP.

Examples include:

Reporting content.
Reporting users.
Reporting communities.

Administrative governance interfaces remain outside the Phase 1 scope.

#### Deferred Capabilities.
The following capabilities are intentionally excluded from Phase 1 architecture.

##### Advanced Governance Interfaces

Examples include:

Moderation dashboards.
Administrative review consoles.
Governance analytics.
Bulk moderation workflows.

##### Notifications

Including:

Push notifications.
In-app notification centers.
Notification preferences.
Background notification processing.

##### Real-Time Capabilities

Including:

Live feeds.
Presence indicators.
Typing indicators.
Live collaboration.
WebSocket infrastructure.

##### Offline Support

Including:

Offline synchronization.
Local persistence.
Conflict resolution.
Background synchronization.

##### Progressive Web Application Features

Including:

Service workers.
Offline installation.
Background caching.
Native application integration.

##### Analytics

Including:

User analytics.
Platform metrics.
Event tracking dashboards.
Behavioral analysis.

##### Internationalization

Including:

Multi-language routing.
Translation infrastructure.
Locale management.

##### Plugin Architecture

Including:

Third-party extensions.
Modular feature loading.
Runtime capability injection.

##### Micro-Frontend Architecture

The platform shall remain a single integrated frontend application.

Distributed frontend architectures are outside the scope of Phase 1.

##### Advanced Rendering Infrastructure

Examples include:

Partial Prerendering optimization.
Edge-specific rendering strategies.
Advanced cache orchestration.
Multi-region rendering optimization.

The approved Hybrid Rendering Architecture remains sufficient for Phase 1.

##### Architectural Rationale

These capabilities are deferred because they introduce additional architectural complexity without supporting approved MVP requirements.

Their implementation would increase:

architectural surface area,
testing effort,
operational complexity,
maintenance cost,

while providing no immediate value to the current implementation roadmap.

Documenting these capabilities as future evolution paths preserves flexibility without compromising the simplicity of the Phase 1 architecture.

#### Evolution Constraints.
Future architectural work shall extend Phase 1 through:

additional domains,
additional capabilities,
additional workflows,
additional rendering strategies where justified,

without replacing the foundational architectural decisions established throughout this document.


### Future Evolution Strategy
Analysis

Periodic architectural redesign increases implementation risk and weakens long-term architectural consistency.

A completely fixed architecture limits adaptability as platform requirements evolve.

An Evolutionary Architecture preserves stable architectural foundations while allowing controlled expansion through incremental change.

This approach directly aligns with the project's approved architectural philosophy.

Evolution Strategy

The frontend architecture shall evolve through incremental architectural extension.

Future capabilities shall extend existing architectural foundations.

They shall not replace them.

The architectural decisions established throughout this document become long-term architectural foundations.

#### Evolution Principles

The following become authoritative.

EVO-01 — Stable Foundations

The following architectural decisions shall remain stable unless formally superseded through the ADR process:

Frontend Architectural Goals.
App Router Philosophy.
Hybrid Rendering Architecture.
Server Component First Architecture.
Domain-Oriented Frontend Organization.
Hybrid Domain-Based Organization.

These decisions form the permanent architectural baseline.

EVO-02 — Domains Evolve Before Infrastructure

New business capabilities should first be evaluated as:

Extensions to existing domains, or
New business domains.

New cross-cutting infrastructure should be introduced only when multiple domains demonstrate a common requirement.

This prevents premature abstraction.

EVO-03 — Shared Infrastructure Evolves Conservatively

Shared infrastructure should expand only when:

Proven reusable.
Domain-neutral.
Required by multiple domains.

Business-specific implementation shall remain within its owning domain.

EVO-04 — Rendering Evolves Incrementally

The approved Hybrid Rendering Architecture remains authoritative.

Future rendering improvements may include:

Partial Prerendering.
Improved streaming.
Edge rendering.
More granular caching.

These enhancements refine rendering implementation rather than altering rendering philosophy.

EVO-05 — Component Architecture Remains Stable

The Server Component First Architecture remains authoritative.

Future interactive capabilities may increase the number of Client Components where justified.

However, Server Components remain the default execution model.

EVO-06 — Application Composition Remains Stable

Future platform capabilities shall integrate through the approved:

App Router hierarchy.
Domain organization.
Layout composition.
Rendering principles.

Application composition should grow by extension rather than restructuring.

EVO-07 — Backend Authority Is Permanent

Regardless of future frontend capabilities, backend ownership remains authoritative for:

Authentication.
Authorization.
Ownership.
Governance.
Business Rules.
Lifecycle Management.

Frontend evolution shall not introduce duplicate business authority.

#### Expected Evolution Paths

The architecture anticipates several categories of future growth.

These represent architectural extension paths rather than implementation commitments.

Richer Client Interaction

Future capabilities may include:

Rich text editing.
Advanced media editing.
Interactive moderation interfaces.
Enhanced user interaction.

These capabilities extend the Client Component Architecture without altering its underlying principles.

Real-Time Platform Features

Future capabilities may include:

Live feeds.
Presence indicators.
Notifications.
Real-time collaboration.

These features should integrate through existing domain boundaries rather than introducing parallel application architecture.

Additional Business Domains

Future platform growth may introduce new domains.

Examples include:

Messaging.
Notifications.
Analytics.
Search.
Recommendations.

Each new domain should integrate using the organizational principles established in this document.

Platform Scale

As the platform grows, future improvements may include:

More sophisticated caching.
Improved rendering optimization.
Infrastructure scaling.
Performance tuning.

These improvements should refine implementation without altering architectural direction.

#### Architectural Evolution Constraints

The following constraints become authoritative.

Architectural principles shall evolve more slowly than implementation.
Domain boundaries shall remain more stable than product features.
Rendering philosophy shall remain more stable than rendering implementation.
Organizational philosophy shall remain more stable than directory structure.
Business ownership shall remain more stable than application workflows.

These stability layers preserve long-term architectural consistency.

#### Architectural Decision Model

Future architectural decisions should follow the following evaluation order.

Does the new capability fit an existing business domain?
Can the capability reuse the existing architectural foundations?
Does it require additional shared infrastructure?
Is an ADR required?
Does the change alter an approved architectural principle?

Only if the final question is answered "Yes" should the existing architectural foundations be reconsidered.

This minimizes unnecessary architectural change.

---
 
Future implementation should extend:

existing domains,
existing routing hierarchy,
existing rendering strategy,
existing component philosophy,

rather than introducing competing architectural models.

---

##

