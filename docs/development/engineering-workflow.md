# Engineering Workflow

This document defines the repository's lightweight engineering workflow. The approval gates and decision rights in [Governance](governance.md) remain authoritative; this workflow does not replace or weaken them.

## Branching strategy

`main` is the protected integration branch. Changes go through Pull Requests; normal direct pushes, force pushes, and deletion are prohibited. Use short-lived branches focused on one approved task or a small coherent change:

- `feat/<issue-number>-short-description`
- `fix/<issue-number>-short-description`
- `chore/<issue-number>-short-description`
- `docs/<issue-number>-short-description`
- `test/<issue-number>-short-description`

Prefer squash merges and do not create a long-lived development branch.

## Development and Pull Request process

1. **Approved Issue:** The human approves scope and acceptance criteria in a GitHub Issue. Alex coordinates only that approved scope.
2. **Implementation:** Bob or Eve implements on a feature branch, adds appropriate tests, runs relevant local checks, documents significant changes, and avoids unrelated modifications.
3. **Independent QA:** Max checks the acceptance criteria, connected code, correctness, regressions, test coverage, security, and maintainability. Findings include severity, evidence, and file locations. Max reports findings and does not silently modify the implementation.
4. **Feedback loop:** The implementer addresses findings and Max revalidates affected work until blocking findings are resolved. This loop needs no additional approval while it remains within approved scope, the supervised session stays active, and it introduces no new architecture, dependency, destructive action, or other approval gate.
5. **Pull Request and CI:** The PR links its approved Issue and records acceptance evidence, local validation, independent QA, risks, and limitations. CI failures are investigated and fixed within scope; affected changes receive relevant local checks and QA revalidation.
6. **Human review:** Alex checks the Definition of Ready for Human Review and presents the PR link, Issue, change summary, acceptance status, QA summary, CI results, and remaining risks. Alex cannot approve for the human.
7. **Merge:** Merge only after explicit human authorization. A passing check, completed checklist, or favorable agent review is not merge approval. Merging does not authorize a release or deployment.

No agent represents Max's QA as a native GitHub review approval. Because the repository has one human owner, the branch policy does not require a separate GitHub reviewer identity; the independent QA record remains in the PR.

### Pull Request transparency

The PR body is the concise, current decision summary. It identifies only the agents who materially participated, their roles, contributions, and supporting evidence. It also records every actionable finding or material concern with its source, impact, owner, status, and resolution or revalidation evidence. If QA finds nothing actionable, the record still states the reviewed scope, checks and results, unverified assumptions, and recommendation.

Use stable concern statuses: `Open`, `Fixed—awaiting revalidation`, `Resolved`, `Accepted risk`, or `Deferred`. Only the human may accept a risk. `Deferred` is limited to non-blocking work outside the approved scope and links to a GitHub Issue. Deferring approved scope or a blocking concern requires an explicit human scope or risk decision, and the PR is not ready until that decision is recorded. Unmet acceptance criteria cannot be deferred while the PR remains ready for human review.

Use timestamped PR comments for material QA reports, corrections and revalidation, scope or architecture escalations, and unresolved disagreement when preserving chronology helps the decision. Attribute Codex reports by agent name while making clear they were posted through the shared GitHub identity. Do not log routine commands or duplicate the full working conversation.

Monitoring and interruption details are optional. Record exceptional stalls, retries, or elapsed phases only when timestamps or tools provide observable evidence. Label durations as elapsed wall-clock time, never active work or productivity. Do not estimate missing durations or publish private reasoning, raw prompts, token usage, credentials, secrets, or private data. Alex verifies the final summary before marking the PR ready.

## Definition of Done

Implementation is done when:

- the approved scope is implemented and the acceptance criteria are satisfied;
- relevant tests are added or updated and local checks pass;
- Max has completed independent QA and all blocking defects are resolved;
- relevant documentation is updated; and
- the change is ready for integration, with known limitations disclosed.

Definition of Done means implementation completion. It does not constitute final human acceptance, merge authorization, release approval, or deployment approval.

## Definition of Ready for Human Review

A Pull Request is ready for final human approval only when:

1. All acceptance criteria have been verified.
2. Max has completed independent QA.
3. All blocking QA findings have been resolved.
4. All required CI checks are passing.
5. Relevant documentation has been updated.
6. Remaining limitations and risks are explicitly disclosed.
7. Changes made after QA have been appropriately revalidated.

Alex checks and reports readiness but has no authority to approve or merge on behalf of the human.

## Continuous integration

`.github/workflows/ci.yml` runs on Pull Requests targeting `main` and pushes to `main`. It has read-only repository permission and uses GitHub-hosted runners with official actions pinned to immutable commits.

The initial `Repository validation` job parses tracked TOML configuration and syntax-checks tracked Python files under `apps/` and `tests/`. There is no application test suite or frontend toolchain yet, so CI does not run placeholder tests or install speculative dependencies. When an approved component introduces a test suite or frontend toolchain, its lockfile-based lint, test, and build commands must be added as separate, meaningful checks.

The local equivalent of the current validation is the Python script embedded in the workflow. Remote CI is successful only when GitHub reports a successful run; local results do not substitute for that evidence.

## Branch protection and merge settings

The intended `main` ruleset is:

- require changes through a Pull Request;
- require zero native approving reviews, so the solo human owner is not locked out;
- require the observed `Repository validation` CI status after its first successful GitHub run;
- prevent force pushes and deletion, with no routine bypass actors;
- allow squash merges only; and
- delete merged feature branches automatically.

The settings must be applied only with explicit human approval. Required status checks are configured only after the workflow has produced the real check context. Until the ruleset and effective protection are verified through GitHub, these controls are intended policy rather than confirmed technical enforcement.

## Human approval gates

The human remains the approval authority for architecture, sprint scope, dependencies and services, destructive operations, merges, releases, and deployments. Any correction that crosses one of those gates stops the feedback loop and returns to the human. CI and branch protection enforce selected technical conditions; they do not infer product acceptance or replace explicit human decisions.
