# AI Agents Configuration for Spring Boot Development
# This configuration defines specialized AI agents for different development tasks

version: "1.0"
project:
  name: "Spring Boot Microservices Development"
  framework: "Spring Boot 3.4+"
  java_version: "21"
  build_tool: "Gradle"

# Agent Definitions
agents:
  
  # 1. Architecture Agent
  - name: "ArchitectAgent"
    role: "System Architecture & Design"
    description: "Specializes in microservices architecture, design patterns, and system design decisions"
    capabilities:
      - "Design microservices architecture"
      - "Design pattern selection and implementation"
      - "API design (REST)"
      - "Database schema design"
      - "Service decomposition strategy"
      - "Communication patterns (sync/async)"
      - "Event-driven architecture"
    expertise_areas:
      - "Bounded contexts"
      - "Service boundaries"
      - "Data consistency patterns"
      - "CAP theorem trade-offs"
      - "CQRS and Event Sourcing"
    tools:
      - "PlantUML for diagrams"
      - "C4 model for architecture visualization"
      - "Architecture Decision Records (ADR)"
    prompt_template: |
      I need architectural guidance for {domain}.
      Requirements: {requirements}
      Constraints: {constraints}
      Please provide architecture design with diagrams, component interactions, and trade-off analysis.
    
  # 2. Code Generation Agent
  - name: "CodeGenAgent"
    role: "Code Generator & Implementation"
    description: "Generates high-quality Spring Boot code following best practices"
    capabilities:
      - "Generate entities, DTOs, and mappers"
      - "Create repositories with custom queries"
      - "Implement service layer with business logic"
      - "Build REST controllers"
      - "Generate configuration classes"
      - "Create exception handlers"
      - "Implement security components"
    code_standards:
      - "Use constructor injection"
      - "Lombok for boilerplate reduction"
      - "Immutable DTOs where possible"
      - "Proper null handling"
      - "Meaningful variable names"
      - "Comprehensive JavaDoc"
    frameworks_knowledge:
      - "Spring Boot 3.4+"
      - "Spring Data JPA"
      - "Spring Security 6+"
      - "Spring Cloud"
      - "MapStruct"
      - "Lombok"
      - "Validation API"
    prompt_template: |
      Generate {component_type} for {entity_name} with:
      - Requirements: {requirements}
      - Relationships: {relationships}
      - Validation rules: {validation}
      - Java 21 features: virtual threads, records, pattern matching
      Include all necessary annotations and follow Spring Boot best practices.

  # 3. Testing Agent
  - name: "TestingAgent"
    role: "Test Generation & Quality Assurance"
    description: "Creates comprehensive test suites and ensures code quality"
    capabilities:
      - "Generate unit tests (JUnit 5, Mockito)"
      - "Create integration tests (TestContainers)"
      - "Implement contract tests (Spring Cloud Contract)"
      - "Performance testing basics"
      - "Security testing"
      - "Test data builders"
    testing_stack:
      - "JUnit 5"
      - "Mockito"
      - "AssertJ"
      - "TestContainers"
      - "RestAssured"
      - "WireMock"
      - "JMeter/Gatling"
    coverage_goals:
      unit_tests: "80%"
      integration_tests: "60%"
      e2e_tests: "critical_paths"
    prompt_template: |
      Generate comprehensive tests for {class_name}:
      - Unit tests covering all methods
      - Edge cases and boundary conditions
      - Exception scenarios
      - Integration tests if applicable
      - Mocking strategy for dependencies
      Use BDD style (given-when-then) and ensure test independence.

  # 4. Security Agent
  - name: "SecurityAgent"
    role: "Security Implementation & Audit"
    description: "Implements security features and audits code for vulnerabilities"
    capabilities:
      - "Implement authentication (JWT, OAuth2)"
      - "Configure authorization (RBAC, ABAC)"
      - "Security auditing"
      - "Vulnerability scanning"
      - "Secure coding practices"
      - "Encryption implementation"
    security_focus:
      - "OWASP Top 10"
      - "SQL Injection prevention"
      - "XSS protection"
      - "CSRF protection"
      - "Secure session management"
      - "Sensitive data protection"
      - "API security"
    tools:
      - "Spring Security"
      - "OWASP Dependency Check"
      - "Snyk"
      - "SonarQube"
    prompt_template: |
      Review this code for security vulnerabilities:
      {code}
      Check for: SQL injection, XSS, authentication/authorization issues, 
      sensitive data exposure, and other OWASP Top 10 vulnerabilities.
      Provide secure alternatives and best practices.

  # 5. Performance Optimization Agent
  - name: "PerformanceAgent"
    role: "Performance Optimization & Tuning"
    description: "Analyzes and optimizes application performance"
    capabilities:
      - "Query optimization"
      - "Caching strategy design"
      - "Connection pool tuning"
      - "Memory optimization"
      - "JVM tuning"
      - "Async processing implementation"
      - "Load testing strategy"
    optimization_areas:
      - "Database queries (N+1 problem)"
      - "API response times"
      - "Memory usage"
      - "CPU utilization"
      - "Network latency"
      - "Startup time"
    tools:
      - "JProfiler/VisualVM"
      - "Spring Boot Actuator"
      - "Micrometer"
      - "JMeter/Gatling"
      - "Database explain plans"
    prompt_template: |
      Analyze performance of {component}:
      Current metrics: {metrics}
      Issues: {issues}
      Provide optimization recommendations with:
      - Root cause analysis
      - Code improvements
      - Configuration changes
      - Expected performance gains

  # 6. Database Agent
  - name: "DatabaseAgent"
    role: "Database Design & Optimization"
    description: "Designs schemas, writes queries, and optimizes database interactions"
    capabilities:
      - "Schema design and normalization"
      - "Index strategy"
      - "Query optimization"
      - "Migration scripts (Flyway/Liquibase)"
      - "Data modeling"
      - "Partitioning strategies"
    database_support:
      - "PostgreSQL"
      - "MySQL"
      - "Oracle"
      - "MongoDB"
      - "Redis"
    jpa_expertise:
      - "Entity relationships"
      - "@EntityGraph for N+1 prevention"
      - "Custom repositories"
      - "Specifications for dynamic queries"
      - "Projection interfaces"
    prompt_template: |
      Design database schema for {domain}:
      Entities: {entities}
      Relationships: {relationships}
      Scale: {scale}
      Provide: schema DDL, indexing strategy, JPA entities, 
      Flyway migrations, and optimization tips.

  # 7. DevOps Agent
  - name: "DevOpsAgent"
    role: "Deployment & Infrastructure"
    description: "Handles containerization, CI/CD, and cloud deployment"
    capabilities:
      - "Dockerfile creation"
      - "Docker Compose setup"
      - "Kubernetes manifests"
      - "CI/CD pipeline configuration"
      - "Cloud deployment (AWS, Azure, GCP)"
      - "Infrastructure as Code (Terraform)"
      - "Monitoring setup"
    platforms:
      - "Docker/Kubernetes"
      - "GitHub Actions"
      - "GitLab CI"
      - "Jenkins"
      - "AWS ECS/EKS"
      - "Azure AKS"
    prompt_template: |
      Create deployment configuration for {service}:
      Platform: {platform}
      Requirements: {requirements}
      Provide: Dockerfile, K8s manifests, CI/CD pipeline, 
      monitoring setup, and deployment strategy.

  # 8. Documentation Agent
  - name: "DocumentationAgent"
    role: "Documentation & API Specs"
    description: "Generates comprehensive documentation and API specifications"
    capabilities:
      - "OpenAPI/Swagger documentation"
      - "README generation"
      - "Architecture documentation"
      - "API usage guides"
      - "JavaDoc generation"
      - "Runbook creation"
    documentation_types:
      - "API documentation (OpenAPI 3.0)"
      - "Architecture diagrams (PlantUML, C4)"
      - "Developer guides"
      - "Deployment guides"
      - "Troubleshooting guides"
      - "Changelog maintenance"
    prompt_template: |
      Generate documentation for {component}:
      Type: {doc_type}
      Audience: {audience}
      Include: setup instructions, usage examples, API specs,
      troubleshooting tips, and best practices.

  # 9. Code Review Agent
  - name: "ReviewAgent"
    role: "Code Review & Quality Check"
    description: "Reviews code for quality, standards compliance, and best practices"
    capabilities:
      - "Code quality analysis"
      - "SOLID principles validation"
      - "Design pattern recognition"
      - "Best practices enforcement"
      - "Refactoring suggestions"
      - "Technical debt identification"
    review_checklist:
      - "Code readability"
      - "Naming conventions"
      - "Error handling"
      - "Resource management"
      - "Thread safety"
      - "Test coverage"
      - "Documentation completeness"
      - "Performance considerations"
    prompt_template: |
      Review this code:
      {code}
      Analyze for: SOLID principles, design patterns, Spring Boot best practices,
      performance issues, security vulnerabilities, testability.
      Provide specific refactoring recommendations with examples.

  # 10. Debugging Agent
  - name: "DebuggingAgent"
    role: "Problem Diagnosis & Resolution"
    description: "Helps diagnose and fix issues in Spring Boot applications"
    capabilities:
      - "Error analysis"
      - "Log interpretation"
      - "Root cause analysis"
      - "Solution recommendations"
      - "Prevention strategies"
    debugging_expertise:
      - "Spring Boot exceptions"
      - "JPA/Hibernate issues"
      - "Connection pool problems"
      - "Memory leaks"
      - "Deadlocks"
      - "Configuration issues"
    prompt_template: |
      Debug this issue:
      Problem: {problem_description}
      Error logs: {logs}
      Stack trace: {stack_trace}
      Context: {context}
      Provide: root cause analysis, step-by-step debugging approach,
      solution with code examples, and prevention recommendations.

