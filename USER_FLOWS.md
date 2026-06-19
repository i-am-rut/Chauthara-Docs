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

## Visitor Flow Relationship
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

## MF-01: Consume Followed User Content
## Related Journey: MJ-01 Consume Followed User Content
## Primary Actor: Member
## Preconditions

Authenticated account exists.
Member follows at least one user.
Eligible content exists in the Following Feed.

## Trigger

Member wants to view activity from followed users.

## Main Flow

Member accesses the Following Feed.
Member views content from followed users.
Member opens a post that appears relevant.
Member reads the post content.
Member optionally reviews comments and replies.
Member returns to the feed.
Member continues consuming followed-user content.

## Alternative Flows
### AF-01: No Followed Users

Member accesses the Following Feed.
No eligible content is available.
Member chooses to discover users to follow.

### AF-02: No New Content

Member accesses the Following Feed.
No recent eligible content exists.
Member refreshes the feed or explores other platform areas.

## Success State

Member successfully consumes relevant content from followed users.

## Failure State

Member cannot access relevant content through the Following Feed.

## Features Involved

Following Feed
Follow System
Personal Posting
Comments & Replies

---

## MF-02: Discover And Follow Interesting People
## Related Journey: MJ-02 Discover And Follow Interesting People
## Primary Actor: Member
## Preconditions

Authenticated account exists.
Public profiles are available.

## Trigger

Member discovers a contributor worth evaluating.

## Main Flow

Member encounters a contributor through content or discussion.
Member opens the contributor profile.
Member reviews profile information.
Member reviews contribution history.
Member decides to follow the contributor.
Member creates a follow relationship.
Contributor becomes part of future Following Feed eligibility.

## Alternative Flows
### AF-01: Contributor Not Relevant

Member reviews the profile.
Member decides not to follow.
Member continues exploring other contributors.

### AF-02: Already Following Contributor

Member opens the profile.
Member confirms an active follow relationship already exists.
Member returns to content consumption.

## Success State

A follow relationship is successfully established.

## Failure State

Member does not identify any contributor worth following.

## Features Involved

User Profiles
Follow System
Personal Posting
Comments & Replies

---

## MF-03: Publish A Personal Post
## Related Journey: MJ-03 Publish A Personal Post
## Primary Actor: Member
## Preconditions

Authenticated active account exists.

## Trigger

Member wants to share an idea, opinion, question, or experience.

## Main Flow

Member starts creating a personal post.
Member enters post content.
Member optionally adds an image.
Member reviews the post.
Member publishes the post.
The post becomes publicly visible.
The post appears on the member profile.
Eligible followers may consume the post through the Following Feed.

## Alternative Flows
### AF-01: Text-Only Post

Member creates and publishes a text-only post.

### AF-02: Image-Enhanced Post

Member creates a post containing text and an image.

### AF-03: Member Abandons Creation

Member starts creating content.
Member decides not to publish.
No post is created.

## Success State

Personal post is successfully published and publicly visible.

## Failure State

The post is not published.

## Features Involved

Personal Posting
User Profiles
Image Uploads

---

## MF-04: Participate In A Discussion
## Related Journey: MJ-04 Participate In A Discussion
## Primary Actor: Member
## Preconditions

An eligible post exists.
Authenticated account exists.

## Trigger

Member wants to respond to existing content.

## Main Flow

Member opens a discussion.
Member reviews existing conversation.
Member creates a comment or reply.
Member submits the contribution.
Contribution becomes part of the discussion thread.
Other participants may view the contribution.

## Alternative Flows
### AF-01: Comment On Post

Member responds directly to a post.

### AF-02: Reply Within Discussion

Member responds to an existing comment or reply.

### AF-03: Member Cancels Participation

Member begins composing a response.
Member decides not to submit it.

## Success State

Contribution becomes part of the discussion.

## Failure State

No discussion contribution is created.

## Features Involved

Comments & Replies

---

## MF-05: Evaluate Content Through Voting
## Related Journey: MJ-05 Evaluate Content Through Voting
## Primary Actor: Member
## Preconditions

Authenticated account exists.
Eligible content exists.

## Trigger

Member encounters content worth evaluating.

## Main Flow

Member views a post, comment, or reply.
Member decides to express feedback.
Member selects HypeUp or HypeDown.
Vote is recorded.
Updated vote totals become visible.

## Alternative Flows
### AF-01: Change Existing Vote

Member changes a previous vote.
The new vote replaces the old vote.

### AF-02: Remove Existing Vote

