# API Contracts

# MVP API Domain Model

## API Domain Design Principles

- API domains represent business capabilities rather than implementation layers.
- API domains should remain stable as the platform evolves.
- API domains should align with approved MVP business domains.
- API domains should be understandable from an API consumer perspective.
- API domains should not be created solely for individual endpoints.
- API domains should remain independent of database design and internal architecture.

## MVP API Domains

### Identity Domain

Purpose:
Manage account identity and profile capabilities.

Related Data Model Areas:
- User Account
- User Profile

### Social Graph Domain

Purpose:
Manage user-to-user relationship capabilities.

Related Data Model Areas:
- Follow Relationship

### Content Domain

Purpose:
Manage discussion participation and content creation.

Related Data Model Areas:
- Post
- Comment
- Vote

### Community Domain

Purpose:
Manage Herds, membership, and community governance structure.

Related Data Model Areas:
- Herd
- Herd Membership
- Shepherd Assignment

### Feed Domain

Purpose:
Manage content aggregation and content consumption surfaces.

Related Data Model Areas:
- Following Feed
- Herd Feed

### Media Domain

Purpose:
Manage image upload and image usage capabilities.

Related Data Model Areas:
- Image

### Governance Domain

Purpose:
Manage reporting, moderation, enforcement, and governance workflows.

Related Data Model Areas:
- Report
- Moderation Action

---

# Map User Flows to API Capabilities
## User Flow → API Capability Mapping
### Visitor Flows
#### VF-01 — Discover Public Content
| Required API Capabilities  | Domain  |
| -------------------------- | ------- |
| View Public Personal Posts | Content |
| View Public Herd Posts     | Content |
| View Discussion Threads    | Content |
| View Content Images        | Media   |

#### VF-02 — Explore Contributors
| Required API Capabilities           | Domain       |
| ----------------------------------- | ------------ |
| View Public User Profiles           | Identity     |
| View Contributor Content History    | Content      |
| View Contributor Discussion History | Content      |
| View Public Follow Relationships    | Social Graph |

#### VF-03 — Explore Communities
| Required API Capabilities        | Domain    |
| -------------------------------- | --------- |
| Discover Herds                   | Community |
| View Herd Identity               | Community |
| View Herd Rules                  | Community |
| View Herd Membership Information | Community |
| View Herd Content                | Content   |
| View Herd Images                 | Media     |

#### VF-04 — Evaluate Community Quality
| Required API Capabilities          | Domain     |
| ---------------------------------- | ---------- |
| View Herd Identity                 | Community  |
| View Herd Rules                    | Community  |
| View Herd Discussions              | Content    |
| View Discussion Threads            | Content    |
| View Community Governance Presence | Governance |

#### VF-05 — Evaluate Platform Relevance
| Required API Capabilities  | Domain    |
| -------------------------- | --------- |
| View Public User Profiles  | Identity  |
| View Public Personal Posts | Content   |
| View Public Herd Posts     | Content   |
| View Discussion Threads    | Content   |
| Discover Herds             | Community |

### Member Flows
#### MF-01 — Consume Followed User Content
| Required API Capabilities | Domain  |
| ------------------------- | ------- |
| Consume Following Feed    | Feed    |
| View Discussion Threads   | Content |

#### MF-02 — Discover And Follow Interesting People
| Required API Capabilities        | Domain       |
| -------------------------------- | ------------ |
| View Public User Profiles        | Identity     |
| View Contributor Content History | Content      |
| Establish Follow Relationship    | Social Graph |
| End Follow Relationship          | Social Graph |

#### MF-03 — Publish A Personal Post
| Required API Capabilities     | Domain  |
| ----------------------------- | ------- |
| Publish Personal Post         | Content |
| Attach Image To Personal Post | Media   |

#### MF-04 — Participate In A Discussion
| Required API Capabilities | Domain  |
| ------------------------- | ------- |
| Contribute Comment        | Content |
| Contribute Reply          | Content |

#### MF-05 — Evaluate Content Through Voting
| Required API Capabilities   | Domain  |
| --------------------------- | ------- |
| Express Content Evaluation  | Content |
| Change Content Evaluation   | Content |
| Withdraw Content Evaluation | Content |