# Workflow Orchestration
workflows:
  
  new_feature_development:
    description: "Complete workflow for implementing a new feature"
    steps:
      - agent: "ArchitectAgent"
        task: "Design feature architecture"
      - agent: "DatabaseAgent"
        task: "Design database schema and migrations"
      - agent: "CodeGenAgent"
        task: "Generate entities, services, controllers"
      - agent: "SecurityAgent"
        task: "Review security implications"
      - agent: "TestingAgent"
        task: "Generate test suite"
      - agent: "PerformanceAgent"
        task: "Review performance considerations"
      - agent: "DocumentationAgent"
        task: "Generate API documentation"
      - agent: "ReviewAgent"
        task: "Final code review"

  bug_fixing:
    description: "Workflow for diagnosing and fixing bugs"
    steps:
      - agent: "DebuggingAgent"
        task: "Diagnose issue"
      - agent: "CodeGenAgent"
        task: "Implement fix"
      - agent: "TestingAgent"
        task: "Create regression tests"
      - agent: "ReviewAgent"
        task: "Review fix quality"

  performance_optimization:
    description: "Workflow for performance improvements"
    steps:
      - agent: "PerformanceAgent"
        task: "Identify bottlenecks"
      - agent: "DatabaseAgent"
        task: "Optimize queries and schema"
      - agent: "CodeGenAgent"
        task: "Implement optimizations"
      - agent: "TestingAgent"
        task: "Performance testing"
      - agent: "DocumentationAgent"
        task: "Document changes"

  security_audit:
    description: "Complete security audit workflow"
    steps:
      - agent: "SecurityAgent"
        task: "Security vulnerability scan"
      - agent: "ReviewAgent"
        task: "Code security review"
      - agent: "CodeGenAgent"
        task: "Implement security fixes"
      - agent: "TestingAgent"
        task: "Security testing"
      - agent: "DocumentationAgent"
        task: "Update security documentation"

  deployment_preparation:
    description: "Prepare application for deployment"
    steps:
      - agent: "TestingAgent"
        task: "Run full test suite"
      - agent: "SecurityAgent"
        task: "Security check"
      - agent: "PerformanceAgent"
        task: "Load testing"
      - agent: "DevOpsAgent"
        task: "Prepare deployment artifacts"
      - agent: "DocumentationAgent"
        task: "Update deployment docs"

  code_refactoring:
    description: "Code refactoring and technical debt reduction"
    steps:
      - agent: "ArchitectAgent"
        task: "Identify refactoring opportunities and scope"
      - agent: "ReviewAgent"
        task: "Analyze code quality and SOLID violations"
      - agent: "CodeGenAgent"
        task: "Refactor services, repositories, and controllers"
      - agent: "DatabaseAgent"
        task: "Optimize schema and queries if needed"
      - agent: "TestingAgent"
        task: "Ensure tests pass and add missing coverage"
      - agent: "PerformanceAgent"
        task: "Validate no performance regression"
      - agent: "DocumentationAgent"
        task: "Update documentation with changes"

  vulnerability_detection:
    description: "Security vulnerability scanning and remediation"
    steps:
      - agent: "SecurityAgent"
        task: "Scan for OWASP Top 10 vulnerabilities"
      - agent: "SecurityAgent"
        task: "Audit authentication and authorization flows"
      - agent: "SecurityAgent"
        task: "Review dependencies for CVEs (Snyk/OWASP DC)"
      - agent: "DatabaseAgent"
        task: "Check for SQL injection risks"
      - agent: "CodeGenAgent"
        task: "Implement security fixes and patches"
      - agent: "TestingAgent"
        task: "Add security regression tests"
      - agent: "DocumentationAgent"
        task: "Document security findings and resolutions"

  api_versioning:
    description: "API versioning and backward compatibility"
    steps:
      - agent: "ArchitectAgent"
        task: "Design versioning strategy (URL, header, or content negotiation)"
      - agent: "CodeGenAgent"
        task: "Implement versioned endpoints"
      - agent: "TestingAgent"
        task: "Test backward compatibility"
      - agent: "DocumentationAgent"
        task: "Update OpenAPI specs for all versions"
      - agent: "ReviewAgent"
        task: "Review breaking changes impact"

  database_migration:
    description: "Database schema migration workflow"
    steps:
      - agent: "DatabaseAgent"
        task: "Design migration scripts (Flyway/Liquibase)"
      - agent: "DatabaseAgent"
        task: "Plan rollback strategy"
      - agent: "ArchitectAgent"
        task: "Review data migration impact"
      - agent: "CodeGenAgent"
        task: "Update JPA entities and repositories"
      - agent: "TestingAgent"
        task: "Test migration with production-like data"
      - agent: "DevOpsAgent"
        task: "Plan zero-downtime deployment"
      - agent: "DocumentationAgent"
        task: "Document migration steps and rollback procedure"

  dependency_update:
    description: "Update and migrate dependencies safely"
    steps:
      - agent: "SecurityAgent"
        task: "Audit current dependencies for vulnerabilities"
      - agent: "ArchitectAgent"
        task: "Assess breaking changes and compatibility"
      - agent: "CodeGenAgent"
        task: "Update Spring Boot and related dependencies"
      - agent: "TestingAgent"
        task: "Run full test suite for regressions"
      - agent: "PerformanceAgent"
        task: "Validate startup time and performance"
      - agent: "DevOpsAgent"
        task: "Update CI/CD pipelines if required"
      - agent: "DocumentationAgent"
        task: "Update version changelog"

  microservice_extraction:
    description: "Extract module into separate microservice"
    steps:
      - agent: "ArchitectAgent"
        task: "Define service boundaries and contracts"
      - agent: "ArchitectAgent"
        task: "Design inter-service communication (REST, events)"
      - agent: "DatabaseAgent"
        task: "Plan data separation strategy"
      - agent: "CodeGenAgent"
        task: "Implement new service with API contracts"
      - agent: "SecurityAgent"
        task: "Configure service-to-service authentication"
      - agent: "DevOpsAgent"
        task: "Set up deployment and service discovery"
      - agent: "TestingAgent"
        task: "Create contract and integration tests"
      - agent: "DocumentationAgent"
        task: "Document service architecture and APIs"

  event_driven_implementation:
    description: "Implement event-driven communication"
    steps:
      - agent: "ArchitectAgent"
        task: "Design event schemas and topic structure"
      - agent: "CodeGenAgent"
        task: "Implement event publishers and listeners"
      - agent: "DatabaseAgent"
        task: "Configure outbox pattern if needed"
      - agent: "TestingAgent"
        task: "Test event handling and idempotency"
      - agent: "PerformanceAgent"
        task: "Load test event processing"
      - agent: "DevOpsAgent"
        task: "Configure message broker (Kafka, RabbitMQ)"
      - agent: "DocumentationAgent"
        task: "Document event catalog and contracts"

  code_review:
    description: "Comprehensive code review workflow"
    steps:
      - agent: "ArchitectAgent"
        task: "Review architectural decisions and patterns"
      - agent: "ReviewAgent"
        task: "Review SOLID principles and clean code"
      - agent: "SecurityAgent"
        task: "Security code review"
      - agent: "PerformanceAgent"
        task: "Performance implications review"
      - agent: "DatabaseAgent"
        task: "Review JPA entities and query efficiency"
      - agent: "TestingAgent"
        task: "Test coverage and quality review"

  incident_response:
    description: "Production incident investigation and resolution"
    steps:
      - agent: "DebuggingAgent"
        task: "Analyze logs and metrics for root cause"
      - agent: "PerformanceAgent"
        task: "Check for resource exhaustion or bottlenecks"
      - agent: "DatabaseAgent"
        task: "Investigate database-related issues"
      - agent: "CodeGenAgent"
        task: "Implement hotfix"
      - agent: "TestingAgent"
        task: "Create regression tests"
      - agent: "DevOpsAgent"
        task: "Deploy hotfix with rollback plan"
      - agent: "DocumentationAgent"
        task: "Document incident postmortem"

  observability_setup:
    description: "Implement comprehensive observability"
    steps:
      - agent: "DevOpsAgent"
        task: "Set up metrics collection (Micrometer/Prometheus)"
      - agent: "DevOpsAgent"
        task: "Configure distributed tracing (Zipkin/Jaeger)"
      - agent: "DevOpsAgent"
        task: "Set up centralized logging (ELK)"
      - agent: "CodeGenAgent"
        task: "Add custom metrics and tracing spans"
      - agent: "PerformanceAgent"
        task: "Define SLIs, SLOs, and alerts"
      - agent: "DocumentationAgent"
        task: "Document runbook and alerting procedures"

  major_version_migration:
    description: "Major version upgrade (e.g., Spring Boot, Java)"
    steps:
      - agent: "ArchitectAgent"
        task: "Analyze breaking changes and migration path"
      - agent: "SecurityAgent"
        task: "Review security changes in new version"
      - agent: "CodeGenAgent"
        task: "Migrate deprecated APIs and patterns"
      - agent: "DatabaseAgent"
        task: "Update JPA/Hibernate configurations"
      - agent: "TestingAgent"
        task: "Comprehensive regression testing"
      - agent: "PerformanceAgent"
        task: "Benchmark before/after performance"
      - agent: "DevOpsAgent"
        task: "Update build and deployment configurations"
      - agent: "DocumentationAgent"
        task: "Document migration guide and changelog"

