# Features

---
## Release Definitions

### MVP
First publicly usable version of Chauthara.

### V1
Usability and engagement enhancements.

### V2
Governance, reputation, and community quality systems.

### Future
Long-term platform expansion.

---

# MVP
## Core Platform

### Feature: User Accounts
Description
Allow users to register, authenticate, and manage their accounts.

Why It Exists
Foundation of identity-first participation.

Dependencies
None

Priority
Critical

Purpose 
User Accounts provide:
Platform identity
Authentication
Authorization foundation
Participation eligibility
Moderation accountability
Every content creator, commenter, voter, follower, Herd member, Shepherd, and moderator must have a User Account.

MVP Requirements
Account Creation
Users must be able to:
Register a new account
Select a unique username
Provide an email address
Create credentials
Must attest that user meets the minimum platform age requirement.
Accept platform terms/policies before account creation

Authentication
Users must be able to:
Sign in
Sign out
Maintain authenticated sessions
Recover access to accounts
Account Ownership

Each account must have:
One unique username
One unique account identity
One owner
Shared accounts are not supported.

Account Management
Users must be able to:
View account information
Update basic account information
Change credentials
Request account deletion

Account States
Active
Normal operational state.
Capabilities:
Full platform access

Suspended
Administrative enforcement action.
Capabilities:
Login may be restricted
Participation prohibited
Reason examples:
Abuse
Harassment
Spam
Repeated policy violations

Deleted
Soft-deleted account.
Account access removed.
Data retained according to platform retention policy.

Pending Verification
Account created but email not yet verified.
Capabilities:
Cannot access authenticated platform functionality.

Account Lifecycle
Stage 1
Registration
    ↓
Stage 2
Account Activation
    ↓
Stage 3
Normal Participation
    ↓
Possible outcomes:
Continued use
Suspension
Deletion

Security Requirements
Authentication Security
Must provide:
Secure credential handling
Secure session handling
Protection against unauthorized account access

Credential Security
Must support:
Password strength requirements
Password reset capability

Abuse Protection
Must include reasonable MVP protections against:
Credential stuffing
Automated account creation
Session hijacking
Exact mechanisms are implementation decisions.

Privacy Requirements
MVP accounts must:
Avoid exposing private account data publicly
Separate public profile information from account information

Authorization Requirements
Only account owners may:
Modify their account
Delete their account
Administrative actions require elevated privileges.

Moderation & Governance Requirements
User Accounts must support platform governance hierarchy defined in PROJECT_CONTEXT.
Administrative Actions
Platform administrators must be able to:
Suspend accounts
Remove platform access
Investigate reports
Issue warnings

Accountability
Every action must be attributable to an account.
Includes:
Posts
Comments
Votes
Reports
Herd creation
Anonymous posting is not part of MVP.

Enforcement Compatibility
Accounts must support future actions such as:
Warnings
Temporary suspensions
Permanent bans
Reputation-based restrictions
Even if not fully implemented in MVP.

Onboarding Requirements
MVP Onboarding
Required:
Register account
Authenticate
Access platform

Optional:
Complete profile later
Follow users later
Join Herds later

Reason:
Faster user activation
Reduced abandonment risk
Simpler implementation

Dependencies on Other MVP Features
User Profiles
Accounts own profiles.

Dependency relationship:
User Account → User Profile

Follow System
Requires authenticated users.

Personal Posting
Requires authenticated users.

Herd Creation
Requires authenticated users.

Herd Membership
Requires authenticated users.

Comments & Replies
Requires authenticated users.

Voting
Requires authenticated users.

Reporting System
Requires authenticated users.

Moderation Systems
Require user identity.

### Feature: User Profiles
Description
Public user identity page containing profile information and contributions.

Why It Exists
Supports audience building and personal reputation.

Dependencies
User Accounts

Priority
Critical

Purpose
User Profiles provide:
Public identity
Contribution history
Audience building
Community participation visibility
Every User Account owns one User Profile.
Dependency relationship:
User Account
    ↓
User Profile

Profile Requirements
Profile Creation
A profile must be created for every account.
Separate profile creation is not required.

Public Profile
Every active user profile must have a public profile page.
Profiles serve as the primary destination for viewing a user's public activity.
Public profiles are viewable without authentication.

Profile Information
Public Information
Profiles must display:
Username
Profile picture/avatar
Bio
Account join date
Followers count
Following count
Visibility of additional participation information is defined below.
Private Information
Profiles must never display:
Email address
Credentials
Security information
Account recovery information
Internal moderation information
Reports submitted by the user

Editable Profile Fields
Users must be able to:
Upload or change profile picture
Create or modify bio
Usernames remain editable according to User Accounts requirements.

