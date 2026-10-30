# Workflow: Release and Deployment

## 1. Objective

Define a standardized process for preparing, validating and deploying software releases.

The objective is to ensure that every release is technically validated, properly documented and deployed to the correct environment with controlled risks.

## 2. When to Use

Use this workflow when:

- Preparing a new software version.
- Publishing application updates.
- Deploying a front-end application.
- Deploying a back-end service.
- Preparing production releases.
- Configuring staging environments.
- Updating deployment configurations.
- Investigating deployment failures.
- Creating release documentation.

## 3. Execution Process

### Phase 1 — Understand the Release

Before preparing a release:

1. Identify the application and repository.
2. Identify the target environment.
3. Understand which changes are included.
4. Check the current application version.
5. Identify relevant branches, commits and Pull Requests.
6. Check whether the release has been authorized.
7. Identify dependencies and external services.
8. Check applicable project instructions.

Distinguish between development, testing, staging and production environments.

Do not assume that a deployment target is production or staging without verification.

**Deliverable:** Release scope and target environment.

### Phase 2 — Inspect the Repository

Inspect the repository before preparing the release.

Check:

- Current Git branch.
- Working tree status.
- Recent commits.
- Changes included in the release.
- Uncommitted modifications.
- Dependencies.
- Build configuration.
- Environment variables.
- Existing deployment configuration.
- Relevant documentation.

Confirm that the intended version includes the correct changes.

Do not include unrelated or unapproved modifications.

**Deliverable:** Repository readiness assessment.

### Phase 3 — Verify Release Requirements

Identify the requirements for a safe release.

Consider:

- Functional requirements.
- Acceptance criteria.
- Compatibility.
- Security.
- Required environment variables.
- External integrations.
- Database dependencies.
- Infrastructure requirements.
- Versioning conventions.
- Rollback strategy.

Check whether the application requires database migrations or infrastructure changes.

Do not assume that a release can be deployed independently of other services.

**Deliverable:** Release requirements checklist.

### Phase 4 — Validate the Application

Execute applicable validations before deployment.

Consider:

- Unit tests.
- Integration tests.
- End-to-end tests.
- Linting.
- Type checking.
- Production build.
- Dependency checks.
- API validation.
- Security checks.
- Manual smoke tests.

Verify that the production build completes successfully.

Investigate failures before proceeding.

Never claim that a validation passed if it was not executed.

If an essential validation cannot be performed, communicate the limitation and request a decision before proceeding.

**Deliverable:** Pre-release validation results.

### Phase 5 — Review Configuration

Verify the configuration required by the target environment.

Check:

- Environment variables.
- API URLs.
- Database connections.
- Authentication configuration.
- CORS settings.
- External integrations.
- Runtime versions.
- Build commands.
- Deployment commands.
- Domain configuration.
- Secret management.

Never expose credentials or copy production secrets into source code.

Use placeholders in documentation.

Do not assume that development environment settings are suitable for production.

**Deliverable:** Environment configuration review.

### Phase 6 — Database and Data Preparation

When the release involves database changes:

1. Inspect the migration files.
2. Identify schema modifications.
3. Evaluate backward compatibility.
4. Identify data transformation requirements.
5. Assess backup and recovery needs.
6. Identify potential downtime.
7. Define the migration execution order.

Treat destructive migrations and irreversible data transformations as high-risk operations.

Do not execute production migrations, delete data or modify production databases without explicit authorization.

**Deliverable:** Database release assessment.

### Phase 7 — Release Preparation

Prepare the release according to the project's conventions.

When applicable:

- Confirm the target branch.
- Verify the included commits.
- Update version information.
- Prepare release notes.
- Confirm required approvals.
- Check deployment dependencies.
- Confirm the rollback procedure.
- Ensure the working tree contains no unintended changes.

Use the project's existing versioning convention.

When Semantic Versioning is applicable:

- **MAJOR:** incompatible changes.
- **MINOR:** backward-compatible functionality.
- **PATCH:** backward-compatible fixes.