Member removes a previously submitted vote.
Content returns to a no-vote state for that member.

### AF-03: No Vote Submitted

Member evaluates content.
Member chooses not to vote.

## Success State

Member feedback is successfully recorded.

## Failure State

No vote is recorded.

## Features Involved

HypeUp / HypeDown Voting

---

## MF-06: Build A Personal Profile
## Related Journey: MJ-06 Build A Personal Profile
## Primary Actor: Member
## Preconditions

Authenticated account exists.
Profile exists.

## Trigger

Member wants to improve profile presentation.

## Main Flow

Member accesses profile settings.
Member updates profile information.
Member optionally updates profile image.
Member optionally updates cover image.
Member updates bio information.
Member saves changes.
Updated profile becomes publicly visible.

## Alternative Flows
### AF-01: Profile Image Update

Member updates only profile image.

### AF-02: Bio Update

Member updates only profile information.

### AF-03: No Changes Saved

Member reviews profile settings.
Member exits without making changes.

## Success State

Profile accurately reflects the member's desired public identity.

## Failure State

Profile remains unchanged.

## Features Involved

User Profiles
Image Uploads

--- 

## MF-07: Join A Herd Community
## Related Journey: MJ-07 Join A Herd Community
## Primary Actor: Member
## Preconditions

Authenticated active account exists.
Target Herd exists and is active.

## Trigger

Member discovers a Herd aligned with personal interests.

## Main Flow

Member opens a Herd.
Member reviews Herd information and rules.
Member decides to join.
Membership is created.
Member gains Herd membership.
Future Herd participation becomes available.

## Alternative Flows
### AF-01: Member Decides Not To Join

Member reviews Herd information.
Member decides not to join.

### AF-02: Already A Member

Member opens the Herd.
Member is already a member.
No membership change occurs.

## Success State

Active Herd membership is established.

## Failure State

Member does not become part of the Herd.

## Features Involved

Herd Creation
Herd Membership

---

## MF-08: Consume Community Content
## Related Journey: MJ-08 Consume Community Content
## Primary Actor: Member
## Preconditions

Authenticated account exists.
Member belongs to at least one Herd.
Eligible Herd content exists.

## Trigger

Member wants to stay informed about community activity.

## Main Flow

Member accesses the Herd Feed.
Member reviews content from joined Herds.
Member opens relevant Herd posts.
Member reads community discussions.
Member continues consuming Herd content.

## Alternative Flows
### AF-01: No Joined Herds

Member accesses the Herd Feed.
No eligible content exists.
Member explores Herds to join.

### AF-02: No Recent Herd Activity

Member accesses the Herd Feed.
Little or no recent content exists.
Member explores individual Herd pages.

## Success State

Member successfully consumes relevant community content.

## Failure State

Member cannot access meaningful community activity.

## Features Involved

Herd Membership
Herd Feed
Herd Posting
Comments & Replies

---

## MF-09: Contribute To A Herd
## Related Journey: MJ-09 Contribute To A Herd
## Primary Actor: Member
## Preconditions

Authenticated active account exists.
Member belongs to the target Herd.

## Trigger

Member wants to contribute to a community discussion.

## Main Flow

Member accesses a joined Herd.
Member creates a Herd post.
Member optionally adds an image.
Member reviews the content.
Member publishes the Herd post.
Post becomes publicly visible.
Post becomes available within Herd participation surfaces.

## Alternative Flows
### AF-01: Text-Only Herd Post

Member publishes a text-only Herd post.

### AF-02: Image-Enhanced Herd Post

Member publishes a Herd post containing an image.

### AF-03: Member Cancels Creation

Member begins creating a Herd post.
Member decides not to publish.

## Success State

Herd post is successfully published.

## Failure State

No Herd contribution is created.

## Features Involved

Herd Membership
Herd Posting
Image Uploads

---

## MF-10: Help Maintain Community Quality
## Related Journey: MJ-10 Help Maintain Community Quality
## Primary Actor: Member
## Preconditions

Authenticated active account exists.
A reportable entity exists.

## Trigger

Member encounters content, behavior, or a community believed to violate rules or policies.

## Main Flow

Member identifies a reportable entity.
Member initiates a report.
Member selects an appropriate report reason.
Member optionally provides additional context.
Member submits the report.
Report enters the moderation review process.
Member receives submission confirmation.

## Alternative Flows
### AF-01: Report Content

Member reports a post, comment, or reply.

### AF-02: Report Profile

Member reports a user profile.

### AF-03: Report Herd

Member reports a Herd.

