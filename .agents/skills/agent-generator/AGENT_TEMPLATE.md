# New Expert Agent Template
## Step-by-Step Guide to Create Custom Expert Agents

**Version:** 1.0  
**Purpose:** Simple 5-step process to define new specialized agents with their skill sets

---

## Overview

An **Expert Agent** is a specialized AI assistant that combines multiple focused skills to solve problems in a specific domain.

**Formula:**
```
Expert Agent = Specific Role + Primary Skills + Workflows + Prompt Template
```

---

## Step 1: Define Agent Identity

Create a new section in your agents configuration with these essential fields:

```markdown
### YourAgentName
**Role:** What this agent specializes in (one-line description)

**Description:** Longer explanation of what problems this agent solves
(2-3 sentences max)

**Primary Expertise:** Main area of knowledge (e.g., "State Management", "Security", "Styling")
```

### Example
```markdown
### DataVisualizationAgent
**Role:** Charts, Graphs & Data Visualization Specialist

**Description:** Expert in implementing scalable, accessible data
visualization components using Angular and visualization libraries.
Handles real-time updates, large datasets, and interactive charts.

**Primary Expertise:** Data Visualization in Angular Applications
```

---

## Step 2: List Primary Skills

Skills are the knowledge sources the agent will use. Select from existing skills in `.agents/skills/` directory.

```markdown
**Primary Skills:**
- `skill-name-1` - Brief description of what this skill provides
- `skill-name-2` - Brief description
- `skill-name-3` - Brief description
```

### How to Choose Skills

1. **Identify the domain** - What area does your agent cover?
2. **List 3-6 primary skills** - Start lean, can add more later
3. **Skills should complement each other** - Together they provide complete expertise
4. **Avoid overlapping skills** - Each skill teaches something different

### Example
```markdown
**Primary Skills:**
- `angular-component` - Component structure and lifecycle
- `angular-http` - Data fetching and real-time subscriptions
- `tailwind-css-patterns` - Styling charts and visualizations
- `tailwindcss-animations` - Animating chart transitions
- `interface-design` - Chart design principles and UX
```

---

## Step 3: Describe Agent Role

Write a concise one-line description of the agent's specialty:

```markdown
**Role:** Angular Framework Specialist
```

### Guidelines
- Keep it to ONE line
- Use domain + specialty (e.g., "Frontend Security Expert")
- Avoid vague descriptions
- Should immediately tell developers what this agent does

**Examples:**
- ✅ "Angular Framework Specialist"
- ✅ "Frontend Architecture & Design"
- ✅ "Tailwind CSS & Styling Specialist"
- ❌ "Various things"
- ❌ "Helps with stuff"

---

## Step 4: Create "When to Use" Example

This shows developers how to ask your agent for help. Format as a code block:

```markdown
**When to Use:**
\`\`\`
@AgentName
[Context: What are you building?]

[Specific task or problem]
Requirements:
- [requirement 1]
- [requirement 2]
- [requirement 3]
\`\`\`
```

### Guidelines
- Start with context (what are they building?)
- State the specific task clearly
- Include 2-3 key requirements
- Keep it practical and realistic
- Avoid overly complex scenarios

**Example:**
```markdown
**When to Use:**
\`\`\`
@AngularAgent
I'm implementing an e-commerce checkout flow.

Task: Create a multi-step form with signal-based state management

Requirements:
- Use standalone components
- Real-time validation
- Dark mode support
- Save progress between steps
\`\`\`
```

---

## Step 5: Register Agent in AGENTS_SKILLS.md

Add your agent to `.agents/AGENTS_SKILLS.md` using this exact format:

```markdown
### YourAgentName
**Role:** Short role description

**Primary Skills:**
- `skill-name-1` - What this skill contributes
- `skill-name-2` - What this skill contributes
- `skill-name-3` - What this skill contributes

**When to Use:**
\`\`\`
@YourAgentName
[Your context and task here]
\`\`\`
```

**Important:** Match the exact format used in AGENTS_SKILLS.md:
✅ `### AgentName` - Use ### header
✅ `**Role:**` - One-line description
✅ `**Primary Skills:**` - Bulleted list with skill descriptions
✅ `**When to Use:**` - Code block with usage example

---

## Available Skills Reference

Before creating your agent, review available skills in `.agents/skills/`:

**Angular Skills:**
- `angular-component` - Standalone components, signals, lifecycle
- `angular-best-practices` - Modern Angular 21+ patterns
- `angular-development` - Expert Angular & TypeScript development
- `angular-routing` - Lazy loading, guards, configuration
- `angular-forms` - Signal Forms, validation, reactive patterns
- `angular-http` - HttpClient, resource(), data fetching
- `angular-signals` - Signals, computed(), effects
- `angular-directives` - Custom directives, host directives

