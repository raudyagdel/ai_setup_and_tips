# Agents & Skills Registry

**Central Registry of Expert Agents and Skill Mappings**

**Version:** 1.0  
**Last Updated:** 2026-02-06  
**Purpose:** Complete inventory of all available Expert Agents and their underlying skills

---

## Quick Lookup

Use this table to quickly find the right agent for your task:

| Agent | Role | Primary Domain | Key Workflows |
|-------|------|---|---|
| **FrontendArchitectAgent** | Frontend Architecture & Design | Architecture Planning | new_feature_development, code_refactoring |
| **AngularAgent** | Angular Framework Specialist | Component Implementation | new_feature_development, bug_fixing |
| **TailwindAgent** | Tailwind CSS & Styling | UI Styling & Theming | new_feature_development, design_system_update |
| **UXAgent** | UI/UX & Accessibility | UX Design & WCAG | accessibility_audit, design_system_update |
| **StateAgent** | Frontend State Management | State Architecture | new_feature_development, code_refactoring |
| **FrontendSecurityAgent** | Frontend Security | Security Auditing | vulnerability_detection, code_review |
| **FrontendPerformanceAgent** | Frontend Performance | Performance Optimization | performance_optimization, code_review |
| **FrontendTestingAgent** | Testing & QA | Test Strategy | (all workflows) |
| **FrontendDevOpsAgent** | Build, CI/CD & Deployment | DevOps & Infrastructure | environment_configuration |
| **FrontendDocumentationAgent** | Documentation & DX | Developer Documentation | (all workflows) |
| **IconsAgent** | Icon Management | @hugeicons/angular | ui_polish, design_system_update |
| **AnimationsAgent** | UI Animations & Motion | Animation Patterns | ui_polish, new_feature_development |
| **EnvironmentsAgent** | Environment Configuration | .env & Config Management | environment_configuration |
| **MockLayerAgent** | Mock Data & API Simulation | Mock APIs | mock_layer_setup |
| **ReviewAgent** | Code Review & QA | Code Quality | code_review |

---

## Agent Details

### 1. FrontendArchitectAgent

**Role:** Frontend Architecture & Design

**Description:** Defines scalable frontend architecture using modern Angular best practices. Expertise in feature-based modular architecture, lazy loading strategies, and domain-driven boundaries.

**Primary Expertise:** Frontend Architecture & Patterns

**Capabilities:**
- "Design feature-based modular architecture"
- "Plan lazy loading and code splitting strategies"
- "Establish domain-driven UI boundaries"
- "Create routing and guard strategies"
- "Design component responsibility patterns"

**Primary Skills:**
- `angular-architecture` - Architecture patterns for Angular
- `clean-ddd-hexagonal` - DDD and hexagonal patterns
- `interface-design` - UI component design

**Focus Areas:**
- Feature-based folder structure
- Routing strategies
- State ownership and boundaries
- Lazy loading optimization

**Used in Workflows:**
- new_feature_development
- code_refactoring
- migration
- code_review

**Usage Template:**
```
@FrontendArchitectAgent
{Describe your application scope}

Task: Design architecture for {feature or module}

Requirements:
- {Requirement 1}
- {Requirement 2}
- {Requirement 3}

Constraints:
- {Any architectural constraints}
```

---

### 2. AngularAgent

**Role:** Angular Framework Specialist

**Description:** Implements Angular code using the latest framework features (v21+). Expert in standalone components, signals, reactive patterns, and Angular best practices.

**Primary Expertise:** Angular Framework Implementation

**Capabilities:**
- "Create standalone components with signals-based state"
- "Implement Angular routing with guards and resolvers"
- "Build typed reactive forms"
- "Set up dependency injection patterns"
- "Implement RxJS/Observable patterns"

**Primary Skills:**
- `angular-best-practices` - Angular 21+ best practices
- `angular-component` - Component architecture
- `angular-forms` - Form implementation
- `angular-http` - HTTP & data fetching
- `angular-routing` - Routing patterns
- `angular-signals` - Signals-based state
- `typescript` - TypeScript patterns

**Focus Areas:**
- Standalone components
- Signal-based state management
- Typed reactive forms
- OnPush change detection
- Strong typing patterns

**Used in Workflows:**
- new_feature_development
- bug_fixing
- code_refactoring
- migration
- code_review

**Usage Template:**
```
@AngularAgent
{What component/service are you building?}

Task: Implement {specific Angular artifact}

Requirements:
- {Framework requirement}
- {Pattern requirement}
- {State requirement}

Constraints:
- {Technical constraints}
```

