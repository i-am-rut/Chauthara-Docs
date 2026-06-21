# Data Model

# MVP Domain Entity Inventory

## Identity Domain

### Core Entities
- User Account
- User Profile

---

## Social Graph Domain

### Core Entities
- Follow Relationship

---

## Content Domain

### Core Entities
- Post
- Comment
- Vote
- Image

---

## Community Domain

### Core Entities
- Herd
- Herd Membership

### Supporting Entities
- Shepherd Assignment

---

## Governance Domain

### Core Entities
- Report

### Supporting Entities
- Moderation Action

---

## Derived / Computed Concepts

- Following Feed
- Herd Feed
- Follower Count
- Following Count
- Membership Count
- Shepherd Count
- Vote Totals
- Aura

---

## Not Entities

- Visitor
- Member
- Herd Owner
- Shepherd
- Platform Administrator
- Personal Post
- Herd Post
- Reply

---

## Final MVP Entity Count

Core Entities: 10

Supporting Entities: 2

Total MVP Entities: 12

---

# MVP Entity Classification Model

## Entity Type Definitions

### Principal Entity
Primary business object with independent business identity.

### Relationship Entity
Represents participation, membership, assignment, or association between business objects.

### Content Entity
Represents user-created discussion and contribution content.

### Governance Entity
Represents reporting, moderation, enforcement, and governance processes.

### Media Entity
Represents reusable media assets used by other platform objects.

### Supporting Entity
Supports platform capabilities but is not a primary business object.

---

## MVP Entity Classification Matrix

| Entity | Classification |
|----------|----------|
| User Account | Principal Entity |
| User Profile | Principal Entity |
| Follow Relationship | Relationship Entity |
| Post | Content Entity |
| Comment | Content Entity |
| Vote | Supporting Entity |
| Image | Media Entity |
| Herd | Principal Entity |
| Herd Membership | Relationship Entity |
| Shepherd Assignment | Relationship Entity |
| Report | Governance Entity |
| Moderation Action | Governance Entity |

---

# MVP Ownership Boundary Model

| Entity              | Creator        | Steward        | Primary Owner  |
| ------------------- | -------------- | -------------- | -------------- |
| User Account        | User           | User           | User           |
| User Profile        | User           | User           | User           |
| Follow Relationship | Following User | Following User | Following User |
| Post                | Author         | Author         | Author         |
| Comment             | Author         | Author         | Author         |
| Vote                | Voting User    | Voting User    | Voting User    |
| Image               | Uploading User | Uploading User | Uploading User |
| Herd                | Creator        | Herd Owner     | Herd Owner     |
| Herd Membership     | Member         | Member         | Member         |
| Shepherd Assignment | Herd Owner     | Herd Owner     | Herd Owner     |
| Report              | Reporter       | Platform       | Platform       |
| Moderation Action   | Moderator      | Platform       | Platform       |


## Ownership Principles

- Ownership is a business responsibility concept.
- Ownership is distinct from moderation authority.
- Ownership is distinct from creation.
- Ownership is distinct from stewardship.
- Herd governance does not transfer ownership of member-created content.
- Platform moderation does not transfer ownership of user-created content.
- Governance entities are platform-owned because they exist to support platform safety, accountability, and enforcement.

---

# MVP Relationship Model

## Relationship Principles
### Principle 1 — Direct Relationships Only

A relationship should exist only when a direct business interaction exists.

Example:

User Account → Herd

No direct relationship.

Relationship exists through Herd Membership.

### Principle 2 — Avoid Redundant Relationships

Do not create both:

User Account ↔ Herd

and

User Account ↔ Herd Membership ↔ Herd

when Herd Membership already represents the business relationship.

### Principle 3 — Relationship Entities Carry Participation Meaning

Relationship entities exist to model participation.

Examples:

Follow Relationship
Herd Membership
Shepherd Assignment
### Principle 4 — Governance Relationships Remain Explicit

Reports and Moderation Actions are governance entities and must explicitly connect to governed entities.

### Principle 5 — Derived Concepts Do Not Create Relationships

Following Feed

Herd Feed

Aura

Vote Totals

Follower Counts

are derived concepts and do not participate in the relationship model.

