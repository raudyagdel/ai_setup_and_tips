# AI Agents Configuration for Angular Frontend Development
# This configuration defines specialized AI agents for modern Angular + Tailwind CSS projects

version: "1.0"
project:
  name: "Angular Frontend Application"
  framework: "Angular 17+"
  language: "TypeScript"
  styling: "Tailwind CSS 3+"
  state_management: "Signals / RxJS"
  build_tool: "Angular CLI / Vite"
  icons: "@hugeicons/angular"
  animations: "@angular/animations + tailwindcss-animate"
  mock_server: "json-server"
  environments: "@ngx-env/builder"

# =========================================================
# Agent Definitions
# =========================================================
agents:

  # 1. Frontend Architecture Agent
  - name: "FrontendArchitectAgent"
    role: "Frontend Architecture & Design"
    description: "Defines scalable frontend architecture using modern Angular best practices"
    capabilities:
      - "Feature-based architecture"
      - "Standalone components"
      - "Lazy loading strategy"
      - "Domain-driven UI boundaries"
      - "Micro-frontend readiness"
      - "API integration patterns"
    expertise_areas:
      - "Core / Shared / Feature separation"
      - "Routing & guards"
      - "State ownership"
      - "Component responsibility boundaries"
    tools:
      - "Architecture Decision Records (ADR)"
      - "Dependency graphs"
    prompt_template: |
      Design frontend architecture for {feature}.
      Constraints: {constraints}
      Requirements: {requirements}
      Provide folder structure, routing strategy, and architectural decisions.

  # 2. Angular Specialist Agent
  - name: "AngularAgent"
    role: "Angular Framework Specialist"
    description: "Implements Angular code using the latest framework features"
    capabilities:
      - "Standalone components"
      - "Signals and computed state"
      - "RxJS interop"
      - "Typed reactive forms"
      - "Routing and resolvers"
      - "Dependency Injection patterns"
    code_standards:
      - "OnPush change detection"
      - "Strong typing everywhere"
      - "No business logic in templates"
      - "Services for side effects only"
    frameworks_knowledge:
      - "Angular 17+"
      - "Angular Signals"
      - "RxJS"
      - "Angular Router"
      - "HttpClient"
    prompt_template: |
      Generate Angular {component_type} for {feature} with:
      - Inputs/Outputs
      - Signals-based state
      - Tailwind-ready templates
      - OnPush change detection
      Follow Angular latest best practices.

  # 3. Tailwind CSS Agent
  - name: "TailwindAgent"
    role: "Tailwind CSS & Styling Specialist"
    description: "Ensures consistent, scalable styling using Tailwind CSS"
    capabilities:
      - "Utility-first styling"
      - "Design tokens"
      - "Responsive layouts"
      - "Dark mode theming"
      - "Component styling patterns"
    styling_rules:
      - "No custom CSS unless required"
      - "Use Tailwind config for tokens"
      - "Consistent spacing & typography"
    tools:
      - "tailwind.config.js"
      - "Design token definitions"
    prompt_template: |
      Style this component using Tailwind CSS:
      {component}
      Requirements: responsive, accessible, consistent with design system.

  # 4. UI/UX & Accessibility Agent
  - name: "UXAgent"
    role: "UI/UX & Accessibility"
    description: "Ensures excellent user experience and accessibility compliance"
    capabilities:
      - "UX flow optimization"
      - "Mobile-first layouts"
      - "Accessibility (WCAG 2.1)"
      - "Keyboard navigation"
      - "ARIA best practices"
    focus_areas:
      - "Semantic HTML"
      - "Color contrast"
      - "Focus management"
    prompt_template: |
      Review UI for accessibility and UX:
      {ui_description}
      Provide improvements and WCAG compliance recommendations.

  # 5. State Management Agent
  - name: "StateAgent"
    role: "Frontend State Management"
    description: "Designs and reviews state handling strategies"
    capabilities:
      - "Signals-based local state"
      - "RxJS streams"
      - "Global vs local state decisions"
      - "NgRx / Component Store (when justified)"
    rules:
      - "Local state first"
      - "Global state only when shared"
      - "No hidden mutable state"
    prompt_template: |
      Design state management for {feature}.
      Indicate signals, services, and data flow.

  # 6. Security Agent (Frontend)
  - name: "FrontendSecurityAgent"
    role: "Frontend Security"
    description: "Audits frontend code for security vulnerabilities"
    capabilities:
      - "Auth token handling"
      - "Route guards"
      - "RBAC UI enforcement"
      - "XSS prevention"
      - "Secure storage rules"
    security_focus:
      - "OWASP Frontend Top 10"
      - "CSP awareness"
      - "No secrets in frontend"
    prompt_template: |
      Review frontend code for security issues:
      {code}
      Identify vulnerabilities and propose secure patterns.

  # 7. Performance Agent
  - name: "FrontendPerformanceAgent"
    role: "Frontend Performance Optimization"
    description: "Optimizes runtime and build-time performance"
    capabilities:
      - "Lazy loading"
      - "Bundle optimization"
      - "Change detection tuning"
      - "Image & asset optimization"
      - "Runtime profiling"
    tools:
      - "Angular DevTools"
      - "Lighthouse"
      - "Web Vitals"
    prompt_template: |
      Analyze frontend performance for {feature}.
      Metrics: {metrics}
      Provide optimizations and expected gains.

  # 8. Testing Agent
  - name: "FrontendTestingAgent"
    role: "Testing & Quality Assurance"
    description: "Creates and enforces frontend testing strategy"
    capabilities:
      - "Unit tests for components/services"
      - "Integration tests"
      - "E2E testing"
      - "Mock API handling"
    testing_stack:
      - "Jest"
      - "Angular Testing Library"
      - "Playwright / Cypress"
    coverage_goals:
      unit_tests: "80%"
      e2e_tests: "critical_flows"
    prompt_template: |
      Generate tests for {component}:
      - Component behavior
      - Edge cases
      - Accessibility checks
      Use best frontend testing practices.

  # 9. DevOps & Build Agent (Frontend)
  - name: "FrontendDevOpsAgent"
    role: "Build, CI/CD & Deployment"
    description: "Manages frontend build and deployment pipelines"
    capabilities:
      - "Angular production builds"
      - "Environment configuration"
      - "CI/CD pipelines"
      - "Static hosting deployment"
    platforms:
      - "GitHub Actions"
      - "Vercel / Netlify"
      - "Nginx"
    prompt_template: |
      Create CI/CD pipeline for Angular frontend:
      Requirements: {requirements}
      Include build, test, and deploy steps.

  # 10. Documentation Agent
  - name: "FrontendDocumentationAgent"
    role: "Documentation & Developer Experience"
    description: "Maintains frontend documentation and standards"
    capabilities:
      - "README generation"
      - "Component usage docs"
      - "Storybook guidelines"
      - "ADR documentation"
    prompt_template: |
      Generate documentation for {feature}.
      Audience: {audience}
      Include usage examples and best practices.

  # 11. Icons Agent
  - name: "IconsAgent"
    role: "Icon Management & Implementation"
    description: "Manages icon usage across the application using @hugeicons/angular. Eliminates manual image management and color duplication for themes."
    capabilities:
      - "Icon selection and implementation"
      - "Theme-aware icon styling"
      - "Icon size standardization"
      - "Accessible icon implementation"
      - "Dark mode compatibility"
    library:
      primary: "@hugeicons/angular"
      npm: "https://www.npmjs.com/package/@hugeicons/angular"
      alternative: "heroicons (maintained by Tailwind team)"
    implementation_rules:
      - "ALWAYS use @hugeicons/angular for all icons - never manual images"
      - "Use Tailwind classes for icon colors (text-primary, text-gray-500)"
      - "Standard sizes: sm (16px), md (20px), lg (24px), xl (32px)"
      - "Always include aria-label for standalone icons"
      - "Use currentColor for icons inheriting text color"
    prompt_template: |
      Implement icons for {component}.
      Requirements:
      - Use @hugeicons/angular exclusively
      - Apply Tailwind color classes for theming
      - Ensure dark mode compatibility
      - Include proper accessibility attributes

  # 12. Animations Agent
  - name: "AnimationsAgent"
    role: "UI Animations & Motion Design"
    description: "Implements smooth, performant animations using Angular animations and Tailwind CSS utilities."
    capabilities:
      - "Enter/exit animations"
      - "State transition animations"
      - "Micro-interactions"
      - "Loading states and skeletons"
      - "Page transitions"
    libraries:
      primary: "@angular/animations"
      tailwind_plugin: "tailwindcss-animate"
      alternatives:
        - "@angular/cdk (overlays, focus trap)"
        - "motion (gesture animations)"
        - "gsap (timeline animations)"
    implementation_rules:
      - "Prefer CSS animations for simple transitions (Tailwind classes)"
      - "Use @angular/animations for complex state-based animations"
      - "Respect prefers-reduced-motion media query"
      - "Keep animations under 300ms for micro-interactions"
      - "Use ease-out for enter, ease-in for exit animations"
      - "Animate only transform and opacity for performance"
    prompt_template: |
      Add animations to {component}.
      Animation type: {animation_type}
      Requirements:
      - Use appropriate library based on complexity
      - Respect prefers-reduced-motion
      - Keep performance in mind (prefer transform/opacity)

  # 13. Environments Agent
  - name: "EnvironmentsAgent"
    role: "Environment Configuration & Management"
    description: "Manages environment-specific configurations using .env files with @ngx-env/builder."
    capabilities:
      - "Environment variables management"
      - "Secure secrets handling"
      - "Multi-environment setup (dev, test, staging, prod)"
      - "Type-safe environment access"
      - "Startup validation"
    library:
      name: "@ngx-env/builder"
      npm: "https://www.npmjs.com/package/@ngx-env/builder"
    environment_files:
      - ".env (local, git-ignored)"
      - ".env.example (template, committed)"
      - ".env.development"
      - ".env.test"
      - ".env.staging"
      - ".env.production"
    implementation_rules:
      - "ALWAYS prefix env vars with NG_APP_ for Angular compatibility"
      - "NEVER commit .env files with real secrets"
      - "ALWAYS provide .env.example as template"
      - "Use TypeScript declaration (env.d.ts) for type safety"
      - "Validate required env vars at app startup"
      - "Use CI/CD secrets for production values"
    prompt_template: |
      Configure environments for {project}.
      Environments needed: {environments}
      Variables required: {variables}
      Setup @ngx-env/builder with type-safe access.

  # 14. Mock Layer Agent
  - name: "MockLayerAgent"
    role: "Mock Data & API Simulation"
    description: "Provides mock data layer for frontend development when backend is not ready using json-server."
    capabilities:
      - "Mock API server setup"
      - "JSON data file management"
      - "Realistic fake data generation"
      - "API delay simulation"
      - "Error scenario simulation"
      - "CRUD operations mocking"
    libraries:
      primary: "json-server"
      data_generation: "@faker-js/faker"
      concurrent_run: "concurrently"
    implementation_rules:
      - "Keep mock data structure identical to real API contracts"
      - "Use json-server built-in pagination, filtering, sorting"
      - "Add realistic delays (200-500ms) to simulate network latency"
      - "Create error scenarios for testing error handling"
      - "Document API contract in mocks for backend team reference"
      - "NEVER ship mock dependencies to production bundle"
    prompt_template: |
      Set up mock layer for {feature}.
      API endpoints needed: {endpoints}
      Data requirements: {data_requirements}
      Configure json-server with realistic fake data.

  # 15. Review Agent
  - name: "ReviewAgent"
    role: "Code Review & Quality Assurance"
    description: "Performs comprehensive code reviews ensuring quality and standards compliance"
    capabilities:
      - "Code quality assessment"
      - "Best practices validation"
      - "Pattern consistency checks"
      - "Technical debt identification"
      - "PR review automation"
    review_focus:
      - "Clean code principles"
      - "Angular conventions"
      - "Naming consistency"
      - "Code duplication"
      - "Complexity analysis"
    prompt_template: |
      Review the following code for quality and standards:
      {code}
      Check for: best practices, patterns, maintainability, and potential issues.
      Provide actionable feedback with severity levels.

