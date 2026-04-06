# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

factory-skills is a shared skill library for factory agents. Each skill is a self-contained SKILL.md file in its own directory. No binaries, no build step, no dependencies.

## Repo Structure

- Each skill lives in its own directory (e.g., `verdict-eval/SKILL.md`)
- Skills are standalone Markdown files with YAML frontmatter
- No shared code between skills -- each skill is fully self-contained
- PRINCIPLES.md defines how factory agents operate (shared philosophy)

## Working With Skills

### Editing a skill
- Read the existing SKILL.md before making changes
- Preserve YAML frontmatter (name, description, allowed-tools)
- Preserve phase numbering -- downstream documentation references phases by number
- Test changes by having the relevant agent run the skill against a real or simulated Issue

### Adding a new skill
- Create a new directory at the repo root
- Add a SKILL.md with YAML frontmatter and phase-based instructions
- Update README.md skill table
- Follow PRINCIPLES.md for agent behavior guidelines

### SKILL.md format
```yaml
---
name: skill-name
version: X.Y.Z
description: |
  What this skill does.
allowed-tools:
  - Bash
  - Read
  ...
---

# Skill instructions here
```

## What NOT to Add

- No binaries or compiled code
- No telemetry or analytics
- No external service dependencies
- No agent-specific configuration (that belongs in each agent's home CLAUDE.md)
- No cross-skill dependencies (each skill must work standalone)
