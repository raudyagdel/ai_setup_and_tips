# Agent-to-Skills Mapping Configuration
## Automated Expert System for Angular Frontend Development

**Version:** 1.1  
**Status:** Authoritative – defines how agents access skills  
**Last Updated:** 2026-02-07

---

## Overview

This file maps each expert agent to its specialized skills. When a developer asks a specific agent a question, the system automatically retrieves and applies all relevant skills to provide comprehensive, expert-level answers.

**Key Principle:** Each agent is a specialist that combines multiple focused skills to deliver expert solutions.

---

## Agent-to-Skills Mapping

### 1. FrontendArchitectAgent
**Role:** Frontend Architecture & Design  
**Primary Skills:**
- `frontend-design` - Distinctive, production-grade interface design and design systems
- `angular-architecture` - Feature-based architecture, folder structure, lazy loading
- `tailwind-design-system` - Design system organization and scalability
- `clean-ddd-hexagonal` - DDD patterns applied to frontend

**When to Use:**
```
@FrontendArchitectAgent
Design the folder structure for a new product management feature.
Include routing strategy and component boundaries.
```

---

### 2. AngularAgent
**Role:** Angular Framework Specialist  
**Primary Skills:**
- `angular-component` - Standalone components, signals inputs/outputs
- `angular-best-practices` - Modern Angular 21+ patterns
- `angular-development` - Expert Angular and TypeScript development
- `angular-routing` - Lazy loading, guards, route configuration
- `angular-forms` - Signal Forms API, validation, dynamic forms
- `angular-http` - HttpClient, resource(), data fetching
- `angular-signals` - Signals, computed(), linkedSignal(), effects
- `angular-directives` - Custom directives, host directives
- `typescript` - Strong typing, generics, advanced patterns

**When to Use:**
```
@AngularAgent
Implement a product list component with filtering and pagination.
Use signals for state, OnPush change detection, and standalone components.
```

---

### 3. TailwindAgent
**Role:** Tailwind CSS & Styling Specialist  
**Primary Skills:**
- `tailwind-4` - Tailwind CSS 4 fundamentals and CSS-First architecture
- `tailwind-css-patterns` - Utility-first styling, responsive design
- `tailwind-design-system` - Design tokens, themes, component styling
- `tailwindcss-fundamentals-v4` - Installation, configuration, 2026 best practices
- `tailwindcss-mobile-first` - Mobile-first responsive design patterns
- `tailwindcss-animations` - Animation utilities, transitions
- `tailwindcss-advanced-layouts` - Grid, Flexbox, complex layouts

**When to Use:**
```
@TailwindAgent
Style the checkout form component with responsive design, dark mode,
and smooth animations. Use Tailwind utility classes exclusively.
```

---

### 4. UXAgent
**Role:** UI/UX & Accessibility Expert  
**Primary Skills:**
- `frontend-design` - Distinctive interface design with high design quality
- `interface-design` - Dashboard, admin panels, interactive products
- `tailwind-patterns` - Utility-first styling, responsive design patterns
- `tailwind-mobile-first` - Mobile-first UX patterns
- `angular-component` - Component architecture for accessibility
- `tailwindcss-advanced-layouts` - Layout patterns for good UX

**When to Use:**
```
@UXAgent
Review the user settings page for accessibility compliance (WCAG 2.1 AA).
Ensure keyboard navigation and proper color contrast.
```

---

### 5. StateAgent
**Role:** Frontend State Management Expert  
**Primary Skills:**
- `angular-signals` - Signals-based state management
- `angular-best-practices` - State ownership patterns
- `angular-development` - State architecture decisions
- `clean-ddd-hexagonal` - DDD state patterns

**When to Use:**
```
@StateAgent
Design the state management for a multi-step wizard, including
validation state, navigation history, and form data persistence.
```

---

### 6. FrontendSecurityAgent
**Role:** Frontend Security Expert  
**Primary Skills:**
- `angular-best-practices` - Security patterns in Angular
- `angular-routing` - Route guards, authorization
- `clean-ddd-hexagonal` - Domain-driven security boundaries
- `typescript` - Type-safe security patterns

**When to Use:**
```
@FrontendSecurityAgent
Audit the authentication module for XSS vulnerabilities and improper
token storage. Review route guards implementation.
```

---

### 7. FrontendPerformanceAgent
**Role:** Frontend Performance Optimization Expert  
**Primary Skills:**
- `angular-best-practices` - Performance patterns
- `angular-routing` - Lazy loading, route-based code splitting
- `tailwind-4` - Efficient CSS generation
- `tailwind-patterns` - Efficient utility-first styling patterns
- `angular-development` - Performance profiling and optimization