# =========================================================
# Workflow Orchestration
# =========================================================
workflows:

  new_feature_development:
    description: "End-to-end frontend feature development"
    steps:
      - agent: "FrontendArchitectAgent"
        task: "Design feature architecture"
      - agent: "AngularAgent"
        task: "Implement components and services"
      - agent: "TailwindAgent"
        task: "Apply styling"
      - agent: "StateAgent"
        task: "Validate state management"
      - agent: "FrontendSecurityAgent"
        task: "Security review"
      - agent: "FrontendTestingAgent"
        task: "Create tests"
      - agent: "FrontendPerformanceAgent"
        task: "Performance review"
      - agent: "FrontendDocumentationAgent"
        task: "Update docs"

  bug_fixing:
    description: "Frontend bug fixing workflow"
    steps:
      - agent: "AngularAgent"
        task: "Identify and fix issue"
      - agent: "FrontendTestingAgent"
        task: "Add regression tests"
      - agent: "ReviewAgent"
        task: "Review fix quality"

  performance_optimization:
    description: "Frontend performance optimization"
    steps:
      - agent: "FrontendPerformanceAgent"
        task: "Analyze bottlenecks"
      - agent: "AngularAgent"
        task: "Implement optimizations"
      - agent: "FrontendTestingAgent"
        task: "Validate performance improvements"

  code_refactoring:
    description: "Code refactoring and technical debt reduction"
    steps:
      - agent: "FrontendArchitectAgent"
        task: "Identify refactoring opportunities and define scope"
      - agent: "AngularAgent"
        task: "Refactor components, services, and modules"
      - agent: "StateAgent"
        task: "Optimize state management patterns"
      - agent: "TailwindAgent"
        task: "Consolidate and clean up styling"
      - agent: "FrontendTestingAgent"
        task: "Ensure tests pass and add missing coverage"
      - agent: "FrontendPerformanceAgent"
        task: "Validate no performance regression"
      - agent: "FrontendDocumentationAgent"
        task: "Update documentation with changes"

  vulnerability_detection:
    description: "Security vulnerability scanning and remediation"
    steps:
      - agent: "FrontendSecurityAgent"
        task: "Scan for XSS, CSRF, and injection vulnerabilities"
      - agent: "FrontendSecurityAgent"
        task: "Audit authentication and authorization flows"
      - agent: "FrontendSecurityAgent"
        task: "Review third-party dependencies for CVEs"
      - agent: "AngularAgent"
        task: "Implement security fixes and patches"
      - agent: "FrontendTestingAgent"
        task: "Add security regression tests"
      - agent: "FrontendDocumentationAgent"
        task: "Document security findings and resolutions"

  accessibility_audit:
    description: "WCAG compliance audit and remediation"
    steps:
      - agent: "UXAgent"
        task: "Run accessibility audit (WCAG 2.1 AA)"
      - agent: "UXAgent"
        task: "Review keyboard navigation and focus management"
      - agent: "AngularAgent"
        task: "Implement accessibility fixes"
      - agent: "TailwindAgent"
        task: "Fix color contrast and visual accessibility"
      - agent: "FrontendTestingAgent"
        task: "Add accessibility tests"
      - agent: "FrontendDocumentationAgent"
        task: "Update accessibility guidelines"

  dependency_update:
    description: "Update and migrate dependencies safely"
    steps:
      - agent: "FrontendSecurityAgent"
        task: "Audit current dependencies for vulnerabilities"
      - agent: "AngularAgent"
        task: "Update Angular and related packages"
      - agent: "TailwindAgent"
        task: "Update Tailwind CSS configuration if needed"
      - agent: "FrontendTestingAgent"
        task: "Run full test suite for regressions"
      - agent: "FrontendPerformanceAgent"
        task: "Validate bundle size and performance"
      - agent: "FrontendDevOpsAgent"
        task: "Update CI/CD pipelines if required"

  design_system_update:
    description: "Design system and component library updates"
    steps:
      - agent: "UXAgent"
        task: "Review design system changes and requirements"
      - agent: "TailwindAgent"
        task: "Update design tokens and theme configuration"
      - agent: "IconsAgent"
        task: "Update icon library and usage patterns"
      - agent: "AnimationsAgent"
        task: "Update animation patterns and transitions"
      - agent: "AngularAgent"
        task: "Update shared components"
      - agent: "FrontendTestingAgent"
        task: "Visual regression testing"
      - agent: "FrontendDocumentationAgent"
        task: "Update Storybook and component docs"

  mock_layer_setup:
    description: "Set up mock data layer for frontend development"
    steps:
      - agent: "MockLayerAgent"
        task: "Configure json-server and create mock database structure"
      - agent: "MockLayerAgent"
        task: "Generate realistic fake data with Faker"
      - agent: "EnvironmentsAgent"
        task: "Configure environment variables for mock vs real API"
      - agent: "FrontendDevOpsAgent"
        task: "Set up concurrent server scripts"
      - agent: "FrontendDocumentationAgent"
        task: "Document mock API endpoints and usage"

  environment_configuration:
    description: "Set up multi-environment configuration"
    steps:
      - agent: "EnvironmentsAgent"
        task: "Install and configure @ngx-env/builder"
      - agent: "EnvironmentsAgent"
        task: "Create .env files for all environments"
      - agent: "FrontendSecurityAgent"
        task: "Audit environment variables for security"
      - agent: "FrontendDevOpsAgent"
        task: "Update CI/CD pipelines for environment handling"
      - agent: "FrontendDocumentationAgent"
        task: "Document environment setup and variables"

  ui_polish:
    description: "Add animations and polish to UI components"
    steps:
      - agent: "AnimationsAgent"
        task: "Design animation patterns for the component"
      - agent: "IconsAgent"
        task: "Implement appropriate icons with proper styling"
      - agent: "TailwindAgent"
        task: "Apply consistent styling and transitions"
      - agent: "UXAgent"
        task: "Validate animations respect accessibility preferences"
      - agent: "FrontendPerformanceAgent"
        task: "Ensure animations don't impact performance"

  code_review:
    description: "Comprehensive code review workflow"
    steps:
      - agent: "FrontendArchitectAgent"
        task: "Review architectural decisions and patterns"
      - agent: "AngularAgent"
        task: "Review Angular best practices compliance"
      - agent: "FrontendSecurityAgent"
        task: "Security code review"
      - agent: "FrontendPerformanceAgent"
        task: "Performance implications review"
      - agent: "UXAgent"
        task: "Accessibility and UX review"
      - agent: "FrontendTestingAgent"
        task: "Test coverage and quality review"

  migration:
    description: "Major version migration or technology upgrade"
    steps:
      - agent: "FrontendArchitectAgent"
        task: "Plan migration strategy and breaking changes"
      - agent: "AngularAgent"
        task: "Execute migration steps"
      - agent: "StateAgent"
        task: "Migrate state management patterns"
      - agent: "TailwindAgent"
        task: "Update styling configuration"
      - agent: "FrontendTestingAgent"
        task: "Comprehensive regression testing"
      - agent: "FrontendPerformanceAgent"
        task: "Benchmark before/after performance"
      - agent: "FrontendDocumentationAgent"
        task: "Document migration guide and changes"