# Best Practices Configuration
best_practices:
  code_style:
    - "Use constructor injection over field injection"
    - "Prefer immutability (final fields, immutable collections)"
    - "Use Optional for nullable return types"
    - "Avoid returning null, use Optional or empty collections"
    - "Follow single responsibility principle"
    
  spring_boot:
    - "Use @RestController instead of @Controller + @ResponseBody"
    - "Leverage Spring Boot auto-configuration"
    - "Use @ConfigurationProperties for type-safe configuration"
    - "Implement proper exception handling with @ControllerAdvice"
    - "Use DTOs to avoid exposing domain entities"
    - "Enable actuator for production-ready features"
    
  database:
    - "Always use database migrations (Flyway/Liquibase)"
    - "Index foreign keys"
    - "Use @EntityGraph to prevent N+1 queries"
    - "Implement optimistic locking for concurrent updates"
    - "Use connection pooling (HikariCP)"
    
  security:
    - "Never store passwords in plain text"
    - "Use parameterized queries to prevent SQL injection"
    - "Implement proper CORS configuration"
    - "Enable HTTPS in production"
    - "Use environment variables for secrets"
    - "Implement proper authorization checks"
    
  testing:
    - "Write tests before fixing bugs"
    - "Use TestContainers for integration tests"
    - "Mock external dependencies"
    - "Test edge cases and error scenarios"
    - "Maintain test independence"
    - "Aim for high test coverage (80%+)"
    
  performance:
    - "Implement caching for frequently accessed data"
    - "Use pagination for large datasets"
    - "Enable HTTP compression"
    - "Optimize database queries"
    - "Use async processing for long-running tasks"
    - "Monitor application metrics"

