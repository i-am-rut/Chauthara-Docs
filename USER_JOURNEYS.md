# User Types

## Visitor

**Description**
A person who has not authenticated and may not even have an account.
They consume public content and evaluate whether Chauthara is worth joining.

**Primary Goals**
V-P1 Discover Valuable Content

Determine whether the platform contains useful discussions, people, and communities.

V-P2 Evaluate Platform Relevance

Decide whether Chauthara is worth joining.

V-P3 Explore Communities

Understand what Herds exist and what topics are discussed.

**Secondary Goals**
V-S1 Explore Individual Contributors

Discover interesting users.

V-S2 Understand Community Culture

Evaluate discussion quality, moderation quality, and platform tone.

V-S3 Browse Public Discussions

Read posts, comments, and community conversations.

**Optional Goals**
V-O1 Identify Potential Communities To Join
V-O2 Identify People Worth Following

**Goal Priority**
Discover Valuable Content
Evaluate Platform Relevance
Explore Communities
Explore Contributors
Browse Discussions

**Goal Relationships**

Discover Content
↓
Evaluate Platform Relevance
↓
Create Account (becomes Member)

## Visitor Journeys

### Journey VJ-01: Discover Public Content
User Goal Supported
Discover Valuable Content
Browse Public Discussions
Journey Description

Visitor explores publicly available posts and discussion threads to determine whether valuable content exists on the platform.

Trigger

Visitor arrives on Chauthara through:

Direct visit
Shared link
Search result
Referral
Success State

Visitor successfully finds content that demonstrates the type and quality of discussions available on the platform.

Features Involved
Personal Posting
Herd Posting
Comments & Replies
Image Uploads
Dependencies
Public profiles
Public posts
Public discussions
Notes

This is the foundational discovery journey for all visitors.

### Journey VJ-02: Explore Contributors
User Goal Supported
Discover Valuable Content
Explore Individual Contributors
Identify People Worth Following
Journey Description

Visitor explores user profiles and contribution history to evaluate the quality and credibility of individual contributors.

Trigger

Visitor encounters an interesting post, comment, or discussion participant.

Success State

Visitor identifies contributors whose content would justify future participation on the platform.

Features Involved
User Profiles
Personal Posting
Comments & Replies
Follow System (visibility only)
Dependencies
Public user profiles
Public contribution history
Notes

Visitor cannot follow users but can evaluate potential future follow targets.

### Journey VJ-03: Explore Communities
User Goal Supported
Explore Communities
Identify Potential Communities To Join
Journey Description

Visitor discovers Herds, reviews their purpose, content, rules, membership visibility, and activity to determine whether relevant communities exist.

Trigger

Visitor wants to investigate topic-focused participation opportunities.

Success State

Visitor identifies one or more Herds aligned with their interests.

Features Involved
Herd Creation
Herd Membership
Herd Posting
Image Uploads
Dependencies
Public Herd visibility
Public Herd content
Public Herd metadata
Notes

This journey focuses on community discovery rather than discussion quality.

### Journey VJ-04: Evaluate Community Quality
User Goal Supported
Understand Community Culture
Explore Communities
Journey Description

Visitor evaluates the quality of discussions occurring within Herds by reading posts, comments, rules, and observing moderation presence.

Trigger

Visitor enters a Herd that appears relevant.

Success State

Visitor determines whether the community demonstrates constructive discussion and healthy participation.

Features Involved
Herd Posting
Comments & Replies
Shepherd Moderation
Herd Creation
Dependencies
Public Herd discussions
Public rules
Visible Shepherd identities
Notes

Focuses on quality assessment rather than discovery.

### Journey VJ-05: Evaluate Platform Relevance
User Goal Supported
Evaluate Platform Relevance
Journey Description

Visitor synthesizes information gathered from content, contributors, and communities to determine whether Chauthara is worth joining.

Trigger

Visitor has completed one or more discovery journeys.

Success State

Visitor reaches one of two conclusions:

Join the platform
Leave the platform
Features Involved
User Profiles
Personal Posting
Herd Posting
Comments & Replies
Herd Creation
Herd Membership
Dependencies

Depends on successful completion of discovery-oriented journeys.

