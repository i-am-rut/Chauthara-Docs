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

