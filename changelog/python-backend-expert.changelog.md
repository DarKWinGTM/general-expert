# Python Backend Expert Changelog

> **Parent Document:** [../design/python-backend-expert.design.md](../design/python-backend-expert.design.md)
> **Current Version:** 0.3.0
> **Last Updated:** 2026-03-30

---

## Version History

| Version | Date | Changes | Summary |
|---------|------|---------|---------|
| 0.3.0 | 2026-03-30 | **Explicit-invocation policy locked** | Closed the validation follow-up by recording `python-backend-expert` as an explicit-invocation-oriented specialist for this environment. |
| 0.2.0 | 2026-03-28 | **Validation review recorded** | First routing matrix showed a FastAPI implementation prompt was handled by generic plan-mode flow instead of explicit specialist delegation. |
| 0.1.0 | 2026-03-28 | **Initial per-agent changelog skeleton** | Established changelog authority for `python-backend-expert`. |

---

## Version 0.3.0: Explicit-Invocation Policy Locked

**Date:** 2026-03-30
**Status:** Recorded

### Added

- Recorded the final current operator policy for `python-backend-expert`

### Findings

- repeated validation did not show reliable explicit specialist delegation for broad implementation-heavy FastAPI/backend prompts
- domain-aligned backend reasoning still remained visible in important prompt classes
- explicit invocation and attached target files are the preferred reliable use model when specialist behavior matters

### Governance decision

For the current environment, `python-backend-expert` should be treated as an **explicit-invocation-oriented specialist** rather than a delegation-first auto-routed specialist.

---

## Version 0.2.0: Validation Review Recorded

**Date:** 2026-03-28
**Status:** Recorded

### Findings

- The first routing validation matrix showed that an implementation-oriented FastAPI prompt was handled by generic plan-mode exploration rather than explicit `python-backend-expert` delegation
- Later tuning still did not produce reliable explicit delegation for that implementation-heavy prompt class
- Narrow validation also showed domain alignment in some prompt shapes even when explicit delegation did not occur

---

## Version 0.1.0: Initial Per-Agent Changelog Skeleton

**Date:** 2026-03-28
**Status:** Draft baseline

### Added

- Created per-agent changelog for `python-backend-expert`
- Linked the changelog to the per-agent design document
- Defined this file as the future history record for Python backend/API routing and scope changes

---

> **Design:** [../design/python-backend-expert.design.md](../design/python-backend-expert.design.md)
