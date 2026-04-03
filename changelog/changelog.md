# General Expert Agents Changelog

> **Parent Document:** [../design/design.md](../design/design.md)
> **Current Version:** 0.7.0
> **Last Updated:** 2026-04-02

---

## Version History

| Version | Date | Changes | Summary |
|---------|------|---------|---------|
| 0.8.0 | 2026-04-03 | **Repo-root install docs normalized and validated** | Reworked the public install story around repo-root local marketplace usage, validated `./`-based install from the standalone repo root, and kept the shared `darkwingtm` route scoped as local workspace development context. |
| 0.7.0 | 2026-04-02 | **Local marketplace install validated** | Added the shared local marketplace scaffold, installed the fleet through local marketplace settings, and verified the plugin-installed fleet appears in normal agent discovery. |
| 0.6.0 | 2026-04-01 | **Plugin-compatible fleet layout validated** | Refactored the fleet into `agents/`, added `.claude-plugin/plugin.json`, fixed agent frontmatter parsing, and verified local `--plugin-dir` loading for the same workspace. |
| 0.5.0 | 2026-03-31 | **Multilingual routing interpretation wave opened** | Began shifting routing strategy from language-specific alias thinking toward multilingual intent-based routing wording. |
| 0.4.0 | 2026-03-30 | **Governance reconciliation and patch baseline added** | Added README plus patch evidence artifacts, reconciled P4/P5 status drift, documented runtime-overlay interpretation, and closed the current frontend/runtime routing-policy baseline. |
| 0.3.0 | 2026-03-28 | **Narrow backend matrix v2 completed** | Recorded PASS / FAIL / INCONCLUSIVE outcomes for the self-contained backend specialist routing tests. |
| 0.2.0 | 2026-03-28 | **First sync and validation completed** | Synced the governed source fleet to runtime and recorded the first routing validation findings. |
| 0.1.0 | 2026-03-28 | **Governance baseline initialized** | Created master changelog skeleton for the `general-expert` governed source fleet. |

---

## Version 0.8.0: Repo-root Install Docs Normalized and Validated

**Date:** 2026-04-03
**Status:** Implemented - Pending Review

### Changed

- Reworked `README.md` so the public install path now starts from the standalone repo root instead of the shared `TEMPLATE/PLUGIN` workspace path.
- Replaced source-side public install examples with repo-root guidance using:
  - `claude plugins marketplace add ./ --scope local`
  - `claude plugins install general-expert@general-expert --scope local`
- Kept the shared `darkwingtm` marketplace route documented only as a checked local development note rather than the public default install story.

### Validation

- `claude plugins marketplace add ./ --scope local` succeeds from the repo root.
- `claude plugins install general-expert@general-expert --scope local` succeeds from the repo root.
- `claude agents` shows the full `general-expert:*` fleet after repo-root install.

### Summary

The fleet now teaches a portable public install story from its own repo root while preserving the shared `darkwingtm` route only as scoped local workspace context.

---

## Version 0.7.0: Local Marketplace Install Validated

**Date:** 2026-04-02
**Status:** Implemented - Pending Review

### Added

- Added the shared local marketplace scaffold at `<marketplace-root>/.claude-plugin/marketplace.json`.
- Added package-local `.claude-plugin/marketplace.json` so this package can later cut over into its own standalone repo-local marketplace root.

### Changed

- Updated README/design/TODO/phase wording to distinguish local plugin-dir testing from marketplace-style local install.
- Installed `general-expert@darkwingtm` into local scope so the same governed fleet now persists through `.claude/settings.local.json`.
- Retired the redundant loose-file runtime copies under `<user-runtime-agents>/` so the fleet now converges on the marketplace-installed path.

### Validation

