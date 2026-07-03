# Landing Page
## Screen ID
LP-001

## Screen Name
Landing Page

## Purpose

Introduce Chauthara to visitors.

Allow visitors to:

Understand platform purpose
Understand platform philosophy
Explore public content
Explore public communities
Explore public members
Register
Login

The Landing Page exists to answer:

"Why should I join Chauthara?"

before asking users to create an account.

## User Types
Primary
Visitor
Secondary
Authenticated Member

Authenticated users should be redirected away from the Landing Page to their default experience.

## User Goals

Visitors should be able to:

Understand Chauthara

Understand what makes it different

See examples of activity

See examples of communities

See examples of people

Create an account

Sign in

## Allowed Actions
Visitor

Allowed:

View Landing Page

View About Page

View Public Herd Preview

View Public Member Preview

View Public Discussion Preview

Navigate to Login

Navigate to Register

Not Allowed:

Create Point

Create Herd

Comment

Vote

Follow

Join Herd

## Information Architecture

Landing Page consists of:

1. Header

2. Hero Section

3. Why Chauthara Section

4. How Chauthara Works Section

5. Recent Discussions Section

6. Explore Herds Section

7. Community Voices Section

8. Final CTA Section

9. Footer

## Section 1 — Header
Purpose

Primary navigation.

Contents
Left
Logo
Platform Name

Center
Home

Herds

People

About
Right
Sign In

Create Account
Mobile Behavior

Desktop navigation collapses into:

Hamburger Menu

Menu contains:

Home

Herds

People

About

Sign In

Create Account
Component Ownership
Shared
shared/components/ui/Button
Custom
modules/landing/components/LandingHeader
modules/landing/components/MobileNavigation

## Section 2 — Hero Section
Purpose

Immediately communicate platform value.

Background

Use community gathering imagery.

Characteristics:

Warm

Inviting

Knowledge Sharing

Discussion

Community

The Chauthara tree imagery is approved as thematic inspiration.

Content
Headline
Speak.
Learn.
Grow.
Together.
Supporting Text
Your voice matters.

Share ideas, join communities,
and build meaningful connections.
CTA Buttons
Create Account

Sign In
Component Ownership
Shared
Button
Custom
HeroSection
HeroBackground

## Section 3 — Why Chauthara
Purpose

Explain platform philosophy.

Cards
Identity First
People follow people.

Build your audience and presence.
Community Driven
Join topic-focused Herds.

Learn, share, and grow together.
Meaningful Discussion
Thoughtful conversations.

Quality over noise.
Component Ownership
Shared
Card
Custom
ValuePillarCard

## Section 4 — How Chauthara Works
Purpose

Teach platform mental model.

Cards
Points
Share your ideas.
Herds
Join communities.
Conversations
Discuss and learn.
Future Evolution

Future versions may include:

Aura

Reputation

Moderation

Not shown in MVP.

## Section 5 — Recent Discussions
Purpose

Demonstrate platform activity.

Data Source

MVP:

Latest public posts

NOT:

Trending

Recommended

Ranked

No ranking algorithms exist in MVP.

Card Contents
Title

Author

Created Time

Comment Count
CTA
View More

## Section 6 — Explore Herds
Purpose

Demonstrate community ecosystem.

Data Source
Featured Herds

Curated manually.

NOT:

Popular Herds

No popularity ranking exists.

Herd Card Contents
Name

Description

Member Count

Cover Image (optional)

## Section 7 — Community Voices
Purpose

Show examples of members.

Data Source
Featured Members

Manually selected.

NOT:

Interesting Contributors

No recommendation system exists.

Member Card Contents
Avatar

Username

Short Bio

## Section 8 — Final CTA
Purpose

Convert interested visitors.

Content
Ready to join the conversation?

Button:

Create Account

## Section 9 — Footer
Contents
About

Community Guidelines

Privacy Policy

Terms of Service

Contact

## Responsive Layout Rules
Mobile (<768px)
Single Column

Stacked Sections

Hamburger Navigation

Cards Full Width

Tablet (768px–1024px)
Two Column Card Grids

Expanded Hero

Partial Navigation

Desktop (>1024px)
Full Navigation

Three Column Discovery Sections

Large Hero

Wide CTA

## Design System Rules
Use Shared Components

From shadcn:

Button

Card

Separator

Sheet

Avatar

Badge

Skeleton

Location:

src/shared/components/ui/

Create Custom Components

Landing-specific:

LandingHeader

HeroSection

ValuePillarCard

HowItWorksCard

DiscussionPreviewCard

HerdPreviewCard

MemberPreviewCard

FinalCTASection

LandingFooter

Location:

src/modules/landing/components/

## Accessibility Requirements

Must support:

Keyboard Navigation

Screen Readers

Focus Indicators

Semantic Headings

Color Contrast Compliance

## Future Enhancements

Not MVP:

Personalized Discovery

Trending Discussions

Recommended Herds

Suggested Members

Global Search

Dynamic Landing Feed

## Backend Dependencies

Required:

Public Discussions Endpoint

Public Herds Endpoint

Public Members Endpoint

Future integration only.

Landing Page UI can initially use mock data.

# Registration Page

## Screen ID

ID-002

## Screen Name

Registration Page

---

## Purpose

Allow a visitor to create a Chauthara account.

The Registration Page exists to:

- Establish platform identity
- Create a new account
- Initiate email verification
- Begin the Identity Lifecycle

The Registration Page does not:

- Authenticate the user
- Complete onboarding
- Collect profile information
- Allow platform participation

Registration success transitions users into the Verification stage of the Identity Lifecycle.

---

## User Types

### Primary

Visitor

### Secondary

Unauthenticated User

---

## User Goals

Visitors should be able to:

- Create an account
- Understand why Chauthara exists
- Understand platform philosophy
- Submit registration information
- Begin email verification
- Navigate to Login if an account already exists

---

## Entry Points

### Landing Page

Header

Create Account

### Landing Page Hero

Create Account CTA

### Login Page

Don't have an account?

Create Account

---

## Exit Points

### Success

Verification Pending Screen

(ID-003)

### Alternative

Login Page

(ID-009)

---

## Allowed Actions

### Visitor

Allowed:

- Enter username
- Enter email
- Enter password
- Confirm password
- Accept age requirement
- Accept Terms of Service
- Submit registration
- Navigate to Login

Not Allowed:

- Access authenticated features
- Participate in discussions
- Join Herds
- Create content
- Follow users

---

## Information Architecture

Registration Page consists of:

1. Minimal Header

2. Registration Hero / Philosophy Panel

3. Registration Form

4. Alternative Authentication Action

5. Footer

---

## Section 1 — Minimal Header

### Purpose

Provide branding and navigation to Login.

---

### Contents

#### Left

Logo

Platform Name

#### Right

Already have an account?

Sign In

---

### Mobile Behavior

Same structure.

No expanded navigation.

No hamburger menu.

The Registration Page intentionally minimizes distractions.

---

### Component Ownership

#### Shared

Button

#### Custom

AuthHeader

Location:

src/modules/identity/components/auth/

---

## Section 2 — Registration Hero / Philosophy Panel

### Purpose

Reinforce Chauthara's purpose and values.

Provide context before account creation.

---

### Desktop Layout

Displayed alongside registration form.

Two-column layout:

```text
| Philosophy Panel | Registration Form |
```

---

### Mobile Layout

Displayed above registration form.

Single-column layout.

---

### Content

#### Headline

Join the conversation.

Build your identity.

---

#### Supporting Text

Create your account and become part of communities built around meaningful discussion and knowledge sharing.

---

### Value Cards

#### Identity First

Build a reputation through your own contributions.

---

#### Community Driven

Join Herds that match your interests.

---

#### Meaningful Discussion

Share ideas, ask questions, and learn from others.

---

### Visual Direction

Should communicate:

- Community
- Discussion
- Learning
- Participation

Should avoid:

- Influencer culture
- Follower counts
- Virality messaging
- Creator economy themes

---

### Component Ownership

#### Shared

Card

#### Custom

RegistrationHero

IdentityValueCard

Location:

src/modules/identity/components/auth/

---

## Section 3 — Registration Form

### Purpose

Collect information required to create an account.

---

### Form Fields

#### Username

Purpose:

Public identity.

Helper Text:

This will be your public username.

Validation:

- Required
- Unique
- Minimum length
- Maximum length

---

#### Email

Purpose:

Verification and account recovery.

Helper Text:

Used for account verification and account recovery.

Validation:

- Required
- Valid email format
- Unique

---

#### Password

Purpose:

Authentication credential.

Validation:

- Required
- Minimum security requirements

Helper Content:

Password Requirements:

- Minimum 8 characters
- One uppercase letter
- One lowercase letter
- One number

Live validation preferred.

---

#### Confirm Password

Purpose:

Prevent password entry mistakes.

Validation:

- Must match password

---

#### Age Confirmation

Component:

Checkbox

Label:

I confirm that I am at least 18 years old.

Validation:

Required

---

#### Terms Acceptance

Component:

Checkbox

Label:

I agree to the Terms of Service and Privacy Policy.

Validation:

Required

---

### Primary Action

Button:

Create Account

Behavior:

Disabled until:

- Form valid
- Age confirmed
- Terms accepted

---

### Loading State

Button Text:

Creating Account...

Behavior:

- Inputs disabled
- Submit disabled
- Spinner displayed

---

### Error Handling

Display inline validation errors.

Examples:

Username already taken.

Email already registered.

Passwords do not match.

You must accept the Terms of Service.

Avoid generic error messaging whenever possible.

---

### Component Ownership

#### Shared

Input

Button

Checkbox

Label

Card

Separator

#### Custom

RegisterForm

PasswordField

FormSection

Location:

src/modules/identity/components/auth/

---

## Section 4 — Alternative Authentication Action

### Purpose

Support existing users.

---

### Content

Already have an account?

Sign In

---

### Behavior

Navigate to:

ID-009

Login Page

---

### Component Ownership

#### Shared

Button

#### Custom

AuthRedirectSection

---

## Section 5 — Footer

### Purpose

Provide legal and informational links.

---

### Contents

Terms of Service

Privacy Policy

Community Guidelines

---

### Mobile Behavior

Stacked links.

---

### Desktop Behavior

Inline links.

---

### Component Ownership

#### Custom

AuthFooter

---

### Success Flow

Successful registration follows:

```text
Registration Form
        ↓
Create Account
        ↓
Account Created
        ↓
Verification Email Sent
        ↓
Verification Pending Screen

```

The user is NOT authenticated.

The user is NOT redirected into the platform.

The account remains in:

Pending Verification

state until email verification succeeds.

---

### Failure Scenarios

#### Username Already Exists

Display field-level error.

---

#### Email Already Exists

Display field-level error.

---

#### Password Validation Failure

Display field-level error.

---

#### Terms Not Accepted

Display field-level error.

---

#### Network Failure

Display form-level error.

Message:

Unable to create account.

Please try again.

---

### Responsive Layout Rules

#### Mobile (<768px)

Single Column

Structure:

```text
Header

Hero

Form

Login Link

Footer
```

Full-width inputs.

Full-width CTA.

---

#### Tablet (768px–1024px)

Single-column layout.

Expanded spacing.

Improved card presentation.

---

#### Desktop (>1024px)

Two-column layout.

```text
| Philosophy Panel | Registration Form |
```

Hero content remains visible during registration.

---

### Design System Rules

#### Use Shared Components

From shadcn:

Button

Input

Card

Checkbox

Label

Separator

Skeleton

---

#### Create Custom Components

Registration-specific:

AuthHeader

RegistrationHero

IdentityValueCard

RegisterForm

PasswordField

FormSection

AuthRedirectSection

AuthFooter

Location:

src/modules/identity/components/auth/

---

### Accessibility Requirements

Must support:

- Keyboard navigation
- Screen readers
- Focus indicators
- Semantic form labels
- Accessible error messaging
- Accessible checkbox interactions
- Color contrast compliance

---

### Backend Dependencies

Required APIs:

POST /auth/register

Future Integration:

Verification Email Workflow

Email Verification API

Resend Verification API

---

### Future Enhancements

Not MVP:

- Social sign-in
- Invite-based registration
- Interest selection
- Herd recommendations
- Profile completion wizard
- Avatar upload during registration

---

## Notes

Registration is intentionally minimal.

