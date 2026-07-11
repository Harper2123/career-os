# ADR 0001 — Adopt Career OS v1

- **Status:** Accepted
- **Date:** 2026-07-11

## Context

The previous approach used a general AI engineering roadmap and a Telco churn prediction service as the main organising structures. That approach no longer matched the actual situation:

- a full-time AI engineering role;
- an active MScFE with substantial weekly workload;
- a long-term financial AI specialisation;
- research and possible PhD ambitions;
- a strong requirement to protect health and avoid burnout;
- a preference for slow, consistent growth rather than fixed sprint pressure.

The earlier repositories and ChatGPT project were intentionally deleted to remove stale assumptions and avoid maintaining two competing systems.

## Decision

Adopt a new public repository, `Harper2123/career-os`, as the version-controlled source of truth for cross-project direction, current state, major decisions, plans, standards, and reviews.

The governing principles are documented in `OPERATING_SYSTEM.md`. The live operational state is documented in `CURRENT.md`.

## Tool boundaries

- GitHub stores authoritative plans, decisions, issues, reviews, and public engineering artifacts.
- Separate project repositories store implementation code and experiments.
- Obsidian will store evergreen conceptual knowledge.
- Calendar will store fixed commitments and deadlines.
- Private storage will hold course materials, graded instructions, and non-public files.
- ChatGPT will coordinate, teach, review, and challenge, but will not be the sole home of important state.

## Key consequences

### Positive

- One clear source of truth replaces fragmented planning.
- MScFE and AI engineering reinforce one professional identity.
- Health and interruption handling are explicit system requirements.
- Important decisions become durable and reviewable.
- Future ChatGPT Projects can share context through the same repository.

### Costs

- `CURRENT.md` must remain reasonably current.
- The system requires discipline to keep private and confidential material out of the public repository.
- Additional tools must not become competing task managers.

### Risks

- Over-engineering the operating system instead of doing real work.
- Excessive administrative updates.
- Treating every course concept as a project or publication opportunity.

These risks are controlled by work-in-progress limits, minimal session traces, explicit step gates, and deliberate exclusions from v1.

## Alternatives considered

### Repurpose the old AI engineering roadmap repository

Rejected because its history, issue structure, and fixed roadmap carried assumptions that no longer matched the financial AI and MScFE-centred direction.

### Keep separate systems for MScFE, AI engineering, and public presence

Rejected because it would create competing priorities, duplicated state, and context fragmentation.

### Use only ChatGPT as the planning system

Rejected because conversations and Projects should not be the sole durable source of operational truth.

## Review trigger

Review this decision after the first complete Career OS work cycle or when sustained real-world friction shows that the source-of-truth architecture is failing.
