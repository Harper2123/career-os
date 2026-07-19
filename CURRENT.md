# Current State

_Last updated: 2026-07-19_

## Operating mode

**Career OS setup mode**

Steps 1, 2, 3, and 4 are complete. Step 5 is active.

## Active setup branch

- Working branch: `setup/step-5`
- Base branch: `main`
- Base checkpoint: `c300278415f42af17636005537682948927b9714`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- `main` remains the last merged top-level checkpoint.
- Unrelated work must not be added to this branch.

## Current objective

Establish and practise one reliable Git and GitHub workflow:

```text
Issue → branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → issue closure
```

The workflow must support Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories without creating excessive process overhead.

## Current task

**Step 5.3 is complete. Step 5.4 has not been authorised.**

Practice issue:

```text
#25 docs: document session-local SSH agent use
```

Draft pull request:

```text
#26 docs: establish Git and GitHub workflow
```

The issue arose from observed workflow friction rather than an invented exercise. It uses the existing `setup/step-5` branch under Decision 0002 rather than creating a nested issue branch.

Do not begin formal review, revise the documentation, mark the pull request ready, merge, close the issue manually, or start cleanup before the exact instruction:

```text
Proceed to Step 5.4
```

## Step 5 execution model

1. **Step 5.1: complete.** Inventory current Git/GitHub state and define the harmless practice issue.
2. **Step 5.2: complete.** Record the minimum workflow standard.
3. **Step 5.3: complete.** Create issue #25, implement and push the first attempt, and open linked draft PR #26.
4. **Step 5.4: not authorised.** Perform senior review, make at least one justified revision or record an evidence-based no-change rationale, decide whether debt exists, mark the PR ready, and merge only after acceptance.
5. **Step 5.5: not authorised.** Verify issue closure, automatic remote branch deletion, clean local `main`, and durable handoff state.

## Step 5 definition of done

Step 5 is complete only when one harmless practice issue proves:

- the issue states purpose, scope, acceptance criteria, verification, and exclusions;
- the branch name is coherent and linked to the issue, or the documented setup-branch exception applies;
- commits are small, meaningful, and use Conventional Commit-style messages where practical;
- the branch is pushed without force;
- a draft pull request is created and linked to the issue;
- review checks architecture, correctness, naming, readability, edge cases, tests or verification, documentation, reproducibility, security, privacy, and maintainability as applicable;
- at least one review-driven revision is made or an explicit no-change rationale is recorded;
- technical debt is either absent or recorded without blocking justified completion;
- the accepted merge strategy is used;
- the issue is closed with evidence;
- the remote head branch is deleted automatically;
- the canonical local checkout returns to clean, up-to-date `main` with the merged local branch deleted;
- the durable Git and GitHub workflow standard is stored in the repository.

## Step 5.1 inventory result

```text
Path: /home/akcoo/projects/career-os
Filesystem: ext4
Owner: akcoo:akcoo
Origin: git@github.com:Harper2123/career-os.git
Git: 2.43.0
GitHub CLI: absent and not required
WSL code command: present, with a recurring interoperability failure observed
User: Ayush Kumar <akcoolkmr@gmail.com>
Default branch: main
core.autocrlf: input
fetch.prune: true
pull.ff: only
push.autoSetupRemote: true
```

WSL Git, GitHub issues and pull requests, VS Code Source Control, and the GitHub Pull Requests extension are sufficient. Do not install GitHub CLI merely to increase tool count.

## Step 5.2 durable standard

The accepted workflow standard is:

```text
standards/git-github-workflow.md
```

It defines issue quality, branch naming, first attempts, commits, pushes, draft pull requests, senior review, revisions, technical debt, merge strategy, closure evidence, cleanup, privacy boundaries, research reproducibility, and tooling policy.

Key merge decisions:

- routine single-issue project work: squash merge by default;
- Career OS `setup/step-<X>` branches: merge commit;
- bounded research issue: squash by default;
- research work whose commit sequence materially improves auditability or reproducibility: merge commit with the reason stated in the PR;
- rebase merge is not the default.

## Step 5.3 evidence

### Issue quality

Issue #25 contains:

- purpose;
- scope;
- acceptance criteria;
- verification;
- exclusions;
- the Decision 0002 setup-branch exception.

### First attempt

Ayush created and pushed:

```text
aa75e21fae8f4a756a9d281089dd67eaa6b2cda0
docs(git): document session-local SSH agent use
```

The commit changed only:

```text
standards/git-github-workflow.md
```

The branch was pushed without force and verified clean with zero ahead and behind counts.

### Command verification

The session-local commands were exercised successfully in WSL:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh-add -l
```

The agent started, the passphrase-protected ED25519 key loaded, and `ssh-add -l` listed the key. No passphrase or private-key material was recorded in the repository.

### Draft pull request

Draft PR #26 links issue #25 with `Closes #25` and records:

- summary and meaningful changes;
- verification performed;
- known draft limitations;
- risks and exclusions;
- technical-debt status pending review;
- privacy confirmation;
- the setup-branch exception.

The PR remains draft because issue #25 acceptance criteria are not yet satisfied.

## Known draft limitations for Step 5.4 review

Formal review has not started, but the draft PR records these visible first-attempt limitations:

- `ssh-add -1` was written instead of the lowercase-L command `ssh-add -l`;
- the prose says the passphrase is added rather than the private key being loaded into the agent;
- the final paragraph contains a spelling error;
- the text does not yet clearly separate retaining the key passphrase from deferring persistent agent startup.

These defects are intentionally preserved in the first-attempt commit so the review and revision trail can be practised without rewriting shared history.

## WSL interoperability observation

`code .` failed during Step 5.3 with the previously observed WSL-to-Windows executable interoperability error. This did not alter the repository and does not change the accepted Step 4 architecture. No persistent workaround is authorised in Step 5.3.

## Branch-history correction note

During Step 5.3 activation, an unintended temporary file named `tmp-do-not-use` was created through the GitHub connector and immediately deleted in the next commit. No temporary file remains in the branch tree.

The two corrective commits remain visible because the governing workflow forbids force-pushing or rewriting shared history merely to make the branch look cleaner. This is transparent workflow evidence for Step 5.4 review.

## Governing constraints

- Do not force-push, rewrite shared history, or bypass review.
- Do not create commits that mix unrelated concerns.
- Do not optimise for commit, issue, PR, or streak counts.
- Never commit raw WQU materials, graded work, confidential information, credentials, private datasets, private health information, or uncleared private paper drafts.
- Research and future paper work must favour reproducibility, traceable decisions, experiment evidence, and clear separation between exploratory notebooks and reusable tested code.
- Step 6 remains unauthorised.

## Research and PhD direction

Potential PhD preparation and publication-quality research are binding Career OS design requirements.

Step 5 supports later research through reproducible histories, issue-based questions and hypotheses, reviewable analysis, traceable limitations and debt, clear result evidence, and separation of public code from restricted materials.

The full research and paper-development system remains in scope for Step 9.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, coursework, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

Step 5.4 requires explicit approval. There is no Step 5.3 technical blocker.

## Next action

Synchronise the canonical local checkout to the latest `setup/step-5` remote commit, verify a clean zero-ahead/zero-behind state, and stop for the exact Step 5.4 gate.