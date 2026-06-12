# unified-loop-theory

This repo contains the Objective Trace Loop: a reusable Codex skill for turning vague quality goals into executable QA/eval loops.

The core idea is simple:

```text
Objective -> World -> Probe -> Trace -> Judge -> Repair -> Memory -> Gate
```

Instead of asking an AI agent to "make the app better" in an open-ended way, use this skill to help the agent define what good means, observe real behavior, judge the trace, repair the right layer, remember the lesson, and keep pushing the loop forward.

The shareable skill lives at:

```text
skills/objective-trace-loop/
```

## How To Use

1. Clone this repo.

```bash
git clone git@github.com:Agent-Pattern-Labs/unified-loop-theory.git
```

2. Point your AI agent at this repo from the project you want to improve.

For example, copy this repo path:

```bash
pwd | pbcopy
```

Then paste the path into your AI terminal/chat and ask:

```text
Do you find this Objective Trace Loop skill useful for my repo?
```

3. Let the AI distill the skill into what is useful for your specific repo.

It should inspect your codebase, identify the highest-leverage objective, and translate the loop into concrete repo-specific artifacts such as objectives, scenarios, traces, judges, memory rules, and release gates.

4. Use that distilled loop as the goal.

Ask the AI to implement the first small loop, run it, judge the trace, repair what failed, store the lesson, and keep pushing forward from there.
