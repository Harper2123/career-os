# Current State

_Last updated: 2026-07-19_

## Operating mode

**Career OS setup mode**

Steps 1 through 5 are complete. Step 6 is active.

## Active setup branch

- Repository: `Harper2123/career-os`
- Working branch: `setup/step-6`
- Base branch: `main`
- Base checkpoint: `357f04d2616e853af9ee362e0666b63e2e0957f7`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- `main` remains the last merged top-level checkpoint.
- One pull request will cover the complete top-level Step 6 under Decision 0002.
- Unrelated work must not be added to this branch.

## Current objective

Set up a lightweight, private Obsidian knowledge system for concepts, finance, AI engineering, mathematics, MScFE learning, books, papers, research, and maps of content.

Do not add LLM integration in Career OS v1.

## Completion condition

Step 6 is complete only when one completed MScFE concept is captured, connected, retrievable, reviewed for clarity and privacy, and supported by a lightweight public-safe vault standard in the Career OS repository.

## Current task

**Step 6.3 is complete. Step 6.4 has not been authorised.**

The local vault and private versioned backup are verified. Do not create or write the weak-stationarity note before the exact instruction:

```text
Proceed to Step 6.4
```

## Step 6 execution model

1. **Activation: complete.** Create `setup/step-6` and record the authorised objective.
2. **Step 6.1: complete.** Inventory installation, vaults, devices, sync, backup, workflows, privacy constraints, and test concept.
3. **Step 6.2: complete.** Accept the minimum vault, storage, folders, navigation, naming, links, metadata, attachments, plugins, Android, privacy, and backup architecture.
4. **Step 6.3: complete.**
   - **Step 6.3a: complete.** Create and verify the local Windows vault, structure, settings, template, and `.gitignore`.
   - **Step 6.3b: complete.** Create and verify the private GitHub backup repository, local Git repository, initial commit, and initial push.
5. **Step 6.4: not authorised.** Capture, connect, and retrieve weak stationarity using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review, record the public-safe standard, open and merge the Step 6 pull request, and clean up.

## Accepted architecture

### Vault

- One private vault named `career-knowledge`.
- Windows location: `%USERPROFILE%\Documents\Obsidian\career-knowledge`.
- WSL path: `/mnt/c/Users/akcoo/Documents/Obsidian/career-knowledge`.
- The vault remains outside the public `career-os` repository.
- The Windows vault is authoritative in v1.
- Android access is deferred.
- Paid Obsidian Sync is not used.

### Folders

```text
00 Home
10 Concepts
20 Learning
30 Sources
40 Research
90 Attachments
99 Templates
```

No inbox, daily-note workflow, archive hierarchy, or deep subject taxonomy is part of v1.

### Navigation

Primary completion-test path:

```text
Home → MOC - Financial Econometrics → Weak stationarity
```

Secondary retrieval will use Obsidian search for `weak stationarity` or a genuine alias.

### Note rules

- Concept: canonical concept name.
- Map: `MOC - <area>`.
- Source: `Author YYYY - Short title` when citation details exist.
- Research: `Research - <question or comparison>`.
- Minimal property:

```yaml
type: concept | map | source | learning | research
```

- Use wikilinks and automatic internal-link updates.
- Prefer direct links and maps over tags.
- No status system, scoring, review dates, large tag vocabulary, community plugins, or LLM integration in v1.

## Step 6.3a verified result

The local Windows vault contains the accepted structural files outside `.obsidian`:

```text
.gitignore
00 Home\Home.md
00 Home\MOC - Financial Econometrics.md
00 Home\MOC - Time series.md
99 Templates\Concept.md
```

The seven accepted folders are present. `Welcome.md` was deleted through Obsidian.

The following concept notes remain absent and blocked until Step 6.4:

```text
10 Concepts\Weak stationarity.md
10 Concepts\Autocovariance and autocorrelation.md
10 Concepts\Unit roots and non-stationarity.md
```

Verified Obsidian settings:

- default new-note folder: `10 Concepts`;
- shortest-path links and wikilinks enabled;
- automatic internal-link updates enabled;
- attachment folder: `90 Attachments`;
- deleted files go to Windows system trash;
- template folder: `99 Templates`;
- Search, Backlinks, Outgoing Links, Templates, Properties view, and File Recovery enabled;
- restricted mode on;
- no community plugins installed.

