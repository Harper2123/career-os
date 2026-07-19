# Git and GitHub Workflow Standard

## Purpose

This document defines the minimum issue, branch, commit, pull-request, review, merge, and closure workflow for Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories.

The workflow should provide traceability and review without turning personal work into unnecessary administration.

## Default workflow

```text
Issue → branch → first attempt → incremental commits → push → draft PR → self-review → review → revisions → merge → issue closure → branch cleanup
```

The default unit of work is one coherent issue that can usually be advanced or completed in one to three focused sessions.

## Health and capacity boundary

A workflow does not create a catch-up obligation.

When work stops because of fatigue, coursework, job pressure, or recovery needs:

- leave a small resume note in the issue when useful;
- keep unfinished work unfinished;
- do not double the next session;
- do not merge merely to remove an open item;
- return when capacity allows.

## Issue standard

### Required issue content

An actionable issue should state:

1. **Purpose:** why the work matters now.
2. **Scope:** the coherent outcome included in this issue.
3. **Acceptance criteria:** observable conditions that prove completion.
4. **Verification:** tests, checks, calculations, review evidence, or reproducibility evidence required.
5. **Exclusions:** related work that is intentionally out of scope.

Add context, risks, dependencies, references, or a resume note only when they improve execution.

### Issue sizing

Prefer an issue that produces one coherent outcome.

Split an issue when it combines independently valuable outcomes, requires unrelated reviewers, or cannot be reviewed safely as one change.

Do not split work merely to increase issue or contribution counts.

### Research issue additions

A research or experiment issue should also record, where applicable:

- research question or hypothesis;
- motivation and relationship to prior work;
- dataset or source provenance;
- baseline or comparison method;
- metrics and evaluation plan;
- reproducibility requirements, including seeds and environment assumptions;
- expected evidence, limitations, and possible negative results.

An issue may represent exploratory work without promising a positive result.

## Branch standard

### Normal issue branches

Use:

```text
<type>/<issue-number>-<short-slug>
```

Approved common types:

```text
feat
fix
docs
test
refactor
research
chore
```

Examples:

```text
feat/42-add-calibration-report
fix/58-handle-missing-prices
docs/63-clarify-reproduction-steps
research/71-reproduce-volatility-baseline
```

The issue number links the branch to its source decision. The slug should describe the outcome, not the implementation sequence.

### Career OS setup branches

Top-level setup work follows Decision 0002:

```text
setup/step-<X>
```

One setup branch and one pull request cover the full authorised top-level setup step. Do not create additional practice or substep branches inside that setup unit.

### Branch rules

- branch from clean, current `main` unless an approved dependency requires another base;
- keep one coherent issue on one branch;
- do not reuse a merged branch for new work;
- do not force-push or rewrite shared history during the normal personal workflow;
- remove merged local branches after synchronising `main`;
- allow GitHub to delete merged remote head branches automatically.

## First-attempt rule

For conceptual, mathematical, implementation, and research work, make a genuine first attempt before asking an AI assistant for a complete solution.

Infrastructure setup may receive direct, detailed guidance when struggle adds little learning value.

The first attempt does not need to be correct. It must provide enough evidence for meaningful review.

## Commit standard

### Format

Use Conventional Commit-style messages where practical:

```text
<type>(optional-scope): imperative summary
```

Common types:

```text
feat
fix
docs
test
refactor
perf
build
ci
chore
research
```

Examples:

```text
feat(pricing): add binomial calibration output
test(pricing): cover zero-volatility boundary
docs: explain experiment reproduction steps
research(volatility): record baseline comparison
```

`research` is an accepted Career OS type for experiment design, reproduction evidence, result analysis, and research documentation that does not fit a product feature or bug fix.

### Commit quality

A commit should:

- represent one meaningful change;
- keep code, tests, and documentation together when they form one inseparable outcome;
- avoid mixing unrelated concerns;
- leave the repository in a reviewable state where practical;
- explain why in the body when the reason is not obvious from the change;
- exclude generated clutter, credentials, private data, and restricted materials.

Do not optimise for a high commit count. Temporary local fix-up commits may exist during work, but the final branch history should remain understandable without rewriting shared history.

## Push standard

Before the first push:

- confirm the intended branch;
- inspect `git status` and the staged diff;
- run the verification appropriate to the current change;
- confirm no private or restricted material is included.

Push normally without `--force` or `--force-with-lease`.

The first push should occur after a coherent initial slice exists. An empty branch provides no useful review evidence.

## Draft pull-request standard

Create a draft pull request after the first coherent implementation or documentation slice is pushed and early review would be useful.

A draft pull request should contain:

1. **Summary:** what outcome the branch is pursuing.
2. **Linked issue:** normally `Closes #<number>` when merge should close the issue.
3. **Changes:** the meaningful changes already made.
4. **Verification:** commands, tests, calculations, or manual checks run.
5. **Risks and limitations:** known uncertainty, edge cases, or research limitations.
6. **Technical debt:** `None` or links to explicitly recorded debt.
7. **Privacy check:** confirmation that no restricted material is included when relevant.

