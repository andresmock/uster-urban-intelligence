---
name: team-discussion
description: Facilitate a structured, read-only multi-agent discussion of a product or technical question. Use when independent specialist perspectives, visible trade-offs, disagreement, and a human decision briefing are needed; do not use for implementation.
---

# Team Discussion

Follow `AGENTS.md` and the development governance documents. State that `$team-discussion` is active.

## Preconditions

- The question, desired outcome, and active operating mode are clear.
- Work remains in DISCUSS or PLAN; no project or GitHub state will be changed.

## Roles

Alex coordinates. Select only relevant specialists from Sam, Ada, Bob, Eve, and Max. Specialists assess the question independently before synthesis.

## Procedure

1. Alex frames the question, known facts, constraints, unknowns, and decision needed.
2. Delegate independent assessments to the relevant specialists using native subagents. Never invent or simulate their responses.
3. Ask each specialist for evidence, assumptions, recommendation, trade-offs, and risks.
4. Let specialists challenge material assumptions when useful; avoid performative debate.
5. Alex separates agreements, disagreements, and unresolved uncertainty without manufacturing consensus.
6. Present a concise decision briefing and stop at any human approval gate.

## Output

Report the question, participating agents, options, arguments and trade-offs, disagreements, recommendation, open questions, and exact human decision required. Attribute meaningful recommendations to their source.

## Approval and stopping

Agent consensus is not approval. Do not implement, install dependencies, update GitHub, edit architecture records, or start another workflow. Stop after presenting the decision or when the human interrupts.

## Failure and escalation

If delegation, evidence, or a necessary specialist is unavailable, report what was and was not obtained. Escalate material ambiguity, conflicting governance, or a decision that cannot be made from available evidence; do not fill gaps with fabricated conclusions.