Non-Editable Profile Fields
Users cannot directly modify:
Account join date
Followers count
Following count
Moderation status
System-generated participation statistics

Profile Customization
MVP customization includes:
Profile picture
Bio
Not included in MVP:
Profile themes
Profile layouts
Featured content
Pinned content
Verification badges
Profile achievements
Profile analytics

Relationship to Following System
Profiles are follow targets.
Follow System depends on User Profiles.
Profiles must support:
Being followed
Displaying follower count
Displaying following count
Access to follower lists
Access to following lists

Relationship to Personal Posting
Profiles must display personal posts created by the user.
Purpose:
Audience building
Contribution visibility
Identity building

Relationship to Herd Participation
Profiles should display:
User-created Herd posts
Herd membership count
Profiles must provide access to the user's Herd membership list.

Relationship to Comments & Replies
Comments and replies are attributable to profiles.
Comment history appears on profiles.
Comment History Controls
Users may choose whether comment history is displayed on their profile.

Relationship to Aura
Aura is not displayed in MVP.
Profiles must remain compatible with future Aura integration.
Examples:
Aura score
Reputation indicators
Contribution recognition

Moderation & Governance Requirements
Accountability
All profile activity must remain attributable to an account.
Includes:
Posts
Comments
Votes
Reports
Herd participation
Anonymous profiles are not part of MVP.

Administrative Actions
Platform administrators must be able to:
Review profile activity
Investigate reports
Enforce moderation actions
Enforcement Compatibility
Profiles must support future actions such as:
Warnings
Temporary suspensions
Permanent bans
Reputation restrictions
Even if not fully implemented in MVP.

Onboarding Requirements
Required:
Account creation
Not Required:
Profile picture
Bio completion
Reason:
Lower onboarding friction.
Users may complete profiles later.

Dependencies on Other MVP Features
User Accounts
Profiles require User Accounts.
Dependency relationship:
User Account
    ↓
User Profile
Follow System
Profiles are follow targets.
Personal Posting
Profiles display user posts.
Comments & Replies
Profiles identify discussion participants.
Herd Membership
Profiles identify community participants.
Reporting System
Profiles can be reported.
Moderation Systems
Profiles support investigation and enforcement.

### Feature: Personal Posting
Description
Users create posts outside of Herds.

Why It Exists
Supports personal expression and follower-driven content.

Dependencies
User Accounts

Priority
Critical

Purpose
Personal Posting enables users to create and publish content in their own identity outside of Herds.
The system exists to support:
Personal expression.
Audience building.
Contribution history.
Follower engagement.
Discussion initiation.
Identity-driven participation.
Dependency relationship:
User Account
    ↓
User Profile
    ↓
Personal Posting
    ↓
Following Feed

MVP Posting Requirements
Authenticated users must be able to:
Create personal posts.
Publish personal posts.
View their personal posts.
Edit eligible personal posts.
Delete their personal posts.
View personal posts created by other users.
Share opinions, knowledge, questions, and discussion topics through personal posts.
Only active accounts may create personal posts.
Every post must have an identifiable author.
Anonymous posting is excluded from MVP.

Supported Content Types
MVP
Personal posts may contain:
Text Post
Required support:
Title
Content
Image Post
Required support:
Title + Image
Title + Content + Image
Images are optional.
Not Included in MVP
Short-form videos
Audio uploads
Livestream content
Polls
Documents
Rich embeds
Stories
Ephemeral content

Post Ownership & Authorship Rules
Every personal post has exactly one author.
Requirements:
Posts are attributable to a User Account.
Posts are attributable to a User Profile.
Ownership cannot be transferred.
Multiple authors are not supported.
Organization accounts are not supported.
Anonymous authorship is not supported.
Accountability requirements:
Every post must remain traceable to its author for moderation and governance purposes.

Post Visibility Rules
Public Visibility
All personal posts are public in MVP.
Personal posts must be visible through:
Author profile.
Following Feed (when applicable).
Direct post access.
Platform discovery surfaces that exist in MVP.
Viewing public posts does not require authentication.
Visibility Restrictions
Posts created by:
Deleted accounts
Suspended accounts
Moderation actions
follow platform governance decisions and enforcement rules.
Exact enforcement behavior remains a future moderation specification concern.
Not Included in MVP
Private posts.
Followers-only posts.
Custom audience controls.
Scheduled publication.
Draft visibility controls.

Post Lifecycle & State Transitions
Draft
User is creating or editing content.
Published
Visible according to platform visibility rules.
Deleted
Soft-deleted content.
No longer publicly visible.
Retained according to platform retention policies.
Removed
Administrative moderation action.
Content removed due to policy enforcement.
Lifecycle
Draft
    ↓
