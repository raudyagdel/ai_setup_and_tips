# Agent-Updater Template
## Step-by-Step Guide to Update Existing Expert Agents

**Version:** 1.0  
**Purpose:** Systematic 4-step process to modify agents in AGENTS_SKILLS.md  
**Pair With:** `agent-generator` skill for complete agent lifecycle

---

## Overview

This template guides you through updating existing expert agents in `.agents/AGENTS_SKILLS.md`. Use this when:

- ✅ Adding new skills to existing agents
- ✅ Removing redundant skills
- ✅ Reordering skills by importance
- ✅ Updating role descriptions
- ✅ Enhancing "When to Use" examples
- ✅ Maintaining agent registry consistency

**Process Time:** 10-30 minutes per update

---

## Step 1: Select & Analyze Agent

### 1a. Identify Target Agent

```
1. Open: .agents/AGENTS_SKILLS.md
2. Search for: Agent name (case-sensitive)
3. Review: Current skills and role
4. Check: Last update date (from git history if needed)
5. Understand: Why this agent needs updating
```

### 1b. Analyze Current State

**Use this checklist:**

```markdown
Agent Name: ____________________
Current Skills Count: ___ / 3-8 ✓
Skills Feel: [ ] Focused [ ] Scattered [ ] Perfect
Redundancy Level: [ ] None [ ] Some [ ] High
Role Clarity: [ ] Clear [ ] Vague [ ] Confusing
Example Freshness: [ ] Current [ ] Outdated [ ] Missing
```

### 1c. Create Update Plan

**Document your changes:**

```markdown
UPDATE PLAN for: [Agent Name]

What needs updating?
□ Add **new skill**: __________ (why?)
□ Remove skill: __________ (why redundant?)
□ Reorder skills: __________ (new order)
□ Update role: From "____" To "____"
□ Enhance example: (describe improvement)

Current skill count: ___
Projected skill count: ___ (must stay 3-8)
```

---

## Step 2: Plan Changes

### 2a. Skill Addition

**When adding a skill:**

```
1. Verify skill exists: .agents/skills/[skill-name]/SKILL.md ✓
2. Confirm fit: Does it complement current skills?
3. Check position: Where should it go? (by importance)
4. Write description: 1-2 line explanation of what it contributes
5. Size check: Will agent still have 3-8 skills? ✓
```

**Validation Template:**

```markdown
Skill to Add: `skill-name`
Already exists? YES ✓ / NO ✗
Complements current skills? YES ✓ / NO ✗
Impact on agent focus? (explain)
Proposed position: (1st, 2nd, 3rd, last)
Skill contribution: [1-2 line description]
Final skill count: ___ (verify 3-8)
```

**Example:**
```markdown
Skill to Add: `tailwind-patterns`
Already exists? YES ✓
Complements current skills? YES ✓ (enhances responsive design)
Impact on agent focus? Strengthens UI/UX core without dilution
Proposed position: 2nd (right after interface-design)
Skill contribution: Utility-first styling and responsive design patterns
Final skill count: 5 (within range ✓)
```

### 2b. Skill Removal

**When removing a skill:**

```
1. Confirm redundancy: Why is this skill redundant?
2. Check impact: Do other agents need this combo?
3. Verify: Is this a true duplicate or complementary?
4. Size check: Will agent still have 3+ skills? ✓
5. Document: Why removal was necessary
```

**Validation Template:**

```markdown
Skill to Remove: `skill-name`
Reason for removal: (explain redundancy)
Confirmed redundant? YES ✓ / NO ✗
Other agents affected? (list agents with this skill)
Impact on agent coverage? (does it still cover domain?)
Final skill count: ___ (verify 3-8)
Safe to remove? YES ✓ / NO ✗
```

### 2c. Skill Reordering

**When reordering skills:**

```
1. List all current skills
2. Rank by importance to agent's PURPOSE
3. Group complementary skills together
4. Review: Does order tell the story of agent?
5. Verify: No other agents' order affected
```

**Template:**

```markdown
Current Order:
1. skill-a
2. skill-b
3. skill-c
4. skill-d

New Order (by importance):
1. skill-d (most critical feature)
2. skill-a (foundation)
3. skill-c (enhancement)
4. skill-b (supplementary)

Reason for reorder: (why does new order make sense?)
```

### 2d. Role Update

**When updating agent role:**

```
Current Role: "____________________________"
New Role:     "____________________________"

Guidelines:
- Keep to exactly ONE line
- Use: Domain + Specialty pattern
- Example: "Frontend Security Expert"
- Avoid: Vague or multi-purpose language
```

