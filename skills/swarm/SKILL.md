---
name: swarm
description: "Fan out N parallel workers, drain them, and return one report. Use for /swarm, 'swarm this', or parallel coverage, races, gauntlets, and exploration."
disable-model-invocation: true
---

# Swarm

Fan out N parallel workers. They may cover separate slices, race the same brief, or mix both. The parent waits, aggregates, and returns one report.

## Start

Open a `todo` list with one entry per phase before launching anything.

1. Frame
2. Fan out
3. Aggregate
4. Report

## Phase A: Frame

1. State the done predicate and the artifact or report the swarm must return.
2. Choose the shape. Partition into slices, race N workers on identical briefs, or mix both. For a race or mixed shape, declare `first pass`, `rank all`, or `best-of` before spawning.
3. Set N from the user or derive it from the shape. N is total workers, not the concurrency cap (omp runs at most 32 subagents at once; the rest queue).
4. Pick the worker agent. Default to `agent: "task"` unless the brief needs otherwise; a `task` item cannot carry a model, it is resolved per agent name via `task.agentModelOverrides` in `~/.omp/agent/config.yml`, then the agent's frontmatter `model:`. For a model race, name each arm's agent up front.
5. Give each worker its own writable output when it writes. Use a worktree, branch, or `/tmp/swarm-<slug>/worker-<n>/`.

## Phase B: Fan out

Spawn all N workers as `task` items in one batch with `agent` set to the chosen worker agent (a `task` item cannot carry a model). They run in the background and auto-deliver results.

When a worker must start from a non-default pushed branch, name the base branch in its brief, and when workers must not share a checkout, spawn them with `agent(..., isolated=True)` from the eval tool or give each a pre-made worktree (`omp worktree`).

Every brief stands alone. Include the goal, scope, exact slice or race arm, how to verify, and what to report. Reports use `PASS`, `ISSUES`, or `BLOCKED` with evidence.

If a worker drops out, proceed with N-1 and note it.

## Phase C: Aggregate

Read the terminal results. For coverage, every required slice needs a result. For a race, apply the selection rule declared up front. Use first pass, rank all, or best-of. Do not paste raw worker dumps.

Keep a compact result table, one-line evidenced issues, and explicit gaps or dropouts.

## Phase D: Report

Return one consolidated in-chat report with the table, issue one-liners, gaps or dropouts, and the race rule when used.