## Entity Relationship Analysis

### User Account
| Related Entity      | Direction                          | Cardinality  |
| ------------------- | ---------------------------------- | ------------ |
| User Profile        | User Account → User Profile        | One-to-One   |
| Follow Relationship | User Account → Follow Relationship | One-to-Many  |
| Post                | User Account → Post                | One-to-Many  |
| Comment             | User Account → Comment             | One-to-Many  |
| Vote                | User Account → Vote                | One-to-Many  |
| Image               | User Account → Image               | One-to-Many  |
| Herd Membership     | User Account → Herd Membership     | One-to-Many  |
| Herd                | User Account → Herd                | One-to-Many  |
| Report              | User Account → Report              | One-to-Many  |
| Moderation Action   | Moderation Action → User Account   | Many-to-Many |

### User Profile
| Related Entity      | Direction                          | Cardinality                                                          |
| ------------------- | ---------------------------------- | -------------------------------------------------------------------- |
| User Account        | User Profile ↔ User Account        | One-to-One                                                           |
| Follow Relationship | User Profile ↔ Follow Relationship | Many-to-Many                                                         |
| Post                | User Profile → Post                | One-to-Many                                                          |
| Comment             | User Profile → Comment             | One-to-Many                                                          |
| Herd                | User Profile ↔ Herd                | Many-to-Many (through membership, ownership, or shepherd assignment) |
| Report              | Report → User Profile              | Many-to-Many                                                         |

### Follow Relationship
| Related Entity | Direction                          | Cardinality  |
| -------------- | ---------------------------------- | ------------ |
| User Account   | Follow Relationship ↔ User Account | Many-to-Many |
| User Profile   | Follow Relationship ↔ User Profile | Many-to-Many |

### Post 
| Related Entity    | Direction                | Cardinality  |
| ----------------- | ------------------------ | ------------ |
| User Account      | User Account → Post      | One-to-Many  |
| User Profile      | User Profile → Post      | One-to-Many  |
| Comment           | Post → Comment           | One-to-Many  |
| Vote              | Post ↔ Vote              | One-to-Many  |
| Image             | Post ↔ Image             | Many-to-Many |
| Herd              | Herd → Post              | One-to-Many  |
| Report            | Report → Post            | Many-to-Many |
| Moderation Action | Moderation Action ↔ Post | Many-to-Many |

### Comment
| Related Entity    | Direction                   | Cardinality  |
| ----------------- | --------------------------- | ------------ |
| User Account      | User Account → Comment      | One-to-Many  |
| User Profile      | User Profile → Comment      | One-to-Many  |
| Post              | Post → Comment              | One-to-Many  |
| Comment           | Comment → Comment           | One-to-Many  |
| Vote              | Comment ↔ Vote              | One-to-Many  |
| Report            | Report → Comment            | Many-to-Many |
| Moderation Action | Moderation Action ↔ Comment | Many-to-Many |

### Vote
| Related Entity    | Direction                | Cardinality  |
| ----------------- | ------------------------ | ------------ |
| User Account      | User Account → Vote      | One-to-Many  |
| Post              | Vote → Post              | Many-to-One  |
| Comment           | Vote → Comment           | Many-to-One  |
| Moderation Action | Moderation Action ↔ Vote | Many-to-Many |

### Image
| Related Entity    | Direction                 | Cardinality  |
| ----------------- | ------------------------- | ------------ |
| User Account      | User Account → Image      | One-to-Many  |
| Post              | Image ↔ Post              | Many-to-Many |
| User Profile      | User Profile ↔ Image      | One-to-Many  |
| Herd              | Herd ↔ Image              | One-to-Many  |
| Moderation Action | Moderation Action ↔ Image | Many-to-Many |

### Herd
| Related Entity      | Direction                  | Cardinality  |
| ------------------- | -------------------------- | ------------ |
| User Account        | User Account → Herd        | One-to-Many  |
| Herd Membership     | Herd → Herd Membership     | One-to-Many  |
| Shepherd Assignment | Herd → Shepherd Assignment | One-to-Many  |
| Post                | Herd → Post                | One-to-Many  |
| Image               | Herd ↔ Image               | One-to-Many  |
| Report              | Report → Herd              | Many-to-Many |
| Moderation Action   | Moderation Action ↔ Herd   | Many-to-Many |

