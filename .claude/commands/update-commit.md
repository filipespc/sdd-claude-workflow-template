---
description: Sync docs, update tracking files, and commit (no prompts)
---

# Update & Commit Command

Automatically sync documentation with code changes, update all tracking files, and commit everything without asking for permission. This is a streamlined command that always chooses to update docs and never asks for confirmation.

## Key Principles

1. **Code is always right** - Documentation is updated to match code, never the other way around
2. **No prompts** - All decisions are made automatically
3. **Tracking files sync** - Update SESSION.md and backlog.md as needed
4. **Auto-commit** - Stage and commit all changes automatically

## Process

### Step 1: Analyze Code Changes

Run `git diff` to see all staged and unstaged changes. Categorize changes:
- New components/modules added/removed
- New functions/methods added/removed
- Interface/type changes
- Data flow changes
- Database schema changes

### Step 2: Identify Documentation to Update

Read `.context/TECH.md` to understand the project's documentation structure.

Based on code changes, check if any documentation files need updates. The TECH.md file should specify where documentation lives in this project.

### Step 3: Auto-Update Documentation

For each relevant documentation file:
1. Read the current documentation
2. Compare with actual code changes
3. Identify discrepancies
4. **Automatically update documentation to match code** (no asking)

**Discrepancy Resolution (Automatic):**
- Documentation missing new code → Add to docs
- Documentation describes removed code → Remove from docs
- Documentation describes different behavior → Update docs to match code
- Documentation has outdated types/signatures → Update to match code

### Step 4: Update Tracking Files

#### .context/SESSION.md

Clean up SESSION.md automatically:

**Remove (completed/outdated):**
- Completed phases or tasks
- Old decisions or context no longer relevant
- Historical notes not needed for next session

**Keep (still relevant):**
- Current work being done RIGHT NOW
- Immediate next steps (remaining phases)
- Active blockers or issues
- Recent technical decisions affecting current work

**Update:**
- Mark completed phases as done
- Update "Current Phase" to next phase if applicable
- Update "Last Updated" date

#### backlog.md

Update `/backlog.md` when:
- **Feature completed:** Move from "In Progress" to "Done"
- **Feature started:** Move from "Planned" to "In Progress"

### Step 5: Auto-Commit

1. Stage all changes: `git add -A`
2. Generate commit message based on changes:
   - Analyze changed files
   - Create concise summary
   - Format:
     ```
     [type]: [brief description]

     - [Key change 1]
     - [Key change 2]

     Documentation synced: [doc files updated, if any]
     Tracking updated: [SESSION.md, backlog.md as applicable]

     Co-Authored-By: Claude <noreply@anthropic.com>
     ```

3. Commit with generated message

**Commit type selection:**
- `feat:` - New functionality
- `fix:` - Bug fixes
- `refactor:` - Code restructuring
- `docs:` - Documentation only
- `chore:` - Maintenance tasks

### Step 6: Report Results

Show summary of what was done:
```
Documentation synced
  - [list of updated docs, or "none needed"]

Tracking files updated
  - .context/SESSION.md: [summary of changes]
  - backlog.md: [summary of changes, or "no changes needed"]

Changes committed
  Commit: [hash]
  Files: [count] changed, [insertions] insertions(+), [deletions] deletions(-)
```

## When to Use This Command

Use `/update-commit` when:
- You've completed work and want to commit everything
- You want documentation to auto-sync without prompts
- You trust the code is correct and docs should follow
- You want SESSION.md cleaned up automatically

**Don't use this command when:**
- You want to review changes before committing
- You're unsure if code or docs are correct
- You want to manually craft the commit message

## Activation

This command runs when user says:
- "/update-commit"
- "auto commit with docs"
