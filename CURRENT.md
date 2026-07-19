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
- One pull request will be created only after the full Step 5 completion condition is met.
- Unrelated work must not be added to this branch.

## Current objective

Establish and practise one reliable Git and GitHub workflow:

```text
Issue → branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → issue closure
```

The workflow must support Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories without creating excessive process overhead.

## Current task

**Step 5.3 is active: execute the issue-to-draft-PR path.**

Practice issue:

```text
#25 docs: document session-local SSH agent use
```

The issue arose from observed workflow friction rather than an invented exercise. It adds a concise SSH-agent subsection to `standards/git-github-workflow.md` without changing authentication architecture or shell startup configuration.

The existing `setup/step-5` branch is used under Decision 0002. Do not create a nested issue branch.

## Step 5 execution model

1. **Step 5.1: complete.** Inventory current Git/GitHub state and define the harmless practice issue.
2. **Step 5.2: complete.** Record the minimum workflow standard.
3. **Step 5.3: active.** Implement issue #25, create one meaningful local commit, push without force, and open a linked draft pull request.
4. **Step 5.4: not authorised.** Perform senior review, make at least one justified revision or record an evidence-based no-change rationale, decide whether debt exists, and merge only after acceptance.
5. **Step 5.5: not authorised.** Verify issue closure, automatic remote branch deletion, clean local `main`, and durable handoff state.

Later units remain gated. Listing them does not authorise them.

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
WSL code command: present
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

## Practice issue #25

### Purpose

Reduce repeated SSH-key passphrase prompts during one working terminal session without weakening the existing passphrase-protected key or adding premature persistent automation.

### Accepted scope

Add a subsection under the workflow standard's tooling policy that documents:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh-add -l
```

The text must distinguish session-local caching from persistent startup, explain that prompts may return after WSL or the agent restarts, and preserve the recommendation to keep the private-key passphrase.

### Exclusions

- no GitHub CLI installation;
- no key or passphrase change;
- no `.bashrc`, `.profile`, WSL startup, Windows service, or credential-manager change;
- no persistent SSH-agent implementation;
- no authentication or remote change.

### Verification

- review the Markdown diff;
- confirm the three commands are syntactically correct;
- confirm no key material, passphrase, credential, or private configuration output is included;
- confirm no unrelated policy changes.

## Branch-history correction note

During Step 5.3 activation, an unintended temporary file named `tmp-do-not-use` was created through the GitHub connector and immediately deleted in the next commit. No temporary file remains in the branch tree.

The two corrective commits remain visible because the governing workflow forbids force-pushing or rewriting shared history merely to make the branch look cleaner. This will be treated as transparent workflow evidence during review, not hidden.

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

The canonical local checkout must first fast-forward to the latest remote `setup/step-5` state. Then Ayush makes the issue #25 documentation change as the first attempt, verifies it, commits it once, and pushes without force.

## Next action

Synchronise the local branch, implement issue #25 in VS Code, inspect the diff, commit with:

```text
docs(git): document session-local SSH agent use
```

Push normally and stop before creating the draft pull request manually. ChatGPT will verify the pushed branch and create the linked draft pull request within Step 5.3.