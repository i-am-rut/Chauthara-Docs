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

Registration Success Screen

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
Registration Success Screen

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

### Notes

Registration is intentionally minimal.

Profile creation, personalization, community discovery, and participation occur after account verification.

The Registration Page exists solely to establish identity and begin the verification lifecycle.