---
name: technical-documentation
description: Creates, reviews and maintains technical documentation for software projects. Use for README files, setup guides, architecture documentation, API references, technical specifications, ADRs, user guides and project documentation.
---

# Technical Documentation

## 1. Objective

Create and maintain accurate, useful and consistent documentation throughout the software development lifecycle.

Documentation must help developers, project members and users understand the system, configure the environment, operate the application and maintain the codebase.

The documentation must reflect the actual implementation, not assumptions or planned functionality.

## 2. Initial Analysis

Before creating or modifying documentation:

1. Read the project's `AGENTS.md` and existing documentation.
2. Inspect the repository structure.
3. Identify the technologies and frameworks actually used.
4. Inspect relevant source code and configuration files.
5. Identify the target audience.
6. Determine the purpose and scope of the documentation.
7. Check whether similar documentation already exists.

Do not duplicate existing documentation unnecessarily.

Do not document functionality as implemented unless the source code or reliable validation confirms it.

## 3. Documentation Principles

All documentation must be:

- Accurate and technically correct.
- Clear and objective.
- Organized into logical sections.
- Consistent with the project's terminology.
- Easy to maintain.
- Appropriate for its target audience.
- Free from unnecessary repetition.
- Explicit about limitations and dependencies.

Use Brazilian Portuguese by default, unless the project or user requests another language.

Prefer practical explanations and examples over vague descriptions.

## 4. README Files

When creating or updating a `README.md`, consider including:

1. Project name.
2. Project description.
3. Main objective.
4. Technologies used.
5. Main features.
6. Repository or directory structure, when useful.
7. Prerequisites.
8. Installation instructions.
9. Environment configuration.
10. Execution commands.
11. Testing instructions.
12. Build instructions.
13. Deployment instructions, when applicable.
14. Team or contribution information, when relevant.

Do not include sections that do not apply.

Commands must be compatible with the actual project configuration.

## 5. Installation and Setup Guides

Setup instructions must allow another developer to reproduce the development environment.

When relevant, document:

- Required software.
- Runtime versions.
- Package managers.
- Dependencies.
- Environment variables.
- Configuration files.
- Database setup.
- External services.
- Installation commands.
- Development commands.
- Troubleshooting.

Use exact commands verified against the project's configuration.

Never invent environment variables, credentials, ports or configuration values.

For sensitive variables, provide placeholders and explain how to configure them securely.

## 6. Architecture Documentation

When documenting architecture, explain the actual organization of the application.

Consider documenting:

- Main architectural components.
- Directory structure.
- Responsibilities of important modules.
- Data flow.
- Application layers.
- External integrations.
- Authentication and authorization.
- Database interactions.
- Communication between front-end and back-end.
- Important architectural decisions.

Use diagrams when they improve understanding.

Possible diagram formats include Mermaid flowcharts, sequence diagrams, entity relationship diagrams and architecture diagrams.

Diagrams must represent verified or explicitly proposed architecture. Clearly distinguish current architecture from planned architecture.

## 7. API Documentation

When documenting an API, verify its implementation or an approved API contract.

For each relevant endpoint, document:

- HTTP method.
- Route.
- Purpose.
- Authentication requirements.
- Required permissions.
- Path parameters.
- Query parameters.
- Request body.
- Response structure.
- HTTP status codes.
- Possible errors.
- Relevant examples.

Use real request and response structures whenever available.

Do not invent endpoints, fields, status codes or authentication requirements.

If the API contract is incomplete, explicitly identify missing information.

## 8. Technical Specifications

When writing technical specifications, organize the information into:

- Context.
- Problem or requirement.
- Objective.
- Scope.
- Functional requirements.
- Non-functional requirements.
- Business rules.
- Technical constraints.
- Dependencies.
- Acceptance criteria.
- Risks.
- Open questions.

Separate confirmed requirements from assumptions and proposals.

Avoid presenting unapproved decisions as established project requirements.

## 9. Architecture Decision Records (ADR)

For important architectural decisions, use an Architecture Decision Record.

Recommended structure:

# ADR-XXX: Decision title

## Status
Proposed, Accepted, Rejected, Superseded or Deprecated.

## Context
Explain the problem and circumstances that require a decision.

## Decision
Describe the selected approach.

## Alternatives Considered
List relevant alternatives and their trade-offs.

## Consequences
Explain benefits, limitations, risks and maintenance implications.

## References
Include relevant documentation, issues or technical discussions.

Do not create an ADR for every minor implementation detail.

## 10. User Documentation

When documenting application usage, write for the actual user rather than the developer.

Include:

- Purpose of the feature.
- Access requirements.
- Navigation instructions.
- Required information.
- Expected results.
- Possible errors.
- Relevant limitations.

Use simple language and numbered steps for procedures.

Do not expose internal implementation details unless they are relevant to the user.

## 11. Code Documentation

Document code when the explanation adds meaningful value.

Prefer:

- Descriptive names.
- Clear function responsibilities.
- Simple architecture.
- Explicit types.
- Useful comments for non-obvious logic.

Comments should explain why something is necessary, not simply repeat what the code already says.

Avoid excessive comments and redundant documentation.

Update comments when the implementation changes.

## 12. Academic and Project Documentation

For academic projects, technical reports and institutional deliverables:

- Follow the requested structure and evaluation criteria.
- Preserve the terminology used by the institution.
- Maintain consistency between objectives, requirements and implementation.
- Distinguish completed work from planned work.
- Avoid unsupported claims.
- Use formal language when required.
- Follow the requested citation and formatting standards.

Do not invent references, research findings, test results or project activities.

## 13. Documentation Maintenance

Whenever relevant implementation changes occur:

1. Identify affected documentation.
2. Check whether existing instructions remain valid.
3. Update outdated information.
4. Remove contradictory instructions.
5. Verify commands and examples.
6. Check links and references when possible.
7. Ensure consistency across related documents.

Do not update unrelated documentation without justification.

## 14. Security and Sensitive Information

Never include:

- Real passwords.
- API keys.
- Access tokens.
- Private credentials.
- Personal customer information.
- Internal secrets.
- Sensitive production data.

Use placeholders such as:

`YOUR_API_KEY`

`YOUR_DATABASE_URL`

Explain how to configure sensitive information through environment variables or approved secret-management mechanisms.

## 15. Documentation Quality Review

Before considering documentation complete, verify:

- Is the information accurate?
- Does it reflect the current implementation?
- Are commands correct?
- Are prerequisites clear?
- Are configuration instructions complete?
- Are examples consistent with the code?
- Are limitations documented?
- Are there contradictions with other files?
- Can the intended audience understand and use it?
- Is there unnecessary or duplicated content?

## 16. Final Report

After creating or updating documentation, report:

### Files Modified
List the created or modified files.

### Documentation Scope
Explain what was documented.

### Verification
Describe which commands, examples, links or technical details were checked.

### Limitations
Identify information that could not be verified.

### Pending Items
List missing information or decisions requiring confirmation.

## 17. Mandatory Rules

- Never invent technical information.
- Never document planned functionality as completed functionality.
- Never fabricate API contracts or examples.
- Never expose credentials or sensitive information.
- Never create unnecessary duplicate documentation.
- Always inspect the implementation before documenting it.
- Always distinguish facts, assumptions and proposals.
- Always respect existing project conventions.
- Always keep documentation consistent with the source code.

## 18. Guiding Principle

Good documentation reduces uncertainty.

Every document must help someone understand, configure, develop, operate or maintain the project with less ambiguity.