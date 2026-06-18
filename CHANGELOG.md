## 2026-06-18

### Documentation

- Completed MVP Comments & Replies specification.

- Defined:
  - Comments & Replies purpose
  - MVP discussion requirements
  - Comment creation requirements
  - Reply creation requirements
  - Nesting and thread structure requirements
  - Visibility and ordering requirements
  - Editing and deletion behavior
  - Moderation and governance requirements
  - Profile integration requirements
  - Post integration requirements
  - Reporting requirements
  - Feature dependencies

- Resolved Comments and Replies Decision:
  - Comments and replies must remain visible with [deleted] as author.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP HypeUp / HypeDown Voting specification.

- Defined:
  - Voting purpose
  - MVP voting requirements
  - Valid voting targets
  - Vote behavior restrictions
  - Vote visibility requirements
  - Vote modification and removal behavior
  - Moderation and governance requirements
  - Voting system dependencies
  - Future compatibility requirements

- Resolved Voting decisions:
  - HypeUp and HypeDown selected as MVP voting model.
  - Self-voting prohibited.
  - One active vote per user per target.
  - Vote identities remain private.
  - Public vote counts visible.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md
  
- Completed MVP Following Feed specification.

- Defined:
  - Following Feed purpose
  - MVP feed requirements
  - Content eligibility rules
  - Feed visibility requirements
  - Content ordering requirements
  - Feed refresh behavior
  - Pagination and loading requirements
  - Follow System integration requirements
  - Moderation and governance requirements
  - Feed dependencies

- Resolved Following Feed decisions:
  - Following Feed is the default platform feed.
  - Following Feed uses chronological ordering in MVP.
  - Only personal posts from followed users are eligible.
  - Real-time feed updates excluded from MVP.
  - Recommendation systems excluded from MVP.

- Updated:
  - FEATURES.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Herd Creation specification.

- Defined:
  - Herd purpose
  - Herd creation requirements
  - Herd ownership model
  - Shepherd leadership requirements
  - Herd metadata requirements
  - Herd visibility requirements
  - Herd membership model
  - Herd lifecycle requirements
  - Moderation and governance requirements
  - Feature dependencies

- Resolved Herd Creation decision:
  - Herd creation does not require Aura in MVP.
  - Shepherd identities must always be publicly visible.
  - Herd rules are mandatory in MVP.
  - New Herds receive default placeholder rules at creation.
  - Herd Owners and Shepherds may replace or modify default rules.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Herd Membership specification.

- Defined:
  - Herd Membership purpose
  - MVP membership requirements
  - Joining behavior
  - Leaving behavior
  - Membership visibility requirements
  - Participation requirements
  - Membership restrictions and eligibility requirements
  - Moderation and governance requirements
  - Feature dependencies
  - Future compatibility requirements

- Resolved Herd Membership decisions:
  - Open Join membership model selected.
  - Membership approval workflow excluded from MVP.
  - Membership lists publicly visible.
  - Joined Herds publicly visible on profiles.
  - Membership does not grant governance authority.
  
- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

## 2026-06-17

### Documentation

- Added release definitions:
  - MVP
  - V1
  - V2
  - Future
  as implementation phases of:
  - Identity Graph
  - Community Graph
  - Discussion System

- Defined release boundaries for Chauthara:
  - MVP
  - V1
  - V2
  - Future

- Established MVP scope:
  - User Accounts
  - User Profiles
  - Follow System
  - Personal Posting
  - Image Uploads
  - Following Feed
  - Comments & Replies
  - HypeUp / HypeDown Voting
  - Herd Creation
  - Herd Membership
  - Herd Posting
  - Herd Feed
  - Reporting System
  - Platform Moderation
  - Shepherd Moderation

- Refined Rich Media scope:
  - Images included in MVP
  - Short-form videos moved to V1

- Reclassified User Blocking as V1.

- Classified remaining features into V1, V2, and Future releases.

- Updated planning artifacts:
  - CURRENT_SPRINT.md
  - TASKS.md

- Transitioned project focus from MVP definition to MVP feature specification.
- Transitioned project phase from planning to MVP system design.

- Completed MVP User Accounts specification.
- Defined:
  - Account purpose
  - Account lifecycle
  - Account states
  - Authentication requirements
  - Security requirements
  - Governance requirements
  - Onboarding requirements
  - Feature dependencies

- Resolved User Accounts decisions:
  - Email verification required before activation
  - Soft deletion policy
  - Username changes allowed
  - One account per email
  - No age verification beyond self-attestation
  - Account verification badges postponed beyond MVP

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md
  - PROJECT_CONTEXT.md

- Completed MVP User Profiles specification.

- Defined 
    - User Profile purpose
    - MVP profile requirements
    - Profile visibility rules
    - Editable profile fields
    - Non-editable profile fields
    - MVP profile customization scope
    - User Profile relationships
    - governance requirements

- Resolved User Profile Decisions:
    - Public profiles included in MVP.
    - Aura visibility excluded from MVP.
    - Follower lists should be publicly visible.
    - Following lists should be publicly visible.
    - Herd membership lists should be publicly visible.
    - Comment history appears on profiles.
    - Users may hide comment history.
    - Follower and following counts should be publicly visible on profile.
    - Profile completion is optional after account creation.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Follow System specification.

- Defined:
  - Follow System purpose
  - Follow relationship model
  - Follow behavior
  - Follower and following visibility
  - Profile integration requirements
  - Following Feed integration requirements
  - Governance requirements
  - Feature dependencies

- Resolved Follow System decisions:
  - Open follow model selected.
  - Follow relationships are directional.
  - Users cannot follow themselves.
  - Follow approval workflow excluded from MVP.
  - Private accounts excluded from MVP.
  - Follower counts publicly visible.
  - Following counts publicly visible.
  - Follower lists publicly visible.
  - Following lists publicly visible.
  - Follow notifications excluded from MVP.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Personal Posting specification.

- Defined:
  - Personal Posting purpose
  - MVP posting requirements
  - Supported content types
  - Post ownership and authorship rules
  - Post visibility rules
  - Post lifecycle
  - Editing and deletion behavior
  - Moderation and governance requirements
  - Profile integration requirements
  - Following Feed integration requirements
  - Reporting requirements
  - Feature dependencies

- Resolved Personal Posting decisions:
  - Display an "edited" tag for Edited posts

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md


## 2026-06-16

### Documentation

- Identified major features and classified them into
  - Core Platform
  - Advanced Platform 
  - Future Platform

- Updated planning artifacts:
  - CURRENT_SPRINT.md
  - TASKS.md
  - QUESTIONS.md
  - FEATURES.md

- Transitioned project focus from Feature inventory and classification to MVP Definitons and boundaries.