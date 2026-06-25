# Project Overview

## Name

Chauthara *(working title)*

---

## Vision

Chauthara is a community-centric social discussion platform that combines the identity-driven nature of Twitter/X with the community-driven nature of Reddit.

The platform enables individuals to build reputation, share ideas, participate in meaningful discussions, and contribute to interest-based communities called Herds.

Chauthara aims to provide a space where personal identity, constructive discussion, and community participation coexist without one overshadowing the others.

---

## Product Positioning

Chauthara is not intended to be a Twitter clone or a Reddit clone.

The platform combines:

* Twitter's identity graph (people follow people)
* Reddit's community graph (people join communities)
* A contribution-centric reputation model (Aura)

The platform is designed around the principle that communities should amplify meaningful contributors rather than replace individual identity.

---

## Core Purpose

Provide a platform where users can:

* Share opinions and ideas
* Participate in discussions
* Join and build communities
* Build reputation through meaningful contributions
* Discover people and topics of interest
* Develop an audience through consistent participation

---

## Target Users

Primary Audience:

* Adults (18+)
* Internet users interested in discussion, learning, sharing ideas, and community participation
* Users seeking both personal expression and community engagement

Potential Future Audience:

* Younger audiences (14+) if additional safety, moderation, content filtering, and regulatory requirements are implemented

---

## Non-Target Users

* Users seeking anonymous-only platforms
* Users primarily interested in long-form blogging
* Users seeking live streaming platforms
* Users seeking short-form algorithmic entertainment feeds

---

# Platform Philosophy

## Identity First

Individuals are the primary unit of identity on the platform.

Users build reputation, relationships, and audiences through their own contributions.

---

## Community Amplification

Herds exist to facilitate:

* Discovery
* Discussion
* Collaboration
* Knowledge sharing

Communities should amplify contributors rather than replace individual identity.

---

## Meaningful Contribution

The platform should reward:

* Constructive discussion
* Knowledge sharing
* Helpful participation
* Community building

The platform should avoid rewarding engagement bait or low-quality interaction.

---

## Knowledge Sharing

Chauthara should encourage users to:

* Share expertise
* Ask questions
* Exchange ideas
* Contribute context to discussions

---

## Community Autonomy

Communities should have meaningful autonomy through Shepherd moderation and community-specific rules.

Community autonomy exists within platform-wide policies and governance.

---

## Evolutionary Architecture Principle

The platform should be built incrementally.

Each iteration should satisfy current requirements while preserving a reasonable path for future planned capabilities.

Avoid:

* Premature optimization
* Overengineering
* Architectural dead ends

Design for today's needs while remaining aware of tomorrow's needs.

---

# Platform Governance

Authority Hierarchy:

1. Applicable Law and Regulatory Requirements
2. Platform Administrators
3. Herd Owners
4. Shepherds (Community Moderators)

Community governance may influence local community decisions but cannot override platform governance or legal requirements.
Shepherd actions remain subject to administrator review and override.

---

# Platform Culture

The platform should optimize for:

* Constructive discussion
* Knowledge sharing
* Community participation
* Respectful disagreement
* Meaningful contribution

The platform should discourage:

* Harassment
* Abuse
* Spam
* Manipulative engagement tactics
* Community disruption

---

# Core Content Types

## Text Posts

Maximum length: approximately 1500 characters

Structure:

* Title + Content
* Title + Media
* Title + Content + Media

---

## Rich Media

Supported content:

* Images
* Short-form videos

Future media types may be considered.

---

# Core User Actions

Users should primarily be able to:

1. Read content
2. Participate in discussions
3. Create content
4. Join and contribute to Herds
5. Follow individuals
6. Reply to posts and comments
7. Vote on content
8. Save content
9. Report policy violations
10. Build reputation and audience

---

# Core Platform Systems

## Personal Content System

Users may create posts in their personal capacity.

Personal posts are:

* Visible to followers
* Visible on user profiles
* Subject to platform moderation

---

## Herd System

Herds are community spaces dedicated to specific topics or interests.

Planned Herd Types:

* Open Join
* Minimum Aura Required
* Request to Join
* Invite Only

Herds are moderated by Shepherds.

---

## Reputation System

The platform uses a reputation mechanism called Aura.

Aura represents user contribution and reputation across the platform.

Aura may eventually influence:

* Community eligibility
* Reputation signals
* Recognition
* Discovery
* Moderation opportunities

Aura is considered a foundational platform system and requires dedicated future design.

---

## Voting & Ranking System

Voting is expressed through:

* HypeUp
* HypeDown

Supported targets:

* Posts
* Comments

Voting contributes to:

* Content ranking
* Visibility
* Reputation signals
* Aura calculations

---

# Feed Philosophy

Chauthara intentionally separates social and community consumption.

## Following Feed

Displays activity from followed users.

Default feed at platform entry.

---

## Herd Feed

Displays content from joined Herds.

Focused on community participation and discovery within subscribed interests.

---

## Future Consideration

A discovery-oriented feed may be considered in future iterations.

No algorithmic "For You" feed is planned for initial versions.

---

# Discovery Philosophy

Users should be able to discover:

* People
* Herds
* Posts

Discovery should support filtering and focused exploration.

Discovery should not be exclusively algorithm-driven.

---

# Identity Philosophy

Supported identity model:

## Real Name Friendly

Users may use real names.

---

## Username First

Usernames are the primary platform identity for interaction.

Usernames are used in:

* Mentions
* Discussions
* Posts
* Comments
* Replies

---

## Anonymous Participation

Anonymous participation is excluded from MVP.

Whether Chauthara should support anonymous participation in a future release remains an open question.

---

# Safety Philosophy

The platform should prioritize:

* User safety
* Content moderation
* Abuse prevention
* Privacy controls
* Reporting mechanisms

Users may provide additional context on content.

The platform does not position itself as an arbiter of truth.

Community context and contribution systems may be explored in future iterations.

---

# Future Expansion

Potential future systems:

* Monetization
* Creator subscriptions
* Community notes / contextual contribution systems
* Discovery feeds
* End-to-end encrypted messaging
* Expanded age support (14+)
* Advanced moderation systems

---

# Non-Goals

The following are not goals for initial versions:

* Long-form blogging platform
* Live video streaming
* TikTok-style recommendation engine
* Audio chat rooms
* NFT functionality
* Cryptocurrency functionality
* End-to-end encrypted messaging (initial versions)

---

# Technical Context

Preferred Stack:

* Next.js
* TypeScript
* Express.js
* MongoDB

Additional technologies will be selected through architecture discussions and ADRs.

---

# Constraints

## Financial Constraints

The platform should prioritize free-tier and low-cost solutions whenever practical.

---

## Team Constraints

The platform is being developed by a solo developer.

---

## Time Constraints

The platform will be developed iteratively.

Each iteration should result in a usable product state.

---

## Learning Constraints

The project serves as a learning vehicle for:

* Product development
* System design
* Software architecture
* Backend engineering
* Frontend engineering
* Security
* Testing
* Deployment
* Monitoring
* Operations

---

# Success Metrics

## Learning Success

* Complete product discovery process
* Create architecture documentation
* Produce ADRs
* Design scalable systems
* Implement real-time capabilities
* Deploy production infrastructure
* Implement moderation systems
* Learn iterative product development

---

## Engineering Success

* Maintainable architecture
* Clean codebase
* Well-defined APIs
* Security best practices
* Automated testing
* CI/CD implementation
* Effective documentation

---

## Portfolio Success

* Demonstrates frontend engineering ability
* Demonstrates backend engineering ability
* Demonstrates system design skills
* Demonstrates architecture thinking
* Demonstrates scalability awareness

---

## Product Success

* 100+ registered users
* 20+ active weekly users
* Multiple active Herds
* Organic content creation
* Organic community participation

---

# Delivery Strategy

The approved MVP remains the complete target scope of the platform.

Implementation may occur through multiple delivery phases.

## Phase 1 — Core Platform

Focus:

- Core platform participation
- Identity
- Communities
- Content creation
- Discussion
- Voting
- Feed consumption

The goal of Phase 1 — Core Platform is to achieve a usable social platform and gain practical implementation experience.

## Phase 2 — Governance & Operations

Focus:

- Reporting
- Moderation
- Governance workflows
- Enforcement
- Escalation
- Remaining MVP governance capabilities

## Architectural Principle

Architectural design may be completed before implementation.

Implementation order does not redefine approved architecture or MVP scope.

Approved architectural decisions remain authoritative even if implementation is deferred.

---

## Current Status

MVP Product Design Consolidation Phase
