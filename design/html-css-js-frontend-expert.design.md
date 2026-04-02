# HTML CSS JS Frontend Expert Design

> **Current Version:** 0.2.0
> **Last Updated:** 2026-03-30
> **Status:** Active - Policy Clarified
> **Full history:** [../changelog/html-css-js-frontend-expert.changelog.md](../changelog/html-css-js-frontend-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/html-css-js-frontend-expert.md`
> **Runtime Target:** `<user-runtime-agents>/html-css-js-frontend-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `html-css-js-frontend-expert`.

This agent should remain the web-platform / vanilla frontend specialist, clearly separated from React/framework-specific frontend architecture.

---

## 2. Ownership Boundary

### 2.1 Owns

- semantic HTML and accessibility structure
- CSS layout, cascade, responsiveness, animations
- browser APIs, DOM/event handling, vanilla JS interaction
- cross-browser issues and browser-platform performance

### 2.2 Defers

- React/Next/Vite framework frontend work -> `react-frontend-expert`
- backend concerns -> backend expert agents
- runtime/tooling issues outside browser behavior -> runtime experts

### 2.3 Not for

- React component/state architecture
- hydration or framework rendering issues
- backend/API architecture

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- semantic HTML
- CSS layout/cascade/responsiveness
- browser APIs and vanilla DOM behavior
- accessibility and cross-browser issues

### 3.2 Common trigger examples

- CSS Grid/Flexbox overflow or layout bugs
- ARIA/semantic markup fixes
- vanilla JS modal/dropdown behavior
- cross-browser rendering or browser API problems

### 3.3 Common misroute risks

- React frontend prompts routing here instead of `react-frontend-expert`
- backend/browser-adjacent prompts being treated as UI-only issues

---

## 4. Prompt Structure Contract

Preferred body sections in the runtime agent file:
- `## Owns`
- `## Defers`
- `## Not for`
- `## Core Principles`
- `## Workflow`
- `## Verification Requirements`
- `## Output`

---

## 5. Validation Targets

The agent is working as intended when:
- pure browser/platform prompts route here first or remain clearly browser-platform-aligned when handled by the main assistant
- React framework prompts do not route here by default
- the agent clearly defers React-specific work when needed

### 5.1 Current validation signal

Current workspace evidence shows:
- browser-platform prompts remained domain-aligned
- explicit specialist delegation was not always observed for browser/UI prompt shapes
- there is not yet evidence strong enough to justify more routing tuning by default

### 5.2 Current operator policy

For this environment:
- browser-platform prompts may remain acceptable under domain-aligned main-assistant handling
- the important boundary is that semantic HTML / CSS / browser-platform reasoning should not drift into React-specific architecture by default
- explicit invocation remains available when specialist behavior is important

---

## 6. Planned Future Refinements

- refine accessibility-vs-framework overlap only if practical usage keeps showing operator confusion
- revisit routing pressure later only if browser-platform prompts start drifting materially into the wrong specialist domain

---

> **Design anchor:** browser platform first, framework frontend by deferral.