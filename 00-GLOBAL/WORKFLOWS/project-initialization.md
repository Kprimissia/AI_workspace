# Workflow: Project Initialization

## 1. Objective

Define a standardized process for analyzing, understanding and preparing a new software project.

The objective is to establish a reliable foundation for development by identifying project requirements, architecture, technologies, dependencies, configuration and initial tasks.

The agent must understand the project before making significant modifications.

## 2. When to Use

Use this workflow when:

- Starting a new software project.
- Opening an unfamiliar repository.
- Joining an existing development team.
- Initializing a development environment.
- Analyzing an existing application before making changes.
- Preparing a repository for development.
- Migrating a project to a new environment.
- Organizing an initial development plan.

## 3. Execution Process

### Phase 1 — Understand the Project

Identify the fundamental information about the project.

Determine:

- Project name.
- Main objective.
- Problem being solved.
- Target users.
- Main functionalities.
- Project scope.
- Current development stage.
- Team structure, when documented.
- Expected deliverables.

Read any requirements, specifications or existing project documentation.

Separate confirmed information from assumptions.

Do not invent requirements or technical decisions.

**Deliverable:** Initial project understanding.

### Phase 2 — Inspect the Repository

Inspect the repository before making changes.

Check:

- Root directory.
- Existing folder structure.
- `AGENTS.md` files.
- README and documentation.
- Source code.
- Configuration files.
- Dependency manifests.
- Existing tests.
- Environment examples.
- Git branches and history.
- Existing integrations.

Identify whether the repository is:

- Empty.
- Partially initialized.
- An existing application.
- A project under active development.
- A repository containing multiple applications or services.

Do not overwrite or replace existing project structures without understanding their purpose.

**Deliverable:** Repository analysis.

### Phase 3 — Identify the Technology Stack

Identify the technologies actually used.

Consider:

- Programming languages.
- Frameworks.
- Runtime versions.
- Package managers.
- Build tools.
- Databases.
- API technologies.
- Testing frameworks.
- Infrastructure.
- Deployment platforms.
- External integrations.

Use configuration files and source code as evidence.

Examples include:

- `package.json`
- `tsconfig.json`
- `vite.config.ts`
- `pom.xml`
- `requirements.txt`
- `pyproject.toml`
- `Dockerfile`
- `docker-compose.yml`

Do not assume that a technology is being used simply because it is common for that type of application.

**Deliverable:** Verified technology inventory.

### Phase 4 — Understand the Architecture

Identify the current architectural organization.

When applicable, inspect:

- Front-end structure.
- Back-end structure.
- API communication.
- Database organization.
- Authentication.
- Authorization.
- Business logic.
- External services.
- Shared modules.
- Infrastructure.

Identify the responsibility of important directories and modules.

For repositories containing multiple applications, establish which parts belong to each application.

Do not propose a complete architectural replacement without a clear technical reason.

**Deliverable:** Architecture overview.

### Phase 5 — Identify Project Constraints

Identify important restrictions and dependencies.

Consider:

- Team ownership.
- Repository boundaries.
- Technologies that must be preserved.
- Existing API contracts.
- Required integrations.
- Security requirements.
- Academic or institutional requirements.
- Deployment restrictions.
- Development environment limitations.
- Project deadlines, when confirmed.

Clearly document what the agent is authorized to modify.

**Deliverable:** Project constraints and boundaries.

### Phase 6 — Verify the Development Environment

Determine what is required to execute the project.

Inspect:

- Required runtime versions.
- Dependencies.
- Installation commands.
- Environment variables.
- Configuration files.
- Database requirements.
- External services.
- Build commands.
- Development commands.
- Test commands.

When authorized, verify whether the environment can be initialized successfully.

Do not install unnecessary software or modify system configuration without justification.

Never invent environment variables, credentials or connection strings.

**Deliverable:** Environment setup instructions and verification status.

### Phase 7 — Verify Git and Collaboration

Inspect the repository's Git configuration.

When applicable, check:

```bash
git status
git branch --show-current
git branch -a
git log --oneline -10
git remote -v
```

Identify:

- Current branch.
- Existing branches.
- Remote repositories.
- Recent commits.
- Uncommitted changes.
- Collaboration conventions.

Do not change branches, discard changes, create commits or push without authorization.

Protect existing contributions from other developers.

**Deliverable:** Git and collaboration assessment.

### Phase 8 — Identify Risks and Missing Information

