# Agent Updater Skill

**Version:** 2.0
**Purpose:** Update, enhance, and maintain existing expert agent definition files
**Framework:** Individual Agent Files (.agents/agents/*.md)
**Pair With:** `agent-generator` skill for complete agent lifecycle
**Status:** Active

---

## Overview

The **Agent Updater** skill provides systematic approaches to modify existing expert agents in `.agents/agents/`. This complements the `agent-generator` skill which creates NEW agents.

**Key Use Cases:**
- ✅ Add new primary skills to existing agents
- ✅ Remove redundant or underutilized skills
- ✅ Update agent role descriptions
- ✅ Reorder skills by importance
- ✅ Enhance usage examples
- ✅ Update collaboration patterns
- ✅ Maintain consistency across agents
- ✅ Archive or deprecate agents

**Key Change in v2.0:** Works with individual agent files instead of centralized AGENTS_SKILLS.md registry.

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

| Type | Impact | Frequency | Files Updated |
|------|--------|-----------|---------------|
| **Skill Add** | Enhance capabilities | Regular | Agent .md + README.md |
| **Skill Remove** | Reduce redundancy | Occasional | Agent .md + README.md |
| **Reorder** | Improve priority | Regular | Agent .md |
| **Role Update** | Clarify purpose | Rare | Agent .md + README.md |
| **Example Enhance** | Better guidance | Regular | Agent .md |
| **Version Update** | Track changes | Always | Agent .md |

---

## 4-Step Agent Update Methodology

### Step 1: SELECT & ANALYZE

**Locate the target agent:**
```bash
# List all agents
ls -1 .agents/agents/*.md

# Read specific agent
cat .agents/agents/AngularAgent.md

# Check agent metadata
head -20 .agents/agents/AngularAgent.md
```

**Validation Checklist:**
- ✅ Agent file exists in `.agents/agents/`
- ✅ Agent follows naming conventions
- ✅ Current skills are still relevant
- ✅ Role description is accurate
- ✅ Usage examples are current
- ✅ Version number is tracked

### Step 2: PLAN CHANGES

**Determine what to update:**

**Option A: Add New Skill**
```
Purpose: Enhance agent with complementary skill
Process:
1. Verify skill exists in `.agents/skills/{skill-name}/`
2. Confirm skill complements current skills
3. Write skill description (what it contributes)
4. Choose insertion position (by importance)
5. Update agent version number
```

**Option B: Remove Skill**
```
Purpose: Reduce redundancy or scope creep
Process:
1. Verify skill is truly redundant
2. Confirm no overlap issues with other agents
3. Check agent still has 3+ skills remaining
4. Plan removal and update agent
5. Update agent version number
```

**Option C: Reorder Skills**
```
Purpose: Prioritize by importance
Process:
1. List skills in order of importance
2. Put most critical skills first
3. Group complementary skills together
4. Ensure logical flow
5. Update agent version number
```

**Option D: Update Role/Description**
```
Purpose: Clarify agent purpose
Process:
1. Keep role focused and specific
2. Update responsibilities list
3. Match existing agent style
4. Update agent version number
```

**Option E: Enhance Examples**
```
Purpose: Provide better guidance
Process:
1. Update context (realistic scenarios)
2. Refresh task descriptions
3. Add current requirements
4. Keep examples actionable
```

### Step 3: VALIDATE CONSISTENCY

**Check cross-impacts:**
```
1. Skill Overlap - Does this overlap with another agent?
   → Check other agent files for conflicts

2. Completeness - Does agent still have 3-8 skills?
   → Too few (< 3) = loses focus
   → Too many (> 8) = loses specialization

3. Complementarity - Do all skills work together?
   → Skills should complement, not duplicate

4. Coverage - Does agent cover its stated domain?
   → Skills should provide complete expertise

5. Format - Does it match other agents?
   → Verify markdown format consistency
```

**Validation Rules:**
- ✅ 3-8 primary skills (never fewer, rarely more)
- ✅ Each skill has descriptive text
- ✅ Skills link to actual SKILL.md files
- ✅ Role is clear and specific
- ✅ Usage examples are in code blocks
- ✅ Version number incremented
- ✅ Skills ordered by importance
- ✅ "Last Updated" date is current

### Step 4: UPDATE & IMPLEMENT

**Apply changes to agent file:**

```markdown
# AgentName

**Agent Type:** Updated type if needed
**Status:** Active
**Version:** 1.1  ← Increment version

---

## Role

Updated role description if needed

---

## Primary Skills

This agent has access to the following skills:

- [`skill-1`](../skills/skill-1/SKILL.md) - Description  ← Ordered by importance
- [`skill-2`](../skills/skill-2/SKILL.md) - Description
- [`new-skill`](../skills/new-skill/SKILL.md) - Description  ← NEW SKILL
- [`skill-3`](../skills/skill-3/SKILL.md) - Description

---

## When to Use

Updated use cases if needed

---

## Usage Examples

Updated examples if needed

---

## Collaboration

Updated collaboration if needed

---

## Output Format

Updated output format if needed

---

**Last Updated:** 2026-02-09  ← Update date
```

**Implementation Steps:**
1. Open agent file in `.agents/agents/{AgentName}.md`
2. Apply changes one type at a time
3. Increment version number
4. Update "Last Updated" date
5. Verify skill links work
6. Check formatting matches other agents
7. Update `.agents/agents/README.md` if needed
8. Save and commit with clear message

---

## Common Update Patterns

### Pattern 1: Add Complementary Skill

**When:** New skill released that enhances agent capabilities

**Process:**
```bash
# 1. Verify skill exists
ls .agents/skills/new-skill-name/

# 2. Open agent file
# 3. Add to Primary Skills section
# 4. Position by importance
# 5. Increment version
# 6. Update date
```

**Example: Add to UXAgent**
```markdown
## Primary Skills

This agent has access to the following skills:

- [`frontend-design`](../skills/frontend-design/SKILL.md) - Distinctive interface design
- [`interface-design`](../skills/interface-design/SKILL.md) - Dashboard, admin panels
- [`tailwind-patterns`](../skills/tailwind-patterns/SKILL.md) - Responsive design patterns  ← NEW
- [`tailwindcss-mobile-first`](../skills/tailwindcss-mobile-first/SKILL.md) - Mobile-first UX
- [`angular-component`](../skills/angular-component/SKILL.md) - Component architecture
```

### Pattern 2: Remove Redundant Skill

**When:** Skill overlap detected or skill becomes obsolete

**Example: Consolidation**
```markdown
Before: IconsAgent has 6 skills including tailwind-patterns and tailwind-css-patterns
After: IconsAgent has 5 skills (removed tailwind-css-patterns)
Reason: tailwind-patterns is more comprehensive
```

### Pattern 3: Reorder for Priority

**When:** Skills need to reflect current importance

**Example: Reorder AngularAgent**
```markdown
Before:
- angular-component
- angular-best-practices
- angular-development
- angular-routing
- angular-forms
- angular-http
- angular-signals  ← Should be first for Angular 21+
- angular-directives
- typescript

After (reordered by importance):
- angular-signals  ← Most important for modern Angular
- angular-component
- angular-best-practices
- angular-development
- angular-routing
- angular-forms
- angular-http
- angular-directives
- typescript
```

### Pattern 4: Update Role Description

**Before:**
```markdown
## Role

Handles various Angular tasks
```

**After:**
```markdown
## Role

Angular Framework Specialist responsible for:
- Standalone component development
- Signal-based state management
- Reactive forms implementation
- HTTP service integration
- Routing configuration
- Custom directives
- TypeScript patterns
```

### Pattern 5: Enhance Usage Example

**Before:**
```markdown
### Example 1: Component
\`\`\`
@AgentName
Create a component
\`\`\`
```

**After:**
```markdown
### Example 1: Product List Component
\`\`\`
@AngularAgent
Implement a product list component with filtering and pagination.
Use signals for state, OnPush change detection, and standalone components.
\`\`\`
```

---

## Command: Update Agent

### Using Agent Updater

```
@AgentUpdater
Update existing agent

Agent Name: {AgentName}
Agent File: .agents/agents/{AgentName}.md

Update Type: [add_skill | remove_skill | reorder | update_role | update_examples]

Details:
{Specific changes to make}

Skills to Add/Remove:
- {skill-name} (reason)

New Order (if reordering):
1. {skill-1}
2. {skill-2}
3. {skill-3}

Reason for Update:
{Why are you making this change?}
```

### Agent Updater Will:

1. ✅ Locate agent file in `.agents/agents/`
2. ✅ Validate proposed changes
3. ✅ Check skill exists (if adding)
4. ✅ Verify skill count (3-8 range)
5. ✅ Apply changes to agent file
6. ✅ Increment version number
7. ✅ Update "Last Updated" date
8. ✅ Update `.agents/agents/README.md` if needed
9. ✅ Provide summary of changes

---

## Update Checklist

Before committing agent updates:

- [ ] **Agent File Found** - File exists in `.agents/agents/`
- [ ] **Changes Identified** - Clear what needs updating and why
- [ ] **Skills Verified** - All skills exist in `.agents/skills/`
- [ ] **Skill Count Valid** - 3-8 primary skills
- [ ] **Links Work** - All `../skills/{name}/SKILL.md` links valid
- [ ] **Descriptions Written** - Each skill has explanation
- [ ] **Ordering Verified** - Skills listed by importance
- [ ] **Format Consistent** - Matches other agent files
- [ ] **No Overlap Issues** - Doesn't duplicate other agents
- [ ] **Examples Updated** - Usage examples are current
- [ ] **Role Clarity** - Role is specific and clear
- [ ] **Version Incremented** - Version number bumped
- [ ] **Date Updated** - "Last Updated" is current
- [ ] **README Updated** - Index updated if needed

---

## Update Safety Practices

**DO:**
- ✅ Update one agent at a time
- ✅ Commit with clear message: "Update: Add X skill to AgentName v1.1"
- ✅ Keep skill descriptions concise
- ✅ Verify all links work
- ✅ Test agent after updates
- ✅ Document why changes were made
- ✅ Increment version number
- ✅ Update date

**DON'T:**
- ❌ Update multiple agents in one commit
- ❌ Add arbitrary skills without purpose
- ❌ Exceed 8 skills per agent
- ❌ Mix formatting styles
- ❌ Remove skills without documenting why
- ❌ Forget to increment version
- ❌ Leave broken skill links

---

## File Structure After Updates

```
.agents/
├── agents/
│   ├── README.md              ← Update if major changes
│   ├── AngularAgent.md        ← Version 1.1 (updated)
│   ├── TailwindAgent.md
│   └── ...
└── skills/
    ├── angular-signals/
    │   └── SKILL.md
    ├── new-skill/             ← Newly added skill
    │   └── SKILL.md
    └── ...
```

---

## Version Management

**Version Numbering:**
- Major update (2.0): Complete rewrite or major role change
- Minor update (1.1): Add/remove skills, significant changes
- Patch update (1.0.1): Fix typos, update examples

**Track Changes:**
```markdown
## Version History (optional section)

| Version | Date | Changes |
|---------|------|---------|
| 1.1 | 2026-02-09 | Added tailwind-patterns skill |
| 1.0 | 2026-02-06 | Initial agent creation |
```

---

## Integration with Agent Generator

**Agent Lifecycle:**

1. **Create** (agent-generator)
   - Define domain and skills
   - Generate agent file
   - Add to index

2. **Use & Gather Feedback**
   - Deploy agent
   - Collect usage data

3. **Update** (agent-updater) ← You are here
   - Add/remove skills
   - Update examples
   - Enhance documentation
   - Increment version

4. **Maintain**
   - Regular reviews
   - Keep synchronized with skills
   - Monitor effectiveness

---

## Real Update Examples

### Example 1: Add Skill to StateAgent

**Command:**
```
@AgentUpdater
Update existing agent

Agent Name: StateAgent
Update Type: add_skill

Skill to Add: angular-forms
Reason: State management often involves form state, and the new
Signal Forms API requires understanding of signal-based form state.

Position: After angular-signals (complementary skill)
```

**Result:**
- StateAgent.md updated
- Version: 1.0 → 1.1
- Skill added in correct position
- Links validated
- Date updated

### Example 2: Remove Redundant Skill

**Command:**
```
@AgentUpdater
Update existing agent

Agent Name: IconsAgent
Update Type: remove_skill

Skill to Remove: tailwind-css-patterns
Reason: Redundant with tailwind-patterns which is more comprehensive

Verify: Agent still has 5 skills (above minimum of 3)
```

**Result:**
- IconsAgent.md updated
- Version: 1.0 → 1.1
- Skill removed
- Still 5 skills remaining
- Date updated

---

## Summary

The **Agent Updater** skill provides:

✅ **Systematic updates** to individual agent files
✅ **Version management** for tracking changes
✅ **Safety checks** to prevent inconsistency
✅ **Clear processes** for all update types
✅ **Integration** with agent-generator
✅ **Validation rules** for consistency
✅ **Real-world examples** for reference

**Result:** Agents stay relevant, focused, and powerful as your skill library evolves.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 2.0 | 2026-02-09 | Moved to individual agent files format |
| 1.0 | 2026-02-06 | Initial release with AGENTS_SKILLS.md |

---

## See Also

- [Agent Generator](../agent-generator/SKILL.md) - Create new agents
- [Agents Directory](../../agents/README.md) - All agent definitions
- [Skills Directory](../) - Available skills

---

**Ready to update an agent?** Use the command format above!
