# Workflow: Bug Fix

## 1. Objective

Define a structured process for identifying, investigating, correcting and validating software defects.

The objective is to solve the actual cause of a problem while preserving existing functionality and minimizing the risk of regressions.

## 2. When to Use

Use this workflow when:

- An application crashes or behaves unexpectedly.
- A page or component does not work correctly.
- An API returns unexpected responses.
- A business rule produces incorrect results.
- A database operation fails.
- An integration stops working.
- A regression appears after a code change.
- A user reports unexpected application behavior.

## 3. Execution Process

### Phase 1 — Understand the Problem

Collect and organize the available information.

Identify:

- What is happening?
- What should happen?
- Where does the problem occur?
- When did it start?
- Does it happen consistently?
- Which users or functionalities are affected?
- Are there error messages, logs or screenshots?
- Were there recent changes related to the problem?

Distinguish observed facts from assumptions.

If essential information is missing, request clarification instead of inventing the problem scenario.

**Deliverable:** Clear problem description.

### Phase 2 — Reproduce the Error

Attempt to reproduce the reported behavior.

1. Identify the affected environment.
2. Follow the steps that trigger the problem.
3. Observe the actual behavior.
4. Record error messages and relevant logs.
5. Identify conditions that influence the failure.
6. Verify whether the problem is reproducible.

If the error cannot be reproduced, document the limitation and investigate available evidence.

Never claim to have reproduced an error without actually doing so.

**Deliverable:** Reproduction steps or documented reproduction limitation.

### Phase 3 — Inspect the Code

Investigate the relevant implementation.

Inspect:

- Related source files.
- Components and services.
- API contracts.
- Data flow.
- Business rules.
- Configuration.
- Dependencies.
- Recent code changes.
- Relevant logs.
- Existing tests.
- Project instructions.

Check Git history and diffs when useful.

Avoid changing unrelated files during the investigation.

**Deliverable:** Technical investigation.

### Phase 4 — Identify the Root Cause

Determine why the problem occurs.

Consider possible causes such as:

- Incorrect business logic.
- Invalid data.
- Missing input validation.
- Incorrect state management.
- API contract mismatch.
- Authentication or authorization failures.
- Database inconsistencies.
- Configuration errors.
- Dependency incompatibility.
- Race conditions.
- Network failures.
- Environment differences.
- Regression introduced by recent changes.

Do not confuse the visible symptom with the underlying cause.

If the root cause cannot be established, explain what is known and what remains uncertain.

**Deliverable:** Root cause analysis.

### Phase 5 — Evaluate the Impact

Before implementing a correction, identify:

- Affected functionality.
- Related components or services.
- Potential side effects.
- Security implications.
- Data integrity risks.
- Compatibility concerns.
- Dependencies on other modules.

Classify severity when useful:

- **Critical:** severe security, data integrity or system availability impact.
- **High:** major functionality is unavailable or incorrect.
- **Medium:** relevant functionality is affected, but workarounds may exist.
- **Low:** limited impact or minor unexpected behavior.

Explain the reasoning behind the classification.

**Deliverable:** Impact assessment.

### Phase 6 — Plan the Correction

Define the smallest appropriate correction that addresses the root cause.

Identify:

- Files to modify.
- Expected code changes.
- Relevant dependencies.
- Tests required.
- Potential risks.
- Acceptance criteria.

Prefer a targeted correction over unnecessary refactoring.

For high-impact or destructive changes, present the proposed correction and obtain approval when required.

**Deliverable:** Correction plan.

### Phase 7 — Implement the Correction

Apply the approved changes incrementally.

Follow these principles:

1. Correct the root cause, not just the symptom.
2. Preserve existing functionality.
3. Follow project architecture and conventions.
4. Avoid unrelated refactoring.
5. Handle invalid inputs and error conditions.
6. Preserve security and authorization controls.
7. Avoid introducing unnecessary dependencies.
8. Protect other developers' changes.
9. Keep modifications within the authorized scope.

Do not suppress errors merely to make the application appear functional.

**Deliverable:** Implemented correction.

### Phase 8 — Validate the Correction

Execute relevant validations.

Consider:

- A test reproducing the original defect.
- Unit tests.
- Integration tests.
- End-to-end tests.
- API checks.
- Linting.
- Type checking.
- Production build.
- Manual verification.
- Regression tests.

Verify both the original scenario and related functionality that could have been affected.

If a test cannot be executed, report why.

**Deliverable:** Actual validation results.

### Phase 9 — Regression Review

Review the correction for unintended effects.

Check:

- Related functionality.
- Existing business rules.
- Data integrity.
- API compatibility.
- Authentication and authorization.
- Error handling.
- Existing tests.
- Unrelated modifications.

Investigate any new failures introduced by the correction.

Do not declare the bug resolved while a known critical regression remains.

**Deliverable:** Regression assessment.

### Phase 10 — Documentation and Final Report

Update documentation or tests when necessary.

Present the final result using this structure:

#### Problem
Describe the original defect.

#### Root Cause
Explain why it occurred.

#### Impact
Identify affected functionality and severity.

#### Correction
Explain what was changed.

#### Files Modified
List relevant files.

#### Validation
List the actual commands and checks executed, including their results.

#### Regression Review
Describe what related functionality was checked.

#### Limitations
Identify unresolved issues or validations that could not be performed.

#### Conclusion
Classify the result as:

- **Resolved:** correction implemented and relevant validations passed.
- **Partially resolved:** correction implemented, but some validation or work remains.
- **Unresolved:** the problem remains or the root cause has not been established.

## 4. Special Situations

### Error Cannot Be Reproduced

Do not invent a correction.

Collect evidence, inspect logs and identify additional information required.

### Problem Depends on an External Service

Separate application failures from external service failures.

Verify available responses, configuration and connectivity before modifying application logic.

### Problem Involves Data Loss or Corruption

Stop potentially destructive operations.

Preserve available evidence and request authorization before attempting recovery or modifying production data.

### Problem Is Outside Authorized Scope

If the root cause requires changes outside the authorized scope (for example, back-end modifications in a front-end-only project):

1. Do not modify unauthorized files or repositories.
2. Document the root cause and technical evidence clearly.
3. Specify what the responsible team needs to fix or provide.
4. Implement only safe, authorized mitigation or error handling within the permitted scope.

## 5. Mandatory Rules

- Never modify code before investigating the problem.
- Never confuse symptoms with the root cause.
- Never suppress errors merely to hide failures.
- Never fabricate reproduction steps or test results.
- Never delete data or execute destructive commands without explicit authorization.
- Never commit, push or merge without explicit authorization.
- Always preserve existing functionality and other developers' work.
- Always respect the project's `AGENTS.md` and scope restrictions.
- Always validate the correction and check for regressions before declaring the issue resolved.

## 6. Completion Criteria

A bug fix is complete when:

- The problem and its root cause have been identified (or limitations documented).
- The correction has been implemented within the authorized scope.
- Relevant tests and validations have been executed.
- Potential regressions have been evaluated.
- The final report has been presented with verifiable evidence.

## 7. Guiding Principle

Fix the cause, not just the symptom.

Every correction must be minimal, verifiable, safe and respectful of the existing architecture and team boundaries.