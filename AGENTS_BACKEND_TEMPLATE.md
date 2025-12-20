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