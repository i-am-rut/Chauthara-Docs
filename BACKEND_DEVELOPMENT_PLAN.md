# Development Planning Principles
## Purpose of Development Planning

Keep this section short.

Define:

Why Development Planning Exists

Bridge approved architecture and implementation work.

Translate approved architecture into executable implementation plans while preserving architectural integrity.

Relationship Between Architecture and Development Planning

Architecture defines:

What the system is
Ownership boundaries
Module boundaries
Authority boundaries
Contracts

Development Planning defines:

How implementation progresses toward that architecture

Planning serves architecture.

Planning does not redesign architecture.

Relationship Between Approved Architecture and Implementation

Implementation must realize approved architecture.

Implementation convenience does not justify architectural changes.

Approved architecture remains authoritative throughout development planning and implementation.

## Development Planning Principles

This is the core section.

I would keep it to approximately 8–10 principles.

DP-01 Architecture-First Planning

Implementation plans must originate from approved architecture.

Architecture drives implementation.

Implementation does not drive architecture.

DP-02 Dependency-Aware Planning

Implementation planning should respect approved dependency relationships.

Dependencies influence implementation sequencing.

Dependency relationships themselves are not modified by planning.

DP-03 Ownership Preservation

Implementation planning must preserve:

Domain ownership
Aggregate ownership
Resource ownership
Governance ownership

Ownership boundaries are not negotiable during planning.

DP-04 Incremental Delivery

Implementation should be decomposed into manageable increments.

Each increment should provide meaningful progress while preserving architectural integrity.

DP-05 Simplicity-First Implementation

Planning should prefer the simplest implementation approach that satisfies approved architecture.

Avoid speculative abstractions.

Avoid premature infrastructure.

Aligns directly with the project's Simplicity First principle.

DP-06 Verification-Driven Development

Planning should encourage implementation steps that can be validated early.

Reduce uncertainty before additional complexity is introduced.

DP-07 Evolutionary Implementation

Implementation should follow the same evolutionary philosophy already approved for architecture.

Build current requirements first.

Preserve future evolution paths.

Avoid future-driven implementation complexity.

DP-08 Learning-Value Alignment

Implementation planning should maximize learning value while preserving correctness and maintainability.

The project exists partly as a learning platform.

DP-09 Solo Developer Operability

Implementation plans should remain executable and maintainable by a single developer.

Avoid plans that introduce disproportionate operational or coordination overhead.

Aligns with approved architectural constraints.

DP-10 Rework Minimization

Planning should reduce the probability of architectural rework, implementation rework, and workflow redesign.

Prefer stable foundations before dependent implementation.

## Development Planning Constraints

This should read similarly to Architecture Constraints.

Examples:

DPC-01

Approved architecture remains authoritative.

DPC-02

Approved ADRs remain authoritative.

ADR-001 may not be reinterpreted through planning.

DPC-03

Approved API contracts remain authoritative.

Implementation plans adapt to contracts.

Contracts do not adapt to implementation.

DPC-04

Approved domain ownership boundaries may not be altered.

DPC-05

Approved module boundaries may not be altered.

DPC-06

Governance authority boundaries may not be altered.

DPC-07

Feed remains a derived read-only domain.

DPC-08

Database ownership rules remain authoritative.

DPC-09

Infrastructure simplicity remains preferred over speculative scalability.

Consistent with Infrastructure Principles.

DPC-10

Development planning may refine implementation details but may not redesign approved architecture.

## Architecture Preservation Rules

This section should explicitly prevent architectural drift.

Domain Boundary Preservation

Implementation tasks must respect approved domain ownership.

Module Boundary Preservation

Cross-module implementation must continue to use approved capability contracts.

Ownership Boundary Preservation

Only owning domains may implement authoritative state mutations.

Governance Authority Preservation

Governance remains an authority domain.

Governance never becomes a resource ownership domain.

Capability Contract Preservation

Cross-module interactions continue through approved module contracts.

Feed Boundary Preservation

Feed remains:

Derived
Read-only
Non-authoritative

