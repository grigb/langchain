---
format_version: 1.0
migrated_from: agents-md-split
migration_date: 2026-02-26T19:57:49
project_name: langchain
project_updated: 2026-02-26T19:57:49
---

# PROJECT-RULES.md

> **This file contains project-specific rules and configuration.**
> Universal agent rules are in `AGENTS.md` (immutable global copy).
> Agents: Read `AGENTS.md` first, then this file.

<!-- MIGRATION-MARKER: format=split-v1 -->

## Quick Decision Guide (AGENTS.md vs PROJECT-RULES.md)

1. `AGENTS.md` = universal rules (immutable, identical across projects).
2. `PROJECT-RULES.md` = this project's configuration and conventions.
3. Modes: keep a short stub in `AGENTS.md`, put full workflow in an external mode file.
4. Project identity (name/description) lives in `PROJECT-RULES.md`.
5. Build/test/dev commands live in `PROJECT-RULES.md`.
6. Repo structure and module boundaries live in `PROJECT-RULES.md`.
7. Coding style and testing expectations live in `PROJECT-RULES.md`.
8. Infra rules (ports, daemons, services) live in `PROJECT-RULES.md`.
9. Discovered patterns, quirks, and known issues live in `PROJECT-RULES.md`.
10. If unsure: default to `PROJECT-RULES.md`.

## Project-Specific Infrastructure Rules

[Add infrastructure rules specific to this project here.
Example: critical service rules, daemon management, port assignments.]

## Repository Guidelines

What goes here:
- What this repo is for (one paragraph)
- Constraints / non-goals
- Any "must know" rules for contributors and agents

[Replace with project-specific content - describe repository purpose, philosophy, approach]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#repository-guidelines`

## Project Structure & Module Organization

What goes here:
- High-level directory map
- Key modules/services and their boundaries
- Where to add new code vs refactor existing

[Replace with project-specific directory structure]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#project-structure--module-organization`

## Build, Test, and Development Commands

What goes here:
- Install dependencies
- Start dev server / run locally
- Run tests (unit/integration/e2e) + any required env
- Lint/format/typecheck/build commands

[Replace with project-specific commands]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#build-test-and-development-commands`

## Coding Style & Naming Conventions

What goes here:
- Naming conventions (files, symbols)
- Code patterns (error handling, logging, tracing)
- Style and formatting expectations (and formatter command)

[Replace with project-specific conventions]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#coding-style--naming-conventions`

## Testing Guidelines

What goes here:
- Testing philosophy (what must be tested)
- Required frameworks and how to run
- Flaky test notes and stability requirements

[Replace with project-specific testing requirements]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#testing-guidelines`

## Project Overview

What goes here:
- One-paragraph overview
- Users / stakeholders
- Key features and priorities

[Replace with project overview]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#project-overview`

## Project Phase & Current Status

What goes here:
- Current phase (discovery/build/launch/etc)
- Active focus, blockers, and near-term plan

[Replace with current status]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#project-phase--current-status`

## Architecture Overview

What goes here:
- High-level architecture diagram (optional)
- Key components/services and data flow
- Deployment/runtime notes

[Replace with architecture overview]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#architecture-overview`

## Repository Structure

What goes here:
- Important directories and what belongs there
- Conventions for docs, tests, scripts

[Replace with actual repository structure]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#repository-structure`

## Key Documentation

What goes here:
- Canon docs to read first
- Any required onboarding docs
- Links/paths to specs, ADRs, etc

[Replace with key documentation paths]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#key-documentation`

## Development Commands

What goes here:
- Common dev workflows (db migrate, seed, start services)
- Troubleshooting commands

[Replace with project-specific development commands]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#development-commands`

## Future Development

What goes here:
- Roadmap bullets (next 1-3 milestones)
- Known follow-ups and refactors

[Replace with roadmap / future work]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#future-development`

## Module Integration Points

What goes here:
- External APIs and integrations
- Service boundaries and contracts
- Shared schemas / message formats

[Replace with module integration points]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#module-integration-points`

## Research Methodology