**When to Use:**
```
@FrontendPerformanceAgent
Analyze and optimize the product listing page. Current bundle size is 2.5MB
and First Contentful Paint is 4.2 seconds.
```

---

### 8. FrontendTestingAgent
**Role:** Testing & Quality Assurance Expert  
**Primary Skills:**
- `angular-component` - Component testing patterns
- `angular-best-practices` - Testability best practices
- `angular-development` - Test architecture
- `typescript` - Type-safe test code

**When to Use:**
```
@FrontendTestingAgent
Create comprehensive tests for the UserProfileComponent including
edge cases, accessibility checks, and error scenarios.
```

---

### 9. FrontendDevOpsAgent
**Role:** Build, CI/CD & Deployment Expert  
**Primary Skills:**
- `angular-development` - Build optimization
- `angular-routing` - Lazy loading strategies
- `tailwind-4` - Production CSS generation

**When to Use:**
```
@FrontendDevOpsAgent
Set up a GitHub Actions CI/CD pipeline for the Angular application
including build, test, and deployment to Netlify.
```

---

### 10. FrontendDocumentationAgent
**Role:** Documentation & Developer Experience Expert  
**Primary Skills:**
- `frontend-design` - Visual design documentation and polished UI examples
- `angular-best-practices` - Pattern documentation
- `interface-design` - Visual documentation
- `angular-development` - Comprehensive guides

**When to Use:**
```
@FrontendDocumentationAgent
Generate component usage documentation and Storybook stories for
the Button, Card, and Modal components.
```

---

### 11. IconsAgent
**Role:** Icon Management & Implementation Expert  
**Primary Skills:**
- `frontend-design` - Icon design aesthetics and visual consistency
- `tailwind-patterns` - Icon styling patterns and responsive handling
- `tailwind-css-patterns` - Icon styling with Tailwind
- `interface-design` - Icon selection and placement
- `tailwindcss-fundamentals-v4` - Dark mode icon support
- `angular-component` - Icon component patterns

**When to Use:**
```
@IconsAgent
Implement icons across all navigation items using @hugeicons/angular.
Ensure dark mode support, proper sizing, and accessibility labels.
```

---

### 12. AnimationsAgent
**Role:** UI Animations & Motion Design Expert  
**Primary Skills:**
- `frontend-design` - Motion design principles and polished animations
- `tailwindcss-animations` - Tailwind animation utilities
- `tailwind-patterns` - Responsive animation patterns
- `angular-best-practices` - Animation patterns in Angular
- `interface-design` - Motion design principles
- `tailwind-css-patterns` - Transition utilities

**When to Use:**
```
@AnimationsAgent
Add smooth enter/exit animations to the modal component and implement
a stagger animation for list items. Respect prefers-reduced-motion.
```

---

### 13. EnvironmentsAgent
**Role:** Environment Configuration & Management Expert  
**Primary Skills:**
- `angular-best-practices` - Environment patterns
- `angular-development` - Configuration management
- `typescript` - Type-safe configuration

**When to Use:**
```
@EnvironmentsAgent
Set up @ngx-env/builder with .env files for development, staging, and
production environments. Include type-safe TypeScript declarations.
```

---

### 14. MockLayerAgent
**Role:** Mock Data & API Simulation Expert  
**Primary Skills:**
- `angular-best-practices` - Mock integration patterns
- `angular-http` - API contract matching
- `angular-development` - Development workflow optimization

**When to Use:**
```
@MockLayerAgent
Create a mock API layer with json-server for the product catalog,
including pagination, filtering, and 100+ realistic product records.
```

---

### 15. ReviewAgent
**Role:** Code Review & Quality Assurance Expert  
**Primary Skills:**
- `angular-best-practices` - Quality standards
- `typescript` - Code quality patterns
- `clean-ddd-hexagonal` - Architecture review
- `angular-component` - Component patterns
- `tailwind-css-patterns` - Styling consistency

**When to Use:**
```
@ReviewAgent
Review my pull request for the dashboard module. Check for Angular
best practices, security issues, and code quality.
```

---

## How to Use Agent-Skills Mapping

### Pattern 1: Direct Agent Request
```markdown
@AngularAgent
Create a standalone product filter component with signals for state,
reactive forms, and tailwind styling.
```

**Automatic Behavior:**
- Agent loads relevant skills: `angular-component`, `angular-signals`, `angular-forms`, `tailwind-css-patterns`
- Applies all skill guidelines to response
- References specific SKILL.md files for deeper patterns

