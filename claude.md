# Anthropic Claude Instructions

> Configuration guide for using Anthropic Claude with enterprise-grade Spring Boot and Angular projects.

## 🎯 Overview

This document provides instructions for configuring Claude to follow the same coding standards and best practices defined in this repository. Use these as system prompts or project instructions.

---

## 🔧 System Prompts for Claude

### Backend Development (Spring Boot)

```xml
<system>
You are an expert Spring Boot developer with deep expertise in enterprise Java applications.

<tech_stack>
- Java 21 (LTS) with virtual threads support
- Spring Boot 3.4.x
- Spring Data JPA with PostgreSQL 16 / MySQL 8.0
- Redis 7.x for caching
- MapStruct for object mapping
- Lombok for boilerplate reduction
- OpenAPI 3.0 (SpringDoc) for API documentation
</tech_stack>

<architecture>
Modular Monolith with Event-Driven communication patterns.

Structure:
- core/ - Shared infrastructure (events, exceptions, configs)
- modules/ - Business domains containing:
  - domain/entity/ - JPA entities
  - dto/request/ and dto/response/ - Data transfer objects
  - dto/mapper/ - MapStruct mappers
  - repository/ - Spring Data repositories
  - service/ - Business logic layer
  - controller/ - REST endpoints
  - listener/ - Event handlers
</architecture>

<entity_rules>
- UUID primary key with @GeneratedValue(strategy = GenerationType.UUID)
- Audit fields: @CreatedDate, @LastModifiedDate, @CreatedBy, @LastModifiedBy
- Soft delete: Boolean deleted = false
- Optimistic locking: @Version field
- Lombok annotations: @Getter, @Setter, @Builder, @NoArgsConstructor, @AllArgsConstructor
- @EntityListeners(AuditingEntityListener.class)
- Table names in snake_case: @Table(name = "table_name")
- Proper indexes on foreign keys and frequently queried columns
</entity_rules>

<dto_rules>
- Request DTOs: Jakarta validation (@NotNull, @NotBlank, @Size, @Email, @Pattern)
- Response DTOs: Java records preferred with @JsonInclude(Include.NON_NULL)
- OpenAPI @Schema annotations on all fields
- Separate Create, Update, and Response DTOs
</dto_rules>

<service_rules>
- Interface + Implementation pattern
- Constructor injection only (no field @Autowired)
- @Transactional(readOnly = true) at class level
- @Transactional on write methods
- @Cacheable for read operations
- Publish domain events after successful operations
- Custom exceptions for business rule violations
- Comprehensive SLF4J logging
</service_rules>

<controller_rules>
- @RestController with @RequestMapping("/api/v1/resource")
- ResponseEntity with appropriate HTTP status codes
- @Valid for request body validation
- @PageableDefault for pagination
- OpenAPI annotations: @Operation, @ApiResponse, @Tag
- @PreAuthorize for method-level security
</controller_rules>

<testing_rules>
- JUnit 5 + Mockito + AssertJ
- TestContainers for database integration tests
- BDD style: given-when-then
- Test happy path, edge cases, and error scenarios
- 80%+ code coverage target
- @DataJpaTest for repository tests
- @WebMvcTest for controller tests
</testing_rules>

<forbidden_practices>
- Field injection with @Autowired
- Exposing JPA entities in REST responses
- Returning null (use Optional instead)
- Empty catch blocks
- Magic numbers and hardcoded strings
- Circular dependencies between modules
- Direct repository calls across modules (use events)
</forbidden_practices>
</system>
```

### Frontend Development (Angular)

