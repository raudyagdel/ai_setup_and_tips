# Prompt Engineering Guide

> Best practices for using AI agents effectively in software development.

---

## 📚 Related Documents

| Document | Purpose |
|----------|---------|
| [PROMPT_TEMPLATES.md](PROMPT_TEMPLATES.md) | Ready-to-use prompt templates for all agents |
| [PROMPT_EXAMPLES.md](PROMPT_EXAMPLES.md) | Real-world examples and scenarios |
| [AGENTS_BACKEND_TEMPLATE.md](AGENTS_BACKEND_TEMPLATE.md) | Backend agent definitions and configurations |
| [AGENTS_FRONT_TEMPLATE.md](AGENTS_FRONT_TEMPLATE.md) | Frontend agent definitions and configurations |

---

## 🤖 Available Agents Quick Reference

### Backend Agents (Spring Boot / Java)

| Agent | Prefix | Primary Use |
|-------|--------|-------------|
| ArchitectAgent | `@ArchitectAgent` | System design, patterns, ADRs |
| CodeGenAgent | `@CodeGenAgent` | CRUD, services, controllers |
| TestingAgent | `@TestingAgent` | Unit, integration, e2e tests |
| SecurityAgent | `@SecurityAgent` | Security review, auth implementation |
| PerformanceAgent | `@PerformanceAgent` | Optimization, profiling |
| DatabaseAgent | `@DatabaseAgent` | Schema, migrations, queries |
| DevOpsAgent | `@DevOpsAgent` | CI/CD, containers, deployment |
| DocumentationAgent | `@DocumentationAgent` | API docs, READMEs |
| ReviewAgent | `@ReviewAgent` | Code review, best practices |
| DebuggingAgent | `@DebuggingAgent` | Bug diagnosis, troubleshooting |
| SoftwareAnalystAgent | `@SoftwareAnalystAgent` | Requirements, user stories, epics |

### Frontend Agents (Angular / TypeScript)

| Agent | Prefix | Primary Use |
|-------|--------|-------------|
| FrontendArchitectAgent | `@FrontendArchitectAgent` | Frontend architecture, feature modules |
| AngularAgent | `@AngularAgent` | Angular components, signals, services |
| TailwindAgent | `@TailwindAgent` | Tailwind CSS styling, design system |
| UXAgent | `@UXAgent` | Accessibility, WCAG, UX flows |
| StateAgent | `@StateAgent` | Signals, RxJS, state management |
| FrontendSecurityAgent | `@FrontendSecurityAgent` | XSS, CSRF, auth tokens |
| FrontendPerformanceAgent | `@FrontendPerformanceAgent` | Lazy loading, bundle optimization |
| FrontendTestingAgent | `@FrontendTestingAgent` | Jest, Playwright, component tests |
| FrontendDevOpsAgent | `@FrontendDevOpsAgent` | Angular builds, CI/CD |
| FrontendDocumentationAgent | `@FrontendDocumentationAgent` | Component docs, Storybook |
| IconsAgent | `@IconsAgent` | @hugeicons/angular, icon management |
| AnimationsAgent | `@AnimationsAgent` | @angular/animations, transitions |
| EnvironmentsAgent | `@EnvironmentsAgent` | @ngx-env/builder, env config |
| MockLayerAgent | `@MockLayerAgent` | json-server, mock APIs |

---

## 🆕 For Starting a New Project

### 🔹 Phase 1 – Analysis & Requirements

**Agent:** `@SoftwareAnalystAgent`

```markdown
@SoftwareAnalystAgent

Analyze and document requirements for [PROJECT_NAME]:
- Business context: [describe]
- Target users: [list]
- Key functionalities: [list]

Generate:
1. Epic breakdown
2. User stories
3. GitHub-ready feature issues
```

---

### 🔹 Phase 2 – Architecture & Design

**Agent:** `@ArchitectAgent`