### AF-04: Member Abandons Report

Member begins the reporting process.
Member decides not to submit.

## Success State

Report is successfully submitted for review.

## Failure State

No report is submitted.

## Features Involved

Reporting System

---

## Member Flow Relationship
MF-01 Consume Followed User Content
            ↓
MF-02 Discover And Follow Interesting People
            ↓
MF-03 Publish A Personal Post
            ↓
MF-04 Participate In A Discussion
            ↓
MF-05 Evaluate Content Through Voting

MF-07 Join A Herd Community
            ↓
MF-08 Consume Community Content
            ↓
MF-09 Contribute To A Herd

MF-06 Build A Personal Profile
            ↓
Supports Identity Across All Member Flows

MF-10 Help Maintain Community Quality
            ↓
Supports Platform Governance Across All Member Flows

---

## HOF-01: Create A Herd
## Related Journey: HOJ-01 Create A Herd
## Primary Actor: Herd Owner
## Preconditions

Authenticated active Member account exists.

## Trigger

Member decides to create a new community.

## Main Flow

Member initiates Herd creation.
Member provides Herd identity information.
Member reviews default community rules.
Member optionally adds community imagery.
Member submits the Herd.
The Herd is created.
Member becomes the Herd Owner.
The Herd becomes publicly visible and available for membership.

## Alternative Flows
### AF-01: Herd Created Without Images

Member creates the Herd without optional images.

### AF-02: Creation Abandoned

Member begins Herd creation.
Member exits before submission.
No Herd is created.

## Success State

A new active Herd exists with the creator assigned as Herd Owner.

## Failure State

No Herd is created.

## Features Involved

Herd Creation
Image Uploads

---

## HOF-02: Define Community Identity
## Related Journey: HOJ-02 Define Community Identity
## Primary Actor: Herd Owner
## Preconditions

Active Herd exists.
Actor is the Herd Owner.

## Trigger

Owner wants to establish or refine community identity.

## Main Flow

Owner accesses Herd management capabilities.
Owner reviews current Herd information.
Owner updates community description.
Owner updates community rules.
Owner optionally updates Herd avatar.
Owner optionally updates Herd cover image.
Owner saves changes.
Updated Herd identity becomes visible.

## Alternative Flows
### AF-01: Rules Update Only

Owner modifies community rules only.

### AF-02: Visual Identity Update Only

Owner updates Herd imagery only.

### AF-03: No Changes Saved

Owner reviews configuration.
Owner exits without saving.

## Success State

Community identity accurately reflects the Herd purpose and expectations.

## Failure State

Community identity remains unchanged.

## Features Involved

Herd Creation
Image Uploads

---

## HOF-03: Grow Community Participation
## Related Journey: HOJ-03 Grow Community Participation
## Primary Actor: Herd Owner
## Preconditions

Active Herd exists.
Community membership exists.

## Trigger

Owner wants to increase community activity and participation.

## Main Flow

Owner reviews current community activity.
Owner contributes community content.
Owner participates in discussions.
Members engage with Herd content.
Additional participation occurs.
Community activity increases.
The Herd attracts ongoing contributions.

## Alternative Flows
### AF-01: Content-Led Growth

Owner publishes Herd content that encourages participation.

### AF-02: Discussion-Led Growth

Owner actively participates in existing discussions.

### AF-03: Limited Community Response

Owner contributes content.
Participation growth does not occur immediately.

## Success State

Community participation and engagement increase.

## Failure State

Community activity remains stagnant.

## Features Involved

Herd Membership
Herd Posting
Herd Feed
Comments & Replies

---

## HOF-04: Delegate Community Governance
## Related Journey: HOJ-04 Delegate Community Governance
## Primary Actor: Herd Owner
## Preconditions

Active Herd exists.
Owner authority exists.
Eligible community members exist.

## Trigger

Owner determines additional moderation support is required.

## Main Flow

Owner reviews community participation.
Owner identifies a suitable member.
Owner appoints the member as a Shepherd.
The member receives Shepherd authority within the Herd.
Moderation responsibilities become shared.
Community governance capacity increases.

## Alternative Flows
### AF-01: Multiple Shepherd Appointments

Owner appoints more than one Shepherd.

### AF-02: No Suitable Candidate

Owner reviews members.
No appointment is made.

### AF-03: Existing Shepherd Team Sufficient

Owner reviews governance needs.
No governance changes occur.

## Success State

One or more Shepherds actively support community moderation.

## Failure State

No governance delegation occurs.

## Features Involved

Herd Creation
Shepherd Moderation

