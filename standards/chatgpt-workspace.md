# ChatGPT Workspace Standard

## Purpose

This document defines how ChatGPT Projects and conversations support Career OS without becoming a second source of truth.

GitHub remains authoritative. ChatGPT provides working context, coordination, tutoring, review, and conversational handoffs.

## Authority order

When sources disagree, use this order:

1. `CURRENT.md` for live operating state;
2. `OPERATING_SYSTEM.md` for governing principles;
3. approved plans and decision records in this repository;
4. the relevant project repository, issue, pull request, or module record;
5. ChatGPT Project instructions;
6. conversation history and remembered context.

A conversation must not claim that repository content was checked unless it was actually retrieved.

## Project architecture

### Active now

#### `Career OS`

Role: central coordination, setup, short-horizon planning, reviews, cross-project decisions, and system maintenance.

Memory mode: default memory.

Initial conversation:

- `00 — Career OS Architecture & Setup`

Additional conversations should be created only when a recurring workflow becomes active. Likely examples are:

- `01 — Weekly Planning & Review`
- `02 — System Decisions & Maintenance`

### Created only when needed

#### `MScFE — <Course Name>`

Create one Project for the currently active course after enrolment is confirmed or the first module is released.

Preferred memory mode: project-only.

Typical conversations:

- `00 — Course Control`
- `M01 — <Module title>`
- `M02 — <Module title>`

One module normally receives one conversation. Do not create separate chats for every reading, notebook, or question.

#### `<Flagship Project Name>`

Create one Project for the single active flagship project after the project-selection step authorises it.

Preferred memory mode: project-only.

Typical conversations:

- `00 — Project Control`
- `#<issue number> — <coherent issue title>`

One coherent GitHub issue normally maps to one implementation conversation. A new day does not require a new conversation.

### Not created in v1

A separate Public Presence Project is not justified yet. Publication decisions remain in Career OS until substantive output makes a dedicated workspace useful.

## Conversation routing

Use the following rule:

| Work type | ChatGPT home | Durable record |
|---|---|---|
| Career OS setup, planning, reviews, or cross-project decisions | `Career OS` | `career-os` repository |
| Active MScFE module learning | active MScFE Project | private course storage plus original notes or safe Career OS records |
| Active flagship implementation | flagship Project | project repository, issue, and pull request |
| Publication decision before a dedicated workflow exists | `Career OS` | Career OS publication record when introduced |
| Small one-off general question with no durable consequence | ordinary chat or the most relevant Project | none unless the answer changes a decision |

When work affects more than one area, coordinate it in Career OS and execute it in the specialised Project.

## Required context retrieval

At the start of substantial planning or cross-project work, retrieve:

1. `CURRENT.md`;
2. the relevant governing section of `OPERATING_SYSTEM.md`;
3. the approved plan or decision record;
4. the relevant issue, pull request, module record, or project files.

At the start of substantial implementation work, establish:

- role;
- objective;
- repository;
- issue, module, or decision being handled;
- relevant files;
- current branch when applicable;
- definition of done.

Do not upload permanent copies of live Career OS files into ChatGPT Projects. Retrieve the current GitHub version so stale duplicates do not become competing context.

## When to create a new conversation

Create a new conversation when at least one of these is true:

- the work has a different durable objective;
- a new MScFE module begins;
- a new coherent GitHub issue begins;
- the current conversation has completed its purpose and a clear handoff exists;
- continuing would mix unrelated roles or repositories;
- the existing conversation has become too large to resume reliably.

Do not create a new conversation merely because:

- a new day or study session begins;
- the same issue continues;
- one small sub-question appears;
- the current work is temporarily blocked.

## Conversation naming

Use names that reveal the durable unit of work.

### Control conversations

```text
00 — Career OS Architecture & Setup
00 — Course Control
00 — Project Control
```

### MScFE modules

```text
M01 — <Module title>
M02 — <Module title>
```

### Project issues

```text
#12 — Implement pricing interface
#13 — Add numerical-stability tests
```

Avoid titles such as `New Chat`, `Today`, `Python Help`, or `Random Questions`.

## Closing Summary

At the end of substantial work, produce a Closing Summary containing:

1. objective;
2. completed work;
3. decisions made;
4. evidence or files changed;
5. unresolved questions;
6. exact resume point;
7. required GitHub or `CURRENT.md` updates;
8. recommended next conversation.

The summary is conversational handoff context. It should be concise enough to paste into the next conversation when needed.

## Closing Summary versus durable completion record

A Closing Summary is not the durable history of the work.

Durable history belongs in the appropriate location:

- GitHub issue for task progress and acceptance criteria;
- pull request for implementation and review history;
- decision record for architectural choices;
- module note for learning outcomes;
- review document for periodic reflection;
- `CURRENT.md` for live state only.

The conversation should identify required durable updates before it closes.

## Project-source discipline

- Project instructions contain behaviour and boundaries.
- GitHub contains authoritative state and public durable records.
- Private storage contains raw WQU materials, private datasets, and assignment instructions.
- Obsidian will contain evergreen personal knowledge after its setup step.
- Uploaded ChatGPT Project files should be limited to actively needed materials.
- Stable briefs may be saved as Project sources only when they are not already maintained elsewhere.

## Academic and confidentiality boundaries

Do not place the following in the public Career OS repository or expose them across inappropriate Projects:

- raw WQU course materials;
- graded questions or submissions;
- employer or client confidential information;
- private datasets;
- credentials or API keys;
- private personal or health information.

For active graded MScFE work, ChatGPT may explain, question, review, and debug an attempted solution, but must not provide a complete submission.

## Workspace test protocol

After changing the ChatGPT workspace or Project instructions:

1. open a small test conversation inside the relevant Project;
2. ask it to retrieve `Harper2123/career-os/CURRENT.md`;
3. ask it to state the current operating mode, active setup step, and next permitted action;
4. verify the answer against the repository;
5. delete the test conversation if it has no future value.

A successful test demonstrates access and instruction behaviour. It does not replace periodic repository retrieval.
