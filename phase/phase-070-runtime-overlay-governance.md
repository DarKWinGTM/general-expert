# Phase 070 - Runtime Overlay Governance

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P7
> **Status:** Implemented - Pending Review
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** [../patch/phase-070-runtime-overlay.patch.md](../patch/phase-070-runtime-overlay.patch.md)

---

## Objective

Document how routing evidence should be interpreted when the managed fleet is evaluated inside a larger live runtime that also contains unmanaged co-resident agents.

## Why this phase exists

File-level source parity for the managed fleet is not the same as total routing control over the entire live runtime. The workspace needed an explicit interpretation rule so validation findings would not overclaim what this source-governed fleet actually controls.

## Design extraction

- Source design: `../design/design.md` section `Runtime Overlay Note`
- Derived execution work: define the difference between managed-fleet truth and mixed-runtime observation
- Target outcome: routing evidence remains honest about scope

## Entry conditions / prerequisites

- The managed source files are already synchronized to runtime
- Validation evidence already shows interference or interception from co-resident agents in some prompt classes

## Action points / execution checklist

- [x] Record that the managed fleet governs 7 source-controlled agents only
- [x] Record that co-resident unmanaged agents can still shape observed routing behavior
- [x] Name the most relevant co-resident overlay agents in the live runtime interpretation model
- [x] Add the overlay note to active governance docs
- [x] Capture the change as a patch-backed governance decision

## Out of scope

- Removing unmanaged co-resident agents from the live runtime
- Expanding governance ownership to every runtime agent in `~/.claude/agents/`
- Re-running the entire routing matrix in a clean-room runtime

## Affected artifacts

- `../README.md`
- `../design/design.md`
- `SUMMARY.md`
- `../patch/phase-070-runtime-overlay.patch.md`
- `../changelog/changelog.md`

## TODO coordination

This phase closes the ambiguity about what the managed-fleet governance model can and cannot claim about live routing behavior.

## Changelog coordination

The overlay note is recorded at fleet level because it changes how validation evidence is interpreted for the whole workspace.

## Evidence / Patch Outputs

- `../patch/phase-070-runtime-overlay.patch.md` captures the before/after interpretation model.

## Verification

- README explains the managed-fleet vs mixed-runtime distinction
- master design defines the runtime-overlay rule explicitly
- summary-level validation interpretation no longer implies a clean 7-agent-only runtime when unmanaged co-resident agents are present

## Exit criteria

- Managed-fleet truth and live-runtime overlay truth are both explicit
- routing evidence is no longer overstated beyond the controlled scope of this workspace

## Risks / rollback notes

- Do not let the overlay note weaken the governed source-of-truth model for the managed fleet itself
- Keep the distinction narrow: file governance remains here, total runtime behavior remains broader

## Next possible phases

- `phase-080-routing-policy-closure.md`