### Herd Membership
| Related Entity    | Direction                           | Cardinality  |
| ----------------- | ----------------------------------- | ------------ |
| User Account      | Herd Membership ↔ User Account      | Many-to-One  |
| Herd              | Herd Membership ↔ Herd              | Many-to-One  |
| Moderation Action | Moderation Action ↔ Herd Membership | Many-to-Many |

### Shepherd Assignment
| Related Entity    | Direction                               | Cardinality  |
| ----------------- | --------------------------------------- | ------------ |
| User Account      | Shepherd Assignment ↔ User Account      | Many-to-One  |
| Herd              | Shepherd Assignment ↔ Herd              | Many-to-One  |
| Moderation Action | Moderation Action ↔ Shepherd Assignment | Many-to-Many |

### Report
| Related Entity    | Direction                  | Cardinality  |
| ----------------- | -------------------------- | ------------ |
| User Account      | User Account → Report      | One-to-Many  |
| User Profile      | Report → User Profile      | Many-to-One  |
| Post              | Report → Post              | Many-to-One  |
| Comment           | Report → Comment           | Many-to-One  |
| Herd              | Report → Herd              | Many-to-One  |
| Moderation Action | Report → Moderation Action | One-to-Many  |


### Moderation Action
| Related Entity      | Direction                               | Cardinality  |
| ------------------- | --------------------------------------- | ------------ |
| Report              | Report → Moderation Action              | One-to-Many  |
| User Account        | Moderation Action ↔ User Account        | Many-to-Many |
| Post                | Moderation Action ↔ Post                | Many-to-Many |
| Comment             | Moderation Action ↔ Comment             | Many-to-Many |
| Vote                | Moderation Action ↔ Vote                | Many-to-Many |
| Image               | Moderation Action ↔ Image               | Many-to-Many |
| Herd                | Moderation Action ↔ Herd                | Many-to-Many |
| Herd Membership     | Moderation Action ↔ Herd Membership     | Many-to-Many |
| Shepherd Assignment | Moderation Action ↔ Shepherd Assignment | Many-to-Many |


## Relationship Matrix
| Entity              | Direct Relationships                                                                                            |
| ------------------- | --------------------------------------------------------------------------------------------------------------- |
| User Account        | User Profile, Follow Relationship, Post, Comment, Vote, Image, Herd Membership, Herd, Report, Moderation Action |
| User Profile        | User Account, Follow Relationship, Post, Comment, Herd, Report                                                  |
| Follow Relationship | User Account, User Profile                                                                                      |
| Post                | User Account, User Profile, Comment, Vote, Image, Herd, Report, Moderation Action                               |
| Comment             | User Account, User Profile, Post, Comment, Vote, Report, Moderation Action                                      |
| Vote                | User Account, Post, Comment, Moderation Action                                                                  |
| Image               | User Account, User Profile, Post, Herd, Moderation Action                                                       |
| Herd                | User Account, Herd Membership, Shepherd Assignment, Post, Image, Report, Moderation Action                      |
| Herd Membership     | User Account, Herd, Moderation Action                                                                           |
| Shepherd Assignment | User Account, Herd, Moderation Action                                                                           |
| Report              | User Account, User Profile, Post, Comment, Herd, Moderation Action                                              |
| Moderation Action   | Report, User Account, Post, Comment, Vote, Image, Herd, Herd Membership, Shepherd Assignment                    |


## Relationship Validation
### Ownership Boundary Consistency

Validated against approved ownership model. No relationship transfers ownership.

### Governance Consistency

Validated against governance hierarchy:

Applicable Law
    ↓
Platform Administrators
    ↓
Herd Owners
    ↓
Shepherds

as defined in PROJECT_CONTEXT and moderation specifications.

### Redundancy Review

Removed:

Direct User Account ↔ Herd participation relationship
Direct User Account ↔ Shepherd authority relationship

Both are represented through relationship entities.

### Entity Coverage Review

All approved MVP entities evaluated:

User Account
User Profile
Follow Relationship
Post
Comment
Vote
Image
Herd
Herd Membership
Shepherd Assignment
Report
Moderation Action

---

# MVP Aggregate Boundary Model

## Aggregate Modeling Principles

### Principle 1 — Aggregate ≠ Relationship Group

Relationships may cross aggregate boundaries.

### Principle 2 — Aggregate Root Is The Control Point

Every aggregate has exactly one aggregate root.

### Principle 3 — User-Created Content Remains Independently Owned

Community participation does not transfer content ownership.

### Principle 4 — Governance Is Separate From Content

Reports and Moderation Actions govern entities but do not belong to their aggregates.

### Principle 5 — Membership Is Participation

Membership does not create community ownership.

### Principle 6 — Aggregate Boundaries Follow Business Authority

Aggregate roots align with primary lifecycle control.

## Aggregate Boundary Matrix
| Aggregate                  | Aggregate Root      | Member Entities            |
| -------------------------- | ------------------- | -------------------------- |
| User Identity Aggregate    | User Account        | User Account, User Profile |
| Follow Aggregate           | Follow Relationship | Follow Relationship        |
| Personal Content Aggregate | Post                | Post                       |
| Discussion Aggregate       | Comment             | Comment                    |
| Voting Aggregate           | Vote                | Vote                       |
| Media Aggregate            | Image               | Image                      |
| Community Aggregate        | Herd                | Herd, Shepherd Assignment  |
| Membership Aggregate       | Herd Membership     | Herd Membership            |
| Reporting Aggregate        | Report              | Report                     |
| Moderation Aggregate       | Moderation Action   | Moderation Action          |


## Aggregate Validation

All approved MVP entities belong to exactly one aggregate.

All aggregates have exactly one aggregate root.

Aggregate boundaries are consistent with:
- Ownership boundaries
- Relationship model
- Governance model

## Future consideration
Re-evaluate aggregate boundaries if future releases introduce:

Community ownership transfer
Community-scoped permissions beyond Shepherd assignment
Rich media asset management
Appeals and moderation case management
Multi-stage governance workflows

---

# MVP Lifecycle Boundary Model

## Lifecycle Modeling Principles
### Principle 1 — States Must Be Business Observable

A lifecycle state must represent something visible and meaningful from a business perspective.

Valid:

Active
Suspended
Submitted
Reviewed

Invalid:

Persisted
Cached
Synced
### Principle 2 — States Must Represent Lifecycle, Not Relationships

Relationship changes are not lifecycle states.

Example:

A Herd is not in a "HasMembers" state.

Membership count changes are relationship changes.

### Principle 3 — Moderation Is Not Automatically A Lifecycle

A moderation action may affect an entity's state.

It is not automatically a state itself.

Example:

"Reported" is not a Post lifecycle state because reports are separate governance entities.

### Principle 4 — States Should Be Stable

A state should persist long enough to be meaningful.

Avoid transient technical states.

### Principle 5 — Terminal States End Normal Participation

Terminal states represent completion of the business lifecycle.

Some terminal states may be recoverable.

Some may be permanent.

## Lifecycle Analysis Per Entity
### User Account
#### Creation Event

User completes account registration.

#### Candidate States
Pending Verification
Active
Suspended
Closed
#### State Transition Analysis

Pending Verification → Active

Email verification completed.

Active → Suspended

Platform enforcement.

Suspended → Active

Enforcement removed.

Active → Closed

User closes account.

Suspended → Closed

Account closed after suspension.

#### Terminal States
Closed
#### Restoration

No restoration assumed in MVP lifecycle model.

#### Lifecycle Rationale

Consistent with approved User Account lifecycle decisions in FEATURES.md and governance specifications.

### User Profile
#### Creation Event

User Account becomes active.

#### Candidate States
Active
Removed
#### State Transition Analysis

Active → Removed

Profile ceases to participate because associated account lifecycle ends.

#### Terminal States
Removed
#### Restoration

No restoration defined.

#### Lifecycle Rationale

Profile is an identity projection of an account.

### Follow Relationship
#### Creation Event

User follows another user.

#### Candidate States
Active
Ended
#### State Transition Analysis

Active → Ended

Follow relationship removed.

