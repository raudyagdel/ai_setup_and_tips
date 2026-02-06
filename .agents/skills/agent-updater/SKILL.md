# Agent-Updater Skill
## Systematic Updates to Expert Agents in AGENTS_SKILLS.md

**Version:** 1.0  
**Purpose:** Update, enhance, and maintain existing expert agents with new skills and capabilities  
**Pair With:** `agent-generator` skill for complete agent lifecycle management  
**Status:** Live - Use for all agent modifications

---

## Overview

The **Agent-Updater** skill provides a systematic approach to modifying existing expert agents in `.agents/AGENTS_SKILLS.md`. This complements the `agent-generator` skill which creates NEW agents.

**Key Use Cases:**
- ✅ Add new primary skills to existing agents
- ✅ Remove redundant or underutilized skills
- ✅ Update agent role descriptions
- ✅ Reorder skills by importance
- ✅ Enhance "When to Use" examples
- ✅ Maintain consistency across agents
- ✅ Archive or deprecate agents
- ✅ Consolidate overlapping agents

---

## Core Concepts

### Agent Lifecycle
```
CREATE (agent-generator)
  ↓
USE & GATHER FEEDBACK
  ↓
UPDATE (agent-updater) ← You are here
  ↓
MAINTAIN & EVOLVE
  ↓
ARCHIVE (when obsolete)
```

### Update Types

| Type | Impact | Frequency | Tool |
|------|--------|-----------|------|
| **Skill Add** | Enhance capabilities | Regular | agent-updater |
| **Skill Remove** | Reduce redundancy | Occasional | agent-updater |
| **Reorder** | Improve priority | Regular | agent-updater |
| **Role Update** | Clarify purpose | Rare | agent-updater |
| **Example Enhance** | Better guidance | Regular | agent-updater |
| **Deprecate** | Mark as outdated | Rare | agent-updater |
| **Archive** | Remove completely | Very rare | agent-updater |

---

## 4-Step Agent Update Methodology

### Step 1: SELECT & ANALYZE

**Identify the target agent:**
```
1. Find agent name in AGENTS_SKILLS.md
2. Review current primary skills (count should be 3-8)
3. Check last update date or git history
4. Identify what needs updating
```

**Validation Checklist:**
- ✅ Agent exists in AGENTS_SKILLS.md
- ✅ Agent name matches naming conventions
- ✅ Current skills are still relevant
- ✅ Role description is accurate
- ✅ "When to Use" example is realistic

### Step 2: PLAN CHANGES

**Determine what to update:**

**Option A: Add New Skill**
```
Purpose: Enhance agent with complementary skill
Process:
1. Verify skill exists in `.agents/skills/`
2. Confirm skill complements current skills
3. Write skill description (what it contributes)
4. Choose insertion position (first, middle, or last)
```

**Option B: Remove Skill**
```
Purpose: Reduce redundancy or scope creep
Process:
1. Verify skill is truly redundant
2. Confirm no overlap issues with other agents
3. Check if any agents depend on this agent's skill overlap
4. Plan removal order (if removing multiple)
```

**Option C: Reorder Skills**
```
Purpose: Prioritize by importance to the agent
Process:
1. List skills in order of importance
2. Put most critical skills first
3. Group complementary skills together
4. Ensure logical flow
```

**Option D: Update Role/Description**
```
Purpose: Clarify agent purpose or scope
Process:
1. Keep role to ONE line
2. Use domain + specialty pattern
3. Avoid vague language
4. Match existing agent style
```

**Option E: Enhance Example**
```
Purpose: Provide better "When to Use" guidance
Process:
1. Update context (what are they building?)
2. Refresh task description
3. Add current requirements
4. Keep it realistic and actionable
```

### Step 3: VALIDATE CONSISTENCY

**Check cross-impacts:**
```
1. Skill Overlap - Does this skill now overlap with another agent?
   → Check if consolidation is needed
   
2. Completeness - Does agent still have 3-8 skills?
   → Too few (< 3) = loses focus
   → Too many (> 8) = loses specialization
   
3. Complementarity - Do all skills work together?
   → Skills should complement, not duplicate
   
4. Coverage - Does agent cover its stated domain?
   → Skills should provide complete expertise
   
5. Format - Does it match other agents exactly?
   → Verify markdown format consistency
```

**Validation Rules:**
- ✅ 3-8 primary skills (never fewer, rarely more)
- ✅ Each skill has a 1-2 line description
- ✅ Role is exactly one line
- ✅ "When to Use" is in code block format
- ✅ Agent name uses proper naming conventions
- ✅ Skills are listed in order of importance
- ✅ No skill applies to multiple agents (unless truly complementary)

### Step 4: UPDATE & IMPLEMENT

**Apply changes to AGENTS_SKILLS.md:**