Profile creation, personalization, community discovery, and participation occur after account verification.

The Registration Page exists solely to establish identity and begin the verification lifecycle.

# Verification Pending Screen

## Screen ID

ID-003

## Screen Name

Verification Pending Screen

---

## Purpose

Guide newly registered users through the email verification process.

The Verification Pending Screen exists to:

- Confirm account creation
- Explain the verification requirement
- Guide the user to the next step
- Provide verification recovery actions
- Prevent confusion about account status

The screen is a transition point between:

```text
Registration
        ↓
Pending Verification
        ↓
Email Verification
        ↓
Account Activation
```

The Verification Pending Screen does not:

- Authenticate the user
- Allow platform access
- Complete onboarding
- Collect profile information

---

## User Types

### Primary

Pending Verification User

### Secondary

Recently Registered User

---

## User Goals

Users should be able to:

- Confirm account creation succeeded
- Understand why verification is required
- Know where the verification email was sent
- Understand what to do next
- Resend the verification email if necessary
- Navigate to Login after verification

---

## Entry Points

### Registration Page

Successful Registration

```text
Registration
        ↓
Account Created
        ↓
Verification Pending Screen
```

### Resend Verification Flow

Successful resend request.

---

## Exit Points

### Verification Link

User clicks verification link received via email.

Navigates to:

ID-004

Verification Processing Screen

### Alternative

Login Page

(ID-009)

---

## Allowed Actions

### Pending Verification User

Allowed:

- View verification instructions
- View registered email address
- Resend verification email
- Navigate to Login
- Wait for email delivery

Not Allowed:

- Access authenticated platform features
- Participate in discussions
- Create content
- Join Herds
- Follow users

---

## Information Architecture

Verification Pending Screen consists of:

1. Status Confirmation Section

2. Verification Instructions Section

3. Registered Email Section

4. Resend Verification Section

5. Secondary Actions Section

---

## Section 1 — Status Confirmation Section

### Purpose

Confirm registration success and communicate current account state.

---

### Contents

#### Status Icon

Success Indicator

```text
✓
```

#### Headline

Account Created

#### Supporting Text

Your Chauthara account has been created successfully.

---

### Visual Priority

Highest priority section.

Visible immediately upon page load.

---

### Component Ownership

#### Shared

Card

#### Custom

VerificationStatusCard

Location:

src/modules/identity/components/auth/

---

## Section 2 — Verification Instructions Section

### Purpose

Explain why verification is required and what must happen next.

---

### Contents

#### Headline

Verify your email to continue.

#### Supporting Text

Before you can sign in and participate on Chauthara, you must verify your email address.

---

### Instruction List

1. Open your email inbox.

2. Find the verification email.

3. Click the verification link.

4. Return to Chauthara and sign in.

---

### Component Ownership

#### Shared

Card

Separator

#### Custom

VerificationInstructions

Location:

src/modules/identity/components/auth/

---

## Section 3 — Registered Email Section

### Purpose

Show where the verification email was delivered.

---

### Contents

#### Label

Verification email sent to:

#### Email Display

Example:

```text
john@example.com
```

Optional future enhancement:

```text
jo***@gmail.com
```

Email masking is not required for MVP.

---

### Component Ownership

#### Shared

Card

#### Custom

VerificationEmailDisplay

---

## Section 4 — Resend Verification Section

### Purpose

Provide recovery path if verification email is not received.

---

### Contents

#### Helper Text

Didn't receive the email?

Check your spam or promotions folder first.

---

#### Primary Action

Button:

Resend Verification Email

---

### Cooldown Behavior

Button disabled during cooldown.

Example:

```text
Resend available in 60 seconds.
```

Cooldown duration determined by backend implementation.

---

### Resend Success Message

Example:

```text
Verification email sent successfully.
```

Displayed inline.

Toast optional.

---

### Resend Failure Message

Example:

```text
Unable to send verification email.

Please try again later.
```

Displayed inline.

---

### Component Ownership

#### Shared

Button

Alert

#### Custom

ResendVerificationSection

Location:

src/modules/identity/components/auth/

---

## Section 5 — Secondary Actions Section

### Purpose

Provide navigation options.

---

### Contents

#### Action

Back to Login

Destination:

ID-009

Login Page

---

### Future Actions

Not MVP:

Change Email Address

---

### Component Ownership

#### Shared

Button

#### Custom

VerificationActions

---

### Screen States

#### State 1

Verification Pending

Default state.

---

#### State 2

Resend Loading

Button text:

```text
Sending...
```

Inputs disabled.

---

#### State 3

Resend Success

Success message displayed.

---

#### State 4

Resend Failure

Error message displayed.

---

#### State 5

Cooldown Active

Resend disabled until cooldown expires.

---

### Success Flow

Successful flow:

```text
Registration
        ↓
Verification Pending
        ↓
Verification Email
        ↓
Verification Link Clicked
        ↓
Verification Processing
```

Navigates to:

ID-004

Verification Processing Screen

---

### Failure Scenarios

### Email Delivery Delay

User remains on Verification Pending Screen.

Resend option available.

---

### Verification Email Not Received

User may resend verification email.

---

### Resend Failure

Display inline error.

Remain on current screen.

---

### Invalid Navigation

If user accesses this page without registration context:

Redirect to:

Registration Page

or

Login Page

depending on implementation strategy.

---

## Responsive Layout Rules

### Mobile (<768px)

Single-column layout.

Structure:

```text
✓

Account Created

Verify your email to continue

Email Address

Instructions

Resend Verification

Back to Login
```

Full-width card.

Full-width actions.

Large touch targets.

---

### Tablet (768px–1024px)

Single-column centered layout.

Maximum content width:

```text
500px
```

Improved spacing.

---

### Desktop (>1024px)

Centered card layout.

Maximum content width:

```text
600px
```

Structure:

```text
Status

Instructions

Email

Resend

Actions
```

No side panels.

No secondary content.

---

## Design System Rules

### Use Shared Components

From shadcn:

Card

Button

Alert

Separator

Skeleton

---

### Create Custom Components

VerificationStatusCard

VerificationInstructions

VerificationEmailDisplay

ResendVerificationSection

VerificationActions

Location:

src/modules/identity/components/auth/

---

## Accessibility Requirements

Must support:

