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

Validate the lightweight private Obsidian system by capturing, connecting, reviewing, retrieving, and privately backing up one completed MScFE concept.

The accepted completion-test concept is **Weak stationarity** from the completed Financial Econometrics course.

## Current task

**Step 6.4 is active.**

Step 6.4 is staged around Ayush's first attempt:

1. **Step 6.4a: active.** Create `10 Concepts/Weak stationarity.md` through the existing map link, insert the accepted concept template, and write a first attempt from memory.
2. **Step 6.4b: pending.** Review the first attempt for conceptual correctness, notation, assumptions, example quality, boundary cases, clarity, links, and privacy; then revise.
3. **Step 6.4c: pending.** Verify navigation and search retrieval, inspect the private vault diff, commit, push, and confirm the off-device backup.

Do not begin Step 6.4b or Step 6.4c before the first attempt is returned for review. Do not create the two related concept notes during Step 6.4.

## Step 6 execution model

1. **Activation: complete.** Create `setup/step-6` and record the authorised objective.
2. **Step 6.1: complete.** Inventory installation, vaults, devices, sync, backup, workflows, privacy constraints, and test concept.
3. **Step 6.2: complete.** Accept the minimum vault, storage, folders, navigation, naming, links, metadata, attachments, plugins, Android, privacy, and backup architecture.
4. **Step 6.3: complete.** Create and verify the local vault and private versioned backup.
5. **Step 6.4: active.** Capture, connect, review, retrieve, and back up weak stationarity using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review the full system, record the public-safe standard, open and merge the Step 6 pull request, and clean up.

## Step 6.4 definition of done

Step 6.4 is complete only when:

1. `10 Concepts/Weak stationarity.md` exists and uses the accepted concept template;
2. the note explains the concept in Ayush's own words;
3. the mathematical statement identifies the required conditions with clear notation and assumptions;
4. one valid example is justified rather than merely named;
5. one counterexample or boundary case identifies which condition fails;
6. the note links to `[[Autocovariance and autocorrelation]]` and `[[Unit roots and non-stationarity]]` without creating those notes;
7. the note is reachable through `Home -> MOC - Financial Econometrics -> Weak stationarity`;
8. Obsidian search retrieves the note through `weak stationarity` and any accepted alias;
9. the note contains no raw WQU material, active graded work, copied assessment text, confidential information, credentials, private data, or uncleared draft material;
10. the reviewed vault change is committed and pushed to the private backup repository with a clean zero-ahead and zero-behind state.

## Learning contract

The governing learning loop remains:

```text
Understand -> Attempt -> Review -> Receive questions or hints -> Revise
```

For Step 6.4a:

- Ayush writes the first attempt before receiving a model answer.
- The first attempt may be incomplete.
- Uncertainty must be recorded rather than hidden.
- No source consultation, AI-generated explanation, or copied course text is required for the first attempt.
- If memory is weak, the note should state the uncertainty and continue with the parts that can be explained.
- A tired session may stop with a clear resume point and creates no guilt debt.

## Accepted vault and backup

- Vault name: `career-knowledge`
- Windows path: `%USERPROFILE%\Documents\Obsidian\career-knowledge`
- WSL path: `/mnt/c/Users/akcoo/Documents/Obsidian/career-knowledge`
- Private backup repository: `Harper2123/career-knowledge-private`
- Backup branch: `main`
- Initial backup commit: `159d10fd26d001f09ca2e1b5f34ca25fb0ecbb0c`
- Initial backup was pushed successfully with zero ahead and behind counts.
- The private repository is backup, not automatic sync.
- Android access remains deferred.

## Accepted navigation and note structure

Primary path:

```text
Home -> MOC - Financial Econometrics -> Weak stationarity
```

Secondary retrieval:

```text
Obsidian search -> weak stationarity
```

Accepted template sections:

```text
Definition in my own words
Mathematical statement
Intuition
Example
Counterexample or boundary case
Why it matters
Related concepts
Questions or uncertainties
Sources
```

Minimal property:

```yaml
type: concept
```

## Step 6.4a boundaries

Authorised:

- open the existing private vault;
- click the unresolved `Weak stationarity` link from `MOC - Financial Econometrics`;
- create the note in `10 Concepts`;
- insert `99 Templates/Concept.md` through the built-in Templates plugin;
- write a first attempt in Ayush's own words;
- add unresolved wikilinks to the two accepted related concepts;
- return the note text and local filename-level verification for review.

Not authorised yet:

- consulting or copying raw WQU materials into the vault;
- asking AI to write the note;
- creating the two related concept notes;
- changing the template, folder architecture, plugins, sync, or Android setup;
- committing or pushing the new note before review;
- beginning Step 6.5.

## Privacy classification

Permitted in the private vault and backup:

- personal study notes;
- completed-course concept notes in Ayush's own words;
- book and paper-reading notes written in Ayush's own words;
- non-confidential research ideas;
- personal learning reflections.

Outside the public repository, general vault, and private backup:

- raw WQU course materials;
- active graded questions or submissions;
- employer or client information;
- credentials, recovery codes, secrets, API keys, and private keys;
- private datasets;
- health records;
- private paper drafts and reviewer correspondence unless separately approved.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority.
- No guilt debt applies.
- Prefer one coherent outcome per session.
- No community plugins or LLM integration in v1.
- Step 7 remains unauthorised.

## Immediate blocker

Step 6.4a requires Ayush's first attempt. There is no infrastructure blocker.

## Next action

Synchronise `setup/step-6` to this activation commit, complete only the first-attempt note, return it for review, and stop before committing or pushing the vault change.
