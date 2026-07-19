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

**Step 6.3a is complete. Step 6.3b has not been authorised.**

The local Windows vault and accepted minimum structure have passed verification. Do not create the private GitHub repository, initialise Git in the vault, push a backup, or write the weak-stationarity concept note before the exact instruction:

```text
Proceed to Step 6.3b
```

## Step 6 execution model

1. **Activation: complete.** Create `setup/step-6` and record the authorised objective.
2. **Step 6.1: complete.** Inventory installation, vaults, devices, sync, backup, workflows, privacy constraints, and test concept.
3. **Step 6.2: complete.** Accept the minimum vault, storage, folders, navigation, naming, links, metadata, attachments, plugins, Android, privacy, and backup architecture.
4. **Step 6.3: active.** Create the accepted vault, minimum structure, configuration, and private backup repository.
   - **Step 6.3a: complete.** Local Windows vault, structure, configuration, template, and `.gitignore` verified.
   - **Step 6.3b: not authorised.** Create the private backup repository, initialise Git through WSL, and perform the initial private backup push.
5. **Step 6.4: not authorised.** Capture, connect, and retrieve weak stationarity using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review, record the public-safe standard, open and merge the Step 6 pull request, and clean up.

## Accepted inventory

- Obsidian `1.12.7` is installed on Windows and launches correctly.
- No migration burden, prior sync service, or prior backup exists.
- Windows laptop access is required.
- Android access is optional and deferred in v1.
- The work computer must not access the vault.
- Paid Obsidian Sync is not acceptable.
- The accepted completion-test concept is **Weak stationarity** from Financial Econometrics.
- Related concepts: autocovariance and autocorrelation; unit roots and non-stationarity.

## Accepted Step 6.2 architecture

### Vault and storage

- One private vault.
- Vault name: `career-knowledge`.
- Windows location: `%USERPROFILE%\Documents\Obsidian\career-knowledge`.
- The vault remains outside the public `career-os` repository.
- The Windows vault is authoritative in v1.

### Minimum folders

```text
00 Home
10 Concepts
20 Learning
30 Sources
40 Research
90 Attachments
99 Templates
```

Purpose:

- `00 Home`: home note and maps of content;
- `10 Concepts`: reusable concept notes;
- `20 Learning`: course-specific maps and learning notes;
- `30 Sources`: book and paper notes written in Ayush's own words;
- `40 Research`: non-confidential research questions, comparisons, and reproduction notes;
- `90 Attachments`: small owned or redistributable images and diagrams only;
- `99 Templates`: minimal built-in templates.

No inbox, daily-notes workflow, archive hierarchy, or deep subject taxonomy is included in v1.

### Navigation

- Root note: `00 Home/Home.md`.
- Initial maps: `MOC - Financial Econometrics` and `MOC - Time series`.
- Primary completion-test path:

```text
Home → MOC - Financial Econometrics → Weak stationarity
```

- Secondary retrieval: Obsidian search for `weak stationarity` or a genuine alias.

### Note names and properties

- Concept: canonical concept name, such as `Weak stationarity`.
- Map: `MOC - <area>`.
- Source: `Author YYYY - Short title` when citation details exist.
- Research: `Research - <question or comparison>`.
- No date prefixes, IDs, status prefixes, scoring, review dates, or large tag vocabulary in v1.
- Minimal property:

```yaml
type: concept | map | source | learning | research
```

### Links and built-in features

- Use Obsidian wikilinks.
- Enable automatic internal-link updates after renaming.
- Prefer direct links and maps over tags.
- Use built-in Search, Backlinks, Outgoing Links, Templates, Properties, and File Recovery as needed.
- Community plugins remain disabled.
- Graph view and Canvas are optional visual aids, not workflow requirements.

### Files and attachments

- Default concept-note location: `10 Concepts`.
- Default attachment location: `90 Attachments`.
- Raw course PDFs and large source files remain outside the vault.
- Use citations or references instead of copying restricted source material into the vault.
- Deleted files go to the Windows system trash.
- File Recovery may remain available, but it is not a backup.