Implementation planning may not introduce feed-owned authoritative state.

This directly aligns with approved architecture.

Layer Responsibility Preservation

Implementation planning must preserve:

Controllers as transport adapters
Application Services as workflow owners
Repositories as persistence owners
Domain Layer as business rule owner

Already established by approved execution architecture.

## Development Planning Success Criteria

These are planning-quality criteria.

Not implementation completion criteria.

Examples:

DPS-01

Provides a clear implementation path.

DPS-02

Preserves approved architecture.

DPS-03

Preserves ownership and governance boundaries.

DPS-04

Reduces implementation uncertainty.

DPS-05

Reduces rework probability.

DPS-06

Supports incremental implementation.

DPS-07

Supports validation throughout implementation.

DPS-08

Remains operable for a solo developer.

DPS-09

Remains aligned with approved infrastructure and deployment assumptions.

DPS-10

Produces predictable implementation progression.

# Backend Build Strategy

## Purpose

Define the implementation strategy that translates approved architecture into executable backend development work while preserving architectural integrity.

---

## Build Strategy Decision

### Approach Evaluated

#### Layer-First Development

Build technical layers across the entire system before completing business workflows.

Examples:

- Controllers first
- Application Services second
- Repositories third
- Domain Rules fourth

#### Module-First Development

Build complete business capabilities end-to-end within approved modules.

Examples:

- Registration
- Authentication
- Profile Management
- Following
- Posting

### Rejected Approach

Layer-First Development

Reason:

- Delays end-to-end validation.
- Increases integration risk.
- Increases rework probability.
- Conflicts with domain-oriented architecture.

### Recommended Approach

Module-First Vertical Slice Development

Build complete backend capabilities through the entire execution stack before beginning additional slices.

### Rationale

The strategy aligns with:

- ADR-001
- Dependency-Aware Planning
- Incremental Delivery
- Verification-Driven Development
- Solo Developer Operability
- Rework Minimization

Benefits:

- Early validation
- Faster feedback
- Reduced integration risk
- Better learning outcomes
- Architecture preservation

---

## Vertical Slice Strategy

### Vertical Slice Definition

A vertical slice is the smallest independently valuable backend capability that traverses:

API Layer
↓
Application Layer
↓
Domain Rules
↓
Repository Layer
↓
Database
↓
Response

### Slice Design Principles

- Feature-oriented
- End-to-end
- Independently verifiable
- Dependency-aware
- Ownership-preserving
- Architecture-preserving

### Recommended Slice Structure

1. User Registration
2. Authentication
3. Profile Management
4. Follow System
5. Personal Posting
6. Comments & Replies
7. Voting
8. Herd Creation & Membership
9. Herd Posting
10. Feed Retrieval
11. Image Uploads

### Slice Validation Rules

A slice is complete only when:

- Workflow functions end-to-end
- Contracts validate
- Domain rules validate
- Persistence validates
- Error handling validates
- Tests pass
- Documentation updated

---

## Development Workflow

### Workflow Philosophy

Implement incrementally.
Validate continuously.
Refactor locally.
Preserve approved architecture.

### Standard Development Sequence

Requirement
↓
Architecture Review
↓
Module Identification
↓
Contract Identification
↓
Implementation
↓
Validation
↓
Testing
↓
Refactoring
↓
Documentation Update
↓
Completion

### Validation Expectations

Validate:

- Architecture compliance
- Ownership boundaries
- Dependency rules
- Workflow execution
- API contracts
- Persistence boundaries

### Documentation Expectations

Implementation completion should evaluate updates for:

- CHANGELOG.md
- LEARNINGS.md
- TASKS.md

Architecture documents change only when architecture changes.

### Workflow Constraints

- Architecture remains authoritative.
- ADR-001 remains authoritative.
- API contracts remain authoritative.
- Module boundaries remain unchanged.
- Governance boundaries remain unchanged.
- Feed remains derived and read-only.

---

## Build Strategy Rules

BS-01 Implement vertical slices rather than technical layers.

BS-02 Complete one slice before starting the next.

BS-03 Follow approved dependency direction.