Do not change version numbers without justification.

**Deliverable:** Release candidate.

### Phase 8 — Deployment Approval

Before deploying, confirm:

- The target environment.
- The version to be deployed.
- Required validations.
- Configuration readiness.
- Required approvals.
- Potential operational impact.
- Rollback availability.

Production deployment requires explicit authorization.

Do not interpret a general request to prepare a release as permission to publish it.

**Deliverable:** Deployment readiness confirmation.

### Phase 9 — Execute Deployment

After authorization:

1. Follow the project's documented deployment process.
2. Confirm the correct environment.
3. Execute the approved deployment commands or platform workflow.
4. Monitor the execution.
5. Capture relevant errors.
6. Confirm the deployment result.
7. Record the deployed version.

Use existing deployment tools and integrations when available and authorized.

Do not invent platform commands or deployment procedures.

Do not expose secrets in terminal output, logs or documentation.

**Deliverable:** Deployment execution result.

### Phase 10 — Post-Deployment Validation

After deployment, verify the application in the target environment.

Consider:

- Application availability.
- Main page loading.
- Authentication.
- Critical user workflows.
- API communication.
- Database connectivity.
- External integrations.
- Error logs.
- Runtime health.
- Relevant performance indicators.

Perform smoke tests focused on critical functionality.

A successful deployment command does not prove that the application is operating correctly.

**Deliverable:** Post-deployment validation results.

### Phase 11 — Rollback and Incident Handling

If deployment causes a serious failure:

1. Identify the impact.
2. Stop additional risky changes.
3. Preserve relevant logs and evidence.
4. Evaluate the available rollback procedure.
5. Obtain authorization when required.
6. Execute the approved recovery procedure.
7. Validate the restored environment.
8. Document the incident.

Do not perform destructive recovery operations without authorization.

Never assume that reverting application code automatically reverses database changes.

**Deliverable:** Recovery result or documented incident.

### Phase 12 — Release Documentation

Record relevant release information.

Include:

- Release version.
- Deployment date.
- Target environment.
- Included changes.
- Relevant commits.
- Deployment result.
- Database changes.
- Known limitations.
- Rollback information.
- Post-deployment validation.

Keep release documentation consistent with what actually happened.

**Deliverable:** Release record.

## 4. Environment Rules

### Development

Used for active implementation and internal validation.

Changes should not be treated as production-ready merely because they work locally.

### Testing

Used for controlled validation.

Use appropriate test data and configurations.

### Staging

Used to validate release candidates in an environment representative of production.

Verify relevant configuration differences.

### Production

Used by real users and operational systems.

Production actions require explicit authorization, careful validation and an available recovery strategy.

## 5. Security Requirements

- Never expose secrets.
- Never commit credentials.
- Never place production secrets in source code.
- Never use production data without authorization.
- Never disable security controls to simplify deployment.
- Verify permissions and access restrictions.
- Protect environment configuration.
- Use approved secret-management mechanisms.
- Evaluate dependency and vulnerability risks.

## 6. Mandatory Rules

- Never deploy without knowing the target environment.
- Never publish unapproved changes.
- Never execute production deployments without explicit authorization.
- Never execute destructive database operations without approval.
- Never claim deployment success without confirmation.
- Never ignore failed pre-release validations.
- Never expose credentials or secrets.
- Never assume rollback automatically reverses database or external state changes.
- Never commit, push, merge or tag releases without explicit authorization.
- Always respect the project's `AGENTS.md` and environment boundaries.

## 7. Completion Criteria

A release and deployment workflow is complete when:

- The release scope and target environment have been verified.
- Pre-release validations and production builds have been executed.
- Environment configurations and database impacts have been reviewed.
- Explicit authorization has been confirmed before any deployment action.
- Post-deployment validations (or pre-release readiness checks) have been recorded.
- Release documentation and rollback procedures have been updated.

## 8. Guiding Principle

A reliable release is predictable, verifiable and reversible.

Never trade operational safety, data integrity or security for deployment speed.