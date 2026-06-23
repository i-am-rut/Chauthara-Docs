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
Identity Domain also owns account lifecycle and identity-access workflows required for platform participation.

Examples:
- Account Registration
- Login
- Logout
- Email Verification
- Password Recovery
- Password Reset

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
### Identity Lifecycle Capabilities
| Required API Capability     | Domain   |
| --------------------------- | -------- |
| Register Account            | Identity |
| Login                       | Identity |
| Logout                      | Identity |
| Retrieve Current Identity   | Identity |
| Verify Email                | Identity |
| Recover Password            | Identity |
| Reset Password              | Identity |

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
| View Herd Description            | Community |
| View Herd Rules                  | Community |
| View Herd Membership Information | Community |
| View Herd Content                | Content   |
| View Herd Images                 | Media     |

#### VF-04 — Evaluate Community Quality
| Required API Capabilities          | Domain     |
| ---------------------------------- | ---------- |
| View Herd Identity                 | Community  |
| View Herd Description              | Community  |
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
| View Herd Description     | Community |
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
| Maintain Herd Description | Community |
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
Register Account
Login
Logout
Retrieve Current Identity
Verify Email
Recover Password
Reset Password

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
View Herd Description
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

### Identity Workflow Operations

The Identity domain contains workflow operations that support account lifecycle management.

These operations do not expose User Account as an independent API resource.

Examples:

- Account Registration
- Login
- Logout
- Email Verification
- Password Recovery
- Password Reset
- Current Identity Retrieval

These capabilities are modeled as workflow endpoints rather than resource endpoints.

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

Identity Fields:

- name
- description

Governance Fields:

- rules

Media Fields:

- image references

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
### Identity Workflow Operations
| Operation                 | Purpose                      |
| ------------------------- | ---------------------------- |
| Register Account          | Create account lifecycle     |
| Login                     | Establish authenticated use  |
| Logout                    | End authenticated use        |
| Retrieve Current Identity | Retrieve active identity     |
| Verify Email              | Activate account lifecycle   |
| Recover Password          | Begin recovery workflow      |
| Reset Password            | Complete recovery workflow   |

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

# MVP Endpoint Inventory
## Endpoint Design Principles
### Principle 1 — Every Endpoint Must Map To A Resource
No capability-only endpoints.

### Principle 2 — Relationship Resources Get Dedicated Endpoints
Applies to:

Follow Relationship
Membership
Shepherd Assignment
Vote
### Principle 3 — Derived Resources Are Read Only
Applies to:

Following Feed
Herd Feed
### Principle 4 — Governance Uses Workflow Endpoints
Governance actions are not forced into CRUD.

### Principle 5 — Parent/Child Relationships Must Be Explicit
Examples:

Comments belong to Posts
Memberships belong to Herds
Shepherd Assignments belong to Herds
### Principle 6 — One Business Operation = One Endpoint
Avoid duplicate retrieval surfaces.

## MVP Endpoint Inventory
### Identity Domain
#### Identity Workflow Endpoints

| Endpoint                     | Purpose                   | Operation | Classification |
| ---------------------------- | ------------------------- | --------- | -------------- |
| POST /auth/register          | Register account          | Workflow  | Identity       |
| POST /auth/login             | Login                     | Workflow  | Identity       |
| POST /auth/logout            | Logout                    | Workflow  | Identity       |
| GET /auth/me                 | Retrieve current identity | Workflow  | Identity       |
| POST /auth/verify-email      | Verify email              | Workflow  | Identity       |
| POST /auth/forgot-password   | Recover password          | Workflow  | Identity       |
| POST /auth/reset-password    | Reset password            | Workflow  | Identity       |

#### User Profile
| Endpoint                           | Purpose                        | Operation | Classification |
| ---------------------------------- | ------------------------------ | --------- | -------------- |
| GET /profiles                      | Discover profiles              | Read      | Resource       |
| GET /profiles/{profileId}          | View profile                   | Read      | Resource       |
| PATCH /profiles/{profileId}        | Update profile                 | Update    | Resource       |
| GET /profiles/{profileId}/posts    | Contributor content history    | Read      | Derived        |
| GET /profiles/{profileId}/comments | Contributor discussion history | Read      | Derived        |

### Social Graph Domain
#### Follow Relationship
| Endpoint                               | Purpose        | Operation | Classification |
| -------------------------------------- | -------------- | --------- | -------------- |
| GET /profiles/{profileId}/followers    | View followers | Read      | Relationship   |
| GET /profiles/{profileId}/following    | View following | Read      | Relationship   |
| POST /profiles/{profileId}/followers   | Follow user    | Create    | Relationship   |
| DELETE /profiles/{profileId}/followers | Unfollow user  | Delete    | Relationship   |

### Content Domain
#### Post
| Endpoint               | Purpose              | Operation | Classification |
| ---------------------- | -------------------- | --------- | -------------- |
| GET /posts             | Discover posts       | Read      | Resource       |
| POST /posts            | Create personal post | Create    | Resource       |
| GET /posts/{postId}    | View post            | Read      | Resource       |
| PATCH /posts/{postId}  | Edit post            | Update    | Resource       |
| DELETE /posts/{postId} | Remove post          | Delete    | Resource       |

#### Comment
| Endpoint                           | Purpose                    | Operation | Classification |
| ---------------------------------- | -------------------------- | --------- | -------------- |
| GET /posts/{postId}/comments       | Retrieve discussion thread | Read      | Resource       |
| POST /posts/{postId}/comments      | Create comment             | Create    | Resource       |
| GET /comments/{commentId}          | View comment/reply         | Read      | Resource       |
| PATCH /comments/{commentId}        | Edit comment/reply         | Update    | Resource       |
| DELETE /comments/{commentId}       | Remove comment/reply       | Delete    | Resource       |
| POST /comments/{commentId}/replies | Create reply               | Create    | Resource       |

#### Vote
| Endpoint                          | Purpose               | Operation | Classification |
| --------------------------------- | --------------------- | --------- | -------------- |
| GET /posts/{postId}/votes         | View vote totals      | Read      | Relationship   |
| PUT /posts/{postId}/vote          | Create or change vote | Update    | Relationship   |
| DELETE /posts/{postId}/vote       | Withdraw vote         | Delete    | Relationship   |
| GET /comments/{commentId}/votes   | View vote totals      | Read      | Relationship   |
| PUT /comments/{commentId}/vote    | Create or change vote | Update    | Relationship   |
| DELETE /comments/{commentId}/vote | Withdraw vote         | Delete    | Relationship   |


### Community Domain
#### Herd
| Endpoint                  | Purpose                    | Operation | Classification |
| ------------------------- | -------------------------- | --------- | -------------- |
| GET /herds                | Discover Herds             | Read      | Resource       |
| POST /herds               | Create Herd                | Create    | Resource       |
| GET /herds/{herdId}       | View Herd                  | Read      | Resource       |
| PATCH /herds/{herdId}     | Update Herd identity/rules | Update    | Resource       |
| GET /herds/{herdId}/posts | View Herd content          | Read      | Derived        |

#### Herd Membership
| Endpoint                                  | Purpose                    | Operation | Classification |
| ----------------------------------------- | -------------------------- | --------- | -------------- |
| GET /herds/{herdId}/members               | View membership            | Read      | Relationship   |
| POST /herds/{herdId}/members              | Join Herd                  | Create    | Relationship   |
| DELETE /herds/{herdId}/members/{memberId} | Leave or remove membership | Delete    | Relationship   |

#### Shepherd Assignment
| Endpoint                                        | Purpose         | Operation | Classification |
| ----------------------------------------------- | --------------- | --------- | -------------- |
| GET /herds/{herdId}/shepherds                   | View shepherds  | Read      | Relationship   |
| POST /herds/{herdId}/shepherds                  | Assign shepherd | Create    | Relationship   |
| DELETE /herds/{herdId}/shepherds/{assignmentId} | Revoke shepherd | Delete    | Relationship   |

### Feed Domain
#### Following Feed
| Endpoint             | Purpose                 | Operation | Classification |
| -------------------- | ----------------------- | --------- | -------------- |
| GET /feeds/following | Retrieve following feed | Read      | Derived        |

#### Herd Feed
| Endpoint         | Purpose            | Operation | Classification |
| ---------------- | ------------------ | --------- | -------------- |
| GET /feeds/herds | Retrieve herd feed | Read      | Derived        |

### Media Domain
#### Image
| Endpoint                 | Purpose        | Operation | Classification |
| ------------------------ | -------------- | --------- | -------------- |
| POST /images             | Upload image   | Create    | Resource       |
| GET /images/{imageId}    | Retrieve image | Read      | Resource       |
| DELETE /images/{imageId} | Remove image   | Delete    | Resource       |

### Governance Domain
#### Report
| Endpoint                | Purpose             | Operation | Classification |
| ----------------------- | ------------------- | --------- | -------------- |
| POST /reports           | Submit report       | Create    | Governance     |
| GET /reports/{reportId} | View report         | Read      | Governance     |
| GET /reports            | Review report queue | Read      | Governance     |

#### Moderation Actions
| Endpoint                           | Purpose                 | Operation | Classification |
| ---------------------------------- | ----------------------- | --------- | -------------- |
| GET /moderation-actions/{actionId} | View moderation outcome | Read      | Governance     |

#### Community Governance Workflow
| Endpoint                          | Purpose                    | Operation         | Classification |
| --------------------------------- | -------------------------- | ----------------- | -------------- |
| POST /reports/{reportId}/dismiss  | Dismiss report             | Governance Action | Governance     |
| POST /reports/{reportId}/moderate | Apply community moderation | Governance Action | Governance     |
| POST /reports/{reportId}/escalate | Escalate report            | Governance Action | Governance     |
| GET /reports/escalated            | Review escalated matters   | Governance        | Governance     |

#### Herd Content Moderation
| Endpoint                          | Purpose              | Operation         | Classification |
| --------------------------------- | -------------------- | ----------------- | -------------- |
| POST /posts/{postId}/remove       | Remove herd post     | Governance Action | Governance     |
| POST /comments/{commentId}/remove | Remove comment/reply | Governance Action | Governance     |

#### Platform Governance Workflow
| Endpoint                                    | Purpose                    | Operation         | Classification |
| ------------------------------------------- | -------------------------- | ----------------- | -------------- |
| POST /moderation-actions/{actionId}/uphold  | Uphold moderation outcome  | Governance Action | Governance     |
| POST /moderation-actions/{actionId}/reverse | Reverse moderation outcome | Governance Action | Governance     |
| POST /moderation-actions/{actionId}/restore | Restore governed content   | Governance Action | Governance     |
| POST /moderation-actions/{actionId}/expand  | Expand enforcement action  | Governance Action | Governance     |

#### Governance Oversight
| Endpoint                    | Purpose                    | Operation  | Classification |
| --------------------------- | -------------------------- | ---------- | -------------- |
| GET /governance/activity    | Review governance activity | Governance | Governance     |
| GET /governance/shepherds   | Review shepherd conduct    | Governance | Governance     |
| GET /governance/herd-owners | Review herd owner conduct  | Governance | Governance     |

#### Profile Enforcement

| Endpoint                          | Purpose                  | Operation         | Classification |
| --------------------------------- | ------------------------ | ----------------- | -------------- |
| POST /profiles/{profileId}/restrict | Restrict user profile   | Governance Action | Governance     |

#### Community Enforcement

| Endpoint                      | Purpose                  | Operation         | Classification |
| ----------------------------- | ------------------------ | ----------------- | -------------- |
| POST /herds/{herdId}/restrict | Restrict community       | Governance Action | Governance     |

#### Membership Moderation

| Endpoint                                         | Purpose                    | Operation         | Classification |
| ------------------------------------------------ | -------------------------- | ----------------- | -------------- |
| POST /herds/{herdId}/members/{memberId}/remove   | Remove herd member         | Governance Action | Governance     |


---

# MVP Authorization Boundaries
## Authorization Principles
### Principle 1 — Authentication And Authorization Are Separate
Identity verification does not automatically grant resource authority.

### Principle 2 — Ownership Does Not Imply Unlimited Authority
Owners manage their resources.

Governance actors may moderate those resources.

### Principle 3 — Governance Overrides Ownership
Approved governance actors may override ownership actions when moderation requires it.

### Principle 4 — Public Discovery Is Fundamental
Public content required by Visitor journeys remains publicly readable.

### Principle 5 — Community Authority Is Herd Scoped
Shepherd authority exists only inside assigned Herds.

### Principle 6 — Herd Owners Govern Communities
Herd Owners govern:
Herd identity
Herd membership
Shepherd assignments
Community moderation disputes
### Principle 7 — Platform Authority Is Universal
Platform Administrators may govern any moderated MVP resource.

### Principle 8 — Higher Governance Roles Inherit Lower Capabilities
Platform Administrator inherits all lower-role capabilities.

Herd Owner inherits Member capabilities.

Shepherd inherits Member capabilities.

## Identity Workflow Authorization

| Workflow Operation         | Visitor | Member | Shepherd | Herd Owner | Platform Admin |
| -------------------------- | ------- | ------ | -------- | ---------- | -------------- |
| Register Account           | Yes     | No     | No       | No         | No             |
| Login                      | Yes     | Yes*   | Yes*     | Yes*       | Yes*           |
| Logout                     | No      | Yes    | Yes      | Yes        | Yes            |
| Retrieve Current Identity  | No      | Yes    | Yes      | Yes        | Yes            |
| Verify Email               | Yes     | No      | No      | No         | No             |
| Recover Password           | Yes     | Yes    | Yes      | Yes        | Yes            |
| Reset Password             | Yes     | Yes    | Yes      | Yes        | Yes            |

*Login is only applicable when not currently authenticated.

## Authorization Actor Matrix
| Capability Category  | Visitor | Member | Shepherd    | Herd Owner           | Platform Admin |
| -------------------- | ------- | ------ | ----------- | -------------------- | -------------- |
| Public Content Read  | Yes     | Yes    | Yes         | Yes                  | Yes            |
| Public Profile Read  | Yes     | Yes    | Yes         | Yes                  | Yes            |
| Follow Users         | No      | Yes    | Yes         | Yes                  | Yes            |
| Create Posts         | No      | Yes    | Yes         | Yes                  | Yes            |
| Create Comments      | No      | Yes    | Yes         | Yes                  | Yes            |
| Vote                 | No      | Yes    | Yes         | Yes                  | Yes            |
| Join Herd            | No      | Yes    | Yes         | Yes                  | Yes            |
| Create Herd          | No      | Yes    | Yes         | Yes                  | Yes            |
| Submit Report        | No      | Yes    | Yes         | Yes                  | Yes            |
| Review Reports       | No      | No     | Herd Scoped | Herd Scoped          | Platform Wide  |
| Moderate Content     | No      | No     | Herd Scoped | Herd Scoped Override | Platform Wide  |
| Moderate Membership  | No      | No     | Herd Scoped | Herd Scoped Override | Platform Wide  |
| Assign Shepherds     | No      | No     | No          | Own Herd Only        | Platform Wide  |
| Platform Enforcement | No      | No     | No          | No                   | Yes            |

## Resource Authorization Matrix
### User Profile
| Authority           | Actors                 |
| ------------------- | ---------------------- |
| Public Read         | Visitor+               |
| Authenticated Read  | Member+                |
| Create              | System Lifecycle       |
| Update              | Profile Owner          |
| Delete              | None                   |
| Governance Override | Platform Administrator |


### Follow Relationship
| Authority           | Actors                 |
| ------------------- | ---------------------- |
| Public Read         | Visitor+               |
| Create              | Following User         |
| Update              | None                   |
| Delete              | Following User         |
| Governance Override | Platform Administrator |


### Post
| Authority           | Actors                                                      |
| ------------------- | ----------------------------------------------------------- |
| Public Read         | Visitor+                                                    |
| Create              | Member+                                                     |
| Update              | Author                                                      |
| Delete              | Author                                                      |
| Governance Override | Shepherd (Herd Context), Herd Owner, Platform Administrator |


