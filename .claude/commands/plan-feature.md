---
description: Generate implementation plan from a feature spec
---

# Plan Feature Command

Generate an implementation plan with phases from a feature specification and save it to `.context/SESSION.md`.

**Input:** `$ARGUMENTS` - Path to the feature spec file (e.g., `specs/milestone-tracking.md`)

## Before You Start

Read `.context/TECH.md` to understand the codebase structure, conventions, and architecture context.

## Process

### Step 1: Read the Feature Spec

Read the spec file at `$ARGUMENTS`. If the path doesn't include a directory, assume it's in `specs/`.

If the file doesn't exist or wasn't provided:
- List available specs in `specs/`
- Ask user to select one or provide a path

### Step 2: Analyze the Spec

Read the spec thoroughly and identify:
- **Core functionality** - What are the main capabilities?
- **Data requirements** - Database schema, types, migrations needed?
- **UI components** - What screens/components need to be built or modified?
- **Integrations** - External services, APIs, or internal systems involved?
- **Dependencies** - What existing code/services does this build on?

### Step 3: Generate Implementation Phases

Break down the feature into logical implementation phases. Each phase should:
- Be completable in a single session (1-4 hours of work)
- Have a clear deliverable that can be tested
- Build on previous phases incrementally

**Phase Structure Guidelines:**

1. **Database/Schema Phase** (if needed)
   - Migrations, types, basic service methods

2. **Core Service Layer** (if needed)
   - Business logic, API integrations

3. **UI Foundation**
   - Basic components, layouts, navigation

4. **UI Polish & Interactions**
   - Forms, modals, validation, error states

5. **Integration Phase** (if needed)
   - External services, AI models, third-party APIs

6. **Testing & Edge Cases**
   - Manual testing, edge case handling

7. **Cleanup & Documentation**
   - Remove deprecated code, update docs

### Step 4: Present Plan to User

Show the proposed implementation plan:

```
## Implementation Plan: [Feature Name]

**Spec:** [path/to/spec.md]
**Estimated Phases:** [N]

### Phase 1: [Phase Name]
- Task 1
- Task 2
- Task 3
**Deliverable:** [What can be tested after this phase]

### Phase 2: [Phase Name]
- Task 1
- Task 2
**Deliverable:** [What can be tested after this phase]

[... more phases ...]

---

Does this plan look good? I can:
1. Adjust the scope or ordering of phases
2. Add/remove phases based on your priorities
3. Proceed to save this plan to .context/SESSION.md
```

### Step 5: Save to SESSION.md

After user approval, create/update `.context/SESSION.md` with the implementation plan:

```markdown
# Current Session State

**Last Updated:** [DATE]
**Current Focus:** [Feature Name]
**Branch:** `[suggested-branch-name]`

---

## [Feature Name]

**Spec:** [specs/feature-name.md](specs/feature-name.md)

### Overview

[Brief 1-2 sentence description from spec]

### Implementation Phases

- [ ] **Phase 1: [Name]** - [Brief description]
- [ ] **Phase 2: [Name]** - [Brief description]
- [ ] **Phase 3: [Name]** - [Brief description]
[...]

### Phase 1: [Name] (Current)

**Tasks:**
- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

**Deliverable:** [What can be tested]

**Key Files:**
- `path/to/file1`
- `path/to/file2`

---

## Context

**Key Decisions:**
- [Any architectural decisions made during planning]

**Blockers:**
- [Any known blockers or dependencies]
```

### Step 6: Update Backlog

Update `/backlog.md`:
- Move the feature from "Planned" to "In Progress"
- Add the branch name

### Step 7: Confirm Completion

Tell the user:
```
Implementation plan saved to .context/SESSION.md

Next steps:
1. Create feature branch: git checkout -b [branch-name]
2. Start Phase 1: [First task description]

Ready to begin implementation?
```

## Important Notes

- **Don't over-engineer phases** - Keep phases focused and achievable
- **Consider dependencies** - Order phases so each builds on the previous
- **Include integration phases separately** - External integrations often need their own phase for testing
- **Be realistic** - A typical feature should have 3-7 phases, not 15
- **Ask clarifying questions** - If the spec is ambiguous, ask before planning
- **SESSION.md is gitignored** - It's branch-local tactical context, not committed
