# Python Backend Expert Design

> **Current Version:** 0.2.0
> **Last Updated:** 2026-03-28
> **Status:** Draft - Validation Review Active
> **Full history:** [../changelog/python-backend-expert.changelog.md](../changelog/python-backend-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/python-backend-expert.md`
> **Runtime Target:** `<user-runtime-agents>/python-backend-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `python-backend-expert`.

This agent should remain the Python backend/API specialist and should not drift into generic Python scripting, notebooks, or ML/data-science work.

---

## 2. Ownership Boundary

### 2.1 Owns

- FastAPI, Django, Flask backend service design
- auth, database integration, async/background jobs
- API architecture, deployment, observability, backend testing
- backend security and operational hardening for Python services

### 2.2 Defers

- notebooks, data science, ML experimentation, non-backend Python analysis
- frontend work -> frontend expert agents
- Node/Bun backend work -> corresponding expert agents

### 2.3 Not for

- generic Python scripting with no backend service context
- package recommendations without verification
- cross-project conclusions from limited local non-findings

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- FastAPI/Django/Flask backend services
- auth/database/API/backend deployment work
- Python async jobs and backend performance

### 3.2 Common trigger examples

- build a FastAPI auth service with SQLAlchemy
- review Django backend architecture
- add background jobs and caching to a Flask API
- ออกแบบ backend Python / FastAPI / Django / Flask
- review ระบบหลังบ้าน Python + auth + database
- แก้ async job, worker, ORM, หรือ API ฝั่ง Python

### 3.2A Multilingual routing rule

Multilingual prompt support should live in the runtime file `description` line through intent-oriented routing language rather than hard-coded language-specific alias lists.
The body should remain English.

### 3.3 Common misroute risks

- generic Python workflow prompts routing here without backend context
- backend prompts for Node/Bun stacks routing here by mistake

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
- Python backend/API prompts route here first
- non-backend Python prompts do not route here by default
- the agent clearly stays inside backend-service scope

### 5.1 Current validation result

First validation matrix status:
- implementation-oriented FastAPI prompt was intercepted by generic plan-mode flow rather than explicitly delegating to `python-backend-expert`

### 5.2 Open decision

Still to decide:
- whether this should be treated as a routing problem that needs stronger description tuning
- or whether plan-mode interception is acceptable for this class of implementation prompt

### 5.3 Interim correction applied

Applied in the governed source/runtime files:
- expanded line-3 routing language to emphasize backend architecture and API implementation prompts explicitly
- added stronger directive wording: "Use this agent specifically" and "Prefer this agent when the user asks how to build, structure, or review a Python backend"
- validation still needs to confirm whether this is enough to beat generic plan-mode interception

### 5.4 Second validation result

Second validation matrix status:
- the FastAPI implementation prompt still did **not** explicitly trigger `python-backend-expert`
- the rerun continued through generic plan-mode exploration and clarification instead of explicit specialist delegation
- current conclusion: line-3 tightening alone is still insufficient to beat plan-mode interception for this implementation-heavy prompt class

### 5.5 Narrow validation matrix v2 result

Round-two classification for `python-backend-expert`:
- **FAIL (explicit routing):** P2-v2 and P5-v2 remained main-assistant direct handling instead of explicit specialist delegation
- **PASS (domain alignment only):** P2-v2 and P5-v2 still stayed inside FastAPI/SQLAlchemy/ARQ backend reasoning rather than drifting to unrelated specialists
- **INCONCLUSIVE:** P1-v2 assumed a FastAPI OAuth callback flow that was not present in the checked FastAPI scope, so it remained a target-existence mismatch rather than a clean routing test

### 5.6 Current conclusion

For this environment, `python-backend-expert` is currently better understood as a governed specialist definition that may still require explicit invocation or attached target files for reliable use. The main assistant often handles backend review/debug prompts directly even when the prompt is self-contained.

---

## 6. Usage Guidance

### 6.1 Best current usage model

For this environment, `python-backend-expert` performs best when used as an **explicit-invocation-oriented specialist** rather than a delegation-first auto-routed specialist.

### 6.2 Preferred prompting shape

Use this agent most intentionally when:
- you explicitly invoke `python-backend-expert`
- you attach concrete file paths or pasted backend code/design snippets
- the task is framed as **review**, **debug**, or **refactor** rather than broad architecture planning

Avoid assuming that broad natural-language planning prompts will auto-route here reliably.

### 6.3 Copy-paste prompt templates

#### Template 1 — OAuth callback review
```text
Use python-backend-expert to review this FastAPI OAuth callback flow.

Target files:
- /path/oauth.py
- /path/routes/oauth.py

Focus on:
- state validation
- CSRF protection
- redirect_uri consistency
- token exchange safety
- issuer/audience verification
```

#### Template 2 — session lifecycle debug
```text
Use python-backend-expert to debug this FastAPI async SQLAlchemy session lifecycle issue.

Target files:
- /path/db.py
- /path/deps.py
- /path/routes/users.py

Focus on:
- dependency yield pattern
- AsyncSession cleanup
- transaction boundary
- session reuse across requests
```

#### Template 3 — background job debug
```text
Use python-backend-expert to debug this FastAPI background job flow.

Target files:
- /path/worker.py
- /path/jobs.py
- /path/main.py

Focus on:
- retry policy
- enqueue semantics
- idempotency
- duplicate execution guards
```

#### Template 4 — backend refactor
```text
Use python-backend-expert to refactor this Python backend service boundary.

Target files:
- /path/routes.py
- /path/service.py
- /path/repository.py

Focus on:
- route vs service separation
- transaction ownership
- database access consistency
```

#### Template 5 — focused debug
```text
Use python-backend-expert to debug this Python backend issue.

Target files:
- /path/file1
- /path/file2

Focus on:
- exact failure mode
- likely root cause
- minimal safe fix
- regression risk
```

## 7. Planned Future Refinements

- refine async/background-job emphasis after prompt validation
- replace ambiguous narrow-matrix prompts with self-contained review/debug prompts for explicit-routing validation
- decide later whether a separate Python runtime/tooling expert is needed

## 8. Narrow Backend Validation Matrix v2

### Python backend-focused prompts

- **P1-v2**
  - `Review a FastAPI OAuth callback flow for security and correctness. Focus on state validation, CSRF protection, code reuse prevention, redirect_uri consistency, token exchange safety, cookie/session flags, and issuer/audience verification.`
- **P2-v2**
  - `Debug an async SQLAlchemy session lifecycle issue in FastAPI. Focus on dependency-yield patterns, AsyncSession cleanup, transaction boundaries, session reuse across requests, and engine/sessionmaker mistakes.`
- **P5-v2**
  - `Debug a FastAPI background job flow using ARQ + Redis. Jobs retry twice unexpectedly. Focus on worker settings, retry policy, enqueue semantics, job idempotency, and duplicate execution guards.`

### Success criterion

These prompts should be self-contained enough to test backend-specialist routing directly without requiring a pre-identified callback file, session file, or ARQ artifact path in the workspace.

---

> **Design anchor:** Python backend/API first, generic Python workflows by deferral.
