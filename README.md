# skills

Agent skills for the omp (Oh My Pi) coding agent: 70 vendored from three upstreams and ported to omp conventions, plus one authored here. This repo is the only skill source omp loads; `~/.agents/skills` is empty by design.

| Upstream | Pinned at | Skills | Path |
|---|---|---|---|
| [cursor/plugins](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166) | `7314f72` | 43 | `pstack/skills`, `cursor-team-kit/skills` |
| [mattpocock/skills](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015) | `3cca18b` | 25 | `skills/engineering`, `skills/productivity` |
| [affaan-m/ECC](https://github.com/affaan-m/ECC/blob/e04ea0b9cc8248686edf5ac751cadff550e162b8) | `e04ea0b` | 2 | `skills` |
| yours | n/a | 1 | authored in this repo |

`skills/` holds the skill packs, one directory each. `agents/` holds omp task-agent definitions, symlinked into `~/.omp/agent/agents/`. Register the pack by adding this to `~/.omp/agent/config.yml`:

```yaml
skills:
  customDirectories:
    - /Users/pronvis/it/skills/skills
```

Legend. Each skill name links to its vendored `SKILL.md`; the Source column links the upstream original. **✱** the text was rewritten for omp; unmarked skills are byte-identical to upstream. **●** the model may auto-select it; the other 51 carry upstream's `disable-model-invocation: true` and are reached with `/skill:<name>` or by reading `skill://<name>`.


## Entry point (pstack)

| Skill | Purpose | Source |
|---|---|---|
| [`poteto-mode`](skills/poteto-mode/SKILL.md) ✱ | poteto's agent style for concise, detailed responses, deliberate subagents, unslopped prose, simple code, and verified work. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/poteto-mode/SKILL.md) |

## Workflow (pstack)

| Skill | Purpose | Source |
|---|---|---|
| [`architect`](skills/architect/SKILL.md) ✱ | Sketch types, signatures, and module structure before code, then stay in the loop while implementation fills in. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/architect/SKILL.md) |
| [`arena`](skills/arena/SKILL.md) ✱ | Spawn N parallel candidates at the same task, pick a base, graft the strongest parts of the losers into it. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/arena/SKILL.md) |
| [`figure-it-out`](skills/figure-it-out/SKILL.md) | Design an auditable playbook when no narrower one fits: a large migration, an ambitious multi-part change, or work a human reviews after stepping… | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/figure-it-out/SKILL.md) |
| [`how`](skills/how/SKILL.md) ✱ | Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\",… | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/how/SKILL.md) |
| [`interrogate`](skills/interrogate/SKILL.md) ✱ | Use for \"interrogate\", \"adversarial review\", \"multi-model review\", \"challenge this\", \"stress test this code\", \"find blind spots\", or… | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/interrogate/SKILL.md) |
| [`no-comments`](skills/no-comments/SKILL.md) ✱ | Spawn Comment Sicko, fix accepted findings, and offer encodings for claimed constraints. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/no-comments/SKILL.md) |
| [`reflect`](skills/reflect/SKILL.md) ✱ | Spawn three parallel review subagents over the active transcript, surface learnings, and route each to a concrete edit on an existing skill. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/reflect/SKILL.md) |
| [`setup-pstack`](skills/setup-pstack/SKILL.md) ✱● | Configure which models pstack uses per role. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/setup-pstack/SKILL.md) |
| [`show-me-your-work`](skills/show-me-your-work/SKILL.md) | Keep a reviewable decision trail for long-running or unattended work: a TSV log with one row per decision (what, why, evidence, result). | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/show-me-your-work/SKILL.md) |
| [`swarm`](skills/swarm/SKILL.md) ✱ | Fan out N parallel workers, drain them, and return one report. Use for /swarm, 'swarm this', or parallel coverage, races, gauntlets, and exploration. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/swarm/SKILL.md) |
| [`technical-writing`](skills/technical-writing/SKILL.md) | Layered technical-writing standard: Diátaxis structure, Google developer style sentences, STE instruction rules, Global English syntax. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/technical-writing/SKILL.md) |
| [`unslop`](skills/unslop/SKILL.md) ● | Cut AI tells from text you write or edit for a human reader (commit messages, PR titles and bodies, docs, code comments, replies). Apply before committing, posting, or sending; leave prose you didn't touch alone. | [michaelshimeles](https://github.com/michaelshimeles/skills/blob/a007fcdd8a3333983b8699baa46a70188461b7d9/unslop/SKILL.md) |
| [`why`](skills/why/SKILL.md) ✱ | Use for 'why does X work this way', 'why we picked Y', design rationale, regressions, postmortems, or data-backed thresholds. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/why/SKILL.md) |
| [`pstack-tdd`](skills/pstack-tdd/SKILL.md) | Use only when the user explicitly asks for TDD, a failing test, or a regression test, OR when the bug has an obvious cheap local test target. (upstream `tdd`) | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/tdd/SKILL.md) |
| [`typescript-best-practices`](skills/typescript-best-practices/SKILL.md) | TypeScript best practices. Use when reading or editing any .ts or .tsx file. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/typescript-best-practices/SKILL.md) |