#### MF-06 — Build A Personal Profile
| Required API Capabilities | Domain   |
| ------------------------- | -------- |
| Maintain User Profile     | Identity |
| Manage Profile Images     | Media    |

#### MF-07 — Join A Herd Community
| Required API Capabilities | Domain    |
| ------------------------- | --------- |
| View Herd Identity        | Community |
| Join Herd                 | Community |
| Leave Herd                | Community |

#### MF-08 — Consume Community Content
| Required API Capabilities | Domain  |
| ------------------------- | ------- |
| Consume Herd Feed         | Feed    |
| View Herd Discussions     | Content |
| View Discussion Threads   | Content |

#### MF-09 — Contribute To A Herd
| Required API Capabilities | Domain  |
| ------------------------- | ------- |
| Publish Herd Post         | Content |
| Attach Image To Herd Post | Media   |

#### MF-10 — Help Maintain Community Quality
| Required API Capabilities | Domain     |
| ------------------------- | ---------- |
| Submit Report             | Governance |

### Herd Owner Flows
#### HOF-01 — Create A Herd
| Required API Capabilities | Domain    |
| ------------------------- | --------- |
| Establish Herd            | Community |
| Manage Herd Images        | Media     |

#### HOF-02 — Define Community Identity
| Required API Capabilities | Domain    |
| ------------------------- | --------- |
| Maintain Herd Identity    | Community |
| Maintain Herd Rules       | Community |
| Manage Herd Images        | Media     |

#### HOF-03 — Grow Community Participation
| Required API Capabilities | Domain  |
| ------------------------- | ------- |
| Consume Herd Feed         | Feed    |
| Publish Herd Post         | Content |
| Contribute Comment        | Content |
| Contribute Reply          | Content |

#### HOF-04 — Delegate Community Governance
| Required API Capabilities | Domain    |
| ------------------------- | --------- |
| Assign Shepherd Authority | Community |
| Revoke Shepherd Authority | Community |

#### HOF-05 — Oversee Community Health
| Required API Capabilities            | Domain     |
| ------------------------------------ | ---------- |
| Review Community Reports             | Governance |
| Review Community Moderation Outcomes | Governance |
| Review Community Activity            | Community  |

#### HOF-06 — Resolve Community Moderation Disputes
| Required API Capabilities              | Domain     |
| -------------------------------------- | ---------- |
| Review Escalated Matters               | Governance |
| Uphold Community Moderation Outcome    | Governance |
| Reverse Community Moderation Outcome   | Governance |
| Escalate Matter To Platform Governance | Governance |

### Shepherd Flows
#### SF-01 — Moderate Herd Content
| Required API Capabilities | Domain     |
| ------------------------- | ---------- |
| Remove Herd Content       | Governance |

#### SF-02 — Review Community Reports
| Required API Capabilities  | Domain     |
| -------------------------- | ---------- |
| Review Community Reports   | Governance |
| Dismiss Report             | Governance |
| Apply Community Moderation | Governance |
| Escalate Matter            | Governance |

#### SF-03 — Moderate Community Membership
| Required API Capabilities | Domain     |
| ------------------------- | ---------- |
| Remove Herd Member        | Governance |

#### SF-04 — Guide Constructive Participation
| Required API Capabilities | Domain    |
| ------------------------- | --------- |
| Review Community Activity | Community |

#### SF-05 — Escalate Serious Community Issues
| Required API Capabilities | Domain     |
| ------------------------- | ---------- |
| Escalate Matter           | Governance |

### Platform Administrator Flow
#### PAF-01 — Review Platform Reports
| Required API Capabilities | Domain     |
| ------------------------- | ---------- |
| Review Platform Reports   | Governance |
| Review Report Context     | Governance |

#### PAF-02 — Enforce Platform Policies
| Required API Capabilities      | Domain     |
| ------------------------------ | ---------- |
| Enforce Content Restrictions   | Governance |
| Enforce Account Restrictions   | Governance |
| Enforce Community Restrictions | Governance |

#### PAF-03 — Resolve Moderation Escalations
| Required API Capabilities  | Domain     |
| -------------------------- | ---------- |
| Review Escalated Matters   | Governance |
| Uphold Moderation Outcome  | Governance |
| Reverse Moderation Outcome | Governance |
| Restore Governed Content   | Governance |
| Expand Enforcement Action  | Governance |

