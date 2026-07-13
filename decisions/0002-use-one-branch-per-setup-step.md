# Decision 0002 — Use one branch per top-level setup step

- **Status:** Accepted
- **Date:** 2026-07-12

## Context

The initial Career OS setup used a separate branch and pull request for many substeps such as `Step 3.4`, `Step 3.5`, and `Step 3.6`. That produced excessive branch and pull-request churn for work that belongs to one coherent top-level setup outcome.

## Decision

For the gated Career OS setup roadmap, use one working branch per top-level step:

```text
setup/step-<X>
```

All authorised substeps `X.Y` are completed iteratively on that branch using small, meaningful commits. Do not create a pull request for each substep.

Create one pull request only after the entire top-level Step `X` has met its completion condition and all substep verification is complete. Review and merge that pull request, then allow GitHub's automatic head-branch deletion setting to remove the branch.

While a top-level setup step is active:

- the active `setup/step-<X>` branch is the working source of truth for that step;
- `CURRENT.md` on that branch records the live substep state;
- `main` represents the last merged top-level checkpoint;
- unrelated work must not be added to the setup branch.

The remaining work in Step 3 adopts this model prospectively on `setup/step-3`. Steps 4–11 will follow it from their start.

## Exception

An early pull request is allowed only when a severe defect, recovery requirement, or independent review need makes waiting until the top-level step finishes unsafe. The reason must be documented explicitly.

## Consequences

- fewer temporary branches and administrative pull requests;
- one coherent review per top-level setup outcome;
- stronger need for clear incremental commits and verification notes;
- a larger final pull request, kept manageable by limiting each setup branch to one top-level step;
- automatic branch deletion remains enabled after merge.