Notes

This is the terminal Visitor journey and the final outcome before becoming a Member.

## Visitor Journey Validation

### Goal Coverage
| Visitor Goal                           | Covered By   |
| -------------------------------------- | ------------ |
| Discover Valuable Content              | VJ-01, VJ-02 |
| Evaluate Platform Relevance            | VJ-05        |
| Explore Communities                    | VJ-03, VJ-04 |
| Explore Individual Contributors        | VJ-02        |
| Understand Community Culture           | VJ-04        |
| Browse Public Discussions              | VJ-01        |
| Identify Potential Communities To Join | VJ-03        |
| Identify People Worth Following        | VJ-02        |

### MVP Feature Coverage
| MVP Feature                               | Visitor Journey Usage      |
| ----------------------------------------- | -------------------------- |
| User Profiles                             | VJ-02, VJ-05               |
| Personal Posting                          | VJ-01, VJ-02, VJ-05        |
| Comments & Replies                        | VJ-01, VJ-02, VJ-04, VJ-05 |
| Herd Creation                             | VJ-03, VJ-04, VJ-05        |
| Herd Membership                           | VJ-03, VJ-05               |
| Herd Posting                              | VJ-01, VJ-03, VJ-04, VJ-05 |
| Shepherd Moderation                       | VJ-04                      |
| Image Uploads                             | VJ-01, VJ-03               |
| Follow System (public visibility aspects) | VJ-02                      |

## Member

**Description**
Authenticated user participating as a normal platform member.
This is the baseline user type.

**Primary Goals**
M-P1 Express Ideas And Opinions

Share knowledge, thoughts, questions, and experiences.

M-P2 Participate In Discussions

Contribute through comments and replies.

M-P3 Build Personal Identity

Establish a recognizable profile and contribution history.

M-P4 Consume Relevant Content

Stay informed through Following Feed and Herd Feed.

M-P5 Participate In Communities

Join Herds and contribute to community discussions.

**Secondary Goals**
M-S1 Build An Audience

Gain followers through valuable participation.

M-S2 Discover Interesting People

Find contributors worth following.

M-S3 Discover Interesting Communities

Find Herds aligned with interests.

M-S4 Evaluate Content Quality

Use HypeUp/HypeDown to express feedback.

M-S5 Maintain Personal Profile

Customize and manage public identity.

**Optional Goals**
M-O1 Create A Herd

Become a community leader.

M-O2 Report Harmful Content

Help maintain platform quality.

M-O3 Share Visual Content

Use images to improve communication.

**Goal Priority**
Consume Relevant Content
Express Ideas And Opinions
Participate In Discussions
Participate In Communities
Build Personal Identity
Build Audience

**Goal Relationships**
Consume Content
↓
Participate In Discussions
↓
Create Content
↓
Build Identity
↓
Build Audience

Participate In Communities
↓
Potential Herd Ownership

## Member Journeys
### MJ-01: Consume Followed User Content
User Goal Supported
Consume Relevant Content
Journey Description

Member consumes content from people they have chosen to follow.

Trigger

User wants to see activity from followed users.

Success State

User discovers and consumes relevant personal content.

Features Involved
User Accounts
Follow System
Following Feed
Personal Posting
Dependencies
Account exists
At least one followed user
Notes

Natural continuation of Visitor content discovery.

### MJ-02: Discover And Follow Interesting People
User Goal Supported
Consume Relevant Content
Build Audience
Journey Description

Member identifies a creator or contributor and follows them for future content.

Trigger

User finds a valuable profile.

Success State

Follow relationship established.

Features Involved
User Profiles
Follow System
Dependencies
Existing profile to follow
Notes

Begins as Visitor profile exploration and transitions into Member participation.

### MJ-03: Publish A Personal Post
User Goal Supported
Express Ideas And Opinions
Build Personal Identity
Build Audience
Journey Description

Member publishes content under their own identity.

Trigger

User wants to share an idea, opinion, experience, question, or knowledge.

Success State

Personal post becomes publicly visible.

Features Involved
Personal Posting
User Profiles
Image Uploads
Dependencies
Authenticated Member
Notes

Primary identity-building journey.