```markdown
### AgentName                              ← Keep agent number/order
**Role:** Updated role description        ← Keep focused, one line

**Primary Skills:**
- `skill-1` - Description of contribution  ← Ordered by importance
- `skill-2` - Description of contribution
- `skill-3` - Description of contribution

**When to Use:**                           ← Keep code block format
\`\`\`
@AgentName
[Updated realistic scenario with context, task, requirements]
\`\`\`
```

**Implementation Steps:**
1. Find agent section in AGENTS_SKILLS.md
2. Apply changes one type at a time
3. Verify formatting matches other agents exactly
4. Test by reviewing in context of nearby agents
5. Update version number in file header
6. Commit changes with clear message

---

## Common Update Patterns

### Pattern 1: Add Complementary Skill

**When:** New skill released that enhances agent capabilities

**Process:**
```
Step 1: Identify agent that would benefit
Step 2: Find skill in `.agents/skills/`
Step 3: Add to Primary Skills list
Step 4: Position by importance
Step 5: Write skill description
Step 6: Update agent last-update date
```

**Example: Add to UXAgent**
```markdown
### UXAgent
**Role:** UI/UX & Accessibility Expert  
**Primary Skills:**
- `interface-design` - Dashboard, admin panels, interactive products
- `tailwind-patterns` - Utility-first styling, responsive design patterns  ← NEW
- `tailwind-mobile-first` - Mobile-first UX patterns
- `angular-component` - Component architecture for accessibility
- `tailwindcss-advanced-layouts` - Layout patterns for good UX
```

### Pattern 2: Remove Redundant Skill

**When:** Skill overlap detected or skill becomes obsolete

**Process:**
```
Step 1: Confirm redundancy (skill X is superseded by skill Y)
Step 2: Check other agents (do they rely on this agent having this skill?)
Step 3: Update this agent (remove skill)
Step 4: Update related agents if needed
Step 5: Document why removed
```

**Example: Consolidation**
```markdown
Before: IconsAgent has [tailwind-patterns, tailwind-css-patterns, ...]
After: IconsAgent has [tailwind-patterns, ...]  ← Removed redundant tailwind-css-patterns
Reason: tailwind-patterns is more comprehensive
```

### Pattern 3: Reorder for Clarity

**When:** Skills out of priority order or related skills separated

**Process:**
```
Step 1: List all current skills
Step 2: Rank by importance to agent's core purpose
Step 3: Group complementary skills together
Step 4: Verify no other agents' order affected
Step 5: Update AGENTS_SKILLS.md
```

**Example: Reorder**
```markdown
Before: AngularAgent primary skills
- angular-component
- angular-best-practices      ← Foundation skill
- angular-development
- angular-routing
- angular-forms
- angular-http
- angular-signals             ← Critical for modern Angular
- angular-directives
- typescript

After: AngularAgent primary skills (reordered)
- angular-signals              ← Moved to position 1 (most important for 21+)
- angular-component            ← Standalone components depend on signals
- angular-best-practices       ← Foundation understanding
- angular-development
- angular-routing
- angular-forms
- angular-http
- angular-directives
- typescript
```

### Pattern 4: Update Role & Description

**When:** Agent purpose shifts or clarity needed

**Before:**
```markdown
### SomeAgent
**Role:** Handles various things
```

**After:**
```markdown
### SomeAgent
**Role:** Specialized Expert in Specific Domain
```

**Guidelines:**
- Use domain + specialty (e.g., "Frontend Security Expert")
- Keep to exactly one line
- Be specific (not vague)
- Match existing agent style

### Pattern 5: Enhance Usage Example

**When:** Current example is outdated or unclear

**Before:**
```markdown
**When to Use:**
\`\`\`
@AgentName
Do something
\`\`\`
```

**After:**
```markdown
**When to Use:**
\`\`\`
@AgentName
Building a real-time dashboard for sales tracking.

Task: Create interactive charts with real-time data updates

Requirements:
- WebSocket integration for live updates
- Multiple chart types (bar, line, pie)
- Export to CSV functionality
- Dark mode support
\`\`\`
```

---

## Update Checklist

Before committing agent updates:

- [ ] **Target Agent Found** - Agent exists in AGENTS_SKILLS.md
- [ ] **Changes Identified** - Clear what needs updating and why
- [ ] **Skills Verified** - All skills exist in `.agents/skills/`
- [ ] **Skill Count Valid** - 3-8 primary skills (not fewer, rarely more)
- [ ] **Descriptions Written** - Each skill has explanation of contribution
- [ ] **Ordering Verified** - Skills listed by importance
- [ ] **Format Consistent** - Matches existing agent formatting exactly
- [ ] **No Overlap Issues** - Doesn't duplicate other agents' skills
- [ ] **Example Updated** - "When to Use" is realistic and current
- [ ] **Role Clarity** - One-line role is specific and clear
- [ ] **Version Updated** - Updated version number in file header
- [ ] **Spell Check** - No typos in agent or skill names
- [ ] **Cross-Reference Check** - Links/references still valid

---

## Update Impact Analysis

**Before Updating, Consider:**