---

### 3. TailwindAgent

**Role:** Tailwind CSS & Styling Specialist

**Description:** Ensures consistent, scalable styling using Tailwind CSS v4. Expert in utility-first styling, design tokens, responsive layouts, and dark mode implementations.

**Primary Expertise:** Tailwind CSS Styling & Design Systems

**Capabilities:**
- "Design responsive layouts with mobile-first approach"
- "Implement dark mode theming"
- "Create consistent design token system"
- "Apply utility-first styling patterns"
- "Build accessible component variations"

**Primary Skills:**
- `tailwind-4` - Tailwind CSS v4 fundamentals
- `tailwind-css-patterns` - Common patterns
- `tailwind-design-system` - Design system patterns
- `tailwind4-expert` - Advanced Tailwind features
- `tailwindcss-advanced-layouts` - Complex layouts
- `tailwindcss-animations` - Animation utilities
- `tailwindcss-fundamentals-v4` - CSS-first architecture
- `tailwindcss-mobile-first` - Mobile-first responsive

**Focus Areas:**
- Utility-first styling
- Design tokens and consistency
- Responsive design patterns
- Dark mode support
- Animation utilities

**Used in Workflows:**
- new_feature_development
- design_system_update
- code_review
- ui_polish

**Usage Template:**
```
@TailwindAgent
{Describe what you're styling}

Task: Style {component/page}

Requirements:
- Responsive: {mobile/tablet/desktop}
- Dark mode: {yes/no}
- Accessibility: {WCAG level}
- Design tokens: {reference}

Constraints:
- {Design constraints}
```

---

### 4. UXAgent

**Role:** UI/UX & Accessibility

**Description:** Ensures excellent user experience and WCAG 2.1 accessibility compliance. Expert in UX flows, keyboard navigation, screen reader support, and inclusive design.

**Primary Expertise:** UX Design & Accessibility

**Capabilities:**
- "Design accessible, keyboard-navigable interfaces"
- "Audit WCAG 2.1 AA compliance issues"
- "Implement focus management and ARIA labels"
- "Design mobile-first responsive experiences"
- "Create inclusive color and contrast schemes"

**Primary Skills:**
- `interface-design` - Interface design principles
- `tailwind-css-patterns` - Accessible styling
- `tailwind-design-system` - Design system consistency

**Focus Areas:**
- Semantic HTML structure
- ARIA attributes and roles
- Keyboard navigation
- Color contrast compliance
- Focus management
- Screen reader support

**Used in Workflows:**
- accessibility_audit
- design_system_update
- new_feature_development
- ui_polish
- code_review

**Usage Template:**
```
@UXAgent
{Describe your UI/interface}

Task: Audit accessibility or design UX flow

Requirements:
- WCAG compliance: {targeted level}
- Keyboard navigation: {yes/no}
- Screen reader: {yes/no}
- Mobile optimization: {yes/no}

Constraints:
- {UX constraints}
```

---

### 5. StateAgent

**Role:** Frontend State Management

**Description:** Designs and reviews state handling strategies. Expert in signal-based local state, RxJS streams, and deciding between global vs local state patterns.

**Primary Expertise:** State Management Architecture

**Capabilities:**
- "Design signal-based local state patterns"
- "Implement RxJS observable streams"
- "Make global vs local state decisions"
- "Optimize computed signals and dependencies"
- "Review state ownership and mutation patterns"

**Primary Skills:**
- `angular-signals` - Signal-based state
- `angular-http` - Async data patterns
- `angular-best-practices` - State best practices

**Focus Areas:**
- Signals and computed state
- RxJS observables
- State ownership
- Immutable patterns
- Side effect management

**Used in Workflows:**
- new_feature_development
- code_refactoring
- performance_optimization
- code_review

**Usage Template:**
```
@StateAgent
{Describe your feature/component}

Task: Design state management for {feature}

Requirements:
- State type: {local/global/hybrid}
- Data flow: {simple/complex}
- Real-time updates: {yes/no}

Constraints:
- {Performance requirements}
```

---

### 6. FrontendSecurityAgent

**Role:** Frontend Security

**Description:** Audits frontend code for security vulnerabilities. Expert in OWASP Frontend Top 10, authentication patterns, authorized routes, and secure data handling.

**Primary Expertise:** Frontend Security & Vulnerability Prevention

