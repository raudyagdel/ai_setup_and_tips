# Agent Generator Skill

**Version:** 1.0  
**Purpose:** Create, configure, and manage Expert Agents with specialized skill sets  
**Framework:** Angular 21+ Development with DDD Architecture  
**Status:** Authoritative

---

## Overview

The **Agent Generator Skill** enables you to:

✅ Create new Expert Agents following best practices  
✅ Add/update capabilities to existing agents  
✅ Map agents to their underlying skills automatically  
✅ Generate agent configuration files  
✅ Maintain AGENTS_SKILLS.md registry  
✅ Create usage prompts and examples  

---

## When to Use This Skill

Use the Agent Generator Skill when:

- ✅ Creating a new Expert Agent for a new domain
- ✅ Adding new capabilities to existing agents
- ✅ Mapping skills to agents in your workspace
- ✅ Maintaining agent documentation (AGENTS_SKILLS.md)
- ✅ Generating agent configuration for CI/CD or automation
- ✅ Planning multi-agent workflows
- ✅ Reviewing agent-skill alignment

---

## Core Concepts

### What is an Expert Agent?

An Expert Agent combines **multiple skills** into a specialized problem-solver:

```
Expert Agent = {
  name: string,              // e.g., "APIIntegrationAgent"
  role: string,              // e.g., "API Integration & HTTP Specialist"
  description: string,       // Why does this agent exist?
  capabilities: string[],    // What can it do?
  primary_skills: string[],  // Which skills power it?
  focus_areas: string[],     // Deep expertise areas
  workflows: string[],       // Which workflows use it?
  prompt_template: string   // How to ask it for help
}
```

### What is a Skill?

A Skill is a **focused knowledge source** that teaches specific patterns:

```
Skill = {
  name: string,              // e.g., "angular-http"
  description: string,       // What does it teach?
  file: string,              // Path to SKILL.md
  domain: string,            // e.g., "Angular", "State Management"
  capabilities: string[]     // What can you learn from it?
}
```

---

## Process: Creating a New Agent

### Step 1: Identify the Domain

What problem domain does your agent address?

**Examples:**
- ❌ Too broad: "Frontend"
- ✅ Specific: "Real-Time Data Synchronization"

- ❌ Too broad: "Styling"
- ✅ Specific: "Dark Mode Theme Management"

### Step 2: Select 3-6 Primary Skills

Search your `.agents/skills/` directory and pick skills that:

1. Cover the domain completely
2. Complement each other (no overlap)
3. Are authoritative and well-maintained

**Skill Selection Framework:**

```
Domain: {Your Domain}

Available Skills:
┌─ Skill 1: {description} ✓ Chosen
├─ Skill 2: {description} ✗ Too overlapping
├─ Skill 3: {description} ✓ Chosen
├─ Skill 4: {description} ✗ Out of scope
└─ Skill 5: {description} ✓ Chosen
```

### Step 3: Define Capabilities

**Turn skills into action verbs:**

| Skill | → | Capability |
|-------|---|------------|
| `angular-signals` | → | "Implement reactive state with signals and computed values" |
| `angular-http` | → | "Set up data fetching with HttpClient and error handling" |
| `interface-design` | → | "Design accessible, responsive layouts" |

**Capability Guidelines:**
- Use action verbs: Create, Build, Implement, Design, Optimize, Review, Audit
- Be specific about *what* the agent can help with
- 5-8 capabilities (not too many)

### Step 4: Create Agent Definition

Name your agent with clear domain indication:

**Good Names:**
- `StateManagementAgent` (clear domain)
- `AccessibilityAuditAgent` (clear action)
- `FormValidationAgent` (clear focus)

**Avoid:**
- `HelperAgent`, `UtilAgent`, `Agent` (too generic)
- `SuperAgent`, `DoEverythingAgent` (scope creep)

### Step 5: Write Usage Prompt

Make it easy for users to ask your agent:

```
@YourAgentName
{What are you building?}

Task: {What do you need help with?}

Requirements:
- {Specific requirement}
- {Specific requirement}

Constraints:
- {Any limitations}
```

### Step 6: Create Workflow Mappings

Identify which workflows benefit from this agent:

```yaml
workflows_using_agent:
  - new_feature_development
  - performance_optimization
  - code_review
```

---

## Command: Create New Agent

Use this command structure to generate a new agent:

```
@AgentGenerator
Create new expert agent

Agent Name: {YourAgentName}
Domain: {Problem domain}
Primary Expertise: {Main knowledge area}

Description: {2-3 sentence description}

Capabilities:
- {Capability 1}
- {Capability 2}
- {Capability 3}
- {Capability 4}
- {Capability 5}

Skills to Map:
- skill-name-1
- skill-name-2
- skill-name-3
- skill-name-4

Focus Areas:
- {Area 1}
- {Area 2}
- {Area 3}

Usage Example:
[Your usage template]
```

---

## Command: Add Capability to Existing Agent

Extend an existing agent with new capabilities:

```
@AgentGenerator
Add capability to existing agent

Agent Name: {AgentName}
New Capability: {capability description}
Supported By Skills: {skill-1, skill-2}
Works in Workflows: {workflow-1, workflow-2}
```

---

## Command: Update Skill Mapping

Reallocate skills between agents:

```
@AgentGenerator
Update skill mapping

Current State:
- Agent A has skills: {skill-1, skill-2}
- Agent B has skills: {skill-3}

Desired State:
- Agent A should have: {skill-1, skill-2, skill-4}
- Agent B should have: {skill-3, skill-5}

Reason: {Why this change?}
```

---

## Command: Generate Agent Registry

Create/update AGENTS_SKILLS.md with full agent inventory:

```
@AgentGenerator
Generate agent registry

Format: Complete registry of all agents
Include: Skills mapping, capabilities, workflows
Output: AGENTS_SKILLS.md (markdown table)
```

---

## Template: New Agent Definition

Copy this template when creating agents:

```markdown
## {AgentName}

**Role:** {One-line role description}

**Description:** {2-3 sentence explanation of expertise and use cases}

**Primary Expertise:** {Main knowledge area}

**Capabilities:**
- "Create/Build/Implement/Design {specific capability}"
- "Create/Build/Implement/Design {specific capability}"
- "Create/Build/Implement/Design {specific capability}"
- "Create/Build/Implement/Design {specific capability}"
- "Create/Build/Implement/Design {specific capability}"

**Primary Skills:**
- `skill-name-1` - What this skill provides to the agent
- `skill-name-2` - What this skill provides to the agent
- `skill-name-3` - What this skill provides to the agent
- `skill-name-4` - What this skill provides to the agent (optional)

**Implementation Focus:**
- Specific area 1
- Specific area 2
- Specific area 3

**Used in Workflows:**
- workflow-name-1
- workflow-name-2
- workflow-name-3

**Usage Template:**

\`\`\`
@{AgentName}
{Context: What are you building?}

Task: {What do you need?}

Requirements:
- {Requirement 1}
- {Requirement 2}
- {Requirement 3}

Constraints: {Any limitations}
\`\`\`

**Example Usage:**

\`\`\`
@{AgentName}
{Real-world example matching your domain}

Task: {Example task}

Requirements:
- {Example requirement 1}
- {Example requirement 2}

Constraints: {Example constraint}
\`\`\`
```

---

## Best Practices

### ✅ DO

- ✅ Keep agents focused (1 primary domain)
- ✅ Use 3-6 skills per agent (not too many, not too few)
- ✅ Name agents after their expertise (not names)
- ✅ Update AGENTS_SKILLS.md after creating agents
- ✅ Document workflow integrations
- ✅ Create clear usage examples
- ✅ Review agent-skill alignment regularly
- ✅ Use action verbs in capabilities
- ✅ Keep descriptions concise (2-3 sentences max)
- ✅ Link agents to existing workflows

### ❌ DON'T

- ❌ Create generic agents ("HelperAgent", "Agent")
- ❌ Add unrelated capabilities to agents
- ❌ Use skills from undocumented sources
- ❌ Forget to update agent registry
- ❌ Create agents without clear workflows
- ❌ Overlap too much with existing agents
- ❌ Skip usage examples
- ❌ Make long, vague descriptions
- ❌ Assume users know how to use your agent

---

## Real-World Examples