Published
    ↓
Possible Outcomes:
Remains Published
Edited
Deleted by Author
Removed by Moderation
This aligns with the platform-wide soft deletion decision already accepted.

Editing & Deletion Behavior
Editing
Authors may edit their own posts.
Requirements:
Authorship does not change.
Post identity does not change.
Edited Post Visibility
Edited posts must display an indication that the post has been edited.
The exact presentation is an implementation decision.
Deletion
Authors may delete their own posts.
Result:
Post becomes deleted.
Post is no longer publicly visible.
Platform retention rules still apply.
Administrative Removal
Administrators may remove posts that violate platform policies.

Moderation & Governance Requirements
Accountability
All posts must be attributable to authenticated users.
Platform Governance
Personal posts are governed by:
Applicable Law
Platform Administrators
As defined in PROJECT_CONTEXT.
Enforcement Compatibility
Personal Posting must support future actions such as:
Warnings
Content removals
Temporary restrictions
Account suspensions
Permanent bans
Abuse Prevention
The platform should support reasonable protections against:
Spam
Harassment
Impersonation
Malicious content
Coordinated abuse
Specific mechanisms remain implementation decisions.

Profile Integration Requirements
Profiles must display personal posts created by the user.
Purpose:
Identity building.
Audience building.
Contribution visibility.
Relationship:
User Profile
    ↓
Personal Posting
Profile ownership determines post authorship visibility.

Following Feed Integration Requirements
Personal posts are the primary content source for the Following Feed.
Requirements:
Posts from followed users are eligible for appearance in the Following Feed.
Follow relationships determine eligibility.
Personal Posting does not define ranking or ordering behavior.
Relationship:
Personal Posting
    ↓
Following Feed
    ↑
Follow System

Reporting Requirements
Users must be able to report personal posts.
Reports should support:
Spam
Harassment
Abuse
Hate content
Illegal content
Other policy violations
Reports become inputs to moderation workflows.
Specific reporting categories may evolve over time.

Dependencies on Other MVP Features
User Accounts
Required.
Only authenticated active users may create posts.
Dependency:
User Accounts
    ↓
Personal Posting
User Profiles
Required.
Profiles display authored posts.
Dependency:
User Profiles
    ↓
Personal Posting
Follow System
Required for Following Feed visibility.
Dependency:
Follow System
    ↓
Following Feed
    ↑
Personal Posting
Reporting System
Required.
Posts must be reportable.
Platform Moderation
Required.
Posts must support enforcement actions.
Comments & Replies
Depends on Personal Posting.
Posts are discussion roots.
Dependency:
Personal Posting
    ↓
Comments & Replies

Intentionally Postponed Beyond MVP
V1
Short-form video posts.
Content sharing enhancements.
Saved content integration.
V2
Audience visibility controls.
Post privacy controls.
Advanced creator analytics.
Mentions inside posts.
Future
Polls.
Scheduled publishing.
Collaborative posts.
Rich embeds.
Ephemeral content.
Creator monetization integrations.

### Feature: Following Feed
Description
Display content from followed users.

Why It Exists
Primary social consumption mechanism.

Dependencies
User Accounts
User Profiles
Follow System

Priority
Critical

Purpose
The Following Feed displays eligible content created by users that the viewer currently follows.
The feed exists to support:
Audience building.
Identity-driven discovery.
Ongoing participation.
Consumption of followed-user content.
Dependency relationship:
User Accounts
    ↓
User Profiles
    ↓
Follow System
    ↓
Following Feed

MVP Feed Requirements
Users must be able to:
View a Following Feed.
View content from followed users.
Refresh the feed.
Load additional feed content.
Open content from the feed.
Only content eligible under feed rules may appear.
The Following Feed is the default platform feed experience. This aligns with the Feed Philosophy defined in PROJECT_CONTEXT.md.

Content Eligibility Rules
Eligible Content
The Following Feed may display:
Personal posts created by followed users.
Requirements:
The author must currently be followed by the viewer.
The content must remain publicly visible.
The content must not be deleted.
The content must not be removed by moderation actions.
Not Eligible
The Following Feed must not display:
Content from unfollowed users.
Deleted content.
Moderation-removed content.
Draft content.
Discovery content.
Recommended content.
Advertisements.
Community-only feed content not created by followed users.
Future content types may become eligible when introduced.

Feed Visibility Requirements
Authenticated Users
Authenticated users may access their Following Feed.
Feed content is personalized based on active follow relationships.
Unauthenticated Users
Following Feed access requires authentication because follow relationships are account-specific.
Public Visibility
Feed membership itself is not publicly visible.
The existence of content in a user's Following Feed is not exposed to other users.