## Verification (pstack, cursor-team-kit)

| Skill | Purpose | Source |
|---|---|---|
| [`control-cli`](skills/control-cli/SKILL.md) ● | Build or adapt a local harness to drive, inspect, and profile an interactive CLI or TUI without external services. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/control-cli/SKILL.md) |
| [`control-ui`](skills/control-ui/SKILL.md) ● | Build or adapt a local browser/CDP harness to drive and inspect a web, IDE, or Electron UI. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/control-ui/SKILL.md) |
| [`verify-this`](skills/verify-this/SKILL.md) ● | Verify a claim with fresh local evidence: restate it falsifiably, capture baseline and treatment, compare artifacts, and return VERIFIED, NOT… | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/verify-this/SKILL.md) |
| [`create-verification-skill`](skills/create-verification-skill/SKILL.md) | Generate a project-local verification skill that drives your app the way a user does — any language, framework, or platform. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/create-verification-skill/SKILL.md) |
| [`maintain-verification-skill`](skills/maintain-verification-skill/SKILL.md) | Periodic pass that keeps a project's verification skill and feature map honest: parallel source readers per feature, one live session driving every… | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/maintain-verification-skill/SKILL.md) |
| [`deslop`](skills/deslop/SKILL.md) ● | Remove AI-generated code slop and clean up code style | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/cursor-team-kit/skills/deslop/SKILL.md) |

## Principles (pstack)

