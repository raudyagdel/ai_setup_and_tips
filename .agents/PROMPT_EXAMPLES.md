# Prompt Examples - Real-World Scenarios

> Practical examples showing how to use each agent with real-world scenarios. Copy and adapt for your projects.

---

## Table of Contents

### Backend Agent Examples

1. [Architecture Agent Examples](#1-architecture-agent-examples)
2. [Code Generation Agent Examples](#2-code-generation-agent-examples)
3. [Testing Agent Examples](#3-testing-agent-examples)
4. [Security Agent Examples](#4-security-agent-examples)
5. [Performance Agent Examples](#5-performance-agent-examples)
6. [Database Agent Examples](#6-database-agent-examples)
7. [DevOps Agent Examples](#7-devops-agent-examples)
8. [Documentation Agent Examples](#8-documentation-agent-examples)
9. [Review Agent Examples](#9-review-agent-examples)
10. [Debugging Agent Examples](#10-debugging-agent-examples)
11. [Software Analyst Agent Examples](#11-software-analyst-agent-examples)
12. [Multi-Agent Workflow Examples](#12-multi-agent-workflow-examples)

### Frontend Agent Examples

13. [Frontend Architecture Agent Examples](#13-frontend-architecture-agent-examples)
14. [Angular Agent Examples](#14-angular-agent-examples)
15. [Tailwind Agent Examples](#15-tailwind-agent-examples)
16. [UX & Accessibility Agent Examples](#16-ux--accessibility-agent-examples)
17. [State Management Agent Examples](#17-state-management-agent-examples)
18. [Frontend Testing Agent Examples](#18-frontend-testing-agent-examples)
19. [Icons & Animations Agent Examples](#19-icons--animations-agent-examples)
20. [Frontend Multi-Agent Workflow Examples](#20-frontend-multi-agent-workflow-examples)

---

## 1. Architecture Agent Examples

### Example: E-commerce Microservices Design

```markdown
@ArchitectAgent

I need architectural guidance for an e-commerce platform.

**Requirements:**
- Product catalog with search functionality
- Shopping cart and checkout
- Order management and tracking
- User authentication and profiles
- Payment processing (multiple gateways)
- Inventory management
- 10,000 concurrent users expected

**Constraints:**
- Must integrate with existing ERP system via REST
- PCI DSS compliance required for payments
- Maximum 200ms response time for product search
- Budget for AWS infrastructure

**Please provide:**
- Architecture design with diagrams (PlantUML/C4)
- Component interactions
- Trade-off analysis
- ADR (Architecture Decision Record)
```

### Example: Event-Driven Architecture

```markdown
@ArchitectAgent

## Design Event-Driven Order Processing

**Domain:** Order fulfillment system

**Business Capabilities:**
1. Order placement and validation
2. Payment processing
3. Inventory reservation
4. Shipping coordination
5. Notification dispatch

**Current State:** Synchronous REST calls between services causing timeout issues

**Please provide:**
1. Event-driven architecture proposal
2. Event schema definitions
3. Message broker selection (Kafka vs RabbitMQ)
4. Saga pattern for distributed transactions
5. Event sourcing considerations
6. Monitoring and observability strategy
```

---

## 2. Code Generation Agent Examples

### Example: User Management CRUD

```markdown
@CodeGenAgent

## Generate Complete CRUD for Entity

**Entity Name:** User

**Fields:**
| Field | Type | Constraints |
|-------|------|-------------|
| id | Long | Primary Key, Auto-generated |
| email | String | Unique, Not Null, Email format |
| firstName | String | Not Null, Max 50 chars |
| lastName | String | Not Null, Max 50 chars |
| password | String | Not Null, Min 8 chars |
| status | Enum | ACTIVE, INACTIVE, PENDING |
| createdAt | LocalDateTime | Auto-generated |
| updatedAt | LocalDateTime | Auto-updated |

**Relationships:**
- One User has many Orders
- Many Users belong to many Roles

**Generate:**
1. Entity with JPA annotations
2. DTO (CreateUserRequest, UpdateUserRequest, UserResponse)
3. Mapper (MapStruct)
4. Repository with custom queries (findByEmail, findByStatus)
5. Service interface and implementation
6. REST Controller with all CRUD endpoints
7. Exception handling (UserNotFoundException, DuplicateEmailException)
```

### Example: REST Controller with Pagination

```markdown
@CodeGenAgent

Generate a REST controller for Product entity with:

**Requirements:**
- Full CRUD operations
- Pagination and sorting for list endpoint
- Search by name and category
- Filter by price range
- Include stock information

**Validation Rules:**
- Name: required, 3-100 characters
- Price: required, positive, max 2 decimal places
- SKU: required, unique, alphanumeric
- Category: required, must exist in database

**Java 21 Features:** Use records for DTOs, pattern matching where applicable.

Include proper response codes, validation messages, and OpenAPI annotations.
```

---

## 3. Testing Agent Examples

### Example: Service Layer Tests

```markdown
@TestingAgent

Generate comprehensive tests for OrderService:

**Class Under Test:**
```java
@Service
@RequiredArgsConstructor
public class OrderServiceImpl implements OrderService {
    private final OrderRepository orderRepository;
    private final ProductService productService;
    private final PaymentService paymentService;
    private final NotificationService notificationService;
    
    public Order createOrder(CreateOrderRequest request) { ... }
    public Order getOrder(Long id) { ... }
    public List<Order> getOrdersByUser(Long userId) { ... }
    public Order cancelOrder(Long id) { ... }
}
```

**Requirements:**
- Unit tests covering all methods
- Edge cases: empty cart, insufficient stock, payment failure
- Exception scenarios: order not found, already cancelled

**Mocking Strategy:**
- Mock all repository and external service dependencies
- Use ArgumentCaptor to verify notification calls

Use BDD style (given-when-then) and ensure test independence.
```

### Example: Integration Test with TestContainers

```markdown
@TestingAgent

## Generate Integration Test

**Service/Controller:** OrderController

**Database:** PostgreSQL

**External Dependencies:**
- PaymentService (mock with WireMock)
- NotificationService (mock)

**Generate:**
1. TestContainers setup with PostgreSQL
2. Test data builders for Order, User, Product
3. Integration test scenarios:
   - Create order successfully
   - Create order with invalid data (validation errors)
   - Get order by ID (found and not found)
   - Cancel order (success and already cancelled)
4. WireMock configuration for payment API
5. Cleanup strategies (@Transactional rollback)
```

---

## 4. Security Agent Examples

### Example: Authentication Code Review

```markdown
@SecurityAgent

Review this authentication code for security vulnerabilities:

```java
@RestController
@RequestMapping("/api/auth")
public class AuthController {
    
    @PostMapping("/login")
    public ResponseEntity<TokenResponse> login(@RequestBody LoginRequest request) {
        User user = userRepository.findByEmail(request.getEmail());
        if (user != null && user.getPassword().equals(request.getPassword())) {
            String token = jwtService.generateToken(user);
            return ResponseEntity.ok(new TokenResponse(token));
        }
        return ResponseEntity.status(401).body(null);
    }
    
    @PostMapping("/register")
    public ResponseEntity<User> register(@RequestBody RegisterRequest request) {
        User user = new User();
        user.setEmail(request.getEmail());
        user.setPassword(request.getPassword());
        return ResponseEntity.ok(userRepository.save(user));
    }
}
```

**Check for:**
- SQL injection
- Password handling issues
- Authentication bypass
- Information disclosure
- OWASP Top 10 vulnerabilities

**Provide:**
- Vulnerability report with severity
- Secure alternatives with code examples
- Best practices recommendations
```

### Example: Implement JWT Security

```markdown
@SecurityAgent

## Implement JWT Authentication System

**Type:** JWT with refresh tokens

**Requirements:**
- Access token expiration: 15 minutes
- Refresh token expiration: 7 days
- Token blacklisting on logout
- Rate limiting on auth endpoints
- Account lockout after 5 failed attempts

**Roles:** ADMIN, MANAGER, USER, GUEST

**Generate:**
1. Security configuration (SecurityFilterChain)
2. JWT authentication filter
3. JWT token service (generate, validate, refresh)
4. User details service
5. Password encoding (BCrypt)
6. Rate limiting configuration
7. Account lockout mechanism
```

---

## 5. Performance Agent Examples

### Example: Slow API Analysis

```markdown
@PerformanceAgent

Analyze performance of ProductSearchController:

**Current Metrics:**
- Average response time: 4.5 seconds
- P99 response time: 12 seconds
- Database queries per request: 47
- Memory usage spike during search

**Issues Observed:**
- N+1 queries when loading product categories
- Full table scan on search queries
- No caching implemented
- Large response payloads (including all product details)

**Provide optimization recommendations with:**
1. Root cause analysis
2. Code improvements (with examples)
3. Configuration changes
4. Expected performance gains
5. Monitoring recommendations
```

### Example: Database Query Optimization

```markdown
@PerformanceAgent

## Optimize Database Queries

**Problematic Query/Method:**
```java
public List<Order> getOrdersWithDetails(Long userId) {
    List<Order> orders = orderRepository.findByUserId(userId);
    for (Order order : orders) {
        order.getItems().size(); // Force load
        for (OrderItem item : order.getItems()) {
            item.getProduct().getName(); // Force load
        }
    }
    return orders;
}
```

**Current Performance:**
- Response time: 3.2 seconds
- Records processed: ~500 orders, ~5000 items

**Analyze and provide:**
1. Query execution plan analysis
2. Index recommendations
3. Query rewrite with @EntityGraph or JOIN FETCH
4. Pagination implementation
5. Caching opportunities (product data)
```

---

## 6. Database Agent Examples

### Example: E-commerce Schema Design

```markdown
@DatabaseAgent

Design database schema for e-commerce order management:

**Entities:**
- Order (id, userId, status, totalAmount, createdAt)
- OrderItem (id, orderId, productId, quantity, price)
- Product (id, name, description, price, stock)
- Category (id, name, parentId)
- User (id, email, name, addresses)
- Address (id, userId, type, street, city, country)

**Relationships:**
- Order has many OrderItems
- OrderItem belongs to Product
- Product belongs to many Categories
- User has many Addresses
- User has many Orders

**Scale:**
- 1 million products
- 10 million orders per year
- 5 million users

**Provide:**
1. Schema DDL (PostgreSQL)
2. Indexing strategy for common queries
3. JPA entities with proper annotations
4. Flyway migration V1__initial_schema.sql
5. Partitioning strategy for orders table
```

### Example: Add Audit Fields Migration

```markdown
@DatabaseAgent

## Generate Database Migration

**Change Type:** ADD_COLUMNS

**Description:**
Add audit fields to all main entities for tracking changes

**Target Table(s):** orders, products, users

**New Columns:**
- created_by (VARCHAR 100)
- created_at (TIMESTAMP, default NOW())
- updated_by (VARCHAR 100)
- updated_at (TIMESTAMP)
- version (INTEGER, default 0)

**Generate:**
1. Flyway migration script (V5__add_audit_fields.sql)
2. Rollback script
3. Updated JPA entity with @CreatedBy, @LastModifiedBy, @Version
4. AuditingEntityListener configuration
```

---

## 7. DevOps Agent Examples

### Example: Kubernetes Deployment

```markdown
@DevOpsAgent

Create deployment configuration for order-service:

**Platform:** Kubernetes (AWS EKS)

**Requirements:**
- 3 replicas minimum, auto-scale to 10
- Health checks (liveness, readiness)
- Resource limits (512Mi memory, 500m CPU)
- ConfigMaps for environment config
- Secrets for database credentials
- Ingress with TLS
- HPA based on CPU and custom metrics

**Provide:**
1. Dockerfile (multi-stage build with JDK 21)
2. Kubernetes manifests:
   - Deployment
   - Service
   - ConfigMap
   - Secret (template)
   - HPA
   - Ingress
3. Helm chart structure (optional)
4. GitHub Actions workflow for EKS deployment
```

### Example: GitHub Actions CI/CD

```markdown
@DevOpsAgent

## Generate CI/CD Pipeline

**Repository:** GitHub

**Build Tool:** Gradle 8.5

**Stages Required:**
- [x] Build with Java 21
- [x] Unit Tests with coverage report
- [x] Integration Tests with TestContainers
- [x] SonarQube analysis
- [x] OWASP dependency check
- [x] Docker build and push to ECR
- [x] Deploy to staging (on develop branch)
- [x] Deploy to production (on main with approval)

**Generate complete GitHub Actions workflow with:**
- Caching for Gradle dependencies
- Parallel test execution
- Coverage reporting to Codecov
- Slack notifications on failure
```

---

## 8. Documentation Agent Examples

### Example: REST API Documentation

```markdown
@DocumentationAgent

Generate OpenAPI documentation for Order API:

**Service:** order-service

**Endpoints:**
| Method | Path | Description |
|--------|------|-------------|
| POST | /api/v1/orders | Create new order |
| GET | /api/v1/orders/{id} | Get order by ID |
| GET | /api/v1/orders | List orders with pagination |
| PUT | /api/v1/orders/{id}/cancel | Cancel order |
| GET | /api/v1/orders/{id}/items | Get order items |

**Generate:**
1. Complete OpenAPI 3.0 specification
2. Request/Response schemas with examples
3. Error responses (400, 401, 403, 404, 500)
4. Authentication requirements (Bearer token)
5. Rate limiting headers
6. Pagination parameters
```

### Example: Service README

```markdown
@DocumentationAgent

Generate comprehensive README for order-service:

**Type:** README.md

**Audience:** developers joining the team

**Include:**
1. Service overview and purpose
2. Architecture diagram
3. Prerequisites (Java 21, Docker, etc.)
4. Local development setup
5. Running with Docker Compose
6. API documentation link
7. Configuration options (environment variables)
8. Testing instructions
9. Deployment process
10. Troubleshooting common issues
11. Contributing guidelines
```

---

## 9. Review Agent Examples

### Example: Service Layer Review

```markdown
@ReviewAgent

Review this order service implementation:

```java
@Service
public class OrderServiceImpl implements OrderService {
    
    @Autowired
    private OrderRepository repo;
    
    @Autowired
    private ProductService productService;
    
    public Order createOrder(OrderRequest req) {
        Order order = new Order();
        order.setUserId(req.getUserId());
        order.setStatus("PENDING");
        
        double total = 0;
        for (ItemRequest item : req.getItems()) {
            Product p = productService.getProduct(item.getProductId());
            if (p.getStock() < item.getQuantity()) {
                throw new RuntimeException("Not enough stock");
            }
            total += p.getPrice() * item.getQuantity();
            // Update stock
            p.setStock(p.getStock() - item.getQuantity());
            productService.save(p);
        }
        
        order.setTotal(total);
        return repo.save(order);
    }
}
```

**Analyze for:**
- SOLID principles compliance
- Design patterns usage
- Spring Boot best practices
- Transaction management
- Error handling
- Testability

**Provide:**
- Specific refactoring recommendations
- Code examples for improvements
- Priority of changes (critical/important/nice-to-have)
```

---

## 10. Debugging Agent Examples

### Example: Transaction Deadlock

```markdown
@DebuggingAgent

Debug this issue:

**Problem:**
Intermittent deadlocks occurring during order processing, causing transactions to timeout

**Error Logs:**
```
2024-01-15 14:23:45 ERROR [order-service] - org.springframework.dao.DeadlockLoserDataAccessException: 
PreparedStatementCallback; SQL [UPDATE products SET stock = ? WHERE id = ?]; 
Deadlock found when trying to get lock; try restarting transaction
```

**Stack Trace:**
```
at org.springframework.jdbc.support.SQLErrorCodeSQLExceptionTranslator.doTranslate
at com.example.service.OrderServiceImpl.createOrder(OrderServiceImpl.java:45)
at com.example.controller.OrderController.create(OrderController.java:28)
```

**Context:**
- High concurrency: 500+ orders per minute
- Multiple services updating same products
- PostgreSQL database with default isolation level

**Provide:**
1. Root cause analysis
2. Step-by-step debugging approach
3. Solution with code examples
4. Prevention recommendations
```

### Example: Memory Leak Investigation

```markdown
@DebuggingAgent

## Investigate Memory Issue

**Symptoms:**
- Heap usage grows from 512MB to 2GB over 6 hours
- Eventually OOM error and pod restart
- No obvious memory-intensive operations

**Heap Dump Analysis:**
- Large number of ProductDTO instances (2 million+)
- HashMap with growing entries
- StringBuilder instances not being released

**Suspect Areas:**
- Product caching mechanism
- Response serialization
- Batch processing jobs

**Provide:**
1. Memory leak identification strategy
2. Code fixes for common patterns
3. JVM tuning recommendations (G1GC settings)
4. Monitoring setup (Prometheus metrics for heap)
```

---

## 11. Software Analyst Agent Examples

### Example: Multi-Payment Gateway Feature

```markdown
@SoftwareAnalystAgent

Analyze the following feature request:

**Feature:** Multi-payment Gateway Support

**Business Context:** 
We need to support multiple payment providers (Stripe, PayPal, MercadoPago) to expand to international markets. Currently only supporting a single payment gateway with hardcoded integration.

**Stakeholders:** 
- Product Owner: Maria (defines priorities)
- Finance Team: Juan (compliance requirements)
- Development Team: Backend squad
- Compliance Officer: Carlos (PCI DSS requirements)

**Current System State:** 
Single payment integration with Stripe, hardcoded in PaymentService. No abstraction layer. Payment credentials in application.properties.

**Please provide (using mandatory templates):**
1. Detailed feature breakdown with sub-features
2. User stories following user-story-template.md
3. Functional requirements list with MoSCoW prioritization
4. Non-functional requirements (latency < 2s, 99.9% uptime)
5. Dependencies and integration points
6. Potential risks and mitigation strategies
7. Suggested implementation approach
8. Effort estimation considerations
9. GitHub-ready feature issues
10. Test cases in Gherkin format
```

### Example: Notification System User Stories

```markdown
@SoftwareAnalystAgent

## User Story Creation Request

**Feature/Epic:** Notification System

**High-Level Requirements:**
1. Send email notifications for order events
2. Send push notifications to mobile apps
3. Display in-app notifications
4. Allow users to manage notification preferences
5. Support notification templates with variables
6. Track notification delivery status

**Target Users:**
- Customer: Receives notifications about their orders
- Admin: Manages notification templates and monitors delivery
- System: Triggers automated notifications

**Please create user stories with:**
- Clear user role identification
- Specific, measurable actions
- Clear business value statement
- Acceptance criteria in Gherkin format
- Story point estimation guidance (S/M/L/XL)
- Dependencies between stories
- INVEST criteria validation for each story
```

### Example: Legacy System Analysis

```markdown
@SoftwareAnalystAgent [Senior Functional Analyst Mode]

## Functional Analysis Request

**Business Problem/Need:**
Our 8-year-old monolithic Spring application is becoming difficult to maintain and scale. We need to assess the feasibility of migrating to microservices.

**Domain Context:**
- E-commerce platform with 500K+ lines of code
- PostgreSQL database with 200+ tables
- Handles 50,000 orders daily
- Integrated with 15 external services
- 3 development teams working on same codebase

**Stakeholders:**
- CTO: Strategic decision maker
- Engineering Managers: Team capacity concerns
- Development Teams: Technical implementation
- Operations: Infrastructure and deployment

**Please provide:**
1. Business need investigation summary
2. Current state assessment (technical debt inventory)
3. Service boundary identification
4. Migration risk analysis
5. Recommended migration approach (strangler fig pattern)
6. Phased implementation roadmap
7. Resource requirements estimation
8. Success metrics definition
```

### Example: Document Verification

```markdown
@SoftwareAnalystAgent [Functional Analyst Verifier Mode]

## Documentation Verification Request

**Document to Verify:** User Story - US-PAYMENT-003

**Content:**
```
# User Story: Payment Gateway Selection

As a customer
I want to choose my preferred payment method
So that I can pay using my favorite provider

## Acceptance Criteria
- User can see available payment methods
- User can select a payment method
- Payment is processed

## Business Rules
- Some rules apply
```

**Please verify:**
1. Compliance with official template structure
2. All mandatory sections are complete
3. Business rules are explicit and unambiguous
4. Acceptance criteria are testable and measurable
5. No ambiguous language or hidden assumptions
6. Traceability is maintained
7. INVEST criteria validation

**Provide:**
- Verification status (APPROVED / NEEDS CORRECTION)
- List of issues found
- Specific correction recommendations
```

### Example: Test Case Design

```markdown
@SoftwareAnalystAgent [Senior QA Analyst Mode]

## Test Case Design Request

**Epic:** EPIC-PAYMENT-001 - Multi-Payment Gateway
**User Story:** US-PAYMENT-003 - Payment Gateway Selection

**Acceptance Criteria:**
- AC-01: Given I'm on checkout, when I click "Select Payment", then I see all available payment methods for my country
- AC-02: Given I selected Stripe, when payment succeeds, then order status changes to PAID and I receive confirmation
- AC-03: Given I selected PayPal, when I'm redirected back, then my session is restored with payment status

**Business Rules:**
- BR-01: Payment methods vary by country (Stripe: US/EU, MercadoPago: LATAM)
- BR-02: Minimum order amount for PayPal is $5
- BR-03: Failed payments allow retry up to 3 times

**Please design test cases covering:**
1. Main flows (positive cases)
2. Negative cases (errors, validations, messages)
3. Edge cases (limits, extreme values)
4. Business rules validation
5. Acceptance criteria verification

**Deliverables:**
- Test cases in natural language
- Test cases in Gherkin format
- Traceability matrix
```

---

## 12. Multi-Agent Workflow Examples

### Example: Complete Feature Implementation

```markdown
## New Feature Development Workflow: Wishlist Feature

### Step 1: Analysis
@SoftwareAnalystAgent
Analyze and create documentation for a Wishlist feature where users can save products for later.

### Step 2: Architecture
@ArchitectAgent
Review the user stories and propose the technical architecture for the Wishlist feature.

### Step 3: Database Design
@DatabaseAgent
Design the database schema for Wishlist (tables, indexes, migrations).

### Step 4: Implementation
@CodeGenAgent
Generate the complete CRUD implementation for Wishlist (Entity, Repository, Service, Controller).

### Step 5: Security Review
@SecurityAgent
Review the Wishlist implementation for security vulnerabilities.

### Step 6: Testing
@TestingAgent
Generate comprehensive test suite for Wishlist (unit + integration tests).

### Step 7: Documentation
@DocumentationAgent
Generate API documentation for Wishlist endpoints.

### Step 8: Final Review
@ReviewAgent
Perform final code review of the complete Wishlist implementation.
```

### Example: Bug Fix Workflow

```markdown
## Bug Fix Workflow: Cart Total Calculation Error

### Step 1: Diagnosis
@DebuggingAgent
Bug: Cart total shows incorrect amount when applying percentage discount on items with quantity > 1.
Error: Expected $90, got $81 for 3 items at $30 each with 10% discount.
Investigate root cause.

### Step 2: Fix Implementation
@CodeGenAgent
Based on the root cause (discount applied per item instead of per line), implement the fix in CartCalculationService.

### Step 3: Regression Tests
@TestingAgent
Generate regression tests covering:
- Single item with discount
- Multiple quantity with discount
- Multiple items with different discounts
- Edge cases (0%, 100% discount)

### Step 4: Review
@ReviewAgent
Review the fix and tests for correctness and best practices.
```

### Example: Performance Improvement Workflow

```markdown
## Performance Optimization Workflow: Product Search

### Step 1: Analysis
@PerformanceAgent
Analyze the slow product search endpoint (currently 4s, target <500ms).
Metrics: 47 queries per request, no caching, full table scans.

### Step 2: Database Optimization
@DatabaseAgent
Based on the analysis, create indexes and optimize queries for product search.

### Step 3: Code Optimization
@CodeGenAgent
Implement the recommended optimizations:
- Add Redis caching
- Use @EntityGraph for eager loading
- Implement pagination

### Step 4: Testing
@TestingAgent
Generate performance tests with JMeter/Gatling scenarios.

### Step 5: Documentation
@DocumentationAgent
Update API documentation with new pagination parameters and caching headers.
```

---

## Tips for Using Examples

1. **Replace placeholders** - All `{...}` values must be replaced with actual data
2. **Combine agents** - Complex tasks benefit from multiple agents in sequence
3. **Be specific** - More context = better results
4. **Iterate** - Use follow-up prompts to refine outputs
5. **Verify outputs** - Always review generated code before using

---

# Frontend Agent Examples (Angular / TypeScript)

---

## 13. Frontend Architecture Agent Examples

### Example: E-commerce Product Catalog Frontend

```markdown
@FrontendArchitectAgent

Design frontend architecture for an e-commerce product catalog.

**Requirements:**
- Product listing with infinite scroll
- Product detail pages with image gallery
- Search with filters (category, price, brand)
- Shopping cart sidebar
- User authentication flow
- Wishlist functionality

**Technical Constraints:**
- Angular 17+ with standalone components
- Tailwind CSS for styling
- Must integrate with existing REST API
- Mobile-first responsive design
- Target bundle size < 200KB initial

**Please provide:**
1. Feature module structure
2. Routing configuration with lazy loading
3. Shared vs feature component breakdown
4. State management approach (Signals vs NgRx)
5. API integration patterns
6. Performance considerations
```

### Example: Dashboard Feature Architecture

```markdown
@FrontendArchitectAgent

## Design Admin Dashboard Architecture

**Feature:** Real-time analytics dashboard

**Components Needed:**
1. Metric cards with live updates
2. Interactive charts (line, bar, pie)
3. Data tables with pagination and sorting
4. Date range picker for filtering
5. Export functionality (CSV, PDF)

**Data Sources:**
- REST API for historical data
- WebSocket for real-time updates

**Please provide:**
1. Component hierarchy diagram
2. Smart vs presentational component separation
3. Data flow architecture
4. State management for real-time data
5. Caching strategy for historical data
6. Error boundary implementation
```

---

## 14. Angular Agent Examples

### Example: Product Card Component

```markdown
@AngularAgent @skill angular-components @skill angular-standalone @skill angular-signals

Generate a ProductCard standalone component.

**Requirements:**
- Display product image, name, price, rating
- "Add to Cart" button with loading state
- "Add to Wishlist" toggle
- Responsive design (grid-friendly)
- Accessible for screen readers

**Inputs:**
| Input | Type | Description |
|-------|------|-------------|
| product | Product | Product data object |
| isInWishlist | boolean | Wishlist status |

**Outputs:**
| Output | Type | Description |
|--------|------|-------------|
| addToCart | Product | Emits when add to cart clicked |
| toggleWishlist | Product | Emits when wishlist toggled |

**Generate (using these skills):**
1. Standalone component with OnPush (@skill angular-components)
2. Signals for loading state (@skill angular-signals)
3. Typed inputs and outputs (@skill angular-components, @skill typescript)
4. Template with Tailwind classes (@skill tailwind-4) and HugeIcons (@skill hugeicons-implementation)
5. Accessibility (@skill accessibility-wcag)
6. Unit test file (@skill angular-testing)
```

### Example: Data Table Component

```markdown
@AngularAgent @skill angular-components @skill angular-signals @skill primeng-components

## Generate Reusable Data Table Component

**Component Name:** DataTableComponent

**Features:**
- Generic typing for any data structure
- Column configuration via input
- Sorting (client and server-side)
- Pagination with configurable page sizes
- Row selection (single and multi)
- Loading skeleton state
- Empty state handling

**Column Config Interface:**
```typescript
interface ColumnDef<T> {
  key: keyof T;
  header: string;
  sortable?: boolean;
  template?: TemplateRef<any>;
  width?: string;
}
```

**Generate (using these skills):**
1. Generic standalone component (@skill angular-components)
2. Signals for sort and pagination state (@skill angular-signals)
3. Computed signals for displayed data (@skill angular-signals)
4. Content projection for custom templates (@skill angular-components)
5. PrimeNG Table integration (@skill primeng-components)
6. Keyboard navigation support (@skill accessibility-wcag)
7. Complete test coverage (@skill angular-testing)
```

### Example: Authentication Service

```markdown
@AngularAgent @skill angular-services @skill angular-signals @skill angular-security

## Generate Authentication Service

**Service Name:** AuthService

**Features:**
- Login with email/password
- Token storage (memory, not localStorage)
- Automatic token refresh
- Logout with cleanup
- Current user state with signal
- Auth guard integration

**API Endpoints:**
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /auth/login | Returns access + refresh tokens |
| POST | /auth/refresh | Refresh access token |
| POST | /auth/logout | Invalidate session |
| GET | /auth/me | Get current user |

**Generate (using these skills):**
1. AuthService with HttpClient (@skill angular-services)
2. Token management (in-memory storage) (@skill angular-security)
3. HTTP interceptor for token injection (@skill angular-security)
4. Signal-based auth state (@skill angular-signals)
5. Login/logout methods (@skill angular-services)
6. AuthGuard using canActivate (@skill angular-security, @skill angular-routing)
7. Unit tests with HttpTestingController (@skill angular-testing)
```

---

## 15. Tailwind Agent Examples

### Example: Product Card Styling

```markdown
@TailwindAgent @skill tailwind-4 @skill accessibility-wcag

Style the ProductCard component using Tailwind CSS.

**Design Requirements:**
- Card with subtle shadow and rounded corners
- Image with aspect ratio 4:3
- Price with strikethrough for discounts
- Star rating display
- Hover effect on the entire card
- "Sale" badge overlay
- Dark mode support

**Layout:**
- Mobile: Full width in grid
- Tablet: 2 columns
- Desktop: 4 columns

**Generate:**
1. Complete Tailwind classes for all elements
2. Responsive breakpoints (sm, md, lg)
3. Dark mode variants (dark:)
4. Hover and focus states
5. Transition animations
```

### Example: Dashboard Layout

```markdown
@TailwindAgent

## Create Dashboard Layout with Tailwind

**Layout Requirements:**
- Fixed sidebar (collapsible on mobile)
- Top navigation bar with user menu
- Main content area with padding
- Breadcrumb navigation
- Footer (optional, sticky bottom)

**Sidebar:**
- Logo at top
- Navigation links with icons
- Active state indicator
- Collapse to icons only on tablet

**Color Scheme:**
- Sidebar: Dark (slate-900)
- Content: Light (gray-50)
- Accent: Blue (blue-600)

**Generate:**
1. Complete layout structure with Tailwind
2. Responsive behavior for all breakpoints
3. Sidebar collapse/expand animation
4. Mobile hamburger menu
5. Dark mode for entire layout
```

### Example: Form Component Styling

```markdown
@TailwindAgent

## Style Login Form with Tailwind

**Form Elements:**
- Email input with icon
- Password input with show/hide toggle
- "Remember me" checkbox
- Submit button with loading state
- "Forgot password" link
- Social login buttons (Google, GitHub)
- Form validation error messages

**Design Requirements:**
- Centered card on page
- Subtle shadow and border
- Focus rings for accessibility
- Error state styling (red border, message)
- Disabled state for submit button
- Responsive (full width on mobile)

**Generate complete Tailwind styling with all states.**
```

---

## 16. UX & Accessibility Agent Examples

### Example: Form Accessibility Audit

```markdown
@UXAgent

Review this login form for accessibility:

```html
<form>
  <div>
    <input type="email" placeholder="Email">
  </div>
  <div>
    <input type="password" placeholder="Password">
  </div>
  <button type="submit">Login</button>
</form>
```

**Please provide:**
1. WCAG 2.1 AA compliance issues
2. Missing labels and ARIA attributes
3. Keyboard navigation improvements
4. Error handling accessibility
5. Focus management recommendations
6. Screen reader testing notes
7. Fixed code with all improvements
```

### Example: Data Table Accessibility

```markdown
@UXAgent

## Improve Data Table Accessibility

**Current Implementation:**
- Uses div-based table layout
- Sorting via click on headers
- Pagination with number buttons
- Row selection with checkboxes
- No keyboard navigation

**Please provide:**
1. Semantic table markup recommendations
2. ARIA attributes for sortable columns
3. Keyboard navigation pattern
4. Screen reader announcements for:
   - Sort changes
   - Page changes
   - Row selection
5. Focus management for pagination
6. Complete accessible implementation
```

### Example: Modal Dialog Accessibility

```markdown
@UXAgent

## Review Modal Dialog Accessibility

**Modal Features:**
- Opened via button click
- Contains form with inputs
- Close button (X) in corner
- Cancel and Submit buttons
- Backdrop click to close

**Issues to Check:**
1. Focus trap inside modal
2. Escape key to close
3. Return focus to trigger on close
4. ARIA role and labels
5. Background scroll lock
6. Announcement for screen readers

**Provide complete accessible modal pattern with Angular implementation.**
```

---

## 17. State Management Agent Examples

### Example: Shopping Cart State

```markdown
@StateAgent

Design state management for shopping cart feature.

**State Requirements:**
- Cart items (product, quantity)
- Cart totals (subtotal, tax, shipping, total)
- Loading states for add/remove/update
- Error handling
- Persistence to localStorage
- Sync with backend on changes

**Actions:**
- Add item to cart
- Remove item from cart
- Update quantity
- Clear cart
- Apply promo code

**Please provide:**
1. Signal-based cart service
2. Computed signals for derived values (totals)
3. Effect for localStorage persistence
4. Optimistic updates pattern
5. Error recovery strategy
6. Complete TypeScript implementation
```

### Example: Filter State with URL Sync

```markdown
@StateAgent

## Design Filter State with URL Synchronization

**Feature:** Product listing filters

**Filter Options:**
- Category (multi-select)
- Price range (min/max)
- Brand (multi-select)
- Rating (minimum stars)
- Sort by (price, rating, newest)
- Search query

**Requirements:**
- Filters sync to URL query params
- Deep linking support (share filtered URLs)
- Browser back/forward navigation
- Default values when no params
- Debounce search input

**Please provide:**
1. Filter state with signals
2. URL synchronization service
3. Computed signal for active filter count
4. Effect for URL updates
5. Router integration pattern
6. Reset filters functionality
```

---

## 18. Frontend Testing Agent Examples

### Example: Component Tests

```markdown
@FrontendTestingAgent

Generate comprehensive tests for ProductCardComponent.

**Component Behavior:**
- Displays product information (name, price, image)
- Shows discounted price with strikethrough original
- "Add to Cart" button emits event with product
- "Add to Wishlist" toggles state and emits event
- Shows loading spinner when adding to cart
- Handles missing image with placeholder

**Test Scenarios:**
1. Renders product information correctly
2. Shows discount badge and strikethrough price
3. Emits addToCart event on button click
4. Toggles wishlist state and emits event
5. Displays loading state during add to cart
6. Shows placeholder for missing image

**Generate with:**
- Jest test setup
- Angular Testing Library
- User event simulation
- Accessibility checks
```

### Example: E2E Checkout Flow

```markdown
@FrontendTestingAgent

## Generate E2E Tests for Checkout Flow

**Flow Steps:**
1. User views product listing
2. Adds product to cart
3. Opens cart sidebar
4. Proceeds to checkout
5. Fills shipping information
6. Selects payment method
7. Places order
8. Sees confirmation page

**Edge Cases:**
- Empty cart navigation
- Invalid shipping address
- Payment failure
- Session timeout

**Generate with Playwright:**
1. Page object models for each step
2. Happy path test
3. Error handling tests
4. Mobile viewport tests
5. Network failure simulation
6. Screenshot comparisons
```

---

## 19. Icons & Animations Agent Examples

### Example: Navigation Icons

```markdown
@IconsAgent

Implement icons for main navigation sidebar.

**Navigation Items:**
| Item | Icon Name | Active State |
|------|-----------|--------------|
| Dashboard | home-01 | Filled variant |
| Products | shopping-bag-01 | Filled variant |
| Orders | document-01 | Filled variant |
| Customers | users-01 | Filled variant |
| Analytics | chart-line-data-01 | Filled variant |
| Settings | settings-01 | Filled variant |

**Requirements:**
- Use @hugeicons/angular
- Size: 24px (w-6 h-6)
- Color: Use currentColor for theming
- Active state: Different icon variant
- Accessibility: aria-hidden with text labels

**Generate:**
1. Icon imports and configuration
2. Navigation component with icons
3. Active state switching logic
4. Dark mode compatibility
```

### Example: Card Enter Animation

```markdown
@AnimationsAgent

Add enter animations for product grid cards.

**Animation Requirements:**
- Cards fade in and slide up
- Stagger effect (each card delayed)
- Duration: 300ms per card
- Stagger delay: 50ms between cards
- Easing: ease-out
- Respect prefers-reduced-motion

**Generate:**
1. Angular animation trigger definition
2. Stagger animation implementation
3. Reduced motion fallback
4. Usage in product grid component
5. Performance considerations
```

### Example: Modal Animations

```markdown
@AnimationsAgent

## Implement Modal Open/Close Animations

**Modal Animation:**
- Backdrop: Fade in/out (200ms)
- Modal: Scale up from center + fade (300ms)
- Close: Reverse of open
- Easing: ease-out for open, ease-in for close

**Additional Effects:**
- Form elements slide in after modal opens
- Buttons have subtle hover animations

**Generate:**
1. Backdrop animation with CSS
2. Modal animation with @angular/animations
3. Stagger for form elements
4. Close animation trigger
5. prefers-reduced-motion support
```

---

## 20. Frontend Multi-Agent Workflow Examples

### Example: Complete Feature Development

```markdown
## New Feature: User Profile Page

### Step 1: Architecture
@FrontendArchitectAgent
Design the profile feature module with:
- Profile overview component
- Edit profile form
- Avatar upload
- Password change section
- Account settings

### Step 2: Component Generation
@AngularAgent
Generate all components with:
- Standalone components with signals
- Reactive forms for editable sections
- Image upload handling
- Form validation

### Step 3: Styling
@TailwindAgent
Style the profile page with:
- Clean, modern card-based layout
- Responsive design for all screen sizes
- Avatar with upload overlay
- Form styling with validation states

### Step 4: Accessibility
@UXAgent
Audit and fix accessibility:
- Form labels and error messages
- Image upload accessibility
- Focus management for modals
- Screen reader announcements

### Step 5: Testing
@FrontendTestingAgent
Generate complete test suite:
- Component unit tests
- Form validation tests
- E2E tests for profile update flow
```

### Example: Component Library Development

```markdown
## Build Button Component for Design System

### Step 1: Architecture
@FrontendArchitectAgent
Design button component API with variants, sizes, states.

### Step 2: Implementation
@AngularAgent
Generate button component:
- Variants: primary, secondary, outline, ghost, danger
- Sizes: sm, md, lg
- States: default, hover, active, disabled, loading
- Icon support (left, right, icon-only)

### Step 3: Styling
@TailwindAgent
Complete Tailwind styling with:
- All variant styles
- All size configurations
- Hover, focus, active states
- Dark mode variants
- Disabled styling

### Step 4: Icons
@IconsAgent
Add icon support with proper sizing and spacing.

### Step 5: Animations
@AnimationsAgent
Add button interactions:
- Click ripple effect
- Loading spinner animation
- Icon transitions

### Step 6: Documentation
@FrontendDocumentationAgent
Generate Storybook stories for all variants and states.

### Step 7: Testing
@FrontendTestingAgent
Complete test coverage for all variants and interactions.
```

### Example: Performance Optimization

```markdown
## Optimize Product Listing Performance

### Step 1: Performance Analysis
@FrontendPerformanceAgent
Analyze current performance:
- Metrics: LCP 4.2s, FID 180ms, CLS 0.15
- Bundle size: 450KB initial
- Issues: All products loaded at once, no virtual scrolling

### Step 2: Code Optimization
@AngularAgent
Implement optimizations:
- Virtual scrolling for product list
- Image lazy loading with intersection observer
- Component-level code splitting

### Step 3: Bundle Optimization
@FrontendDevOpsAgent
Configure build optimizations:
- Lazy load feature modules
- Tree-shake unused imports
- Configure proper chunk splitting

### Step 4: Testing
@FrontendTestingAgent
Add performance tests:
- Lighthouse CI integration
- Bundle size assertions
- Web Vitals monitoring

### Step 5: Documentation
@FrontendDocumentationAgent
Document performance best practices and results.
```

---

## Tips for Using Examples

1. **Replace placeholders** - All `{...}` values must be replaced with actual data
2. **Combine agents** - Complex tasks benefit from multiple agents in sequence
3. **Be specific** - More context = better results
4. **Iterate** - Use follow-up prompts to refine outputs
5. **Verify outputs** - Always review generated code before using
6. **Frontend + Backend** - Use both agent sets for full-stack development

---

**See also:**
- [PROMPT_TEMPLATES.md](PROMPT_TEMPLATES.md) - Ready-to-use templates
- [PROMPT_TIPS.md](PROMPT_TIPS.md) - Best practices for prompting
- [AGENTS_BACKEND_TEMPLATE.md](AGENTS_BACKEND_TEMPLATE.md) - Backend agent definitions
- [AGENTS_FRONT_TEMPLATE.md](AGENTS_FRONT_TEMPLATE.md) - Frontend agent definitions
