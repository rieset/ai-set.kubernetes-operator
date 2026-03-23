# Project Context: ai-set.kubernetes-operator

This document contains the complete context of the `ai-set.kubernetes-operator` Kubernetes operator project.

## General Information

**Project Type**: Kubernetes Operator (template project, not yet initialized)

**Status**: Template project - operator not yet initialized

**Author**: Albert Iblyaminov

**License**: MIT License

## Current State

### Implemented

- ✅ Project structure template
- ✅ `.cursorrules` with development guidelines
- ✅ Documentation templates in `docs/`
- ✅ README.md with project overview
- ✅ TEMPLATE.md with template information

### Not Implemented

- ❌ Operator initialization (not yet run `operator-sdk init`)
- ❌ API (CRD) - no custom resources defined
- ❌ Controllers - no reconciliation logic
- ❌ Business logic - operator doesn't exist yet
- ❌ Unit tests
- ❌ E2E tests
- ❌ Makefile (will be created after operator initialization)
- ❌ go.mod (will be created after operator initialization)

## Project Structure

```
ai-set.kubernetes-operator/
├── .cursorrules          # Rules for AI assistant
├── .gitignore            # .dev/ and .skills/ are gitignored
├── .golangci.yml         # Linter configuration (version: "2")
├── README.md             # Project overview
├── TEMPLATE.md           # Template project information
├── context.md            # This file - project context
├── docs/                 # Documentation (lowercase kebab-case filenames)
│   ├── best-practices.md
│   ├── function-rating.md
│   ├── glossary.md
│   ├── linting.md
│   ├── logging.md
│   ├── modules.md
│   └── operator-sdk-go-guide.md
├── operator/             # Directory for operator initialization (empty)
├── .dev/                 # In .gitignore — development notes, TZ, implementation plans
│   └── README.md
├── .skills/              # In .gitignore — AI skills for development
│   ├── README.md
│   └── find-skills/
│       └── SKILL.md      # Find skills skill
└── LICENSE               # MIT License
```

## Technology Stack

- **Language**: Go 1.23+ (for development)
- **Framework**: Operator SDK v1.42.0+
- **Target**: Kubernetes Operator
- **Kubernetes**: 1.19+

## Development Rules

### 1. File Size Limits

- **Maximum**: 500 lines per file
- **Modularization required**: Files with 300+ lines MUST be modularized
- **Refactoring**: Files exceeding 500 lines require immediate refactoring

### 2. Function Rating System

Every function MUST have a `FunctionRating` comment. See `docs/function-rating.md` for details.

**Rating Requirements:**
- Functions with score < 60: prioritize for refactoring
- Functions with score < 45: MUST refactor before merging
- Functions with CRITICAL issues: fix immediately

### 3. Linting

- **Tool**: `golangci-lint` v2.1.0
- **Configuration**: `.golangci.yml` (will be created after operator initialization)
- **Mandatory**: Run linting after code generation
- **Auto-fix**: `make lint-fix`
- **Check**: `make lint`

### 4. Logging

- **Library**: `zap` via controller-runtime
- **Format**: Structured logging with color highlighting
- **Time format**: ISO8601
- **Standard fields**: `resourceName`, `namespace`, `host`, `path`
- **Levels**: ERROR (red), INFO (blue), DEBUG (yellow)

### 5. Documentation

- **Language**: All documentation and comments MUST be in English
- **Required**: Comments for all exported functions
- **Location**: Documentation in `docs/` directory
- **Format**: Markdown files

### 6. Code Generation

- **After generation**: MANDATORY linting check
- **Commands requiring linting**:
  - `make generate` - code generation (deepcopy, client)
  - `make manifests` - manifest generation (CRD, RBAC)
  - `operator-sdk generate` - operator code generation
  - `operator-sdk generate kustomize manifests` - Kustomize manifest generation

## Next Steps for Development

### 1. Initialize Operator