### Example 1: Creating a Refactoring Agent

```
Domain: Code Refactoring & Technical Debt

Selected Skills:
✓ angular-best-practices
✓ tailwind-css-patterns
✓ typescript
✓ interface-design

Capabilities:
- "Identify and refactor large components into smaller ones"
- "Convert Observable-based code to Signal patterns"
- "Consolidate and clean up duplicate styling"
- "Suggest TypeScript type improvements"
- "Improve component organization and responsibility"

Workflows:
- code_refactoring
- code_review
- migration
```

### Example 2: Adding Security Capability

```
Existing Agent: AngularAgent
New Capability: "Audit authentication and authorization flows"
Supporting Skills: FrontendSecurityAgent knowledge
Workflows: vulnerability_detection, code_review
```

---

## File Structure

After creating your agent, your workspace should look like:

```
.agents/
├── skills/
│   ├── skill-1/
│   │   └── SKILL.md
│   ├── skill-2/
│   │   └── SKILL.md
│   └── skill-3/
│       └── SKILL.md
├── AGENTS_SKILLS.md          ← Agent registry (auto-generated/updated)
├── AGENT_TEMPLATE.md         ← Template for creating agents
└── agent-generator/
    ├── SKILL.md             ← This file
    └── QUICK_REFERENCE.md   ← Quick commands
```

---

## Outputs Generated

When using the Agent Generator Skill, you get:

1. **Agent Definition** (markdown)
   - Full agent specification
   - Capabilities list
   - Skill mapping
   - Usage template

2. **AGENTS_SKILLS.md Registry** (auto-updated)
   - Complete agent inventory
   - Skill-to-agent mapping
   - Workflow references
   - Quick lookup table

3. **Configuration Files** (optional)
   - YAML agent definitions
   - Workflow integrations
   - Prompt templates

---

## FAQ

**Q: Can I create an agent without skills?**  
A: No. Every agent must map to 2+ existing skills. Otherwise, what is it an expert in?

**Q: How many agents should I have?**  
A: Start with 8-12 focused agents covering your major domains. Add more as needed.

**Q: Can agents share skills?**  
A: Yes! Skills are shared knowledge. Multiple agents can use the same skill.

**Q: What if my domain doesn't have a skill?**  
A: Create the skill first, then create the agent using it.

**Q: How often should I update AGENTS_SKILLS.md?**  
A: After any agent creation, capability addition, or skill changes. Keep it as source of truth.

**Q: Can I modify an existing agent?**  
A: Yes! Add capabilities, update skills, improve documentation. Use the "Add Capability" command.

---

## Quick Commands Summary

| Command | Purpose |
|---------|---------|
| `create_agent` | Create new expert agent from scratch |
| `add_capability` | Add new capability to existing agent |
| `map_skills` | Assign skills to agent |
| `gen_registry` | Generate AGENTS_SKILLS.md |
| `add_workflow` | Link agent to workflows |
| `update_prompt` | Improve usage prompt template |
| `review_alignment` | Check agent-skill fit |

---

## Integration with Your Workspace

This skill works best with:

- **AGENT_TEMPLATE.md** - Reference for creating agents
- **AGENTS_SKILLS.md** - Central registry of all agents (auto-maintained)
- **Skills directory** - `.agents/skills/` contains all skill definitions
- **Your Angular project** - Agents help solve real frontend problems

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-02-06 | Initial release |

---

## Support & Questions

When using this skill, provide:

1. **What agent you're creating** - Name, domain, purpose
2. **Available skills** - List of existing skills to use
3. **Expected workflows** - Where this agent will be used
4. **Real-world example** - How someone would use it

Example question:
```
@AgentGenerator
Create new agent for real-time data synchronization

Existing skills available:
- angular-http
- angular-signals
- interface-design
- tailwindcss-animations

Expected workflows:
- real-time_data_features
- performance_optimization

Example task:
Build a live event feed component showing user activities
```

---

## See Also

- [AGENT_TEMPLATE.md](../AGENT_TEMPLATE.md) - Full template guide
- [AGENTS_SKILLS.md](../AGENTS_SKILLS.md) - Agent registry
- [Skills Directory](../) - Available skills
