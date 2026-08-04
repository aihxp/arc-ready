# arc-ready

![arc-ready](assets/hero.png)

**From "I have an idea" to "it's live" without the guesswork.**

One AI skill that walks a software project through every stage it has to go through anyway: what to build, how to build it, in what order, with what tools, then writing it, shipping it, watching it, launching it, and attacking it before someone else does.

[![lint](https://github.com/hannsxpeter/arc-ready/actions/workflows/lint.yml/badge.svg)](https://github.com/hannsxpeter/arc-ready/actions/workflows/lint.yml)
[![release](https://img.shields.io/badge/release-v1.2.1-blue)](https://github.com/hannsxpeter/arc-ready/releases/tag/v1.2.1)
[![version](https://img.shields.io/badge/source-1.2.1-blue)](CHANGELOG.md)
[![agent skills](https://img.shields.io/badge/Agent%20Skills-compatible-2f6fed)](SKILL.md)
[![hannsxpeter/pillars](https://img.shields.io/badge/hannsxpeter%2Fpillars-standard-0f766e)](https://github.com/hannsxpeter/pillars)
[![smoke](https://img.shields.io/badge/smoke-12%2F12-brightgreen)](scripts/dogfood-smoke.sh)
[![eval](https://img.shields.io/badge/eval-14%2F14-brightgreen)](EVALS.md)
[![license](https://img.shields.io/github/license/hannsxpeter/arc-ready)](LICENSE)

---

## The problem it solves

AI coding assistants are very good at producing something that looks finished. A screen appears. A button exists. A demo runs.

Then you look closer. The login screen is real but the data behind it is fake. The dashboard renders but nothing saves. The roadmap has no order. The "monitoring" fires alerts nobody can act on. The launch page makes claims the product cannot back up. Half of it is scaffolding with a note that says "hook this up later," and later never comes.

That is not a model problem. It is a process problem. Real software follows an arc, and skipping steps in that arc is exactly what produces work that demos well and collapses in contact with real users.

arc-ready makes the arc explicit and refuses to skip it.

## How it works, in plain language

Every software project travels the same road, whether anyone names it or not:

```
idea -> what to build -> how it fits together -> in what order
     -> with what tools -> a real repo -> the actual app
     -> shipping it -> watching it -> launching it -> hardening it
```

arc-ready turns each of those into a step with a written outcome, and each step has to pass before the next one starts. You cannot get an architecture without a clear product definition. You cannot get code without a roadmap. You cannot launch without a security pass.

That single rule (no step without the one before it) is where the quality comes from. There is no "we'll figure that out during the build," because the build is downstream of the figuring out.

## What you actually get

Each step leaves behind a plain-English document you can read, share, and hand to anyone: a teammate, an investor, a contractor, or another AI tool six months from now.

| Step | What it answers | What it leaves behind |
|---|---|---|
| Kickoff | Where are we, and what is the plan | A running progress ledger |
| Product definition | What are we building, for whom, and how do we know it worked | A product requirements doc |
| Architecture | How do the pieces fit, and what breaks first | A system design with the reasoning kept |
| Roadmap | What order, and what does "done" look like at each stage | A sequenced plan with real completion gates |
| Stack | Which technologies, and what would make us change our minds | A scored decision, not a preference |
| Repository | Is the project set up like a professional one | Structure, docs, automated checks, quality tooling |
| The app | Does it actually work end to end | Working features wired to a real backend, no placeholders |
| Deploy | Can we ship safely and undo it if we are wrong | A release pipeline with a tested rollback |
| Observe | Will we know when it breaks, before customers tell us | Health targets, alerts, and runbooks that were actually run |
| Launch | Is the public-facing story true and ready | Landing copy, share cards, waitlist, launch-week plan |
| Harden | What would an attacker find | A security review with fixes ranked by severity |

Everything lands in the project folder as ordinary Markdown files. Nothing is locked in a tool you have to keep paying for. See the [full file map](#where-everything-gets-written) below.

## Who it is for

- **Founders and solo builders** who can describe the product clearly but do not want to discover in month three that the foundation was never poured.
- **Product and project managers** working with AI-assisted engineers, who need the artifacts (requirements, roadmap, launch plan) to exist and be trustworthy.
- **Engineers** who want the discipline of a senior team's process without writing the checklists themselves.
- **Agencies and consultancies** delivering client work that has to survive a handover.
- **Teams adopting AI coding tools** who have already been burned by impressive-looking output that was not connected to anything.

You do not need to be technical to start. You need to be able to describe what you want to exist. arc-ready asks the rest.

## Getting started

Install once:

```bash
git clone https://github.com/hannsxpeter/arc-ready ~/.claude/skills/arc-ready
```

Then just talk to your AI assistant in your own words. It picks up from wherever you are:

**Starting from nothing:**

```text
I have an idea for a booking app for small salons. Walk me through to launch.
```

**Already have something half-built:**

```text
Write a PRD for this app.
```

```text
Set up a deploy pipeline for this project.
```

**Want an honest second opinion on work already done:**

```text
Audit the architecture in .architecture-ready/ARCH.md.
```

There is no dashboard to learn and no configuration to fill out. The skill reads your project, works out which stage you are at, and starts there.

## Four ways to use it

- **Full arc.** Start at an idea, finish at a hardened launch. This is the default.
- **Fill a gap.** You already have a codebase and you are missing one thing (requirements, a roadmap, monitoring, a launch plan). It goes straight to that step.
- **Audit.** Score what already exists against the same standard, and get told plainly what is missing.
- **Multi-repo.** Design a set of related projects that have to stay consistent with each other.

## It knows what kind of thing you are building

A command-line tool does not need a design system. A data pipeline does not need share cards. A mobile app has an app-store review that a web app does not. arc-ready decides what kind of product you are building first, then applies only the standards that actually apply.

| If you are building | "Done" means, at minimum |
|---|---|
| A web application | A real user journey that works end to end, including permissions and failure states |
| An API or service | A versioned contract, a working authenticated request, and telemetry an operator can use |
| A CLI or SDK | Something installable, a stable interface, a working example, and a compatibility test |
| A mobile or desktop app | Correct lifecycle behavior, offline handling, permissions, packaging, and an upgrade path |
| A data or ML system | A reproducible pipeline, data contracts, quality checks, evaluation, and a way back |
| Infrastructure | A validated plan, policy checks, a safe apply, drift detection, and rollback |

On top of that, guidance composes across four dimensions: the product form, the product archetype (marketplace, SaaS, internal tool, and so on), the industry, and any regulated environment you are in. That last one matters if you touch health data, payments, or personal data in Europe.

Details live in the [product-form router](references/building/product-form-router.md), the [domain registry](references/building/domain-registry.md), and the [domain router](references/building/domain-considerations.md), which covers 37 focused profiles.

## Common questions

**Do I have to be a developer?**
No. You need to be able to describe the product you want. The planning steps are conversations in plain English, and the documents they produce are meant to be read by non-engineers. The building steps do assume an AI coding assistant is doing the typing.

**Does it write the code, or just the paperwork?**
Both, and the paperwork is the reason the code holds up. The building step ships working features connected to a real backend. Placeholder data, stub screens, and "TODO: wire this up" are explicitly refused.

**What is a PRD?**
A product requirements document: a short written answer to what you are building, who it is for, what it must do, and how you will know it worked. It is the thing that stops a project from quietly becoming a different project.

**I already started building. Is it too late?**
No. Point it at your existing project and ask for whichever piece is missing. It fills gaps without demanding a rewrite.

**How long does the full arc take?**
That depends entirely on the product. The planning steps are typically a session or two of back and forth. The value is not speed, it is not having to redo the work.

**Does this replace my developers?**
No. It replaces the checklists, the forgotten steps, and the arguments about what "done" means. Judgment stays with people, and arc-ready deliberately stops and asks when a decision is genuinely yours to make.

**Where does my project data go?**
Into your own project folder, as plain Markdown files, on your machine. arc-ready is a set of instructions your AI assistant reads. It is not a service, and there is no account.

**Is it locked to one AI tool?**
No. It follows the Agent Skills standard and works across several assistants. See [Installation options](#installation-options).

## Installation options

arc-ready is an Agent Skills compatible skill. Install it the way your assistant expects:

- **Claude Code**: run `/skills install` from this repo, or symlink the repo into `~/.claude/skills/arc-ready/`.
- **Codex CLI**: follow the Codex Skills install protocol.
- **Cursor or Windsurf**: copy `SKILL.md` into the rules directory and reference it.
- **Antigravity, Pi, OpenClaw**: use the harness's Agent Skills install path.
- **Any AGENTS.md-aware tool** (Aider, Zed, Warp, Roo Code, Jules, Factory, Amp, Devin): arc-ready writes an `AGENTS.md` into your project describing how to load its context, and the tool reads the artifacts directly.

## Where everything gets written

Everything is written into your project as `.<step>-ready/` folders. These paths are a stable contract, so other tools can rely on them.

| Step | Artifact | Path |
|---|---|---|
| 0 | Arc progress ledger | `.arc-ready/PROGRESS.md` |
| 1.1 | Product requirements | `.prd-ready/PRD.md` (plus HANDOFF, AUDIT) |
| 1.2 | Architecture | `.architecture-ready/ARCH.md` (plus HANDOFF, adr/) |
| 1.3 | Roadmap | `.roadmap-ready/ROADMAP.md` (plus HANDOFF, retrospectives/) |
| 1.4 | Stack decision | `.stack-ready/STACK.md` |
| 2.1 | Repo scaffolding | repo root (`.github/`, `package.json`, README, and so on) plus `.repo-ready/SCAFFOLD.md` (or `.repo-ready/AUDIT-REPORT.md` in audit mode) |
| 2.2 | Production state | `.production-ready/STATE.md` |
| 3.1 | Deploy state | `.deploy-ready/DEPLOY.md` (plus PLAN, TOPOLOGY, STATE) |
| 3.2 | Observability state | `.observe-ready/OBSERVE.md` (plus SLOs, INDEPENDENCE, STATE) |
| 3.3 | Launch state | `.launch-ready/STATE.md` (plus runbook, copy, and `.launch-ready/PREPUBLICATION.md` before anything goes public) |
| 3.4 | Hardening findings | `.harden-ready/FINDINGS.md` (plus remediation) |
| 0 / 2.1 | Cross-tool agent brief | Pillars-compatible `AGENTS.md` at the project root |
| 2.1 | Agent memory | `agents/context.md`, `agents/repo.md`, and source-backed `agents/*.md` |

### Memory that outlives the session

Chat history disappears. Six months later a new assistant (or a new hire) opens the project and knows nothing about why anything was decided the way it was.

arc-ready fixes that by writing a durable memory layer into the project using the [Pillars](https://github.com/hannsxpeter/pillars) standard: a short brief at the root plus task-routed notes distilled from the arc documents. Whoever picks the project up next loads context in seconds instead of reading everything from scratch. Existing `AGENTS.md` files are never silently overwritten.

## What it refuses to do

Guardrails are the product. arc-ready will not:

- Produce architecture diagrams that contain no actual decisions.
- Call a technology preference an architecture.
- Ship features backed by fake data or stub screens.
- Write monitoring that alerts on things nobody can act on.
- Write launch copy that survives only because nobody checked it.
- Mark a security review complete with unresolved critical findings.
- Let anything go public without a fresh pre-publication record tied to the current security pass.

Each of those is a named failure mode with a mechanical check behind it, carried over from the eleven skills arc-ready consolidates. They live under `references/<tier>/<skill>-antipatterns.md`.

## Where it came from

arc-ready is the evolution of [hannsxpeter/ready-suite](https://github.com/hannsxpeter/ready-suite), which did the same job across eleven separate skills and twelve repositories.

The discipline worked. The overhead did not: eleven installs, coordinated patches, a synchronization ritual across repos. arc-ready keeps every failure mode, every check, and every guardrail, and collapses it into one install, one file to read, one repo to update.

The documents it produces are at exactly the same paths, so existing projects, the dogfood example, and downstream orchestrators (GSD, BMAD, Spec Kit, Superpowers) keep working unchanged. Already on ready-suite? See [MIGRATION.md](MIGRATION.md). The eleven-skill suite remains available and supported.

## Current release

**v1.2.1** is a documentation release. This README was rewritten for a general audience, so someone who is not an engineer can tell what arc-ready does and whether it is for them. No workflow behavior changed.

From v1.2.0: capacity estimation in the planning step, so the architecture stage works out its own resource envelope (peak traffic, storage growth, bandwidth, cost, and the thresholds that would force a redesign) instead of borrowing numbers that later stages then spend.

Also current, from v1.1.0: product-form routing, composable domain guidance, progressive disclosure of the reference library, deterministic and live evaluations, official Agent Skills validation, OWASP Top 10:2025 routing, and the serialized public activation gate. The 1.0 artifact contract is stable.

## Stability promise

The contract is intentionally small, and it holds:

- The canonical `.<step>-ready/` paths remain the source of truth.
- File-system projects always get a Pillars-compatible `AGENTS.md` plus `agents/context.md` and `agents/repo.md` as the memory floor.
- Additional `agents/*.md` files are added only when the arc documents contain enough evidence to support them. A stub says it is a stub instead of inventing decisions.
- An existing non-Pillars `AGENTS.md` is respected, and the blocker is recorded rather than the file being overwritten.
- Public activation always requires a fresh pre-publication record tied to the current hardening revision. Preparing a launch never authorizes one.

## Documentation map

- **New here**: read this file, then [SKILL.md](SKILL.md) for the workflow body.
- **Coming from ready-suite**: [MIGRATION.md](MIGRATION.md).
- **Maintaining arc-ready**: [MAINTAINING.md](MAINTAINING.md) for release rituals and evidence requirements.
- **Evaluating it**: [EVALS.md](EVALS.md) for the deterministic checks and scoring rules.
- **Contributing**: [CONTRIBUTING.md](CONTRIBUTING.md) and [AGENTS.md](AGENTS.md) before touching load-bearing files.
- **Changing emitted project memory**: read `references/orchestration/agents-md-template.md` and `references/building/pillars-integration.md` together.

<details>
<summary><strong>Phrases that trigger arc-ready</strong> (you do not need to memorize any of these)</summary>

Say what you want in your own words. These are the surfaces the skill recognizes, consolidated from the eleven-skill suite.

**Kickoff**: kickoff, new project from scratch, walk me through idea to launch, help me ship it end-to-end, orchestrate the whole arc, I have an idea what next.

**Planning**: write a PRD, product spec, requirements doc, one-pager, product brief, problem statement, design the architecture, system diagram, monolith or microservices, integration shape, service boundaries, data architecture, ADR, trust boundaries, C4 diagram, build a roadmap, milestone plan, quarterly plan, sequence the work, Now-Next-Later, Shape Up cycle, PI planning, what stack should I use, Next.js vs Remix, pick a database, Postgres or Mongo, which auth provider, hosting recommendation.

**Building**: set up a repo, initialize a project, add documentation, set up CI, configure linting, add a README, set up GitHub Actions, make my repo professional, add contributing guidelines, set up release automation, adopt Pillars, task-routed agent memory, build a web app, API or service, CLI or SDK, mobile or desktop app, data or ML system, infrastructure project, dashboard, admin panel, internal tool, or CRUD app.

**Shipping**: deploy this, CI/CD pipeline, promote to staging, zero-downtime migration, expand-contract, rollback, canary, blue/green, progressive rollout, first deploy, environment parity, GitHub Actions pipeline, GitOps, add monitoring, define an SLO, alerts when X, add Datadog / Honeycomb / Sentry / Grafana, write a runbook, on-call setup, post-mortem, structured logging, OpenTelemetry, distributed tracing, error budget policy, launch my product, build a landing page, Product Hunt, Show HN, waitlist, OG card, launch-day SEO, press kit, launch week plan, adversarial review, pen-test prep, OWASP walkthrough, SOC 2 / HIPAA / PCI-DSS / GDPR gap check, responsible disclosure, bug bounty, post-incident hardening, security review before launch.

</details>

<details>
<summary><strong>Jargon, translated</strong></summary>

- **PRD**: the written answer to what you are building, for whom, and how you will know it worked.
- **Architecture**: how the parts of the system fit together, and which decisions would be expensive to reverse.
- **Stack**: the specific technologies chosen, and the conditions that would justify changing them.
- **Repo (repository)**: the folder holding your code, its history, and its automated checks.
- **CI/CD**: automation that checks and ships your code so a human does not do it by hand each time.
- **Rollback**: undoing a release safely when it turns out to be wrong.
- **Canary**: releasing to a small slice of users first, with a rule for when to stop.
- **SLO**: the reliability target you promise, phrased so you can tell whether you are meeting it.
- **Runbook**: step-by-step instructions for handling a specific failure at 3am.
- **OWASP Top 10**: the industry list of the most common ways applications get attacked.
- **Hardening**: deliberately attacking your own product before someone else does.
- **Agent memory**: durable project notes an AI assistant can load later instead of relearning everything.

</details>

<details>
<summary><strong>Repository layout</strong> (for contributors)</summary>

```
arc-ready/
  SKILL.md                       The orchestrator body.
  CHANGELOG.md                   Version history.
  README.md                      This file.
  LICENSE                        MIT.
  AGENTS.md                      Cross-tool agent brief for arc-ready itself.
  CLAUDE.md -> AGENTS.md         Symlink (Claude Code overlay).
  SECURITY.md                    Vulnerability reporting channel.
  CONTRIBUTING.md                Contribution guide.
  MAINTAINING.md                 Single-repo release rituals.
  MIGRATION.md                   Migration guide for ready-suite users.
  EVALS.md                       Evaluation model and release evidence.
  evals/cases/                   Live-harness prompts and rubrics.
  scripts/lint.sh                Single-repo meta-linter.
  scripts/eval.sh                Deterministic behavioral checks.
  scripts/release-check.sh       Release-grade validation entry point.
  requirements/skills-ref.txt    Pinned official validator dependency.
  config/unicode-baseline.txt    Reviewed inherited Unicode counts.
  .github/
    CODEOWNERS                   Code ownership.
    workflows/lint.yml           CI lint job.
  references/
    orchestration/               Tier 0 references.
    planning/                    Tier 1 references (PRD, ARCH, ROADMAP, STACK).
    building/                    Tier 2 references (REPO, PRODUCTION).
      domains/                   Focused product and industry profiles.
    shipping/                    Tier 3 references (DEPLOY, OBSERVE, LAUNCH, HARDEN).
    shared/                      Cross-tier references (RESEARCH, ORCHESTRATORS).
```

</details>

## License and contributing

MIT. See [LICENSE](LICENSE).

Contributions are welcome: start with [CONTRIBUTING.md](CONTRIBUTING.md). Release rituals are in [MAINTAINING.md](MAINTAINING.md), and security reports go through [SECURITY.md](SECURITY.md).