### MJ-04: Participate In A Discussion
User Goal Supported
Participate In Discussions
Build Personal Identity
Journey Description

Member contributes comments or replies within a discussion.

Trigger

User wants to respond to existing content.

Success State

Contribution becomes part of the discussion thread.

Features Involved
Comments & Replies
Dependencies
Existing post or discussion
Notes

Core discussion outcome.

### MJ-05: Evaluate Content Through Voting
User Goal Supported
Participate In Discussions
Consume Relevant Content
Journey Description

Member expresses approval or disapproval of content.

Trigger

User encounters content worth evaluating.

Success State

Vote recorded on content.

Features Involved
HypeUp / HypeDown Voting
Dependencies
Existing post, comment, or reply
Notes

Lightweight participation journey.

### MJ-06: Build A Personal Profile
User Goal Supported
Build Personal Identity
Journey Description

Member customizes and maintains their public identity.

Trigger

User wants to improve profile presentation.

Success State

Profile accurately represents the user.

Features Involved
User Profiles
Image Uploads
Dependencies
Existing account
Notes

Identity-focused journey separate from content creation.

### MJ-07: Join A Herd Community
User Goal Supported
Participate In Communities
Consume Relevant Content
Journey Description

Member becomes part of a topic-focused community.

Trigger

User discovers a Herd relevant to their interests.

Success State

Active Herd membership established.

Features Involved
Herd Creation
Herd Membership
Dependencies
Existing Herd
Notes

Community participation entry point.

### MJ-08: Consume Community Content
User Goal Supported
Consume Relevant Content
Participate In Communities
Journey Description

Member consumes content from joined Herds.

Trigger

User wants to stay informed about community activity.

Success State

Relevant Herd content is consumed.

Features Involved
Herd Membership
Herd Feed
Herd Posting
Dependencies
Joined Herd
Notes

Community equivalent of Following Feed consumption.

### MJ-09: Contribute To A Herd
User Goal Supported
Participate In Communities
Express Ideas And Opinions
Build Personal Identity
Journey Description

Member contributes original content inside a Herd.

Trigger

User wants to participate in a community conversation.

Success State

Herd post becomes visible within the community.

Features Involved
Herd Membership
Herd Posting
Image Uploads
Dependencies
Membership in target Herd
Notes

Primary community contribution journey.

### MJ-10: Help Maintain Community Quality
User Goal Supported
Participate In Communities
Journey Description

Member reports content, profiles, or communities that violate rules or policies.

Trigger

User encounters problematic content.

Success State

Report submitted for review.

Features Involved
Reporting System
Dependencies
Reportable entity exists
Notes

Participation in platform governance without moderation authority.

## Member Journey Validation

### Goal Coverage
| Member Goal                | Covered By                 |
| -------------------------- | -------------------------- |
| Consume Relevant Content   | MJ-01, MJ-07, MJ-08        |
| Express Ideas And Opinions | MJ-03, MJ-09               |
| Participate In Discussions | MJ-04, MJ-05               |
| Participate In Communities | MJ-07, MJ-08, MJ-09, MJ-10 |
| Build Personal Identity    | MJ-03, MJ-04, MJ-06, MJ-09 |
| Build Audience             | MJ-02, MJ-03               |

### MVP Feature Coverage
| MVP Feature        | Exercised |
| ------------------ | --------- |
| User Accounts      | Yes       |
| User Profiles      | Yes       |
| Personal Posting   | Yes       |
| Following Feed     | Yes       |
| Follow System      | Yes       |
| Comments & Replies | Yes       |
| HypeUp / HypeDown  | Yes       |
| Herd Membership    | Yes       |
| Herd Posting       | Yes       |
| Herd Feed          | Yes       |
| Reporting System   | Yes       |
| Image Uploads      | Yes       |

### Common Journeys with Visitor
| Visitor Outcome             | Member Continuation |
| --------------------------- | ------------------- |
| Discover Valuable Content   | MJ-01, MJ-08        |
| Explore Communities         | MJ-07, MJ-08        |
| Evaluate Platform Relevance | MJ-02, MJ-03, MJ-07 |

