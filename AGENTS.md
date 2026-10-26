# Uster Urban Intelligence

Uster Urban Intelligence is an open-source, local-first urban analytics platform for Uster, Switzerland, with a long-term vision of an interactive 3D digital twin.

Current phase: Multi-Agent Team Configuration. No application implementation is approved by default.

## Governing documents

- Read [Team Charter](docs/development/team-charter.md) for the team's mission, provisional roles, and ways of working.
- Read [Governance](docs/development/governance.md) for decision rights, approval gates, and execution boundaries.
- If these documents conflict, stop and ask the human to resolve the conflict. Human instructions take precedence within their explicitly approved scope.

## Human authority

The human is Product Owner, final decision maker, human-in-the-loop supervisor, and approval authority for architecture, sprint scope, merges, releases, and deployments. Agent consensus is never human approval.

Approval must be explicit and specific. A human request that clearly directs implementation and states its scope counts as approval for that scope only. Never carry approval into later tasks or expand it by inference.

Obtain human approval before:

1. Starting implementation.
2. Making a significant architectural change.
3. Expanding approved scope.
4. Installing a dependency or introducing an external service.
5. Performing a destructive or irreversible operation.
6. Merging a pull request.
7. Creating a release or deploying software.

## Non-negotiable operating rules

- Work only in an actively supervised human session. Do not schedule development, continue after the session ends, or start unattended implementation.
- Background operations may run only when explicitly requested and while the human remains able to supervise and interrupt them.
- Respect interruptions and stop requests immediately.
- Stop for significant uncertainty, conflicting instructions, missing approval, or a consequential blocker. Report it; do not silently broaden scope.
- Distinguish facts, assumptions, recommendations, and decisions. Make risks, trade-offs, tool actions, and results visible without claiming access to private model reasoning.
- Never fabricate approvals, GitHub activity, test results, reviews, completed work, or tool output.

These are behavioral instructions. `AGENTS.md` does not itself enforce permissions, prevent scheduled execution, or guarantee supervision; use technical controls described in Governance where available.

## Operating modes

The human controls the operating mode. If no mode or implementation authorization is explicit, default to **DISCUSS**. Agents must not transition to **EXECUTE** by themselves.

- **DISCUSS:** read, analyze, research, and recommend. Do not modify project files, install dependencies, or change GitHub state.
- **PLAN:** prepare requirements, acceptance criteria, architecture proposals, tasks, and dependencies. Do not implement, install dependencies, modify project configuration, or change GitHub state without explicit authorization.
- **EXECUTE:** implement and validate only the explicitly approved scope. An explicit human instruction to implement a bounded change establishes EXECUTE for that change only.

## Development lifecycle

Use the smallest useful version of this sequence:

1. **Discover:** explore the problem, assumptions, alternatives, risks, and dependencies.
2. **Specify:** define scope, acceptance criteria, proposed design, and tasks.
3. **Approve:** present the proposal and wait for explicit human approval.
4. **Build:** implement only the approved scope.
5. **Validate:** run risk-appropriate tests and independent review; report observed evidence.
6. **Review:** demonstrate results against acceptance criteria and disclose incomplete work, defects, and debt.
7. **Release:** merge, release, or deploy only with explicit human approval.

Do not automatically start another task or sprint.

## Collaboration and quality

- Involve only relevant specialists. The Team Lead coordinates but cannot override the human or suppress dissent.
- Specialists evaluate material questions independently before discussion. Preserve meaningful disagreement and explain recommendations.
- Product analysis is not product approval. Architecture advice is not approved architecture. Developers do not approve their own work.
- Tests and inspection provide evidence; confidence statements do not.
- Use GitHub Issues, Projects, Milestones, Pull Requests, and Actions as the operational source of truth when access is available. Do not duplicate the backlog in repository Markdown.

## Engineering constraints

- Prefer simple, maintainable, independently testable increments; avoid premature abstractions.
- Favor open-source, local-first, reproducible solutions. Do not introduce paid cloud services or paid APIs.
- Treat data licensing, attribution, provenance, secrets, credentials, and private data as first-class concerns.
- Add no dependency without explicit approval. Never commit secrets, credentials, or private data.
- Record significant technical decisions as Architecture Decision Records.
- Do not prescribe the application stack before collaborative evaluation and human approval.
