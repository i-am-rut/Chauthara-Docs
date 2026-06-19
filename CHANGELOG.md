## 2026-06-19

### Documentation

- Completed User Type Identification for MVP User Journey Inventory.

- Identified and documented the primary platform actors:
  - Visitor
  - Member
  - Herd Owner
  - Shepherd
  - Platform Administrator

- Evaluated additional candidate actors:
  - Herd Member
  - Herd Creator
  - Content Creator
  - Reporter
  - Follower
  - Reported User
  - Suspended User
  - Deleted User
  - Banned User

- Determined that the above candidates should not be treated as separate user types for journey mapping because they represent:
  - Feature behaviors
  - Participation states
  - Governance states
  - Account states

- Established the official MVP User Journey actor hierarchy:
  - Visitor
  - Member
    - Herd Owner
    - Shepherd
  - Platform Administrator

- Created 
  - USER_JOURNEYS.md 
  as the authoritative source for user journey analysis.

- Confirmed that future User Goals, User Journeys, and User Flows will be built using the identified user types.

- Updated
  - CHANGELOG.md
  - TASKS.md 

- Completed User Goal Identification for MVP User Journey Inventory.

- Defined goals for:
  - Visitor
  - Member
  - Herd Owner
  - Shepherd
  - Platform Administrator

- Classified goals into:
  - Primary Goals
  - Secondary Goals
  - Optional Goals

- Established goal priorities for each user type.

- Defined goal relationships and progression paths.

- Created platform-wide goal hierarchy.

- Performed MVP feature coverage validation against identified user goals.

- Confirmed that all MVP features support at least one user goal.

- Identified the recommended goal set for upcoming User Journey Mapping.

- Updated:
  - USER_JOURNEYS.md
  - CHANGELOG.md
  - TASKS.md

- Completed Visitor User Journey Mapping.

- Converted Visitor goals into outcome-based MVP user journeys:
  - VJ-01 Discover Public Content
  - VJ-02 Explore Contributors
  - VJ-03 Explore Communities
  - VJ-04 Evaluate Community Quality
  - VJ-05 Evaluate Platform Relevance

- Defined for each journey:
  - Supported goals
  - Journey description
  - Trigger
  - Success state
  - Features involved
  - Dependencies
  - Notes

- Performed goal coverage validation.

- Confirmed all Visitor goals are covered by at least one journey.

- Performed journey overlap analysis and removed unnecessary duplication.

- Performed MVP feature coverage analysis for Visitor journeys.

- Confirmed Visitor journeys exercise public discovery and evaluation features while authenticated participation features remain exclusive to Members.

- Updated:
  - USER_JOURNEYS.md
  - CHANGELOG.md
  - TASKS.md

- Completed Member User Journey Mapping.

  - Added complete Member User Journey inventory.
  - Added Member journey coverage validation against approved Member goals.
  - Added Member journey validation against MVP feature inventory.
  - Added Visitor-to-Member journey relationship analysis.
  - Identified Member-exclusive journeys for MVP participation.

- Updated: 
  - USER_JOURNEYS.md
  - CHANGELOG.md
  - TASKS.md


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

- Completed MVP Herd Posting specification.

- Defined:
  - Herd Posting purpose
  - MVP posting requirements
  - Posting eligibility requirements
  - Supported content types
  - Post ownership and authorship rules
  - Herd-specific posting permissions
  - Post visibility requirements
  - Editing and deletion behavior
  - Moderation and governance requirements
  - Herd Membership integration
  - Comments and voting integration
  - Reporting requirements
  - Feature dependencies

- Resolved Herd Posting decisions:
  - Herd membership required for posting.
  - Herd posts are publicly visible.
  - Herd posts use the same content model as Personal Posts.
  - Herd post ownership remains with the author.
  - Edited Herd posts display an edited indicator.
  - Shepherds may moderate Herd posts but do not own member-created content.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Herd Feed specification.

- Defined:
  - Herd Feed purpose
  - MVP feed requirements
  - Content eligibility rules
  - Visibility and access requirements
  - Feed ordering requirements
  - Feed refresh behavior
  - Pagination and loading requirements
  - Herd Membership integration requirements
  - Herd Posting integration requirements
  - Moderation and governance requirements
  - Feed dependencies