## Step 6.3a verified result

### Vault tree

The local Windows vault contains exactly the accepted structural files outside `.obsidian`:

```text
.gitignore
00 Home\Home.md
00 Home\MOC - Financial Econometrics.md
00 Home\MOC - Time series.md
99 Templates\Concept.md
```

The seven accepted folders are present:

```text
00 Home
10 Concepts
20 Learning
30 Sources
40 Research
90 Attachments
99 Templates
```

The initial automatically created `Welcome.md` was deleted through Obsidian and no longer exists.

### Blocked concept notes

The following notes do not exist and remain blocked until Step 6.4:

```text
10 Concepts\Weak stationarity.md
10 Concepts\Autocovariance and autocorrelation.md
10 Concepts\Unit roots and non-stationarity.md
```

### Settings verification

Verified values:

- default new-note behavior: folder specified below;
- new-note folder: `10 Concepts`;
- link format: shortest path when possible;
- wikilinks: enabled;
- automatic internal-link updates: enabled;
- attachment behavior: folder specified below;
- attachment folder: `90 Attachments`;
- deleted files: Windows system trash;
- template folder: `99 Templates`;
- Search: enabled;
- Backlinks: enabled;
- Outgoing Links: enabled;
- Templates: enabled;
- Properties view: enabled;
- File Recovery: enabled;
- restricted mode: on;
- installed community plugins: none.

### `.gitignore`

The root `.gitignore` contains:

```text
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.obsidian/cache/
.trash/
.DS_Store
Thumbs.db
```

### Windows path-case verification note

PowerShell `Test-Path` returned `True` for both `MOC - Time series.md` and `MOC - Time Series.md` because the Windows filesystem resolves those path strings case-insensitively. That command cannot distinguish filename capitalization on this filesystem.

The actual directory listing and Obsidian File explorer both show the accepted filename exactly as:

```text
MOC - Time series.md
```

No duplicate differently capitalised file exists.

## Accepted private backup architecture

Ayush explicitly accepted storing permitted private-vault contents in a separate private GitHub repository.

- Repository name: `career-knowledge-private`.
- It must be private and separate from `career-os`.
- The local Windows vault remains the working copy.
- WSL Git provides deliberate versioned off-device backup.
- Commit and push after a meaningful note session or before risky structural changes.
- No collaborators are added.
- GitHub account two-factor authentication must remain enabled.
- Volatile Obsidian workspace files and trash must be excluded from version control.
- The private repository is backup, not automatic multi-device sync.

## Privacy classification

### Public-safe when deliberately prepared

- Ayush's own concept explanations and derivations;
- citations to public sources;
- summaries written in Ayush's own words;
- public-safe templates and operating guidance.

Public-safe does not mean automatically public. Publication remains deliberate.

### Private personal vault and backup repository

- personal study notes;
- completed-course concept notes;
- book and paper-reading notes;
- non-confidential research ideas;
- personal learning reflections.

### Outside the public repository, general vault, and private backup repository

- raw WQU materials;
- active graded questions or submissions;
- employer or client information;
- credentials, recovery codes, secrets, and private keys;
- health records;
- private paper drafts and reviewer correspondence unless a separately reviewed private research location is approved.

## Accepted constraints

- Windows-first and offline-first.
- Free backup only.
- Android must not complicate v1.
- Minimal maintenance.
- No community plugins initially.
- No LLM integration.
- Prefer folders, links, maps, and search over elaborate tags or metadata.
- Do not optimise for note, folder, link, map, property, plugin, vault, commit, or streak counts.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This does not block Obsidian setup and must not be addressed on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority.
- No guilt debt applies.
- Prefer one coherent outcome per session.
- Never commit raw WQU materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Step 7 remains unauthorised.

## Immediate blocker

Step 6.3b requires explicit approval. There is no Step 6.3a blocker.

## Next action

Synchronise the canonical local checkout to the latest `setup/step-6` remote commit, verify a clean zero-ahead and zero-behind state, and stop for the exact instruction:

```text
Proceed to Step 6.3b
```