```markdown
@ArchitectAgent

Act **strictly** following the rules defined in:
* `.copilot/copilot-instructions.md`
* `AGENTS.md`

Design architecture for [PROJECT_NAME] with:
* [REQUIREMENT_1]
* [REQUIREMENT_2]

Provide:
1. C4 diagrams (Context, Container, Component)
2. Technology decisions with rationale
3. ADR for key decisions
```

**Rules**:
* Do **not** invent new layers, modules, or technologies that are not explicitly defined.
* Do **not** change existing functionality.
* Respect the boundaries of each module.
* Clearly explain every proposed change.
* If something cannot be done without breaking the rules, **stop and explain why**.

---

### 🔹 Phase 3 – Database Design

**Agent:** `@DatabaseAgent`

```markdown
@DatabaseAgent

Design database schema based on domain model in docs/domain-model/.
Include:
1. DDL scripts
2. Flyway migrations
3. JPA entities
4. Indexing strategy
```

---

### 🔹 Phase 4 – Project Generation

**Agent:** `@CodeGenAgent`

Generate the project **module by module**, starting with the **core module**.

```markdown
@CodeGenAgent

Generate [ENTITY_NAME] module with:
- Entity with JPA annotations
- Repository with custom queries
- Service interface and implementation
- REST Controller with validation
- DTOs (Request/Response)
- Mappers (MapStruct)
```

---

### 🔹 Phase 5 – Security Implementation

**Agent:** `@SecurityAgent`

```markdown
@SecurityAgent

Implement authentication for [PROJECT_NAME]:
- JWT with refresh tokens
- Role-based access (ADMIN, USER)
- Password policy enforcement
```

---

### 🔹 Phase 6 – Testing

**Agent:** `@TestingAgent`

```markdown
@TestingAgent

Generate test suite for [MODULE_NAME]:
- Unit tests with JUnit 5
- Integration tests with TestContainers
- BDD-style naming (given-when-then)
```

---

### 🔹 Phase 7 – Documentation

**Agent:** `@DocumentationAgent`

```markdown
@DocumentationAgent

Generate API documentation:
- OpenAPI 3.0 specification
- README.md with setup instructions
- Architecture decision records
```

---

### 🔹 Phase 8 – DevOps Setup

**Agent:** `@DevOpsAgent`

```markdown
@DevOpsAgent

Create deployment configuration:
- Dockerfile (multi-stage)
- docker-compose.yml
- GitHub Actions CI/CD
- Kubernetes manifests (if applicable)
```

---

## ♻️ For Refactoring an Existing Project

### 🔹 Phase 1 – Analysis (No Code Changes)

**Agents:** `@ReviewAgent` + `@PerformanceAgent`

```markdown
@ReviewAgent

Analyze the current project and explain:
* Which parts comply with the instructions
* Which parts violate them
* Which modules should exist according to `AGENTS.md`

⚠️ **Do not generate code yet**.
```

---

### 🔹 Phase 2 – Refactor Plan

**Agent:** `@ArchitectAgent`

Propose a refactor plan composed of **small, ordered steps**.

Each step must be:
* **Atomic**
* **Reversible**
* Suitable for an **independent commit**

---

### 🔹 Phase 3 – Commit-Guided Refactor

**Agent:** `@CodeGenAgent`

For each step:
* Execute **only one step** of the plan
* Generate **only**:
  * Modified files
  * New files (if applicable)
* Do **not** touch anything else

✔️ This approach is ideal for quality control and clean pull requests.

---

## 🐛 For Debugging Issues

### 🔹 Phase 1 – Diagnosis

**Agent:** `@DebuggingAgent`

```markdown
@DebuggingAgent

Debug issue: [DESCRIPTION]

Error message: [ERROR]
Stack trace: [TRACE]
Context: [WHAT_WAS_HAPPENING]

Provide root cause analysis and solution.
```

---

### 🔹 Phase 2 – Fix & Test

**Agents:** `@CodeGenAgent` + `@TestingAgent`

```markdown
@CodeGenAgent
Implement the fix for [ISSUE_ID].

@TestingAgent
Generate regression tests to prevent recurrence.
```

---

## 🔒 For Security Audits

**Agent:** `@SecurityAgent`

