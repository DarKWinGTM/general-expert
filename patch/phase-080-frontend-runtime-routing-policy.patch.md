# Phase 080 Frontend and Runtime Routing Policy Patch

## 0) Document Control

> **Current Version:** 1.0
> **Status:** Implemented
> **Target Design:** [../design/design.md](../design/design.md) v0.2.0
> **Target Phase:** [../phase/phase-080-routing-policy-closure.md](../phase/phase-080-routing-policy-closure.md)
> **Session:** 599bf14e-665e-4915-a64a-535b73bed417
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch closes the current operator policy surface for:
- Bun runtime prompts
- browser-platform prompts
- broader React prompt families

Why this patch matters:
- these domains remained open questions in TODO after the first validation wave
- the workspace needed explicit operator guidance instead of carrying indefinite “decide later” wording

---

## 2) Analysis

Risk level: Low

Dependencies:
- `../design/bun-expert.design.md`
- `../design/html-css-js-frontend-expert.design.md`
- `../design/react-frontend-expert.design.md`
- `../TODO.md`
- `../README.md`

Review concern:
- policy closure should not exaggerate explicit specialist reliability where the evidence only supports domain-aligned handling

---

## 3) Change Items

### Change Item 1
- **Target location:** Bun runtime operator policy
- **Change type:** replacement

**Before**
```text
TODO still asked whether Bun runtime prompts should be pushed toward explicit specialist delegation.
```

**After**
```text
Current policy: Bun runtime prompts may remain acceptable under domain-aligned main-assistant handling as long as reasoning stays inside Bun runtime/tooling scope and does not drift into Bun backend service design.
```

### Change Item 2
- **Target location:** browser-platform operator policy
- **Change type:** replacement

**Before**
```text
TODO still asked whether browser UI prompts should be pushed toward explicit specialist delegation.
```

**After**
```text
Current policy: browser-platform prompts may remain acceptable under domain-aligned main-assistant handling as long as reasoning stays inside semantic HTML / CSS / browser-platform scope and does not drift into React-specific architecture.
```

### Change Item 3
- **Target location:** React operator policy
- **Change type:** replacement

**Before**
```text
TODO still asked whether react-frontend-expert should be tuned further after the direct hydration prompt success case.
```

**After**
```text
Current policy:
- direct hydration-debug work remains a clear explicit react-frontend-expert win
- broader React prompt families do not need further tuning right now if handling remains React/domain-aligned
- explicit invocation remains available when specialist behavior matters
```

---

## 4) Verification

- [ ] Confirm TODO no longer carries Bun/browser/React as unresolved operator-policy decisions for the current wave
- [ ] Confirm the affected design/changelog files now reflect explicit policy rather than open-ended review language
- [ ] Confirm React hydration-debug remains recorded as an explicit validated win
- [ ] Confirm this patch does not overstate explicit routing where only domain-aligned handling was evidenced

---

## 5) Rollback Approach

If later evidence shows stronger need for explicit delegation in these domains:
- preserve this policy as the historical baseline
- create a new patch-backed policy revision
- do not silently re-open the decision surface without evidence
