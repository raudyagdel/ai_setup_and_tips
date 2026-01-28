# GitHub Copilot Instructions - Spring Boot Projects

## Project Context
Enterprise-grade Spring Boot application with Modular Monolith architecture and Event-Driven communication patterns.

## Prerequisites
- Java 21 or later (LTS recommended)
- Maven 3.9+ or Gradle 8.5+
- Docker & Docker Compose
- Git
- IDE: IntelliJ IDEA / VS Code with Java extensions

## Technology Stack
- **Spring Boot**: 3.4.x
- **Java**: 21 (with virtual threads support)
- **Database**: PostgreSQL 16 / MySQL 8.0
- **Cache**: Redis 7.x
- **Documentation**: OpenAPI 3.0 (SpringDoc)

## Architecture Pattern
**Modular Monolith** - Organized by business modules, event-driven communication, prepared for microservices extraction

```
src/main/java/com/{company}/
├── core/                           # Shared infrastructure
│   ├── event/                      # Event definitions & bus
│   ├── common/                     # Shared utilities
│   ├── exception/                  # Global exceptions
│   └── config/                     # Global configurations
├── modules/                        # Business modules
│   ├── {domain1}/                  # Business domain 1
│   ├── {domain2}/                  # Business domain 2
│   └── {domainN}/                  # Business domain N
└── Application.java
```

## Module Structure (Each Module)
```
module-name/
├── domain/
│   ├── entity/                     # JPA Entities
│   ├── enums/                      # Domain enums
│   └── event/                      # Module-specific events
├── dto/
│   ├── request/                    # Request DTOs
│   ├── response/                   # Response DTOs
│   └── mapper/                     # MapStruct mappers
├── repository/                     # Spring Data JPA repos
├── service/
│   ├── impl/                       # Service implementations
│   └── [ModuleName]Service.java   # Service interface
├── controller/                     # REST Controllers
├── listener/                       # Event listeners
└── config/                         # Module-specific config
```

## Architecture Diagram

### Modular Monolith + Hexagonal Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           PRESENTATION LAYER                                │
│  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐                   │
│  │ REST Controllers│ │  GraphQL      │  │  WebSocket    │                   │
│  │ (HTTP Adapters) │ │  Resolvers    │  │  Handlers     │                   │
│  └───────┬───────┘  └───────┬───────┘  └───────┬───────┘                   │
└──────────┼──────────────────┼──────────────────┼────────────────────────────┘
           │                  │                  │
           └──────────────────┴──────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            APPLICATION LAYER                                │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐             │
│  │ Service Facades │  │  Use Cases      │  │  Event Handlers │             │
│  │ (Orchestration) │  │  (Business)     │  │  (Listeners)    │             │
│  └────────┬────────┘  └────────┬────────┘  └────────┬────────┘             │
│           │                    │                    │                       │
│  ┌────────┴────────────────────┴────────────────────┴────────┐             │
│  │              DTOs / Mappers / Validators                  │             │
│  └───────────────────────────────────────────────────────────┘             │
└─────────────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                              DOMAIN LAYER                                   │
│  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐│
│  │   Entities    │  │   Value Objs  │  │  Domain Evts  │  │   Enums       ││
│  │   (JPA)       │  │   (Immutable) │  │  (Internal)   │  │   (States)    ││
│  └───────────────┘  └───────────────┘  └───────────────┘  └───────────────┘│
│                                                                             │
│  ┌───────────────────────────────────────────────────────────────────────┐ │
│  │                    Repository Interfaces (Ports)                      │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          INFRASTRUCTURE LAYER                               │
│  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐│
│  │  JPA Repos    │  │  Redis Cache  │  │  Msg Broker   │  │  External     ││
│  │  (Adapters)   │  │  (Adapters)   │  │  (Kafka/RMQ)  │  │  API Clients  ││
│  └───────┬───────┘  └───────┬───────┘  └───────┬───────┘  └───────┬───────┘│
└──────────┼──────────────────┼──────────────────┼──────────────────┼─────────┘
           │                  │                  │                  │
           ▼                  ▼                  ▼                  ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           EXTERNAL SYSTEMS                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  PostgreSQL │  │    Redis    │  │    Kafka    │  │  Third-party│        │