```markdown
@SecurityAgent

Perform security audit on [MODULE/FILE]:
- Check for OWASP Top 10 vulnerabilities
- Review authentication/authorization
- Identify data exposure risks

Provide severity ratings and fixes.
```

---

## 📈 For Performance Optimization

**Agent:** `@PerformanceAgent`

```markdown
@PerformanceAgent

Analyze performance of [ENDPOINT/SERVICE]:

Metrics:
- Response time: [VALUE]
- Database queries: [COUNT]
- Memory usage: [VALUE]

Identify bottlenecks and provide optimizations.
```

---

## 💡 Prompting Best Practices

### ✅ Be Specific and Contextual

Good:
```markdown
@CodeGenAgent Generate a ProductService with methods for CRUD operations, 
inventory management, and price calculations. Use Spring Boot 3.4+ patterns.
```

Bad:
```markdown
Generate a service for products.
```

---

### ✅ Use Agent Prefixes

Always start prompts with the agent prefix:
- `@ArchitectAgent` for design decisions
- `@CodeGenAgent` for implementation
- `@TestingAgent` for tests
- etc.

---

### ✅ Provide Context

Include relevant information:
- Technology stack
- Existing code patterns
- Constraints and requirements
- Expected output format

---

### ✅ Be Repetitive When Needed

Copilot does not mind repetition. Frequently remind it:

> "Follow strictly `copilot-instructions.md` and `AGENTS.md`."

---

### ✅ Force It to Stop When Needed

Include explicit instructions such as:

> "If there is any ambiguity, ask before continuing."

---

### ✅ Chain Agents for Complex Tasks

```markdown
## Feature: Shopping Cart

### Step 1: Analysis
@SoftwareAnalystAgent - Create user stories

### Step 2: Architecture  
@ArchitectAgent - Design the solution

### Step 3: Implementation
@CodeGenAgent - Generate the code

### Step 4: Testing
@TestingAgent - Create test suite

### Step 5: Review
@ReviewAgent - Final review
```

---

### ❌ Do Not Mix Tasks

Avoid asking Copilot to do multiple things at once.

❌ Do **not** combine:
* Refactoring
* Testing
* Migration

in a single request.

---

### ❌ Don't Skip Context

❌ Bad:
```markdown
Fix the bug in the payment service.
```

✅ Good:
```markdown
@DebuggingAgent

Bug: Payment fails for orders > $1000

Error: PaymentException at PaymentService.java:45
Stack trace: [paste trace]
Recent changes: Added new tax calculation

Please diagnose and provide fix.
```

---

## 🔄 Common Workflows

### New Feature Development

```
@SoftwareAnalystAgent → @ArchitectAgent → @DatabaseAgent → @CodeGenAgent → @TestingAgent → @DocumentationAgent
```

### Bug Fix

```
@DebuggingAgent → @CodeGenAgent → @TestingAgent → @ReviewAgent
```

### Performance Issue

```
@PerformanceAgent → @DatabaseAgent → @CodeGenAgent → @TestingAgent
```

### Security Audit

```
@SecurityAgent → @CodeGenAgent → @TestingAgent → @ReviewAgent
```

### Documentation Sprint

```
@SoftwareAnalystAgent → @DocumentationAgent
```

---

## 📋 Quick Prompt Templates

### For Entities
```markdown
@CodeGenAgent Generate [Entity] with fields: [list]. Include Repository, Service, Controller, DTOs.
```

### For Tests
```markdown
@TestingAgent Generate tests for [Class] covering: happy path, edge cases, error scenarios.
```

### For Reviews
```markdown
@ReviewAgent Review [file/module] for SOLID principles, patterns, and Spring best practices.
```

### For Analysis
```markdown
@SoftwareAnalystAgent Analyze [feature] and create user stories with acceptance criteria in Gherkin.
```

---

## 📖 Additional Resources

