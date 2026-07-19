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
- Practice issue: `#25 docs: document session-local SSH agent use`
- Draft pull request: `#26 docs: establish Git and GitHub workflow`
- `main` remains the last merged top-level checkpoint.
- Unrelated work must not be added to this branch.

## Current objective

Establish and practise one reliable Git and GitHub workflow:

```text
Issue → branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → issue closure
```

The workflow must support Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories without creating excessive process overhead.

## Current task

**Step 5.4 is active: review, revision, acceptance, debt decision, and merge.**

Formal review submission `4730284065` on draft PR #26 records four blocking findings in the SSH-agent subsection. Ayush must correct them in one new review-driven commit without rewriting the first-attempt commit.

Do not mark the pull request ready, merge it, close issue #25 manually, or begin post-merge cleanup until the revision is reviewed and accepted.

## Step 5 execution model

1. **Step 5.1: complete.** Inventory current Git/GitHub state and define the harmless practice issue.
2. **Step 5.2: complete.** Record the minimum workflow standard.
3. **Step 5.3: complete.** Create issue #25, implement and push the first attempt, and open linked draft PR #26.
4. **Step 5.4: active.** Resolve formal review findings, verify the revision, decide whether debt remains, mark the PR ready, and merge only after acceptance.
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
- bounded research issue: squash merge by default;
- research work whose commit sequence materially improves auditability or reproducibility: merge commit with the reason stated in the PR;
- rebase merge is not the default.

## Step 5.3 evidence

Issue #25 contains purpose, scope, acceptance criteria, verification, exclusions, and the Decision 0002 setup-branch exception.

Ayush created and pushed without force:

```text
aa75e21fae8f4a756a9d281089dd67eaa6b2cda0
docs(git): document session-local SSH agent use
```

The first-attempt commit changed only `standards/git-github-workflow.md`. The branch was verified clean with zero ahead and behind counts.

The session-local commands were exercised successfully in WSL:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh-add -l
```

The agent started, the passphrase-protected ED25519 key loaded, and `ssh-add -l` listed the key. No passphrase or private-key material was recorded in the repository.

Draft PR #26 links issue #25 with `Closes #25` and records verification, risks, privacy boundaries, technical-debt status, and the setup-branch exception.

## Step 5.4 formal review

### Accepted aspects

- issue #25 is coherent and small;
- the branch exception is explicit;
- the first attempt and push are traceable;
- no restricted or private material was committed;
- no authentication, key, shell-startup, credential-manager, or remote configuration changed;
- the broader Git and GitHub standard is proportionate and supports reproducible research.

### Blocking findings

1. `ssh-add -1` uses the digit `1`; the verification command must be `ssh-add -l` with a lowercase `L`.
2. `ssh-add ~/.ssh/id_ed25519` loads the private key into the agent after passphrase entry; the passphrase itself is not added.
3. The security guidance must explicitly preserve the private-key passphrase and state that removing it is not the recommended convenience fix.
4. Persistent agent startup must be described as a separate, deliberately deferred decision that requires repeated friction and a separately reviewed change.
5. Correct `presistent` to `persistent` and tighten the prose so each command has an accurate purpose.

### Required revision verification

- `git diff --check` returns no output;
- `git diff --cached --check` returns no output;
- the command block is exactly:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh-add -l
```

- no unrelated workflow policy changes;
- no key material, passphrase, credential, or private configuration output committed;
- one new review-driven commit is added without force-push rewriting.

## Known observations

`code .` failed during Step 5.3 with the previously observed WSL-to-Windows executable interoperability error. This did not alter the repository and does not change the accepted Step 4 architecture. No persistent workaround is authorised in Step 5.

During Step 5.3 activation, an unintended temporary file named `tmp-do-not-use` was created through the GitHub connector and immediately deleted in the next commit. No temporary file remains in the branch tree. The corrective commits remain visible because shared history is not rewritten merely to make it look cleaner.

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

The formal review findings must be corrected and pushed in one new review-driven commit before PR #26 can be accepted.

## Next action

Synchronise the canonical local checkout to the latest `setup/step-5` remote commit, revise only the SSH-agent subsection, verify the diff, commit with a review-driven Conventional Commit-style message, push without force, and stop for re-review.