| Skill | Purpose | Source |
|---|---|---|
| [`principle-boundary-discipline`](skills/principle-boundary-discipline/SKILL.md) | Apply when wiring validation, error handling, or framework adapters. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-boundary-discipline/SKILL.md) |
| [`principle-build-the-lever`](skills/principle-build-the-lever/SKILL.md) | Apply to any non-trivial work, not just bulk work: edits, migrations, analyses, checks. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-build-the-lever/SKILL.md) |
| [`principle-encode-lessons-in-structure`](skills/principle-encode-lessons-in-structure/SKILL.md) | Apply when you catch yourself writing the same instruction a second time, or notice a recurring correction. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-encode-lessons-in-structure/SKILL.md) |
| [`principle-exhaust-the-design-space`](skills/principle-exhaust-the-design-space/SKILL.md) | Apply when facing a novel UI interaction or architectural decision with no precedent in the codebase. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-exhaust-the-design-space/SKILL.md) |
| [`principle-experience-first`](skills/principle-experience-first/SKILL.md) | Apply when product, UX, or feature-scope tradeoffs come up. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-experience-first/SKILL.md) |
| [`principle-fix-root-causes`](skills/principle-fix-root-causes/SKILL.md) | Apply when debugging. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-fix-root-causes/SKILL.md) |
| [`principle-foundational-thinking`](skills/principle-foundational-thinking/SKILL.md) | Apply before writing logic: choosing core types and data structures, sequencing scaffold-vs-feature work, asking what concurrent actors share. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-foundational-thinking/SKILL.md) |
| [`principle-guard-the-context-window`](skills/principle-guard-the-context-window/SKILL.md) | Apply when context is filling up: large outputs, long files, repeated reads, fan-out planning. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-guard-the-context-window/SKILL.md) |
| [`principle-laziness-protocol`](skills/principle-laziness-protocol/SKILL.md) | Apply when refactoring, evaluating diff size, or tempted to add abstractions, layers, or signal threading. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-laziness-protocol/SKILL.md) |
| [`principle-make-operations-idempotent`](skills/principle-make-operations-idempotent/SKILL.md) | Apply when designing commands, lifecycle steps, or processing loops that run amid crashes, restarts, and retries. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-make-operations-idempotent/SKILL.md) |
| [`principle-migrate-callers-then-delete-legacy-apis`](skills/principle-migrate-callers-then-delete-legacy-apis/SKILL.md) | Apply when introducing a new internal API while old callers still exist. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-migrate-callers-then-delete-legacy-apis/SKILL.md) |
| [`principle-minimize-reader-load`](skills/principle-minimize-reader-load/SKILL.md) | Apply when reviewing or shaping code that's hard to trace. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-minimize-reader-load/SKILL.md) |
| [`principle-model-the-domain`](skills/principle-model-the-domain/SKILL.md) | Apply when writing stateful logic, or when code branches a lot or repeats a shape assumption across files. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-model-the-domain/SKILL.md) |
| [`principle-never-block-on-the-human`](skills/principle-never-block-on-the-human/SKILL.md) | Apply when tempted to ask 'should I do X?' on reversible work. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-never-block-on-the-human/SKILL.md) |
| [`principle-outcome-oriented-execution`](skills/principle-outcome-oriented-execution/SKILL.md) | Apply during planned rewrites and migrations with explicit phase boundaries. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-outcome-oriented-execution/SKILL.md) |
| [`principle-prove-it-works`](skills/principle-prove-it-works/SKILL.md) | Apply after completing a task, before declaring done. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-prove-it-works/SKILL.md) |
| [`principle-redesign-from-first-principles`](skills/principle-redesign-from-first-principles/SKILL.md) | Apply when integrating a new requirement into an existing design. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-redesign-from-first-principles/SKILL.md) |
| [`principle-separate-before-serializing-shared-state`](skills/principle-separate-before-serializing-shared-state/SKILL.md) | Apply when concurrent actors might write to the same file, branch, key, or state object. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-separate-before-serializing-shared-state/SKILL.md) |
| [`principle-sequence-verifiable-units`](skills/principle-sequence-verifiable-units/SKILL.md) | Apply to multi-step work (sweeps, migrations, runs of similar edits) and to how you stack commits and PRs. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-sequence-verifiable-units/SKILL.md) |
| [`principle-subtract-before-you-add`](skills/principle-subtract-before-you-add/SKILL.md) | Apply when sequencing an addition, refactor, or rewrite. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-subtract-before-you-add/SKILL.md) |
| [`principle-type-system-discipline`](skills/principle-type-system-discipline/SKILL.md) | Apply when designing types, reviewing a function signature, or writing code in any statically-typed language. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/skills/principle-type-system-discipline/SKILL.md) |

## Engineering (mattpocock)

