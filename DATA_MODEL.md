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
(TBD)

---

# MVP Aggregate Boundary Model
(TBD)

---

# MVP Lifecycle Boundary Model
(TBD)

---