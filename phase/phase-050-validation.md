# Phase 050 - Validation

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P5
> **Status:** Completed With Follow-up
> **Design References:** [../design/design.md](../design/design.md), [../design/nodejs-expert.design.md](../design/nodejs-expert.design.md), [../design/nodejs-backend-expert.design.md](../design/nodejs-backend-expert.design.md), [../design/bun-expert.design.md](../design/bun-expert.design.md), [../design/bun-backend-expert.design.md](../design/bun-backend-expert.design.md), [../design/html-css-js-frontend-expert.design.md](../design/html-css-js-frontend-expert.design.md), [../design/react-frontend-expert.design.md](../design/react-frontend-expert.design.md), [../design/python-backend-expert.design.md](../design/python-backend-expert.design.md)
> **Patch References:** [../patch/phase-050-validation-round-1.patch.md](../patch/phase-050-validation-round-1.patch.md), [../patch/phase-055-backend-specialist-policy.patch.md](../patch/phase-055-backend-specialist-policy.patch.md)

---

## Objective

Validate that the deployed runtime agent fleet routes prompts according to the governed design contracts.

## Why this phase exists

A governed source workspace is not enough by itself. The deployed runtime must also demonstrate correct discovery and routing behavior against the intended taxonomy.

## Design extraction

- Source design: `../design/design.md` sections `Routing and Boundary Rules`, `Validation and Policy Model`
- Per-agent source input: each `../design/*.design.md` validation target and routing intent section
- Derived execution work: run discovery and prompt-routing checks against the deployed agent fleet
- Target outcome: routing becomes evidence-backed instead of assumed

## Entry conditions / prerequisites

- Runtime sync phase has completed
- Runtime agent copies are discoverable by Claude Code

## Action points / execution checklist

- [x] Verify runtime discovery with the deployed fleet
- [x] Run prompt-routing checks across the managed-agent taxonomy
- [x] Record misroutes and successful specialist wins against the per-agent design documents
- [x] Decide whether fixes belong in `description`, design policy, or operator usage guidance
- [x] Update changelog/TODO and patch evidence for backend-specialist policy closure
- [x] Carry remaining Bun / browser / React closure work into explicit follow-up governance phases

## Out of scope

- New agent additions outside the current 7-agent fleet
- Runtime sync procedure redesign

## Affected artifacts

- `<user-runtime-agents>/*.md`
- `../design/*.design.md`
- `../patch/phase-050-validation-round-1.patch.md`
- `../patch/phase-055-backend-specialist-policy.patch.md`
- `../TODO.md`
- `../changelog/changelog.md`

## TODO coordination

This phase completed the first routing-validation wave and handed remaining Bun / browser / React policy closure into the 080 family instead of leaving the work implicit.

## Changelog coordination

Validation outcomes that changed governed routing policy are recorded at fleet level and in the affected per-agent histories.

## Evidence / Patch Outputs

- `../patch/phase-050-validation-round-1.patch.md` captures the first routing-matrix before/after evidence surface.
- `../patch/phase-055-backend-specialist-policy.patch.md` captures the shift from assumed auto-routing to explicit-invocation-oriented backend specialist policy.

## Verification

- The managed runtime fleet was discoverable in live validation work
- `nodejs-expert` showed a clear explicit runtime/tooling routing win
- `bun-backend-expert` showed a clear explicit Bun backend architecture routing win
- direct React hydration-debug work showed a clear explicit `react-frontend-expert` win
- `nodejs-backend-expert` and `python-backend-expert` did not show reliable explicit delegation for broad architecture-heavy prompts, but remained domain-aligned enough to justify explicit-invocation policy instead of more description-only tuning

## Exit criteria

- The deployed routing behavior is evidence-backed rather than assumed
- Remaining misroutes are identified with a clear next-fix location
- Backend-specialist policy is explicit for this environment

## Risks / rollback notes

- Do not over-correct one agent description in a way that creates new collisions elsewhere
- Prefer evidence-backed policy closure over endless wording tuning when the environment keeps favoring main-assistant direct handling

## Next possible phases

- `phase-060-governance-reconciliation.md`
- `phase-070-runtime-overlay-governance.md`
- `phase-080-routing-policy-closure.md`
