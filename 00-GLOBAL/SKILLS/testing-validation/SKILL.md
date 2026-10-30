---
name: testing-validation
description: Plans, implements, executes and analyzes software tests and quality checks. Use for unit, integration, API, end-to-end, regression, lint, type checks, builds and software validation reports.
---

# Testing and Validation

## 1. Objective

Ensure software quality through structured testing and validation.

This Skill guides the agent in selecting appropriate tests, executing available quality checks, analyzing failures and reporting results accurately.

The objective is not simply to make tests pass, but to verify that the software behaves as expected and that changes do not introduce regressions.

## 2. Initial Analysis

Before creating or executing tests:

1. Read the project's `AGENTS.md` and relevant documentation.
2. Identify the project's architecture and technology stack.
3. Inspect the existing test structure.
4. Check available scripts and commands in configuration files.
5. Identify existing testing frameworks and tools.
6. Understand the feature, requirements and expected behavior.
7. Identify risks and areas that may be affected by the changes.

Do not assume that a project uses a particular testing framework.

Prefer existing tools and conventions. Do not introduce new dependencies without a clear justification.

## 3. Testing Strategy

Choose tests according to the feature, architecture, complexity and risk.

Consider the following testing levels:

### 3.1 Unit Tests

Verify small, isolated units of code, such as:

- Functions.
- Methods.
- Business rules.
- Utility functions.
- Data transformations.
- Individual components when appropriate.

Unit tests should be focused, predictable and independent whenever possible.

### 3.2 Integration Tests

Verify whether different parts of the application work correctly together.

Examples:

- Front-end and API communication.
- Service and repository interactions.
- Database operations.
- Authentication flows.
- External service integrations.
- Component interactions.

### 3.3 End-to-End Tests

Verify complete user workflows from beginning to end.

Examples:

- Login and logout.
- Registration.
- Form submission.
- Navigation between pages.
- Main business workflows.
- Permission-based access.

Use end-to-end tests when they provide meaningful coverage of critical user journeys.

### 3.4 Regression Tests

Verify that existing functionality continues to work after modifications.

Whenever a bug is corrected, consider creating a test that reproduces the original problem and verifies the correction.

## 4. Test Design

Tests must verify expected behavior, including normal and abnormal situations.

Consider:

- **Happy paths:** valid inputs and successful operations.
- **Negative paths:** invalid inputs and unsuccessful operations.
- **Boundary conditions:** minimum, maximum, empty and unusually large values.
- **Edge cases:** unexpected but possible scenarios.
- **Permissions:** authorized and unauthorized users.
- **Error handling:** network failures, unavailable services and invalid responses.
- **Data integrity:** correct creation, modification and preservation of information.
- **Regression:** previously working functionality after changes.

Avoid tests that only verify implementation details without checking meaningful behavior.

## 5. Test Quality

Every test should:

- Have a clear purpose.
- Verify an observable result.
- Be repeatable.
- Avoid unnecessary dependencies.
- Use isolated test data whenever possible.
- Avoid relying on execution order.
- Have meaningful names.
- Be maintainable.
- Avoid arbitrary delays and unstable conditions.

Do not create tests that depend on production data.

Do not weaken assertions, remove relevant tests or change expected results merely to make the test suite pass.

## 6. Front-end Validation

For front-end projects, evaluate applicable areas:

- Component rendering.
- Navigation and routing.
- Forms and validation.
- User interactions.
- Loading states.
- Empty states.
- Error states.
- Responsiveness.
- Accessibility.
- API communication.
- Authentication and route protection.
- Browser console errors.

When appropriate, verify the application at different screen sizes.

Do not consider a page visually correct solely because the development server starts successfully.

## 7. Back-end Validation

For back-end projects, evaluate applicable areas:

- API endpoint behavior.
- HTTP status codes.
- Request validation.
- Response structure.
- Business rules.
- Authentication.
- Authorization.
- Database operations.
- Transaction handling.
- Error handling.
- Data integrity.
- External integrations.
- Security controls.