│  │   Database  │  │    Cache    │  │   Broker    │  │    APIs     │        │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘        │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Event-Driven Communication Pattern

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                         MODULE COMMUNICATION                                 │
│                                                                              │
│    ┌────────────┐         EVENT BUS           ┌────────────┐                │
│    │  MODULE A  │                             │  MODULE B  │                │
│    │            │    ┌─────────────────┐      │            │                │
│    │  Service   │───▶│  Domain Event   │───▶  │  Listener  │                │
│    │  (Publish) │    │  (Async/Sync)   │      │  (Handle)  │                │
│    │            │    └─────────────────┘      │            │                │
│    └────────────┘                             └────────────┘                │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     REQUEST → RESPONSE FLOW                         │   │
│   │                                                                     │   │
│   │   Controller ──▶ Service ──▶ Repository ──▶ Entity ──▶ Response     │   │
│   │       ▲             │             │            │           │        │   │
│   │       │             ▼             ▼            ▼           │        │   │
│   │       │        Validation     Database      Mapper         │        │   │
│   │       │                                                    │        │   │
│   │       └────────────────────────────────────────────────────┘        │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

## Code Generation Rules

### 1. ENTITIES
Always generate entities with:
- UUID as @Id with @GeneratedValue(strategy = GenerationType.UUID)
- Audit fields: @CreatedDate, @LastModifiedDate, @CreatedBy, @LastModifiedBy
- Soft delete: Boolean deleted = false
- @EntityListeners(AuditingEntityListener.class)
- Lombok: @Getter, @Setter, @NoArgsConstructor, @AllArgsConstructor, @Builder
- @Version for optimistic locking
- Proper indexes on foreign keys and frequently queried fields
- Table name in snake_case: @Table(name = "table_name")

**Template:**
```java
@Entity
@Table(name = "table_name", indexes = {
    @Index(name = "idx_field", columnList = "field")
})
@EntityListeners(AuditingEntityListener.class)
@Getter @Setter @NoArgsConstructor @AllArgsConstructor @Builder
public class EntityName {
    @Id
    @GeneratedValue(strategy = GenerationType.UUID)
    private UUID id;
    
    // Business fields
    
    @CreatedDate
    @Column(nullable = false, updatable = false)
    private LocalDateTime createdAt;
    
    @LastModifiedDate
    private LocalDateTime updatedAt;
    
    @CreatedBy
    @Column(updatable = false)
    private String createdBy;
    
    @LastModifiedBy
    private String lastModifiedBy;
    
    @Version
    private Long version;
    
    @Column(nullable = false)
    private Boolean deleted = false;
}
```

### 2. DTOs
Always generate:
- **Request DTOs**: With Jakarta validation (@NotNull, @NotBlank, @Email, @Size, @Pattern)
- **Response DTOs**: With @JsonInclude(Include.NON_NULL)
- **Update DTOs**: Partial fields (all optional)
- Use record types for immutable DTOs where appropriate
- Lombok @Data for mutable DTOs
- Swagger/OpenAPI annotations

**Template:**
```java
// Request DTO
@Data
@Schema(description = "Request to create entity")
public class EntityRequestDTO {
    @NotBlank(message = "Field is required")
    @Size(max = 100)
    @Schema(description = "Field description", example = "value")
    private String field;
}

// Response DTO (prefer records)
@Schema(description = "Entity response")
public record EntityResponseDTO(
    @Schema(description = "Unique identifier") UUID id,
    @Schema(description = "Field description") String field,
    LocalDateTime createdAt
) {}
```

### 3. MAPPERS (MapStruct)
Always generate:
- @Mapper(componentModel = "spring", unmappedTargetPolicy = IGNORE)
- Separate methods: toEntity, toResponseDTO, toResponseDTOList
- updateEntityFromDTO with @MappingTarget
- Handle null values properly