Content Ordering Requirements
MVP Ordering Model
The Following Feed must use chronological ordering.
Requirements:
Newer eligible content appears before older eligible content.
Ordering must be deterministic.
All users viewing the same followed author's content should observe consistent ordering behavior.
The Following Feed does not perform engagement ranking in MVP.
Examples of excluded MVP behavior:
Popularity ranking.
Recommendation ranking.
Aura-based ranking.
Personalized ranking.

Feed Refresh Behavior
Users must be able to refresh the Following Feed.
Refresh Requirements
When refreshed:
Newly eligible content should become visible.
Content no longer eligible should no longer appear.
Active follow relationship changes should be reflected.
Example:
User follows Author A.
Author A publishes a post.
Feed refresh occurs.
New post becomes eligible.
Real-time feed updates are not required for MVP.

Pagination & Loading Requirements
The Following Feed must support incremental loading of content.
Requirements:
Initial feed view displays a subset of eligible content.
Additional content can be loaded.
Loading additional content must preserve ordering consistency.
Users should be able to continue viewing older feed content.
Exact loading mechanisms are implementation decisions.

Integration With Following Relationships
The Following Feed depends on active follow relationships.
Follow Relationship Effects
When a follow occurs:
Future eligible content from that user may appear in the feed.
When an unfollow occurs:
Future content from that user becomes ineligible.
Requirements:
Feed eligibility must reflect current follow relationships.
Follow relationships determine content inclusion.
The Following Feed does not create or modify follow relationships.
Relationship:
Follow System
    ↓
Following Feed
    ↑
Personal Posting

Moderation & Governance Requirements
Platform Governance
The Following Feed is governed by:
Applicable Law
Platform Administrators
As defined in PROJECT_CONTEXT.md.
Content Enforcement
Content that becomes:
Deleted
Removed
Restricted by moderation
must no longer appear in the Following Feed.
Abuse Prevention
The platform should support reasonable protections against:
Spam amplification.
Feed abuse.
Automated content flooding.
Manipulative engagement behavior.
Specific mechanisms remain implementation decisions.
Enforcement Compatibility
The Following Feed must remain compatible with future:
Content restrictions.
Account suspensions.
Reputation systems.
Feed governance systems.

Dependencies on Other MVP Features
User Accounts
Required.
Feed ownership is account-specific.
User Profiles
Required.
Feed content is attributable to profiles.
Follow System
Required.
Determines content eligibility.
Dependency:
Follow System
    ↓
Following Feed
Personal Posting
Required.
Primary content source.
Dependency:
Personal Posting
    ↓
Following Feed
Reporting System
Required.
Feed content must remain reportable.
Platform Moderation
Required.
Moderation actions affect feed visibility.

Intentionally Postponed Beyond MVP
V1
Feed filtering.
Feed search.
Content sharing integration.
Read/unread indicators.
V2
Feed customization.
User-controlled sorting options.
Aura-aware feed experiences.
Advanced feed preferences.
Future
Discovery feed.
Recommendation systems.
Algorithmic ranking.
Cross-feed blending.
Personalized feed intelligence.
Reputation-aware feed ranking.

### Feature: Follow System
Description
Users follow other users.

Why It Exists
Creates identity graph.

Dependencies
User Accounts

Priority
Critical

Purpose
The Follow System enables users to establish ongoing relationships with other users.
The system provides:
Audience building
Contributor discovery
Identity graph creation
Following Feed personalization
Reputation and influence foundations
Dependency relationship:
User Accounts
    ↓
User Profiles
    ↓
Follow System
    ↓
Following Feed

Follow Relationship Requirements
A follow relationship represents one user choosing to subscribe to another user's public activity.
Requirements:
Users may follow other users.
Users may unfollow users.
Follow relationships are directional.
Following is not mutual by default.
Following does not require approval in MVP.
Users cannot follow themselves.
Only active accounts may create follow relationships.
Example:
User A follows User B.
Result:
User A becomes a follower of User B.
User B becomes followed by User A.
User B is not automatically following User A.

Follow Behavior
Users must be able to:
Follow a profile.
Unfollow a profile.
View whether they currently follow a profile.
When a follow occurs:
Relationship becomes active immediately.
Follower count increases.
Following count increases.
Followed user's future content becomes eligible for Following Feed visibility.
When an unfollow occurs:
Relationship is removed immediately.
Follower count decreases.
Following count decreases.
Future content from that user no longer appears in the Following Feed because of that relationship.
Historical content remains publicly accessible through profiles and other platform surfaces where otherwise visible.

