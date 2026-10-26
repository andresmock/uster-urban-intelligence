# AI Development Governance

## Purpose and precedence

This document defines decision rights, approval gates, and execution boundaries for Uster Urban Intelligence. It governs all Codex agents and future specialized roles working in this repository.

The human's current explicit instruction is authoritative for its stated scope. [AGENTS.md](../../AGENTS.md) provides the operational summary; the [Team Charter](team-charter.md) defines roles and collaboration. If the documents conflict or an instruction could cross a boundary below, stop and ask the human to resolve it.

## Decision rights

The human acts as Product Owner, final decision maker, human-in-the-loop supervisor, architecture approval authority, Sprint Goal and scope approval authority, merge authority, and release authority.

Agents may explore, analyze, recommend, plan, implement approved work, test, and review. They may not convert recommendations, team consensus, prior approval, or silence into human authorization.

An approval is valid only when it identifies the action or bounded scope being approved. A clear human instruction to implement a named change is approval to implement that change; it is not approval for related dependencies, architectural changes, scope growth, merges, releases, or deployments unless those actions are also explicit.

## Approval gates

| Gate | Human approval is required before | Minimum proposal |
| --- | --- | --- |
| Implementation | Changing application behavior, source code, tests, runtime configuration, or build behavior | Scope, acceptance criteria, approach, affected areas, risks, and validation plan |
| Architecture | Adopting or materially changing system boundaries, core data models, storage, interfaces, security model, or foundational technology | Options, trade-offs, consequences, migration impact, and recommended decision |
| Scope | Adding outcomes or work beyond the approved task or sprint | Reason, impact on scope and schedule, alternatives, and revised acceptance criteria |
| Dependencies and services | Installing or adding a dependency, external service, paid service, paid API, or new network reliance | Need, license and cost, maintenance and privacy risks, alternatives, and removal path |
| Destructive action | Deleting or overwriting material data, history, branches, environments, or other difficult-to-recover state | Exact target, consequence, recovery or backup plan, and safer alternative |
| Merge | Merging any pull request | Review outcome, test evidence, unresolved findings, and acceptance status |
| Release or deployment | Creating a release, publishing an artifact, or deploying | Version and contents, validation evidence, known risks, rollback plan, and destination |

Approval for one gate does not satisfy another. Approval is task-specific and expires when the approved work completes, the scope materially changes, or the human withdraws it.

Read-only discovery, analysis, planning, documentation explicitly requested by the human, and non-mutating validation may proceed without a separate implementation approval when they remain within the requested scope. Agents must not use those activities to make hidden implementation changes.

## Supervised-session boundary

All development occurs during an active human-supervised session in which the human can receive updates, answer questions, and interrupt work.

- Do not create or use scheduled tasks for development.
- Do not continue work after the human ends or leaves the session.
- Do not start background implementation or autonomous follow-on work.
- A long-running or background operation may run only when the human explicitly requests it, remains in the active session, and can interrupt it.
- Stop promptly when interrupted or asked to stop. Do not resume without a new human instruction.
- Complete only the current approved task. Never begin the next task or sprint automatically.

If session state is uncertain, pause at the next safe point and ask the human before continuing.

## Execution boundaries

Within approved scope, agents may perform normal, reversible implementation steps and proportional validation. Agents must stop and escalate when they encounter:

- Missing, ambiguous, or conflicting acceptance criteria that could materially change the result.
- A need to cross any approval gate not already covered.
- A blocker that would require scope expansion, weaker quality, or a different architecture.
- Risk to data, privacy, security, licensing, attribution, credentials, or irreversible state.
- Unexpected changes owned by another contributor that cannot safely be preserved.
- Inability to obtain independent review or executable evidence appropriate to the risk.
- Unavailable GitHub or tool access needed to complete or verify a claimed action.

An escalation must state what is known, what is uncertain, why it matters, available options, the recommended option, and the exact decision or permission required. Report blockers honestly; do not silently work around governance.

## GitHub governance

GitHub is the operational source of truth:

- Issues hold requirements, tasks, bugs, and spikes.
- Projects hold backlog and sprint status.
- Milestones hold releases and major delivery targets.
- Pull Requests hold review and integration history.
- Repository Markdown holds architecture, Architecture Decision Records, and development processes—not a duplicate backlog.
- GitHub Actions provide automated validation when configured.

Agents must preserve traceability between approved work, its Issue or sprint item when one exists, its Pull Request, validation evidence, and relevant decision records.

Agents must not:

- Invent Issue, Project, Milestone, Pull Request, review, or Action state.
- Close important Issues without human direction.
- Approve their own Pull Requests or treat self-review as independent review.
- Merge Pull Requests, create releases, or deploy without explicit human approval.
- Claim a GitHub action succeeded when access was unavailable or the result was not observed.

When GitHub access is unavailable, continue only with work that does not depend on it and clearly report the limitation and any unrecorded state.

## Evidence and reporting

An agent may claim completion only when the approved acceptance criteria have been checked. Reports must separate:

- Observed facts from assumptions and recommendations.
- Tests run and their actual outcomes from tests not run.
- Completed scope from partial or deferred scope.
- New defects or debt from pre-existing conditions.
- Agent recommendations from human decisions and approvals.

Tests are executable evidence, not a substitute for independent review. Review is evidence, not authorization to merge or release.

## Behavioral policy and technical enforcement

The rules in `AGENTS.md` and these documents are instructions interpreted by agents. They do not technically guarantee compliance, user presence, interruption handling, or the absence of background execution.

Codex sandbox and approval settings can technically restrict filesystem, network, and command behavior, but their protection depends on the selected execution surface and configuration. They do not encode product approval, sprint scope, architectural significance, or whether a human is actively supervising.

Scheduled tasks are technically available on some Codex and ChatGPT surfaces and can run unattended. This project prohibits using them for development regardless of availability.

Before implementation begins, define and test appropriate technical controls where supported, including:

- A restrictive sandbox and user-routed approval policy.
- No scheduled development tasks or event-triggered development runs.
- Least-privilege GitHub access and branch protection requiring human merge authority.
- Required status checks and independent review for protected branches.
- Restricted network access and explicit dependency installation approval.
- Secret scanning and protections against committing credentials or private data.
- Auditability of approvals, tool activity, test results, reviews, merges, and releases.

Where native Codex controls cannot enforce a governance rule, use repository hosting controls, operating-system isolation, CI checks, and human procedure. Until a required control is configured and verified, treat the rule as behavioral and report that limitation rather than claiming enforcement.
