# Claude Agent Definitions

This directory contains Claude agent definitions for the my-geo-app project. Each agent is a specialist that combines multiple focused skills to deliver expert solutions.

**Version:** 1.0
**Last Updated:** 2026-02-09
**Total Agents:** 15

---

## Available Agents

### Architecture & Design (1 agent)

1. **[FrontendArchitectAgent](./FrontendArchitectAgent.md)** - Frontend Architecture & Design
   - Feature-based architecture, folder structure, lazy loading
   - Design system integration, component boundaries
   - DDD patterns applied to frontend

### Core Development (2 agents)

2. **[AngularAgent](./AngularAgent.md)** - Angular Framework Specialist
   - Standalone components, signals, forms, routing, HTTP, directives
   - Modern Angular 21+ patterns and TypeScript

3. **[TailwindAgent](./TailwindAgent.md)** - Tailwind CSS & Styling Specialist
   - Utility-first styling, responsive design, dark mode
   - Animations, advanced layouts, design tokens

### User Experience (2 agents)

4. **[UXAgent](./UXAgent.md)** - UI/UX & Accessibility Expert
   - Interface design, accessibility compliance (WCAG 2.1 AA)
   - Mobile-first patterns, keyboard navigation

5. **[AnimationsAgent](./AnimationsAgent.md)** - UI Animations & Motion Design Expert
   - Entrance/exit animations, transitions, micro-interactions
   - Performance optimization, accessibility considerations

### State & Data (2 agents)

6. **[StateAgent](./StateAgent.md)** - Frontend State Management Expert
   - Signal-based state, reactive patterns, derived state
   - State persistence, synchronization

7. **[MockLayerAgent](./MockLayerAgent.md)** - Mock Data & API Simulation Expert
   - json-server setup, realistic test data generation
   - API contract matching, development workflow

### Quality & Security (4 agents)

8. **[FrontendSecurityAgent](./FrontendSecurityAgent.md)** - Frontend Security Expert
   - Security audits, XSS/CSRF prevention, authentication
   - Route guards, secure token storage

9. **[FrontendPerformanceAgent](./FrontendPerformanceAgent.md)** - Frontend Performance Optimization Expert
   - Bundle optimization, lazy loading, change detection
   - Core Web Vitals, rendering performance

10. **[FrontendTestingAgent](./FrontendTestingAgent.md)** - Testing & Quality Assurance Expert
    - Unit tests, component tests, E2E tests
    - Test coverage, accessibility testing

11. **[ReviewAgent](./ReviewAgent.md)** - Code Review & Quality Assurance Expert
    - Code quality analysis, architecture review
    - Security audits, best practices enforcement

### DevOps & Infrastructure (3 agents)

12. **[FrontendDevOpsAgent](./FrontendDevOpsAgent.md)** - Build, CI/CD & Deployment Expert
    - CI/CD pipelines, build optimization, deployment
    - Docker, environment configuration

13. **[EnvironmentsAgent](./EnvironmentsAgent.md)** - Environment Configuration & Management Expert
    - Multi-environment setup, type-safe configuration
    - Secret management, feature flags

14. **[FrontendDocumentationAgent](./FrontendDocumentationAgent.md)** - Documentation & Developer Experience Expert
    - Component documentation, API docs, architecture diagrams
    - Storybook stories, developer guides

### Specialized Components (1 agent)

15. **[IconsAgent](./IconsAgent.md)** - Icon Management & Implementation Expert
    - Icon library integration, icon components
    - Dark mode icons, accessibility labels

---

## How to Use These Agents

### Pattern 1: Direct Agent Request
```markdown
@AngularAgent
Create a standalone product filter component with signals for state,
reactive forms, and Tailwind styling.
```

### Pattern 2: Multi-Agent Collaboration
```markdown
@FrontendArchitectAgent @AngularAgent @TailwindAgent
Design and implement a user dashboard with statistics, charts, and real-time data.
```

### Pattern 3: Specific Task
```markdown
@FrontendSecurityAgent
Review the authentication module for security vulnerabilities and
implement proper route guards.
```

---

## Agent Selection Guide

| Task Type | Recommended Agent(s) |
|-----------|---------------------|
| **New Feature** | FrontendArchitectAgent → AngularAgent → TailwindAgent |
| **Component Creation** | AngularAgent + TailwindAgent |
| **State Management** | StateAgent + AngularAgent |
| **Styling** | TailwindAgent (+ UXAgent for accessibility) |
| **Security Review** | FrontendSecurityAgent + ReviewAgent |
| **Performance Issues** | FrontendPerformanceAgent + ReviewAgent |
| **Testing** | FrontendTestingAgent |
| **Deployment** | FrontendDevOpsAgent + EnvironmentsAgent |
| **Documentation** | FrontendDocumentationAgent |
| **Code Review** | ReviewAgent |

---

## Agent Skill Mapping

Each agent has access to specific skills from [.agents/skills/](.agents/skills/). The mapping is defined in [AGENTS_SKILLS.md](../AGENTS_SKILLS.md).

**Key Principle:** Each agent combines multiple focused skills to provide comprehensive, expert-level solutions.

---

## Creating Custom Agents

To create a new agent:

1. Create a new `.md` file in this directory
2. Follow the format of existing agents
3. Define the agent's role and primary skills
4. Update [AGENTS_SKILLS.md](../AGENTS_SKILLS.md)
5. Add the agent to this README

---

## Related Documentation

- **[AGENTS_SKILLS.md](../AGENTS_SKILLS.md)** - Complete agent-to-skills mapping
- **[AGENTS_SKILLS_FULL.md](../AGENTS_SKILLS_FULL.md)** - Extended documentation
- **[skills/](.agents/skills/)** - Individual skill documentation
- **[/CLAUDE.md](/CLAUDE.md)** - Project-wide guidance for Claude Code

---

**Questions?** Check individual agent files or refer to [AGENTS_SKILLS.md](../AGENTS_SKILLS.md).