**Capabilities:**
- "Audit authentication and authorization flows"
- "Identify XSS, CSRF, and injection vulnerabilities"
- "Review secure token storage patterns"
- "Validate route guard implementations"
- "Audit third-party dependency vulnerabilities"

**Primary Skills:**
- `angular-best-practices` - Secure patterns
- `angular-routing` - Guard-based security

**Focus Areas:**
- OWASP Frontend Top 10
- Authentication flows
- Authorization (RBAC)
- Secure storage
- Token management
- Third-party auditing

**Used in Workflows:**
- vulnerability_detection
- code_review
- dependency_update
- new_feature_development

**Usage Template:**
```
@FrontendSecurityAgent
{Describe the code/flow to audit}

Task: Perform security audit

Focus areas:
- {Security concern 1}
- {Security concern 2}
- {Security concern 3}

Technology stack:
- {Framework/library details}
```

---

### 7. FrontendPerformanceAgent

**Role:** Frontend Performance Optimization

**Description:** Optimizes runtime and build-time performance. Expert in lazy loading, bundle optimization, change detection tuning, and Web Vitals.

**Primary Expertise:** Performance Optimization

**Capabilities:**
- "Identify performance bottlenecks"
- "Optimize lazy loading strategies"
- "Reduce bundle size and improve load times"
- "Tune change detection for OnPush"
- "Optimize images and assets"

**Primary Skills:**
- `angular-best-practices` - Performance patterns
- `angular-routing` - Lazy loading strategies

**Focus Areas:**
- Lazy loading strategies
- Bundle size optimization
- Change detection tuning
- Web Vitals metrics
- Image optimization
- Runtime performance profiling

**Used in Workflows:**
- performance_optimization
- code_review
- dependency_update
- new_feature_development

**Usage Template:**
```
@FrontendPerformanceAgent
{Describe your application}

Task: Performance audit and optimization

Current Metrics:
- Bundle size: {size}
- FCP: {time}
- LCP: {time}
- TTI: {time}

Target Goals:
- Bundle: {target size}
- FCP: {target time}
- Performance score: {target}
```

---

### 8. FrontendTestingAgent

**Role:** Testing & Quality Assurance

**Description:** Creates and enforces frontend testing strategy. Expert in unit tests, integration tests, E2E tests, and accessibility testing with Jest, Angular Testing Library, and Playwright.

**Primary Expertise:** Frontend Testing Strategy

**Capabilities:**
- "Generate unit tests for components and services"
- "Create integration tests for features"
- "Build E2E tests for critical flows"
- "Add accessibility tests (WCAG compliance)"
- "Design mock API scenarios"

**Primary Skills:**
- `angular-component` - Component testing
- `typescript` - Test patterns

**Focus Areas:**
- Unit testing (Jest)
- Integration testing
- E2E testing (Playwright)
- Mock API testing
- Accessibility testing
- Coverage goals (80%+)

**Used in Workflows:**
- new_feature_development
- bug_fixing
- code_refactoring
- vulnerability_detection
- accessibility_audit
- code_review

**Usage Template:**
```
@FrontendTestingAgent
{Describe what to test}

Task: Create tests for {component/service}

Test Types:
- Unit tests: {yes/no}
- Integration tests: {yes/no}
- E2E tests: {yes/no}
- Accessibility: {yes/no}

Coverage Target: {%}
```

---

### 9. FrontendDevOpsAgent

**Role:** Build, CI/CD & Deployment

**Description:** Manages frontend build and deployment pipelines. Expert in Angular production builds, environment configuration, and CI/CD automation on GitHub Actions, Vercel, Netlify.

**Primary Expertise:** Build & Deployment Automation

**Capabilities:**
- "Create optimized production builds"
- "Set up multi-environment configurations"
- "Design CI/CD pipelines"
- "Automate testing and deployment"
- "Configure static hosting deployment"

**Primary Skills:**
- `angular-best-practices` - Build optimization

**Focus Areas:**
- Production build optimization
- Environment configuration
- CI/CD pipeline design
- GitHub Actions/other platforms
- Static hosting setup
- Deployment automation

**Used in Workflows:**
- environment_configuration
- dependency_update
- migration

**Usage Template:**
```
@FrontendDevOpsAgent
{Describe your deployment needs}

Task: Set up CI/CD pipeline

Environments:
- {environment 1}
- {environment 2}
- {environment 3}

Requirements:
- {Requirement 1}
- {Requirement 2}

Deployment target: {hosting platform}
```

---

### 10. FrontendDocumentationAgent

**Role:** Documentation & Developer Experience

