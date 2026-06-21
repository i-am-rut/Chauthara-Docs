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
| User Profile      | Report → User Profile      | Many-to-Many |
| Post              | Report → Post              | Many-to-Many |
| Comment           | Report → Comment           | Many-to-Many |
| Herd              | Report → Herd              | Many-to-Many |
| Moderation Action | Report → Moderation Action | One-to-Many  |
#### Refinement 
| Relationship          | Cardinality |
| --------------------- | ----------- |
| Report → User Profile | Many-to-One |
| Report → Post         | Many-to-One |
| Report → Comment      | Many-to-One |
| Report → Herd         | Many-to-One |


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

