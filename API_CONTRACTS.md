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
| Endpoint                                    | Classification       |
| ------------------------------------------- | -------------------- |
| POST /reports/{reportId}/dismiss            | Path Parameter Only  |
| POST /reports/{reportId}/moderate           | Path + Request Body  |
| POST /reports/{reportId}/escalate           | Path Parameter Only  |
| GET /reports/escalated                      | Query Parameter Only |
| POST /posts/{postId}/remove                 | Path Parameter Only  |
| POST /comments/{commentId}/remove           | Path Parameter Only  |
| POST /moderation-actions/{actionId}/uphold  | Path Parameter Only  |
| POST /moderation-actions/{actionId}/reverse | Path Parameter Only  |
| POST /moderation-actions/{actionId}/restore | Path Parameter Only  |
| POST /moderation-actions/{actionId}/expand  | Path + Request Body  |
| GET /governance/activity                    | Query Parameter Only |
| GET /governance/shepherds                   | Query Parameter Only |
| GET /governance/herd-owners                 | Query Parameter Only |

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
#### Optional
moderation rationale
expansion rationale
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
| Endpoint                        | Classification      |
| ------------------------------- | ------------------- |
| GET moderation-action           | Governance Resource |
| All governance action endpoints | Workflow Outcome    |

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

#