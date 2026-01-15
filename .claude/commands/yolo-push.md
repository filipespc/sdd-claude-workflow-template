---
description: Sync docs, commit, push, and merge to main (no review)
---

# YOLO Push Command

Syncs documentation with code changes, commits everything, pushes to origin, and merges to the main branch. No confirmations, no review - just ship it.

## Warning

This command bypasses code review entirely. Use only when:
- You're confident the changes are correct
- You've tested locally
- You understand the risks of direct-to-main deployment

## Process

### Step 1: Pre-flight Checks

Before doing anything destructive, verify:

1. Run `git status` to see what will be committed
2. Run `git diff --stat` to show a summary of changes
3. Check for any obvious issues (uncommitted migrations, env files, etc.)

**Report to user:**
```
YOLO Push - Pre-flight Check
=============================
Current branch: [branch-name]
Files to commit: [count]
[git diff --stat output]

Proceeding with YOLO push...
```

### Step 2: Sync Documentation (Auto)

Before committing, automatically sync documentation with code changes. **Code is always right** - docs are updated to match, no prompts.

#### 2a: Analyze Code Changes

Categorize changes from the diff:
- New components/modules added/removed
- New functions/methods added/removed
- Interface/type changes
- Data flow changes
- Database schema changes

#### 2b: Auto-Update Documentation

Read `.context/TECH.md` to understand where documentation lives.

Based on code changes, check and update relevant documentation files.

**Discrepancy Resolution (Automatic):**
- Documentation missing new code → Add to docs
- Documentation describes removed code → Remove from docs
- Documentation describes different behavior → Update docs to match code
- Documentation has outdated types/signatures → Update to match code

#### 2c: Update Tracking Files

**.context/SESSION.md** - Clean up automatically:
- Remove completed phases and old context
- Keep only: current work, immediate next steps, active blockers
- Update phase progress

**backlog.md** - Update when:
- Feature completed → Move to "Done"
- Feature started → Move to "In Progress"

### Step 3: Commit All Changes

1. Stage all changes: `git add -A`
2. Generate commit message based on changes:
   - Analyze changed files
   - Create concise summary
   - Format:
     ```
     [type]: [brief description]

     Files changed:
     - [list of key files]

     Documentation synced: [doc files updated, if any]

     Co-Authored-By: Claude <noreply@anthropic.com>
     ```

3. Commit with generated message

**Commit type selection:**
- `feat:` - New functionality
- `fix:` - Bug fixes
- `refactor:` - Code restructuring
- `docs:` - Documentation only
- `chore:` - Maintenance tasks

### Step 4: Push to Origin

1. Push current branch to origin: `git push -u origin [branch-name]`
2. Report success/failure

### Step 5: Merge to Main

1. Checkout main: `git checkout main`
2. Pull latest: `git pull origin main`
3. Merge the branch: `git merge [branch-name] --no-edit`
4. Push main: `git push origin main`
5. Return to original branch: `git checkout [branch-name]`

**If merge conflict:**
- Report the conflict
- Do NOT force push
- Stop and ask user to resolve manually

### Step 6: Report Results

Show final summary:
```
YOLO Push Complete!
===================
Commit: [hash] - [message]
Docs synced: [list of updated docs, or "none needed"]
Tracking updated: [SESSION.md, backlog.md as applicable]
Pushed to: origin/[branch-name]
Merged to: main

All done. Ship it!
```

## Error Handling

**On any failure:**
1. Report exactly what failed and why
2. Report the current state (which branch, what's committed)
3. Suggest recovery steps
4. Do NOT continue to subsequent steps

**Common failures:**
- No changes to commit → Report "Nothing to commit" and stop
- Push rejected → Pull and retry once, then report if still failing
- Merge conflict → Stop immediately, report conflict, suggest resolution

## Safety Rails

Even in YOLO mode, these things will stop the command:

1. **Merge conflicts** - Must be resolved manually
2. **Force push to main** - Never allowed
3. **Sensitive files detected** - Warn if .env, credentials, secrets are staged

## Customization

To use a different main branch (e.g., `master`), or add a staging branch:
- Update this command file
- Or specify in `.context/TECH.md` under Environment section

## Activation

This command runs when user says:
- "/yolo-push"
- "yolo push"
- "ship it"