### 2e. Example Enhancement

**When improving "When to Use" section:**

```markdown
Current Example:
@AgentName
[old text]

New Example:
@AgentName
[Building context]

[Specific task with updated skills in mind]

Requirements:
- [requirement reflecting new/removed skills]
- [requirement]
- [requirement]
```

---

## Step 3: Validate Consistency

### 3a. Agent Validation Checklist

```markdown
AGENT VALIDATION: [Agent Name]

□ Agent name exists in AGENTS_SKILLS.md
□ Agent name follows conventions ({Domain}Agent, {Domain}Specialist, etc.)
□ Role is exactly ONE line
□ Role uses Domain + Specialty pattern
□ Primary Skills count is 3-8
□ All skills exist in .agents/skills/
□ Each skill has 1-2 line description
□ Skills ordered by importance
□ No skill duplicates within this agent
□ "When to Use" is in code block (```)
□ Example is realistic and updated
□ Formatting matches other agents exactly
```

### 3b. Cross-Agent Validation

```markdown
CROSS-AGENT CHECKS:

□ Does this agent's skills overlap with another agent?
   If YES: Is it intentional and complementary? 
   
□ Is there conflict between agents with same skills?
   If YES: Are roles clearly different?
   
□ Would consolidation improve focus?
   If YES: Document recommendation
   
□ Do related agents have consistent formatting?
   If NO: Update to match
   
□ Are there skill gaps in the overall system?
   If YES: Note for future agent-generator
```

### 3c. Format Validation

**Verify exact format matching:**

```markdown
### AgentName                                ← ### header (3 hashes)
**Role:** One-line role description         ← **Bold** with colon

**Primary Skills:**                          ← **Bold** exact label
- `skill-name` - Description (1-2 lines)   ← - bullet, backticks, hyphen

**When to Use:**                             ← **Bold** exact label
\`\`\`                                       ← Code block (3 backticks)
@AgentName
[example content]
\`\`\`

---                                          ← Separator line
```

---

## Step 4: Update & Implement

### 4a. Format Your Changes

**Prepare the updated agent section:**

```markdown
### AgentName
**Role:** Updated role (keep ONE line)

**Primary Skills:**
- `skill-1` - What this skill brings to the agent
- `skill-2` - What this skill brings to the agent
- `skill-3` - What this skill brings to the agent
- `skill-4` - What this skill brings to the agent (optional)
- `skill-5` - What this skill brings to the agent (optional)

**When to Use:**
\`\`\`
@AgentName
Building a [context: what are they building?]

Task: [specific task with updated skills in mind]

Requirements:
- [requirement 1]
- [requirement 2]
- [requirement 3]
\`\`\`
```

### 4b. Locate in AGENTS_SKILLS.md

```
1. Open: .agents/AGENTS_SKILLS.md
2. Find: ### AgentName (search for exact name)
3. Highlight: Current agent section
4. Identify: Lines to replace (include surrounding context)
5. Prepare: Replacement text from 4a above
```

### 4c. Apply Changes

**Using text editor or git:**

Option 1: Manual replacement
```
1. Select entire agent section (including ### header)
2. Delete old section
3. Paste new section
4. Verify formatting and spacing
```

Option 2: Use string replacement (if using tools)
```
Find: [entire old agent section - include 3-5 lines context]
Replace: [entire new agent section - exact same lines]
```

### 4d. Verify Changes

**After updating, check:**

```markdown
FINAL VERIFICATION:

□ Agent section copied correctly
□ No extra blank lines or formatting errors
□ Skill descriptions are clear (1-2 lines max)
□ Role is still ONE line
□ "When to Use" example is complete and formatted
□ Numbering of agents unchanged (e.g., ### 1, ### 2, etc.)
□ Separator (---) present and correct
□ No duplicate agents
□ Cross-referencing still works
□ Matches style of nearby agents
```

### 4e. Update File Metadata

**Update the top of AGENTS_SKILLS.md:**

```markdown
# Agent-to-Skills Mapping Configuration
## Automated Expert System for Angular Frontend Development

**Version:** 1.1  ← INCREMENT VERSION
**Status:** Authoritative – defines how agents access skills  
**Last Updated:** 2026-02-06  ← UPDATE DATE
```

### 4f. Document Changes

**Add to git commit message:**

```
Update: Add [skill-name] to [AgentName]

- Added `skill-name`: [brief description of why]
- Reordered skills by importance
- Enhanced "When to Use" example
- Updated version to 1.1

Skills now: [old count] → [new count]
Validation: All checks passed ✓
```

