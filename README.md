# Uster Urban Intelligence

Uster Urban Intelligence is an open-source, local-first urban analytics platform for Uster, Switzerland. Its long-term vision is an interactive 3D digital twin that supports trustworthy exploration of the city and its data.

## Project status

The engineering foundation is complete: the repository has a human-supervised agent team, reusable workflows, automated configuration validation, and protected Pull Request-based integration.

Application functionality has not started. Product Discovery is the next phase and will define the first validated user needs before implementation or technology choices are approved.

## Repository structure

| Path | Purpose |
| --- | --- |
| `.codex/` | Project-scoped Codex configuration and agent definitions |
| `.agents/skills/` | Reusable team workflows |
| `.github/` | Issue and Pull Request templates plus GitHub Actions |
| `apps/backend/` | Reserved for an approved backend application |
| `apps/frontend/` | Reserved for an approved frontend application |
| `docs/development/` | Team, governance, skills, and engineering process documentation |
| `docs/product/` | Reserved for approved product documentation |
| `tests/` | Reserved for shared tests and fixtures |

## How work enters the repository

1. The human approves a GitHub Issue and its acceptance criteria.
2. Work is implemented on a short-lived, Issue-linked branch.
3. Max performs independent QA and the implementer resolves blocking findings.
4. A Pull Request records the change, validation evidence, QA outcome, risks, and limitations.
5. Required CI checks pass.
6. The human explicitly approves the merge.

Agent review, passing CI, and repository automation provide evidence; they do not replace human approval.

## Project documentation

- [Team Charter](docs/development/team-charter.md)
- [Governance](docs/development/governance.md)
- [Agent Team](docs/development/agent-team.md)
- [Reusable Skills](docs/development/skills.md)
- [Engineering Workflow](docs/development/engineering-workflow.md)

## License

This project is available under the [MIT License](LICENSE).