### Member Specific Journeys
MJ-02 Discover And Follow Interesting People
MJ-03 Publish A Personal Post
MJ-04 Participate In A Discussion
MJ-05 Evaluate Content Through Voting
MJ-06 Build A Personal Profile
MJ-07 Join A Herd Community
MJ-09 Contribute To A Herd
MJ-10 Help Maintain Community Quality

## Herd Owner

**Description**
Creator and leader of a Herd.
Responsible for community stewardship.

Herd Owner inherits all Member goals.
**Additional Primary Goals**
HO-P1 Build A Community

Create and grow a topic-focused Herd.

HO-P2 Establish Community Identity

Define purpose, rules, and culture.

HO-P3 Maintain Community Health

Keep discussions constructive and aligned with community goals.

**Secondary Goals**
HO-S1 Recruit Contributors

Encourage membership growth and participation.

HO-S2 Delegate Moderation

Appoint Shepherds to support governance.

HO-S3 Resolve Community Disputes

Handle escalations and moderation disagreements.

**Optional Goals**
HO-O1 Become A Recognized Community Leader
HO-O2 Develop A High-Quality Knowledge Community

**Goal Priority**
Build Community
Maintain Community Health
Establish Community Identity
Recruit Contributors
Resolve Disputes

**Goal Relationships**
Create Herd
↓
Build Community
↓
Grow Membership
↓
Maintain Community Health
↓
Long-Term Community Success

## Herd Owner Journeys

### Journey HOJ-01: Create A Herd
User Goal Supported
Build Community
Journey Description

Herd Owner creates a new Herd to establish a topic-focused community.

Trigger

User decides a desired community does not already exist or wants to lead a new community.

Success State

A new active Herd exists with an identifiable owner and is available for members to join.

Features Involved
Herd Creation
Image Uploads
Dependencies
Authenticated Member
Active account
Notes

This is the entry-point journey that transforms a Member into a Herd Owner.

### Journey HOJ-02: Define Community Identity
User Goal Supported
Build Community
Establish Community Identity
Journey Description

Herd Owner establishes the purpose, presentation, expectations, and culture of the Herd.

Trigger

New Herd creation or need to refine community direction.

Success State

Community members can clearly understand the Herd's purpose, rules, and identity.

Features Involved
Herd Creation
Image Uploads
Dependencies
Existing Herd
Herd ownership
Notes

Includes maintaining descriptions, rules, avatar, and cover image.

### Journey HOJ-03: Grow Community Participation
User Goal Supported
Build Community
Recruit Contributors
Journey Description

Herd Owner attracts members and encourages ongoing participation within the Herd.

Trigger

Owner wants to increase activity, membership, or community engagement.

Success State

Community gains active members, contributors, and ongoing discussion.

Features Involved
Herd Membership
Herd Posting
Herd Feed
Comments & Replies
Dependencies
Existing Herd
Existing community activity
Notes

Focuses on community growth rather than moderation.

### Journey HOJ-04: Delegate Community Governance
User Goal Supported
Maintain Community Health
Delegate Moderation
Journey Description

Herd Owner appoints Shepherds to assist with moderation and community governance responsibilities.

Trigger

Community growth creates a need for additional governance support.

Success State

One or more Shepherds are actively supporting community moderation.

Features Involved
Herd Creation
Shepherd Moderation
Dependencies
Existing Herd
Eligible community members
Notes

Represents delegation of governance responsibilities rather than direct moderation activity.

### Journey HOJ-05: Oversee Community Health
User Goal Supported
Maintain Community Health
Develop A High-Quality Knowledge Community
Journey Description

Herd Owner reviews community activity, moderation outcomes, and participation quality to ensure the Herd remains constructive and aligned with its goals.

Trigger

Routine leadership oversight or concerns regarding community quality.

Success State

Community remains aligned with its rules, purpose, and expected standards.

Features Involved
Herd Posting
Comments & Replies
Reporting System
Shepherd Moderation
Dependencies
Existing Herd
Active community participation
Notes

Focuses on stewardship and governance oversight rather than direct dispute handling.

### Journey HOJ-06: Resolve Community Moderation Disputes
User Goal Supported
Resolve Community Disputes
Maintain Community Health
Journey Description