**Template:**
```java
@Mapper(componentModel = "spring", 
        unmappedTargetPolicy = ReportingPolicy.IGNORE,
        nullValuePropertyMappingStrategy = NullValuePropertyMappingStrategy.IGNORE)
public interface EntityMapper {
    @Mapping(target = "id", ignore = true)
    @Mapping(target = "createdAt", ignore = true)
    @Mapping(target = "deleted", ignore = true)
    Entity toEntity(EntityRequestDTO dto);
    
    EntityResponseDTO toResponseDTO(Entity entity);
    
    List<EntityResponseDTO> toResponseDTOList(List<Entity> entities);
    
    @BeanMapping(nullValuePropertyMappingStrategy = IGNORE)
    void updateEntityFromDTO(EntityRequestDTO dto, @MappingTarget Entity entity);
}
```

### 4. REPOSITORIES
Always include:
- extends JpaRepository<Entity, UUID>, JpaSpecificationExecutor<Entity>
- Soft delete filter in custom queries: andDeletedFalse()
- Pagination support
- Custom queries with proper naming
- @Query with JPQL or native SQL for complex queries

**Template:**
```java
@Repository
public interface EntityRepository extends JpaRepository<Entity, UUID>, 
                                          JpaSpecificationExecutor<Entity> {
    Optional<Entity> findByFieldAndDeletedFalse(String field);
    
    Page<Entity> findByDeletedFalse(Pageable pageable);
    
    @Query("SELECT e FROM Entity e WHERE e.deleted = false AND " +
           "LOWER(e.field) LIKE LOWER(CONCAT('%', :search, '%'))")
    Page<Entity> searchEntities(@Param("search") String search, Pageable pageable);
    
    boolean existsByFieldAndDeletedFalse(String field);
}
```

### 5. SERVICES
Always implement:
- Interface + Implementation pattern
- Constructor injection (never @Autowired fields)
- @Transactional(readOnly = true) on class, @Transactional on write methods
- @Cacheable on read operations
- Publish domain events after successful operations
- Custom exceptions for business logic violations
- Comprehensive logging

**Template:**
```java
public interface EntityService {
    EntityResponseDTO create(EntityRequestDTO request);
    EntityResponseDTO getById(UUID id);
    Page<EntityResponseDTO> getAll(Pageable pageable);
    EntityResponseDTO update(UUID id, EntityRequestDTO request);
    void delete(UUID id);
}

@Service
@Transactional(readOnly = true)
@RequiredArgsConstructor
@Slf4j
public class EntityServiceImpl implements EntityService {
    private final EntityRepository repository;
    private final EntityMapper mapper;
    private final ApplicationEventPublisher eventPublisher;
    
    @Override
    @Transactional
    @CacheEvict(value = "entities", allEntries = true)
    public EntityResponseDTO create(EntityRequestDTO request) {
        log.info("Creating entity: {}", request);
        
        // Validate business rules
        if (repository.existsByFieldAndDeletedFalse(request.getField())) {
            throw new DuplicateEntityException("Entity already exists");
        }
        
        Entity entity = mapper.toEntity(request);
        Entity saved = repository.save(entity);
        
        // Publish domain event
        eventPublisher.publishEvent(new EntityCreatedEvent(saved.getId()));
        
        log.info("Entity created with ID: {}", saved.getId());
        return mapper.toResponseDTO(saved);
    }
    
    @Override
    @Cacheable(value = "entities", key = "#id")
    public EntityResponseDTO getById(UUID id) {
        Entity entity = repository.findById(id)
            .filter(e -> !e.getDeleted())
            .orElseThrow(() -> new EntityNotFoundException("Entity not found: " + id));
        return mapper.toResponseDTO(entity);
    }
}
```

