# Agent Generator Skill

**Version:** 2.0
**Purpose:** Create and configure Expert Agent definitions with specialized skill sets
**Framework:** Individual Agent Definition Files (.agents/agents/*.md)
**Status:** Active

---

## Overview

The **Agent Generator Skill** enables you to:

✅ Create new Expert Agent definition files in `.agents/agents/`
✅ Automatically detect and suggest skills from `.agents/skills/`
✅ Map agents to their underlying skills intelligently
✅ Generate standardized agent markdown files
✅ Maintain consistency across all agent definitions
✅ Create usage examples and collaboration patterns

**Key Change in v2.0:** Uses individual agent files (e.g., `AngularAgent.md`) instead of centralized AGENTS_SKILLS.md registry.

---

## When to Use This Skill

Use the Agent Generator when:

- ✅ Creating a new Expert Agent for a specific domain
- ✅ Analyzing available skills for agent creation
- ✅ Generating agent definition files
- ✅ Planning agent skill combinations
- ✅ Setting up agent collaboration patterns
- ✅ Creating agent documentation

---

## Core Concepts

### What is an Expert Agent?

An Expert Agent combines **multiple skills** into a specialized problem-solver:

```
Expert Agent = {
  name: string,              // e.g., "APIIntegrationAgent"
  type: string,              // e.g., "API Integration & HTTP Specialist"
  role: string,              // What does this agent do?
  primary_skills: Skill[],   // Which skills power it? (3-8 skills)
  when_to_use: string[],     // Clear use cases
  usage_examples: Example[], // 3+ practical examples
  collaboration: Agent[],    // Which agents work well together
  output_format: string[]    // What to expect from responses
}
```

### Agent Definition File Structure

Each agent is defined in `.agents/agents/{AgentName}.md`:

```markdown
# AgentName

**Agent Type:** {Specialization}
**Status:** Active
**Version:** 1.0

## Role
{Detailed role description with responsibilities}

## Primary Skills
- [`skill-name`](../skills/skill-name/SKILL.md) - Description

## When to Use
{List of use cases}

## Usage Examples
{3+ realistic examples}

## Collaboration
{Which agents work well together}

## Output Format
{What to expect from this agent}
```

---

## Process: Creating a New Agent

### Step 1: Identify the Domain

What problem domain does your agent address?

**Examples:**
- ❌ Too broad: "Frontend Development"
- ✅ Specific: "Real-Time Data Synchronization"
- ✅ Specific: "Accessibility Compliance & WCAG"

### Step 2: Discover Available Skills

**Automatic Skill Discovery:**
```bash
# List all available skills
ls -1 .agents/skills/

# Read skill descriptions
grep -r "^description:" .agents/skills/*/SKILL.md
```

**Skill Selection Framework:**
- Coverage: Do skills cover the domain completely?
- Complementarity: Do skills work well together?
- Relevance: Are all skills necessary for this domain?
- Count: 3-8 skills (not too few, not too many)

### Step 3: Define Agent Metadata

**Agent Naming Convention:**
- Pattern: `{Domain}{Type}Agent`
- Examples: `StateManagementAgent`, `PerformanceOptimizationAgent`
- Avoid: `HelperAgent`, `GenericAgent`, `Agent`

**Agent Type:**
- One-line specialization description
- Format: "{Domain} {Specialty}"
- Examples: "Frontend Performance Optimization Expert"

### Step 4: Map Skills to Agent

**For each skill, document:**
```markdown
- [`skill-name`](../skills/skill-name/SKILL.md) - What this skill contributes to the agent
```

**Example:**
```markdown
## Primary Skills

- [`angular-signals`](../skills/angular-signals/SKILL.md) - Signal-based reactive state management
- [`angular-component`](../skills/angular-component/SKILL.md) - Standalone components with signals
- [`angular-best-practices`](../skills/angular-best-practices/SKILL.md) - Modern Angular 21+ patterns
```

### Step 5: Create Usage Examples

Provide 3+ realistic examples showing:
- Context (what are they building?)
- Task (what do they need?)
- Expected outcome

**Example Format:**
```markdown
### Example 1: Component Creation
\`\`\`
@AgentName
Create a product list component with filtering and pagination.
Use signals for state and OnPush change detection.
\`\`\`
```

### Step 6: Define Collaboration

List which agents work well together:
```markdown
## Collaboration

Works well with:
- **ArchitectAgent** - For architectural decisions
- **TailwindAgent** - For styling implementation
- **TestingAgent** - For test coverage
```

---

## Command: Create New Agent

### Using Agent Generator

```
@AgentGenerator
Create new expert agent

Agent Name: {YourAgentName}
Domain: {Problem domain}
Specialization: {Specific expertise area}

Role Description:
{2-3 sentence description of agent's responsibilities}

Skills to Include:
- skill-name-1 (explain why)
- skill-name-2 (explain why)
- skill-name-3 (explain why)
- skill-name-4 (explain why)

Use Cases:
- {Use case 1}
- {Use case 2}
- {Use case 3}

Example Usage:
{Provide realistic scenario}

Collaborates With:
- {Agent 1}
- {Agent 2}
```

### Agent Generator Will:

1. ✅ Validate agent name follows conventions
2. ✅ Check that all skills exist in `.agents/skills/`
3. ✅ Verify skill count (3-8 skills)
4. ✅ Generate agent definition file
5. ✅ Create skill links with descriptions
6. ✅ Format usage examples
7. ✅ Add collaboration section
8. ✅ Save to `.agents/agents/{AgentName}.md`
9. ✅ Update `.agents/agents/README.md` index

---

## Agent Definition Template

```markdown
# {AgentName}

**Agent Type:** {Domain} {Specialty}
**Status:** Active
**Version:** 1.0

---

## Role

{Agent specialization} responsible for:
- {Responsibility 1}
- {Responsibility 2}
- {Responsibility 3}
- {Responsibility 4}
- {Responsibility 5}

---

## Primary Skills

This agent has access to the following skills:

- [\`skill-1\`](../skills/skill-1/SKILL.md) - What skill-1 provides
- [\`skill-2\`](../skills/skill-2/SKILL.md) - What skill-2 provides
- [\`skill-3\`](../skills/skill-3/SKILL.md) - What skill-3 provides
- [\`skill-4\`](../skills/skill-4/SKILL.md) - What skill-4 provides

---

## When to Use

Use this agent when you need to:

✅ {Use case 1}
✅ {Use case 2}
✅ {Use case 3}
✅ {Use case 4}
✅ {Use case 5}

---

## Usage Examples

### Example 1: {Scenario Name}
\`\`\`
@{AgentName}
{Context: What are they building?}

{Task: What do they need?}
\`\`\`

### Example 2: {Scenario Name}
\`\`\`
@{AgentName}
{Different scenario}
\`\`\`

### Example 3: {Scenario Name}
\`\`\`
@{AgentName}
{Another scenario}
\`\`\`

---

## Collaboration

Works well with:
- **{Agent1}** - For {what}
- **{Agent2}** - For {what}
- **{Agent3}** - For {what}

---

## Output Format

When responding, this agent will:
1. {Expected output 1}
2. {Expected output 2}
3. {Expected output 3}
4. {Expected output 4}
5. {Expected output 5}

---

**Last Updated:** {YYYY-MM-DD}
```

---

## Best Practices

### ✅ DO

- ✅ Keep agents focused on one domain
- ✅ Use 3-8 skills per agent
- ✅ Name agents descriptively (not generic names)
- ✅ Update `.agents/agents/README.md` after creating
- ✅ Link to actual skill files
- ✅ Provide realistic usage examples
- ✅ Define clear collaboration patterns
- ✅ Use consistent formatting

### ❌ DON'T

- ❌ Create generic agents ("HelperAgent")
- ❌ Add unrelated skills
- ❌ Link to non-existent skills
- ❌ Skip usage examples
- ❌ Use vague descriptions
- ❌ Overlap heavily with existing agents
- ❌ Exceed 8 skills (loses focus)
- ❌ Go below 3 skills (insufficient expertise)

---

## File Organization

After creating an agent:

```
.agents/
├── agents/
│   ├── README.md                    ← Update index
│   ├── YourNewAgent.md              ← New agent file
│   ├── AngularAgent.md
│   ├── TailwindAgent.md
│   └── ...
└── skills/
    ├── skill-1/
    │   └── SKILL.md
    ├── skill-2/
    │   └── SKILL.md
    └── ...
```

---

## Automatic Skill Discovery

The Agent Generator can automatically suggest skills:

**Discovery Process:**
1. Scan `.agents/skills/` directory
2. Read each `SKILL.md` file
3. Extract skill name and description
4. Categorize by domain (Angular, Tailwind, Architecture, etc.)
5. Suggest relevant skills for your agent's domain

**Example Output:**
```
Available Angular Skills:
✓ angular-best-practices - Modern Angular 21+ patterns
✓ angular-signals - Signal-based state management
✓ angular-component - Standalone components
✓ angular-forms - Reactive forms with signals
✓ angular-http - HTTP services and data fetching

Available Tailwind Skills:
✓ tailwind-4 - Tailwind CSS 4 fundamentals
✓ tailwindcss-animations - Animation utilities
✓ tailwind-design-system - Design tokens and themes

Available Architecture Skills:
✓ clean-ddd-hexagonal - DDD + Hexagonal patterns
✓ angular-architecture - Feature-based structure
```

---

## Integration with Agent Updater

**Agent Lifecycle:**

1. **Create** (agent-generator) ← You are here
   - Define domain and skills
   - Generate agent file
   - Add to index

2. **Use & Gather Feedback**
   - Deploy agent
   - Collect usage data

3. **Update** (agent-updater)
   - Add/remove skills
   - Update examples
   - Enhance documentation

4. **Maintain**
   - Regular reviews
   - Keep synchronized with skills

---

## Example: Creating a New Agent

### Request:
```
@AgentGenerator
Create new expert agent

Agent Name: DataVisualizationAgent
Domain: Data Visualization & Charts
Specialization: Chart.js & Interactive Data Display

Role Description:
Expert in creating interactive data visualizations using Chart.js with
Angular integration. Handles chart configuration, real-time updates,
and responsive design.

Skills to Include:
- angular-component (for chart components)
- angular-signals (for reactive data)
- interface-design (for visual design)
- tailwind-css-patterns (for styling)

Use Cases:
- Create dashboard charts
- Implement real-time data visualization
- Design responsive chart layouts
- Configure Chart.js with Angular

Collaborates With:
- AngularAgent (for component implementation)
- TailwindAgent (for styling)
- StateAgent (for data management)
```

### Generated Output:
Creates `DataVisualizationAgent.md` with:
- Proper header and metadata
- Role description
- 4 mapped skills with links
- Clear use cases
- 3 usage examples
- Collaboration section
- Output format expectations

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0 | 2026-02-09 | Moved to individual agent files format |
| 1.0 | 2026-02-06 | Initial release with AGENTS_SKILLS.md |

---

## Support

When using this skill, provide:

1. **Agent name** - Descriptive, follows conventions
2. **Domain** - Clear problem area
3. **Available skills** - From `.agents/skills/`
4. **Use cases** - Real-world scenarios
5. **Collaboration needs** - Which agents work together

---

## See Also

- [Agent Updater](../agent-updater/SKILL.md) - Update existing agents
- [Agents Directory](../../agents/README.md) - All agent definitions
- [Skills Directory](../) - Available skills

---

**Ready to create an agent?** Use the command format above and specify your domain!