Visibility Requirements
Public Visibility
The following information is publicly visible:
Follower count
Following count
Follower list
Following list
Reason:
These relationships support:
Discovery
Audience building
Identity transparency
Private Visibility
The following are not exposed:
Internal follow timestamps
Internal relationship metadata
Moderation-related relationship data
Authentication Rules
Viewing profiles does not require authentication.
Following and unfollowing require authenticated accounts.

Profile Integration Requirements
Profiles are follow targets.
Profiles must support:
Being followed
Displaying follower count
Displaying following count
Access to follower list
Access to following list
Follow information is part of profile identity and audience visibility.
Relationship:
User Profile
    ↓
Follow System

Feed Integration Requirements
The Follow System is a dependency of the Following Feed.
Following Feed requirements:
Feed displays content from followed users.
Feed visibility is determined by active follow relationships.
Personal posts from followed users appear in Following Feed.
Future supported content types may also appear.
The Follow System itself does not define ranking or ordering behavior.
Those are feed concerns rather than follow-system concerns.

Moderation & Governance Requirements
Accountability
Every follow relationship must be attributable to authenticated accounts.
Anonymous participation is excluded from MVP.
Enforcement Compatibility
The system must support future moderation actions affecting follow relationships.
Examples:
Account suspension
Account bans
Abuse investigations
Spam investigations
Abuse Prevention
The platform should support reasonable protections against:
Follow spam
Automated account abuse
Artificial audience manipulation
Specific mechanisms remain implementation decisions.
Governance Consistency
Follow relationships do not override platform governance hierarchy defined in PROJECT_CONTEXT.

Dependencies on Other MVP Features
User Accounts
Required.
Only authenticated users may create follow relationships.
Dependency:
User Accounts
    ↓
Follow System
User Profiles
Required.
Profiles are follow targets.
Dependency:
User Profiles
    ↓
Follow System
Following Feed
Depends on Follow System.
Dependency:
Follow System
    ↓
Following Feed
Personal Posting
Follow relationships determine which personal posts appear in Following Feed.
Dependency:
Personal Posting
    ↓
Following Feed
    ↑
Follow System

Intentionally Postponed Beyond MVP
V1
Follow notifications
User blocking interactions with follow relationships
V2
Private accounts
Follow approval requests
Follow privacy controls
Follower visibility controls
Following visibility controls
Future
Suggested users
Follow recommendations
Mutual follower indicators
Creator audience analytics
Reputation-influenced discovery

### Feature: Comments & Replies
Description
Users discuss posts through threaded conversations.

Why It Exists
Core discussion functionality.

Dependencies
Posting System

Priority
Critical

Purpose
Comments & Replies enable users to participate in discussions around posts.
The system exists to support:
Discussion.
Knowledge sharing.
Question answering.
Clarification.
Community participation.
Contribution visibility.
Dependency relationship:
User Account
    ↓
User Profile
    ↓
Personal Post / Herd Post
    ↓
Comments & Replies

MVP Discussion Requirements
Authenticated users must be able to:
Create comments.
Create replies.
View comments.
View replies.
Edit eligible comments.
Edit eligible replies.
Delete their comments.
Delete their replies.
Only active accounts may participate.
Every comment and reply must have an identifiable author.
Anonymous participation is excluded from MVP.

Comment Creation Requirements
Comments are direct responses to posts.
Requirements:
Users may comment on eligible posts.
Every comment must have exactly one author.
Comments must be attributable to a User Account.
Comments must be attributable to a User Profile.
Users may create multiple comments on a post.
Empty comments are not permitted.
Comment authorship cannot be transferred.

Reply Creation Requirements
Replies are responses to comments or other replies.
Requirements:
Users may reply to comments.
Users may reply to replies.
Every reply must have exactly one author.
Replies remain attributable to their author.
Empty replies are not permitted.
Reply ownership cannot be transferred.
Nesting & Thread Structure Requirements
Discussion Structure
Post
    ↓
Comment
    ↓
Reply
    ↓
Reply
    ↓
Additional Replies
Requirements:
Comments belong to a single post.
Replies belong to a single discussion thread.
Discussion relationships must be preserved.
Parent-child relationships must remain intact.
Exact visual presentation is an implementation decision.

Visibility & Ordering Requirements
Public Visibility
All comments and replies are public in MVP.
Comments and replies must be visible through:
Associated post.
Author profile (subject to profile comment-history preference).
Direct access mechanisms that exist in MVP.
Viewing public discussions does not require authentication.

Ordering Requirements
Comments and replies must have a deterministic ordering mechanism.
The exact ordering strategy is an implementation decision for MVP.
Examples:
Chronological.
Reverse chronological.
Future ranking systems.
Comments & Replies do not define ranking behavior.
Future voting systems may influence ordering.

Comment & Reply Lifecycle
Draft
    ↓
Published
    ↓
