# Technical Context

<!-- 
This file describes HOW this project is built.
Keep it stable - update when architecture or conventions change.
-->

## Architecture Context

<!-- 
Things that aren't obvious from reading the code.
Focus on relationships, patterns, and gotchas.
-->

### How Things Connect

<!-- 
Explain non-obvious relationships between components.
Example: "API requests flow through the auth middleware before reaching controllers"
-->

- [Describe key architectural relationships]

### Gotchas

<!-- 
Things that would trip up someone new to the codebase.
Example: "Don't call the database directly from components, use the service layer"
-->

- [List gotchas and pitfalls]

### Key Abstractions

<!-- 
Core patterns and concepts to understand.
Example: "All data access is scoped by userId via the context"
-->

- [Describe key patterns]

## Conventions

### Naming

<!-- 
How things are named in this project.
-->

- Files: `[convention, e.g., kebab-case]`
- Components: `[convention, e.g., PascalCase]`
- Functions: `[convention, e.g., camelCase]`
- Database tables: `[convention, e.g., snake_case]`

### Git Workflow

- Branch prefix: `[e.g., username/]`
- Main branch: `[main or master]`
- Commit format: `[e.g., conventional commits]`

### Code Organization

<!-- 
Where different types of code live.
-->

- Source code: `[e.g., src/]`
- Tests: `[e.g., src/__tests__/ or tests/]`
- Documentation: `[e.g., docs/]`

## Environment

### Development

- Server: `[e.g., http://localhost:3000]`
- Database: `[local/remote, type]`
- Config: See `.env.example`

### External Services

<!-- 
List external services and their purpose.
Don't include secrets - reference .env.example instead.
-->

| Service | Purpose |
|---------|---------|
| [Service name] | [What it's used for] |

### Deployment

- Production: `[e.g., Vercel, main branch]`
- Staging: `[if applicable]`