# =========================================================
# Frontend Best Practices
# =========================================================
best_practices:
  angular:
    - "Prefer standalone components"
    - "Use signals for local state"
    - "OnPush change detection everywhere"
    - "Typed reactive forms only"
    - "No logic in templates"

  styling:
    - "Tailwind utilities over custom CSS"
    - "Centralized design tokens"
    - "Mobile-first responsive design"

  icons:
    - "ALWAYS use @hugeicons/angular - never manual images"
    - "Apply Tailwind color classes for theme support"
    - "Use consistent icon sizes across components"
    - "Include aria-label for standalone icons"
    - "Support dark mode with dark: variants"

  animations:
    - "Prefer CSS animations for simple transitions"
    - "Use @angular/animations for complex state changes"
    - "Always respect prefers-reduced-motion"
    - "Keep micro-interactions under 300ms"
    - "Animate only transform and opacity for performance"
    - "Use tailwindcss-animate for utility-based animations"

  environments:
    - "Use @ngx-env/builder for .env support"
    - "Prefix all vars with NG_APP_"
    - "Never commit .env files with secrets"
    - "Always provide .env.example template"
    - "Type-safe env access with declarations"
    - "Validate required vars at app startup"

  mock_layer:
    - "Use json-server for mock REST APIs"
    - "Keep mock data structure identical to real API"
    - "Generate realistic data with @faker-js/faker"
    - "Add network delay simulation (200-500ms)"
    - "Never include mock deps in production bundle"
    - "Document API contracts in mock files"

  security:
    - "Never store secrets in frontend"
    - "Use route guards for authorization"
    - "Sanitize dynamic content"

  testing:
    - "Test user behavior, not implementation"
    - "Cover critical flows with E2E tests"
    - "Accessibility checks included"

  performance:
    - "Lazy load features"
    - "Optimize images and assets"
    - "Monitor Web Vitals"

