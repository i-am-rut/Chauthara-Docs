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

##