---

## HOF-05: Oversee Community Health
## Related Journey: HOJ-05 Oversee Community Health
## Primary Actor: Herd Owner
## Preconditions

Active Herd exists.
Community activity exists.

## Trigger

Owner performs routine governance oversight or identifies community concerns.

## Main Flow

Owner reviews Herd activity.
Owner reviews discussions and participation trends.
Owner reviews moderation outcomes.
Owner reviews reports affecting the community.
Owner evaluates whether activity aligns with community rules and purpose.
Owner identifies governance concerns when necessary.
Owner determines whether corrective action or guidance is needed.

## Alternative Flows
### AF-01: Community Operating Normally

Owner reviews activity.
No intervention is required.

### AF-02: Governance Concern Identified

Owner identifies moderation or participation concerns.
Owner initiates further review.

### AF-03: Community Rule Adjustments Needed

Owner determines existing rules are insufficient.
Owner updates community guidance.

## Success State

Community remains aligned with its purpose, rules, and governance expectations.

## Failure State

Community health concerns remain unresolved.

## Features Involved

Herd Posting
Comments & Replies
Reporting System
Shepherd Moderation

---

## HOF-06: Resolve Community Moderation Disputes
## Related Journey: HOJ-06 Resolve Community Moderation Disputes
## Primary Actor: Herd Owner
## Preconditions

Active Herd exists.
Moderation dispute, escalation, or contested decision exists.

## Trigger

A matter is escalated to the Herd Owner.

## Main Flow

Owner receives an escalation.
Owner reviews the dispute or moderation decision.
Owner reviews relevant reports and context.
Owner evaluates whether the original decision was appropriate.
Owner reaches a governance decision.
Owner either upholds or reverses the prior decision.
If platform-level review is required, the matter is escalated.
The dispute reaches resolution.

## Alternative Flows
### AF-01: Decision Upheld

Owner determines original moderation action was appropriate.

### AF-02: Decision Reversed

Owner determines original moderation action should be reversed.

### AF-03: Escalation To Platform Administrators

Owner determines platform-level review is required.
Matter is escalated.

## Success State

Dispute is resolved or successfully escalated to Platform Administrators.

## Failure State

Dispute remains unresolved.

## Features Involved

Reporting System
Shepherd Moderation
Platform Moderation

---

## Herd Owner Flow Relationship
Inherited Member Flows
MJ-01 through MJ-10
            ↓

HOF-01 Create A Herd
            ↓
HOF-02 Define Community Identity
            ↓
HOF-03 Grow Community Participation
            ↓
HOF-04 Delegate Community Governance
            ↓
HOF-05 Oversee Community Health
            ↓
HOF-06 Resolve Community Moderation Disputes
            ↓
Platform Governance Escalation

---

## SF-01: Moderate Herd Content
## Related Journey: SHJ-01 Moderate Herd Content
## Primary Actor: Shepherd
## Preconditions

Active Herd exists.

Actor has Shepherd authority within the Herd.

Eligible Herd content exists.

## Trigger

Shepherd identifies content that may violate Herd rules or disrupt constructive participation.

## Main Flow

Shepherd reviews a Herd post, comment, or reply.

Shepherd evaluates the content against Herd rules.

Shepherd determines that moderation action is required.

Shepherd removes the violating content.

Removed content is no longer visible through normal Herd participation surfaces.

Community discussion continues without the violating content.

## Alternative Flows
### AF-01: Herd Post Removal

Shepherd removes a Herd post that violates community rules.

### AF-02: Comment Or Reply Removal

Shepherd removes a comment or reply that violates community rules.

### AF-03: No Violation Found

Shepherd reviews the content.

Shepherd determines no action is required.

Content remains visible.

## Success State

Violating content is removed from normal Herd visibility surfaces.

## Failure State

Problematic content remains visible despite requiring moderation.

## Features Involved

Herd Posting

Comments & Replies

Shepherd Moderation

---

## SF-02: Review Community Reports
## Related Journey: SHJ-02 Review Community Reports
## Primary Actor: Shepherd
## Preconditions

Actor has Shepherd authority within the Herd.

At least one eligible report exists.

## Trigger

A report enters the Herd moderation review process.

## Main Flow

Shepherd opens a report.

Shepherd reviews the reported content or behavior.

Shepherd reviews available report context.

Shepherd evaluates whether a violation occurred.

Shepherd reaches a moderation determination.

Shepherd dismisses the report, applies community moderation, or escalates the matter.

The report review process concludes.