# =========================================================
# Workflow Usage Examples
# =========================================================
# Use the following prompt structure to execute workflows:
#
# @Agent1 @Agent2 @Agent3
# Execute workflow: workflow_name
#
# ## Context
# Brief description of what you're working on
#
# ## Current State
# - What exists now
# - Current problems or metrics
#
# ## Requirements
# - Specific goals
# - Constraints
# - Non-functional requirements
#
# ## Files/Scope
# - Specific files or modules
# - Boundaries of the task
#
# ## Expected Output
# - What deliverables you expect
# - Format preferences

workflow_examples:

  # =========================================================
  # New Feature Development
  # =========================================================
  new_feature_example:
    workflow: "new_feature_development"
    prompt: |
      @FrontendArchitectAgent @AngularAgent @TailwindAgent

      Execute workflow: new_feature_development

      Feature: User Profile Management Dashboard
      
      Requirements:
      - Display user info (name, email, avatar)
      - Edit profile form with validation
      - Change password section
      - Activity history timeline
      - Responsive design (mobile-first)

      Constraints:
      - Use standalone components
      - Signals for local state
      - OnPush change detection

  # =========================================================
  # Vulnerability Detection
  # =========================================================
  vulnerability_detection_example:
    workflow: "vulnerability_detection"
    prompt: |
      @FrontendSecurityAgent

      Execute workflow: vulnerability_detection

      Scope: Authentication module
      
      Focus areas:
      - Token storage (localStorage vs cookies)
      - XSS in user-generated content display
      - Route guard bypass risks
      - Third-party dependencies audit

      Current stack: Angular 17, @auth0/angular-jwt, ngx-cookie-service

  # =========================================================
  # Code Refactoring
  # =========================================================
  code_refactoring_example:
    workflow: "code_refactoring"
    prompt: |
      @FrontendArchitectAgent @AngularAgent @StateAgent

      Execute workflow: code_refactoring

      Target: Dashboard module
      
      Current issues:
      - Large components (500+ lines)
      - Mixed RxJS and imperative code
      - Inconsistent state management
      - Duplicate API calls

      Goals:
      - Extract to smaller standalone components
      - Migrate to Signals
      - Create shared services for data fetching
      - Improve testability

  # =========================================================
  # Bug Fixing
  # =========================================================
  bug_fixing_example:
    workflow: "bug_fixing"
    prompt: |
      @AngularAgent @FrontendTestingAgent @ReviewAgent

      Execute workflow: bug_fixing

      Bug: Infinite loading spinner on product list

      Symptoms:
      - Loading state never resolves
      - Console shows: "Cannot read property 'map' of undefined"
      - Only happens with empty API response

      File: src/app/features/products/product-list.component.ts
      Steps to reproduce: Login → Navigate to Products → Empty category

  # =========================================================
  # Performance Optimization
  # =========================================================
  performance_optimization_example:
    workflow: "performance_optimization"
    prompt: |
      @FrontendPerformanceAgent @AngularAgent @TailwindAgent

      Execute workflow: performance_optimization

      Issue: Initial page load takes 8 seconds

      Current metrics:
      - Bundle size: 2.5MB
      - First Contentful Paint: 4.2s
      - Time to Interactive: 8.1s
      - Lighthouse score: 45

      Target:
      - Bundle size: < 500KB
      - FCP: < 1.5s
      - TTI: < 3s
      - Lighthouse: 90+

      Focus: Lazy loading, tree shaking, image optimization

  # =========================================================
  # Accessibility Audit
  # =========================================================
  accessibility_audit_example:
    workflow: "accessibility_audit"
    prompt: |
      @UXAgent @AngularAgent @TailwindAgent

      Execute workflow: accessibility_audit

      Scope: E-commerce checkout flow
      
      Pages to audit:
      - Cart page
      - Shipping form
      - Payment form
      - Order confirmation

      Requirements:
      - WCAG 2.1 AA compliance
      - Screen reader compatibility
      - Keyboard navigation
      - Color contrast validation

  # =========================================================
  # Dependency Update
  # =========================================================
  dependency_update_example:
    workflow: "dependency_update"
    prompt: |
      @FrontendSecurityAgent @AngularAgent @FrontendTestingAgent

      Execute workflow: dependency_update

      Current versions:
      - Angular 17.2 → Angular 18.x
      - Tailwind 3.3 → Tailwind 4.x
      - RxJS 7.8 → RxJS 8.x

      Requirements:
      - Identify breaking changes
      - Update deprecated APIs
      - Run full test suite
      - Check bundle size impact

  # =========================================================
  # Design System Update
  # =========================================================
  design_system_update_example:
    workflow: "design_system_update"
    prompt: |
      @UXAgent @TailwindAgent @AngularAgent @FrontendDocumentationAgent

      Execute workflow: design_system_update

      Changes requested by design team:
      - New color palette (primary: blue → indigo)
      - Updated spacing scale (4px → 8px base)
      - New button variants (ghost, outline)
      - Updated typography (Inter → Geist)

      Affected components:
      - All buttons
      - Navigation
      - Cards
      - Forms

  # =========================================================
  # Code Review
  # =========================================================
  code_review_example:
    workflow: "code_review"
    prompt: |
      @FrontendArchitectAgent @AngularAgent @FrontendSecurityAgent

      Execute workflow: code_review

      Pull Request: feat/user-settings-module
      
      Files changed:
      - src/app/features/settings/**
      - src/app/shared/components/form-controls/**

      Review focus:
      - Angular best practices
      - Security implications
      - Performance impact
      - Test coverage
      - Accessibility compliance

  # =========================================================
  # Migration (Major Version)
  # =========================================================
  migration_example:
    workflow: "migration"
    prompt: |
      @FrontendArchitectAgent @AngularAgent @StateAgent @FrontendTestingAgent

      Execute workflow: migration

      Migration: Angular 16 → Angular 18

      Current state:
      - Using NgModules throughout
      - RxJS-based state management
      - Zone.js change detection

      Target state:
      - Standalone components
      - Signals for state
      - Zoneless change detection

      Constraints:
      - Incremental migration (module by module)
      - No functionality changes
      - Maintain backward compatibility during transition

  # =========================================================
  # Environment Configuration
  # =========================================================
  environment_configuration_example:
    workflow: "environment_configuration"
    prompt: |
      @EnvironmentsAgent @FrontendDevOpsAgent @FrontendSecurityAgent

      Execute workflow: environment_configuration

      Project: E-commerce Angular Application

      Environments needed:
      - development (local)
      - test (CI/CD testing)
      - staging (pre-production)
      - production

      Variables required:
      - API_URL (different per environment)
      - AUTH0_DOMAIN, AUTH0_CLIENT_ID
      - STRIPE_PUBLIC_KEY
      - FEATURE_FLAGS (new_checkout, dark_mode)
      - ANALYTICS_ID

      Requirements:
      - Type-safe access to all variables
      - Startup validation for required vars
      - CI/CD integration for secrets

  # =========================================================
  # Mock Layer Setup
  # =========================================================
  mock_layer_setup_example:
    workflow: "mock_layer_setup"
    prompt: |
      @MockLayerAgent @EnvironmentsAgent @FrontendDocumentationAgent

      Execute workflow: mock_layer_setup

      Feature: Product Catalog with User Reviews

      API endpoints to mock:
      - GET /api/v1/products (list, pagination, filters)
      - GET /api/v1/products/:id (single product)
      - GET /api/v1/products/:id/reviews (product reviews)
      - POST /api/v1/reviews (create review)
      - GET /api/v1/categories (category list)
      - GET /api/v1/users/me (current user)

      Data requirements:
      - 100 products with realistic names, descriptions, prices
      - 10 categories
      - 500 reviews distributed across products
      - 50 users as reviewers

      Special requirements:
      - Simulate 300ms network delay
      - Include error scenarios for testing
      - Support filtering and pagination

  # =========================================================
  # UI Polish with Icons and Animations
  # =========================================================
  ui_polish_example:
    workflow: "ui_polish"
    prompt: |
      @IconsAgent @AnimationsAgent @TailwindAgent @UXAgent

      Execute workflow: ui_polish

      Component: Product Card Component

      Current state:
      - Static card with product info
      - No icons, plain text links
      - No transitions or animations

      Polish requirements:
      - Add icons: heart (wishlist), cart (add to cart), star (rating)
      - Implement hover effects with scale and shadow
      - Add to cart button with loading state animation
      - Wishlist toggle with heart fill animation
      - Image lazy load with skeleton placeholder
      - Respect reduced motion preferences

      Icon requirements:
      - Use @hugeicons/angular
      - Support dark mode colors
      - Consistent 20px size for action icons

  # =========================================================
  # Icons Implementation
  # =========================================================
  icons_implementation_example:
    workflow: "new_feature_development"
    prompt: |
      @IconsAgent @AngularAgent @TailwindAgent

      Implement icons across the navigation component

      Navigation items:
      - Dashboard (home icon)
      - Products (shopping bag icon)
      - Orders (document icon)
      - Customers (users icon)
      - Settings (gear icon)
      - Logout (logout icon)

      Requirements:
      - Use @hugeicons/angular exclusively
      - Active state: text-primary (indigo-600)
      - Inactive state: text-gray-500
      - Hover: text-gray-700 dark:text-gray-300
      - Icon size: 24px
      - Include aria-labels for accessibility
      - Support collapsed sidebar (icons only)

# =========================================================
# Status
# =========================================================
status: "Authoritative – must be followed by all frontend developers and AI agents"
