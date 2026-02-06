# Agent Generator Full Skill

**Version:** 1.0  
**Purpose:** Create, configure, and manage Expert Agents with comprehensive skill mapping and advanced features  
**Framework:** Angular 21+ Development with DDD Architecture  
**Status:** Authoritative

---

## Overview

The **Agent Generator Full Skill** enables you to create sophisticated expert agents with:

✅ Comprehensive agent specifications with all metadata  
✅ Multi-skill composition and deep skill mapping  
✅ Workflow integration and orchestration  
✅ Advanced capability modeling with examples  
✅ Complete agent registry generation (AGENTS_SKILLS_FULL.md)  
✅ Agent hierarchy and inheritance patterns  
✅ Skill synchronization and validation  
✅ Agent performance metrics and monitoring  

---

## When to Use This Skill

Use the Agent Generator Full Skill when:

- ✅ Creating complex agents with 5+ skills
- ✅ Designing agent hierarchies and inheritance
- ✅ Integrating agents into workflows
- ✅ Building agent registries with detailed metadata
- ✅ Creating agent collaboration patterns
- ✅ Implementing skill validation and synchronization
- ✅ Planning sophisticated multi-agent systems
- ✅ Documenting agent ecosystems

---

## Core Concepts

### Expert Agent Architecture

A comprehensive Expert Agent combines multiple specialized skills:

```
Expert Agent = {
  name: string,                    // Unique identifier
  role: string,                    // Primary role (one-liner)
  description: string,             // Detailed description (2-3 sentences)
  primary_expertise: string,       // Main knowledge domain
  
  capabilities: Capability[],      // What it can do
  primary_skills: Skill[],        // Skills that power it
  focus_areas: FocusArea[],       // Deep expertise zones
  
  workflows: Workflow[],           // Workflows using this agent
  integration_pattern: string,     // How it integrates
  
  metadata: AgentMetadata,        // Advanced metadata
  usage_template: string,         // How to ask for help
  examples: UsageExample[]        // Real-world examples
}
```

### Advanced Skill Composition

Skills form a directed acyclic graph (DAG):

```
Agent:
  Skill A (foundation)
    ├─ Concept X
    ├─ Concept Y
    └─ Pattern Z
  
  Skill B (specialization, depends on A)
    ├─ Advanced Concept A1
    └─ Advanced Pattern A3
  
  Skill C (specialization, independent)
    └─ Orthogonal Knowledge
```

### Capability Specification

Each capability is fully specified:

```
Capability = {
  name: string,                           // What it does
  description: string,                    // How it works
  required_skills: Skill[],               // Skills needed
  complexity: 'simple' | 'medium' | 'advanced',
  examples: Example[],                    // Real examples
  related_capabilities: Capability[],     // Related capabilities
  anti_patterns: string[]                 // What NOT to do
}
```

---

## Process: Creating a Comprehensive Agent

### Phase 1: Domain Analysis

**Define the Problem Domain:**

```markdown
### Domain Specification

**Problem Statement:**
What specific problems does this agent solve?
- Problem 1: [description]
- Problem 2: [description]
- Problem 3: [description]

**Scope Boundaries:**
- In scope: [What agent handles]
- Out of scope: [What other agents handle]

**Target Users:**
- [User persona 1]
- [User persona 2]
- [User persona 3]

**Success Criteria:**
- [Measurable success metric 1]
- [Measurable success metric 2]
```

### Phase 2: Skill Selection & Composition

**Analyze Required Skills:**

1. **Inventory available skills** from `.agents/skills/`
2. **Map skill dependencies** - Some skills build on others
3. **Select non-overlapping skills** - Each teaches something unique
4. **Validate coverage** - Together, do they cover the domain completely?

**Example Skill Composition:**

```markdown
### Selected Skills for [Agent Name]

**Foundation Skills (Level 1):**
- `angular-component` (v21.x component patterns)
- `typescript` (strong typing fundamentals)

**Specialization Skills (Level 2):**
- `angular-signals` (state management, depends on typescript)
- `angular-http` (data fetching, depends on typescript)

**Advanced Skills (Level 3):**
- `tailwind-css-patterns` (styling patterns, independent)
- `interface-design` (UX design principles, independent)

**Skill Dependency Graph:**
```
typescript (root)
├── angular-component
├── angular-signals
└── angular-http

interface-design (independent)
tailwind-css-patterns (independent)
```
```

### Phase 3: Detailed Capability Modeling

**Define Each Capability Comprehensively:**

