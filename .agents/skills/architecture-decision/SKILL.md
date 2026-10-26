---
name: architecture-decision
description: Compare significant technical or architectural choices and prepare an evidence-based recommendation for human approval. Use for consequential boundaries, storage, interfaces, security, or foundational technology; not for trivial implementation choices.
---

# Architecture Decision

Follow `AGENTS.md` and the development governance documents. State that `$architecture-decision` is active.

## Preconditions

- The architectural problem, current mode, and decision authority are clear.
- Relevant requirements and constraints are available or explicitly marked unknown.

## Roles

Ada leads. Request independent input from Bob, Eve, or Max only when their domains affect the decision. Alex may coordinate a broader discussion.

## Procedure

1. Define the problem, scope, constraints, and decision criteria.
2. Identify at least two viable alternatives when meaningful; do not manufacture alternatives when only one is feasible.
3. Compare complexity, maintainability, local-first operation, open-source fit, cost, testing, security, migration impact, and future extensibility.
4. Surface specialist evidence, assumptions, risks, and meaningful disagreement.
5. Recommend the simplest option that satisfies the known needs.
6. Present the decision and consequences for explicit human approval.
7. Only after approval and separate authorization, prepare an ADR in `docs/architecture/decisions/`.

## Output

Report the problem, constraints, alternatives, trade-off comparison, recommendation, risks, unresolved assumptions, consequences, and exact human decision required.

## Approval and stopping

Architecture recommendations are not decisions. Stop at the human approval gate. Do not introduce dependencies or services, implement the choice, or create an ADR during read-only DISCUSS mode.

## Failure and escalation

If evidence or requirements cannot distinguish viable options, recommend a bounded spike or benchmark and state its acceptance criteria. Escalate conflicts involving governance, cost, licensing, privacy, security, or irreversible migration.