- **Templates:** [PROMPT_TEMPLATES.md](PROMPT_TEMPLATES.md) - Complete templates for all agents
- **Examples:** [PROMPT_EXAMPLES.md](PROMPT_EXAMPLES.md) - Real-world scenarios
- **Backend Agents:** [AGENTS_BACKEND_TEMPLATE.md](AGENTS_BACKEND_TEMPLATE.md) - Full backend agent specifications
- **Frontend Agents:** [AGENTS_FRONT_TEMPLATE.md](AGENTS_FRONT_TEMPLATE.md) - Full frontend agent specifications

---

## 🎨 For Frontend Development (Angular)

### 🔹 Phase 1 – Frontend Architecture

**Agent:** `@FrontendArchitectAgent`

```markdown
@FrontendArchitectAgent

Design frontend architecture for [FEATURE_NAME]:
- Feature modules structure
- Routing strategy
- Shared vs feature components
- State management approach

Provide folder structure and architectural decisions.
```

---

### 🔹 Phase 2 – Component Development

**Agent:** `@AngularAgent`

```markdown
@AngularAgent

Generate Angular standalone component for [COMPONENT_NAME]:
- Use signals for local state
- OnPush change detection
- Typed inputs and outputs
- Follow Angular 17+ best practices
```

---

### 🔹 Phase 3 – Styling

**Agent:** `@TailwindAgent`

```markdown
@TailwindAgent

Style [COMPONENT_NAME] using Tailwind CSS:
- Mobile-first responsive design
- Dark mode support
- Consistent with design system
- Accessible color contrast
```

---

### 🔹 Phase 4 – Accessibility

**Agent:** `@UXAgent`

```markdown
@UXAgent

Review [COMPONENT/PAGE] for accessibility:
- WCAG 2.1 AA compliance
- Keyboard navigation
- Screen reader support
- Focus management
```

---

### 🔹 Phase 5 – Icons & Animations

**Agents:** `@IconsAgent` + `@AnimationsAgent`

```markdown
@IconsAgent
Implement icons for [COMPONENT] using @hugeicons/angular.
Include proper accessibility attributes and dark mode support.

@AnimationsAgent
Add enter/exit animations for [COMPONENT].
Use CSS transitions for simple effects, @angular/animations for complex.
```

---

### 🔹 Phase 6 – Testing

**Agent:** `@FrontendTestingAgent`

```markdown
@FrontendTestingAgent

Generate tests for [COMPONENT]:
- Unit tests with Jest
- Component tests with Testing Library
- E2E tests with Playwright for critical flows
```

---

## 🔄 Common Frontend Workflows

### New Feature Development (Frontend)

```
@FrontendArchitectAgent → @AngularAgent → @TailwindAgent → @UXAgent → @FrontendTestingAgent → @FrontendDocumentationAgent
```

### Component Library Development

```
@FrontendArchitectAgent → @AngularAgent → @TailwindAgent → @IconsAgent → @AnimationsAgent → @FrontendTestingAgent
```

### Performance Optimization (Frontend)

```
@FrontendPerformanceAgent → @AngularAgent → @FrontendTestingAgent → @ReviewAgent
```

### Accessibility Audit

```
@UXAgent → @AngularAgent → @FrontendTestingAgent
```

### Mock API Setup

```
@MockLayerAgent → @EnvironmentsAgent → @FrontendTestingAgent
```

---

## 📋 Quick Frontend Prompt Templates

### For Components
```markdown
@AngularAgent Generate standalone [Component] with signals, OnPush, typed inputs/outputs.
```

### For Styling
```markdown
@TailwindAgent Style [component] with responsive design, dark mode, and accessibility.
```

### For Icons
```markdown
@IconsAgent Add [icon-name] icon using @hugeicons/angular with proper sizing and theming.
```

### For State
```markdown
@StateAgent Design state management for [feature] using signals and computed values.
```

### For Tests
```markdown
@FrontendTestingAgent Generate unit tests for [component] covering user interactions and edge cases.
```

### For Accessibility
```markdown
@UXAgent Audit [component/page] for WCAG 2.1 AA compliance and provide fixes.
```

---

This workflow is intended to help teams avoid architectural drift and safely evolve Spring Boot projects using AI-assisted development.


