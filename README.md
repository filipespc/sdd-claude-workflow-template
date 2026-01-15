# Claude Workflow Template

A template for structured feature development with Claude Code.

## What's Included

```
├── .claude/
│   ├── CLAUDE.md              # Project instructions for Claude
│   └── commands/
│       ├── new-feature.md     # Document new features
│       ├── plan-feature.md    # Generate implementation plans
│       ├── update-commit.md   # Auto-sync docs and commit
│       └── yolo-push.md       # Ship to main (no review)
├── .context/
│   ├── PRODUCT.md             # Product overview (stable)
│   ├── TECH.md                # Technical context (stable)
│   └── SESSION.md             # Current work context (gitignored)
├── specs/                     # Feature specifications
├── backlog.md                 # Work tracking
└── .gitignore
```

## Quick Start

1. **Copy this template** to your project
2. **Fill in context files (preferably using Claude Code):**
   - `.context/PRODUCT.md` - What your product is
   - `.context/TECH.md` - How it's built
3. **Start working** with the slash commands

## Workflow

### Define → Plan → Build → Ship

```
/new-feature          Create a feature spec through conversation
        ↓
/plan-feature         Break spec into implementation phases
        ↓
    [implement]       Work through phases
        ↓
/update-commit        Sync docs and commit
        ↓
/yolo-push            Push and merge to main
```

## Slash Commands

### `/new-feature`

Start an interactive conversation to document a new feature. Creates a spec in `specs/` and updates `backlog.md`.

**Use when:** You have a new feature idea and want to define it properly before coding.

### `/plan-feature [spec-path]`

Generate implementation phases from a feature spec. Saves the plan to `.context/SESSION.md`.

**Use when:** You have a spec and want to break it into actionable phases.

**Example:** `/plan-feature specs/user-auth.md`

### `/update-commit`

Automatically sync documentation with code changes, update tracking files, and commit. No prompts - code is always right.

**Use when:** You've finished work and want to commit with docs synced.

### `/yolo-push`

Like `/update-commit` but also pushes to origin and merges to main. No code review.

**Use when:** You're feeling confident and want to ship immediately (which can be often).

**Note:** Bypasses code review.

## Context Files

### `.context/PRODUCT.md` (committed)

Describes **what** your product is:
- Product overview
- Feature areas
- User personas

Keep this stable. Only update when the product vision changes.

### `.context/TECH.md` (committed)

Describes **how** your project is built:
- Architecture relationships and gotchas
- Naming and code conventions
- Environment setup

Keep this stable. Update when architecture or conventions change.

### `.context/SESSION.md` (gitignored)

Tracks **current work in progress**:
- Current phase and tasks
- Key files being modified
- Blockers and decisions

This is ephemeral and branch-local. Created by `/plan-feature`, updated by `/update-commit`.

### `backlog.md` (committed)

Tracks all work items:
- **Planned** - Ready to start
- **In Progress** - Currently being worked on
- **Done** - Completed

Each item has: Name, Type (feature/bug/improvement), Description, Spec link.

### `specs/` (committed)

Feature specifications created by `/new-feature`. Each spec includes:
- Overview
- User stories
- UX/UI flows
- Acceptance criteria
- Edge cases

## Customization

### Different main branch

If you use `master` instead of `main`, update `.claude/commands/yolo-push.md`.

### Additional documentation

If your project has specific documentation (API docs, architecture docs, etc.), update `.context/TECH.md` to list where they live. The `/update-commit` command will check those locations.

### Project-specific conventions

Fill in `.context/TECH.md` with your actual:
- Naming conventions
- File organization
- Git workflow
- Environment details

## Philosophy

1. **Stable context** - PRODUCT.md and TECH.md rarely change
2. **Ephemeral session** - SESSION.md is disposable, branch-local
3. **Code is truth** - Docs sync to match code, not the other way around
4. **Explicit tracking** - backlog.md shows all work, specs/ documents features
5. **Slash commands** - Collaborate with Claude in a structured way.
