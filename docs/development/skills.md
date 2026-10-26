# Reusable Team Skills

Uster Urban Intelligence stores repository-wide Codex skills under `.agents/skills/`. They define repeatable workflows; agent responsibilities and decision authority remain in the [Team Charter](team-charter.md), [Agent Team](agent-team.md), and [Governance](governance.md).

## Available skills

| Skill | Purpose | Expected users |
| --- | --- | --- |
| `team-discussion` | Produce a multi-agent decision briefing without changing project state | Alex with relevant specialists |
| `sprint-planning` | Prepare a focused sprint proposal from approved priorities | Alex, Sam, and relevant specialists |
| `architecture-decision` | Compare consequential technical choices for human approval | Ada with relevant engineering and QA input |
| `code-review` | Independently review an implementation and its evidence | Max with specialists as needed |
| `sprint-review` | Evaluate an actual sprint and conduct a concise retrospective | Alex, Max, Sam, and implementers as needed |

Together they cover Discover and Specify, the human approval gate, Validate, and Review. They do not authorize Build, merge, release, deployment, or a new sprint.

## Discovery and invocation

From the repository, use `/skills` in Codex CLI to list discovered skills. Invoke one explicitly with `$<skill-name>`, for example:

```text
$team-discussion Should the MVP use GeoParquet or PostgreSQL/PostGIS?
$sprint-planning Prepare a Sprint 1 proposal from the approved priorities.
$code-review Review the current implementation without modifying it.
```

Codex may select a skill automatically when a request matches its frontmatter description. Explicit invocation is preferable when the required workflow matters. Confirm loading by selecting it through `/skills` or using `$<skill-name>` and checking that Codex announces the active skill before following its procedure. If a new or changed skill is absent, reload the skill list or restart Codex.

Repository skills are discoverable to every agent; their directory does not restrict them to named roles. Agent instructions contain routing cues, but those cues are behavioral. Supported `skills.config` settings can disable a skill by path for an agent, but this project does not add restrictions because collaboration requires shared access.

## Maintenance and testing

To add a skill, create `.agents/skills/<name>/SKILL.md` with matching lowercase-hyphenated `name`, a discriminating `description`, and the smallest complete workflow. Add scripts, references, assets, or UI metadata only when they provide a concrete benefit.

Review existing content before updates. Validate each skill with the bundled skill-creator validator, confirm discovery in a fresh Codex session, and run a realistic read-only test when behavior matters. Tests must verify observable behavior, approval gates, and side effects rather than matching exact prose.
