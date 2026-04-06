# Factory Skills

Shared skill library for factory agents (Verdict, Scout, and future agents). Each skill is a self-contained SKILL.md that any Claude Code agent can load.

No binaries, no telemetry, no external dependencies. Just Markdown skill definitions.

## Install

```bash
git clone https://github.com/0xsmcai/factory-skills.git ~/.claude/skills/factory
```

Each agent's CLAUDE.md or settings should reference skills at:
```
~/.claude/skills/factory/{skill-name}/SKILL.md
```

## Skills

| Skill | Agent | Description |
|-------|-------|-------------|
| `verdict-eval` | Verdict | Startup/builder idea evaluation via GitHub Issues. Six forcing questions, premise challenge, two-level alternatives, design doc output. |

## Repo Structure

```
factory-skills/
├── README.md
├── CLAUDE.md
├── PRINCIPLES.md
├── LICENSE
├── verdict-eval/
│   └── SKILL.md
└── (future skills as sibling directories)
```

Each skill is one directory with one SKILL.md file. Skills are self-contained -- no shared binaries, no cross-skill dependencies. An agent loads a skill by reading its SKILL.md and following the instructions.

## Adding a New Skill

1. Create a directory: `mkdir my-skill/`
2. Write `my-skill/SKILL.md` with YAML frontmatter (name, description, allowed-tools) and the skill instructions
3. Add the skill to the table above
4. Commit and push

## How Skills Work

A skill is a Markdown file with:
- **YAML frontmatter** -- name, description, allowed tools
- **Phase-based instructions** -- step-by-step workflow the agent follows
- **Templates** -- output formats (design docs, reports, etc.)

Agents load skills via Claude Code's skill system. The skill defines what the agent does; the agent's CLAUDE.md defines who the agent is.

## Agents

| Agent | Role | Home | Skills Used |
|-------|------|------|-------------|
| Verdict | VC partner -- evaluates startup ideas | `~/` on verdict host | `verdict-eval` |
| Scout | Idea researcher -- finds ideas on X, posts as GitHub Issues | TBD | TBD |

All agents operate through GitHub Issues on [0xsmcai/factory-ops](https://github.com/0xsmcai/factory-ops).