### 6. CONTROLLERS
Always implement:
- @RestController with @RequestMapping("/api/v1/resource")
- @RequiredArgsConstructor for constructor injection
- @Validated for validation support
- OpenAPI annotations (@Operation, @ApiResponse, @Tag)
- @PreAuthorize for security
- ResponseEntity with proper HTTP status
- Pagination with @PageableDefault

**Template:**
```java
@RestController
@RequestMapping("/api/v1/entities")
@RequiredArgsConstructor
@Validated
@Tag(name = "Entity Management", description = "APIs for entity operations")
@Slf4j
public class EntityController {
    private final EntityService service;
    
    @PostMapping
    @Operation(summary = "Create entity", description = "Creates a new entity")
    @ApiResponses({
        @ApiResponse(responseCode = "201", description = "Entity created"),
        @ApiResponse(responseCode = "400", description = "Invalid input"),
        @ApiResponse(responseCode = "409", description = "Entity already exists")
    })
    @PreAuthorize("hasRole('ADMIN')")
    public ResponseEntity<EntityResponseDTO> create(@Valid @RequestBody EntityRequestDTO request) {
        log.info("Received request to create entity");
        EntityResponseDTO response = service.create(request);
        return ResponseEntity.status(HttpStatus.CREATED).body(response);
    }
    
    @GetMapping("/{id}")
    @Operation(summary = "Get entity by ID")
    @ApiResponses({
        @ApiResponse(responseCode = "200", description = "Entity found"),
        @ApiResponse(responseCode = "404", description = "Entity not found")
    })
    public ResponseEntity<EntityResponseDTO> getById(@PathVariable UUID id) {
        return ResponseEntity.ok(service.getById(id));
    }
    
    @GetMapping
    @Operation(summary = "Get all entities with pagination")
    public ResponseEntity<Page<EntityResponseDTO>> getAll(
            @PageableDefault(size = 20, sort = "createdAt") Pageable pageable) {
        return ResponseEntity.ok(service.getAll(pageable));
    }
}
```

### 7. EVENT-DRIVEN COMMUNICATION

#### Domain Events (in core/event/)
```java
// Base event
@Getter
@AllArgsConstructor
public abstract class DomainEvent {
    private final UUID eventId = UUID.randomUUID();
    private final LocalDateTime occurredOn = LocalDateTime.now();
    private final String eventType;
}

// Specific event
@Getter
@EqualsAndHashCode(callSuper = true)
public class EntityCreatedEvent extends DomainEvent {
    private final UUID entityId;
    
    public EntityCreatedEvent(UUID entityId) {
        super("ENTITY_CREATED");
        this.entityId = entityId;
    }
}
```

#### Event Publishers (in service layer)
```java
@Service
@RequiredArgsConstructor
public class SomeService {
    private final ApplicationEventPublisher eventPublisher;
    
    public void doSomething() {
        // Business logic
        eventPublisher.publishEvent(new EntityCreatedEvent(entityId));
    }
}
```

#### Event Listeners (in module/listener/)
```java
@Component
@Slf4j
@RequiredArgsConstructor
public class EntityEventListener {
    private final SomeService service;
    
    @EventListener
    @TransactionalEventListener(phase = TransactionPhase.AFTER_COMMIT)
    @Async
    public void handleEntityCreated(EntityCreatedEvent event) {
        log.info("Handling entity created event: {}", event.getEntityId());
        // React to event
        service.processNewEntity(event.getEntityId());
    }
}
```

### 8. EXCEPTION HANDLING

#### Custom Exceptions (in core/exception/)
```java
public class EntityNotFoundException extends RuntimeException {
    public EntityNotFoundException(String message) {
        super(message);
    }
}

public class DuplicateEntityException extends RuntimeException {
    public DuplicateEntityException(String message) {
        super(message);
    }
}

public class BusinessRuleViolationException extends RuntimeException {
    public BusinessRuleViolationException(String message) {
        super(message);
    }
}
```