**Styling Skills:**
- `tailwind-4` - Tailwind CSS 4 fundamentals
- `tailwind-css-patterns` - Utility-first styling, responsive design
- `tailwind-design-system` - Design tokens, themes
- `tailwindcss-fundamentals-v4` - Installation, configuration
- `tailwindcss-mobile-first` - Mobile-first patterns
- `tailwindcss-animations` - Animation utilities, transitions
- `tailwindcss-advanced-layouts` - Grid, Flexbox patterns

**Architecture Skills:**
- `angular-architecture` - Feature-based architecture, folder structure
- `clean-ddd-hexagonal` - DDD patterns for frontend
- `interface-design` - Dashboard, admin panels, UX

**Other Skills:**
- `typescript` - Strong typing, generics, advanced patterns

---

## Complete Template: Copy & Paste Ready

Use this template to create agents for `.agents/AGENTS_SKILLS.md`:

```markdown
### YourNewAgent
**Role:** Short role description

**Primary Skills:**
- `skill-name-1` - What this skill contributes
- `skill-name-2` - What this skill contributes
- `skill-name-3` - What this skill contributes

**When to Use:**
\`\`\`
@YourNewAgent
Context: What are you building?

Task: What specific problem to solve?
Requirements:
- requirement 1
- requirement 2
- requirement 3
\`\`\`
```

---

## Real Examples from AGENTS_SKILLS.md

### Example 1: AngularAgent (9 skills)
```markdown
### AngularAgent
**Role:** Angular Framework Specialist  
**Primary Skills:**
- `angular-component` - Standalone components, signals inputs/outputs
- `angular-best-practices` - Modern Angular 21+ patterns
- `angular-development` - Expert Angular and TypeScript development
- `angular-routing` - Lazy loading, guards, route configuration
- `angular-forms` - Signal Forms API, validation, dynamic forms
- `angular-http` - HttpClient, resource(), data fetching
- `angular-signals` - Signals, computed(), linkedSignal(), effects
- `angular-directives` - Custom directives, host directives
- `typescript` - Strong typing, generics, advanced patterns

**When to Use:**
\`\`\`
@AngularAgent
Implement a product list component with filtering and pagination.
Use signals for state, OnPush change detection, and standalone components.
\`\`\`
```

### Example 2: TailwindAgent (7 skills)
```markdown
### TailwindAgent
**Role:** Tailwind CSS & Styling Specialist  
**Primary Skills:**
- `tailwind-4` - Tailwind CSS 4 fundamentals and CSS-First architecture
- `tailwind-css-patterns` - Utility-first styling, responsive design
- `tailwind-design-system` - Design tokens, themes, component styling
- `tailwindcss-fundamentals-v4` - Installation, configuration, 2026 best practices
- `tailwindcss-mobile-first` - Mobile-first responsive design patterns
- `tailwindcss-animations` - Animation utilities, transitions
- `tailwindcss-advanced-layouts` - Grid, Flexbox, complex layouts

**When to Use:**
\`\`\`
@TailwindAgent
Style the checkout form component with responsive design, dark mode,
and smooth animations. Use Tailwind utility classes exclusively.
\`\`\`
```

### Example 3: FrontendArchitectAgent (3 skills)
```markdown
### FrontendArchitectAgent
**Role:** Frontend Architecture & Design  
**Primary Skills:**
- `angular-architecture` - Feature-based architecture, folder structure, lazy loading
- `tailwind-design-system` - Design system organization and scalability
- `clean-ddd-hexagonal` - DDD patterns applied to frontend

**When to Use:**
\`\`\`
@FrontendArchitectAgent
Design the folder structure for a new product management feature.
Include routing strategy and component boundaries.
\`\`\`
```

---

## Quick Reference: Agent Creation Checklist

- [ ] **Step 1:** Agent name defined (matches naming conventions)
- [ ] **Step 2:** 3-6 primary skills selected from `.agents/skills/`
- [ ] **Step 3:** One-line role description written
- [ ] **Step 4:** "When to Use" example created with realistic scenario
- [ ] **Step 5:** Agent formatted for AGENTS_SKILLS.md (exact format)
- [ ] **Testing:** Asked the agent a test question to verify it works
- [ ] **Registration:** Added to `.agents/AGENTS_SKILLS.md` alphabetically

---

## Naming Conventions

Use these suffixes to clarify agent types:

```
{DomainName}Agent          → General expert (e.g., APIAgent)
{DomainName}Specialist     → Narrow specialization (e.g., AccessibilitySpecialist)
{DomainName}Architect      → Design/planning focused (e.g., PerformanceArchitect)
{DomainName}ReviewAgent    → Code review focused (e.g., SecurityReviewAgent)
{DomainName}Coach          → Educational focused (e.g., ReactivityCoach)
```

---

## Avoiding Agent Overlap

**Good:** Each agent covers distinct problems
- APIIntegrationAgent ← Data communication
- FormBuilderAgent ← User input handling
- StateManagementAgent ← Application state

**Bad:** Agents solving similar problems
- FormAgent AND FormBuilderAgent ← Too similar
- HttpAgent AND APIAgent ← Overlapping

**Rule of Thumb:** If two agents could answer the same question, consolidate them.

---

## Extending an Existing Agent

To ADD skills to an existing agent:

1. Find the agent in `.agents/AGENTS_SKILLS.md`
2. Identify an existing skill in `.agents/skills/`
3. Add to the **Primary Skills** list:

```markdown
**Primary Skills:**
- `existing-skill-1`
- `existing-skill-2`
- `new-skill-to-add` ← NEW
```

4. Update the agent description if needed
5. Test with a question in that new skill area

---

## Common Mistakes to Avoid

❌ **Too many skills** (10+) - Agent loses focus  
✅ **Right:** 3-6 complementary skills

❌ **Vague usage template** - Hard to ask the agent  
✅ **Right:** Specific example with placeholders

❌ **No capability examples** - Users don't know what agent does  
✅ **Right:** 5-8 action-verb capabilities

❌ **Skills don't exist** - Can't load knowledge  
✅ **Right:** Verify skill exists in `.agents/skills/`

❌ **Duplicate agents** - Confusing for users  
✅ **Right:** Check existing agents first

---

## Summary

Creating an expert agent for AGENTS_SKILLS.md is **5 simple steps**:

1. **Define Identity** - Choose a clear, descriptive name
2. **Add Skills** - Select 3-6 complementary skills from `.agents/skills/`
3. **Write Role** - One-line description of the agent's specialty
4. **Create Example** - Show "When to Use" with realistic scenario
5. **Register Agent** - Add to AGENTS_SKILLS.md in proper format

**Result:** A new expert agent available when developers ask specific questions in your domain.

---

---

## Format Rules for AGENTS_SKILLS.md

**These rules ensure consistency with existing agents:**

✅ **DO:**
- Use exactly 3-6 primary skills
- Provide skill descriptions (explain what it contributes)
- Format "When to Use" as a code block with agent mention
- Keep role description to one line
- Add line breaks between agents

❌ **DON'T:**
- Use **Description:** field (use **Role:** only)
- Mix format styles with other agents
- Forget to include what each skill contributes
- Create vague "When to Use" examples

---

## Step-by-Step: From Template to AGENTS_SKILLS.md

### 1. Choose 3-6 skills
```
Look at your agent's purpose and select complementary skills.
Example: For AngularAgent → select angular-component, angular-signals, angular-http, etc.
```

### 2. Write a one-line role
```
❌ "Complex agent for multiple things"
✅ "Angular Framework Specialist"
```

### 3. Add skill contributions
```
For each skill, explain what it brings to the agent:
- `angular-component` - Standalone components, signals inputs/outputs
- `angular-signals` - Signals, computed(), linkedSignal(), effects
```

### 4. Create usage example
```
Show how developers should ask this agent for help:
@YourAgentName
[Context] Building XYZ
[Task] Implement ABC
[Requirements] - Item 1, - Item 2
```

### 5. Copy into AGENTS_SKILLS.md
```markdown
Add your agent section in alphabetical order by agent name.
Keep consistent spacing and formatting with other agents.
```

---

## Next Steps

1. **Review existing agents** in `.agents/AGENTS_SKILLS.md`
2. **Identify skill gaps** - What domain is missing an agent?
3. **Select primary skills** from the skills reference above
4. **Complete the template** using the format shown
5. **Add to AGENTS_SKILLS.md** in proper location
6. **Test your agent** by asking it a question

**Need ideas?** Check AGENTS_SKILLS.md for these 15 existing agents:
- FrontendArchitectAgent
- AngularAgent
- TailwindAgent
- UXAgent
- StateAgent
- FrontendSecurityAgent
- FrontendPerformanceAgent
- FrontendTestingAgent
- FrontendDevOpsAgent
- FrontendDocumentationAgent
- IconsAgent
- AnimationsAgent
- EnvironmentsAgent
- MockLayerAgent
- ReviewAgent

**Ready to create a new agent?** Follow the 5 steps above and use the template provided.
