# Project Instructions

This project uses a structured workflow for feature development with Claude Code.

## Context Files

Before starting work, read these context files:

| File | Purpose |
|------|---------|
| `.context/PRODUCT.md` | Product overview - what this project is about |
| `.context/TECH.md` | Technical context - architecture, conventions, environment |
| `.context/SESSION.md` | Current work context - what's in progress (gitignored) |
| `backlog.md` | Planned, in-progress, and completed work items |
| `specs/` | Feature specifications |

## Available Slash Commands

| Command | Description |
|---------|-------------|
| `/new-feature` | Document a new feature through iterative conversation |
| `/plan-feature [spec-path]` | Generate implementation phases from a spec |
| `/update-commit` | Sync docs, update tracking, and commit (no prompts) |
| `/yolo-push` | Sync, commit, push, and merge to main (no review) |

## Workflow

### Starting New Work

1. **Define the feature:** Run `/new-feature` to document what you're building
2. **Plan implementation:** Run `/plan-feature` to break it into phases
3. **Implement:** Work through phases, using `.context/SESSION.md` to track progress

### Committing Work

- **With review:** Use standard git workflow
- **Auto-sync:** Run `/update-commit` to sync docs and commit automatically
- **Ship it:** Run `/yolo-push` to push and merge to main

## Key Principles

1. **PRODUCT.md** is stable - rarely changes, describes what the product is
2. **TECH.md** is stable - describes architecture and conventions
3. **SESSION.md** is ephemeral - branch-local, gitignored, tracks current work
4. **backlog.md** tracks all work - planned, in-progress, and done
5. **specs/** contains feature documentation - created by `/new-feature`

## Conventions

See `.context/TECH.md` for project-specific conventions including:
- Code style and naming
- File organization
- Git workflow
- Environment setup