#### Terminal States
Ended
#### Restoration

New follow relationship required.

#### Lifecycle Rationale

Relationship exists only while follow intent exists.

### Post
#### Creation Event

User publishes a post.

#### Candidate States
Published
Removed
#### State Transition Analysis

Published → Removed

Author deletion or moderation removal.

#### Terminal States
Removed
#### Restoration

Possible through governance reversal.

#### Lifecycle Rationale

Post lifecycle intentionally remains simple.

Reporting is handled through Report entities, not Post states.

### Comment
#### Creation Event

User submits a comment or reply.

#### Candidate States
Published
Removed
#### State Transition Analysis

Published → Removed

Author deletion or moderation removal.

#### Terminal States
Removed
#### Restoration

Possible through governance reversal.

#### Lifecycle Rationale

Matches approved discussion model and moderation model.

### Vote
#### Creation Event

User submits HypeUp or HypeDown.

#### Candidate States
Active
Withdrawn
#### State Transition Analysis

Active → Withdrawn

User removes vote.

#### Terminal States
Withdrawn
#### Restoration

New vote action required.

#### Lifecycle Rationale

Vote exists only while user expresses evaluation.

### Image
#### Creation Event

User uploads image for supported usage.

#### Candidate States
Active
Removed
#### State Transition Analysis

Active → Removed

User removal or moderation removal.

#### Terminal States
Removed
#### Restoration

Possible through governance reversal.

#### Lifecycle Rationale

Images inherit business meaning from parent usage while remaining independent entities.

### Herd
#### Creation Event

Member creates Herd.

#### Candidate States
Active
Restricted
Closed
#### State Transition Analysis

Active → Restricted

Platform governance limits community participation.

Restricted → Active

Restrictions removed.

Active → Closed

Community permanently ceases operation.

Restricted → Closed

Community permanently closed.

#### Terminal States
Closed
#### Restoration

Not assumed.

#### Lifecycle Rationale

Community governance introduces lifecycle complexity beyond ordinary content.

### Herd Membership
#### Creation Event

Member joins Herd.

#### Candidate States
Active
Removed
Left
#### State Transition Analysis

Active → Left

Member voluntarily leaves.

Active → Removed

Community moderation removes member.

#### Terminal States
Left
Removed
#### Restoration

New membership required.

#### Lifecycle Rationale

Membership participation and moderation outcomes must remain distinguishable.

### Shepherd Assignment
#### Creation Event

Herd Owner appoints Shepherd.

#### Candidate States
Active
Revoked
#### State Transition Analysis

Active → Revoked

Authority removed.

#### Terminal States
Revoked
#### Restoration

New assignment required.

#### Lifecycle Rationale

Authority delegation is temporary and community-controlled.

### Report
#### Creation Event

User submits report.

#### Candidate States
Submitted
Under Review
Resolved
Dismissed
Escalated
#### State Transition Analysis

Submitted → Under Review

Review begins.

Under Review → Resolved

Violation confirmed.

Under Review → Dismissed

No violation found.

Under Review → Escalated

Higher authority required.

Escalated → Under Review

Receiving authority begins review.

Escalated → Resolved

Final determination reached.

Escalated → Dismissed

Final determination reached.

#### Terminal States
Resolved
Dismissed
#### Restoration

Not applicable.

#### Lifecycle Rationale

Matches approved governance hierarchy:

Report → Shepherd → Herd Owner → Platform Administrator.

### Moderation Action
#### Creation Event

Moderator determines enforcement is required.

#### Candidate States
Proposed
Applied
Reversed
#### State Transition Analysis

Proposed → Applied

Enforcement executed.

Applied → Reversed

Governance review overturns action.

#### Terminal States
Applied
Reversed
#### Restoration

Not applicable.

#### Lifecycle Rationale

Represents governance decisions rather than content participation.

