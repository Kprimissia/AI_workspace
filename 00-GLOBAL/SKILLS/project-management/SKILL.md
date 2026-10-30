---
name: project-management
description: Plans, organizes and tracks software projects. Use for backlog management, sprint planning, task breakdown, prioritization, milestones, requirements, acceptance criteria, team coordination and project progress reporting.
---

# Project Management

## 1. Objective

Organize and coordinate software development work to ensure that project activities are clear, prioritized, trackable and aligned with the project's objectives.

This Skill guides the agent in planning work, managing backlogs, organizing sprints, defining deliverables and monitoring progress.

The goal is to improve project visibility, reduce ambiguity and help the team deliver work in a structured way.

## 2. Initial Analysis

Before planning or modifying project management artifacts:

1. Read the project's `AGENTS.md` and relevant documentation.
2. Understand the project's objective and scope.
3. Identify the team members and their responsibilities when documented.
4. Inspect the current backlog and project board.
5. Identify existing milestones, sprints and deadlines.
6. Check current progress and blocked activities.
7. Identify dependencies and risks.
8. Confirm the tools actually used by the team.

Do not assume that a project uses Scrum, Kanban or another methodology without checking its existing process.

Respect the methodology already adopted by the team.

## 3. Requirements Management

When analyzing a requirement, identify:

- Requirement description.
- Business objective.
- Expected behavior.
- Users or stakeholders involved.
- Functional requirements.
- Non-functional requirements.
- Dependencies.
- Constraints.
- Acceptance criteria.
- Priority.

Separate confirmed requirements from assumptions and suggestions.

If important information is missing, identify the uncertainty instead of inventing a requirement.

## 4. Task Breakdown

Convert large requirements into small, actionable tasks.

Each task should contain, when applicable:

- **Title:** short and descriptive.
- **Description:** what must be done.
- **Objective:** why the task is necessary.
- **Scope:** what is included.
- **Acceptance criteria:** how completion will be verified.
- **Priority:** relative importance.
- **Dependencies:** tasks or decisions required first.
- **Responsible person:** only when assigned or confirmed.
- **Estimate:** only when requested or supported by the team's estimation process.
- **Status:** current progress.

Tasks should be specific enough for a team member to understand and execute without unnecessary ambiguity.

Avoid tasks that are too broad, such as "finish the system" or "improve the application".

Break them into smaller deliverables.

## 5. Backlog Management

Maintain an organized backlog containing the work that may need to be completed.

For each backlog item:

1. Verify whether it already exists.
2. Identify its objective.
3. Check its priority.
4. Define acceptance criteria.
5. Identify dependencies.
6. Confirm whether it belongs to the project scope.
7. Avoid duplicate or contradictory tasks.

Keep the backlog focused on actual project needs.

Do not create artificial tasks merely to increase the number of cards.

## 6. Prioritization

Prioritize tasks based on factors such as:

- Business value.
- User impact.
- Technical risk.
- Dependencies.
- Urgency.
- Project deadlines.
- Effort.
- Security and reliability.

Use the following priority levels when appropriate:

- **Critical:** blocks the project or involves a serious operational or security risk.
- **High:** essential for an important deliverable.
- **Medium:** relevant but not immediately blocking.
- **Low:** useful improvement with limited immediate impact.

Explain the reasoning behind important prioritization decisions.

Do not treat every task as urgent.

## 7. Sprint Planning

When the project uses sprints:

1. Confirm the sprint duration.
2. Review the available backlog.
3. Identify the sprint objective.
4. Select tasks according to priority and team capacity.
5. Check dependencies.
6. Define expected deliverables.
7. Establish acceptance criteria.
8. Identify possible blockers.
9. Confirm the planned scope with the team when necessary.

A sprint should have a clear objective, not merely a collection of unrelated tasks.

Do not assign work beyond the team's realistic capacity.

Do not invent sprint dates or team availability.

## 8. Kanban Management

When using Kanban, organize work according to the actual board configuration.

A common structure is:

- **Backlog:** identified work not yet scheduled.
- **To Do:** selected tasks ready to begin.
- **In Progress:** tasks currently being executed.
- **In Review:** tasks awaiting review or validation.
- **Done:** completed and verified tasks.

Adapt these columns to the project's existing workflow.

Keep task statuses accurate.

Do not move a task to Done simply because implementation started or code was written.

Use explicit completion criteria.

## 9. GitHub Projects