Possible Outcomes:
Remains Published
Edited
Deleted by Author
Removed by Moderation
Deleted
Soft-deleted content.
Removed from public visibility.
Retained according to platform retention policies.
Removed
Administrative moderation action.
Content removed due to policy violations.

Editing & Deletion Behavior
Editing
Authors may edit their own comments and replies.
Requirements:
Authorship does not change.
Comment identity does not change.
Reply identity does not change.
Edited Visibility
Edited comments and replies must display an indication that they were edited.
The exact presentation is an implementation decision.
Deletion
Authors may delete their own comments and replies.
Result:
Content becomes deleted.
Content is no longer publicly visible.
Platform retention policies still apply.
Administrative Removal
Administrators may remove comments and replies that violate platform policies.
Deleted Account Behavior
When an account is deleted:
- Comments and replies created by that account remain visible.
- Discussion continuity should be preserved.
- The original username is no longer displayed.
- The author must be indicated as a deleted account.
- Exact presentation is an implementation decision.
Example:
[deleted]

Moderation & Governance Requirements
Accountability
All comments and replies must be attributable to authenticated users.
Anonymous participation is excluded from MVP.
Platform Governance
Comments and replies are governed by:
Applicable Law
Platform Administrators
As defined in PROJECT_CONTEXT.
Abuse Prevention
The platform should support reasonable protections against:
Spam
Harassment
Abuse
Impersonation
Coordinated abuse
Specific mechanisms remain implementation decisions.
Enforcement Compatibility
Discussion systems must support future actions such as:
Warnings
Content removals
Temporary restrictions
Account suspensions
Permanent bans

Profile Integration Requirements
Comments and replies are attributable to profiles.
Profiles must support displaying user comment history.
Users may choose whether comment history appears on their profile.
This follows the previously resolved profile decision.
Purpose:
Contribution visibility.
Reputation building.
Accountability.
Relationship:
User Profile
    ↓
Comments & Replies

Post Integration Requirements
Comments and replies are discussion extensions of posts.
Requirements:
Posts act as discussion roots.
Comments belong to posts.
Replies exist within post discussion threads.
Deleting a post does not automatically define comment handling behavior.
Moderation behavior affecting discussion trees is a future decision.
Relationship:
Post
    ↓
Comments
    ↓
Replies

Reporting Requirements
Users must be able to report:
Comments
Replies
Reports should support:
Spam
Harassment
Abuse
Hate content
Illegal content
Other policy violations
Reports become inputs to moderation workflows.
Specific reporting categories may evolve over time.

Dependencies on Other MVP Features
User Accounts
Required.
Only authenticated active users may participate.
Dependency:
User Accounts
    ↓
Comments & Replies
User Profiles
Required.
Profiles identify discussion participants.
Dependency:
User Profiles
    ↓
Comments & Replies
Personal Posting
Required.
Posts are discussion roots.
Dependency:
Personal Posting
    ↓
Comments & Replies
Herd Posting
Required.
Herd posts also act as discussion roots.
Dependency:
Herd Posting
    ↓
Comments & Replies
Reporting System
Required.
Comments and replies must be reportable.
Platform Moderation
Required.
Comments and replies must support enforcement actions.
HypeUp / HypeDown Voting
Depends on Comments & Replies.
Comments are valid voting targets.
Dependency:
Comments & Replies
    ↓
HypeUp / HypeDown

Intentionally Postponed Beyond MVP
V1
Comment sharing.
Saved comments.
Comment permalinks enhancements.
V2
User mentions in comments.
Advanced discussion sorting.
Comment search.
Comment collapse preferences.
Moderation history visibility.
Future
Community notes integration.
Reputation-aware discussion ranking.
AI-assisted moderation.
Rich media comments.
Anonymous discussion modes (if ever adopted).

### Feature: HypeUp / HypeDown Voting
Description
Voting mechanism for posts and comments.

Why It Exists
Supports ranking and reputation signals.

Dependencies
User Accounts
User Profiles
Personal Posting
Herd Posting
Comments & Replies

Priority
Critical

Purpose
HypeUp / HypeDown Voting enables users to express approval or disapproval of content.
The system exists to support:
Contribution evaluation.
Content quality signaling.
Future content ranking systems.
Future reputation systems.
Community participation.
Dependency relationship:
User Account
    ↓
Posts / Comments
    ↓
HypeUp / HypeDown Voting
    ↓
Future Ranking Systems
    ↓
Future Aura Systems

MVP Voting Requirements
Authenticated users must be able to:
HypeUp eligible content.
HypeDown eligible content.
Remove their vote.
View vote totals.
Only active accounts may vote.
Every vote must be attributable to a User Account.
Anonymous voting is excluded from MVP.