```bash
cd operator
operator-sdk init --domain <domain> --repo <repo>
```

**Example:**
```bash
cd operator
operator-sdk init --domain example.com --repo github.com/example/ai-set-operator
```

After initialization, the following will be created:
- Basic project structure
- `go.mod` file with dependencies
- `Makefile` with build and deployment commands
- Kustomize configuration
- Basic test files
- `cmd/main.go` entry point

### 2. Create API and Controller

```bash
cd operator
operator-sdk create api --group <group> --version <version> --kind <Kind> --resource --controller
```

**Example:**
```bash
operator-sdk create api --group ai --version v1alpha1 --kind AISet --resource --controller
```

### 3. Implement Business Logic

- Add reconciliation logic
- Implement business logic
- Add error handling
- Add logging

### 4. Add Tests

- Write unit tests for business logic
- Write E2E tests
- Achieve >80% code coverage

### 5. Documentation

- Update README with operator purpose
- Document API resources
- Add usage examples
- Update `context.md` with new information

## Documentation Files

### Best Practices (`docs/best-practices.md`)

- Code formatting
- Error handling
- Context usage
- Naming conventions
- Documentation requirements
- Reconciliation loop patterns
- Resource management
- Finalizers
- Logging configuration
- Testing practices
- Code structure and modularization
- Function rating system

### Function Rating System (`docs/function-rating.md`)

- Rating format and criteria
- Complexity evaluation
- Integration counting
- External risk assessment
- Test coverage requirements
- Typing evaluation
- Critical issues (hardcode, deep nesting)
- Score calculation
- Refactoring priorities

### Logging Guide (`docs/logging.md`)

- Zap configuration
- Log levels
- Standard fields
- Log filtering
- Production mode

### Linting Guide (`docs/linting.md`)

- golangci-lint setup
- Enabled linters
- CI/CD integration
- Best practices

### Operator SDK Guide (`docs/operator-sdk-go-guide.md`)

- Prerequisites
- Project initialization
- API creation
- Controller creation
- Testing

### Glossary (`docs/glossary.md`)

- Core Kubernetes terms
- Operator SDK terms
- Project-specific terminology

## Important Notes

1. **Project Independence**: This project is independent from other projects in the workspace. Do not use context from other projects.

2. **File Size**: Files must be less than 500 lines. Files with 300+ lines require modularization.

3. **Function Ratings**: All exported functions must have rating comments.

4. **Linting**: Always run linting after code generation.

5. **Documentation**: All documentation must be in English.

6. **Testing**: Write comprehensive unit and E2E tests.

7. **Error Handling**: Always handle errors explicitly with context.

8. **Context Usage**: Always pass `context.Context` as first parameter for I/O operations.

9. **Context File**: Always read and update `context.md` when working on this project.

## Related Projects

This project is part of the `operators` workspace but is **independent**:
- `istio-gas/` - Istio HTTP01 Operator (separate project)
- `istio-dns01-bind9/` - Istio DNS01 Bind9 Operator (separate project)

**Important**: Do not mix context or code between these projects.

## Context File Maintenance

### IMPORTANT: Keep This File Updated

This `context.md` file is the **single source of truth** for project context. It MUST be kept up to date.

**When to Update:**
- After adding new API resources (CRDs)
- After implementing new controllers
- After adding/removing dependencies
- After changing project structure
- After updating configuration
- After adding new documentation
- After changing development workflow
- After updating technical specifications

**How to Update:**
1. Read the current `context.md` file
2. Identify sections that need updating
3. Update relevant sections with new information
4. Update the "Last Updated" date below
5. Ensure all information is accurate and complete

**AI Assistant Instructions:**
- ALWAYS read `context.md` before starting work on this project
- ALWAYS update `context.md` after making significant changes
- Use `context.md` as the primary reference for project state

---

**Last Updated**: 2026-01-XX
**Context Version**: 1.0