What goes here:
- How research is captured and validated
- Citation/link capture rules
- Output expectations for research docs

[Replace with project research methodology]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#research-methodology`

## Team Workflow

What goes here:
- How work is requested/approved (PRs, reviews, WOs)
- Communication norms and escalation paths

[Replace with team workflow]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#team-workflow`

## Important Notes

What goes here:
- Known gotchas
- Env quirks
- "Don’t do X" rules

[Replace with important notes]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#important-notes`

## Agent-Specific Instructions

What goes here:
- Any special instructions for agents in this repo
- Constraints and guardrails beyond the universal rules

[Replace with agent-specific instructions]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#agent-specific-instructions`

## AI Document Migration Status

What goes here:
- Whether the repo has migrated to `.dev/ai/` conventions
- Any legacy locations still in use

[Replace with AI document migration status]

**Examples:** `~/.agents/templates/PROJECT-SECTIONS-EXAMPLES.md#ai-document-migration-status`

## Discovered Patterns & Conventions

[Agents: append project-specific patterns discovered during implementation work.]

## Known Issues & Quirks

[Agents: append known issues, flaky tests, CI quirks, environment gotchas.]

## Custom Mode Configuration

[Agents: document project-specific mode behavior or overrides, if any.]

## Legacy CLAUDE.md Content

### Migrated from CLAUDE.md (2026-03-14-21-19-27)

Previous CLAUDE.md content extracted during sync.
Backup: `/Users/grig/work/peermesh/repo/peermesh-core/.dev/reference-repos/applications/langchain/.dev/ai/agents-backup/CLAUDE-2026-03-14-21-19-27.md`

# Global development guidelines for the LangChain monorepo

This document provides context to understand the LangChain Python project and assist with development.

## Project architecture and context

### Monorepo structure

This is a Python monorepo with multiple independently versioned packages that use `uv`.

```txt
langchain/
├── libs/
│   ├── core/             # `langchain-core` primitives and base abstractions
│   ├── langchain/        # `langchain-classic` (legacy, no new features)
│   ├── langchain_v1/     # Actively maintained `langchain` package
│   ├── partners/         # Third-party integrations
│   │   ├── openai/       # OpenAI models and embeddings
│   │   ├── anthropic/    # Anthropic (Claude) integration
│   │   ├── ollama/       # Local model support
│   │   └── ... (other integrations maintained by the LangChain team)
│   ├── text-splitters/   # Document chunking utilities
│   ├── standard-tests/   # Shared test suite for integrations
│   ├── model-profiles/   # Model configuration profiles
│   └── cli/              # Command-line interface tools
├── .github/              # CI/CD workflows and templates
├── .vscode/              # VSCode IDE standard settings and recommended extensions
└── README.md             # Information about LangChain
```

- **Core layer** (`langchain-core`): Base abstractions, interfaces, and protocols. Users should not need to know about this layer directly.
- **Implementation layer** (`langchain`): Concrete implementations and high-level public utilities
- **Integration layer** (`partners/`): Third-party service integrations. Note that this monorepo is not exhaustive of all LangChain integrations; some are maintained in separate repos, such as `langchain-ai/langchain-google` and `langchain-ai/langchain-aws`. Usually these repos are cloned at the same level as this monorepo, so if needed, you can refer to their code directly by navigating to `../langchain-google/` from this monorepo.
- **Testing layer** (`standard-tests/`): Standardized integration tests for partner integrations

### Development tools & commands**

- `uv` – Fast Python package installer and resolver (replaces pip/poetry)
- `make` – Task runner for common development commands. Feel free to look at the `Makefile` for available commands and usage patterns.
- `ruff` – Fast Python linter and formatter
- `mypy` – Static type checking
- `pytest` – Testing framework

This monorepo uses `uv` for dependency management. Local development uses editable installs: `[tool.uv.sources]`

Each package in `libs/` has its own `pyproject.toml` and `uv.lock`.

```bash
# Run unit tests (no network)
make test

# Run specific test file
uv run --group test pytest tests/unit_tests/test_specific.py
```

