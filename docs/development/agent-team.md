# Codex Agent Team

## Overview

Uster Urban Intelligence uses six project-scoped custom Codex agents. They provide specialist perspectives and bounded execution while the human retains all decision rights defined in [Governance](governance.md). Team behavior is governed by [AGENTS.md](../../AGENTS.md) and the [Team Charter](team-charter.md).

| Agent | Responsibility |
| --- | --- |
| Alex (`alex`) | Coordinates relevant specialists and summarizes decisions required |
| Sam (`sam`) | Clarifies requirements, user value, stories, and acceptance criteria |
| Ada (`ada`) | Compares architecture, technology, boundaries, risks, and trade-offs |
| Bob (`bob`) | Handles approved backend, data, and geospatial implementation |
| Eve (`eve`) | Handles approved frontend, map, and visualization implementation |
| Max (`max`) | Performs independent QA and evidence-based review |

## Configuration

Project multi-agent support is enabled in `.codex/config.toml`, where all six identifiers are explicitly registered under `[agents.<identifier>]`. Each registration references `.codex/agents/<identifier>.toml`, which defines the native `name`, `description`, and `developer_instructions` fields. No role pins a model or reasoning level; each inherits the parent session's supported settings.

Codex loads project-scoped configuration only for a trusted project. Start a new Codex session after configuration changes so discovery uses the current files.

## Invocation and delegation

Ask Codex directly to delegate to a named role, for example:

- `Use Sam to turn this approved idea into testable acceptance criteria.`
- `Ask Ada and Bob to independently compare these storage options, then have Alex summarize their disagreements and the human decision required.`
- `Use Max to review this change without modifying it.`

In the CLI, `/subagents` displays agent threads. Supported app and IDE interfaces expose their activity in the subagent panel. Invoke only roles relevant to the task; subagents add cost and context overhead.

Alex may coordinate specialists through native delegation when the active Codex surface exposes multi-agent tools. If nested delegation is unavailable, the main session should invoke the specialists and give their results to Alex for synthesis. A specialist's report returns to the parent session; it never constitutes human approval.

## Operating modes

The modes in `AGENTS.md` apply to every role:

- **DISCUSS** for read-only exploration, evidence, alternatives, and recommendations.
- **PLAN** for requirements, acceptance criteria, architecture proposals, and implementation plans without implementation.
- **EXECUTE** only for an explicitly approved scope.

If no mode or implementation authorization is explicit, agents default to DISCUSS. They cannot promote themselves to EXECUTE.

## Discussion protocol

For a material question, Alex states the topic and asks only relevant specialists for independent input. Each visible contribution uses this form:

```text
<Name> — <Perspective>
Facts and evidence:
Assumptions and uncertainties:
Recommendation and trade-offs:
Risks or limitations:
```

Alex then reports the options, meaningful agreements and disagreements, recommendation, unresolved questions, and exact human decision required. The format is optional for trivial questions, and it exposes explicit arguments rather than private model reasoning.

## Technical limitations

- Subagents inherit the parent session's sandbox, approval policy, provider, and MCP servers. Role instructions can request read-only behavior but cannot create a separate read-only sandbox.
- DISCUSS, PLAN, EXECUTE, human supervision, and product approval are behavioral rules; TOML configuration does not technically enforce them.
- Discovery requires a trusted project and a session that loaded the current project configuration.
- Native delegation is model-directed rather than a fixed workflow. Alex cannot guarantee which roles run unless the prompt explicitly names them.
- In the read-only validation on Codex CLI 0.164.0, all roles were discovered and the requested discussion produced a synthesis, but Alex's nested delegation emitted ephemeral thread-store and thread-limit errors before retrying. Until this is retested successfully in a normal interactive session, prefer main-session delegation with Alex synthesizing the returned specialist reports.
- Concurrent agents share the repository. Avoid parallel write-heavy tasks; assign non-overlapping files or serialize changes.
- Human-visible agent output does not expose private model reasoning.

## Changing the team

To add an agent, create `.codex/agents/<identifier>.toml` with a unique `name`, a specific discovery `description`, and focused `developer_instructions` that reference the governing documents. To modify a role, edit its existing file and keep authority boundaries consistent with Governance.

Validate TOML and strict Codex configuration, then start a new session and run a read-only discovery test. Changes to responsibilities, permissions, or governance require explicit human approval.