- `claude plugins marketplace add <marketplace-root> --scope local` succeeds.
- `claude plugins install general-expert@darkwingtm --scope local` succeeds.
- `claude agents` shows the full `general-expert:*` fleet in normal discovery after install.
- plugin cache materializes under `~/.claude/plugins/cache/darkwingtm/general-expert/1.0.0/`.
- the full `general-expert:*` fleet remains visible after `/reload-plugins`.
- the full `general-expert:*` fleet also remains visible from a fresh CLI process, closing the current restart-time lifecycle check.

### Summary

The governed fleet now works through a real local marketplace install path, not only through `--plugin-dir` or loose-file deployment.

---

## Version 0.6.0: Plugin-Compatible Fleet Layout Validated

**Date:** 2026-04-01
**Status:** Implemented - Pending Review

### Added

- Added `.claude-plugin/plugin.json` to the main `general-expert` workspace.
- Added `agents/` as the plugin-compatible runtime directory for the managed fleet.

### Changed

- Moved the 7 managed agent runtime files from the workspace root into `agents/`.
- Fixed YAML frontmatter parsing by quoting long `description` strings in the runtime agent files.
- Updated README/design/TODO toward the plugin-compatible workspace model.

### Validation

- `claude plugins validate "<workspace-root>"` passes.
- `claude --plugin-dir "<workspace-root>" agents` shows the full `general-expert:*` fleet.
- direct invocation works in the checked plugin-dir session.

### Summary

The `general-expert` fleet now works as a single-workspace plugin-compatible source without creating a duplicate project.

---

## Version 0.5.0: Multilingual Routing Interpretation Wave Opened

**Date:** 2026-03-31
**Status:** In Progress

### Added

- Opened `phase-090-multilingual-routing-interpretation.md`
- Added `patch/phase-090-multilingual-routing-interpretation.patch.md`

### Changed

- Began shifting the routing strategy from language-specific alias thinking toward multilingual intent-based routing wording
- Began updating specialist runtime descriptions so routing should follow task/domain intent rather than exact wording or prompt language
- Began updating fleet-level governance wording so multilingual routing remains a front-door interpretation concern rather than a body-translation project

---

## Version 0.4.0: Governance Reconciliation and Patch Baseline Added

**Date:** 2026-03-30
**Status:** Implemented - Pending Review

### Added

- Added workspace `README.md` as the operator entrypoint for the governed fleet
- Added the first governed `patch/*.patch.md` evidence layer for sync, validation, policy, reconciliation, runtime-overlay, and frontend/runtime routing-policy closure
- Opened the governance-hardening family:
  - `phase-060-governance-reconciliation.md`
  - `phase-070-runtime-overlay-governance.md`
  - `phase-080-routing-policy-closure.md`

### Changed

- Reconciled P4/P5 phase-state drift so the child phase files now match the already-recorded sync and validation outcomes
- Updated the master design to remove stale future-state wording and to define patch/evidence and runtime-overlay boundaries explicitly
- Tightened TODO so pending sections now contain pending work only
- Documented that the managed fleet is governed here, while observed routing behavior still emerges from a mixed live runtime that also contains unmanaged co-resident agents

### Governance decisions recorded

- `nodejs-backend-expert` and `python-backend-expert` remain explicit-invocation-oriented specialists for this environment
- Bun runtime, browser-platform, and broader React prompt families are currently acceptable under domain-aligned main-assistant handling when explicit delegation does not occur, as long as routing does not drift into the wrong specialist domain
- direct React hydration-debug work remains a clear explicit specialist win and does not require further tuning at this stage

### Patch linkage established

The current evidence-bearing patch set is:
- `../patch/phase-040-runtime-sync.patch.md`
- `../patch/phase-050-validation-round-1.patch.md`
- `../patch/phase-055-backend-specialist-policy.patch.md`
- `../patch/phase-060-governance-reconciliation.patch.md`
- `../patch/phase-070-runtime-overlay.patch.md`
- `../patch/phase-080-frontend-runtime-routing-policy.patch.md`

---

## Version 0.3.0: Narrow Backend Matrix v2 Completed

**Date:** 2026-03-28
**Status:** Validation conclusions recorded

### Added