BS-04 Validate every slice end-to-end.

BS-05 Preserve module ownership boundaries.

BS-06 Use capability contracts for cross-module communication.

BS-07 Refactor after working functionality exists.

BS-08 Avoid speculative abstractions.

BS-09 Every slice must produce executable functionality.

BS-10 Implementation convenience must not override approved architecture.

BS-11 Feed implementation follows authoritative domain implementation.

BS-12 Governance implementation follows Core Platform delivery.

# Foundation Implementation Plan
## Purpose

The Foundation Implementation Plan defines the shared backend infrastructure required before implementation of any business module.

The foundation exists to provide:

Stable application startup
Stable runtime configuration
Stable database integration
Stable error handling
Stable middleware execution
Stable implementation structure

The foundation does not implement business capabilities.

Business implementation begins only after foundation validation is complete.

Foundation Responsibility Model
## Project Structure Foundation
Foundation Responsibility

Provide a stable implementation structure aligned with:

ADR-001
Approved module boundaries
Approved layer boundaries
Approved dependency model

This prevents architectural drift during implementation.

Possible Approaches
Approach A — Technical Layer Structure

Organize by:

controllers
services
repositories
models
Approach B — Domain-Oriented Structure

Organize by:

Identity
Social Graph
Content
Community
Feed
Media
Governance

with internal layer separation inside each module.

Rejected Approach

Technical Layer Structure.

Reasons:

Conflicts with ADR-001.
Weakens module ownership visibility.
Encourages cross-module coupling.
Reduces future extraction readiness.
Recommended Approach

Domain-Oriented Structure.

Reasons:

Directly aligns with ADR-001.
Preserves module ownership.
Preserves capability-based dependencies.
Supports Module-First Development.
Supports Vertical Slice Development.
Foundation Structure

src/

├── modules/
│   ├── identity/
│   ├── social-graph/
│   ├── content/
│   ├── community/
│   ├── feed/
│   ├── media/
│   └── governance/

├── shared/
│   ├── application/
│   ├── domain/
│   ├── infrastructure/
│   ├── errors/
│   ├── middleware/
│   ├── configuration/
│   ├── contracts/
│   └── utils/

├── bootstrap/
│   ├── express/
│   ├── database/
│   ├── configuration/
│   └── startup/

├── api/
│   ├── routes/
│   ├── mappers/
│   └── responses/

├── server/
└── index.js

Must Exist Before Modules
src/modules/
src/shared/
src/bootstrap/
src/api/
src/server/