- Keyboard navigation
- Screen readers
- Focus indicators
- Accessible button states
- Accessible status messaging
- Accessible error messaging
- Color contrast compliance

---

## Backend Dependencies

Required APIs:

POST /auth/resend-verification

Future Verification APIs:

GET /auth/verify-email

Verification Token Validation

Verification Status Resolution

---

## Future Enhancements

Not MVP:

- Email inbox shortcuts
- Automatic verification detection
- Verification polling
- Change email address flow
- Deep-link sign in after verification
- Email provider detection

---

## Notes

This screen replaces the previously proposed Registration Success Screen.

Registration success and verification pending are treated as a single lifecycle state.

The user's only objective on this screen is to complete email verification.

The design intentionally minimizes distractions and focuses entirely on helping users activate their account.


# Identity Verification Screens
## Screen Family ID

ID-004 – ID-006

## Screen Family Name

Identity Verification Screens

## Purpose

Support the Email Verification stage of the Identity Lifecycle.

These screens exist to:

Inform users about verification status
Process email verification requests
Confirm successful verification
Handle verification failures
Guide users toward the next appropriate action

The Identity Verification Screens do not:

Authenticate users
Create accounts
Collect profile information
Grant platform participation

Email verification is a prerequisite for platform participation.

Unverified accounts are not considered eligible participants within the platform identity model.

## Lifecycle Position

Registration
↓
Verification Pending
↓
Verification Processing
↓
Verification Success

or

Registration
↓
Verification Pending
↓
Verification Processing
↓
Verification Failure

## Shared User Types
Primary

Unverified Member

Secondary

Visitor

Authenticated Member (Edge Cases)

## Shared User Goals

Users should be able to:

Understand verification status
Confirm account activation
Recover from verification failures
Request a replacement verification email
Continue into platform participation after verification

## Shared Authentication Navigation Rules

Authenticated User

May not access:

- Registration Page
- Login Page

Redirect:

Following Feed

---

Unauthenticated User

May not access:

- Profile Page
- Edit Profile Page
- Following Feed

Redirect:

Login Page

or

ID-012 Identity Error Resolution

depending on failure context.

---

Unverified User

May not access:

- Authenticated experiences
- Following Feed
- Profile Management

Redirect:

ID-003 Verification Pending

---

Access evaluation occurs only after
authentication state resolution.

Authoritative states:

- unknown
- authenticated
- unauthenticated

## Shared Layout Strategy

All verification screens use a common status-oriented layout.

Layout Characteristics
Centered content
Minimal distractions
Single primary task
Status-focused messaging
Strong visual feedback
Mobile-first presentation

## Shared Information Architecture

Verification screens consist of:

Status Icon
Status Title
Status Description
Verification Details
Primary Action Area
Secondary Action Area

## Shared Component Ownership
Shared Components

From:

src/shared/components/ui/

Use:

Card
Button
Alert
Separator
Skeleton
Custom Components

From:

src/modules/identity/components/

Create:

VerificationStatusLayout
VerificationStatusIcon
VerificationStatusContent
VerificationStatusActions

## Shared Responsive Layout Rules
Mobile (<768px)
Single column layout
Full-width card
Stacked actions
Tablet (768px–1024px)
Centered card
Maximum width 500px
Desktop (>1024px)
Centered card
Maximum width 600px
Comfortable whitespace

## Shared Accessibility Requirements

Must support:

Keyboard navigation
Screen readers
Focus indicators
Semantic headings
Color contrast compliance
Status announcements

Status changes must be announced to assistive technologies.

## Backend Dependencies

Required:

Verify Email API
Resend Verification API

Identity verification is part of the approved Identity lifecycle and Identity module implementation sequence.

# Verification Processing Page
## Screen ID

ID-004

## Screen Name

Verification Processing

## Purpose

Validate an email verification request.

The Verification Processing screen exists to:

Receive verification tokens
Execute verification requests
Display verification progress
Transition users to success or failure outcomes

The screen acts as a workflow execution state rather than a destination page.

## User Types
Primary

Unverified Member

## User Goals

Users should be able to:

Confirm that verification is being processed
Understand that action is occurring
Receive a clear outcome
Avoid duplicate actions
## Entry Points
Verification Email

Verification Link

Resend Verification Email

Replacement Verification Link

## Exit Points
Success

Verification Success

(ID-005)

Failure

Verification Failure

(ID-006)

## Allowed Actions
User

Allowed:

Wait for processing
Observe status

Not Allowed:

Submit forms
Modify account information
Trigger duplicate verification requests
## Information Architecture

Verification Processing consists of:

Status Indicator
Processing Message
Verification Progress State
## Section 1 — Status Indicator
Purpose

Communicate that verification is actively being processed.

Contents

Loading Spinner

or

Loading Animation

Component Ownership
Shared

Skeleton

Custom

VerificationStatusIcon

## Section 2 — Processing Message
Purpose

Explain current system activity.

Headline

Verifying Your Email

Supporting Text

Please wait while we verify your account.

This usually takes only a few seconds.

Component Ownership
Custom

VerificationStatusContent

## Section 3 — Verification Progress State
Purpose

Execute verification workflow.

Behavior

On page load:

Extract verification token
Call Verify Email API
Await response

If verification succeeds:

Navigate to:

ID-005 Verification Success

If verification fails:

Navigate to:

ID-006 Verification Failure

## Loading States
Initial State

Verification request initiated.

Active State

Verification API request in progress.

Completion State

Redirect to outcome screen.

## Error Handling

Verification Processing does not directly display error states.

All verification failures transition to:

ID-006 Verification Failure

This preserves a clear separation between workflow execution and user-facing failure handling.

## Design System Rules

Use Shared Components

From shadcn:

Card
Skeleton

Create Custom Components:

VerificationStatusLayout
VerificationStatusIcon
VerificationStatusContent

Location:

src/modules/identity/components/

## Responsive Layout Rules

Inherits all rules from:

Identity Verification Screens

## Accessibility Requirements

Must support:

Screen reader status announcements
Keyboard accessibility
Semantic loading states
Focus preservation during redirects

## Backend Dependencies

Required:

Verify Email API

Verification token validation

Verification state transition

Account activation

Verification Processing exists specifically to consume the Verify Email workflow defined within the Identity Module and Email Verification Foundation.

