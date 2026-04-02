# Bun Backend Expert Design

> **Current Version:** 0.1.0
> **Last Updated:** 2026-03-28
> **Status:** Draft - Initial Skeleton
> **Full history:** [../changelog/bun-backend-expert.changelog.md](../changelog/bun-backend-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/bun-backend-expert.md`
> **Runtime Target:** `<user-runtime-agents>/bun-backend-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `bun-backend-expert`.

This agent should own Bun-native backend and API architecture, especially Bun.serve and Bun-first frameworks such as Hono and Elysia.

---

## 2. Ownership Boundary

### 2.1 Owns

- Bun-native backend design
- Bun.serve services
- Hono and Elysia backend patterns
- auth, DB integration, caching, background jobs, deployment on Bun

### 2.2 Defers

- pure Bun runtime/tooling/platform work -> `bun-expert`
- generic Node backend architecture -> `nodejs-backend-expert`
- frontend concerns -> frontend expert agents

### 2.3 Not for

- pure package-manager/build/test workflow issues without backend context
- browser/frontend architecture
- unverified Bun ecosystem assumptions

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- Bun.serve APIs
- Hono/Elysia services
- Bun backend auth/DB/caching/background work
- Bun production backend architecture

### 3.2 Common trigger examples

- design a Bun.serve + Hono backend with Postgres
- review an Elysia auth flow
- add caching and jobs to a Bun API service

### 3.3 Common misroute risks

- Bun tooling prompts routing here instead of `bun-expert`
- generic Node backend prompts routing here instead of `nodejs-backend-expert`

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
- Bun-native backend/API prompts route here first
- Bun runtime/tooling prompts do not route here by default
- the agent explicitly defers low-level Bun platform/tooling blockers to `bun-expert`

---

## 6. Planned Future Refinements

- refine Hono/Elysia/Bun.serve emphasis after routing validation
- decide later whether framework-specific sub-splitting is needed

---

> **Design anchor:** Bun-native backend architecture first, Bun tooling by deferral.