## Lifecycle State Definitions
| State                | Definition                           |
| -------------------- | ------------------------------------ |
| Pending Verification | Awaiting activation requirements     |
| Active               | Participating normally               |
| Published            | Visible contribution exists          |
| Submitted            | Governance request created           |
| Under Review         | Governance evaluation occurring      |
| Escalated            | Sent to higher authority             |
| Resolved             | Governance action completed          |
| Dismissed            | No action required                   |
| Suspended            | Participation temporarily restricted |
| Restricted           | Community operation limited          |
| Removed              | Participation or visibility ended    |
| Left                 | Voluntary membership termination     |
| Revoked              | Delegated authority removed          |
| Closed               | Lifecycle permanently ended          |
| Withdrawn            | User evaluation removed              |
| Applied              | Enforcement active                   |
| Reversed             | Enforcement overturned               |


## Lifecycle Transition Matrix
| Entity              | First State          | Normal Active State | Exceptional States | Terminal States     |
| ------------------- | -------------------- | ------------------- | ------------------ | ------------------- |
| User Account        | Pending Verification | Active              | Suspended          | Closed              |
| User Profile        | Active               | Active              | None               | Removed             |
| Follow Relationship | Active               | Active              | None               | Ended               |
| Post                | Published            | Published           | None               | Removed             |
| Comment             | Published            | Published           | None               | Removed             |
| Vote                | Active               | Active              | None               | Withdrawn           |
| Image               | Active               | Active              | None               | Removed             |
| Herd                | Active               | Active              | Restricted         | Closed              |
| Herd Membership     | Active               | Active              | Removed            | Left, Removed       |
| Shepherd Assignment | Active               | Active              | None               | Revoked             |
| Report              | Submitted            | Under Review        | Escalated          | Resolved, Dismissed |
| Moderation Action   | Proposed             | Applied             | Reversed           | Applied, Reversed   |


## Lifecycle Validation
### Entity Coverage

All approved MVP entities have lifecycle definitions.

User Account
User Profile
Follow Relationship
Post
Comment
Vote
Image
Herd
Herd Membership
Shepherd Assignment
Report
Moderation Action

### Aggregate Consistency

Lifecycle ownership aligns with approved aggregate roots and aggregate boundaries.

### Governance Consistency

Lifecycle states align with:

Reporting System
Shepherd Moderation
Platform Moderation
Governance escalation hierarchy

defined in approved MVP specifications.

### Relationship Consistency

No lifecycle state duplicates:

Ownership changes
Relationship changes
Governance relationships

Lifecycle concerns remain independent from relationship modeling.

## Future Considerations
Future releases may require lifecycle expansion for:

Appeals
Multi-stage moderation review
Community ownership transfer
Temporary community restrictions
Advanced governance workflows

---

# MVP Data Stewardship Model

## Data Stewardship Categories

### User-Owned Data

Data primarily created, controlled, and maintained by users to express identity, relationships, participation, or content.

### System-Owned Data

Data primarily maintained by the platform to support governance, safety, accountability, enforcement, and platform operation.

### Mixed Responsibility Data

Data that originates from user activity but serves ongoing community governance or platform stewardship responsibilities.

## Data Stewardship Matrix
| Entity              | Stewardship Classification |
| ------------------- | -------------------------- |
| User Account        | User-Owned                 |
| User Profile        | User-Owned                 |
| Follow Relationship | User-Owned                 |
| Post                | User-Owned                 |
| Comment             | User-Owned                 |
| Vote                | User-Owned                 |
| Image               | User-Owned                 |
| Herd                | Mixed Responsibility       |
| Herd Membership     | User-Owned                 |
| Shepherd Assignment | Mixed Responsibility       |
| Report              | System-Owned               |
| Moderation Action   | System-Owned               |


## Stewardship Principles

- Data stewardship is distinct from ownership.
- Data stewardship is distinct from moderation authority.
- User-created content remains User-Owned even when moderated.
- Governance records remain System-Owned regardless of who submitted them.
- Community governance entities may require Mixed Responsibility classification.
- Stewardship classifications support future privacy, moderation, retention, and deletion discussions.

---

# MVP Moderation Boundary Model

## Governance Principles
### Principle 1 — Ownership Does Not Create Moderation Authority

Ownership answers:

"Whose entity is this?"

Moderation answers:

"Who may govern this entity?"

These are independent concepts.

Example:

A Member owns a Post.
A Shepherd may moderate that Post inside a Herd.
A Platform Administrator may override the moderation outcome.