# Verification Success Page
## Screen ID

ID-005

## Screen Name

Verification Success

## Purpose

Confirm successful email verification.

The Verification Success screen exists to:

Confirm account activation
Communicate successful identity verification
Reinforce platform participation readiness
Guide users toward authentication

The Verification Success screen does not:

Authenticate the user
Create a session
Collect profile information
Perform onboarding

Successful verification completes the Email Verification stage of the Identity Lifecycle and makes the account eligible for authentication and platform participation.

## User Types
Primary

Verified Member

## User Goals

Users should be able to:

Understand that verification succeeded
Confirm account activation
Understand next steps
Proceed to Login
## Entry Points
Verification Processing

(ID-004)

Successful verification outcome

Verification Link

Direct verification completion flow

## Exit Points
Primary

Login Page

(ID-009)

Secondary

Landing Page

(LP-001)

## Allowed Actions
Verified Member

Allowed:

Continue to Login
Return to Landing Page

Not Allowed:

Access authenticated features without logging in
Create content
Join Herds
Participate in discussions
## Information Architecture

Verification Success consists of:

Status Indicator
Success Message
Account Activation Details
Primary Action Area
## Section 1 — Status Indicator
Purpose

Provide immediate visual confirmation of success.

Contents

Success Icon

Verification Complete Indicator

Component Ownership
Custom

VerificationStatusIcon

## Section 2 — Success Message
Purpose

Clearly communicate successful verification.

Headline

Email Verified Successfully

Supporting Text

Your account has been activated.

You can now sign in and begin participating on Chauthara.

Component Ownership
Custom

VerificationStatusContent

## Section 3 — Account Activation Details
Purpose

Explain what has changed.

Contents
Email address verified
Account activated
Platform participation enabled
Authentication available
Component Ownership
Custom

VerificationStatusContent

## Section 4 — Primary Action Area
Purpose

Guide users toward authentication.

Primary Action

Sign In

Navigate to:

ID-009 Login Page

Secondary Action

Return to Home

Navigate to:

LP-001 Landing Page

## Component Ownership
Shared

Button

Custom

VerificationStatusActions

## Loading States
Initial State

Screen loads completed verification outcome.

No loading state required.

## Error Handling

Verification Success is a terminal success state.

Errors should not occur on this screen.

If verification status cannot be determined:

Redirect to:

ID-006 Verification Failure

## Design System Rules

Use Shared Components

From shadcn:

Card
Button
Separator

Create Custom Components:

VerificationStatusLayout
VerificationStatusIcon
VerificationStatusContent
VerificationStatusActions

Location:

src/modules/identity/components/

## Responsive Layout Rules

Inherits all rules from:

Identity Verification Screens

## Accessibility Requirements

Must support:

Keyboard navigation
Screen readers
Focus indicators
Semantic headings
Success status announcements

Success state must be announced to assistive technologies.

## Backend Dependencies

Required:

Verify Email API

Verification completion outcome

Login API

Next-step authentication flow

Verification success exists as the completion state of the Email Verification workflow within the Identity module.

# Verification Failure Page
## Screen ID

ID-006

## Screen Name

Verification Failure

## Purpose

Communicate that email verification failed and provide recovery options.

The Verification Failure screen exists to:

Explain verification failure
Provide recovery guidance
Allow verification email resend
Prevent user confusion

The screen does not:

Attempt verification retries automatically
Authenticate users
Activate accounts

Verification Failure is the authoritative recovery screen for:

- Expired verification token
- Invalid verification token
- Reused verification token

Verification-specific failures are not routed through:

ID-012 Identity Error Resolution

## User Types
Primary

Unverified Member

## User Goals

Users should be able to:

Understand why verification failed
Recover from expired or invalid verification links
Request a replacement verification email
Continue toward successful account activation
## Entry Points
Verification Processing

(ID-004)

Failed verification outcome

Expired Verification Link
Invalid Verification Link
Reused Verification Link
Verification Service Failure
## Exit Points
Primary

Verification Pending

(ID-003)

via successful resend workflow

Secondary

Login Page

(ID-009)

for already verified accounts

## Allowed Actions
Unverified Member

Allowed:

Request new verification email
Return to Login
Return to Landing Page

Not Allowed:

Authenticate if account remains unverified
Access platform participation features
## Information Architecture

Verification Failure consists of:

Status Indicator
Failure Message
Failure Details
Recovery Actions
## Section 1 — Status Indicator
Purpose

Provide immediate visual feedback that verification failed.

Contents

Error Icon

Verification Failed Indicator

Component Ownership
Custom

VerificationStatusIcon

## Section 2 — Failure Message
Purpose

Explain verification failure.

Headline

Verification Failed

Supporting Text

We were unable to verify your account.

The verification link may be invalid, expired, or already used.

Component Ownership
Custom

VerificationStatusContent

## Section 3 — Failure Details
Purpose

Provide recovery guidance.

Possible Failure Reasons
Verification token expired
Verification token invalid
Verification token already used
Account already verified
Verification request unavailable
User Guidance

Request a new verification email to continue account activation.

Component Ownership
Custom

VerificationStatusContent

## Section 4 — Recovery Actions
Purpose

Provide account recovery options.

Primary Action

Resend Verification Email

Behavior:

Call Resend Verification API
Show loading state
Show resend success feedback
Redirect to:

ID-003 Verification Pending

Secondary Action

Sign In

Used when account may already be verified.

Navigate to:

ID-009 Login Page

Tertiary Action

Return to Home

Navigate to:

LP-001 Landing Page

## Component Ownership
Shared

Button

Alert

Custom

VerificationStatusActions

## Loading States
Resend Verification Request

Show:

Button loading state
Action disabled state
Success States
Verification Email Resent

Display:

Verification email sent successfully.

Please check your inbox.

Redirect:

ID-003 Verification Pending

## Error Handling
Resend Verification Failure

Display:

Unable to send verification email.

Please try again later.

Rate Limit Reached

Display:

Too many verification requests.

Please wait before requesting another email.

The resend workflow must respect verification resend rate limiting requirements.

## Design System Rules

Use Shared Components

From shadcn:

Card
Button
Alert
Separator

Create Custom Components:

VerificationStatusLayout
VerificationStatusIcon
VerificationStatusContent
VerificationStatusActions

Location:

src/modules/identity/components/

Responsive Layout Rules

Inherits all rules from:

Identity Verification Screens

## Accessibility Requirements

Must support:

Keyboard navigation
Screen readers
Focus indicators
Semantic headings
Error status announcements

Failure and resend outcomes must be announced to assistive technologies.

## Backend Dependencies

Required:

Verify Email API

Failure outcome generation

Resend Verification API

Replacement verification workflow

Login API

Alternative navigation path

Verification Failure exists to support recovery from the email verification workflow while preserving the Identity-first participation model and verification requirements.

# Login Page

## Screen ID

ID-007

## Screen Name

Login Page

---

## Purpose

Allow verified users to authenticate and establish an active session.

The Login Page exists to:

- Authenticate verified accounts
- Create authenticated sessions
- Restore platform access
- Re-enter the platform after logout
- Recover from session expiration

The Login Page does not:

- Create accounts
- Verify email addresses
- Reset passwords
- Complete onboarding

Authentication is only available to verified accounts.

---

## User Types

### Primary

Verified Member

### Secondary

Unverified Member

Session Expired User

---

## User Goals

Users should be able to:

- Sign into their account
- Restore platform access
- Continue participation
- Navigate to Registration if they do not have an account

---

## Entry Points

### Landing Page

Header

Sign In

### Landing Page Hero

Sign In CTA

### Registration Page

Already have an account?

Sign In

### Verification Success Page

Sign In

### Session Expired Page

Sign In Again

---

## Exit Points

### Success

Authenticated Platform Experience

(Default Destination)

Following Feed

### Failure

Invalid credentials remain on the Login Page and are displayed as inline authentication errors.

Identity lifecycle errors may redirect to:

Identity Error Resolution Page

(ID-012)

---

## Allowed Actions

### Verified Member

Allowed:

- Enter email
- Enter password
- Submit login request
- Navigate to Registration
- Navigate to Forgot Password

### Unverified Member

Allowed:

- Attempt authentication

Not Allowed:

- Create session
- Access authenticated features

Unverified accounts must complete email verification before authentication is allowed.

---

## Authentication State Awareness

Frontend authentication follows the approved
authentication awareness model.

Authoritative states:

- unknown
- authenticated
- unauthenticated

The Login Page may only render for:

unauthenticated

users.

If:

authenticated

Redirect to:

Following Feed

Authentication state must not be evaluated until
session hydration completes.

---

## Successful Authentication Routing

After successful authentication:

Priority 1

Return user to preserved destination.

Examples:

- /profile/edit
- /following
- /herds/my-herd

Priority 2

Following Feed

Default authenticated experience.

The Login Page should not hardcode a single
destination if a preserved destination exists.

---

## Information Architecture

Login Page consists of:

1. Minimal Header

2. Authentication Hero / Philosophy Panel

3. Login Form

4. Alternative Authentication Action

5. Footer

---

## Section 1 — Minimal Header

### Purpose

Provide branding and Registration navigation.

---

### Contents

#### Left

Logo

Platform Name

#### Right

Need an account?

Create Account

---

### Mobile Behavior

Same structure.

No expanded navigation.

No hamburger menu.

The Login Page intentionally minimizes distractions.

---

### Component Ownership

#### Shared

Button

#### Custom

AuthHeader

Location:

src/modules/identity/components/auth/

---

## Section 2 — Authentication Hero / Philosophy Panel

### Purpose

Reinforce Chauthara's purpose and provide visual consistency with Registration.

The Login and Registration experiences should feel like part of the same Identity system.

---

### Desktop Layout

Displayed alongside login form.

Two-column layout:

```text
| Philosophy Panel | Login Form |
```

---

### Mobile Layout

Displayed above login form.

Single-column layout.

---

### Content

#### Headline

Welcome Back

#### Supporting Text

Continue meaningful conversations, reconnect with your communities, and participate in discussions that matter.

---

### Value Cards

#### Identity First

Build your reputation through your contributions.

---

#### Community Driven

Participate in Herds that matter to you.

---

#### Meaningful Discussion

Share ideas, ask questions, and learn from others.

---

### Visual Direction

Should communicate:

- Community
- Discussion
- Learning
- Participation

Should remain visually consistent with Registration Page.

---

### Component Ownership

#### Shared

Card

#### Custom

AuthHero

IdentityValueCard

Location:

src/modules/identity/components/auth/

---

## Section 3 — Login Form

### Purpose

Collect credentials required to authenticate a verified account.

---

### Form Fields

#### Email

Purpose:

Account identification.

Validation:

- Required
- Valid email format

---

#### Password

Purpose:

Authentication credential.

Validation:

- Required

---

#### Password Visibility Toggle

Purpose:

Improve usability.

Behavior:

Allow users to show or hide password contents.

---

### Forgot Password

Link:

Forgot Password?

Destination:

ID-008

Forgot Password Page

Future implementation.

---

### Primary Action

Button:

Sign In

Behavior:

Disabled while authentication request is processing.

---

### Loading State

Button Text:

Signing In...

Behavior:

- Inputs disabled
- Submit disabled
- Loading indicator displayed

---

### Error Handling
#### Login-Specific Error Rules

The following errors shall remain inline within the Login Page:

- Invalid credentials
- Missing email
- Missing password
- Invalid email format

The following errors shall navigate to ID-012:

- Email not verified
- Session expired
- Authentication required
- Verification link expired
- Invalid verification link
- Service unavailable
- Network failure

---

### Component Ownership

#### Shared

Input

Button

Label

Card

Separator

#### Custom

LoginForm

PasswordField

FormSection

Location:

src/modules/identity/components/auth/

---

## Section 4 — Authentication Error Handling
### Purpose

Provide clear feedback when authentication fails while keeping the user within the login workflow.

Field-level and credential-level failures should not navigate away from the Login Page.

### Inline Error Types
#### Invalid Credentials

Trigger:

Incorrect email
Incorrect password

Message:

Invalid email or password.

Behavior:

Remain on Login Page
Preserve email field value
Clear password field
Focus returned to password field

---

### Navigate to Identity Error Resolution Page Errors

#### Account Not Verified

Trigger:

Attempted login using an unverified account.

