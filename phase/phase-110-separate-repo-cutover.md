# Phase 110 - Separate repo cutover

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P11
> **Status:** Implemented - Pending Review
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** [../patch/phase-110-separate-repo-cutover.patch.md](../patch/phase-110-separate-repo-cutover.patch.md)

---

## Objective

Finalize `general-expert` as its own standalone GitHub repo authority without leaving duplicate public install posture behind in the shared workspace.

## Action points / execution checklist
- [x] finish restart-time visibility validation
- [ ] close remaining multilingual-routing and governance follow-up as needed for cutover
- [x] create/push `DarKWinGTM/general-expert`
- [x] validate repo-root local marketplace install from `./`
- [ ] switch authority from shared workspace to standalone repo
- [ ] retire shared-workspace authority cleanly
