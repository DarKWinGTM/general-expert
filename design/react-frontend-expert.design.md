# React Frontend Expert Design

> **Current Version:** 0.2.0
> **Last Updated:** 2026-03-30
> **Status:** Active - Policy Clarified
> **Full history:** [../changelog/react-frontend-expert.changelog.md](../changelog/react-frontend-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/react-frontend-expert.md`
> **Runtime Target:** `<user-runtime-agents>/react-frontend-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `react-frontend-expert`.

This agent should own React framework frontend work, especially TSX, hooks, state flow, hydration, and Next.js App Router patterns.

---

## 2. Ownership Boundary

### 2.1 Owns

- React and TSX component architecture
- hooks, state management, rendering behavior, testing
- forms, routing, hydration, performance
- Next.js App Router boundaries, layouts, route segments, loading/error states, RSC interaction
- React-centric Vite/Next application patterns

### 2.2 Defers

- pure browser-platform / semantic HTML / CSS / vanilla DOM issues -> `html-css-js-frontend-expert`
- backend/API/server architecture -> backend expert agents
- runtime/tooling issues that are not specifically React-app problems -> runtime experts

### 2.3 Not for

- framework-free frontend work
- pure browser support questions without React integration
- backend system architecture

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- React hooks/state/TSX
- hydration issues
- Next.js App Router
- rendering/performance in React apps
- Vite/Next frontend architecture

### 3.2 Common trigger examples

- Next.js App Router hydration mismatch
- refactor React hooks to reduce re-renders
- state flow and component boundary issues
- TSX component architecture questions

### 3.3 Common misroute risks

- browser-platform prompts routing here instead of `html-css-js-frontend-expert`
- backend questions embedded in React UI flows routing here by mistake

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
- React/Next/Vite prompts route here first or remain clearly React/domain-aligned when handled by the main assistant
- pure HTML/CSS/browser prompts do not route here by default
- the agent clearly defers browser-platform-only issues to `html-css-js-frontend-expert`

### 5.1 Current validation signal

Current workspace evidence shows:
- direct Next.js App Router hydration-debug work is a clear explicit specialist win for `react-frontend-expert`
- broader React prompt families have remained domain-aligned even when explicit specialist delegation was not always observed

### 5.2 Current operator policy

For this environment:
- no additional routing tuning is required right now beyond the direct hydration-debug success already observed
- broader React prompt families may remain acceptable under domain-aligned handling as long as reasoning stays clearly inside React/framework scope
- explicit invocation remains available when specialist behavior is important

---

## 6. Planned Future Refinements

- revisit state-library wording later only if practical usage shows repeated routing ambiguity
- consider deeper routing refinement later only if broader React prompts stop remaining React/domain-aligned

---

> **Design anchor:** React/framework frontend first, browser-platform issues by deferral.