### Comment
| Authority           | Actors                                                      |
| ------------------- | ----------------------------------------------------------- |
| Public Read         | Visitor+                                                    |
| Create              | Member+                                                     |
| Update              | Author                                                      |
| Delete              | Author                                                      |
| Governance Override | Shepherd (Herd Context), Herd Owner, Platform Administrator |

### Vote
| Authority           | Actors                 |
| ------------------- | ---------------------- |
| Read Totals         | Visitor+               |
| Create              | Voting User            |
| Update              | Voting User            |
| Delete              | Voting User            |
| Governance Override | Platform Administrator |

### Herd
| Authority           | Actors                 |
| ------------------- | ---------------------- |
| Public Read         | Visitor+               |
| Create              | Member+                |
| Update              | Herd Owner             |
| Delete              | None                   |
| Governance Override | Platform Administrator |

### Membership
| Authority           | Actors                                       |
| ------------------- | -------------------------------------------- |
| Public Read         | Visitor+                                     |
| Create              | Member (Join)                                |
| Delete              | Member (Leave)                               |
| Governance Override | Shepherd, Herd Owner, Platform Administrator |

### Shepherd Assignment
| Authority           | Actors                 |
| ------------------- | ---------------------- |
| Public Read         | Visitor+               |
| Create              | Herd Owner             |
| Delete              | Herd Owner             |
| Governance Override | Platform Administrator |

### Feed
| Authority           | Actors         |
| ------------------- | -------------- |
| Following Feed Read | Member+        |
| Herd Feed Read      | Member+        |
| Create              | None           |
| Update              | None           |
| Delete              | None           |
| Governance Override | Not Applicable |

### Image 
| Authority           | Actors                                                      |
| ------------------- | ----------------------------------------------------------- |
| Public Read         | Visitor+                                                    |
| Create              | Member+                                                     |
| Delete              | Uploading User                                              |
| Governance Override | Shepherd (Herd Context), Herd Owner, Platform Administrator |

### Report
| Authority           | Actors                               |
| ------------------- | ------------------------------------ |
| Read                | Reporter, Relevant Governance Actors |
| Create              | Member+                              |
| Update              | None                                 |
| Delete              | None                                 |
| Governance Override | Applicable Governance Authority      |

### Moderation Action
| Authority           | Actors                                       |
| ------------------- | -------------------------------------------- |
| Read                | Relevant Governance Actors                   |
| Create              | Shepherd, Herd Owner, Platform Administrator |
| Update              | None                                         |
| Delete              | None                                         |
| Governance Override | Higher Governance Authority                  |

## Endpoint Authorization Matrix
### Visitor Accessible
#### Identity
GET /profiles
GET /profiles/{profileId}
GET /profiles/{profileId}/posts
GET /profiles/{profileId}/comments
#### Social Graph
GET /profiles/{profileId}/followers
GET /profiles/{profileId}/following
#### Content
GET /posts
GET /posts/{postId}
GET /posts/{postId}/comments
GET /comments/{commentId}
GET vote-total endpoints
#### Community
GET /herds
GET /herds/{herdId}
GET membership visibility endpoints
GET shepherd visibility endpoints
#### Media
Public image retrieval endpoints

### Member Only
PATCH own profile
Follow / unfollow
Create post
Edit own post
Delete own post
Create comment
Edit own comment
Delete own comment
Vote operations
Join herd
Leave herd
Create herd
Upload image
Submit report
Read following feed
Read herd feed

### Herd Owner
Additional authority:
Update owned herd
Maintain herd rules
Assign shepherd
Revoke shepherd
Review community reports
Resolve escalations
Reverse shepherd moderation decisions

### Shepherd
Additional authority:
Review herd reports
Dismiss herd reports
Remove herd content
Remove herd members
Escalate reports

### Platform Administrator
Additional authority:
Review all reports
Review all moderation actions
Restrict content
Restrict communities
Restrict profiles
Reverse moderation actions
Expand enforcement actions
Restore governed content
Oversee governance actors

## Governance Override Matrix
| Resource            | Shepherd          | Herd Owner                | Platform Admin |
| ------------------- | ----------------- | ------------------------- | -------------- |
| User Profile        | No                | No                        | Yes            |
| Follow Relationship | No                | No                        | Yes            |
| Personal Post       | No                | No                        | Yes            |
| Herd Post           | Yes               | Yes                       | Yes            |
| Herd Comment        | Yes               | Yes                       | Yes            |
| Herd Image          | Yes               | Yes                       | Yes            |
| Herd Membership     | Yes               | Yes                       | Yes            |
| Herd                | No                | Yes (Own Herd Governance) | Yes            |
| Shepherd Assignment | No                | Owner Authority           | Yes            |
| Report              | Review Scope Only | Review Scope Only         | Yes            |
| Moderation Action   | Create            | Override Shepherd         | Final Override |


## Authorization Validation
### User Flow Validation
Visitor flows require public discovery access.

Satisfied.

Member flows require participation capabilities.

Satisfied.

Herd Owner governance flows require shepherd assignment and dispute resolution authority.

Satisfied.

Shepherd moderation flows require content moderation, membership moderation, and report review authority.

Satisfied.

Platform Administrator flows require platform-wide override authority.

Satisfied.

### Ownership Boundary Validation
Ownership remains distinct from governance authority.

Consistent with approved ownership model.

### Moderation Boundary Validation
Consistent with approved moderation hierarchy:

Platform Administrator
        ↓
Herd Owner
        ↓
Shepherd

### Endpoint Inventory Validation
All approved endpoints have an identified authorization boundary.

No endpoint requires creation, removal, or restructuring.

Consistent with approved endpoint inventory.

---

# MVP Request Contract Model

## Request Contract Principles
### Principle 1 — Ownership Is Never Client Supplied
### Principle 2 — Lifecycle State Is Never Client Supplied
### Principle 3 — Governance State Is Never Client Supplied
### Principle 4 — Derived Metrics Are Never Client Supplied
### Principle 5 — Relationship Ownership Is Identity Derived
### Principle 6 — Governance Actions Operate On Existing Resources

## Endpoint Request Classification Matrix
### Identity Workflow
| Endpoint                   | Classification    |
| -------------------------- | ----------------- |
| POST /auth/register        | Request Body Only |
| POST /auth/login           | Request Body Only |
| POST /auth/logout          | No Input          |
| GET /auth/me               | No Input          |
| POST /auth/verify-email    | Request Body Only |
| POST /auth/forgot-password | Request Body Only |
| POST /auth/reset-password  | Request Body Only |

### User Profiles
| Endpoint                           | Classification       |
| ---------------------------------- | -------------------- |
| GET /profiles                      | Query Parameter Only |
| GET /profiles/{profileId}          | Path Parameter Only  |
| PATCH /profiles/{profileId}        | Path + Request Body  |
| GET /profiles/{profileId}/posts    | Path + Query         |
| GET /profiles/{profileId}/comments | Path + Query         |

### Follow Relationships
| Endpoint                               | Classification      |
| -------------------------------------- | ------------------- |
| GET /profiles/{profileId}/followers    | Path + Query        |
| GET /profiles/{profileId}/following    | Path + Query        |
| POST /profiles/{profileId}/followers   | Path Parameter Only |
| DELETE /profiles/{profileId}/followers | Path Parameter Only |

### Posts
| Endpoint               | Classification       |
| ---------------------- | -------------------- |
| GET /posts             | Query Parameter Only |
| POST /posts            | Request Body Only    |
| GET /posts/{postId}    | Path Parameter Only  |
| PATCH /posts/{postId}  | Path + Request Body  |
| DELETE /posts/{postId} | Path Parameter Only  |

### Comments
| Endpoint                           | Classification      |
| ---------------------------------- | ------------------- |
| GET /posts/{postId}/comments       | Path + Query        |
| POST /posts/{postId}/comments      | Path + Request Body |
| GET /comments/{commentId}          | Path Parameter Only |
| PATCH /comments/{commentId}        | Path + Request Body |
| DELETE /comments/{commentId}       | Path Parameter Only |
| POST /comments/{commentId}/replies | Path + Request Body |

### Votes
| Endpoint                          | Classification      |
| --------------------------------- | ------------------- |
| GET /posts/{postId}/votes         | Path Parameter Only |
| PUT /posts/{postId}/vote          | Path + Request Body |
| DELETE /posts/{postId}/vote       | Path Parameter Only |
| GET /comments/{commentId}/votes   | Path Parameter Only |
| PUT /comments/{commentId}/vote    | Path + Request Body |
| DELETE /comments/{commentId}/vote | Path Parameter Only |

### Herds
| Endpoint                  | Classification       |
| ------------------------- | -------------------- |
| GET /herds                | Query Parameter Only |
| POST /herds               | Request Body Only    |
| GET /herds/{herdId}       | Path Parameter Only  |
| PATCH /herds/{herdId}     | Path + Request Body  |
| GET /herds/{herdId}/posts | Path + Query         |

### Memberships
| Endpoint                                  | Classification      |
| ----------------------------------------- | ------------------- |
| GET /herds/{herdId}/members               | Path + Query        |
| POST /herds/{herdId}/members              | Path Parameter Only |
| DELETE /herds/{herdId}/members/{memberId} | Path Parameter Only |

### Shepherd Assignments
| Endpoint                                        | Classification      |
| ----------------------------------------------- | ------------------- |
| GET /herds/{herdId}/shepherds                   | Path + Query        |
| POST /herds/{herdId}/shepherds                  | Path + Request Body |
| DELETE /herds/{herdId}/shepherds/{assignmentId} | Path Parameter Only |

### Feeds
| Endpoint             | Classification       |
| -------------------- | -------------------- |
| GET /feeds/following | Query Parameter Only |
| GET /feeds/herds     | Query Parameter Only |

### Images
| Endpoint                 | Classification      |
| ------------------------ | ------------------- |
| POST /images             | Request Body Only   |
| GET /images/{imageId}    | Path Parameter Only |
| DELETE /images/{imageId} | Path Parameter Only |

### Reports
| Endpoint                | Classification       |
| ----------------------- | -------------------- |
| POST /reports           | Request Body Only    |
| GET /reports/{reportId} | Path Parameter Only  |
| GET /reports            | Query Parameter Only |

### Governance Workflows
| Endpoint                                         | Classification       |
| ------------------------------------------------ | -------------------- |
| POST /reports/{reportId}/dismiss                 | Path Parameter Only  |
| POST /reports/{reportId}/moderate                | Path + Request Body  |
| POST /reports/{reportId}/escalate                | Path Parameter Only  |
| GET /reports/escalated                           | Query Parameter Only |
| POST /posts/{postId}/remove                      | Path Parameter Only  |
| POST /comments/{commentId}/remove                | Path Parameter Only  |
| POST /moderation-actions/{actionId}/uphold       | Path Parameter Only  |
| POST /moderation-actions/{actionId}/reverse      | Path Parameter Only  |
| POST /moderation-actions/{actionId}/restore      | Path Parameter Only  |
| POST /moderation-actions/{actionId}/expand       | Path + Request Body  |
| GET /governance/activity                         | Query Parameter Only |
| GET /governance/shepherds                        | Query Parameter Only |
| GET /governance/herd-owners                      | Query Parameter Only |
| POST /profiles/{profileId}/restrict              | Path + Request Body  |
| POST /herds/{herdId}/restrict                    | Path + Request Body  |
| POST /herds/{herdId}/members/{memberId}/remove   | Path + Request Body  |

## Input Source Matrix
### Client Supplied
Examples:

#### Identity
registration credentials
login credentials
verification token
password reset token
new password
#### Profile
display name
bio
profile image reference
cover image reference
#### Post
post content
attached image references
#### Comment
comment content
reply content
#### Vote
vote direction
#### Herd
name
description
rules
image references
#### Shepherd Assignment
target member identifier
#### Report
report target
report reason
optional report context
#### Governance
moderation rationale
enforcement scope expansion details

### URL Derived
Examples:

profileId
postId
commentId
herdId
memberId
reportId
actionId
assignmentId

### Authenticated Identity Derived
Examples:

accountId
profile owner
author
commenter
voter
follower
membership creator
shepherd assigner
reporter
moderator

### System Derived
Examples:

createdAt
updatedAt
reportStatus
moderationOutcome
lifecycleState
ownership fields
vote totals
follower counts
membership counts
shepherd counts
feed composition
governance history

Validated against ownership, lifecycle, moderation, and stewardship models.

## Required / Optional / Forbidden Input Matrix
### Identity
#### Required
registration credentials
login credentials
verification token
reset token
new password
#### Optional
none
#### Forbidden
account status
verification state
suspension state
### User Profile
#### Required
profileId (update)
#### Optional
bio
display information
image references
#### Forbidden
accountId
followerCount
followingCount
aura
createdAt
updatedAt

### Post
#### Required
content (create)
#### Optional
image references
#### Forbidden
authorId
voteTotals
lifecycleState
moderationState

### Comment
#### Required
content
#### Optional
none
#### Forbidden
authorId
parent ownership fields
lifecycle state

### Vote
#### Required
vote direction
#### Optional
none
#### Forbidden
voterId
voteTotals

### Herd
#### Required
herd identity information
#### Optional
image references
custom rules updates
#### Forbidden
ownerId
memberCount
shepherdCount
lifecycleState
governanceState

### Membership
#### Required
herdId
#### Optional
none
#### Forbidden
memberId
membershipState

### Shepherd Assignment
#### Required
target member
#### Optional
none
#### Forbidden
ownerId
assignmentState

### Image
#### Required
image upload
#### Optional
none
#### Forbidden
ownerId
moderationState

### Report
#### Required
target entity
report reason
#### Optional
report context
#### Forbidden
reporterId
reportStatus
moderationOutcome
escalationState

### Moderation
#### Required
target identifier
moderation rationale
#### Optional
restriction reason
restriction duration
enforcement notes
#### Forbidden
moderatorId
moderationActionId creation
governance status fields

## Request Contract Validation

Validated Against:
- User Flows
- API Capability Model
- Resource Model
- CRUD Model
- Endpoint Inventory
- Authorization Boundaries
- Ownership Boundaries
- Aggregate Boundaries
- Lifecycle Boundaries
- Moderation Boundaries

Result:
- Complete
- No ownership violations
- No governance violations
- Ready for Response Contract Definition

---

# MVP Response Contract Model

## Response Contract Principles
### Principle 1 — Responses Expose Business Resources
Responses expose business concepts.

Responses do not expose:

database structures
implementation details
internal workflow state
infrastructure metadata

### Principle 2 — Public Discovery Is Preserved
Visitor flows require public visibility for:

User Profiles
Posts
Comments
Herds
Membership information
Shepherd information

Required by Visitor discovery flows.


### Principle 3 — Ownership Must Be Visible Where Participation Matters
Resources that represent user participation expose:

Author identity
Herd owner identity
Shepherd identity

unless governance rules explicitly restrict visibility.


### Principle 4 — Governance Data Is Need-To-Know
Governance resources expose different information depending on actor authority.

Public users never receive:

internal review details
enforcement rationale
escalation history
moderation notes

### Principle 5 — Derived Metrics Are First-Class Response Data
The following derived concepts are visible where relevant:

Vote Totals
Follower Count
Following Count
Membership Count
Shepherd Count
Aura

Derived concepts are approved MVP computed concepts.


### Principle 6 — Lifecycle State Visibility Is Explicit
Business-visible lifecycle state may be exposed when required for user decisions.

Examples:

Herd Restricted
Report Under Review
Membership Removed

### Principle 7 — Workflow Endpoints Return Outcomes, Not Resources
Workflow endpoints are not resource retrieval endpoints.

Examples:

Register
Login
Logout
Verify Email
Reset Password
Dismiss Report
Escalate Report

These return workflow outcomes rather than authoritative resource representations.

