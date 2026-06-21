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
(TBD)

---

# MVP Lifecycle Boundary Model
(TBD)

---