#### Global Exception Handler
```java
@RestControllerAdvice
@Slf4j
public class GlobalExceptionHandler {
    
    @ExceptionHandler(EntityNotFoundException.class)
    public ResponseEntity<ProblemDetail> handleNotFound(EntityNotFoundException ex) {
        log.error("Entity not found: {}", ex.getMessage());
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
            HttpStatus.NOT_FOUND, ex.getMessage());
        problem.setTitle("Resource Not Found");
        problem.setProperty("timestamp", LocalDateTime.now());
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(problem);
    }
    
    @ExceptionHandler(DuplicateEntityException.class)
    public ResponseEntity<ProblemDetail> handleDuplicate(DuplicateEntityException ex) {
        log.error("Duplicate entity: {}", ex.getMessage());
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
            HttpStatus.CONFLICT, ex.getMessage());
        problem.setTitle("Resource Already Exists");
        problem.setProperty("timestamp", LocalDateTime.now());
        return ResponseEntity.status(HttpStatus.CONFLICT).body(problem);
    }
    
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<ProblemDetail> handleValidation(MethodArgumentNotValidException ex) {
        Map<String, String> errors = new HashMap<>();
        ex.getBindingResult().getFieldErrors()
            .forEach(error -> errors.put(error.getField(), error.getDefaultMessage()));
        
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
            HttpStatus.BAD_REQUEST, "Validation failed");
        problem.setProperty("errors", errors);
        problem.setProperty("timestamp", LocalDateTime.now());
        return ResponseEntity.badRequest().body(problem);
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<ProblemDetail> handleGeneric(Exception ex) {
        log.error("Unexpected error", ex);
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
            HttpStatus.INTERNAL_SERVER_ERROR, "An unexpected error occurred");
        problem.setProperty("timestamp", LocalDateTime.now());
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(problem);
    }
}
```

## Security Best Practices
- Always use @PreAuthorize for method-level security
- Never expose entities directly in REST responses
- Validate all inputs with Bean Validation
- Use JWT for stateless authentication
- Implement rate limiting on public endpoints
- Sanitize user inputs to prevent injection attacks
- Use HTTPS in production
- Implement CORS properly
- Store passwords with BCrypt
- Never log sensitive information

## Testing Best Practices
- Generate unit tests with JUnit 5, Mockito, AssertJ
- Use @SpringBootTest for integration tests
- Use TestContainers for database integration tests
- Test happy path + edge cases + error scenarios
- Use BDD style: given-when-then
- Mock external dependencies
- Aim for 80%+ code coverage
- Use @DataJpaTest for repository tests
- Use @WebMvcTest for controller tests

**Test Template:**
```java
@SpringBootTest
@Testcontainers
class EntityServiceTest {
    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16");
    
    @Autowired
    private EntityService service;
    
    @MockBean
    private ApplicationEventPublisher eventPublisher;
    
    @Test
    @DisplayName("Should create entity successfully")
    void shouldCreateEntity() {
        // given
        EntityRequestDTO request = new EntityRequestDTO("test");
        
        // when
        EntityResponseDTO response = service.create(request);
        
        // then
        assertThat(response.id()).isNotNull();
        assertThat(response.field()).isEqualTo("test");
        verify(eventPublisher).publishEvent(any(EntityCreatedEvent.class));
    }
    
    @Test
    @DisplayName("Should throw exception when entity not found")
    void shouldThrowWhenNotFound() {
        // given
        UUID nonExistentId = UUID.randomUUID();
        
        // when & then
        assertThatThrownBy(() -> service.getById(nonExistentId))
            .isInstanceOf(EntityNotFoundException.class)
            .hasMessageContaining("not found");
    }
}
```

## Database Best Practices
- Always use Flyway or Liquibase migrations
- Never modify existing migrations
- Index foreign keys and frequently queried fields
- Use appropriate data types (VARCHAR vs TEXT, INT vs BIGINT)
- Add meaningful comments to complex fields
- Use snake_case for table/column names
- Normalize data appropriately (3NF for transactional data)
- Use database constraints (NOT NULL, UNIQUE, CHECK)
- Implement soft deletes for audit trails
- Use database-level default values where appropriate