Herd Owner reviews escalated moderation matters, evaluates Shepherd decisions, resolves community disputes, and escalates platform-level concerns when necessary.

Trigger

A moderation decision, report outcome, or governance disagreement is escalated to the Herd Owner.

Success State

The dispute is resolved, reversed, upheld, or escalated to Platform Administrators when appropriate.

Features Involved
Reporting System
Shepherd Moderation
Platform Moderation
Dependencies
Existing moderation dispute or escalation
Notes

Includes review of Shepherd actions and escalation to Platform Administrators when required.

## Herd Owner Journey Validations

### Goal Coverage
| Herd Owner Goal                            | Covered By                                |
| ------------------------------------------ | ----------------------------------------- |
| Build Community                            | HOJ-01, HOJ-02, HOJ-03                    |
| Establish Community Identity               | HOJ-02                                    |
| Maintain Community Health                  | HOJ-04, HOJ-05, HOJ-06                    |
| Recruit Contributors                       | HOJ-03                                    |
| Delegate Moderation                        | HOJ-04                                    |
| Resolve Community Disputes                 | HOJ-06                                    |
| Become A Recognized Community Leader       | Emergent outcome of HOJ-01 through HOJ-06 |
| Develop A High-Quality Knowledge Community | HOJ-05                                    |

### MVP Feature Coverage
| MVP Feature         | Herd Owner Usage       |
| ------------------- | ---------------------- |
| Herd Creation       | HOJ-01, HOJ-02, HOJ-04 |
| Herd Membership     | HOJ-03                 |
| Herd Posting        | HOJ-03, HOJ-05         |
| Herd Feed           | HOJ-03                 |
| Comments & Replies  | HOJ-03, HOJ-05         |
| Reporting System    | HOJ-05, HOJ-06         |
| Shepherd Moderation | HOJ-04, HOJ-05, HOJ-06 |
| Platform Moderation | HOJ-06                 |
| Image Uploads       | HOJ-01, HOJ-02         |


### Governance Coverage
| Governance Responsibility         | Covered By |
| --------------------------------- | ---------- |
| Community Creation                | HOJ-01     |
| Community Identity & Rules        | HOJ-02     |
| Community Growth                  | HOJ-03     |
| Moderation Delegation             | HOJ-04     |
| Moderation Oversight              | HOJ-05     |
| Dispute Resolution                | HOJ-06     |
| Escalation To Platform Governance | HOJ-06     |

### Inherited Member Journeys
Herd Owners continue to perform all Member journeys:
MJ-01 through MJ-10

### Herd Owner Specific Journeys
HOJ-01 Create A Herd
HOJ-02 Define Community Identity
HOJ-03 Grow Community Participation
HOJ-04 Delegate Community Governance
HOJ-05 Oversee Community Health
HOJ-06 Resolve Community Moderation Disputes

## Shepherd

**Description**
Community moderator operating inside a Herd.

Shepherd inherits all Member goals.
**Additional Primary Goals**
SH-P1 Enforce Community Rules

Ensure Herd discussions follow established standards.

SH-P2 Maintain Discussion Quality

Reduce spam, abuse, disruption, and off-topic participation.

SH-P3 Protect Community Members

Respond to harmful behavior within the Herd.

**Secondary Goals**
SH-S1 Review Reports

Investigate reported content and behavior.

SH-S2 Guide Community Participation

Encourage constructive discussion.

SH-S3 Escalate Serious Issues

Forward matters requiring higher authority.

**Optional Goals**
SH-O1 Help Community Growth
SH-O2 Support Herd Owner Governance

**Goal Priority**
Enforce Community Rules
Maintain Discussion Quality
Protect Community Members
Review Reports
Escalate Serious Issues

**Goal Relationships**
Review Community Activity
↓
Identify Issues
↓
Apply Community Moderation
↓
Maintain Community Health

## Shepherd Journeys
### Journey SHJ-01: Moderate Herd Content
User Goal Supported
Enforce Community Rules
Maintain Discussion Quality
Protect Community Members
Journey Description

Shepherd reviews Herd posts, comments, and replies and removes content that violates Herd rules or disrupts constructive discussion.

Trigger

Shepherd observes problematic content through normal community participation or moderation review.