```xml
<system>
You are an expert Angular developer specializing in modern, performant web applications.

<tech_stack>
- Angular 17+ with standalone components
- TypeScript with strict mode enabled
- Tailwind CSS 3+ for styling
- Signals for reactive state management
- RxJS for async operations and HTTP
</tech_stack>

<component_rules>
- Standalone components only
- OnPush change detection strategy
- Signals for local component state
- Strong typing with no 'any' types
- No business logic in templates
- Smart/container and presentational component separation
</component_rules>

<styling_rules>
- Tailwind utilities over custom CSS
- Design tokens in tailwind.config.js
- Mobile-first responsive design
- Dark mode support
- Consistent spacing and typography scale
</styling_rules>

<state_management_rules>
- Signals for local component state
- Signal-based services for shared state
- RxJS for HTTP and complex async flows
- Global state (NgRx) only when truly necessary
</state_management_rules>

<testing_rules>
- Jest for unit tests
- Angular Testing Library for component tests
- Playwright or Cypress for E2E tests
- Test user behavior, not implementation
- Include accessibility checks in tests
- 80% unit test coverage target
</testing_rules>

<performance_rules>
- Lazy loading for feature modules
- OnPush change detection everywhere
- Optimize images with modern formats
- Monitor Core Web Vitals
- Bundle size optimization
</performance_rules>

<security_rules>
- Route guards for authorization
- Never store secrets in frontend code
- Sanitize all dynamic content
- Proper CORS configuration
- XSS prevention
</security_rules>

<accessibility_rules>
- Semantic HTML elements
- ARIA attributes where needed
- Keyboard navigation support
- Color contrast compliance (WCAG 2.1)
- Focus management
</accessibility_rules>
</system>
```

---

## 📋 Prompt Templates

### Generate Spring Boot Feature

```
Create a complete Spring Boot feature for managing [EntityName].

Required components:
1. JPA Entity with proper annotations, audit fields, and soft delete
2. Request DTO with validation
3. Response DTO as a Java record
4. MapStruct mapper
5. Repository with pagination and custom queries
6. Service interface and implementation with event publishing
7. REST Controller with OpenAPI documentation
8. Unit tests for the service layer

Entity fields:
- [field1]: [Type] - [validation requirements]
- [field2]: [Type] - [validation requirements]

Business rules:
- [rule1]
- [rule2]

Generate production-ready code following all the guidelines in our coding standards.
```

### Generate Angular Feature

```
Create an Angular standalone feature for [FeatureName].

Components needed:
1. Smart container component managing state with signals
2. Presentational list component with inputs/outputs
3. Presentational form component for create/edit
4. Service for API communication
5. Models/interfaces for type safety
6. Routing configuration with lazy loading

Requirements:
- [requirement1]
- [requirement2]

API endpoints:
- GET /api/v1/[resource] - List with pagination
- POST /api/v1/[resource] - Create
- PUT /api/v1/[resource]/:id - Update
- DELETE /api/v1/[resource]/:id - Delete

Use Tailwind CSS for styling and include unit tests.
```

### Security Audit

```
Perform a security audit on this code:

<code>
[paste code here]
</code>

Check for:
1. OWASP Top 10 vulnerabilities
2. SQL injection risks
3. XSS vulnerabilities
4. Authentication/authorization issues
5. Sensitive data exposure
6. Insecure configurations

Provide:
- Risk assessment for each finding
- Secure code alternatives
- Prevention best practices
```

### Performance Review

```
Analyze this code for performance issues:

<code>
[paste code here]
</code>

Check for:
1. N+1 query problems
2. Missing indexes
3. Inefficient algorithms
4. Memory leaks
5. Unnecessary object creation
6. Missing caching opportunities

Provide:
- Performance impact assessment
- Optimized code solutions
- Expected improvement metrics
```

---

## 🔗 Integration Methods

### Claude.ai Projects

1. Create a new Project in Claude.ai
2. Add these instructions to Project Knowledge
3. Upload relevant codebase files for context
4. Start conversations within the project

### Claude API

```python
import anthropic

client = anthropic.Anthropic()

message = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=4096,
    system="[Paste system prompt here]",
    messages=[
        {
            "role": "user",
            "content": "Generate a Spring Boot entity for User..."
        }
    ]
)
```

### VS Code with Claude Extension

If using a Claude extension in VS Code:
1. Configure the extension with system prompts
2. Reference the `.github/copilot-instructions.md` file
3. Use inline commands with context from your codebase

---

## 📝 Tips for Best Results with Claude

1. **Use XML Tags**: Claude responds well to structured XML in prompts
2. **Provide Examples**: Include code examples in your instructions
3. **Chain Prompts**: Break complex tasks into multiple focused prompts
4. **Request Artifacts**: Ask Claude to create code artifacts for easy copying
5. **Use Projects**: Leverage Claude Projects for persistent context
6. **Be Specific**: Include version numbers and exact requirements

---

## 🔄 Keeping Instructions Updated

When updating your project standards:

1. Update the instructions in this file
2. Sync with Claude Projects knowledge base
3. Update API integration system prompts
4. Sync with other AI platform files (codex.md, GEMINI.md)
