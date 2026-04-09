# Factory Skills

Skill library for factory agents. Each skill is a self-contained `SKILL.md` in its own directory. No binaries, no build step, no external dependencies. Just Markdown skill definitions that Claude Code agents load and follow.

Built for the [0xSMC](https://github.com/0xsmcai) autonomous startup factory.

## Quick Start

```bash
git clone https://github.com/verdict-partnerai/factory-skills.git ~/.claude/skills/factory
```

Then symlink the skills your agent needs:

```bash
# For Verdict agent
ln -sf ~/.claude/skills/factory/verdict-eval ~/.claude/skills/verdict-eval
```

## Skills

| Skill | Agent | Phase | Description |
|-------|-------|-------|-------------|
| [`verdict-eval`](verdict-eval/SKILL.md) | Verdict | Think | Idea evaluation through six forcing questions, premise challenge, alternatives generation, and design doc output. Startup mode (go/no-go) and Builder mode (brainstorm). |

## How It Works

1. **Scout** finds ideas on X, posts them as GitHub Issues on `smcfactory/factory-ops` with raw signal (tweet, engagement, gut take)
2. **Verdict** picks up Issues labeled `evaluate`, sends Scout a tailored research brief, then runs the evaluation
3. Approved ideas get a design doc committed to the repo. Rejected ideas get a clear explanation why.

The evaluation follows a strict phase sequence:

```
Intake -> Research Brief -> Forcing Questions -> Landscape Check -> Premise Challenge -> Independent Review -> Alternatives -> Design Doc -> Verdict
```

Every phase completes before the next begins. No shortcuts. No skipped questions.

## Agents

| Agent | Role | GitHub | Skills |
|-------|------|--------|--------|
| Verdict | VC partner -- evaluates ideas, delivers go/no-go | [`verdict-partnerai`](https://github.com/verdict-partnerai) | `verdict-eval` |
| Scout | Idea researcher -- finds signals on X, posts Issues | [`0xsmcai`](https://github.com/0xsmcai) | TBD |

All agents communicate through GitHub Issues on [smcfactory/factory-ops](https://github.com/smcfactory/factory-ops).

## Repo Structure

```
factory-skills/
├── README.md           # This file
├── CLAUDE.md           # Instructions for Claude Code when editing this repo
├── PRINCIPLES.md       # Shared agent operating principles
├── docs/
│   └── skills.md       # Detailed skill documentation
└── verdict-eval/
    └── SKILL.md        # Verdict's evaluation skill
```

## Philosophy

**Rigor over speed.** Building the wrong thing costs more than an extra hour of hard questions.

**Evidence over assumption.** Positions based on what you can point to -- a tweet, a transaction, a behavior, a number. When evidence is missing, say so.

**Grounded proposals only.** Every recommendation references a proven model. Speculative approaches are options, never recommendations.

See [PRINCIPLES.md](PRINCIPLES.md) for the full set.

## Adding a New Skill

1. Create a directory: `mkdir my-skill/`
2. Write `my-skill/SKILL.md` with YAML frontmatter and phase-based instructions
3. Add the skill to the table above and to `docs/skills.md`
4. Follow [PRINCIPLES.md](PRINCIPLES.md) for agent behavior guidelines
5. Commit and push

## Skill Format

```yaml
---
name: skill-name
version: X.Y.Z
description: |
  What this skill does and when to invoke it.
allowed-tools:
  - Bash
  - Read
  ...
---

# Skill instructions here (phase-based)
```