---

## Common Update Scenarios

### Scenario 1: Add `tailwind-patterns` to Responsive Agent

**Agent:** UXAgent  
**Change:** Add `tailwind-patterns` skill

```markdown
### 4. UXAgent
**Role:** UI/UX & Accessibility Expert  
**Primary Skills:**
- `interface-design` - Dashboard, admin panels, interactive products
- `tailwind-patterns` - Utility-first styling, responsive design patterns ← NEW
- `tailwind-mobile-first` - Mobile-first UX patterns
- `angular-component` - Component architecture for accessibility
- `tailwindcss-advanced-layouts` - Layout patterns for good UX

**When to Use:**
\`\`\`
@UXAgent
Redesigning the settings dashboard for accessibility.

Task: Implement responsive design with utility-first styling

Requirements:
- Mobile-first responsive layout
- WCAG 2.1 AA compliance
- Keyboard navigation support
- Dark mode support
- Touch-friendly interactive elements
\`\`\`
```

**Changes:**
- ✅ Added `tailwind-patterns` after `interface-design`
- ✅ Still 5 skills (within range)
- ✅ Updated example to reflect styling focus
- ✅ Version bumped (update file header)

### Scenario 2: Reorder AngularAgent Skills

**Agent:** AngularAgent  
**Change:** Move `angular-signals` to position 1

```markdown
### 2. AngularAgent
**Role:** Angular Framework Specialist  
**Primary Skills:**
- `angular-signals` - Signals, computed(), linkedSignal(), effects ← MOVED TO TOP
- `angular-component` - Standalone components, signals inputs/outputs
- `angular-best-practices` - Modern Angular 21+ patterns
- `angular-development` - Expert Angular and TypeScript development
- `angular-routing` - Lazy loading, guards, route configuration
- `angular-forms` - Signal Forms API, validation, dynamic forms
- `angular-http` - HttpClient, resource(), data fetching
- `angular-directives` - Custom directives, host directives
- `typescript` - Strong typing, generics, advanced patterns

**When to Use:**
\`\`\`
@AngularAgent
Implement a product list component with filtering and pagination.
Use signals for state, OnPush change detection, and standalone components.
\`\`\`
```

**Changes:**
- ✅ Signals moved to most important position
- ✅ All 9 skills maintained
- ✅ Example already emphasizes signals
- ✅ Version updated

### Scenario 3: Remove Redundant Skill

**Agent:** IconsAgent  
**Change:** Remove `tailwind-css-patterns` (superseded by `tailwind-patterns`)

```markdown
### 11. IconsAgent
**Role:** Icon Management & Implementation Expert  
**Primary Skills:**
- `tailwind-patterns` - Icon styling patterns and responsive handling
- `interface-design` - Icon selection and placement
- `tailwindcss-fundamentals-v4` - Dark mode icon support
- `angular-component` - Icon component patterns

**When to Use:**
\`\`\`
@IconsAgent
Implement icons across all navigation items using @hugeicons/angular.
Ensure dark mode support, proper sizing, and accessibility labels.
\`\`\`
```

**Changes:**
- ✅ Removed `tailwind-css-patterns` (redundant with `tailwind-patterns`)
- ✅ Reduced from 5 to 4 skills (still within range)
- ✅ Improved agent focus
- ✅ Version updated

---

## Update Checklist (Quick Reference)

**Before committing:**

```markdown
□ Target agent identified
□ Changes documented with clear reasoning
□ All skills verified to exist
□ Skill count within 3-8 range
□ Skills ordered by importance
□ Format matches other agents exactly
□ "When to Use" example is realistic
□ Role is one line with Domain + Specialty pattern
□ No skill overlap issues identified
□ Formatting validation passed
□ Version number incremented
□ Last updated date refreshed
□ Commit message written
```

---

## Next Steps

1. **Select an agent** to update from AGENTS_SKILLS.md
2. **Follow the 4 steps** (Select, Plan, Validate, Update)
3. **Use the checklist** to verify before committing
4. **Reference examples** if unsure about format
5. **Test agent** by asking it a question with updated skills

**Questions?**
- Creating new agents? → Use [agent-generator](../agent-generator/AGENT_TEMPLATE.md)
- Need skill details? → Check `.agents/skills/{skill-name}/SKILL.md`
- Understand update methodology? → Review [agent-updater SKILL.md](./SKILL.md)

---

**Ready to update an agent?** Pick one from AGENTS_SKILLS.md and follow the 4 steps! 🚀