Ownership remains unchanged.

Consistent with approved ownership model.

### Principle 2 — Governance Is Layered

Moderation authority exists at multiple levels:

Community Governance

Herd Owner
Shepherd

Platform Governance

Platform Administrator

Legal Governance

Law

Higher authority may override lower authority.

Lower authority may not override higher authority.

### Principle 3 — Community Authority Is Herd-Scoped

Herd Owners and Shepherds govern:

Herd participation
Herd discussions
Herd membership
Herd community identity

They do not perform platform-wide enforcement.

Consistent with approved moderation specifications.

### Principle 4 — Platform Authority Is Universal

Platform Administrators may intervene in any governed MVP entity.

Platform authority is never delegated below the platform layer.

Consistent with approved Platform Moderation specification.

### Principle 5 — Governance Authority May Be Delegated Downward But Not Upward

Example:

Herd Owner may delegate community moderation through Shepherd Assignment.
Shepherd cannot create authority beyond what was delegated.
Platform authority is never delegated.

Consistent with approved Shepherd Assignment lifecycle and governance model.

### Principle 6 — Reports Initiate Governance

Governance begins when:

Governance actors observe violations
Reports enter governance workflows

Reports are governance-entry entities.

Moderation Actions are governance-outcome entities.

Consistent with approved governance domain model.

## Governance Actor Analysis
| Governance Actor       | Governance Scope | Override Authority                |
| ---------------------- | ---------------- | --------------------------------- |
| Law                    | Entire platform  | Absolute                          |
| Platform Administrator | Entire platform  | Overrides all platform actors     |
| Herd Owner             | Herd governance  | Overrides Shepherd decisions      |
| Shepherd               | Herd moderation  | No override authority above owner |
| Member                 | Reporting only   | None                              |


## Moderation Analysis Per Entity
### User Account
#### Governance Relevance Analysis

Represents platform participation identity.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Platform Administrator
Law
#### Recommended Moderation Boundary

Platform Governance Boundary

#### Moderation Rationale

Account participation may be restricted, suspended, or closed through platform governance.

Community actors do not govern accounts directly.

### User Profile
#### Governance Relevance Analysis

Public identity representation.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Platform Administrator
Law
#### Recommended Moderation Boundary

Platform Governance Boundary

#### Moderation Rationale

Profiles are reportable entities and participate directly in governance workflows.

### Follow Relationship
#### Governance Relevance Analysis

Private participation relationship.

#### Candidate Moderation Scope

Indirect governance only.

#### Candidate Governance Actors
Platform Administrator
Law
#### Recommended Moderation Boundary

Indirect Platform Governance

#### Moderation Rationale

Governance occurs through account governance rather than relationship governance.

The relationship itself is not a moderation target.

### Post
#### Governance Relevance Analysis

Primary user-generated content.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Shepherd (Herd context)
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Shared Community + Platform Governance

#### Moderation Rationale

Posts are directly reportable and directly moderated. Community moderation may affect visibility. Platform moderation may affect the entity itself.

### Comment
#### Governance Relevance Analysis

Discussion participation content.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Shepherd
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Shared Community + Platform Governance

#### Moderation Rationale

Comments participate directly in reporting and moderation workflows.

### Vote
#### Governance Relevance Analysis

Participation signal.

#### Candidate Moderation Scope

Indirect governance.

#### Candidate Governance Actors
Platform Administrator
Law
#### Recommended Moderation Boundary

Indirect Platform Governance

#### Moderation Rationale

Votes are not reportable entities.

Governance occurs indirectly through governance of accounts, content, or abuse behavior.

### Image
#### Governance Relevance Analysis

User-created content asset.

#### Candidate Moderation Scope

Indirect and Direct.

#### Candidate Governance Actors
Shepherd (when attached to Herd content)
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Inherited Content Governance Boundary

#### Moderation Rationale

Images inherit moderation scope from the governed entity using them. Approved specifications already state images are moderated through existing moderation systems.

### Herd
#### Governance Relevance Analysis

Community entity.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Community Governance + Platform Governance

#### Moderation Rationale

Herds are reportable entities and may be governed both by community leadership and platform authority.

### Herd Membership
#### Governance Relevance Analysis