Verify both successful and unsuccessful requests.

Do not assume that an endpoint works merely because it exists in the source code.

## 8. Execution Workflow

Follow this sequence:

1. Identify the requirements and expected behavior.
2. Inspect existing tests and available commands.
3. Define the testing scope.
4. Select the appropriate testing levels.
5. Implement or update tests when requested or necessary.
6. Execute the relevant existing test commands.
7. Execute applicable static checks, linting and type checks.
8. Execute the production build when relevant.
9. Analyze failures and investigate their causes.
10. Correct identified problems only within the authorized scope.
11. Repeat relevant validations after corrections.
12. Report the actual results.

Prioritize tests related to the modified functionality before running broader validation suites.

## 9. Diagnosing Failures

When a test fails:

1. Identify the failing test and the reported error.
2. Locate the relevant source code.
3. Determine whether the failure is caused by the implementation, the test, configuration or environment.
4. Check whether the failure existed before the current changes, when that information is available.
5. Identify the root cause.
6. Propose or implement an appropriate correction within the authorized scope.
7. Execute the affected test again.

Do not assume every failure is a software defect.

Clearly distinguish:

- Implementation failure.
- Incorrect or outdated test.
- Configuration problem.
- Missing dependency.
- Environment limitation.
- External service failure.
- Unknown cause requiring further investigation.

Never hide failed tests or report an unresolved failure as successful.

## 10. Coverage and Quality Metrics

Use test coverage as an indicator, not as proof of software quality.

When coverage tools are available, consider:

- Statement coverage.
- Branch coverage.
- Function coverage.
- Line coverage.

Prioritize meaningful coverage of critical business rules and high-risk functionality.

Do not optimize only for coverage percentages.

## 11. Security and Data Protection

During testing:

- Never expose credentials, tokens or private information.
- Do not use real customer data without explicit authorization.
- Prefer isolated test environments.
- Avoid destructive operations against real databases.
- Do not execute production migrations or destructive tests without explicit approval.
- Protect environment variables and configuration files.
- Avoid committing test secrets or sensitive data.

## 12. Project and Team Protection

Before changing test infrastructure or configuration:

- Inspect existing conventions.
- Avoid unnecessary changes to shared configurations.
- Do not modify unrelated modules.
- Respect repository ownership and project boundaries.
- Coordinate changes that affect other team members.
- Do not commit, push or merge without authorization.

## 13. Documentation

When relevant, document:

- How to execute the tests.
- Required environment configuration.
- Test prerequisites.
- Known limitations.
- Test scenarios.
- Validation results.

Keep documentation consistent with the actual implementation.

## 14. Final Report

After validation, provide a concise and objective report containing:

### Scope
What functionality or changes were evaluated.

### Tests Executed
List the actual commands and test categories executed.

### Results
Identify successful, failed, skipped or blocked validations.

### Problems Found
Describe relevant defects, their impact and their locations.

### Corrections
Explain what was corrected, if applicable.

### Limitations
Identify validations that could not be performed and explain why.

### Conclusion
State whether the evaluated changes are validated, partially validated or not validated.

## 15. Mandatory Rules

- Never claim that a test was executed if it was not.
- Never fabricate test results.
- Never hide failures.
- Never remove meaningful tests just to obtain a successful result.
- Never use production data without authorization.
- Never execute destructive operations without explicit approval.
- Never introduce testing dependencies without justification.
- Always investigate the cause of failures.
- Always report the commands actually executed.
- Always respect the project's `AGENTS.md` and scope restrictions.
- Prioritize reliable evidence over assumptions.

## 16. Guiding Principle

A successful build does not guarantee correct functionality.

A passing test suite does not guarantee the absence of defects.

Validate the behavior that matters, investigate failures and communicate exactly what was and was not verified.