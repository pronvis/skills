# skills

Agent skills for the omp (Oh My Pi) coding agent, vendored from [cursor/plugins@7314f72](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166) and ported from Cursor to omp conventions.

`skills/` holds the skill packs. `agents/` holds omp task-agent definitions, symlinked into `~/.omp/agent/agents/`. Register the pack by adding `skills.customDirectories: [/Users/pronvis/it/skills/skills]` to `~/.omp/agent/config.yml`.

A ✱ marks a skill whose text was rewritten for omp: Cursor tool names, model slugs, `.cursor/rules` paths, and Cursor-only built-in skills were replaced. Unmarked skills are byte-identical to upstream.

Most skills carry `disable-model-invocation: true` upstream, so the model will not auto-select them; invoke with `/skill:<name>` or read `skill://<name>`. The 5 auto-selectable ones are marked ●.


## Entry point

| Skill | Purpose | Source |
|---|---|---|
| `poteto-mode` ✱ | poteto's agent style for concise, detailed responses, deliberate subagents, unslopped prose, simple code, and verified work. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/poteto-mode/SKILL.md) |

## Workflow

| Skill | Purpose | Source |
|---|---|---|
| `architect` ✱ | Sketch types, signatures, and module structure before code, then stay in the loop while implementation fills in. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/architect/SKILL.md) |
| `arena` ✱ | Spawn N parallel candidates at the same task, pick a base, graft the strongest parts of the losers into it. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/arena/SKILL.md) |
| `figure-it-out` | Design an auditable playbook when no narrower one fits: a large migration, an ambitious multi-part change, or work a human reviews after stepping… | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/figure-it-out/SKILL.md) |
| `how` ✱ | Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\",… | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/how/SKILL.md) |
| `interrogate` ✱ | Use for \"interrogate\", \"adversarial review\", \"multi-model review\", \"challenge this\", \"stress test this code\", \"find blind spots\", or… | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/interrogate/SKILL.md) |
| `no-comments` ✱ | Spawn Comment Sicko, fix accepted findings, and offer encodings for claimed constraints. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/no-comments/SKILL.md) |
| `reflect` ✱ | Spawn three parallel review subagents over the active transcript, surface learnings, and route each to a concrete edit on an existing skill. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/reflect/SKILL.md) |
| `setup-pstack` ✱● | Configure which models pstack uses per role. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/setup-pstack/SKILL.md) |
| `show-me-your-work` | Keep a reviewable decision trail for long-running or unattended work: a TSV log with one row per decision (what, why, evidence, result). | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/show-me-your-work/SKILL.md) |
| `swarm` ✱ | Fan out N parallel workers, drain them, and return one report. Use for /swarm, 'swarm this', or parallel coverage, races, gauntlets, and exploration. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/swarm/SKILL.md) |
| `technical-writing` | Layered technical-writing standard: Diátaxis structure, Google developer style sentences, STE instruction rules, Global English syntax. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/technical-writing/SKILL.md) |
| `unslop` | Cut AI tells from any writing. Must always apply. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/unslop/SKILL.md) |
| `why` ✱ | Use for 'why does X work this way', 'why we picked Y', design rationale, regressions, postmortems, or data-backed thresholds. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/why/SKILL.md) |
| `pstack-tdd` | Use only when the user explicitly asks for TDD, a failing test, or a regression test, OR when the bug has an obvious cheap local test target. (upstream `tdd`) | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/tdd/SKILL.md) |
| `typescript-best-practices` | TypeScript best practices. Use when reading or editing any .ts or .tsx file. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/typescript-best-practices/SKILL.md) |

## Verification

| Skill | Purpose | Source |
|---|---|---|
| `control-cli` ● | Build or adapt a local harness to drive, inspect, and profile an interactive CLI or TUI without external services. | [cursor-team-kit](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/control-cli/SKILL.md) |
| `control-ui` ● | Build or adapt a local browser/CDP harness to drive and inspect a web, IDE, or Electron UI. | [cursor-team-kit](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/control-ui/SKILL.md) |
| `verify-this` ● | Verify a claim with fresh local evidence: restate it falsifiably, capture baseline and treatment, compare artifacts, and return VERIFIED, NOT… | [cursor-team-kit](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/verify-this/SKILL.md) |
| `create-verification-skill` | Generate a project-local verification skill that drives your app the way a user does — any language, framework, or platform. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/create-verification-skill/SKILL.md) |
| `maintain-verification-skill` | Periodic pass that keeps a project's verification skill and feature map honest: parallel source readers per feature, one live session driving every… | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/maintain-verification-skill/SKILL.md) |
| `deslop` ● | Remove AI-generated code slop and clean up code style | [cursor-team-kit](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/deslop/SKILL.md) |

## Principles