Success State

Violating content is removed and no longer appears through normal Herd visibility surfaces.

Features Involved
Herd Posting
Comments & Replies
Shepherd Moderation
Dependencies
Existing Herd
Existing content
Shepherd authority within Herd
Notes

Includes moderation of:

Herd posts
Comments
Replies

Does not include platform-wide enforcement.

### Journey SHJ-02: Review Community Reports
User Goal Supported
Review Reports
Enforce Community Rules
Protect Community Members
Journey Description

Shepherd reviews reports involving Herd content, discussions, and community-rule violations and determines whether enforcement is required.

Trigger

A report enters the moderation queue for the Herd.

Success State

Report is reviewed and either:

Dismissed
Actioned through community moderation
Escalated
Features Involved
Reporting System
Shepherd Moderation
Dependencies
Existing report
Shepherd authority within Herd
Notes

Represents the primary report-handling workflow for community moderation.

### Journey SHJ-03: Moderate Community Membership
User Goal Supported
Enforce Community Rules
Protect Community Members
Maintain Discussion Quality
Journey Description

Shepherd removes disruptive or rule-violating members from the Herd when continued participation would harm the community.

Trigger

A member repeatedly violates community expectations or community participation standards.

Success State

Member is removed from the Herd and loses future participation eligibility within that Herd.

Features Involved
Herd Membership
Shepherd Moderation
Dependencies
Existing Herd member
Shepherd authority within Herd
Notes

Community removal is not platform enforcement.

Existing authored content remains attributable to the original author.

### Journey SHJ-04: Guide Constructive Participation
User Goal Supported
Maintain Discussion Quality
Guide Community Participation
Help Community Growth
Journey Description

Shepherd actively encourages constructive discussion and healthy community participation through visible moderation presence and community guidance.

Trigger

Routine community stewardship or emerging discussion-quality concerns.

Success State

Discussions remain aligned with community expectations and participation quality remains healthy.

Features Involved
Herd Posting
Comments & Replies
Shepherd Moderation
Dependencies
Active Herd discussions
Notes

Represents proactive moderation rather than enforcement.

Focuses on maintaining discussion quality before formal moderation becomes necessary.

### Journey SHJ-05: Escalate Serious Community Issues
User Goal Supported
Escalate Serious Issues
Protect Community Members
Support Herd Owner Governance
Journey Description

Shepherd escalates reports, moderation disputes, severe violations, or governance concerns that exceed community moderation authority.

Trigger

A matter requires review beyond Shepherd authority.

Examples:

Potential platform policy violations
Illegal content concerns
Severe harassment
Governance disputes
Cases potentially requiring account-level enforcement
Success State

Matter is successfully escalated to the appropriate authority for further review.

Features Involved
Reporting System
Shepherd Moderation
Platform Moderation
Dependencies
Existing report, violation, or moderation dispute
Notes

Escalation path:

Shepherd → Herd Owner → Platform Administrator

Platform Administrators may directly review matters when required.

## Shepherd Journey Validations

### Goal Coverage
| Shepherd Goal                 | Covered By                     |
| ----------------------------- | ------------------------------ |
| Enforce Community Rules       | SHJ-01, SHJ-02, SHJ-03         |
| Maintain Discussion Quality   | SHJ-01, SHJ-03, SHJ-04         |
| Protect Community Members     | SHJ-01, SHJ-02, SHJ-03, SHJ-05 |
| Review Reports                | SHJ-02                         |
| Guide Community Participation | SHJ-04                         |
| Escalate Serious Issues       | SHJ-05                         |
| Help Community Growth         | SHJ-04                         |
| Support Herd Owner Governance | SHJ-05                         |

### MVP Features Coverage
| MVP Feature         | Shepherd Journey Usage                 |
| ------------------- | -------------------------------------- |
| Herd Membership     | SHJ-03                                 |
| Herd Posting        | SHJ-01, SHJ-04                         |
| Comments & Replies  | SHJ-01, SHJ-04                         |
| Reporting System    | SHJ-02, SHJ-05                         |
| Shepherd Moderation | SHJ-01, SHJ-02, SHJ-03, SHJ-04, SHJ-05 |
| Platform Moderation | SHJ-05                                 |