- Completed the self-contained narrow backend validation matrix v2 for `nodejs-backend-expert` and `python-backend-expert`
- Recorded PASS / FAIL / INCONCLUSIVE outcomes separately from round one

### Findings

- `nodejs-backend-expert`
  - **FAIL (explicit routing):** N2-v2, N4-v2
  - **PASS (domain alignment only):** N2-v2, N4-v2
  - **INCONCLUSIVE:** N1-v2 because no Fastify auth middleware target existed in the checked workspace
- `python-backend-expert`
  - **FAIL (explicit routing):** P2-v2, P5-v2
  - **PASS (domain alignment only):** P2-v2, P5-v2
  - **INCONCLUSIVE:** P1-v2 because no FastAPI OAuth callback flow existed in the checked FastAPI scope

### Conclusion

Current evidence supports treating `nodejs-backend-expert` and `python-backend-expert` as governed specialists that are most reliable when explicitly invoked or when given attached target files, rather than expecting delegation-first routing from generic natural-language prompts in this environment.

### Final governance decision

For this environment:
- backend specialist quality is real
- explicit specialist invocation is reliable
- auto-routing for broad backend prompts is not reliably specialist-first
- attached target files improve precision, but do not by themselves guarantee explicit delegation

Therefore, the operational recommendation is to prefer explicit invocation for `nodejs-backend-expert` and `python-backend-expert` when specialist behavior is important.

---

## Version 0.2.0: First Sync and Validation Completed

**Date:** 2026-03-28
**Status:** In progress with follow-up refinement

### Added

- Completed the first governed source-to-runtime sync for all 7 managed agent files into `<user-runtime-agents>/`
- Verified that deployed runtime copies match the governed source files
- Ran the first routing validation matrix against the synced runtime fleet

### Findings

- Explicit PASS: `nodejs-expert` for Node runtime/module/tooling prompts
- Explicit PASS: `bun-backend-expert` for Bun.serve + Hono backend architecture prompts
- Explicit PASS: `react-frontend-expert` for direct Next.js App Router hydration-mismatch debugging prompt
- Behavioral PASS: React collision prompt stayed in React/Next-oriented plan/explore behavior and did not drift to browser-platform specialization
- Misroute candidate: `nodejs-backend-expert` did not trigger explicitly for backend architecture/design prompt
- First tuning round for `nodejs-backend-expert` improved backend wording but revalidation still routed through `multi-hat-system` instead of explicit specialist delegation
- Follow-up review needed: `python-backend-expert`, browser UI, and Bun runtime prompts should be evaluated for whether current plan/direct behavior is acceptable or whether stronger explicit specialist delegation is desired
- First tuning round for `python-backend-expert` improved backend framing but revalidation still stayed in generic plan-mode flow rather than explicit specialist delegation

### Next focus

- accept that architecture-heavy backend prompts are currently generic planning territory rather than forced specialist-routing territory
- note that narrow backend matrix v2 still failed explicit routing for backend specialists even after ambiguity reduction
- decide whether to stop further routing-tuning and document `nodejs-backend-expert` / `python-backend-expert` as specialists that benefit from explicit invocation
- if more testing is desired later, use artifact-attached review/debug prompts rather than generic natural-language prompts alone

---

## Version 0.1.0: Governance Baseline Initialized

**Date:** 2026-03-28
**Status:** Draft baseline

### Added

- Established master changelog authority for the `general-expert` source fleet
- Linked changelog to `design/design.md`
- Defined this file as the historical record for fleet-wide changes

### Intended future usage

Use this changelog for:
- fleet-level taxonomy changes
- routing policy changes
- sync workflow changes
- major rollout milestones affecting multiple agents

---

## Changelog Rules

- Record shipped or synchronized changes, not tentative ideas
- Use `design/design.md` as the architecture/governance authority
- Keep per-agent wording changes and recorded routing outcomes in per-agent changelog files
- Use this master changelog when changes affect the fleet as a whole

---

> **Design:** [../design/design.md](../design/design.md)