Valid Voting Targets
MVP voting supports:
Posts
Users may vote on:
Personal Posts
Herd Posts
Comments & Replies
Users may vote on:
Comments
Replies
Voting is not supported for:
User Profiles
Herds
Follow Relationships
Reports
Accounts

Vote Behavior Requirements
Single Vote Rule
A user may have at most one active vote on a voting target.
Possible states:
No Vote
HypeUp
HypeDown
A user cannot simultaneously HypeUp and HypeDown the same content.
Vote Switching
Users may change:
HypeUp
    ↓
HypeDown
or
HypeDown
    ↓
HypeUp
The previous vote is replaced.
Self-Voting
Users cannot vote on their own content.
Applies to:
Posts
Comments
Replies
Reason:
Prevents artificial inflation of contribution signals.
Authentication Requirements
Viewing vote totals does not require authentication.
Casting, changing, or removing votes requires authentication.

Vote Visibility Requirements
Public Visibility
The following must be publicly visible:
HypeUp count
HypeDown count
Reason:
Supports transparency of community feedback.
Private Visibility
The following are not publicly visible:
Identity of HypeUp voters
Identity of HypeDown voters
Internal vote metadata
Moderation-related vote information

Vote Modification & Removal Requirements
Users must be able to:
Add a vote.
Change a vote.
Remove a vote.
Vote removal returns content to the user's "No Vote" state.
Removing a vote does not affect authorship, ownership, or visibility of the content itself.

Moderation & Governance Requirements
Accountability
All votes must be attributable to authenticated accounts.
Anonymous participation is excluded from MVP.
Platform Governance
Voting is governed by:
Applicable Law
Platform Administrators
As defined in PROJECT_CONTEXT.md.
Abuse Prevention
The platform should support reasonable protections against:
Vote manipulation.
Automated voting.
Coordinated voting abuse.
Artificial reputation inflation.
Specific mechanisms remain implementation decisions.
Enforcement Compatibility
Voting must support future moderation actions such as:
Vote abuse investigations.
Reputation abuse investigations.
Account suspensions.
Platform bans.

Influence on Platform Systems
MVP
Voting provides signals to:
Content evaluation.
Community feedback.
No Aura behavior is defined in MVP.
No ranking behavior is defined in MVP.
Future Compatibility
Voting must remain compatible with future:
Content ranking systems.
Aura calculations.
Reputation systems.
Governance systems.
Discovery systems.
This aligns with PROJECT_CONTEXT.md and existing feature planning.

Dependencies on Other MVP Features
User Accounts
Required.
Only authenticated active users may vote.
Dependency:
User Accounts
    ↓
HypeUp / HypeDown
User Profiles
Required.
Votes are attributable to user identity.
Dependency:
User Profiles
    ↓
HypeUp / HypeDown
Personal Posting
Required.
Personal posts are valid voting targets.
Dependency:
Personal Posting
    ↓
HypeUp / HypeDown
Herd Posting
Required.
Herd posts are valid voting targets.
Dependency:
Herd Posting
    ↓
HypeUp / HypeDown
Comments & Replies
Required.
Comments and replies are valid voting targets.
Dependency:
Comments & Replies
    ↓
HypeUp / HypeDown
Platform Moderation
Required.
Voting activity must support moderation and enforcement actions.

Intentionally Postponed Beyond MVP
V1
Vote notifications.
Saved list of voted content.
Vote activity visibility.
V2
Aura integration.
Reputation-weighted voting.
Community-specific voting policies.
Vote analytics.
Future
Public voter visibility.
Reputation-based governance voting.
Specialized reaction systems.
Advanced vote abuse detection systems.
Community notes integration with voting.

### Feature: Herd Creation
Description
Users create topic-based communities.

Why It Exists
Community-centric participation.

Dependencies
User Accounts

Priority
Critical

### Feature: Herd Membership
Description
Users join and leave Herds.

Why It Exists
Build community graph.

Dependencies
Herd System

Priority
Critical

### Feature: Herd Posting
Description
Users create posts inside Herds.

Why It Exists
Community discussion.

Dependencies
Herd System

Priority
Critical

### Feature: Herd Feed
Description
Feed showing content from joined Herds.

Why It Exists
Community-focused consumption.

Dependencies
Herd Membership

Priority
Critical

### Feature: Reporting System
Description
Users report content and behavior.

Why It Exists
Safety and abuse prevention.

Dependencies
Posts, Comments, Users

Priority
Critical

### Feature: Platform Moderation
Description
Administrative moderation tools.

Why It Exists
Governance and policy enforcement.

Dependencies
Reporting System

Priority
Critical

### Feature: Shepherd Moderation
Description
Community moderation tools.