Identify uncertainties that could affect development.

Consider:

- Incomplete requirements.
- Missing API documentation.
- Unknown database structure.
- Unavailable credentials.
- Missing dependencies.
- Unclear responsibilities.
- Incomplete infrastructure.
- Security concerns.
- Conflicting documentation.
- Unverified integrations.

Classify important items as:

- **Confirmed:** supported by available evidence.
- **Assumption:** plausible but not verified.
- **Pending:** requires information or a decision.
- **Risk:** may negatively affect project execution.

Do not silently convert assumptions into confirmed facts.

**Deliverable:** Initial risk and uncertainty register.

### Phase 9 — Prepare the Project Structure

Only when required and authorized, prepare or improve the project structure.

Consider:

- Source directories.
- Component organization.
- Service organization.
- Configuration.
- Tests.
- Documentation.
- Environment examples.
- Git ignore rules.
- Development scripts.

Respect existing architecture and conventions.

Do not create unnecessary folders, abstractions or dependencies simply to make the project appear more sophisticated.

**Deliverable:** Prepared project structure, when applicable.

### Phase 10 — Create the Initial Development Plan

Translate the project's objectives into an actionable plan.

Identify:

- Initial technical tasks.
- Essential functionalities.
- Dependencies.
- Priorities.
- Potential blockers.
- Validation requirements.
- Documentation needs.
- Suggested milestones.

Break large objectives into small tasks with clear acceptance criteria.

Do not invent deadlines, estimates or responsibilities.

**Deliverable:** Initial backlog and development plan.

### Phase 11 — Validate the Initial Setup

When the environment is ready and execution is authorized, perform relevant checks.

Consider:

- Dependency installation.
- Development server startup.
- Application initialization.
- Database connectivity.
- API availability.
- Existing tests.
- Linting.
- Type checking.
- Production build.

Record the actual commands executed and their results.

Distinguish between an environment that is configured, an application that starts successfully and a system whose functionality has been validated.

These are different levels of verification.

**Deliverable:** Initial environment validation report.

### Phase 12 — Final Project Assessment

Present the results using the following structure:

#### Project Overview
Name, objective and current stage.

#### Repository
Location and relevant structure.

#### Technology Stack
Technologies verified in the project.

#### Architecture
Summary of the current organization.

#### Development Environment
Prerequisites, setup instructions and validation status.

#### Git and Collaboration
Repository state, branches and relevant conventions.

#### Constraints
Authorized scope and project restrictions.

#### Risks and Pending Information
Uncertainties, blockers and decisions required.

#### Initial Development Plan
Recommended tasks and priorities.

#### Validation
Commands executed and actual results.

#### Conclusion
Classify the project as:

- **Ready for Development**
- **Ready with Pending Items**
- **Partially Prepared**
- **Blocked**

## 4. Special Situations

### Empty Repository

Do not immediately create a complete application.

First understand the requirements, identify the intended architecture and propose a suitable initial structure.

### Existing Application

Preserve the current implementation.

Understand the architecture and existing conventions before proposing changes.

### Multiple Repositories

Identify the responsibility of each repository and how they communicate.

Do not mix front-end and back-end responsibilities without authorization.

### Incomplete Requirements

Document missing information and ask focused questions when the missing details prevent reliable implementation.

### Existing Team Contributions

Inspect current changes and avoid modifying files that may belong to another developer.

## 5. Mandatory Rules

- Never modify a project before understanding its structure.
- Never assume the technology stack.
- Never invent requirements or architecture.
- Never overwrite existing work without justification.
- Never install unnecessary dependencies.
- Never expose credentials or sensitive information.
- Never change Git history without authorization.
- Never assume integrations are operational without verification.
- Always inspect applicable `AGENTS.md` files.
- Always identify project boundaries.
- Always distinguish facts from assumptions.
- Always report the actual environment validation results.

## 6. Completion Criteria

Project initialization may be considered complete when:

- The project's objective is understood.
- The repository has been inspected.
- The technology stack has been identified.
- The architecture has been analyzed.
- Project boundaries have been documented.
- Development prerequisites are understood.
- Git status has been inspected.
- Important risks and uncertainties have been identified.
- An initial development plan has been prepared.
- Relevant environment validations have been performed or their limitations documented.

## 7. Guiding Principle

Understand before building.

A well-initialized project gives the development team a clear view of what exists, what needs to be done, which restrictions must be respected and how work should begin.