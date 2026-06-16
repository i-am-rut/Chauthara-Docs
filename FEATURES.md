# Features

## Core Platform

These are considered essential for a usable first version.

### Feature: User Accounts
Description
Allow users to register, authenticate, and manage their accounts.

Why It Exists
Foundation of identity-first participation.

Dependencies
None

Priority
Critical

### Feature: User Profiles
Description
Public user identity page containing profile information and contributions.

Why It Exists
Supports audience building and personal reputation.

Dependencies
User Accounts

Priority
Critical

### Feature: Personal Posting
Description
Users create posts outside of Herds.

Why It Exists
Supports personal expression and follower-driven content.

Dependencies
User Accounts

Priority
Critical

### Feature: Post Feed (Following Feed)
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

### Feature: Rich Media Uploads
Description
Images and short videos.

Why It Exists
Improves content quality.

Dependencies
Posting System

Priority
High

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

### Feature: User Blocking
Description
Prevent interactions from specific users.

Why It Exists
Safety and personal control.

Dependencies
Accounts

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
