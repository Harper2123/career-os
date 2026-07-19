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

**Step 6.3b is active.** Create and verify the accepted private GitHub backup for the already-verified local Windows vault.

Do not write the weak-stationarity concept note or begin Step 6.4.

## Step 6 execution model

1. **Activation: complete.** Create `setup/step-6` and record the authorised objective.
2. **Step 6.1: complete.** Inventory installation, vaults, devices, sync, backup, workflows, privacy constraints, and test concept.
3. **Step 6.2: complete.** Accept the minimum vault, storage, folders, navigation, naming, links, metadata, attachments, plugins, Android, privacy, and backup architecture.
4. **Step 6.3: active.** Create the accepted vault, minimum structure, configuration, and private backup repository.
   - **Step 6.3a: complete.** Local Windows vault, structure, configuration, template, and `.gitignore` verified.
   - **Step 6.3b: active.** Create the private repository, initialise Git through WSL, preserve empty structural folders, and perform the initial private backup push.
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

### Navigation

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

## Step 6.3b authorised scope

Create only:

1. a new GitHub repository owned by `Harper2123` named `career-knowledge-private`;
2. private visibility;
3. no README, licence, or GitHub-generated `.gitignore` at creation;
4. no collaborators;
5. a local Git repository inside the accepted Windows vault, operated through WSL Git;
6. `.gitkeep` placeholders in currently empty accepted folders so a clone restores the approved structure;
7. local `core.filemode=false` for the Windows-mounted working tree;
8. one inspected initial commit;
9. SSH remote `git@github.com:Harper2123/career-knowledge-private.git`;
10. one normal initial push to `main` without force;
11. verification that ignored workspace and trash paths are not tracked;
12. verification that the GitHub repository is private and contains no collaborators.

The private repository is versioned off-device backup, not automatic sync.

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

GitHub account two-factor authentication must remain enabled. No collaborator is authorised.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This does not block Obsidian setup and must not be addressed on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority.
- No guilt debt applies.
- Prefer one coherent outcome per session.
- Never commit raw WQU materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Step 7 remains unauthorised.

## Immediate blocker

Step 6.3b requires creation and verification of the private repository and initial backup. There is no Step 6.3a blocker.

## Next action

Synchronise the Career OS branch to this Step 6.3b activation commit, create and verify only the authorised private backup, return the requested evidence, and stop before Step 6.4.