- Resolved Herd Feed decisions:
  - Herd Feed uses chronological ordering in MVP.
  - Only Herd posts from joined Herds are eligible.
  - Herd Membership determines Herd Feed eligibility.
  - Real-time feed updates excluded from MVP.
  - Recommendation systems excluded from MVP.
  - Herd moderation removals remove content from Herd Feed visibility.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Reporting System specification.

- Defined:
  - Reporting System purpose
  - MVP reporting requirements
  - Reportable entities
  - Reporting eligibility requirements
  - Report categories and reasons
  - Report submission requirements
  - Report visibility requirements
  - Moderation workflow requirements
  - Shepherd responsibilities
  - Platform Administrator responsibilities
  - Report outcome requirements
  - Abuse prevention requirements
  - Feature dependencies
  - Future compatibility requirements

- Resolved Reporting System decision:
  - Shared governance reporting model selected.
  - User Profiles, Personal Posts, Herd Posts, Comments, Replies, and Herds are reportable entities.
  - Reports are private and not publicly visible.
  - Anonymous reporting is excluded from MVP.
  - Shepherds may review Herd-related reports.
  - Platform Administrators retain review and override authority for all reports.
  - Reporters should receive notifications when moderation action is taken on their reports once the Notifications system exists.
  - Report outcome notifications are excluded from MVP and deferred until Notifications are implemented.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Shepherd Moderation specification.

- Defined:
  - Shepherd Moderation purpose
  - Shepherd authority and responsibilities
  - Community moderation requirements
  - Membership management requirements
  - Content moderation requirements
  - Escalation requirements
  - Relationship with Platform Administrators
  - Audit and accountability requirements
  - Abuse prevention requirements
  - Feature dependencies
  - Future compatibility requirements

- Resolved Shepherd Moderation decisions:
  - Shared governance moderation model selected.
  - Shepherd authority limited to their Herd.
  - Shepherds may remove Herd posts, comments, replies, and members.
  - Shepherds may review and dismiss Herd-related reports.
  - Shepherds may escalate reports and moderation disputes to Herd Owners.
  - Herd Owners may escalate platform-level matters to Platform Administrators.
  - Platform Administrators retain final override authority.
  - Platform-wide enforcement remains exclusive to Platform Administrators.

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Platform Moderation specification.

- Defined:
  - Platform Moderation purpose
  - Platform-wide moderation requirements
  - Platform Administrator authority
  - Platform moderation scope
  - Relationship with Herd Owners and Shepherds
  - Escalation requirements
  - User account moderation requirements
  - Content moderation requirements
  - Community moderation requirements
  - Enforcement actions
  - Audit and accountability requirements
  - Abuse prevention requirements
  - Feature dependencies
  - Future compatibility requirements

- Resolved Platform Moderation decisions:
  - Layered governance model selected.
  - Platform Administrators retain final moderation authority.
  - Platform Administrators may review any report and moderation action.
  - Platform Administrators may issue account warnings.
  - Platform Administrators may suspend accounts.
  - Platform Administrators may issue platform bans.
  - Platform Administrators may override Herd Owner and Shepherd decisions.
  - Escalation hierarchy defined as:
        Report → Shepherd → Herd Owner → Platform Administrator

- Updated:
  - FEATURES.md
  - QUESTIONS.md
  - CHANGELOG.md
  - TASKS.md

- Completed MVP Image Uploads specification.

- Defined:
  - Image Upload purpose.
  - MVP image upload requirements.
  - Supported upload locations.
  - Image ownership requirements.
  - Image visibility requirements.
  - Image moderation requirements.
  - Upload restrictions and limits.
  - Image lifecycle requirements.
  - Feature dependencies.
  - Future compatibility requirements.

- Resolved Image Upload decisions:
  - Images included in MVP.
  - Images supported in Personal Posts.
  - Images supported in Herd Posts.
  - Profile pictures supported.
  - Herd avatars supported.
  - Images inherit visibility from parent content.
  - Images are moderated through existing moderation systems.
  - Images are not standalone reportable entities.
  - Anonymous image uploads excluded.

- Expanded Image Uploads scope:
  - Profile cover images added to MVP.
  - Herd cover images added to MVP.

- Updated User Profile specification:
  - Profile customization now includes optional cover images.

- Updated Herd Creation specification:
  - Herd metadata now supports optional cover images.

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