Community participation relationship.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Shepherd
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Community Participation Governance

#### Moderation Rationale

Membership removal is an approved moderation outcome.

### Shepherd Assignment
#### Governance Relevance Analysis

Delegated governance authority.

#### Candidate Moderation Scope

Direct governance.

#### Candidate Governance Actors
Herd Owner
Platform Administrator
Law
#### Recommended Moderation Boundary

Governance Authority Boundary

#### Moderation Rationale

The assignment itself may be revoked or reviewed.

Platform Administrators may review governance conduct.

### Report
#### Governance Relevance Analysis

Governance workflow entity.

#### Candidate Moderation Scope

Governed rather than moderated.

#### Candidate Governance Actors
Shepherd
Herd Owner
Platform Administrator
#### Recommended Moderation Boundary

Governance Process Boundary

#### Moderation Rationale

Reports are reviewed, dismissed, escalated, or resolved.

Reports participate in governance workflows but are not themselves moderation targets.

###### # Moderation Action
#### Governance Relevance Analysis

Governance outcome entity.

#### Candidate Moderation Scope

Governed rather than moderated.

#### Candidate Governance Actors
Herd Owner
Platform Administrator
#### Recommended Moderation Boundary

Governance Decision Boundary

#### Moderation Rationale

Moderation Actions may be upheld, reversed, reviewed, or overridden through escalation.

## Moderation Boundary Matrix
| Entity              | Can Be Moderated | Direct / Indirect   | Governance Actors                    | Highest Authority |
| ------------------- | ---------------- | ------------------- | ------------------------------------ | ----------------- |
| User Account        | Yes              | Direct              | Platform Admin                       | Law               |
| User Profile        | Yes              | Direct              | Platform Admin                       | Law               |
| Follow Relationship | No               | Indirect            | Platform Admin                       | Law               |
| Post                | Yes              | Direct              | Shepherd, Herd Owner, Platform Admin | Law               |
| Comment             | Yes              | Direct              | Shepherd, Herd Owner, Platform Admin | Law               |
| Vote                | No               | Indirect            | Platform Admin                       | Law               |
| Image               | Yes              | Inherited           | Shepherd, Herd Owner, Platform Admin | Law               |
| Herd                | Yes              | Direct              | Herd Owner, Platform Admin           | Law               |
| Herd Membership     | Yes              | Direct              | Shepherd, Herd Owner, Platform Admin | Law               |
| Shepherd Assignment | Yes              | Direct              | Herd Owner, Platform Admin           | Law               |
| Report              | No               | Governance Workflow | Shepherd, Herd Owner, Platform Admin | Law               |
| Moderation Action   | No               | Governance Workflow | Herd Owner, Platform Admin           | Law               |


## Governance Escalation Model
### Standard Escalation Path
Report
    ↓
Shepherd
    ↓
Herd Owner
    ↓
Platform Administrator
    ↓
Law

Consistent with approved moderation specifications and governance journeys.

### Override Model
| Authority              | Can Override         |
| ---------------------- | -------------------- |
| Shepherd               | None                 |
| Herd Owner             | Shepherd             |
| Platform Administrator | Shepherd, Herd Owner |
| Law                    | Entire platform      |


## Moderation Validation
### Ownership Consistency

Moderation authority never transfers ownership.

Validated against approved Ownership Boundary Model.

### Stewardship Consistency

Moderation authority and stewardship remain independent concepts.

Validated against approved Data Stewardship Model.

### Lifecycle Consistency

Moderation outcomes align with approved lifecycle states:

Suspended
Restricted
Removed
Revoked
Applied
Reversed

Validated against Lifecycle Boundary Model.

### Governance Consistency

Fully aligned with:

Reporting System
Shepherd Moderation
Platform Moderation
Governance escalation hierarchy

---

## Validation Verdict

Status: APPROVED

Validation Results

- Completeness Validation: PASS
- Consistency Validation: PASS
- Coverage Validation: PASS
- Modeling Quality Validation: PASS
- Readiness Validation: PASS

Validation Conclusion

The MVP Data Model is approved as the authoritative MVP business data model.

The project may proceed to MVP API Surface Definition.

--- 

