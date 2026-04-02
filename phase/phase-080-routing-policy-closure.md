# Phase 080 - Routing Policy Closure

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P8
> **Status:** Implemented - Pending Review
> **Design References:** [../design/design.md](../design/design.md), [../design/bun-expert.design.md](../design/bun-expert.design.md), [../design/html-css-js-frontend-expert.design.md](../design/html-css-js-frontend-expert.design.md), [../design/react-frontend-expert.design.md](../design/react-frontend-expert.design.md)
> **Patch References:** [../patch/phase-080-frontend-runtime-routing-policy.patch.md](../patch/phase-080-frontend-runtime-routing-policy.patch.md)

---

## Objective

Close the current open routing-policy surface for Bun runtime, browser-platform, and broader React prompt families.

## Why this phase exists

After the first validation wave, backend-specialist policy was already explicit, but Bun/browser/React still remained in TODO as an unresolved operator decision. That left the workspace with an avoidable ambiguity between explicit specialist routing and acceptable domain-aligned main-assistant handling.

## Design extraction

- Source design: `../design/design.md` section `Validation and Policy Model`
- Per-agent inputs: `../design/bun-expert.design.md`, `../design/html-css-js-frontend-expert.design.md`, `../design/react-frontend-expert.design.md`
- Derived execution work: turn open operator judgment into explicit policy guidance
- Target outcome: current operator expectations are clear even when explicit specialist delegation does not always happen

## Entry conditions / prerequisites

- First routing validation wave has completed
- Backend-specialist explicit-invocation policy is already locked
- Runtime-overlay interpretation is already explicit

## Action points / execution checklist

- [x] Decide whether Bun runtime prompts should be pushed toward explicit specialist delegation or remain acceptable as domain-aligned main-assistant handling
- [x] Decide whether browser-platform prompts should be pushed toward explicit specialist delegation or remain acceptable as domain-aligned main-assistant handling
- [x] Decide whether `react-frontend-expert` should be tuned further beyond the direct hydration-debug explicit win
- [x] Update the affected design/changelog/TODO/governance artifacts with the resulting policy
- [x] Capture the policy change in patch form

## Out of scope

- Adding new frontend/runtime specialists
- Rewriting the runtime agent files solely to chase more explicit delegation right now
- Changing the already-locked backend-specialist policy

## Affected artifacts

- `../design/bun-expert.design.md`
- `../design/html-css-js-frontend-expert.design.md`
- `../design/react-frontend-expert.design.md`
- `../changelog/bun-expert.changelog.md`
- `../changelog/html-css-js-frontend-expert.changelog.md`
- `../changelog/react-frontend-expert.changelog.md`
- `../README.md`
- `../TODO.md`
- `../patch/phase-080-frontend-runtime-routing-policy.patch.md`
- `../changelog/changelog.md`

## TODO coordination

This phase closes the remaining active routing-policy questions so TODO no longer carries unresolved Bun/browser/React ambiguity for the current wave.

## Changelog coordination

Only completed policy outcomes should be recorded in changelog; the open-question state should no longer remain the dominant changelog posture after this phase.

## Evidence / Patch Outputs

- `../patch/phase-080-frontend-runtime-routing-policy.patch.md` captures the before/after policy surface for Bun/browser/React routing interpretation.

## Verification

- Bun runtime policy is explicit
- browser-platform policy is explicit
- React policy is explicit about the direct hydration-debug win and the decision not to force more tuning right now
- TODO no longer uses open-ended wording for this decision surface

## Exit criteria

- Current Bun/browser/React operator expectations are explicit
- The workspace no longer relies on implied judgment for these prompt families

## Risks / rollback notes

- Do not overstate explicit specialist reliability where the current evidence only supports domain-aligned handling
- Do not force additional tuning when the current policy can already guide operators safely

## Current policy decision

For the current environment:
- Bun runtime prompts may remain acceptable under domain-aligned main-assistant handling when routing stays inside Bun-runtime/tooling reasoning and does not drift into backend/service design
- browser-platform prompts may remain acceptable under domain-aligned main-assistant handling when routing stays inside semantic HTML / CSS / browser-platform reasoning and does not drift into React-specific architecture
- direct hydration-debug work remains a clear explicit `react-frontend-expert` win
- broader React prompt families do not need further routing-tuning right now as long as handling remains React/domain-aligned and explicit invocation remains available when specialist behavior is important

## Next possible phases

- later bounded routing-validation slices only if new evidence shows material regression or repeated operator confusion