**Description:** Maintains frontend documentation and standards. Expert in README generation, component usage docs, architecture decisions, and developer guidance.

**Primary Expertise:** Documentation & Developer Experience

**Capabilities:**
- "Generate comprehensive READMEs"
- "Create component usage documentation"
- "Write Storybook component stories"
- "Document Architecture Decision Records (ADR)"
- "Create developer onboarding guides"

**Primary Skills:**
- `interface-design` - Component documentation

**Focus Areas:**
- README and setup guides
- Component API documentation
- Architecture documentation
- Getting started guides
- Troubleshooting docs
- Best practices guides

**Used in Workflows:**
- new_feature_development
- code_refactoring
- migration
- design_system_update
- environment_configuration

**Usage Template:**
```
@FrontendDocumentationAgent
{Describe what to document}

Task: Create documentation for {component/feature}

Documentation Type:
- {Type 1}
- {Type 2}

Audience:
- {Audience description}

Details:
- {Include this in docs}
```

---

### 11. IconsAgent

**Role:** Icon Management & Implementation

**Description:** Manages icon usage across the application using @hugeicons/angular. Expert in icon selection, theme-aware styling, accessibility, and dark mode support.

**Primary Expertise:** @hugeicons/angular Implementation

**Capabilities:**
- "Implement @hugeicons/angular icons with proper sizing"
- "Apply theme-aware icon colors using Tailwind"
- "Ensure dark mode compatibility with dark: variants"
- "Add accessibility attributes (aria-label) to icons"
- "Create icon usage guidelines and standards"

**Primary Skills:**
- `angular-component` - Icon component integration
- `tailwind-css-patterns` - Color and styling
- `interface-design` - Icon design patterns

**Focus Areas:**
- @hugeicons/angular library
- Icon sizing standards (sm/md/lg/xl)
- Tailwind color utilities
- Dark mode support
- Accessibility attributes
- Icon naming conventions

**Used in Workflows:**
- ui_polish
- design_system_update
- new_feature_development
- code_review

**Usage Template:**
```
@IconsAgent
{Describe where you need icons}

Task: Implement icons for {component/section}

Icon Requirements:
- Icon names: {list}
- Sizes: {sizes needed}
- Colors: {color scheme}
- Dark mode: {yes/no}

Accessibility: {aria-label requirements}
```

---

### 12. AnimationsAgent

**Role:** UI Animations & Motion Design

**Description:** Implements smooth, performant animations using @angular/animations and tailwindcss-animate. Expert in enter/exit animations, state transitions, micro-interactions, and accessibility compliance.

**Primary Expertise:** Animation Patterns & Motion Design

**Capabilities:**
- "Implement enter/exit animations with @angular/animations"
- "Create state-based transition animations"
- "Build micro-interactions (< 300ms)"
- "Respect accessibility preferences (prefers-reduced-motion)"
- "Optimize animations for performance (transform/opacity only)"

**Primary Skills:**
- `angular-component` - Animation directives
- `tailwindcss-animations` - CSS animation utilities
- `tailwind-css-patterns` - Styling animations
- `interface-design` - Motion design UX

**Focus Areas:**
- Enter/exit animations
- State transitions
- Micro-interactions
- Motion accessibility
- Performance optimization
- Animation timing and easing

**Used in Workflows:**
- ui_polish
- new_feature_development
- design_system_update
- code_review

**Usage Template:**
```
@AnimationsAgent
{Describe what you're animating}

Task: Add animations to {component}

Animation Types:
- Enter/exit: {yes/no}
- State transitions: {yes/no}
- Micro-interactions: {yes/no}

Requirements:
- Duration: {timing}
- Easing: {easing function}
- Accessibility: {prefers-reduced-motion support}
```

---

### 13. EnvironmentsAgent

**Role:** Environment Configuration & Management

**Description:** Manages environment-specific configurations using .env files with @ngx-env/builder. Expert in multi-environment setup, secure secrets handling, and type-safe access.

**Primary Expertise:** Environment & Configuration Management

**Capabilities:**
- "Set up multi-environment configurations (.env files)"
- "Configure @ngx-env/builder with type safety"
- "Manage secrets securely (never commit)"
- "Validate required environment variables"
- "Create environment-specific configurations"

**Primary Skills:**
- `angular-best-practices` - Environment patterns

**Focus Areas:**
- .env file structure and variables
- @ngx-env/builder configuration
- Type-safe env.d.ts declarations
- Multi-environment setup
- Secrets management
- CI/CD environment handling

