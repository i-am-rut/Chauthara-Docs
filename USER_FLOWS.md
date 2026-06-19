# User Flows

## VF-01: Discover Public Content

## Related Journey: VJ-01 Discover Public Content

## Primary Actor: Visitor

## Preconditions

Public content exists on the platform.
Visitor has access to the platform.
Content is publicly visible.

## Trigger

Visitor arrives on Chauthara through a direct visit, referral, shared link, or search result.

## Main Flow

Visitor accesses the platform.
Visitor views publicly visible content.
Visitor opens a post that appears interesting.
Visitor reads the post content.
Visitor reviews comments and replies associated with the post.
Visitor optionally opens additional posts.
Visitor continues browsing public discussions.
Visitor identifies content that demonstrates platform value.

## Alternative Flows

### AF-01: Visitor Opens Shared Content Directly
Visitor arrives through a direct post link.
Visitor reads the content.
Visitor explores related discussions.
Visitor continues browsing additional public content.
### AF-02: Visitor Finds Content Uninteresting
Visitor reviews several posts.
Visitor determines available content is not relevant.
Visitor exits the platform.

## Success State

Visitor discovers content that demonstrates discussion quality and platform value.

## Failure State

Visitor fails to find relevant or valuable content and leaves the platform.

## Features Involved

Personal Posting
Herd Posting
Comments & Replies
Image Uploads

---

## VF-02: Explore Contributors

## Related Journey: VJ-02 Explore Contributors

## Primary Actor: Visitor

## Preconditions

Public user profiles exist.
Public contribution history is visible.

## Trigger

Visitor encounters a contributor through a post, comment, or reply.

## Main Flow

Visitor encounters content created by a contributor.
Visitor opens the contributor's profile.
Visitor reviews profile information.
Visitor reviews the contributor's public posts.
Visitor reviews the contributor's public discussion participation.
Visitor reviews audience indicators and public relationships.
Visitor evaluates contributor credibility and relevance.
Visitor identifies the contributor as a potential future follow target.

## Alternative Flows

### AF-01: Contributor Has Limited Public Activity
Visitor opens a profile.
Visitor finds insufficient public activity.
Visitor returns to content browsing.
### AF-02: Contributor Not Relevant
Visitor reviews profile activity.
Visitor determines contributor is not relevant.
Visitor continues exploring other contributors.

## Success State

Visitor identifies one or more contributors worth following after registration.

## Failure State

Visitor fails to identify contributors that justify future participation.

## Features Involved

User Profiles
Personal Posting
Comments & Replies
Follow System (public visibility aspects)

---

## VF-03: Explore Communities

## Related Journey: VJ-03 Explore Communities

## Primary Actor: Visitor

## Preconditions

Public Herds exist.
Public Herd information is visible.

## Trigger

Visitor wants to discover topic-focused communities.

## Main Flow

Visitor discovers a Herd.
Visitor opens the Herd page.
Visitor reviews Herd identity and purpose.
Visitor reviews Herd rules.
Visitor reviews Herd membership information.
Visitor reviews recent Herd content.
Visitor explores additional Herds.
Visitor identifies one or more Herds aligned with personal interests.

## Alternative Flows

### AF-01: Herd Does Not Match Interests
Visitor reviews Herd information.
Visitor determines the topic is not relevant.
Visitor returns to community exploration.
### AF-02: Herd Has Limited Activity
Visitor reviews Herd content.
Visitor determines community activity is insufficient.
Visitor continues exploring other Herds.

## Success State

Visitor identifies one or more communities that appear relevant and worth joining.

## Failure State

Visitor fails to find any community aligned with personal interests.

## Features Involved

Herd Creation
Herd Membership
Herd Posting
Image Uploads

---

## VF-04: Evaluate Community Quality

## Related Journey: VJ-04 Evaluate Community Quality

## Primary Actor: Visitor

## Preconditions

Public Herd discussions are available.
Community rules are visible.
Shepherd identities are visible.

## Trigger

Visitor enters a Herd that appears relevant.

## Main Flow

Visitor opens a Herd.
Visitor reviews community rules.
Visitor reviews recent Herd posts.
Visitor reviews comments and replies within discussions.
Visitor observes discussion tone and participation quality.
Visitor reviews visible moderation presence.
Visitor evaluates whether discussions appear constructive and healthy.
Visitor forms an opinion regarding community quality.

## Alternative Flows

### AF-01: Community Appears Low Quality
Visitor observes disruptive or low-value discussions.
Visitor determines the community is not suitable.
Visitor exits the Herd and continues exploration.
### AF-02: Insufficient Activity For Evaluation
Visitor reviews available discussions.
Visitor finds insufficient activity for assessment.
Visitor postpones evaluation or explores another Herd.

## Success State

Visitor determines whether the community demonstrates constructive participation and healthy governance.

## Failure State

Visitor cannot confidently assess community quality.

## Features Involved

Herd Posting
Comments & Replies
Shepherd Moderation
Herd Creation

---

## VF-05: Evaluate Platform Relevance

## Related Journey: VJ-05 Evaluate Platform Relevance

## Primary Actor: Visitor

## Preconditions

Visitor has completed one or more discovery-oriented flows.

## Trigger

Visitor wants to determine whether Chauthara is worth joining.

## Main Flow

Visitor reflects on discovered content.
Visitor evaluates contributors encountered.
Visitor evaluates communities explored.
Visitor evaluates discussion quality observed.
Visitor compares findings against personal interests and expectations.
Visitor makes a participation decision.
Visitor either proceeds toward registration or leaves the platform.

## Alternative Flows

### AF-01: Positive Evaluation
Visitor determines sufficient value exists.
Visitor decides to create an account.
Visitor transitions toward Member onboarding.
### AF-02: Negative Evaluation
Visitor determines insufficient value exists.
Visitor leaves the platform.
### AF-03: Deferred Decision
Visitor remains undecided.
Visitor continues exploration activities.
Evaluation is postponed.

## Success State

Visitor reaches a clear decision regarding platform participation.

## Failure State

Visitor remains unconvinced of platform value and abandons evaluation.

## Features Involved

User Profiles
Personal Posting
Herd Posting
Comments & Replies
Herd Creation
Herd Membership

---

## Flow Relationship
VF-01 Discover Public Content
            ↓
     VF-02 Explore Contributors
            ↓
      VF-03 Explore Communities
            ↓
   VF-04 Evaluate Community Quality
            ↓
    VF-05 Evaluate Platform Relevance
            ↓
      Create Account (Member)

---