### Skill Added
- ✅ Does it complement existing skills?
- ✅ Does agent now have 8+ skills? (might be too many)
- ✅ Do other agents also need this skill?

### Skill Removed
- ✅ Is it truly redundant?
- ✅ Do any developers rely on this skill combo?
- ✅ Should skill be merged with another agent?

### Skills Reordered
- ✅ Does new order reflect importance?
- ✅ Are complementary skills still grouped?

### Role Updated
- ✅ Is old role still used by developers?
- ✅ Should related agents' roles change too?

### Example Changed
- ✅ Is new example realistic?
- ✅ Does it showcase updated skills well?

---

## Update Safety Practices

**DO:**
- ✅ Update one agent at a time
- ✅ Commit with clear message: "Update: Add X skill to AgentName"
- ✅ Keep skill descriptions concise (1-2 lines)
- ✅ Verify formatting before committing
- ✅ Test agent with updated skills
- ✅ Document why changes were made

**DON'T:**
- ❌ Update multiple agents in one commit (hard to review)
- ❌ Add arbitrary skills (must have clear purpose)
- ❌ Exceed 8 skills per agent (creates unfocused agents)
- ❌ Mix formatting styles between agents
- ❌ Remove skills without documenting why
- ❌ Update role without testing agent clarity

---

## Real Update Examples

### Example 1: Add `tailwind-patterns` to UXAgent

**Scenario:** New `tailwind-patterns` skill released with responsive design patterns

**Change:**
```markdown
### UXAgent
**Role:** UI/UX & Accessibility Expert  
**Primary Skills:**
- `interface-design` - Dashboard, admin panels, interactive products
+ `tailwind-patterns` - Utility-first styling, responsive design patterns  ← NEW
- `tailwind-mobile-first` - Mobile-first UX patterns
- `angular-component` - Component architecture for accessibility
- `tailwindcss-advanced-layouts` - Layout patterns for good UX
```

**Validation:**
- ✅ Skill exists in `.agents/skills/`
- ✅ Complements UX focus
- ✅ Still 5 skills (within range)
- ✅ No conflicts with other agents
- ✅ Updated version number

### Example 2: Remove Redundant Skill from IconsAgent

**Scenario:** `tailwind-patterns` is more comprehensive than `tailwind-css-patterns`

**Change:**
```markdown
### IconsAgent
**Role:** Icon Management & Implementation Expert  
**Primary Skills:**
- `tailwind-patterns` - Icon styling patterns and responsive handling
- `tailwind-css-patterns` ← REMOVED (superseded by tailwind-patterns)
- `interface-design` - Icon selection and placement
- `tailwindcss-fundamentals-v4` - Dark mode icon support
- `angular-component` - Icon component patterns
```

**Validation:**
- ✅ Confirmed redundancy
- ✅ No other agents rely on this combo
- ✅ Still 4 skills (within range)
- ✅ Improves agent focus

### Example 3: Reorder AngularAgent Skills

**Scenario:** Angular Signals should be most important for modern Angular 21+

**Change:**
```markdown
### AngularAgent
**Role:** Angular Framework Specialist  
**Primary Skills:**
+ `angular-signals` - Signals, computed(), linkedSignal(), effects  ← MOVED TO TOP
- `angular-component` - Standalone components, signals inputs/outputs
- `angular-best-practices` - Modern Angular 21+ patterns
- `angular-development` - Expert Angular and TypeScript development
- ... (rest of skills)
```

**Validation:**
- ✅ New order reflects importance
- ✅ Signals is foundation for modern Angular
- ✅ Still all 9 skills
- ✅ Updated version number

---

## Integration with Agent-Generator

**Agent Lifecycle:**

1. **Create** (agent-generator)
   - Use AGENT_TEMPLATE.md
   - Follow 5-step creation process
   - Add to AGENTS_SKILLS.md

2. **Use & Gather Feedback**
   - Developers ask the agent
   - Collect feedback on skill gaps

3. **Update** (agent-updater) ← Current skill
   - Add missing skills
   - Remove redundant skills
   - Reorder by importance
   - Enhance examples

4. **Maintain**
   - Regular skill reviews
   - Keep agent sharp and focused
   - Evolution based on usage patterns

5. **Archive** (if needed)
   - Mark obsolete agents
   - Redirect to replacement agents

---

## Summary

The **Agent-Updater** skill provides:

✅ **Systematic approach** to agent modifications  
✅ **Safety checks** to prevent inconsistency  
✅ **Clear processes** for all update types  
✅ **Integration** with agent-generator  
✅ **Validation rules** for consistency  
✅ **Real-world examples** for reference  

**Result:** Agents stay relevant, focused, and powerful as your skill library evolves.

---

**Ready to update an agent?** See [AGENT_TEMPLATE.md](./AGENT_TEMPLATE.md)  
**Creating new agents?** Use [agent-generator](../agent-generator/AGENT_TEMPLATE.md)