#### PAF-04 — Oversee Community Governance
| Required API Capabilities  | Domain     |
| -------------------------- | ---------- |
| Review Governance Activity | Governance |
| Review Shepherd Conduct    | Governance |
| Review Herd Owner Conduct  | Governance |


## Domain → Capability Matrix
### Identity
View Public User Profiles
Maintain User Profile
### Social Graph
View Public Follow Relationships
Establish Follow Relationship
End Follow Relationship
### Content
View Public Personal Posts
View Public Herd Posts
View Contributor Content History
View Contributor Discussion History
View Herd Content
View Herd Discussions
View Discussion Threads
Publish Personal Post
Publish Herd Post
Contribute Comment
Contribute Reply
Express Content Evaluation
Change Content Evaluation
Withdraw Content Evaluation
### Community
Discover Herds
View Herd Identity
View Herd Rules
View Herd Membership Information
Join Herd
Leave Herd
Establish Herd
Maintain Herd Identity
Maintain Herd Rules
Assign Shepherd Authority
Revoke Shepherd Authority
Review Community Activity
### Feed
Consume Following Feed
Consume Herd Feed
### Media
View Content Images
View Herd Images
Attach Image To Personal Post
Attach Image To Herd Post
Manage Profile Images
Manage Herd Images
### Governance
Submit Report
Review Community Reports
Review Platform Reports
Review Report Context
Dismiss Report
Apply Community Moderation
Remove Herd Content
Remove Herd Member
Review Community Moderation Outcomes
Review Escalated Matters
Uphold Community Moderation Outcome
Reverse Community Moderation Outcome
Escalate Matter
Escalate Matter To Platform Governance
Enforce Content Restrictions
Enforce Account Restrictions
Enforce Community Restrictions
Restore Governed Content
Expand Enforcement Action
Review Governance Activity
Review Shepherd Conduct
Review Herd Owner Conduct
Uphold Moderation Outcome
Reverse Moderation Outcome

## Capability Reuse Analysis
### Highly Reused Capabilities
#### View Discussion Threads
Used By:

VF-01
VF-04
VF-05
MF-01
MF-08
#### View Public User Profiles
Used By:

VF-02
VF-05
MF-02
#### Discover Herds
Used By:

VF-03
VF-05
#### Publish Herd Post
Used By:

MF-09
HOF-03
#### Consume Herd Feed
Used By:

MF-08
HOF-03
#### Review Community Reports
Used By:

HOF-05
SF-02
#### Review Escalated Matters
Used By:

HOF-06
PAF-03

## Flow Coverage Validation
| Flow Group                   | Coverage Status |
| ---------------------------- | --------------- |
| Visitor Flows                | Complete        |
| Member Flows                 | Complete        |
| Herd Owner Flows             | Complete        |
| Shepherd Flows               | Complete        |
| Platform Administrator Flows | Complete        |

---

# MVP Resource Model

## Identity
- User Profile
### Resource: User Profile
Type

Primary Resource

Why It Exists

Represents the public-facing identity of a user.

User Flows
View profile
Edit profile
Discover creators
Navigate from content to profile
API Capabilities
Profile retrieval
Profile updates
Domain Justification

Identity owns user identity representation.

Ownership

User-owned

Aggregate Alignment

Aggregate Root

### Resource That Should NOT Exist
User Account
Reason

Authentication and account credentials are implementation concerns.

Users do not directly manage accounts as business resources.

Account lifecycle remains inside Identity domain operations.

## Social Graph
- Follow Relationship
### Resource: Follow Relationship
Type

Relationship Resource

Why It Exists

Users actively create and remove follow relationships.

User Flows
Follow user
Unfollow user
View followers
View following
API Capabilities
Create follow
Remove follow
Retrieve relationship lists
Domain Justification

Represents user-to-user graph relationships.

Ownership

User-owned

Aggregate Alignment

Relationship between User Profile aggregates.

## Content
- Post
- Comment
- Vote

### Resource: Post
Type

Primary Resource

Why It Exists

Core content unit of the platform.

User Flows
Create post
View post
Edit post
Delete post
API Capabilities
Post creation
Post retrieval
Post management
Domain Justification

Primary content object.

Ownership

User-owned

Aggregate Alignment

Aggregate Root

### Resource: Comment
Type

Child Resource

Parent

Post

