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

## 