| Skill | Purpose | Source |
|---|---|---|
| `principle-boundary-discipline` | Apply when wiring validation, error handling, or framework adapters. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-boundary-discipline/SKILL.md) |
| `principle-build-the-lever` | Apply to any non-trivial work, not just bulk work: edits, migrations, analyses, checks. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-build-the-lever/SKILL.md) |
| `principle-encode-lessons-in-structure` | Apply when you catch yourself writing the same instruction a second time, or notice a recurring correction. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-encode-lessons-in-structure/SKILL.md) |
| `principle-exhaust-the-design-space` | Apply when facing a novel UI interaction or architectural decision with no precedent in the codebase. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-exhaust-the-design-space/SKILL.md) |
| `principle-experience-first` | Apply when product, UX, or feature-scope tradeoffs come up. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-experience-first/SKILL.md) |
| `principle-fix-root-causes` | Apply when debugging. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-fix-root-causes/SKILL.md) |
| `principle-foundational-thinking` | Apply before writing logic: choosing core types and data structures, sequencing scaffold-vs-feature work, asking what concurrent actors share. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-foundational-thinking/SKILL.md) |
| `principle-guard-the-context-window` | Apply when context is filling up: large outputs, long files, repeated reads, fan-out planning. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-guard-the-context-window/SKILL.md) |
| `principle-laziness-protocol` | Apply when refactoring, evaluating diff size, or tempted to add abstractions, layers, or signal threading. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-laziness-protocol/SKILL.md) |
| `principle-make-operations-idempotent` | Apply when designing commands, lifecycle steps, or processing loops that run amid crashes, restarts, and retries. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-make-operations-idempotent/SKILL.md) |
| `principle-migrate-callers-then-delete-legacy-apis` | Apply when introducing a new internal API while old callers still exist. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-migrate-callers-then-delete-legacy-apis/SKILL.md) |
| `principle-minimize-reader-load` | Apply when reviewing or shaping code that's hard to trace. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-minimize-reader-load/SKILL.md) |
| `principle-model-the-domain` | Apply when writing stateful logic, or when code branches a lot or repeats a shape assumption across files. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-model-the-domain/SKILL.md) |
| `principle-never-block-on-the-human` | Apply when tempted to ask 'should I do X?' on reversible work. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-never-block-on-the-human/SKILL.md) |
| `principle-outcome-oriented-execution` | Apply during planned rewrites and migrations with explicit phase boundaries. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-outcome-oriented-execution/SKILL.md) |
| `principle-prove-it-works` | Apply after completing a task, before declaring done. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-prove-it-works/SKILL.md) |
| `principle-redesign-from-first-principles` | Apply when integrating a new requirement into an existing design. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-redesign-from-first-principles/SKILL.md) |
| `principle-separate-before-serializing-shared-state` | Apply when concurrent actors might write to the same file, branch, key, or state object. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-separate-before-serializing-shared-state/SKILL.md) |
| `principle-sequence-verifiable-units` | Apply to multi-step work (sweeps, migrations, runs of similar edits) and to how you stack commits and PRs. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-sequence-verifiable-units/SKILL.md) |
| `principle-subtract-before-you-add` | Apply when sequencing an addition, refactor, or rewrite. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-subtract-before-you-add/SKILL.md) |
| `principle-type-system-discipline` | Apply when designing types, reviewing a function signature, or writing code in any statically-typed language. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-type-system-discipline/SKILL.md) |

## Task agents

omp resolves a subagent's model by agent name, so each panel seat is its own definition. `@opus`, `@gpt-sol` and `@fable` are role aliases from `modelRoles` in `~/.omp/agent/config.yml`.

| Agent | Model | Role | Source |
|---|---|---|---|
| `poteto-agent` | `@fable` | Routing target for poteto-mode work; autoloads the `poteto-mode` skill and may spawn delegates. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/agents/poteto-agent.md) |
| `comment-sicko` | `@opus` | Comment Sicko. Read-only hunt for narrating comments and workaround prose in a diff. | [pstack](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/agents/comment-sicko.md) |
| `poteto-critic-opus` | `@opus` | Read-only critic panel seat. | original |
| `poteto-critic-gpt` | `@gpt-sol` | Read-only critic panel seat. | original |
| `poteto-critic-fable` | `@fable` | Read-only critic panel seat. | original |
| `poteto-runner-opus` | `@opus` | Writing runner panel seat for arena and architect bakeoffs. | original |
| `poteto-runner-gpt` | `@gpt-sol` | Writing runner panel seat for arena and architect bakeoffs. | original |
| `poteto-runner-fable` | `@fable` | Writing runner panel seat for arena and architect bakeoffs. | original |

## Ports applied

| Cursor | omp |
|---|---|
| `subagent_type: "X"` | `task` item with `agent: "X"` |
| `run_in_background: true` | dropped; `task` items are background and auto-deliver |
| `AskQuestion`, `Task`, todolist | `ask`, `task`, `todo` |
| `readonly: true` | a read-only agent type (`scout`, `poteto-critic-*`) |
| `grok-4.6-fast-xhigh` | `@sonnet` |
| `claude-fable-5-1-thinking-max` | `@fable` |
| `~/.cursor/rules/pstack-models.mdc` | `~/.omp/agent/config.yml` (`task.agentModelOverrides`, `modelRoles`) |
| `create-skill` | the `writing-for-agents` skill |
| `/loop`, `/goal` | an autonomous-run request; a goal file plus the `todo` list |
| cloud agents, Cursor dashboard | local `task` items; `hub list` / `hub jobs`; `~/.omp/agent/sessions/` |
| `git show origin/main:pstack/skills/…` | `skill://<name>` |
| `.cursor/worktrees` | `omp worktree list --json` |