Why It Exists

Requires independent user interaction.

User Flows
Add comment
View comments
Remove comment
API Capabilities
Comment creation
Comment retrieval
Comment management
Domain Justification

Content interaction attached to posts.

Ownership

User-owned

Aggregate Alignment

Child within Post aggregate boundary.

### Resource: Vote
Type

Relationship Resource

Parent

Post

Why It Exists

Represents user-content voting interaction.

User Flows
Upvote
Remove vote
API Capabilities
Cast vote
Remove vote
Domain Justification

Content engagement behavior.

Ownership

User-owned

Aggregate Alignment

Relationship between User Profile and Post.

## Community
- Herd
- Membership
- Shepherd
### Resource: Herd
Type

Primary Resource

Why It Exists

Represents community boundary.

User Flows
Create herd
Discover herd
Join herd
Leave herd
View herd
API Capabilities
Herd management
Herd discovery
Membership management
Domain Justification

Primary community object.

Ownership

User-owned with community governance controls.

Aggregate Alignment

Aggregate Root

### Resource: Membership
Type

Relationship Resource

Parent

Herd

Backing Entity

Herd Membership

Why It Exists

Users actively join and leave herds.

User Flows
Join herd
Leave herd
View members
API Capabilities
Membership management
Domain Justification

Community participation relationship.

### Resource: Shepherd
Type

Relationship Resource

Parent

Herd

Backing Entity

Shepherd Assignment

Why It Exists

Community leadership assignments require independent management.

User Flows
Assign shepherd
Remove shepherd
View shepherds
API Capabilities
Shepherd management
Domain Justification

Community governance relationship.

## Feed
- Feed

### Resource: Feed
Type

Derived Resource

Why It Exists

Users directly interact with feeds.

User Flows
View home feed
Refresh feed
API Capabilities
Feed retrieval
Domain Justification

Feed is not a stored entity but requires independent API interaction.

Ownership

System-generated

Aggregate Alignment

None

### Resources That Should NOT Exist
Feed Item
Ranking
Recommendation
Reason

Derived system concepts.

No independent lifecycle.

## Media
- Image

### Resource: Image
Type

Primary Resource

Why It Exists

Requires independent upload and retrieval workflows.

User Flows
Upload image
Attach image to post
Display image
API Capabilities
Upload media
Retrieve media
Domain Justification

Media lifecycle differs from content lifecycle.

Ownership

User-owned

Aggregate Alignment

Independent aggregate.

## Governance
- Report
- Moderation Action

### Resource: Report
Type

Governance Resource

Why It Exists

Users actively submit reports.

User Flows
Report post
Report comment
API Capabilities
Report submission
Report review
Domain Justification

Governance intake object.

Ownership

Mixed (user-created, system-governed)

Aggregate Alignment

Aggregate Root

### Resource: Moderation Action
Type

Governance Resource

Why It Exists

Represents moderation decisions.

User Flows

Indirectly involved in moderation workflow.

API Capabilities
Review report
Execute moderation action
Domain Justification

Governance enforcement object.

Ownership

System-owned

Aggregate Alignment

Aggregate Root

## Resources Not Exposed As Independent Resources

- User Account
- Feed Item
- Ranking
- Recommendation

Rationale:
Internal or derived concepts that do not require independent API interaction.

## Final Resource Inventory
| Resource            | Type         | Domain       |
| ------------------- | ------------ | ------------ |
| User Profile        | Primary      | Identity     |
| Follow Relationship | Relationship | Social Graph |
| Post                | Primary      | Content      |
| Comment             | Child        | Content      |
| Vote                | Relationship | Content      |
| Herd                | Primary      | Community    |
| Membership          | Relationship | Community    |
| Shepherd            | Relationship | Community    |
| Feed                | Derived      | Feed         |
| Image               | Primary      | Media        |
| Report              | Governance   | Governance   |
| Moderation Action   | Governance   | Governance   |

## Resource Relationship Matrix
| Parent Resource | Child / Relationship Resource |
| --------------- | ----------------------------- |
| User Profile    | Follow Relationship           |
| Post            | Comment                       |
| Post            | Vote                          |
| Herd            | Membership                    |
| Herd            | Shepherd                      |
| Report          | Moderation Action             |

---