---

### Pattern 2: Multi-Agent Collaboration
```markdown
@FrontendArchitectAgent @AngularAgent @TailwindAgent
Execute workflow: new_feature_development

Feature: User dashboard with statistics, charts, and real-time data.
```

**Automatic Behavior:**
- Each agent pools its primary skills
- Agent 1 focuses on architecture/structure
- Agent 2 implements components using Angular skills
- Agent 3 handles styling with Tailwind skills
- All agents maintain consistency through shared skill knowledge

---

### Pattern 3: Workflow-Triggered Skills
When executing a workflow like `code_refactoring`, all agents in the workflow automatically load their skill sets:

```yaml
Workflow: code_refactoring
  - FrontendArchitectAgent (loads: angular-architecture, clean-ddd-hexagonal)
  - AngularAgent (loads: all Angular + TypeScript skills)
  - StateAgent (loads: angular-signals, state patterns)
  - TailwindAgent (loads: all Tailwind skills)
  - FrontendTestingAgent (loads: testing skills)
```

---

## Skill File Structure

Each skill is located in:
```
.agents/skills/{skill-name}/SKILL.md
```

Skills contain:
- **Overview** - What the skill covers
- **Concepts** - Key terminology and patterns
- **Implementation** - Step-by-step guidance
- **Best Practices** - Do's and Don'ts
- **Code Examples** - Practical implementations
- **Common Pitfalls** - What to avoid
- **Related Skills** - Links to complementary skills

---

## Adding New Skills to Agents

To add a skill to an agent:

1. **Identify the skill file** in `.agents/skills/{skill-name}/SKILL.md`
2. **Find the agent section** in this file
3. **Add to the "Primary Skills" list:**

```markdown
### UpdatedAgentName
**Role:** Description  
**Primary Skills:**
- `skill-name-1` - Description
- `skill-name-2` - Description  ← NEW SKILL
- `skill-name-3` - Description
```

4. **Test by using the agent** with that new skill domain

---

## When Agent Skills Are Applied

Skills are automatically applied in these scenarios:

| Scenario | Skills Applied | Example |
|----------|---|---|
| Direct agent request | Agent's primary skills | `@AngularAgent` → loads angular-* skills |
| Workflow execution | Each agent's primary skills | `new_feature_development` → all agents load their skills |
| Multi-agent request | All requested agents' skills | `@Agent1 @Agent2` → combine their skill sets |
| Inheritance | Parent skills used by child agents | Child agents access core skills |

---

## Principle: Skill Consistency

All agents follow these principles when using skills:

✅ **DO:**
- Apply ALL relevant skill guidelines from primary skills
- Reference skill files for deep patterns
- Maintain consistency across agent responses
- Escalate to specialized agents when skills don't overlap
- Combine skills for comprehensive solutions

❌ **DON'T:**
- Ignore skill guidelines to save time
- Apply skills outside the agent's domain
- Contradict other agent skillsets
- Use outdated skill knowledge
- Invent patterns not covered by skills

---

## Example: Complete Agent Usage

### Setup
```
@AngularAgent
I need to create a product search component with:
- Real-time search as user types
- Filter results by category and price
- Display 10 results per page with pagination
- Save search history
- Dark mode support
```

### Agent Behavior (Uses Primary Skills)

1. **Angular-component** → Creates standalone component structure
2. **Angular-signals** → Implements reactive search state with signals
3. **Angular-forms** → Builds search input form with validation
4. **Angular-routing** → Handles pagination routing parameters
5. **Angular-http** → Fetches search results from API
6. **Tailwind-css-patterns** → Styles with responsive utilities
7. **Tailwindcss-animations** → Adds smooth input focus animations
8. **Angular-best-practices** → Ensures OnPush change detection

### Output
A production-ready component that follows all skill guidelines, with code examples referencing specific SKILL.md sections.

---

## Summary

This mapping system ensures:

✅ **Consistency** - All agents follow the same skill-based approach  
✅ **Expertise** - Each agent brings specialized skill knowledge  
✅ **Scalability** - Easy to add new skills to agents  
✅ **Efficiency** - No manual skill selection needed  
✅ **Quality** - Automatic application of best practices  

**Result:** When you ask an expert agent, you get solutions infused with deep skill knowledge across multiple domains.

---

**Questions?** Check the specific SKILL.md file for your domain.  
**Adding new agent?** See [AGENT_TEMPLATE.md](./AGENT_TEMPLATE.md)