| Skill | Purpose | Source |
|---|---|---|
| [`ask-matt`](skills/ask-matt/SKILL.md) | Ask which skill or flow fits your situation. A router over the skills in this repo. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/ask-matt/SKILL.md) |
| [`code-review`](skills/code-review/SKILL.md) ● | Review the changes since a fixed point (commit, branch, tag, or merge-base) along two axes: Standards (does the code follow this repo's documented… | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/code-review/SKILL.md) |
| [`codebase-design`](skills/codebase-design/SKILL.md) ● | Shared vocabulary for designing deep modules. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/codebase-design/SKILL.md) |
| [`diagnosing-bugs`](skills/diagnosing-bugs/SKILL.md) ● | Diagnosis loop for hard bugs and performance regressions. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/diagnosing-bugs/SKILL.md) |
| [`domain-modeling`](skills/domain-modeling/SKILL.md) ● | Build and sharpen a project's domain model. Use when discussing codebase terminology, writing or editing a CONTEXT.md, or recording or editing an ADR. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/domain-modeling/SKILL.md) |
| [`grill-with-docs`](skills/grill-with-docs/SKILL.md) ✱ | A relentless interview to sharpen a plan or design, which also creates docs (ADR's and glossary) as we go. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/grill-with-docs/SKILL.md) |
| [`implement`](skills/implement/SKILL.md) | Implement a piece of work based on a spec or set of tickets. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md) |
| [`improve-codebase-architecture`](skills/improve-codebase-architecture/SKILL.md) ✱ | Scan a codebase for deepening opportunities, present them as a visual HTML report, then grill through whichever one you pick. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/improve-codebase-architecture/SKILL.md) |
| [`prototype`](skills/prototype/SKILL.md) ● | Build a throwaway prototype to answer a design question. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/prototype/SKILL.md) |
| [`research`](skills/research/SKILL.md) ● | Investigate a question against high-trust primary sources and capture the findings as a Markdown file in the repo. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/research/SKILL.md) |
| [`resolving-merge-conflicts`](skills/resolving-merge-conflicts/SKILL.md) ● | Use when you need to resolve an in-progress git merge/rebase conflict. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/resolving-merge-conflicts/SKILL.md) |
| [`setup-matt-pocock-skills`](skills/setup-matt-pocock-skills/SKILL.md) | Configure this repo for the engineering skills: set up its issue tracker, triage label vocabulary, and domain doc layout. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/setup-matt-pocock-skills/SKILL.md) |
| [`tdd`](skills/tdd/SKILL.md) ✱● | Test-driven development. Use when the user wants to build features or fix bugs test-first, mentions "red-green-refactor", or wants integration tests. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/tdd/SKILL.md) |
| [`to-spec`](skills/to-spec/SKILL.md) | Turn the current conversation into a spec and publish it to the project issue tracker: no interview, just synthesis of what you've already discussed. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-spec/SKILL.md) |
| [`to-tickets`](skills/to-tickets/SKILL.md) | Break a plan, spec, or the current conversation into a set of tracer-bullet tickets, each declaring its blocking edges, published to the configured… | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets/SKILL.md) |
| [`triage`](skills/triage/SKILL.md) ✱ | Move issues and external PRs through a state machine of triage roles, categorise, verify, grill if needed, and write agent-ready briefs. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/triage/SKILL.md) |
| [`wayfinder`](skills/wayfinder/SKILL.md) ✱ | Plan a huge chunk of work (more than one agent session can hold) as a shared map of decision tickets on your issue tracker, and resolve them one at a… | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/wayfinder/SKILL.md) |
| [`wizard`](skills/wizard/SKILL.md) ● | Generate an interactive bash wizard that walks a human through steps only they can perform. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/wizard/SKILL.md) |

## Productivity (mattpocock)

| Skill | Purpose | Source |
|---|---|---|
| [`grill-me`](skills/grill-me/SKILL.md) ✱ | A relentless interview to sharpen a plan or design. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/grill-me/SKILL.md) |
| [`grilling`](skills/grilling/SKILL.md) ● | Grill the user relentlessly about a plan, decision, or idea. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/grilling/SKILL.md) |
| [`handoff`](skills/handoff/SKILL.md) ✱ | Compact the current conversation into a handoff document for another agent to pick up. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/handoff/SKILL.md) |
| [`teach`](skills/teach/SKILL.md) | Teach the user a new skill or concept, within this workspace. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/teach/SKILL.md) |
| [`to-questionnaire`](skills/to-questionnaire/SKILL.md) | Turn a decision you can't fully answer into a questionnaire for someone else to fill in. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/to-questionnaire/SKILL.md) |
| [`wait-what`](skills/wait-what/SKILL.md) | Stop. That last message did not land: re-pitch it. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/wait-what/SKILL.md) |
| [`writing-for-agents`](skills/writing-for-agents/SKILL.md) ● | Writing documents for agents. Use when creating or editing skills, or modifying AGENTS.md or CLAUDE.md. | [mattpocock](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/writing-for-agents/SKILL.md) |

## Rust (ECC)