# MVP CRUD Operations
## CRUD Decision Principles
### Principle 1 — CRUD Must Be Flow Driven

A CRUD operation exists only if required by an approved MVP user flow.

### Principle 2 — Relationship Resources Rarely Require Full CRUD

Relationship resources typically support:

Create relationship
Read relationship
Remove relationship

Not arbitrary updates.

Examples:

Follow Relationship
Membership
Shepherd Assignment
### Principle 3 — Governance Resources Are Workflow Driven

Governance resources support governance actions rather than traditional CRUD.

Examples:

Report
Moderation Action
### Principle 4 — Derived Resources Are Read-Only

Derived resources do not own data.

Examples:

Following Feed
Herd Feed
### Principle 5 — Delete Means Business Removal

Delete represents a meaningful business operation.

It does not imply physical deletion.

### Principle 6 — Lifecycle Constraints Override Generic CRUD

Entity lifecycle definitions determine whether update/delete operations make business sense.

## MVP CRUD Matrix
| Resource            | Create | Read | Update | Delete |
| ------------------- | ------ | ---- | ------ | ------ |
| User Profile        | No*    | Yes  | Yes    | No     |
| Follow Relationship | Yes    | Yes  | No     | Yes    |
| Post                | Yes    | Yes  | Yes    | Yes    |
| Comment             | Yes    | Yes  | Yes    | Yes    |
| Vote                | Yes    | Yes  | Yes**  | Yes    |
| Herd                | Yes    | Yes  | Yes    | No     |
| Membership          | Yes    | Yes  | No     | Yes    |
| Shepherd Assignment | Yes    | Yes  | No     | Yes    |
| Feed                | No     | Yes  | No     | No     |
| Image               | Yes    | Yes  | No     | Yes    |
| Report              | Yes    | Yes  | No     | No     |
| Moderation Action   | Yes*** | Yes  | No     | No     |
Notes:

- *User Profile is automatically created through account lifecycle and is not independently created.
- **Vote update represents changing HypeUp ↔ HypeDown.
- ***Moderation Action is created through governance workflows, not normal user CRUD.

## Non-CRUD Action Inventory
### Relationship Management Operations
| Resource            | Action             |
| ------------------- | ------------------ |
| Follow Relationship | Follow User        |
| Follow Relationship | Unfollow User      |
| Membership          | Join Herd          |
| Membership          | Leave Herd         |
| Membership          | Remove Herd Member |
| Shepherd Assignment | Assign Shepherd    |
| Shepherd Assignment | Revoke Shepherd    |

### Governance Actions
| Resource          | Action                       |
| ----------------- | ---------------------------- |
| Report            | Dismiss Report               |
| Report            | Escalate Report              |
| Report            | Review Report                |
| Moderation Action | Apply Moderation Action      |
| Moderation Action | Reverse Moderation Action    |
| Moderation Action | Uphold Moderation Outcome    |
| Moderation Action | Expand Enforcement Action    |
| Moderation Action | Restore Governed Content     |
| Herd              | Restrict Herd                |
| Herd              | Close Herd                   |
| User Profile*     | Enforce Profile Restrictions |
- *Governance affects the resource but is not CRUD.

### Derived Resource Retrieval Operations
| Resource | Action                  |
| -------- | ----------------------- |
| Feed     | Retrieve Following Feed |
| Feed     | Retrieve Herd Feed      |

## Resources That Should NOT Support Full CRUD
| Resource            | Reason                       |
| ------------------- | ---------------------------- |
| User Profile        | No independent Create/Delete |
| Follow Relationship | No Update                    |
| Membership          | No Update                    |
| Shepherd Assignment | No Update                    |
| Feed                | Read-only derived resource   |
| Image               | No Update                    |
| Report              | No Update/Delete             |
| Moderation Action   | No Update/Delete             |
| Herd                | No Delete                    |


## CRUD Validation
### Validated against:
Visitor Flows
Member Flows
Herd Owner Flows
Shepherd Flows
Platform Administrator Flows
API Capability Model
Resource Model
Lifecycle Model
Moderation Boundary Model

### Validation Result:
All approved MVP user flows supported.
All approved MVP capabilities supported.
No resource requires additional CRUD operations.
No unsupported CRUD operations remain.
Governance workflows remain separated from business CRUD.
Derived resources remain read-only.

---

# 
