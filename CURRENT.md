# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, 3, and 4 are complete. Step 5 is active.

## Active setup branch

- Working branch: `setup/step-5`
- Base branch: `main`
- Base checkpoint: `c300278415f42af17636005537682948927b9714`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- `main` remains the last merged top-level checkpoint.
- One pull request will be created only after the full Step 5 completion condition is met.
- Unrelated work must not be added to this branch.

## Current objective

Establish and practise one reliable Git and GitHub workflow covering:

```text
Issue → branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → issue closure
```

The workflow must be suitable for Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories without creating excessive process overhead.

## Current task

**Step 5.1 is active: inventory and workflow design.**

Before creating the harmless practice issue, verify the current local and remote Git/GitHub state and define the minimum conventions that the practice cycle will test.

Do not create an additional practice branch or pull request yet. Decision 0002 requires one working branch and one final pull request per top-level setup step. The Step 5 practice issue will therefore be implemented and closed through `setup/step-5` and its final pull request.

## Step 5 execution model

1. **Step 5.1: active.** Inventory current Git/GitHub state and define the harmless practice issue.
2. **Step 5.2:** record the minimum workflow standard, including issue quality, branch names, Conventional Commits, draft PRs, reviews, revisions, debt, merge strategy, and closure evidence.
3. **Step 5.3:** create the practice issue and execute the issue-to-draft-PR path on `setup/step-5`.
4. **Step 5.4:** perform senior review, make at least one justified revision, decide whether any debt exists, and merge only after acceptance.
5. **Step 5.5:** verify issue closure, automatic remote branch deletion, clean local `main`, and durable handoff state.

Later units remain gated. Listing them does not authorise them.

## Step 5 definition of done

Step 5 is complete only when one harmless practice issue proves:

- the issue states purpose, scope, acceptance criteria, and exclusions;
- the branch name is coherent and linked to the issue;
- commits are small, meaningful, and use Conventional Commit-style messages where practical;
- the branch is pushed without force;
- a draft pull request is created and linked to the issue;
- review checks architecture, correctness, naming, readability, edge cases, tests or verification, documentation, reproducibility, security, and maintainability as applicable;
- at least one review-driven revision is made or an explicit no-change rationale is recorded;
- technical debt is either absent or recorded without blocking justified completion;
- the accepted merge strategy is used;
- the issue is closed with evidence;
- the remote head branch is deleted automatically;
- the canonical local checkout returns to clean, up-to-date `main` with the merged local branch deleted;
- the durable Git and GitHub workflow standard is stored in the repository.

## Governing workflow constraints

- Follow Decision 0002: one branch and one pull request per top-level setup step.
- Do not force-push, rewrite shared history, or bypass review merely to make the practice cycle look clean.
- Do not create commits that mix unrelated concerns.
- Do not treat commit count, issue count, PR count, or contribution streaks as progress measures.
- Preserve private course materials, graded work, confidential information, credentials, private datasets, and private health information outside the public repository.
- Research and future paper work must favour reproducibility, traceable decisions, experiment evidence, and clear separation between exploratory notebooks and reusable tested code.
- Step 6 remains unauthorised.

## Current repository state

The Step 4 closure completed successfully:

- pull request `#24` merged into `main`;
- merge commit `c300278415f42af17636005537682948927b9714`;
- canonical checkout is on clean `main`;
- local and remote `setup/step-4` branches are absent;
- upstream is `origin/main`;
- local ahead and behind counts are both zero.

The remote `setup/step-5` branch was created from the Step 4 merge checkpoint when Step 5 was authorised.

## Research and PhD direction

Potential PhD preparation and publication-quality research are binding Career OS design requirements.

Step 5 does not create a paper workflow, but the Git/GitHub standard must support later research work through:

- reproducible experiment histories;
- issue-based research questions and hypotheses;
- reviewable code and analysis changes;
- traceable limitations and technical debt;
- clear evidence for results and revisions;
- clean separation of public code from private or restricted materials.

The full research and paper-development system remains in scope for Step 9.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, coursework, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

No technical blocker is known. Step 5.1 requires a read-only local and remote workflow inventory before the practice issue is created.

## Next action

Complete the Step 5.1 inventory and stop for review before beginning Step 5.2.
