---
name: setup-pstack
description: Configure which models pstack uses per role. Detects your available models and writes the role aliases and agent overrides into omp's config that override the skill defaults. Use for /setup-pstack, "configure pstack models", or changing pstack's model choices.
---

# Setup pstack

Write pstack's per-role model choices into `~/.omp/agent/config.yml`: `modelRoles` maps each role alias (`opus`, `fable`, `sonnet`, `gpt-sol`) to a concrete model selector, and `task.agentModelOverrides` maps each agent pstack dispatches to an `@role` alias. The skills name the aliases inline and an agent with no override falls back to its own frontmatter `model:` and then to the parent chat model, so this is an override layer, not a requirement.

## Steps

### 1. Detect available models

Run `omp models --json`; the `selector` field of each entry (`provider/model`) is the value form `modelRoles` takes, optionally with a `:level` suffix drawn from that entry's `thinking` list. That is the dependable source. The catalog lists every provider omp knows, including ones without credentials, so treat the providers the current `modelRoles` already use as the entitled set and confirm with the user before choosing a selector from any other provider. If the command fails, ask the user to paste the selectors they have access to. Never write a selector you have not confirmed is available. An absent override is always valid: an agent with no `task.agentModelOverrides` entry and no frontmatter `model:` runs on the parent chat model, which is omp's equivalent of `inherit-parent` / `auto`.

### 2. Load current state

The default role-to-alias and agent-to-alias mapping is the shape shown in step 5 below. Read `~/.omp/agent/config.yml` and treat its existing `modelRoles` and `task.agentModelOverrides` values as the current choices. Roles or agents absent from the file take the defaults.

### 3. Map and confirm

Show every pstack role with the alias it rides and every alias with its current selector, marking any selector not in the detected set as needing a choice. Ask whether to accept as-is or change specific aliases or agent overrides, offering the detected selectors plus "no override" (the role runs on the parent chat model) as the options. Prefer the `ask` tool over free text. For panel roles (how critics, arena runners, architect runners, interrogate reviewers) the value is a list of agents, one subagent per entry, so the list length sets the count: critics and interrogate reviewers dispatch `poteto-critic-opus`, `poteto-critic-gpt`, `poteto-critic-fable`; arena and architect runners dispatch `poteto-runner-opus`, `poteto-runner-gpt`, `poteto-runner-fable`. Only two model families are available (anthropic and openai), so two panel entries share a family. `arena cross-judge pool` is the critic list, but Arena selects one `poteto-critic-*` from it whose model family differs from the winning runner's when possible. `swarm workers` is the default model for every worker unless a race or comparison assigns another model per arm. A `task` item cannot carry a model, so a pstack role is served by dispatching the agent whose configured alias matches the tier; changing an alias's selector changes every role that rides it.

### 4. Validate

Every selector written must be in the detected set, with any `:level` suffix present in that model's `thinking` list; "no override" always passes. If a chosen selector is not available, stop and ask again. A role pointing at a model the user cannot use breaks every delegation that reads it.

### 5. Write the config

Edit `~/.omp/agent/config.yml` in place, touching only the `modelRoles.<alias>` and `task.agentModelOverrides.<agent>` keys you are setting: update a key that exists, insert one that does not, and leave every other key, comment, and ordering untouched (the file also holds `statusLine`, `theme`, `extensions`, and more). Never rewrite the whole file. Re-runs converge on the same keys, so the edit stays idempotent. Shape:

```yaml
# pstack per-role model choices (overrides skill defaults). Remove an agent override to run it on the parent chat model.
modelRoles:
  opus: anthropic/claude-opus-5:high
  fable: anthropic/claude-fable-5-1:high
  sonnet: anthropic/claude-sonnet-5:high
  gpt-sol: openai-codex/gpt-5.6-sol:high
task:
  agentModelOverrides:
    task: "@gpt-sol"
    sonic: "@sonnet"
    scout: "@sonnet"
    poteto-agent: "@fable"
    comment-sicko: "@opus"
    reviewer: "@fable"
    fixer: "@gpt-sol"
    poteto-critic-opus: "@opus"
    poteto-critic-gpt: "@gpt-sol"
    poteto-critic-fable: "@fable"
    poteto-runner-opus: "@opus"
    poteto-runner-gpt: "@gpt-sol"
    poteto-runner-fable: "@fable"
```

Role-to-alias defaults the skills use, one line per role. `feature, refactoring: @gpt-sol`; `bug-fix: @fable`; `perf-issue: @fable`; `hillclimb: @fable`; `judgment and prose: @fable`; `hardest tasks: @fable`; `how explorer: @sonnet`; `how explainer: @fable`; `how critics: @opus, @gpt-sol, @fable`; `why investigators: @sonnet`; `why synthesizer: @fable`; `reflect tooling: @gpt-sol`; `reflect judgment, divergent, synthesizer: @fable`; `arena runners: @opus, @gpt-sol, @fable`; `arena cross-judge pool: @opus, @gpt-sol, @fable`; `swarm workers: @sonnet`; `architect runners: @opus, @gpt-sol, @fable`; `interrogate reviewers: @opus, @gpt-sol, @fable`.

### 6. Confirm

Tell the user the config was written and that task and eval preflight reload it, so new delegations pick it up without restarting; `/model`'s Roles view shows the same mapping. Re-running this skill updates it.

### 7. Offer a verification skill (optional)

Check whether the project has a way to drive the real app for proof (a `verify-*` skill, or an existing harness). If not, offer once: "want a project-local verification skill, so agents can drive the app the way a user does and prove changes work? I can generate one with /create-verification-skill." On yes, invoke `/create-verification-skill` (resolves wherever pstack is installed — project, user, or the vendored `~/it/skills` root). On no, move on without pushing.
