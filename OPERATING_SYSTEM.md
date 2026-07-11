# Career OS v1

## 1. Purpose

Career OS coordinates five connected areas:

1. health and recovery;
2. professional work;
3. MScFE study;
4. personal AI engineering and research;
5. public proof of work.

Its purpose is to support slow, sustainable growth toward this identity:

> An AI engineer specialising in financial AI systems who can research ideas deeply and turn them into reliable, usable software.

The system optimises for durable capability over several years, not rapid output over a week, month, or quarter.

---

## 2. First principles

### 2.1 Health is the highest priority

The system must not reward progress achieved through repeatedly sacrificing sleep, exercise, or recovery.

A tired day is not a failed day. Recovery is part of the plan.

### 2.2 No guilt debt

Unfinished work remains unfinished work; it does not become a moral obligation or an automatically doubled workload for the next day.

When a task is interrupted:

- keep the current task open;
- record the smallest useful resume note;
- do not create a compensatory catch-up task;
- reassess capacity at the next planning point.

### 2.3 Consistency does not mean daily completion

Consistency means returning to the system over months and years. It does not mean maintaining a streak, studying every evening, posting every week, or closing every planned task on time.

### 2.4 One meaningful outcome at a time

A focused session should usually complete or advance one coherent outcome, such as:

- answering one conceptual question;
- completing one derivation;
- implementing one function;
- reviewing one pull request;
- finishing one purposeful reading section.

### 2.5 AI does not replace the first attempt

The default learning and implementation loop is:

```text
Understand → Attempt → Review → Receive questions or hints → Revise
```

Direct assistance is appropriate after a genuine attempt, when blocked, or for infrastructure setup where struggling adds little learning value.

### 2.6 Public presence is an output

The order is:

```text
Learn → Derive or build → Document → Publish when worthwhile
```

No work is created merely to satisfy a posting schedule.

---

## 3. Priority hierarchy

### During an active MScFE course

1. Health and sleep
2. Job obligations
3. MScFE deadlines and required learning
4. Deeper MScFE mastery
5. Aligned AI engineering or book work
6. Public presence

### During an MScFE break

1. Health and recovery
2. Job obligations
3. One flagship project or supporting engineering lab
4. Book learning
5. Environment improvement
6. Public presence

### During high-pressure work periods

1. Health
2. Job
3. Minimum MScFE obligations
4. Optional light reading
5. Everything else pauses

### Recovery mode

Recovery mode can be activated whenever exhaustion is high. Rest, light reading, or passive review are valid. Project work, publishing, and catch-up are not required.

---

## 4. Capacity model

### Course mode

- MScFE: approximately 15–20 hours per week when completed honestly and thoroughly.
- Additional AI engineering: approximately 3–4 hours per week.
- Unrelated side projects should not compete with an active course.

### Break mode

- Personal AI engineering: approximately 6–10 hours per week.
- A break must still include recovery; it is not automatically a side-project sprint.

---

## 5. Planning system

### 5.1 Rolling horizon

Detailed planning covers the next two to three days. The system should always identify:

- the current task;
- the next likely task;
- any imminent deadline.

Longer horizons contain direction, not fragile daily schedules.

### 5.2 Weekly review

A 20–30 minute review checks:

- upcoming MScFE deadlines;
- current module state;
- current GitHub issue;
- unfinished work;
- expected job intensity;
- whether the next week needs normal or reduced capacity.

The review is a planning activity, not a performance judgement.

### 5.3 Work-in-progress limits

During course mode:

- one primary MScFE task;
- at most one optional supporting learning task.

During break mode:

- one active project issue;
- one active book or research thread.

A project branch should normally represent one coherent issue finishable in one to three focused sessions.

---

## 6. Session protocol

### Green session

Sufficient energy for 60–120 minutes of deep work: derivations, coding, architecture, complex reading, or difficult assessment preparation.

### Amber session

Some fatigue but capable of 30–60 minutes of useful work: purposeful reading, note review, small experiments, documentation, or test review.

### Red session

Exhausted. Rest is the correct action. A red session creates no backlog and requires no compensation.

### Session close

Leave a minimal trace where appropriate:

- a commit;
- an issue update;
- answers to questions;
- a short progress note;
- an Obsidian note.

The trace records state; it must not become administrative work.

---

## 7. Tool responsibilities

### GitHub

The operating and execution system for version-controlled plans, current state, decisions, standards, issues, pull requests, and public engineering artifacts.

### Project repositories

The home of implementation code, tests, notebooks, architecture, experiments, documentation, and releases for each flagship project.

### Obsidian

The future long-term knowledge system for concepts, derivations, book notes, research notes, and links between finance, mathematics, and AI. It is not a task manager.

### Calendar

The home of fixed deadlines, meetings, group commitments, exams, and selected protected study windows.

