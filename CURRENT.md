# Current State

_Last updated: 2026-07-19_

## Operating mode

**Career OS setup mode**

Steps 1 through 5 are complete.

No setup step is active. Step 6 has not been authorised.

## Current objective

Preserve the completed Git and GitHub workflow checkpoint and wait for the exact instruction:

```text
Proceed to Step 6
```

Do not begin the Obsidian knowledge-system setup before that gate.

## Repository state

- Repository: `Harper2123/career-os`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- Active local branch: `main`
- Step 5 pull request: `#26 docs: establish Git and GitHub workflow`
- Step 5 merge commit: `46a67c99222a87ce2632fbf019ad38cae6c6aa69`
- Step 5 practice issue: `#25 docs: document session-local SSH agent use`
- Local `setup/step-5` branch: deleted after merge
- Remote `setup/step-5` branch and tracking reference: deleted and pruned

At Step 5 closure, the canonical checkout was verified clean on `main`, equal to `origin/main`, and zero commits ahead and behind.

## Step 5 completion result

### Durable standard

The approved workflow is recorded in:

```text
standards/git-github-workflow.md
```

It defines:

- issue purpose, scope, acceptance criteria, verification, and exclusions;
- normal issue-branch naming and the Career OS setup-branch exception;
- first-attempt expectations;
- Conventional Commit-style messages;
- normal pushes without force;
- draft pull-request content and readiness criteria;
- senior review dimensions;
- review-driven revisions and no-change rationale;
- technical-debt recording;
- merge-strategy selection;
- automatic issue closure and post-merge cleanup;
- public and private repository boundaries;
- research reproducibility expectations;
- lightweight tooling policy.

### Proved workflow

Step 5 practised the complete path:

```text
Issue → branch → first attempt → commit → push → draft PR → formal review → revision → final author review → merge → issue closure → branch cleanup
```

Evidence:

- issue #25 contained purpose, scope, acceptance criteria, verification, exclusions, and the Decision 0002 branch exception;
- Ayush created the first-attempt commit `aa75e21fae8f4a756a9d281089dd67eaa6b2cda0`;
- the branch was pushed without force;
- draft PR #26 linked issue #25 through `Closes #25`;
- formal review recorded blocking documentation findings;
- Ayush resolved them in `e2f16811ff82d1a16d658d73e0cec4792d963afb` without rewriting shared history;
- the final branch diff was reviewed and explicitly accepted;
- PR #26 was marked ready and merged using a merge commit;
- issue #25 closed automatically as completed;
- GitHub deleted the remote setup branch automatically;
- the canonical checkout returned to clean, synchronised `main`;
- the merged local setup branch was deleted normally with `git branch -d`.

### Review outcome

The review corrected:

- `ssh-add -1` to `ssh-add -l`;
- the incorrect claim that the passphrase is added to the agent;
- ambiguous passphrase-preservation guidance;
- unclear separation between session-local caching and persistent startup;
- spelling and wording defects.

No technical debt remains from issue #25.

### Merge decisions

- routine single-issue project work: squash merge by default;
- Career OS `setup/step-<X>` branches: merge commit;
- bounded research issue: squash merge by default;
- research work whose commit sequence materially improves auditability or reproducibility: merge commit with the reason stated in the pull request;
- rebase merge is not the default.

## Tooling and authentication state

- WSL Git remains the primary Git runtime.
- GitHub CLI is absent and not required.
- Git identity and global defaults remain configured.
- The GitHub SSH key remains passphrase-protected.
- A session-local SSH agent may be started with:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
ssh-add -l
```

- Persistent automatic agent startup remains deferred until repeated friction justifies a separately reviewed change.
- No authentication architecture, shell startup file, key, passphrase, credential manager, repository remote, or Windows service was changed in Step 5.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This observation predates Step 5, made no repository change, and does not invalidate the approved Step 4 environment architecture. No persistent workaround has been authorised.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority over optional progress.
- No guilt debt applies.
- Plan detailed work only for the next two to three days.
- Prefer one coherent outcome per session.
- Do not optimise for issue, branch, pull-request, commit, streak, or hour counts.
- Never commit raw WQU course materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Research work must favour reproducibility, traceable decisions, experiment evidence, and separation of exploratory notebooks from reusable tested modules.

## Research and PhD direction

Potential PhD preparation and publication-quality research remain binding Career OS design requirements.

The Step 5 workflow now supports issue-based research questions or hypotheses, reviewable experiments, traceable revisions, explicit limitations and debt, and public/private separation. The full research and paper-development system remains in scope for Step 9.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, coursework, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

Step 6 requires explicit approval. There is no Step 5 technical blocker.

## Next action

Synchronise the canonical local `main` branch to this final Step 5 state commit, verify a clean zero-ahead/zero-behind checkout, and stop for the exact Step 6 gate.
