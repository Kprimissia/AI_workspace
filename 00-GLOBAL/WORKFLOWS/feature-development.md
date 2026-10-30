# Workflow: Feature Development

## 1. Objective

Define a standardized process for analyzing, planning, implementing and validating new software features.

This workflow ensures that development activities are organized, technically consistent and aligned with project requirements.

## 2. When to Use

Use this workflow when:

- Creating a new application feature.
- Implementing a new page or module.
- Adding functionality to an existing component.
- Creating or extending an API integration.
- Implementing a new business requirement.
- Expanding an existing application workflow.

Do not use this workflow for isolated documentation changes or simple configuration tasks unless the change requires a broader implementation process.

## 3. Execution Process

### Phase 1 — Understand the Request

Before changing anything:

1. Read the user's request carefully.
2. Identify the expected functionality.
3. Identify the users affected.
4. Understand the expected behavior.
5. Identify requirements and constraints.
6. Identify what is explicitly outside the scope.
7. Resolve critical ambiguities before implementation.

**Deliverable:** Clear understanding of the requested feature.

### Phase 2 — Inspect the Project

Inspect the current project before proposing modifications.

Check:

- `AGENTS.md` and other applicable instructions.
- Repository structure.
- Existing architecture.
- Relevant components and modules.
- Existing services and integrations.
- Dependencies and configuration.
- Current Git state.
- Existing tests and documentation.

Do not assume that the project uses a particular architecture or technology without verification.

**Deliverable:** Technical understanding of the existing implementation.

### Phase 3 — Analyze Requirements

Translate the request into technical requirements.

Identify:

- Functional requirements.
- Non-functional requirements.
- Business rules.
- User interactions.
- Data requirements.
- API dependencies.
- Permissions.
- Error scenarios.
- Security considerations.
- Acceptance criteria.

Separate confirmed requirements from assumptions and suggestions.

**Deliverable:** Structured requirements and acceptance criteria.

### Phase 4 — Plan the Implementation

Define how the feature should be implemented.

Identify:

- Files likely to be created.
- Files likely to be modified.
- Components or services involved.
- Data flow.
- Dependencies.
- Potential risks.
- Testing strategy.
- Documentation impact.

Break complex work into small, manageable steps.

Prefer solutions consistent with the existing architecture.

For complex or high-impact changes, present the plan and wait for approval when necessary.

**Deliverable:** Implementation plan.

### Phase 5 — Implement the Feature

Execute the approved plan incrementally.

Follow these principles:

1. Preserve existing functionality.
2. Reuse established project conventions.
3. Avoid unnecessary dependencies.
4. Keep responsibilities well separated.
5. Maintain readable and maintainable code.
6. Validate inputs and handle errors.
7. Respect authentication and authorization rules.
8. Avoid unrelated modifications.
9. Keep changes within the authorized project scope.

Do not replace entire modules when a smaller change is sufficient.

**Deliverable:** Implemented feature.

### Phase 6 — Validate the Implementation

Execute applicable validations.

Consider:

- Unit tests.
- Integration tests.
- End-to-end tests.
- Linting.
- Type checking.
- Production build.
- API validation.
- Responsiveness.
- Accessibility.
- Security checks.
- Regression tests.

Verify the acceptance criteria defined in Phase 3.

Report validations that could not be executed.

Never claim that a test passed if it was not executed successfully.

**Deliverable:** Validation results.

### Phase 7 — Review the Changes

Review the implementation before considering it complete.

Check:

- Correctness.
- Architecture.
- Security.
- Maintainability.
- Performance.
- Error handling.
- Unnecessary code.
- Accidental modifications.
- Compatibility with existing functionality.

Correct relevant issues within the authorized scope.

**Deliverable:** Reviewed implementation.

### Phase 8 — Update Documentation

Update documentation when the feature changes relevant project information.

Consider:

- README.
- Setup instructions.
- API documentation.
- Architecture documentation.
- Technical specifications.
- User instructions.

Only document behavior that is implemented or explicitly identified as planned.

**Deliverable:** Updated documentation, when applicable.

### Phase 9 — Final Report

Present the outcome using the following structure:

#### Feature
Name and objective of the implemented functionality.

#### Implementation
Summary of the technical changes.

#### Files Modified
List the relevant files created or changed.

#### Validation
List commands executed and their actual results.

#### Documentation
Describe documentation changes, if applicable.

#### Limitations
Identify incomplete functionality, external dependencies and unresolved issues.

#### Pending Actions
List any decisions, approvals or tasks still required.

#### Conclusion
State whether the feature is completed, partially completed or blocked.

## 4. Execution Rules

- Do not modify files before understanding the project.
- Do not assume missing requirements.
- Do not expand the requested scope without justification.
- Do not overwrite another developer's work.
- Do not change shared architecture unnecessarily.
- Do not install dependencies without justification.
- Do not execute destructive operations without approval.
- Do not commit, push or merge without authorization.
- Do not claim completion without validating the acceptance criteria.
- Always respect the project's `AGENTS.md`.

## 5. Completion Criteria

A feature may be considered complete when:

- The requested behavior is implemented.
- The acceptance criteria are satisfied.
- Relevant validations have been executed.
- No known critical issue remains unresolved.
- Relevant documentation has been updated.
- Limitations and pending actions have been reported.

If any condition is not satisfied, clearly identify the remaining work.

## 6. Guiding Principle

Understand first, plan second, implement incrementally and validate before declaring completion.

The objective is not simply to produce code, but to deliver a working, maintainable and verifiable feature.