**Migration Template (Flyway):**
```sql
-- V1__create_entities_table.sql
CREATE TABLE entities (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    description TEXT,
    status VARCHAR(50) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_by VARCHAR(255),
    last_modified_by VARCHAR(255),
    version BIGINT NOT NULL DEFAULT 0,
    deleted BOOLEAN NOT NULL DEFAULT FALSE
);

CREATE INDEX idx_entities_name ON entities(name) WHERE deleted = FALSE;
CREATE INDEX idx_entities_status ON entities(status) WHERE deleted = FALSE;
CREATE INDEX idx_entities_created_at ON entities(created_at);

COMMENT ON TABLE entities IS 'Main entity table';
COMMENT ON COLUMN entities.status IS 'Current status: ACTIVE, INACTIVE, PENDING';
```

## Performance Best Practices
- Enable query pagination by default (max 100 items per page)
- Use @EntityGraph to prevent N+1 queries
- Implement caching with Redis for frequently accessed data
- Use async processing (@Async) for long-running tasks
- Enable virtual threads (Java 21) for better throughput
- Connection pooling with HikariCP (default in Spring Boot)
- Use database connection pooling appropriately
- Implement query result caching
- Use lazy loading for relationships
- Profile queries with Spring Boot Actuator
- Monitor database performance with explain plans

**Caching Configuration:**
```java
@Configuration
@EnableCaching
public class CacheConfig {
    
    @Bean
    public RedisCacheConfiguration cacheConfiguration() {
        return RedisCacheConfiguration.defaultCacheConfig()
            .entryTtl(Duration.ofMinutes(60))
            .disableCachingNullValues()
            .serializeValuesWith(
                RedisSerializationContext.SerializationPair.fromSerializer(
                    new GenericJackson2JsonRedisSerializer()
                )
            );
    }
}
```

## API Documentation Best Practices
- Generate OpenAPI documentation automatically
- Use meaningful operation summaries and descriptions
- Document all error responses
- Include request/response examples
- Group endpoints by tags
- Document authentication requirements
- Version your APIs (/api/v1, /api/v2)

**OpenAPI Configuration:**
```java
@Configuration
public class OpenApiConfig {
    
    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
            .info(new Info()
                .title("Application API")
                .version("1.0")
                .description("RESTful API documentation")
                .contact(new Contact()
                    .name("API Support")
                    .email("support@company.com")))
            .addSecurityItem(new SecurityRequirement().addList("bearerAuth"))
            .components(new Components()
                .addSecuritySchemes("bearerAuth", 
                    new SecurityScheme()
                        .type(SecurityScheme.Type.HTTP)
                        .scheme("bearer")
                        .bearerFormat("JWT")));
    }
}
```

## Logging Best Practices
- Use SLF4J with Logback
- Use appropriate log levels (ERROR, WARN, INFO, DEBUG, TRACE)
- Include contextual information in logs
- Never log sensitive information (passwords, tokens, PII)
- Use structured logging for production
- Implement correlation IDs for request tracking
- Log exceptions with stack traces
- Use MDC for thread-local context

**Logging Examples:**
```java
@Slf4j
public class SomeService {
    
    public void processData(String id) {
        log.debug("Starting data processing for ID: {}", id);
        
        try {
            // Business logic
            log.info("Successfully processed data for ID: {}", id);
        } catch (Exception e) {
            log.error("Failed to process data for ID: {}", id, e);
            throw new ProcessingException("Processing failed", e);
        }
    }
}
```

## Module Communication Rules
- **NEVER** direct repository calls between modules
- **ALWAYS** use events for cross-module communication
- **PREFER** async event processing
- **USE** service interfaces for synchronous needs (rare cases)
- Keep modules loosely coupled
- Define clear bounded contexts
- Use DTOs for inter-module communication

