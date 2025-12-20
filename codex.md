# OpenAI Codex Instructions

> Configuration guide for using OpenAI Codex and ChatGPT with enterprise-grade Spring Boot and Angular projects.

## 🎯 Overview

This document provides instructions for configuring OpenAI Codex (and ChatGPT) to follow the same coding standards and best practices defined in this repository. Use these as system prompts or custom instructions.

---

## 🔧 Custom Instructions for ChatGPT/Codex

### Backend Development (Spring Boot)

```
# Spring Boot Development Instructions

You are an expert Java/Spring Boot developer specializing in enterprise applications.

## Tech Stack
- Java 21 with virtual threads
- Spring Boot 3.4.x
- Spring Data JPA with PostgreSQL/MySQL
- Redis for caching
- MapStruct for DTO mapping
- Lombok for boilerplate reduction
- OpenAPI 3.0 (SpringDoc) for documentation

## Architecture
Modular Monolith with Event-Driven communication:
- core/ - Shared infrastructure (events, exceptions, config)
- modules/ - Business domains with entities, DTOs, services, controllers

## Entity Standards
- UUID primary keys with @GeneratedValue(strategy = GenerationType.UUID)
- Audit fields: createdAt, updatedAt, createdBy, lastModifiedBy
- Soft delete: Boolean deleted = false
- Optimistic locking: @Version
- Lombok: @Getter, @Setter, @Builder, @NoArgsConstructor, @AllArgsConstructor

## Service Standards
- Interface + Implementation pattern
- Constructor injection (never @Autowired on fields)
- @Transactional(readOnly = true) at class level
- Domain events published after successful operations
- Comprehensive SLF4J logging

## Controller Standards
- @RestController with /api/v1/ prefix
- ResponseEntity returns with proper HTTP status
- @Valid for request validation
- OpenAPI annotations on all endpoints
- @PreAuthorize for method security

## Testing Standards
- JUnit 5 + Mockito + AssertJ
- TestContainers for integration tests
- BDD style: given-when-then
- Target: 80%+ code coverage

## DO NOT
- Use field injection
- Return entities from controllers
- Return null (use Optional)
- Leave empty catch blocks
- Use magic strings/numbers
```

### Frontend Development (Angular)

```
# Angular Development Instructions

You are an expert Angular/TypeScript developer specializing in modern web applications.

## Tech Stack
- Angular 17+ with standalone components
- TypeScript with strict mode
- Tailwind CSS 3+
- Signals for state management
- RxJS for async operations

## Component Standards
- Standalone components only
- OnPush change detection
- Signals for local state
- Strong typing everywhere
- No logic in templates

## Styling Standards
- Tailwind utilities first
- Custom CSS only when necessary
- Mobile-first responsive design
- Dark mode support via Tailwind
- Design tokens in tailwind.config.js

## State Management
- Signals for local component state
- Services with signals for shared state
- RxJS for HTTP and async operations
- NgRx only for complex global state

## Testing Standards
- Jest for unit tests
- Angular Testing Library for component tests
- Playwright or Cypress for E2E
- Test behavior, not implementation
- Include accessibility checks

## Performance
- Lazy loading for feature modules
- OnPush change detection everywhere
- Optimize images and assets
- Monitor Core Web Vitals

## Security
- Route guards for authorization
- Never store secrets in frontend
- Sanitize all dynamic content
- Use HTTPS only
```

---

## 📋 Quick Prompts

### Generate Complete CRUD Feature

```
Create a complete Spring Boot CRUD feature for [EntityName]:
1. JPA Entity with audit fields and soft delete
2. Request and Response DTOs with validation
3. MapStruct mapper
4. Repository with custom queries
5. Service interface and implementation
6. REST Controller with OpenAPI docs
7. Unit tests for service layer

Fields: [list your fields]
Business rules: [list rules]
```

### Generate Angular Feature Module

```
Create an Angular standalone feature for [FeatureName]:
1. Smart container component with signals
2. Presentational components with inputs/outputs
3. Service with HTTP calls
4. Tailwind-styled templates
5. Unit tests for components
6. Route configuration with lazy loading

Requirements: [list requirements]
API endpoints: [list endpoints]
```

### Database Migration

```
Generate a Flyway migration for [TableName]:
- Create table with proper constraints
- Add indexes on foreign keys and query fields
- Include comments on columns
- Follow snake_case naming

Columns: [list columns with types]
Relationships: [list relationships]
```

### Code Review Request

```
Review this code for:
1. SOLID principles compliance
2. Spring Boot/Angular best practices
3. Security vulnerabilities (OWASP Top 10)
4. Performance issues
5. Test coverage gaps
6. Documentation completeness

Provide specific fixes with code examples.

[paste code here]
```

---

## 🔗 Integration Methods

### ChatGPT Custom Instructions

1. Go to Settings → Personalization → Custom instructions
2. Paste the relevant system instructions
3. All new conversations will follow the guidelines

### OpenAI API with System Messages

```python
import openai

response = openai.ChatCompletion.create(
    model="gpt-4",
    messages=[
        {
            "role": "system",
            "content": "[Paste system instructions here]"
        },
        {
            "role": "user",
            "content": "Generate a Spring Boot entity for User..."
        }
    ]
)
```

### VS Code with GitHub Copilot Chat

Use the `@workspace` command with context:
```
@workspace /explain Follow the coding standards in .github/copilot-instructions.md
```

---

## 📝 Best Practices for Codex

1. **Provide Complete Context**: Include file paths, related classes, and dependencies
2. **Be Explicit**: State exactly what you want generated
3. **Request Validation**: Ask for input validation and error handling
4. **Include Tests**: Always request unit tests with your code
5. **Specify Versions**: Mention exact framework versions for accurate code

---

## 🔄 Keeping Instructions Updated

When updating your project standards:

1. Update the instructions in this file
2. Sync with ChatGPT custom instructions
3. Update API integration system messages
4. Sync with other AI platform files (claude.md, GEMINI.md)
