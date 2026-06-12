# Unified Loop Theory

Unified Loop Theory is a reusable Codex skill for turning any vague goal into an operating loop.

One loop to control all loops.

The thesis:

```text
Every useful improvement loop has the same shape.
```

The loop:

```text
Objective -> World -> Probe -> Trace -> Judge -> Repair -> Memory -> Gate -> Objective
```

In plain English:

```text
Define good.
Challenge the system.
Observe what happened.
Judge the trace.
Repair the right layer.
Store the lesson.
Decide whether to ship, continue, escalate, or redefine the objective.
Repeat.
```

This repo is meant to be the master loop for other loops: QA loops, eval loops, coding-agent loops, product-improvement loops, AI-app loops, release loops, debugging loops, and taste/quality loops.

The shareable Codex skill lives at:

```text
skills/unified-loop-theory/
```

## How To Use

1. Clone this repo.

```bash
git clone git@github.com:Agent-Pattern-Labs/unified-loop-theory.git
```

2. Copy this repo path.

From inside this repo:

```bash
pwd | pbcopy
```

3. Go to the repo, app, product, or project you want to improve.

Point your AI agent at the copied path and say:

```text
Use $unified-loop-theory as the master loop for my project.

1. Inspect my repo.
2. Identify the highest-leverage objective.
3. Define the world, probes, traces, judges, memory, and gate.
4. Turn that into an explicit goal.
5. Run the first loop.
6. Judge the trace.
7. Repair what failed.
8. Store the lesson.
9. Repeat until the objective is satisfied or the loop needs a better objective.
```

4. Keep the AI inside the loop.

Do not stop at a plan. Ask the agent to execute the first probe, capture evidence, judge the result, make the next repair, and continue.

The expected output is not just an explanation. The expected output is a living loop:

```text
current objective
current world model
current probes
latest trace
latest judgment
latest repair
memory updates
next gate decision
next loop
```

## What Makes It Recursive

The loop improves the system, but it can also improve itself.

If the objective is vague, repair the objective.
If the probe is weak, repair the probe.
If the trace is incomplete, repair instrumentation.
If the judge is wrong, repair the judge.
If the world model missed reality, repair the world model.
If memory is not compounding, repair memory.
If the gate is too loose or too strict, repair the gate.

That is the unified part: every failure becomes evidence about either the system or the loop controlling the system.