### Private storage

The home of WQU PDFs, downloaded notebooks, datasets, assignment instructions, and private drafts.

### ChatGPT

A coordination and mentorship layer that can act as architect, tutor, research assistant, senior engineer, reviewer, project manager, editor, and critical challenger. Important state must be written back to GitHub or Obsidian rather than existing only in a conversation.

---

## 8. Information routing

When new information appears:

- **Actionable work:** create or update a GitHub issue.
- **Conceptual knowledge:** capture it in the Obsidian inbox.
- **Project decision:** record it in the project repository or a decision record.
- **Time-sensitive commitment:** place it in Calendar.
- **Raw course resource:** store it privately.

Knowledge moves through:

```text
Capture → Clarify → Connect → Apply
```

Not every captured note must become permanent.

---

## 9. MScFE module workflow

When a module is released and its materials are shared:

1. **Inventory** notes, readings, notebooks, datasets, assignments, deadlines, and prerequisites.
2. **Define the module brief:** why it exists and what capability it should build.
3. **Create a question map** covering conceptual, mathematical, computational, engineering, and research questions.
4. **Study purposefully** with those questions in mind.
5. **Attempt first:** answer questions and implement relevant work before requesting solutions.
6. **Review deeply:** correctness, reasoning, assumptions, mathematical gaps, and code quality.
7. **Create a reusable artifact where justified:**

```text
Exploratory notebook → validated implementation → reusable Python module → tests → documentation
```

8. **Close the module** when its important questions are answered satisfactorily or an artifact demonstrates the capability.

Not every module needs a portfolio project. It may result in a note, derivation, notebook, small library, experiment, or feature in a larger system.

### Academic-integrity boundary

For active graded work, ChatGPT must not provide quiz answers, complete graded code, write submissions, or perform the analysis on the student's behalf. It may explain concepts, clarify requirements, guide an approach, review attempts, identify errors, and assist with debugging after an attempt.

---

## 10. Book and paper workflows

### Books

Before a chapter or section, define:

- why it matters now;
- which questions it should answer;
- whether it should influence a project;
- how deeply it should be studied.

A chapter may close when important questions are answered, a concept is implemented, a project decision changes, or an experiment is completed.

### Research papers

The preferred workflow is:

```text
Research question → prerequisite map → paper reading → minimal reproduction → comparison → extension → documentation
```

Papers should usually support an MScFE topic, flagship project, research question, or potential PhD direction.

---

## 11. Flagship-project system

Maintain one active flagship project at a time. The long-term target is three to five polished projects rather than many shallow repositories.

A flagship project should demonstrate several of:

- financial-domain understanding;
- sound mathematics;
- research grounding;
- software architecture;
- testing and reproducibility;
- documentation;
- API or application design;
- deployment and evaluation thinking.

Project lifecycle:

```text
Problem framing → architecture → small working version → tested reusable system → evaluation → portfolio-quality release → maintenance
```

### Architecture-defect rule

Stop and refactor when a defect invalidates the system or creates severe future risk. Otherwise, document the debt, finish the current version, and address it in a later version.

### Notebook-to-module rule

Notebooks are for exploration, visualisation, research, and result explanation. Reusable logic moves into Python modules with tests.

---

## 12. Git and review workflow

Default personal workflow:

```text
Issue → feature branch → first attempt → incremental commits → push → draft PR → review → revisions → merge → close issue
```

Use clear Conventional Commit-style messages where practical.

Review should examine architecture, mathematical correctness, naming, readability, edge cases, numerical stability, testing, documentation, reproducibility, security, and maintainability.

---

## 13. Public-presence system

- **GitHub:** primary proof of work.
- **Medium:** deeper engineering and learning narratives.
- **LinkedIn:** concise outcome-oriented insights.
- **Portfolio:** final curated presentation of flagship work and research direction.

There is no posting quota. Publication stops first during overload.

---

## 14. Progress measurement

Do not optimise primarily for hours, pages, posts, repositories, or contribution streaks.

Better evidence includes:

- important questions answered;
- derivations understood;
- tested modules completed;
- project decisions improved;
- pull requests reviewed and merged;
- experiments reproduced;
- portfolio-quality releases;
- health maintained.

---

## 15. Deliberate exclusions from v1

Career OS v1 excludes:

- Obsidian LLM integration;
- complex dashboards;
- automated content publishing;
- productivity scoring;
- multiple simultaneous flagship projects;
- migrating every old note;
- fixed social-media quotas;
- excessive VS Code customisation;
- cloud or CI/CD infrastructure before a project requires it.

Complexity should be added only after real friction demonstrates a need.

---

## Governing statement

> Protect health, honour fixed commitments, learn with questions, build reusable systems, document decisions, publish only what has substance, and continue without guilt after interruptions.
