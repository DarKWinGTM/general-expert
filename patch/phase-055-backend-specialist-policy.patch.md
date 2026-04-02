# Phase 055 Backend Specialist Policy Patch

## 0) Document Control

> **Current Version:** 1.0
> **Status:** Backend policy closure recorded
> **Target Design:** [../design/design.md](../design/design.md) v0.2.0
> **Target Phase:** [../phase/phase-050-validation.md](../phase/phase-050-validation.md)
> **Session:** 599bf14e-665e-4915-a64a-535b73bed417
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch captures the policy transition for the backend specialist agents:
- `nodejs-backend-expert`
- `python-backend-expert`

Why this patch matters:
- the original expectation still leaned toward delegation-first specialist behavior
- repeated validation did not support that expectation strongly enough in this environment
- the workspace needed an explicit operator policy instead of open-ended further tuning

---

## 2) Analysis

Risk level: Medium

Dependencies:
- `../design/nodejs-backend-expert.design.md`
- `../design/python-backend-expert.design.md`
- `../changelog/nodejs-backend-expert.changelog.md`
- `../changelog/python-backend-expert.changelog.md`
- `../phase/phase-050-validation.md`

Review concern:
- the policy should not erase the domain value of the backend specialists
- it should only stop over-claiming auto-routing reliability for broad backend prompts in this environment

---

## 3) Change Items

### Change Item 1
- **Target location:** backend specialist operator model
- **Change type:** replacement

**Before**
```text
Node/Python backend specialists were still implicitly treated like normal delegation-first specialists that should be made to auto-route with stronger wording.
```

**After**
```text
Node/Python backend specialists are now governed as explicit-invocation-oriented specialists for this environment.
Explicit invocation and attached target files are the preferred reliable usage model when specialist behavior matters.
```

### Change Item 2
- **Target location:** validation interpretation for backend specialists
- **Change type:** additive

**Before**
```text
Validation gaps were still framed mainly as more description-tuning work.
```

**After**
```text
Validation now supports this completed policy decision:
- explicit routing for broad architecture-heavy prompts is not reliably specialist-first
- domain alignment still exists in many cases
- explicit invocation is the reliable specialist path
```

### Change Item 3
- **Target location:** artifact-role boundary for backend routing closure
- **Change type:** replacement

**Before**
```text
Open-decision material remained spread across changelog-style history and follow-up notes.
```

**After**
```text
Backend specialist policy is now treated as a completed governance decision.
Open-ended “should we keep tuning?” framing is replaced by explicit operator guidance.
```

---

## 4) Verification

- [ ] Confirm the master design states explicit invocation as the preferred backend-specialist model
- [ ] Confirm `nodejs-backend-expert` and `python-backend-expert` artifacts no longer treat the current policy as unresolved
- [ ] Confirm this patch reads as a policy transition rather than just another tuning note
- [ ] Confirm the policy remains scoped to this environment only

---

## 5) Rollback Approach

If later evidence shows materially stronger auto-routing for these backend specialists:
- keep the recorded validation history
- supersede this policy with a new patch-backed routing-policy revision
- do not silently erase the current environment-specific conclusion