Remains Empty Until Module Development
modules/identity/*
modules/social-graph/*
modules/content/*
modules/community/*
modules/feed/*
modules/media/*
modules/governance/*

Only structural placeholders should exist.

## Express Bootstrap Foundation
Foundation Responsibility

Provide deterministic application startup.

Possible Approaches
Approach A

Distributed initialization inside modules.

Approach B

Centralized bootstrap process.

Rejected Approach

Distributed initialization.

Reasons:

Startup ordering becomes unclear.
Difficult validation.
Increased coupling.
Recommended Approach

Centralized Bootstrap.

Startup Sequence
Load Configuration
        ↓
Validate Configuration
        ↓
Initialize Database
        ↓
Create Express App
        ↓
Register Middleware
        ↓
Register Routes
        ↓
Register Error Middleware
        ↓
Start HTTP Server
Bootstrap Ownership

Configuration Bootstrap

Owns:

Environment loading
Environment validation

Database Bootstrap

Owns:

Mongo connection
Database readiness validation

Express Bootstrap

Owns:

Express initialization
Middleware registration
Route registration

Server Bootstrap

Owns:

Runtime startup
HTTP listener startup
## Configuration Foundation
Foundation Responsibility

Provide centralized runtime configuration.

Possible Approaches
Approach A

Environment access throughout application.

Approach B

Centralized configuration module.

Rejected Approach

Direct environment access.

Reasons:

Configuration scattering.
Validation duplication.
Environment inconsistency.
Recommended Approach

Centralized Configuration Module.

Configuration Categories

Required:

Application
Server
Database
Authentication
Media
Environment
Example Structure
shared/configuration/

├── app.config.js
├── database.config.js
├── auth.config.js
├── media.config.js
└── index.js
Configuration Loading Strategy
.env
        ↓
Configuration Loader
        ↓
Configuration Validation
        ↓
Typed Configuration Object
        ↓
Application Startup
Startup Validation

Application startup fails immediately when:

Required variables missing.
Invalid values detected.
Environment configuration inconsistent.

Fail-fast behavior is mandatory.

## Database Foundation
Foundation Responsibility

Provide authoritative MongoDB integration.

Possible Approaches
Approach A

Per-module database connections.

Approach B

Single application-owned connection.

Rejected Approach

Per-module connections.

Reasons:

Violates operational simplicity.
Creates ownership ambiguity.
Unnecessary for modular monolith.
Recommended Approach

Single Application-Owned MongoDB Connection.

Database Bootstrap Responsibilities

Own:

Connection creation
Connection lifecycle
Startup validation
Graceful shutdown
Module Responsibilities

Own:

Schemas
Repositories
Queries
Persistence rules

Modules do not own:

Database connections
Connection lifecycle
Failure Behavior

Database unavailable:

Startup Failure
        ↓
Application Does Not Start

No degraded mode.

## Error Framework Foundation
Foundation Responsibility

Provide standardized error handling before module implementation begins.

Possible Approaches
Approach A

Ad-hoc error creation.

Approach B

Shared error hierarchy.

Rejected Approach

Ad-hoc errors.

Reasons:

Inconsistent API responses.
Difficult translation.
Difficult maintenance.
Recommended Approach

Shared Error Hierarchy.

Foundation Error Inventory

Required Before Modules

ApplicationError
ValidationError
AuthenticationError
AuthorizationError
NotFoundError
ConflictError
InfrastructureError
ConfigurationError
DatabaseError
Error Categories
Input Errors
Authentication Errors
Authorization Errors
Ownership Errors
Governance Errors
Domain Errors
Infrastructure Errors
Unexpected Errors

Ownership, Governance, and Domain-specific errors are implemented during module development.

Error Translation
Application Error
        ↓
Global Error Middleware
        ↓
API Error Contract
        ↓
HTTP Response

Centralized translation remains mandatory.

Middleware Foundation
Foundation Responsibility

Provide request processing infrastructure required by all modules.

Possible Approaches
Approach A

Module-owned middleware registration.

Approach B

Application-owned middleware registration.

Rejected Approach

Module-owned registration.

Reasons:

Startup ordering becomes unpredictable.
Violates centralized execution architecture.
Recommended Approach

Application-Owned Middleware Registration.

Foundation Middleware Inventory

Required Before Modules

Correlation Middleware
Request Logging Middleware
Security Middleware
Authentication Middleware
Request Parsing Middleware
Error Logging Middleware
Global Error Middleware
Middleware Ordering
Correlation
        ↓
Request Logging
        ↓
Security
        ↓
Authentication
        ↓
Request Parsing
        ↓
Routes
        ↓
Error Logging
        ↓
Global Error Handler
Deferred Middleware

Implemented during module development:

Module Validation Middleware
Feature-Specific Middleware
Module Route Middleware
## Foundation Implementation Sequence
Project Structure
        ↓
Configuration Foundation
        ↓
Express Bootstrap Foundation
        ↓
Database Bootstrap Foundation
        ↓
Error Framework Foundation
        ↓
Middleware Foundation
        ↓
Foundation Validation
        ↓
Identity Module Development
Rationale

Project Structure

Creates architectural skeleton.

↓

Configuration

Required by every other foundation component.

↓

Express Bootstrap

Requires configuration.

↓

Database Bootstrap

Integrated into startup lifecycle.

↓

Error Framework

Required before route execution.

↓

Middleware

Depends on configuration and error handling.

↓

Foundation Validation

Confirms operational readiness.

↓

Module Development

Begins only after foundation stability is proven.

## Foundation Component Inventory
Must Exist Before Modules
Structure
Domain module directories
Shared infrastructure directories
Bootstrap directories
API directories
Configuration
Configuration loader
Configuration validator
Environment definitions
Bootstrap
Express bootstrap
Server bootstrap
Database bootstrap
Database
Mongo connection manager
Error Framework
Base error hierarchy
Error translation layer
Middleware
Correlation middleware
Logging middleware
Authentication middleware
Error middleware
Optional Foundation Components
Health endpoint
Graceful shutdown utilities
Startup diagnostics
Deferred Components
Domain schemas
Domain repositories
Application services
Controllers
Module contracts
Authorization implementation
Governance implementation
Feed implementation
Media implementation
## Foundation Validation Strategy
Startup Validation

Validate:

Application starts successfully.
Startup sequence executes correctly.
Configuration Validation

Validate:

Required environment variables present.
Invalid configuration prevents startup.
Database Validation

Validate:

Mongo connection established.
Connection failure prevents startup.
Middleware Validation

Validate:

Middleware executes in approved order.
Authentication context available.
Error middleware receives failures.
Error Framework Validation

Validate:

Known errors translated correctly.
Unknown errors handled safely.
API error contract preserved.
Foundation Completion Criteria

Foundation is complete when:

Application starts successfully.
Configuration validation passes.
Database connection established.
Middleware chain operational.
Error translation operational.
No module implementation required for startup.
## Foundation Rules
FP-01

All modules inherit the approved foundation.

FP-02

No module may redefine configuration loading.

FP-03

No module may access environment variables directly.

FP-04

No module may create independent database connections.

FP-05

Database connection ownership remains application-owned.

FP-06

Error translation remains centralized.

FP-07

Modules may create domain errors but may not create alternative error frameworks.

FP-08

Middleware registration remains application-owned.

FP-09

Modules may consume middleware but may not redefine middleware ordering.

FP-10

Bootstrap ownership remains centralized.

FP-11

Foundation components must remain domain-neutral.

FP-12

Cross-module dependencies remain prohibited during foundation implementation.

FP-13

Foundation implementation must not introduce business workflows.

FP-14

Foundation implementation must not introduce domain ownership.

FP-15

Module development may begin only after foundation validation succeeds.

## Compatibility Validation

Validated Against:

PROJECT_CONTEXT.md
ADR-001
ARCHITECTURE.md
DATABASE.md
INFRASTRUCTURE.md
API_CONTRACTS.md
Development Planning Principles
Backend Build Strategy

Validation Results:

No ownership violations detected.
No dependency violations detected.
No governance violations detected.
No module boundary violations detected.
No infrastructure conflicts detected.
No architectural redesign introduced.

Foundation Implementation Plan is compatible with approved architecture and approved development planning strategy.

# Module Implementation Roadmap — Part 4A

## Dependency-Based Module Sequence

### Context

The foundation implementation phase establishes the application structure required before domain implementation begins.

Module implementation begins only after completion of:

* Foundation Implementation Plan
* Application Bootstrap
* Database Bootstrap
* Configuration Foundation
* Error Framework
* Middleware Foundation

The implementation sequence must respect the approved module dependency graph.

Implementation sequencing exists to reduce integration risk, enable early validation, and minimize rework.

---

## Module Dependency Principles

### MRP-01 — Foundational Dependencies First

Modules with no upstream dependencies should be implemented before dependent modules.

### MRP-02 — Dependency Order Preserved

Implementation order must follow approved module dependency relationships.

Planning does not modify dependency direction.

### MRP-03 — End-to-End Vertical Slices

Each module should be implemented through complete vertical slices.

Partial layer implementation across multiple modules is prohibited.

### MRP-04 — Verification Before Expansion

A module should reach implementation stability before dependent modules begin development.

### MRP-05 — Derived Domains Last

Derived domains should be implemented after authoritative domains they consume.

### MRP-06 — Governance Deferred

Governance implementation remains deferred according to the approved roadmap.

Governance architecture remains approved.

Governance implementation remains Phase 2 work.

---

## Approved Module Dependency Graph

Identity
↓
Social Graph
↓
Content
↓
Feed

Identity
↓
Community
↓
Content
↓
Feed

Identity
↓
Media
↓
Content
↓
Feed

Governance remains deferred.

Feed remains dependent upon all authoritative content providers.

---

## Stage 1 — Foundational Domain

### Module 1 — Identity

Purpose

Establish platform identity and participation eligibility.

Capabilities

* Registration
* Authentication
* Session Management
* Profile Retrieval
* Profile Updates

Dependency Status

No upstream dependencies.

Implementation Priority

Highest.

Completion Requirement

Identity must be operational before dependent modules begin implementation.

---

## Stage 2 — Relationship Domain

### Module 2 — Social Graph

Purpose

Establish user-to-user relationships.

Capabilities

* Follow User
* Unfollow User
* Followers Retrieval
* Following Retrieval

Dependencies

* Identity

Rationale

Social Graph depends only on Identity and provides required relationships for Following Feed.

Completion Requirement

Relationship workflows operate end-to-end.

---

## Stage 3 — Community Foundation

### Module 3 — Community

Purpose

Establish community participation structure.

Capabilities

* Create Herd
* Update Herd
* Join Herd
* Leave Herd
* Membership Management

Dependencies

* Identity

Rationale

Community provides participation structures required by Herd content workflows.

Completion Requirement

Community lifecycle and membership workflows operate end-to-end.

---

## Stage 4 — Media Foundation

### Module 4 — Media

Purpose

Provide reusable image management.

Capabilities

* Upload Image
* Retrieve Image
* Remove Image

Dependencies

* Identity

Rationale

Media is an independent supporting domain consumed by multiple downstream modules.

Completion Requirement

Media lifecycle operates end-to-end.

---

## Stage 5 — Content Domain

### Module 5 — Content

Purpose

Establish platform discussion and participation capabilities.

Capabilities

* Personal Posts
* Herd Posts
* Comments
* Replies
* Voting

Dependencies

* Identity
* Community
* Media

Rationale

Content is the largest business domain and depends on participation, identity, and media capabilities.

Completion Requirement

Discussion workflows operate end-to-end.

---

## Stage 6 — Feed Domain

### Module 6 — Feed

Purpose

Provide content consumption experiences.

Capabilities

* Following Feed
* Herd Feed

Dependencies

* Identity
* Social Graph
* Community
* Content
* Media

Rationale

Feed consumes authoritative state from all previously implemented domains.

Feed implementation before dependency completion would create artificial stubs and increase rework.

Completion Requirement

Feed retrieval and composition operate end-to-end using authoritative domain data.

---

## Deferred Domain

### Governance

Status

Deferred to Phase 2 — Governance & Operations.

Reason

Governance implementation depends on operational moderation workflows that are intentionally excluded from Phase 1 implementation.

Approved governance architecture remains authoritative and unchanged.

---

## Implementation Sequence Summary

| Order    | Module                    | Dependency Status                                            |
| -------- | ------------------------- | ------------------------------------------------------------ |
| 0        | Foundation Implementation | Required Precondition                                        |
| 1        | Identity                  | No Dependencies                                              |
| 2        | Social Graph              | Depends on Identity                                          |
| 3        | Community                 | Depends on Identity                                          |
| 4        | Media                     | Depends on Identity                                          |
| 5        | Content                   | Depends on Identity, Community, Media                        |
| 6        | Feed                      | Depends on Identity, Social Graph, Community, Content, Media |
| Deferred | Governance                | Phase 2                                                      |

---

## Module Roadmap Validation

The implementation sequence confirms:

* Approved dependency graph is preserved.
* ADR-001 remains unchanged.
* Domain ownership boundaries remain unchanged.
* Governance boundaries remain unchanged.
* Feed remains a derived domain.
* Module-first development remains preserved.
* Vertical slice implementation remains preserved.
* Dependency-aware planning remains preserved.
* Implementation risk is minimized through progressive dependency realization.

---

## Planning Validation

Validated Against:

* PROJECT_CONTEXT.md
* ADR-001
* ARCHITECTURE.md
* DATABASE.md
* API_CONTRACTS.md
* Development Planning Principles
* Backend Build Strategy

Validation Results:

* No dependency conflicts detected.
* No ownership conflicts detected.
* No governance conflicts detected.
* No architectural redesign introduced.

Status:

Module Implementation Roadmap Part 4A approved as authoritative implementation planning guidance.

# Standard Module Development Pattern
## Purpose

The Standard Module Development Pattern defines the repeatable implementation approach that shall be used for all backend modules during development.

Its objectives are to:

Preserve approved architecture during implementation.
Standardize implementation across modules.
Reduce implementation uncertainty.
Support consistent validation.
Minimize architectural drift.
Reduce rework.
Improve implementation predictability.

The pattern applies to:

Identity
Social Graph
Community
Media
Content
Feed

Governance implementation remains deferred according to the approved roadmap.

Implementation planning serves the approved architecture.

Implementation patterns do not redefine architecture, ownership boundaries, authority boundaries, module boundaries, or API contracts.

## Module Development Principles
SMP-01 Architecture Preservation

Implementation shall preserve all approved architectural decisions.

Approved architecture remains authoritative throughout module development.

SMP-02 Vertical Slice Implementation

Capabilities shall be implemented end-to-end through the approved execution stack.

Implementation shall favor complete workflows over partial technical-layer completion.

SMP-03 Dependency Awareness

Module implementation shall respect the approved dependency graph.

Dependencies influence implementation sequencing.

Dependencies do not change during implementation.

SMP-04 Validation Before Expansion

New capabilities shall be validated before additional capabilities are introduced.

Validation reduces integration risk and implementation uncertainty.

SMP-05 Incremental Completion

Modules shall be completed through independently verifiable capabilities.

Implementation progresses through validated increments rather than large unverified batches.

SMP-06 Rework Minimization

Implementation shall prioritize stable foundations before dependent capabilities.

Dependent functionality should not be built on unverified implementation.

SMP-07 Ownership Preservation

Only the owning module may implement authoritative mutations for resources it owns.

Cross-module implementation must continue to use approved capability contracts.

SMP-08 Verification-Driven Development

Implementation completion is determined by successful execution and validation rather than file creation.

Working software is the primary measure of completion.

## Module Completion Philosophy

A module is not considered implemented because:

Directories exist.
Controllers exist.
Repositories exist.
Endpoints exist.
Database collections exist.

A module is complete only when:

Approved workflows execute successfully end-to-end.
Validation architecture executes correctly.
Persistence behavior functions correctly.
API contracts are satisfied.
Error handling behaves correctly.
Dependency interactions function correctly.
Required tests pass.
Module verification is completed.

Implementation completion is workflow-oriented rather than file-oriented.

The objective of module implementation is operational capability, not structural completeness.

## Standard Module Implementation Sequence

The following sequence is authoritative for all module implementation work.

Step 1 — Module Structure Creation

Establish the approved module structure.

Create:

Module boundaries
Folder structure
Public module contract
Internal organization

No business behavior is implemented at this stage.

Step 2 — Domain Models

Implement domain-owned models and aggregate structures.

Preserve:

Ownership boundaries
Aggregate boundaries
Lifecycle boundaries
Step 3 — Repository Contracts

Implement repository interfaces and persistence contracts.

Repositories remain owned by the module.

Repository responsibilities remain consistent with approved architecture.

Step 4 — Application Services

Implement application services for approved workflows.

Application Services remain:

Workflow owners
Transaction owners
Cross-module coordination owners
Step 5 — Module Contracts

Implement public capability contracts exposed to other modules.

Contracts expose capabilities rather than persistence details.

Cross-module communication shall remain capability-based.

Step 6 — API Layer Integration

Implement:

Routes
Controllers
Request mapping
Response mapping

API behavior shall remain compliant with approved API contracts.

Step 7 — Validation Integration

Implement:

Input validation
Authorization validation
Ownership validation
Governance validation
Domain validation

Validation ownership remains unchanged.

Step 8 — Error Handling Integration

Implement module-specific error behavior.

Ensure compatibility with:

Error architecture
Error propagation architecture
API error contracts
Step 9 — Testing

Validate:

Workflow execution
Domain behavior
Persistence behavior
Contract compliance
Error behavior
Step 10 — Module Verification

Perform final verification against:

Architecture
API contracts
Ownership boundaries
Dependency rules
Module exit criteria

Only verified modules may be considered complete.

## Vertical Slice Pattern

Capabilities shall be implemented using the approved vertical slice approach.

Authoritative Pattern:

Capability Selection
↓
Contract Review
↓
Workflow Implementation
↓
Validation Integration
↓
Testing
↓
Verification
↓
Completion

Capability Selection

Select a single approved capability.

Examples:

Register User
Login User
Follow User
Create Herd
Create Post
Contract Review

Review:

API contracts
Ownership rules
Authorization requirements
Governance requirements
Dependency requirements
Workflow Implementation

Implement the complete workflow through the approved execution architecture.

Validation Integration

Implement all required validation categories.

Testing

Verify workflow behavior.

Verification

Confirm architecture compliance before moving to the next capability.

## Validation Expectations

A capability shall not be considered complete until all required validation passes.

API Contract Validation

Verify compliance with approved request and response contracts.

Ownership Validation

Verify ownership boundaries remain preserved.

Only owning modules may mutate owned resources.

Authorization Validation

Verify authorization behavior aligns with approved authority rules.

Governance Validation

Verify governance restrictions and governance outcomes behave correctly where applicable.

Persistence Validation

Verify:

Resource creation
Resource updates
Resource retrieval
Resource lifecycle transitions

Persistence behavior must remain consistent with approved ownership rules.

Error Validation

Verify:

Expected failures
Validation failures
Authorization failures
Ownership failures
Governance failures
Persistence failures
Dependency Validation

Verify approved capability-contract interactions.

No dependency rule violations may be introduced.

## Module Exit Criteria

A module shall not be considered complete until all criteria are satisfied.

MEC-01

All approved module capabilities have been implemented.

MEC-02

All workflows execute end-to-end.

MEC-03

All API contracts are satisfied.

MEC-04

All required validation categories pass.

MEC-05

Persistence behavior is verified.

MEC-06

Error behavior is verified.

MEC-07

Approved dependency rules remain preserved.

MEC-08

Ownership boundaries remain preserved.

MEC-09

Layer responsibility boundaries remain preserved.

MEC-10

Cross-module interactions use approved capability contracts only.

MEC-11

Required tests pass.

MEC-12

Module verification completes without unresolved architectural conflicts.

Only after all exit criteria are satisfied may a module be marked complete.

## Implementation Constraints

The following constraints are authoritative.

IMC-01

Approved ownership boundaries remain unchanged.

IMC-02

Approved dependency graph remains unchanged.

IMC-03

Approved capability contracts remain the exclusive cross-module communication mechanism.

IMC-04

Governance authority boundaries remain unchanged.

IMC-05

Feed remains a derived read-only module.

Feed shall not acquire authoritative state ownership.

IMC-06

Layer responsibilities remain unchanged.

Preserve:

Controllers as transport adapters
Application Services as workflow owners
Domain Layer as business rule owner
Repositories as persistence owners
IMC-07

Database ownership rules remain authoritative.

IMC-08

Infrastructure simplicity principles remain unchanged.

IMC-09

Implementation planning may refine implementation details but may not redesign approved architecture.

## Planning Validation

Validated against:

PROJECT_CONTEXT.md
ADR-001
ARCHITECTURE.md
DATABASE.md
API_CONTRACTS.md
Development Planning Principles
Backend Build Strategy
Module Implementation Roadmap

Validation Results:

No ownership conflicts detected.
No dependency conflicts detected.
No governance conflicts detected.
No API contract conflicts detected.
No database ownership conflicts detected.
No infrastructure conflicts detected.
No architectural redesign introduced.

Status:

Standard Module Development Pattern approved as authoritative implementation planning guidance.

