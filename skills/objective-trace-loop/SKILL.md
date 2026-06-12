---
name: objective-trace-loop
description: Use when designing, reviewing, or implementing QA/eval control loops for software, live apps, AI products, release gates, synthetic testing, production replay, trace capture, LLM judges, taste/product-quality review, or failure diagnosis. Helps Codex turn vague quality goals into objectives, probes/scenarios, traces, judges, repairs, memory updates, and ship/warn/canary/block decisions.
---

# Objective Trace Loop

## Overview

Use this skill to turn quality assurance into a control loop around an objective:

```text
Objective -> World -> Probe -> Trace -> Judge -> Repair -> Memory -> Gate
```

Keep the work practical. Start from one critical flow or failure mode, produce executable next steps, and avoid presenting the loop as a philosophy unless the user asks for theory.

## Core Objects

- Objective: what good means, including hard constraints, quality bars, and preference direction.
- System: the app, service, model, workflow, prompt, repo, or product behavior being improved.
- World: the environment the system operates inside, such as data, users, APIs, AI responses, devices, networks, time, and production state.
- Probe: a challenge to the system, such as a test, scenario, synthetic user journey, replay, fuzz case, or adversarial case.
- Trace: the full record of what happened when the system was challenged.
- Judge: the checks, metrics, rubrics, LLM judges, human review, or production metrics that score the trace against the objective.
- Repair: the decision about what to change: system, world, probe, judge, objective, deployment policy, or memory.
- Memory: stored traces, failures, fixes, examples, preferences, regressions, and release decisions.
- Gate: the release decision: ship, warn, canary, human-review, or block.

## Workflow

1. Pick the objective.
   - Select one critical flow, outcome, incident class, or product behavior.
   - Define the desired outcome, hard constraints, measurable quality bars, preference direction, and release policy.

2. Model the world.
   - Identify real conditions the system must survive: user states, data shapes, permissions, third-party APIs, model outputs, latency, device/network states, and production edge cases.
   - Start with the smallest useful world model, not a comprehensive simulation.

3. Generate probes.
   - Create happy paths, common failures, edge cases, adversarial cases, production replays, and taste/product-direction cases.
   - Treat existing tests as probes, then add missing scenario probes around observed risk.

4. Capture traces.
   - Record enough information to judge behavior: inputs, UI states, actions, API calls, AI prompts/responses, logs, errors, latency, state changes, screenshots/video if useful, and final outcome.
   - Prefer structured traces that can become future regression cases.

5. Build the judge stack.
   - Use deterministic checks first for hard correctness, contracts, schemas, privacy, security, payments, and data integrity.
   - Add metric/rubric/LLM/human judges for task success, UX quality, AI quality, safety, taste, and real-world outcomes.
   - Calibrate subjective judges with golden, bad, and ambiguous examples.

6. Diagnose failures.
   - Classify whether the failure came from code, data, dependency, AI behavior, UX, taste, objective, judge, world model, or probe design.
   - Repair the failing layer; do not always assume the application code is wrong.

7. Update memory.
   - Store traces, scores, failures, decisions, fixes, human judgments, golden examples, bad examples, and regressions.
   - Convert escaped production failures into future scenarios.

8. Gate the release.
   - Block hard failures and high-impact known-bad outcomes.
   - Warn on soft quality regressions when risk is low.
   - Canary uncertain but plausible behavior.
   - Escalate ambiguous, high-risk, or taste-sensitive cases to humans.

## Applying To A Repo Or App

- First inspect the repo's existing test, eval, CI, telemetry, logging, and fixture patterns. Fit the loop into those patterns instead of creating a parallel QA universe.
- If no structure exists, propose a minimal `qa-loop/` or `evals/` folder with objectives, scenarios, world profiles, judges, traces, memory, and gates.
- Keep the first implementation small: one objective, 5-20 scenarios, one trace format, a few deterministic judges, one subjective rubric if needed, and a simple release gate.
- Prefer runnable probes over abstract checklists. If a probe cannot be run yet, specify the harness or instrumentation needed to make it runnable.
- For frontend/live-app flows, include browser traces, screenshots, user actions, latency, network/API calls, and final visible state.
- For AI-powered flows, include AI profiles: good, mediocre, wrong, slow, empty, malformed, unsafe, and expensive. Judge schema validity, grounding, instruction following, usefulness, safety, tone, concision, cost, latency, fallback behavior, and product taste.
- For production learning, map incidents, support tickets, user complaints, session replays, analytics drop-offs, and excellent outcomes back into scenarios or judge calibration examples.

## Output Shape

When asked to design or review a loop, produce concise artifacts in this order:

1. Objective: desired outcome, hard constraints, quality bars, preference direction.
2. World model: the minimal user/data/API/AI/environment profiles needed.
3. Probe set: scenarios or tests that challenge the objective.
4. Trace plan: what to capture and where to store it.
5. Judge stack: deterministic checks, metrics, rubrics, LLM judges, and human review rules.
6. Failure taxonomy: how failures should be classified.
7. Memory update rules: what becomes a regression, golden example, bad example, or judge calibration case.
8. Release gate: ship/warn/canary/review/block rules.
9. Implementation path: the smallest concrete next steps in the codebase.

## Release Decisions

Use this default policy unless the codebase or user supplies a stricter one:

```text
Known good -> ship
Known bad -> block
Unknown low risk -> ship with warning or monitor
Unknown high risk -> canary or human review
Judge disagreement -> human review
Taste uncertainty -> product/founder review
Reality uncertainty -> limited rollout with production learning
```

Hard failures block by default: privacy violations, security regressions, data loss, payment integrity failures, permission failures, crashes in critical flows, invalid required structured output, or critical task failure.

Soft failures warn or escalate: UX friction, latency regression, mediocre AI quality, taste misalignment, confusing copy, non-critical accessibility issues, or uncertain product direction.

## Failure Diagnosis Taxonomy

Classify failed traces using these categories:

- Code failure: logic, state, UI, backend, race condition, migration, or integration bug.
- Data failure: missing, dirty, duplicate, inconsistent, malformed, or unrealistic data.
- Dependency failure: third-party API, webhook, email, payment, storage, timeout, schema drift, or outage.
- AI failure: wrong, hallucinated, unsafe, malformed, slow, expensive, ungrounded, or bad tool use.
- UX failure: confusing flow, dead end, unclear copy, poor loading state, too many steps, or missing feedback.
- Taste failure: technically works but feels generic, noisy, cheap, misaligned, overbuilt, or off-brand.
- Objective failure: goal is vague, contradictory, stale, unowned, or missing a hard constraint.
- Judge failure: judge missed a real issue, over-penalized acceptable behavior, or lacked calibration examples.
- World-model failure: synthetic/mocked world did not represent production reality.
- Probe failure: scenario did not challenge the right behavior or missed an important path.

## Memory Rules

- Every production incident becomes a scenario or regression.
- Every escaped bug becomes a regression probe.
- Every great experience becomes a golden trace.
- Every bad experience becomes a bad trace.
- Every ambiguous review becomes a labeled example.
- Every judge mistake updates judge calibration.
- Every synthetic-world miss updates the world model.
- Every user complaint becomes a probe candidate.
- Every release decision is stored with the evidence used to make it.

## References

- Read `references/templates.md` when creating concrete YAML/spec artifacts for objectives, scenarios, traces, judges, gates, or folder structure.
- Read `references/objective-trace-control-loop.md` only when the user asks for the full framework, theory, maturity model, dashboard, 30-day rollout, or a more complete explanation.
