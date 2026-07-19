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

**Step 6.2 is active.** Design the minimum architecture before creating the vault.

The proposed design is awaiting Ayush's acceptance. Do not create a vault, private backup repository, folders, templates, notes, sync configuration, or plugins until the design is accepted and Step 6.3 is explicitly authorised.

## Step 6 execution model

1. **Activation: complete.** Create `setup/step-6` and record the authorised objective.
2. **Step 6.1: complete.** Inventory installation, vaults, devices, sync, backup, workflows, privacy constraints, and test concept.
3. **Step 6.2: active.** Decide storage, one-vault architecture, folders, navigation, note types, naming, links, metadata, attachments, deletion, backup, Android scope, and public/private flow.
4. **Step 6.3: not authorised.** Create the accepted vault and minimum structure.
5. **Step 6.4: not authorised.** Capture, connect, and retrieve weak stationarity using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review, record the public-safe standard, open and merge the Step 6 pull request, and clean up.

## Step 6.1 accepted inventory

- Obsidian `1.12.7` is installed on Windows and launches correctly.
- No existing registered vault, Markdown-note folder, migration burden, sync service, or backup exists.
- Windows laptop access is required.
- Android access is optional.
- The work computer must not access the vault.
- Paid Obsidian Sync is not acceptable.
- No established note-taking workflow exists.
- The accepted completion-test concept is **Weak stationarity** from Financial Econometrics.
- Related concepts: autocovariance and autocorrelation; unit roots and non-stationarity.

## Accepted constraints

- Windows-first and offline-first.
- Free backup only.
- Android must not complicate v1.
- Minimal maintenance.
- One general personal vault unless a concrete reason justifies separation.
- No community plugins initially.
- No LLM integration.
- Prefer folders, links, maps, and search over elaborate tags or metadata.
- Do not optimise for note, folder, link, map, property, plugin, or vault counts.

## Proposed Step 6.2 architecture

### Vault and storage

- One private vault.
- Proposed vault name: `career-knowledge`.
- Proposed Windows location: `%USERPROFILE%\Documents\Obsidian\career-knowledge`.
- The vault remains outside the public `career-os` repository.
- Raw WQU files, active graded work, confidential material, credentials, health records, and uncleared private paper drafts remain outside the vault.

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

Design intent:

- `00 Home`: home note and maps of content;
- `10 Concepts`: reusable concept notes;
- `20 Learning`: course-specific maps and learning notes;
- `30 Sources`: book and paper notes written in Ayush's own words;
- `40 Research`: non-confidential research questions, comparisons, and reproduction notes;
- `90 Attachments`: small owned or redistributable images and diagrams only;
- `99 Templates`: minimal built-in templates.

No inbox, daily-notes workflow, archive hierarchy, or deep domain taxonomy is proposed in v1.

### Navigation

- Root navigation note: `00 Home/Home.md`.
- Initial maps: `MOC - Financial Econometrics` and `MOC - Time series`.
- Primary retrieval path for the completion test:

```text
Home → MOC - Financial Econometrics → Weak stationarity
```

- Secondary retrieval: Obsidian search for `weak stationarity` or an accepted alias.

### Note types and names

- Concept: canonical concept name, for example `Weak stationarity`.
- Map: `MOC - <area>`.
- Source: `Author YYYY - Short title` when citation information exists.
- Research: `Research - <question or comparison>`.

Avoid date prefixes and identifiers unless a later workflow demonstrates a need.

### Minimal properties

Use properties only when they materially improve retrieval:

```yaml
type: concept | map | source | learning | research
```

Optional aliases are allowed for genuine alternative names. No status system, scoring, review date, or large tag vocabulary is proposed in v1.

### Links

- Use Obsidian wikilinks.
- Enable automatic internal-link updates after renaming.
- Prefer direct links and maps over tags.
- Unresolved links may represent planned related concepts, but Step 6.4 must clearly distinguish completed notes from stubs.

### Files and attachments

- Default concept-note location: `10 Concepts`.
- Default attachment location: `90 Attachments`.
- Raw course PDFs and large source files remain outside the vault.
- Use external citations or references rather than copying restricted source material into the vault.
- Deleted files should go to the Windows system trash rather than permanent deletion.
- Keep the built-in File Recovery core plugin available, but do not treat it as a backup.

### Plugins

- Community plugins remain disabled in v1.
- Use built-in Search, Backlinks, Outgoing Links, Templates, Properties, and File Recovery as needed.
- Graph view and Canvas are optional visual aids, not required workflow components.

### Android

- Android access is deferred in v1.
- The Windows vault remains authoritative.
- No third-party mobile sync tool or mobile Git workflow is introduced merely to satisfy optional access.
- Revisit Android only after the Windows workflow proves useful and repeated mobile friction exists.

### Proposed free backup

Recommended v1 backup:

- a separate **private GitHub repository**, not `career-os`;
- proposed name: `career-knowledge-private`;
- local vault remains the working copy;
- WSL Git provides versioned off-device backup through deliberate commits and pushes;
- commit and push after a meaningful note session or before risky structural changes;
- do not add collaborators;
- enable two-factor authentication on the GitHub account;
- exclude volatile workspace files and trash from version control;
- do not store any material classified as outside both the public repository and general vault.

The proposed private GitHub repository is a backup destination, not automatic multi-device sync. Android remains deferred.

## Privacy classification

### Public-safe when deliberately prepared

- Ayush's own concept explanations and derivations;
- citations to public sources;
- summaries written in Ayush's own words;
- public-safe templates and operating guidance.

### Private personal vault

- study notes;
- completed-course concept notes;
- book and paper-reading notes;
- non-confidential research ideas;
- personal learning reflections.

### Outside both

- raw WQU materials;
- active graded questions or submissions;
- employer or client information;
- credentials, recovery codes, secrets, and private keys;
- health records;
- private paper drafts and reviewer correspondence unless a separately reviewed private research location is approved.

## Decision still required

Ayush must explicitly accept or reject storing the private vault's permitted contents in a private GitHub backup repository.

If private GitHub backup is rejected, Step 6.2 must identify another free off-device backup before vault creation. A second local folder on the same laptop is not sufficient as the only backup.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This does not block Obsidian design and must not be addressed on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority.
- No guilt debt applies.
- Prefer one coherent outcome per session.
- Never commit raw WQU materials, active graded work, confidential material, credentials, private datasets, private health information, or uncleared private paper drafts.
- Step 7 remains unauthorised.

## Immediate blocker

Step 6.2 requires Ayush's design review and explicit backup decision.

## Next action

Review the proposed architecture and reply with either:

```text
Accept Step 6.2 design and private GitHub backup
```

or provide the specific design changes and backup objection. Do not begin Step 6.3 before acceptance.