## Endpoint Response Classification Matrix
### Identity Workflow
| Endpoint                   | Classification   |
| -------------------------- | ---------------- |
| POST /auth/register        | Workflow Outcome |
| POST /auth/login           | Workflow Outcome |
| POST /auth/logout          | Workflow Outcome |
| GET /auth/me               | Single Resource  |
| POST /auth/verify-email    | Workflow Outcome |
| POST /auth/forgot-password | Workflow Outcome |
| POST /auth/reset-password  | Workflow Outcome |

Primary Resource:
- User Profile (GET /auth/me)

### User Profiles
| Endpoint                    | Classification      |
| --------------------------- | ------------------- |
| GET /profiles               | Resource Collection |
| GET /profiles/{id}          | Single Resource     |
| PATCH /profiles/{id}        | Single Resource     |
| GET /profiles/{id}/posts    | Resource Collection |
| GET /profiles/{id}/comments | Resource Collection |

Supporting Resources:
- Author Profile
- Profile Images
- Public Herd Memberships

Derived Information:
- Follower Count
- Following Count
- Aura
- Membership Count

### Follow Relationships
| Endpoint      | Classification          |
| ------------- | ----------------------- |
| GET followers | Relationship Collection |
| GET following | Relationship Collection |
| POST follow   | Workflow Outcome        |
| DELETE follow | Workflow Outcome        |

Primary Resource:
- Follow Relationship

Supporting Resources:
- User Profile

Derived:
- follower totals
- following totals

### Posts
| Endpoint           | Classification      |
| ------------------ | ------------------- |
| GET /posts         | Resource Collection |
| POST /posts        | Single Resource     |
| GET /posts/{id}    | Single Resource     |
| PATCH /posts/{id}  | Single Resource     |
| DELETE /posts/{id} | Workflow Outcome    |

Supporting Resources:
- Author Profile
- Herd Identity (if herd post)
- Image References

Derived:
- Vote Totals
- Comment Count

Lifecycle:
- Published
- Removed

### Comments
| Endpoint       | Classification      |
| -------------- | ------------------- |
| GET thread     | Resource Collection |
| POST comment   | Single Resource     |
| GET comment    | Single Resource     |
| PATCH comment  | Single Resource     |
| DELETE comment | Workflow Outcome    |
| POST reply     | Single Resource     |

Supporting Resources:
- Author Profile
- Parent Post
- Parent Comment

Derived:
- Vote Totals
- Reply Count

Relationship Visibility:
- Full comment hierarchy

Required by discussion flows.

### Votes
| Endpoint    | Classification     |
| ----------- | ------------------ |
| GET votes   | Derived Collection |
| PUT vote    | Workflow Outcome   |
| DELETE vote | Workflow Outcome   |

Visible:
- Vote Totals

Not Visible:
- Individual voter identities

Consistent with approved voting rules.

### Herds
| Endpoint              | Classification      |
| --------------------- | ------------------- |
| GET /herds            | Resource Collection |
| POST /herds           | Single Resource     |
| GET /herds/{id}       | Single Resource     |
| PATCH /herds/{id}     | Single Resource     |
| GET /herds/{id}/posts | Resource Collection |

Supporting Resources:
- Owner Profile
- Shepherd Profiles
- Image References

Derived:
- Membership Count
- Shepherd Count

Lifecycle:
- Active
- Restricted
- Closed

Visible Herd Identity Information:
- Name
- Description
- Rules
- Images

### Membership
| Endpoint          | Classification          |
| ----------------- | ----------------------- |
| GET members       | Relationship Collection |
| POST join         | Workflow Outcome        |
| DELETE membership | Workflow Outcome        |

Supporting Resources:
- User Profiles

Derived:
- Membership Count

### Shepherd Assignments
| Endpoint      | Classification          |
| ------------- | ----------------------- |
| GET shepherds | Relationship Collection |
| POST assign   | Workflow Outcome        |
| DELETE revoke | Workflow Outcome        |

Supporting Resources:
- Shepherd Profile
- Herd Identity

### Following Feed
| Endpoint             | Classification     |
| -------------------- | ------------------ |
| GET /feeds/following | Derived Collection |

Feed Entry Shape:
- Post
- Author Profile
- Image References
- Vote Totals
- Comment Count
- Publication Timestamp

### Herd Feed
| Endpoint         | Classification     |
| ---------------- | ------------------ |
| GET /feeds/herds | Derived Collection |

Feed Entry Shape:
- Post
- Author Profile
- Herd Identity
- Image References
- Vote Totals
- Comment Count

### Images
| Endpoint     | Classification   |
| ------------ | ---------------- |
| POST image   | Single Resource  |
| GET image    | Single Resource  |
| DELETE image | Workflow Outcome |

Visible:
- Image reference
- Ownership identity

Not Visible:
- storage internals

### Reports
| Endpoint    | Classification                 |
| ----------- | ------------------------------ |
| POST report | Workflow Outcome               |
| GET report  | Governance Resource            |
| GET reports | Governance Resource Collection |

Supporting Resources:
- Report Target
- Reporter (governance only)

Lifecycle:
- Submitted
- Under Review
- Escalated
- Resolved
- Dismissed

### Moderation Actions 
| Endpoint                                       | Classification      |
| ---------------------------------------------- | ------------------- |
| GET moderation-action                          | Governance Resource |
| All governance action endpoints                | Workflow Outcome    |
| POST /profiles/{profileId}/restrict            | Workflow Outcome    |
| POST /herds/{herdId}/restrict                  | Workflow Outcome    |
| POST /herds/{herdId}/members/{memberId}/remove | Workflow Outcome    |

Supporting Resources:
- Related Report
- Governed Resource

Lifecycle:
- Applied
- Reversed

## Resource Visibility Matrix
| Resource                  | Public | Authenticated         | Governance    |
| ------------------------- | ------ | --------------------- | ------------- |
| User Profile              | Yes    | Yes                   | Yes           |
| Follow Relationship Lists | Yes    | Yes                   | Yes           |
| Post                      | Yes    | Yes                   | Yes           |
| Comment                   | Yes    | Yes                   | Yes           |
| Vote Totals               | Yes    | Yes                   | Yes           |
| Vote Identities           | No     | No                    | Platform Only |
| Herd                      | Yes    | Yes                   | Yes           |
| Membership Lists          | Yes    | Yes                   | Yes           |
| Shepherd Assignments      | Yes    | Yes                   | Yes           |
| Following Feed            | No     | Yes                   | Yes           |
| Herd Feed                 | No     | Yes                   | Yes           |
| Image References          | Yes    | Yes                   | Yes           |
| Reports                   | No     | Reporter + Governance | Governance    |
| Moderation Actions        | No     | Limited               | Governance    |


## Ownership Visibility Matrix
| Ownership Information | Public | Authenticated | Governance |
| --------------------- | ------ | ------------- | ---------- |
| Post Author           | Yes    | Yes           | Yes        |
| Comment Author        | Yes    | Yes           | Yes        |
| Herd Owner            | Yes    | Yes           | Yes        |
| Shepherd Identity     | Yes    | Yes           | Yes        |
| Membership Identity   | Yes    | Yes           | Yes        |
| Reporter Identity     | No     | No            | Yes        |
| Moderator Identity    | No     | No            | Yes        |


## Lifecycle Visibility Matrix
| Entity              | Visible Lifecycle States                                |
| ------------------- | ------------------------------------------------------- |
| User Profile        | Active                                                  |
| Post                | Published, Removed                                      |
| Comment             | Published, Removed                                      |
| Herd                | Active, Restricted, Closed                              |
| Membership          | Active, Removed, Left                                   |
| Shepherd Assignment | Active, Revoked                                         |
| Report              | Submitted, Under Review, Escalated, Resolved, Dismissed |
| Moderation Action   | Applied, Reversed                                       |

## Moderation Visibility Matrix
| Information            | Public  | Reporter             | Shepherd/Herd Owner (Relevant Herd) | Platform Admin |
| ---------------------- | ------- | -------------------- | ----------------------------------- | -------------- |
| Content Removed        | Yes     | Yes                  | Yes                                 | Yes            |
| User Profile Restricted| Yes     | Yes                  | Limited                             | Yes            |
| Herd Restricted        | Yes     | Yes                  | Yes                                 | Yes            |
| Membership Removed     | Limited | Limited              | Yes                                 | Yes            |
| Report Existence       | No      | Own Reports Only     | Relevant Reports Only               | Yes            |
| Report Details         | No      | Own Reports Only     | Relevant Reports Only               | Yes            |
| Reporter Identity      | No      | Self Only            | Usually No                          | Yes            |
| Escalation History     | No      | No                   | Limited                             | Yes            |
| Enforcement Rationale  | No      | Outcome Summary Only | Limited                             | Yes            |
| Internal Notes         | No      | No                   | No                                  | Yes            |
| Moderator Notes        | No      | No                   | No                                  | Yes            |
| Governance Audit Trail | No      | No                   | No                                  | Yes            |


Governance Actors:
Shepherd
Herd Owner
Platform Administrator

per approved moderation hierarchy.

## Forbidden Response Data Matrix
### Identity Domain
Never Expose:

Password
Password Hash
Verification Token
Password Reset Token
Authentication Secrets
Intrnal Account Status Metadata

### Governance Domain
Never Expose:

Internal Moderation Notes
Internal Enforcement Rationale
Escalation Commentary
Investigation Metadata
Intrnal Governance Discussions

### System Domain
Never Expose:

Internal Audit Metadata
Internal Persistence Identifiers
Internal Storage Paths
Queue State
Cache State
Serice-Level Metadata

### Voting Domain
Never Expose:

Individual Vote Identities

Approved voting specification requires private vote identities.

## Response Contract Validation
| Area                     | Status |
| ------------------------ | ------ |
| User Flows               | Pass   |
| API Capability Model     | Pass   |
| Resource Model           | Pass   |
| CRUD Model               | Pass   |
| Endpoint Inventory       | Pass   |
| Authorization Boundaries | Pass   |
| Ownership Boundaries     | Pass   |
| Aggregate Boundaries     | Pass   |
| Lifecycle Boundaries     | Pass   |
| Moderation Boundaries    | Pass   |

---

# MVP Query & Pagination Standards
## Pagination Strategy Decision
### MVP Standard
Offset Pagination

Platform-wide standard:

?page={number}
&limit={number}

Rationale:

Simplest implementation.
Matches MVP simplicity objective.
Sufficient for projected MVP data volume.
Consistent across all collection endpoints.
Easier to document and consume.

### Future Consideration

If feed scale or performance requirements increase:

Feed endpoints may migrate to cursor pagination.
Collection contract should be designed so cursor metadata can be added later without breaking clients.

No cursor pagination is introduced in MVP.

## Query Design Principles
### Principle 1 — Platform-Wide Consistency
Collection endpoints use the same query model whenever possible.

### Principle 2 — Predictable Parameters
Parameter names must have identical meaning everywhere.

Example:
page
limit
sort
order
search

must never change meaning between endpoints.

### Principle 3 — Authorization-Aware Results
Filtering never bypasses authorization boundaries.

Returned results remain subject to approved authorization rules.

### Principle 4 — Query Parameters Refine Collections
Query parameters may refine collections.

They never change business ownership, lifecycle state, or governance authority.

### Principle 5 — Simplicity First
Only MVP-required filters are supported.

Future filtering capabilities remain out of scope.

### Principle 6 — Future Extensibility
Additional filters may be added later without changing existing parameter semantics.

## Pagination Design Principles
### Principle 1 — One Pagination Model
All MVP collection endpoints use the same pagination model.

### Principle 2 — Pagination Is Optional
When omitted:

page=1
limit=20

are assumed.

### Principle 3 — Stable Ordering Required
Pagination requires deterministic ordering.

Every paginated collection must define a default sort order.

### Principle 4 — Authorization Before Pagination
Authorization filtering occurs before pagination.

Unauthorized resources never contribute to page calculations.

## Standard Pagination Parameters
### Allowed Parameters
| Parameter | Purpose     |
| --------- | ----------- |
| page      | Page number |
| limit     | Page size   |

### Forbidden Parameters
| Parameter | Reason                            |
| --------- | --------------------------------- |
| cursor    | Cursor pagination not used in MVP |
| before    | Cursor pagination not used in MVP |
| after     | Cursor pagination not used in MVP |
| offset    | Internal implementation detail    |

### Defaults
page=1
limit=20
### Maximum
limit=100

Requests above 100 are rejected.

### Pagination Limits
Minimum page: 1

Minimum limit: 1

Maximum limit: 100

Requests exceeding the maximum limit are rejected.

### Invalid Pagination Values
The following are invalid:

page < 1
limit < 1
limit > maximum allowed limit

Invalid values result in a validation error.

## Standard Query Parameter Inventory
| Parameter  | Purpose                           | Category   |
|------------|-----------------------------------|------------|
| page       | Collection page number            | Pagination |
| limit      | Collection page size              | Pagination |
| sort       | Sort field                        | Sorting    |
| order      | Sort direction                    | Sorting    |
| search     | Text search                       | Filtering  |
| authorId   | Filter by author                  | Filtering  |
| herdId     | Filter by Herd                    | Filtering  |
| status     | Filter governance lifecycle state | Filtering  |

## Standard Sorting Model
### Allowed Directions
order=asc
order=desc
### Default Direction
order=desc
Newest first.

### Standard Sort Parameter
sort

### Profiles
Default:

sort=createdAt
order=desc

### Posts
Default:

sort=createdAt
order=desc

### Comments
Default:

sort=createdAt
order=asc

Rationale:

Discussion readability.

### Herds
Default:

sort=createdAt
order=desc

### Members
Default:

sort=joinedAt
order=desc

### Shepherds
Default:

sort=assignedAt
order=desc

### Reports
Default:

sort=createdAt
order=asc

Oldest unresolved reports reviewed first.

### Feeds
Default:

sort=createdAt
order=desc

Consistent with approved feed specifications.

## Standard Filtering Model
### MVP-Supported Filters
#### Text Search
Applicable:

GET /profiles
GET /posts
GET /herds

Parameter:

search

#### Author Filtering
Applicable:

GET /posts

Parameter:

authorId

#### Herd Filtering
Applicable:

GET /posts

Parameter:

herdId

#### Report Status Filtering
Applicable:

GET /reports

Parameter:

status

Allowed values:

submitted
under_review
escalated
resolved
dismissed

Lifecycle-aligned.

#### Future Filters
Not MVP:

date ranges
vote thresholds
follower counts
membership counts
moderation outcome filters
advanced governance filters

#### Forbidden Filters
Clients may not filter by:

ownership state
moderation authority
internal governance assignments
derived ranking scores
internal lifecycle transitions

## Feed Query Standards
### Following Feed
Endpoint:

GET /feeds/following

Rules:

Chronological ordering.
Newest eligible content first.
Pagination uses page/limit.
Refresh returns current first page.
No recommendations.
No ranking system.

Consistent with approved Following Feed requirements.

### Herd Feed
Endpoint:

GET /feeds/herds

Rules:

Chronological ordering.
Newest eligible content first.
Pagination uses page/limit.
Refresh returns current first page.
Joined Herd content only.

Consistent with approved Herd Feed consumption flows.

### Duplicate Prevention
- MVP does not guarantee duplicate-free pagination across refreshes.
- Clients should replace feed state when refreshing from page 1.

## Governance Query Standards
### Report Queue
Endpoint:

GET /reports

Supported filter:

status

### Escalated Review Queue
Endpoint:

GET /reports/escalated

Ordering:

createdAt asc

Oldest escalation first.

### Governance Visibility
Report visibility remains governed by approved authorization boundaries:

Reporter
Relevant Shepherd
Relevant Herd Owner
Platform Administrator

Unauthorized users cannot query governance collections.

## Collection Response Metadata Standard
All paginated collection responses include:
{
  "page": 1,
  "limit": 20,
  "totalCount": 125,
  "totalPages": 7,
  "hasNextPage": true,
  "hasPreviousPage": false
}