Behavior:

Navigate to:

ID-012
Identity Error Resolution Page

Variant:

email-not-verified

#### Service Unavailable

Trigger:

Identity service unavailable.

Behavior:

Navigate to:

ID-012
Identity Error Resolution Page

Variant:

service-unavailable

#### Network Failure

Trigger:

Frontend cannot reach backend.

Behavior:

Navigate to:

ID-012
Identity Error Resolution Page

Variant:

network-failure

## Section 5 — Alternative Authentication Action

### Purpose

Support users who do not yet have an account.

---

### Content

Don't have an account?

Create Account

---

### Behavior

Navigate to:

ID-002

Registration Page

---

### Component Ownership

#### Shared

Button

#### Custom

AuthRedirectSection

---

## Section 6 — Footer

### Purpose

Provide legal and informational links.

---

### Contents

Terms of Service

Privacy Policy

Community Guidelines

---

### Mobile Behavior

Stacked links.

---

### Desktop Behavior

Inline links.

---

### Component Ownership

#### Custom

AuthFooter

---

### Success Flow

Successful authentication follows:

```text
Login
        ↓
Credentials Valid
        ↓
Account Verified
        ↓
Session Created
        ↓
Following Feed
```

Users enter the authenticated platform experience.

---

### Failure Scenarios

#### Invalid Credentials

Navigate to:

ID-012

Login Failure Page

Reason:

Invalid Email or Password

---

#### Account Not Verified

Navigate to:

ID-012

Login Failure Page

Reason:

Email Verification Required

---

#### Session Creation Failure

Navigate to:

ID-012

Login Failure Page

Reason:

Authentication Failed

---

#### Network Failure

Navigate to:

ID-012

Login Failure Page

Reason:

Unable To Reach Authentication Service

---

## Responsive Layout Rules

### Mobile (<768px)

Single Column

Structure:

```text
Header

Hero

Login Form

Registration Link

Footer
```

Full-width inputs.

Full-width CTA.

---

### Tablet (768px–1024px)

Single-column layout.

Expanded spacing.

Improved card presentation.

---

### Desktop (>1024px)

Two-column layout.

```text
| Philosophy Panel | Login Form |
```

Hero content remains visible during authentication.

---

## Design System Rules

### Use Shared Components

From shadcn:

Button

Input

Card

Label

Separator

Skeleton

---

### Create Custom Components

AuthHeader

AuthHero

IdentityValueCard

LoginForm

PasswordField

FormSection

AuthRedirectSection

AuthFooter

Location:

src/modules/identity/components/auth/

---

## Accessibility Requirements

Must support:

- Keyboard navigation
- Screen readers
- Focus indicators
- Semantic form labels
- Accessible validation messaging
- Accessible password visibility controls
- Color contrast compliance

---

## Backend Dependencies

Required APIs:

POST /auth/login

GET /auth/session

Future APIs:

POST /auth/forgot-password

Authentication requires successful email verification before session creation.

---

## Future Enhancements

Not MVP:

- Social Authentication
- Google Login
- GitHub Login
- Apple Login
- Passwordless Authentication
- Biometric Authentication

---

## Notes

The Login Page intentionally mirrors the Registration Page experience.

Both screens belong to the Identity module and share common layout, branding, and component structure.

Authentication is restricted to verified accounts.

Users with valid credentials but unverified accounts must complete email verification before they can establish a session and participate on the platform.


# Identity Error Resolution Page

## Screen ID

ID-012

## Screen Name

Identity Error Resolution Page

---

## Purpose

Provide a dedicated recovery experience for identity-related failures that require user action beyond simple credential correction.

The Identity Error Resolution Page exists to:

- Explain identity-related failures
- Provide clear recovery guidance
- Route users into the correct recovery workflow
- Support authentication lifecycle continuity
- Reduce user confusion during identity recovery scenarios

The page is not intended for:

- Field-level validation errors
- Incorrect password attempts
- Incorrect email entry
- General form validation failures

These remain inline form errors within the originating screen.

The Identity Error Resolution Page is not used for:

- Expired verification tokens
- Invalid verification tokens
- Reused verification tokens

These failures are handled by:

ID-006 Verification Failure

---

## User Types

### Primary

Visitor

### Secondary

Unauthenticated User

### Tertiary

Authenticated User with Invalid Session

---

## User Goals

Users should be able to:

- Understand what happened
- Understand why the action failed
- Understand what to do next
- Access the appropriate recovery workflow
- Return to the authentication flow
- Continue account activation when required

---

## Supported Error Variants

The Identity Error Resolution Page supports:

email-not-verified

session-expired

authentication-required

service-unavailable

network-failure

Each variant should provide:

- Explanation
- Recovery guidance
- Appropriate recovery actions

The page layout remains consistent across
all variants.

---

## Entry Points

### Login Page

(ID-009)

When login fails due to:

- Email not verified

---

Verification-related failures are handled by:

ID-006 Verification Failure

The Identity Error Resolution Page does not handle
email verification token failures.

---

### Protected Routes

When access fails due to:

- Missing authentication
- Expired session

---

### Global Authentication Middleware

When identity lifecycle validation fails.

---

### System Error Recovery

When authentication infrastructure is temporarily unavailable.

---

## Exit Points

Depends on error type.

Possible destinations:

### Login Page

(ID-009)

### Verification Pending Page

(ID-003)

### Registration Page

(ID-002)

### Landing Page

(LP-001)

### Original Protected Destination

After successful authentication.

---

## Allowed Actions

### Visitor

Allowed:

- Return to Login
- Return to Registration
- Request a new verification email
- Retry authentication

### Unauthenticated User

Allowed:

- Resolve identity issue
- Resume authentication flow

### Authenticated User

Allowed:

- Reauthenticate when required

---

## Information Architecture

The Identity Error Resolution Page consists of:

1. Minimal Header

2. Identity Hero / Context Panel

3. Error Resolution Card

4. Recovery Actions

5. Footer

---

## Section 1 — Minimal Header

### Purpose

Provide branding and limited navigation.

### Contents

#### Left

Logo

Platform Name

#### Right

Sign In

Create Account

### Mobile Behavior

Same structure.

No expanded navigation.

No hamburger menu.

The page should remain focused on recovery.

---

