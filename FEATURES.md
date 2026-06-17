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

### Feature: Following Feed
Description
Display content from followed users.

Why It Exists
Primary social consumption mechanism.

Dependencies
Follow System

Priority
Critical

### Feature: Follow System
Description
Users follow other users.

Why It Exists
Creates identity graph.

Dependencies
User Accounts

Priority
Critical

### Feature: Comments & Replies
Description
Users discuss posts through threaded conversations.

Why It Exists
Core discussion functionality.

Dependencies
Posting System

Priority
Critical

### Feature: HypeUp / HypeDown Voting
Description
Voting mechanism for posts and comments.

Why It Exists
Supports ranking and reputation signals.

Dependencies
Posts, Comments

Priority
Critical

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

## Advanced Platform

Post-MVP features that strengthen engagement and governance.

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
