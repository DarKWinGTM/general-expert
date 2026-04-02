# Phase 020 - Per-Agent Design Baseline

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P2
> **Status:** Completed
> **Design References:** [../design/design.md](../design/design.md), [../design/nodejs-expert.design.md](../design/nodejs-expert.design.md), [../design/nodejs-backend-expert.design.md](../design/nodejs-backend-expert.design.md), [../design/bun-expert.design.md](../design/bun-expert.design.md), [../design/bun-backend-expert.design.md](../design/bun-backend-expert.design.md), [../design/html-css-js-frontend-expert.design.md](../design/html-css-js-frontend-expert.design.md), [../design/react-frontend-expert.design.md](../design/react-frontend-expert.design.md), [../design/python-backend-expert.design.md](../design/python-backend-expert.design.md)
> **Patch References:** none

---

## Objective

Establish per-agent design authority for all managed agents so routing and scope changes can be governed at the agent level instead of only at the fleet level.

## Why this phase exists

Once the fleet is split into multiple specialists, the master design is not enough. Each agent needs its own design contract for ownership, routing intent, and refinement history.

## Design extraction

- Source design: `../design/design.md` sections `Agent Fleet Baseline`, `Routing and Boundary Rules`, `Authoring Contract`
- Derived execution work: create one per-agent design skeleton for each managed agent
- Target outcome: every agent has its own design-level authority file

## Entry conditions / prerequisites

- Governance baseline exists
- The managed-agent list is stable enough to define per-agent documents

## Action points / execution checklist

- [x] Create `nodejs-expert.design.md`
- [x] Create `nodejs-backend-expert.design.md`
- [x] Create `bun-expert.design.md`
- [x] Create `bun-backend-expert.design.md`
- [x] Create `html-css-js-frontend-expert.design.md`
- [x] Create `react-frontend-expert.design.md`
- [x] Create `python-backend-expert.design.md`

## Out of scope

- Runtime sync
- Prompt-matrix validation
- Per-agent changelog history details beyond skeleton creation

## Affected artifacts

- `../design/*.design.md`
- `../design/design.md`

## TODO coordination

This phase clears the “add per-agent design files” decision by implementing the skeletons directly.

## Changelog coordination

This phase should be reflected in the master changelog as the creation of per-agent design authority files.

## Verification

- There is one design file per managed agent
- Each file links to its future per-agent changelog
- Each file defines purpose, ownership boundary, routing intent, and validation targets

## Exit criteria

- All 7 managed agents have design skeletons
- The per-agent design layer is linked into the governed workspace

## Risks / rollback notes

- Keep the files skeletal and high-signal; do not overfill before real refinement work begins

## Next possible phases

- `phase-030-per-agent-changelog-baseline.md`
- `phase-040-runtime-sync.md`
