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