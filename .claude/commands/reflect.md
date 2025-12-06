---
description: Review session and recommend updates to CLAUDE.md, skills, and docs
---

# Session Reflection

Review this session and identify learnings worth capturing. Focus on:

- **Corrections** - Where you made mistakes and had to fix them
- **Discoveries** - Things we figured out about this codebase, tools, or workflows
- **Patterns** - Approaches that worked well and should be repeated

## Guiding Principles

- **Terse** - Minimal words, maximum signal
- **Tactical** - Specific and actionable, not abstract guidance
- **Evidence-based** - Each recommendation must tie to a specific session event
- **Simplest thing possible** - Seek to improve, not fix; one small improvement over none
- **Project-local only** - Never modify global config or ~/.claude/

## Update Targets

| Target | Location | When to use |
|--------|----------|-------------|
| CLAUDE.md | `./CLAUDE.md` | Project conventions, gotchas, tool usage |
| Skills | `./.claude/skills/` | Reusable workflows worth capturing |
| Docs | `./docs/` | Documentation gaps discovered |

**Scoping rule:** If a learning relates to a global skill, recommend copying it to `.claude/skills/` first, then modifying the local copy.

## Output Format

Present recommendations in two tiers:

```
## Recommended

1. [CLAUDE.md] <brief description of what to add/update>
2. [skill] <brief description of skill to create>
3. [doc] <brief description of doc update>

## Consider

4. [CLAUDE.md] <lower confidence suggestion>
5. [skill] <broader scope idea>
```

## Instructions

1. Review the session for corrections, discoveries, and patterns
2. Apply the guiding principles strictly - when in doubt, leave it out
3. Present recommendations in the format above
4. **Wait for user approval** - do not make any changes yet
5. After user responds, apply only the approved items
6. Confirm what was updated

If the session has no meaningful learnings, say so briefly and don't force recommendations.