```markdown
### Capability: Create Interactive Forms

**Description:**
Build reactive, type-safe forms with validation, dynamic fields, and
state management using Angular Signals and Reactive Forms API.

**Complexity Level:** Advanced

**Required Skills:**
- `angular-forms` (v21 Signal Forms API)
- `angular-signals` (form state management)
- `typescript` (type-safe form structures)
- `tailwind-css-patterns` (form field styling)

**Detailed Steps:**
1. Create form structure with typed schema
2. Implement validation rules
3. Add dynamic field support
4. Manage form state with signals
5. Style with Tailwind utilities
6. Handle error states and messages

**Code Example:**
```typescript
// See SKILL.md for implementation details
```

**Anti-Patterns to Avoid:**
- ❌ Mutable form state (use signals)
- ❌ Late field type validation (validate early)
- ❌ Complex nested form structures (flatten when possible)
- ❌ Missing accessibility labels (always add aria-label)

**Related Capabilities:**
- "Handle complex field validation"
- "Implement multi-step form wizards"
- "Create conditional field visibility"

**Performance Considerations:**
- Use OnPush change detection
- Memoize computed form selectors
- Lazy load form sections if large
```

### Phase 4: Workflow Integration

**Define Agent Participation in Workflows:**

```markdown
### Workflow Integration

**Primary Workflows:**
1. `new_feature_development`
   - Role: Implement core feature components
   - Seq: Step 2 (after architecture)
   - Dependencies: FrontendArchitectAgent

2. `code_refactoring`
   - Role: Refactor existing components
   - Seq: Step 2 (after architecture review)
   - Dependencies: FrontendArchitectAgent, StateAgent

3. `design_system_update`
   - Role: Update component library components
   - Seq: Step X (parallel with TailwindAgent)
   - Dependencies: [TailwindAgent for styling]

**Workflow Decision Tree:**
```
Is this about...?
├─ Building new components? → Primary workflow: new_feature_development
├─ Fixing bugs? → Primary workflow: bug_fixing
├─ Improving code structure? → Primary workflow: code_refactoring
├─ Updating design system? → Primary workflow: design_system_update
└─ Performance issues? → Primary workflow: performance_optimization
```
```

### Phase 5: Advanced Metadata

**Define Agent Metadata for Management:**

```markdown
### Agent Metadata

**Versioning:**
- Version: 1.0
- Release Date: 2026-02-06
- Last Updated: {date}
- Maturity Level: Stable | Beta | Experimental

**Resource Requirements:**
- Estimated Response Time: 2-5 minutes
- Typical Token Usage: 2000-5000 tokens
- Compute Requirements: Standard | High | GPU

**Knowledge Base:**
- Primary Documentation: {links}
- Code Examples: {count} examples
- Test Coverage: {percentage}

**Maintenance Schedule:**
- Review Frequency: Quarterly
- Skill Update Cadence: {monthly/quarterly/as-needed}
- Performance Monitoring: Enabled

**Metrics & Monitoring:**
- Success Rate: {track usage success}
- Average Response Quality: {rate by users}
- Common Failure Points: {identify and track}
- Improvement Opportunities: {document improvement areas}
```

### Phase 6: Comprehensive Documentation

**Create Complete Agent Documentation:**

```markdown
### Complete Agent Profile

**Quick Start:**
For a quick introduction, see [AGENT_TEMPLATE.md](../agent-generator/AGENT_TEMPLATE.md)

**Detailed Reference:**
For comprehensive agent creation with all metadata, continue reading.

**[Agent Name] Agent**

**Role:** {One-line role}

**Description:** {2-3 sentence description}

**Primary Expertise:** {Main domain}

**Capabilities:**
{Numbered list of detailed capabilities}

**Primary Skills:**
{List with skill descriptions and dependencies}

**Focus Areas:**
{Deep expertise zones}

**Workflows:**
{Workflow participation details}

**Integration Pattern:**
{How it works with other agents}

**Usage Template:**
{Comprehensive usage template with placeholders}

**Advanced Examples:**
{Real-world complex examples}

**Extending This Agent:**
{How to add skills and capabilities}

**Related Agents:**
{Similar or complementary agents}

**Common Questions:**
{FAQ section}
```

---

## Creating the Full Agent Registry

### Generate AGENTS_SKILLS_FULL.md

The full registry includes:

```markdown
# Agents & Skills Registry - Full Version

**Central Registry with Complete Metadata**

## Quick Lookup Table
[Table with all agents, roles, domains, workflows]

## Detailed Agent Profiles
[All agents with full specifications]

## Skill Dependency Graphs
[Visual or text-based dependency graphs]

## Workflow Matrix
[Which agents participate in which workflows]

## Integration Patterns
[How agents work together]

## Metrics & Performance
[Agent usage metrics and performance data]

## Advanced Usage Examples
[Complex multi-agent scenarios]
```