### MVP Metadata Fields
| Field           | Included |
| --------------- | -------- |
| page            | Yes      |
| limit           | Yes      |
| totalCount      | Yes      |
| totalPages      | Yes      |
| hasNextPage     | Yes      |
| hasPreviousPage | Yes      |
| nextCursor      | No       |
| previousCursor  | No       |

## Validation Results
### User Flows
Validated against:

Visitor discovery flows
Member feed consumption flows
Community participation flows
Governance review flows

No conflicts identified.

### Resource Model
Validated against:

Primary resources
Relationship resources
Derived resources
Governance resources

No resource-specific pagination exception required.

### Authorization Boundaries
Authorization filtering occurs before pagination and sorting.

No authorization conflicts identified.

### Lifecycle Model
Report filtering aligns with approved Report lifecycle states.

No lifecycle conflicts identified.

---

# MVP Error Contract Model

## Error Contract Principles
### Principle 1 — Consistency
All API failures must use the same response structure regardless of endpoint, resource, or domain.

The client should never need endpoint-specific error parsing logic.

### Principle 2 — Predictability
Identical error conditions must always produce:

Same HTTP status
Same error code
Same response structure

Example:

Unauthorized access must always return:

401 Unauthorized
AUTHENTICATION_REQUIRED

Never:

401
AUTH_REQUIRED

on one endpoint and:

401
LOGIN_REQUIRED

on another.

### Principle 3 — Simplicity
Error responses should expose only information required for client behavior.

Avoid:

stack traces
exception names
database details
infrastructure details

### Principle 4 — Security
Error responses must never reveal:

account existence
internal moderation data
report existence
authorization rules
database structure
implementation details

Consistent with approved governance visibility boundaries and authorization model.

### Principle 5 — Client Usability
Errors must provide enough information for clients to:

display messages
highlight invalid fields
retry requests
redirect users
handle governance restrictions

without custom endpoint logic.

### Principle 6 — Future Extensibility
New error codes may be added.

Existing error codes must remain stable.

Clients must be able to safely ignore unknown future error codes.

## Standard Error Response Structure
### Standard Error
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Post not found"
  }
}

### Required Fields
#### error.code
Machine-readable stable identifier.

Example:

"RESOURCE_NOT_FOUND"

#### error.message
Human-readable explanation.

Example:

"Post not found"

### Optional Fields
#### error.fields

Used only for validation failures.

{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "fields": {
      "displayName": [
        "Display name is required"
      ]
    }
  }
}

#### error.retryAfter

Used only for rate limiting.

{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Too many requests",
    "retryAfter": 60
  }
}

Seconds until retry.

### Forbidden Fields

Never expose:

stack
trace
exception
databaseError
internalCode
service
hostname
query
sql

Never expose implementation details.

## Error Classification Model
### Bad Request Errors
Status Code:
400 Bad Request

Purpose:
Returned when the platform cannot interpret the request.

Examples:
- Malformed JSON
- Invalid Content-Type
- Unsupported request encoding
- Corrupted request body

Principle:
400 Bad Request is reserved for request parsing failures.

Business validation failures use:
422 Validation Error

### Validation Errors
Input violates request contract.

Examples:

missing fields
invalid values
invalid pagination
invalid query parameters

### Authentication Errors
Identity cannot be verified.

Examples:

not logged in
invalid credentials
expired session
invalid reset token

### Authorization Errors
Identity verified.

Action not permitted.

Examples:

ownership violation
governance scope violation
herd authority violation

### Resource Errors
Requested resource unavailable.

Examples:

missing post
missing comment
missing herd
removed resource

### Conflict Errors
Request conflicts with current state.

Examples:

already following
already member
duplicate shepherd assignment
duplicate vote state

### Governance Errors
Governance workflow constraints violated.

Examples:

report already resolved
invalid moderation action
invalid escalation

### Rate Limiting Errors
Request exceeds allowed rate.

Examples:

excessive login attempts
excessive API usage

### Internal Errors
Unexpected platform failures.
Examples:

database unavailable
unexpected exception
infrastructure failure

## HTTP Status Code Standards
### Success Status Codes
#### 200 OK
Successful read/update/workflow retrieval.

#### 201 Created
Successful creation.

Examples:
- post created
- herd created
- report submitted

#### 204 No Content
Successful delete-like operations.

Examples:
- unfollow
- leave herd
- delete post
- delete comment

### Client Error Status Codes
#### 400 Bad Request
Malformed request.

Examples:

invalid JSON
malformed request body

#### 401 Unauthorized
Authentication failure.

Examples:

not logged in
expired session
invalid credentials

#### 403 Forbidden
Authenticated but not authorized.

Examples:

ownership violation
governance scope violation

#### 404 Not Found
Requested resource unavailable.

Examples:

post not found
comment not found
herd not found

Also used to prevent information disclosure where appropriate.

#### 409 Conflict
State conflict.

Examples:

already following
already member
duplicate shepherd assignment

#### 422 Unprocessable Entity
Validation failure.

Examples:

invalid field value
invalid pagination
invalid lifecycle transition

#### 429 Too Many Requests
Approved for MVP.

Rationale:

protects authentication workflows
protects public APIs
future-safe
industry standard

### Server Error Status Codes
#### 500 Internal Server Error
Unexpected platform failure.

#### 503 Service Unavailable
Temporary service outage.

Examples:

database unavailable
maintenance state

## Approved HTTP Status Code Standards

### HTTP Status Code Matrix
| Status | Category | Usage |
|----------|----------|----------|
| 400 | Bad Request | Malformed request syntax or unreadable payload |
| 401 | Authentication | Authentication required or invalid authentication |
| 403 | Authorization | Authenticated but not authorized |
| 404 | Resource | Resource unavailable or not visible |
| 409 | Conflict | Lifecycle or state conflict |
| 422 | Validation | Request validation failure |
| 429 | Rate Limiting | Rate limit exceeded |
| 500 | Internal | Unexpected platform error |
| 503 | Service Unavailable | Temporary platform unavailability |

### Status Codes Not Approved For MVP
Avoid:
402
405
406
408
410
412
415
451
No approved MVP requirement currently needs them.

## Validation Error Standards
### Status Code
422 Unprocessable Entity

Used for all request contract violations.

Consistent with approved Request Contract Model and Query & Pagination Standards.

### Error Code
VALIDATION_ERROR

### Standard Format
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "fields": {
      "displayName": [
        "Display name is required"
      ],
      "bio": [
        "Bio exceeds maximum length"
      ]
    }
  }
}

### Field-Level Error Reporting
Allowed only for validation failures.

Structure:

{
  "fieldName": [
    "message"
  ]
}

Supports future multiple validations per field.

### Multiple Validation Errors
All validation failures should be returned together.

Preferred:

{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "fields": {
      "title": [
        "Title is required"
      ],
      "content": [
        "Content is required"
      ]
    }
  }
}
Avoid fail-fast validation.

Improves client usability.

### Validation Coverage
Applies to:
missing required fields
invalid field values
invalid enum values
invalid query parameters
invalid sort values
invalid filter values
invalid pagination values
invalid lifecycle transitions

## Authentication Error Standards
### Status Code
401 Unauthorized

### Error Codes
#### Authentication Required
AUTHENTICATION_REQUIRED

Example:
Unauthenticated access to:

POST /posts
POST /comments
GET /feeds/*

#### Invalid Credentials
INVALID_CREDENTIALS

Used for login failures.

#### Session Expired
SESSION_EXPIRED

Used when authentication previously existed but is no longer valid.

#### Invalid Verification Token
INVALID_VERIFICATION_TOKEN

#### Invalid Password Reset Token
INVALID_PASSWORD_RESET_TOKEN

### Information Disclosure Restrictions

Never reveal:

email exists
email does not exist
account suspended
account deleted
password incorrect

Example:

Avoid:

{
  "error": {
    "code": "PASSWORD_INCORRECT"
  }
}

Use:

{
  "error": {
    "code": "INVALID_CREDENTIALS"
  }
}

## Authorization Error Standards
### Status Code
403 Forbidden

### Error Codes
#### Insufficient Permissions
INSUFFICIENT_PERMISSIONS

General authorization denial.

#### Ownership Violation
RESOURCE_OWNERSHIP_REQUIRED

Examples:

edit another user's post
delete another user's comment
edit another profile

Consistent with Ownership Boundaries and Authorization Matrix.

#### Herd Governance Scope Violation
HERD_GOVERNANCE_SCOPE_VIOLATION

Examples:

shepherd moderating outside assigned herd

#### Platform Governance Required
PLATFORM_GOVERNANCE_REQUIRED

Examples:

platform-only governance operation

### Visibility Rules
Never reveal:

existence of hidden moderation records
governance rationale
internal moderation scope

## Resource Error Standards
### Status Code
404 Not Found

### Error Codes
#### Resource Not Found
RESOURCE_NOT_FOUND

Examples:

post not found
comment not found
herd not found
profile not found

#### Relationship Not Found
RELATIONSHIP_NOT_FOUND

Examples:

follow relationship absent
membership absent

### Removed Content Behavior

Lifecycle Model defines:

Published → Removed
Active → Removed

for content entities.

Clients should not be able to distinguish:

does not exist
removed
moderated

through error responses.

Return:

404
RESOURCE_NOT_FOUND

This avoids governance information leakage.

### Governed Content Visibility

Removed content should not expose:

removed by shepherd
removed by owner
removed by platform

All return:

404 RESOURCE_NOT_FOUND

## Governance Error Standards
### Status Code
409 Conflict

Used when governance workflow state prevents action.

### Error Codes
#### Report Already Resolved
REPORT_ALREADY_RESOLVED

Consistent with Report lifecycle.

#### Report Already Dismissed
REPORT_ALREADY_DISMISSED
#### Invalid Moderation Action
INVALID_MODERATION_ACTION
#### Invalid Escalation
INVALID_ESCALATION

Examples:

escalation from terminal state
escalation outside governance path
#### Governance Scope Violation
GOVERNANCE_SCOPE_VIOLATION

### Visibility Requirements
Never expose:

report creator
report count
report details
moderator notes
internal review history

Consistent with governance visibility decisions already approved.

## Conflict Error Standards
### Status Code
409 Conflict
### Error Codes
#### Already Following
ALREADY_FOLLOWING

#### Already Member
ALREADY_MEMBER

#### Duplicate Vote State
DUPLICATE_VOTE_STATE

#### Duplicate Shepherd Assignment
DUPLICATE_SHEPHERD_ASSIGNMENT

### Conflict Principle
Conflict errors represent:
Valid Request
+
Valid Resource
+
Invalid Current State

## Rate Limiting Error Standards
### MVP Decision
Include 429

Approved.

Reasoning:

protects authentication workflows
protects public APIs
prevents abuse
standard HTTP behavior
future compatible

### Status Code
429 Too Many Requests

### Error Code
RATE_LIMIT_EXCEEDED
Format
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Too many requests",
    "retryAfter": 60
  }
}

### Retry Information
Expose:

retryAfter

Only.

Do not expose:

internal thresholds
algorithm
security rules

## Internal Error Standards
### Status Code
#### Unexpected Failure
500 Internal Server Error

Error Code:
INTERNAL_SERVER_ERROR

#### Temporary Platform Failure
503 Service Unavailable

Error Code:

SERVICE_UNAVAILABLE

### Response Example
{
  "error": {
    "code": "INTERNAL_SERVER_ERROR",
    "message": "An unexpected error occurred"
  }
}

### Security Requirements
Never expose:

stack trace
exception class
database name
query details
server details
internal identifiers

## Error Code Naming Convention
### Convention
UPPER_SNAKE_CASE

Examples:

VALIDATION_ERROR
AUTHENTICATION_REQUIRED
RESOURCE_NOT_FOUND
REPORT_ALREADY_RESOLVED
RATE_LIMIT_EXCEEDED

### Naming Rules
#### Rule 1
Use business terminology.

Good:

ALREADY_MEMBER

Bad:

MEMBERSHIP_CREATE_FAILED

#### Rule 2
Codes describe the problem.

Not implementation.

Good:

INVALID_CREDENTIALS

Bad:

JWT_VERIFICATION_FAILED

#### Rule 3
Codes Must Be Stable

Clients may rely on codes.

Never rename approved codes.

New codes may be added later.


## Error Contract Validation
### User Flows
Validated.

All flow failure scenarios supported.

### API Capability Model
Validated.

All capability categories covered:

Identity
Social Graph
Content
Community
Feed
Media
Governance

### Resource Model
Validated.

All exposed resources covered.

### Endpoint Inventory

Validated.

All endpoint types covered.

### Authorization Boundaries
Validated.

Authorization failures consistently map to:

403 Forbidden

and approved authorization codes.

### Request Contracts
Validated.

Input failures consistently map to:

422 VALIDATION_ERROR

### Response Contracts

Validated.

Error envelope remains separate from success response model.

### Query & Pagination Standards
Validated.

Invalid:

page
limit
sort
filter

all handled by validation contract.

### Lifecycle Model
Validated.

Lifecycle violations handled through:

409 Conflict

or governance-specific errors.

### Moderation Boundary Model
Validated.

Governed content does not leak moderation state.

---

# MVP Feed API Model
## Feed API Design Principles
### Principle 1 — Feed Remains A Derived Resource
The Feed resource remains a Derived Resource.

Feed does not represent a persisted business entity.

Feed composition is generated from existing business resources.

Consistent with the approved Resource Model.

### Principle 2 — Feed Remains Read Only
Feeds support retrieval only.

No Feed endpoint supports:

Create
Update
Delete

Consistent with the approved CRUD Model.

### Principle 3 — Feed Items Are Not Resources
Feed Items are response projections.

Feed Items:

Are not entities
Are not resources
Have no lifecycle
Have no independent endpoints

Consistent with the approved Resource Model.

### Principle 4 — Ranking Remains Internal
Ranking implementation is not exposed through the API.

The API exposes ordering behavior only.

Internal ranking calculations, scoring, and feed generation mechanisms remain implementation concerns.

### Principle 5 — Recommendation Is Out Of Scope
MVP feeds are eligibility-driven.

MVP feeds do not expose:

Recommendations
Discovery content
Suggested content
Personalized ranking
Algorithmic ranking

Consistent with approved Feed feature specifications.

## Feed Retrieval Model
### Following Feed
#### Purpose
Provide a content stream composed of eligible content from followed users.

#### Eligible Content
The Following Feed contains:

Personal Posts authored by followed users

Requirements:

Follow relationship must be active.
Author account must remain active.
Post must remain publicly visible.
Post must not be deleted.
Post must not be removed by moderation.

Consistent with Following Feed and Follow System specifications.

#### Not Eligible
The Following Feed must not contain:

Personal posts from non-followed users
Herd posts
Deleted posts
Moderation-removed posts
Restricted content
Recommended content
Discovery content
Advertisements

### Herd Feed
#### Purpose
Provide a content stream composed of eligible content from joined Herds.

#### Eligible Content
The Herd Feed contains:

Herd Posts created within Herds the member currently belongs to

Requirements:

Viewer must currently be a Herd member.
Herd must remain Active.
Post must remain publicly visible.
Post must not be deleted.
Post must not be removed by moderation.

Consistent with Herd Feed specifications.

#### Not Eligible
The Herd Feed must not contain:

Personal posts
Posts from Herds not joined
Deleted posts
Moderation-removed posts
Restricted content
Recommended content
Discovery content
Advertisements

Consistent with Herd Feed specifications.

## Feed Visibility Rules
### Following Feed
Access:

Authenticated Member+
Shepherd+
Herd Owner+
Platform Administrator+

Not Accessible To:

Visitors

Authorization Source:

Authenticated identity.

Consistent with Authorization Boundaries.

### Herd Feed
Access:

Authenticated Member+
Shepherd+
Herd Owner+
Platform Administrator+

Not Accessible To:

Visitors

Authorization Source:

Authenticated identity.

Consistent with Authorization Boundaries.

## Feed Composition Rules
### Included Information
Each Feed Item represents an eligible Post projection.

#### Post Information
postId
content
createdAt

#### Author Information
profileId
displayName
profileImage

#### Herd Information
Included only for Herd Feed:

herdId
herdName
herdImage

#### Image Information
Included when attached:

imageId
imageUrl

#### Derived Information
voteTotals
commentCount

Consistent with approved Response Contract principles requiring business-resource visibility and derived metric exposure.

### Excluded Information
Feed responses must not expose:

Internal ranking score
Recommendation source
Recommendation metadata
Governance history
Moderation notes
Report existence
Report details
Enforcement rationale
Internal ownership metadata
Internal lifecycle metadata
Internal system identifiers

Consistent with approved Response Contract and Governance visibility rules.

## Feed Ordering Rules 
### Following Feed Ordering
Authoritative MVP Ordering:

#### Newest First
Requirements:

Newer eligible content appears before older eligible content.
Ordering must be deterministic.
Ordering must remain stable within paginated results.

The Following Feed must not use:

Popularity ranking
Recommendation ranking
Engagement ranking
Aura ranking
Personalized ranking

Consistent with MVP Feed simplicity and approved Following Feed feature requirements.

### Herd Feed Ordering
Authoritative MVP Ordering:

#### Newest First
Requirements:

Newer eligible content appears before older eligible content.
Ordering must be deterministic.
Ordering must remain stable within paginated results.

The Herd Feed must not use:

Engagement ranking
Recommendation ranking
Aura ranking
Personalized ranking
Shepherd prioritization

Consistent with Herd Feed feature specification.

## Feed Query Standards
### Supported Query Parameters
| Parameter | Required | Type    |
| --------- | -------- | ------- |
| page      | No       | Integer |
| limit     | No       | Integer |

### Unsupported Parameters
The Feed APIs do not support:

sort
filter
search
cursor
before
after
offset

Rationale:
Feed ordering is fixed by Feed specifications.

Feed filtering and Feed search are explicitly postponed beyond MVP.

## Feed Pagination Behaviour
Pagination follows approved platform-wide Pagination Standards.

### Default Page Size

20

### Maximum Page Size

100

### Empty Page Behavior

Valid empty collection response.

Status:

200 OK

Example:

{
  "data": [],
  "pagination": {
    "page": 4,
    "limit": 20,
    "totalItems": 52,
    "totalPages": 3
  }
}

### End Of Feed Behavior
No special response.

Return:

200 OK
Empty data collection

### Pagination Guarantees
No duplicate Feed Items within a response.
Stable ordering across page retrieval.
Consistent pagination metadata.

## Following Feed API Specification
### Endpoint
GET /feeds/following

### Classification
Derived Resource

### Authorization
Member+

### Request Parameters
| Parameter | Required |
| --------- | -------- |
| page      | No       |
| limit     | No       |

### Response Classification
Resource Collection

### Response Contents
Collection of:

Personal Posts from followed users

Supporting Resources:
Author Profile
Attached Images

Derived Information:
Vote Totals
Comment Count

## Herd Feed API Specification
### Endpoint
GET /feeds/herds

### Classification
Derived Resource

### Authorization
Member+

### Request Parameters
| Parameter | Required |
| --------- | -------- |
| page      | No       |
| limit     | No       |

### Response Classification
Resource Collection

### Response Contents
Collection of:
Herd Posts from joined Herds

Supporting Resources:
Author Profile
Herd Information
Attached Images

Derived Information:
Vote Totals
Comment Count

## Feed Response Model
```json
{
  "data": [
    {
      "postId": "post_123",
      "content": "...",
      "createdAt": "2026-06-22T12:00:00Z",
      "author": {
        "profileId": "profile_123",
        "displayName": "Member",
        "profileImage": {}
      },
      "herd": {},
      "images": [],
      "voteTotals": {
        "hypeUp": 10,
        "hypeDown": 2
      },
      "commentCount": 5
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "totalItems": 250,
    "totalPages": 13
  }
}
```
Notes:
herd is omitted for Following Feed items.
Response shape follows approved Resource Collection standards.

## Feed Error Behavior
| Scenario                           | Status | Error Code              |
| ---------------------------------- | ------ | ----------------------- |
| Authentication Required            | 401    | AUTHENTICATION_REQUIRED |
| Invalid Page                       | 400    | INVALID_PAGE            |
| Invalid Limit                      | 400    | INVALID_LIMIT           |
| Unsupported Query Parameter        | 400    | INVALID_QUERY_PARAMETER |
| Feed Access Without Authentication | 401    | AUTHENTICATION_REQUIRED |
| Rate Limited                       | 429    | RATE_LIMIT_EXCEEDED     |
| Internal Failure                   | 500    | INTERNAL_ERROR          |
All error responses must follow the approved Error Contract Model.

## Feed Performance Constraints
Requirements:
Ordering must remain deterministic.
Pagination must remain consistent.
No duplicate Feed Items within a response.
Feed eligibility changes must be reflected on subsequent retrieval.
Moderation visibility changes must be reflected on subsequent retrieval.
Membership changes must be reflected on subsequent retrieval.
Follow relationship changes must be reflected on subsequent retrieval.

No implementation requirements are imposed regarding:
Caching
Feed generation
Storage strategy
Indexing

## Feed Validation Results
Validated Against:
API Domain Model
API Capability Model
Resource Model
CRUD Model
Endpoint Inventory
Authorization Boundaries
Request Contract Model
Response Contract Model
Query & Pagination Standards
Error Contract Model
Lifecycle Boundary Model
Moderation Boundary Model
User Flows MF-01 and MF-08

Validation Result:
Feed remains a Derived Resource.
Feed remains Read Only.
Feed Item remains a non-resource projection.
No new resources introduced.
No endpoint changes required.
No authorization conflicts detected.
No request contract conflicts detected.
No response contract conflicts detected.
No query contract conflicts detected.
No governance visibility violations detected.
Recommendation systems remain out of MVP scope.

--- 

# Moderation API Model (Part 1)
## Moderation API Design Principles
#### Principle 1 — Governance Is Workflow Driven
Moderation APIs exist to support governance workflows rather than generic resource management.

Governance decisions progress through:
Report Submission → Review → Moderation Action → Resolution

Moderation behavior must remain aligned with the approved governance lifecycle.

#### Principle 2 — Moderation Does Not Transfer Ownership
Moderation authority may affect visibility, participation, or access.

Moderation actions never transfer ownership of:
User Profiles
Posts
Comments
Images
Herds
Memberships

Ownership remains governed by the approved ownership boundary model.

#### Principle 3 — Governance Authority Follows Approved Hierarchy
Moderation authority follows the approved governance hierarchy:

Applicable Law
↓
Platform Administrator
↓
Herd Owner
↓
Shepherd

No moderation action may bypass the approved governance chain.

#### Principle 4 — Governance Scope Is Explicit
Governance actors may act only within their approved authority scope.

Examples:
Shepherd authority is limited to assigned Herds.
Herd Owner authority is limited to owned Herds.
Platform Administrator authority is platform-wide.

Authority scope must be enforced by all moderation endpoints.

#### Principle 5 — Visibility Is Need-To-Know
Governance information is visible only to actors who require access to perform governance responsibilities.

Moderation APIs must not expose:
Internal review notes
Governance deliberations
Escalation history
Enforcement rationale

unless explicitly authorized.

#### Principle 6 — Moderation Actions Must Be Auditable
All moderation actions must produce auditable governance records.

Governance records must preserve:
Action origin
Action target
Acting authority
Governance rationale
Lifecycle progression

Moderation Action is the authoritative enforcement record.

#### Principle 7 — Escalation Preserves Governance Chain
Escalation transfers review responsibility to a higher governance authority.

Escalation does not:
Resolve a report
Reverse a moderation action
Terminate governance review

Escalation exists solely to move review responsibility upward through the governance hierarchy.

#### Principle 8 — Reports And Enforcement Are Separate Concerns
Reports represent governance intake.

Moderation Actions represent governance enforcement.
A Report may:

Be dismissed
Produce one or more Moderation Actions
Be escalated

Governance intake and governance enforcement remain separate resources.

#### Principle 9 — Governance Actions Follow Lifecycle Rules
Moderation APIs must respect approved lifecycle states.

Examples:
Resolved Reports cannot re-enter normal review.
Dismissed Reports cannot receive new enforcement.
Reversed Moderation Actions remain part of governance history.

Lifecycle rules are authoritative.

#### Principle 10 — Higher Governance Authority May Override Lower Governance Authority
Higher governance authorities may review and override decisions made by lower governance authorities.

Examples:
Herd Owner may reverse Shepherd moderation outcomes.
Platform Administrator may reverse Herd Owner moderation outcomes.
Platform Administrator serves as final governance authority within the platform.

Governance overrides must create auditable Moderation Actions.

## Governance Resource Roles
### Report
#### Purpose
Report is the governance intake resource for suspected rule violations, policy violations, or governance concerns.

#### Responsibilities
Capture governance concerns.
Identify a governance target.
Record reporter-provided context.
Initiate moderation review.
Support governance escalation.

#### Lifecycle Role
Report progresses through:

Submitted → Under Review → Escalated → Resolved / Dismissed

Report is the authoritative lifecycle resource for governance review.

#### Relationship To Moderation
Report does not perform enforcement.

Report may result in:

No action
One Moderation Action
Multiple Moderation Actions

Report remains the governance review record.

### Moderation Action
#### Purpose
Moderation Action is the authoritative governance enforcement resource.

#### Responsibilities
Record governance decisions.
Record enforcement execution.
Preserve moderation audit history.
Support governance reversal workflows.
Support governance oversight.

#### Lifecycle Role
Moderation Action progresses through:

Proposed → Applied → Reversed

Moderation Action is the authoritative lifecycle resource for governance enforcement.

#### Relationship To Reports
Moderation Actions originate from governance review.

A Moderation Action may:

Be linked to a Report.
Affect one or more governed resources.
Be reviewed by higher governance authority.
Be reversed through approved governance workflows.

Moderation Action remains distinct from Report lifecycle management.

## Governance Authority Model
### Shepherd
#### Permitted Moderation Scope
Shepherd authority is limited to assigned Herds.

Permitted moderation targets:
Herd Posts
Herd Comments
Herd Images
Herd Memberships

#### Permitted Governance Actions
Review Reports
Dismiss Reports
Apply Community Moderation
Remove Herd Content
Remove Herd Members
Escalate Reports

#### Escalation Responsibilities
Shepherd must escalate matters that:
Exceed Herd-scoped authority
Require ownership-level review
Require platform-level review
Present governance conflicts

Escalation transfers review responsibility to the Herd Owner or Platform Administrator as appropriate.

### Herd Owner
#### Permitted Moderation Scope
Herd Owner authority applies to owned Herds.

Authority includes all Shepherd-scoped moderation responsibilities.

#### Override Responsibilities
Herd Owner may:
Review Shepherd decisions
Uphold Shepherd decisions
Reverse Shepherd decisions
Review escalated reports
Direct community governance outcomes

#### Dispute Resolution Responsibilities
Herd Owner serves as the primary community dispute resolution authority.

Responsibilities include:
Reviewing contested moderation outcomes
Resolving community governance disputes
Determining whether escalation is required
Escalating unresolved matters to Platform Administrators

### Platform Administrator
#### Platform-Wide Authority
Platform Administrator authority is platform-wide.

Authority applies to:
User Profiles
Posts
Comments
Images
Herds
Memberships
Reports
Moderation Actions

#### Final Enforcement Authority
Platform Administrator may:
Restrict Profiles
Restrict Herds
Expand Enforcement
Reverse Moderation Actions
Restore Governed Content
Resolve Escalations

Platform Administrator serves as the final governance authority within the platform.

#### Governance Oversight Responsibilities
Platform Administrators oversee:
Governance consistency
Shepherd conduct
Herd Owner conduct
Escalation handling
Platform policy enforcement

## Governance Visibility Model
### Report Visibility
| Actor                  | Visibility            |
| ---------------------- | --------------------- |
| Reporter               | Own Reports           |
| Shepherd               | Relevant Herd Reports |
| Herd Owner             | Relevant Herd Reports |
| Platform Administrator | All Reports           |
| General Members        | No Access             |
| Visitors               | No Access             |

Governance Rationale Visibility
Governance rationale is visible only to governance actors participating in the review process.

Internal Moderation Notes Visibility
Internal moderation notes are restricted to applicable governance authorities.

They are never visible to:
Reporter
Affected User
General Members
Visitors

### Moderation Action Visibility
| Actor                  | Visibility                           |
| ---------------------- | ------------------------------------ |
| Reporter               | Related Outcome Visibility Only      |
| Affected User          | Actions Affecting User Participation |
| Shepherd               | Relevant Herd Actions                |
| Herd Owner             | Relevant Herd Actions                |
| Platform Administrator | All Actions                          |
| General Members        | No Access                            |
| Visitors               | No Access                            |

Governance Rationale Visibility
Governance rationale is visible only to governance authorities responsible for review, enforcement, escalation, or oversight.

Internal Moderation Notes Visibility
Internal moderation notes are governance-only information.

They are never publicly exposed.

### Escalation Information Visibility
#### Visible To
Shepherd (participating review scope)
Herd Owner
Platform Administrator

#### Not Visible To
Visitors
General Members
Reporters
Affected Users
unless governance policy explicitly requires disclosure.

#### Governance Significance
Escalation information exists to preserve governance chain integrity and governance accountability.

## Governance State Model
### Report States
#### Submitted
Governance concern has been received.
No review activity has started.

#### Under Review
An authorized governance actor is actively evaluating the report.

#### Escalated
Review responsibility has been transferred to a higher governance authority.
The report remains unresolved.

#### Resolved
Governance review completed.
Required governance outcome has been determined.
Associated enforcement, if required, has been applied.
Terminal State.

#### Dismissed
Governance review completed.
No enforcement action is required.
Terminal State.

### Moderation Action States
#### Proposed
Governance review has determined enforcement should occur.
Enforcement has not yet been executed.

#### Applied
Enforcement has been executed and is active.
Terminal enforcement state unless governance review reverses the action.

#### Reversed
A higher governance authority has overturned a previously applied enforcement action.
Terminal State.
Governance history remains preserved.

## Moderation API Validation
### User Flow Validation
All approved moderation flows are supported.

### Governance Hierarchy Validation
No contradictions identified.

### Authorization Boundary Validation
No additional authority grants are required.
No endpoint authorization changes are required.

### Lifecycle Validation
No lifecycle changes are required.

### Endpoint Inventory Validation
No additional moderation endpoints are required.

### Missing Governance Concepts
None identified.

### Contradictions
None identified.

# Moderation API Model (Part 2A)
## Governance Query Principles
### Principle 1 — Governance Queries Are Visibility Constrained
Governance endpoints return only records visible to the requesting actor.
Authorization boundaries remain authoritative.

### Principle 2 — Governance Queries Use Platform Query Standards
Governance endpoints use the approved platform query model:
page
limit
sort
No governance-specific query conventions exist.

### Principle 3 — Lifecycle Filtering Uses Approved Lifecycle States
Governance queries may filter only using approved lifecycle states.
No endpoint may introduce new governance states.

### Principle 4 — Governance Queries Never Expand Authority
Query parameters may narrow results.
Query parameters may not expand governance authority.

## Report Queue Query Standards
### Endpoint

GET /reports

### Supported Query Parameters
| Parameter  | Purpose                     |
| ---------- | --------------------------- |
| page       | Pagination                  |
| limit      | Pagination                  |
| sort       | Collection ordering         |
| status     | Report lifecycle filtering  |
| targetType | Governance target filtering |

### Supported Status Values
Submitted
Under Review
Escalated
Resolved
Dismissed

### Supported Target Types
Post
Comment
User Profile
Herd

### Supported Sorting
| Value  | Meaning                     |
| ------ | --------------------------- |
| newest | Most recently created first |
| oldest | Oldest first                |

### Default Sorting
newest

## Escalated Report Queue Query Standards
### Endpoint
GET /reports/escalated

### Supported Query Parameters
| Parameter | Purpose             |
| --------- | ------------------- |
| page      | Pagination          |
| limit     | Pagination          |
| sort      | Collection ordering |

### Supported Sorting
| Value  | Meaning                       |
| ------ | ----------------------------- |
| newest | Most recently escalated first |
| oldest | Oldest escalated first        |

### Default Sorting
newest

### Filtering Behavior
Only reports currently in the Escalated lifecycle state are eligible.

## Governance Activity Query Standards
### Endpoint
GET /governance/activity

### Supported Query Parameters
| Parameter  | Purpose                     |
| ---------- | --------------------------- |
| page       | Pagination                  |
| limit      | Pagination                  |
| sort       | Collection ordering         |
| actionType | Moderation action filtering |

### Supported Action Types
Content Removal
Membership Removal
Profile Restriction
Herd Restriction
Enforcement Expansion
Content Restoration
Moderation Reversal

### Supported Sorting
| Value  | Meaning                    |
| ------ | -------------------------- |
| newest | Most recent activity first |
| oldest | Oldest activity first      |

### Default Sorting
newest

## Shepherd Oversight Query Standards
### Endpoint
GET /governance/shepherds

### Supported Query Parameters
| Parameter | Purpose             |
| --------- | ------------------- |
| page      | Pagination          |
| limit     | Pagination          |
| sort      | Collection ordering |

### Supported Sorting
| Value  | Meaning                               |
| ------ | ------------------------------------- |
| newest | Most recent governance activity first |
| oldest | Oldest governance activity first      |

### Default Sorting
newest

## Herd Owner Oversight Query Standards
### Endpoint
GET /governance/herd-owners

### Supported Query Parameters
| Parameter | Purpose             |
| --------- | ------------------- |
| page      | Pagination          |
| limit     | Pagination          |
| sort      | Collection ordering |

### Supported Sorting
| Value  | Meaning                               |
| ------ | ------------------------------------- |
| newest | Most recent governance activity first |
| oldest | Oldest governance activity first      |

### Default Sorting
newest

## Pagination Specifications
### Applicable Collections
Pagination applies to:
Report collections
Escalated report collections
Governance activity collections
Shepherd oversight collections
Herd Owner oversight collections
### Pagination Parameters
| Parameter | Purpose                  |
| --------- | ------------------------ |
| page      | Collection page number   |
| limit     | Maximum records returned |

Pagination behavior must follow approved platform-wide standards.

### Collection Metadata

All paginated governance collections return:
| Field      | Purpose                |
| ---------- | ---------------------- |
| page       | Current page           |
| limit      | Applied page size      |
| totalItems | Total matching records |
| totalPages | Total available pages  |

### Ordering Guarantees

Governance collections must provide deterministic ordering.

Identical queries must return identical ordering when underlying data has not changed.

### Deterministic Pagination Rules
Rule 1 — Sorting Occurs Before Pagination
Ordering is applied before page boundaries are calculated.

Rule 2 — Stable Ordering Is Required
Governance collections must always produce stable ordering for identical query inputs.

Rule 3 — Pagination Never Alters Visibility
Pagination limits visible records.
Pagination does not alter authorization scope.

Rule 4 — Pagination Never Alters Lifecycle State
Pagination affects retrieval only.
Lifecycle behavior remains unchanged.

Rule 5 — Pagination Never Alters Governance Authority
Pagination is a retrieval concern only.
Governance authority remains governed by authorization boundaries.

## Governance Collection Response Shape
### Report Collections
Return:
Report resources
Pagination metadata

### Escalated Report Collections
Return:
Escalated Report resources
Pagination metadata

### Governance Activity Collections
Return:
Moderation Action resources
Pagination metadata

### Governance Actor Collections
Return:
Governance actor resources
Pagination metadata

# Moderation API Model (Part 2B)
## Reporting API Specifications
### Reporting API Design Principles
#### Principle 1 — Reports Are Governance Intake Objects
Reports represent requests for governance review.
Reports do not directly perform moderation.
Moderation outcomes are represented by Moderation Actions.

#### Principle 2 — Reports Are Immutable After Submission
Report content cannot be edited after creation.
Report lifecycle changes occur through governance workflows only.

#### Principle 3 — Reports Never Grant Governance Authority
Submitting a report creates governance visibility.
Submitting a report does not create governance authority.

#### Principle 4 — Reports Are Visibility Constrained
Report visibility is governed by approved moderation visibility rules.
Authorization remains authoritative.

#### Principle 5 — Report State Is System Controlled
Clients may not create or modify:
report status
escalation status
moderation outcome
Governance workflows control lifecycle progression.

### Report Resource Representation
Report Fields
| Field      | Description                        |
| ---------- | ---------------------------------- |
| reportId   | Unique report identifier           |
| targetType | Type of governed target            |
| targetId   | Identifier of governed target      |
| reason     | Report reason                      |
| context    | Optional reporter explanation      |
| status     | Current report lifecycle state     |
| createdAt  | Report creation timestamp          |
| updatedAt  | Last governance activity timestamp |

#### Supported Target Types
Reports may target:
Post
Comment
User Profile
Herd
Consistent with approved governance coverage validation.

#### Report Lifecycle States
Supported states:
Submitted
Under Review
Escalated
Resolved
Dismissed
Lifecycle definitions remain governed by the approved lifecycle model.

## POST /reports
### Purpose
Submit a governance report.

### Authorization
Allowed:
Member
Shepherd
Herd Owner
Platform Administrator

Not Allowed:
Visitor

### Request Requirements
#### Required Fields
| Field      | Description                |
| ---------- | -------------------------- |
| targetType | Governed target type       |
| targetId   | Governed target identifier |
| reason     | Report reason              |

#### Optional Fields
| Field   | Description               |
| ------- | ------------------------- |
| context | Additional report context |

#### Forbidden Fields
reporterId
reportStatus
escalationStatus
moderationOutcome
createdAt
updatedAt

### Processing Rules
#### Rule 1 — Reporter Identity Is Derived
Reporter identity is derived from authenticated identity.

#### Rule 2 — Target Must Exist
Report creation requires an existing governed target.

#### Rule 3 — Lifecycle State Is Assigned By System
New reports are created in:
Submitted
state.

#### Rule 4 — Ownership Is Not Evaluated
Any authenticated participant may report an eligible target.

### Success Outcome
Creates a new Report resource.
Initial lifecycle state:
Submitted

### Error Conditions
| Condition           | Error |
| ------------------- | ----- |
| Unauthenticated     | 401   |
| Unauthorized Actor  | 403   |
| Target Not Found    | 404   |
| Invalid Target Type | 400   |
| Invalid Request     | 400   |

## GET /reports/{reportId}
### Purpose
Retrieve a specific report.

### Authorization
Visible to:
Reporter
Relevant Governance Actors
Platform Administrator

Visibility remains governed by moderation visibility rules.

### Response Contents
May include:

reportId
targetType
targetId
reason
context
status
createdAt
updatedAt

Subject to visibility restrictions.

### Error Condition
| Condition             | Error |
| --------------------- | ----- |
| Unauthenticated       | 401   |
| Visibility Restricted | 403   |
| Report Not Found      | 404   |

## GET /reports
### Purpose
Retrieve report review queues.

### Authorization
Available only to governance actors with report review authority.

### Query Behavior
Governed by:
Governance Query Standards (Part 2A)
Including:
page
limit
sort
status
targetType

### Response Contents
Returns:

Report collection
Pagination metadata

### Queue Visibility Rules
#### Shepherd
May view reports relevant to assigned Herds.

#### Herd Owner
May view reports relevant to owned Herds.

#### Platform Administrator
May view all reports.

### Error Conditions
| Condition       | Error |
| --------------- | ----- |
| Unauthenticated | 401   |
| Unauthorized    | 403   |
| Invalid Query   | 400   |

## Report Visibility Rules
### Reporter Visibility
Reporter may view:
Own reports
Report lifecycle status
Final outcome status

Reporter may not view:
Internal governance notes
Moderator notes
Governance audit history

### Governance Visibility
Governance actors may view reports within their authority scope.
Visibility never expands governance authority.

### Public Visibility
Reports are never publicly visible.

## Report State Transition Authority
| Transition               | Authority                 |
| ------------------------ | ------------------------- |
| Submitted → Under Review | Relevant Governance Actor |
| Under Review → Escalated | Shepherd / Herd Owner     |
| Under Review → Resolved  | Relevant Governance Actor |
| Under Review → Dismissed | Relevant Governance Actor |
| Escalated → Under Review | Receiving Authority       |
| Escalated → Resolved     | Receiving Authority       |
| Escalated → Dismissed    | Receiving Authority       |

## Reporting API Validation
Validated Against:
Domain Model
Resource Model
CRUD Model
Endpoint Inventory
Authorization Boundaries
Request Contracts
Response Contracts
Query & Pagination Standards
Lifecycle Model
Moderation Boundary Model

Validation Result:
Complete
No governance inconsistencies identified
No lifecycle inconsistencies identified
No authorization inconsistencies identified

# Moderation API Model (Part 2C)
## Community Governance Workflow APIs
### Community Governance Workflow Principles
#### Principle 1 — Reports Drive Governance Review
All community moderation workflows begin with a Report.
Governance actions must reference an existing report.

#### Principle 2 — Moderation Actions Represent Enforcement
Enforcement outcomes are represented through Moderation Actions.
Reports do not directly perform enforcement.

#### Principle 3 — Governance Authority Remains Scoped
Shepherd authority is limited to assigned Herds.
Herd Owners may override Shepherd decisions within owned Herds.
Platform Administrators retain platform-wide authority.
Consistent with approved governance hierarchy.

#### Principle 4 — Report Lifecycle And Moderation Lifecycle Remain Separate
Report Lifecycle:
Submitted
Under Review
Escalated
Resolved
Dismissed

Moderation Action Lifecycle:
Proposed
Applied
Reversed
The two lifecycles remain independent.

#### Principle 5 — Governance Decisions Must Be Auditable
Every dismissal, moderation action, and escalation must create governance history.
Governance history remains internal.

## POST /reports/{reportId}/dismiss
### Purpose
Dismiss a report without applying moderation.

### Authorization
Allowed:
Shepherd (relevant Herd)
Herd Owner (relevant Herd)
Platform Administrator

Not Allowed:
Visitor
Member

### Processing Rules
#### Rule 1 — Report Must Be Active
Allowed report states:
Submitted
Under Review
Escalated

Not Allowed:
Resolved
Dismissed

#### Rule 2 — No Moderation Action Created
Dismissal closes governance review.
No Moderation Action is created.

#### Rule 3 — Report State Updated
Final report state:
Dismissed

### Success Outcome
Returns workflow outcome.
Report lifecycle becomes:
Dismissed

### Error Conditions
| Condition               | Error |
| ----------------------- | ----- |
| Unauthorized            | 403   |
| Report Not Found        | 404   |
| Invalid Lifecycle State | 409   |

## POST /reports/{reportId}/moderate
### Purpose
Apply moderation based on report review.

### Authorization
Allowed:
Shepherd (relevant Herd)
Herd Owner (relevant Herd)
Platform Administrator

### Request Body
#### Required
| Field      | Description            |
| ---------- | ---------------------- |
| actionType | Moderation action type |
| rationale  | Governance rationale   |

#### Optional
| Field    | Description          |
| -------- | -------------------- |
| duration | Restriction duration |
| notes    | Enforcement notes    |

#### Forbidden
moderatorId
actionId
reportStatus
moderationStatus

### Supported Moderation Actions
#### Content Actions
Remove Post
Remove Comment

#### Membership Actions
Remove Herd Member

#### Community Actions
Restrict Herd

#### Identity Actions
Restrict Profile
These actions correspond to approved governance capabilities and endpoints.

### Processing Rules
#### Rule 1 — Moderation Action Created
System creates:
Moderation Action
resource.

#### Rule 2 — Moderation Action Applied
Initial moderation lifecycle state:
Applied

#### Rule 3 — Report Resolved
Associated report lifecycle becomes:
Resolved

#### Rule 4 — Authority Scope Validation
Governance actor must possess authority over target resource.

### Success Outcome
Returns:
moderationActionId
moderationActionState
reportState

### Error Conditions
| Condition               | Error |
| ----------------------- | ----- |
| Unauthorized            | 403   |
| Report Not Found        | 404   |
| Invalid Action Type     | 400   |
| Invalid Lifecycle State | 409   |

## POST /reports/{reportId}/escalate
### Purpose
Escalate a report to a higher governance authority.

### Authorization
Allowed:
Shepherd
Herd Owner

Not Allowed:
Member
Visitor
Platform Administrators do not escalate matters.
They are the final governance authority.

### Processing Rules
#### Rule 1 — Escalation Must Follow Governance Hierarchy
Allowed escalation paths:
Shepherd → Herd Owner
Herd Owner → Platform Administrator

#### Rule 2 — Report State Updated
Report lifecycle becomes:
Escalated

#### Rule 3 — No Moderation Action Created
Escalation transfers review authority.
It does not apply enforcement.

#### Rule 4 — Escalation History Recorded
Governance escalation history is recorded internally.

### Success Outcome
Returns workflow outcome.
Report lifecycle becomes:
Escalated

### Error Conditions
| Condition               | Error |
| ----------------------- | ----- |
| Unauthorized            | 403   |
| Report Not Found        | 404   |
| Invalid Lifecycle State | 409   |
| Invalid Escalation Path | 403   |

## GET /reports/escalated
### Purpose

Retrieve reports requiring higher-level review.

### Authorization
#### Herd Owner
May retrieve:
Reports escalated from Shepherds within owned Herds.

#### Platform Administrator
May retrieve:
Reports escalated to platform governance.

### Query Behavior
Governed by:
Governance Query Standards (Part 2A)

Supported filters:
status
targetType
sort
order
page
limit

### Response Contents
Returns:
Report collection
Pagination metadata
Subject to governance visibility rules.

### Queue Visibility Rules
#### Herd Owner Queue
Contains:
Escalated reports requiring community-owner review.

#### Platform Administrator Queue
Contains:
Escalated reports requiring platform review.

### Error Conditions
| Condition     | Error |
| ------------- | ----- |
| Unauthorized  | 403   |
| Invalid Query | 400   |

## Governance Workflow Validation
Validated Against:
Governance Domain Model
Resource Model
CRUD Model
Endpoint Inventory
Authorization Boundaries
Request Contracts
Response Contracts
Governance Query Standards
Lifecycle Boundary Model
Moderation Boundary Model

Validation Result:
Complete
Consistent with governance hierarchy
Consistent with lifecycle model
Consistent with moderation boundary model
No additional endpoints required

# Moderation API Model (Part 2D)
## Enforcement API Specifications
### Enforcement Design Principles
#### Principle 1 — Enforcement Requires Authority
Only authorized governance actors may execute enforcement.

#### Principle 2 — Enforcement Produces A Moderation Action
Every enforcement action creates or operates on a Moderation Action.

#### Principle 3 — Enforcement Changes Lifecycle State
Enforcement affects governed resources through lifecycle transitions.

#### Principle 4 — Enforcement Never Transfers Ownership
Ownership remains unchanged.

#### Principle 5 — Enforcement Is Auditable
Every enforcement action must be reviewable by higher governance authority.

## Content Enforcement
### POST /posts/{postId}/remove
#### Purpose
Remove a governed post.

#### Authorization
Shepherd (relevant Herd)
Herd Owner (relevant Herd)
Platform Administrator

#### Required Inputs
moderation rationale

#### Optional Inputs
enforcement notes

#### Forbidden Inputs
moderatorId
lifecycleState
moderationActionId

#### Processing Rules
System:
Validate authority.
Create Moderation Action.
Associate target Post.
Apply enforcement.

#### Lifecycle Effect
Published
    ↓
Removed

#### Moderation Action Effect
Proposed
    ↓
Applied

#### Success Outcome
Post removed.
Moderation Action created.

#### Error Conditions
Unauthorized
Post not found
Already removed

### POST /comments/{commentId}/remove
Identical behavior to post removal.

#### Lifecycle Effect
Published
    ↓
Removed

## Profile Enforcement
### POST /profiles/{profileId}/restrict
#### Purpose
Restrict profile participation.

#### Authorization
Platform Administrator only.

#### Required Inputs
moderation rationale

#### Optional Inputs
restriction reason
restriction duration

#### Forbidden Inputs
profile lifecycle state
moderatorId

#### Processing Rules
System:
Validate platform authority.
Create Moderation Action.
Apply profile restriction.

#### Lifecycle Effect
Profile remains active projection.
Underlying account governance restrictions become effective.

#### Moderation Action Effect
Proposed
    ↓
Applied

#### Success Outcome
Profile restricted.

## Community Enforcement
### POST /herds/{herdId}/restrict
#### Purpose
Restrict community participation.

#### Authorization
Platform Administrator.

#### Required Inputs
moderation rationale

#### Optional Inputs
restriction duration
restriction reason

#### Forbidden Inputs
herd lifecycle state
moderatorId

#### Lifecycle Effect
Active
    ↓
Restricted

#### Success Outcome
Herd becomes restricted.

## Membership Enforcement
### POST /herds/{herdId}/members/{memberId}/remove
#### Purpose
Remove member from Herd.

#### Authorization
Shepherd
Herd Owner
Platform Administrator
Scope rules apply.

#### Required Inputs
moderation rationale

#### Optional Inputs
enforcement notes

#### Forbidden Inputs
membership state
moderatorId

#### Lifecycle Effect
Active
    ↓
Removed

#### Success Outcome
Membership removed.
Moderation Action created.

## Enforcement Review APIs
### POST /moderation-actions/{actionId}/uphold
#### Purpose
Confirm existing moderation decision.

#### Authorization
Higher governance authority.
Examples:
Shepherd Decision
    → Herd Owner Uphold

Herd Owner Decision
    → Platform Admin Uphold

#### Processing Rules
No lifecycle change.
Decision remains valid.

#### Moderation Action Effect
No state change.
Audit trail updated.

#### Success Outcome
Outcome upheld.

### POST /moderation-actions/{actionId}/reverse
#### Purpose
Overturn moderation decision.

#### Authorization
Higher governance authority.

#### Processing Rules
Validate authority.
Reverse enforcement.
Update moderation action.

#### Moderation Action Effect
Applied
    ↓
Reversed

#### Success Outcome
Decision overturned.

### POST /moderation-actions/{actionId}/restore
#### Purpose
Restore governed content after reversal.

#### Authorization
Platform Administrator.

#### Supported Targets
Post
Comment

#### Lifecycle Effects
Post
Removed
    ↓
Published
Comment
Removed
    ↓
Published
#### Success Outcome
Content restored.

### POST /moderation-actions/{actionId}/expand
#### Purpose
Increase enforcement scope.
Example:
Remove Post
      ↓
Restrict Profile
or
Restrict Profile
      ↓
Restrict Herd

#### Authorization
Platform Administrator.

#### Required Inputs
expansion rationale

#### Optional Inputs
additional enforcement scope

#### Forbidden Inputs
moderatorId
moderation lifecycle fields

#### Processing Rules
Existing moderation action reviewed.
Additional enforcement applied.
Additional moderation action created.

#### Success Outcome
Enforcement scope expanded.

---

# Moderation API MOdel (Part 2E) 
## Governance Oversight APIs
### Governance Oversight Design Principles
#### Principle 1 — Oversight Is Read Only
Oversight endpoints never execute moderation.

#### Principle 2 — Oversight Reviews Governance Behavior
Focus is governance activity rather than governed content.

#### Principle 3 — Oversight Respects Visibility Rules
Visibility remains governed by approved moderation visibility policies.

#### Principle 4 — Oversight Supports Accountability
Governance actors must remain reviewable by higher authority.

#### Principle 5 — Oversight Does Not Create New Governance State
Oversight APIs expose governance information only.

### Governance Activity Review
#### GET /governance/activity
##### Purpose
Review governance activity occurring across the platform.

##### Authorization
Platform Administrator only.

##### Supported Query Parameters
page
limit
sort
order
status
Consistent with governance query standards.

##### Default Sorting
sort=createdAt
order=desc
Newest governance activity first.

##### Returned Information
May include:
Report identifier
Moderation action identifier
Governance actor type
Governance action type
Governed resource type
Governance outcome
Timestamp

##### Must Not Include
Internal notes
Investigation notes
Audit trail details
Internal governance discussions

##### Success Outcome
Governance activity collection returned.

### Shepherd Conduct Review
#### GET /governance/shepherds
##### Purpose
Review Shepherd governance behavior.

##### Authorization
Platform Administrator only.

#### Supported Query Parameters
page
limit
search
herdId

##### Returned Information
May include:
Shepherd identity
Assigned Herds
Active assignments
Moderation actions performed
Reports reviewed
Escalations initiated

##### Derived Information
May include:
Total moderation actions
Total reports reviewed
Total escalations

##### Must Not Include
Internal moderation notes
Investigation commentary

##### Success Outcome
Governance review collection returned.

### Herd Owner Conduct Review
#### GET /governance/herd-owners
##### Purpose
Review Herd Owner governance activity.

##### Authorization
Platform Administrator only.

#### Supported Query Parameters
page
limit
search
herdId

##### Returned Information
May include:
Herd Owner identity
Owned Herds
Shepherd appointments
Escalation resolutions
Moderation reversals
Governance actions performed

##### Derived Information
May include:
Herd count
Shepherd count
Governance action count

##### Must Not Include
Internal governance discussions
Internal moderation notes

##### Success Outcome
Governance review collection returned.

### Governance Oversight Visibility Model
#### Platform Administrator
Full access to governance oversight endpoints.

##### Accessible
Governance activity
Shepherd conduct
Herd Owner conduct
Governance outcomes
Governance history summaries

##### Restricted
Internal moderation notes
Internal investigations
Internal governance discussions

#### Herd Owner
Does not access governance oversight endpoints.
Uses:
GET /reports
GET /reports/escalated
GET /moderation-actions/{actionId}
for community governance oversight.

#### Shepherd
Does not access governance oversight endpoints.
Uses community governance workflows only.

#### Members
No governance oversight access.

### Response Model Requirements
#### Governance Activity Entry
May expose:
activityId
activityType
actorType
resourceType
outcome
createdAt

#### Shepherd Review Entry
May expose:
profileId
assignedHerds
reportsReviewed
moderationActions
escalationsCreated

#### Herd Owner Review Entry
May expose:
profileId
ownedHerds
shepherdAssignments
reversalsPerformed
escalationsResolved

### Error Behavior
#### 401 Unauthorized
Unauthenticated request.

#### 403 Forbidden
Authenticated actor lacks Platform Administrator authority.

#### 422 Validation Error
Invalid query parameters.

#### 429 Too Many Requests
Rate limiting.

### Validation
#### Capability Validation
| Capability                 | Status |
| -------------------------- | ------ |
| Review Governance Activity | Pass   |
| Review Shepherd Conduct    | Pass   |
| Review Herd Owner Conduct  | Pass   |

#### User Flow Validation
| Flow                                | Status |
| ----------------------------------- | ------ |
| PAF-04 Oversee Community Governance | Pass   |
| HOJ-05 Community Oversight          | Pass   |
| HOJ-06 Governance Escalation        | Pass   |


#### Endpoint Inventory Validation
Validated against approved governance oversight endpoints.

# Platform Governance Workflow APIs
## Governance Workflow Principles
### Principle 1 — Higher Authority Review
Platform Governance Workflow endpoints exist to review existing moderation outcomes.

These endpoints do not create initial moderation decisions.

### Principle 2 — Governance Hierarchy Enforcement
A governance actor may only review moderation outcomes within approved authority boundaries.

Higher authority may override lower authority.

Lower authority may not override higher authority.

### Principle 3 — Auditability Required
Every governance workflow action must generate a governance audit record.

Governance review actions must remain traceable.

### Principle 4 — Lifecycle Consistency
Governance workflow actions must not create invalid moderation lifecycle transitions.

### Principle 5 — Visibility Restrictions Remain Enforced
Governance review does not expand visibility rights.

Approved visibility rules remain authoritative.

## POST /moderation-actions/{actionId}/uphold
### Purpose
Confirm that an existing moderation outcome remains valid.

Represents governance agreement with a previously applied moderation action.

### Authorization
Platform Administrator

Herd Owner may uphold moderation outcomes originating from Shepherd authority within their own Herd.

Lower authority may not uphold decisions made by higher authority.

Consistent with Governance Override Matrix.

### Required Inputs
Path Parameters:

actionId

### Optional Inputs
None.

### Forbidden Inputs
moderationOutcome
lifecycleState
moderatorId
governanceState

### Processing Rules
Retrieve Moderation Action.
Validate governance authority.
Validate moderation action exists.
Validate moderation action is reviewable.
Record governance review outcome.
Preserve existing moderation outcome.

### Governance Validation Rules
Must verify:

Moderation Action exists.
Reviewing authority is higher or equal authority.
Review scope is valid.
Action has not already been reversed.

### Visibility Rules
No visibility expansion.

Existing visibility rules remain unchanged.

### Lifecycle Effects
No lifecycle transition occurs.

Moderation Action remains:

Applied

### Moderation Action Effects
No enforcement changes occur.

Original moderation outcome remains active.

### Audit Requirements
Audit record must capture:

actionId
reviewActor
reviewType=uphold
timestamp

### Success Outcome
Moderation outcome confirmed.

### Error Conditions
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict

## POST /moderation-actions/{actionId}/reverse
### Purpose
Overturn an existing moderation outcome.

Represents governance disagreement with a previously applied moderation action.

### Authorization
Platform Administrator

Herd Owner may reverse moderation outcomes originating from Shepherd authority within the same Herd.

Lower authority may not reverse higher authority decisions.

### Required Inputs
Path Parameters:

actionId

### Optional Inputs
None.

### Forbidden Inputs
newLifecycleState
newAuthorityLevel
moderatorId

### Processing Rules
Retrieve Moderation Action.
Validate authority.
Validate action is reversible.
Apply governance reversal.
Update moderation lifecycle.

### Governance Validation Rules
Must verify:

Action currently Applied.
Action not previously reversed.
Reviewing authority exceeds or equals originating authority.
Governance scope remains valid.

### Visibility Rules
Governance rationale visibility remains restricted.

Internal review information remains hidden.

### Lifecycle Effects
Applied → Reversed

Only valid moderation lifecycle transition.

Consistent with approved lifecycle model.

### Moderation Action Effects
Original enforcement becomes inactive.

### Audit Requirements
Audit record must capture:

actionId
reviewActor
reviewType=reverse
timestamp

### Success Outcome
Moderation outcome reversed.

### Error Conditions
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict

## POST /moderation-actions/{actionId}/restore
### Purpose
Restore previously governed content after moderation reversal review.

### Authorization
Platform Administrator only.

### Required Inputs
Path Parameters:

actionId

### Optional Inputs
None.

### Forbidden Inputs
targetId
targetType
contentState

### Processing Rules
Retrieve Moderation Action.
Validate governed resource.
Validate restoration eligibility.
Restore governed content.

### Governance Validation Rules
Restoration is allowed only when:

Moderation Action has been reversed.
Governed resource still exists.
Resource lifecycle supports restoration.

### Restoration Eligibility Rules
Eligible:

Post
Comment
Image

Potentially eligible because approved lifecycle model explicitly permits governance restoration.

Not Eligible:

Herd Membership
Shepherd Assignment
User Profile Restriction
Herd Restriction

These require new governance actions rather than content restoration.

### Visibility Rules
Restored content follows normal visibility rules.

No governance information becomes public.

### Lifecycle Effects
Governed resource returns to normal participation state.

Moderation Action remains:

Reversed

No new moderation lifecycle state created.

### Moderation Action Effects
Previously removed content becomes visible again.

### Audit Requirements
Audit record must capture:

actionId
reviewActor
reviewType=restore
timestamp

### Success Outcome
Governed content restored.

### Error Conditions
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Validation Error

## POST /moderation-actions/{actionId}/expand
### Purpose
Increase enforcement scope after platform governance review.

### Authorization
Platform Administrator only.

### Required Inputs
Path Parameters:

actionId

Request Body:

expansionType
expansionReason

### Optional Inputs
restrictionDuration
enforcementNotes

### Forbidden Inputs
moderatorId
governanceState
reportStatus

### Processing Rules
Retrieve Moderation Action.
Validate authority.
Validate expansion eligibility.
Apply expanded enforcement.
Create additional enforcement action if required.

### Governance Validation Rules
Must verify:

Original Moderation Action exists.
Original Moderation Action remains Applied.
Expansion scope is valid.
Expansion target is governable.
Expansion does not exceed platform authority rules.

### Enforcement Expansion Rules
Examples:

Content Removal
    →
Profile Restriction

Content Removal
    →
Community Restriction

Membership Removal
    →
Profile Restriction

Expansion represents broader enforcement based on governance review.

### Scope Validation Rules
Expansion must:

Reference existing Moderation Action.
Remain linked to original governance record.
Target valid governance resources.
Remain auditable.
### Visibility Rules
Expanded enforcement follows existing moderation visibility rules.

No audit information becomes public.

### Lifecycle Effects
Original Moderation Action remains:

Applied

Expanded enforcement produces additional governance outcomes.

No new lifecycle states created.

### Moderation Action Effects
Additional enforcement may be applied.

Original enforcement remains active.

### Audit Requirements
Audit record must capture:

actionId
reviewActor
reviewType=expand
expansionType
timestamp

### Success Outcome
Expanded enforcement applied.

### Error Conditions
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Validation Error

## Findings
### Finding 1 — Additional Constraint Required For Restore
Restoration must require a previously reversed Moderation Action.

Without this rule:

Applied → Restore

would bypass governance review.

Constraint required.

### Finding 2 — Additional Constraint Required For Expand
Expansion must only operate on active moderation outcomes.

Constraint required:

Applied only

Expansion of reversed actions should be forbidden.

### Finding 3 — Additional Constraint Required For Reverse
Reverse must be single-use.

Constraint required:

Applied → Reversed

only once.

### Finding 4 — Additional Constraint Required For Uphold
Uphold should not operate on already reversed actions.

Constraint required.

## Validation
| Validation Area                     | Result |
| ----------------------------------- | ------ |
| Governance Hierarchy                | Pass   |
| Governance Authority Model          | Pass   |
| Governance Visibility Model         | Pass   |
| Governance State Model              | Pass   |
| Authorization Boundaries            | Pass   |
| Endpoint Inventory                  | Pass   |
| Request Contract Model              | Pass   |
| Response Contract Model             | Pass   |
| Error Contract Model                | Pass   |
| Lifecycle Consistency               | Pass   |
| Auditability                        | Pass   |
| Platform Administrator Flows        | Pass   |
| Herd Owner Dispute Resolution Flows | Pass   |

---

# Moderation API Surface Validation
## Governance Capability Coverage Validation
### Reporting Capabilities
| Capability      | Workflow Coverage             | Endpoint Coverage                 | Status   |
| --------------- | ----------------------------- | --------------------------------- | -------- |
| Submit Report   | Report Submission             | POST /reports                     | Complete |
| Review Report   | Governance Review Queue       | GET /reports                      | Complete |
| Dismiss Report  | Community Governance Workflow | POST /reports/{reportId}/dismiss  | Complete |
| Escalate Report | Community Governance Workflow | POST /reports/{reportId}/escalate | Complete |

Validation Result:
Reporting Coverage = Complete

### Community Governance Capabilities
| Capability                 | Workflow Coverage               | Endpoint Coverage                                              | Status   |
| -------------------------- | ------------------------------- | -------------------------------------------------------------- | -------- |
| Review Community Reports   | Community Review Workflow       | GET /reports                                                   | Complete |
| Apply Community Moderation | Moderation Workflow             | POST /reports/{reportId}/moderate                              | Complete |
| Remove Herd Content        | Enforcement Workflow            | POST /posts/{postId}/remove, POST /comments/{commentId}/remove | Complete |
| Remove Herd Member         | Membership Enforcement Workflow | POST /herds/{herdId}/members/{memberId}/remove                 | Complete |
| Review Escalated Matters   | Escalation Review Workflow      | GET /reports/escalated                                         | Complete |

Validation Result:
Community Governance Coverage = Complete

### Platform Governance Capabilities
| Capability                 | Workflow Coverage               | Endpoint Coverage                           | Status   |
| -------------------------- | ------------------------------- | ------------------------------------------- | -------- |
| Restrict User Profile      | Profile Enforcement Workflow    | POST /profiles/{profileId}/restrict         | Complete |
| Restrict Herd              | Community Enforcement Workflow  | POST /herds/{herdId}/restrict               | Complete |
| Uphold Moderation Outcome  | Governance Review Workflow      | POST /moderation-actions/{actionId}/uphold  | Complete |
| Reverse Moderation Outcome | Governance Review Workflow      | POST /moderation-actions/{actionId}/reverse | Complete |
| Restore Governed Content   | Governance Restoration Workflow | POST /moderation-actions/{actionId}/restore | Complete |
| Expand Enforcement Action  | Governance Expansion Workflow   | POST /moderation-actions/{actionId}/expand  | Complete |

Validation Result:
Platform Governance Coverage = Complete

### Governance Oversight Capabilities
| Capability                 | Workflow Coverage  | Endpoint Coverage           | Status   |
| -------------------------- | ------------------ | --------------------------- | -------- |
| Review Governance Activity | Oversight Workflow | GET /governance/activity    | Complete |
| Review Shepherd Conduct    | Oversight Workflow | GET /governance/shepherds   | Complete |
| Review Herd Owner Conduct  | Oversight Workflow | GET /governance/herd-owners | Complete |

Validation Result:
Governance Oversight Coverage = Complete

## Endpoint Inventory Coverage Validation
### Capability Model Validation
Every approved governance capability maps to at least one endpoint.

Validation Result:

Pass

### Resource Model Validation
Governance Resources:

Report
Moderation Action

Both governance resources have complete workflow support.

Validation Result:

Pass

### CRUD Model Validation
Governance resources remain workflow-driven rather than CRUD-driven.

Validation Result:

Pass
### Authorization Model Validation
Every governance endpoint has an approved authority boundary.

Validation Result:

Pass

### Orphan Endpoint Validation
No governance endpoint exists without a corresponding capability.

Validation Result:

Pass

### Duplicate Responsibility Validation
No governance endpoint duplicates another endpoint's responsibility.

Validation Result:

Pass

## Authorization Coverage Validation
### Shepherd Authority

Authorized Capabilities:

Review Reports
Dismiss Reports
Apply Community Moderation
Remove Herd Content
Remove Herd Members
Escalate Reports

Validation Result:

Pass

### Herd Owner Authority
Authorized Capabilities:

Review Reports
Review Escalations
Override Shepherd Outcomes
Uphold Moderation Outcomes
Reverse Moderation Outcomes

Validation Result:

Pass

### Platform Administrator Authority
Authorized Capabilities:

Platform-wide Report Review
Profile Restriction
Herd Restriction
Uphold Moderation Outcomes
Reverse Moderation Outcomes
Restore Governed Content
Expand Enforcement Actions
Governance Oversight

Validation Result:

Pass

### Governance Hierarchy Validation
Approved hierarchy:

Applicable Law
    ↓
Platform Administrator
    ↓
Herd Owner
    ↓
Shepherd

Validation Result:

Pass

No authority escalation loopholes identified.

No hierarchy violations identified.

## Governance Workflow Coverage Validation

## Visibility Model Validation

Validated Against:

Public Users
Reporters
Shepherds
Herd Owners
Platform Administrators

Confirmed:

No governance information leaks.
No reporter identity leaks.
No moderation rationale leaks.
No audit trail exposure conflicts.
No visibility rule conflicts.

Validation Result:

Pass

Consistent with Governance Visibility Model and Moderation Visibility Matrix.

## Governance Resource Validation
### Report Resource Coverage

Supported Operations:

Creation
Review
Escalation
Resolution
Dismissal

Validation Result:

Complete

### Moderation Action Resource Coverage
Supported Operations:

Creation
Enforcement
Reversal
Restoration
Expansion
Oversight

Validation Result:

Complete

### Governance Resource Gap Validation
Additional governance resources required:

None

Validation Result:

Pass

### Moderation Boundary Validation

Approved Moderation Targets:

Post
Comment
User Profile
Herd
Herd Membership

#### Validation Result
| Moderation Target | Enforcement Coverage | Authority Coverage | Visibility Coverage | Audit Coverage | Status   |
| ----------------- | -------------------- | ------------------ | ------------------- | -------------- | -------- |
| Post              | Yes                  | Yes                | Yes                 | Yes            | Complete |
| Comment           | Yes                  | Yes                | Yes                 | Yes            | Complete |
| User Profile      | Yes                  | Yes                | Yes                 | Yes            | Complete |
| Herd              | Yes                  | Yes                | Yes                 | Yes            | Complete |
| Herd Membership   | Yes                  | Yes                | Yes                 | Yes            | Complete |


## Findings
### Finding 1
Every approved governance capability is represented by:

At least one workflow
At least one endpoint

Status:

Resolved

### Finding 2
Every approved moderation target has:

Enforcement coverage
Authority coverage
Visibility coverage
Audit coverage

Status:

Resolved

### Finding 3
All approved governance lifecycle transitions have workflow support.

Status:

Resolved

### Finding 4
No orphan governance endpoints exist.

Status:

Resolved

### Finding 5
No duplicate governance endpoint responsibilities exist.

Status:

Resolved

# API Surface Validation
## Domain Coverage Validation
### Identity Domain
Validation Result
Complete.
No approved Identity capability lacks endpoint support.

### Social Graph Domain 
Validation Result
Complete.
Approved support exists for:
Follow User
Unfollow User
View Followers
View Following
No Social Graph capability gaps identified.

### Content Domain
Validation Result
Complete.
Approved support exists for:
Personal Posts
Herd Posts
Comments
Replies
Voting
No Content capability gaps identified.

### Community Domain
Validation Result
Complete.
Approved support exists for:
Herd Creation
Herd Management
Membership
Shepherd Assignment
No Community capability gaps identified.

### Feed Domain
Validation Result
Complete.
Approved support exists for:
Following Feed
Herd Feed
No Feed capability gaps identified.

### Media Domain
Validation Result
Complete.
Approved support exists for:
Image Upload
Image Retrieval
Image Removal
No Media capability gaps identified.

### Governance Domain
Validation Result
Complete.
Approved support exists for:
Reporting
Community Moderation
Platform Moderation
Governance Oversight
No Governance capability gaps identified.

### Conclusion
Domain Coverage Status: Complete
Findings:
Every approved API domain has endpoint support.
Every approved domain capability maps to at least one endpoint.
No unsupported approved domain capability identified.
No additional domain endpoints required.

## User Flow Coverage Validation
### Visiter Flows
Validation Result
All Visitor journeys can be executed using existing public endpoints.
No missing visitor workflow support identified.

### Member Flows
Validation Result
All Member participation workflows supported.
No missing member workflow support identified.

### Herd Flows
Validation Result
All Herd Owner workflows supported.
No missing Herd Owner workflow support identified.

### Shepherd Flows
Validation Result
All Shepherd workflows supported.
No missing Shepherd workflow support identified.

### Platform Administrator Flows
Validation Result
All Platform Administrator workflows supported.
No missing Platform Administrator workflow support identified.

### Conclusion
User Flow Coverage Status: Complete
Findings:
Every approved journey has endpoint support.
Every approved flow has capability support.
No workflow requires additional MVP endpoints.
No unsupported user path identified.

## Capability Coverage Validation
### Capability Coverage Result
| Area                               | Status   |
| ---------------------------------- | -------- |
| Capability → Resource Mapping      | Complete |
| Capability → Endpoint Mapping      | Complete |
| Capability → Authorization Mapping | Complete |
| Governance Hierarchy Consistency   | Complete |

### Conclusion
Capability Coverage Status: Complete
Findings:
Every approved capability maps to a resource.
Every approved capability maps to an endpoint.
Every approved capability has an authorization boundary.
No orphan capabilities exist.
No governance hierarchy violations exist.
No additional capability-supporting endpoints required.

## Resource Coverage Validation
### Primary Resources
#### Validation Result
Complete.

Identity resource fully specified.
No unsupported lifecycle behavior identified.

Post lifecycle:
Published → Removed
fully supported through endpoint inventory and governance workflows.

Approved lifecycle:
Active → Restricted → Closed
is supported through governance authority model.
No lifecycle gaps identified.

Media lifecycle fully supported.
No missing media workflows identified.

### Relationship Resources
#### Validation Result
Complete.
Supports:
Follow User
Unfollow User
View Followers
View Following
No relationship gaps identified.

### Membership
Validation Result
Complete.

Governance and participation lifecycles remain distinguishable and fully supported.

### Shepherd Assignment 
Validation Result

Complete.

Authority delegation lifecycle fully represented.

### Vote
Validation Result

Complete.

Vote lifecycle fully supported.

### Governance Resources
Validation Result
Complete.

Entire governance intake lifecycle supported.
No report-state gaps identified.

Governance enforcement lifecycle fully supported.

### Derived Resources
Validation Result

Complete.

Confirmed:

Feed remains derived.
Feed remains read-only.
Feed Items remain non-resources.
Ranking remains non-resource.
Recommendation remains non-resource.

No derived-resource inconsistencies identified.

### Conclusion
Conclusion

Resource Coverage Status: Complete

Findings:

Every approved resource has endpoint support.
Every approved resource has authorization support.
Every approved resource has lifecycle support.
Every approved resource has visibility support.
No orphan resources identified.
No unsupported resources identified.

## Endpoint Inventory Validation
### Endpoint Inventory Result
| Area                            | Status   |
| ------------------------------- | -------- |
| Capability Alignment            | Complete |
| Resource Alignment              | Complete |
| CRUD Alignment                  | Complete |
| Authorization Alignment         | Complete |
| Duplicate Responsibility Review | Complete |
| Endpoint Gap Review             | Complete |

### Conclusion
Endpoint Coverage Status: Complete
Findings:
No orphan endpoints.
No endpoint gaps.
No duplicate responsibilities.
No conflicting endpoint behavior.
No additional MVP endpoints required.

## Contract Consistency Validation
### Contract Consistency Result
| Area               | Status   |
| ------------------ | -------- |
| Request Contracts  | Complete |
| Response Contracts | Complete |
| Error Contracts    | Complete |

### Conclusion
Contract Coverage Status: Complete
Findings:
All required inputs defined.
No ownership fields client controlled.
No lifecycle fields client controlled.
No governance fields client controlled.
Visibility rules remain internally consistent.
Error coverage exists for all endpoint categories.
Governance workflows have complete error coverage.
Authorization failures have complete error coverage.
Validation failures have complete error coverage.

## Authorization Validation
### Ownership Validation Result
| Area                      | Status   |
| ------------------------- | -------- |
| Ownership Model           | Complete |
| Ownership Isolation       | Complete |
| Governance Override Model | Complete |

### Conclusion
Ownership authority model remains internally consistent.
No ownership conflicts identified.

## Community Governance Authority Validation
### Shepherd Authority Review

Approved Shepherd Capabilities

Review Community Reports
Dismiss Report
Remove Herd Content
Remove Herd Member
Escalate Matter

Validation:

All Shepherd authority remains:

Herd-scoped
Membership-scoped
Report-scoped

No global authority granted.

Result:

Pass.

### Herd Owner Authority Review

Approved Herd Owner Capabilities

Review Community Reports
Review Community Moderation Outcomes
Resolve Escalations
Reverse Shepherd Decisions
Assign Shepherds
Revoke Shepherds

Validation:

Authority limited to:

Owned Herds
Related Memberships
Related Governance Actions

Result:

Pass.

### Governance Escalation Review

Approved Escalation Chain

Shepherd
    ↓
Herd Owner
    ↓
Platform Administrator

Validated Against:

Report Escalation
Moderation Review
Governance Override
Enforcement Expansion

Result:

Pass.

No hierarchy bypass identified.

## Platform Governance Authority Validation
### Platform Administrator Authority Review

Approved Authority

Review All Reports
Review All Moderation Actions
Restrict Profiles
Restrict Herds
Uphold Decisions
Reverse Decisions
Restore Content
Expand Enforcement
Review Governance Conduct

Validation:

Platform authority remains:

Platform-wide
Final governance authority
Override authority

Result:

Pass.

### Governance Oversight Review
Validated:

Governance Activity Review
Shepherd Conduct Review
Herd Owner Conduct Review

Endpoints:

GET /governance/activity
GET /governance/shepherds
GET /governance/herd-owners

Result:

Pass.

Governance oversight fully supported.

## Authorization Coverage Result
| Area                            | Status   |
| ------------------------------- | -------- |
| Ownership Authority             | Complete |
| Community Governance Authority  | Complete |
| Platform Governance Authority   | Complete |
| Governance Escalation Model     | Complete |
| Privilege Escalation Prevention | Complete |
| Hierarchy Consistency           | Complete |

### Conclusion
Conclusion

Authorization Coverage Status: Complete

Findings:

No privilege escalation paths identified.
No ownership/governance conflicts identified.
No governance hierarchy violations identified.
Every endpoint has an authorization boundary.
Governance authority remains consistently enforced.

## Lifecycle Coverage Validation
### Lifecycle Coverage Result
| Entity              | Status   |
| ------------------- | -------- |
| User Profile        | Complete |
| Post                | Complete |
| Comment             | Complete |
| Herd                | Complete |
| Membership          | Complete |
| Shepherd Assignment | Complete |
| Report              | Complete |
| Moderation Action   | Complete |

### Conclusion
Lifecycle Coverage Status: Complete
Findings:
Every approved lifecycle state has workflow support.
Every approved lifecycle transition has endpoint support.
No unsupported lifecycle transitions identified.
Governance workflows remain lifecycle-consistent.
Resource lifecycles remain internally consistent.

## Cross-Document Consistency Validation
### Feature Coverage Result
| Area                  | Status   |
| --------------------- | -------- |
| Identity Features     | Complete |
| Social Graph Features | Complete |
| Content Features      | Complete |
| Community Features    | Complete |
| Feed Features         | Complete |
| Media Features        | Complete |
| Governance Features   | Complete |
No approved feature lacks API support.

### Journey Coverage Result
| Journey Group          | Status   |
| ---------------------- | -------- |
| Visitor                | Complete |
| Member                 | Complete |
| Herd Owner             | Complete |
| Shepherd               | Complete |
| Platform Administrator | Complete |
No approved journey lacks API support.

### User Flow Validation
Confirmed:
Every approved flow maps to approved capabilities.
Every approved capability maps to approved endpoints.
Every approved endpoint maps to approved resources.

No unsupported flow identified.

### Data Model Validation
Entity Representation Result
| Entity Category       | Status   |
| --------------------- | -------- |
| Primary Entities      | Complete |
| Relationship Entities | Complete |
| Governance Entities   | Complete |
| Derived Concepts      | Complete |
No approved entity lacks resource representation.

### Governance Consistency Validation
Result:
Complete.

## Documentation Gaps
None Identified

## Contradictions 
None Identified

# Future Considerations

Out of MVP scope:

Cursor pagination
Advanced search and filtering
Recommendation systems
Feed ranking
Governance analytics
Audit export workflows
Moderation automation