Why It Exists
Supports Herd autonomy.

Dependencies
Herd System

Priority
Critical

### Feature: Image Uploads
Description
Images.

Why It Exists
Improves content quality.

Dependencies
Posting System

Priority
High

# V1 
## Core Platform

### Feature: Search & Discovery
Description
Search people, Herds, and posts.

Why It Exists
Supports exploration and growth.

Dependencies
Users, Herds, Posts

Priority
High

### Feature: Save Content
Description
Users bookmark posts.

Why It Exists
Supports knowledge retention.

Dependencies
Posts

Priority
High

### Feature: Content Sharing
Description
Share platform content elsewhere.

Why It Exists
Content sharing promots content propagation.

Dependencies
Profiles, Herds, Posts, Comments, URL Routing / Deep Linking, (canonical url)

Priority
High

### Feature: Notifications
Description
Alerts for follows, replies, votes, mentions, and Herd activity.

Why It Exists
Encourages engagement.

Dependencies
Core social actions

Priority
High


### Feature: Aura Reputation Foundation
Description
Display user Aura and basic reputation indicators.

Why It Exists
Supports contribution-centric identity.

Dependencies
Voting System

Priority
High

## Advanced Platform

Post-MVP features that strengthen engagement and governance.

### Feature: Short Video Uploads
Description
Short videos.

Why It Exists
Improves content quality.

Dependencies
Posting System

Priority
High

### Feature: User Blocking
Description
Prevent interactions from specific users.

Why It Exists
Safety and personal control.

Dependencies
Accounts

Priority
High

# V2
## Advance Platform 
Post-MVP features that strengthen engagement and governance. 

### Feature: Mentions
Description
Reference users in posts and comments.

Why It Exists
Improves discussion connectivity.

Dependencies
Profiles

Priority
Medium

### Feature: Direct Notifications Preferences
Description
Granular notification controls.

Why It Exists
User experience improvement.

Dependencies
Notifications

Priority
Medium

### Feature: Aura-Based Herd Access
Description
Minimum Aura requirements for communities.

Why It Exists
Supports quality-focused communities.

Dependencies
Aura System

Priority
High

### Feature: Request-to-Join Herds
Description
Approval-based communities.

Why It Exists
Supports controlled participation.

Dependencies
Herd Membership

Priority
Medium

### Feature: Invite-Only Herds
Description
Private communities.

Why It Exists
Supports exclusive groups.

Dependencies
Herd Membership

Priority
Medium

### Feature: Enhanced Aura System
Description
Advanced reputation calculations and contributor recognition.

Why It Exists
Strengthens contribution incentives.

Dependencies
Aura Foundation

Priority
High


### Feature: User Privacy Controls
Description
Control visibility and interactions.

Why It Exists
User safety.

Dependencies
Accounts

Priority
High

### Feature: Moderator Tooling Expansion
Description
Queues, actions, moderation history.

Why It Exists
Scale moderation efforts.

Dependencies
Moderation System

Priority
High

### Feature: Analytics Dashboard
Description
Basic creator and community metrics.

Why It Exists
Community growth visibility.

Dependencies
Posts, Herds

Priority
Medium

# FUTURE
## Future Platform

Long-term expansion features already mentioned or implied by project vision.

### Feature: Discovery Feed
Description
Content recommendation feed.

Why It Exists
Broader content discovery.

Dependencies
Ranking Systems

Priority
Future

### Feature: Community Notes
Description
Context and clarification contributions.

Why It Exists
Improve discussion quality.

Dependencies
Reputation System

Priority
Future

### Feature: Creator Subscriptions
Description
Paid creator support.

Why It Exists
Monetization.

Dependencies
Payments

Priority
Future

### Feature: Herd Monetization
Description
Community-level monetization.

Why It Exists
Support community growth.

Dependencies
Payments

Priority
Future

### Feature: Private Messaging
Description
User-to-user communication.

Why It Exists
Relationship building.

Dependencies
Accounts

Priority
Future

### Feature: End-to-End Encrypted Messaging
Description
Secure private conversations.

Why It Exists
Privacy enhancement.

Dependencies
Messaging System

Priority
Future

### Feature: Advanced Moderation Automation
Description
Automated abuse and spam detection.

Why It Exists
Operational scaling.

Dependencies
Moderation System

Priority
Future

### Feature: Reputation-Based Governance
Description
Community participation in governance decisions.

Why It Exists
Increase community ownership.

Dependencies
Advanced Aura

Priority
Future

### Feature: Expanded Youth Support (14+)
Description
Additional safety systems and compliance features.

Why It Exists
Expand audience.

Dependencies
Safety Infrastructure

Priority
Future
