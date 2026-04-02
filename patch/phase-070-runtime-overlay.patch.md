# Phase 070 Runtime Overlay Patch

## 0) Document Control

> **Current Version:** 1.0
> **Status:** Implemented
> **Target Design:** [../design/design.md](../design/design.md) v0.2.0
> **Target Phase:** [../phase/phase-070-runtime-overlay-governance.md](../phase/phase-070-runtime-overlay-governance.md)
> **Session:** 599bf14e-665e-4915-a64a-535b73bed417
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch captures the governance decision that managed-fleet truth and live-runtime routing behavior must be interpreted separately.

Why this patch matters:
- the workspace governs 7 managed agents
- but the live runtime also contains unmanaged co-resident agents
- routing evidence should not overclaim that the managed fleet alone determines every observed runtime outcome

---

## 2) Analysis

Risk level: Low

Dependencies:
- `../design/design.md`
- `../README.md`
- `../phase/SUMMARY.md`

Review concern:
- the overlay note should improve evidence honesty without weakening source-of-truth ownership for the managed fleet itself

---

## 3) Change Items

### Change Item 1
- **Target location:** routing-evidence interpretation model
- **Change type:** replacement

**Before**
```text
Routing evidence could be read as if the managed 7-agent fleet alone explained the live runtime behavior.
```

**After**
```text
Routing evidence is now interpreted with an explicit overlay rule:
- managed source-of-truth governs the 7 controlled agents
- observed runtime behavior may still be influenced by co-resident unmanaged agents in ~/.claude/agents/
```

### Change Item 2
- **Target location:** co-resident runtime examples
- **Change type:** additive

**Before**
```text
Unmanaged co-resident agents were not named in the workspace governance model.
```

**After**
```text
The overlay note now explicitly names notable co-resident examples such as:
- multi-hat-system.md
- prompt-optimizer.md
- generative-media-navigator.md
```

### Change Item 3
- **Target location:** workspace operator guidance
- **Change type:** additive

**Before**
```text
Operators could conflate file parity truth with full runtime-routing truth.
```

**After**
```text
Operators now get an explicit rule:
- managed-file parity can still be true
- while routing outcomes are interpreted inside a mixed live runtime
```

---

## 4) Verification

- [ ] Confirm README explains the managed-fleet vs runtime-overlay distinction
- [ ] Confirm the master design defines the overlay rule explicitly
- [ ] Confirm the summary no longer implies a clean managed-only runtime where that is not true
- [ ] Confirm the overlay note remains a scope-interpretation rule, not a source-of-truth rewrite

---

## 5) Rollback Approach

If the overlay note is judged too detailed:
- keep the distinction itself
- reduce the number of named examples if needed
- do not revert to implicit mixed-scope interpretation
