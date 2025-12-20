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
# Status
# =========================================================
status: "Authoritative – must be followed by all frontend developers and AI agents"