The root `.gitignore` excludes:

```text
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.obsidian/cache/
.trash/
.DS_Store
Thumbs.db
```

## Step 6.3b verified result

### Private repository

- Repository: `Harper2123/career-knowledge-private`.
- Visibility: private.
- Default branch: `main`.
- Collaborators added: none.
- GitHub account two-factor authentication: enabled.
- Purpose: versioned off-device backup, not automatic multi-device sync.

### Local Git state

- Local repository path: `/mnt/c/Users/akcoo/Documents/Obsidian/career-knowledge`.
- Branch: `main`.
- Local `core.filemode`: `false` for the Windows-mounted working tree.
- Remote: `git@github.com:Harper2123/career-knowledge-private.git`.
- Initial commit:

```text
159d10fd26d001f09ca2e1b5f34ca25fb0ecbb0c
chore: initialize private knowledge vault
```

- Initial push to `origin/main`: successful without force.
- Local and remote `main`: zero commits ahead and behind.
- Worktree after push: clean.
- Remote head matched the initial commit.

### Initial backup contents

The initial commit contains 15 paths:

- root `.gitignore`;
- safe Obsidian application, appearance, core-plugin, graph, and template configuration;
- three structural navigation notes;
- one concept template without concept content;
- five `.gitkeep` placeholders preserving empty folders.

The following remained excluded or absent:

- `.obsidian/workspace.json`;
- `.obsidian/workspace-mobile.json`;
- `.obsidian/cache/`;
- `.trash/`;
- weak-stationarity content;
- raw WQU files;
- graded work;
- employer or client material;
- credentials, keys, secrets, and recovery data;
- private datasets;
- health records;
- private paper drafts and reviewer correspondence.

Filename and text-pattern privacy scans returned no findings. `git diff --cached --check` returned no errors, and no ignored path was tracked.

### Empty-folder preservation

Git does not track empty folders. The initial backup therefore contains:

```text
10 Concepts/.gitkeep
20 Learning/.gitkeep
30 Sources/.gitkeep
40 Research/.gitkeep
90 Attachments/.gitkeep
```

These placeholders preserve the accepted structure after cloning.

### Non-blocking observations

- Git warned that the PowerShell-created `.gitignore` uses CRLF and would be normalised to LF when Git next writes it. This is normal line-ending conversion and did not block the commit or push.
- Obsidian's built-in Sync core plugin remains enabled in configuration but is not signed in or configured. Paid Obsidian Sync remains outside the accepted v1 workflow.
- Built-in Daily Notes may remain enabled, but no daily-note workflow is authorised or used in v1.

## Privacy classification

### Permitted in the private vault and backup

- personal study notes;
- completed-course concept notes;
- book and paper-reading notes written in Ayush's own words;
- non-confidential research ideas;
- personal learning reflections.

### Outside the public repository, general vault, and private backup

- raw WQU course materials;
- active graded questions or submissions;
- employer or client information;
- credentials, recovery codes, secrets, API keys, and private keys;
- private datasets;
- health records;
- private paper drafts and reviewer correspondence unless a separately reviewed private research location is approved.

## Backup operating rule

Commit and push after a meaningful note session or before risky structural changes. Do not optimise for commit frequency. A clean local working tree does not prove off-device backup until the commit is pushed successfully.

The private repository is not sync. Android access remains deferred.

## Step 6.4 completion-test concept

The accepted test concept is **Weak stationarity** from completed Financial Econometrics work.

Related concepts:

- autocovariance and autocorrelation;
- unit roots and non-stationarity.

Step 6.4 must use Ayush's first attempt. The note should be narrow, written in Ayush's own words, mathematically precise, connected through the existing maps, retrievable through navigation and search, and free from raw course text or active graded material.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This does not block Obsidian work and must not be addressed on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority.
- No guilt debt applies.
- Prefer one coherent outcome per session.
- Use questions, hints, checkpoints, and Ayush's first attempt for conceptual learning.
- Never commit raw WQU materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Step 7 remains unauthorised.

## Immediate blocker

Step 6.4 requires explicit approval. There is no Step 6.3 implementation blocker.

## Next action

Synchronise the canonical Career OS checkout to the latest `setup/step-6` remote commit, verify a clean zero-ahead and zero-behind state, and stop for the exact instruction:

```text
Proceed to Step 6.4
```