| Skill | Purpose | Source |
|---|---|---|
| [`rust-patterns`](skills/rust-patterns/SKILL.md) ● | Idiomatic Rust patterns, ownership, error handling, traits, concurrency, and best practices for building safe, performant applications. | [affaan-m/ECC](https://github.com/affaan-m/ECC/blob/e04ea0b9cc8248686edf5ac751cadff550e162b8/skills/rust-patterns/SKILL.md) |
| [`rust-testing`](skills/rust-testing/SKILL.md) ● | Rust testing patterns including unit tests, integration tests, async testing, property-based testing, mocking, and coverage. Follows TDD methodology. | [affaan-m/ECC](https://github.com/affaan-m/ECC/blob/e04ea0b9cc8248686edf5ac751cadff550e162b8/skills/rust-testing/SKILL.md) |

## Yours

| Skill | Purpose | Source |
|---|---|---|
| [`coordinator-prompt`](skills/coordinator-prompt/SKILL.md) | Generate a multi-agent coordinator prompt file from a GitHub issue or parent issue graph — waves, worktrees, implementer/reviewer/fixer briefs, gates, PR. | authored locally |

## Task agents

omp resolves a subagent's model by agent name, so each panel seat is its own definition. `@opus`, `@gpt-sol` and `@fable` are role aliases from `modelRoles` in `~/.omp/agent/config.yml`.

| Agent | Model | Role | Source |
|---|---|---|---|
| [`poteto-agent`](agents/poteto-agent.md) | `@fable` | Routing target for poteto-mode work; autoloads the `poteto-mode` skill and may spawn delegates. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/agents/poteto-agent.md) |
| [`comment-sicko`](agents/comment-sicko.md) | `@opus` | Comment Sicko. Read-only hunt for narrating comments and workaround prose in a diff. | [cursor](https://github.com/cursor/plugins/blob/7314f723a487ec406b6369fe5865ba034cfed166/pstack/agents/comment-sicko.md) |
| [`poteto-critic-opus`](agents/poteto-critic-opus.md) | `@opus` | Read-only critic panel seat. | original |
| [`poteto-critic-gpt`](agents/poteto-critic-gpt.md) | `@gpt-sol` | Read-only critic panel seat. | original |
| [`poteto-critic-fable`](agents/poteto-critic-fable.md) | `@fable` | Read-only critic panel seat. | original |
| [`poteto-runner-opus`](agents/poteto-runner-opus.md) | `@opus` | Writing runner panel seat for arena and architect bakeoffs. | original |
| [`poteto-runner-gpt`](agents/poteto-runner-gpt.md) | `@gpt-sol` | Writing runner panel seat for arena and architect bakeoffs. | original |
| [`poteto-runner-fable`](agents/poteto-runner-fable.md) | `@fable` | Writing runner panel seat for arena and architect bakeoffs. | original |

## Ports applied

The pstack pack assumed Cursor's tools, model slugs and built-in skills. The mattpocock packs were already harness-agnostic apart from Claude Code's `Skill` tool, in 15 places. The ECC Rust skills needed nothing: they contain no harness references.

| Upstream | omp |
|---|---|
| `subagent_type: "X"` | `task` item with `agent: "X"` |
| `run_in_background: true` | dropped; `task` items are background and auto-deliver |
| `AskQuestion`, `Task`, todolist | `ask`, `task`, `todo` |
| `readonly: true` | a read-only agent type (`scout`, `poteto-critic-*`) |
| Call the `Skill` tool with "x" | read `skill://x` |
| `grok-4.6-fast-xhigh` | `@sonnet` |
| `claude-fable-5-1-thinking-max` | `@fable` |
| `~/.cursor/rules/pstack-models.mdc` | `~/.omp/agent/config.yml` (`task.agentModelOverrides`, `modelRoles`) |
| `create-skill` | the `writing-for-agents` skill, vendored here |
| `/loop`, `/goal` | an autonomous-run request; a goal file plus the `todo` list |
| cloud agents, Cursor dashboard | local `task` items; `hub list` / `hub jobs`; `~/.omp/agent/sessions/` |
| `git show origin/master:pstack/skills/…` | `skill://<name>` |
| `.cursor/worktrees` | `omp worktree list --json` |

## License

Every vendored skill is MIT licensed by its original author. The upstream license texts are kept verbatim in `LICENSES/`, one per upstream:

| Upstream | Copyright | File |
|---|---|---|
| cursor/plugins (pstack, cursor-team-kit) | Lauren Tan | [`LICENSES/pstack-cursor-plugins-MIT.txt`](LICENSES/pstack-cursor-plugins-MIT.txt) |
| mattpocock/skills | Matt Pocock | [`LICENSES/mattpocock-skills-MIT.txt`](LICENSES/mattpocock-skills-MIT.txt) |
| affaan-m/ECC | Affaan Mustafa | [`LICENSES/affaan-m-ECC-MIT.txt`](LICENSES/affaan-m-ECC-MIT.txt) |