```bash
# Lint code
make lint

# Format code
make format

# Type checking
uv run --group lint mypy .
```

#### Key config files

- pyproject.toml: Main workspace configuration with dependency groups
- uv.lock: Locked dependencies for reproducible builds
- Makefile: Development tasks

#### Commit standards

Suggest PR titles that follow Conventional Commits format. Refer to .github/workflows/pr_lint for allowed types and scopes.

#### Pull request guidelines

- Always add a disclaimer to the PR description mentioning how AI agents are involved with the contribution.
- Describe the "why" of the changes, why the proposed solution is the right one. Limit prose.
- Highlight areas of the proposed changes that require careful review.

## Core development principles

### Maintain stable public interfaces

CRITICAL: Always attempt to preserve function signatures, argument positions, and names for exported/public methods. Do not make breaking changes.

**Before making ANY changes to public APIs:**

- Check if the function/class is exported in `__init__.py`
- Look for existing usage patterns in tests and examples
- Use keyword-only arguments for new parameters: `*, new_param: str = "default"`
- Mark experimental features clearly with docstring warnings (using MkDocs Material admonitions, like `!!! warning`)

Ask: "Would this change break someone's code if they used it last week?"

### Code quality standards

All Python code MUST include type hints and return types.

```python title="Example"
def filter_unknown_users(users: list[str], known_users: set[str]) -> list[str]:
    """Single line description of the function.

    Any additional context about the function can go here.

    Args:
        users: List of user identifiers to filter.
        known_users: Set of known/valid user identifiers.

    Returns:
        List of users that are not in the known_users set.
    """
```

- Use descriptive, self-explanatory variable names.
- Follow existing patterns in the codebase you're modifying
- Attempt to break up complex functions (>20 lines) into smaller, focused functions where it makes sense

### Testing requirements

Every new feature or bugfix MUST be covered by unit tests.

- Unit tests: `tests/unit_tests/` (no network calls allowed)
- Integration tests: `tests/integration_tests/` (network calls permitted)
- We use `pytest` as the testing framework; if in doubt, check other existing tests for examples.
- The testing file structure should mirror the source code structure.

**Checklist:**

- [ ] Tests fail when your new logic is broken
- [ ] Happy path is covered
- [ ] Edge cases and error conditions are tested
- [ ] Use fixtures/mocks for external dependencies
- [ ] Tests are deterministic (no flaky tests)
- [ ] Does the test suite fail if your new logic is broken?

### Security and risk assessment

- No `eval()`, `exec()`, or `pickle` on user-controlled input
- Proper exception handling (no bare `except:`) and use a `msg` variable for error messages
- Remove unreachable/commented code before committing
- Race conditions or resource leaks (file handles, sockets, threads).
- Ensure proper resource cleanup (file handles, connections)

### Documentation standards

Use Google-style docstrings with Args section for all public functions.

```python title="Example"
def send_email(to: str, msg: str, *, priority: str = "normal") -> bool:
    """Send an email to a recipient with specified priority.

    Any additional context about the function can go here.

    Args:
        to: The email address of the recipient.
        msg: The message body to send.
        priority: Email priority level.

    Returns:
        `True` if email was sent successfully, `False` otherwise.

    Raises:
        InvalidEmailError: If the email address format is invalid.
        SMTPConnectionError: If unable to connect to email server.
    """
```

- Types go in function signatures, NOT in docstrings
  - If a default is present, DO NOT repeat it in the docstring unless there is post-processing or it is set conditionally.
- Focus on "why" rather than "what" in descriptions
- Document all parameters, return values, and exceptions
- Keep descriptions concise but clear
- Ensure American English spelling (e.g., "behavior", not "behaviour")

## Additional resources

- **Documentation:** https://docs.langchain.com/oss/python/langchain/overview and source at https://github.com/langchain-ai/docs or `../docs/`. Prefer the local install and use file search tools for best results. If needed, use the docs MCP server as defined in `.mcp.json` for programmatic access.
- **Contributing Guide:** [`.github/CONTRIBUTING.md`](https://docs.langchain.com/oss/python/contributing/overview)