## Forbidden Practices
- ❌ Field injection (@Autowired on fields)
- ❌ Exposing entities in REST responses
- ❌ Returning null (use Optional)
- ❌ Catching generic Exception without rethrowing
- ❌ Empty catch blocks
- ❌ Magic numbers/strings (use constants/enums)
- ❌ Direct JDBC/SQL in service layer
- ❌ Mutable DTOs for responses
- ❌ Hardcoded configuration values
- ❌ Ignoring compiler warnings
- ❌ Using deprecated APIs
- ❌ Circular dependencies between modules

## Recommended Practices
- ✅ Use constructor injection over field injection
- ✅ Implement proper exception handling with @ControllerAdvice
- ✅ Use DTOs for API responses (never expose entities)
- ✅ Implement request validation with @Valid
- ✅ Use Lombok to reduce boilerplate
- ✅ Enable actuator endpoints for monitoring
- ✅ Implement circuit breakers with Resilience4j
- ✅ Use async processing for long-running tasks
- ✅ Implement proper logging (structured logging)
- ✅ Use environment variables for configuration
- ✅ Implement rate limiting for APIs
- ✅ Use database migrations (Flyway/Liquibase)
- ✅ Write comprehensive tests
- ✅ Document your APIs with OpenAPI
- ✅ Use meaningful variable and method names
- ✅ Follow SOLID principles
- ✅ Keep methods small and focused
- ✅ Use design patterns appropriately

## When Generating Code
1. Check if entity exists, reuse if possible
2. Follow package structure strictly
3. Apply all required annotations
4. Include comprehensive validation
5. Add meaningful logging statements
6. Publish domain events where appropriate
7. Handle exceptions properly
8. Generate corresponding tests
9. Add OpenAPI documentation
10. Verify soft delete filters are applied

## Quick Commands for Copilot

**Generate Entity:** "Create JPA entity for [Name] with fields [list], following template"
**Generate Repository:** "Create repository for [Entity] with custom queries [list]"
**Generate Service:** "Create service for [Entity] with CRUD and event publishing"
**Generate Controller:** "Create REST controller for [Entity] with security"
**Generate DTOs:** "Create request/response DTOs for [Entity] with validation"
**Generate Mapper:** "Create MapStruct mapper for [Entity]"
**Generate Tests:** "Create unit and integration tests for [Entity]Service"
**Generate Event:** "Create domain event [EventName] and listener in [Module]"
**Generate Configuration:** "Create configuration class for [Feature]"
**Generate Migration:** "Create Flyway migration for [Table]"

## Configuration Best Practices

### Application Properties Structure
```yaml
# application.yml
spring:
  application:
    name: ${APP_NAME:application}
  
  datasource:
    url: ${DB_URL:jdbc:postgresql://localhost:5432/db}
    username: ${DB_USERNAME:user}
    password: ${DB_PASSWORD:password}
    hikari:
      maximum-pool-size: 10
      minimum-idle: 5
      connection-timeout: 30000
  
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: false
    properties:
      hibernate:
        format_sql: true
        dialect: org.hibernate.dialect.PostgreSQLDialect
  
  cache:
    type: redis
    redis:
      time-to-live: 3600000
  
  data:
    redis:
      host: ${REDIS_HOST:localhost}
      port: ${REDIS_PORT:6379}

logging:
  level:
    root: INFO
    com.company: DEBUG
  pattern:
    console: "%d{yyyy-MM-dd HH:mm:ss} - %msg%n"

management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics,prometheus
  endpoint:
    health:
      show-details: when-authorized
```

## Additional Resources

- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)
- [Spring Framework Documentation](https://docs.spring.io/spring-framework/reference/)
- [Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)
- [Spring Security](https://docs.spring.io/spring-security/reference/)
- [Baeldung Spring Tutorials](https://www.baeldung.com/spring-tutorial)
- [12-Factor App Principles](https://12factor.net/)
- [Clean Code by Robert Martin](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
- [Domain-Driven Design](https://martinfowler.com/bliki/DomainDrivenDesign.html)

---

**Note:** Adapt these guidelines to your specific project requirements while maintaining the core principles of clean code, testability, and maintainability.