## Alternative Flows
### AF-01: Report Dismissed

Shepherd determines no violation occurred.

Report is dismissed.

### AF-02: Community Enforcement Applied

Shepherd determines a community rule violation occurred.

Appropriate community moderation action is applied.

### AF-03: Escalation Required

Shepherd determines the matter exceeds community authority.

Matter is escalated.

## Success State

Report is reviewed and reaches an appropriate outcome.

## Failure State

Report remains unresolved.

## Features Involved

Reporting System

Shepherd Moderation

---

## SF-03: Moderate Community Membership
## Related Journey: SHJ-03 Moderate Community Membership
## Primary Actor: Shepherd
## Preconditions

Active Herd exists.

Actor has Shepherd authority within the Herd.

Target member belongs to the Herd.

## Trigger

A member repeatedly violates community rules or participation standards.

## Main Flow

Shepherd reviews member behavior.

Shepherd determines continued participation is harmful to the community.

Shepherd removes the member from the Herd.

Member loses Herd membership.

Member loses future participation eligibility within the Herd.

Previously authored content remains attributable to the original author.

## Alternative Flows
### AF-01: Community Warning Through Guidance

Shepherd reviews member behavior.

Shepherd determines removal is not yet necessary.

Member remains in the Herd.

### AF-02: Immediate Removal

Severe community disruption is identified.

Shepherd removes the member without further participation.

### AF-03: No Violation Found

Shepherd reviews the situation.

No membership action is taken.

## Success State

Community participation standards are protected through appropriate membership moderation.

## Failure State

A disruptive member remains in the Herd despite requiring moderation.

## Features Involved

Herd Membership

Shepherd Moderation

---

## SF-04: Guide Constructive Participation
## Related Journey: SHJ-04 Guide Constructive Participation
## Primary Actor: Shepherd
## Preconditions

Active Herd discussions exist.

Actor has Shepherd authority within the Herd.

## Trigger

Routine community stewardship or emerging discussion-quality concerns.

## Main Flow

Shepherd reviews ongoing discussions.

Shepherd identifies participation patterns affecting discussion quality.

Shepherd provides community guidance through visible moderation presence.

Community members continue participating.

Discussion quality remains aligned with Herd expectations.

Community participation remains constructive.

## Alternative Flows
### AF-01: Healthy Discussion Environment

Shepherd observes discussions.

No additional intervention is required.

### AF-02: Early Guidance Prevents Escalation

Shepherd identifies emerging concerns.

Guidance is provided.

Formal moderation becomes unnecessary.

### AF-03: Guidance Insufficient

Discussion quality continues to decline.

Formal moderation activity becomes necessary.

## Success State

Discussions remain constructive and aligned with community expectations.

## Failure State

Discussion quality deteriorates despite moderation guidance.

## Features Involved

Herd Posting

Comments & Replies

Shepherd Moderation

---

## SF-05: Escalate Serious Community Issues
## Related Journey: SHJ-05 Escalate Serious Community Issues
## Primary Actor: Shepherd
## Preconditions

Actor has Shepherd authority within the Herd.

A report, violation, moderation dispute, or governance concern exists.

The matter exceeds Shepherd authority.

## Trigger

Shepherd identifies a matter requiring higher-level review.

## Main Flow

Shepherd reviews the issue.

Shepherd determines the matter exceeds community moderation authority.

Shepherd prepares escalation context.

Matter is escalated to the Herd Owner.

The Herd Owner reviews the matter.

If platform-level review is required, the matter is escalated further.

Appropriate authority assumes responsibility for resolution.

## Alternative Flows
### AF-01: Herd Owner Resolution

Matter is escalated.

Herd Owner resolves the issue.

### AF-02: Platform-Level Escalation

Matter requires platform review.

Herd Owner escalates the matter to Platform Administrators.

### AF-03: Direct Administrative Review

Platform Administrators directly assume review responsibility when necessary.

## Success State

Matter is successfully transferred to the appropriate authority for resolution.

## Failure State

Serious issue remains unresolved or unreviewed.

## Features Involved

Reporting System
Shepherd Moderation
Platform Moderation

---

## Shepherd Flow Relationship 
Inherited Member Flows
MF-01 through MF-10
      ↓
SF-04 Guide Constructive Participation
      ↓
SF-01 Moderate Herd Content
      ↓
SF-02 Review Community Reports
      ↓
SF-03 Moderate Community Membership
      ↓
SF-05 Escalate Serious Community Issues
      ↓
Herd Owner Governance Review
      ↓
Platform Governance Review

---