**Used in Workflows:**
- environment_configuration
- new_feature_development
- dependency_update

**Usage Template:**
```
@EnvironmentsAgent
{Describe your application needs}

Task: Configure environments

Environments Needed:
- {env 1}
- {env 2}
- {env 3}

Variables Required:
- {VAR_NAME}: {description}
- {VAR_NAME}: {description}

Constraints:
- {Security/config constraints}
```

---

### 14. MockLayerAgent

**Role:** Mock Data & API Simulation

**Description:** Provides mock data layer for frontend development when backend is not ready. Expert in json-server setup, realistic data generation with Faker.js, and API contract documentation.

**Primary Expertise:** Mock APIs & Test Data

**Capabilities:**
- "Set up json-server with mock database"
- "Generate realistic fake data with Faker.js"
- "Create API delay simulation (200-500ms)"
- "Design error scenarios for testing"
- "Document API contracts in mock files"

**Primary Skills:**
- `angular-http` - API contract patterns

**Focus Areas:**
- json-server configuration
- Mock database structure
- Faker.js data generation
- API endpoint simulation
- Error scenario setup
- API contract documentation

**Used in Workflows:**
- mock_layer_setup
- new_feature_development
- environment_configuration

**Usage Template:**
```
@MockLayerAgent
{Describe your API needs}

Task: Set up mock layer for {feature}

API Endpoints:
- {endpoint 1}
- {endpoint 2}
- {endpoint 3}

Data Requirements:
- {Data 1}: {count}
- {Data 2}: {count}

Special Scenarios:
- {Scenario 1}
- {Error handling}
```

---

### 15. ReviewAgent

**Role:** Code Review & Quality Assurance

**Description:** Performs comprehensive code reviews ensuring quality, standards compliance, and best practices adherence. Expert in identifying code smells, technical debt, and improvement opportunities.

**Primary Expertise:** Code Quality & Review

**Capabilities:**
- "Review code for best practices and standards"
- "Identify technical debt and refactoring opportunities"
- "Check for SOLID principles violations"
- "Validate naming conventions and patterns"
- "Assess complexity and maintainability"

**Primary Skills:**
- `angular-best-practices` - Angular standards
- `typescript` - TypeScript patterns
- `interface-design` - Design review

**Focus Areas:**
- Code quality metrics
- Best practices compliance
- SOLID principles
- Naming conventions
- Complexity analysis
- Technical debt identification

**Used in Workflows:**
- code_review
- new_feature_development
- bug_fixing
- code_refactoring

**Usage Template:**
```
@ReviewAgent
{Provide code or description}

Task: Review code for quality

Focus Areas:
- {Area 1}
- {Area 2}
- {Area 3}

Standards to Check:
- {Standard 1}
- {Standard 2}

Severity Level: {High/Medium/Low}
```

---

## Skill-to-Agent Mapping

This matrix shows which skills power which agents:

| Skill | Agents Using It |
|---|---|
| `angular-architecture` | FrontendArchitectAgent |
| `angular-best-practices` | AngularAgent, FrontendSecurityAgent, FrontendPerformanceAgent, ReviewAgent |
| `angular-component` | AngularAgent, IconsAgent, AnimationsAgent, FrontendTestingAgent |
| `angular-development` | AngularAgent |
| `angular-directives` | AngularAgent |
| `angular-forms` | AngularAgent |
| `angular-http` | AngularAgent, StateAgent, MockLayerAgent |
| `angular-routing` | AngularAgent, FrontendSecurityAgent, FrontendPerformanceAgent |
| `angular-signals` | AngularAgent, StateAgent |
| `clean-ddd-hexagonal` | FrontendArchitectAgent |
| `interface-design` | FrontendArchitectAgent, UXAgent, IconsAgent, AnimationsAgent, FrontendDocumentationAgent, ReviewAgent |
| `tailwind-4` | TailwindAgent |
| `tailwind-css-patterns` | TailwindAgent, UXAgent, IconsAgent, AnimationsAgent |
| `tailwind-design-system` | TailwindAgent, UXAgent |
| `tailwind4-expert` | TailwindAgent |
| `tailwindcss-advanced-layouts` | TailwindAgent |
| `tailwindcss-animations` | TailwindAgent, AnimationsAgent |
| `tailwindcss-fundamentals-v4` | TailwindAgent |
| `tailwindcss-mobile-first` | TailwindAgent |
| `typescript` | AngularAgent, ReviewAgent, FrontendTestingAgent |

---

## Workflow-to-Agent Mapping

