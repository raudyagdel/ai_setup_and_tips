# Comprehensive Expert Agent Template
## Complete Guide to Create Enterprise-Grade Expert Agents

**Version:** 2.0 (Full Edition)  
**Purpose:** Detailed process to design sophisticated Expert Agents with comprehensive skill mapping, workflow integration, and advanced metadata  
**Audience:** Advanced agent designers and system architects  
**Status:** Authoritative

---

## Table of Contents

1. [Overview](#overview)
2. [Phase 1: Domain Analysis](#phase-1-domain-analysis)
3. [Phase 2: Skill Composition](#phase-2-skill-composition)
4. [Phase 3: Capability Definition](#phase-3-capability-definition)
5. [Phase 4: Workflow Integration](#phase-4-workflow-integration)
6. [Phase 5: Agent Specification](#phase-5-agent-specification)
7. [Phase 6: Documentation](#phase-6-documentation)
8. [Complete Template](#complete-template)
9. [Real-World Examples](#real-world-examples)
10. [Advanced Patterns](#advanced-patterns)

---

## Overview

An **Enterprise-Grade Expert Agent** combines strategic skill composition, workflow integration, and advanced metadata to solve complex problems at scale.

**Three-Tier Agent System:**

```
┌─────────────────────────────────────────┐
│  Simple Agents (5-step template)         │
│  - Quick agent creation                  │
│  - 3-6 skills                            │
│  - Single primary workflow                │
│  - Minimal metadata                       │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│  Advanced Agents (This template)          │
│  - Comprehensive design                  │
│  - 5-8 skills with dependencies          │
│  - Multiple workflow participation        │
│  - Rich metadata and metrics              │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│  Meta-Agents (Agent Orchestrators)       │
│  - Manage other agents                   │
│  - Workflow coordination                 │
│  - Cross-agent delegation                 │
│  - System-level optimization             │
└─────────────────────────────────────────┘
```

---

## Phase 1: Domain Analysis

### Step 1.1: Define the Problem Domain

Start by precisely defining what problems this agent solves:

```markdown
### Domain Analysis

**Agent Name:** [Your Agent Name]

**Problem Statement:**
{Describe the specific problems this agent solves}

Example:
The frontend has no centralized pattern for handling complex async
data dependencies. Services use RxJS inconsistently, and developers
struggle with managing interdependent data streams, race conditions,
and stale data in real-time scenarios.

**Core Problems:**
1. [Problem 1]: [Why it matters]
2. [Problem 2]: [Why it matters]
3. [Problem 3]: [Why it matters]

**Business Impact:**
- Development Speed: [Impact]
- Code Quality: [Impact]
- User Experience: [Impact]

**Success Metrics:**
- [Measurable metric 1] (target: [value])
- [Measurable metric 2] (target: [value])
- [Measurable metric 3] (target: [value])
```

### Step 1.2: Analyze Scope & Boundaries

Determine what falls IN and OUT of scope:

```markdown
### Scope Definition

**In Scope (Agent Responsibility):**
- What this agent DOES handle
- Features it includes
- Problems it solves
- Domains it covers

**Out of Scope (Other Agents Handle):**
- What falls to other agents
- Features excluded
- Related but separate concerns
- Complementary domains

**Boundary Examples:**

IN SCOPE:
✅ Managing async data dependencies between multiple sources
✅ Handling race conditions in real-time data
✅ Coordinating RxJS streams

OUT OF SCOPE:
❌ Individual HTTP request handling (belongs to APIIntegrationAgent)
❌ Component-level state (belongs to StateAgent)
❌ Styling and UI presentation (belongs to TailwindAgent)
```

### Step 1.3: Identify Target Users

Who will use this agent's expertise?

```markdown
### User Personas

**Primary Users:**
1. [User Type 1]: [What they need from this agent]
2. [User Type 2]: [What they need from this agent]
3. [User Type 3]: [What they need from this agent]

**Experience Level:**
- Beginner friendly? [Yes/No]
- Requires domain knowledge? [Yes/No]
- Advanced techniques included? [Yes/No]

**Use Frequency:**
- Daily: [Yes/No]
- Weekly: [Yes/No]
- As-needed: [Yes/No]
```

---

## Phase 2: Skill Composition

### Step 2.1: Audit Available Skills

List all available skills that could contribute to this agent:

```markdown
### Skill Inventory

**Candidate Skills Found:**

| Skill Name | Domain | Status | Notes |
|---|---|---|---|
| `skill-1` | Domain A | ✅ Candidate | Covers [aspect] |
| `skill-2` | Domain B | ✅ Candidate | Covers [aspect] |
| `skill-3` | Domain C | ⚠️ Partial | Only [specific part] applies |
| `skill-4` | Domain D | ❌ Rejected | Too overlapping with skill-1 |
```

### Step 2.2: Map Skill Dependencies

Understand how skills relate and depend on each other:

```markdown
### Skill Dependency Graph

**Foundation Skills (Independent):**
- `typescript` - foundational type system knowledge
- `angular-development` - Angular fundamentals

**Level 1 Skills (Depend on Foundation):**
- `angular-http` (depends: typescript, angular-development)
- `angular-signals` (depends: typescript, angular-development)

**Level 2 Skills (Depend on Level 1):**
- `angular-forms` (depends: angular-signals, typescript)
- `clean-ddd-hexagonal` (depends: angular-development)

**Orthogonal Skills (No Dependencies):**
- `tailwind-css-patterns` - independent styling knowledge
- `interface-design` - independent UX knowledge

**Visual Dependency Graph:**
```
typescript ──┬──→ angular-http
             ├──→ angular-signals ──→ angular-forms
             └──→ angular-development

tailwind-css-patterns (independent)
interface-design (independent)
```
```

### Step 2.3: Validate Skill Coverage

Ensure the selected skills comprehensively cover your agent's domain:

```markdown
### Coverage Validation Matrix

**Domain Requirements vs Skill Coverage:**

| Requirement | Skill A | Skill B | Skill C | Skill D | Status |
|---|---|---|---|---|---|
| Handle async data | ✅ | ✅ | - | - | ✅ Covered |
| Manage race conditions | ✅ | - | ✅ | - | ✅ Covered |
| Real-time updates | - | ✅ | ✅ | - | ✅ Covered |
| Type safety | ✅ | ✅ | ✅ | ✅ | ✅ Covered |
| UI patterns | - | - | - | ✅ | ✅ Covered |

**Coverage Analysis:**
- 100% of requirements covered ✅
- No major gaps identified ✅
- Skills complement without overlap ✅

**Skills NOT Selected (Rejected List):**
- `skill-x`: Too overlapping with Skill A
- `skill-y`: Out of scope
- `skill-z`: Redundant coverage
```

### Step 2.4: Select Final Skill Set

Final selection of 5-8 primary skills:

```markdown
### Final Skill Composition

**Primary Skills for [Agent Name]:**

1. **`skill-1`** - [Purpose]
   - Covers: [What it teaches]
   - Contributes to capabilities: [cap1, cap2, cap3]
   - Required for: [What depends on it]

2. **`skill-2`** - [Purpose]
   - Covers: [What it teaches]
   - Contributes to capabilities: [cap1, cap2]
   - Required for: [What depends on it]

[... 3-8 skills total ...]

**Complementarity Check:** ✅ All skills complement each other
**Overlap Check:** ✅ No significant overlaps between skills
**Coverage Check:** ✅ All domain areas covered
```

---

## Phase 3: Capability Definition

### Step 3.1: Identify Required Capabilities

What can this agent DO?

```markdown
### Capability Inventory

**Initial Capability Brainstorm:**
- Potential capability 1
- Potential capability 2
- Potential capability 3
- Potential capability 4
- Potential capability 5
- Potential capability 6
- Potential capability 7
- Potential capability 8

**Refined Capabilities (5-8 selected):**
[Select the most impactful and distinct capabilities]
```

### Step 3.2: Define Capabilities in Detail

Each capability needs comprehensive documentation:

```markdown
### Detailed Capability Specification

#### Capability 1: {Specific, Action-Oriented Name}

**Description:**
{2-3 sentence explanation of what this capability does}

**Complexity Level:**
- ⭐ Simple: Can be done with one skill directly
- ⭐⭐ Medium: Requires combining 2-3 skills
- ⭐⭐⭐ Advanced: Requires deep skill knowledge and examples

**Skills Required:**
- `skill-1` (essential): [what it contributes]
- `skill-2` (supporting): [what it contributes]
- `skill-3` (optional): [what it contributes]

**Prerequisite Knowledge:**
- [Concept 1]
- [Concept 2]
- [Pattern 1]

**Step-by-Step Process:**
1. [Step 1]: [Description]
2. [Step 2]: [Description]
3. [Step 3]: [Description]
4. [Step 4]: [Description]
5. [Step 5]: [Description]

**Code Example:**
```typescript
// Real-world implementation example
// See SKILL.md for full details
```

**Common Pitfalls (Anti-Patterns):**
- ❌ Pitfall 1: [Why it's wrong]
- ❌ Pitfall 2: [Why it's wrong]
- ❌ Pitfall 3: [Why it's wrong]

**Best Practices:**
- ✅ Practice 1: [Why it's good]
- ✅ Practice 2: [Why it's good]
- ✅ Practice 3: [Why it's good]

**Related Capabilities:**
- [Capability A]: [How they relate]
- [Capability B]: [How they relate]

**When to Use This Capability:**
- Use when: [Scenario 1]
- Use when: [Scenario 2]
- Don't use when: [Scenario 3]

**Performance Implications:**
- Time complexity: [O(n)]
- Space complexity: [O(n)]
- Network calls: [How many]
- Real-world constraints: [What matters]

**Accessibility Considerations:**
- [a11y requirement 1]
- [a11y requirement 2]

**Mobile/Responsive Considerations:**
- [Mobile consideration 1]
- [Mobile consideration 2]

**Testing Strategy:**
- Unit test approach: [What to test]
- Integration test approach: [What to test]
- E2E test approach: [What to test]

[... Repeat for each capability ...]
```

### Step 3.3: Capability Usage Matrix

Show how capabilities combine:

```markdown
### Capability Usage Matrix

**Common Usage Patterns:**

| Scenario | Capability 1 | Capability 2 | Capability 3 | Other Agents |
|---|---|---|---|---|
| Scenario A | ✅ | ✅ | - | - |
| Scenario B | ✅ | - | ✅ | Agent X |
| Scenario C | - | ✅ | ✅ | Agent Y |

**Capability Combinations:**
- To [Goal A]: Use capabilities [1, 2]
- To [Goal B]: Use capabilities [2, 3]
- To [Goal C]: Use capabilities [1, 3] + hand off to Agent X
```

---

## Phase 4: Workflow Integration

### Step 4.1: Identify Workflow Participation

Which workflows does this agent participate in?

```markdown
### Workflow Participation Map

**Primary Workflows:**
1. `new_feature_development` ← Main workflow for this agent
2. `code_refactoring` ← Secondary workflow
3. `design_system_update` ← Tertiary workflow

**Workflow Roles:**

**In new_feature_development:**
- Role: [What this agent does in this workflow]
- Sequence: Step [X] of [Y total steps]
- Dependencies: [What must happen before]
- Outputs: [What this agent produces]
- Triggers: [What causes this workflow to use this agent]

**In code_refactoring:**
- Role: [What this agent does]
- Sequence: Step [X]
- Dependencies: [Previous steps]
- Outputs: [Refactoring recommendations]

**In design_system_update:**
- Role: [What this agent does]
- Sequence: Step [X]
- Dependencies: [Other agents]
- Outputs: [Updated components/patterns]
```

### Step 4.2: Define Agent Decision Trees

When should users invoke this agent?

```markdown
### Agent Invocation Decision Tree

**When to Use This Agent:**
```
┌─ What are you working on?
│
├─ Building a [domain feature]?
│  └─→ YES: Use this agent in `new_feature_development` workflow
│
├─ Refactoring [domain area]?
│  └─→ YES: Use this agent in `code_refactoring` workflow
│
├─ Updating [domain part] of design system?
│  └─→ YES: Use this agent in `design_system_update` workflow
│
└─ None of the above
   └─→ Consider other agents or workflows
```

**Escalation Criteria:**
- ✅ Use this agent when: [Criterion 1]
- ✅ Use this agent when: [Criterion 2]
- ❌ Don't use when: [What other agent handles]
- ❌ Don't use when: [Out of scope]
```

---

## Phase 5: Agent Specification

### Step 5.1: Complete Agent Profile

Fill in the comprehensive agent profile:

```markdown
### Complete Agent Profile

**Agent Name:** [Unique, descriptive name]

**Role:** [One-line description of specialization]

**Description:**
[2-3 sentence explanation of what this agent does, what problems it
solves, and why it exists]

**Primary Expertise:** [Main knowledge domain]

**Status:** [Stable | Beta | Experimental]
**Version:** 1.0
**Last Updated:** [Date]
**Maintained By:** [Owner/Team]

---

#### Capabilities (5-8 total)

1. **[Capability Name 1]** - [Brief description]
2. **[Capability Name 2]** - [Brief description]
3. **[Capability Name 3]** - [Brief description]
4. **[Capability Name 4]** - [Brief description]
5. **[Capability Name 5]** - [Brief description]
6. **[Capability Name 6]** - [Brief description] (optional)
7. **[Capability Name 7]** - [Brief description] (optional)
8. **[Capability Name 8]** - [Brief description] (optional)

---

#### Primary Skills

1. **`skill-name-1`**
   - Version: [x.y.z]
   - Purpose: [What it contributes]
   - Coverage: [% of agent's domain]
   - [Additional metadata]

2. **`skill-name-2`**
   - Version: [x.y.z]
   - Purpose: [What it contributes]
   - Coverage: [% of agent's domain]

[... all skills ...]

**Skill Coverage Analysis:**
- Domain Coverage: [X%]
- Skill Dependencies: [Satisfied/Gaps]
- Complementarity: [Score/Status]

---

#### Focus Areas (Deep Expertise Zones)

- Focus Area 1: [Detailed description]
- Focus Area 2: [Detailed description]
- Focus Area 3: [Detailed description]

---

#### Workflow Integration

**Primary Workflows:**
1. `workflow-1` (Step X)
2. `workflow-2` (Step Y)

**Workflow Roles:**
- In `workflow-1`: [Specific role]
- In `workflow-2`: [Specific role]

---

#### Agent Metadata

**Resource Requirements:**
- Typical Response Time: [X-Y minutes]
- Average Token Usage: [X-Y tokens]
- Compute Class: [Standard | High | GPU]

**Knowledge Maturity:**
- Content: [% complete]
- Examples: [Count]
- Test Coverage: [%]

**Performance Metrics:**
- Success Rate: [%]
- User Satisfaction: [Score/5]
- Average Response Quality: [Score]

**Dependencies:**
- Dependent Skills: [Loaded automatically]
- Related Agents: [List for collaboration]
- System Requirements: [Node version, etc.]

---

#### Usage Template

**How developers ask this agent for help:**

\`\`\`
@AgentName
[Context: What are you building/fixing?]

Task: [Specific task or problem]

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Constraints:
- [Constraint 1]
- [Constraint 2]

Additional Context:
- [Any other relevant info]
\`\`\`

---

#### Usage Examples

**Example 1: [Specific Scenario]**

User Request:
\`\`\`
@AgentName
[Complete example request]
\`\`\`

Expected Response:
[What the agent returns]

---

**Example 2: [Another Scenario]**

[Second complete example]

---

#### Integration Patterns

**How This Agent Works With Others:**

1. **Agent A Integration:**
   - When: [Under what conditions]
   - How: [How they collaborate]
   - Data Exchange: [What data passes between them]

2. **Agent B Integration:**
   - When: [Under what conditions]
   - How: [How they collaborate]
   - Data Exchange: [What data passes between them]

---

#### Common Questions & Answers

**Q: When should I use this agent?**
A: [Clear answer with examples]

**Q: What's the difference between this and similar agents?**
A: [Comparison and clarification]

**Q: Can it handle [specific scenario]?**
A: [Detailed answer]

**Q: What if it fails?**
A: [Escalation and recovery process]

---

#### Limitations & Boundaries

**What This Agent CAN'T Do:**
- ❌ [Limitation 1]
- ❌ [Limitation 2]
- ❌ [Limitation 3]

**Why:**
[Explain reasoning for limitations]

**Alternative:**
[Suggest alternative agents or approaches]

---

#### Roadmap & Future Improvements

**Current Version (1.0):**
- ✅ Feature A
- ✅ Feature B
- ✅ Feature C

**Planned (v2.0):**
- 🔄 Enhancement 1
- 🔄 Enhancement 2

**Proposed (Future):**
- 💡 Enhancement 3
- 💡 Enhancement 4
```

### Step 5.2: Validation Checklist

Ensure agent is complete and ready:

```markdown
### Agent Validation Checklist

**Specification:**
- [ ] Agent name is unique and descriptive
- [ ] Role clearly distinguishes from other agents
- [ ] Description is 2-3 sentences, clear and compelling
- [ ] Primary expertise specified

**Capabilities:**
- [ ] 5-8 capabilities defined
- [ ] Each uses action verbs
- [ ] Capabilities are distinct (no overlap)
- [ ] User can understand what agent does

**Skills:**
- [ ] 5-8 primary skills selected
- [ ] All skills exist in `.agents/skills/`
- [ ] Skills complement and don't overlap
- [ ] Dependency chain is valid (no circular deps)
- [ ] Coverage validation passed

**Documentation:**
- [ ] Usage template is clear and copy-paste ready
- [ ] At least 2 usage examples provided
- [ ] Common questions answered
- [ ] Limitations documented
- [ ] Integration patterns described

**Quality Checks:**
- [ ] No external links (or links are stable)
- [ ] Code examples are syntactically correct
- [ ] Formatting is consistent
- [ ] Grammar and spelling checked
- [ ] Technical accuracy verified

**Integration:**
- [ ] Workflows identified where agent participates
- [ ] Dependencies on other agents documented
- [ ] No circular agent dependencies
- [ ] Can be tested independently

**Final Review:**
- [ ] Ready for publication
- [ ] Team has reviewed
- [ ] No blocking issues
- [ ] Metrics baseline established
```

---

## Phase 6: Documentation

### Step 6.1: Create Agent Documentation

Document the agent comprehensively:

```markdown
### Documentation Structure

**Folder Structure:**
```
.agents/skills/{agent-name}/
├── SKILL.md                    # Skill definition
├── AGENT_TEMPLATE.md          # Template for creating agents
├── README.md                   # Quick start guide
├── examples/
│   ├── example-1.md
│   ├── example-2.md
│   └── example-3.md
├── troubleshooting.md         # Common issues and solutions
└── roadmap.md                 # Future improvements
```

**Documentation Checklist:**
- [ ] SKILL.md (complete skill definition)
- [ ] README.md (quick start, 5 minute read)
- [ ] Usage examples (at least 3)
- [ ] Troubleshooting guide (common issues)
- [ ] Integration guide (how it works with other agents)
- [ ] Roadmap (future improvements)
```

### Step 6.2: Update Agent Registry

Add agent to the central registries:

```markdown
### Registry Updates

**Update AGENTS_SKILLS.md:**
- [ ] Add agent section
- [ ] List primary skills
- [ ] Provide usage template
- [ ] Include one example

**Update AGENTS_SKILLS_FULL.md:**
- [ ] Add comprehensive profile
- [ ] Include all metadata
- [ ] List all capabilities
- [ ] Document workflow participation
- [ ] Show skill dependency graph

**Update Other Registries:**
- [ ] Update workflow definitions if new workflows
- [ ] Update related agent cross-references
- [ ] Update skill-to-agent indices
```

---

## Complete Template

Here's a complete, copy-paste ready template for an advanced agent:

```markdown
### [AgentName]

**Role:** [One-line role description]

**Description:**
[2-3 sentence explanation of what this agent does and why it matters]

**Primary Expertise:** [Main domain]

**Status:** Stable | Version 1.0 | Last Updated: [Date]

---

#### Capabilities (8 total)

1. **[Capability 1 Name]** - [Brief description of what it does]
2. **[Capability 2 Name]** - [Brief description]
3. **[Capability 3 Name]** - [Brief description]
4. **[Capability 4 Name]** - [Brief description]
5. **[Capability 5 Name]** - [Brief description]
6. **[Capability 6 Name]** - [Brief description]
7. **[Capability 7 Name]** - [Brief description]
8. **[Capability 8 Name]** - [Brief description]

---

#### Primary Skills

- `skill-1` - [What it teaches and contributes to this agent]
- `skill-2` - [What it teaches and contributes]
- `skill-3` - [What it teaches and contributes]
- `skill-4` - [What it teaches and contributes]
- `skill-5` - [What it teaches and contributes]
- `skill-6` - [What it teaches and contributes]
- `skill-7` - [What it teaches and contributes]
- `skill-8` - [What it teaches and contributes]

---

#### Focus Areas

- **[Deep expertise 1]:** [Description of deep knowledge]
- **[Deep expertise 2]:** [Description of deep knowledge]
- **[Deep expertise 3]:** [Description of deep knowledge]

---

#### Workflow Integration

**Primary Workflows:**
- `workflow-1` (Step X of Y): [Agent's role in this workflow]
- `workflow-2` (Step X of Y): [Agent's role in this workflow]
- `workflow-3` (Step X of Y): [Agent's role in this workflow]

---

#### Usage Template

\`\`\`
@AgentName
[Context about what you're building]

Task: [Specific task]

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Constraints:
- [Constraint 1]
- [Constraint 2]
\`\`\`

---

#### Real-World Examples

[Include 2-3 complete usage examples with expected responses]

---

#### Integration With Other Agents

- **Collaborates with Agent A:** [How/when they work together]
- **Collaborates with Agent B:** [How/when they work together]
- **Delegates to Agent C:** [When this happens]

---

#### Common Questions

**Q: When should I use this agent?**
A: [Clear answer]

**Q: What if it can't handle my use case?**
A: [Escalation path]

---

#### Metadata

- Response Time: [X-Y minutes]
- Token Usage: [X-Y tokens]
- Success Rate: [X%]
- Last Updated: [Date]
- Maintained By: [Owner]

```

---

## Real-World Examples

### Example 1: Real-Time Data Sync Agent

[Detailed walkthrough of creating a complex agent]

### Example 2: Form Building Agent

[Another detailed example]

### Example 3: Testing Strategy Agent

[Third complex example]

---

## Advanced Patterns

### Pattern 1: Agent Inheritance

Agents can inherit from parent agents...

### Pattern 2: Agent Composition

Agents can delegate to other agents...

### Pattern 3: Multi-Agent Workflows

Agents working together on complex problems...

---

## Summary

This comprehensive template enables you to create enterprise-grade Expert Agents that:

✅ Solve complex problems comprehensively  
✅ Integrate seamlessly with other agents  
✅ Participate in sophisticated workflows  
✅ Are well-documented and maintainable  
✅ Have clear success metrics  
✅ Scale to support large systems  

---

**Next Steps:**
1. Use this template to design your advanced agent
2. Work with team to validate design
3. Implement using the SKILL.md file as guidance
4. Add to AGENTS_SKILLS_FULL.md registry
5. Gather metrics and refine based on usage
6. Document improvements and plan v2.0

---

**Questions?** See related documentation:
- [Simple Agent Template](../agent-generator/AGENT_TEMPLATE.md)
- [AGENTS_SKILLS_FULL.md](../../AGENTS_SKILLS_FULL.md)
- [SKILL.md](./SKILL.md)
