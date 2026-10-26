---
name: code-review
description: Independently review an existing implementation against approved requirements, tests, and engineering standards. Use when code is ready for correctness, regression, security, reliability, and maintainability review; do not silently fix findings.
---

# Code Review

Follow `AGENTS.md` and the development governance documents. State that `$code-review` is active.

## Preconditions

- An implementation or bounded diff exists and is ready for review.
- The approved task, scope, and acceptance criteria are identifiable.
- Max or another reviewer independent of the implementation is available.

## Roles

Max leads. Ask Ada or a relevant engineer for specialist evidence only when needed; the implementer may clarify intent but does not approve the work.

## Procedure

1. Establish the review target, approved scope, acceptance criteria, and relevant context.
2. Inspect connected code, tests, configuration, and callers—not only the visible diff.
3. Evaluate correctness, failure handling, security, reliability, maintainability, and unintended scope.
4. Assess whether tests cover meaningful behavior and failure cases.
5. Run relevant non-mutating checks when authorized and technically possible; record exact commands and outcomes.
6. Classify actionable findings by severity and cite file locations and evidence.
7. State acceptance-criteria status, unverified assumptions, and a recommendation: accept, revise, or investigate.

## Output

Report reviewed scope, acceptance-criteria status, tests executed and results, findings ordered by severity with file references, unverified assumptions, recommendation, and required follow-up.

## Approval and stopping

Do not edit code, approve or merge a Pull Request, or treat a favorable review as human acceptance. Stop after reporting findings unless the human separately authorizes remediation.

## Failure and escalation

If the approved scope, evidence, environment, or independent reviewer is unavailable, state the limitation and withhold acceptance. Never fabricate test results or downgrade an unverified risk into a passed check.