### Component Ownership

#### Shared

Button

#### Custom

AuthHeader

Location:

src/modules/identity/components/auth/

---

## Section 2 — Identity Hero / Context Panel

### Purpose

Provide continuity with the Identity experience.

Reduce perceived failure severity.

Communicate that the issue is recoverable.

---

### Desktop Layout

Displayed alongside the Error Resolution Card.

Two-column layout:

```text
| Identity Context Panel | Error Resolution Card |
```

### Mobile Layout

Displayed above the Error Resolution Card.

Single-column layout.

---

### Visual Direction

Should communicate:

- Guidance
- Recovery
- Trust
- Security
- Clarity

Should avoid:

- Alarm
- Failure-focused messaging
- Technical diagnostics
- Error codes visible to users

---

### Component Ownership

#### Custom

AuthHero

Location:

src/modules/identity/components/auth/

---

## Section 3 — Error Resolution Card

### Purpose

Explain the failure and guide recovery.

This is the only dynamic section of the page.

All error variants render through the same component structure.

---

### Standard Structure

Contents:

1. Status Icon

2. Title

3. Explanation

4. Primary Recovery Action

5. Secondary Recovery Action

---

### Component Ownership

#### Shared

Card

Button

#### Custom

IdentityErrorCard

Location:

src/modules/identity/components/auth/

---

## Error Variants

### Variant A — Email Verification Required

#### Trigger

Login attempt by an unverified account.

#### Title

Email Verification Required

#### Message

Your account exists but your email address has not yet been verified.

Please verify your email before signing in.

#### Primary Action

Resend Verification Email

#### Secondary Action

Back To Login

---

### Variant B — Verification Link Expired

#### Trigger

Expired verification token.

#### Title

Verification Link Expired

#### Message

Your verification link has expired.

Request a new verification email to continue.

#### Primary Action

Send New Verification Email

#### Secondary Action

Back To Login

---

### Variant C — Invalid Verification Link

#### Trigger

Invalid or already-used verification token.

#### Title

Invalid Verification Link

#### Message

The verification link is invalid or has already been used.

Request a new verification email to continue.

#### Primary Action

Resend Verification Email

#### Secondary Action

Back To Login

---

### Variant D — Session Expired

#### Trigger

Expired authentication session.

#### Title

Session Expired

#### Message

Your session has expired.

Please sign in again to continue.

#### Primary Action

Sign In Again

#### Secondary Action

Return Home

---

### Variant E — Authentication Required

#### Trigger

Attempt to access a protected route without authentication.

#### Title

Authentication Required

#### Message

You must sign in to access this page.

#### Primary Action

Go To Login

#### Secondary Action

Return Home

---

### Variant F — Service Temporarily Unavailable

#### Trigger

Authentication infrastructure unavailable.

Examples:

- Authentication service failure
- Session validation failure
- Identity service outage

#### Title

Unable To Sign In

#### Message

We are currently experiencing technical issues.

Please try again shortly.

#### Primary Action

Try Again

#### Secondary Action

Return Home

---

### Variant G — Network Connection Problem

#### Trigger

Frontend unable to communicate with backend.

#### Title

Connection Problem

#### Message

We couldn't reach the server.

Check your connection and try again.

#### Primary Action

Try Again

#### Secondary Action

Return Home

---

## URL Strategy

Single route.

Dynamic rendering based on error type.

### Route

```text
/auth/error
```

### Examples

```text
/auth/error?type=email-not-verified

/auth/error?type=verification-expired

/auth/error?type=verification-invalid

/auth/error?type=session-expired

/auth/error?type=authentication-required

/auth/error?type=service-unavailable

/auth/error?type=network-failure
```

---

## Layout Rules

### Desktop (>1024px)

Two-column layout.

Identity Hero Panel

+

Error Resolution Card

Centered horizontally.

---

### Tablet (768px–1024px)

Reduced two-column layout.

Hero content condensed.

---

### Mobile (<768px)

Single-column layout.

Hero Panel above Error Resolution Card.

Actions full-width.

---

## Design System Rules

Use Shared Components:

- Button
- Card
- Separator
- Skeleton

Location:

src/shared/components/ui/

Create Custom Components:

- IdentityErrorCard

Location:

src/modules/identity/components/auth/

Reuse Existing Components:

- AuthHeader
- AuthHero
- AuthFooter

No separate error page layout shall be created.

Identity screens share the same authentication shell.

---

## Accessibility Requirements

Must support:

- Keyboard navigation
- Screen readers
- Focus indicators
- Semantic headings
- ARIA-compliant status messaging
- Color contrast compliance

Status messages must be announced appropriately to assistive technologies.

---

## Destination Preservation

Protected route failures should preserve
the originally requested destination.

Example:

/profile/edit
        ↓
Authentication Failure
        ↓
ID-012
        ↓
Login
        ↓
Return To:
/profile/edit

The original destination should be restored
after successful identity recovery.

---

## Error Handling Rules

Field-level validation failures shall not navigate to this page.

Examples:

- Invalid email format
- Missing password
- Incorrect password
- Incorrect email

These remain inline form errors.

Only workflow-level identity failures may use this screen.

---

## Backend Dependencies

Required:

- Login API
- Verify Email API
- Resend Verification API
- Session Validation API

The screen consumes backend error codes and maps them into approved error variants.

Backend error codes shall not be displayed directly to users.

---

## Future Enhancements

Not MVP:

- Support links
- Contact support workflow
- Recovery diagnostics
- Account recovery wizard
- Multi-step identity recovery
- Localization
- Context-aware recovery recommendations




# Important section to add to every protected page
## Session Hydration Behavior

Protected pages must wait for authentication
state resolution before evaluating access rules.

During:

unknown

state:

Display authentication loading state.

Do not redirect.

Access evaluation occurs only after:

authenticated

or

unauthenticated

is resolved.


# Add to Profile page when designed
## Profile Ownership Model

The Profile Page supports both:

Own Profile
and
Public User Profile

Route Pattern

/me

Authenticated user's profile

/:username

Public profile

Ownership-Aware Actions

Own Profile:

Allowed:

- Edit Profile
- View Followers
- View Following

Public Profile:

Allowed:

- Follow User
- View Followers
- View Following

Not Allowed:

- Edit Profile