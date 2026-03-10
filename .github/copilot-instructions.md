# Copilot Instructions for CI_TestRepo6

## Repository Overview

**CI_TestRepo6** is a minimal test repository used for experimenting with CI/CD pipelines and GitHub Actions workflows. It is owned by `Fabletest4` and currently contains only a `README.md`. There is no application code, build system, or test infrastructure in place yet.

## Repository Structure

```
CI_TestRepo6/
├── .github/
│   └── copilot-instructions.md   # This file
└── README.md                     # Minimal readme ("# CI_TestRepo6")
```

## Key Facts for Efficient Agent Work

- **No build system exists.** Do not assume `npm`, `pip`, `make`, `gradle`, or any other build tool is available. If a task requires adding code, start by deciding on the appropriate language/framework and create the necessary config files (e.g., `package.json`, `requirements.txt`) from scratch.
- **No test infrastructure exists.** If writing tests, create the test runner configuration alongside the tests.
- **No linting or formatting configuration exists.** If adding code, include a linter/formatter config appropriate for the language chosen.
- **No CI/CD workflows exist.** If a task involves CI, create a `.github/workflows/` directory and add the relevant YAML workflow files.
- **The default branch is `main`.** All pull requests should target `main`.
- **There is no `.gitignore`.** Add one when introducing a new language or framework (e.g., `node_modules/`, `__pycache__/`, `dist/`, etc.).

## How to Add New Features

1. **Choose a language/framework** appropriate for the task.
2. **Initialize the project** using the ecosystem's standard tooling:
   - Node.js: `npm init -y`
   - Python: create `pyproject.toml` or `requirements.txt`
   - Go: `go mod init`
3. **Add a `.gitignore`** for the chosen ecosystem.
4. **Write the feature code** in the appropriate directory structure.
5. **Add tests** using the ecosystem's standard testing library.
6. **Add a CI workflow** under `.github/workflows/` that installs dependencies, builds, lints, and tests.
7. **Update `README.md`** with setup and usage instructions.

## CI/CD Guidance

When creating GitHub Actions workflows for this repository:

- Use the `ubuntu-latest` runner for most tasks.
- Pin action versions (e.g., `actions/checkout@v4`) to avoid unexpected breakage.
- Cache dependencies (e.g., `actions/cache@v4`) to speed up runs.
- Run workflows on `push` to `main` and on `pull_request` targeting `main`.

Example workflow skeleton:

```yaml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      # Add language setup, install, lint, test steps here
```

## Known Issues and Workarounds

- **Empty repository:** Because there are no source files, tools that scan existing code (e.g., linters, static analyzers) will produce no output or errors until code is added. This is expected.
- **Copilot agent branches:** When Copilot creates feature branches, they follow the naming convention `copilot/<task-description>`. These branches should always be merged via pull request into `main` and not used as long-lived branches.
- **No package lock files:** Because no dependencies have been installed, there are no lock files. Always commit lock files (`package-lock.json`, `poetry.lock`, etc.) when adding dependencies.

## Coding Conventions

Since the repository has no existing code, follow these general best practices when adding code:

- Keep files small and focused.
- Use clear, descriptive names for files, functions, and variables.
- Add inline comments only where logic is non-obvious.
- Prefer well-known, maintained libraries over custom implementations.
- Validate inputs and handle errors explicitly.
