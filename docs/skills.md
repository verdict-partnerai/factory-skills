# Skills Reference

Detailed documentation for every skill in the factory-skills library.

---

## verdict-eval

**Agent:** Verdict
**Version:** 1.0.0
**Source:** [`verdict-eval/SKILL.md`](../verdict-eval/SKILL.md)

Idea evaluation skill with two modes. Operates entirely through GitHub Issue comments on `smcfactory/factory-ops`.

### Startup Mode

Rigorous go/no-go evaluation for ideas intended as businesses. Six forcing questions expose demand reality, status quo, desperate specificity, narrowest wedge, observation & surprise, and future-fit. Produces a design doc with verdict.

### Builder Mode

Collaborative brainstorming for hackathons, side projects, open source, research, and learning. Generative questions instead of interrogation. Can upgrade to Startup mode if real demand emerges.

### Phase Sequence

| Phase | Name | What Happens |
|-------|------|--------------|
| 1 | Issue Intake | Read issue, verify `evaluate` label, determine mode and product stage |
| 1.5 | Research Brief | Post tailored research tasks for Scout to complete before evaluation begins |
| 2A | Startup: Forcing Questions | Six questions, one at a time, pushed until answers are specific and evidence-based |
| 2B | Builder: Design Partner | Generative brainstorming questions, one at a time |
| 2.5 | Landscape Check | Web search for existing solutions, failed attempts, gaps |
| 3 | Premise Challenge | State premises as clear claims, Scout agrees or pushes back |
| 3.5 | Independent Review | Subagent reviews a structured summary, catches blind spots |
| 4 | Alternatives | Product approaches (Level 1) then implementation approaches (Level 2) |
| 5 | Design Doc | Structured doc from templates, self-reviewed then independently reviewed |
| 6 | Verdict | Final APPROVED/REJECTED decision with reasoning |
| 7 | Commit (if approved) | Design doc committed to repo on a branch |

### Label Lifecycle

```
new-idea -> evaluate -> in-review -> approved / rejected
```

Scout creates the issue and adds labels. Verdict transitions `evaluate` to `in-review` on pickup, then to `approved` or `rejected` on completion.

### Allowed Tools

`Bash`, `Read`, `Grep`, `Glob`, `WebSearch`, `Agent`
