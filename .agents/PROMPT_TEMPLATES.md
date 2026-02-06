# Prompt Templates for AI Agents

> Ready-to-use prompt templates for backend and frontend development agents. Copy, fill in placeholders, and use.

---

## Table of Contents

### Backend Agents (Spring Boot / Java)

1. [Architecture Agent](#1-architecture-agent)
2. [Code Generation Agent](#2-code-generation-agent)
3. [Testing Agent](#3-testing-agent)
4. [Security Agent](#4-security-agent)
5. [Performance Agent](#5-performance-agent)
6. [Database Agent](#6-database-agent)
7. [DevOps Agent](#7-devops-agent)
8. [Documentation Agent](#8-documentation-agent)
9. [Review Agent](#9-review-agent)
10. [Debugging Agent](#10-debugging-agent)
11. [Software Analyst Agent](#11-software-analyst-agent)
    - [General Analysis](#general-analysis)
    - [Senior Functional Analyst Mode](#senior-functional-analyst-mode)
    - [Functional Verifier Mode](#functional-verifier-mode)
    - [Senior QA Analyst Mode](#senior-qa-analyst-mode)
12. [Documentation Generation](#12-documentation-generation)
13. [Quick Prompts](#13-quick-prompts)

### Frontend Agents (Angular / TypeScript)

14. [Frontend Architecture Agent](#14-frontend-architecture-agent)
15. [Angular Agent](#15-angular-agent)
16. [Tailwind Agent](#16-tailwind-agent)
17. [UX & Accessibility Agent](#17-ux--accessibility-agent)
18. [State Management Agent](#18-state-management-agent)
19. [Frontend Security Agent](#19-frontend-security-agent)
20. [Frontend Performance Agent](#20-frontend-performance-agent)
21. [Frontend Testing Agent](#21-frontend-testing-agent)
22. [Icons Agent](#22-icons-agent)
23. [Animations Agent](#23-animations-agent)
24. [Environments Agent](#24-environments-agent)
25. [Mock Layer Agent](#25-mock-layer-agent)
26. [Frontend Quick Prompts](#26-frontend-quick-prompts)

---

## 1. Architecture Agent

### Architecture Design Request

```markdown
@ArchitectAgent

I need architectural guidance for {domain}.

**Requirements:**
{requirements}

**Constraints:**
{constraints}

**Please provide:**
- Architecture design with diagrams (PlantUML/C4)
- Component interactions
- Trade-off analysis
- ADR (Architecture Decision Record)
```

### Microservices Design

```markdown
@ArchitectAgent

## Microservices Architecture Design

**Domain:** {domain_name}

**Business Capabilities:**
1. {capability_1}
2. {capability_2}
3. {capability_3}

**Current State:** {monolith/existing_services}

**Please provide:**
1. Service decomposition with bounded contexts
2. Communication patterns (sync REST, async messaging)
3. Data consistency strategy
4. API gateway design
5. Service mesh considerations
6. Deployment topology
```

---

## 2. Code Generation Agent

### Generate Component

```markdown
@CodeGenAgent

Generate {component_type} for {entity_name} with:

**Requirements:**
{requirements}

**Relationships:**
{relationships}

**Validation Rules:**
{validation}

**Java 21 Features:** Use virtual threads, records, pattern matching where applicable.

Include all necessary annotations and follow Spring Boot 3.4+ best practices.
```

### Generate Complete CRUD

```markdown
@CodeGenAgent

## Generate Complete CRUD for Entity

**Entity Name:** {EntityName}

**Fields:**
| Field | Type | Constraints |
|-------|------|-------------|
| {field1} | {type} | {constraints} |
| {field2} | {type} | {constraints} |

**Relationships:**
- {relationship_description}

**Generate:**
1. Entity with JPA annotations
2. DTO (Request/Response)
3. Mapper (MapStruct)
4. Repository with custom queries
5. Service interface and implementation
6. REST Controller with all CRUD endpoints
7. Exception handling
```

---

## 3. Testing Agent

### Generate Test Suite

```markdown
@TestingAgent

Generate comprehensive tests for {class_name}:

**Class Under Test:**
{class_code_or_description}

**Requirements:**
- Unit tests covering all methods
- Edge cases and boundary conditions
- Exception scenarios
- Integration tests if applicable

**Mocking Strategy:**
{dependencies_to_mock}

Use BDD style (given-when-then) and ensure test independence.
```

### Integration Test with TestContainers

```markdown
@TestingAgent

## Generate Integration Test

**Service/Controller:** {component_name}

**Database:** {PostgreSQL/MySQL/MongoDB}

**External Dependencies:**
- {dependency_1}
- {dependency_2}

**Generate:**
1. TestContainers setup
2. Test data builders
3. Integration test scenarios
4. Cleanup strategies
```

---

## 4. Security Agent

### Security Code Review

```markdown
@SecurityAgent

Review this code for security vulnerabilities:

```java
{code}
```

**Check for:**
- SQL injection
- XSS vulnerabilities
- Authentication/authorization issues
- Sensitive data exposure
- OWASP Top 10 vulnerabilities

**Provide:**
- Vulnerability report
- Secure alternatives
- Best practices recommendations
```

### Implement Authentication

```markdown
@SecurityAgent

## Implement Authentication System

**Type:** {JWT/OAuth2/Session}

**Requirements:**
- {requirement_1}
- {requirement_2}

**Roles:** {ADMIN, USER, etc.}

**Generate:**
1. Security configuration
2. Authentication filter/provider
3. Token service (if JWT)
4. User details service
5. Password encoding setup
```

---

## 5. Performance Agent

### Performance Analysis

```markdown
@PerformanceAgent

Analyze performance of {component}:

**Current Metrics:**
{metrics}

**Issues Observed:**
{issues}

**Provide optimization recommendations with:**
1. Root cause analysis
2. Code improvements
3. Configuration changes
4. Expected performance gains
5. Monitoring recommendations
```

### Query Optimization

```markdown
@PerformanceAgent

## Optimize Database Queries

**Problematic Query/Method:**
{query_or_code}

**Current Performance:**
- Response time: {time}
- Records processed: {count}

**Analyze and provide:**
1. Query execution plan analysis
2. Index recommendations
3. Query rewrite suggestions
4. Caching opportunities
5. Pagination strategies
```

---

## 6. Database Agent

### Database Schema Design

```markdown
@DatabaseAgent

Design database schema for {domain}:

**Entities:**
{entities}

**Relationships:**
{relationships}

**Scale:**
{expected_data_volume}

**Provide:**
1. Schema DDL
2. Indexing strategy
3. JPA entities
4. Flyway migrations
5. Optimization tips
```

### Migration Script

```markdown
@DatabaseAgent

## Generate Database Migration

**Change Type:** {ADD_TABLE/ADD_COLUMN/MODIFY/etc.}

**Description:**
{change_description}

**Target Table(s):** {tables}

**Generate:**
1. Flyway migration script (V{version}__{description}.sql)
2. Rollback script
3. Data migration if needed
4. Updated JPA entity
```

---

## 7. DevOps Agent

### Deployment Configuration

```markdown
@DevOpsAgent

Create deployment configuration for {service}:

**Platform:** {Docker/Kubernetes/AWS ECS}

**Requirements:**
{requirements}

**Provide:**
1. Dockerfile (multi-stage build)
2. Kubernetes manifests (or Docker Compose)
3. CI/CD pipeline (GitHub Actions)
4. Monitoring setup
5. Deployment strategy (rolling/blue-green)
```

### CI/CD Pipeline

```markdown
@DevOpsAgent

## Generate CI/CD Pipeline

**Repository:** {GitHub/GitLab}

**Build Tool:** {Gradle/Maven}

**Stages Required:**
- [ ] Build
- [ ] Unit Tests
- [ ] Integration Tests
- [ ] Security Scan
- [ ] Docker Build
- [ ] Deploy to {environment}

**Generate complete pipeline configuration.**
```

---

## 8. Documentation Agent

### API Documentation

```markdown
@DocumentationAgent

Generate documentation for {component}:

**Type:** {OpenAPI/README/Guide}

**Audience:** {developers/end-users/ops}

**Include:**
- Setup instructions
- Usage examples
- API specs
- Troubleshooting tips
- Best practices
```

### OpenAPI Specification

```markdown
@DocumentationAgent

## Generate OpenAPI Spec

**Service:** {service_name}

**Endpoints:**
| Method | Path | Description |
|--------|------|-------------|
| {method} | {path} | {description} |

**Generate:**
1. Complete OpenAPI 3.0 specification
2. Request/Response schemas
3. Error responses
4. Authentication requirements
5. Example requests/responses
```

---

## 9. Review Agent

### Code Review

```markdown
@ReviewAgent

Review this code:

```java
{code}
```

**Analyze for:**
- SOLID principles compliance
- Design patterns usage
- Spring Boot best practices
- Performance issues
- Security vulnerabilities
- Testability

**Provide:**
- Specific refactoring recommendations
- Code examples for improvements
- Priority of changes (critical/important/nice-to-have)
```

### Architecture Review

```markdown
@ReviewAgent

## Review Architecture Decision

**Decision:** {description}

**Context:**
{context}

**Alternatives Considered:**
1. {alternative_1}
2. {alternative_2}

**Review for:**
1. Alignment with system architecture
2. Scalability implications
3. Maintainability
4. Security considerations
5. Technical debt
```

---

## 10. Debugging Agent

### Debug Issue

```markdown
@DebuggingAgent

Debug this issue:

**Problem:**
{problem_description}

**Error Logs:**
```
{logs}
```

**Stack Trace:**
```
{stack_trace}
```

**Context:**
{context}

**Provide:**
1. Root cause analysis
2. Step-by-step debugging approach
3. Solution with code examples
4. Prevention recommendations
```

### Memory Leak Investigation

```markdown
@DebuggingAgent

## Investigate Memory Issue

**Symptoms:**
{symptoms}

**Heap Dump Analysis:**
{findings_if_any}

**Suspect Areas:**
- {area_1}
- {area_2}

**Provide:**
1. Memory leak identification
2. Code fixes
3. JVM tuning recommendations
4. Monitoring setup
```

---

## 11. Software Analyst Agent

### General Analysis

```markdown
@SoftwareAnalystAgent

Analyze the following feature request:

**Feature:** {feature_description}

**Business Context:** {business_context}

**Stakeholders:** {stakeholders}

**Current System State:** {current_state}

**Please provide (using mandatory templates):**
1. Detailed feature breakdown with sub-features
2. User stories following user-story-template.md
3. Functional requirements list with MoSCoW prioritization
4. Non-functional requirements
5. Dependencies and integration points
6. Potential risks and mitigation strategies
7. Suggested implementation approach
8. Effort estimation considerations
9. GitHub-ready feature issues
10. Test cases in Gherkin format
```

### Senior Functional Analyst Mode

```markdown
@SoftwareAnalystAgent [Senior Functional Analyst Mode]

## Functional Analysis Request

**Business Problem/Need:**
{problem_description}

**Domain Context:**
{domain_context}

**Stakeholders:**
{stakeholders}

**Please provide:**
1. Business need investigation summary
2. Functional and non-functional requirements analysis
3. Explicit and implicit business rules identification
4. Epic documentation following epic-template.md
5. User stories decomposition following user-story-template.md
6. Main and alternative scenarios
7. Input/Process/Output documentation
8. Impact analysis on related systems
```

### Functional Verifier Mode

```markdown
@SoftwareAnalystAgent [Functional Analyst Verifier Mode]

## Documentation Verification Request

**Document to Verify:** {document_type} - {document_id}

**Content:**
{document_content}

**Please verify:**
1. Compliance with official template structure
2. All mandatory sections are complete
3. Business rules are explicit and unambiguous
4. Acceptance criteria are testable and measurable
5. No ambiguous language or hidden assumptions
6. Traceability is maintained (Epic → Story → AC)
7. INVEST criteria validation (for user stories)
8. Definition of Done compliance

**Provide:**
- Verification status (APPROVED / NEEDS CORRECTION)
- List of issues found (if any)
- Specific correction recommendations
```

### Senior QA Analyst Mode

```markdown
@SoftwareAnalystAgent [Senior QA Analyst Mode]

## Test Case Design Request

**Epic:** {epic_id} - {epic_name}
**User Story:** {story_id} - {story_name}

**Acceptance Criteria:**
{acceptance_criteria}

**Business Rules:**
{business_rules}

**Please design test cases covering:**
1. Main flows (positive cases)
2. Negative cases (errors, validations, messages)
3. Edge cases (limits, extreme values)
4. Business rules validation
5. Acceptance criteria verification
6. Calculations, balances, amounts (when applicable)

**Deliverables:**
- Test cases in natural language (following natural-language-test-case-template.md)
- Test cases in Gherkin format (following gherkin-test-case-template.md)
- Traceability matrix linking test cases to AC and BR
```

---

## 12. Documentation Generation

### Generate Epic

```markdown
@SoftwareAnalystAgent

## Generate Epic Documentation

**Instructions:** Create a complete epic following the mandatory template at 
`docs/standards/templates/epic-template.md`. Fill in ALL sections.

---

**Epic Name:** {name}

**Business Problem/Opportunity:**
{description}

**Target Users:**
- {persona_1}
- {persona_2}

**High-Level Requirements:**
1. {requirement_1}
2. {requirement_2}
3. {requirement_3}

**Success Criteria:**
- {criteria}

**Known Constraints:**
- {constraints}

---

**Generate the following:**
1. Complete Epic Header with ID, Owner, Status
2. Business Objective and Problem Statement
3. Proposed Solution with Key Features
4. Detailed Scope (In/Out of Scope, Assumptions, Constraints)
5. Stakeholder analysis
6. User personas table
7. User Stories breakdown with IDs, priorities, and status
8. Functional Requirements (MoSCoW prioritization)
9. Non-Functional Requirements table
10. Dependencies and Risks with mitigations
11. Success Metrics with current/target values
12. Timeline with milestones
13. Mermaid process flow diagram
14. Approval section
```

### Generate User Stories

```markdown
@SoftwareAnalystAgent

## Generate User Stories

**Instructions:** Create user stories following the mandatory template at
`docs/standards/templates/user-story-template.md`. Each story must be complete.

---

**Epic:** {epic_name} (EPIC-XXX)

**Feature Description:**
{feature_description}

**User Roles Involved:**
- {role_1}: {description}
- {role_2}: {description}

**Key Functionality:**
1. {functionality_1}
2. {functionality_2}
3. {functionality_3}

**Business Rules:**
- {rule_1}
- {rule_2}

---

**For EACH user story, generate:**
1. Story Header (ID, Epic, Priority, Story Points, Sprint)
2. User Story Statement (As a / I want / So that)
3. Detailed Description
4. Scope (In Scope / Out of Scope)
5. Acceptance Criteria in Gherkin format (minimum 3 per story)
6. Business Rules table
7. Input / Process / Output section
8. Technical Notes (API, Database, Dependencies)
9. Dependencies (Blocked By / Blocks)
10. Definition of Done checklist
11. INVEST Validation table
12. Open Questions and Notes
```

### Generate GitHub Feature Issue

```markdown
@SoftwareAnalystAgent

## Generate GitHub Feature Issue

**Instructions:** Create a GitHub-ready feature issue following the template at
`docs/standards/templates/github-feature-issue-template.md`. Ready for Copilot/developer.

---

**Feature to Implement:** {feature}

**Related User Story:** US-{id} - {title}
**Related Epic:** EPIC-{id} - {title}

**Technical Context:**
- Framework: {Spring Boot 3.4+}
- Language: {Java 21}
- Database: {PostgreSQL}

**Existing Code Context:**
{context}

---

**Generate:**
1. Feature Overview (ID, Epic, Story, Priority, Effort)
2. Description with business value
3. User Story statement
4. Acceptance Criteria in Gherkin (minimum 3)
5. Technical Requirements (API, Data Model, DB Changes)
6. Files to Create/Modify with directory structure
7. Implementation Guide with code snippets
8. Testing Requirements
9. Security Considerations
10. Performance Considerations
11. Documentation Requirements
12. Definition of Done checklist
13. AI Implementation Instructions
```

### Generate Gherkin Test Cases

```markdown
@SoftwareAnalystAgent

## Generate Gherkin Test Cases

**Instructions:** Create comprehensive Gherkin test cases following the template at
`docs/standards/templates/gherkin-test-case-template.md`.

---

**User Story:** US-{id} - {title}
**Epic:** EPIC-{id} - {title}

**Feature Description:**
{description}

**Acceptance Criteria to Cover:**
- AC-01: {criterion}
- AC-02: {criterion}
- AC-03: {criterion}

**Business Rules:**
- BR-01: {rule}
- BR-02: {rule}

---

**Generate:**
1. Test Case Header (ID, Epic, Story, Business Rules, AC references)
2. Complete Feature file with:
   - Feature description (As a / I want / So that)
   - Background section for common preconditions
   - Happy Path Scenarios (minimum 2)
   - Validation Scenarios (minimum 2)
   - Edge Case Scenarios (minimum 2)
   - Error Handling Scenarios (minimum 1)
   - Data-Driven Scenarios with Examples table
3. Test Data Requirements table
4. Traceability Matrix linking TC → AC → BR
5. Automation Notes
6. Environment Requirements table
```

### Generate Natural Language Test Cases

```markdown
@SoftwareAnalystAgent

## Generate Natural Language Test Cases

**Instructions:** Create detailed natural language test cases following the template at
`docs/standards/templates/natural-language-test-case-template.md`.

---

**User Story:** US-{id} - {title}
**Epic:** EPIC-{id} - {title}

**Feature Description:**
{description}

**Test Scenarios to Cover:**
1. {scenario_1}
2. {scenario_2}
3. {scenario_3}

---

**For EACH test case, generate:**
1. Test Case Identification (ID, Name, Version, Dates)
2. Functional References (Epic, Story, BR, AC)
3. Test Classification (Type, Priority, Complexity, Duration)
4. Test Objective
5. Detailed Test Description
6. Preconditions table
7. Test Data (Input and Reference data)
8. Step-by-step Test Steps table
9. Expected Results
10. Postconditions / Cleanup steps
11. Test Variations
12. Edge Cases & Boundary Conditions table
13. Error Scenarios table
14. Dependencies
15. Notes for tester
```

### Generate Complete Feature Package

```markdown
@SoftwareAnalystAgent

## Generate Complete Feature Documentation Package

**Instructions:** Create a COMPLETE documentation package for this feature using
ALL mandatory templates. Ready for sprint planning and implementation.

---

**Feature Name:** {name}

**Business Context:**
{context}

**Current State:**
{current}

**Desired State:**
{desired}

**User Personas:**
- {persona_1}: {description}
- {persona_2}: {description}

**High-Level Requirements:**
1. {requirement_1}
2. {requirement_2}
3. {requirement_3}
4. {requirement_4}

**Technical Context:**
- Framework: {Spring Boot 3.4+}
- Language: {Java 21}
- Database: {PostgreSQL}
- Architecture: {Microservices, REST API}

**Constraints:**
- {constraint_1}
- {constraint_2}

---

**Generate the COMPLETE package:**

### 1. Epic Documentation (epic-template.md)
- Full epic with all sections
- Mermaid diagrams for process flow

### 2. User Stories (user-story-template.md)
- 4-8 user stories depending on complexity
- Each with complete acceptance criteria
- INVEST validation for each

### 3. GitHub Feature Issues (github-feature-issue-template.md)
- One issue per user story
- Ready for Copilot/developer assignment
- Complete implementation guides

### 4. Test Cases (gherkin-test-case-template.md)
- Gherkin test cases for each story
- Full scenario coverage
- Traceability matrix

### 5. Summary Documentation
- Feature overview
- Story map visualization
- Implementation roadmap
- Risk assessment
```

---

## 13. Quick Prompts

### Quick User Story

```markdown
@SoftwareAnalystAgent

**Quick User Story:** {one_sentence_description}

**User Type:** {role}

**Generate:** Complete user story following user-story-template.md with
INVEST validation and Gherkin acceptance criteria.
```

### Quick GitHub Issue

```markdown
@SoftwareAnalystAgent

**Quick Feature:** {one_sentence_description}

**Tech Stack:** {Spring Boot, Java 21, PostgreSQL}

**Generate:** Complete GitHub issue following github-feature-issue-template.md
ready for Copilot implementation.
```

### Quick Test Cases

```markdown
@SoftwareAnalystAgent

**Story:** US-{id} - {title}

**Acceptance Criteria:**
- AC-01: {criterion}
- AC-02: {criterion}

**Generate:** Complete Gherkin test cases following gherkin-test-case-template.md
with happy path, validation, and edge case scenarios.
```

### Quick Code Review

```markdown
@ReviewAgent

**Review this code quickly:**
```java
{code}
```

**Focus on:** {SOLID/Security/Performance/All}
```

### Quick Debug

```markdown
@DebuggingAgent

**Error:** {error_message}

**Context:** {what_was_happening}

**Quick diagnosis and fix please.**
```

---

## Multi-Agent Workflow Prompts

### New Feature Development (All Agents)

```markdown
## New Feature Development Workflow

**Feature:** {feature_name}

**Execute the following workflow:**

1. @ArchitectAgent - Design feature architecture
2. @DatabaseAgent - Design database schema and migrations
3. @CodeGenAgent - Generate entities, services, controllers
4. @SecurityAgent - Review security implications
5. @TestingAgent - Generate test suite
6. @PerformanceAgent - Review performance considerations
7. @DocumentationAgent - Generate API documentation
8. @ReviewAgent - Final code review
```

### Feature Analysis to Implementation

```markdown
## Feature Analysis to Implementation Workflow

**Feature:** {feature_name}

**Execute:**

1. @SoftwareAnalystAgent - Analyze requirements, create epic and user stories
2. @ArchitectAgent - Technical feasibility review
3. @SoftwareAnalystAgent - Generate GitHub issues for each story
4. @SoftwareAnalystAgent - Generate test cases
5. @ReviewAgent - Validate documentation package
```

### Bug Fix Workflow

```markdown
## Bug Fix Workflow

**Bug:** {bug_description}

**Execute:**

1. @DebuggingAgent - Diagnose issue and identify root cause
2. @CodeGenAgent - Implement fix
3. @TestingAgent - Create regression tests
4. @ReviewAgent - Review fix quality
```

---

## Template Reference

| Template | Location | Used By |
|----------|----------|---------|
| Epic | `docs/standards/templates/epic-template.md` | SoftwareAnalystAgent |
| User Story | `docs/standards/templates/user-story-template.md` | SoftwareAnalystAgent |
| GitHub Issue | `docs/standards/templates/github-feature-issue-template.md` | SoftwareAnalystAgent |
| Gherkin Tests | `docs/standards/templates/gherkin-test-case-template.md` | SoftwareAnalystAgent, TestingAgent |
| Natural Language Tests | `docs/standards/templates/natural-language-test-case-template.md` | SoftwareAnalystAgent, TestingAgent |

---

# Frontend Agents (Angular / TypeScript)

---

## 14. Frontend Architecture Agent

### Frontend Architecture Design

```markdown
@FrontendArchitectAgent @skill angular-architecture

Design frontend architecture for {feature}.

**Requirements:**
{requirements}

**UI/UX Constraints:**
{constraints}

**Please provide:**
- Folder structure with feature modules (use @skill angular-architecture pattern)
- Routing strategy with lazy loading (@skill angular-routing)
- Shared vs feature component separation
- State management approach: Signals (@skill angular-signals) for local state, advanced patterns (@skill signal-state-management)
- Architectural decisions with rationale
```

### Feature Module Design

```markdown
@FrontendArchitectAgent @skill angular-architecture @skill angular-routing

## Design Feature Module Architecture

**Feature:** {feature_name}

**Capabilities:**
1. {capability_1}
2. {capability_2}
3. {capability_3}

**Integration Points:**
- Backend APIs: {api_endpoints}
- Shared components: {shared_components}

**Please provide (using these skills):**
1. Feature module structure (@skill angular-architecture)
2. Smart vs presentational component breakdown (@skill angular-components)
3. Service layer design (@skill angular-services)
4. State management strategy (@skill angular-signals + @skill signal-state-management)
5. Routing configuration (@skill angular-routing)
6. Lazy loading strategy (@skill angular-routing)
```

---

## 15. Angular Agent

### Generate Angular Component

```markdown
@AngularAgent @skill angular-components @skill angular-standalone @skill angular-signals

Generate Angular {component_type} for {feature} with:

**Requirements:**
{requirements}

**Inputs:**
{inputs}

**Outputs:**
{outputs}

**Follow Angular 21+ best practices:**
- Standalone component (@skill angular-standalone)
- Signals for local state (@skill angular-signals)
- OnPush change detection via signals
- Typed inputs/outputs with input()/output() helpers
- Proper lifecycle hooks using effect()
- Accessibility (@skill accessibility-wcag)
```

### Generate Complete Feature

```markdown
@AngularAgent

## Generate Complete Feature Module

**Feature Name:** {FeatureName}

**Components:**
| Component | Type | Description |
|-----------|------|-------------|
| {component1} | Smart | {description} |
| {component2} | Presentational | {description} |

**Services:**
- {service_name}: {responsibility}

**Generate (using these skills):**
1. Standalone components (@skill angular-standalone) with signals (@skill angular-signals)
2. Feature service (@skill angular-services) with HttpClient and caching
3. Models and interfaces (@skill typescript)
4. Routing configuration (@skill angular-routing)
5. Barrel exports (index.ts)
6. Component tests (@skill angular-testing)
7. Styled with Tailwind (@skill tailwind-4) and accessibility (@skill accessibility-wcag)
```

### Generate Service

```markdown
@AngularAgent @skill angular-services @skill angular-signals @skill rxjs-patterns

## Generate Angular Service

**Service Name:** {ServiceName}

**Responsibilities:**
- {responsibility_1}
- {responsibility_2}

**API Endpoints:**
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | {endpoint} | {description} |
| POST | {endpoint} | {description} |

**Generate (using these skills):**
1. Service with HttpClient injection (@skill angular-services)
2. Typed request/response interfaces (@skill typescript)
3. Error handling with catchError (@skill rxjs-patterns)
4. Loading state management with signals (@skill angular-signals)
5. Caching strategy if applicable (@skill signal-state-management)
```

---

## 16. Tailwind Agent

### Style Component

```markdown
@TailwindAgent @skill tailwind-4 @skill accessibility-wcag

Style this component using Tailwind CSS:

**Component:** {component_name}

**Design Requirements:**
{requirements}

**Generate styling that is:**
- Mobile-first responsive (@skill tailwind-4)
- Accessible with proper contrast and focus states (@skill accessibility-wcag)
- Consistent with design system (see tailwind.config.js theme)
- Dark mode compatible (dark: variants) (@skill tailwind-4)
- Using only Tailwind utilities - NO custom CSS, NO var() usage
```

### Design System Setup

```markdown
@TailwindAgent @skill tailwind-4 @skill ngx-env-builder

## Configure Design System

**Brand Colors:**
- Primary: {hex}
- Secondary: {hex}
- Accent: {hex}

**Typography:**
- Font Family: {font}
- Scale: {sm, base, lg, xl, 2xl}

**Spacing:**
- Base unit: {4px, 8px}

**Generate:**
1. tailwind.config.js with custom theme (@skill tailwind-4)
2. CSS custom properties (no var() in className - use Tailwind colors)
3. Utility classes for common patterns
4. Dark mode configuration with dark: variants
5. Example component showcasing design system
```

### Responsive Layout

```markdown
@TailwindAgent @skill tailwind-4 @skill hugeicons-implementation

## Create Responsive Layout

**Layout Type:** {grid/flexbox/dashboard}

**Breakpoints:**
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

**Requirements:**
{layout_requirements}

**Generate (using these skills):**
1. Responsive container structure (@skill tailwind-4)
2. Grid/flex layout with breakpoints (@skill tailwind-4)
3. Mobile navigation pattern with icons (@skill hugeicons-implementation)
4. Spacing and sizing utilities (@skill tailwind-4)
5. Ensure accessibility (@skill accessibility-wcag)
```

---

## 17. UX & Accessibility Agent

### Accessibility Audit

```markdown
@UXAgent @skill accessibility-wcag @skill tailwind-4

Review UI for accessibility and UX:

**Component/Page:** {component_name}

**Current Implementation:**
{code_or_description}

**Please provide (using these skills):**
1. WCAG 2.1 AA compliance check (@skill accessibility-wcag)
2. Keyboard navigation improvements (@skill accessibility-wcag)
3. Screen reader compatibility with proper ARIA (@skill accessibility-wcag)
4. Focus management recommendations (@skill accessibility-wcag)
5. Color contrast issues (@skill tailwind-4 semantic colors)
6. ARIA attribute suggestions (@skill accessibility-wcag)
```

### Form Accessibility

```markdown
@UXAgent @skill accessibility-wcag @skill angular-forms

## Improve Form Accessibility

**Form Purpose:** {purpose}

**Fields:**
{list_of_fields}

**Please provide (using these skills):**
1. Proper label-input associations (@skill accessibility-wcag)
2. Error message accessibility with aria-describedby (@skill accessibility-wcag)
3. Required field indicators (@skill accessibility-wcag)
4. Focus order optimization (tabindex strategy) (@skill accessibility-wcag)
5. Validation feedback for screen readers with aria-invalid (@skill accessibility-wcag)
6. Auto-complete attributes (@skill angular-forms)
```

### UX Flow Review

```markdown
@UXAgent

## Review User Flow

**Flow Name:** {flow_name}

**Steps:**
1. {step_1}
2. {step_2}
3. {step_3}

**Please analyze:**
1. Cognitive load reduction opportunities
2. Error prevention strategies
3. Feedback mechanisms
4. Loading state UX
5. Empty state handling
6. Mobile UX considerations
```

---

## 18. State Management Agent

### Design State Management

```markdown
@StateAgent @skill angular-signals @skill signal-state-management

Design state management for {feature}.

**State Requirements:**
- {requirement_1}
- {requirement_2}

**Data Flow:**
{describe_data_flow}

**Please provide (using these skills):**
1. Local state with signals (@skill angular-signals)
2. Computed values for derived state (@skill angular-signals)
3. Effects for side effects (@skill angular-signals)
4. Service layer for API calls (@skill angular-services)
5. State synchronization strategy (@skill signal-state-management)
```

### Signal-Based State

```markdown
@StateAgent @skill angular-signals

## Implement Signal-Based State

**Feature:** {feature_name}

**State Shape:**
```typescript
interface {Feature}State {
  {property}: {type};
  loading: boolean;
  error: string | null;
}
```

**Generate (using this skill):**
1. State service with signals (@skill angular-signals)
2. Computed signals for derived values (@skill angular-signals)
3. Effect for persistence/logging (@skill angular-signals)
4. State selectors/accessors (@skill angular-signals)
5. Actions/mutations pattern (@skill angular-signals)
```

### Complex State with NgRx

```markdown
@StateAgent

## Design NgRx State (when justified)

**Feature:** {feature_name}

**Justification for NgRx:**
{why_ngrx_over_signals}

**State Requirements:**
{requirements}

**Generate:**
1. Feature state interface
2. Actions with typed payloads
3. Reducer with immutable updates
4. Selectors with memoization
5. Effects for async operations
6. Facade service for encapsulation
```

---

## 19. Frontend Security Agent

### Security Review

```markdown
@FrontendSecurityAgent @skill angular-security @skill accessibility-wcag

Review frontend code for security issues:

**Code/Component:**
{code}

**Please check for (using these skills):**
1. XSS vulnerabilities (@skill angular-security)
2. CSRF protection (@skill angular-security)
3. Sensitive data in localStorage/sessionStorage (@skill angular-security)
4. Secure token handling (@skill angular-security)
5. Content Security Policy compliance (@skill angular-security)
6. Third-party script risks (@skill angular-security)

**Provide:**
- Vulnerability report with severity
- Secure alternatives with code examples
- Security best practices
```

### Secure Auth Implementation

```markdown
@FrontendSecurityAgent @skill angular-security @skill angular-routing

## Implement Secure Authentication

**Auth Type:** {JWT/OAuth2/Session}

**Requirements:**
- Token storage: {httpOnly cookie/memory}
- Refresh strategy: {silent refresh/explicit}
- Session timeout: {duration}

**Generate (using these skills):**
1. Auth service with secure token handling (@skill angular-security)
2. HTTP interceptor for token injection (@skill angular-security, @skill angular-services)
3. Route guards for protected routes (@skill angular-security, @skill angular-routing)
4. Logout with token cleanup (@skill angular-security)
5. Session timeout handling (@skill angular-security)
```

---

## 20. Frontend Performance Agent

### Performance Analysis

```markdown
@FrontendPerformanceAgent @skill angular-routing

Analyze frontend performance for {feature}.

**Current Metrics:**
- LCP: {value}
- FID: {value}
- CLS: {value}
- Bundle size: {value}

**Issues Observed:**
{issues}

**Provide:**
1. Root cause analysis
2. Code splitting opportunities (@skill angular-routing for lazy loading)
3. Lazy loading recommendations (@skill angular-routing)
4. Image optimization strategies
5. Caching improvements
6. Expected performance gains
```

### Bundle Optimization

```markdown
@FrontendPerformanceAgent

## Optimize Bundle Size

**Current Bundle:**
- Main: {size}
- Vendor: {size}
- Lazy chunks: {sizes}

**Analysis:**
{webpack_bundle_analyzer_output}

**Provide:**
1. Large dependency alternatives
2. Tree-shaking opportunities
3. Dynamic import strategies
4. Compression configuration
5. CDN recommendations
```

---

## 21. Frontend Testing Agent

### Component Test Suite

```markdown
@FrontendTestingAgent @skill angular-testing @skill angular-components

Generate tests for {component}:

**Component Description:**
{description}

**Key Behaviors:**
1. {behavior_1}
2. {behavior_2}
3. {behavior_3}

**Generate (using these skills):**
1. Unit tests with Jest (@skill angular-testing)
2. Component tests with Testing Library (@skill angular-testing)
3. Input/output validation tests (@skill angular-components)
4. User interaction tests (@skill angular-testing)
5. Accessibility tests (@skill accessibility-wcag)
6. Snapshot tests (if appropriate)
```

### E2E Test Suite

```markdown
@FrontendTestingAgent @skill angular-testing

## Generate E2E Tests

**Feature:** {feature_name}

**Critical User Flows:**
1. {flow_1}
2. {flow_2}

**Generate with Playwright (using this skill):**
1. Page object models (@skill angular-testing)
2. Test scenarios for each flow
3. API mocking setup (@skill json-server-mocks)
4. Screenshot comparison
5. Accessibility checks (@skill accessibility-wcag)
6. Mobile viewport tests
```

---

## 22. Icons Agent

### Implement Icons

```markdown
@IconsAgent @skill hugeicons-implementation

Implement icons for {component}.

**Required Icons:**
| Icon | Use Case | Size |
|------|----------|------|
| {icon_name} | {use_case} | {size} |

**Generate (using this skill):**
1. Import from @hugeicons/angular (@skill hugeicons-implementation)
2. Proper sizing (w-4, w-6, etc.) (@skill tailwind-4)
3. Color using currentColor (@skill tailwind-4)
4. Accessibility attributes (aria-hidden or aria-label) (@skill accessibility-wcag)
5. Dark mode compatibility (@skill hugeicons-implementation with dark: variants)
```

### Icon System Setup

```markdown
@IconsAgent @skill hugeicons-implementation

## Configure Icon System

**Icon Library:** @hugeicons/angular (NEVER use Material icons, Font Awesome, or manual SVG)

**Common Icons Needed:**
- Navigation: {list}
- Actions: {list}
- Status: {list}

**Generate (using this skill):**
1. Icon module/component setup (@skill hugeicons-implementation)
2. Icon registry pattern (@skill hugeicons-implementation)
3. Reusable icon wrapper component (@skill angular-components)
4. Size variants (sm=16px, md=20px, lg=24px, xl=32px) (@skill tailwind-4)
5. Color theming integration (@skill tailwind-4 + @skill hugeicons-implementation)
```

---

## 23. Animations Agent

### Component Animations

```markdown
@AnimationsAgent @skill animations-ux @skill tailwind-4

Add animations to {component}.

**Animation Requirements:**
- Enter animation: {type}
- Exit animation: {type}
- Interaction feedback: {type}

**Generate (using these skills):**
1. CSS transitions for simple effects (@skill tailwind-4)
2. @angular/animations for complex sequences (@skill animations-ux)
3. Reduced motion media query support (@skill animations-ux)
4. Performance-optimized (transform/opacity only) (@skill animations-ux)
5. Consistent timing with design system (@skill tailwind-4)
```

### Page Transitions

```markdown
@AnimationsAgent @skill animations-ux @skill angular-routing

## Implement Page Transitions

**Transition Type:** {fade/slide/scale}

**Requirements:**
- Duration: {ms}
- Easing: {ease-out/ease-in-out}
- Respect prefers-reduced-motion

**Generate (using these skills):**
1. Router animation configuration (@skill animations-ux, @skill angular-routing)
2. Animation trigger and states (@skill animations-ux)
3. Stagger animations for lists (@skill animations-ux)
4. Loading skeleton animations (@skill animations-ux)
5. Transition cleanup on destroy (@skill animations-ux)
```

---

## 24. Environments Agent

### Environment Configuration

```markdown
@EnvironmentsAgent @skill ngx-env-builder

Configure environments for {project}.

**Environments:**
- Development: localhost
- Staging: {staging_url}
- Production: {production_url}

**Variables Needed:**
| Variable | Dev | Staging | Prod |
|----------|-----|---------|------|
| API_URL | {val} | {val} | {val} |
| {var} | {val} | {val} | {val} |

**Generate (using this skill):**
1. .env file templates for each environment (@skill ngx-env-builder)
2. Environment validation at startup (@skill ngx-env-builder)
3. Type-safe environment access with env.d.ts (@skill ngx-env-builder, @skill typescript)
4. Build configuration (@skill ngx-env-builder)
5. Documentation for team
```

---

## 25. Mock Layer Agent

### Mock API Setup

```markdown
@MockLayerAgent @skill json-server-mocks

Set up mock API layer for {feature}.

**Endpoints to Mock:**
| Method | Endpoint | Response |
|--------|----------|----------|
| GET | {path} | {description} |
| POST | {path} | {description} |

**Generate (using this skill):**
1. db.json with seed data (@skill json-server-mocks, @skill faker-data-generation)
2. Custom routes configuration (@skill json-server-mocks)
3. Delay simulation for loading states (@skill json-server-mocks)
4. Error simulation for testing (@skill json-server-mocks)
5. npm scripts for mock server (@skill json-server-mocks)
```

### Mock Data Generation

```markdown
@MockLayerAgent @skill faker-data-generation

## Generate Mock Data

**Entity:** {entity_name}

**Schema:**
```typescript
interface {Entity} {
  {property}: {type};
}
```

**Generate (using this skill):**
1. Faker-based data generators (@skill faker-data-generation)
2. Realistic seed data (10-50 records) (@skill faker-data-generation)
3. Relationship handling (@skill faker-data-generation)
4. Edge case data (empty, long strings, etc.) (@skill faker-data-generation)
5. Date range variations (@skill faker-data-generation)
```

---

## 26. Frontend Quick Prompts

### One-Line Prompts

```markdown
# Components
@AngularAgent Generate standalone {Component} with signals, OnPush, typed inputs/outputs for {feature}.

# Styling
@TailwindAgent Style {component} with mobile-first responsive design and dark mode support.

# Icons
@IconsAgent Add {icon-name} icon from @hugeicons/angular with proper accessibility attributes.

# Animations
@AnimationsAgent Add {enter/exit/hover} animation to {component} using CSS transitions.

# Tests
@FrontendTestingAgent Generate Jest tests for {component} covering user interactions and edge cases.

# Accessibility
@UXAgent Audit {component} for WCAG 2.1 AA compliance and provide code fixes.

# State
@StateAgent Convert {component} state to signals with computed values for derived data.

# Performance
@FrontendPerformanceAgent Analyze {component} bundle impact and suggest lazy loading strategy.

# Security
@FrontendSecurityAgent Review {form/auth code} for XSS vulnerabilities and secure alternatives.

# Mock
@MockLayerAgent Generate json-server mock for {entity} CRUD endpoints with seed data.
```

### Combined Workflows

```markdown
## New Feature Development (Frontend)

@FrontendArchitectAgent + @AngularAgent + @TailwindAgent

Develop {feature_name} feature:
1. Design architecture and folder structure
2. Generate components with Angular 17+ patterns
3. Style with Tailwind CSS and dark mode

## Accessibility Enhancement

@UXAgent + @AngularAgent

Improve accessibility for {component}:
1. Audit for WCAG 2.1 compliance
2. Implement recommended fixes
3. Add proper ARIA attributes

## Component Polish

@TailwindAgent + @IconsAgent + @AnimationsAgent

Polish {component} UI:
1. Refine styling with Tailwind
2. Add appropriate icons
3. Implement smooth animations
```

---

**Note:** Replace all `{placeholders}` with actual values before using the prompts.