---

## Advanced Patterns

### Agent Inheritance

Agents can inherit from parent agents:

```markdown
### Parent Agent (Base)
[Core capabilities and skills]

### Child Agent (Specialized)
**Inherits From:** Parent Agent

**Additional Skills:**
- `specialized-skill-1`
- `specialized-skill-2`

**Additional Capabilities:**
- "Specialized capability 1"
- "Specialized capability 2"

**Behavior:**
- Inherits all parent capabilities
- Can override parent behavior (if justified)
- Must maintain parent API compatibility
```

### Agent Composition

Agents can delegate to other agents:

```markdown
### Composite Agent

**Primary Role:** {role}

**Delegates To:**
- `ChildAgent1` → {domain}
- `ChildAgent2` → {domain}

**Coordination Strategy:**
{How agents coordinate and exchange information}

**Workflow:**
1. User asks CompositeAgent
2. CompositeAgent analyzes request
3. CompositeAgent delegates to appropriate child agent(s)
4. Child agents return results
5. CompositeAgent synthesizes results
6. CompositeAgent returns comprehensive answer
```

### Multi-Agent Collaboration

Agents working together on complex tasks:

```markdown
### Multi-Agent Workflow: {Workflow Name}

**Participating Agents:**
1. Agent A → {Phase 1: Architecture}
2. Agent B → {Phase 2: Implementation}
3. Agent C → {Phase 3: Styling}
4. Agent D → {Phase 4: Testing}

**Data Flow:**
Agent A output → Agent B input
Agent B output → Agent C input
Agent C output → Agent D input

**Synchronization Points:**
- [Sync point 1]: Validate architecture before implementation
- [Sync point 2]: Cross-check styling with design system
- [Sync point 3]: Ensure test coverage

**Handoff Protocols:**
- Format of output from each agent
- Required metadata for next agent
- Error handling if validation fails
```

---

## Skill Validation & Synchronization

### Skill Coverage Validation

Ensure agent skills cover the domain:

```markdown
### Coverage Analysis for {Agent}

**Domain Requirements:**
- Requirement 1
- Requirement 2
- Requirement 3

**Skill Coverage:**

| Requirement | Covered By | Skill | Status |
|---|---|---|---|
| Req 1 | Skill A | angular-component | ✅ |
| Req 2 | Skill B | angular-signals | ✅ |
| Req 3 | Skill C, D | tailwind-css | ✅ |

**Coverage Score:** 100% ✅

**Gaps:** None identified

**Recommendations:** [If any gaps exist]
```

### Skill Synchronization

When skills are updated:

```markdown
### Skill Update Impact Analysis

**Updated Skill:** `angular-signals` (v1.0 → v1.1)

**Affected Agents:**
- StateAgent ← Primary skill
- AngularAgent ← Uses signal patterns
- FormBuilderAgent ← Uses signal forms

**Required Updates:**
- Verify agent documentation matches new skill content
- Update examples if patterns changed
- Test agent with new skill knowledge
- Update focus areas if applicable

**Testing Checklist:**
- [ ] Agent responds with updated skill knowledge
- [ ] Examples use new patterns
- [ ] Documentation is consistent
- [ ] No conflicting advice between related agents
```

---

## Agent Performance Metrics

### Tracking Agent Quality

```markdown
### Agent Metrics Dashboard

**Success Rate:** {percentage of successful queries}
**Average Response Quality:** {rating 1-5}
**Response Time:** {average minutes}
**Token Efficiency:** {tokens per useful response}

**Common Success Patterns:**
- Pattern 1: {what works well}
- Pattern 2: {what works well}

**Common Failure Patterns:**
- Failure 1: {when it struggles}
- Failure 2: {when it struggles}

**Improvement Roadmap:**
1. Priority 1: {improvement}
2. Priority 2: {improvement}
3. Priority 3: {improvement}
```

---

## Summary

The **Agent Generator Full Skill** enables you to:

✅ Create comprehensive, enterprise-grade agents  
✅ Use advanced skill composition patterns  
✅ Implement agent hierarchies and inheritance  
✅ Design sophisticated multi-agent workflows  
✅ Generate complete agent registries  
✅ Monitor and optimize agent performance  
✅ Maintain consistency across agent ecosystems  

---

**For Quick Agent Creation:**
Use [AGENT_TEMPLATE.md](../agent-generator/AGENT_TEMPLATE.md) in the simple agent-generator skill.

**For Comprehensive Agent Design:**
Continue reading this document for advanced patterns and full specifications.

**Questions?**
Check [AGENTS_SKILLS_FULL.md](../../AGENTS_SKILLS_FULL.md) for examples of fully-featured agents.
