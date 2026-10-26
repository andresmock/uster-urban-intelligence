---
name: sprint-review
description: Review an actual completed sprint against its approved goal and acceptance criteria, then run a concise retrospective. Use when delivery and quality evidence exist and human acceptance or process feedback is needed; do not simulate a sprint.
---

# Sprint Review

Follow `AGENTS.md` and the development governance documents. State that `$sprint-review` is active.

## Preconditions

- An approved Sprint Goal, scoped work, and acceptance criteria exist.
- Delivery, test, and review evidence is available; missing evidence is explicitly identified.

## Roles

Alex coordinates, Max presents quality evidence, and Sam evaluates product outcomes. Add implementers only to demonstrate or clarify their work.

## Procedure

1. Restate the approved Sprint Goal and scope.
2. Separate completed, partial, failed, and deferred work.
3. Compare observed outcomes with each acceptance criterion and present test and review evidence.
4. Demonstrate functionality when possible and authorized; identify defects, limitations, and technical debt.
5. Ask the human for acceptance or feedback.
6. Retrospect on what worked, delays, collaboration value, delegation overhead, role clarity, and approval-gate compliance.
7. Propose a small number of concrete improvements with expected benefit and a way to verify them.
8. Stop before changing governance or starting another sprint.

## Output

Report Sprint Goal status, delivered and incomplete outcomes, acceptance-criteria status, quality evidence, open issues, human feedback required, retrospective findings, and proposed improvements.

## Approval and stopping

Only the human accepts the sprint and approves governance or responsibility changes. Completion does not authorize the next sprint. Do not create follow-up Issues or apply improvements without the required approval.

## Failure and escalation

If the sprint goal, scope, or evidence is missing, do not reconstruct success from agent claims. Report what can be verified, mark the remainder unknown, and request the missing evidence or human direction.