### Moderation Coverage
| Moderation Responsibility | Covered By             |
| ------------------------- | ---------------------- |
| Report Handling           | SHJ-02                 |
| Content Moderation        | SHJ-01                 |
| Comment Moderation        | SHJ-01                 |
| Reply Moderation          | SHJ-01                 |
| Member Moderation         | SHJ-03                 |
| Discussion Quality        | SHJ-04                 |
| Escalation Handling       | SHJ-05                 |
| Community Protection      | SHJ-01, SHJ-03, SHJ-05 |

### Inherited Member Journeys
Shepherds continue to perform all Member journeys:
MJ-01 through MJ-10

### Shepherd Specific Journeys
SHJ-01 Moderate Herd Content
SHJ-02 Review Community Reports
SHJ-03 Moderate Community Membership
SHJ-04 Guide Constructive Participation
SHJ-05 Escalate Serious Community Issues

## Platform Administrator

**Description**
Platform-wide governance actor.
Responsible for platform safety and enforcement.

**Primary Goals**
PA-P1 Protect Platform Safety

Keep users safe across the platform.

PA-P2 Enforce Platform Policies

Apply platform-wide governance consistently.

PA-P3 Resolve Escalated Disputes

Act as final authority for moderation conflicts.

PA-P4 Ensure Legal And Governance Compliance

Maintain compliance with laws and platform rules.

**Secondary Goals**
PA-S1 Review Reports

Investigate reported content and behavior.

PA-S2 Oversee Community Governance

Ensure Herd Owners and Shepherds act appropriately.

PA-S3 Prevent Platform Abuse

Address spam, coordinated abuse, impersonation, and harmful behavior.

PA-S4 Maintain Moderation Consistency

Ensure similar cases receive similar treatment.

**Optional Goals**
PA-O1 Improve Platform Quality
PA-O2 Improve Governance Processes

**Goal Priority**
Protect Platform Safety
Enforce Platform Policies
Resolve Escalated Disputes
Ensure Legal Compliance
Prevent Platform Abuse

**Goal Relationships**
Review Reports
↓
Investigate
↓
Apply Enforcement
↓
Maintain Platform Safety
↓
Protect Platform Integrity


# User Type Hierarchy

Visitor
    ↓
Member
    ├── Herd Owner
    └── Shepherd

Platform Administrator

# Notes

The following are not separate user types for journey mapping:

- Herd Member
- Herd Creator
- Content Creator
- Reporter
- Follower
- Reported User
- Suspended User
- Deleted User
- Banned User

These are feature behaviors, role states, or account states rather than distinct journey actors.

# Goal Hierarchy
Visitor
├─ Discover Content
├─ Explore Communities
└─ Evaluate Platform

Member
├─ Consume Content
├─ Create Content
├─ Participate In Discussions
├─ Participate In Communities
├─ Build Identity
└─ Build Audience

Herd Owner
├─ Build Community
├─ Establish Community Identity
├─ Maintain Community Health
└─ Resolve Community Issues

Shepherd
├─ Enforce Rules
├─ Maintain Discussion Quality
├─ Review Reports
└─ Protect Community Members

Platform Administrator
├─ Protect Platform Safety
├─ Enforce Policies
├─ Resolve Escalations
└─ Maintain Governance

# Goal Coverage Analysis
| MVP Feature         | Supported Goal(s)               |
| ------------------- | ------------------------------- |
| User Accounts       | Join Platform, Participate      |
| User Profiles       | Build Identity                  |
| Follow System       | Build Audience, Discover People |
| Personal Posting    | Express Ideas                   |
| Comments & Replies  | Participate In Discussions      |
| HypeUp/HypeDown     | Evaluate Content Quality        |
| Following Feed      | Consume Relevant Content        |
| Herd Creation       | Build Community                 |
| Herd Membership     | Participate In Communities      |
| Herd Posting        | Community Contribution          |
| Herd Feed           | Community Content Consumption   |
| Reporting System    | Protect Community / Platform    |
| Shepherd Moderation | Maintain Community Health       |
| Platform Moderation | Protect Platform Safety         |
| Image Uploads       | Visual Communication, Identity  |