This shows which agents participate in each workflow:

### new_feature_development
- FrontendArchitectAgent (Design)
- AngularAgent (Implement)
- TailwindAgent (Style)
- StateAgent (State)
- FrontendSecurityAgent (Security)
- FrontendTestingAgent (Tests)
- FrontendPerformanceAgent (Performance)
- FrontendDocumentationAgent (Docs)

### bug_fixing
- AngularAgent (Fix)
- FrontendTestingAgent (Tests)
- ReviewAgent (Review)
- FrontendPerformanceAgent (Performance check)

### performance_optimization
- FrontendPerformanceAgent (Analyze)
- AngularAgent (Optimize)
- TailwindAgent (CSS optimization)
- FrontendTestingAgent (Validate)

### code_refactoring
- FrontendArchitectAgent (Plan)
- AngularAgent (Execute)
- StateAgent (State patterns)
- TailwindAgent (Styling cleanup)
- FrontendTestingAgent (Tests)
- ReviewAgent (Quality gate)

### vulnerability_detection
- FrontendSecurityAgent (Scan)
- AngularAgent (Fix)
- FrontendTestingAgent (Tests)
- ReviewAgent (Validate)
- FrontendDocumentationAgent (Document)

### accessibility_audit
- UXAgent (Audit)
- AngularAgent (Implement)
- TailwindAgent (Styling)
- FrontendTestingAgent (Tests)
- FrontendDocumentationAgent (Guide)

### dependency_update
- FrontendSecurityAgent (Security scan)
- AngularAgent (Update)
- TailwindAgent (Config update)
- FrontendTestingAgent (Regression tests)
- FrontendPerformanceAgent (Benchmark)
- FrontendDevOpsAgent (CI/CD)

### design_system_update
- UXAgent (Review)
- TailwindAgent (Tokens)
- IconsAgent (Icons)
- AnimationsAgent (Animations)
- AngularAgent (Components)
- FrontendTestingAgent (Visual regression)
- FrontendDocumentationAgent (Docs)

### mock_layer_setup
- MockLayerAgent (Setup)
- EnvironmentsAgent (Config)
- FrontendDocumentationAgent (Docs)

### environment_configuration
- EnvironmentsAgent (Setup)
- FrontendSecurityAgent (Security)
- FrontendDevOpsAgent (CI/CD)

### ui_polish
- AnimationsAgent (Animations)
- IconsAgent (Icons)
- TailwindAgent (Styling)
- UXAgent (UX validation)
- FrontendPerformanceAgent (Performance)

### code_review
- FrontendArchitectAgent (Architecture)
- AngularAgent (Angular)
- FrontendSecurityAgent (Security)
- FrontendPerformanceAgent (Performance)
- UXAgent (Accessibility)
- ReviewAgent (Quality)

### migration
- FrontendArchitectAgent (Plan)
- AngularAgent (Execute)
- StateAgent (State)
- TailwindAgent (Styling)
- FrontendTestingAgent (Tests)
- FrontendPerformanceAgent (Benchmark)
- FrontendDocumentationAgent (Guide)

---

## How to Use This Registry

### 1. **Find Agent by Task**

"I need to audit accessibility" → Look for **UXAgent**

"I need to implement a feature" → Look for **AngularAgent** (with **FrontendArchitectAgent** for planning)

### 2. **Find Skills by Agent**

Want to know what **StateAgent** is powered by?
- `angular-signals`
- `angular-http`
- `angular-best-practices`

### 3. **Find Agents by Workflow**

Working on **new_feature_development**?
Use: FrontendArchitectAgent → AngularAgent → TailwindAgent → StateAgent → [others as needed]

### 4. **Discover Multi-Agent Workflows**

Need comprehensive code review?
```
@FrontendArchitectAgent @AngularAgent @FrontendSecurityAgent @ReviewAgent
Execute workflow: code_review
```

---

## Adding New Agents

To add a new agent to this registry:

1. Use the **Agent Generator Skill** (`.agents/skills/agent-generator/`)
2. Follow the **Agent Template** (`.agents/AGENT_TEMPLATE.md`)
3. Define agent with name, role, capabilities, and skills
4. Regenerate this file: `@AgentGenerator Generate complete agent registry`

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-02-06 | Initial complete registry of all 15 agents |

---

## See Also

- [Agent Generator Skill](./skills/agent-generator/) - Create/manage agents
- [Agent Template](./AGENT_TEMPLATE.md) - Creating agents step-by-step
- [Skills Directory](./skills/) - All available skills