Keep the pull request in draft while major scope, correctness, or verification work remains.

Mark it ready for review only after:

- the issue acceptance criteria appear satisfied;
- the branch is current enough to review safely;
- verification has been run;
- the author has reviewed the full diff;
- limitations and debt are stated honestly.

## Review standard

Review the change according to what applies:

- architecture and scope coherence;
- functional and mathematical correctness;
- numerical stability;
- naming and readability;
- edge cases and failure behaviour;
- tests and verification quality;
- documentation and reproducibility;
- data provenance and experiment validity;
- security, privacy, and secret handling;
- maintainability and unnecessary complexity.

A reviewer should distinguish:

- **blocking findings:** correctness, security, privacy, reproducibility, or scope defects that invalidate safe completion;
- **non-blocking improvements:** useful refinements that may be accepted now or recorded separately;
- **questions:** requests for clarification where evidence is incomplete.

Review should challenge weak assumptions. It should not manufacture changes merely to demonstrate that review occurred.

## Revision standard

Respond to each blocking review finding with one of:

- a revision and verification evidence;
- a reasoned disagreement supported by evidence;
- a documented scope change approved in the issue or pull request.

Create a new commit for meaningful review-driven changes. Do not hide the review trail through force-push rewriting.

When review produces no justified code or documentation change, record a concise no-change rationale.

## Technical-debt standard

Technical debt is not a synonym for unfinished scope.

Record debt when a conscious compromise remains after the issue's acceptance criteria are met.

Debt that can affect correctness, security, privacy, reproducibility, or the validity of research results is normally blocking.

Non-blocking debt should be recorded as a separate issue containing:

- the compromise;
- impact and affected area;
- why deferral is acceptable;
- evidence or trigger for revisiting it;
- relationship to the originating pull request.

Do not bury durable debt only in a chat, commit message, or pull-request comment.

## Merge strategy

### Routine single-issue project work

Default to **squash merge** when the branch contains implementation scaffolding or incremental commits that do not need to remain first-class commits on `main`.

The pull-request title should then be suitable as the final Conventional Commit-style squash message.

### Career OS top-level setup steps

Use a **merge commit** for `setup/step-<X>` branches. This preserves the top-level checkpoint and the verified sequence of authorised substeps governed by Decision 0002.

### Research and experiment work

Use squash merge by default for a routine bounded research issue.

Use a merge commit when preserving a meaningful sequence of experiment design, reproduction, comparison, and revision commits materially improves auditability or reproducibility. State that reason in the pull request before merging.

Rebase merge is not the default Career OS strategy.

Never merge while required checks or blocking review findings remain unresolved.

## Issue closure and evidence

Prefer automatic issue closure through `Closes #<number>` in the accepted pull request.

At closure, the issue or pull request should make it possible to identify:

- the merged pull request;
- the acceptance criteria satisfied;
- verification performed;
- important decisions and limitations;
- linked technical-debt issues, or an explicit statement that none remain.

Close an issue as not planned when the work is deliberately abandoned or superseded. Do not mark it completed merely to remove it from view.

## Post-merge cleanup

After merge:

1. confirm the pull request and intended issue are closed;
2. confirm the remote head branch was deleted automatically;
3. switch the canonical checkout to `main`;
4. fetch and prune remote references;
5. fast-forward `main` to `origin/main`;
6. delete the merged local branch;
7. verify clean status and zero ahead/behind counts;
8. update durable current state when the work changes Career OS operation.

Do not use force deletion when normal merged-branch deletion should succeed. Investigate first if Git considers a branch unmerged.

## Public and private boundary

Never commit:

- raw WQU course materials;
- active graded questions or submissions;
- employer or client confidential information;
- private datasets or licensed data that cannot be redistributed;
- credentials, tokens, SSH private keys, or secrets;
- private personal or health information;
- private paper drafts or reviewer correspondence unless intentionally cleared for public release.

Use synthetic, public, anonymised, or explicitly redistributable evidence in public repositories.

For research, record enough provenance to reproduce the public workflow without publishing restricted source material.

## Tooling policy

The baseline workflow uses:

- WSL Git for local repository operations;
- GitHub issues and pull requests as durable collaboration records;
- VS Code Source Control for diff inspection and normal Git work;
- GitHub Pull Requests and Issues for review from VS Code when useful;
- ChatGPT as a mentor and reviewer, with durable outcomes written back to GitHub.

GitHub CLI is optional. Do not install it merely to increase tool count. Add it only when repeated workflow friction demonstrates a real need.

## Template policy

Career OS v1 does not require repository-wide issue or pull-request templates yet.

Use the headings in this standard for the Step 5 practice issue and pull request. Add templates only after repeated omissions or friction demonstrate that automation would reduce mistakes without creating administrative overhead.

## Progress measurement

Do not measure progress primarily by issues closed, branches created, pull requests merged, commits made, or contribution streaks.

Better evidence includes:

- coherent outcomes completed;
- review findings resolved;
- tests and reproducibility improved;
- decisions made traceable;
- research claims supported by evidence;
- private boundaries preserved;
- health and fixed commitments maintained.