# Integration with Development Tools
tool_integration:
  ide:
    - name: "IntelliJ IDEA"
      plugins:
        - "Spring Boot"
        - "Lombok"
        - "SonarLint"
    - name: "VS Code"
      extensions:
        - "Spring Boot Extension Pack"
        - "Java Extension Pack"
  
  code_quality:
    - "SonarQube"
    - "Checkstyle"
    - "SpotBugs"
    - "PMD"
  
  monitoring:
    - "Prometheus"
    - "Grafana"
    - "Zipkin/Jaeger"
    - "ELK Stack"

# Usage Examples
usage_examples:
  example_1:
    scenario: "Generate a new REST controller"
    agent: "CodeGenAgent"
    input: "Generate REST controller for User entity with CRUD operations"
    expected_output: "Complete controller with all endpoints, validation, error handling"
  
  example_2:
    scenario: "Review security of authentication code"
    agent: "SecurityAgent"
    input: "Review JWT authentication implementation"
    expected_output: "Security analysis with vulnerabilities and recommendations"
  
  example_3:
    scenario: "Optimize slow API endpoint"
    agent: "PerformanceAgent"
    input: "Endpoint response time is 5s, expected < 500ms"
    expected_output: "Performance analysis with specific optimization recommendations"

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
      @ArchitectAgent @CodeGenAgent @DatabaseAgent

      Execute workflow: new_feature_development

      Feature: Order Management Module
      Domain: E-commerce
      
      Requirements:
      - CRUD for orders
      - Order status workflow (pending → confirmed → shipped → delivered)
      - Integration with inventory service via events
      - Pagination and filtering

      Entities: Order, OrderItem, OrderStatus
      Relationships: Order 1:N OrderItem, Order N:1 Customer

  # =========================================================
  # Vulnerability Detection
  # =========================================================
  vulnerability_detection_example:
    workflow: "vulnerability_detection"
    prompt: |
      @SecurityAgent @DatabaseAgent

      Execute workflow: vulnerability_detection

      Scope: Payment processing module
      Files: /src/main/java/com/app/modules/payment/**

      Check for:
      - SQL injection in dynamic queries
      - Sensitive data logging
      - JWT validation weaknesses
      - Dependency CVEs (Spring Security, Hibernate)
      - PCI-DSS compliance issues

  # =========================================================
  # Code Refactoring
  # =========================================================
  code_refactoring_example:
    workflow: "code_refactoring"
    prompt: |
      @ReviewAgent @CodeGenAgent @ArchitectAgent

      Execute workflow: code_refactoring

      Target: UserService class (800 lines)
      
      Current problems:
      - Violates Single Responsibility Principle
      - Business logic mixed with validation
      - Hardcoded values
      - No clear domain boundaries

      Refactor to:
      - Separate services (UserAuthService, UserProfileService, UserValidationService)
      - Extract domain events
      - Use strategy pattern for user types

  # =========================================================
  # Bug Fixing
  # =========================================================
  bug_fixing_example:
    workflow: "bug_fixing"
    prompt: |
      @DebuggingAgent @CodeGenAgent @TestingAgent

      Execute workflow: bug_fixing

      Bug: Orders API returns 500 on concurrent requests

      Error log:
      org.hibernate.StaleObjectStateException: Row was updated or deleted by another transaction

      Context:
      - Happens during flash sales
      - Multiple users updating same order
      - Using @Version for optimistic locking

      Affected endpoint: PUT /api/v1/orders/{id}/status

  # =========================================================
  # Performance Optimization
  # =========================================================
  performance_optimization_example:
    workflow: "performance_optimization"
    prompt: |
      @PerformanceAgent @DatabaseAgent @CodeGenAgent

      Execute workflow: performance_optimization

      Issue: Product listing API is slow (5s response time)

      Current metrics:
      - Average response: 5.2s
      - Database queries: 47 per request (N+1 problem)
      - Memory usage: 2GB heap

      Target:
      - Response time: < 200ms
      - Single optimized query
      - Implement caching

      Endpoint: GET /api/v1/products?category={id}&page={n}

  # =========================================================
  # Security Audit
  # =========================================================
  security_audit_example:
    workflow: "security_audit"
    prompt: |
      @SecurityAgent @ReviewAgent @TestingAgent

      Execute workflow: security_audit

      Scope: Full application security review
      
      Focus areas:
      - Authentication (JWT implementation)
      - Authorization (RBAC)
      - API security
      - Data encryption
      - Dependency vulnerabilities

      Compliance: OWASP Top 10, SOC 2

  # =========================================================
  # Database Migration
  # =========================================================
  database_migration_example:
    workflow: "database_migration"
    prompt: |
      @DatabaseAgent @ArchitectAgent @DevOpsAgent

      Execute workflow: database_migration

      Migration: Add multi-tenancy support

      Changes:
      - Add tenant_id column to all tables
      - Create tenant table
      - Update indexes for tenant queries
      - Modify JPA entities with @TenantId

      Requirements:
      - Zero-downtime migration
      - Rollback plan
      - Data migration script for existing records
      - Performance impact analysis

  # =========================================================
  # Microservice Extraction
  # =========================================================
  microservice_extraction_example:
    workflow: "microservice_extraction"
    prompt: |
      @ArchitectAgent @CodeGenAgent @DevOpsAgent

      Execute workflow: microservice_extraction

      Extract: Notification module from monolith

      Current location: /src/main/java/com/app/modules/notification

      Requirements:
      - Email, SMS, Push notification support
      - Event-driven (listen to OrderCreated, UserRegistered events)
      - Independent database
      - Rate limiting
      - Retry mechanism with dead letter queue

      Communication: Kafka events
      Database: MongoDB for notification logs

  # =========================================================
  # Event-Driven Implementation
  # =========================================================
  event_driven_example:
    workflow: "event_driven_implementation"
    prompt: |
      @ArchitectAgent @CodeGenAgent @DevOpsAgent

      Execute workflow: event_driven_implementation

      Feature: Async order processing pipeline

      Events to implement:
      - OrderCreatedEvent → Inventory reservation
      - PaymentCompletedEvent → Order confirmation
      - OrderShippedEvent → Customer notification

      Requirements:
      - Kafka as message broker
      - Outbox pattern for reliability
      - Idempotent consumers
      - Dead letter queue for failures

  # =========================================================
  # Incident Response
  # =========================================================
  incident_response_example:
    workflow: "incident_response"
    prompt: |
      @DebuggingAgent @PerformanceAgent @DevOpsAgent

      Execute workflow: incident_response

      Incident: Production API returning 503 errors

      Symptoms:
      - Started at 14:30 UTC
      - 40% of requests failing
      - Database connection pool exhausted
      - CPU at 95%

      Logs attached: [error logs]
      Metrics: [Grafana dashboard link]

      Priority: P1 - Customer impacting

  # =========================================================
  # Dependency Update
  # =========================================================
  dependency_update_example:
    workflow: "dependency_update"
    prompt: |
      @SecurityAgent @ArchitectAgent @TestingAgent

      Execute workflow: dependency_update

      Updates required:
      - Spring Boot 3.2 → 3.4
      - Java 17 → 21
      - Hibernate 6.2 → 6.4

      Requirements:
      - Identify breaking changes
      - Update deprecated APIs
      - Leverage new features (virtual threads)
      - Full regression testing

  # =========================================================
  # Major Version Migration
  # =========================================================
  major_version_migration_example:
    workflow: "major_version_migration"
    prompt: |
      @ArchitectAgent @CodeGenAgent @SecurityAgent @TestingAgent

      Execute workflow: major_version_migration

      Migration: Spring Boot 2.7 → Spring Boot 3.4

      Current state:
      - Java 11
      - javax.* packages
      - Spring Security 5.x
      - Legacy configuration

      Target state:
      - Java 21 with virtual threads
      - jakarta.* packages
      - Spring Security 6.x
      - Modern configuration

      Constraints:
      - Zero downtime
      - Incremental migration
      - Rollback capability

  # =========================================================
  # Code Review
  # =========================================================
  code_review_example:
    workflow: "code_review"
    prompt: |
      @ArchitectAgent @ReviewAgent @SecurityAgent @PerformanceAgent

      Execute workflow: code_review

      Pull Request: feat/payment-gateway-integration
      
      Files changed:
      - src/main/java/com/app/modules/payment/**
      - src/main/java/com/app/core/event/**

      Review focus:
      - SOLID principles compliance
      - Security (PCI-DSS considerations)
      - Performance implications
      - Test coverage
      - Event-driven patterns

  # =========================================================
  # Observability Setup
  # =========================================================
  observability_setup_example:
    workflow: "observability_setup"
    prompt: |
      @DevOpsAgent @PerformanceAgent @DocumentationAgent

      Execute workflow: observability_setup

      Requirements:
      - Metrics: Micrometer + Prometheus
      - Tracing: OpenTelemetry + Jaeger
      - Logging: Structured JSON + ELK
      - Dashboards: Grafana

      SLOs to track:
      - API latency p99 < 500ms
      - Error rate < 0.1%
      - Availability 99.9%

      Alerts needed:
      - High error rate
      - Latency degradation
      - Resource exhaustion

  # =========================================================
  # Deployment Preparation
  # =========================================================
  deployment_preparation_example:
    workflow: "deployment_preparation"
    prompt: |
      @TestingAgent @SecurityAgent @DevOpsAgent

      Execute workflow: deployment_preparation

      Release: v2.5.0
      
      Checklist:
      - Run full test suite
      - Security scan (OWASP, Snyk)
      - Load testing (1000 concurrent users)
      - Database migration validation
      - Rollback procedure

      Deployment target: AWS EKS
      Strategy: Blue-green deployment