When managing work through GitHub Projects:

- Inspect the existing organization and project configuration.
- Reuse existing fields, labels and status conventions.
- Link tasks to the appropriate Issues and Pull Requests.
- Use milestones when they provide useful project organization.
- Keep descriptions and acceptance criteria consistent.
- Avoid duplicate cards and unnecessary labels.
- Respect repository and project permissions.
- Verify that changes were actually saved.

Do not claim that a task, Issue, milestone or Project was created or modified unless the operation was successfully completed.

Use available GitHub integrations when authorized. If the necessary integration is unavailable, prepare the content for manual creation.

## 10. Team Coordination

When coordinating a team:

1. Understand each member's confirmed responsibilities.
2. Identify task ownership.
3. Avoid assigning work without authorization or confirmation.
4. Identify overlapping activities.
5. Identify dependencies between members.
6. Communicate blockers clearly.
7. Keep task ownership and status updated.
8. Avoid unnecessary interference with another member's work.

Do not assume a team member's availability, skill level or responsibility without evidence.

When a task depends on another team or project area, describe the dependency and the expected deliverable.

## 11. Dependencies and Blockers

Identify dependencies that may prevent work from progressing.

For each blocker, document:

- Description.
- Impact.
- Related tasks.
- Responsible area or team, if known.
- Required action.
- Current status.

Distinguish between:

- Technical dependency.
- External dependency.
- Pending decision.
- Resource limitation.
- Access or permission problem.
- Environment limitation.

Prioritize resolving blockers that affect critical deliverables.

## 12. Progress Tracking

Evaluate project progress using verifiable information.

Consider:

- Completed tasks.
- Tasks in progress.
- Pending tasks.
- Blocked tasks.
- Sprint objectives.
- Milestone progress.
- Outstanding risks.
- Changes in scope.

Do not calculate progress using arbitrary percentages.

When presenting metrics, explain their calculation and data source.

A completed task must satisfy its acceptance criteria.

## 13. Scope and Change Management

When new requirements or changes appear:

1. Understand the requested change.
2. Identify its impact on existing requirements.
3. Evaluate affected tasks and deliverables.
4. Identify additional dependencies.
5. Assess risks and potential delays.
6. Determine whether the change requires replanning.
7. Present the impact before modifying the project plan when approval is necessary.

Do not silently expand the project's scope.

Keep a clear distinction between approved requirements and proposed improvements.

## 14. Risk Management

Identify and monitor risks involving:

- Technical complexity.
- Security.
- External integrations.
- Team dependencies.
- Deadlines.
- Unclear requirements.
- Infrastructure.
- Data integrity.
- Insufficient testing.
- Scope changes.

For relevant risks, describe:

- Probability.
- Impact.
- Severity.
- Mitigation strategy.
- Responsible area, when known.

Prioritize risks that could compromise important deliverables.

## 15. Documentation

Maintain relevant project management documentation, such as:

- Project objectives.
- Scope.
- Requirements.
- Backlog.
- Sprint plans.
- Milestones.
- Task dependencies.
- Risks.
- Decisions.
- Meeting summaries.
- Progress reports.

Keep documents consistent with the actual project board and implementation.

Do not create unnecessary documentation that duplicates information already maintained in the team's tools.

## 16. Communication and Reporting

Project reports must be objective and based on actual information.

When preparing a status report, include:

### Project Status
Current overall situation.

### Completed Work
Deliverables verified as completed.

### Work in Progress
Tasks currently being executed.

### Pending Work
Relevant outstanding tasks.

### Blockers
Problems preventing progress.

### Risks
Relevant risks and potential impacts.

### Next Steps
Recommended actions based on current priorities.

### Decisions Required
Questions or approvals that require stakeholder involvement.

Clearly distinguish confirmed facts from estimates and recommendations.

## 17. Mandatory Rules

- Never invent project progress.
- Never fabricate task completion.
- Never assign responsibilities without confirmation.
- Never invent deadlines or estimates.
- Never create duplicate tasks unnecessarily.
- Never expand scope without making the impact clear.
- Always define acceptance criteria for meaningful deliverables.
- Always identify relevant dependencies.
- Always respect the team's existing workflow.
- Always use verified information when reporting progress.
- Always respect project permissions and authorization requirements.

## 18. Guiding Principle

A well-managed project makes work visible, responsibilities clear and priorities understandable.

Every planning decision should help the team know what needs to be done, why it matters and how completion will be verified.