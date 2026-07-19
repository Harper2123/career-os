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

Establish and practise one reliable Git and GitHub workflow covering:

```text
Issue → branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → issue closure
```

The workflow must support Career OS, flagship engineering projects, reproducible research, and future paper-related code or experiment repositories without creating excessive process overhead.

## Current task

**Step 5.2 is complete. Step 5.3 has not been authorised.**

The minimum Git and GitHub workflow standard now exists at:

```text
standards/git-github-workflow.md
```

The next authorised unit will create one harmless practice issue and execute the issue-to-draft-PR path through the already-approved `setup/step-5` branch.

Do not create the issue, edit files, commit, push, or create a pull request before the exact instruction:

```text
Proceed to Step 5.3
```

## Step 5 execution model

1. **Step 5.1: complete.** Inventory current Git/GitHub state and define the harmless practice issue.
2. **Step 5.2: complete.** Record the minimum workflow standard.
3. **Step 5.3: not authorised.** Create the practice issue and execute the issue-to-draft-PR path on `setup/step-5`.
4. **Step 5.4: not authorised.** Perform senior review, make at least one justified revision or record an evidence-based no-change rationale, decide whether debt exists, and merge only after acceptance.
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

### Canonical repository

```text
Path: /home/akcoo/projects/career-os
Filesystem: ext4
Owner: akcoo:akcoo
Origin: git@github.com:Harper2123/career-os.git
Local branch after synchronisation: setup/step-5
Local upstream: origin/setup/step-5
Worktree: clean
Ahead of upstream: 0
Behind upstream: 0
Fetch refspec: +refs/heads/*:refs/remotes/origin/*
```

### Git and tool state

```text
Git: 2.43.0
GitHub CLI: absent
WSL code command: present through the Windows VS Code installation
User name: Ayush Kumar
User email: akcoolkmr@gmail.com
Default branch: main
core.autocrlf: input
fetch.prune: true
pull.ff: only
push.autoSetupRemote: true
```

GitHub CLI is not required for Step 5. WSL Git, GitHub issues and pull requests, VS Code Source Control, and the GitHub Pull Requests extension are sufficient.

The SSH private key remains passphrase-protected. A session-local `ssh-agent` may cache the unlocked key for a terminal session. Do not remove the passphrase merely for convenience. Persistent agent startup should be added only after repeated friction justifies a separate documented change.

### Workflow-document state before Step 5.2

The repository had no:

- `.github` issue or pull-request templates;
- `CONTRIBUTING.md`;
- `standards/git-github-workflow.md`.

Step 5.2 resolves the durable-standard gap. Templates and `CONTRIBUTING.md` remain deliberately absent in v1 unless repeated workflow friction demonstrates a need.

## Step 5.2 accepted workflow decisions

### Issue quality

An actionable issue states:

1. purpose;
2. scope;
3. acceptance criteria;
4. verification;
5. exclusions.

Research issues additionally record the question or hypothesis, provenance, baseline, metrics, reproducibility assumptions, evidence, and limitations where applicable.

### Branch naming

Normal issue branches use:

```text
<type>/<issue-number>-<short-slug>
```

Career OS top-level setup work remains the documented exception:

```text
setup/step-<X>
```

### Commits

Use small, meaningful Conventional Commit-style messages where practical:

```text
<type>(optional-scope): imperative summary
```

`research` is accepted as a project-specific type for experiment design, reproduction, comparison, and research documentation.

### Draft pull requests

Create a draft pull request after a coherent initial slice exists and has been pushed. The body records summary, linked issue, changes, verification, risks and limitations, technical debt, and privacy checks where relevant.

### Review and revisions

Review applies senior engineering and research standards according to the change. Blocking findings must be revised, rebutted with evidence, or resolved through an approved scope change. Do not manufacture revisions merely to demonstrate activity.

### Technical debt

Debt that threatens correctness, security, privacy, reproducibility, or research validity is normally blocking. Legitimate non-blocking debt is recorded as a separate issue with impact, deferral rationale, revisit trigger, and originating PR.

### Merge strategy

- routine single-issue project work: squash merge by default;
- Career OS `setup/step-<X>` branches: merge commit;
- bounded research issue: squash by default;
- research work whose commit sequence materially improves auditability or reproducibility: merge commit with the reason stated in the PR;
- rebase merge is not the default.

### Closure and cleanup

Prefer `Closes #<number>` in the accepted pull request. After merge, verify PR and issue closure, remote branch deletion, clean updated `main`, local branch deletion, and zero ahead/behind counts.

## Harmless practice issue design

Step 5.3 will create one documentation-only issue with the provisional outcome:

```text
Add a compact workflow quick reference to the Git and GitHub standard
```

The issue will require:

- a concise checklist covering issue selection through post-merge cleanup;
- the normal issue-branch convention and the Career OS setup-branch exception;
- verification that the Markdown change is readable and contains no unrelated content;
- no new tooling, templates, automation, or environment changes.

Because Decision 0002 requires one branch per top-level setup step, the practice issue will use the existing `setup/step-5` branch rather than creating a nested practice branch. The issue and final Step 5 pull request must document this exception clearly.

## Governing constraints

- Do not force-push, rewrite shared history, or bypass review merely to make the practice cycle look clean.
- Do not create commits that mix unrelated concerns.
- Do not treat commit count, issue count, PR count, or contribution streaks as progress measures.
- Preserve private course materials, graded work, confidential information, credentials, private datasets, and private health information outside the public repository.
- Research and future paper work must favour reproducibility, traceable decisions, experiment evidence, and clear separation between exploratory notebooks and reusable tested code.
- Step 6 remains unauthorised.

## Research and PhD direction

Potential PhD preparation and publication-quality research are binding Career OS design requirements.

Step 5 does not create the paper-development workflow, but its standard supports later research through:

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

Step 5.3 requires explicit approval. There is no technical Step 5.2 blocker.

## Next action

Synchronise the canonical local checkout to the latest `setup/step-5` remote commit, verify a clean zero-ahead/zero-behind state, and stop for the explicit Step 5.3 gate.
